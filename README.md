
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Hacker Mines</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=M+PLUS+1+Code&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }
        
        html, body {
            font-family: 'M PLUS 1 Code', monospace;
            height: 100%;
            width: 100%;
            overflow-x: hidden;
            background-color: #00000000;
            color: #fff;
            position: relative;
        }
        
        /* Matrix Canvas */
        #matrix {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
        }
        
        /* Login Container */
        .login-wrapper {
            display: flex;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            width: 100%;
            padding: 20px;
        }
        
        .custom-container {
            width: 100%;
            max-width: 320px;
            text-align: center;
        }
        
        /* Animated Logo */
        #animated-image {
            width: 120px;
            height: auto;
            margin: 0 auto 30px;
            filter: brightness(50%);
            animation: pulse 1.5s infinite;
        }
        
        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }
        
        /* Text */
        .register-form p {
            color: #fff;
            margin-bottom: 20px;
            font-size: 14px;
        }
        
        /* Buttons */
        .btn-row {
            display: flex;
            gap: 10px;
            margin-bottom: 30px;
        }
        
        .btn {
            flex: 1;
            height: 60px;
            border: none;
            border-radius: 8px;
            font-family: 'M PLUS 1 Code', monospace;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            position: relative;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
        }
        
       .btn-primary1 {
    background-color: #000;
    border: 2px solid #8e8484;
    color: #fff;
    box-shadow: 0 0 10px rgb(203 160 160 / 50%), 0 0 20px rgb(189 154 154 / 30%);}
        
        .btn-primary2 {
             background-color: #000;
    border: 2px solid #8e8484;
    color: #fff;
    box-shadow: 0 0 10px rgb(203 160 160 / 50%), 0 0 20px rgb(189 154 154 / 30%);
        }
        
        .btn::before {
            content: '';
            position: absolute;
            top: -200%;
            left: 0;
            width: 100%;
            height: 200%;
            transform: rotate(45deg);
            transition: all 0.5s ease;
        }
        
  .btn-primary1::before {
    background: rgb(255 255 255 / 54%);
}
        .btn-primary2::before {
            background: rgb(255 255 255 / 54%);
        }

        .btn:hover::before {
            top: 0;
        }

        .btn:hover {
            transform: scale(1.05);
        }

        .btn:active {
            transform: scale(0.95);
        }

        .btn-primary1:hover {
            background-color: transparent;
            color: #000;
            box-shadow: 0 0 30px rgba(255 255 255 / 54%);
        }

        .btn-primary2:hover {
            background-color: transparent;
            color: #000;
            box-shadow: 0 0 30px rgba(255, 230, 0, 0.8);
        }

        .large-icon {
            width: 80%;
            max-width: 100px;
            height: auto;
        }

        /* Social Icons */
        .social-icons {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
        }

        .social-icons a {
            color: #fff;
            font-size: 28px;
            transition: all 0.3s ease;
            position: relative;
        }

        .social-icons a.instagram:hover {
            color: #C13584;
            transform: scale(1.2);
            text-shadow: 0 0 15px rgba(225, 48, 108, 0.8);
        }

        .social-icons a.telegram:hover {
            color: #0088cc;
            transform: scale(1.2);
            text-shadow: 0 0 15px rgba(0, 172, 238, 0.8);
        }

        .social-icons a.whatsapp:hover {
            color: #25D366;
            transform: scale(1.2);
            text-shadow: 0 0 15px rgba(18, 140, 126, 0.8);
        }

        /* Iframe Container */
        #iframe-container {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 100;
        }

        iframe {
            width: 100%;
            height: 100%;
            border: none;
        }

        /* Hacker Icon - Fixo (sem arrastar) */
        @keyframes hackerPulse {
            0% {
                box-shadow: 0 0 0 0 rgba(255, 0, 0, 0.7);
            }
            70% {
                box-shadow: 0 0 0 15px rgba(255, 0, 0, 0);
            }
            100% {
                box-shadow: 0 0 0 0 rgba(255, 0, 0, 0);
            }
        }

        .hacker-icon {
            position: fixed;
            top: 20px;
            right: 20px;
            width: 120px;
            height: 120px;
            background: rgba(0, 0, 0, 0.8);
            border: 2px solid #ff0000;
            border-radius: 50%;
            display: none;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            z-index: 10001;
            font-size: 2rem;
            color: #ff0000;
            box-shadow: 0 0 20px rgba(255, 0, 0, 0.5);
            transition: all 0.3s ease;
            user-select: none;
            -webkit-user-select: none;
            -moz-user-select: none;
            -ms-user-select: none;
            animation: hackerPulse 2s infinite;
        }

        .hacker-icon:hover {
            transform: scale(1.1);
            box-shadow: 0 0 30px rgba(255, 0, 0, 0.8);
        }

        .hacker-icon:active {
            transform: scale(0.95);
        }

        .hacker-icon img {
            width: 80%;
            height: auto;
        }

        @media (hover: none) and (pointer: coarse) {
            .hacker-icon {
                cursor: pointer;
            }
        }

        @media (max-width: 480px) {
            .hacker-icon {
                width: 90px !important;
                height: 90px !important;
                font-size: 1.5rem;
                top: 80% !important;
                right: 75px !important;
            }
        }

       .white-square {
    width: 402px;
    height: 448px;
    position: absolute;
    top: 154px;
    left: 7px;
    z-index: 10000;
    overflow: hidden;
    pointer-events: none;
}
.grid-container {
    display: grid
;
    grid-template-columns: repeat(5, 71px);
    grid-template-rows: repeat(5, 70px);
    gap: 5px;
    height: 100%;
    width: 100%;
}
.grid-item {
    background-color: #ffffff00;
    border: 15px solid #00000000;
}
        .grid-item img {
            width: 100%;
            height: auto;
            max-width: 40px;
        }
        .markdown-body img {
    background-color: transparent !important;
}

        
        /* Context Menu */
        .context-options {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: rgba(0, 0, 0, 0.8);
            padding: 20px;
            border-radius: 10px;
            border: 2px solid #285ff4;
            font-family: 'M PLUS 1 Code', sans-serif;
            color: #ffffff;
            display: none;
            z-index: 10000;
            width: 280px;
            max-width: 90vw;
        }
        
        .context-options .background-video {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
            z-index: -1;
            opacity: 0.3;
            border-radius: 8px;
        }
        
        .context-options .bot-title {
            font-size: 18px;
            text-align: center;
            margin-bottom: 20px;
            display: block;
            color: #ffffff;
        }
        
        .context-options .context-option {
            width: 100%;
            height: 50px;
            border: 2px solid rgb(255, 0, 0);
            color: rgb(255, 0, 0);
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            background: rgba(0, 0, 0, 0.8);
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            border-radius: 25px;
            z-index: 3;
            box-shadow: rgba(255, 0, 0, 0.5) 0px 0px 10px;
            transition: background-color 0.3s, transform 0.2s, box-shadow 0.2s;
            margin-top: 10px;
        }
        
        .context-options .context-option:active {
            transform: scale(0.95);
            box-shadow: 0 0 20px red, 0 0 40px rgba(255, 0, 0, 0.6);
            background-color: rgba(255, 0, 0, 0.2);
        }
        
        .assertividade {
            font-size: 18px;
            margin-bottom: 10px;
            color: #00ff00;
            text-align: center;
            font-weight: bold;
            text-shadow: 0 0 5px rgba(0, 255, 0, 0.5);
        }
        
        /* Loading Animation */
        .loading-hidden {
            display: none;
        }
        
        .loading-visible {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 10001;
        }
        
       h1 {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  clip-path: inset(50%);
  white-space: nowrap;
}
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        .hackeando-text {
            color: red;
            font-size: 24px;
            font-weight: bold;
            margin-top: 20px;
            text-shadow: 0 0 10px red, 0 0 20px red;
        }
        
        /* Loading Overlay */
        #loading-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            flex-direction: column;
        }
        
        /* Mobile Optimizations */
        @media (max-width: 480px) {
            .custom-container {
                padding: 0 10px;
            }
            
            #animated-image {
                width: 100px;
            }
            
            .social-icons a {
                font-size: 24px;
            }
          
        }
    </style>
</head>

<body>
    <!-- Matrix Background Canvas -->
    <canvas id="matrix"></canvas>

    <!-- Login Screen -->
    <div class="login-wrapper" id="login-wrapper">
        <div class="custom-container">
            <img id="animated-image" src="https://i.ibb.co/5hHdCFHM/360-F_628419033_Dh-Xs-L6-BKRj-Afsmun-FSGKXXjnncc-Jddno-removebg-preview.png" alt="Hacker Logo" class="img-fluid">
            
            <div class="register-form">
                <p>Escolha a Plataforma Chinesa para Hackear</p>
                <div class="btn-row">
                    <button class="btn btn-primary1" type="button" onclick="login('https://sheik.cc/ypi8223jx')">
                        <img src="https://sheik.cc/img/logo.9abb6909.png" alt="Logo" class="large-icon">
                    </button>
                    <button class="btn btn-primary2" type="button" onclick="login('https://sheik.cc/ypi8223jx')">
                        <img src="https://sheik.cc/img/logo.9abb6909.png" alt="Logo" class="large-icon">
                    </button>
                </div>
                
                <div class="social-icons">
                    <a href="https://www.instagram.com/marquez.digital/?hl=pt-br" target="_blank" class="instagram">
                        <i class="fab fa-instagram"></i>
                    </a>
                    <a href="@MarquezBlaze" target="_blank" class="telegram">
                        <i class="fab fa-telegram"></i>
                    </a>
                    <a href="https://api.whatsapp.com/send/?phone=5542998059651&text&type=phone_number&app_absent=0" target="_blank" class="whatsapp">
                        <i class="fab fa-whatsapp"></i>
                    </a>
                </div>
            </div>
        </div>
    </div>

    <!-- Iframe Container -->
    <div id="iframe-container">
        <iframe id="login-iframe" src="/placeholder.svg"></iframe>
        
        <!-- Hacker Icon Fixo -->
        <div id="hacker-icon" class="hacker-icon" onclick="activateHacker()" style="display: flex;">
            <img src="https://i.ibb.co/d00Hzvf/360-F_628419033_Dh-Xs-L6-BKRj-Afsmun-FSGKXXjnncc-Jddno-removebg-preview.png" alt="Hacker">
        </div>
        
        <!-- Grid Overlay -->
        <div class="white-square">
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
        
        <!-- Loading Overlay -->
        <div id="loading-overlay" class="loading-overlay"></div>
        
        <!-- Overlay for black background -->
        <div id="overlay" class="overlay" style="display: none;"></div>
    </div>



    <!-- Simple Loading Animation (for iframe loading) -->
    <div id="simple-loading" class="loading-hidden">
        <div class="spinner"></div>
    </div>

    <script>
        // Matrix Rain Effect
        const c = document.getElementById("matrix");
        const ctx = c.getContext("2d");
        
        function resizeCanvas() {
            c.height = window.innerHeight;
            c.width = window.innerWidth;
        }
        
        resizeCanvas();
        window.addEventListener('resize', resizeCanvas);
        
        const letters = ["日","ﾊ","ﾐ","ﾋ","ｰ","ｳ","ｼ","ﾅ","ﾓ","ﾆ","ｻ","ﾜ","ﾂ","ｵ","ﾘ","ｱ","ﾎ","ﾃ","ﾏ","ｹ","ﾒ","エ","カ","キ","ム","ユ","ラ","セ","ネ","ス","タ","ヌ","ヘ",":","・",".","=","*","+","-","<",">","¦","｜","ﾘ"];
        const fontSize = 18;
        const columns = c.width / fontSize;
        const drops = new Array(Math.floor(columns)).fill(1);
        
        function draw() {
            ctx.fillStyle = "rgba(0, 0, 0, 0.1)";
            ctx.fillRect(0, 0, c.width, c.height);
            
            ctx.fillStyle = "#FF0000";
            ctx.font = `${fontSize}px arial`;
            
            for (let i = 0; i < drops.length; i++) {
                const text = letters[Math.floor(Math.random() * letters.length)];
                ctx.fillText(text, i * fontSize, drops[i] * fontSize);
                
                if (drops[i] * fontSize > c.height && Math.random() > 0.95) {
                    drops[i] = 0;
                }
                
                drops[i]++;
            }
            
            window.requestAnimationFrame(draw);
        }
        
        draw();
        
        // Login Function - Modificado para mostrar apenas um loading simples
        function login(url) {
            document.getElementById('login-wrapper').style.display = 'none';
            document.getElementById('iframe-container').style.display = 'block';
            
            // Mostrar loading simples
            const simpleLoading = document.getElementById('simple-loading');
            simpleLoading.className = 'loading-visible';
            
            // Carregar o iframe
            const iframe = document.getElementById('login-iframe');
            iframe.src = url;
            
            // Esconder loading quando o iframe carregar
            iframe.onload = function() {
                simpleLoading.className = 'loading-hidden';
            };
            
            // Timeout de segurança para esconder o loading caso o iframe não carregue
            setTimeout(function() {
                simpleLoading.className = 'loading-hidden';
            }, 5000);
        }
        const link = document.querySelector('h1 a[href="https://aplicativomarquez.github.io/"]');
if (link && link.parentElement.tagName === 'H1') {
    link.parentElement.remove();
}
function activateHacker() {
    // Criar o overlay de loading
    let loadingOverlay = document.createElement("div");
    loadingOverlay.style.position = "fixed";
    loadingOverlay.style.top = "0";
    loadingOverlay.style.left = "0";
    loadingOverlay.style.width = "100%";
    loadingOverlay.style.height = "100%";
    loadingOverlay.style.backgroundColor = "rgba(0, 0, 0, 0.9)";
    loadingOverlay.style.zIndex = "99999";
    loadingOverlay.style.display = "flex";
    loadingOverlay.style.flexDirection = "column";
    loadingOverlay.style.alignItems = "center";
    loadingOverlay.style.justifyContent = "center";
    document.body.appendChild(loadingOverlay);

    // Texto de loading
    let loadingTextEl = document.createElement("div");
    loadingTextEl.innerHTML = "HACKEANDO PLATAFORMA...";
    loadingTextEl.style.color = "#ff0000";
    loadingTextEl.style.fontSize = "24px";
    loadingTextEl.style.fontWeight = "bold";
    loadingTextEl.style.marginBottom = "16px";
    loadingTextEl.style.fontFamily = "monospace";
    loadingTextEl.style.letterSpacing = "2px";
    loadingTextEl.style.textShadow = "0 0 10px rgba(255, 0, 0, 0.8)";
    loadingOverlay.appendChild(loadingTextEl);

    // Barra de progresso
    let loadingBarContainer = document.createElement("div");
    loadingBarContainer.style.width = "60%";
    loadingBarContainer.style.maxWidth = "600px";
    loadingBarContainer.style.height = "12px";
    loadingBarContainer.style.backgroundColor = "rgba(255, 255, 255, 0.2)";
    loadingBarContainer.style.borderRadius = "6px";
    loadingBarContainer.style.border = "1px solid rgba(255, 0, 0, 0.5)";
    loadingBarContainer.style.marginBottom = "16px";
    loadingOverlay.appendChild(loadingBarContainer);

    let loadingBar = document.createElement("div");
    loadingBar.style.height = "100%";
    loadingBar.style.width = "0";
    loadingBar.style.background = "linear-gradient(90deg, #ff0000, #ff4444, #ff0000)";
    loadingBar.style.transition = "width 4s ease-in-out";
    loadingBar.style.borderRadius = "6px";
    loadingBar.style.boxShadow = "0 0 15px rgba(255, 0, 0, 0.7)";
    loadingBarContainer.appendChild(loadingBar);

    setTimeout(() => {
        loadingBar.style.width = "100%";
    }, 100);

    // ALERTA PERSONALIZADO
    setTimeout(() => {
        loadingOverlay.innerHTML = ""; // Limpa o conteúdo anterior

        let alertBox = document.createElement("div");
        alertBox.style.background = "#000000";
        alertBox.style.padding = "30px";
        alertBox.style.border = "2px solid #ff0000";
        alertBox.style.borderRadius = "10px";
        alertBox.style.color = "#ff4444";
        alertBox.style.fontFamily = "monospace";
        alertBox.style.fontSize = "18px";
        alertBox.style.textAlign = "center";
        alertBox.style.boxShadow = "0 0 20px rgba(255,0,0,0.6)";
        alertBox.innerHTML = `
            <p><strong>⚠️ ERRO DETECTADO!</strong></p>
            <p>Você não fez a entrada no <span style="color:#ffffff">MINES</span>.</p>
            <p>Por isso, os <span style="color:#ffffff">diamantes</span> não foram revelados.</p>
            <br>
            <button id="closeAlertBtn" style="margin-top: 10px; padding: 10px 20px; background-color: #ff0000; color: white; border: none; border-radius: 6px; font-weight: bold; cursor: pointer;">
                FECHAR
            </button>
        `;
        loadingOverlay.appendChild(alertBox);

        // Botão para remover o overlay
        document.getElementById("closeAlertBtn").onclick = () => {
            document.body.removeChild(loadingOverlay);
        };
    }, 4500);
}


        // Ensure video plays on mobile
        document.addEventListener('DOMContentLoaded', function() {
            const video = document.querySelector('.background-video');
            
            if (video) {
                video.play().catch(error => {
                    video.muted = true;
                    video.play();
                });
                
                video.addEventListener('ended', () => {
                    video.play();
                });
            }
        });
    </script>
</body>
</html>
