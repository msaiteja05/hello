<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday!</title>
    <!-- Tailwind CSS CDN for styling -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Custom font import from Google Fonts */
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap');
        body {
            font-family: 'Inter', sans-serif;
        }
        /* Hide scrollbars for a cleaner look */
        body::-webkit-scrollbar {
            display: none;
        }
        .container-bg {
            background: radial-gradient(circle, #6d28d9 0%, #4c1d95 100%);
        }

        /* Floating animation for background images */
        @keyframes float-animation {
            0% {
                transform: translateY(0) scale(1) rotate(0deg);
                opacity: 0.8;
            }
            50% {
                transform: translateY(-50px) scale(1.1) rotate(5deg);
                opacity: 1;
            }
            100% {
                transform: translateY(0) scale(1) rotate(0deg);
                opacity: 0.8;
            }
        }
        .floating-element {
            position: absolute;
            animation-name: float-animation;
            animation-iteration-count: infinite;
            animation-timing-function: ease-in-out;
            opacity: 0.8;
        }
        /* Transition for a smooth appearance */
        #present-screen {
            transition: opacity 1s ease-in-out;
            opacity: 0;
        }
        #present-screen.active {
            opacity: 1;
        }

        /* Fade out for video */
        .fade-out-video {
            transition: opacity 1s ease-in-out;
            opacity: 0;
        }

        /* Fade in for after-video message */
        .fade-in-message {
            transition: opacity 1s ease-in-out;
            opacity: 0;
        }
        .fade-in-message.active {
            opacity: 1;
        }

        /* Pulsing animation for the gift box */
        @keyframes pulse {
            0% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.05);
            }
            100% {
                transform: scale(1);
            }
        }
        .pulse-animation {
            animation: pulse 2s infinite ease-in-out;
        }
        /* New shaking animation */
        @keyframes shake {
            0% { transform: translateX(0); }
            25% { transform: translateX(-5px); }
            50% { transform: translateX(5px); }
            75% { transform: translateX(-5px); }
            100% { transform: translateX(0); }
        }
        .shake-animation {
            animation: shake 0.5s infinite;
        }

        /* Gift box opening animation */
        @keyframes gift-lid-open {
            0% {
                transform: translateY(0) rotateX(0deg);
                opacity: 1;
            }
            50% {
                transform: translateY(-100px) rotateX(45deg);
            }
            100% {
                transform: translateY(-200px) rotateX(90deg);
                opacity: 0;
            }
        }
        .lid-open {
            animation: gift-lid-open 1.5s forwards ease-in-out;
        }
    </style>
</head>
<body class="container-bg h-screen flex items-center justify-center text-white p-4 overflow-hidden">

    <!-- Floating Background Elements -->
    <div class="fixed inset-0 z-0">
        <span class="floating-element text-5xl" style="top: 10%; left: 15%; animation-duration: 10s; animation-delay: 1s;">🎉</span>
        <span class="floating-element text-6xl" style="top: 25%; left: 80%; animation-duration: 12s; animation-delay: 2s;">🎈</span>
        <span class="floating-element text-4xl" style="top: 50%; left: 5%; animation-duration: 9s; animation-delay: 0s;">🎂</span>
        <span class="floating-element text-7xl" style="top: 70%; left: 40%; animation-duration: 14s; animation-delay: 3s;">🎁</span>
        <span class="floating-element text-5xl" style="top: 85%; left: 75%; animation-duration: 11s; animation-delay: 4s;">🎈</span>
        <span class="floating-element text-4xl" style="top: 30%; left: 45%; animation-duration: 13s; animation-delay: 1.5s;">🎉</span>
        <span class="floating-element text-6xl" style="top: 60%; left: 20%; animation-duration: 10s; animation-delay: 5s;">🎂</span>
        <span class="floating-element text-5xl" style="top: 5%; left: 60%; animation-duration: 15s; animation-delay: 2.5s;">🎁</span>
    </div>

    <!-- Main Container -->
    <div id="app-container" class="w-full max-w-4xl bg-white bg-opacity-10 backdrop-filter backdrop-blur-lg rounded-xl shadow-2xl p-8 md:p-12 text-center flex flex-col items-center z-10">

        <!-- Initial "Open Present" Screen -->
        <div id="initial-screen" class="flex flex-col items-center justify-center space-y-8">
            <h1 class="text-4xl md:text-5xl font-bold mb-4 animate-pulse">It's a Present for You!</h1>
            <p class="text-lg md:text-xl text-gray-300">Click the gift box to open.</p>

            <!-- Gift Box SVG (Stylized) -->
            <div id="gift-box-container" class="cursor-pointer transform transition-all duration-300 hover:scale-105 shake-animation" style="width: 250px;">
                <svg id="gift-svg" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 200">
                    <defs>
                        <linearGradient id="boxGradient" x1="0%" y1="0%" x2="0%" y2="100%">
                            <stop offset="0%" style="stop-color:#f87171;stop-opacity:1" />
                            <stop offset="100%" style="stop-color:#b91c1c;stop-opacity:1" />
                        </linearGradient>
                        <linearGradient id="boxSideGradient" x1="0%" y1="0%" x2="100%" y2="0%">
                            <stop offset="0%" style="stop-color:#b91c1c;stop-opacity:1" />
                            <stop offset="100%" style="stop-color:#7f1d1d;stop-opacity:1" />
                        </linearGradient>
                        <linearGradient id="lidGradient" x1="0%" y1="0%" x2="0%" y2="100%">
                            <stop offset="0%" style="stop-color:#ef4444;stop-opacity:1" />
                            <stop offset="100%" style="stop-color:#b91c1c;stop-opacity:1" />
                        </linearGradient>
                        <linearGradient id="ribbonGradient" x1="0%" y1="0%" x2="0%" y2="100%">
                            <stop offset="0%" style="stop-color:#fcd34d;stop-opacity:1" />
                            <stop offset="100%" style="stop-color:#d97706;stop-opacity:1" />
                        </linearGradient>
                        <filter id="shadow">
                            <feDropShadow dx="2" dy="4" stdDeviation="2" flood-color="#000" flood-opacity="0.3"/>
                        </filter>
                    </defs>
                    <!-- Box Base -->
                    <rect x="30" y="80" width="140" height="80" fill="url(#boxGradient)" filter="url(#shadow)" />
                    <!-- Ribbon -->
                    <rect x="85" y="80" width="30" height="80" fill="url(#ribbonGradient)" />
                    <!-- Box Lid -->
                    <g id="gift-lid">
                        <path d="M20 75 C 40 60, 160 60, 180 75 L 175 80 C 158 70, 42 70, 25 80 Z" fill="url(#lidGradient)" filter="url(#shadow)" />
                        <rect x="25" y="70" width="150" height="10" fill="#ef4444" />
                        <!-- Bow -->
                        <path d="M100 70 C 80 50, 60 65, 60 40 C 60 15, 80 25, 100 50 Z" fill="#fcd34d" />
                        <path d="M100 70 C 120 50, 140 65, 140 40 C 140 15, 120 25, 100 50 Z" fill="#fcd34d" />
                        <circle cx="100" cy="70" r="8" fill="#d97706" />
                    </g>
                </svg>
            </div>
        </div>

        <!-- Present Content Screen (Initially Hidden) -->
        <div id="present-screen" class="hidden w-full space-y-8">
            <h2 class="text-3xl md:text-4xl font-bold text-yellow-300">Happy Birthday, Vinitha! 🎉</h2>

            <!-- The Video Container -->
            <div id="video-container" class="w-full flex justify-center">
                <!-- IMPORTANT: This is a placeholder video for testing. -->
                <!-- Replace the video 'src' with a direct link to your own video file. -->
                <div class="relative w-full max-h-96 rounded-xl shadow-lg border-4 border-yellow-300">
                    <video id="present-video" playsinline class="w-full h-full object-cover">
                        <source src="https://media.w3.org/2010/05/sintel/trailer.mp4" type="video/mp4">
                        Your browser does not support the video tag.
                    </video>
                    <!-- Modern SVG Play button -->
                    <button id="video-play-button" class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 bg-white bg-opacity-50 hover:bg-opacity-75 transition-all duration-300 rounded-full p-4 text-white">
                        <svg class="h-16 w-16" fill="currentColor" viewBox="0 0 24 24">
                            <path d="M8 5v14l11-7z"/>
                        </svg>
                    </button>
                </div>
            </div>
        </div>

        <!-- After-Video Message Screen (Initially Hidden) -->
        <div id="after-video-message" class="hidden w-full space-y-8 fade-in-message">
            <h2 class="text-3xl md:text-4xl font-bold text-yellow-300">A Final Message for You...</h2>
            <p class="text-lg md:text-xl text-gray-200 leading-relaxed">
                “Wishing you a day filled with happiness and a year filled with joy. Happy birthday!”Congratulations on completing another trip around the sun! May your year be filled with joy, laughter, and all the things that make you happy. You are an incredible person, and I'm so grateful to have you in my life. 
            <h3 class="text-xl md:text-2xl font-bold text-yellow-400 mt-6"> Always Keep Smiling!!
            </p></h3>
            <p class="text-lg md:text-xl text-gray-200"></p>
        </div>

    </div>

    <!-- General Message Box to replace `alert()` -->
    <div id="message-box" class="fixed inset-0 bg-black bg-opacity-70 hidden items-center justify-center p-4">
        <div class="bg-gray-800 text-white p-6 rounded-xl shadow-lg text-center max-w-sm">
            <p id="message-text" class="text-lg"></p>
            <button id="message-close-button" class="mt-4 bg-purple-500 hover:bg-purple-600 transition-colors duration-300 text-white font-bold py-2 px-4 rounded-full">
                OK
            </button>
        </div>
    </div>

    <script>
        // Use a custom message box instead of alert()
        function showMessage(message) {
            const messageBox = document.getElementById('message-box');
            const messageText = document.getElementById('message-text');
            const messageCloseButton = document.getElementById('message-close-button');

            messageText.textContent = message;
            messageBox.classList.remove('hidden');
            messageBox.classList.add('flex');

            messageCloseButton.onclick = () => {
                messageBox.classList.add('hidden');
                messageBox.classList.remove('flex');
            };
        }

        window.onload = function() {
            // Get all the necessary DOM elements
            const initialScreen = document.getElementById('initial-screen');
            const presentScreen = document.getElementById('present-screen');
            const afterVideoMessage = document.getElementById('after-video-message');
            const giftBoxContainer = document.getElementById('gift-box-container');
            const presentVideo = document.getElementById('present-video');
            const videoPlayButton = document.getElementById('video-play-button');
            const videoContainer = document.getElementById('video-container');
            const giftLid = document.getElementById('gift-lid');

            // Event listener for the "Open Present" button
            giftBoxContainer.addEventListener('click', () => {
                // Animate the gift box lid
                giftLid.classList.add('lid-open');

                // Wait for the lid animation to complete before transitioning to the next screen
                setTimeout(() => {
                    initialScreen.classList.add('hidden');
                    presentScreen.classList.remove('hidden');
                    setTimeout(() => {
                        presentScreen.classList.add('active');
                    }, 10); // A small delay to trigger the transition
                }, 1500); // Wait for the 1.5s animation to finish
            });

            // Event listener for the custom play button
            videoPlayButton.addEventListener('click', () => {
                // Hide the custom play button
                videoPlayButton.classList.add('hidden');
                
                // Play the video
                presentVideo.play();
            });
            
            // Listen for when the present video ends
            presentVideo.addEventListener('ended', () => {
                // Add the fade-out class to the video container
                videoContainer.classList.add('fade-out-video');
                
                // Wait for the fade-out to complete before changing screens
                setTimeout(() => {
                    // Hide the video screen and show the final message
                    presentScreen.classList.add('hidden');
                    afterVideoMessage.classList.remove('hidden');
                    setTimeout(() => {
                        afterVideoMessage.classList.add('active');
                    }, 10); // A small delay to trigger the transition
                }, 1000); // 1000ms matches the CSS transition duration
            });
        };
    </script>

</body>
</html>
