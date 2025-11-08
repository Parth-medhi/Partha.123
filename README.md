<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Will You Be My Girlfriend?</title>
    <style>
        body {
            font-family: 'Dancing Script', cursive; /* Romantic font */
            text-align: center;
            background: linear-gradient(135deg, #ff9a9e, #fecfef, #fecfef); /* Pink gradient background */
            padding: 50px;
            overflow: hidden;
            color: #333;
        }
        h1 {
            font-size: 3em;
            color: #ff69b4;
            animation: fadeIn 2s ease-in;
        }
        p {
            font-size: 1.5em;
            animation: fadeIn 3s ease-in;
        }
        .buttons {
            margin-top: 50px;
            animation: slideUp 2s ease-out;
        }
        button {
            padding: 15px 30px;
            font-size: 20px;
            margin: 20px;
            border: 2px solid #fff;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
        }
        #yes {
            background-color: #4CAF50;
            color: white;
        }
        #yes:hover {
            transform: scale(1.1);
            background-color: #45a049;
        }
        #no {
            background-color: #f44336;
            color: white;
            position: absolute;
            transition: transform 0.5s ease; /* Smooth movement */
        }
        #no:hover {
            transform: scale(0.9);
        }
        .celebration {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.9);
            color: white;
            justify-content: center;
            align-items: center;
            font-size: 3em;
            z-index: 1000;
            animation: zoomIn 1s ease-out;
        }
        canvas {
            position: absolute;
            top: 0;
            left: 0;
            pointer-events: none;
        }
        .heart {
            position: absolute;
            font-size: 2em;
            animation: float 3s infinite ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        @keyframes slideUp {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        @keyframes zoomIn {
            from { transform: scale(0); }
            to { transform: scale(1); }
        }
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }
    </style>
</head>
<body>
    <h1>Will You Be My Girlfriend?</h1>
    <p>From the moment I saw you, my heart skipped a beat. You've been on my mind every day. Will you make me the happiest person alive?</p>
    <div class="buttons">
        <button id="yes">Yes! 💕</button>
        <button id="no">No 😢</button>
    </div>
    <div class="celebration" id="celebration">
        🎉 Congratulations! We're together now! 💖 Let's celebrate forever! 🎊
    </div>
    <canvas id="confetti-canvas"></canvas>

    <!-- Floating hearts for ambiance -->
    <div class="heart" style="left: 10%; top: 20%;">❤️</div>
    <div class="heart" style="left: 80%; top: 40%;">💖</div>
    <div class="heart" style="left: 50%; top: 70%;">💕</div>

    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <script>
        const noButton = document.getElementById('no');
        const yesButton = document.getElementById('yes');
        const celebration = document.getElementById('celebration');

        // Function to move the No button randomly with smooth animation
        function moveNoButton() {
            const x = Math.random() * (window.innerWidth - 150); // Random X position
            const y = Math.random() * (window.innerHeight - 150); // Random Y position
            noButton.style.left = x + 'px';
            noButton.style.top = y + 'px';
        }

        // Move only on click
        noButton.addEventListener('click', function(event) {
            event.preventDefault();
            moveNoButton();
        });

        // Handle Yes button click with enhanced celebration
        yesButton.addEventListener('click', function() {
            // Hide buttons
            document.querySelector('.buttons').style.display = 'none';
            // Show celebration overlay
            celebration.style.display = 'flex';
            // Trigger multiple confetti bursts
            confetti({
                particleCount: 300,
                spread: 100,
                origin: { y: 0.6 }
            });
            setTimeout(() => {
                confetti({
                    particleCount: 200,
                    angle: 60,
                    spread: 55,
                    origin: { x: 0 }
                });
            }, 500);
            setTimeout(() => {
                confetti({
                    particleCount: 200,
                    angle: 120,
                    spread: 55,
                    origin: { x: 1 }
                });
            }, 1000);
            // Optional: Auto-hide after a few seconds
            setTimeout(() => {
                celebration.style.display = 'none';
            }, 8000);
        });
    </script>
</body>
</html>
