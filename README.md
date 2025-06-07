<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Projeto Mobile</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bootstrap/5.3.0/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.10.5/font/bootstrap-icons.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=M+PLUS+1+Code:wght@400;700&display=swap');

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html, body {
            height: 100%;
            overflow-x: hidden;
            font-family: 'M PLUS 1 Code', monospace;
            background: #000;
            color: #fff;
        }

        /* Canvas Matrix Background */
        #matrix {
            position: fixed;
            top: 0;
            left: 0;
            z-index: -1;
            width: 100vw;
            height: 100vh;
        }

        /* Main Container */
        .main-container {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 20px;
            position: relative;
            z-index: 10;
        }

        /* Logo Animation */
        .logo-container {
            margin-bottom: 2rem;
            animation: pulse 2s infinite;
        }

        .logo-container img {
            width: 120px;
            height: 120px;
            object-fit: contain;
            filter: brightness(0.7);
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }

        /* Title */
        .main-title {
            font-size: 2rem;
            font-weight: bold;
            text-align: center;
            margin-bottom: 1rem;
            color: #fff;
        }

        /* Description */
        .description {
            text-align: center;
            margin-bottom: 2rem;
            max-width: 300px;
            font-size: 0.9rem;
            color: #ccc;
        }

        /* Buttons Container */
        .buttons-container {
            width: 100%;
            max-width: 320px;
            margin-bottom: 2rem;
        }

        /* Custom Buttons */
        .btn-custom {
            width: 100%;
            height: 85px;
            border: 2px solid;
            background: rgba(0, 0, 0, 0.95);
            font-family: 'M PLUS 1 Code', monospace;
            font-size: 1.1rem;
            font-weight: bold;
            text-transform: uppercase;
            transition: all 0.3s ease;
            margin-bottom: 1rem;
            position: relative;
            overflow: hidden;
            -webkit-tap-highlight-color: transparent;
            touch-action: manipulation;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 15px 25px;
            backdrop-filter: blur(10px);
            border-radius: 8px;
        }

        .btn-custom img {
            max-width: 220px;
            max-height: 55px;
            object-fit: contain;
            filter: brightness(1.2) contrast(1.2) saturate(1.1);
            image-rendering: -webkit-optimize-contrast;
            image-rendering: crisp-edges;
        }

        .btn-custom:hover img, .btn-custom:active img {
            filter: brightness(1.4) contrast(1.3) saturate(1.2);
            transform: scale(1.05);
        }

        .btn-red {
            border-color: #ff0000;
            color: #ff0000;
            box-shadow: 0 0 15px rgba(255, 0, 0, 0.4);
        }

        .btn-red:hover, .btn-red:active {
            background: rgba(255, 0, 0, 0.1);
            transform: scale(1.02);
            box-shadow: 0 0 25px rgba(255, 0, 0, 0.7);
        }

        .btn-yellow {
            border-color: #ffc400;
            color: #ffc400;
            box-shadow: 0 0 15px rgba(255, 196, 0, 0.4);
        }

        .btn-yellow:hover, .btn-yellow:active {
            background: rgba(255, 196, 0, 0.1);
            transform: scale(1.02);
            box-shadow: 0 0 25px rgba(255, 196, 0, 0.7);
        }

        /* Social Icons */
        .social-icons {
            display: flex;
            gap: 2rem;
            margin-bottom: 2rem;
        }

        .social-icons a {
            color: #fff;
            font-size: 2rem;
            transition: all 0.3s ease;
            -webkit-tap-highlight-color: transparent;
        }

        .social-icons a:hover {
            transform: scale(1.2);
        }

        .social-icons .instagram:hover {
            color: #e1306c;
            text-shadow: 0 0 15px rgba(225, 48, 108, 0.8);
        }

        .social-icons .telegram:hover {
            color: #0088cc;
            text-shadow: 0 0 15px rgba(0, 136, 204, 0.8);
        }

        .social-icons .whatsapp:hover {
            color: #25d366;
            text-shadow: 0 0 15px rgba(37, 211, 102, 0.8);
        }

        /* Footer */
        .footer-text {
            text-align: center;
            font-size: 0.8rem;
            color: #666;
        }

        /* Mobile Optimizations */
        @media (max-width: 480px) {
            .main-title {
                font-size: 1.5rem;
            }

            .logo-container img {
                width: 100px;
                height: 100px;
            }

            .buttons-container {
                max-width: 280px;
            }

            .btn-custom {
                height: 75px;
                font-size: 1rem;
                padding: 12px 20px;
            }
            
            .btn-custom img {
                max-width: 200px;
                max-height: 50px;
            }

            .social-icons {
                gap: 1.5rem;
            }

            .social-icons a {
                font-size: 1.8rem;
            }
        }

        @media (max-width: 320px) {
            .main-title {
                font-size: 1.3rem;
            }

            .buttons-container {
                max-width: 260px;
            }
        }

        /* Loading Animation */
        .loading {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 9999;
            justify-content: center;
            align-items: center;
        }

        .spinner {
            border: 4px solid #333;
            border-top: 4px solid #ff0000;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* iFrame Container */
        #iframe-container {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 9999;
            background: #000;
        }

        #site-iframe {
            width: 100%;
            height: 100%;
            border: none;
        }

        /* Draggable Hacker Icon */
        .hacker-icon {
            position: fixed;
            width: 80px;
            height: 80px;
            background: rgba(0, 0, 0, 0.8);
            border: 2px solid #ff0000;
            border-radius: 50%;
            display: none;
            align-items: center;
            justify-content: center;
            cursor: move;
            z-index: 10001;
            font-size: 2rem;
            color: #ff0000;
            box-shadow: 0 0 20px rgba(255, 0, 0, 0.5);
            transition: all 0.3s ease;
            user-select: none;
            -webkit-user-select: none;
            -moz-user-select: none;
            -ms-user-select: none;
            touch-action: none;
            animation: hackerPulse 2s infinite;
        }

        .hacker-icon:hover {
            transform: scale(1.1);
            box-shadow: 0 0 30px rgba(255, 0, 0, 0.8);
        }

        .hacker-icon.dragging {
            transform: scale(1.2);
            box-shadow: 0 0 40px rgba(255, 0, 0, 1);
        }

        .hacker-icon img {
            width: 100%;
            height: 100%;
            object-fit: contain;
            border-radius: 50%;
        }

        @keyframes hackerPulse {
            0%, 100% { 
                box-shadow: 0 0 20px rgba(255, 0, 0, 0.5);
            }
            50% { 
                box-shadow: 0 0 30px rgba(255, 0, 0, 0.8);
            }
        }

        /* Loading Overlay */
        .loading-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 10002;
            overflow: hidden;
        }

        .loading-overlay::before {
            content: "";
            position: absolute;
            top: 40%;
            left: -9%;
            width: 122%;
            height: 5px;
            background-color: rgb(128, 0, 0);
            animation: moveUpDown 2s ease-in-out infinite;
        }

        .loading-overlay::after {
            content: "";
            position: absolute;
            left: 50%;
            top: -10%;
            width: 5px;
            height: 120%;
            background-color: rgb(128, 0, 0);
            animation: moveLeftRight 2s ease-in-out infinite;
        }

        .hackeando-text {
            color: red;
            font-size: 28px;
            font-weight: bold;
            z-index: 10000;
            position: relative;
            text-align: center;
            text-shadow: 0 0 10px red, 0 0 20px red;
        }

        /* Animação vertical do risco horizontal */
        @keyframes moveUpDown {
            0% {
                top: 20%;
            }
            50% {
                top: 50%;
            }
            100% {
                top: 60%;
            }
        }

        /* Animação horizontal do risco vertical */
        @keyframes moveLeftRight {
            0% {
                left: 20%;
            }
            50% {
                left: 50%;
            }
            100% {
                left: 80%;
            }
        }

        /* Grid Container */
        .white-square {
            width: 402px;
            height: 448px;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            z-index: 10000;
            overflow: hidden;
            pointer-events: none;
            display: none;
        }

        .grid-container {
            display: grid;
            grid-template-columns: repeat(5, 71px);
            grid-template-rows: repeat(5, 70px);
            gap: 5px;
            height: 100%;
            width: 100%;
        }

        .grid-item {
            background-color: rgba(255, 255, 255, 0);
            border: 15px solid rgba(0, 0, 0, 0);
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .grid-item img {
            max-width: 100%;
            max-height: 100%;
        }

        /* Context Options */
        .context-options {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: rgba(0, 0, 0, 0.8);
            padding: 15px;
            border-radius: 10px;
            font-family: 'M PLUS 1 Code', sans-serif;
            color: #ffffff;
            display: none;
            z-index: 10000;
            overflow: hidden;
            filter: contrast(1.2) brightness(0.8);
        }

        .assertividade {
            font-size: 18px;
            margin-bottom: 10px;
            color: green;
            text-align: center;
        }

        /* Video Background */
        .video-background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            z-index: -2;
        }

        .video-background video {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            min-width: 100%;
            min-height: 100%;
            width: auto;
            height: auto;
            object-fit: cover;
        }

        /* Mobile adjustments */
        @media (max-width: 480px) {
            .hacker-icon {
                width: 60px;
                height: 60px;
                font-size: 1.5rem;
            }

            .white-square {
                width: 300px;
                height: 336px;
            }

            .grid-container {
                grid-template-columns: repeat(5, 53px);
                grid-template-rows: repeat(5, 53px);
                gap: 4px;
            }

            .grid-item {
                border: 10px solid rgba(0, 0, 0, 0);
            }

            .hackeando-text {
                font-size: 22px;
            }
        }
    </style>
</head>
<body>
    <!-- Video Background -->
    <div class="video-background">
        <video autoplay muted loop playsinline id="background-video">
            <source src="https://assets.codepen.io/3364143/7btrrd.mp4" type="video/mp4">
            Seu navegador não suporta vídeos.
        </video>
    </div>

    <!-- Matrix Background Canvas -->
    <canvas id="matrix"></canvas>

    <!-- Loading Overlay -->
    <div id="loading" class="loading">
        <div class="spinner"></div>
    </div>

    <!-- Hacking Overlay -->
    <div id="loading-overlay" class="loading-overlay"></div>

    <!-- Context Options -->
    <div id="contextOptions" class="context-options"></div>

    <!-- Grid Container -->
    <div class="white-square" id="white-square">
        <div class="grid-container">
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
        </div>
    </div>

    <!-- Main Content -->
    <div class="main-container" id="main-container">
        <!-- Logo -->
        <div class="logo-container">
            <img src="https://via.placeholder.com/120x120/000000/ffffff?text=LOGO" alt="Logo">
        </div>

        <!-- Title -->
        <h1 class="main-title">PROJETO MOBILE</h1>

        <!-- Description -->
        <p class="description">
            Interface otimizada para dispositivos móveis
        </p>

        <!-- Action Buttons -->
        <div class="buttons-container">
            <button class="btn-custom btn-red" onclick="openSite('https://winrico.net/yhgcds1al')">
                <img src="https://i.postimg.cc/Xqz8QZPX/winrico-logo.png" alt="WinRico" loading="lazy">
            </button>
            <button class="btn-custom btn-yellow" onclick="openSite('https://como.bet/yvrgjmbyb')">
                <img src="https://i.postimg.cc/VkQJBLhL/como-bet-logo.png" alt="Como.bet" loading="lazy">
            </button>
        </div>

        <!-- Social Icons -->
        <div class="social-icons">
            <a href="#" class="instagram">
                <i class="bi bi-instagram"></i>
            </a>
            <a href="#" class="telegram">
                <i class="bi bi-telegram"></i>
            </a>
            <a href="#" class="whatsapp">
                <i class="bi bi-whatsapp"></i>
            </a>
        </div>

        <!-- Footer -->
        <div class="footer-text">
            <p>Projeto Escolar - Layout Mobile</p>
        </div>
    </div>

    <!-- iFrame Container -->
    <div id="iframe-container">
        <iframe id="site-iframe" src="/placeholder.svg" title="Site Externo"></iframe>
    </div>

    <!-- Draggable Hacker Icon -->
    <div id="hacker-icon" class="hacker-icon" onclick="stopScroll()">
        <img src="https://i.ibb.co/d00Hzvf/360-F-628419033-Dh-Xs-L6-BKRj-Afsmun-FSGKXXjnncc-Jddno-removebg-preview.png" alt="Hacker">
    </div>

    <script>
        // Matrix Rain Effect
        const canvas = document.getElementById("matrix");
        const ctx = canvas.getContext("2d");

        function resizeCanvas() {
            canvas.height = window.innerHeight;
            canvas.width = window.innerWidth;
        }

        resizeCanvas();
        window.addEventListener('resize', resizeCanvas);

        const letters = ["日","ﾊ","ﾐ","ﾋ","ｰ","ｳ","ｼ","ﾅ","ﾓ","ﾆ","ｻ","ﾜ","ﾂ","ｵ","ﾘ","ｱ","ﾎ","ﾃ","ﾏ","ｹ","ﾒ","エ","カ","キ","ム","ユ","ラ","セ","ネ","ス","タ","ヌ","ヘ",":","・",".","=","*","+","-","<",">","¦","｜","ﾘ"];
        const fontSize = 18;
        const columns = canvas.width / fontSize;
        const drops = new Array(Math.floor(columns)).fill(1);

        function draw() {
            ctx.fillStyle = "rgba(0, 0, 0, 0.1)";
            ctx.fillRect(0, 0, canvas.width, canvas.height);
            ctx.fillStyle = "#FF0000";
            ctx.font = `${fontSize}px arial`;

            for (let i = 0; i < drops.length; i++) {
                const text = letters[Math.floor(Math.random() * letters.length)];
                ctx.fillText(text, i * fontSize, drops[i] * fontSize);

                if (drops[i] * fontSize > canvas.height && Math.random() > 0.95) {
                    drops[i] = 0;
                }
                drops[i]++;
            }

            window.requestAnimationFrame(draw);
        }

        draw();

        // Draggable functionality
        let isDragging = false;
        let dragOffset = { x: 0, y: 0 };
        const hackerIcon = document.getElementById('hacker-icon');

        // Mouse events
        hackerIcon.addEventListener('mousedown', startDrag);
        document.addEventListener('mousemove', drag);
        document.addEventListener('mouseup', stopDrag);

        // Touch events
        hackerIcon.addEventListener('touchstart', startDragTouch, { passive: false });
        document.addEventListener('touchmove', dragTouch, { passive: false });
        document.addEventListener('touchend', stopDrag);

        function startDrag(e) {
            e.preventDefault();
            isDragging = true;
            hackerIcon.classList.add('dragging');
            
            const rect = hackerIcon.getBoundingClientRect();
            dragOffset.x = e.clientX - rect.left;
            dragOffset.y = e.clientY - rect.top;
        }

        function startDragTouch(e) {
            e.preventDefault();
            isDragging = true;
            hackerIcon.classList.add('dragging');
            
            const rect = hackerIcon.getBoundingClientRect();
            const touch = e.touches[0];
            dragOffset.x = touch.clientX - rect.left;
            dragOffset.y = touch.clientY - rect.top;
        }

        function drag(e) {
            if (!isDragging) return;
            e.preventDefault();
            
            const x = e.clientX - dragOffset.x;
            const y = e.clientY - dragOffset.y;
            
            // Keep icon within screen bounds
            const maxX = window.innerWidth - hackerIcon.offsetWidth;
            const maxY = window.innerHeight - hackerIcon.offsetHeight;
            
            hackerIcon.style.left = Math.max(0, Math.min(x, maxX)) + 'px';
            hackerIcon.style.top = Math.max(0, Math.min(y, maxY)) + 'px';
        }

        function dragTouch(e) {
            if (!isDragging) return;
            e.preventDefault();
            
            const touch = e.touches[0];
            const x = touch.clientX - dragOffset.x;
            const y = touch.clientY - dragOffset.y;
            
            const maxX = window.innerWidth - hackerIcon.offsetWidth;
            const maxY = window.innerHeight - hackerIcon.offsetHeight;
            
            hackerIcon.style.left = Math.max(0, Math.min(x, maxX)) + 'px';
            hackerIcon.style.top = Math.max(0, Math.min(y, maxY)) + 'px';
        }

        function stopDrag() {
            isDragging = false;
            hackerIcon.classList.remove('dragging');
        }

        // Site functions
        function openSite(url) {
            const loading = document.getElementById('loading');
            loading.style.display = 'flex';

            setTimeout(() => {
                loading.style.display = 'none';
                document.getElementById('main-container').style.display = 'none';
                document.getElementById('site-iframe').src = url;
                document.getElementById('iframe-container').style.display = 'block';
                document.body.style.overflow = 'hidden';
                
                // Show hacker icon
                showHackerIcon();
            }, 1500);
        }

        function closeSite() {
            document.getElementById('iframe-container').style.display = 'none';
            document.getElementById('site-iframe').src = '';
            document.getElementById('main-container').style.display = 'flex';
            document.body.style.overflow = 'auto';
            
            // Hide hacker icon
            hideHackerIcon();
            
            // Hide grid and overlay
            document.getElementById('white-square').style.display = 'none';
            document.getElementById('loading-overlay').style.display = 'none';
        }

        // Hacker icon functions
        function showHackerIcon() {
            hackerIcon.style.display = 'flex';
            hackerIcon.style.left = '20px';
            hackerIcon.style.top = '60px';
        }

        function hideHackerIcon() {
            hackerIcon.style.display = 'none';
        }

        // Hacking function
        function stopScroll() {
            if (isDragging) return; // Don't activate if dragging
            
            const loadingOverlay = document.getElementById('loading-overlay');
            const contextOptions = document.getElementById('contextOptions');
            const whiteSquare = document.getElementById('white-square');

            // 1. Mostrar o overlay de carregamento
            if (loadingOverlay) {
                loadingOverlay.style.display = 'flex';
                loadingOverlay.innerHTML = '';

                const hackeandoText = document.createElement('div');
                hackeandoText.textContent = 'HACKEANDO MINES';
                hackeandoText.className = 'hackeando-text';
                loadingOverlay.appendChild(hackeandoText);
            }

            // 2. Após 5 segundos, esconder loading e exibir diamantes
            setTimeout(() => {
                // Esconder overlay de carregamento
                if (loadingOverlay) {
                    loadingOverlay.style.display = 'none';
                }

                // Mostrar o grid
                if (whiteSquare) {
                    whiteSquare.style.display = 'block';
                }

                // Lógica principal: inserir elemento de "Assertividade" e diamantes
                const assertividade = '100%';
                if (contextOptions) {
                    // Remove assertividade anterior, se existir
                    const existing = contextOptions.querySelector('.assertividade');
                    if (existing) {
                        contextOptions.removeChild(existing);
                    }

                    // Cria e adiciona assertividade
                    const assertElem = document.createElement('div');
                    assertElem.textContent = `Assertividade: ${assertividade}`;
                    assertElem.className = 'assertividade';
                    contextOptions.appendChild(assertElem);
                    contextOptions.style.display = 'block';

                    // Limpa o grid e insere diamantes em posições aleatórias
                    const gridItems = document.querySelectorAll('.grid-item');
                    gridItems.forEach(item => item.innerHTML = '');

                    const numDiamantes = Math.floor(Math.random() * 5) + 1;
                    const shuffled = Array.from(gridItems).sort(() => Math.random() - 0.5);
                    for (let i = 0; i < numDiamantes; i++) {
                        const cell = shuffled[i];
                        if (cell) {
                            const urlDiamante = 'https://brwinner.net/mines/zs.png';
                            cell.innerHTML = `<img src="${urlDiamante}" alt="Diamante">`;
                        }
                    }
                }

                // 3. Após 7 segundos, restaurar tudo
                setTimeout(() => {
                    // Remove assertividade (se existir)
                    if (contextOptions) {
                        contextOptions.style.display = 'none';
                        const assertElem = contextOptions.querySelector('.assertividade');
                        if (assertElem) {
                            contextOptions.removeChild(assertElem);
                        }
                    }

                    // Limpa o grid novamente
                    const allItems = document.querySelectorAll('.grid-item');
                    allItems.forEach(item => item.innerHTML = '');

                    // Esconde o grid
                    if (whiteSquare) {
                        whiteSquare.style.display = 'none';
                    }
                }, 7000); // 7 segundos para restaurar
            }, 5000); // 5 segundos de "carregando"
        }

        // Adicionar evento de teclado para fechar o site (Escape)
        document.addEventListener('keydown', function(e) {
            if (e.key === 'Escape' && document.getElementById('iframe-container').style.display === 'block') {
                closeSite();
            }
        });

        // Video background
        document.addEventListener('DOMContentLoaded', function () {
            var video = document.getElementById('background-video');

            // Tenta reproduzir o vídeo quando a página é carregada
            video.play().then(() => {
                // Sucesso, o vídeo está sendo reproduzido
            }).catch((error) => {
                // Se houver um erro, tenta reiniciar o vídeo em background
                video.muted = true;
                video.play();
            });
        });

        // Touch optimization
        document.addEventListener('touchstart', function() {}, {passive: true});

        let lastTouchEnd = 0;
        document.addEventListener('touchend', function (event) {
            const now = (new Date()).getTime();
            if (now - lastTouchEnd <= 300) {
                event.preventDefault();
            }
            lastTouchEnd = now;
        }, false);
    </script>
</body>
</html>
