<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For Aina Shehzadi | A Journey of Love</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&family=Dancing+Script:wght@700&display=swap');

        :root {
            --bg: #050507;
            --primary: #ff2d75;
            --secondary: #7000ff;
            --accent: #00f2ff;
            --text: #ffffff;
            --glass: rgba(255, 255, 255, 0.03);
            --glass-border: rgba(255, 255, 255, 0.1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            cursor: default;
        }

        body {
            background-color: var(--bg);
            color: var(--text);
            font-family: 'Inter', sans-serif;
            overflow: hidden;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* --- Animated Background --- */
        #canvas-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: radial-gradient(circle at center, #1a1025 0%, #050507 100%);
        }

        /* --- Layout --- */
        .container {
            width: 90%;
            max-width: 600px;
            z-index: 10;
            text-align: center;
        }

        section {
            display: none;
            opacity: 0;
            transform: translateY(20px) scale(0.98);
            transition: all 0.8s cubic-bezier(0.4, 0, 0.2, 1);
        }

        section.active {
            display: block;
            opacity: 1;
            transform: translateY(0) scale(1);
        }

        /* --- Components --- */
        .glass-card {
            background: var(--glass);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid var(--glass-border);
            border-radius: 32px;
            padding: 3rem 2rem;
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.5);
            position: relative;
            overflow: hidden;
        }

        .heart-glow {
            font-size: 4rem;
            margin-bottom: 1.5rem;
            filter: drop-shadow(0 0 15px var(--primary));
            animation: heartBeat 1.5s infinite ease-in-out;
            display: inline-block;
        }

        h1 {
            font-size: 2.5rem;
            font-weight: 800;
            margin-bottom: 1rem;
            background: linear-gradient(to right, var(--primary), var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            letter-spacing: -1px;
        }

        .script-font {
            font-family: 'Dancing Script', cursive;
            font-size: 2.2rem;
            color: var(--primary);
            margin-bottom: 1rem;
        }

        p {
            line-height: 1.8;
            color: rgba(255, 255, 255, 0.8);
            font-size: 1.1rem;
            margin-bottom: 2rem;
        }

        .typewriter-text {
            min-height: 150px;
            text-align: left;
            font-weight: 300;
            border-left: 2px solid var(--primary);
            padding-left: 1.5rem;
            margin: 2rem 0;
        }

        /* --- Buttons --- */
        .btn-group {
            display: flex;
            gap: 1.5rem;
            justify-content: center;
            align-items: center;
            margin-top: 2rem;
            flex-wrap: wrap;
        }

        .btn {
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            color: white;
            border: none;
            padding: 1rem 2.5rem;
            border-radius: 50px;
            font-size: 1rem;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 2px;
            transition: all 0.3s ease;
            box-shadow: 0 10px 20px rgba(255, 45, 117, 0.3);
            cursor: pointer;
        }

        .btn:hover {
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 15px 30px rgba(255, 45, 117, 0.5);
        }

        .btn-reject {
            background: transparent;
            border: 1px solid var(--glass-border);
            color: rgba(255,255,255,0.6);
            transition: none; /* Instant movement */
            position: relative;
        }

        /* --- Success State --- */
        #success-screen h1 {
            background: linear-gradient(to right, #00f2ff, #7000ff);
            -webkit-background-clip: text;
        }

        /* --- Animations --- */
        @keyframes heartBeat {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.2); }
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        .floating { animation: float 3s ease-in-out infinite; }

        @media (max-width: 480px) {
            h1 { font-size: 1.8rem; }
            .glass-card { padding: 2rem 1.5rem; }
            .btn { width: 100%; }
            .btn-group { flex-direction: column; }
        }
    </style>
</head>
<body>

    <canvas id="canvas-bg"></canvas>

    <div class="container">
        
        <!-- Welcome -->
        <section id="step1" class="active">
            <div class="glass-card">
                <div class="heart-glow">✨</div>
                <h1>For Aina Shehzadi</h1>
                <p>A message from Zia Ullah. A story of a heart that found its home.</p>
                <button class="btn" onclick="nextStep(2)">Open the Story</button>
            </div>
        </section>

        <!-- Message Part 1 -->
        <section id="step2">
            <div class="glass-card">
                <div class="script-font">Dearest Aina,</div>
                <div class="typewriter-text" id="type1"></div>
                <button class="btn" id="btn2" style="display:none" onclick="nextStep(3)">Next</button>
            </div>
        </section>

        <!-- Message Part 2 -->
        <section id="step3">
            <div class="glass-card">
                <div class="typewriter-text" id="type2"></div>
                <button class="btn" id="btn3" style="display:none" onclick="nextStep(4)">Continue</button>
            </div>
        </section>

        <!-- Proposal Screen -->
        <section id="step4">
            <div class="glass-card">
                <div class="heart-glow">💍</div>
                <h1>Aina Shehzadi,</h1>
                <p style="font-style: italic;">
                    "So today, with all my heart… I choose you. I respect you. I love you."
                </p>
                <h2 style="margin-bottom: 2rem; font-weight: 300;">Will you be mine forever?</h2>
                
                <div class="btn-group">
                    <button class="btn" onclick="celebrate()">✅ Accept</button>
                    <button class="btn btn-reject" id="reject-btn" onmouseover="moveReject()" onclick="moveReject()">❌ Reject</button>
                </div>
            </div>
        </section>

        <!-- Success Screen -->
        <section id="success-screen">
            <div class="glass-card">
                <div class="heart-glow">♾️</div>
                <h1>She said YES ❤️</h1>
                <p>Proposal Accepted. Zia & Aina — Forever starts now.</p>
                <div style="font-family: 'Dancing Script'; font-size: 1.5rem; color: var(--accent);">
                    The best is yet to come.
                </div>
            </div>
        </section>

    </div>

    <script>
        // --- Particle Background ---
        const canvas = document.getElementById('canvas-bg');
        const ctx = canvas.getContext('2d');
        let particles = [];

        function initCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }

        class Particle {
            constructor() {
                this.reset();
            }
            reset() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.size = Math.random() * 2 + 0.5;
                this.speedX = Math.random() * 0.5 - 0.25;
                this.speedY = Math.random() * 0.5 - 0.25;
                this.color = Math.random() > 0.5 ? '#ff2d75' : '#7000ff';
                this.opacity = Math.random();
            }
            update() {
                this.x += this.speedX;
                this.y += this.speedY;
                if (this.x > canvas.width || this.x < 0 || this.y > canvas.height || this.y < 0) this.reset();
            }
            draw() {
                ctx.globalAlpha = this.opacity;
                ctx.fillStyle = this.color;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
            }
        }

        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particles.forEach(p => { p.update(); p.draw(); });
            requestAnimationFrame(animate);
        }

        initCanvas();
        for(let i=0; i<100; i++) particles.push(new Particle());
        animate();
        window.addEventListener('resize', initCanvas);

        // --- Navigation & Typewriter ---
        const text1 = "From the moment you came into my life, everything started to feel right. You are not just a part of my story — you are the reason it has meaning.\n\nYour smile is my peace. Your voice is my comfort. Your presence is my happiness.";
        const text2 = "I don’t promise a perfect life, but I promise a loyal heart, honest love, and a hand that will never let go.\n\nYou are the dream I never want to wake up from. You are the prayer I didn’t know I was making.";

        function nextStep(num) {
            document.querySelectorAll('section').forEach(s => s.classList.remove('active'));
            setTimeout(() => {
                document.querySelectorAll('section').forEach(s => s.style.display = 'none');
                const next = document.getElementById(`step${num}`);
                next.style.display = 'block';
                setTimeout(() => next.classList.add('active'), 50);
                
                if(num === 2) typeWriter(text1, 'type1', 'btn2');
                if(num === 3) typeWriter(text2, 'type2', 'btn3');
            }, 600);
        }

        function typeWriter(text, elementId, btnId) {
            let i = 0;
            const target = document.getElementById(elementId);
            target.innerHTML = "";
            function type() {
                if (i < text.length) {
                    target.innerHTML += text.charAt(i);
                    i++;
                    setTimeout(type, 30);
                } else {
                    document.getElementById(btnId).style.display = 'inline-block';
                    document.getElementById(btnId).style.animation = 'fadeIn 0.5s forwards';
                }
            }
            type();
        }

        // --- Reject Button Logic ---
        function moveReject() {
            const btn = document.getElementById('reject-btn');
            // Ensure button doesn't move off screen
            const maxX = window.innerWidth - btn.offsetWidth - 20;
            const maxY = window.innerHeight - btn.offsetHeight - 20;
            
            const randomX = Math.max(20, Math.floor(Math.random() * maxX));
            const randomY = Math.max(20, Math.floor(Math.random() * maxY));
            
            btn.style.position = 'fixed';
            btn.style.left = randomX + 'px';
            btn.style.top = randomY + 'px';
            btn.style.zIndex = '1000';
        }

        // --- Success Celebration ---
        function celebrate() {
            // Switch screen
            document.querySelectorAll('section').forEach(s => s.classList.remove('active'));
            setTimeout(() => {
                document.querySelectorAll('section').forEach(s => s.style.display = 'none');
                const finish = document.getElementById('success-screen');
                finish.style.display = 'block';
                setTimeout(() => finish.classList.add('active'), 50);
            }, 600);

            // Boost particles
            for(let i=0; i<150; i++) {
                let p = new Particle();
                p.speedX *= 10;
                p.speedY *= 10;
                p.size *= 3;
                p.opacity = 1;
                particles.push(p);
            }
        }
    </script>
</body>
</html>
