<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MINES - Hacker Da Blaze</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #4c1d95, #1e3a8a, #312e81);
            min-height: 100vh;
            color: white;
            padding: 1rem;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        .card {
            background: rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(147, 51, 234, 0.3);
            border-radius: 12px;
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            backdrop-filter: blur(10px);
        }

        .header {
            text-align: center;
            background: rgba(0, 0, 0, 0.2);
            border: 1px solid rgba(147, 51, 234, 0.3);
        }

        .title {
            font-size: 2rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
        }

        .subtitle {
            color: #c4b5fd;
            margin-bottom: 0.5rem;
        }

        .highlight {
            color: #fde047;
            font-weight: bold;
        }

        .player-id {
            color: #86efac;
            font-size: 0.875rem;
            margin-top: 0.5rem;
        }

        .notification {
            position: fixed;
            top: 1rem;
            right: 1rem;
            background: #16a34a;
            color: white;
            padding: 1rem;
            border-radius: 8px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
            border: 1px solid #22c55e;
            z-index: 1000;
            animation: slideIn 0.5s ease-out;
            display: none;
        }

        @keyframes slideIn {
            from { transform: translateX(100%); }
            to { transform: translateX(0); }
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
            width: 4rem;
            height: 4rem;
            background: #dc2626;
            border: none;
            border-radius: 50%;
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
            transition: all 0.3s;
        }

        .play-button:hover {
            background: #b91c1c;
            transform: scale(1.1);
        }

        .button {
            padding: 0.75rem 1.5rem;
            border: none;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            margin: 0.25rem;
        }

        .button-primary {
            background: linear-gradient(135deg, #7c3aed, #2563eb);
            color: white;
        }

        .button-primary:hover {
            background: linear-gradient(135deg, #6d28d9, #1d4ed8);
        }

        .button-secondary {
            background: linear-gradient(135deg, #eab308, #ea580c);
            color: white;
        }

        .button-whatsapp {
            background: linear-gradient(135deg, #16a34a, #059669);
            color: white;
            width: 100%;
        }

        .button:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .game-layout {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 1.5rem;
        }

        @media (max-width: 768px) {
            .game-layout {
                grid-template-columns: 1fr;
            }
        }

        .status-panel {
            background: rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(147, 51, 234, 0.3);
        }

        .badge {
            background: rgba(107, 114, 128, 0.8);
            color: white;
            padding: 0.5rem 1rem;
            border-radius: 6px;
            font-size: 1.125rem;
            display: inline-block;
        }

        .discount-display {
            font-size: 3rem;
            font-weight: bold;
            color: #4ade80;
            text-align: center;
        }

        .price-info {
            border-top: 1px solid rgba(147, 51, 234, 0.3);
            padding-top: 1rem;
            margin-top: 1rem;
        }

        .original-price {
            text-decoration: line-through;
            color: #9ca3af;
        }

        .final-price {
            font-size: 2rem;
            font-weight: bold;
            color: #4ade80;
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
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 0.5rem;
            max-width: 400px;
            margin: 0 auto;
        }

        .cell {
            aspect-ratio: 1;
            height: 4rem;
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
        }

        .cell:hover:not(:disabled) {
            background: #4b5563;
            border-color: rgba(147, 51, 234, 0.8);
        }

        .cell:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .cell.revealed {
            background: #16a34a;
        }

        .cell.bomb {
            background: #dc2626;
        }

        .instructions {
            background: rgba(0, 0, 0, 0.2);
            border: 1px solid rgba(147, 51, 234, 0.3);
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
    </style>
</head>
<body>
    <div class="container">
        <!-- Header -->
        <div class="card header">
            <h1 class="title">
                💣 MINES - Hacker Da Blaze 💎
            </h1>
            <p class="subtitle">Encontre os diamantes e ganhe descontos incríveis!</p>
            <p class="highlight">🎁 ALGUNS JOGADORES ESTÃO GANHANDO O PRODUTO DE GRAÇA! 🎁</p>
            <p class="player-id" id="playerId">🆔 Seu ID: Carregando...</p>
        </div>

        <!-- Notification -->
        <div class="notification" id="notification">
            <div class="flex" style="align-items: center; justify-content: space-between;">
                <div style="display: flex; align-items: center; gap: 0.5rem;">
                    <span>🔔</span>
                    <div>
                        <p style="font-weight: bold; font-size: 0.875rem;" id="notifName"></p>
                        <p style="font-size: 0.75rem;" id="notifDiscount"></p>
                        <p style="font-size: 0.75rem; opacity: 0.75;" id="notifTime"></p>
                    </div>
                </div>
                <button onclick="hideNotification()" style="background: none; border: none; color: white; cursor: pointer;">✕</button>
            </div>
        </div>

        <!-- Warning if already played -->
        <div class="card warning-message hidden" id="alreadyPlayedWarning">
            <div style="display: flex; align-items: center; justify-content: center; gap: 0.5rem;">
                <span>🔒</span>
                <p style="font-weight: bold;">Você já utilizou sua chance única! Não é possível jogar novamente.</p>
            </div>
        </div>

        <!-- Video Section -->
        <div class="card video-section" id="videoSection">
            <h2 style="color: white; margin-bottom: 1rem; display: flex; align-items: center; gap: 0.5rem;">
                <span style="color: #eab308;">📹</span>
                Veja como funciona o sistema
            </h2>
            <div class="video-container">
                <div class="video-placeholder">
                    <button class="play-button" onclick="startVideo()">▶</button>
                </div>
            </div>
            <div class="text-center">
                <button class="button button-primary" onclick="startVideo()">▶ Assistir Vídeo</button>
                <button class="button button-secondary" onclick="skipVideo()">Pular Vídeo</button>
                <button class="button button-primary" onclick="initializeGame()">Jogar Agora</button>
            </div>
            <p style="color: #86efac; text-align: center; font-size: 0.875rem; font-weight: bold; margin-top: 1rem;">
                ⚡ Você pode jogar sem assistir o vídeo completo!
            </p>
        </div>

        <!-- Game Layout -->
        <div class="game-layout hidden" id="gameLayout">
            <!-- Status Panel -->
            <div class="card status-panel">
                <h2 style="color: white; margin-bottom: 1rem; display: flex; align-items: center; gap: 0.5rem;">
                    <span style="color: #eab308;">🎁</span>
                    Status do Jogo
                </h2>
                <div class="space-y-4">
                    <div class="text-center">
                        <span class="badge" id="clicksLeft">Cliques Restantes: 5</span>
                    </div>
                    <div class="text-center">
                        <p style="color: #c4b5fd; margin-bottom: 0.5rem;">Desconto Acumulado:</p>
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
                    <button class="button button-whatsapp hidden" id="whatsappButton" onclick="openWhatsapp()">
                        📱 Resgatar no WhatsApp
                    </button>
                    <div class="success-message hidden" id="redeemedMessage">
                        <p style="color: #86efac; font-weight: bold; font-size: 0.875rem;">✅ Promoção Resgatada!</p>
                        <p style="color: #bbf7d0; font-size: 0.75rem;" id="redeemedId">ID: </p>
                        <p style="color: #bbf7d0; font-size: 0.75rem;">Aguarde o contato via WhatsApp</p>
                    </div>
                </div>
            </div>

            <!-- Game Board -->
            <div class="card game-board">
                <h2 class="text-center" style="color: white; margin-bottom: 1rem;" id="gameTitle">
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
        </div>

        <!-- Instructions -->
        <div class="card instructions">
            <h3 style="color: white; font-weight: bold; margin-bottom: 0.75rem;">Como Jogar:</h3>
            <ul style="color: #c4b5fd; list-style: none; padding: 0;">
                <li style="margin-bottom: 0.5rem;">• Você tem apenas 5 cliques para acumular desconto</li>
                <li style="margin-bottom: 0.5rem;">• Clique nas células para encontrar diamantes</li>
                <li style="margin-bottom: 0.5rem;">• Todos os cliques são diamantes - sem bombas!</li>
                <li style="margin-bottom: 0.5rem;">• Na 4ª jogada, você pode encontrar uma bomba, mas ainda ganha o desconto!</li>
                <li style="margin-bottom: 0.5rem;">• Mesmo explodindo, você garante seus 57% de desconto</li>
                <li style="margin-bottom: 0.5rem;">• Alguns jogadores estão ganhando o produto TOTALMENTE GRÁTIS!</li>
                <li style="margin-bottom: 0.5rem;">• Após os 5 cliques, resgate sua promoção pelo WhatsApp</li>
                <li style="margin-bottom: 0.5rem;">• Cada pessoa pode jogar apenas uma vez</li>
                <li style="margin-bottom: 0.5rem;">• Guarde seu ID para acompanhar o resgate</li>
            </ul>
        </div>
    </div>

    <script>
        // Game State
        let gameState = 'intro'; // intro, playing, won, finished
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
            document.getElementById('playerId').textContent = `🆔 Seu ID: ${playerId}`;
            
            // Start fake notifications
            setTimeout(generateNotification, 2000);
            setInterval(() => {
                generateNotification();
            }, Math.random() * 7000 + 8000);
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
            // Video functionality placeholder
            console.log('Video started');
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
                        cellElement.innerHTML = '💣<br><span style="font-size: 0.75rem;">BOOM!</span>';
                    } else {
                        cellElement.classList.add('revealed');
                        cellElement.innerHTML = `💎<br><span style="font-size: 0.75rem;">${cell.discount}%</span>`;
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
        }

        function handleCellClick(cellId) {
            if (gameState !== 'playing' || clicksLeft === 0 || hasRedeemed) return;
            if (cells[cellId].isRevealed || clickedCells.includes(cellId)) return;

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
            const whatsappUrl = `https://wa.me/554299094212?text=${encodedMessage}`;

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
    </script>
</body>
</html>
