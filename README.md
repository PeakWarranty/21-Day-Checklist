<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>30-Day Manufactured Home Warranty Checklist</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        /* Custom styling for status cards */
        .card-UNCHECKED { border-color: #e5e7eb; background-color: #ffffff; }
        .card-OK { border-color: #6ee7b7; background-color: #f0fdfa; }
        .card-ISSUE { border-color: #fca5a5; background-color: #fef2f2; }
    </style>
</head>
<body class="bg-gray-100 p-4 sm:p-8">
    <div class="max-w-4xl mx-auto">
        <header class="text-center mb-8">
            <h1 class="text-4xl font-extrabold text-gray-900">
                30-Day Move-In Warranty Checklist
            </h1>
            <p class="text-lg text-gray-600 mt-2">
                For New Manufactured Home Owners
            </p>
        </header>

        <div class="bg-white p-6 sm:p-8 rounded-3xl shadow-2xl border border-gray-200" id="main-content">
            <form id="warranty-form" class="space-y-6">
                <!-- Homeowner Information -->
                <div class="bg-blue-50 border border-blue-200 p-4 rounded-xl space-y-3">
                    <h2 class="text-xl font-bold text-blue-700">Homeowner Information (Required)</h2>
                    <input type="text" id="homeownerName" name="homeownerName" placeholder="Homeowner Name *" class="w-full p-2 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500" required>
                    
                    <select id="community" name="community" class="w-full p-2 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500" required>
                        <option value="" disabled selected>Select Community *</option>
                        <option value="Rancho Serenidad">Rancho Serenidad</option>
                        <option value="Villas De Mariposa">Villas De Mariposa</option>
                        <option value="Brazos Pointe">Brazos Pointe</option>
                        <option value="Solena">Solena</option>
                        <option value="Other">Other</option>
                    </select>
                    
                    <div id="otherCommunityDiv" class="hidden">
                         <input type="text" id="otherCommunity" name="otherCommunity" placeholder="Specify Other Community Name *" class="w-full p-2 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500">
                    </div>
                    
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                        <input type="text" id="lotNumber" name="lotNumber" placeholder="Lot Number *" class="w-full p-2 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500" required>
                        <input type="text" id="serialNumber" name="serialNumber" placeholder="Home Serial Number" class="w-full p-2 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500">
                    </div>
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                        <input type="tel" id="contactPhone" name="contactPhone" placeholder="Contact Phone Number" class="w-full p-2 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500">
                        <input type="email" id="email" name="email" placeholder="Email Address *" class="w-full p-2 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500" required>
                    </div>
                </div>

                <!-- Checklist Container -->
                <div id="checklist-container" class="space-y-6">
                    <!-- Dynamic sections will be rendered here -->
                </div>
            </form>

            <div class="mt-8 pt-4 border-t">
                 <button id="review-button" type="button" class="w-full py-3 px-4 bg-blue-600 hover:bg-blue-700 rounded-full text-white font-bold text-lg transition duration-150 ease-in-out shadow-lg">
                    Review & Submit Report
                </button>
            </div>
        </div>

        <!-- Modal for Review and Submission -->
        <div id="review-modal" class="fixed inset-0 bg-gray-900 bg-opacity-75 z-50 flex items-center justify-center p-4 hidden">
            <div class="bg-white p-6 sm:p-8 rounded-xl shadow-2xl w-full max-w-2xl transform transition-all overflow-y-auto max-h-full">
                <h2 class="text-2xl font-bold text-gray-800 mb-4">Final Submission Report</h2>
                <div id="modal-content" class="space-y-4">
                    <div class="p-4 bg-yellow-50 border border-yellow-200 rounded-lg text-yellow-800 text-sm">
                        <p id="issue-summary" class="font-semibold mb-1">Checking issues...</p>
                        <p id="submission-date"></p>
                    </div>
                    
                    <h3 class="text-lg font-semibold text-gray-700">Detailed Report Preview</h3>
                    <textarea id="report-preview" rows="10" readonly class="w-full p-2 border border-gray-300 rounded-lg font-mono text-sm resize-none bg-gray-50"></textarea>
                </div>

                <div id="submission-message" class="mt-4 p-3 text-center rounded-lg font-medium hidden"></div>

                <div class="mt-6 flex space-x-4">
                    <button id="submit-button" type="button" class="flex-1 py-3 px-4 bg-teal-600 hover:bg-teal-700 rounded-full text-white font-bold transition duration-150 ease-in-out shadow-lg disabled:opacity-50">
                        Submit Warranty Request
                    </button>
                    <button id="close-modal" type="button" class="flex-1 py-3 px-4 bg-gray-200 hover:bg-gray-300 rounded-full text-gray-800 font-semibold">
                        Back to Checklist
                    </button>
                </div>
            </div>
        </div>
    </div>

    <script>
        // --- CONFIGURATION DATA ---
        // 🚨 IMPORTANT: This URL is the Form Response URL for reliable Google Form submission.
        const GOOGLE_FORM_ACTION_URL = 'https://docs.google.com/forms/d/e/1FAIpQLSf3gsCzV8c7RfnWdSrLb3-0YoHLxay0GNCbxaF3Rwit8yY8mg/formResponse';

        // 🚨 CRITICAL: These are the ENTRY IDs for the 8 fields in your Google Form (in order).
        const FIELD_ENTRY_MAP = {
            homeownerName: 'entry.1740954541',
            community: 'entry.159491752',
            lotNumber: 'entry.1691238930',
            serialNumber: 'entry.1018512133',
            contactPhone: 'entry.1345914614',
            email: 'entry.999665671',
            submissionDate: 'entry.1082539054',
            reportedIssues: 'entry.1687051280'
        };

        const CHECKLIST_SECTIONS = [
            // [Section 1]
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
            // [Section 2]
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
            // [Section 3]
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

        let checklistState = {};

        // --- Utility Functions ---

        /**
         * Generates a unique ID for a checklist item.
         */
        const generateId = (item, location) => 
            `${item.replace(/\s/g, '_')}_${location.replace(/\s/g, '_')}`.toLowerCase();

        /**
         * Initializes the checklist state object.
         */
        const initializeChecklistState = () => {
            CHECKLIST_SECTIONS.forEach(section => {
                section.items.forEach(item => {
                    const id = generateId(item.item, item.location);
                    checklistState[id] = {
                        status: 'UNCHECKED', // OK, ISSUE, UNCHECKED
                        notes: '',
                        item: item.item,
                        location: item.location,
                        description: item.description // Keep original description for reference
                    };
                });
            });
        };

        /**
         * Gets the current submission date formatted as a string.
         * @returns {string} Formatted date string.
         */
        const getSubmissionDate = () => {
            return new Date().toLocaleDateString('en-US', {
                year: 'numeric',
                month: 'long',
                day: 'numeric'
            });
        };

        // --- Rendering and Event Handlers ---

        /**
         * Renders the entire checklist into the DOM.
         */
        const renderChecklist = () => {
            const container = document.getElementById('checklist-container');
            container.innerHTML = ''; // Clear previous content

            CHECKLIST_SECTIONS.forEach((section, sectionIndex) => {
                const sectionDiv = document.createElement('div');
                sectionDiv.className = 'space-y-3 p-4 bg-white rounded-xl shadow-md border border-gray-100';
                sectionDiv.innerHTML = `<h2 class="text-2xl font-extrabold text-gray-800 border-b pb-2 mb-4">${section.title}</h2>`;

                section.items.forEach((item, itemIndex) => {
                    const id = generateId(item.item, item.location);
                    const state = checklistState[id];
                    const isIssue = state.status === 'ISSUE';

                    const cardClasses = `p-4 rounded-lg border-2 transition-colors duration-200 card-${state.status}`;

                    const itemHtml = `
                        <div id="item-${id}" class="${cardClasses}">
                            <div class="flex flex-col sm:flex-row justify-between items-start space-y-2 sm:space-y-0 sm:space-x-4 mb-2">
                                <div class="flex-1">
                                    <p class="font-semibold text-lg text-gray-900">${item.item}</p>
                                    <p class="text-sm text-gray-500">
                                        <span class="font-medium text-gray-600">Location:</span> ${item.location}
                                        <span class="mx-2 text-gray-300 hidden sm:inline">|</span>
                                        <span class="font-medium text-gray-600">Check:</span> ${item.description}
                                    </p>
                                </div>
                                <div class="flex space-x-2 flex-shrink-0 pt-1">
                                    <button data-id="${id}" data-status="OK" class="status-btn px-3 py-1 text-sm font-medium rounded-full transition ${state.status === 'OK' ? 'bg-green-600 text-white shadow-md' : 'bg-green-100 text-green-700 hover:bg-green-200'}">
                                        <span class="hidden sm:inline">Mark </span>OK
                                    </button>
                                    <button data-id="${id}" data-status="ISSUE" class="status-btn px-3 py-1 text-sm font-medium rounded-full transition ${state.status === 'ISSUE' ? 'bg-red-600 text-white shadow-md' : 'bg-red-100 text-red-700 hover:bg-red-200'}">
                                        <span class="hidden sm:inline">Mark </span>Issue
                                    </button>
                                    <button data-id="${id}" data-status="UNCHECKED" class="status-btn px-3 py-1 text-sm font-medium rounded-full transition ${state.status === 'UNCHECKED' ? 'bg-gray-600 text-white shadow-md' : 'bg-gray-100 text-gray-700 hover:bg-gray-200'}">
                                        Clear
                                    </button>
                                </div>
                            </div>
                            
                            ${isIssue ? `
                                <textarea
                                    data-id="${id}"
                                    class="notes-input mt-2 w-full p-3 border border-red-300 rounded-lg focus:ring-red-500 focus:border-red-500 text-gray-800"
                                    placeholder="REQUIRED: Describe the issue in detail for repair submission (e.g., 'Squeak in hallway floor near linen closet')."
                                    rows="2"
                                >${state.notes}</textarea>
                            ` : ''}
                        </div>
                    `;
                    sectionDiv.insertAdjacentHTML('beforeend', itemHtml);
                });
                container.appendChild(sectionDiv);
            });

            // Re-attach event listeners after rendering
            document.querySelectorAll('.status-btn').forEach(button => {
                button.addEventListener('click', handleStatusChange);
            });

            document.querySelectorAll('.notes-input').forEach(input => {
                input.addEventListener('input', handleNotesChange);
            });
        };

        /**
         * Updates the status of a checklist item and re-renders if necessary.
         * @param {Event} e 
         */
        const handleStatusChange = (e) => {
            const id = e.target.closest('.status-btn').dataset.id;
            const newStatus = e.target.closest('.status-btn').dataset.status;

            if (checklistState[id].status !== newStatus) {
                checklistState[id].status = newStatus;
                // Clear notes if switching away from ISSUE
                if (newStatus !== 'ISSUE') {
                    checklistState[id].notes = '';
                }
                renderChecklist(); // Re-render the checklist to show notes/color changes
            }
        };

        /**
         * Updates the notes for a checklist item.
         * @param {Event} e 
         */
        const handleNotesChange = (e) => {
            const id = e.target.dataset.id;
            checklistState[id].notes = e.target.value;
        };
        
        /**
         * Toggles the visibility and required status of the 'Other Community' input.
         */
        const handleCommunityChange = () => {
            const communitySelect = document.getElementById('community');
            const otherDiv = document.getElementById('otherCommunityDiv');
            const otherInput = document.getElementById('otherCommunity');

            if (communitySelect.value === 'Other') {
                otherDiv.classList.remove('hidden');
                otherInput.required = true;
            } else {
                otherDiv.classList.add('hidden');
                otherInput.required = false;
                otherInput.value = ''; // Clear value when hidden
            }
        };

        // --- Submission and Report Logic ---

        /**
         * Validates the required homeowner info fields.
         * @param {object} formData - The compiled data.
         * @returns {string|null} Error message or null if valid.
         */
        const validateHomeownerInfo = (formData) => {
            if (!formData.homeownerName.trim()) return "Homeowner Name is required.";
            if (!formData.email.trim()) return "Email Address is required.";
            if (!formData.lotNumber.trim()) return "Lot Number is required.";
            if (!formData.community.trim()) return "Community selection is required.";
            if (formData.community === 'Other' && !formData.otherCommunity.trim()) return "Please specify the Other Community Name.";
            return null;
        };
        
        /**
         * Compiles all submission data and the formatted report.
         * @returns {object} Contains form data, issues list, and report text.
         */
        const compileSubmissionData = () => {
            const form = document.getElementById('warranty-form');
            const formData = {
                homeownerName: form.elements.homeownerName.value.trim(),
                community: form.elements.community.value,
                otherCommunity: form.elements.otherCommunity ? form.elements.otherCommunity.value.trim() : '',
                lotNumber: form.elements.lotNumber.value.trim(),
                serialNumber: form.elements.serialNumber.value.trim(),
                contactPhone: form.elements.contactPhone.value.trim(),
                email: form.elements.email.value.trim(),
            };
            
            // Determine final community value
            const finalCommunity = formData.community === 'Other' ? formData.otherCommunity : formData.community;

            const submissionDate = getSubmissionDate();
            
            const issuesList = Object.values(checklistState).filter(item => 
                item.status === 'ISSUE' && item.notes.trim() !== ''
            );

            const emptyNotesCount = Object.values(checklistState).filter(item => 
                item.status === 'ISSUE' && item.notes.trim() === ''
            ).length;

            const issuesReport = issuesList.map((item, index) => {
                const locationDetail = item.location ? ` (Location: ${item.location})` : '';
                // Use markdown formatting in the report string for better readability in the submission form
                return `${index + 1}. ${item.item}${locationDetail}\nDescription: ${item.notes}\n---`;
            }).join('\n');

            const finalReportText = `*** Homeowner Information ***\n` +
                                   `Name: ${formData.homeownerName}\n` +
                                   `Community: ${finalCommunity}\n` +
                                   `Lot #: ${formData.lotNumber}\n` +
                                   `Serial #: ${formData.serialNumber}\n` +
                                   `Phone: ${formData.contactPhone}\n` +
                                   `Email: ${formData.email}\n` +
                                   `Date: ${submissionDate}\n\n` +
                                   `*** Reported Issues (${issuesList.length} Total) ***\n` +
                                   (issuesReport || 'No actionable issues with description were reported.');

            return {
                formData,
                issuesList,
                emptyNotesCount,
                submissionDate,
                finalCommunity,
                finalReportText
            };
        };

        /**
         * Displays the review modal and sets up the report.
         */
        const openReviewModal = () => {
            const { formData, issuesList, emptyNotesCount, finalReportText, submissionDate } = compileSubmissionData();
            const modal = document.getElementById('review-modal');
            const messageDiv = document.getElementById('submission-message');
            const submitBtn = document.getElementById('submit-button');
            const issueSummary = document.getElementById('issue-summary');

            // 1. Validate Homeowner Info
            const infoError = validateHomeownerInfo(formData);
            if (infoError) {
                // Show modal to display error
                setMessage(messageDiv, `❌ Error: ${infoError}`, 'bg-red-100 text-red-700');
                submitBtn.disabled = true;
                modal.classList.remove('hidden');
                document.getElementById('report-preview').value = "";
                return;
            }

            // 2. Validate Checklist Notes
            if (issuesList.length === 0 && emptyNotesCount === 0) {
                issueSummary.innerHTML = 'All checklist items are marked OK or UNCHECKED. Report will show no issues.';
                submitBtn.disabled = false; 
            } else if (emptyNotesCount > 0) {
                setMessage(messageDiv, `⚠️ Submission blocked: ${emptyNotesCount} issue(s) marked but missing descriptions. Please return to the checklist and add notes.`, 'bg-red-100 text-red-700');
                submitBtn.disabled = true;
                modal.classList.remove('hidden');
                return;
            } else {
                issueSummary.innerHTML = `You have identified **${issuesList.length} actionable issues** with detailed descriptions.`;
                submitBtn.disabled = false;
            }
            
            // Set date and report preview
            document.getElementById('submission-date').textContent = `Date of Submission: ${submissionDate}`;
            document.getElementById('report-preview').value = finalReportText;
            
            messageDiv.classList.add('hidden'); // Clear previous messages
            submitBtn.textContent = `Submit Warranty Request (${issuesList.length} Issues)`;
            
            modal.classList.remove('hidden');
        };

        /**
         * Sets the submission status message in the modal.
         */
        const setMessage = (element, text, classes) => {
            element.classList.remove('hidden', 'bg-green-100', 'text-green-700', 'bg-red-100', 'text-red-700', 'bg-blue-100', 'text-blue-700', 'bg-yellow-100', 'text-yellow-700');
            element.classList.add(classes);
            element.innerHTML = text;
        };

        /**
         * Handles the final submission of data to the Google Form URL.
         */
        const handleSubmission = () => {
            const { formData, finalReportText, submissionDate, finalCommunity } = compileSubmissionData();
            const messageDiv = document.getElementById('submission-message');
            const submitBtn = document.getElementById('submit-button');
            
            // 1. Set UI to Sending
            submitBtn.disabled = true;
            submitBtn.textContent = 'Redirecting...';
            setMessage(messageDiv, '⏳ Submitting request...', 'bg-blue-100 text-blue-700');

            // 2. Construct the URL query string using the Entry IDs
            const params = new URLSearchParams();
            params.append(FIELD_ENTRY_MAP.homeownerName, formData.homeownerName);
            params.append(FIELD_ENTRY_MAP.community, finalCommunity);
            params.append(FIELD_ENTRY_MAP.lotNumber, formData.lotNumber);
            params.append(FIELD_ENTRY_MAP.serialNumber, formData.serialNumber);
            params.append(FIELD_ENTRY_MAP.contactPhone, formData.contactPhone);
            params.append(FIELD_ENTRY_MAP.email, formData.email);
            params.append(FIELD_ENTRY_MAP.submissionDate, submissionDate);
            params.append(FIELD_ENTRY_MAP.reportedIssues, finalReportText);
            
            // 3. Construct the full submission URL (using GET/FormResponse)
            const submissionUrl = `${GOOGLE_FORM_ACTION_URL}?${params.toString()}`;
            
            // 4. Close the modal and redirect the user's browser (most reliable method)
            document.getElementById('review-modal').classList.add('hidden');
            window.location.href = submissionUrl;

            // Since the page redirects, the following code is primarily for internal handling if the redirect fails.
            setMessage(messageDiv, '✅ Redirecting to Google Form...', 'bg-green-100 text-green-700');
        };
        
        /**
         * Initializes the app on window load.
         */
        const initApp = () => {
             initializeChecklistState();
             renderChecklist();
             
             // Event Listeners
             document.getElementById('community').addEventListener('change', handleCommunityChange);
             document.getElementById('review-button').addEventListener('click', openReviewModal);
             
             // Modal Listeners
             document.getElementById('submit-button').addEventListener('click', handleSubmission);
             document.getElementById('close-modal').addEventListener('click', () => {
                 document.getElementById('review-modal').classList.add('hidden');
             });
        }

        // --- Initialization ---
        window.onload = initApp;
    </script>
</body>
</html>
