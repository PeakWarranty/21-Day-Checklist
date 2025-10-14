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
                <label for="user-name" class="block text-sm font-medium text-gray-700">Person Requesting Service</label>
                <select id="user-name" name="user-name" required class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500 transition duration-150 ease-in-out">
                    <option value="" disabled selected>Select a person</option>
                    <option value="Brandon Hatfield">Brandon Hatfield</option>
                    <option value="Iesha Coatney">Iesha Coatney</option>
                    <option value="Jessica Baez">Jessica Baez</option>
                    <option value="Karen Green">Karen Green</option>
                    <option value="Leender Othan">Leender Othan</option>
                    <option value="Nicole Filburn">Nicole Filburn</option>
                    <option value="Shawn Thomas">Shawn Thomas</option>
                    <option value="Tom Roberson">Tom Roberson</option>
                    <option value="Tonya Johnson">Tonya Johnson</option>
                    <option value="Other">Other (Please specify)</option>
                </select>
            </div>
            
            <div id="other-user-div" class="space-y-2 hidden">
                <label for="other-user-name" class="block text-sm font-medium text-gray-700">Specify Requester's Name</label>
                <input type="text" id="other-user-name" name="other-user-name" class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500 transition duration-150 ease-in-out">
            </div>

            <div class="space-y-2">
                <label for="urgency" class="block text-sm font-medium text-gray-700">Urgency</label>
                <select id="urgency" name="urgency" required class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500 transition duration-150 ease-in-out">
                    <option value="" disabled selected>Select urgency</option>
                    <option value="Low">Low</option>
                    <option value="Medium">Medium</option>
                    <option value="High">High</option>
                    <option value="Emergency">Emergency</option>
                </select>
            </div>
            
            <div class="space-y-2">
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

            <div class="space-y-2">
                <label for="lot-number" class="block text-sm font-medium text-gray-700">Lot Number</label>
                <input type="text" id="lot-number" name="lot-number" required class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500 transition duration-150 ease-in-out">
            </div>
            <div class="space-y-2">
                <label for="serial-number" class="block text-sm font-medium text-gray-700">Serial Number</label>
                <input type="text" id="serial-number" name="serial-number" class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500 transition duration-150 ease-in-out">
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
            
            <div id="parts-container" class="space-y-6 mt-6">
            </div>
            
            <div class="flex space-x-4">
                <button type="button" id="add-part-btn" class="w-full py-2 px-4 bg-gray-200 hover:bg-gray-300 rounded-full text-gray-700 font-semibold text-sm transition duration-150 ease-in-out">
                    Add Additional Warranty Item
                </button>
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
            const userNameSelect = document.getElementById('user-name');
            const otherUserDiv = document.getElementById('other-user-div');
            const otherUserInput = document.getElementById('other-user-name');
            const communitySelect = document.getElementById('community-select');
            const otherCommunityDiv = document.getElementById('other-community-div');
            const otherCommunityInput = document.getElementById('other-community');
            const urgencySelect = document.getElementById('urgency');
            const statusDiv = document.getElementById('status-message');
            const submitBtn = document.getElementById('submit-btn');
            const partsContainer = document.getElementById('parts-container');
            const addPartBtn = document.getElementById('add-part-btn');
            const formMainContent = document.querySelector('form');

            let itemCounter = 0; // Renamed from partCounter to itemCounter for clarity

            const partLocations = [
                "Exterior", 
                "Primary Bedroom",
                "Primary Bathroom",
                "Bedroom #2",
                "Bedroom #3",
                "Bedroom #4",
                "Flex Space",
                "Hall",
                "Guest Bath",
                "Living Area",
                "Laundry Area",
                "Dining Area",
                "Kitchen",
                "Pantry"
            ];
            
            function updatePartEntryHeadings() {
                const services = partsContainer.querySelectorAll('.part-entry');
                itemCounter = services.length; // Sync the counter

                services.forEach((service, index) => {
                    const heading = service.querySelector('h3 span');
                    // Renamed "Service Requested" to "Warranty Item"
                    heading.textContent = index === 0 ? 'Warranty Item' : `Warranty Item #${index + 1}`; 
                    
                    // Update field names and IDs to match the new number
                    const newIndex = index + 1; 
                    service.querySelector('textarea').id = `part-description-${newIndex}`;
                    service.querySelector('textarea').name = `part-description-${newIndex}`;
                    service.querySelector('select').id = `part-location-${newIndex}`;
                    service.querySelector('select').name = `part-location-${newIndex}`;

                    // Show remove button for all parts after the first one
                    let removeBtn = service.querySelector('.remove-part-btn');
                    if (index > 0 && !removeBtn) {
                         const removeBtnHTML = '<button type="button" class="remove-part-btn text-red-500 hover:text-red-700 text-sm font-normal transition duration-150 ease-in-out">Remove</button>';
                         service.querySelector('h3').insertAdjacentHTML('beforeend', removeBtnHTML);
                         removeBtn = service.querySelector('.remove-part-btn');
                         removeBtn.addEventListener('click', () => {
                             partsContainer.removeChild(service);
                             updatePartEntryHeadings();
                            });
                    } else if (index === 0 && removeBtn) {
                        removeBtn.remove();
                    }
                });
            }

            function addPartEntry() {
                // Use itemCounter for naming/ID purposes
                itemCounter++; 
                const partDiv = document.createElement('div');
                partDiv.classList.add('part-entry', 'bg-gray-50', 'p-4', 'rounded-lg', 'border', 'border-gray-200', 'space-y-2');
                
                // Renamed "Service Requested" to "Warranty Item"
                partDiv.innerHTML = `
                    <h3 class="font-semibold text-gray-700 flex justify-between items-center">
                        <span>${itemCounter === 1 ? 'Warranty Item' : `Warranty Item #${itemCounter}`}</span>
                    </h3>
                    <div class="space-y-2">
                        <label for="part-description-${itemCounter}" class="block text-sm font-medium text-gray-700">Service Description</label>
                        <textarea id="part-description-${itemCounter}" name="part-description-${itemCounter}" rows="2" required class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500 transition duration-150 ease-in-out"></textarea>
                    </div>
                    <div class="space-y-2">
                        <label for="part-location-${itemCounter}" class="block text-sm font-medium text-gray-700">Location of Issue</label>
                        <select id="part-location-${itemCounter}" name="part-location-${itemCounter}" required class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500 transition duration-150 ease-in-out">
                            <option value="" disabled selected>Select location</option>
                            ${partLocations.map(location => `<option value="${location}">${location}</option>`).join('')}
                        </select>
                    </div>
                `;
                partsContainer.appendChild(partDiv);
                
                // Add remove button logic managed by updatePartEntryHeadings
                updatePartEntryHeadings(); 
            }

            function resetForm() {
                form.reset();
                partsContainer.innerHTML = '';
                itemCounter = 0; // Reset item counter
                addPartEntry();
                statusDiv.classList.add('hidden');
                statusDiv.innerHTML = '';
                
                // Reset conditional fields
                otherCommunityDiv.classList.add('hidden');
                otherCommunityInput.required = false;
                otherCommunityInput.name = 'home-address-unused';
                otherCommunityInput.value = '';

                otherUserDiv.classList.add('hidden');
                otherUserInput.required = false;
                otherUserInput.name = 'unused-user';
                otherUserInput.value = '';
                
                formMainContent.style.display = 'block';
            }

            addPartEntry();

            addPartBtn.addEventListener('click', addPartEntry);
            
            // Event listener for the user-name select field
            userNameSelect.addEventListener('change', (event) => {
                if (event.target.value === 'Other') {
                    otherUserDiv.classList.remove('hidden');
                    otherUserInput.required = true;
                    otherUserInput.name = 'user-name-other';
                } else {
                    otherUserDiv.classList.add('hidden');
                    otherUserInput.required = false;
                    otherUserInput.name = 'unused-user';
                    otherUserInput.value = ''; // Clear the input when switching back
                }
            });

            // Event listener for the community select field
            communitySelect.addEventListener('change', (event) => {
                if (event.target.value === 'Other') {
                    otherCommunityDiv.classList.remove('hidden');
                    otherCommunityInput.required = true;
                    otherCommunityInput.name = 'home-address'; // This name will be used by EmailJS
                } else {
                    otherCommunityDiv.classList.add('hidden');
                    otherCommunityInput.required = false;
                    otherCommunityInput.name = 'home-address-unused'; // Change name so EmailJS ignores it
                    otherCommunityInput.value = ''; // Clear the input when switching back
                }
            });

            emailjs.init(USER_ID);

            document.getElementById('parts-form').addEventListener('submit', function(event) {
                event.preventDefault();
                
                // Show sending status
                statusDiv.classList.remove('hidden', 'bg-green-100', 'text-green-800', 'bg-red-100', 'text-red-800');
                statusDiv.classList.add('bg-blue-100', 'text-blue-800');
                statusDiv.innerHTML = 'Sending request... Please wait.';
                
                submitBtn.disabled = true;
                
                // Collect all dynamic service requests into a single string
                const partDescriptions = partsContainer.querySelectorAll('[name^="part-description-"]');
                const partLocations = partsContainer.querySelectorAll('[name^="part-location-"]');
                let partsString = '';
                for (let i = 0; i < partDescriptions.length; i++) {
                    // Changed output label to reflect "Warranty Item"
                    partsString += `Warranty Item #${i + 1}:\n`; 
                    partsString += `  Location of Issue: ${partLocations[i].value}\n`;
                    partsString += `  Service Description: ${partDescriptions[i].value}\n\n`;
                }
                
                // Determine the final user-name value
                const finalUserName = userNameSelect.value === 'Other'  
                    ? otherUserInput.value 
                    : userNameSelect.value;
                    
                // Determine the final community value
                const finalCommunity = communitySelect.value === 'Other'  
                    ? otherCommunityInput.value 
                    : communitySelect.value;

                const emailParams = {
                    'user-name': finalUserName,
                    'urgency': urgencySelect.value,
                    'home-address': finalCommunity,
                    'lot-number': form.elements['lot-number'].value,
                    'serial-number': form.elements['serial-number'].value,
                    'home-manufacturer': form.elements['home-manufacturer'].value,
                    'part-description': partsString, // The compiled list of services
                    'secondary_email': SECONDARY_EMAIL
                };
                
                // EMAILJS PATH REMAINS INTACT
                emailjs.send(SERVICE_ID, TEMPLATE_ID, emailParams)
                    .then(function() {
                        statusDiv.classList.remove('bg-blue-100', 'text-blue-800');
                        statusDiv.classList.add('bg-green-100', 'text-green-800');
                        statusDiv.innerHTML = '<strong>Success!</strong> Your request has been sent. <br><br> <button id="continue-btn" class="py-2 px-4 mt-2 bg-blue-600 hover:bg-blue-700 rounded-full text-white font-bold transition duration-150 ease-in-out">Submit Another Request</button>';
                        
                        formMainContent.style.display = 'none'; // Hide form only on success
                        document.getElementById('continue-btn').addEventListener('click', resetForm);
                    }, function(error) {
                        statusDiv.classList.remove('bg-blue-100', 'text-blue-800');
                        statusDiv.classList.add('bg-red-100', 'text-red-800');
                        statusDiv.innerHTML = `<strong>Failed!</strong> There was an error sending your request. Please try again.`;
                        console.error('EmailJS Error:', error);
                        // Form remains visible on failure
                    })
                    .finally(() => {
                        submitBtn.disabled = false;
                    });
            });
        })();
    </script>
</body>
</html>
