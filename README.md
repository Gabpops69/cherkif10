<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cherki</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            background: #000;
            color: #fff;
            font-family: -apple-system, BlinkMacSystemFont, "Helvetica Neue", Arial, sans-serif;
            overflow-x: hidden;
        }

        /* =========================
           FOND
        ========================= */

        body::before {
            content: "";
            position: fixed;
            width: 700px;
            height: 700px;
            top: -350px;
            left: 50%;
            transform: translateX(-50%);

            background: radial-gradient(
                circle,
                rgba(90, 80, 120, 0.35),
                transparent 70%
            );

            filter: blur(30px);
            pointer-events: none;
            z-index: -1;
        }

        /* =========================
           NAVBAR
        ========================= */

        nav {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;

            padding: 25px 40px;

            display: flex;
            justify-content: space-between;
            align-items: center;

            background: rgba(0, 0, 0, 0.45);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);

            border-bottom: 1px solid rgba(255, 255, 255, 0.08);

            z-index: 100;
        }

        .logo {
            font-size: 18px;
            font-weight: 600;
            letter-spacing: -0.5px;
        }

        .nav-text {
            color: #666;
            font-size: 11px;
            letter-spacing: 3px;
            text-transform: uppercase;
        }

        /* =========================
           HERO
        ========================= */

        .hero {
            min-height: 100vh;

            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;

            text-align: center;

            padding: 120px 25px 80px;
        }

        .small-title {
            color: #777;
            font-size: 12px;
            letter-spacing: 5px;
            text-transform: uppercase;

            margin-bottom: 30px;

            animation: fadeUp 1s ease both;
        }

        h1 {
            font-size: clamp(80px, 17vw, 220px);
            line-height: 0.8;

            font-weight: 600;
            letter-spacing: -12px;

            background: linear-gradient(
                180deg,
                #ffffff 0%,
                #bcbcbc 50%,
                #666666 100%
            );

            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;

            animation: titleAppear 1.3s cubic-bezier(.16, 1, .3, 1) both;
        }

        .description {
            max-width: 650px;

            margin-top: 45px;

            color: #888;

            font-size: 20px;
            line-height: 1.6;
            font-weight: 300;

            animation: fadeUp 1s ease 0.4s both;
        }

        .scroll {
            margin-top: 80px;

            color: #555;

            font-size: 10px;
            text-transform: uppercase;
            letter-spacing: 3px;

            animation: pulse 2s ease-in-out infinite;
        }

        /* =========================
           GALERIE
        ========================= */

        .gallery {
            padding: 20px 0 160px;
            overflow: hidden;
        }

        .gallery-title {
            text-align: center;

            margin-bottom: 35px;

            color: #555;

            font-size: 10px;
            text-transform: uppercase;
            letter-spacing: 4px;
        }

        .track {
            display: flex;
            gap: 20px;
            width: max-content;

            animation: slide 30s linear infinite;
        }

        .track:hover {
            animation-play-state: paused;
        }

        .card {
            width: 320px;
            height: 420px;

            flex-shrink: 0;

            border-radius: 25px;
            overflow: hidden;

            position: relative;

            border: 1px solid rgba(255,255,255,0.08);

            transition: transform 0.5s ease;
        }

        .card:hover {
            transform: scale(1.03);
        }

        /* Presets visuels sans images externes */

        .image1 {
            background:
                radial-gradient(circle at 70% 20%, #595959, transparent 20%),
                linear-gradient(145deg, #292929, #050505);
        }

        .image2 {
            background:
                radial-gradient(circle at 30% 30%, #777, transparent 18%),
                linear-gradient(145deg, #161616, #333);
        }

        .image3 {
            background:
                radial-gradient(circle at 65% 70%, #555, transparent 20%),
                linear-gradient(160deg, #050505, #272727);
        }

        .image4 {
            background:
                radial-gradient(circle at 50% 40%, #888, transparent 15%),
                linear-gradient(120deg, #333, #050505);
        }

        .image5 {
            background:
                radial-gradient(circle at 20% 70%, #666, transparent 18%),
                linear-gradient(145deg, #0a0a0a, #3a3a3a);
        }

        .card::after {
            content: "";
            position: absolute;
            inset: 0;

            background: linear-gradient(
                to top,
                rgba(0,0,0,0.45),
                transparent 55%
            );
        }

        /* =========================
           CATEGORIES
        ========================= */

        .categories {
            max-width: 1200px;
            margin: auto;

            padding: 20px 25px 180px;

            display: grid;
            grid-template-columns: repeat(2, 1fr);

            gap: 25px;
        }

        .category {
            min-height: 430px;

            padding: 45px;

            display: flex;
            flex-direction: column;
            justify-content: space-between;

            text-decoration: none;
            color: #fff;

            border-radius: 30px;

            background: linear-gradient(
                135deg,
                rgba(255,255,255,0.10),
                rgba(255,255,255,0.025)
            );

            border: 1px solid rgba(255,255,255,0.10);

            transition:
                transform 0.5s ease,
                border-color 0.5s ease,
                background 0.5s ease;
        }

        .category:hover {
            transform: translateY(-10px);

            background: linear-gradient(
                135deg,
                rgba(255,255,255,0.16),
                rgba(255,255,255,0.04)
            );

            border-color: rgba(255,255,255,0.22);
        }

        .number {
            color: #666;
            font-size: 12px;
            letter-spacing: 3px;
        }

        .category h2 {
            font-size: clamp(38px, 5vw, 62px);
            font-weight: 500;
            letter-spacing: -3px;
        }

        .bottom {
            display: flex;
            justify-content: space-between;
            align-items: flex-end;
            gap: 30px;
        }

        .text {
            max-width: 280px;

            color: #777;

            font-size: 14px;
            line-height: 1.6;
        }

        .arrow {
            width: 55px;
            height: 55px;

            flex-shrink: 0;

            display: flex;
            justify-content: center;
            align-items: center;

            border: 1px solid rgba(255,255,255,0.15);
            border-radius: 50%;

            font-size: 22px;

            transition:
                background 0.4s ease,
                color 0.4s ease,
                transform 0.4s ease;
        }

        .category:hover .arrow {
            background: #fff;
            color: #000;
            transform: translate(4px, -4px);
        }

        /* =========================
           FOOTER
        ========================= */

        footer {
            border-top: 1px solid rgba(255,255,255,0.08);

            padding: 30px 40px;

            display: flex;
            justify-content: space-between;

            color: #444;

            font-size: 10px;
            letter-spacing: 3px;
            text-transform: uppercase;
        }

        /* =========================
           ANIMATIONS
        ========================= */

        @keyframes titleAppear {
            from {
                opacity: 0;
                transform: translateY(70px) scale(0.95);
                filter: blur(15px);
            }

            to {
                opacity: 1;
                transform: translateY(0) scale(1);
                filter: blur(0);
            }
        }

        @keyframes fadeUp {
            from {
                opacity: 0;
                transform: translateY(25px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes pulse {
            0%, 100% {
                opacity: 0.3;
                transform: translateY(0);
            }

            50% {
                opacity: 1;
                transform: translateY(7px);
            }
        }

        @keyframes slide {
            from {
                transform: translateX(0);
            }

            to {
                transform: translateX(-50%);
            }
        }

        /* =========================
           MOBILE
        ========================= */

        @media (max-width: 800px) {

            nav {
                padding: 20px;
            }

            .nav-text {
                display: none;
            }

            .hero {
                padding-left: 20px;
                padding-right: 20px;
            }

            h1 {
                letter-spacing: -7px;
            }

            .description {
                font-size: 17px;
            }

            .card {
                width: 250px;
                height: 340px;
            }

            .categories {
                grid-template-columns: 1fr;
            }

            .category {
                min-height: 350px;
                padding: 30px;
            }

            footer {
                padding: 25px 20px;
            }
        }
    </style>
</head>

<body>

    <nav>
        <div class="logo">CHERKI.</div>
        <div class="nav-text">Football · Creativity · Vision</div>
    </nav>

    <section class="hero">

        <div class="small-title">
            The creative player
        </div>

        <h1>Cherki</h1>

        <p class="description">
            Une immersion dans l'univers d'un joueur
            qui transforme chaque ballon en possibilité.
        </p>

        <div class="scroll">
            Scroll ↓
        </div>

    </section>

    <section class="gallery">

        <div class="gallery-title">
            The moments
        </div>

        <div class="track">

            <!-- Série 1 -->

            <div class="card image1"></div>
            <div class="card image2"></div>
            <div class="card image3"></div>
            <div class="card image4"></div>
            <div class="card image5"></div>

            <!-- Série 2 = copie pour boucle infinie -->

            <div class="card image1"></div>
            <div class="card image2"></div>
            <div class="card image3"></div>
            <div class="card image4"></div>
            <div class="card image5"></div>

        </div>

    </section>

    <section class="categories">

        <a href="presentation.html" class="category">

            <span class="number">01</span>

            <h2>Présentation</h2>

            <div class="bottom">

                <p class="text">
                    Son parcours, son histoire,
                    ses débuts et l'évolution
                    de sa carrière.
                </p>

                <span class="arrow">↗</span>

            </div>

        </a>

        <a href="style.html" class="category">

            <span class="number">02</span>

            <h2>Style de jeu</h2>

            <div class="bottom">

                <p class="text">
                    Technique, créativité,
                    dribbles, vision et
                    intelligence de jeu.
                </p>

                <span class="arrow">↗</span>

            </div>

        </a>

    </section>

    <footer>
        <span>CHERKI</span>
        <span>2026</span>
    </footer>

</body>
</html>
```
