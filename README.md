<!DOCTYPE html>
<html lang="az">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Toy Dəvətnaməsi — Fuad & Sevinc</title>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,400&family=Montserrat:wght@200;300;400;500&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-color: #fdfbf7;
            --card-bg: #ffffff;
            --envelope-color: #f7f2e8;
            --envelope-inner: #efe6d5;
            --gold-gradient: linear-gradient(135deg, #d4af37 0%, #fff3a7 35%, #aa771c 70%, #fbf5b7 100%);
            --gold-solid: #c5a059;
            --gold-soft: rgba(197, 160, 89, 0.25);
            --text-main: #2b2b2b;
            --text-muted: #888888;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            background-color: var(--bg-color);
            font-family: 'Montserrat', sans-serif;
            color: var(--text-main);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }

        /* ULDUZ ANİMASİYASI */
        #stars-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 5;
            overflow: hidden;
        }

        .star {
            position: absolute;
            background: radial-gradient(circle, #fff 10%, #c5a059 80%);
            border-radius: 50%;
            opacity: 0;
            animation: twinkleFall linear infinite;
        }

        @keyframes twinkleFall {
            0% { transform: translateY(-10px) scale(0.3); opacity: 0; }
            30% { opacity: 0.7; }
            70% { opacity: 0.7; }
            100% { transform: translateY(105vh) scale(0.8); opacity: 0; }
        }

        /* 3D LUX ZƏRF WRAPPER */
        #envelope-wrapper {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            perspective: 1500px;
            background: radial-gradient(circle, #ffffff 0%, #f4ede0 100%);
            transition: opacity 1s cubic-bezier(0.4, 0, 0.2, 1) 0.8s, visibility 1s 0.8s;
        }

        #envelope-wrapper.fade-out {
            opacity: 0;
            visibility: hidden;
        }

        /* BÖYÜK ZƏRF */
        .envelope-3d {
            position: relative;
            width: 95vw;
            max-width: 640px;
            height: 420px;
            background: var(--envelope-color);
            border-radius: 16px;
            box-shadow: 0 40px 80px rgba(197, 160, 89, 0.18), 0 15px 35px rgba(0,0,0,0.06);
            border: 1px solid rgba(197, 160, 89, 0.35);
            display: flex;
            justify-content: center;
            align-items: center;
            transform-style: preserve-3d;
        }

        .envelope-inner-frame {
            position: absolute;
            inset: 14px;
            border: 1px solid rgba(197, 160, 89, 0.25);
            border-radius: 12px;
            pointer-events: none;
            z-index: 2;
        }

        /* BANT STRUKTURU VƏ DÜYÜN DİZAYNI */
        .ribbon-horizontal-line {
            position: absolute;
            top: 50%;
            left: 0;
            width: 100%;
            height: 32px;
            background: linear-gradient(180deg, #d4af37 0%, #fff3a7 40%, #aa771c 80%, #fbf5b7 100%);
            transform: translateY(-50%);
            box-shadow: 0 4px 12px rgba(0,0,0,0.08);
            z-index: 12;
            pointer-events: none;
            transition: opacity 0.5s ease;
        }

        .bow-container {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 180px;
            height: 100px;
            z-index: 13;
            pointer-events: none;
            transition: opacity 0.5s ease;
        }

        .bow-loop-left {
            position: absolute;
            top: 22px;
            left: 10px;
            width: 65px;
            height: 40px;
            background: linear-gradient(135deg, #d4af37 0%, #fff3a7 50%, #aa771c 100%);
            border-radius: 50px 10px 10px 50px;
            transform: rotate(-12deg);
            box-shadow: -4px 4px 10px rgba(0,0,0,0.15);
        }

        .bow-loop-right {
            position: absolute;
            top: 22px;
            right: 10px;
            width: 65px;
            height: 40px;
            background: linear-gradient(-135deg, #d4af37 0%, #fff3a7 50%, #aa771c 100%);
            border-radius: 10px 50px 50px 10px;
            transform: rotate(12deg);
            box-shadow: 4px 4px 10px rgba(0,0,0,0.15);
        }

        .bow-tail-left {
            position: absolute;
            top: 50px;
            left: 35px;
            width: 30px;
            height: 60px;
            background: linear-gradient(180deg, #d4af37 0%, #aa771c 100%);
            clip-path: polygon(0 0, 100% 0, 80% 100%, 0 85%);
            transform: rotate(15deg);
            box-shadow: -2px 5px 8px rgba(0,0,0,0.12);
        }

        .bow-tail-right {
            position: absolute;
            top: 50px;
            right: 35px;
            width: 30px;
            height: 60px;
            background: linear-gradient(180deg, #d4af37 0%, #aa771c 100%);
            clip-path: polygon(0 0, 100% 0, 100% 85%, 20% 100%);
            transform: rotate(-15deg);
            box-shadow: 2px 5px 8px rgba(0,0,0,0.12);
        }

        /* ZƏRFİN YUXARI QAPAĞI */
        .envelope-flap {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            clip-path: polygon(0 0, 50% 55%, 100% 0);
            background: linear-gradient(180deg, #eaddc5 0%, var(--envelope-color) 100%);
            transform-origin: top;
            transition: transform 0.8s cubic-bezier(0.4, 0, 0.2, 1);
            z-index: 10;
            border-top: 1px solid rgba(197, 160, 89, 0.4);
        }

        /* ORTADAN ARALANAN LENT HİSSƏLƏRİ */
        .envelope-side-left {
            position: absolute;
            top: 0;
            left: 0;
            width: 50%;
            height: 100%;
            background: linear-gradient(90deg, var(--envelope-color) 70%, var(--envelope-inner) 100%);
            clip-path: polygon(0 0, 100% 50%, 0 100%);
            transition: transform 1s cubic-bezier(0.77, 0, 0.175, 1) 0.4s;
            z-index: 8;
        }

        .envelope-side-right {
            position: absolute;
            top: 0;
            right: 0;
            width: 50%;
            height: 100%;
            background: linear-gradient(-90deg, var(--envelope-color) 70%, var(--envelope-inner) 100%);
            clip-path: polygon(100% 0, 0 50%, 100% 100%);
            transition: transform 1s cubic-bezier(0.77, 0, 0.175, 1) 0.4s;
            z-index: 8;
        }

        .envelope-bottom {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--envelope-color);
            clip-path: polygon(0 100%, 50% 50%, 100% 100%);
            z-index: 7;
        }

        /* MÖHÜR VƏ DÜYÜN HİSSƏSİ */
        .seal-wrapper {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            z-index: 20;
            cursor: pointer;
            transition: transform 0.4s ease, opacity 0.4s ease;
            text-align: center;
        }

        .seal-btn {
            width: 85px;
            height: 85px;
            background: var(--gold-gradient);
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            box-shadow: 0 14px 35px rgba(197, 160, 89, 0.45), inset 0 0 10px rgba(255,255,255,0.9);
            border: 3px solid #ffffff;
            margin: 0 auto;
            transition: transform 0.3s ease;
        }

        .seal-btn:hover { transform: scale(1.06); }

        .seal-text {
            font-family: 'Cormorant Garamond', serif;
            font-size: 26px;
            font-weight: 600;
            color: #3b2805;
            letter-spacing: 1.5px;
        }

        .tap-hint {
            margin-top: 25px;
            font-size: 10px;
            color: var(--gold-solid);
            letter-spacing: 3px;
            text-transform: uppercase;
            font-weight: 500;
            background: rgba(255, 255, 255, 0.95);
            padding: 8px 18px;
            border-radius: 20px;
            border: 1px solid var(--gold-soft);
            box-shadow: 0 4px 14px rgba(0,0,0,0.05);
            white-space: nowrap;
        }

        /* ANİMASİYA MƏRHƏLƏLƏRİ */
        #envelope-wrapper.open-flap .envelope-flap {
            transform: rotateX(180deg);
            z-index: 4;
        }

        #envelope-wrapper.open-flap .seal-wrapper,
        #envelope-wrapper.open-flap .ribbon-horizontal-line,
        #envelope-wrapper.open-flap .bow-container {
            opacity: 0;
            pointer-events: none;
        }

        #envelope-wrapper.split-envelope .envelope-side-left {
            transform: translateX(-120%);
        }

        #envelope-wrapper.split-envelope .envelope-side-right {
            transform: translateX(120%);
        }

        /* ƏSAS DƏVƏTNAMƏ KART */
        #main-card {
            display: block;
            opacity: 0;
            transform: translateY(80px) scale(0.92);
            width: 100%;
            max-width: 480px;
            background: var(--card-bg);
            padding: 40px 25px;
            margin: 20px auto;
            border-radius: 16px;
            box-shadow: 0 25px 55px rgba(197, 160, 89, 0.12);
            text-align: center;
            border: 1px solid var(--gold-soft);
            transition: transform 1.2s cubic-bezier(0.16, 1, 0.3, 1), opacity 1.2s ease;
            z-index: 10;
            position: relative;
        }

        #main-card.show-card {
            opacity: 1;
            transform: translateY(0) scale(1);
        }

        .card-frame {
            border: 1px solid var(--gold-soft);
            padding: 25px 15px;
            border-radius: 10px;
        }

        .header-date {
            font-family: 'Cormorant Garamond', serif;
            font-size: 20px;
            letter-spacing: 5px;
            color: var(--gold-solid);
            font-weight: 600;
        }

        .sub-title {
            font-size: 10px;
            letter-spacing: 4px;
            text-transform: uppercase;
            color: var(--text-muted);
            margin-top: 5px;
            margin-bottom: 20px;
        }

        .names-area {
            margin: 18px 0;
            padding: 12px 0;
            border-top: 1px solid var(--gold-soft);
            border-bottom: 1px solid var(--gold-soft);
        }

        .names {
            font-family: 'Cormorant Garamond', serif;
            font-size: 36px;
            font-weight: 400;
            color: #222;
            font-style: italic;
        }

        .names span {
            font-family: 'Montserrat', sans-serif;
            font-size: 16px;
            font-style: normal;
            color: var(--gold-solid);
            margin: 0 8px;
        }

        .description { font-size: 12px; line-height: 1.8; color: #555; margin: 18px 0; font-weight: 300; }
        .section-divider { height: 1px; background: linear-gradient(90deg, transparent, var(--gold-solid), transparent); margin: 25px auto; width: 60%; opacity: 0.4; }
        .section-title { font-family: 'Cormorant Garamond', serif; font-size: 22px; color: var(--gold-solid); margin-bottom: 12px; font-weight: 600; }

        /* GERYƏ SAYIM */
        .countdown { display: flex; justify-content: center; gap: 12px; }
        .time-box {
            background: #fff;
            width: 56px;
            height: 56px;
            border-radius: 50%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            border: 1px solid var(--gold-soft);
            box-shadow: 0 4px 10px rgba(197, 160, 89, 0.08);
        }
        .time-box span { font-size: 14px; font-weight: 500; color: var(--gold-solid); }
        .time-box label { font-size: 7px; color: var(--text-muted); text-transform: uppercase; letter-spacing: 1px; margin-top: 2px; }

        /* AŞAĞI SÜRÜŞDÜR İŞARƏSİ VƏ YAZISI */
        .scroll-indicator {
            margin-top: 18px;
            font-size: 11px;
            color: var(--gold-solid);
            letter-spacing: 1.5px;
            font-weight: 400;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 4px;
            animation: bounce 2s infinite;
        }

        .scroll-indicator .arrow {
            font-size: 14px;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
            40% { transform: translateY(6px); }
            60% { transform: translateY(3px); }
        }

        /* TOY PROQRAMI */
        .program-list { text-align: left; max-width: 280px; margin: 0 auto; }
        .program-item {
            display: flex;
            align-items: center;
            margin-bottom: 10px;
            padding: 8px 10px;
            background: rgba(247, 244, 239, 0.5);
            border-radius: 6px;
            border-left: 2px solid var(--gold-solid);
        }
        .program-time { font-size: 12px; font-weight: 500; color: var(--gold-solid); width: 55px; }
        .program-desc { font-size: 12px; color: var(--text-main); }

        /* GEYİM KODU */
        .dress-code { display: flex; gap: 10px; }
        .dress-item {
            flex: 1;
            background: rgba(247, 244, 239, 0.4);
            padding: 10px 5px;
            border-radius: 6px;
            border: 1px solid rgba(197, 160, 89, 0.15);
        }
        .dress-item h4 { font-size: 10px; text-transform: uppercase; color: var(--gold-solid); }
        .dress-item p { font-size: 11px; color: #444; margin-top: 2px; }

        /* DÜYMƏLƏR */
        .btn-group { display: flex; justify-content: center; gap: 10px; margin-top: 15px; }
        .btn {
            background: var(--gold-solid);
            color: #fff;
            padding: 9px 18px;
            text-decoration: none;
            border-radius: 20px;
            font-size: 11px;
            letter-spacing: 1px;
            text-transform: uppercase;
            border: none;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(197, 160, 89, 0.25);
            transition: all 0.2s;
        }
        .btn:hover { background: #b08b46; }
        .btn-outline { background: transparent; color: var(--gold-solid); border: 1px solid var(--gold-solid); box-shadow: none; }

        /* FORM */
        .rsvp-options { display: flex; gap: 8px; margin-bottom: 10px; }
        .rsvp-btn {
            flex: 1;
            padding: 9px;
            border: 1px solid var(--gold-soft);
            background: #fff;
            color: var(--text-main);
            border-radius: 20px;
            cursor: pointer;
            font-size: 11px;
        }
        .rsvp-btn.active { background: var(--gold-solid); color: #fff; border-color: var(--gold-solid); }

        input, select, textarea {
            width: 100%;
            padding: 10px;
            margin: 5px 0;
            border: 1px solid rgba(197, 160, 89, 0.25);
            border-radius: 6px;
            font-size: 12px;
            background: rgba(255, 255, 255, 0.9);
            font-family: 'Montserrat', sans-serif;
            outline: none;
        }

        .success-msg {
            display: none;
            background: #f0f7f4;
            color: #2d6a4f;
            padding: 12px;
            border-radius: 6px;
            font-size: 12px;
            margin-top: 12px;
            border: 1px solid #b7e4c7;
        }
    </style>
</head>
<body>

    <audio id="bg-music" loop preload="auto">
        <source src="music.mp3" type="audio/mpeg">
    </audio>

    <div id="stars-container"></div>

    <!-- LUX BÖYÜK ZƏRF DÜYÜNLÜ BANT İLƏ -->
    <div id="envelope-wrapper">
        <div class="envelope-3d">
            <div class="envelope-inner-frame"></div>
            <div class="envelope-flap"></div>
            <div class="envelope-side-left"></div>
            <div class="envelope-side-right"></div>
            <div class="envelope-bottom"></div>

            <!-- QIZILI HORİZONTAL BANT QATI -->
            <div class="ribbon-horizontal-line"></div>

            <!-- DÜYÜN DİZAYNI -->
            <div class="bow-container">
                <div class="bow-loop-left"></div>
                <div class="bow-loop-right"></div>
                <div class="bow-tail-left"></div>
                <div class="bow-tail-right"></div>
            </div>

            <div class="seal-wrapper" onclick="startUnfoldSequence()">
                <div class="seal-btn">
                    <span class="seal-text">N&L</span>
                </div>
                <div class="tap-hint">Açmaq üçün toxunun</div>
            </div>
        </div>
    </div>

    <!-- ƏSAS DƏVƏTNAMƏ KART -->
    <div id="main-card">
        <div class="card-frame">
            <div class="header-date">10 . 10 . 2026</div>
            <div class="sub-title">Xoş gəldiniz</div>
            
            <div class="names-area">
                <div class="names">Nizami <span>&</span> Lətifə</div>
            </div>

            <p class="description">
                Həyatımızın ən xüsusi gününü siz dəyərli doğmalarımızla bölüşməkdən hüdudsuz xoşbəxtlik duyarıq.
            </p>

            <div class="section-divider"></div>

            <div class="section-title">Toya qalan vaxt</div>
            <div class="countdown">
                <div class="time-box"><span id="days">00</span><label>Gün</label></div>
                <div class="time-box"><span id="hours">00</span><label>Saat</label></div>
                <div class="time-box"><span id="minutes">00</span><label>Dəqiqə</label></div>
                <div class="time-box"><span id="seconds">00</span><label>Saniyə</label></div>
            </div>

            <!-- DAVAMI ÜÇÜN AŞAĞI SÜRÜŞDÜRÜN BÖLMƏSİ -->
            <div class="scroll-indicator">
                <span>Davamı üçün aşağıya sürüşdürün</span>
                <span class="arrow">⇩</span>
            </div>

            <div class="section-divider"></div>

            <div class="section-title">Toy Proqramı</div>
            <div class="program-list">
                <div class="program-item">
                    <div class="program-time">18:00</div>
                    <div class="program-desc">Qonaqların qarşılanması</div>
                </div>
                <div class="program-item">
                    <div class="program-time">19:00</div>
                    <div class="program-desc">Bəy və Gəlinin gəlişi</div>
                </div>
                <div class="program-item">
                    <div class="program-time">20:00</div>
                    <div class="program-desc">Şam yeməyi və Təbriklər</div>
                </div>
                <div class="program-item">
                    <div class="program-time">22:00</div>
                    <div class="program-desc">Tort kəsilməsi mərasimi</div>
                </div>
                <div class="program-item">
                    <div class="program-time">23:00</div>
                    <div class="program-desc">Şou proqramı və Yekun</div>
                </div>
            </div>

            <div class="section-divider"></div>

            <div class="section-title">Geyim Kodu</div>
            <div class="dress-code">
                <div class="dress-item">
                    <h4>Kişilər</h4>
                    <p>Kostyum / Smoking</p>
                </div>
                <div class="dress-item">
                    <h4>Xanımlar</h4>
                    <p>Ziyafət geyimi</p>
                </div>
            </div>

            <div class="section-divider"></div>

            <div class="section-title">Məkan və Tarix</div>
            <p style="font-weight: 500; font-size: 13px;">16 Noyabr 2026, Saat 18:00</p>
            <p style="font-size: 12px; color: var(--text-muted); margin-top: 4px;">Golden Ring Şadlıq Sarayı</p>
            <p style="font-size: 11px; color: var(--text-muted);">Bəkir Çobanzadə küç. 332, Bakı</p>
         
            <div class="btn-group">
                <a href="https://maps.app.goo.gl/fGDo9Pi52LuR53FUA?g_st=iw" target="_blank" class="btn">Google Maps</a>
                <a href="https://waze.com/ul/htp5tb6n4b" target="_blank" class="btn btn-outline">Waze</a>
            </div>

            <div class="section-divider"></div>

            <div class="section-title">İştirak Təsdiqi</div>
            
            <form id="rsvpForm">
                <div class="rsvp-options">
                    <button type="button" class="rsvp-btn active" onclick="selectAttendance('Gələcəyəm', this)">✓ Mənuniyyətlə iştirak edəcəyəm</button>
                    <button type="button" class="rsvp-btn" onclick="selectAttendance('Gələ bilməyəcəyəm', this)">✕ Təəssüf ki, iştirak edə bilməyəcəyəm</button>
                </div>
                <input type="hidden" id="attendanceStatus" value="Gələcəyəm">
                
                <input type="text" id="guestName" placeholder="Adınız və Soyadınız" required>
                <select id="guestCount" required>
                    <option value="" disabled selected>Qonaq sayısı (özünüz daxil)</option>
                    <option value="1 nəfər">1 nəfər</option>
                    <option value="2 nəfər">2 nəfər</option>
                    <option value="3 nəfər">3 nəfər</option>
                    <option value="4+ nəfər">4 və ya daha çox</option>
                </select>
                
                <textarea id="guestWish" rows="3" placeholder="Təbrik və xoş arzularınız (könüllü)..."></textarea>
                
                <button type="submit" id="submitBtn" class="btn" style="width: 100%; margin-top: 10px;">Təsdiq Et və Göndər</button>
            </form>

            <div id="successMsg" class="success-msg">
                ✨ Təşəkkür edirik! Cavabınız və xoş arzularınız uğurla qeydə alındı.
            </div>
        </div>
    </div>

    <script>
        function startUnfoldSequence() {
            var wrapper = document.getElementById('envelope-wrapper');
            var card = document.getElementById('main-card');
            var music = document.getElementById('bg-music');

            if (music) {
                music.play().catch(function(err) { console.log("Musiqi dəstəklənmədi:", err); });
            }

            wrapper.classList.add('open-flap');

            setTimeout(function() {
                wrapper.classList.add('split-envelope');
            }, 450);

            setTimeout(function() {
                card.classList.add('show-card');
                createStars();
            }, 850);

            setTimeout(function() {
                wrapper.classList.add('fade-out');
            }, 1300);
        }

        function createStars() {
            var container = document.getElementById('stars-container');
            for (var i = 0; i < 20; i++) {
                var star = document.createElement('div');
                star.className = 'star';
                var size = Math.random() * 5 + 3;
                star.style.width = size + 'px';
                star.style.height = size + 'px';
                star.style.left = Math.random() * 100 + '%';
                star.style.animationDuration = (Math.random() * 4 + 3) + 's';
                star.style.animationDelay = (Math.random() * 3) + 's';
                container.appendChild(star);
            }
        }

        var weddingDate = new Date("Oct 10, 2026 18:00:00").getTime();

        setInterval(function() {
            var now = new Date().getTime();
            var distance = weddingDate - now;

            if (distance > 0) {
                var days = Math.floor(distance / (1000 * 60 * 60 * 24));
                var hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                var minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
                var seconds = Math.floor((distance % (1000 * 60)) / 1000);

                document.getElementById("days").innerText = days < 10 ? "0" + days : days;
                document.getElementById("hours").innerText = hours < 10 ? "0" + hours : hours;
                document.getElementById("minutes").innerText = minutes < 10 ? "0" + minutes : minutes;
                document.getElementById("seconds").innerText = seconds < 10 ? "0" + seconds : seconds;
            }
        }, 1000);

        function selectAttendance(status, btn) {
            document.getElementById('attendanceStatus').value = status;
            var buttons = document.querySelectorAll('.rsvp-btn');
            buttons.forEach(function(b) { b.classList.remove('active'); });
            btn.classList.add('active');
        }

        var scriptURL = "https://script.google.com/macros/s/AKfycby_6u4N2Zp_mBVNDKdstAQp0G2v-qb8wqkAkcwDKZQwb_55fMCcb3Ncy8DAJw7oPdcg/exec";

        document.getElementById('rsvpForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            var submitBtn = document.getElementById('submitBtn');
            submitBtn.disabled = true;
            submitBtn.innerText = "Göndərilir...";

            var formData = new FormData();
            formData.append('status', document.getElementById('attendanceStatus').value);
            formData.append('name', document.getElementById('guestName').value);
            formData.append('count', document.getElementById('guestCount').value);
            formData.append('wish', document.getElementById('guestWish').value);

            fetch(scriptURL, { method: 'POST', body: formData })
                .then(function(response) {
                    document.getElementById('rsvpForm').style.display = 'none';
                    document.getElementById('successMsg').style.display = 'block';
                })
                .catch(function(error) {
                    alert("Xəta baş verdi! Lütfən yenidən cəhd edin.");
                    submitBtn.disabled = false;
                    submitBtn.innerText = "Təsdiq Et və Göndər";
                });
        });
    </script>
</body>
</html>
