<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Enhanced and Luxuriant Code Rain Animation</title>
   <style>
       body {
           margin: 0;
           overflow: hidden;
           background: radial-gradient(circle, #000000, #1a1a1a, #333333); /* Fancy background */
           font-family: monospace;
           display: flex;
           justify-content: center;
           align-items: center;
           height: 100vh;
       }
       .container {
           position: relative;
           width: 100%;
           height: 100%;
           overflow: hidden;
       }
       .code {
           position: absolute;
           top: 0;
           width: 30px;
           animation: rain linear infinite;
       }
       .char {
           display: block;
           text-shadow: 0 0 10px, 0 0 20px; /* Neon glow effect */
           animation: flicker 1s infinite; /* Flickering effect */
           font-size: 20px;
       }
       @keyframes rain {
           0% { transform: translateY(-100%); }
           100% { transform: translateY(100vh); }
       }
       @keyframes flicker {
           0%, 100% { opacity: 1; }
           50% { opacity: 0.6; }
           70% { opacity: 0.9; }
       }
       .emoji {
           position: absolute;
           font-size: 30px;
           pointer-events: none;
           animation: fadeOut 1s forwards, wiggle 1s ease-in-out;
       }
       @keyframes fadeOut {
           0% { opacity: 1; }
           100% { opacity: 0; }
       }
       @keyframes wiggle {
           0% { transform: rotate(0deg); }
           50% { transform: rotate(15deg); }
           100% { transform: rotate(-15deg); }
       }
   </style>
</head>
<body>
   <div class="container"></div>
   <script>
       const container = document.querySelector('.container');
       const columnWidth = 30;
       const columns = Math.floor(window.innerWidth / columnWidth);
       const colors = ['#80FF00', '#FF00FF', '#00FFFF', '#FFFF00', '#FF8000', '#FF4500', '#32CD32', '#1E90FF', '#FFD700', '#FF6347', '#8A2BE2', '#00FA9A']; // Additional colors

       function generateCode() {
           const chars = ['C1', 'I', 'B', 'V', 'F', 'S']; // Specified character set
           let text = '';
           const numChars = Math.floor(Math.random() * 25) + 5;
           for (let i = 0; i < numChars; i++) {
               const char = chars[Math.floor(Math.random() * chars.length)];
               const opacity = Math.random() * 0.7 + 0.3;
               const color = colors[Math.floor(Math.random() * colors.length)];
               text += `<span class="char" style="opacity: ${opacity}; color: ${color}; text-shadow: 0 0 10px ${color}, 0 0 20px ${color};">${char}</span><br>`;
           }
           return text;
       }

       for (let i = 0; i < columns; i++) {
           const code = document.createElement('div');
           code.classList.add('code');
           code.style.left = `${i * columnWidth}px`;
           code.style.animationDuration = `${Math.random() * 6.5 + 0.5}s`;
           code.style.animationDelay = `${Math.random() * 5}s`;
           code.innerHTML = generateCode();
           container.appendChild(code);
       }

       const emojis = ['😀', '😂', '😍', '🤔', '😎', '😭', '😡', '🤯', '🥳', '😇'];

       document.addEventListener('mousemove', (e) => {
           const emoji = document.createElement('div');
           emoji.classList.add('emoji');
           emoji.style.left = `${e.pageX}px`;
           emoji.style.top = `${e.pageY}px`;
           emoji.innerText = emojis[Math.floor(Math.random() * emojis.length)];
           document.body.appendChild(emoji);

           setTimeout(() => {
               emoji.remove();
           }, 1000);
       });
   </script>
</body>
</html>
