import { useEffect, useState, useMemo, useCallback } from 'react';


// --- CONFIGURATION DATA ---
const EMAILJS_USER_ID = 'YOUR_EMAILJS_USER_ID'; // <-- REPLACE THIS with your actual EmailJS User ID

const CHECKLIST_SECTIONS = [
    {
        title: "Interior: Cosmetic & Structure",
        items: [
            { item: "Batten Strips/Trim", location: "Throughout", description: "Loose, missing, or misaligned strips." },
            { item: "Wall/Ceiling Seams", location: "Throughout", description: "Obvious gaps or large cracks in drywall/seams." },
            { item: "Flooring", location: "Throughout", description: "Squeaks, bubbles, loose tiles, or lifted seams." },
            { item: "Doors (Interior)", location: "Throughout", description: "Do not latch, stick, rub the frame, or have loose hardware." },
            { item: "Doors (Exterior)", location: "Front/Back", description: "Seal properly, latch securely, and align correctly." },
            { item: "Cabinets/Drawers", location: "Kitchen/Baths", description: "Loose hinges, drawers stick, missing hardware, or visible damage." },
            { item: "Countertops", location: "Kitchen/Baths", description: "Scratches, chips, or loose/lifting seams." },
            { item: "Vinyl/Laminate", location: "Throughout", description: "Scratches, dents, or tears on finished surfaces." },
            { item: "Windows", location: "Throughout", description: "Screens installed, open/close smoothly, and lock securely." },
            { item: "Faucets/Fixtures", location: "Kitchen/Baths", description: "Loose handles or visible leaks at the base/connection." },
        ]
    },
    {
        title: "Plumbing, Electrical, & Appliances",
        items: [
            { item: "Water Flow/Pressure", location: "All Sinks/Tubs", description: "Test all faucets; check for low pressure or unusual noise." },
            { item: "Toilets", location: "All Bathrooms", description: "Flush properly, no running or leaks at the base." },
            { item: "Water Heater", location: "Utility/Exterior", description: "Functioning (providing hot water). Check for leaks near the unit." },
            { item: "GFCI Outlets", location: "Kitchen/Baths/Exterior", description: "Press TEST button to ensure they trip, then press RESET." },
            { item: "Switches & Outlets", location: "Throughout", description: "All switches operate their lights/fans; outlets have power." },
            { item: "Smoke/Carbon Monoxide Alarms", location: "Throughout", description: "Test all alarms (usually a test button on the unit)." },
            { item: "Appliances", location: "Kitchen", description: "Range, Dishwasher, Microwave, Refrigerator are fully operational." },
        ]
    },
    {
        title: "Exterior & HVAC",
        items: [
            { item: "Siding & Skirting", location: "Exterior", description: "Missing panels, dents, gaps, or improperly fastened skirting." },
            { item: "Roof Vents/Shingles", location: "Roof/Exterior", description: "Check for loose shingles, damage, or open vents/seals." },
            { item: "HVAC (Heat/AC)", location: "Thermostat/Units", description: "Run both Heat and Cooling cycles to ensure proper function." },
            { item: "Ductwork/Vents", location: "Floor/Ceiling", description: "Vents are securely fastened and air is flowing strongly to all rooms." },
            { item: "Home Leveling", location: "Foundation", description: "Check for noticeable slopes in floors or difficulty closing doors (structural issue)." },
            { item: "Tie-Downs/Anchors", location: "Under Home", description: "Visibly check anchors/straps for obvious signs of looseness or damage." },
        ]
    }
];

const COMMUNITY_OPTIONS = [
    "Rancho Serenidad",
    "Villas De Mariposa",
    "Brazos Pointe",
    "Solena",
    "Other"
];

const DEFAULT_FORM_DATA = {
    homeownerName: '',
    community: '',
    otherCommunity: '', // New field for 'Other' community
    lotNumber: '',
    serialNumber: '',
    // purchaseDate removed
    contactPhone: '',
    email: '',
    checklistStatus: CHECKLIST_SECTIONS.flatMap(section =>
        section.items.map(item => ({
            id: `${item.item.replace(/\s/g, '_')}_${item.location.replace(/\s/g, '_')}`,
            item: item.item,
            location: item.location,
            status: 'UNCHECKED', // OK, ISSUE, UNCHECKED
            notes: '',
        }))
    )
};

// --- MAIN APP COMPONENT ---

const App = () => {
    // --- EMAILJS CONFIG CONSTANTS ---
    // NOTE: Replace these placeholder IDs with your actual IDs from EmailJS
    const SERVICE_ID = 'service_warranty_submissions';
    const PRIMARY_TEMPLATE_ID = 'template_warranty_report'; // For sending to warranty@peakmhc.com
    const CONFIRMATION_TEMPLATE_ID = 'template_auto_response'; // For sending to the homeowner

    // Load EmailJS script on component mount - NOW CORRECTLY PLACED INSIDE THE FUNCTIONAL COMPONENT
    useEffect(() => {
        // Check if the script is already loaded
        if (!document.getElementById('emailjs-script')) {
            const script = document.createElement('script');
            script.id = 'emailjs-script';
            script.src = 'https://cdn.jsdelivr.net/npm/@emailjs/browser@4/dist/email.min.js';
            script.onload = () => {
                // Initialize EmailJS once the script is loaded
                if (window.emailjs) {
                     // --- IMPORTANT: REPLACE WITH YOUR ACTUAL USER ID ---
                    window.emailjs.init(EMAILJS_USER_ID);
                }
            };
            document.head.appendChild(script);
        } else {
             // Re-initialize if the script was already there (e.g., in development environment)
            if (window.emailjs) {
                window.emailjs.init(EMAILJS_USER_ID);
            }
        }
    }, []);


    // Resetting state to default as Firebase persistence is removed
    const [formData, setFormData] = useState(DEFAULT_FORM_DATA);
    const [message, setMessage] = useState('');
    const [view, setView] = useState('checklist'); // 'checklist' or 'report'
    const [isSubmitting, setIsSubmitting] = useState(false);
    
    // Auto-calculate submission date
    const submissionDate = useMemo(() => new Date().toLocaleDateString('en-US', {
        year: 'numeric',
        month: 'long',
        day: 'numeric'
    }), []);


    // Handler for general form input (Name, Lot, etc.)
    const handleFormChange = (e) => {
        const { name, value } = e.target;
        setFormData(prev => ({
            ...prev,
            [name]: value,
        }));
        setMessage('');
    };

    // Handler for checklist item updates
    const handleChecklistChange = useCallback((id, key, value) => {
        setFormData(prev => {
            const newChecklistStatus = prev.checklistStatus.map(item => {
                if (item.id === id) {
                    return {
                        ...item,
                        [key]: value,
                        // If status changes from ISSUE, clear notes
                        ...(key === 'status' && value !== 'ISSUE' && { notes: '' })
                    };
                }
                return item;
            });
            return {
                ...prev,
                checklistStatus: newChecklistStatus,
            };
        });
        setMessage('');
    }, []);

    // Memoized array of only the items marked as 'ISSUE'
    const issuesList = useMemo(() => {
        return formData.checklistStatus.filter(item => item.status === 'ISSUE' && item.notes.trim() !== '');
    }, [formData.checklistStatus]);

    // Memoized final report text for email body (using template variables)
    const finalReportText = useMemo(() => {
        const issuesSummary = issuesList.map((item, index) => {
            const locationDetail = item.location ? ` (Location: ${item.location})` : '';
            return `${index + 1}. ${item.item}${locationDetail}\n   Description: ${item.notes}`;
        }).join('\n\n');

        return issuesSummary || 'No actionable issues with description were reported on the 30-Day Checklist.';
    }, [issuesList]);

    // Consolidate final form data for submission
    const finalSubmissionData = useMemo(() => {
        const community = formData.community === 'Other' ? formData.otherCommunity : formData.community;
        
        return {
            ...formData,
            community: community,
            issuesReport: finalReportText,
            totalIssues: issuesList.length,
            toEmail: 'warranty@peakmhc.com', // Target email
            submissionDate: submissionDate, // Include submission date
            // These map to EmailJS template variables
        };
    }, [formData, finalReportText, issuesList, submissionDate]);
    
    // Function to handle EmailJS submission
    const handleEmailSubmit = async () => {
        if (isSubmitting || !window.emailjs) return;

        // Simple validation check for required fields before sending
        if (!formData.homeownerName || !formData.email || !formData.lotNumber || (formData.community === 'Other' && !formData.otherCommunity) || (!formData.community && formData.community !== 'Other')) {
            setMessage('❌ Please fill in all required Homeowner Information fields (Name, Email, Lot Number, Community).');
            return;
        }

        // Check if issues were marked but no notes were provided
        const emptyNotes = formData.checklistStatus.filter(item => item.status === 'ISSUE' && item.notes.trim() === '');
        if (emptyNotes.length > 0) {
            setMessage(`⚠️ ${emptyNotes.length} issue(s) are marked but missing descriptions. Please complete all notes before submitting.`);
            return;
        }
        
        setIsSubmitting(true);
        setMessage('⏳ Sending report...');

        try {
            // Send the primary email to warranty@peakmhc.com
            const primaryResponse = await window.emailjs.send(
                SERVICE_ID, // Using descriptive constant
                PRIMARY_TEMPLATE_ID, // Using descriptive constant
                finalSubmissionData
            );
            
            // Send the confirmation email to the homeowner
            await window.emailjs.send(
                SERVICE_ID, // Using descriptive constant
                CONFIRMATION_TEMPLATE_ID, // Using descriptive constant
                finalSubmissionData
            );

            setMessage('✅ Success! Your 30-Day Warranty Request has been submitted, and a confirmation email has been sent to you.');
            // Optionally reset the form after successful submission
            setFormData(DEFAULT_FORM_DATA);

        } catch (error) {
            console.error('EmailJS Submission Error:', error);
            setMessage(`❌ Submission failed. Error: ${error.text || error}. Please ensure EmailJS IDs are configured correctly.`);
        } finally {
            setIsSubmitting(false);
        }
    };


    // --- CHECKLIST VIEW COMPONENT ---

    const ChecklistView = () => (
        <div className="space-y-6">
            <div className="bg-blue-50 border border-blue-200 p-4 rounded-xl space-y-3">
                <h2 className="text-xl font-bold text-blue-700">Homeowner Information (Required)</h2>
                <input
                    type="text"
                    name="homeownerName"
                    placeholder="Homeowner Name *"
                    value={formData.homeownerName}
                    onChange={handleFormChange}
                    className="w-full p-2 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500"
                    required
                />
                
                {/* Community Dropdown Logic */}
                <select
                    name="community"
                    value={formData.community}
                    onChange={handleFormChange}
                    className="w-full p-2 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500"
                    required
                >
                    <option value="" disabled>Select Community *</option>
                    {COMMUNITY_OPTIONS.map(name => (
                        <option key={name} value={name}>{name}</option>
                    ))}
                </select>
                
                {formData.community === 'Other' && (
                     <input
                        type="text"
                        name="otherCommunity"
                        placeholder="Specify Other Community Name *"
                        value={formData.otherCommunity}
                        onChange={handleFormChange}
                        className="w-full p-2 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500"
                        required
                    />
                )}
                
                <div className="grid grid-cols-1 sm:grid-cols-2 gap-3">
                    <input
                        type="text"
                        name="lotNumber"
                        placeholder="Lot Number *"
                        value={formData.lotNumber}
                        onChange={handleFormChange}
                        className="w-full p-2 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500"
                        required
                    />
                    <input
                        type="text"
                        name="serialNumber"
                        placeholder="Home Serial Number"
                        value={formData.serialNumber}
                        onChange={handleFormChange}
                        className="w-full p-2 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500"
                    />
                </div>
                <div className="grid grid-cols-1 sm:grid-cols-2 gap-3">
                    <input
                        type="tel"
                        name="contactPhone"
                        placeholder="Contact Phone Number"
                        value={formData.contactPhone}
                        onChange={handleFormChange}
                        className="w-full p-2 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500"
                    />
                    <input
                        type="email"
                        name="email"
                        placeholder="Email Address *"
                        value={formData.email}
                        onChange={handleFormChange}
                        className="w-full p-2 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500"
                        required
                    />
                </div>
                {/* Removed Date of Purchase input field */}
            </div>

            {CHECKLIST_SECTIONS.map((section, sectionIndex) => (
                <div key={sectionIndex} className="space-y-3 p-4 bg-white rounded-xl shadow-md border border-gray-100">
                    <h2 className="text-2xl font-extrabold text-gray-800 border-b pb-2 mb-4">
                        {section.title}
                    </h2>
                    
                    {section.items.map((item, itemIndex) => {
                        const uniqueId = `${item.item.replace(/\s/g, '_')}_${item.location.replace(/\s/g, '_')}`;
                        const currentStatus = formData.checklistStatus.find(s => s.id === uniqueId) || { status: 'UNCHECKED', notes: '' };
                        const isIssue = currentStatus.status === 'ISSUE';
                        const cardClasses = isIssue ? 'border-red-400 bg-red-50' : currentStatus.status === 'OK' ? 'border-green-400 bg-green-50' : 'border-gray-200 bg-white';
                        
                        return (
                            <div key={itemIndex} className={`p-4 rounded-lg border-2 transition-colors duration-200 ${cardClasses}`}>
                                <div className="flex justify-between items-start space-x-4 mb-2">
                                    <div className="flex-1">
                                        <p className="font-semibold text-lg text-gray-900">{item.item}</p>
                                        <p className="text-sm text-gray-500">
                                            <span className="font-medium text-gray-600">Location:</span> {item.location}
                                            <span className="mx-2 text-gray-300">|</span>
                                            <span className="font-medium text-gray-600">Check:</span> {item.description}
                                        </p>
                                    </div>
                                    <div className="flex space-x-2 flex-shrink-0">
                                        <button
                                            type="button"
                                            onClick={() => handleChecklistChange(uniqueId, 'status', 'OK')}
                                            className={`px-3 py-1 text-sm font-medium rounded-full transition ${currentStatus.status === 'OK' ? 'bg-green-600 text-white shadow-md' : 'bg-green-100 text-green-700 hover:bg-green-200'}`}
                                        >
                                            <span className='hidden sm:inline'>Mark </span>OK
                                        </button>
                                        <button
                                            type="button"
                                            onClick={() => handleChecklistChange(uniqueId, 'status', 'ISSUE')}
                                            className={`px-3 py-1 text-sm font-medium rounded-full transition ${currentStatus.status === 'ISSUE' ? 'bg-red-600 text-white shadow-md' : 'bg-red-100 text-red-700 hover:bg-red-200'}`}
                                        >
                                            <span className='hidden sm:inline'>Mark </span>Issue
                                        </button>
                                    </div>
                                </div>
                                
                                {isIssue && (
                                    <textarea
                                        value={currentStatus.notes}
                                        onChange={(e) => handleChecklistChange(uniqueId, 'notes', e.target.value)}
                                        placeholder="REQUIRED: Describe the issue in detail for repair submission (e.g., 'Squeak in hallway floor near linen closet')."
                                        rows="2"
                                        className="mt-2 w-full p-3 border border-red-300 rounded-lg focus:ring-red-500 focus:border-red-500 text-gray-800"
                                    />
                                )}
                            </div>
                        );
                    })}
                </div>
            ))}
        </div>
    );

    // --- REPORT VIEW COMPONENT ---

    const ReportView = () => (
        <div className="space-y-6">
            <h2 className="text-2xl font-bold text-gray-800 border-b pb-2">Final Report Overview ({issuesList.length} Actionable Issues)</h2>
            <div className="p-4 bg-yellow-50 border border-yellow-200 rounded-xl text-yellow-800 text-sm">
                <p className="font-semibold mb-1">Status:</p>
                <p>You have identified **{issuesList.length} actionable issues** with detailed descriptions.</p>
                <p>Click **Submit Warranty Request** below to officially send this report to **warranty@peakmhc.com**.</p>
                <p className="mt-2 text-sm text-gray-600">
                    Submission Date: <span className="font-semibold text-gray-800">{submissionDate}</span>
                </p>
            </div>
            
            {/* Submission Button */}
            <button
                onClick={handleEmailSubmit}
                disabled={isSubmitting || issuesList.length === 0}
                className="w-full py-3 px-4 bg-teal-600 hover:bg-teal-700 rounded-full text-white font-bold text-lg transition duration-150 ease-in-out shadow-lg disabled:opacity-50"
            >
                {isSubmitting ? 'Submitting...' : `Submit Warranty Request (${issuesList.length} Issues)`}
            </button>
            <button
                onClick={() => setView('checklist')}
                className="w-full py-2 px-4 bg-gray-200 hover:bg-gray-300 rounded-full text-gray-800 font-semibold transition duration-150 ease-in-out"
            >
                ← Edit Checklist
            </button>
            
            {/* Submission Message */}
            {message && (
                <div className={`p-3 text-center rounded-lg font-medium ${message.startsWith('✅') ? 'bg-green-100 text-green-700' : message.startsWith('⏳') ? 'bg-blue-100 text-blue-700' : 'bg-red-100 text-red-700'}`}>
                    {message}
                </div>
            )}

            {/* Preview Area */}
            <div className="mt-4 p-4 bg-gray-50 border border-gray-200 rounded-xl">
                <h3 className="text-lg font-semibold text-gray-700 mb-2">Detailed Report Preview</h3>
                <textarea
                    value={finalReportText}
                    rows={10}
                    readOnly
                    className="w-full p-2 border border-gray-300 rounded-lg font-mono text-sm resize-none bg-white"
                    placeholder="No issues with detailed notes available for report."
                />
            </div>
        </div>
    );

    return (
        <div className="min-h-screen bg-gray-100 p-4 sm:p-8">
            <div className="max-w-4xl mx-auto">
                <header className="text-center mb-8">
                    <h1 className="text-4xl font-extrabold text-gray-900">
                        30-Day Move-In Warranty Checklist
                    </h1>
                    <p className="text-lg text-gray-600 mt-2">
                        For New Manufactured Home Owners
                    </p>
                </header>

                <div className="bg-white p-6 sm:p-8 rounded-3xl shadow-2xl border border-gray-200">
                    
                    {view === 'checklist' && <ChecklistView />}
                    {view === 'report' && <ReportView />}
                    
                    <div className="mt-8 pt-4 border-t">
                         <button
                            onClick={() => setView(view === 'checklist' ? 'report' : 'checklist')}
                            className="w-full py-3 px-4 bg-blue-600 hover:bg-blue-700 rounded-full text-white font-bold text-lg transition duration-150 ease-in-out shadow-lg"
                        >
                            {view === 'checklist' ? 'Review & Submit Report' : 'Back to Checklist'}
                        </button>
                    </div>
                </div>
            </div>
        </div>
    );
};

export default App;
