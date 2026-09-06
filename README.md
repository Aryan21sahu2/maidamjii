<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Magical Love Adventure 👑❤️</title>
    <!-- Canvas Confetti & FontAwesome -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Fredoka+One&family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Poppins', sans-serif;
            user-select: none;
        }

        body {
            background: radial-gradient(circle at center, #ff0844 0%, #ffb199 40%, #2e0854 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
            position: relative;
            padding: 15px;
        }

        /* Floating Background Particles */
        .bg-particle {
            position: fixed;
            top: -10vh;
            color: rgba(255, 255, 255, 0.7);
            animation: floatDown linear infinite;
            z-index: 0;
            pointer-events: none;
            filter: drop-shadow(0 0 10px rgba(255,255,255,0.8));
        }

        @keyframes floatDown {
            0% { transform: translateY(0) rotate(0deg) scale(0.6); opacity: 1; }
            100% { transform: translateY(110vh) rotate(360deg) scale(1.3); opacity: 0; }
        }

        /* Glassmorphic Main Card */
        .card-stage {
            background: rgba(255, 255, 255, 0.12);
            backdrop-filter: blur(25px);
            -webkit-backdrop-filter: blur(25px);
            border: 2px solid rgba(255, 255, 255, 0.3);
            border-radius: 30px;
            padding: 35px 25px;
            width: 100%;
            max-width: 650px;
            text-align: center;
            color: white;
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.6);
            z-index: 10;
            display: none;
            animation: cardIn 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
        }

        .active-stage { display: block; }

        @keyframes cardIn {
            from { opacity: 0; transform: scale(0.8) translateY(30px); }
            to { opacity: 1; transform: scale(1) translateY(0); }
        }

        h1, h2 {
            font-family: 'Dancing Script', cursive;
            font-size: 42px;
            margin-bottom: 10px;
            color: #ffeaa7;
            text-shadow: 0 0 20px rgba(255, 0, 127, 0.8);
        }

        p.subtitle { font-size: 14px; opacity: 0.95; margin-bottom: 25px; line-height: 1.6; }

        /* Fancy Inputs & Buttons */
        .custom-input {
            width: 100%;
            padding: 15px;
            border-radius: 20px;
            border: 2px solid rgba(255, 255, 255, 0.5);
            background: rgba(255, 255, 255, 0.9);
            color: #333;
            font-size: 16px;
            outline: none;
            margin-bottom: 15px;
            box-shadow: inset 0 3px 6px rgba(0,0,0,0.1);
            transition: 0.3s;
        }

        .btn-glow {
            background: linear-gradient(45deg, #ff007f, #7928ca);
            color: white;
            border: none;
            padding: 16px 35px;
            font-size: 18px;
            font-weight: bold;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 0 25px rgba(255, 0, 127, 0.8);
            transition: all 0.3s ease;
            width: 100%;
            margin-top: 10px;
        }

        .btn-glow:hover {
            transform: scale(1.03);
            box-shadow: 0 0 35px rgba(255, 0, 127, 1);
        }

        /* Balloon Minigame */
        .balloon-field {
            position: relative;
            height: 250px;
            background: rgba(0,0,0,0.2);
            border-radius: 20px;
            overflow: hidden;
            margin: 20px 0;
            border: 2px dashed rgba(255,255,255,0.4);
        }

        .pop-balloon {
            position: absolute;
            font-size: 45px;
            cursor: pointer;
            animation: balloonFly 4s linear infinite;
        }

        @keyframes balloonFly {
            0% { bottom: -60px; }
            100% { bottom: 270px; }
        }

        /* Candle & Cake Effect */
        .candle-flame {
            font-size: 35px;
            display: inline-block;
            animation: flameFlicker 0.3s infinite alternate;
        }

        @keyframes flameFlicker {
            0% { transform: scale(1) rotate(-5deg); filter: drop-shadow(0 0 10px #ff0); }
            100% { transform: scale(1.3) rotate(5deg); filter: drop-shadow(0 0 20px #f00); }
        }

        /* Scratch Card Box */
        .scratch-card {
            background: #ffeaa7;
            color: #d63384;
            padding: 25px;
            border-radius: 20px;
            font-size: 20px;
            font-weight: bold;
            margin: 20px 0;
            cursor: pointer;
            border: 3px dashed #ff007f;
            transition: 0.4s;
        }

        /* Love Coupons */
        .coupon-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
            gap: 15px;
            margin: 20px 0;
        }

        .coupon-box {
            background: rgba(255,255,255,0.2);
            border: 1px solid rgba(255,255,255,0.4);
            padding: 15px;
            border-radius: 18px;
            cursor: pointer;
            transition: 0.3s;
        }

        .coupon-box:hover { background: rgba(255,255,255,0.4); transform: translateY(-5deg); }

        /* Polaroid Wall */
        .polaroid-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }

        .polaroid {
            background: white;
            padding: 8px 8px 18px 8px;
            border-radius: 8px;
            color: #333;
            box-shadow: 0 10px 20px rgba(0,0,0,0.3);
            transform: rotate(-3deg);
        }

        .polaroid img { width: 100%; height: 110px; object-fit: cover; border-radius: 4px; }
        .polaroid p { font-size: 11px; margin-top: 6px; font-weight: bold; }

        /* Floating Sound Control */
        .audio-btn {
            position: fixed;
            top: 20px;
            right: 20px;
            background: rgba(255, 255, 255, 0.9);
            color: #ff007f;
            border: none;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            cursor: pointer;
            box-shadow: 0 0 20px rgba(255, 0, 127, 0.6);
            z-index: 100;
            font-size: 20px;
        }
    </style>
</head>
<body>

    <!-- Background Particle Engine -->
    <div id="particle-container"></div>

    <!-- Background Romantic Song -->
    <audio id="bg-music" loop preload="auto">
        <source src="https://assets.mixkit.co/music/preview/mixkit-romantic-piano-wedding-399.mp3" type="audio/mpeg">
    </audio>

    <button class="audio-btn" onclick="toggleMusic()" title="Play/Pause Romantic Song">
        <i id="music-icon" class="fas fa-music"></i>
    </button>

    <!-- STAGE 1: MAGICAL GATEWAY -->
    <div class="card-stage active-stage" id="stage-1">
        <h1>👑 Welcome My Queen 👑</h1>
        <p class="subtitle">Enter your name & your Fav person name to launch your personalized interactive birthday realm!</p>

        <input type="text" id="gf-name" class="custom-input" placeholder="Your Gorgeous Name 👸" required>
        <input type="text" id="bf-name" class="custom-input" placeholder="Your Loving 's Name 🤴" required>

        <button class="btn-glow" onclick="startAdventure()">Launch Surprise Adventure ✨</button>
    </div>

    <!-- STAGE 2: BALLOON POPPING GAME -->
    <div class="card-stage" id="stage-2">
        <h2>Level 1: Pop 5 Birthday Balloons 🎈</h2>
        <p class="subtitle">Tap on the flying balloons to pop them! Pops Left: <b id="pops-left" style="color: #ffeaa7; font-size: 18px;">5</b></p>

        <div class="balloon-field" id="balloon-field">
            <!-- Dynamic Balloons Spawn Here -->
        </div>
    </div>

    <!-- STAGE 3: LOVE METER CALCULATOR -->
    <div class="card-stage" id="stage-3">
        <h2>Level 2: Love Compatibility Test 💖</h2>
        <p class="subtitle">Testing love percentage between <b id="test-gf"></b> & <b id="test-bf"></b>...</p>

        <div style="font-size: 70px; margin: 20px 0;" id="heart-pulse">💖</div>
        <h3 id="love-percent" style="font-size: 36px; color: #ffeaa7;">0%</h3>

        <button class="btn-glow" id="calc-btn" onclick="runLoveMeter()">Calculate Eternal Love ⚡</button>
    </div>

    <!-- STAGE 4: CANDLE BLOW & CAKE CUT -->
    <div class="card-stage" id="stage-4">
        <h2>Level 3: Blow Candle & Cut Cake 🕯️</h2>
        <p class="subtitle">Close your eyes, make a sweet wish, and TAP the flame to blow it out!</p>

        <div style="margin: 25px 0; cursor: pointer;" onclick="blowCandle()">
            <div id="candle-flame" class="candle-flame">🔥</div>
            <div style="font-size: 40px; margin-top: -10px;">🕯️</div>
            <div id="cake-emoji" style="font-size: 85px; margin-top: -15px;">🎂</div>
        </div>

        <p id="cake-status" style="font-weight: bold; color: #ffeaa7;">👉 TAP THE FLAME TO BLOW! 👈</p>
    </div>

    <!-- STAGE 5: SCRATCH CARD WISHER -->
    <div class="card-stage" id="stage-5">
        <h2>Level 4: Secret Scratch Voucher 🎟️</h2>
        <p class="subtitle">Tap below to scratch and reveal your secret birthday gift from <b class="bf-tag"></b>!</p>

        <div class="scratch-card" id="scratch-box" onclick="scratchVoucher()">
            ❓ TAP TO SCRATCH YOUR SURPRISE VOUCHER ❓
        </div>

        <button class="btn-glow" id="next-to-grand" style="display:none;" onclick="showGrandDashboard()">Enter Grand Gallery 💖</button>
    </div>

    <!-- STAGE 6: GRAND DASHBOARD & POLAROID MEMORIES -->
    <div class="card-stage" id="stage-6">
        <h1 style="font-size: 38px;">🎉 Happy Birthday <span id="final-gf" style="color: #ffeaa7;"></span>! 🎉</h1>
        <p class="subtitle">
            You are the absolute best thing that ever happened to me! Forever yours, <b id="final-bf" style="color: #ffeaa7;"></b> ❤️
        </p>

        <!-- Interactive Love Coupons -->
        <h3 style="color: #ffeaa7; text-align: left; margin-top: 15px;">🎟️ Your Birthday Coupons:</h3>
        <div class="coupon-grid">
            <div class="coupon-box" onclick="claimCoupon(this, '🕯️ Romantic Candle Light Dinner Date!')">
                <div style="font-size: 28px;">🍕</div>
                <p style="font-size: 11px; margin-top: 5px;">Tap to Unlock</p>
            </div>
            <div class="coupon-box" onclick="claimCoupon(this, '🤗 Unlimited Warm Hugs & Kisses!')">
                <div style="font-size: 28px;">🧸</div>
                <p style="font-size: 11px; margin-top: 5px;">Tap to Unlock</p>
            </div>
            <div class="coupon-box" onclick="claimCoupon(this, '🎬 Late Night Movie & Ice Cream!')">
                <div style="font-size: 28px;">🍿</div>
                <p style="font-size: 11px; margin-top: 5px;">Tap to Unlock</p>
            </div>
        </div>

        <!-- Polaroid Wall -->
        <div style="text-align: left; margin-top: 25px;">
            <h3 style="color: #ffeaa7; font-size: 18px;">📸 Memory Polaroid Album</h3>
            
            <input type="file" id="img-picker" accept="image/*" style="display:none" onchange="uploadPhoto(event)">
            <button class="btn-glow" style="padding: 10px 20px; font-size: 14px; width: auto; margin-top: 10px;" onclick="document.getElementById('img-picker').click()">
                <i class="fas fa-camera"></i> Add Memory Photo
            </button>

            <div class="polaroid-grid" id="polaroid-grid">
                <div class="polaroid">
                    <img src="https://images.unsplash.com/photo-1518199266791-5375a83190b7?w=500" alt="Love">
                    <p>Forever Together ❤️</p>
                </div>
                <div class="polaroid">
                    <img src="https://images.unsplash.com/photo-1513151233558-d860c5398176?w=500" alt="Party">
                    <p>Best Birthday Ever 🥳</p>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Floating Particle Engine
        function generateParticles() {
            const container = document.getElementById('particle-container');
            const p = document.createElement('div');
            p.className = 'bg-particle';
            p.innerHTML = ['❤️', '💖', '✨', '🎈', '👑', '🌸', '🎁'][Math.floor(Math.random() * 7)];
            p.style.left = Math.random() * 100 + 'vw';
            p.style.animationDuration = Math.random() * 3 + 3 + 's';
            p.style.fontSize = Math.random() * 15 + 16 + 'px';
            container.appendChild(p);
            setTimeout(() => p.remove(), 6000);
        }
        setInterval(generateParticles, 250);

        // Music Control
        const audio = document.getElementById('bg-music');
        let isPlaying = false;

        function toggleMusic() {
            const icon = document.getElementById('music-icon');
            if (isPlaying) {
                audio.pause();
                icon.className = 'fas fa-music';
            } else {
                audio.play();
                icon.className = 'fas fa-pause';
            }
            isPlaying = !isPlaying;
        }

        // Global Variables
        let gf = "", bf = "";
        let popsNeeded = 5;

        function showStage(stageId) {
            document.querySelectorAll('.card-stage').forEach(s => s.classList.remove('active-stage'));
            document.getElementById(stageId).classList.add('active-stage');
        }

        // Stage 1: Entry
        function startAdventure() {
            gf = document.getElementById('gf-name').value || "Princess";
            bf = document.getElementById('bf-name').value || "Your Boyfriend";

            document.getElementById('test-gf').innerText = gf;
            document.getElementById('test-bf').innerText = bf;
            document.getElementById('final-gf').innerText = gf;
            document.getElementById('final-bf').innerText = bf;
            document.querySelectorAll('.bf-tag').forEach(el => el.innerText = bf);

            audio.play().catch(() => {});
            isPlaying = true;
            document.getElementById('music-icon').className = 'fas fa-pause';

            showStage('stage-2');
            spawnBalloons();
        }

        // Stage 2: Balloon Game
        function spawnBalloons() {
            const field = document.getElementById('balloon-field');
            field.innerHTML = '';
            for(let i=0; i<8; i++) {
                const b = document.createElement('div');
                b.className = 'pop-balloon';
                b.innerHTML = ['🎈', '💖', '🎁', '🎂'][Math.floor(Math.random() * 4)];
                b.style.left = (i * 12 + 5) + '%';
                b.style.animationDelay = (Math.random() * 2) + 's';
                b.onclick = function() {
                    this.remove();
                    popsNeeded--;
                    document.getElementById('pops-left').innerText = popsNeeded;
                    triggerConfetti();
                    if(popsNeeded <= 0) {
                        alert("🎉 Balloon Challenge Completed! Proceeding to Love Meter!");
                        showStage('stage-3');
                    }
                };
                field.appendChild(b);
            }
        }

        // Stage 3: Love Meter
        function runLoveMeter() {
            const btn = document.getElementById('calc-btn');
            btn.disabled = true;
            let current = 0;
            const timer = setInterval(() => {
                current += 5;
                document.getElementById('love-percent').innerText = current + '%';
                if(current >= 1000) {
                    clearInterval(timer);
                    document.getElementById('love-percent').innerText = "1000% ETERNAL LOVE! ❤️";
                    triggerFireworks();
                    setTimeout(() => showStage('stage-4'), 2000);
                }
            }, 30);
        }

        // Stage 4: Candle Blow
        function blowCandle() {
            document.getElementById('candle-flame').style.display = 'none';
            document.getElementById('cake-emoji').innerText = '🍰';
            document.getElementById('cake-status').innerText = '🎉 YAAAAY! Cake Cut Successfully!';
            triggerFireworks();

            setTimeout(() => showStage('stage-5'), 2000);
        }

        // Stage 5: Scratch Card
        function scratchVoucher() {
            const box = document.getElementById('scratch-box');
            box.style.background = '#ffffff';
            box.style.color = '#ff007f';
            box.innerHTML = `🎁 VIP BIRTHDAY PASS: Unlimited Shopping & Endless Love from ${bf}! ❤️`;
            triggerFireworks();
            document.getElementById('next-to-grand').style.display = 'block';
        }

        function showGrandDashboard() {
            showStage('stage-6');
            triggerFireworks();
        }

        // Coupons Claim
        function claimCoupon(box, text) {
            box.innerHTML = `<b style="font-size:12px; color:#ffeaa7;">${text}</b>`;
            triggerConfetti();
        }

        // Photo Upload
        function uploadPhoto(e) {
            const file = e.target.files[0];
            if(file) {
                const reader = new FileReader();
                reader.onload = function(evt) {
                    const caption = prompt("Enter a sweet caption for this photo:", "Precious Moment ❤️");
                    const grid = document.getElementById('polaroid-grid');
                    const card = document.createElement('div');
                    card.className = 'polaroid';
                    card.innerHTML = `
                        <img src="${evt.target.result}" alt="Memory">
                        <p>${caption || "Sweet Memory ❤️"}</p>
                    `;
                    grid.prepend(card);
                };
                reader.readAsDataURL(file);
            }
        }

        // Confetti Engine
        function triggerConfetti() {
            confetti({ particleCount: 40, spread: 60, origin: { y: 0.7 } });
        }

        function triggerFireworks() {
            confetti({ particleCount: 150, spread: 100, origin: { y: 0.5 } });
        }
    </script>
</body>
</html>
