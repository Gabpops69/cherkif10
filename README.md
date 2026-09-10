```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Cherki — The Artist</title>

    <style>
        /* =========================
           RESET
        ========================= */

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
            font-family:
                -apple-system,
                BlinkMacSystemFont,
                "SF Pro Display",
                "Helvetica Neue",
                Arial,
                sans-serif;
            overflow-x: hidden;
        }

        /* =========================
           BACKGROUND
        ========================= */

        body::before {
            content: "";
            position: fixed;
            width: 800px;
            height: 800px;
            top: -400px;
            left: 50%;
            transform: translateX(-50%);

            background:
                radial-gradient(
                    circle,
                    rgba(90, 90, 110, 0.25) 0%,
                    rgba(50, 50, 60, 0.08) 40%,
                    transparent 70%
                );

            pointer-events: none;
            z-index: -3;
            filter: blur(20px);
        }

        body::after {
            content: "";
            position: fixed;
            inset: 0;

            background:
                radial-gradient(
                    circle at 50% 50%,
                    transparent 0%,
                    rgba(0, 0, 0, 0.3) 60%,
                    #000 100%
                );

            pointer-events: none;
            z-index: -2;
        }

        /* =========================
           NAVBAR
        ========================= */

        nav {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;

            padding: 25px 50px;

            display: flex;
            justify-content: space-between;
            align-items: center;

            z-index: 100;

            background: rgba(0, 0, 0, 0.35);
            backdrop-filter: blur(18px);
            -webkit-backdrop-filter: blur(18px);

            border-bottom: 1px solid rgba(255, 255, 255, 0.06);
        }

        .logo {
            font-size: 18px;
            font-weight: 600;
            letter-spacing: -0.5px;
        }

        .nav-right {
            font-size: 12px;
            letter-spacing: 2px;
            text-transform: uppercase;
            color: #777;
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

            padding: 120px 30px 80px;

            position: relative;
        }

        .eyebrow {
            font-size: 13px;
            letter-spacing: 5px;
            text-transform: uppercase;
            color: #777;

            margin-bottom: 30px;

            opacity: 0;
            animation: fadeUp 1s ease forwards;
            animation-delay: 0.15s;
        }

        .hero h1 {
            font-size: clamp(90px, 16vw, 230px);

            line-height: 0.82;

            font-weight: 600;

            letter-spacing: -12px;

            background:
                linear-gradient(
                    180deg,
                    #ffffff 0%,
                    #bdbdbd 48%,
                    #686868 100%
                );

            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;

            opacity: 0;
            animation:
                heroTitle 1.3s cubic-bezier(.16,1,.3,1) forwards;
            animation-delay: 0.2s;
        }

        .intro {
            max-width: 700px;

            margin-top: 45px;

            color: #858585;

            font-size: clamp(18px, 2vw, 24px);

            line-height: 1.5;

            font-weight: 300;

            opacity: 0;

            animation: fadeUp 1s ease forwards;
            animation-delay: 0.6s;
        }

        /* =========================
           SCROLL INDICATOR
        ========================= */

        .scroll {
            position: absolute;
            bottom: 35px;

            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 10px;

            color: #555;

            font-size: 10px;
            text-transform: uppercase;
            letter-spacing: 3px;

            animation: scrollPulse 2s infinite ease-in-out;
        }

        .scroll-line {
            width: 1px;
            height: 45px;
            background: linear-gradient(
                to bottom,
                #777,
                transparent
            );
        }

        /* =========================
           IMAGE MARQUEE
        ========================= */

        .gallery-section {
            padding: 30px 0 150px;
            overflow: hidden;
        }

        .gallery-title {
            text-align: center;

            color: #555;

            font-size: 11px;

            text-transform: uppercase;

            letter-spacing: 4px;

            margin-bottom: 35px;
        }

        .marquee {
            width: 100%;
            overflow: hidden;
            position: relative;
        }

        .marquee-track {
            display: flex;
            width: max-content;
            gap: 20px;

            animation:
                marquee 35s linear infinite;
        }

        .marquee:hover .marquee-track {
            animation-play-state: paused;
        }

        .image-card {
            width: 340px;
            height: 460px;

            flex-shrink: 0;

            border-radius: 24px;

            overflow: hidden;

            position: relative;

            background: #111;

            border: 1px solid rgba(255, 255, 255, 0.08);

            transition:
                transform 0.5s ease,
                border-color 0.5s ease;
        }

        .image-card:hover {
            transform: scale(1.03);
            border-color: rgba(255, 255, 255, 0.25);
        }

        .image-card img {
            width: 100%;
            height: 100%;

            object-fit: cover;

            display: block;

            filter: grayscale(20%);

            transition:
                transform 0.8s cubic-bezier(.16,1,.3,1),
                filter 0.5s ease;
        }

        .image-card:hover img {
            transform: scale(1.08);
            filter: grayscale(0%);
        }

        .image-card::after {
            content: "";

            position: absolute;
            inset: 0;

            background:
                linear-gradient(
                    to top,
                    rgba(0, 0, 0, 0.6),
                    transparent 45%
                );

            pointer-events: none;
        }

        /* =========================
           CATEGORIES
        ========================= */

        .categories-section {
            padding: 50px 30px 180px;
        }

        .categories {
            max-width: 1200px;

            margin: auto;

            display: grid;

            grid-template-columns: repeat(2, 1fr);

            gap: 25px;
        }

        .category {
            position: relative;

            min-height: 430px;

            padding: 48px;

            display: flex;

            flex-direction: column;

            justify-content: space-between;

            color: white;

            text-decoration: none;

            border-radius: 30px;

            overflow: hidden;

            background:
                linear-gradient(
                    135deg,
                    rgba(255, 255, 255, 0.11),
                    rgba(255, 255, 255, 0.025)
                );

            border:
                1px solid rgba(255, 255, 255, 0.10);

            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);

            transition:
                transform 0.6s cubic-bezier(.16,1,.3,1),
                background 0.4s ease,
                border-color 0.4s ease;
        }

        .category::before {
            content: "";

            position: absolute;

            width: 300px;
            height: 300px;

            top: -150px;
            right: -100px;

            background:
                radial-gradient(
                    circle,
                    rgba(255,255,255,0.10),
                    transparent 70%
                );

            filter: blur(10px);

            transition: transform 0.8s ease;
        }

        .category:hover {
            transform: translateY(-12px);

            border-color:
                rgba(255,255,255,0.23);

            background:
                linear-gradient(
                    135deg,
                    rgba(255,255,255,0.15),
                    rgba(255,255,255,0.04)
                );
        }

        .category:hover::before {
            transform: scale(1.5);
        }

        .category-number {
            color: #666;

            font-size: 12px;

            letter-spacing: 3px;
        }

        .category h2 {
            position: relative;

            font-size: clamp(38px, 4vw, 60px);

            font-weight: 500;

            letter-spacing: -2px;
        }

        .category-bottom {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .category-description {
            color: #777;

            font-size: 14px;

            max-width: 260px;

            line-height: 1.5;
        }

        .arrow {
            width: 55px;
            height: 55px;

            display: flex;
            justify-content: center;
            align-items: center;

            border:
                1px solid rgba(255,255,255,0.15);

            border-radius: 50%;

            font-size: 24px;

            transition:
                transform 0.5s ease,
                background 0.4s ease;
        }

        .category:hover .arrow {
            transform: translate(5px, -5px);

            background: white;
            color: black;
        }

        /* =========================
           FOOTER
        ========================= */

        footer {
            padding: 35px 50px;

            border-top:
                1px solid rgba(255,255,255,0.08);

            display: flex;
            justify-content: space-between;

            color: #444;

            font-size: 11px;

            letter-spacing: 2px;

            text-transform: uppercase;
        }

        /* =========================
           ANIMATIONS
        ========================= */

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

        @keyframes heroTitle {
            from {
                opacity: 0;
                transform: translateY(60px) scale(0.95);
                filter: blur(10px);
            }

            to {
                opacity: 1;
                transform: translateY(0) scale(1);
                filter: blur(0);
            }
        }

        @keyframes scrollPulse {
            0%, 100% {
                opacity: 0.4;
                transform: translateY(0);
            }

            50% {
                opacity: 1;
                transform: translateY(8px);
            }
        }

        @keyframes marquee {
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

            .nav-right {
                display: none;
            }

            .hero {
                padding-left: 20px;
                padding-right: 20px;
            }

            .hero h1 {
                letter-spacing: -7px;
            }

            .categories {
                grid-template-columns: 1fr;
            }

            .category {
                min-height: 360px;
                padding: 32px;
            }

            .image-card {
                width: 260px;
                height: 360px;
            }

            footer {
                padding: 25px 20px;
            }
        }

        @media (prefers-reduced-motion: reduce) {

            *,
            *::before,
            *::after {
                scroll-behavior: auto !important;
                animation-duration: 0.01ms !important;
                animation-iteration-count: 1 !important;
                transition-duration: 0.01ms !important;
            }
        }
    </style>
</head>

<body>

    <!-- =========================
         NAVIGATION
    ========================= -->

    <nav>
        <div class="logo">CHERKI.</div>

        <div class="nav-right">
            Football · Talent · Vision
        </div>
    </nav>


    <!-- =========================
         HERO
    ========================= -->

    <main>

        <section class="hero">

            <div class="eyebrow">
                The creative player
            </div>

            <h1>Cherki</h1>

            <p class="intro">
                Une immersion dans l'univers d'un joueur
                dont la créativité transforme chaque ballon
                en possibilité.
            </p>

            <div class="scroll">
                Scroll
                <div class="scroll-line"></div>
            </div>

        </section>


        <!-- =========================
             GALERIE INFINIE
        ========================= -->

        <section class="gallery-section">

            <div class="gallery-title">
                The moments
            </div>

            <div class="marquee">

                <div class="marquee-track">

                    <!-- PREMIÈRE SÉRIE -->

                    <div class="image-card">
                        <img
                            src="https://images.unsplash.com/photo-1579952363873-27f3bade9f55?auto=format&fit=crop&w=900&q=85"
                            alt="Football"
                        >
                    </div>

                    <div class="image-card">
                        <img
                            src="https://images.unsplash.com/photo-1579952363873-27f3bade9f55?auto=format&fit=crop&w=900&q=85"
                            alt="Football"
                        >
                    </div>

                    <div class="image-card">
                        <img
                            src="https://images.unsplash.com/photo-1577223625816-7546f13df25d?auto=format&fit=crop&w=900&q=85"
                            alt="Football"
                        >
                    </div>

                    <div class="image-card">
                        <img
                            src="https://images.unsplash.com/photo-1431324155629-1a6deb1dec8d?auto=format&fit=crop&w=900&q=85"
                            alt="Stadium"
                        >
                    </div>

                    <div class="image-card">
                        <img
                            src="https://images.unsplash.com/photo-1575361204480-aadea25e6e68?auto=format&fit=crop&w=900&q=85"
                            alt="Football stadium"
                        >
                    </div>

                    <div class="image-card">
                        <img
                            src="https://images.unsplash.com/photo-1522778119026-d647f0596c20?auto=format&fit=crop&w=900&q=85"
                            alt="Football player"
                        >
                    </div>


                    <!-- DEUXIÈME SÉRIE
                         DOIT ÊTRE IDENTIQUE
                         POUR L'EFFET INFINI -->

                    <div class="image-card">
                        <img
                            src="https://images.unsplash.com/photo-1579952363873-27f3bade9f55?auto=format&fit=crop&w=900&q=85"
                            alt="Football"
                        >
                    </div>

                    <div class="image-card">
                        <img
                            src="https://images.unsplash.com/photo-1579952363873-27f3bade9f55?auto=format&fit=crop&w=900&q=85"
                            alt="Football"
                        >
                    </div>

                    <div class="image-card">
                        <img
                            src="https://images.unsplash.com/photo-1577223625816-7546f13df25d?auto=format&fit=crop&w=900&q=85"
                            alt="Football"
                        >
                    </div>

                    <div class="image-card">
                        <img
                            src="https://images.unsplash.com/photo-1431324155629-1a6deb1dec8d?auto=format&fit=crop&w=900&q=85"
                            alt="Stadium"
                        >
                    </div>

                    <div class="image-card">
                        <img
                            src="https://images.unsplash.com/photo-1575361204480-aadea25e6e68?auto=format&fit=crop&w=900&q=85"
                            alt="Football stadium"
                        >
                    </div>

                    <div class="image-card">
                        <img
                            src="https://images.unsplash.com/photo-1522778119026-d647f0596c20?auto=format&fit=crop&w=900&q=85"
                            alt="Football player"
                        >
                    </div>

                </div>

            </div>

        </section>


        <!-- =========================
             CATÉGORIES
        ========================= -->

        <section class="categories-section">

            <div class="categories">

                <a href="presentation.html" class="category">

                    <span class="category-number">
                        01
                    </span>

                    <h2>
                        Présentation
                    </h2>

                    <div class="category-bottom">

                        <p class="category-description">
                            Son parcours, son histoire,
                            ses débuts et l'évolution
                            de sa carrière.
                        </p>

                        <span class="arrow">
                            ↗
                        </span>

                    </div>

                </a>


                <a href="style.html" class="category">

                    <span class="category-number">
                        02
                    </span>

                    <h2>
                        Style de jeu
                    </h2>

                    <div class="category-bottom">

                        <p class="category-description">
                            Créativité, dribbles, vision,
                            technique et intelligence
                            dans le jeu.
                        </p>

                        <span class="arrow">
                            ↗
                        </span>

                    </div>

                </a>

            </div>

        </section>

    </main>


    <!-- =========================
         FOOTER
    ========================= -->

    <footer>

        <span>
            CHERKI
        </span>

        <span>
            2026
        </span>

    </footer>

</body>
</html>
```
