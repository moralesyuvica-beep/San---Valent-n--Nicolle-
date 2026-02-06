<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Para Nicolle ❤️</title>

    <style>
        body {
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            background-color: #ffe6e6;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            overflow: hidden;
            text-align: center;
        }

        #contenedor-principal {
            z-index: 10;
        }

        h1 {
            color: #d63384;
            font-size: 2.5rem;
            margin-bottom: 30px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        }

        .botones {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 20px;
            position: relative;
            min-height: 200px;
        }

        button {
            padding: 15px 30px;
            font-size: 1.2rem;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
            transition: all 0.2s ease;
        }

        #btn-si {
            background-color: #ff4d6d;
            color: white;
            z-index: 100;
        }

        #btn-no {
            background-color: #6c757d;
            color: white;
            position: absolute;
        }

        #celebracion {
            display: none;
            flex-direction: column;
            align-items: center;
            z-index: 20;
        }

        #celebracion h1 {
            font-size: 3rem;
            color: #ff0054;
        }

        .gif-container {
            margin-top: 20px;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        /* Corazones cayendo */
        .corazon {
            position: fixed;
            top: -10vh;
            font-size: 1.5rem;
            user-select: none;
            pointer-events: none;
            animation: caer linear forwards;
        }

        @keyframes caer {
            to {
                transform: translateY(110vh) rotate(360deg);
            }
        }
    </style>
</head>
<body>

    <!-- Música (oculta) -->
    <iframe
        id="musica"
        width="0"
        height="0"
        src=""
        frameborder="0"
        allow="autoplay"
        allowfullscreen>
    </iframe>

    <div id="contenedor-principal">
        <h1>Nicolle, ¿quieres ser mi San Valentín? 🌹</h1>
        <div class="botones">
            <button id="btn-si">¡SÍ! ❤️</button>
            <button id="btn-no">No 💔</button>
        </div>
    </div>

    <div id="celebracion">
        <h1>¡SABÍA QUE DIRÍAS QUE SÍ! 😍</h1>
        <p style="font-size: 1.5rem; color: #d63384;">
            Eres lo mejor que me ha pasado, Nicolle.
        </p>
        <div class="gif-container">
            <img src="https://media.giphy.com/media/KztT2c4u8mYYUiMKdJ/giphy.gif" width="300">
        </div>
    </div>

    <script>
        const btnNo = document.getElementById('btn-no');
        const btnSi = document.getElementById('btn-si');
        const principal = document.getElementById('contenedor-principal');
        const celebracion = document.getElementById('celebracion');

        let siPaddingV = 15;
        let siPaddingH = 30;
        let siFontSize = 1.2;

        function moverNo() {
            const x = Math.random() * (window.innerWidth - btnNo.offsetWidth);
            const y = Math.random() * (window.innerHeight - btnNo.offsetHeight);

            btnNo.style.left = x + "px";
            btnNo.style.top = y + "px";

            siPaddingV += 10;
            siPaddingH += 20;
            siFontSize += 0.3;

            btnSi.style.padding = siPaddingV + "px " + siPaddingH + "px";
            btnSi.style.fontSize = siFontSize + "rem";
        }

        btnNo.addEventListener('mouseover', moverNo);
        btnNo.addEventListener('touchstart', (e) => {
            e.preventDefault();
            moverNo();
        });

        function crearLluvia() {
            for (let i = 0; i < 100; i++) {
                setTimeout(() => {
                    const corazon = document.createElement('div');
                    corazon.className = "corazon";
                    corazon.innerHTML = "❤️";
                    corazon.style.left = Math.random() * 100 + "vw";
                    corazon.style.animationDuration = Math.random() * 2 + 3 + "s";
                    corazon.style.opacity = Math.random();
                    corazon.style.fontSize = Math.random() * 20 + 10 + "px";
                    document.body.appendChild(corazon);
                }, i * 100);
            }
        }

        btnSi.addEventListener('click', () => {
            principal.style.display = "none";
            celebracion.style.display = "flex";
            document.body.style.backgroundColor = "#ffc2d1";

            // 🎵 Antes de ti - NIKI
            document.getElementById('musica').src =
                "https://www.youtube.com/embed/9mSgq2Zz4GQ?autoplay=1";

            crearLluvia();
        });
    </script>

</body>
</html>
