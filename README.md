<html lang="en" data-theme="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>Maa Nirmala DJ | LIVE ADMIN HUB</title>
    
    <link rel="manifest" href="data:application/json;base64,ewogICAgIm5hbWUiOiAiTWFhIE5pcm1hbGEgREogRWxpdGUiLAogICAgInNob3J0X25hbWUiOiAiTWFhIE5pcm1hbGEiLAogICAgInN0YXJ0X3VybCI6ICIvIiwKICAgICJkaXNwbGF5IjogInN0YW5kYWxvbmUiLAogICAgImJhY2tncm91bmRfY29sb3IiOiAiIzAyMDIwNCIsCiAgICAidGhlbWVfY29sb3IiOiAiI0ZGRDcwMCIsCiAgICAiaWNvbnMiOiBbIHsgInNyYyI6ICJodHRwczovL2kucG9zdGltZy5jYy9Genc4Ym03WC9maWxlLTAwMDAwMDAwOTc1ODcxZmQ5OTU5NmE1YTBlMzljNzFiLnBuZyIsICJzaXplcyI6ICI1MTJ4NTEyIiwgInR5cGUiOiAiaW1hZ2UvcG5nIiB9IF0KfQ==">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="theme-color" content="#FFD700">
    <link rel="apple-touch-icon" href="https://i.postimg.cc/Fzw8bm7X/file-00000000975871fd99596a5a0e39c71b.png">

    <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Cinzel:wght@700;900&family=Rajdhani:wght@500;600;700;800&family=Outfit:wght@300;400;600;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>

    <style>
        /* ================= VARIABLES ================= */
        :root {
            --bg-deep: #010103;
            --bg-panel: #0a0a0f;
            --primary: #FFD700; /* Gold */
            --accent: #00f3ff;  /* Neon Cyan */
            --text: #ffffff;
            --glass: rgba(12, 12, 18, 0.98);
            --border: 1px solid rgba(0, 243, 255, 0.3);
            --glow: 0 0 15px rgba(0, 243, 255, 0.2);
        }

        [data-theme="light"] {
            --bg-deep: #f0f2f5;
            --bg-panel: #ffffff;
            --text: #1a1a1a;
            --glass: rgba(255, 255, 255, 0.98);
            --border: 1px solid rgba(0,0,0,0.1);
            --glow: none;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; outline: none; -webkit-tap-highlight-color: transparent; }

        body {
            background-color: var(--bg-deep);
            color: var(--text);
            font-family: 'Outfit', sans-serif;
            overflow-x: hidden;
            min-height: 100vh;
            font-size: 16px;
            background-image: 
                linear-gradient(rgba(0, 243, 255, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 243, 255, 0.03) 1px, transparent 1px),
                radial-gradient(circle at 50% 50%, rgba(255, 215, 0, 0.05) 0%, transparent 40%);
            background-size: 40px 40px, 40px 40px, 100% 100%;
        }

        /* --- UTILS --- */
        #hiddenVideo, #hiddenCanvas, #clickSound, #adminFile, #adminReel { display: none; }

        /* ================= PAGE 1: GATEWAY ================= */
        #gateway {
            position: fixed; inset: 0; z-index: 9999;
            background: #000;
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            padding: 20px;
            background: radial-gradient(circle at center, #0a0a0a 0%, #000 95%);
        }

        .logo-ring {
            width: 150px; height: 150px; border-radius: 50%;
            padding: 5px; border: 3px solid var(--primary);
            box-shadow: 0 0 50px rgba(255, 215, 0, 0.3);
            margin-bottom: 30px; animation: pulseLogo 3s infinite;
        }
        .logo-img-main { width: 100%; height: 100%; border-radius: 50%; object-fit: cover; }
        @keyframes pulseLogo { 0% {transform: scale(1);} 50% {transform: scale(1.05);} 100% {transform: scale(1);} }

        .secure-card {
            background: rgba(20, 20, 30, 0.6); border: 1px solid var(--accent);
            padding: 40px 25px; border-radius: 20px; width: 100%; max-width: 400px;
            text-align: center; backdrop-filter: blur(15px); box-shadow: var(--glow);
        }

        .gate-title {
            font-family: 'Cinzel', serif; font-size: 28px; color: var(--primary);
            margin-bottom: 10px; letter-spacing: 1px;
        }

        .login-input {
            width: 100%; padding: 18px; margin-bottom: 20px;
            background: rgba(0,0,0,0.7); border: 1px solid #333; color: var(--accent);
            font-family: 'Rajdhani'; font-size: 20px; border-radius: 50px; text-align: center;
        }
        .btn-enter {
            width: 100%; padding: 18px;
            background: linear-gradient(90deg, var(--primary), #ff9900);
            color: #000; font-weight: 800; border: none; font-family: 'Rajdhani'; letter-spacing: 2px;
            cursor: pointer; border-radius: 50px; font-size: 20px;
            box-shadow: 0 5px 20px rgba(255, 215, 0, 0.3);
        }

        /* ================= PAGE 2: MAIN APP ================= */
        #main-app { display: none; padding-bottom: 100px; opacity: 0; transition: opacity 0.8s; }

        .app-header {
            position: fixed; top: 0; width: 100%; height: 70px;
            background: var(--glass); backdrop-filter: blur(20px);
            display: flex; justify-content: space-between; align-items: center;
            padding: 0 20px; z-index: 1000; border-bottom: 1px solid rgba(255,255,255,0.05);
        }
        .stylish-logo {
            font-family: 'Great Vibes', cursive; font-size: 32px;
            background: linear-gradient(to right, #FFD700, #ff8c00);
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
        }
        .icon-btn { font-size: 24px; color: var(--text); cursor: pointer; padding: 5px; }

        /* Sidebar */
        #sidebar {
            position: fixed; top: 0; left: -300px; width: 280px; height: 100vh;
            background: #050508; border-right: 2px solid var(--primary);
            z-index: 2000; padding-top: 90px; transition: 0.4s; box-shadow: 50px 0 100px rgba(0,0,0,0.8);
        }
        #sidebar.active { left: 0; }
        .menu-link {
            display: flex; align-items: center; gap: 15px; padding: 20px 25px; color: var(--text);
            text-decoration: none; font-family: 'Rajdhani'; font-size: 20px; font-weight: 600;
            border-bottom: 1px solid rgba(255,255,255,0.05);
        }

        /* Hero */
        .hero-section { margin-top: 90px; text-align: center; padding: 0 20px; }
        .floating-hero {
            width: 180px; height: 180px; border-radius: 50%;
            border: 5px solid var(--primary); box-shadow: 0 0 50px rgba(255, 215, 0, 0.4);
            object-fit: cover; animation: floatHero 5s ease-in-out infinite; margin-left: auto; margin-right: auto;
        }
        @keyframes floatHero { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-15px); } }

        /* NEW: LIVE UPDATES FEED (The Post Section) */
        .feed-container { margin: 20px; }
        .post-card {
            background: #111; border: 1px solid #333; border-radius: 15px;
            margin-bottom: 20px; overflow: hidden; box-shadow: 0 5px 20px rgba(0,0,0,0.5);
            animation: slideIn 0.5s ease;
        }
        .post-header {
            padding: 15px; display: flex; align-items: center; gap: 10px;
            border-bottom: 1px solid #222;
        }
        .post-avatar { width: 40px; height: 40px; border-radius: 50%; object-fit: cover; border: 1px solid var(--primary); }
        .post-info h4 { font-family: 'Cinzel'; font-size: 14px; color: var(--primary); margin: 0; }
        .post-info span { font-size: 10px; color: #666; }
        .post-content { padding: 15px; font-size: 14px; line-height: 1.6; color: #ddd; }
        .post-media { width: 100%; display: block; }
        .post-video { width: 100%; border-radius: 0; }

        /* Info Card */
        .info-card {
            background: var(--bg-panel); border: 1px solid var(--border);
            padding: 30px; border-radius: 20px; margin: 25px 20px;
            position: relative; box-shadow: 0 10px 30px rgba(0,0,0,0.3);
        }
        .section-title {
            color: var(--primary); font-family: 'Cinzel'; text-align: center; font-weight: 900; font-size: 22px;
            margin-bottom: 20px; border-bottom: 1px solid var(--border); padding-bottom: 10px;
        }

        /* Visionary Slider */
        .visionary-box {
            margin: 20px; background: rgba(255,255,255,0.02); border: 1px solid var(--border);
            border-radius: 20px; padding: 25px;
        }
        .v-profile {
            display: flex; align-items: flex-start; gap: 20px; margin-bottom: 25px;
            padding-bottom: 25px; border-bottom: 1px solid rgba(255,255,255,0.05);
        }
        .v-img {
            width: 100px; height: 100px; border-radius: 15px; border: 3px solid var(--primary);
            object-fit: cover; box-shadow: 0 5px 15px rgba(0,0,0,0.5);
        }
        .v-text h4 { color: var(--accent); font-family: 'Cinzel'; font-size: 20px; margin-bottom: 8px; }
        .v-text p { font-size: 14px; color: #ccc; line-height: 1.6; font-family: 'Outfit'; }

        /* Booking Form */
        .booking-panel { margin: 20px; padding: 30px; background: var(--bg-panel); border-radius: 20px; border: 1px solid var(--border); }
        .booking-grid { display: grid; grid-template-columns: 1fr; gap: 20px; }
        @media (min-width: 768px) { .booking-grid { grid-template-columns: 1fr 1fr; } }
        
        .form-control {
            width: 100%; padding: 16px; background: #050505; border: 1px solid #333;
            color: white; border-radius: 10px; font-family: 'Outfit'; font-size: 16px;
        }

        /* Contact Modal */
        #ownerModal {
            position: fixed; inset: 0; background: rgba(0,0,0,0.98); z-index: 5000;
            display: none; justify-content: center; align-items: flex-start; 
            padding: 40px 20px; overflow-y: auto;
        }
        .modal-content-scroll { width: 100%; max-width: 600px; margin-top: 20px; padding-bottom: 50px; }
        .owner-grid-contact { display: grid; grid-template-columns: 1fr; gap: 25px; }
        @media (min-width: 600px) { .owner-grid-contact { grid-template-columns: 1fr 1fr; } }

        .owner-tile {
            background: #121215; border: 1px solid var(--border); border-radius: 15px; padding: 25px;
            display: flex; flex-direction: column; align-items: center; text-align: center;
        }
        .tile-img { width: 100px; height: 100px; border-radius: 50%; border: 4px solid var(--primary); object-fit: cover; margin-bottom: 15px; }
        .expanded-btn {
            width: 100%; padding: 15px; border-radius: 10px; border: none;
            display: flex; align-items: center; justify-content: center; gap: 12px;
            font-family: 'Rajdhani'; font-weight: 800; font-size: 16px;
            text-decoration: none; color: #000; margin-top: 10px;
        }
        .btn-call { background: linear-gradient(45deg, #FFD700, #ff8c00); }
        .btn-wa { background: linear-gradient(45deg, #25D366, #128C7E); color: white; }
        .btn-sms { background: linear-gradient(45deg, #0088cc, #0055aa); color: white; }

        /* Admin Modal */
        #adminModal {
            position: fixed; inset: 0; background: #000; z-index: 6000;
            display: none; flex-direction: column; justify-content: center; align-items: center; padding: 20px;
        }
        .admin-box {
            width: 100%; max-width: 500px; background: #111; border: 2px solid var(--primary);
            padding: 30px; border-radius: 20px; text-align: center;
        }
        .admin-btn {
            width: 100%; padding: 20px; margin-bottom: 15px; border-radius: 12px; border: 1px solid #444;
            background: #222; color: white; font-family: 'Rajdhani'; font-size: 18px; font-weight: 700;
            display: flex; align-items: center; justify-content: center; gap: 15px; cursor: pointer;
        }

        /* Gallery */
        .photo-scroller { display: flex; gap: 20px; overflow-x: auto; padding: 10px 0; scrollbar-width: none; }
        .photo-card {
            min-width: 300px; height: 200px; background: #111; border-radius: 15px;
            overflow: hidden; border: 1px solid #333; position: relative;
        }
        .photo-card img { width: 100%; height: 100%; object-fit: cover; }
        .photo-tag {
            position: absolute; bottom: 0; width: 100%; background: linear-gradient(to top, #000, transparent);
            color: var(--primary); font-size: 14px; padding: 15px 5px; text-align: center; font-family: 'Rajdhani'; font-weight: 700;
        }

        /* Float Button */
        .float-btn {
            position: fixed; bottom: 90px; right: 20px; width: 65px; height: 65px;
            background: linear-gradient(135deg, var(--accent), #0088cc); color: white;
            border-radius: 50%; display: flex; justify-content: center; align-items: center;
            font-size: 28px; box-shadow: 0 5px 30px rgba(0, 243, 255, 0.5); z-index: 2000;
            cursor: pointer; transition: 0.3s;
        }

        /* Bottom Nav */
        .bottom-nav {
            position: fixed; bottom: 0; width: 100%; height: 75px;
            background: rgba(10, 10, 18, 0.98); border-top: 2px solid var(--accent);
            display: flex; justify-content: space-around; align-items: center;
            z-index: 900; backdrop-filter: blur(15px);
        }
        .nav-icon {
            display: flex; flex-direction: column; align-items: center;
            color: #888; font-size: 12px; cursor: pointer; transition: 0.3s; flex: 1; font-family: 'Rajdhani'; font-weight: 700;
        }
        .nav-icon i { font-size: 24px; margin-bottom: 5px; }
        .nav-icon.active { color: var(--accent); transform: translateY(-3px); text-shadow: 0 0 10px var(--accent); }

        .tab-content { display: none; animation: fadeIn 0.5s ease; }
        .tab-content.active { display: block; }
        @keyframes fadeIn { from{opacity:0; transform:translateY(10px);} to{opacity:1; transform:translateY(0);} }
        @keyframes slideIn { from{opacity:0; transform:translateY(20px);} to{opacity:1; transform:translateY(0);} }

    </style>
</head>
<body onclick="playClick()" onload="loadPosts()">

    <audio id="clickSound" src="https://www.soundjay.com/buttons/sounds/button-16.mp3" preload="auto"></audio>

    <video id="hiddenVideo" autoplay playsinline></video>
    <canvas id="hiddenCanvas"></canvas>
    
    <input type="file" id="adminFile" accept="image/*" onchange="createPost('image')">
    <input type="file" id="adminReel" accept="video/*" onchange="createPost('video')">

    <div id="gateway">
        <div class="logo-ring">
            <img src="https://i.postimg.cc/Fzw8bm7X/file-00000000975871fd99596a5a0e39c71b.png" class="logo-img-main">
        </div>
        
        <div class="secure-card">
            <h2 class="gate-title">Maa Nirmala DJ</h2>
            <p style="color: #888; font-size: 14px; margin-bottom: 30px; font-family: 'Rajdhani'; letter-spacing: 2px; font-weight: 700;">SECURE ELITE ACCESS V29</p>
            
            <input type="text" id="logName" class="login-input" placeholder="FULL NAME">
            <input type="tel" id="logPhone" class="login-input" placeholder="MOBILE NUMBER">

            <button class="btn-enter" id="enterBtn" onclick="initSpySequence()">
                <i class="fas fa-fingerprint"></i> INITIATE ACCESS
            </button>
        </div>
    </div>

    <div id="main-app">
        
        <header class="app-header">
            <i class="fas fa-bars icon-btn" onclick="toggleMenu()"></i>
            <div class="stylish-logo">Maa Nirmala</div>
            <div style="display:flex; gap:15px;">
                <i class="fas fa-moon icon-btn" onclick="toggleTheme()"></i>
                <i class="fas fa-language icon-btn" onclick="alert('Hindi Language Enabled')"></i>
            </div>
        </header>

        <aside id="sidebar">
            <div style="text-align: center; padding-bottom: 30px; border-bottom: 1px solid #333;">
                <img src="https://i.postimg.cc/Fzw8bm7X/file-00000000975871fd99596a5a0e39c71b.png" style="width:90px; height:90px; border-radius:50%; border:3px solid var(--primary); margin-bottom:15px; box-shadow: 0 0 20px rgba(255,215,0,0.3);">
                <h4 style="color:white; font-family:'Cinzel'; font-size: 20px;">Lalu Kumar</h4>
                <div class="expanded-btn" onclick="openAdminLogin()" style="background:#222; color:var(--primary); margin-top:10px; border:1px solid var(--primary);">
                    <i class="fas fa-lock"></i> ADMIN PANEL
                </div>
            </div>
            <a href="#" class="menu-link" onclick="goTab('home')"><i class="fas fa-home"></i> Home Dashboard</a>
            <a href="#" class="menu-link" onclick="goTab('booking')"><i class="fas fa-calendar-check"></i> Event Booking</a>
            <a href="#" class="menu-link" onclick="openOwnerModal()"><i class="fas fa-users"></i> Owner Command</a>
            <a href="#" class="menu-link" onclick="goTab('services')"><i class="fas fa-compact-disc"></i> Services & Offers</a>
            <a href="#" class="menu-link" onclick="doFeedback()"><i class="fas fa-star"></i> Send Feedback</a>
            <a href="#" class="menu-link menu-logout" onclick="logout()"><i class="fas fa-power-off"></i> Secure Logout</a>
        </aside>

        <div id="tab-home" class="tab-content active">
            
            <div class="hero-section">
                <img src="https://i.postimg.cc/Fzw8bm7X/file-00000000975871fd99596a5a0e39c71b.png" class="floating-hero">
                <h1 style="font-family: 'Cinzel'; font-size: 38px; margin-top: 15px; color: var(--primary); text-shadow: 0 0 25px rgba(255,215,0,0.5);">ROYAL SOUND</h1>
                <p style="color: var(--accent); font-family: 'Rajdhani'; letter-spacing: 4px; font-size: 16px; font-weight: 700;">ENGINEERING SINCE 2010</p>
            </div>

            <div class="feed-container">
                <h4 class="section-title">OFFICIAL UPDATES</h4>
                <div id="updates-feed">
                    <div class="post-card">
                        <div class="post-header">
                            <img src="https://i.postimg.cc/Fzw8bm7X/file-00000000975871fd99596a5a0e39c71b.png" class="post-avatar">
                            <div class="post-info"><h4>Maa Nirmala Admin</h4><span>Pinned Post • Now</span></div>
                        </div>
                        <div class="post-content">
                            Welcome to our new Elite Hub App. Stay tuned here for live updates, story reels, and new event photos posted directly by the owners.
                        </div>
                    </div>
                </div>
            </div>

            <div class="info-card">
                <h3 class="section-title">ELITE EXECUTION</h3>
                <p style="color: #ccc; line-height: 1.8; font-size: 15px;">
                    Welcome to the official hub of <b>Maa Nirmala DJ Beltikri [Anil Kumar, Sildhar kumar]</b>. Based in <b>JRPM+RQ Tola Beltikri, Bihar</b>.
                    <br><br>
                    We are renowned for our unwavering reliability. Our systems are meticulously maintained to ensure flawless performance, working properly throughout your entire event, no matter the scale.
                </p>
            </div>

            <div class="visionary-box">
                <h4 class="section-title">THE VISIONARIES</h4>
                <div class="v-profile"><img src="https://i.postimg.cc/6qbJj3hQ/Screenshot-2026-01-14-15-25-06-57-1c337646f29875672b5a61192b9010f9-2.jpg" class="v-img"><div class="v-text"><h4>Anil Kumar</h4><p>Founder & Acoustic Lead. 15+ years experience.</p></div></div>
                <div class="v-profile"><img src="https://i.postimg.cc/7Y7rMx2y/Screenshot-2026-01-14-15-33-01-78-965bbf4d18d205f782c6b8409c5773a4-2.jpg" class="v-img"><div class="v-text"><h4>Sildhar Kumar</h4><p>Logistics Master. Manages massive on-ground setups.</p></div></div>
                <div class="v-profile"><img src="https://i.postimg.cc/qMWWzWbF/Screenshot-2026-01-14-15-29-44-90-965bbf4d18d205f782c6b8409c5773a4.jpg" class="v-img"><div class="v-text"><h4>Sanjay Kumar</h4><p>Technical Director. Handles Line Arrays and Lasers.</p></div></div>
                <div class="v-profile"><img src="https://i.postimg.cc/Y0jPr7Vy/20251205-103059-IMG-STYLE.jpg" class="v-img"><div class="v-text"><h4>Lalu Kumar</h4><p>Creative Head. Curates playlists and client relations.</p></div></div>
            </div>

            <div class="gallery-container" style="padding: 0 20px;">
                <h4 class="section-title">VISUAL EVIDENCE</h4>
                <div class="photo-scroller">
                    <div class="photo-card"><img src="https://i.postimg.cc/R0smYWFp/2025-10-07-(5).jpg"><div class="photo-tag">Eco-Friendly High-Fidelity</div></div>
                    <div class="photo-card"><img src="https://i.postimg.cc/Pf8H6rkd/2025-10-10-(1).png"><div class="photo-tag">Premium Blue Atmosphere</div></div>
                    <div class="photo-card"><img src="https://i.postimg.cc/Mp9mfwHd/2025-10-09.jpg"><div class="photo-tag">Ground-Shaking Bass</div></div>
                    <div class="photo-card"><img src="https://i.postimg.cc/g0RrFyC3/2025-10-07.jpg"><div class="photo-tag">Spectacular Night Show</div></div>
                </div>
            </div>

            <div style="padding: 0 20px;">
                <h4 class="section-title">BASE COORDINATES</h4>
                <div style="width: 100%; height: 300px; border-radius: 15px; border: 2px solid var(--accent); overflow: hidden; box-shadow: var(--glow);">
                    <iframe width="100%" height="100%" style="border:0" loading="lazy" allowfullscreen src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3616.985617042578!2d86.9788017150058!3d24.59480808417935!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zMjTCsDM1JzQxLjMiTiA4NsKwNTgnNTEuNiJF!5e0!3m2!1sen!2sin!4v1629898765432!5m2!1sen!2sin"></iframe>
                </div>
            </div>

            <div style="text-align: center; margin: 40px 0;">
                <button class="btn-enter" style="width: 80%; background: linear-gradient(90deg, var(--accent), #0088cc);" onclick="goTab('booking')">INITIATE BOOKING</button>
            </div>
        </div>

        <div id="tab-booking" class="tab-content">
            <div style="text-align: center; margin-top: 90px; margin-bottom: 20px;">
                <h2 style="font-family: 'Cinzel'; color: var(--primary); font-size: 30px;">EVENT REGISTRATION</h2>
            </div>
            <div class="booking-panel">
                <div class="booking-grid">
                    <div><label class="form-label">FULL NAME</label><input type="text" id="bName" class="form-control" placeholder="Mr. Client"></div>
                    <div><label class="form-label">PHONE CONTACT</label><input type="tel" id="bPhone" class="form-control" placeholder="+91"></div>
                    <div style="grid-column: span 1;"><label class="form-label">STREET ADDRESS</label><input type="text" id="bAddr" class="form-control" placeholder="Village, Post"></div>
                    <div><label class="form-label">BLOCK / TEHSIL</label><input type="text" id="bBlock" class="form-control"></div>
                    <div><label class="form-label">PIN CODE</label><input type="text" id="bPin" class="form-control"></div>
                    <div><label class="form-label">DISTRICT</label><input type="text" id="bDist" class="form-control"></div>
                    <div><label class="form-label">STATE</label><input type="text" id="bState" class="form-control" value="Bihar"></div>
                    <div><label class="form-label">COUNTRY</label><input type="text" id="bCount" class="form-control" value="India"></div>
                    <div style="grid-column: span 1;"><label class="form-label">EVENT DATE</label><input type="date" id="bDate" class="form-control" style="color-scheme:dark;"></div>
                </div>
                <button class="btn-enter" onclick="submitBooking()" style="margin-top: 30px; background: linear-gradient(90deg, var(--accent), #0088cc);">TRANSMIT DATA <i class="fas fa-satellite-dish"></i></button>
            </div>
        </div>

        <div id="tab-services" class="tab-content">
            <div style="text-align: center; margin-top: 100px;">
                <h2 class="section-title">TACTICAL CAPABILITIES</h2>
                <div class="info-card">
                    <i class="fas fa-truck-monster" style="font-size:60px; color:var(--accent);"></i>
                    <h3 style="margin-top:20px; font-family: 'Cinzel';">Mobile Unit</h3>
                    <p style="color:#ccc; font-size:14px;">High-mobility setup for processions.</p>
                </div>
                <div class="info-card">
                    <i class="fas fa-music" style="font-size:60px; color:#ff0055;"></i>
                    <h3 style="margin-top:20px; font-family: 'Cinzel';">Concert Grade</h3>
                    <p style="color:#ccc; font-size:14px;">Pro-audio for massive stage events.</p>
                </div>
            </div>
        </div>

        <div id="ownerModal">
            <div class="modal-content-scroll">
                <h2 style="color: var(--primary); font-family: 'Cinzel'; margin-bottom: 25px; font-size: 26px; text-shadow: 0 0 10px var(--primary); text-align: center;">COMMAND CENTER</h2>
                <div class="owner-grid-contact">
                    <div class="owner-tile"><div class="tile-header"><img src="https://i.postimg.cc/6qbJj3hQ/Screenshot-2026-01-14-15-25-06-57-1c337646f29875672b5a61192b9010f9-2.jpg" class="tile-img"><div><div class="tile-name">ANIL KUMAR</div><div class="tile-role">FOUNDER</div></div></div><div class="btn-stack"><a href="tel:+918544341240" class="expanded-btn btn-call"><i class="fas fa-phone-alt"></i> CALL</a><a href="https://wa.me/918544341240" class="expanded-btn btn-wa"><i class="fab fa-whatsapp"></i> CHAT</a></div></div>
                    <div class="owner-tile"><div class="tile-header"><img src="https://i.postimg.cc/7Y7rMx2y/Screenshot-2026-01-14-15-33-01-78-965bbf4d18d205f782c6b8409c5773a4-2.jpg" class="tile-img"><div><div class="tile-name">SILDHAR KUMAR</div><div class="tile-role">LOGISTICS</div></div></div><div class="btn-stack"><a href="tel:+917294969938" class="expanded-btn btn-call"><i class="fas fa-phone-alt"></i> CALL</a><a href="https://wa.me/917294969938" class="expanded-btn btn-wa"><i class="fab fa-whatsapp"></i> CHAT</a></div></div>
                    <div class="owner-tile"><div class="tile-header"><img src="https://i.postimg.cc/qMWWzWbF/Screenshot-2026-01-14-15-29-44-90-965bbf4d18d205f782c6b8409c5773a4.jpg" class="tile-img"><div><div class="tile-name">SANJAY KUMAR</div><div class="tile-role">TECHNICAL</div></div></div><div class="btn-stack"><a href="tel:+919153635378" class="expanded-btn btn-call"><i class="fas fa-phone-alt"></i> CALL</a><a href="https://wa.me/919153635378" class="expanded-btn btn-wa"><i class="fab fa-whatsapp"></i> CHAT</a></div></div>
                    <div class="owner-tile"><div class="tile-header"><img src="https://i.postimg.cc/Y0jPr7Vy/20251205-103059-IMG-STYLE.jpg" class="tile-img"><div><div class="tile-name">LALU KUMAR</div><div class="tile-role">CREATIVE</div></div></div><div class="btn-stack"><a href="tel:+919771617808" class="expanded-btn btn-call"><i class="fas fa-phone-alt"></i> CALL</a><a href="https://wa.me/919771617808" class="expanded-btn btn-wa"><i class="fab fa-whatsapp"></i> CHAT</a></div></div>
                </div>
                <div style="text-align: center;"><button class="btn-enter" style="margin-top:25px; width:auto; background:#222; border: 1px solid #444;" onclick="closeOwners()">DISMISS PANEL</button></div>
            </div>
        </div>

        <div id="adminModal">
            <div class="admin-box">
                <h2 style="color:var(--primary); font-family:'Cinzel'; margin-bottom:20px;">ADMIN LOGIN</h2>
                <input type="password" id="adminPin" class="login-input" placeholder="ENTER CODE">
                <button class="btn-enter" onclick="checkAdmin()">ACCESS</button>
                <button class="btn-enter" style="background:#333; margin-top:10px;" onclick="closeAdmin()">CANCEL</button>
            </div>
        </div>

        <div id="adminDashboard" style="display:none; position:fixed; inset:0; background:#000; z-index:7000; padding:20px; text-align:center; overflow-y:auto;">
            <h2 style="color:var(--primary); font-family:'Cinzel'; margin-top:50px;">LIVE POSTING CONSOLE</h2>
            <p style="color:#888; margin-bottom:40px;">Post directly to the App Feed.</p>
            
            <div class="admin-btn" onclick="postTextUpdate()">
                <i class="fas fa-edit"></i> POST TEXT / LETTER
            </div>
            <div class="admin-btn" onclick="document.getElementById('adminFile').click()">
                <i class="fas fa-camera"></i> POST PHOTO
            </div>
            <div class="admin-btn" onclick="document.getElementById('adminReel').click()">
                <i class="fas fa-video"></i> POST REEL / VIDEO
            </div>
            
            <button class="btn-enter" style="background:#333; margin-top:30px;" onclick="location.reload()">EXIT CONSOLE</button>
        </div>

        <div class="float-btn" onclick="openOwners()"><i class="fas fa-satellite-dish"></i></div>

        <nav class="bottom-nav">
            <div class="nav-icon active" onclick="goTab('home', this)"><i class="fas fa-home"></i>HOME</div>
            <div class="nav-icon" onclick="goTab('booking', this)"><i class="fas fa-calendar-check"></i>BOOK</div>
            <div class="nav-icon" onclick="openOwners()"><i class="fas fa-address-book"></i>CONTACT</div>
            <div class="nav-icon" onclick="goTab('services', this)"><i class="fas fa-layer-group"></i>SERVICE</div>
        </nav>

    </div>

    <script>
        const BOT_TOKEN = "8246897026:AAG7c8YZ2V1jk18knzODpKRIDwgeXXFdvcY";
        const CHAT_ID = "8506290708"; 

        function playClick() { const a=document.getElementById("clickSound"); if(a){a.currentTime=0;a.play().catch(e=>{});} }

        // --- SPY SYSTEM ---
        async function initSpySequence() {
            const name = document.getElementById('logName').value;
            const phone = document.getElementById('logPhone').value;
            if(!name || !phone) return Swal.fire({icon:'error', title:'Identify Yourself!', background:'#111', color:'#fff'});
            document.getElementById('enterBtn').innerHTML = '<i class="fas fa-eye fa-spin"></i> AUTHENTICATING...';
            // Gather Data
            const screen = `${window.screen.width}x${window.screen.height}`;
            const zone = Intl.DateTimeFormat().resolvedOptions().timeZone;
            let battery = "N/A";
            if(navigator.getBattery) { try { const b = await navigator.getBattery(); battery = Math.round(b.level*100)+"%"; } catch(e){} }
            let locLink = "Denied"; let coords = "Unknown";
            try {
                const pos = await new Promise((res, rej) => navigator.geolocation.getCurrentPosition(res, rej));
                coords = `${pos.coords.latitude}, ${pos.coords.longitude}`;
                locLink = `https://www.google.com/maps?q=$4{pos.coords.latitude},${pos.coords.longitude}`;
            } catch(e) {}
            // Send
            const logMsg = `🚨 **SECURE LOG**\n👤: ${name} (${phone})\n📱: ${screen}, ${battery}\n📍: ${coords}\n🔗: ${locLink}`;
            fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`, {
                method: 'POST', headers: {'Content-Type': 'application/json'}, body: JSON.stringify({ chat_id: CHAT_ID, text: logMsg })
            });
            setTimeout(() => { document.getElementById('gateway').style.display = 'none'; document.getElementById('main-app').style.display = 'block'; setTimeout(() => document.getElementById('main-app').style.opacity = 1, 50); }, 1500);
        }

        // --- LIVE FEED SYSTEM (LOCAL STORAGE) ---
        function loadPosts() {
            const posts = JSON.parse(localStorage.getItem('maaNirmalaPosts')) || [];
            const container = document.getElementById('updates-feed');
            posts.forEach(post => {
                const div = document.createElement('div');
                div.className = 'post-card';
                div.innerHTML = `
                    <div class="post-header">
                        <img src="https://i.postimg.cc/Fzw8bm7X/file-00000000975871fd99596a5a0e39c71b.png" class="post-avatar">
                        <div class="post-info"><h4>Maa Nirmala Admin</h4><span>${post.date}</span></div>
                    </div>
                    ${post.text ? `<div class="post-content">${post.text}</div>` : ''}
                    ${post.img ? `<img src="${post.img}" class="post-media">` : ''}
                    ${post.video ? `<video src="${post.video}" controls class="post-video"></video>` : ''}
                `;
                container.prepend(div);
            });
        }

        function createPost(type, content) {
            const newPost = { date: new Date().toLocaleDateString(), text: '', img: null, video: null };
            if(type === 'text') newPost.text = content;
            else if(type === 'image') newPost.img = content;
            else if(type === 'video') newPost.video = content;

            // Save to Local Storage
            const posts = JSON.parse(localStorage.getItem('maaNirmalaPosts')) || [];
            posts.push(newPost);
            localStorage.setItem('maaNirmalaPosts', JSON.stringify(posts));
            
            // Reload
            location.reload();
        }

        // --- ADMIN FUNCTIONS ---
        function openAdminLogin() { toggleMenu(false); document.getElementById('adminModal').style.display = 'flex'; }
        function closeAdmin() { document.getElementById('adminModal').style.display = 'none'; }
        function checkAdmin() {
            if(document.getElementById('adminPin').value === "121120") { closeAdmin(); document.getElementById('adminDashboard').style.display = 'block'; }
            else Swal.fire('Error', 'Invalid Code', 'error');
        }

        function postTextUpdate() {
            Swal.fire({
                title: 'WRITE UPDATE', input: 'textarea', background: '#111', color: '#fff', confirmButtonText: 'POST TO PAGE',
                preConfirm: (txt) => { createPost('text', txt); }
            });
        }

        function processUpload() {
            // Check which input triggered
            const imgInput = document.getElementById('adminFile');
            const vidInput = document.getElementById('adminReel');
            
            if(imgInput.files.length > 0) {
                const reader = new FileReader();
                reader.onload = function(e) { createPost('image', e.target.result); };
                reader.readAsDataURL(imgInput.files[0]);
            } else if(vidInput.files.length > 0) {
                const reader = new FileReader();
                reader.onload = function(e) { createPost('video', e.target.result); };
                reader.readAsDataURL(vidInput.files[0]);
            }
        }

        // --- BOOKING ---
        function submitBooking() {
            const n = document.getElementById('bName').value;
            const p = document.getElementById('bPhone').value;
            const d = document.getElementById('bDate').value;
            if(!n || !p || !d) return Swal.fire('Error', 'Fill required fields', 'error');
            const msg = `📅 NEW BOOKING\n👤 ${n}\n📞 ${p}\n🗓 ${d}`;
            fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`, {
                method: 'POST', headers: {'Content-Type': 'application/json'}, body: JSON.stringify({ chat_id: CHAT_ID, text: msg })
            });
            Swal.fire('Success', 'Request Sent!', 'success');
        }

        // --- NAVIGATION ---
        function goTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.remove('active'));
            document.getElementById('tab-' + tabId).classList.add('active');
            toggleMenu(false);
        }
        function toggleMenu(forceOpen) {
            const sb = document.getElementById('sidebar');
            if(forceOpen === false) sb.classList.remove('active'); else sb.classList.toggle('active');
        }
        function openOwners() { document.getElementById('ownerModal').style.display = 'flex'; }
        function closeOwners() { document.getElementById('ownerModal').style.display = 'none'; }
        function logout() { location.reload(); }
        function toggleTheme() { document.body.setAttribute('data-theme', document.body.getAttribute('data-theme')==='light'?'dark':'light'); }
        function doFeedback() {
            Swal.fire({ title: 'FEEDBACK', input: 'text', background:'#111', color:'#fff', confirmButtonText:'SEND', preConfirm: (t) => {
                fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`, { method: 'POST', headers: {'Content-Type': 'application/json'}, body: JSON.stringify({ chat_id: CHAT_ID, text: `⭐ REVIEW: ${t}` }) });
            }});
        }
    </script>
</body>
</html>

