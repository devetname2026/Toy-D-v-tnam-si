<!DOCTYPE html>
<html lang="az">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fuad & Sevinc - Toy Dəvətnaməsi</title>
    <!-- Estetik Şriftlər -->
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;700&family=Pinyon+Script&family=Montserrat:wght@300;400;500&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-color: #f6f2eb;
            --primary-color: #2c2420;
            --accent-gold: #c5a059;
            --accent-gold-light: #e5cb90;
            --card-bg: #ffffff;
            --text-muted: #5e564e;
            --envelope-bg: #f0e8d8;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            background-color: var(--bg-color);
            font-family: 'Montserrat', sans-serif;
            color: var(--primary-color);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px 10px;
            overflow-x: hidden;
        }

        /* ----- INTERAKTIV ZƏRF SƏHİFƏSİ ----- */
        #envelope-wrapper {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background-color: rgba(246, 242, 235, 0.98);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            transition: opacity 1s ease, visibility 1s ease;
        }

        .envelope {
            width: 320px;
            height: 220px;
            background-color: var(--envelope-bg);
            border: 2px solid var(--accent-gold-light);
            border-radius: 12px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.12);
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            transition: transform 0.4s ease;
        }

        .envelope:hover {
            transform: scale(1.03);
        }

        /* Qızılı Möhür */
        .wax-seal {
            width: 75px;
            height: 75px;
            background: radial-gradient(circle, #e5cb90 0%, #c5a059 70%, #9e7b37 100%);
            border-radius: 50%;
            box-shadow: 0 6px 15px rgba(197, 160, 89, 0.4), inset 0 2px 4px rgba(255,255,255,0.6);
            display: flex;
            justify-content: center;
            align-items: center;
            border: 2px solid #b08d46;
            z-index: 2;
        }

        .wax-seal span {
            font-family: 'Pinyon Script', cursive;
            font-size: 2.2rem;
            color: #2c2420;
            text-shadow: 0 1px 1px rgba(255,255,255,0.4);
        }

        .envelope-text {
            margin-top: 25px;
            font-family: 'Cinzel', serif;
            font-size: 0.85rem;
            letter-spacing: 3px;
            text-transform: uppercase;
            color: var(--accent-gold);
            animation: pulse 1.8s infinite;
        }

        @keyframes pulse {
            0% { opacity: 0.5; transform: scale(0.98); }
            50% { opacity: 1; transform: scale(1.02); }
            100% { opacity: 0.5; transform: scale(0.98); }
        }

        /* ----- ƏSAS DƏVƏTNAMƏ KARTI ----- */
        .invitation-card {
            background: var(--card-bg);
            max-width: 500px;
            width: 100%;
            padding: 50px 30px;
            border-radius: 18px;
            box-shadow: 0 15px 35px rgba(197, 160, 89, 0.15);
            border: 2px solid #f2e9d8;
            text-align: center;
            position: relative;
            opacity: 0;
            transform: translateY(40px);
            transition: all 1s ease;
        }

        .invitation-card.show {
            opacity: 1;
            transform: translateY(0);
        }

        .invitation-card::before {
            content: "";
            position: absolute;
            top: 15px; left: 15px; right: 15px; bottom: 15px;
            border: 1px solid var(--accent-gold);
            border-radius: 12px;
            pointer-events: none;
            opacity: 0.6;
        }

        /* Musiqi idarəetmə düyməsi */
        .music-player {
            position: absolute;
            top: 25px;
            right: 25px;
            z-index: 10;
        }

        #music-btn {
            background: #faf6ef;
            border: 1px solid var(--accent-gold);
            color: var(--primary-color);
            padding: 6px 14px;
            border-radius: 20px;
            font-family: 'Cinzel', serif;
            font-size: 0.7rem;
            letter-spacing: 1px;
            cursor: pointer;
        }

        .top-subtitle {
            font-family: 'Cinzel', serif;
            font-size: 0.85rem;
            letter-spacing: 5px;
            text-transform: uppercase;
            color: var(--accent-gold);
            margin-bottom: 15px;
            font-weight: 600;
        }

        .names {
            font-family: 'Pinyon Script', cursive;
            font-size: 4.5rem;
            color: var(--accent-gold);
            margin-bottom: 10px;
            line-height: 1.1;
        }

        .divider {
            width: 80px;
            height: 1px;
            background: linear-gradient(90deg, transparent, var(--accent-gold), transparent);
            margin: 15px auto 25px auto;
        }

        .invitation-text {
            font-size: 0.95rem;
            line-height: 1.8;
            color: var(--text-muted);
            margin-bottom: 30px;
            font-weight: 300;
        }

        .details-box {
            background-color: #faf6ef;
            border: 1px solid #ebd8b6;
            padding: 22px 15px;
            border-radius: 12px;
            margin-bottom: 30px;
        }

        .event-hall {
            font-family: 'Cinzel', serif;
            font-size: 1.3rem;
            font-weight: 700;
            letter-spacing: 1px;
            color: var(--primary-color);
            margin-bottom: 8px;
        }

        .event-date-time {
            font-family: 'Cinzel', serif;
            font-size: 1rem;
            font-weight: 600;
            color: var(--accent-gold);
            margin-bottom: 8px;
        }

        .event-address {
            font-size: 0.85rem;
            color: var(--text-muted);
        }

        /* Program / Agenda */
        .timeline {
            display: flex;
            flex-direction: column;
            gap: 12px;
            text-align: left;
            margin-top: 10px;
        }

        .timeline-item {
            display: flex;
            align-items: center;
            gap: 15px;
            background: #ffffff;
            padding: 12px 15px;
            border-radius: 8px;
            border-left: 3px solid var(--accent-gold);
            box-shadow: 0 2px 5px rgba(0,0,0,0.03);
        }

        .timeline-time {
            font-family: 'Cinzel', serif;
            font-weight: 700;
            color: var(--accent-gold);
            font-size: 0.95rem;
            min-width: 55px;
        }

        .timeline-desc {
            font-size: 0.85rem;
            color: var(--primary-color);
        }

        /* Countdown */
        .timer-title {
            font-family: 'Cinzel', serif;
            font-size: 0.8rem;
            letter-spacing: 3px;
            text-transform: uppercase;
            color: var(--accent-gold);
            margin-bottom: 15px;
            font-weight: 600;
        }

        #countdown {
            display: flex;
            justify-content: center;
            gap: 12px;
            margin-bottom: 35px;
        }

        .time-box {
            background: linear-gradient(145deg, #ffffff, #f7efe2);
            border: 1px solid var(--accent-gold-light);
            color: var(--primary-color);
            padding: 10px 8px;
            border-radius: 10px;
            min-width: 65px;
        }

        .time-box span {
            display: block;
            font-family: 'Cinzel', serif;
            font-size: 1.3rem;
            font-weight: 700;
            color: var(--accent-gold);
        }

        .time-box label {
            font-size: 0.65rem;
            text-transform: uppercase;
            color: var(--text-muted);
        }

        /* Forms */
        .section-box {
            background-color: #faf6ef;
            border: 1px solid #ebd8b6;
            padding: 22px 20px;
            border-radius: 12px;
            margin-bottom: 25px;
            text-align: left;
        }

        .section-title {
            font-family: 'Cinzel', serif;
            font-size: 1.05rem;
            font-weight: 600;
            color: var(--primary-color);
            margin-bottom: 15px;
            text-align: center;
        }

        .form-group {
            margin-bottom: 12px;
        }

        .form-group label {
            display: block;
            font-size: 0.8rem;
            color: var(--text-muted);
            margin-bottom: 5px;
        }

        .form-input, .form-select, .form-textarea {
            width: 100%;
            padding: 10px 12px;
            border: 1px solid #dcc8a4;
            border-radius: 8px;
            font-family: inherit;
            font-size: 0.85rem;
            background-color: #ffffff;
            color: var(--primary-color);
            outline: none;
        }

        .form-textarea {
            resize: vertical;
            height: 75px;
        }

        .radio-group {
            display: flex;
            gap: 15px;
            margin-top: 5px;
        }

        .radio-option {
            display: flex;
            align-items: center;
            gap: 5px;
            font-size: 0.85rem;
            cursor: pointer;
        }

        .btn-action {
            width: 100%;
            background-color: var(--accent-gold);
            color: #ffffff;
            border: none;
            padding: 12px;
            border-radius: 20px;
            font-family: 'Cinzel', serif;
            font-size: 0.8rem;
            font-weight: 600;
            cursor: pointer;
        }

        .btn-map {
            display: block;
            padding: 13px 25px;
            border-radius: 25px;
            text-decoration: none;
            font-family: 'Cinzel', serif;
            font-size: 0.8rem;
            font-weight: 600;
            text-align: center;
            background-color: transparent;
            color: var(--accent-gold);
            border: 2px solid var(--accent-gold);
        }
    </style>
</head>
<body>

    <!-- INTERAKTIV ZƏRF SƏHİFƏSİ -->
    <div id="envelope-wrapper">
        <div class="envelope" onclick="openEnvelope()">
            <div class="wax-seal">
                <span>F&S</span>
            </div>
        </div>
        <div class="envelope-text">✉️ Açmaq üçün toxunun</div>
    </div>

    <!-- DƏVƏTNAMƏ KARTI -->
    <div class="invitation-card" id="card">
        
        <div class="music-player">
            <button id="music-btn" onclick="toggleMusic()">🔊 Musiqini Dayandır</button>
            <audio id="bg-music" loop>
                <source src="musiqi.mp3" type="audio/mpeg">
            </audio>
        </div>

        <div class="top-subtitle">Toy Dəvətnaməsi</div>
        <h1 class="names">Fuad & Sevinc</h1>
        <div class="divider"></div>
        
        <p class="invitation-text">
            Həyatımızın bu ən özəl və unudulmaz günündə – yeni ailəmizin təməlini qoyarkən siz dəyərli qonaqlarımızı yanımızda görməkdən böyük şadlıq duyarıq.
        </p>

        <div class="details-box">
            <div class="event-hall">DIVA WEDDING HALL</div>
            <div class="event-date-time">10 OKTYABR 2026 | SAAT: 18:00</div>
            <div class="event-address">📍 Bakı şəhəri, Həsən Əliyev küçəsi 141</div>
        </div>

        <div class="section-box">
            <div class="section-title">✨ TƏDBİR PROQRAMI</div>
            <div class="timeline">
                <div class="timeline-item">
                    <div class="timeline-time">18:00</div>
                    <div class="timeline-desc">Qonaqların qarşılanması</div>
                </div>
                <div class="timeline-item">
                    <div class="timeline-time">19:00</div>
                    <div class="timeline-desc">Bəy və Gəlinin gəlişi</div>
                </div>
                <div class="timeline-item">
                    <div class="timeline-time">20:30</div>
                    <div class="timeline-desc">Şou proqram və rəqslər</div>
                </div>
                <div class="timeline-item">
                    <div class="timeline-time">22:30</div>
                    <div class="timeline-desc">Tort kəsilməsi mərasimi</div>
                </div>
            </div>
        </div>

        <div class="timer-title">TƏDBİRƏ QALAN VAXT</div>
        <div id="countdown">
            <div class="time-box"><span id="days">00</span><label>Gün</label></div>
            <div class="time-box"><span id="hours">00</span><label>Saat</label></div>
            <div class="time-box"><span id="minutes">00</span><label>Dəq</label></div>
            <div class="time-box"><span id="seconds">00</span><label>San</label></div>
        </div>

        <!-- RSVP -->
        <div class="section-box">
            <div class="section-title">✉️ İŞTİRAK TƏSDİqİ (RSVP)</div>
            <div class="form-group">
                <label for="rsvp-name">Adınız və Soyadınız:</label>
                <input type="text" id="rsvp-name" class="form-input" placeholder="Məsələn: Əli Məmmədov">
            </div>
            <div class="form-group">
                <label>İştirak durumunuz:</label>
                <div class="radio-group">
                    <label class="radio-option">
                        <input type="radio" name="attendance" value="İştirak edəcəyəm" checked> İştirak edəcəyəm
                    </label>
                    <label class="radio-option">
                        <input type="radio" name="attendance" value="Təəssüf ki, gələ bilməyəcəyəm"> Gələ bilməyəcəyəm
                    </label>
                </div>
            </div>
            <div class="form-group">
                <label for="rsvp-count">Nəfər sayı (Özünüz daxil):</label>
                <select id="rsvp-count" class="form-select">
                    <option value="1 nəfər">1 nəfər</option>
                    <option value="2 nəfər">2 nəfər</option>
                    <option value="3 nəfər">3 nəfər</option>
                    <option value="4+ nəfər">4 və ya daha çox nəfər</option>
                </select>
            </div>
            <button class="btn-action" onclick="sendRSVP()">TƏSDİQİ GÖNDƏR (WHATSAPP)</button>
        </div>

        <!-- Arzular Bölməsi -->
        <div class="section-box">
            <div class="section-title">💌 BƏY VƏ GƏLİNƏ ARZULARINIZ</div>
            <div class="form-group">
                <label for="guest-name">Adınız və Soyadınız:</label>
                <input type="text" id="guest-name" class="form-input" placeholder="Məsələn: Əli Məmmədov">
            </div>
            <div class="form-group">
                <label for="guest-wish">Arzu və Təbrikiniz:</label>
                <textarea id="guest-wish" class="form-textarea" placeholder="Ürək sözlərinizi buraya yazın..."></textarea>
            </div>
            <button class="btn-action" onclick="sendWish()">ARZUNU GÖNDƏR (WHATSAPP)</button>
        </div>

        <a href="https://maps.google.com/?q=Hasan+Aliyev+141+Baku" target="_blank" class="btn-map">🗺️ XƏRİTƏDƏ MƏKANA BAX</a>
    </div>

    <script>
        function openEnvelope() {
            const wrapper = document.getElementById("envelope-wrapper");
            const card = document.getElementById("card");
            const music = document.getElementById("bg-music");

            // Zərfi itiririk
            wrapper.style.opacity = "0";
            wrapper.style.visibility = "hidden";

            // Kartı göstəririk
            card.classList.add("show");

            // Musiqini başladırıq
            music.play().catch(e => console.log("Musiqi səsi bloklandı"));
        }

        const eventDate = new Date(2026, 9, 10, 18, 0, 0).getTime();

        const timer = setInterval(function() {
            const now = new Date().getTime();
            const distance = eventDate - now;

            if (distance < 0) {
                clearInterval(timer);
                document.getElementById("countdown").innerHTML = "<b style='color:var(--accent-gold)'>Tədbir Başladı!</b>";
                return;
            }

            const days = Math.floor(distance / (1000 * 60 * 60 * 24));
            const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((distance % (1000 * 60)) / 1000);

            document.getElementById("days").innerText = days < 10 ? "0" + days : days;
            document.getElementById("hours").innerText = hours < 10 ? "0" + hours : hours;
            document.getElementById("minutes").innerText = minutes < 10 ? "0" + minutes : minutes;
            document.getElementById("seconds").innerText = seconds < 10 ? "0" + seconds : seconds;
        }, 1000);

        const phone = "994000000000"; 

        function sendRSVP() {
            const name = document.getElementById("rsvp-name").value;
            const attendance = document.querySelector('input[name="attendance"]:checked').value;
            const count = document.getElementById("rsvp-count").value;
            
            if (!name.trim()) {
                alert("Zəhmət olmasa adınızı qeyd edin.");
                return;
            }
            
            const message = encodeURIComponent("Salam! Mən " + name + ".\n\nİştirak Təsdiqi (RSVP):\nStatus: " + attendance + "\nNəfər sayı: " + count);
            window.open("https://wa.me/" + phone + "?text=" + message, "_blank");
        }

        function sendWish() {
            const name = document.getElementById("guest-name").value;
            const wish = document.getElementById("guest-wish").value;
            
            if (!name.trim() || !wish.trim()) {
                alert("Zəhmət olmasa adınızı və arzularınızı qeyd edin.");
                return;
            }
            
            const message = encodeURIComponent("Salam! Mən " + name + ".\n\nTəbrikim və arzum:\n" + wish);
            window.open("https://wa.me/" + phone + "?text=" + message, "_blank");
        }

        function toggleMusic() {
            const music = document.getElementById("bg-music");
            const btn = document.getElementById("music-btn");

            if (music.paused) {
                music.play();
                btn.innerHTML = "🔊 Musiqini Dayandır";
            } else {
                music.pause();
                btn.innerHTML = "🎵 Musiqini Qoş";
            }
        }
    </script>

</body>
</html>
