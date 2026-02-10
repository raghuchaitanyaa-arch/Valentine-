# Valentine-<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Will You Be My Valentine?</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: linear-gradient(135deg, #ffafbd, #ffc3a0);
            overflow: hidden;
            padding: 20px;
        }
        
        .container {
            text-align: center;
            max-width: 800px;
            background-color: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
            position: relative;
            overflow: hidden;
            border: 8px solid #ff6b8b;
        }
        
        h1 {
            color: #ff4d6d;
            font-size: 3rem;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }
        
        .heart-icon {
            color: #ff4d6d;
            font-size: 5rem;
            margin: 20px 0;
            animation: heartbeat 1.5s infinite;
        }
        
        .question {
            font-size: 1.8rem;
            color: #333;
            margin-bottom: 40px;
            line-height: 1.5;
        }
        
        .buttons-container {
            position: relative;
            height: 200px;
            margin: 30px 0;
        }
        
        #yes-btn {
            background-color: #ff4d6d;
            color: white;
            border: none;
            padding: 20px 60px;
            font-size: 2rem;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 8px 20px rgba(255, 77, 109, 0.4);
            transition: all 0.3s;
            font-weight: bold;
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%);
            z-index: 10;
        }
        
        #yes-btn:hover {
            background-color: #ff3355;
            transform: translate(-50%, -50%) scale(1.05);
            box-shadow: 0 10px 25px rgba(255, 77, 109, 0.6);
        }
        
        .no-option {
            font-size: 1.2rem;
            color: #666;
            margin-top: 10px;
            font-style: italic;
        }
        
        .message {
            display: none;
            font-size: 2.2rem;
            color: #ff4d6d;
            margin-top: 30px;
            padding: 20px;
            background-color: rgba(255, 255, 255, 0.8);
            border-radius: 15px;
            border: 3px dashed #ff4d6d;
            animation: fadeIn 1s;
        }
        
        .hearts-background {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }
        
        .heart {
            position: absolute;
            color: rgba(255, 77, 109, 0.2);
            font-size: 1.5rem;
            animation: float 5s infinite linear;
        }
        
        @keyframes heartbeat {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        @keyframes float {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 0.8;
            }
            90% {
                opacity: 0.8;
            }
            100% {
                transform: translateY(-100px) rotate(360deg);
                opacity: 0;
            }
        }
        
        .instructions {
            margin-top: 30px;
            font-size: 1.1rem;
            color: #666;
            font-style: italic;
        }
        
        @media (max-width: 768px) {
            h1 { font-size: 2.2rem; }
            .question { font-size: 1.5rem; }
            #yes-btn { font-size: 1.7rem; padding: 15px 40px; }
            .container { padding: 25px; }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="hearts-background" id="hearts-bg"></div>
        
        <h1>Happy Valentine's Day!</h1>
        
        <div class="heart-icon">
            <i class="fas fa-heart"></i>
        </div>
        
        <p class="question">
            You mean so much to me. I have an important question to ask you...
        </p>
        
        <p class="question" style="font-size: 2.2rem; color: #ff4d6d; font-weight: bold;">
            Will you be my Valentine?
        </p>
        
        <div class="buttons-container">
            <button id="yes-btn">YES!</button>
            <p class="no-option">There's no "no" option because you're already perfect for me!</p>
        </div>
        
        <div id="success-message" class="message">
            Yay! You made me the happiest person! ❤️
        </div>
        
        <p class="instructions">
            (Try to click the YES button... it's excited to be clicked!)
        </p>
    </div>

    <script>
        // Create floating hearts in background
        const heartsBg = document.getElementById('hearts-bg');
        for (let i = 0; i < 25; i++) {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '<i class="fas fa-heart"></i>';
            heart.style.left = `${Math.random() * 100}%`;
            heart.style.animationDelay = `${Math.random() * 5}s`;
            heart.style.fontSize = `${Math.random() * 20 + 10}px`;
            heartsBg.appendChild(heart);
        }
        
        const yesBtn = document.getElementById('yes-btn');
        const successMessage = document.getElementById('success-message');
        const container = document.querySelector('.container');
        
        // Make the button move when mouse approaches
        yesBtn.addEventListener('mouseover', function() {
            // Calculate random position within container
            const containerRect = container.getBoundingClientRect();
            const btnRect = yesBtn.getBoundingClientRect();
            
            const maxX = containerRect.width - btnRect.width - 40;
            const maxY = containerRect.height - btnRect.height - 40;
            
            // Generate random position, but not too close to edges
            const randomX = Math.max(40, Math.random() * maxX);
            const randomY = Math.max(40, Math.random() * maxY);
            
            // Move the button
            yesBtn.style.left = `${randomX}px`;
            yesBtn.style.top = `${randomY}px`;
            yesBtn.style.transform = 'translate(0, 0)';
            
            // Add some fun effects
            yesBtn.style.backgroundColor = getRandomColor();
        });
        
        // When button is finally clicked
        yesBtn.addEventListener('click', function() {
            // Stop the button from moving
            yesBtn.style.pointerEvents = 'none';
            
            // Show success message
            successMessage.style.display = 'block';
            
            // Create explosion of hearts
            for (let i = 0; i < 30; i++) {
                createHeartExplosion();
            }
            
            // Change background color
            document.body.style.background = 'linear-gradient(135deg, #ffdde1, #ee9ca7)';
            
            // Play a sound (if allowed by browser)
            playClickSound();
            
            // Change title
            document.title = "She Said YES! ❤️";
        });
        
        // Create heart explosion effect
        function createHeartExplosion() {
            const heart = document.createElement('div');
            heart.innerHTML = '<i class="fas fa-heart"></i>';
            heart.style.position = 'fixed';
            heart.style.color = getRandomColor();
            heart.style.fontSize = `${Math.random() * 30 + 20}px`;
            heart.style.left = `${Math.random() * 100}vw`;
            heart.style.top = `${Math.random() * 100}vh`;
            heart.style.zIndex = '1000';
            heart.style.pointerEvents = 'none';
            
            // Random animation
            heart.style.animation = `explode ${Math.random() * 1 + 1}s forwards`;
            
            document.body.appendChild(heart);
            
            // Remove heart after animation
            setTimeout(() => {
                heart.remove();
            }, 1500);
        }
        
        // Generate random Valentine-appropriate color
        function getRandomColor() {
            const colors = [
                '#ff4d6d', '#ff8fa3', '#ffb3c1', '#ff758f',
                '#ff477e', '#ff5c8a', '#ff0a54', '#ff477e'
            ];
            return colors[Math.floor(Math.random() * colors.length)];
        }
        
        // Play a subtle click sound
        function playClickSound() {
            try {
                const audioContext = new (window.AudioContext || window.webkitAudioContext)();
                const oscillator = audioContext.createOscillator();
                const gainNode = audioContext.createGain();
                
                oscillator.connect(gainNode);
                gainNode.connect(audioContext.destination);
                
                oscillator.frequency.value = 523.25; // C5
                oscillator.type = 'sine';
                
                gainNode.gain.setValueAtTime(0.3, audioContext.currentTime);
                gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.5);
                
                oscillator.start(audioContext.currentTime);
                oscillator.stop(audioContext.currentTime + 0.5);
            } catch (e) {
                // Audio context not supported or autoplay policy prevented playback
                console.log("Could not play sound: ", e);
            }
        }
        
        // Add CSS for explode animation
        const style = document.createElement('style');
        style.textContent = `
            @keyframes explode {
                0% {
                    transform: translate(0, 0) scale(0) rotate(0deg);
                    opacity: 1;
                }
                100% {
                    transform: translate(${Math.random() * 200 - 100}px, ${Math.random() * 200 - 100}px) scale(1) rotate(360deg);
                    opacity: 0;
                }
            }
        `;
        document.head.appendChild(style);
    </script>
</body>
</html>
