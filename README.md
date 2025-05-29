
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>MINES - Hacker Da Blaze</title>
    <meta name="description" content="Jogue MINES e ganhe até 57% de desconto no Hacker Da Blaze!">
    <meta name="theme-color" content="#4c1d95">
    
    <!-- PWA Meta Tags -->
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="apple-mobile-web-app-title" content="MINES Game">
    
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: linear-gradient(135deg, #4c1d95, #1e3a8a, #312e81);
            min-height: 100vh;
            color: white;
            padding: 0.5rem;
            overflow-x: hidden;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 0.5rem;
        }

        .card {
            background: rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(147, 51, 234, 0.3);
            border-radius: 12px;
            padding: 1rem;
            margin-bottom: 1rem;
            backdrop-filter: blur(10px);
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
        }

        .header {
            text-align: center;
            background: rgba(0, 0, 0, 0.2);
            border: 1px solid rgba(147, 51, 234, 0.3);
            padding: 1rem 0.5rem;
        }

        .title {
            font-size: 1.5rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
            flex-wrap: wrap;
        }

        .subtitle {
            color: #c4b5fd;
            margin-bottom: 0.5rem;
            font-size: 0.9rem;
        }

        .highlight {
            color: #fde047;
            font-weight: bold;
            font-size: 0.8rem;
            text-align: center;
        }

        .player-id {
            color: #86efac;
            font-size: 0.75rem;
            margin-top: 0.5rem;
        }

        .notification {
            position: fixed;
            top: 0.5rem;
            right: 0.5rem;
            left: 0.5rem;
            background: #16a34a;
            color: white;
            padding: 0.75rem;
            border-radius: 8px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
            border: 1px solid #22c55e;
            z-index: 1000;
            animation: slideDown 0.5s ease-out;
            display: none;
            font-size: 0.875rem;
        }

        @keyframes slideDown {
            from { transform: translateY(-100%); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .video-section {
            background: rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(147, 51, 234, 0.3);
        }

        .video-container {
            position: relative;
            aspect-ratio: 16/9;
            background: rgba(0, 0, 0, 0.5);
            border-radius: 8px;
            overflow: hidden;
            margin-bottom: 1rem;
        }

        .video-placeholder {
            width: 100%;
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            background: rgba(0, 0, 0, 0.6);
        }

        .play-button {
            width: 3rem;
            height: 3rem;
            background: #dc2626;
            border: none;
            border-radius: 50%;
            color: white;
            font-size: 1.2rem;
            cursor: pointer;
            transition: all 0.3s;
            touch-action: manipulation;
        }

        .play-button:hover, .play-button:active {
            background: #b91c1c;
            transform: scale(1.1);
        }

        .button {
            padding: 0.75rem 1rem;
            border: none;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            margin: 0.25rem;
            font-size: 0.875rem;
            touch-action: manipulation;
            min-height: 44px; /* iOS touch target */
        }

        .button-primary {
            background: linear-gradient(135deg, #7c3aed, #2563eb);
            color: white;
        }

        .button-primary:hover, .button-primary:active {
            background: linear-gradient(135deg, #6d28d9, #1d4ed8);
            transform: translateY(-1px);
        }

        .button-secondary {
            background: linear-gradient(135deg, #eab308, #ea580c);
            color: white;
        }

        .button-whatsapp {
            background: linear-gradient(135deg, #16a34a, #059669);
            color: white;
            width: 100%;
            font-size: 1rem;
            padding: 1rem;
        }

        .button:disabled {
            opacity: 0.5;
            cursor: not-allowed;
            transform: none;
        }

        .button-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 0.5rem;
        }

        .game-layout {
            display: grid;
            grid-template-columns: 1fr;
            gap: 1rem;
        }

        @media (min-width: 768px) {
            .container {
                padding: 1rem;
            }
            
            .card {
                padding: 1.5rem;
                margin-bottom: 1.5rem;
            }
            
            .title {
                font-size: 2rem;
            }
            
            .subtitle {
                font-size: 1rem;
            }
            
            .highlight {
                font-size: 1rem;
            }
            
            .game-layout {
                grid-template-columns: 1fr 2fr;
                gap: 1.5rem;
            }
            
            .notification {
                top: 1rem;
                right: 1rem;
                left: auto;
                max-width: 300px;
            }
            
            .play-button {
                width: 4rem;
                height: 4rem;
                font-size: 1.5rem;
            }
        }

        .status-panel {
            background: rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(147, 51, 234, 0.3);
            order: 2;
        }

        @media (min-width: 768px) {
            .status-panel {
                order: 1;
            }
        }

        .badge {
            background: rgba(107, 114, 128, 0.8);
            color: white;
            padding: 0.5rem 1rem;
            border-radius: 6px;
            font-size: 1rem;
            display: inline-block;
            width: 100%;
            text-align: center;
        }

        .discount-display {
            font-size: 2.5rem;
            font-weight: bold;
            color: #4ade80;
            text-align: center;
        }

        @media (min-width: 768px) {
            .discount-display {
                font-size: 3rem;
            }
        }

        .price-info {
            border-top: 1px solid rgba(147, 51, 234, 0.3);
            padding-top: 1rem;
            margin-top: 1rem;
        }

        .original-price {
            text-decoration: line-through;
            color: #9ca3af;
            font-size: 0.875rem;
        }

        .final-price {
            font-size: 1.5rem;
            font-weight: bold;
            color: #4ade80;
        }

        @media (min-width: 768px) {
            .final-price {
                font-size: 2rem;
            }
        }

        .winners-list {
            border-top: 1px solid rgba(147, 51, 234, 0.3);
            padding-top: 1rem;
            margin-top: 1rem;
        }

        .winner-item {
            background: rgba(34, 197, 94, 0.3);
            border: 1px solid rgba(34, 197, 94, 0.3);
            padding: 0.5rem;
            border-radius: 4px;
            margin-bottom: 0.25rem;
            font-size: 0.75rem;
        }

        .game-board {
            background: rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(147, 51, 234, 0.3);
            order: 1;
        }

        @media (min-width: 768px) {
            .game-board {
                order: 2;
            }
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 0.25rem;
            max-width: 350px;
            margin: 0 auto;
            padding: 0.5rem;
        }

        @media (min-width: 768px) {
            .grid {
                gap: 0.5rem;
                max-width: 400px;
                padding: 0;
            }
        }

        .cell {
            aspect-ratio: 1;
            height: 3rem;
            background: #374151;
            border: 2px solid rgba(147, 51, 234, 0.5);
            border-radius: 8px;
            color: white;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            font-size: 0.75rem;
            touch-action: manipulation;
            user-select: none;
        }

        @media (min-width: 768px) {
            .cell {
                height: 4rem;
                font-size: 1rem;
            }
        }

        .cell:hover:not(:disabled), .cell:active:not(:disabled) {
            background: #4b5563;
            border-color: rgba(147, 51, 234, 0.8);
            transform: scale(0.95);
        }

        .cell:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .cell.revealed {
            background: #16a34a;
            transform: scale(1.05);
        }

        .cell.bomb {
            background: #dc2626;
            animation: shake 0.5s ease-in-out;
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-5px); }
            75% { transform: translateX(5px); }
        }

        .instructions {
            background: rgba(0, 0, 0, 0.2);
            border: 1px solid rgba(147, 51, 234, 0.3);
        }

        .instructions ul {
            list-style: none;
            padding: 0;
        }

        .instructions li {
            margin-bottom: 0.5rem;
            font-size: 0.875rem;
            line-height: 1.4;
        }

        .success-message {
            background: rgba(34, 197, 94, 0.3);
            border: 1px solid rgba(34, 197, 94, 0.5);
            padding: 1rem;
            border-radius: 8px;
            text-align: center;
        }

        .warning-message {
            background: rgba(220, 38, 38, 0.3);
            border: 1px solid rgba(220, 38, 38, 0.5);
            padding: 1rem;
            border-radius: 8px;
            text-align: center;
            color: #fca5a5;
        }

        .hidden {
            display: none;
        }

        .text-center {
            text-align: center;
        }

        .mb-4 {
            margin-bottom: 1rem;
        }

        .mt-4 {
            margin-top: 1rem;
        }

        .space-y-4 > * + * {
            margin-top: 1rem;
        }

        .flex {
            display: flex;
        }

        .justify-center {
            justify-content: center;
        }

        .gap-4 {
            gap: 1rem;
        }

        /* Loading animation */
        .loading {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 3px solid rgba(255,255,255,.3);
            border-radius: 50%;
            border-top-color: #fff;
            animation: spin 1s ease-in-out infinite;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        /* Pulse effect for important elements */
        .pulse {
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }

        /* Smooth scrolling */
        html {
            scroll-behavior: smooth;
        }

        /* Better touch feedback */
        .cell:active {
            background: #6b7280 !important;
        }

        .button:active {
            transform: scale(0.98);
        }

        /* Prevent zoom on input focus (iOS) */
        input, select, textarea {
            font-size: 16px;
        }

        /* Safe area for notched devices */
        @supports (padding: max(0px)) {
            body {
                padding-left: max(0.5rem, env(safe-area-inset-left));
                padding-right: max(0.5rem, env(safe-area-inset-right));
                padding-bottom: max(0.5rem, env(safe-area-inset-bottom));
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header -->
        <div class="card header">
            <h1 class="title">
                <span>💣</span>
                <span>MINES</span>
                <span>-</span>
                <span>Hacker Da Blaze</span>
                <span>💎</span>
            </h1>
            <p class="subtitle">Encontre os diamantes e ganhe descontos incríveis!</p>
            <p class="highlight">🎁 ALGUNS JOGADORES ESTÃO GANHANDO O PRODUTO DE GRAÇA! 🎁</p>
            <p class="player-id" id="playerId">🆔 Seu ID: <span class="loading"></span></p>
        </div>

        <!-- Notification -->
        <div class="notification" id="notification">
            <div style="display: flex; align-items: center; justify-content: space-between;">
                <div style="display: flex; align-items: center; gap: 0.5rem; flex: 1;">
                    <span>🔔</span>
                    <div style="flex: 1;">
                        <p style="font-weight: bold; font-size: 0.875rem;" id="notifName"></p>
                        <p style="font-size: 0.75rem;" id="notifDiscount"></p>
                        <p style="font-size: 0.75rem; opacity: 0.75;" id="notifTime"></p>
                    </div>
                </div>
                <button onclick="hideNotification()" style="background: none; border: none; color: white; cursor: pointer; padding: 0.5rem; font-size: 1.2rem;">✕</button>
            </div>
        </div>

        <!-- Warning if already played -->
        <div class="card warning-message hidden" id="alreadyPlayedWarning">
            <div style="display: flex; align-items: center; justify-content: center; gap: 0.5rem; flex-wrap: wrap;">
                <span>🔒</span>
                <p style="font-weight: bold; text-align: center;">Você já utilizou sua chance única! Não é possível jogar novamente.</p>
            </div>
        </div>

        <!-- Video Section -->
        <div class="card video-section" id="videoSection">
            <h2 style="color: white; margin-bottom: 1rem; display: flex; align-items: center; gap: 0.5rem; font-size: 1.25rem;">
                <span style="color: #eab308;">📹</span>
                Veja como funciona o sistema
            </h2>
            <div class="video-container">
                <div class="video-placeholder">
                    <button class="play-button" onclick="startVideo()">▶</button>
                </div>
            </div>
            <div class="button-container">
                <button class="button button-primary" onclick="startVideo()">▶ Assistir Vídeo</button>
                <button class="button button-secondary" onclick="skipVideo()">Pular Vídeo</button>
                <button class="button button-primary pulse" onclick="initializeGame()">🎮 Jogar Agora</button>
            </div>
            <p style="color: #86efac; text-align: center; font-size: 0.875rem; font-weight: bold; margin-top: 1rem;">
                ⚡ Você pode jogar sem assistir o vídeo completo!
            </p>
        </div>

        <!-- Game Layout -->
        <div class="game-layout hidden" id="gameLayout">
            <!-- Game Board -->
            <div class="card game-board">
                <h2 class="text-center" style="color: white; margin-bottom: 1rem; font-size: 1.125rem;" id="gameTitle">
                    Você tem 5 cliques! Encontre os diamantes!
                </h2>
                <div class="grid" id="gameGrid"></div>
                <div class="success-message hidden mt-4" id="winMessage">
                    <p style="color: #86efac; font-weight: bold; font-size: 1.125rem;">
                        INCRÍVEL! Você ganhou <span id="winPercent">57</span>% de desconto!
                    </p>
                    <p style="color: #bbf7d0; font-size: 0.875rem; margin-top: 0.25rem;">
                        Clique no botão "Resgatar no WhatsApp" para garantir sua promoção
                    </p>
                    <p style="color: #fde047; font-size: 0.75rem; margin-top: 0.5rem;" id="winPlayerId">🆔 Seu ID: </p>
                </div>
            </div>

            <!-- Status Panel -->
            <div class="card status-panel">
                <h2 style="color: white; margin-bottom: 1rem; display: flex; align-items: center; gap: 0.5rem; font-size: 1.125rem;">
                    <span style="color: #eab308;">🎁</span>
                    Status do Jogo
                </h2>
                <div class="space-y-4">
                    <div class="text-center">
                        <span class="badge" id="clicksLeft">Cliques Restantes: 5</span>
                    </div>
                    <div class="text-center">
                        <p style="color: #c4b5fd; margin-bottom: 0.5rem; font-size: 0.875rem;">Desconto Acumulado:</p>
                        <div class="discount-display" id="totalDiscount">0%</div>
                    </div>
                    <div class="price-info">
                        <p style="color: #c4b5fd; font-size: 0.875rem; margin-bottom: 0.5rem;">Produto: Hacker Da Blaze</p>
                        <p class="original-price">Preço Original: R$ 299,99</p>
                        <p class="final-price" id="finalPrice">Preço Final: R$ 299,99</p>
                        <p style="color: #c4b5fd; font-size: 0.875rem;" id="savings">Economia: R$ 0,00</p>
                    </div>
                    <div class="winners-list">
                        <h4 style="color: white; font-weight: bold; font-size: 0.875rem; margin-bottom: 0.5rem;">🔥 Últimos Ganhadores:</h4>
                        <div id="winnersList" style="max-height: 8rem; overflow-y: auto;"></div>
                    </div>
                    <button class="button button-whatsapp hidden pulse" id="whatsappButton" onclick="openWhatsapp()">
                        📱 Resgatar no WhatsApp
                    </button>
                    <div class="success-message hidden" id="redeemedMessage">
                        <p style="color: #86efac; font-weight: bold; font-size: 0.875rem;">✅ Promoção Resgatada!</p>
                        <p style="color: #bbf7d0; font-size: 0.75rem;" id="redeemedId">ID: </p>
                        <p style="color: #bbf7d0; font-size: 0.75rem;">Aguarde o contato via WhatsApp</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Instructions -->
        <div class="card instructions">
            <h3 style="color: white; font-weight: bold; margin-bottom: 0.75rem; font-size: 1.125rem;">Como Jogar:</h3>
            <ul style="color: #c4b5fd;">
                <li>• Você tem apenas 5 cliques para acumular desconto</li>
                <li>• Clique nas células para encontrar diamantes</li>
                <li>• Todos os cliques são diamantes - sem bombas!</li>
                <li>• Na 4ª jogada, você pode encontrar uma bomba, mas ainda ganha o desconto!</li>
                <li>• Mesmo explodindo, você garante seus 57% de desconto</li>
                <li>• Alguns jogadores estão ganhando o produto TOTALMENTE GRÁTIS!</li>
                <li>• Após os 5 cliques, resgate sua promoção pelo WhatsApp</li>
                <li>• Cada pessoa pode jogar apenas uma vez</li>
                <li>• Guarde seu ID para acompanhar o resgate</li>
            </ul>
        </div>
    </div>

    <script>
        // Game State
        let gameState = 'intro';
        let clicksLeft = 5;
        let totalDiscount = 0;
        let hasPlayed = false;
        let hasRedeemed = false;
        let clickedCells = [];
        let playerId = '';
        let cells = [];

        // Constants
        const productPrice = 299.99;
        const productName = "Hacker Da Blaze";
        const whatsappNumber = "+55 42 9848-2255";
        const clickValues = [12, 15, 13, 17, 0];

        const randomNames = [
            "Carlos M.", "Ana S.", "João P.", "Maria L.", "Pedro R.", "Julia C.",
            "Lucas O.", "Fernanda A.", "Rafael B.", "Camila T.", "Bruno F.", "Larissa M.",
            "Diego S.", "Beatriz L.", "Thiago N.", "Gabriela R.", "Mateus V.", "Isabella K.",
            "Felipe G.", "Sophia D.", "Gustavo H.", "Valentina P."
        ];

        // Generate unique player ID
        function generatePlayerId() {
            const timestamp = Date.now().toString().slice(-6);
            const random = Math.floor(Math.random() * 9999).toString().padStart(4, '0');
            return `HB${timestamp}${random}`;
        }

        // Initialize
        function init() {
            playerId = generatePlayerId();
            document.getElementById('playerId').innerHTML = `🆔 Seu ID: ${playerId}`;
            
            // Start fake notifications
            setTimeout(generateNotification, 2000);
            setInterval(() => {
                generateNotification();
            }, Math.random() * 7000 + 8000);

            // Add touch feedback
            addTouchFeedback();
        }

        // Add touch feedback for better mobile experience
        function addTouchFeedback() {
            const buttons = document.querySelectorAll('.button, .cell');
            buttons.forEach(button => {
                button.addEventListener('touchstart', function() {
                    this.style.transform = 'scale(0.95)';
                });
                button.addEventListener('touchend', function() {
                    setTimeout(() => {
                        this.style.transform = '';
                    }, 150);
                });
            });
        }

        // Generate fake notifications
        function generateNotification() {
            const name = randomNames[Math.floor(Math.random() * randomNames.length)];
            const discounts = [15, 25, 35, 45, 55, 60, 70, 80, 85, 90, 95, 100];
            const discount = discounts[Math.floor(Math.random() * discounts.length)];
            const now = new Date();
            const timestamp = `${now.getHours().toString().padStart(2, '0')}:${now.getMinutes().toString().padStart(2, '0')}`;

            document.getElementById('notifName').textContent = name;
            document.getElementById('notifDiscount').textContent = `Ganhou ${discount}% de desconto!`;
            document.getElementById('notifTime').textContent = timestamp;
            
            showNotification();
            
            // Add to winners list
            const winnersList = document.getElementById('winnersList');
            const winnerItem = document.createElement('div');
            winnerItem.className = 'winner-item';
            winnerItem.innerHTML = `
                <span style="color: #86efac; font-weight: bold;">${name}</span>
                <span style="color: white;"> - ${discount}%</span>
                <span style="color: #9ca3af; float: right;">${timestamp}</span>
            `;
            winnersList.insertBefore(winnerItem, winnersList.firstChild);
            
            // Keep only last 5 winners
            while (winnersList.children.length > 5) {
                winnersList.removeChild(winnersList.lastChild);
            }
        }

        function showNotification() {
            const notification = document.getElementById('notification');
            notification.style.display = 'block';
            setTimeout(() => {
                hideNotification();
            }, 4000);
        }

        function hideNotification() {
            document.getElementById('notification').style.display = 'none';
        }

        function startVideo() {
            console.log('Video started');
            // Add your video logic here
        }

        function skipVideo() {
            console.log('Video skipped');
        }

        function initializeGame() {
            if (hasPlayed) return;

            // Hide video section, show game
            document.getElementById('videoSection').classList.add('hidden');
            document.getElementById('gameLayout').classList.remove('hidden');

            // Initialize cells
            cells = [];
            for (let i = 0; i < 25; i++) {
                cells.push({
                    id: i,
                    isMine: false,
                    isRevealed: false,
                    discount: 0
                });
            }

            gameState = 'playing';
            clicksLeft = 5;
            totalDiscount = 0;
            hasPlayed = true;
            clickedCells = [];

            renderGame();
            
            // Scroll to game on mobile
            if (window.innerWidth < 768) {
                document.getElementById('gameLayout').scrollIntoView({ behavior: 'smooth' });
            }
        }

        function renderGame() {
            // Update UI
            document.getElementById('clicksLeft').textContent = `Cliques Restantes: ${clicksLeft}`;
            document.getElementById('totalDiscount').textContent = `${totalDiscount}%`;
            
            const finalPrice = productPrice - (productPrice * totalDiscount / 100);
            const savings = productPrice - finalPrice;
            
            document.getElementById('finalPrice').textContent = `Preço Final: R$ ${finalPrice.toFixed(2)}`;
            document.getElementById('savings').textContent = `Economia: R$ ${savings.toFixed(2)}`;

            // Render grid
            const grid = document.getElementById('gameGrid');
            grid.innerHTML = '';
            
            cells.forEach((cell, index) => {
                const cellElement = document.createElement('button');
                cellElement.className = 'cell';
                cellElement.onclick = () => handleCellClick(index);
                
                if (cell.isRevealed) {
                    cellElement.disabled = true;
                    if (cell.isMine) {
                        cellElement.classList.add('bomb');
                        cellElement.innerHTML = '💣<br><span style="font-size: 0.6rem;">BOOM!</span>';
                    } else {
                        cellElement.classList.add('revealed');
                        cellElement.innerHTML = `💎<br><span style="font-size: 0.6rem;">${cell.discount}%</span>`;
                    }
                } else if (gameState !== 'playing' || clicksLeft === 0 || hasRedeemed) {
                    cellElement.disabled = true;
                }
                
                grid.appendChild(cellElement);
            });

            // Update game title
            let title = '';
            if (gameState === 'playing') {
                title = `Você tem ${clicksLeft} cliques! Encontre os diamantes!`;
            } else if (gameState === 'won') {
                const hasExploded = cells.some(c => c.isRevealed && c.isMine);
                if (hasExploded) {
                    title = '💣 BOOM! Mas você ainda ganhou 57% de desconto!';
                } else {
                    title = '🎉 Parabéns! Você ganhou 57% de desconto!';
                }
            } else if (gameState === 'finished') {
                title = '🔒 Jogo finalizado - Promoção resgatada';
            }
            document.getElementById('gameTitle').textContent = title;

            // Re-add touch feedback to new cells
            addTouchFeedback();
        }

        function handleCellClick(cellId) {
            if (gameState !== 'playing' || clicksLeft === 0 || hasRedeemed) return;
            if (cells[cellId].isRevealed || clickedCells.includes(cellId)) return;

            // Add haptic feedback on supported devices
            if (navigator.vibrate) {
                navigator.vibrate(50);
            }

            const clickIndex = 5 - clicksLeft;
            const isFourthClick = clickIndex === 3;
            const shouldExplode = isFourthClick && Math.random() < 0.3;

            if (shouldExplode) {
                // Explode on 4th click but still win 57%
                cells[cellId].isRevealed = true;
                cells[cellId].isMine = true;
                cells[cellId].discount = 0;
                clickedCells.push(cellId);
                totalDiscount = 57;
                clicksLeft = 0;
                
                // Stronger vibration for explosion
                if (navigator.vibrate) {
                    navigator.vibrate([100, 50, 100]);
                }
                
                setTimeout(() => {
                    gameState = 'won';
                    showWinMessage();
                    renderGame();
                }, 1500);
            } else {
                // Normal diamond click
                const discountValue = clickIndex < 4 ? clickValues[clickIndex] : 0;
                cells[cellId].isRevealed = true;
                cells[cellId].discount = discountValue;
                clickedCells.push(cellId);
                totalDiscount += discountValue;
                clicksLeft--;

                if (clicksLeft === 0) {
                    setTimeout(() => {
                        gameState = 'won';
                        showWinMessage();
                        renderGame();
                    }, 1000);
                }
            }

            renderGame();
        }

        function showWinMessage() {
            document.getElementById('whatsappButton').classList.remove('hidden');
            document.getElementById('winMessage').classList.remove('hidden');
            document.getElementById('winPercent').textContent = totalDiscount;
            document.getElementById('winPlayerId').textContent = `🆔 Seu ID: ${playerId}`;
            
            // Scroll to WhatsApp button on mobile
            if (window.innerWidth < 768) {
                setTimeout(() => {
                    document.getElementById('whatsappButton').scrollIntoView({ behavior: 'smooth', block: 'center' });
                }, 500);
            }
        }

        function openWhatsapp() {
            const discountText = "57";
            const productText = "Hacker Da Blaze";
            const currentDate = new Date();
            const dateStr = currentDate.toLocaleDateString("pt-BR");
            const timeStr = currentDate.toLocaleTimeString("pt-BR", { hour: "2-digit", minute: "2-digit" });

            const message = `🎮 *RESGATE DE PROMOÇÃO - MINES*

👤 *ID do Jogador:* ${playerId}
💎 *Desconto Conquistado:* ${discountText}%
📱 *Produto:* ${productText}
📅 *Data/Hora:* ${dateStr} às ${timeStr}

✅ Quero resgatar minha promoção agora!

_Este é um código único e intransferível._`;

            const encodedMessage = encodeURIComponent(message);
            const whatsappUrl = `https://wa.me/5542984822255?text=${encodedMessage}`;

            window.open(whatsappUrl, "_blank", "noopener,noreferrer");

            // Mark as redeemed
            hasRedeemed = true;
            gameState = 'finished';
            
            document.getElementById('whatsappButton').classList.add('hidden');
            document.getElementById('winMessage').classList.add('hidden');
            document.getElementById('redeemedMessage').classList.remove('hidden');
            document.getElementById('redeemedId').textContent = `ID: ${playerId}`;
            document.getElementById('alreadyPlayedWarning').classList.remove('hidden');

            renderGame();
        }

        // Initialize when page loads
        window.onload = init;

        // Prevent zoom on double tap (iOS)
        let lastTouchEnd = 0;
        document.addEventListener('touchend', function (event) {
            const now = (new Date()).getTime();
            if (now - lastTouchEnd <= 300) {
                event.preventDefault();
            }
            lastTouchEnd = now;
        }, false);

        // Handle orientation change
        window.addEventListener('orientationchange', function() {
            setTimeout(() => {
                renderGame();
            }, 500);
        });
    </script>
</body>
</html>
