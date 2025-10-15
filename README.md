<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>21-Day Move-in Warranty Checklist</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script type="text/javascript" src="https://cdn.jsdelivr.net/npm/@emailjs/browser@4/dist/email.min.js"></script>
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        /* Styles for the checklist buttons and status */
        .status-ok { background-color: #d1fae5; color: #065f46; border-color: #10b981; }
        .status-issue { background-color: #fee2e2; color: #991b1b; border-color: #f87171; }
        
        /* Button colors for unselected state */
        .btn-ok-active { background-color: #10b981 !important; color: white !important; }
        .btn-issue-active { background-color: #ef4444 !important; color: white !important; }

        /* Custom alignment for buttons: Adjusted widths for single-line text */
        .button-group-alignment {
            display: flex;
            gap: 8px; 
            justify-content: flex-end;
            width: 100%;
        }
        .button-group-alignment .btn-ok {
            width: 60px; 
        }
        .button-group-alignment .btn-issue {
            width: 80px; 
        }
        .button-group-alignment .btn-clear {
            width: 60px; 
            white-space: nowrap; 
        }
        /* Ensure all action buttons have a consistent small text size */
        .button-group-alignment button {
            font-size: 0.875rem; 
            padding-left: 0.75rem; 
            padding-right: 0.75rem; 
        }
        /* Style for visual indication of unaddressed items */
        .unaddressed-item {
            border: 2px solid #f87171 !important;
            box-shadow: 0 0 5px rgba(248, 113, 113, 0.5);
        }
        .photo-ready { color: #059669; }
        .photo-error { color: #dc2626; }
    </style>
</head>
<body class="bg-gray-100 flex items-center justify-center min-h-screen p-4">
    <div class="bg-white p-8 rounded-2xl shadow-xl w-full max-w-2xl border border-gray-200">
        <h1 class="text-3xl font-bold text-center text-gray-800 mb-2">21-Day Move-in Warranty Checklist</h1>
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
                <p class="text-xs text-gray-500 italic mt-1">This number can be found on the information sheet under your kitchen sink.</p>
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
                
                <h2 class="text-xl font-bold text-gray-800">Interior: Cosmetic & Structure</h2>

                <!-- Item 1: Batten Strips/Trim -->
                <div id="item-batten-strips" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
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
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="batten-strips" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="batten-strips" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="batten-strips" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="batten-strips">
                        <label for="comment-batten-strips" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-batten-strips" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-batten-strips" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>

                <!-- Item 2: Wall/Ceiling Seams -->
                <div id="item-wall-seams" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Wall/Ceiling Seams">Wall/Ceiling Seams</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Throughout">Throughout</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Obvious gaps or large cracks in drywall/seams">
                                Check: Obvious gaps or large cracks in drywall/seams
                            </div>
                            <input type="hidden" name="issue-wall-seams" data-item-input data-item-index="2" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="wall-seams" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="wall-seams" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="wall-seams" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="wall-seams">
                        <label for="comment-wall-seams" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-wall-seams" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-wall-seams" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>

                <!-- Item 3: Flooring -->
                <div id="item-flooring" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Flooring">Flooring</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Throughout">Throughout</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Squeaks, bubbles, loose tiles, or lifted seams">
                                Check: Squeaks, bubbles, loose tiles, or lifted seams
                            </div>
                            <input type="hidden" name="issue-flooring" data-item-input data-item-index="3" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="flooring" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="flooring" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="flooring" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="flooring">
                        <label for="comment-flooring" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-flooring" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-flooring" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>

                <!-- Item 4: Doors (Interior) -->
                <div id="item-doors-interior" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Doors (Interior)">Doors (Interior)</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Throughout">Throughout</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Do not latch, stick, rub the frame, or have loose hardware">
                                Check: Do not latch, stick, rub the frame, or have loose hardware
                            </div>
                            <input type="hidden" name="issue-doors-interior" data-item-input data-item-index="4" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="doors-interior" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="doors-interior" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="doors-interior" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="doors-interior">
                        <label for="comment-doors-interior" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-doors-interior" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-doors-interior" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>
                
                <!-- Item 5: Doors (Exterior) -->
                <div id="item-doors-exterior" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Doors (Exterior)">Doors (Exterior)</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Front/Back">Front/Back</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Seal properly, latch securely, and align correctly">
                                Check: Seal properly, latch securely, and align correctly
                            </div>
                            <input type="hidden" name="issue-doors-exterior" data-item-input data-item-index="5" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="doors-exterior" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="doors-exterior" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="doors-exterior" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="doors-exterior">
                        <label for="comment-doors-exterior" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-doors-exterior" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-doors-exterior" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>
                
                <!-- Item 6: Cabinets/Drawers -->
                <div id="item-cabinets" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Cabinets/Drawers">Cabinets/Drawers</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Kitchen/Baths">Kitchen/Baths</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Loose hinges, drawers stick, missing hardware, or visible damage">
                                Check: Loose hinges, drawers stick, missing hardware, or visible damage
                            </div>
                            <input type="hidden" name="issue-cabinets" data-item-input data-item-index="6" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="cabinets" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="cabinets" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="cabinets" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="cabinets">
                        <label for="comment-cabinets" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-cabinets" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-cabinets" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>

                <!-- Item 7: Countertops -->
                <div id="item-countertops" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Countertops">Countertops</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Kitchen/Baths">Kitchen/Baths</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Scratches, chips, or loose/lifting seams">
                                Check: Scratches, chips, or loose/lifting seams
                            </div>
                            <input type="hidden" name="issue-countertops" data-item-input data-item-index="7" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="countertops" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="countertops" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="countertops" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="countertops">
                        <label for="comment-countertops" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-countertops" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-countertops" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>

                <!-- Item 8: Vinyl/Laminate -->
                <div id="item-vinyl-laminate" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Vinyl/Laminate">Vinyl/Laminate</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Throughout">Throughout</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Scratches, dents, or tears on finished surfaces">
                                Check: Scratches, dents, or tears on finished surfaces
                            </div>
                            <input type="hidden" name="issue-vinyl-laminate" data-item-input data-item-index="8" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="vinyl-laminate" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="vinyl-laminate" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="vinyl-laminate" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="vinyl-laminate">
                        <label for="comment-vinyl-laminate" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-vinyl-laminate" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-vinyl-laminate" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>

                <!-- Item 9: Windows -->
                <div id="item-windows" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Windows">Windows</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Throughout">Throughout</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Screens installed, open/close smoothly, and lock securely">
                                Check: Screens installed, open/close smoothly, and lock securely
                            </div>
                            <input type="hidden" name="issue-windows" data-item-input data-item-index="9" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="windows" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="windows" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="windows" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="windows">
                        <label for="comment-windows" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-windows" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-windows" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>

                <!-- Item 10: Faucets/Fixtures -->
                <div id="item-faucets" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Faucets/Fixtures">Faucets/Fixtures</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Kitchen/Baths">Kitchen/Baths</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Loose handles or visible leaks at the base/connection">
                                Check: Loose handles or visible leaks at the base/connection
                            </div>
                            <input type="hidden" name="issue-faucets" data-item-input data-item-index="10" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="faucets" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="faucets" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="faucets" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="faucets">
                        <label for="comment-faucets" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-faucets" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-faucets" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>


                <h2 class="text-xl font-bold text-gray-800 mt-8 pt-4 border-t border-gray-200">Plumbing, Electrical, & Appliance</h2>

                <!-- Item 11: Water Flow/Pressure -->
                <div id="item-water-flow-11" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Water Flow/Pressure">Water Flow/Pressure</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="All Sinks/Tubs">All Sinks/Tubs</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Test all faucets; check for low pressure or unusual noise">
                                Check: Test all faucets; check for low pressure or unusual noise
                            </div>
                            <input type="hidden" name="issue-water-flow-11" data-item-input data-item-index="11" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="water-flow-11" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="water-flow-11" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="water-flow-11" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="water-flow-11">
                        <label for="comment-water-flow-11" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-water-flow-11" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-water-flow-11" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>

                <!-- Item 12: Toilets -->
                <div id="item-toilets-12" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Toilets">Toilets</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="All Bathrooms">All Bathrooms</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Flush properly, no running or leaks at the base">
                                Check: Flush properly, no running or leaks at the base
                            </div>
                            <input type="hidden" name="issue-toilets-12" data-item-input data-item-index="12" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="toilets-12" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="toilets-12" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="toilets-12" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="toilets-12">
                        <label for="comment-toilets-12" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-toilets-12" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-toilets-12" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>

                <!-- Item 13: Water Heater -->
                <div id="item-water-heater-13" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Water Heater">Water Heater</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Utility Closet">Utility Closet</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Functioning (providing hot water). Check for leaks near the unit">
                                Check: Functioning (providing hot water). Check for leaks near the unit
                            </div>
                            <input type="hidden" name="issue-water-heater-13" data-item-input data-item-index="13" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="water-heater-13" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="water-heater-13" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="water-heater-13" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="water-heater-13">
                        <label for="comment-water-heater-13" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-water-heater-13" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-water-heater-13" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>

                <!-- Item 14: GFCI Outlets -->
                <div id="item-gfci-14" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="GFCI Outlets">GFCI Outlets</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Kitchen/Baths/Exterior">Kitchen/Baths/Exterior</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Press TEST button to ensure they trip, then press RESET">
                                Check: Press TEST button to ensure they trip, then press RESET
                            </div>
                            <input type="hidden" name="issue-gfci-14" data-item-input data-item-index="14" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="gfci-14" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="gfci-14" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="gfci-14" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="gfci-14">
                        <label for="comment-gfci-14" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-gfci-14" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-gfci-14" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>

                <!-- Item 15: Switches & Outlets -->
                <div id="item-switches-15" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Switches & Outlets">Switches & Outlets</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Throughout">Throughout</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="All switches operate their lights/fans; outlets have power">
                                Check: All switches operate their lights/fans; outlets have power
                            </div>
                            <input type="hidden" name="issue-switches-15" data-item-input data-item-index="15" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="switches-15" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="switches-15" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="switches-15" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="switches-15">
                        <label for="comment-switches-15" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-switches-15" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-switches-15" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>

                <!-- Item 16: Smoke/Carbon Monoxide Alarms -->
                <div id="item-alarms-16" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Smoke/Carbon Monoxide Alarms">Smoke/Carbon Monoxide Alarms</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Throughout">Throughout</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Test all alarms (usually a test button on the unit)">
                                Check: Test all alarms (usually a test button on the unit)
                            </div>
                            <input type="hidden" name="issue-alarms-16" data-item-input data-item-index="16" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="alarms-16" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="alarms-16" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="alarms-16" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="alarms-16">
                        <label for="comment-alarms-16" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-alarms-16" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-alarms-16" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>

                <!-- Item 17: Appliances -->
                <div id="item-appliances-17" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Appliances">Appliances</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Kitchen">Kitchen</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Range, Dishwasher, Microwave, Refrigerator are fully operational">
                                Check: Range, Dishwasher, Microwave, Refrigerator are fully operational
                            </div>
                            <input type="hidden" name="issue-appliances-17" data-item-input data-item-index="17" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="appliances-17" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="appliances-17" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="appliances-17" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="appliances-17">
                        <label for="comment-appliances-17" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-appliances-17" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-appliances-17" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>
                
                <h2 class="text-xl font-bold text-gray-800 mt-8 pt-4 border-t border-gray-200">Exterior & HVAC</h2>

                <!-- Item 25: Siding & Skirting -->
                <div id="item-siding" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Siding & Skirting">Siding & Skirting</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Exterior">Exterior</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Missing panels, dents, gaps, or improperly fastened skirting">
                                Check: Missing panels, dents, gaps, or improperly fastened skirting
                            </div>
                            <input type="hidden" name="issue-siding" data-item-input data-item-index="25" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="siding" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="siding" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="siding" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="siding">
                        <label for="comment-siding" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-siding" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-siding" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>

                <!-- Item 26: Roof Vents/Shingles -->
                <div id="item-roof" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Roof Vents/Shingles">Roof Vents/Shingles</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Roof/Exterior">Roof/Exterior</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Check for loose shingles, damage, or open vents/seals">
                                Check: Check for loose shingles, damage, or open vents/seals
                            </div>
                            <input type="hidden" name="issue-roof" data-item-input data-item-index="26" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="roof" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="roof" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="roof" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="roof">
                        <label for="comment-roof" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-roof" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-roof" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>

                <!-- Item 27: HVAC (Heat/AC) -->
                <div id="item-hvac" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="HVAC (Heat/AC)">HVAC (Heat/AC)</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Thermostat/Units">Thermostat/Units</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Run both Heat and Cooling cycles to ensure proper function">
                                Check: Run both Heat and Cooling cycles to ensure proper function
                            </div>
                            <input type="hidden" name="issue-hvac" data-item-input data-item-index="27" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="hvac" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="hvac" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="hvac" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="hvac">
                        <label for="comment-hvac" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-hvac" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-hvac" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>

                <!-- Item 28: Ductwork/Vents -->
                <div id="item-ductwork" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Ductwork/Vents">Ductwork/Vents</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Floor/Ceiling">Floor/Ceiling</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Vents are securely fastened and air is flowing strongly to all rooms">
                                Check: Vents are securely fastened and air is flowing strongly to all rooms
                            </div>
                            <input type="hidden" name="issue-ductwork" data-item-input data-item-index="28" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="ductwork" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="ductwork" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="ductwork" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="ductwork">
                        <label for="comment-ductwork" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-ductwork" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-ductwork" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>

                <!-- Item 29: Home Leveling -->
                <div id="item-leveling" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Home Leveling">Home Leveling</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Foundation">Foundation</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Check for noticeable slopes in floors or difficulty closing doors (structural issue)">
                                Check: Check for noticeable slopes in floors or difficulty closing doors (structural issue)
                            </div>
                            <input type="hidden" name="issue-leveling" data-item-input data-item-index="29" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="leveling" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="leveling" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="leveling" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="leveling">
                        <label for="comment-leveling" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-leveling" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-leveling" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>

                <!-- Item 30: Tie-Downs/Anchors -->
                <div id="item-tie-downs" class="warranty-item border p-4 rounded-lg bg-gray-50 transition duration-150 ease-in-out" data-photo-base64="" data-photo-name="">
                    <div class="flex flex-col justify-between items-start space-y-2">
                        <div class="flex-1 w-full space-y-1">
                            <p class="font-semibold text-gray-800" data-item-name="Tie-Downs/Anchors">Tie-Downs/Anchors</p>
                            <div class="flex space-x-4 text-sm text-gray-600">
                                <span class="font-medium">Location:</span>
                                <span data-item-location="Under Home">Under Home</span>
                            </div>
                            <div class="text-xs text-gray-500 italic" data-item-check="Visibly check anchors/straps for obvious signs of looseness or damage">
                                Check: Visibly check anchors/straps for obvious signs of looseness or damage
                            </div>
                            <input type="hidden" name="issue-tie-downs" data-item-input data-item-index="30" value=""> 
                        </div>
                        <div class="button-group-alignment">
                            <button type="button" data-action="ok" data-item="tie-downs" class="btn-ok py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">OK</button>
                            <button type="button" data-action="issue" data-item="tie-downs" class="btn-issue py-1 px-3 bg-white border border-gray-300 rounded-full text-sm hover:bg-gray-100 transition duration-150 ease-in-out">Issue</button>
                            <button type="button" data-action="clear" data-item="tie-downs" class="btn-clear py-1 px-3 bg-gray-200 border border-gray-300 rounded-full text-sm text-gray-600 hover:bg-gray-300 transition duration-150 ease-in-out">Clear</button>
                        </div>
                    </div>
                    <div class="comment-area space-y-2 mt-3 hidden" data-item-id="tie-downs">
                        <label for="comment-tie-downs" class="block text-xs font-medium text-gray-600">Additional Comments:</label>
                        <textarea id="comment-tie-downs" rows="2" class="w-full px-3 py-2 text-sm border border-gray-300 rounded-md focus:ring-red-500 focus:border-red-500"></textarea>
                        <!-- UPDATED: Photo Upload with camera capture and resizing note -->
                        <label class="block text-xs font-medium text-gray-600 pt-2">Attach Photo (Will be auto-resized to 1024px):</label>
                        <input type="file" id="photo-tie-downs" accept="image/*" capture="camera" data-photo-input class="text-xs w-full p-1 border border-gray-300 rounded-md bg-white cursor-pointer" onchange="handlePhotoChange(this)">
                        <div data-photo-status class="text-xs mt-1 font-semibold text-gray-500 min-h-[1.25rem]"></div>
                    </div>
                </div>

            </div>
            <div class="mt-6">
                <button type="submit" id="submit-btn" class="w-full py-3 px-4 bg-blue-600 hover:bg-blue-700 rounded-full text-white font-bold text-lg transition duration-150 ease-in-out shadow-lg">
                    Submit
                </button>
            </div>
        </form>

        <div id="status-message" class="mt-6 p-4 rounded-lg text-center hidden"></div>
    </div>

    <script>
        // --- UTILITY FUNCTIONS ---

        /**
         * Resizes an image loaded from a File object and converts it to a compressed Base64 JPEG URI.
         * Enforces a maximum dimension (MAX_WIDTH) for reliable email transmission.
         * @param {File} file - The image file to process.
         * @returns {Promise<string|null>} - Compressed Base64 data URI string or null if conversion fails.
         */
        function resizeAndConvertToBase64(file) {
            return new Promise((resolve, reject) => {
                if (!file) return resolve(null);
                const reader = new FileReader();
                reader.onload = function(event) {
                    const img = new Image();
                    img.onload = function() {
                        const MAX_WIDTH = 1024;
                        const MAX_HEIGHT = 1024;
                        const MIME_TYPE = 'image/jpeg';
                        const QUALITY = 0.7; // 70% compression for JPEG

                        let width = img.width;
                        let height = img.height;

                        // Calculate new dimensions to fit within MAX_WIDTH/MAX_HEIGHT while maintaining aspect ratio
                        if (width > height) {
                            if (width > MAX_WIDTH) {
                                height *= MAX_WIDTH / width;
                                width = MAX_WIDTH;
                            }
                        } else {
                            if (height > MAX_HEIGHT) {
                                width *= MAX_HEIGHT / height;
                                height = MAX_HEIGHT;
                            }
                        }
                        
                        const canvas = document.createElement('canvas');
                        canvas.width = width;
                        canvas.height = height;
                        
                        const ctx = canvas.getContext('2d');
                        // Draw the image at the new size
                        ctx.drawImage(img, 0, 0, width, height);
                        
                        // Convert canvas content to compressed JPEG Base64 string
                        const base64Data = canvas.toDataURL(MIME_TYPE, QUALITY);
                        resolve(base64Data);
                    };
                    img.onerror = reject;
                    img.src = event.target.result;
                };
                reader.onerror = reject;
                reader.readAsDataURL(file);
            });
        }


        /**
         * Handles the file input change, performs resizing, and stores the Base64 data.
         * @param {HTMLInputElement} fileInput - The file input element that triggered the change.
         */
        async function handlePhotoChange(fileInput) {
            const itemDiv = fileInput.closest('.warranty-item');
            const statusDiv = itemDiv.querySelector('[data-photo-status]');

            const file = fileInput.files[0];
            
            // Clear previous status and stored data
            statusDiv.textContent = '';
            itemDiv.dataset.photoBase64 = '';
            itemDiv.dataset.photoName = '';
            statusDiv.classList.remove('photo-ready', 'photo-error', 'text-blue-500');

            if (!file) return;

            statusDiv.classList.add('text-blue-500');
            statusDiv.innerHTML = 'Processing image... (Auto-resizing)'; // Added feedback
            
            // The file size check is now largely replaced by the aggressive compression/resizing
            // but a *very* large initial file might be slow to load, so we'll allow all.

            try {
                // Use the new resizing and compression utility
                const base64 = await resizeAndConvertToBase64(file);
                
                // Store Base64 and name on the parent item div's dataset
                itemDiv.dataset.photoBase64 = base64;
                itemDiv.dataset.photoName = file.name;
                
                statusDiv.classList.remove('text-blue-500');
                statusDiv.classList.add('photo-ready');
                statusDiv.innerHTML = `✅ Photo attached: <strong>${file.name}</strong> (Resized)`;
                
            } catch (error) {
                console.error("Image processing failed:", error);
                statusDiv.classList.remove('text-blue-500');
                statusDiv.classList.add('photo-error');
                statusDiv.innerHTML = `❌ Error processing image. Try a smaller file.`;
                fileInput.value = '';
            }
        }


        (function() {
            // !!! IMPORTANT: REPLACE THESE WITH YOUR ACTUAL EmailJS CREDENTIALS !!!
            const USER_ID = 'bSgwpRuVeEky48mPe';  
            const SERVICE_ID = 'service_7lbsq24';
            const TEMPLATE_ID_CONFIRMATION = 'template_of2vt65'; 
            const TEMPLATE_ID_STAFF = 'template_2a7qx72'; 
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


            // --- CHECKLIST LOGIC (UPDATED to clear photo data) ---
            checklistContainer.addEventListener('click', function(event) {
                const button = event.target.closest('button');
                if (!button) return;

                const itemDiv = button.closest('.warranty-item');
                const action = button.dataset.action;
                const issueInput = itemDiv.querySelector('[data-item-input]');
                const commentArea = itemDiv.querySelector('.comment-area');
                const commentInput = commentArea.querySelector('textarea');
                const photoInput = itemDiv.querySelector('[data-photo-input]');
                const photoStatus = itemDiv.querySelector('[data-photo-status]');
                
                // 1. Remove all active button classes
                itemDiv.querySelectorAll('button[data-action]').forEach(btn => {
                    btn.classList.remove('btn-ok-active', 'btn-issue-active');
                });
                // 2. Remove visual status classes
                itemDiv.classList.remove('status-ok', 'status-issue', 'unaddressed-item');


                if (action === 'ok') {
                    button.classList.add('btn-ok-active');
                    itemDiv.classList.add('status-ok');
                    issueInput.value = 'OK'; 
                    commentArea.classList.add('hidden');
                    commentInput.value = ''; 
                    
                    // Clear image specific fields
                    itemDiv.dataset.photoBase64 = '';
                    itemDiv.dataset.photoName = '';
                    if (photoInput) photoInput.value = '';
                    if (photoStatus) {
                        photoStatus.textContent = '';
                        photoStatus.classList.remove('photo-ready', 'photo-error', 'text-blue-500');
                    }
                } else if (action === 'issue') {
                    button.classList.add('btn-issue-active');
                    itemDiv.classList.add('status-issue');
                    
                    const itemName = itemDiv.querySelector('[data-item-name]').textContent.trim();
                    const itemLocation = itemDiv.querySelector('[data-item-location]').textContent.trim();

                    // Simplify the data stored in the hidden input to just the Issue Description and Location.
                    issueInput.value = `${itemName} (Location: ${itemLocation})`;
                    
                    commentArea.classList.remove('hidden'); 

                } else if (action === 'clear') {
                    issueInput.value = ''; 
                    commentInput.value = '';
                    commentArea.classList.add('hidden'); 
                    
                    // Clear image specific fields
                    itemDiv.dataset.photoBase64 = '';
                    itemDiv.dataset.photoName = '';
                    if (photoInput) photoInput.value = '';
                    if (photoStatus) {
                        photoStatus.textContent = '';
                        photoStatus.classList.remove('photo-ready', 'photo-error', 'text-blue-500');
                    }
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

                // Reset checklist items visually and internally (including photo data)
                document.querySelectorAll('.warranty-item').forEach(item => {
                    item.classList.remove('status-ok', 'status-issue', 'unaddressed-item');
                    item.querySelector('[data-item-input]').value = '';
                    item.querySelector('.comment-area').classList.add('hidden');
                    item.querySelector('.comment-area textarea').value = '';
                    item.querySelectorAll('button[data-action]').forEach(btn => {
                        btn.classList.remove('btn-ok-active', 'btn-issue-active');
                    });

                    // Clear photo data
                    item.dataset.photoBase64 = '';
                    item.dataset.photoName = '';
                    const photoInput = item.querySelector('[data-photo-input]');
                    const photoStatus = item.querySelector('[data-photo-status]');
                    if (photoInput) photoInput.value = '';
                    if (photoStatus) {
                        photoStatus.textContent = '';
                        photoStatus.classList.remove('photo-ready', 'photo-error', 'text-blue-500');
                    }
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

                // Disable button and show loading status
                submitBtn.disabled = true;
                statusDiv.classList.remove('hidden', 'bg-green-100', 'text-green-800', 'bg-red-100', 'text-red-800');
                statusDiv.classList.add('bg-blue-100', 'text-blue-800');
                statusDiv.innerHTML = 'Sending request... Please wait.';

                // 1. INITIAL FORM VALIDATION (Browser check for required HTML fields)
                if (!form.checkValidity()) {
                    // This triggers the browser's native error popups for required fields
                    submitBtn.disabled = false;
                    return;
                }
                
                // 2. CHECKLIST VALIDATION: Ensure ALL items are marked OK or Issue
                let allItemsAddressed = true;
                document.querySelectorAll('.warranty-item').forEach(item => {
                    item.classList.remove('unaddressed-item'); // Clear previous visual warnings
                    const value = item.querySelector('[data-item-input]').value.trim();
                    
                    if (value === '') {
                        allItemsAddressed = false;
                        item.classList.add('unaddressed-item'); // Highlight unaddressed item
                    }
                });

                if (!allItemsAddressed) {
                    statusDiv.classList.remove('hidden', 'bg-blue-100', 'text-blue-800', 'bg-green-100', 'text-green-800');
                    statusDiv.classList.add('bg-red-100', 'text-red-800');
                    statusDiv.innerHTML = '<strong>Validation Error:</strong> Please mark every item as either **OK** or **Issue** before submitting.';
                    submitBtn.disabled = false;
                    return;
                }

                // 3. COMPILE CHECKLIST ISSUES (At least one Issue must be marked)
                let issuesString = '';
                let hasIssue = false;
                let photoCount = 0;
                const photoParams = {};
                
                document.querySelectorAll('.warranty-item').forEach((item, index) => {
                    const issueInput = item.querySelector('[data-item-input]');
                    const commentInput = item.querySelector('.comment-area textarea');
                    const value = issueInput.value.trim();
                    
                    if (value && value !== 'OK') {
                        hasIssue = true;
                        
                        let itemReport = `Issue Reported: ${value}`;
                        
                        // Include comment
                        if (commentInput && commentInput.value.trim().length > 0) {
                            itemReport += `\n    Comment: ${commentInput.value.trim()}`;
                        }
                        
                        // NEW: Include photo data
                        const photoBase64 = item.dataset.photoBase64;
                        const photoName = item.dataset.photoName;

                        if (photoBase64 && photoName) {
                            if (photoCount < 5) { // Limit to 5 photos for reasonable email size
                                photoCount++;
                                // Pass Base64 data and name as dedicated parameters for the EmailJS template
                                photoParams[`photo_${photoCount}_name`] = photoName;
                                photoParams[`photo_${photoCount}_data`] = photoBase64;
                                itemReport += `\n    Photo: Yes (Attached as Photo ${photoCount} - Resized)`; // Updated report text
                            } else {
                                itemReport += `\n    Photo: Yes (Limit of 5 photos reached, this photo was NOT attached to email.)`;
                            }
                        } else {
                            itemReport += `\n    Photo: No`;
                        }
                        issuesString += itemReport + '\n\n';
                    }
                });

                // 4. CHECK IF THERE ARE ANY ISSUES REPORTED
                if (!hasIssue) {
                    statusDiv.classList.remove('hidden', 'bg-blue-100', 'text-blue-800', 'bg-green-100', 'text-green-800');
                    statusDiv.classList.add('bg-red-100', 'text-red-800');
                    statusDiv.innerHTML = '<strong>Submission Error:</strong> All items are marked OK. Please mark at least one item as an **Issue** if you wish to proceed with a warranty request.';
                    submitBtn.disabled = false;
                    return;
                }
                
                // Determine the final community value
                const finalCommunity = communitySelect.value === 'Other'  
                    ? otherCommunityInput.value 
                    : communitySelect.value;

                // --- PARAMETERS FOR BOTH EMAILS ---
                const emailParams = {
                    'to_email': contactEmailInput.value, 
                    'user-name': 'Homeowner', 
                    'homeowner-name': homeownerNameInput.value,
                    'contact-phone': contactPhoneInput.value,
                    'contact-email': contactEmailInput.value,
                    'urgency': 'Medium', 
                    'home-address': finalCommunity,
                    'lot-number': form.elements['lot-number'].value,
                    'serial-number': form.elements['serial-number'].value,
                    'home-manufacturer': form.elements['home-manufacturer'].value,
                    'part-description': issuesString, 
                    'secondary_email': SECONDARY_EMAIL, 
                    
                    // NEW: Dynamically added photo parameters (up to 5)
                    ...photoParams 
                };
                
                // SEND EMAILS
                const confirmationSend = emailjs.send(SERVICE_ID, TEMPLATE_ID_CONFIRMATION, emailParams);
                const primarySend = emailjs.send(SERVICE_ID, TEMPLATE_ID_STAFF, emailParams);


                // HANDLE BOTH PROMISES
                Promise.all([primarySend, confirmationSend])
                    .then(function() {
                        statusDiv.classList.remove('bg-blue-100', 'text-blue-800');
                        statusDiv.classList.add('bg-green-100', 'text-green-800');
                        statusDiv.innerHTML = '<strong>Success!</strong> Your request has been sent. A confirmation email has been sent to your address. <br><br> <button id="continue-btn" class="py-2 px-4 mt-2 bg-blue-600 hover:bg-blue-700 rounded-full text-white font-bold transition duration-150 ease-in-out">Submit Another Request</button>';
                        
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
