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
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: linear-gradient(135deg, #0f766e 0%, #0e7490 100%);
            min-height: 100vh;
            padding: 2rem;
        }

        .container {
            max-width: 1000px;
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

        .menu-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
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
        }

        .btn:hover {
            background: #f3f4f6;
        }

        /* Flashcards */
        .flashcard {
            height: 400px;
            perspective: 1000px;
            cursor: pointer;
            margin-bottom: 2rem;
            max-width: 700px;
            margin-left: auto;
            margin-right: auto;
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

        .flashcard-term {
            font-size: 3rem;
            font-weight: bold;
        }

        .flashcard-label {
            font-size: 0.9rem;
            opacity: 0.6;
            margin-bottom: 1rem;
        }

        .flashcard-controls {
            display: flex;
            justify-content: space-between;
            gap: 1rem;
            max-width: 700px;
            margin: 0 auto;
        }

        /* Matching Game */
        .matching-wrapper {
            display: flex;
            justify-content: center;
            margin-bottom: 2rem;
        }

        .matching-columns {
            display: flex;
            gap: 2rem;
        }

        .match-column {
            width: 220px;
        }

        .match-column h3 {
            color: white;
            font-size: 1.3rem;
            margin-bottom: 1rem;
            text-align: center;
        }

        .match-options {
            display: flex;
            flex-direction: column;
            gap: 0.75rem;
        }

        .match-btn {
            background: white;
            border: none;
            padding: 0.75rem;
            border-radius: 8px;
            font-size: 0.95rem;
            cursor: pointer;
            font-weight: 600;
            text-align: left;
            transition: all 0.2s;
        }

        .match-btn:hover {
            background: #f3f4f6;
        }

        .match-btn.selected {
            background: #14b8a6;
            color: white;
        }

        .match-btn.wrong {
            background: #ef4444;
            color: white;
            animation: shake 0.4s;
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-8px); }
            75% { transform: translateX(8px); }
        }

        .stats {
            background: white;
            padding: 1.5rem;
            border-radius: 12px;
            text-align: center;
            max-width: 500px;
            margin: 0 auto;
        }

        .stats h3 {
            color: #0f766e;
            margin-bottom: 1rem;
        }

        .stat-row {
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

        .complete {
            background: white;
            padding: 3rem;
            border-radius: 12px;
            text-align: center;
            max-width: 500px;
            margin: 2rem auto;
        }

        .complete h2 {
            color: #0f766e;
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }

        .complete .btn {
            margin-top: 2rem;
            background: #0f766e;
            color: white;
            padding: 1rem 2rem;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Menu -->
        <div id="menu">
            <div class="header">
                <h1>Latneskorð úr kafla 5</h1>
                <p>Veldu æfingu til að byrja</p>
            </div>
            <div class="menu-grid">
                <div class="card" onclick="showFlashcards()">
                    <h2>📇 Fléttispjöld</h2>
                    <p>Fara í gegnum öll orðin. Smelltu til að snúa.</p>
                </div>
                <div class="card" onclick="showMatching(1)">
                    <h2>🎮 Pörun 1</h2>
                    <p>Tengdu saman fyrstu 10 orðin.</p>
                </div>
                <div class="card" onclick="showMatching(2)">
                    <h2>🎯 Pörun 2</h2>
                    <p>Tengdu saman næstu 10 orðin.</p>
                </div>
            </div>
        </div>

        <!-- Flashcards -->
        <div id="flashcards" class="hidden">
            <div class="nav-bar">
                <button class="btn" onclick="showMenu()">← Til baka</button>
                <span id="fcProgress" style="color: white; font-weight: bold;"></span>
                <button class="btn" onclick="shuffle()">🔀 Stokka</button>
            </div>
            <div class="flashcard" id="card" onclick="flip()">
                <div class="flashcard-inner">
                    <div class="flashcard-front">
                        <div class="flashcard-label">LATNESKA</div>
                        <div class="flashcard-term" id="latin"></div>
                    </div>
                    <div class="flashcard-back">
                        <div class="flashcard-label">ÍSLENSKA</div>
                        <div class="flashcard-term" id="icelandic"></div>
                    </div>
                </div>
            </div>
            <div class="flashcard-controls">
                <button class="btn" id="prev" onclick="prev()">← Fyrra</button>
                <button class="btn" id="next" onclick="next()">Næsta →</button>
            </div>
        </div>

        <!-- Matching -->
        <div id="matching" class="hidden">
            <div class="nav-bar">
                <button class="btn" onclick="showMenu()">← Til baka</button>
                <h2 id="matchTitle" style="color: white;"></h2>
                <button class="btn" onclick="resetMatch()">🔄 Byrja aftur</button>
            </div>

            <div class="matching-wrapper">
                <div class="matching-columns">
                    <div class="match-column">
                        <h3>Latneska</h3>
                        <div class="match-options" id="latinCol"></div>
                    </div>
                    <div class="match-column">
                        <h3>Íslenska</h3>
                        <div class="match-options" id="icelandicCol"></div>
                    </div>
                </div>
            </div>

            <div class="stats">
                <h3>Frammistaða</h3>
                <div class="stat-row">
                    <div class="stat">
                        <div class="stat-value" id="moves">0</div>
                        <div class="stat-label">Tilraunir</div>
                    </div>
                    <div class="stat">
                        <div class="stat-value" id="matched">0</div>
                        <div class="stat-label">Pör</div>
                    </div>
                    <div class="stat">
                        <div class="stat-value" id="timer">00:00</div>
                        <div class="stat-label">Tími</div>
                    </div>
                </div>
            </div>

            <div id="completeMsg"></div>
        </div>
    </div>

    <script>
        const terms = [
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

        let fcIndex = 0;
        let fcTerms = [...terms];
        let currentGame = 1;
        let selectedLatin = null;
        let matchedTerms = [];
        let moveCount = 0;
        let matchCount = 0;
        let startTime;
        let timerInterval;

        function shuffleArr(arr) {
            const a = [...arr];
            for (let i = a.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [a[i], a[j]] = [a[j], a[i]];
            }
            return a;
        }

        function showMenu() {
            document.getElementById('menu').classList.remove('hidden');
            document.getElementById('flashcards').classList.add('hidden');
            document.getElementById('matching').classList.add('hidden');
            clearInterval(timerInterval);
        }

        // Flashcards
        function showFlashcards() {
            document.getElementById('menu').classList.add('hidden');
            document.getElementById('flashcards').classList.remove('hidden');
            shuffle();
        }

        function shuffle() {
            fcTerms = shuffleArr(terms);
            fcIndex = 0;
            updateCard();
        }

        function updateCard() {
            const t = fcTerms[fcIndex];
            document.getElementById('latin').textContent = t.latin;
            document.getElementById('icelandic').textContent = t.icelandic;
            document.getElementById('fcProgress').textContent = `${fcIndex + 1} / ${fcTerms.length}`;
            document.getElementById('card').classList.remove('flipped');
            document.getElementById('prev').disabled = fcIndex === 0;
            document.getElementById('next').disabled = fcIndex === fcTerms.length - 1;
        }

        function flip() {
            document.getElementById('card').classList.toggle('flipped');
        }

        function prev() {
            if (fcIndex > 0) {
                fcIndex--;
                updateCard();
            }
        }

        function next() {
            if (fcIndex < fcTerms.length - 1) {
                fcIndex++;
                updateCard();
            }
        }

        // Matching
        function showMatching(game) {
            currentGame = game;
            document.getElementById('menu').classList.add('hidden');
            document.getElementById('matching').classList.remove('hidden');
            document.getElementById('matchTitle').textContent = `Pörun ${game}`;
            resetMatch();
        }

        function resetMatch() {
            selectedLatin = null;
            matchedTerms = [];
            moveCount = 0;
            matchCount = 0;
            document.getElementById('moves').textContent = '0';
            document.getElementById('matched').textContent = '0';
            document.getElementById('completeMsg').innerHTML = '';
            renderMatch();
            startTimer();
        }

        function renderMatch() {
            const gameTerms = currentGame === 1 ? terms.slice(0, 10) : terms.slice(10, 20);
            const unmatched = gameTerms.filter(t => !matchedTerms.includes(t.latin));
            const latinShuffled = shuffleArr(unmatched);
            const icelandicShuffled = shuffleArr(unmatched);

            const latinCol = document.getElementById('latinCol');
            const icelandicCol = document.getElementById('icelandicCol');
            latinCol.innerHTML = '';
            icelandicCol.innerHTML = '';

            latinShuffled.forEach(t => {
                const btn = document.createElement('button');
                btn.className = 'match-btn';
                btn.textContent = t.latin;
                btn.onclick = () => selectLatin(t);
                latinCol.appendChild(btn);
            });

            icelandicShuffled.forEach(t => {
                const btn = document.createElement('button');
                btn.className = 'match-btn';
                btn.textContent = t.icelandic;
                btn.onclick = () => selectIcelandic(t);
                icelandicCol.appendChild(btn);
            });
        }

        function selectLatin(term) {
            selectedLatin = term;
            document.querySelectorAll('#latinCol .match-btn').forEach(b => {
                b.classList.remove('selected');
                if (b.textContent === term.latin) b.classList.add('selected');
            });
        }

        function selectIcelandic(term) {
            if (!selectedLatin) return;

            moveCount++;
            document.getElementById('moves').textContent = moveCount;

            if (selectedLatin.icelandic === term.icelandic) {
                matchedTerms.push(selectedLatin.latin);
                matchCount++;
                document.getElementById('matched').textContent = matchCount;
                selectedLatin = null;

                if (matchCount === 10) {
                    showComplete();
                } else {
                    setTimeout(renderMatch, 300);
                }
            } else {
                const latinBtn = Array.from(document.querySelectorAll('#latinCol .match-btn')).find(b => b.textContent === selectedLatin.latin);
                const iceBtn = Array.from(document.querySelectorAll('#icelandicCol .match-btn')).find(b => b.textContent === term.icelandic);
                
                if (latinBtn) latinBtn.classList.add('wrong');
                if (iceBtn) iceBtn.classList.add('wrong');
                
                setTimeout(() => {
                    if (latinBtn) latinBtn.classList.remove('wrong', 'selected');
                    if (iceBtn) iceBtn.classList.remove('wrong');
                }, 600);
            }
        }

        function startTimer() {
            clearInterval(timerInterval);
            startTime = Date.now();
            timerInterval = setInterval(() => {
                const elapsed = Math.floor((Date.now() - startTime) / 1000);
                const m = Math.floor(elapsed / 60);
                const s = elapsed % 60;
                document.getElementById('timer').textContent = `${String(m).padStart(2, '0')}:${String(s).padStart(2, '0')}`;
            }, 1000);
        }

        function showComplete() {
            clearInterval(timerInterval);
            const elapsed = Math.floor((Date.now() - startTime) / 1000);
            const m = Math.floor(elapsed / 60);
            const s = elapsed % 60;
            document.getElementById('completeMsg').innerHTML = `
                <div class="complete">
                    <h2>Til hamingju! 🎉</h2>
                    <p>Þú kláraðir Pörun ${currentGame}!</p>
                    <p style="color: #6b7280; margin-top: 1rem;">
                        Tilraunir: ${moveCount}<br>
                        Tími: ${m}:${String(s).padStart(2, '0')}
                    </p>
                    <button class="btn" onclick="resetMatch()">Spila aftur</button>
                    <button class="btn" onclick="showMenu()">Til baka</button>
                </div>
            `;
        }
    </script>
</body>
</html>
