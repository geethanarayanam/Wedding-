<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bhavani & Manoj Wedding</title>
    <style>
        :root {
            --gold: #D4AF37;
            --maroon: #800000;
            --cream: #FFFDD0;
        }

        body, html {
            margin: 0;
            padding: 0;
            font-family: 'Georgia', serif;
            background-color: var(--cream);
            color: var(--maroon);
            scroll-behavior: smooth;
            overflow-x: hidden;
        }

        section {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 20px;
            position: relative;
        }

        /* --- Page 1: Addutera Curtain --- */
        #curtain-page {
            background: #111;
            overflow: hidden;
        }

        .curtain-wrapper {
            position: absolute;
            width: 100%;
            height: 100%;
            display: flex;
            z-index: 10;
        }

        .curtain {
            width: 50%;
            height: 100%;
            background: var(--maroon);
            background-image: 
                repeating-linear-gradient(to right, transparent, transparent 35px, rgba(0,0,0,0.2) 40px),
                url('https://www.transparenttextures.com/patterns/silk.png');
            transition: transform 2.5s cubic-bezier(0.4, 0, 0.2, 1);
            box-shadow: inset 0 0 80px #000;
            border-bottom: 15px solid var(--gold);
        }

        .left-curtain { transform-origin: left; border-right: 4px solid var(--gold); }
        .right-curtain { transform-origin: right; border-left: 4px solid var(--gold); }

        .opened .left-curtain { transform: translateX(-100%); }
        .opened .right-curtain { transform: translateX(100%); }

        /* --- ROUND REVEAL BUTTON --- */
        .round-btn {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            background: radial-gradient(circle, #f3e5ab, #d4af37);
            color: var(--maroon);
            border: 5px double var(--maroon);
            font-weight: bold;
            font-size: 1.2rem;
            cursor: pointer;
            z-index: 20;
            box-shadow: 0 0 20px rgba(212, 175, 55, 0.6), inset 0 0 10px rgba(0,0,0,0.2);
            transition: 0.4s;
            animation: pulse 2s infinite;
            display: flex;
            align-items: center;
            justify-content: center;
            text-transform: uppercase;
        }
        .round-btn:hover { transform: scale(1.1); box-shadow: 0 0 30px var(--gold); }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }

        /* --- CATCHY NAMES BACKGROUND --- */
        .names-bg {
            position: absolute;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: radial-gradient(circle, #fff9e6 20%, #f3e5ab 100%);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 1;
        }

        /* Animated Petal Background Effect */
        .petal {
            position: absolute;
            background: var(--gold);
            border-radius: 100% 0 100% 0;
            opacity: 0.3;
            animation: falling 10s linear infinite;
        }

        @keyframes falling {
            0% { top: -10%; transform: translateX(0) rotate(0); }
            100% { top: 110%; transform: translateX(100px) rotate(360deg); }
        }

        .couple-name {
            font-size: 5rem;
            margin: 20px 0;
            color: var(--maroon);
            text-shadow: 2px 2px 0px var(--gold), 4px 4px 8px rgba(0,0,0,0.1);
            font-family: 'Playfair Display', serif;
        }

        /* Standard Buttons */
        .btn {
            margin: 15px;
            padding: 15px 35px;
            background: var(--maroon);
            color: white;
            border: 2px solid var(--gold);
            cursor: pointer;
            font-size: 1.1rem;
            border-radius: 5px;
            transition: 0.4s;
            text-transform: uppercase;
        }
        .btn:hover { background: var(--gold); color: var(--maroon); }

        .reveal-box {
            font-size: 2.2rem;
            color: var(--gold);
            background: white;
            border: 1px solid var(--gold);
            width: 300px;
            margin: 10px auto;
            padding: 10px;
            border-radius: 10px;
        }

        .hidden { display: none; }
    </style>
</head>
<body>

    <section id="curtain-page">
        <div class="curtain-wrapper" id="curtainWrapper">
            <div class="curtain left-curtain"></div>
            <div class="curtain right-curtain"></div>
        </div>

        <button id="enterBtn" class="round-btn" onclick="openCurtains()">Reveal<br>Names</button>

        <div class="names-bg" id="namesDisplay">
            <h3 style="color: var(--maroon); letter-spacing: 4px;">THE WEDDING CELEBRATION OF</h3>
            <h1 class="couple-name">Bhavani <br>&<br> Manoj</h1>
            <div style="width: 250px; height: 3px; background: var(--gold); margin-bottom: 30px;"></div>
            <button class="btn" onclick="showPage('date-page')">Press for Date Details</button>
        </div>
    </section>

    <section id="date-page" class="hidden">
        <h2>Click to Reveal the Details</h2>
        
        <div class="reveal-box" id="disp-date">---</div>
        <button class="btn" onclick="revealItem('disp-date', 'October 25th')">Reveal Date</button>

        <div class="reveal-box" id="disp-day">---</div>
        <button class="btn" onclick="revealItem('disp-day', 'Sunday')">Reveal Day</button>

        <div class="reveal-box" id="disp-year">---</div>
        <button class="btn" onclick="revealItem('disp-year', '2026')">Reveal Year</button>

        <div id="inviteTrigger" class="hidden">
            <p style="margin-top:40px;">Scroll down for Invitation</p>
            <div style="font-size: 30px;">↓</div>
        </div>
    </section>

    <section id="invite-text">
        <div style="max-width: 600px; border: 15px double var(--gold); padding: 50px; background: white; border-radius: 5px;">
            <h2 style="font-style: italic; color: var(--maroon);">Wedding Invitation</h2>
            <p>Dear Colleagues,</p>
            <p>We invite you to share in our joy as we celebrate our wedding. Your presence would make our celebration truly complete.</p>
            <p>Please join us as we say "I do" and begin our life together.</p>
            <p>Warm Regards,<br><strong>Bhavani & Manoj</strong></p>
        </div>
        <button class="btn" onclick="showPage('venue-page')">Venue Location</button>
    </section>

    <section id="venue-page" class="hidden">
        <div style="font-size: 100px;">🏛️</div>
        <h2>The Venue</h2>
        <p style="font-size: 2rem; margin: 5px 0;"><strong>Swathi Function Hall</strong></p>
        <p>Ongole, Andhra Pradesh</p>
        <button class="btn" onclick="showPage('lunch-page')">Lunch Details</button>
    </section>

    <section id="lunch-page" class="hidden">
        <h1 style="color: var(--gold);">Grand Wedding Lunch</h1>
        <div style="font-size: 1.6rem; padding: 40px; border: 2px solid var(--gold); background: white;">
            <p>Join us for the feast at</p>
            <p><strong style="font-size: 2.5rem;">12:30 PM</strong></p>
            <p>Sunday | At the Venue</p>
        </div>
        <button class="btn" onclick="showPage('final-page')">Final Message</button>
    </section>

    <section id="final-page" class="hidden">
        <h1 style="color: var(--gold); font-size: 4rem;">Thank You!</h1>
        <p style="font-size: 1.6rem; max-width: 600px;">Thanks to all the guests. <br><strong>Your presence is precious to us.</strong></p>
    </section>

    <script>
        let counter = 0;

        // Create decorative petals for the names background
        const namesBg = document.getElementById('namesDisplay');
        for (let i = 0; i < 15; i++) {
            const petal = document.createElement('div');
            petal.className = 'petal';
            petal.style.left = Math.random() * 100 + '%';
            petal.style.width = Math.random() * 20 + 10 + 'px';
            petal.style.height = petal.style.width;
            petal.style.animationDelay = Math.random() * 5 + 's';
            namesBg.appendChild(petal);
        }

        function openCurtains() {
            document.getElementById('enterBtn').style.display = 'none';
            document.getElementById('curtainWrapper').classList.add('opened');
        }

        function showPage(pageId) {
            const page = document.getElementById(pageId);
            page.classList.remove('hidden');
            page.scrollIntoView({ behavior: 'smooth' });
        }

        function revealItem(id, value) {
            const display = document.getElementById(id);
            if (display.innerText === "---") {
                display.innerText = value;
                counter++;
            }
            if (counter >= 3) {
                document.getElementById('inviteTrigger').classList.remove('hidden');
            }
        }
    </script>
</body>
</html>
