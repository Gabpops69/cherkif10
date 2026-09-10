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
            min-height: 100vh;
            background: #000;
            color: #fff;
            font-family: -apple-system, BlinkMacSystemFont, "Helvetica Neue", Arial, sans-serif;
            overflow-x: hidden;
        }

        /* Dégradé lumineux */
        body::before {
            content: "";
            position: fixed;
            width: 900px;
            height: 900px;
            top: -300px;
            left: 50%;
            transform: translateX(-50%);
            background: radial-gradient(
                circle,
                rgba(90, 90, 110, 0.30) 0%,
                rgba(30, 30, 40, 0.12) 40%,
                transparent 70%
            );
            pointer-events: none;
            z-index: -1;
        }

        .page {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 60px;
        }

        .container {
            width: 100%;
            max-width: 1400px;
            text-align: center;
        }

        .eyebrow {
            font-size: 14px;
            letter-spacing: 4px;
            text-transform: uppercase;
            color: #888;
            margin-bottom: 30px;
        }

        h1 {
            font-size: clamp(80px, 15vw, 210px);
            line-height: 0.9;
            font-weight: 600;
            letter-spacing: -10px;
            margin-bottom: 45px;
        }

        .subtitle {
            max-width: 650px;
            margin: 0 auto 85px;
            color: #999;
            font-size: clamp(18px, 2vw, 24px);
            line-height: 1.5;
            font-weight: 300;
        }

        .categories {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 25px;
            max-width: 1050px;
            margin: auto;
        }

        .category {
            position: relative;
            min-height: 330px;
            padding: 45px;

            display: flex;
            align-items: flex-end;
            justify-content: flex-start;

            text-align: left;
            text-decoration: none;
            color: white;

            border-radius: 30px;
            overflow: hidden;

            background:
                linear-gradient(
                    145deg,
                    rgba(255,255,255,0.12),
                    rgba(255,255,255,0.025)
                );

            border: 1px solid rgba(255,255,255,0.10);

            transition:
                transform 0.5s cubic-bezier(.2,.8,.2,1),
                border-color 0.5s ease,
                background 0.5s ease;
        }

        .category::before {
            content: "";
            position: absolute;
            inset: 0;

            background: radial-gradient(
                circle at 20% 20%,
                rgba(255,255,255,0.12),
                transparent 45%
            );

            opacity: 0.7;
        }

        .category:hover {
            transform: translateY(-10px) scale(1.015);
            border-color: rgba(255,255,255,0.25);

            background:
                linear-gradient(
                    145deg,
                    rgba(255,255,255,0.17),
                    rgba(255,255,255,0.04)
                );
        }

        .category-content {
            position: relative;
            z-index: 2;
        }

        .number {
            display: block;
            margin-bottom: 15px;

            font-size: 14px;
            color: #777;
            letter-spacing: 2px;
        }

        .category h2 {
            font-size: clamp(32px, 4vw, 50px);
            font-weight: 500;
            letter-spacing: -2px;
        }

        .arrow {
            position: absolute;
            top: 40px;
            right: 40px;

            font-size: 32px;
            color: #777;

            transition: transform 0.4s ease, color 0.4s ease;
        }

        .category:hover .arrow {
            transform: translate(6px, -6px);
            color: white;
        }

        @media (max-width: 800px) {

            .page {
                padding: 30px 20px;
            }

            h1 {
                letter-spacing: -6px;
            }

            .subtitle {
                margin-bottom: 55px;
            }

            .categories {
                grid-template-columns: 1fr;
            }

            .category {
                min-height: 250px;
                padding: 30px;
            }
        }
    </style>
</head>

<body>

    <main class="page">

        <div class="container">

            <div class="eyebrow">
                Football · Créativité · Talent
            </div>

            <h1>Cherki</h1>

            <p class="subtitle">
                Un regard sur le parcours, la personnalité
                et le style de jeu de Rayan Cherki.
            </p>

            <div class="categories">

                <a href="#" class="category">

                    <span class="arrow">↗</span>

                    <div class="category-content">
                        <span class="number">01</span>
                        <h2>Présentation</h2>
                    </div>

                </a>

                <a href="#" class="category">

                    <span class="arrow">↗</span>

                    <div class="category-content">
                        <span class="number">02</span>
                        <h2>Style de jeu</h2>
                    </div>

                </a>

            </div>

        </div>

    </main>

</body>
</html>
```
