<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>30 Day Move-in Warranty Checklist</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script type="text/javascript" src="https://cdn.jsdelivr.net/npm/@emailjs/browser@4/dist/email.min.js"></script>
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        /* Styles for the checklist buttons and status */
        .status-ok { background-color: #d1fae5; color: #065f46; border-color: #10b981; }
        .status-issue { background-color: #fee2e2; color: #991b1b; border-color: #f87171; }
        
        /* New button colors for unselected state */
        .btn-ok-active { background-color: #10b981 !important; color: white !important; }
        .btn-issue-active { background-color: #ef4444 !important; color: white !important; }
    </style>
</head>
<body class="bg-gray-100 flex items-center justify-center min-h-screen p-4">
    <div class="bg-white p-8 rounded-2xl shadow-xl w-full max-w-2xl border border-gray-200">
        <h1 class="text-3xl font-bold text-center text-gray-800 mb-2">30 Day Move-in Warranty Checklist</h1>
        <p class="text-center text-gray-500 mb-6">Fill out the form below to submit a request.
            <br>
        </p>
        
        <form id="parts-form" class="space-y-4">
            
            <div class="space-y-2">
                <h2 class="text-lg font-semibold text-gray-800">Homeowner & Contact Details</h2>
            </div>

            <div class="space-y-2">
                <label for="homeowner-name" class="block text-sm font-medium text-gray-700">Homeowner's Name</label>
                <input type="text" id="homeowner-name" name="homeowner-name" required class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500 transition duration-150 ease-in-out">
            </div>

            <div class="space-y-2">
                <label for="contact-phone" class="block text-sm font-medium text-gray-700">Contact Phone Number</label>
                <input type="tel" id="contact-phone" name="contact-phone" required class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500 transition duration-150 ease-in-out">
            </div>

            <div class="space-y-2">
                <label for="contact-email" class="block text-sm font-medium text-gray-700">Email Address</label>
                <input type="email" id="contact-email" name="contact-email" required class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500 transition duration-150 ease-in-out">
            </div>
            
            <div class="space-y-2">
                <label for="lot-number" class="block text-sm font-medium text-gray-700">Lot Number</label>
                <input type="text" id="lot-number" name="lot-number" required class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500 transition duration-150 ease-in-out">
            </div>
            
            <div class="space-y-2">
                <label for="serial-number" class="block text-sm font-medium text-gray-700">Serial Number</label>
                <input type="text" id="serial-number" name="serial-number" class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500 transition duration-150 ease-in-out">
                <p class="text-xs text-gray-500 italic mt-1">This number can be found on the **information** sheet under your kitchen sink.</p>
            </div>

            <div class="space-y-2">
                <label for="home-manufacturer" class="block text-sm font-medium text-gray-700">Home Manufacturer</label>
                <select id="home-manufacturer" name="home-manufacturer" required class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500 transition duration-150 ease-in-out">
                    <option value="" disabled selected>Select a manufacturer</option>
                    <option value="CAVCO/Fleetwood">CAVCO/Fleetwood</option>
                    <option value="Champion Homes">Champion Homes</option>
                    <option value="Clayton Athens">Clayton Athens</option>
                    <option value="Clayton Bonham">Clayton Bonham</option>
                    <option value="Clayton Southern Energy">Clayton Southern Energy</option>
                    <option value="Clayton Sulphur Springs">Clayton Sulphur Springs</option>
                    <option value="Clayton Waco1">Clayton Waco1</option>
                    <option value="Jessup">Jessup</option>
                    <option value="New Vision">New Vision</option>
                    <option value="Oak Creek">Oak Creek</option>
                    <option value="RGN">RGN</option>
                </select>
            </div>
            
            <div class="space-y-2 pt-4 border-t border-gray-200">
                <label for="community-select" class="block text-sm font-medium text-gray-700">Community</label>
                <select id="community-select" name="community" required class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500 transition duration-150 ease-in-out">
                    <option value="" disabled selected>Select your community</option>
                    <option value="Rancho Serenidad">Rancho Serenidad</option>
                    <option value="Villas De Mariposa">Villas De Mariposa</option>
                    <option value="Brazos Point">Brazos Point</option>
                    <option value="Solena">Solena</option>
                    <option value="Other">Other (Please specify)</option>
                </select>
            </div>
            
            <div id="other-community-div" class="space-y-2 hidden">
                <label for="other-community" class="block text-sm font-medium text-gray-700">Specify Community</label>
                <input type="text" id="other-community" name="home-address-unused" class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500 transition duration-150 ease-in-out">
            </div>

            <div id="checklist-container" class="space-y-4 mt-6 pt-4 border-t border-gray-200">
                <h2 class="text-xl font-bold text-gray-800">30-Day Warranty Checklist Items</h2>

                <div id="item-batten-strips" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Batten Strips/Trim">Batten Strips/Trim</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Throughout">Throughout</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Loose, missing, misaligned batten strips/trim">
                                Check: Loose, missing, misaligned batten strips/trim
                            </div>
                            <input type="hidden" name="issue-batten-strips" data-item-input data-item-index="1" value=""> 
                        </div>

                        <div class="flex space-x-2 flex-shrink-0 w-full justify-end">
                            <button type="button" data-action="ok" data-item="batten-strips" class="btn-ok w-20 py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">
                                OK
                            </button>
                            <button type="button" data-action="issue" data-item="batten-strips" class="btn-issue w-20 py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">
                                Issue
                            </button>
                            <button type="button" data-action="clear" data-item="batten-strips" class="w-16 py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">
                                Clear
                            </button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden">
                        <label for="comment-batten-strips" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-batten-strips" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                    </div>
                </div>
                </div>
            <div class="mt-6">
                <button type="submit" id="submit-btn" class="w-full py-3 px-4 bg-blue-600 hover:bg-blue-700 rounded-full text-white font-bold text-lg transition duration-150 ease-in-out shadow-lg">
                    Submit Request
                </button>
            </div>
        </form>

        <div id="status-message" class="mt-6 p-4 rounded-lg text-center hidden"></div>
    </div>

    <script>
        (function() {
            // !!! IMPORTANT: REPLACE THESE WITH YOUR ACTUAL EmailJS CREDENTIALS !!!
            const USER_ID = 'bSgwpRuVeEky48mPe';  
            const SERVICE_ID = 'service_7lbsq24';
            const TEMPLATE_ID = 'template_dvr6oem';
            const SECONDARY_EMAIL = 'warranty@peakmhc.com'; 

            const form = document.getElementById('parts-form');
            const communitySelect = document.getElementById('community-select');
            const otherCommunityDiv = document.getElementById('other-community-div');
            const otherCommunityInput = document.getElementById('other-community');
            const statusDiv = document.getElementById('status-message');
            const submitBtn = document.getElementById('submit-btn');
            const formMainContent = document.querySelector('form');
            const checklistContainer = document.getElementById('checklist-container');
            
            // Field references
            const homeownerNameInput = document.getElementById('homeowner-name');
            const contactPhoneInput = document.getElementById('contact-phone');
            const contactEmailInput = document.getElementById('contact-email');


            // --- CHECKLIST LOGIC ---
            checklistContainer.addEventListener('click', function(event) {
                const button = event.target.closest('button');
                if (!button) return;

                const itemDiv = button.closest('.warranty-item');
                const action = button.dataset.action;
                const itemId = button.dataset.item;
                const issueInput = itemDiv.querySelector('[data-item-input]');
                const commentArea = itemDiv.querySelector('.comment-area');
                const commentInput = commentArea.querySelector('textarea');
                
                // Remove all active classes from all buttons in this item
                itemDiv.querySelectorAll('button[data-action]').forEach(btn => {
                    btn.classList.remove('btn-ok-active', 'btn-issue-active');
                });
                // Remove visual status classes
                itemDiv.classList.remove('status-ok', 'status-issue');


                if (action === 'ok') {
                    button.classList.add('btn-ok-active');
                    itemDiv.classList.add('status-ok');
                    issueInput.value = 'OK'; 
                    commentArea.classList.add('hidden');
                    commentInput.value = ''; // Clear comment if OK
                } else if (action === 'issue') {
                    button.classList.add('btn-issue-active');
                    itemDiv.classList.add('status-issue');
                    
                    // Set the primary issue value
                    const itemName = itemDiv.querySelector('[data-item-name]').textContent.trim();
                    const itemLocation = itemDiv.querySelector('[data-item-location]').textContent.trim();
                    const itemCheck = itemDiv.querySelector('[data-item-check]').textContent.replace('Check: ', '').trim();

                    issueInput.value = `ISSUE: ${itemName} (Location: ${itemLocation}). Check: ${itemCheck}`;
                    
                    commentArea.classList.remove('hidden'); // Show comment box

                } else if (action === 'clear') {
                    issueInput.value = ''; 
                    commentInput.value = '';
                    commentArea.classList.add('hidden'); // Hide comment box
                }
            });
            // --- END CHECKLIST LOGIC ---

            function resetForm() {
                form.reset();
                statusDiv.classList.add('hidden');
                statusDiv.innerHTML = '';
                
                // Reset conditional fields
                otherCommunityDiv.classList.add('hidden');
                otherCommunityInput.required = false;
                otherCommunityInput.name = 'home-address-unused';
                otherCommunityInput.value = '';

                // Reset checklist items visually and internally
                document.querySelectorAll('.warranty-item').forEach(item => {
                    item.classList.remove('status-ok', 'status-issue');
                    item.querySelector('[data-item-input]').value = '';
                    item.querySelector('.comment-area').classList.add('hidden');
                    item.querySelector('.comment-area textarea').value = '';
                    item.querySelectorAll('button[data-action]').forEach(btn => {
                        btn.classList.remove('btn-ok-active', 'btn-issue-active');
                    });
                });
                
                formMainContent.style.display = 'block';
            }
            
            // Event listener for the community select field
            communitySelect.addEventListener('change', (event) => {
                if (event.target.value === 'Other') {
                    otherCommunityDiv.classList.remove('hidden');
                    otherCommunityInput.required = true;
                    otherCommunityInput.name = 'home-address'; 
                } else {
                    otherCommunityDiv.classList.add('hidden');
                    otherCommunityInput.required = false;
                    otherCommunityInput.name = 'home-address-unused'; 
                    otherCommunityInput.value = ''; 
                }
            });

            emailjs.init(USER_ID);

            document.getElementById('parts-form').addEventListener('submit', function(event) {
                event.preventDefault();
                
                // --- NEW: COMPILE CHECKLIST ISSUES ---
                let issuesString = '';
                let hasIssue = false;
                
                document.querySelectorAll('.warranty-item').forEach((item, index) => {
                    const issueInput = item.querySelector('[data-item-input]');
                    const commentInput = item.querySelector('.comment-area textarea');
                    const value = issueInput.value.trim();
                    
                    if (value && value !== 'OK') {
                        hasIssue = true;
                        
                        // Start the issue string with the item's main description
                        let itemReport = `Item #${index + 1}: ${value}`;
                        
                        // Append comment if present
                        if (commentInput && commentInput.value.trim().length > 0) {
                            itemReport += `\n    Comment: ${commentInput.value.trim()}`;
                        }
                        issuesString += itemReport + '\n\n';
                    }
                });

                if (!hasIssue) {
                    statusDiv.classList.remove('hidden', 'bg-blue-100', 'text-blue-800', 'bg-red-100', 'text-red-800');
                    statusDiv.classList.add('bg-red-100', 'text-red-800');
                    statusDiv.innerHTML = '<strong>Submission Error:</strong> Please mark at least one item as an issue, or ensure all required contact fields are filled.';
                    submitBtn.disabled = false;
                    return;
                }
                
                // Show sending status
                statusDiv.classList.remove('hidden', 'bg-green-100', 'text-green-800', 'bg-red-100', 'text-red-800');
                statusDiv.classList.add('bg-blue-100', 'text-blue-800');
                statusDiv.innerHTML = 'Sending request... Please wait.';
                
                submitBtn.disabled = true;
                
                // Determine the final community value
                const finalCommunity = communitySelect.value === 'Other'  
                    ? otherCommunityInput.value 
                    : communitySelect.value;

                const emailParams = {
                    'user-name': 'Homeowner', 
                    'homeowner-name': homeownerNameInput.value,
                    'contact-phone': contactPhoneInput.value,
                    'contact-email': contactEmailInput.value,
                    'urgency': 'Medium', 
                    'home-address': finalCommunity,
                    'lot-number': form.elements['lot-number'].value,
                    'serial-number': form.elements['serial-number'].value,
                    'home-manufacturer': form.elements['home-manufacturer'].value,
                    'part-description': issuesString, // The compiled checklist with comments
                    'secondary_email': SECONDARY_EMAIL
                };
                
                // EMAILJS PATH REMAINS INTACT
                emailjs.send(SERVICE_ID, TEMPLATE_ID, emailParams)
                    .then(function() {
                        statusDiv.classList.remove('bg-blue-100', 'text-blue-800');
                        statusDiv.classList.add('bg-green-100', 'text-green-800');
                        statusDiv.innerHTML = '<strong>Success!</strong> Your request has been sent. <br><br> <button id="continue-btn" class="py-2 px-4 mt-2 bg-blue-600 hover:bg-blue-700 rounded-full text-white font-bold transition duration-150 ease-in-out">Submit Another Request</button>';
                        
                        formMainContent.style.display = 'none'; 
                        document.getElementById('continue-btn').addEventListener('click', resetForm);
                    }, function(error) {
                        statusDiv.classList.remove('bg-blue-100', 'text-blue-800');
                        statusDiv.classList.add('bg-red-100', 'text-red-800');
                        statusDiv.innerHTML = `<strong>Failed!</strong> There was an error sending your request. Please try again.`;
                        console.error('EmailJS Error:', error);
                    })
                    .finally(() => {
                        submitBtn.disabled = false;
                    });
            });
        })();
    </script>
</body>
</html>
