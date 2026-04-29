<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>🎉 Happy Birthday Vaishali 🎉</title>

<style>
body {
    margin: 0;
    font-family: 'Segoe UI', sans-serif;
    text-align: center;
    background: linear-gradient(270deg, #ff9a9e, #fad0c4, #fbc2eb);
    background-size: 600% 600%;
    animation: gradientBG 10s ease infinite;
    overflow: hidden;
}

@keyframes gradientBG {
    0% {background-position: 0% 50%;}
    50% {background-position: 100% 50%;}
    100% {background-position: 0% 50%;}
}

h1 {
    margin-top: 50px;
    font-size: 3em;
    color: white;
}

button {
    padding: 15px 30px;
    font-size: 18px;
    border: none;
    border-radius: 25px;
    background: #ff4081;
    color: white;
    cursor: pointer;
}

button:hover {
    background: #e91e63;
}

#message {
    margin-top: 30px;
    font-size: 1.6em;
    color: white;
    width: 80%;
    margin: auto;
}

.cake {
    display: none;
    margin-top: 30px;
    font-size: 90px;
    animation: bounce 1s infinite alternate;
}

@keyframes bounce {
    from { transform: translateY(0px); }
    to { transform: translateY(-15px); }
}

canvas {
    position: fixed;
    top: 0;
    left: 0;
    pointer-events: none;
}
</style>
</head>

<body>

<h1>🎉 Happy Birthday Vaishali 🎉</h1>

<button onclick="startSurprise()">Click for Surprise 🎁</button>

<div id="message"></div>
<div class="cake">🎂🕯️</div>

<audio id="music" loop>
  <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
</audio>

<canvas id="confetti"></canvas>

<script>

// Typing effect
function typeMessage(text, element, speed = 40) {
    let i = 0;
    function typing() {
        if (i < text.length) {
            element.innerHTML += text.charAt(i);
            i++;
            setTimeout(typing, speed);
        }
    }
    typing();
}

function startSurprise() {
    const msg = `
💖 Happy Birthday Vaishali! 💖<br><br>
🎂 May your day be full of cake<br>
🎁 Surprises and happiness<br>
💃 Endless fun and laughter<br><br>
You are truly amazing and special! 🥳<br><br>
✨ Wishing you the best year ever ✨<br><br>
— From Vinay 💖
`;

    const messageBox = document.getElementById("message");
    messageBox.innerHTML = "";
    typeMessage(msg, messageBox);

    document.querySelector(".cake").style.display = "block";
    document.getElementById("music").play();

    startConfetti();
}

// CONFETTI
const canvas = document.getElementById("confetti");
const ctx = canvas.getContext("2d");
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let pieces = [];

for (let i = 0; i < 150; i++) {
    pieces.push({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height,
        size: Math.random() * 8 + 2,
        speed: Math.random() * 3 + 2
    });
}

function startConfetti() {
    function update() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);

        pieces.forEach(p => {
            p.y += p.speed;
            if (p.y > canvas.height) p.y = 0;

            ctx.beginPath();
            ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
            ctx.fillStyle = `hsl(${Math.random()*360},100%,50%)`;
            ctx.fill();
        });

        requestAnimationFrame(update);
    }
    update();
}

</script>

</body>
</html>
