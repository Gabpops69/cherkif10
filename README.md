<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Un titre</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;

            font-family: Arial, Helvetica, sans-serif;
            color: white;

            background:
                radial-gradient(circle at 50% 40%,
                    #202020 0%,
                    #0d0d0d 45%,
                    #000000 100%);
        }

        .container {
            width: 90%;
            max-width: 900px;
            text-align: center;
        }

        h1 {
            font-size: clamp(50px, 8vw, 100px);
            font-weight: 300;
            letter-spacing: -4px;
            margin-bottom: 70px;
        }

        .categories {
            display: flex;
            justify-content: center;
            gap: 25px;
        }

        .category {
            width: 280px;
            padding: 30px;

            color: white;
            text-decoration: none;

            background: rgba(255, 255, 255, 0.04);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 18px;

            backdrop-filter: blur(10px);

            transition: 0.3s ease;
        }

        .category:hover {
            transform: translateY(-6px);
            background: rgba(255, 255, 255, 0.08);
            border-color: rgba(255, 255, 255, 0.25);
        }

        .category h2 {
            font-size: 20px;
            font-weight: 400;
            letter-spacing: 0.5px;
        }

        @media (max-width: 650px) {
            .categories {
                flex-direction: column;
                align-items: center;
            }

            .category {
                width: 100%;
                max-width: 320px;
            }

            h1 {
                margin-bottom: 45px;
            }
        }
    </style>
</head>

<body>

    <main class="container">

        <h1>un titre</h1>

        <div class="categories">

            <a href="#" class="category">
                <h2>Présentation</h2>
            </a>

            <a href="#" class="category">
                <h2>Style de jeu</h2>
            </a>

        </div>

    </main>

</body>
</html>
```
