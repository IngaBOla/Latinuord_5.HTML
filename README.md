<!DOCTYPE html>
<html lang="is">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Latneskorð úr kafla 5</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
            background: linear-gradient(135deg, #0f766e 0%, #0e7490 100%);
            min-height: 100vh;
            padding: 2rem;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        .header {
            text-align: center;
            color: white;
            margin-bottom: 3rem;
        }

        .header h1 {
            font-size: 2.5rem;
            margin-bottom: 0.5rem;
        }

        .header p {
            font-size: 1.1rem;
            opacity: 0.9;
        }

        .menu-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            max-width: 1000px;
            margin: 0 auto;
        }

        .card {
            background: white;
            border-radius: 12px;
            padding: 2rem;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        .card:hover {
            transform: translateY(-4px);
            box-shadow: 0 12px 24px rgba(0,0,0,0.2);
        }

        .card h2 {
            color: #0f766e;
            font-size: 1.8rem;
            margin-bottom: 0.75rem;
        }

        .card p {
            color: #4b5563;
            line-height: 1.6;
            margin-bottom: 0.5rem;
        }

        .card .word-count {
            color: #0f766e;
            font-weight: 600;
            font-size: 0.9rem;
        }

        .hidden {
            display: none;
        }

        .nav-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
            color: white;
            flex-wrap: wrap;
            gap: 1rem;
        }

        .btn {
            background: white;
            color: #0f766e;
            border: none;
            padding: 0.75rem 1.5rem;
            border-radius: 8px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s;
        }

        .btn:hover {
            background: #f3f4f6;
        }

        .btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        /* Flashcard styles */
        .flashcard-container {
            max-width: 700px;
            margin: 0 auto;
        }

        .flashcard {
            height: 400px;
            perspective: 1000px;
            cursor: pointer;
            margin-bottom: 2rem;
        }

        .flashcard-inner {
            position: relative;
            width: 100%;
            height: 100%;
            transition: transform 0.6s;
            transform-style: preserve-3d;
        }

        .flashcard.flipped .flashcard-inner {
            transform: rotateY(180deg);
        }

        .flashcard-front, .flashcard-back {
            position: absolute;
            width: 100%;
            height: 100%;
            backface-visibility: hidden;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            border-radius: 12px;
            box-shadow: 0 12px 24px rgba(0,0,0,0.2);
            padding: 2rem;
        }

        .flashcard-front {
            background: white;
        }

        .flashcard-back {
            background: #0d9488;
            transform: rotateY(180deg);
            color: white;
        }

        .flashcard-label {
            font-size: 0.9rem;
            opacity: 0.6;
            margin-bottom: 1rem;
        }

        .flashcard-term {
            font-size: 3.5rem;
            font-weight: bold;
        }

        .flashcard-hint {
            margin-top: 2rem;
            font-size: 0.9rem;
            opacity: 0.6;
        }

        .flashcard-controls {
            display: flex;
            justify-content: space-between;
            gap: 1rem;
        }

        /* Game styles */
        .game-container {
            max-width: 900px;
            margin: 0 auto;
        }

        .game-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 1rem;
            margin-bottom: 2rem;
        }

        .game-card {
            aspect-ratio: 1;
            background: white;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 1rem;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            font-size: 1rem;
            font-weight: 600;
        }

        .game-card:hover {
            transform: scale(1.05);
        }

        .game-card.flipped {
            background: #14b8a6;
            color: white;
        }

        .game-card.matched {
            background: #10b981;
            color: white;
            cursor: default;
            opacity: 0.6;
        }

        .game-card.wrong {
            background: #ef4444;
            color: white;
            animation: shake 0.4s;
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-10px); }
            75% { transform: translateX(10px); }
        }

        .score-panel {
            background: white;
            padding: 1.5rem;
            border-radius: 12px;
            text-align: center;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        .score-panel h3 {
            color: #0f766e;
            font-size: 1.5rem;
            margin-bottom: 1rem;
        }

        .stats {
            display: flex;
            justify-content: space-around;
            gap: 2rem;
        }

        .stat {
            text-align: center;
        }

        .stat-value {
            font-size: 2rem;
            font-weight: bold;
            color: #0f766e;
        }

        .stat-label {
            color: #6b7280;
            font-size: 0.9rem;
        }

        .complete-card {
            background: white;
            padding: 3rem;
            border-radius: 12px;
            text-align: center;
            box-shadow: 0 12px 24px rgba(0,0,0,0.2);
        }

        .complete-card h2 {
            color: #0f766e;
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }

        .complete-card p {
            font-size: 1.2rem;
            margin-bottom: 0.5rem;
            color: #374151;
        }

        .complete-card .btn {
            margin-top: 2rem;
            background: #0f766e;
            color: white;
            padding: 1rem 2rem;
            font-size: 1.1rem;
        }

        .complete-card .btn:hover {
            background: #115e59;
        }

        @media (max-width: 768px) {
            body {
                padding: 1rem;
            }

            .header h1 {
                font-size: 1.8rem;
            }

            .flashcard {
                height: 300px;
            }

            .flashcard-term {
                font-size: 2.5rem;
            }

            .game-grid {
                grid-template-columns: repeat(3, 1fr);
                gap: 0.75rem;
            }

            .game-card {
                font-size: 0.85rem;
                padding: 0.5rem;
            }

            .stats {
                flex-direction: column;
                gap: 1rem;
            }
        }

        @media (max-width: 480px) {
            .game-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Menu View -->
        <div id="menuView">
            <div class="header">
                <h1>Latneskorð úr kafla 5</h1>
                <p>Veldu æfingu til að byrja að læra</p>
            </div>
            <div class="menu-grid">
                <div class="card" onclick="startFlashcards()">
                    <h2>📇 Fléttispjöld</h2>
                    <p>Fara í gegnum öll orðin eitt í einu. Smelltu á kortið til að sjá þýðinguna.</p>
                    <p class="word-count">20 orð</p>
                </div>
                <div class="card" onclick="startGame(1)">
                    <h2>🎮 Pörun 1</h2>
                    <p>Finndu parið fyrir hvert latneskt orð.</p>
                    <p class="word-count">10 orð</p>
                </div>
                <div class="card" onclick="startGame(2)">
                    <h2>🎯 Pörun 2</h2>
                    <p>Haltu áfram að æfa með fleiri orðum!</p>
                    <p class="word-count">10 orð</p>
                </div>
            </div>
        </div>

        <!-- Flashcard View -->
        <div id="flashcardView" class="hidden">
            <div class="flashcard-container">
                <div class="nav-bar">
                    <button class="btn" onclick="showMenu()">← Til baka</button>
                    <span id="flashcardProgress" class="score"></span>
                    <button class="btn" onclick="shuffleFlashcards()">🔀 Stokka</button>
                </div>

                <div class="flashcard" id="flashcard" onclick="flipCard()">
                    <div class="flashcard-inner">
                        <div class="flashcard-front">
                            <div class="flashcard-label">LATNESKA</div>
                            <div class="flashcard-term" id="latinTerm"></div>
                            <div class="flashcard-hint">Smelltu til að snúa</div>
                        </div>
                        <div class="flashcard-back">
                            <div class="flashcard-label">ÍSLENSKA</div>
                            <div class="flashcard-term" id="icelandicTerm"></div>
                            <div class="flashcard-hint">Smelltu til að snúa</div>
                        </div>
                    </div>
                </div>

                <div class="flashcard-controls">
                    <button class="btn" id="prevBtn" onclick="prevCard()">← Fyrra</button>
                    <button class="btn" id="nextBtn" onclick="nextCard()">Næsta →</button>
                </div>
            </div>
        </div>

        <!-- Game View -->
        <div id="gameView" class="hidden">
            <div class="game-container">
                <div class="nav-bar">
                    <button class="btn" onclick="showMenu()">← Til baka</button>
                    <h2 id="gameTitle" style="color: white; font-size: 1.5rem;"></h2>
                    <button class="btn" onclick="resetGame()">🔄 Byrja aftur</button>
                </div>

                <div id="gameGrid" class="game-grid"></div>

                <div class="score-panel">
                    <h3>Frammistaða</h3>
                    <div class="stats">
                        <div class="stat">
                            <div class="stat-value" id="movesCount">0</div>
                            <div class="stat-label">Tilraunir</div>
                        </div>
                        <div class="stat">
                            <div class="stat-value" id="matchesCount">0</div>
                            <div class="stat-label">Pör fundin</div>
                        </div>
                        <div class="stat">
                            <div class="stat-value" id="timeCount">00:00</div>
                            <div class="stat-label">Tími</div>
                        </div>
                    </div>
                </div>

                <div id="completeScreen" class="hidden"></div>
            </div>
        </div>
    </div>

    <script>
        const allTerms = [
            { latin: "Cutis", icelandic: "húð" },
            { latin: "Rubor", icelandic: "húðroði" },
            { latin: "Calor", icelandic: "hiti" },
            { latin: "Dolor", icelandic: "verkur" },
            { latin: "Tumor", icelandic: "fyrirferð / æxli" },
            { latin: "Inflammatio", icelandic: "bólga" },
            { latin: "Pallor", icelandic: "húðfölvi" },
            { latin: "Icterus", icelandic: "gulur litarháttur" },
            { latin: "Cyanosis", icelandic: "húðblámi" },
            { latin: "Abscessus", icelandic: "grafarkýli" },
            { latin: "Cellulitis", icelandic: "netjubólga" },
            { latin: "Impetigo", icelandic: "kossageit" },
            { latin: "Decubitus", icelandic: "þrýstingssár" },
            { latin: "Dermatitis", icelandic: "bólga í húð" },
            { latin: "Erysipelas", icelandic: "heimakoma" },
            { latin: "Herpes simplex", icelandic: "áblástur" },
            { latin: "Keloid", icelandic: "ofholdgun" },
            { latin: "Pruritus", icelandic: "kláði í húð" },
            { latin: "Psoriasis", icelandic: "húðhreistur" },
            { latin: "Verruca", icelandic: "smitvarta" }
        ];

        const game1Terms = allTerms.slice(0, 10);
        const game2Terms = allTerms.slice(10, 20);

        // Flashcard variables
        let currentCard = 0;
        let shuffledTerms = [...allTerms];

        // Game variables
        let currentGame = 1;
        let gameCards = [];
        let flippedCards = [];
        let matchedPairs = 0;
        let moves = 0;
        let startTime;
        let timerInterval;

        function shuffleArray(array) {
            const arr = [...array];
            for (let i = arr.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [arr[i], arr[j]] = [arr[j], arr[i]];
            }
            return arr;
        }

        function showMenu() {
            document.getElementById('menuView').classList.remove('hidden');
            document.getElementById('flashcardView').classList.add('hidden');
            document.getElementById('gameView').classList.add('hidden');
            clearInterval(timerInterval);
        }

        // ========== FLASHCARD FUNCTIONS ==========
        function startFlashcards() {
            document.getElementById('menuView').classList.add('hidden');
            document.getElementById('flashcardView').classList.remove('hidden');
            document.getElementById('gameView').classList.add('hidden');
            shuffleFlashcards();
        }

        function shuffleFlashcards() {
            shuffledTerms = shuffleArray(allTerms);
            currentCard = 0;
            updateFlashcard();
        }

        function updateFlashcard() {
            const term = shuffledTerms[currentCard];
            document.getElementById('latinTerm').textContent = term.latin;
            document.getElementById('icelandicTerm').textContent = term.icelandic;
            document.getElementById('flashcardProgress').textContent = `${currentCard + 1} / ${shuffledTerms.length}`;
            document.getElementById('flashcard').classList.remove('flipped');
            
            document.getElementById('prevBtn').disabled = currentCard === 0;
            document.getElementById('nextBtn').disabled = currentCard === shuffledTerms.length - 1;
        }

        function flipCard() {
            document.getElementById('flashcard').classList.toggle('flipped');
        }

        function nextCard() {
            if (currentCard < shuffledTerms.length - 1) {
                currentCard++;
                updateFlashcard();
            }
        }

        function prevCard() {
            if (currentCard > 0) {
                currentCard--;
                updateFlashcard();
            }
        }

        // ========== GAME FUNCTIONS ==========
        function startGame(gameNumber) {
            currentGame = gameNumber;
            
            document.getElementById('menuView').classList.add('hidden');
            document.getElementById('flashcardView').classList.add('hidden');
            document.getElementById('gameView').classList.remove('hidden');
            document.getElementById('gameTitle').textContent = `Pörun ${gameNumber}`;
            document.getElementById('completeScreen').classList.add('hidden');
            
            resetGame();
        }

        function resetGame() {
            const terms = currentGame === 1 ? game1Terms : game2Terms;
            
            // Create card pairs
            gameCards = [];
            terms.forEach((term, index) => {
                gameCards.push({ id: index, text: term.latin, type: 'latin', pairId: index });
                gameCards.push({ id: index + 100, text: term.icelandic, type: 'icelandic', pairId: index });
            });
            
            gameCards = shuffleArray(gameCards);
            flippedCards = [];
            matchedPairs = 0;
            moves = 0;
            
            updateStats();
            renderGame();
            startTimer();
        }

        function renderGame() {
            const grid = document.getElementById('gameGrid');
            grid.innerHTML = '';
            
            // Separate and shuffle latin and icelandic cards
            const latinCards = shuffleArray(gameCards.filter(c => c.type === 'latin'));
            const icelandicCards = shuffleArray(gameCards.filter(c => c.type === 'icelandic'));
            
            // Alternate between latin (left) and icelandic (right) cards
            const orderedCards = [];
            for (let i = 0; i < Math.max(latinCards.length, icelandicCards.length); i++) {
                if (latinCards[i]) orderedCards.push(latinCards[i]);
                if (icelandicCards[i]) orderedCards.push(icelandicCards[i]);
            }
            
            orderedCards.forEach(card => {
                const cardEl = document.createElement('div');
                cardEl.className = 'game-card';
                cardEl.textContent = card.text;
                cardEl.dataset.id = card.id;
                cardEl.dataset.pairId = card.pairId;
                cardEl.onclick = () => flipGameCard(card, cardEl);
                grid.appendChild(cardEl);
            });
        }

        function flipGameCard(card, cardEl) {
            if (flippedCards.length >= 2 || cardEl.classList.contains('matched') || cardEl.classList.contains('flipped')) {
                return;
            }
            
            cardEl.classList.add('flipped');
            flippedCards.push({ card, element: cardEl });
            
            if (flippedCards.length === 2) {
                moves++;
                updateStats();
                checkMatch();
            }
        }

        function checkMatch() {
            const [first, second] = flippedCards;
            
            if (first.card.pairId === second.card.pairId) {
                // Match found
                setTimeout(() => {
                    first.element.classList.remove('flipped');
                    second.element.classList.remove('flipped');
                    first.element.classList.add('matched');
                    second.element.classList.add('matched');
                    matchedPairs++;
                    updateStats();
                    flippedCards = [];
                    
                    if (matchedPairs === (currentGame === 1 ? game1Terms.length : game2Terms.length)) {
                        showComplete();
                    }
                }, 500);
            } else {
                // No match
                setTimeout(() => {
                    first.element.classList.add('wrong');
                    second.element.classList.add('wrong');
                    
                    setTimeout(() => {
                        first.element.classList.remove('flipped', 'wrong');
                        second.element.classList.remove('flipped', 'wrong');
                        flippedCards = [];
                    }, 600);
                }, 500);
            }
        }

        function updateStats() {
            document.getElementById('movesCount').textContent = moves;
            document.getElementById('matchesCount').textContent = matchedPairs;
        }

        function startTimer() {
            clearInterval(timerInterval);
            startTime = Date.now();
            
            timerInterval = setInterval(() => {
                const elapsed = Math.floor((Date.now() - startTime) / 1000);
                const minutes = Math.floor(elapsed / 60);
                const seconds = elapsed % 60;
                document.getElementById('timeCount').textContent = 
                    `${String(minutes).padStart(2, '0')}:${String(seconds).padStart(2, '0')}`;
            }, 1000);
        }

        function showComplete() {
            clearInterval(timerInterval);
            const elapsed = Math.floor((Date.now() - startTime) / 1000);
            const minutes = Math.floor(elapsed / 60);
            const seconds = elapsed % 60;
            const timeStr = `${minutes}:${String(seconds).padStart(2, '0')}`;
            
            setTimeout(() => {
                document.getElementById('completeScreen').innerHTML = `
                    <div class="complete-card">
                        <h2>Til hamingju! 🎉</h2>
                        <p>Þú kláraðir Pörun ${currentGame}!</p>
                        <p style="color: #6b7280; margin-top: 1rem;">
                            Tilraunir: ${moves}<br>
                            Tími: ${timeStr}
                        </p>
                        <button class="btn" onclick="resetGame()">Spila aftur</button>
                        <button class="btn" onclick="showMenu()" style="margin-left: 1rem;">Til baka</button>
                    </div>
                `;
                document.getElementById('completeScreen').classList.remove('hidden');
            }, 1000);
        }

        // Initialize
        shuffleFlashcards();
    </script>
</body>
</html>
