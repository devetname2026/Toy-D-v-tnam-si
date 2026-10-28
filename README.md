<!DOCTYPE html>
<html lang="az" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fuad & Sevinc — Toy Dəvətnaməsi</title>
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Google Fonts: Italiana, Plus Jakarta Sans, Cormorant Garamond -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,400&family=Italiana&family=Plus+Jakarta+Sans:ital,wght@0,200;0,300;0,400;0,500;0,600;1,300&display=swap" rel="stylesheet">
    
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- JS Confetti -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        chic: {
                            50: '#FAF7F2',
                            100: '#F5EFEB',
                            200: '#EAE0D5',
                            300: '#DDD0C0',
                        },
                        camel: {
                            100: '#E8D8C3',
                            200: '#D6BC9B',
                            300: '#C19A6B',
                            400: '#A37C4E',
                            500: '#8B5E34',
                            600: '#6E4723',
                            700: '#523317',
                        },
                        charcoal: {
                            900: '#26211C',
                            800: '#3D352E',
                        }
                    },
                    fontFamily: {
                        editorial: ['"Italiana"', 'serif'],
                        serif: ['"Cormorant Garamond"', 'serif'],
                        sans: ['"Plus Jakarta Sans"', 'sans-serif'],
                    }
                }
            }
        }
    </script>

    <style>
        body {
            background: linear-gradient(135deg, #FAF7F2 0%, #F5EFEB 50%, #EAE0D5 100%);
            color: #26211C;
            font-family: 'Plus Jakarta Sans', sans-serif;
            overflow-x: hidden;
            -webkit-font-smoothing: antialiased;
        }

        /* Subtle Ambient Warm Camel Glow Mesh */
        .ambient-glow {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 100vw;
            height: 100vh;
            background: radial-gradient(circle at 50% 35%, rgba(193, 154, 107, 0.18), rgba(245, 239, 235, 0) 70%);
            pointer-events: none;
            z-index: 0;
        }

        /* Canvas Particle Layer */
        #particleCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        /* Minimal Chic Container */
        .minimal-card {
            background: rgba(250, 247, 242, 0.88);
            backdrop-filter: blur(24px);
            -webkit-backdrop-filter: blur(24px);
            border: 1px solid rgba(193, 154, 107, 0.3);
            box-shadow: 0 20px 50px -15px rgba(110, 71, 35, 0.07);
        }

        /* Custom Radio Selection Pill */
        .rsvp-pill input:checked + label {
            background: linear-gradient(135deg, #8B5E34 0%, #6E4723 100%);
            color: #FAF7F2;
            border-color: #6E4723;
            box-shadow: 0 6px 20px rgba(139, 94, 52, 0.25);
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 4px;
        }
        ::-webkit-scrollbar-track {
            background: #FAF7F2;
        }
        ::-webkit-scrollbar-thumb {
            background: #C19A6B;
            border-radius: 4px;
        }
    </style>
</head>
<body class="relative min-h-screen">

    <!-- AMBIENT BACKGROUND LAYER -->
    <div class="ambient-glow"></div>
    <canvas id="particleCanvas"></canvas>

    <!-- FLOATING AUDIO CONTROL -->
    <div class="fixed top-6 right-6 z-50">
        <button id="musicBtn" onclick="toggleAudio()" class="w-11 h-11 rounded-full bg-chic-50/90 backdrop-blur-md border border-camel-300/30 text-camel-600 shadow-sm hover:shadow-md flex items-center justify-center transition-all duration-300 active:scale-95">
            <i id="musicIcon" class="fa-solid fa-music text-xs"></i>
        </button>
    </div>

    <!-- MAIN APP WRAPPER -->
    <main class="max-w-md mx-auto px-4 sm:px-6 py-8 sm:py-12 relative z-10 flex flex-col min-h-screen justify-center">

        <!-- SINGLE CONTINUOUS ELEGANT CARD -->
        <div class="minimal-card rounded-3xl p-6 sm:p-10 shadow-2xl space-y-10 relative my-auto">

            <!-- HEADER SECTION -->
            <header class="text-center pt-2">
                <p class="text-[10px] uppercase tracking-[0.4em] text-camel-500 font-semibold mb-4">Toy Dəvətnaməsi</p>
                
                <!-- COUPLE NAMES -->
                <h1 class="font-editorial text-5xl sm:text-6xl tracking-tight text-charcoal-900 leading-none mb-3">
                    Fuad <span class="font-serif italic font-light text-3xl sm:text-4xl text-camel-400">&</span> Sevinc
                </h1>

                <div class="w-10 h-[1px] bg-gradient-to-r from-transparent via-camel-300 to-transparent mx-auto my-5 opacity-70"></div>

                <p class="font-editorial text-xl text-charcoal-800 tracking-wider">16 NOYABR 2026</p>
                <p class="text-[11px] font-medium tracking-[0.2em] text-camel-500 uppercase mt-1">SAAT 18:00</p>

                <!-- ANIMATED SCROLL DOWN INDICATOR -->
                <div class="pt-8 flex flex-col items-center justify-center animate-bounce opacity-75">
                    <span class="text-[9px] uppercase tracking-[0.25em] text-camel-500 font-medium mb-1.5">Aşağı sürüşdürün</span>
                    <i class="fa-solid fa-chevron-down text-xs text-camel-400"></i>
                </div>
            </header>

            <!-- OPENING MESSAGE -->
            <section class="text-center pt-2 border-t border-camel-300/20">
                <p class="font-serif text-lg sm:text-xl italic leading-relaxed text-charcoal-800 font-normal pt-6">
                    “Həyatımızın ən xoşbəxt gününün başlanğıcında yanımızda olmağınız və bu sevincə şərik çıxmağınız bizə sonsuz qürur verər.”
                </p>
            </section>

            <!-- MINIMAL COUNTDOWN TIMER -->
            <section class="pt-2 border-t border-camel-300/20">
                <p class="text-center text-[10px] uppercase tracking-[0.3em] text-camel-500 font-semibold mb-5">Mərasimə Qalan Vaxt</p>
                
                <div class="grid grid-cols-4 gap-2.5 text-center">
                    <div class="bg-chic-50/80 backdrop-blur-md rounded-xl p-2.5 border border-camel-300/20 shadow-sm">
                        <span id="cd-days" class="font-editorial text-2xl text-camel-600 block font-normal">00</span>
                        <span class="text-[8px] uppercase tracking-wider text-camel-500 mt-0.5 block">Gün</span>
                    </div>
                    <div class="bg-chic-50/80 backdrop-blur-md rounded-xl p-2.5 border border-camel-300/20 shadow-sm">
                        <span id="cd-hours" class="font-editorial text-2xl text-camel-600 block font-normal">00</span>
                        <span class="text-[8px] uppercase tracking-wider text-camel-500 mt-0.5 block">Saat</span>
                    </div>
                    <div class="bg-chic-50/80 backdrop-blur-md rounded-xl p-2.5 border border-camel-300/20 shadow-sm">
                        <span id="cd-minutes" class="font-editorial text-2xl text-camel-600 block font-normal">00</span>
                        <span class="text-[8px] uppercase tracking-wider text-camel-500 mt-0.5 block">Dəq</span>
                    </div>
                    <div class="bg-chic-50/80 backdrop-blur-md rounded-xl p-2.5 border border-camel-300/20 shadow-sm">
                        <span id="cd-seconds" class="font-editorial text-2xl text-camel-600 block font-normal">00</span>
                        <span class="text-[8px] uppercase tracking-wider text-camel-500 mt-0.5 block">San</span>
                    </div>
                </div>
            </section>

            <!-- VENUE & NAVIGATION -->
            <section class="pt-2 border-t border-camel-300/20 text-center space-y-4">
                <div class="w-10 h-10 mx-auto rounded-full bg-chic-100 flex items-center justify-center text-camel-500 mt-4 border border-camel-300/30">
                    <i class="fa-solid fa-location-dot text-sm"></i>
                </div>
                
                <div>
                    <h2 class="font-editorial text-2xl text-charcoal-900 tracking-wide">Golden Ring</h2>
                    <p class="text-[10px] uppercase tracking-[0.2em] text-camel-500 font-medium mt-0.5">Şadlıq Sarayı</p>
                </div>

                <!-- NAVIGATION BUTTONS -->
                <div class="pt-2 flex flex-col gap-2.5">
                    <a href="https://maps.app.goo.gl/2Rz43K1oTn1Wor3w9?g_st=ic" target="_blank" rel="noopener"
                       class="w-full py-3 px-4 rounded-xl bg-gradient-to-r from-camel-500 to-camel-600 text-chic-50 text-[11px] font-medium tracking-widest uppercase hover:opacity-95 transition-all shadow-md flex items-center justify-center gap-2">
                        <i class="fa-brands fa-google text-xs"></i>
                        <span>Google Maps ilə Aç</span>
                    </a>
                    
                    <a href="https://waze.com/ul/htp5tb6n4b" target="_blank" rel="noopener"
                       class="w-full py-3 px-4 rounded-xl bg-chic-50 border border-camel-300/40 text-charcoal-900 text-[11px] font-medium tracking-widest uppercase hover:bg-chic-100 transition-all flex items-center justify-center gap-2 shadow-sm">
                        <i class="fa-brands fa-waze text-camel-500 text-sm"></i>
                        <span>Waze Naviqasiya</span>
                    </a>
                </div>
            </section>

            <!-- MODERN MINIMAL RSVP -->
            <section class="pt-2 border-t border-camel-300/20">
                <div class="text-center mb-5 mt-2">
                    <h2 class="font-editorial text-2xl text-charcoal-900">İştirak Təsdiqi</h2>
                    <p class="text-[11px] text-camel-500 mt-1">Zəhmət olmasa gəlişinizi bizə bildirin</p>
                </div>

                <!-- SUCCESS MESSAGE CONTAINER -->
                <div id="rsvpSuccess" class="hidden text-center py-4 space-y-2">
                    <div id="rsvpStatusIcon" class="text-2xl text-camel-500"></div>
                    <h3 id="rsvpTitle" class="font-editorial text-xl text-charcoal-900"></h3>
                    <p id="rsvpText" class="text-xs text-camel-600 font-light leading-relaxed"></p>
                    <button onclick="resetRSVP()" class="text-[10px] text-camel-400 uppercase tracking-widest underline pt-2 hover:text-camel-600 transition-colors">
                        Cavabı dəyişdir
                    </button>
                </div>

                <!-- RSVP FORM -->
                <form id="rsvpForm" onsubmit="submitRSVP(event)" class="space-y-4">
                    <div>
                        <label for="guestName" class="block text-[10px] uppercase tracking-widest text-camel-500 font-semibold mb-2">Ad və Soyadınız</label>
                        <input type="text" id="guestName" required placeholder="Adınız və Soyadınız"
                               class="w-full px-4 py-3 rounded-xl bg-chic-50/90 border border-camel-300/30 focus:border-camel-500 outline-none text-charcoal-900 text-xs placeholder-camel-300 transition-all shadow-sm">
                    </div>

                    <div>
                        <label class="block text-[10px] uppercase tracking-widest text-camel-500 font-semibold mb-2">Qərarınız</label>
                        <div class="grid grid-cols-1 gap-2">
                            <div class="rsvp-pill">
                                <input type="radio" id="attending" name="attendance" value="YES" checked class="hidden">
                                <label for="attending" class="w-full py-3 px-4 rounded-xl border border-camel-300/30 bg-chic-50/70 text-charcoal-900 text-xs font-medium text-center block cursor-pointer transition-all shadow-sm">
                                    ✨ Gələcəyəm
                                </label>
                            </div>
                            <div class="rsvp-pill">
                                <input type="radio" id="notAttending" name="attendance" value="NO" class="hidden">
                                <label for="notAttending" class="w-full py-3 px-4 rounded-xl border border-camel-300/30 bg-chic-50/70 text-charcoal-800 text-xs font-medium text-center block cursor-pointer transition-all shadow-sm">
                                    🤍 Təəssüf ki, gələ bilməyəcəm
                                </label>
                            </div>
                        </div>
                    </div>

                    <button type="submit" 
                            class="w-full py-3.5 rounded-xl bg-gradient-to-r from-camel-500 to-camel-600 text-chic-50 text-[11px] font-medium tracking-widest uppercase shadow-md hover:opacity-95 transition-all">
                        Təsdiq Et
                    </button>
                </form>
            </section>

            <!-- FOOTER -->
            <footer class="pt-2 border-t border-camel-300/20 text-center pb-2">
                <p class="text-[10px] text-camel-500 uppercase tracking-widest">Fuad & Sevinc • 16 Noyabr 2026</p>
            </footer>

        </div>

    </main>

    <!-- BACKGROUND AUDIO -->
    <audio id="bgAudio" loop preload="auto">
        <source src="https://cdn.pixabay.com/download/audio/2022/05/27/audio_1808fbf07a.mp3?filename=wedding-march-114407.mp3" type="audio/mpeg">
    </audio>

    <script>
        /* 1. PARTICLES ANIMATION (FLOATING CAMEL DUST) */
        const canvas = document.getElementById('particleCanvas');
        const ctx = canvas.getContext('2d');
        let particles = [];

        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        class Particle {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.size = Math.random() * 1.8 + 0.4;
                this.speedY = -(Math.random() * 0.3 + 0.1);
                this.speedX = (Math.random() - 0.5) * 0.2;
                this.opacity = Math.random() * 0.4 + 0.1;
            }
            update() {
                this.y += this.speedY;
                this.x += this.speedX;
                if (this.y < 0) {
                    this.y = canvas.height;
                    this.x = Math.random() * canvas.width;
                }
            }
            draw() {
                ctx.fillStyle = `rgba(193, 154, 107, ${this.opacity})`;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
            }
        }

        for (let i = 0; i < 40; i++) {
            particles.push(new Particle());
        }

        function animateParticles() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particles.forEach(p => {
                p.update();
                p.draw();
            });
            requestAnimationFrame(animateParticles);
        }
        animateParticles();

        /* ... existing code for countdown, audio & RSVP ... */

        /* RSVP CONFETTI COLOR CUSTOMIZATION */
        function submitRSVP(event) {
            event.preventDefault();
            const name = document.getElementById('guestName').value.trim();
            const attendance = document.querySelector('input[name="attendance"]:checked').value;

            if (!name) return;

            const form = document.getElementById('rsvpForm');
            const successBox = document.getElementById('rsvpSuccess');
            const icon = document.getElementById('rsvpStatusIcon');
            const title = document.getElementById('rsvpTitle');
            const text = document.getElementById('rsvpText');

            if (attendance === 'YES') {
                if (typeof confetti === 'function') {
                    confetti({
                        particleCount: 65,
                        spread: 60,
                        origin: { y: 0.7 },
                        colors: ['#C19A6B', '#8B5E34', '#A37C4E', '#EAE0D5']
                    });
                }
                icon.innerHTML = '<i class="fa-solid fa-sparkles"></i>';
                title.innerText = `Təşəkkür edirik, ${name}!`;
                text.innerText = "Sizi bu xüsusi günümüzdə yanımızda görməkdən sonsuz məmnunluq duyacağıq.";
            } else {
                icon.innerHTML = '<i class="fa-regular fa-heart"></i>';
                title.innerText = `Çox sağ olun, ${name}!`;
                text.innerText = "Diqqətiniz və xoş arzularınız üçün sizə təşəkkür edirik.";
            }

            form.classList.add('hidden');
            successBox.classList.remove('hidden');

            localStorage.setItem('fs_rsvp', JSON.stringify({ name, attendance }));
        }
<!-- ... existing code -->
