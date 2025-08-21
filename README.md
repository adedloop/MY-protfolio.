# MY-protfolio

#HTML
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>My Portfolio</title>
  <link rel="stylesheet" href="styles.css" />
  <style>*{cursor:none;}</style>
</head>
<body>
  <!-- Particle Canvas -->
  <canvas id="bgCanvas"></canvas>

  <!-- Intro Section -->
  <div class="intro-section">
    <h1 id="typewriter"></h1>
    <ul class="self-intro">
      <li>◦•●◉✿sʜɪᴠɪ✿◉●•◦
        <li>An average commerce student</li>
      <li>Not very talkative, but a good gamer</li>
      <li>Slim and simple in appearance</li>
      <li>Under 20, full of curiosity and learning spirit</li>
      <li>My heart is already committed elsewhere</li>
      <li>gmail id = adedloop1452008@gmail.com</li>
      <li>universal gamig id = _adedloop<li>
       <li>UP - Lucknow---
    </ul>
  </div>

  <!-- Custom Cursor -->
  <div class="cursor"></div>

  <!-- Sound Effect -->
  <audio id="clickSound" src="click.mp3" preload="auto"></audio>

  <!-- Scripts -->
  <script src="scripts.js"></script>
  <script>
    document.querySelectorAll('li, h1').forEach(el => {
      el.addEventListener('click', () => {
        document.getElementById('clickSound').play();
      });
    });
  </script>


#CSS 

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  cursor: none;
}

body {
  font-family: 'Segoe UI', sans-serif;
  background: linear-gradient(135deg, #1f1c2c, #928dab);
  color: #fff;
  overflow-x: hidden;
}

canvas {
  position: fixed;
  top: 0;
  left: 0;
  z-index: -1;
}

.intro-section {
  padding: 60px 20px;
  text-align: center;
  animation: fadeIn 2s ease-in-out;
}

h1 {
  font-size: 3em;
  animation: glow 1.5s ease-in-out infinite alternate;
}

.self-intro {
  margin-top: 30px;
  max-width: 600px;
  margin-inline: auto;
  background: rgba(255, 255, 255, 0.1);
  padding: 30px;
  border-radius: 15px;
  box-shadow: 0 0 30px rgba(0,0,0,0.5);
  animation: slideUp 2s ease-out;
  list-style: none;
  text-align: left;
}

.self-intro li {
  margin-bottom: 15px;
  font-size: 1.2em;
  position: relative;
  padding-left: 25px;
}

.self-intro li::before {
  content: '➤';
  position: absolute;
  left: 0;
  color: #00ffe7;
  animation: bounce 1s infinite alternate;
}

.cursor {
  width: 20px;
  height: 20px;
  border: 2px solid #00ffe7;
  border-radius: 50%;
  position: fixed;
  pointer-events: none;
  z-index: 9999;
  transform: translate(-50%, -50%);
  box-shadow: 0 0 10px #00ffe7;
  transition: transform 0.1s ease;
}

/* Animations */
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes slideUp {
  from { transform: translateY(40px); opacity: 0; }
  to { transform: translateY(0); opacity: 1; }
}

@keyframes bounce {
  from { transform: translateY(0); }
  to { transform: translateY(-5px); }
}

@keyframes glow {
  from { text-shadow: 0 0 10px #00ffe7, 0 0 20px #00ffe7; }
  to { text-shadow: 0 0 20px #00ffff, 0 0 40px #00ffff; }
}


#JAVA

// ✨ Typewriter Effect
const text = "Hello, I'm Me";
const typeTarget = document.getElementById('typewriter');
let i = 0;
function typeWriter() {
  if (i < text.length) {
    typeTarget.innerHTML += text.charAt(i);
    i++;
    setTimeout(typeWriter, 100);
  }
}
window.onload = typeWriter;

// 🖱️ Custom Cursor Follower
const cursor = document.querySelector('.cursor');
document.addEventListener('mousemove', e => {
  cursor.style.left = e.clientX + 'px';
  cursor.style.top = e.clientY + 'px';
});

// 🌌 Particle Background
const canvas = document.getElementById('bgCanvas');
const ctx = canvas.getContext('2d');

function resizeCanvas() {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
}
window.addEventListener('resize', resizeCanvas);
resizeCanvas();

let particles = [];
for (let i = 0; i < 120; i++) {
  particles.push({
    x: Math.random() * canvas.width,
    y: Math.random() * canvas.height,
    radius: Math.random() * 2 + 1,
    speedX: (Math.random() - 0.5),
    speedY: (Math.random() - 0.5)
  });
}

function animateParticles() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  particles.forEach(p => {
    ctx.beginPath();
    ctx.arc(p.x, p.y, p.radius, 0, Math.PI * 2);
    ctx.fillStyle = '#00ffe7';
    ctx.fill();
    p.x += p.speedX;
    p.y += p.speedY;
    if (p.x < 0 || p.x > canvas.width) p.speedX *= -1;
    if (p.y < 0 || p.y > canvas.height) p.speedY *= -1;
  });
  requestAnimationFrame(animateParticles);
}
animateParticles();

</body>
</html>
