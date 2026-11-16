# For-you-Mei
a little website made with code

<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<meta name="theme-color" content="#09040e">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<title>For Someone Special ♡</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;500&family=Prompt:wght@300;400;500&display=swap');

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html {
    width: 100%;
    min-height: 100%;
    -webkit-text-size-adjust: 100%;
}

body {
    width: 100%;
    min-height: 100vh;
    min-height: 100svh;
    overflow: hidden;
    background: radial-gradient(ellipse at 50% 42%,
        #30102f 0%, #130817 40%, #050308 100%);
    color: white;
    font-family: 'Prompt', sans-serif;
    -webkit-tap-highlight-color: transparent;
}

canvas {
    position: fixed;
    inset: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
}

#stars { z-index: 0; }
#roseCanvas { z-index: 1; }

.container {
    position: relative;
    z-index: 2;
    width: 100%;
    min-height: 100vh;
    min-height: 100svh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 25px 20px;
    padding-top: max(25px, env(safe-area-inset-top));
    padding-bottom: max(35px, env(safe-area-inset-bottom));
}

.rose-area {
    position: relative;
    width: min(85vw, 430px);
    height: min(55vh, 460px);
    min-height: 280px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.glow {
    position: absolute;
    width: 230px;
    height: 230px;
    border-radius: 50%;
    background: #ec3b9d;
    filter: blur(100px);
    opacity: .22;
    animation: breathe 4s ease-in-out infinite;
}

@keyframes breathe {
    0%,100% { transform: scale(.8); opacity: .15; }
    50% { transform: scale(1.25); opacity: .35; }
}

.heading {
    margin-top: -5px;
    animation: appear 2s ease both;
}

.heading h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(30px, 8vw, 55px);
    font-weight: 400;
    letter-spacing: 2px;
    background: linear-gradient(120deg,#fff,#ffb5d9,#e86cb0);
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
}

.heading p {
    margin-top: 12px;
    font-size: 11px;
    letter-spacing: 4px;
    color: #e9b4d0;
    font-weight: 300;
}

.open-btn {
    margin-top: 30px;
    min-height: 48px;
    padding: 13px 30px;
    border: 1px solid #f28abb88;
    border-radius: 50px;
    background: linear-gradient(135deg,#a42c70aa,#55153f88);
    color: white;
    font-family: 'Prompt', sans-serif;
    font-size: 13px;
    letter-spacing: 2px;
    cursor: pointer;
    box-shadow: 0 0 25px #e83e9940;
    transition: .35s;
    touch-action: manipulation;
}

.open-btn:active {
    transform: scale(.96);
    background: #d34491;
}

.footer {
    position: absolute;
    bottom: max(22px, env(safe-area-inset-bottom));
    font-size: 10px;
    letter-spacing: 2px;
    color: #a98ba6;
    opacity: .65;
}

@keyframes appear {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
}

/* Letter */

.overlay {
    position: fixed;
    inset: 0;
    z-index: 10;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 20px;
    padding-top: max(20px, env(safe-area-inset-top));
    padding-bottom: max(20px, env(safe-area-inset-bottom));
    background: #050208d9;
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    opacity: 0;
    visibility: hidden;
    transition: .5s;
}

.overlay.show {
    opacity: 1;
    visibility: visible;
}

.letter {
    width: 100%;
    max-width: 440px;
    max-height: 85svh;
    overflow-y: auto;
    padding: 38px 28px;
    border: 1px solid #e68ab555;
    border-radius: 22px;
    background: linear-gradient(145deg,#271226,#100a16);
    box-shadow: 0 0 60px #e73d8530;
    text-align: center;
    transform: translateY(25px) scale(.95);
    transition: .5s;
    overscroll-behavior: contain;
}

.overlay.show .letter {
    transform: translateY(0) scale(1);
}

.letter h2 {
    font-family: 'Playfair Display',serif;
    font-size: 32px;
    font-weight: 400;
    color: #ffb2d5;
    margin-bottom: 22px;
}

.letter .message {
    font-size: 14px;
    line-height: 2.2;
    color: #f4dce9;
    font-weight: 300;
    white-space: pre-line;
}

.heart {
    display: block;
    margin: 24px auto;
    font-size: 27px;
    color: #ff80b9;
    animation: heartbeat 1.5s infinite;
}

@keyframes heartbeat {
    0%,100% { transform: scale(1); }
    50% { transform: scale(1.2); }
}

.close-btn {
    min-height: 44px;
    padding: 10px 26px;
    border: 1px solid #e88ab566;
    border-radius: 30px;
    color: #ffd5e8;
    background: transparent;
    font-family: 'Prompt',sans-serif;
    font-size: 12px;
    letter-spacing: 2px;
    cursor: pointer;
    touch-action: manipulation;
}

/* Mobile */

@media (max-width: 600px) {
    .container {
        padding-left: 16px;
        padding-right: 16px;
    }

    .rose-area {
        width: 100%;
        height: 46svh;
        min-height: 260px;
        max-height: 400px;
    }

    .heading h1 {
        font-size: clamp(28px, 8vw, 39px);
        letter-spacing: 1px;
    }

    .heading p {
        font-size: 9px;
        letter-spacing: 3px;
    }

    .open-btn {
        margin-top: 25px;
        padding: 14px 25px;
        font-size: 12px;
    }

    .letter {
        padding: 30px 20px;
    }

    .letter h2 {
        font-size: 28px;
    }

    .letter .message {
        font-size: 13px;
        line-height: 2;
    }
}

@media (max-height: 650px) {
    .rose-area {
        height: 38svh;
        min-height: 190px;
    }

    .open-btn {
        margin-top: 15px;
    }
}

@media (prefers-reduced-motion: reduce) {
    *, *::before, *::after {
        animation-duration: .01ms !important;
        transition-duration: .01ms !important;
    }
}
</style>
</head>

<body>

<canvas id="stars"></canvas>
<canvas id="roseCanvas"></canvas>

<main class="container">
    <div class="rose-area">
        <div class="glow"></div>
    </div>

    <div class="heading">
        <h1>For Someone Special</h1>
        <p>YOU MAKE MY WORLD BLOOM</p>
    </div>

    <button class="open-btn" onclick="openMessage()">
        OPEN MY HEART ♡
    </button>

    <div class="footer">
        MADE WITH LOVE · JUST FOR YOU
    </div>
</main>

<div class="overlay" id="message">
    <div class="letter">
        <h2>Dear You ♡</h2>

        <div class="message">มีบางคนที่เข้ามาในชีวิต
แล้วทำให้วันธรรมดา
กลายเป็นวันที่พิเศษขึ้นมา

ขอบคุณที่เข้ามาเป็นรอยยิ้ม
และเป็นความสุขเล็ก ๆ ในทุกวัน

ไม่รู้ว่าอนาคตจะเป็นอย่างไร
แต่ในวันนี้...
ดีใจนะที่ได้รู้จักเธอ

ขอให้ดอกกุหลาบดอกนี้
เป็นตัวแทนความรู้สึกดี ๆ
ที่อยากมอบให้เธอ</div>

        <span class="heart">♡</span>

        <button class="close-btn" onclick="closeMessage()">
            CLOSE ♡
        </button>
    </div>
</div>

<script>
const canvas = document.getElementById("roseCanvas");
const ctx = canvas.getContext("2d");

const starsCanvas = document.getElementById("stars");
const starsCtx = starsCanvas.getContext("2d");

let w, h, cx, cy;
let time = 0;
let stars = [];
let petals = [];

function resize() {
    const dpr = Math.min(window.devicePixelRatio || 1, 2);

    w = window.innerWidth;
    h = window.innerHeight;
    cx = w / 2;
    cy = h * 0.39;

    [canvas, starsCanvas].forEach(c => {
        c.width = w * dpr;
        c.height = h * dpr;
        c.style.width = w + "px";
        c.style.height = h + "px";
    });

    ctx.setTransform(dpr,0,0,dpr,0,0);
    starsCtx.setTransform(dpr,0,0,dpr,0,0);

    createStars();
}

window.addEventListener("resize", resize);

function random(min,max) {
    return Math.random() * (max-min) + min;
}

function createStars() {
    stars = [];

    for(let i=0;i<100;i++) {
        stars.push({
            x:random(0,w),
            y:random(0,h),
            r:random(.4,1.8),
            a:random(.2,.9),
            speed:random(.01,.035)
        });
    }
}

function drawStars() {
    starsCtx.clearRect(0,0,w,h);

    stars.forEach(s => {
        s.a += Math.sin(time*s.speed)*.003;
        s.a = Math.max(.15,Math.min(.9,s.a));

        starsCtx.beginPath();
        starsCtx.arc(s.x,s.y,s.r,0,Math.PI*2);
        starsCtx.fillStyle=`rgba(255,210,238,${s.a})`;
        starsCtx.shadowBlur=10;
        starsCtx.shadowColor="#ff80cc";
        starsCtx.fill();
    });
}

function createPetal() {
    return {
        x:random(0,w),
        y:random(-h,-10),
        size:random(4,9),
        speed:random(.5,1.6),
        rotation:random(0,Math.PI*2),
        swing:random(0,6),
        opacity:random(.3,.8)
    };
}

function drawPetals() {
    if(petals.length<45 && Math.random()<.06) {
        petals.push(createPetal());
    }

    petals.forEach((p,i) => {
        p.y += p.speed;
        p.x += Math.sin(time*.02+p.swing)*.8;
        p.rotation += .012;

        ctx.save();
        ctx.translate(p.x,p.y);
        ctx.rotate(p.rotation);

        ctx.beginPath();
        ctx.ellipse(0,0,p.size*.55,p.size,0,0,Math.PI*2);
        ctx.fillStyle=`rgba(255,105,175,${p.opacity})`;
        ctx.shadowBlur=12;
        ctx.shadowColor="#ff4b9c";
        ctx.fill();

        ctx.restore();

        if(p.y>h+20) {
            petals[i]=createPetal();
        }
    });
}

function drawLeaf(x,y,rotation,size) {
    ctx.save();
    ctx.translate(x,y);
    ctx.rotate(rotation);

    const gradient=ctx.createLinearGradient(0,-size,0,size);
    gradient.addColorStop(0,"#8bd28a");
    gradient.addColorStop(1,"#174c38");

    ctx.beginPath();
    ctx.moveTo(0,0);
    ctx.bezierCurveTo(size*1.1,-size*.9,size*2,-size*.5,size*2.4,0);
    ctx.bezierCurveTo(size*1.5,size*.9,size*.5,size*.5,0,0);

    ctx.fillStyle=gradient;
    ctx.shadowBlur=12;
    ctx.shadowColor="#4fa66b";
    ctx.fill();

    ctx.beginPath();
    ctx.moveTo(0,0);
    ctx.lineTo(size*2.2,0);
    ctx.strokeStyle="#a4e6a0";
    ctx.globalAlpha=.5;
    ctx.lineWidth=.8;
    ctx.stroke();

    ctx.restore();
}

function drawStem(scale) {
    ctx.save();
    ctx.translate(cx,cy);
    ctx.scale(scale,scale);

    const gradient=ctx.createLinearGradient(0,0,0,250);
    gradient.addColorStop(0,"#6cc078");
    gradient.addColorStop(1,"#174a32");

    ctx.beginPath();
    ctx.moveTo(0,35);
    ctx.bezierCurveTo(-7,100,8,160,0,245);

    ctx.strokeStyle=gradient;
    ctx.lineWidth=5;
    ctx.lineCap="round";
    ctx.shadowBlur=12;
    ctx.shadowColor="#58c777";
    ctx.stroke();

    drawLeaf(0,115,-.45,18);
    drawLeaf(0,165,Math.PI+.5,18);

    ctx.restore();
}

function drawRose(scale) {
    ctx.save();
    ctx.translate(cx,cy);
    ctx.scale(scale,scale);

    const pulse=1+Math.sin(time*.035)*.025;
    ctx.scale(pulse,pulse);

    for(let i=0;i<9;i++) {
        const angle=(i/9)*Math.PI*2;

        ctx.save();
        ctx.rotate(angle);

        const gradient=ctx.createLinearGradient(0,-55,0,30);
        gradient.addColorStop(0,"#ff9fcb");
        gradient.addColorStop(.5,"#ec478e");
        gradient.addColorStop(1,"#8d174f");

        ctx.beginPath();
        ctx.ellipse(0,-37,20,39,0,0,Math.PI*2);
        ctx.fillStyle=gradient;
        ctx.shadowBlur=18;
        ctx.shadowColor="#ff3d9d";
        ctx.fill();

        ctx.restore();
    }

    for(let i=0;i<7;i++) {
        const angle=(i/7)*Math.PI*2+.3;

        ctx.save();
        ctx.rotate(angle);

        const gradient=ctx.createLinearGradient(0,-30,0,15);
        gradient.addColorStop(0,"#ffc2df");
        gradient.addColorStop(.6,"#ed5b9e");
        gradient.addColorStop(1,"#9c2059");

        ctx.beginPath();
        ctx.ellipse(0,-20,15,27,0,0,Math.PI*2);
        ctx.fillStyle=gradient;
        ctx.shadowBlur=12;
        ctx.shadowColor="#ff7fbd";
        ctx.fill();

        ctx.restore();
    }

    const centerGradient=ctx.createRadialGradient(-5,-8,2,0,0,18);
    centerGradient.addColorStop(0,"#ffe0ed");
    centerGradient.addColorStop(.45,"#ff8bbd");
    centerGradient.addColorStop(1,"#b32668");

    ctx.beginPath();
    ctx.arc(0,0,17,0,Math.PI*2);
    ctx.fillStyle=centerGradient;
    ctx.shadowBlur=20;
    ctx.shadowColor="#ff7dbd";
    ctx.fill();

    ctx.restore();
}

function drawRoseBud() {
    const scale=Math.min(w/430,h/650,1.15);
    drawStem(scale);
    drawRose(scale);
}

function animate() {
    ctx.clearRect(0,0,w,h);
    time++;

    drawPetals();
    drawRoseBud();
    drawStars();

    requestAnimationFrame(animate);
}

function openMessage() {
    document.getElementById("message").classList.add("show");
}

function closeMessage() {
    document.getElementById("message").classList.remove("show");
}

document.getElementById("message").addEventListener("click",function(e) {
    if(e.target===this) closeMessage();
});

document.addEventListener("keydown",function(e) {
    if(e.key==="Escape") closeMessage();
});

resize();
animate();
</script>

</body>
</html>
