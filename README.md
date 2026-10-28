<!DOCTYPE html>
<html lang="az">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Fuad & Sevinc — Toy Dəvətnaməsi</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;1,400&family=Montserrat:wght@300;400;500;600&display=swap" rel="stylesheet">
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
  <style>
    :root {
      --bg-chic: #FAF7F2;
      --bg-card: #FFFFFF;
      --camel-main: #C19A6B;
      --camel-dark: #8B5E34;
      --camel-light: #EAE0D5;
      --text-dark: #3D2B1F;
      --text-muted: #7A685B;
      --shadow: 0 15px 35px rgba(139, 94, 52, 0.08);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      -webkit-tap-highlight-color: transparent;
    }

    body {
      background-color: var(--bg-chic);
      color: var(--text-dark);
      font-family: 'Montserrat', sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      overflow-x: hidden;
    }

    .container {
      width: 100%;
      max-width: 440px;
      min-height: 100vh;
      background: var(--bg-chic);
      position: relative;
      box-shadow: 0 0 50px rgba(0,0,0,0.05);
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    /* ENVELOPE SCREEN */
    #envelope-screen {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      background: var(--bg-chic);
      z-index: 999;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      transition: opacity 0.8s ease, visibility 0.8s;
    }

    .envelope-wrapper {
      width: 320px;
      height: 220px;
      background: #F2E9E1;
      border: 1px solid var(--camel-light);
      border-radius: 8px;
      position: relative;
      box-shadow: 0 20px 40px rgba(139, 94, 52, 0.12);
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;
    }

    .ribbon {
      position: absolute;
      width: 40px;
      height: 100%;
      background: var(--camel-light);
      border-left: 1px solid rgba(193, 154, 107, 0.3);
      border-right: 1px solid rgba(193, 154, 107, 0.3);
    }

    .wax-seal {
      width: 75px;
      height: 75px;
      background: linear-gradient(135deg, #C19A6B, #8B5E34);
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      color: #FFF;
      font-family: 'Cormorant Garamond', serif;
      font-size: 24px;
      font-weight: 600;
      letter-spacing: 2px;
      box-shadow: 0 6px 18px rgba(139, 94, 52, 0.35);
      position: relative;
      z-index: 2;
      border: 2px solid #EAE0D5;
      transition: transform 0.3s ease;
    }

    .envelope-wrapper:hover .wax-seal {
      transform: scale(1.06);
    }

    .tap-hint {
      margin-top: 25px;
      font-size: 12px;
      letter-spacing: 2px;
      text-transform: uppercase;
      color: var(--camel-dark);
      opacity: 0.8;
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%, 100% { opacity: 0.4; }
      50% { opacity: 0.9; }
    }

    /* MAIN INVITATION CONTENT */
    .content {
      width: 100%;
      padding: 40px 24px;
      display: flex;
      flex-direction: column;
      gap: 28px;
      opacity: 0;
      transform: translateY(20px);
      transition: opacity 1s ease, transform 1s ease;
    }

    .content.visible {
      opacity: 1;
      transform: translateY(0);
    }

    .card {
      background: var(--bg-card);
      border-radius: 16px;
      padding: 32px 24px;
      text-align: center;
      box-shadow: var(--shadow);
      border: 1px solid rgba(234, 224, 213, 0.6);
    }

    .subtitle {
      font-size: 11px;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--camel-main);
      font-weight: 600;
      margin-bottom: 12px;
    }

    .couples-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: 38px;
      font-weight: 400;
      color: var(--text-dark);
      margin-bottom: 16px;
    }

    .couples-title span {
      font-style: italic;
      color: var(--camel-main);
    }

    .date-badge {
      display: inline-block;
      padding: 8px 18px;
      background: var(--bg-chic);
      border-radius: 20px;
      font-size: 13px;
      font-weight: 500;
      color: var(--camel-dark);
      margin-bottom: 20px;
    }

    .opening-text {
      font-family: 'Cormorant Garamond', serif;
      font-size: 18px;
      line-height: 1.6;
      color: var(--text-muted);
      font-style: italic;
    }

    /* COUNTDOWN */
    .timer-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 8px;
      margin-top: 16px;
    }

    .timer-box {
      background: var(--bg-chic);
      padding: 12px 6px;
      border-radius: 10px;
      border: 1px solid var(--camel-light);
    }

    .timer-value {
      font-family: 'Cormorant Garamond', serif;
      font-size: 24px;
      font-weight: 600;
      color: var(--camel-dark);
    }

    .timer-label {
      font-size: 10px;
      text-transform: uppercase;
      color: var(--text-muted);
      margin-top: 2px;
    }

    /* LOCATION & MAPS */
    .venue-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: 24px;
      color: var(--text-dark);
      margin-bottom: 6px;
    }

    .venue-address {
      font-size: 12px;
      color: var(--text-muted);
      margin-bottom: 20px;
    }

    .btn-group {
      display: flex;
      gap: 12px;
    }

    .btn-map {
      flex: 1;
      padding: 12px;
      border-radius: 10px;
      text-decoration: none;
      font-size: 12px;
      font-weight: 500;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 6px;
      transition: background 0.3s ease;
    }

    .btn-gmaps {
      background: var(--camel-main);
      color: #FFF;
    }

    .btn-waze {
      background: var(--bg-chic);
      color: var(--camel-dark);
      border: 1px solid var(--camel-light);
    }

    /* DRESS CODE */
    .dresscode-items {
      display: flex;
      justify-content: space-around;
      margin-top: 16px;
    }

    .dress-item {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 6px;
    }

    .dress-icon {
      font-size: 24px;
    }

    .dress-text {
      font-size: 12px;
      color: var(--text-muted);
    }

    /* RSVP */
    .rsvp-btns {
      display: flex;
      flex-direction: column;
      gap: 10px;
      margin-top: 16px;
    }

    .btn-rsvp {
      width: 100%;
      padding: 14px;
      border-radius: 10px;
      border: none;
      font-family: 'Montserrat', sans-serif;
      font-size: 13px;
      font-weight: 500;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    .btn-accept {
      background: var(--camel-dark);
      color: #FFF;
    }

    .btn-decline {
      background: var(--bg-chic);
      color: var(--text-muted);
      border: 1px solid var(--camel-light);
    }

    .rsvp-message {
      margin-top: 12px;
      font-size: 13px;
      color: var(--camel-dark);
      font-weight: 500;
      display: none;
    }
  </style>
</head>
<body>

  <!-- ENVELOPE SCREEN -->
  <div id="envelope-screen" onclick="openEnvelope()">
    <div class="envelope-wrapper">
      <div class="ribbon"></div>
      <div class="wax-seal">F&S</div>
    </div>
    <div class="tap-hint">Açmaq üçün toxunun</div>
  </div>

  <!-- MAIN CONTENT -->
  <div class="container">
    <div class="content" id="main-content">
      
      <!-- HERO CARD -->
      <div class="card">
        <div class="subtitle">TOY DƏVƏTNAMƏSİ</div>
        <h1 class="couples-title">Fuad <span>&</span> Sevinc</h1>
        <div class="date-badge">16 NOYABR 2026 • SAAT 18:00</div>
        <p class="opening-text">
          “Həyatımızın ən xoşbəxt gününün başlanğıcında yanımızda olmağınız və bu sevincə şərik çıxmağınız bizə sonsuz qürur verər.”
        </p>
      </div>

      <!-- TIMER CARD -->
      <div class="card">
        <div class="subtitle">Toya qalan vaxt</div>
        <div class="timer-grid">
          <div class="timer-box"><div class="timer-value" id="days">00</div><div class="timer-label">Gün</div></div>
          <div class="timer-box"><div class="timer-value" id="hours">00</div><div class="timer-label">Saat</div></div>
          <div class="timer-box"><div class="timer-value" id="minutes">00</div><div class="timer-label">Dəqiqə</div></div>
          <div class="timer-box"><div class="timer-value" id="seconds">00</div><div class="timer-label">Saniyə</div></div>
        </div>
      </div>

      <!-- LOCATION CARD -->
      <div class="card">
        <div class="subtitle">MƏKAN</div>
        <div class="venue-title">Golden Ring Şadlıq Sarayı</div>
        <div class="venue-address">Bakı şəhəri, Bakıxanov qəsəbəsi</div>
        <div class="btn-group">
          <a href="https://maps.google.com" target="_blank" class="btn-map btn-gmaps">📍 Google Maps</a>
          <a href="https://waze.com" target="_blank" class="btn-map btn-waze">🚗 Waze</a>
        </div>
      </div>

      <!-- DRESS CODE CARD -->
      <div class="card">
        <div class="subtitle">GEYİM FORMASI</div>
        <div class="dresscode-items">
          <div class="dress-item">
            <span class="dress-icon">🤵</span>
            <span class="dress-text">Kişilər: Smoking / Kostyum</span>
          </div>
          <div class="dress-item">
            <span class="dress-icon">👗</span>
            <span class="dress-text">Xanımlar: Ziyafət geyimi</span>
          </div>
        </div>
      </div>

      <!-- RSVP CARD -->
      <div class="card">
        <div class="subtitle">İŞTİRAKIN TƏSDİQİ</div>
        <div class="rsvp-btns" id="rsvp-actions">
          <button class="btn-rsvp btn-accept" onclick="respondRSVP(true)">✨ Gələcəyəm</button>
          <button class="btn-rsvp btn-decline" onclick="respondRSVP(false)">🤍 Təəssüf ki, gələ bilməyəcəm</button>
        </div>
        <div class="rsvp-message" id="rsvp-msg"></div>
      </div>

    </div>
  </div>

  <script>
    function openEnvelope() {
      const env = document.getElementById('envelope-screen');
      const content = document.getElementById('main-content');
      
      env.style.opacity = '0';
      setTimeout(() => {
        env.style.visibility = 'hidden';
        content.classList.add('visible');
      }, 800);
    }

    // Countdown Timer
    const weddingDate = new Date('November 16, 2026 18:00:00').getTime();

    function updateTimer() {
      const now = new Date().getTime();
      const diff = weddingDate - now;

      if (diff > 0) {
        document.getElementById('days').innerText = String(Math.floor(diff / (1000 * 60 * 60 * 24))).padStart(2, '0');
        document.getElementById('hours').innerText = String(Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))).padStart(2, '0');
        document.getElementById('minutes').innerText = String(Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60))).padStart(2, '0');
        document.getElementById('seconds').innerText = String(Math.floor((diff % (1000 * 60)) / 1000)).padStart(2, '0');
      }
    }

    setInterval(updateTimer, 1000);
    updateTimer();

    // RSVP Action
    function respondRSVP(attending) {
      const actions = document.getElementById('rsvp-actions');
      const msg = document.getElementById('rsvp-msg');

      actions.style.display = 'none';
      msg.style.display = 'block';

      if (attending) {
        msg.innerText = "Təşəkkür edirik! Sizi aramızda görməyə şad olarıq ✨";
        confetti({
          particleCount: 80,
          spread: 60,
          origin: { y: 0.7 },
          colors: ['#C19A6B', '#8B5E34', '#EAE0D5']
        });
      } else {
        msg.innerText = "Diqqətiniz üçün təşəkkür edirik 🤍";
      }
    }
  </script>
</body>
</html>
