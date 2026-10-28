<!DOCTYPE html>
<html lang="az" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fuad & Sevinc — Toy Dəvətnaməsi</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;0,700;1,400;1,600&family=Great+Vibes&family=Montserrat:wght@300;400;500;600&display=swap" rel="stylesheet">
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        gold: {
                            100: '#fef9e7',
                            300: '#f3e5ab',
                            500: '#d4af37',
                            600: '#c5a028',
                            700: '#aa820a',
                        },
                        cream: '#fdfbf7',
                        blush: '#f9f3f0',
                        darkgreen: '#1a3323',
                    },
                    fontFamily: {
                        serif: ['"Cormorant Garamond"', 'serif'],
                        script: ['"Great Vibes"', 'cursive'],
                        sans: ['"Montserrat"', 'sans-serif'],
                    },
                    keyframes: {
                        float: {
                            '0%, 100%': { transform: 'translateY(0px)' },
                            '50%': { transform: 'translateY(-10px)' },
                        },
                        fadeIn: {
                            '0%': { opacity: '0', transform: 'translateY(15px)' },
                            '100%': { opacity: '1', transform: 'translateY(0)' },
                        },
                        pulseSlow: {
                            '0%, 100%': { opacity: '1', transform: 'scale(1)' },
                            '50%': { opacity: '0.85', transform: 'scale(1.03)' },
                        }
                    },
                    animation: {
                        float: 'float 4s ease-in-out infinite',
                        fadeIn: 'fadeIn 1.2s ease-out forwards',
                        pulseSlow: 'pulseSlow 3s ease-in-out infinite',
                    }
                }
            }
        }
    </script>
    <style>
        /* Custom scrollbar and ambient styles */
        ::-webkit-scrollbar {
            width: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #fdfbf7;
        }
        ::-webkit-scrollbar-thumb {
            background: #d4af37;
            border-radius: 3px;
        }
        
        .gold-border {
            border: 1px solid rgba(212, 175, 55, 0.3);
        }
        .gold-gradient-text {
            background: linear-gradient(135deg, #bf953f 0%, #fcf6ba 25%, #b38728 50%, #fbf5b7 75%, #aa771c 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        .gold-gradient-bg {
            background: linear-gradient(135deg, #d4af37 0%, #edd892 50%, #b38728 100%);
        }
        .luxury-card {
            background: rgba(253, 251, 247, 0.92);
            backdrop-filter: blur(10px);
            box-shadow: 0 15px 35px rgba(0,0,0,0.06), 0 5px 15px rgba(212,175,55,0.08);
        }
    </style>
</head>
<body class="bg-cream text-gray-800 font-sans antialiased selection:bg-gold-300 selection:text-darkgreen relative overflow-x-hidden">

    <!-- Musical Audio Control Button (Floating) -->
    <div class="fixed top-5 right-5 z-50">
        <button id="musicToggleBtn" onclick="toggleAudio()" class="w-12 h-12 rounded-full gold-gradient-bg text-white flex items-center justify-center shadow-lg hover:scale-105 transition-all duration-300 focus:outline-none" title="Musiqini Yandır/Söndür">
            <i id="musicIcon" class="fa-solid fa-music text-lg animate-pulse"></i>
        </button>
    </div>

    <!-- Background Decorative SVG Petals floating -->
    <div class="fixed inset-0 pointer-events-none z-0 opacity-20 overflow-hidden">
        <div class="absolute top-10 left-5 text-gold-500 text-4xl animate-float" style="animation-delay: 0s;"><i class="fa-solid fa-leaf"></i></div>
        <div class="absolute top-1/3 right-8 text-gold-500 text-3xl animate-float" style="animation-delay: 1.5s;"><i class="fa-solid fa-heart"></i></div>
        <div class="absolute bottom-1/4 left-10 text-gold-500 text-4xl animate-float" style="animation-delay: 0.8s;"><i class="fa-solid fa-spa"></i></div>
    </div>

    <!-- Main Wrapper Container -->
    <main class="max-w-3xl mx-auto min-h-screen px-4 py-8 relative z-10 flex flex-col justify-between">

        <!-- HEADER / HERO SECTION -->
        <header class="text-center pt-8 pb-6 animate-fadeIn">
            <!-- Ornamental Monogram Icon -->
            <div class="inline-flex items-center justify-center w-20 h-20 rounded-full border-2 border-gold-500/40 p-2 mb-4 bg-white/50 shadow-inner">
                <div class="w-full h-full rounded-full border border-gold-500/80 flex items-center justify-center">
                    <span class="font-serif text-2xl font-bold text-gold-600 tracking-wider">F & S</span>
                </div>
            </div>

            <!-- Monogram Subtitle -->
            <p class="font-sans text-xs uppercase tracking-[0.3em] text-gold-700 font-semibold mb-2">Toy Dəvətnaməsi</p>

            <!-- Main Couple Names -->
            <h1 class="font-script text-6xl md:text-8xl text-darkgreen my-2 leading-tight drop-shadow-sm">
                Fuad <span class="font-serif text-3xl md:text-5xl italic text-gold-500 font-light">&</span> Sevinc
            </h1>

            <!-- Floral Divider -->
            <div class="flex items-center justify-center space-x-3 my-4">
                <div class="h-[1px] w-16 bg-gradient-to-r from-transparent to-gold-500"></div>
                <i class="fa-solid fa-gem text-gold-500 text-xs"></i>
                <div class="h-[1px] w-16 bg-gradient-to-l from-transparent to-gold-500"></div>
            </div>

            <!-- Date Display Header -->
            <p class="font-serif text-2xl md:text-3xl text-gray-700 font-medium tracking-wide">
                16 Noyabr 2026
            </p>
            <p class="font-sans text-sm text-gold-700 mt-1 tracking-widest font-medium">SAAT 18:00</p>
        </header>


        <!-- OPENING INVITATION TEXT CARD -->
        <section class="my-6 luxury-card rounded-2xl p-6 md:p-10 border border-gold-500/30 text-center relative overflow-hidden animate-fadeIn shadow-xl">
            <!-- Frame Corner Accents -->
            <div class="absolute top-2 left-2 w-6 h-6 border-t-2 border-l-2 border-gold-500/50"></div>
            <div class="absolute top-2 right-2 w-6 h-6 border-t-2 border-r-2 border-gold-500/50"></div>
            <div class="absolute bottom-2 left-2 w-6 h-6 border-b-2 border-l-2 border-gold-500/50"></div>
            <div class="absolute bottom-2 right-2 w-6 h-6 border-b-2 border-r-2 border-gold-500/50"></div>

            <i class="fa-solid fa-quote-left text-3xl text-gold-500/30 mb-4 block"></i>
            <p class="font-serif text-xl md:text-2xl italic leading-relaxed text-gray-800 px-2 md:px-6">
                "Həyatımızın ən xoşbəxt gününün başlanğıcında yanımızda olmağınız və bu sevincə şərik çıxmağınız bizə sonsuz qürur verər."
            </p>
            <i class="fa-solid fa-quote-right text-3xl text-gold-500/30 mt-4 block"></i>
        </section>


        <!-- COUNTDOWN TIMER SECTION -->
        <section class="my-8 text-center">
            <h2 class="font-serif text-2xl text-darkgreen font-semibold mb-6 flex items-center justify-center gap-2">
                <i class="fa-regular fa-clock text-gold-500 text-xl"></i>
                Toy Gününə Qalan Vaxt
            </h2>
            
            <div class="grid grid-cols-4 gap-2 md:gap-4 max-w-lg mx-auto">
                <div class="luxury-card rounded-xl p-3 md:p-4 border border-gold-300">
                    <span id="days" class="font-serif text-2xl md:text-4xl font-bold text-gold-600 block">00</span>
                    <span class="text-[10px] md:text-xs uppercase tracking-wider text-gray-500 font-medium">Gün</span>
                </div>
                <div class="luxury-card rounded-xl p-3 md:p-4 border border-gold-300">
                    <span id="hours" class="font-serif text-2xl md:text-4xl font-bold text-gold-600 block">00</span>
                    <span class="text-[10px] md:text-xs uppercase tracking-wider text-gray-500 font-medium">Saat</span>
                </div>
                <div class="luxury-card rounded-xl p-3 md:p-4 border border-gold-300">
                    <span id="minutes" class="font-serif text-2xl md:text-4xl font-bold text-gold-600 block">00</span>
                    <span class="text-[10px] md:text-xs uppercase tracking-wider text-gray-500 font-medium">Dəqiqə</span>
                </div>
                <div class="luxury-card rounded-xl p-3 md:p-4 border border-gold-300">
                    <span id="seconds" class="font-serif text-2xl md:text-4xl font-bold text-gold-600 block">00</span>
                    <span class="text-[10px] md:text-xs uppercase tracking-wider text-gray-500 font-medium">Saniyə</span>
                </div>
            </div>
        </section>


        <!-- EVENT DETAILS & NAVIGATION MAP LINKS -->
        <section class="my-8 luxury-card rounded-2xl p-6 md:p-8 border border-gold-500/30 text-center shadow-lg">
            <div class="w-12 h-12 mx-auto rounded-full bg-gold-100 flex items-center justify-center text-gold-600 mb-4 text-xl">
                <i class="fa-solid fa-location-dot"></i>
            </div>
            
            <h2 class="font-serif text-3xl font-bold text-darkgreen mb-1">Golden Ring</h2>
            <p class="font-sans text-xs uppercase tracking-widest text-gold-600 font-semibold mb-4">Şadlıq Sarayı</p>

            <div class="space-y-2 text-gray-700 font-medium my-4">
                <p class="flex items-center justify-center gap-2">
                    <i class="fa-regular fa-calendar-check text-gold-600"></i>
                    <span>16 Noyabr 2026, Bazar ertəsi</span>
                </p>
                <p class="flex items-center justify-center gap-2">
                    <i class="fa-regular fa-clock text-gold-600"></i>
                    <span>Qonaqların qarşılanması: Saat 18:00</span>
                </p>
            </div>

            <!-- Navigation Buttons -->
            <div class="mt-6 pt-6 border-t border-gold-200/80">
                <p class="text-sm text-gray-600 mb-4 font-medium">Məkana rahat çatmanız üçün naviqasiya seçin:</p>
                
                <div class="flex flex-col sm:flex-row items-center justify-center gap-3">
                    <!-- Google Maps Button -->
                    <a href="https://maps.app.goo.gl/2Rz43K1oTn1Wor3w9?g_st=ic" target="_blank" rel="noopener noreferrer" 
                       class="w-full sm:w-auto px-6 py-3 rounded-xl bg-white border border-gray-300 text-gray-700 font-medium flex items-center justify-center gap-3 shadow-sm hover:border-gold-500 hover:text-gold-600 transition-all duration-300">
                        <i class="fa-brands fa-google text-red-500 text-lg"></i>
                        <span>Google Maps ilə Aç</span>
                    </a>

                    <!-- Waze Button -->
                    <a href="https://waze.com/ul/htp5tb6n4b" target="_blank" rel="noopener noreferrer" 
                       class="w-full sm:w-auto px-6 py-3 rounded-xl bg-sky-500 text-white font-medium flex items-center justify-center gap-3 shadow-md hover:bg-sky-600 transition-all duration-300">
                        <i class="fa-brands fa-waze text-xl"></i>
                        <span>Waze ilə Naviqasiya</span>
                    </a>
                </div>
            </div>
        </section>


        <!-- RSVP / CONFIRMATION FORM SECTION -->
        <section class="my-8 luxury-card rounded-2xl p-6 md:p-8 border border-gold-500/30 shadow-lg">
            <div class="text-center mb-6">
                <div class="w-12 h-12 mx-auto rounded-full bg-gold-100 flex items-center justify-center text-gold-600 mb-3 text-xl">
                    <i class="fa-solid fa-envelope-open-text"></i>
                </div>
                <h2 class="font-serif text-3xl font-bold text-darkgreen">İştirak Təsdiqi (RSVP)</h2>
                <p class="text-sm text-gray-600 mt-1">Zəhmət olmasa toyda iştirak edəcəyinizi öncədən bildirin</p>
            </div>

            <form id="rsvpForm" onsubmit="handleRSVP(event)" class="space-y-4 max-w-md mx-auto">
                <div>
                    <label for="guestName" class="block text-xs font-semibold uppercase tracking-wider text-gray-700 mb-1">Adınız və Soyadınız</label>
                    <input type="text" idguestName id="guestName" required placeholder="Məsələn: Əli Əliyev" 
                           class="w-full px-4 py-3 rounded-xl border border-gold-300 focus:ring-2 focus:ring-gold-500 focus:border-transparent outline-none bg-white text-gray-800 text-sm">
                </div>

                <div>
                    <label class="block text-xs font-semibold uppercase tracking-wider text-gray-700 mb-1">İştirak vəziyyəti</label>
                    <div class="grid grid-cols-2 gap-3">
                        <label class="flex items-center justify-center p-3 rounded-xl border border-gold-300 cursor-pointer bg-white hover:bg-gold-50 transition-colors">
                            <input type="radio" name="attendance" value="Gələcəyəm" checked class="text-gold-600 focus:ring-gold-500">
                            <span class="ml-2 text-sm font-medium text-gray-700">Gələcəyəm</span>
                        </label>
                        <label class="flex items-center justify-center p-3 rounded-xl border border-gold-300 cursor-pointer bg-white hover:bg-gold-50 transition-colors">
                            <input type="radio" name="attendance" value="Gələ bilməyəcəyəm" class="text-gold-600 focus:ring-gold-500">
                            <span class="ml-2 text-sm font-medium text-gray-700">Gələ bilməyəcəyəm</span>
                        </label>
                    </div>
                </div>

                <div>
                    <label for="guestCount" class="block text-xs font-semibold uppercase tracking-wider text-gray-700 mb-1">Qonaq Sayı</label>
                    <select id="guestCount" class="w-full px-4 py-3 rounded-xl border border-gold-300 focus:ring-2 focus:ring-gold-500 focus:border-transparent outline-none bg-white text-gray-800 text-sm">
                        <option value="1 nəfər">Tək (1 nəfər)</option>
                        <option value="2 nəfər">2 nəfər</option>
                        <option value="Ailəvi">Ailəvi</option>
                    </select>
                </div>

                <div>
                    <label for="guestNote" class="block text-xs font-semibold uppercase tracking-wider text-gray-700 mb-1">Cütlüyə Ürək Sözləriniz (İstəyə bağlı)</label>
                    <textarea id="guestNote" rows="2" placeholder="Təbriklərinizi yazın..." 
                              class="w-full px-4 py-3 rounded-xl border border-gold-300 focus:ring-2 focus:ring-gold-500 focus:border-transparent outline-none bg-white text-gray-800 text-sm resize-none"></textarea>
                </div>

                <button type="submit" class="w-full py-3.5 rounded-xl gold-gradient-bg text-white font-semibold text-sm tracking-wide shadow-lg hover:opacity-95 transition-all duration-300 flex items-center justify-center gap-2">
                    <i class="fa-brands fa-whatsapp text-lg"></i>
                    <span>Təsdiqi WhatsApp ilə Göndər</span>
                </button>
            </form>
        </section>


        <!-- CALENDAR ADD EVENT BUTTON SECTION -->
        <section class="my-6 text-center">
            <button onclick="addToCalendar()" class="inline-flex items-center gap-2 text-sm font-medium text-gold-700 hover:text-gold-600 underline underline-offset-4 transition-colors">
                <i class="fa-regular fa-calendar-plus"></i>
                <span>Təqvimə əlavə et (Google Calendar)</span>
            </button>
        </section>


        <!-- FOOTER -->
        <footer class="text-center py-8 mt-4 border-t border-gold-200/60">
            <p class="font-script text-3xl text-gold-600">Fuad & Sevinc</p>
            <p class="text-xs text-gray-500 mt-1">Sizi yanımızda görməkdən şad olarıq!</p>
            <p class="text-[10px] text-gray-400 mt-4">16 Noyabr 2026 • Golden Ring Şadlıq Sarayı</p>
        </footer>

    </main>

    <!-- AUDIO SOURCE FOR BACKGROUND MUSIC (Romantic Wedding Instrumental) -->
    <audio id="bgAudio" loop preload="auto">
        <source src="https://cdn.pixabay.com/download/audio/2022/05/27/audio_1808fbf07a.mp3?filename=wedding-march-114407.mp3" type="audio/mpeg">
    </audio>

    <!-- JAVASCRIPT LOGIC -->
    <script>
        // Target Wedding Date: November 16, 2026, 18:00:00
        const weddingDate = new Date('2026-11-16T18:00:00').getTime();

        function updateCountdown() {
            const now = new Date().getTime();
            const difference = weddingDate - now;

            if (difference > 0) {
                const days = Math.floor(difference / (1000 * 60 * 60 * 24));
                const hours = Math.floor((difference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                const minutes = Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60));
                const seconds = Math.floor((difference % (1000 * 60)) / 1000);

                document.getElementById('days').innerText = days < 10 ? '0' + days : days;
                document.getElementById('hours').innerText = hours < 10 ? '0' + hours : hours;
                document.getElementById('minutes').innerText = minutes < 10 ? '0' + minutes : minutes;
                document.getElementById('seconds').innerText = seconds < 10 ? '0' + seconds : seconds;
            } else {
                document.getElementById('days').innerText = '00';
                document.getElementById('hours').innerText = '00';
                document.getElementById('minutes').innerText = '00';
                document.getElementById('seconds').innerText = '00';
            }
        }

        // Run Timer
        setInterval(updateCountdown, 1000);
        updateCountdown();

        // Audio Music Control Logic
        let isPlaying = false;
        const audio = document.getElementById('bgAudio');
        const musicIcon = document.getElementById('musicIcon');

        function toggleAudio() {
            if (isPlaying) {
                audio.pause();
                musicIcon.className = "fa-solid fa-music text-lg";
                isPlaying = false;
            } else {
                audio.play().then(() => {
                    musicIcon.className = "fa-solid fa-volume-high text-lg animate-bounce";
                    isPlaying = true;
                }).catch(err => {
                    console.log("Audio playback blocked or failed: ", err);
                });
            }
        }

        // WhatsApp RSVP Handler Function
        function handleRSVP(event) {
            event.preventDefault();
            
            const name = document.getElementById('guestName').value.trim();
            const attendance = document.querySelector('input[name="attendance"]:checked').value;
            const count = document.getElementById('guestCount').value;
            const note = document.getElementById('guestNote').value.trim();

            if (!name) return;

            // Constructing WhatsApp message
            let message = `Salam! Mən, ${name}.\n\n`;
            message += `Fuad & Sevinc cütlüyünün toy dəvətnaməsinə cavabım:\n`;
            message += `• İştirak: ${attendance}\n`;
            if (attendance === "Gələcəyəm") {
                message += `• Qonaq sayı: ${count}\n`;
            }
            if (note) {
                message += `• Təbrik və qeyd: ${note}\n`;
            }

            // Encoded WhatsApp Web URL
            const whatsappUrl = `https://api.whatsapp.com/send?text=${encodeURIComponent(message)}`;
            
            // Open WhatsApp link
            window.open(whatsappUrl, '_blank');
        }

        // Google Calendar Add Event Function
        function addToCalendar() {
            const title = encodeURIComponent("Fuad & Sevinc Toy Mərasimi");
            const details = encodeURIComponent("Həyatımızın ən xoşbəxt gününün başlanğıcında yanımızda olmağınız bizə sonsuz qürur verər. Məkan: Golden Ring Şadlıq Sarayı.");
            const location = encodeURIComponent("Golden Ring Şadlıq Sarayı, Bakı");
            
            // 16 Nov 2026 18:00 to 23:00 UTC/Local estimation
            const googleCalendarUrl = `https://calendar.google.com/calendar/render?action=TEMPLATE&text=${title}&dates=20261116T140000Z/20261116T190000Z&details=${details}&location=${location}`;
            
            window.open(googleCalendarUrl, '_blank');
        }
    </script>
</body>
</html>
