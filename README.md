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
            gap: 2rem;
            max-width: 800px;
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

        .matching-container {
            max-width: 1200px;
            margin: 0 auto;
        }

        .matching-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
        }

        .matching-column h3 {
            color: white;
            font-size: 1.5rem;
            margin-bottom: 1rem;
        }

        .matching-options {
            display: flex;
            flex-direction: column;
            gap: 0.75rem;
        }

        .matching-btn {
            background: white;
            border: none;
            padding: 1.25rem;
            border-radius: 8px;
            font-size: 1.1rem;
            cursor: pointer;
            transition: all 0.2s;
            text-align: left;
        }

        .matching-btn:hover {
            background: #f3f4f6;
            transform: translateX(4px);
        }

        .matching-btn.selected {
            background: #14b8a6;
            color: white;
        }

        .score-display {
            text-align: center;
            color: white;
        }

        .score-display .score {
            font-size: 2rem;
            font-weight: bold;
        }

        .score-display .attempts {
            font-size: 0.9rem;
        }

        .feedback {
            padding: 1rem 1.5rem;
            border-radius: 8px;
            margin-bottom: 1.5rem;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .feedback.success {
            background: #d1fae5;
            color: #065f46;
        }

        .feedback.error {
            background: #fee2e2;
            color: #991b1b;
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

            .matching-grid {
                grid-template-columns: 1fr;
                gap: 2rem;
            }

            .flashcard {
                height: 300px;
            }

            .flashcard-term {
                font-size: 2.5rem;
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
                </div>
                <div class="card" onclick="startMatching()">
                    <h2>🎯 Tengispurningar</h2>
                    <p>Tengdu latnesku orðin við íslenska þýðingu þeirra.</p>
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

        <!-- Matching View -->
        <div id="matchingView" class="hidden">
            <div class="matching-container">
                <div class="nav-bar">
                    <button class="btn" onclick="showMenu()">← Til baka</button>
                    <div class="score-display">
                        <div class="score" id="matchScore">0 / 20</div>
                        <div class="attempts">Tilraunir: <span id="matchAttempts">0</span></div>
                    </div>
                    <button class="btn" onclick="resetMatching()">🔄 Byrja aftur</button>
                </div>

                <div id="feedbackDiv"></div>

                <div id="matchingGame">
                    <div class="matching-grid">
                        <div class="matching-column">
                            <h3>Latneska</h3>
                            <div class="matching-options" id="latinOptions"></div>
                        </div>
                        <div class="matching-column">
                            <h3>Íslenska</h3>
                            <div class="matching-options" id="icelandicOptions"></div>
                        </div>
                    </div>
                </div>

                <div id="completeScreen" class="hidden"></div>
            </div>
        </div>
    </div>

    <script>
        const medicalTerms = [
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
            { latin: "Herpex simplex", icelandic: "áblástur" },
            { latin: "Keloid", icelandic: "ofholdgun" },
            { latin: "Pruritus", icelandic: "kláði í húð" },
            { latin: "Psoriasis", icelandic: "húðhreistur" },
            { latin: "Verruca", icelandic: "smitvarta" }
        ];

        let currentCard = 0;
        let shuffledTerms = [...medicalTerms];
        let selectedLatin = null;
        let matches = {};
        let score = 0;
        let attempts = 0;

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
            document.getElementById('matchingView').classList.add('hidden');
        }

        // Flashcard functions
        function startFlashcards() {
            document.getElementById('menuView').classList.add('hidden');
            document.getElementById('flashcardView').classList.remove('hidden');
            shuffleFlashcards();
        }

        function shuffleFlashcards() {
            shuffledTerms = shuffleArray(medicalTerms);
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

        // Matching functions
        function startMatching() {
            document.getElementById('menuView').classList.add('hidden');
            document.getElementById('matchingView').classList.remove('hidden');
            resetMatching();
        }

        function resetMatching() {
            matches = {};
            selectedLatin = null;
            score = 0;
            attempts = 0;
            document.getElementById('matchScore').textContent = `0 / ${medicalTerms.length}`;
            document.getElementById('matchAttempts').textContent = '0';
            document.getElementById('feedbackDiv').innerHTML = '';
            document.getElementById('completeScreen').classList.add('hidden');
            document.getElementById('matchingGame').classList.remove('hidden');
            renderMatching();
        }

        function renderMatching() {
            const unmatched = medicalTerms.filter(t => !matches[t.latin]);
            const shuffledLatin = shuffleArray(unmatched);
            const shuffledIcelandic = shuffleArray(unmatched);

            const latinDiv = document.getElementById('latinOptions');
            const icelandicDiv = document.getElementById('icelandicOptions');

            latinDiv.innerHTML = '';
            icelandicDiv.innerHTML = '';

            shuffledLatin.forEach(term => {
                const btn = document.createElement('button');
                btn.className = 'matching-btn';
                btn.textContent = term.latin;
                btn.onclick = () => selectLatin(term);
                latinDiv.appendChild(btn);
            });

            shuffledIcelandic.forEach(term => {
                const btn = document.createElement('button');
                btn.className = 'matching-btn';
                btn.textContent = term.icelandic;
                btn.onclick = () => selectIcelandic(term);
                icelandicDiv.appendChild(btn);
            });
        }

        function selectLatin(term) {
            selectedLatin = term;
            document.getElementById('feedbackDiv').innerHTML = '';
            
            document.querySelectorAll('#latinOptions .matching-btn').forEach(btn => {
                btn.classList.remove('selected');
                if (btn.textContent === term.latin) {
                    btn.classList.add('selected');
                }
            });
        }

        function selectIcelandic(term) {
            if (!selectedLatin) {
                showFeedback('error', '⚠️ Veldu fyrst latneskt orð!');
                return;
            }

            attempts++;
            document.getElementById('matchAttempts').textContent = attempts;

            if (selectedLatin.icelandic === term.icelandic) {
                matches[selectedLatin.latin] = term.icelandic;
                score++;
                document.getElementById('matchScore').textContent = `${score} / ${medicalTerms.length}`;
                showFeedback('success', '✓ Rétt! 🎉');
                selectedLatin = null;

                if (score === medicalTerms.length) {
                    showComplete();
                } else {
                    setTimeout(() => renderMatching(), 500);
                }
            } else {
                showFeedback('error', '✗ Reyndu aftur!');
            }
        }

        function showFeedback(type, message) {
            const feedbackDiv = document.getElementById('feedbackDiv');
            feedbackDiv.innerHTML = `<div class="feedback ${type}">${message}</div>`;
        }

        function showComplete() {
            document.getElementById('matchingGame').classList.add('hidden');
            const percentage = Math.round((score / attempts) * 100);
            document.getElementById('completeScreen').innerHTML = `
                <div class="complete-card">
                    <h2>Til hamingju! 🎉</h2>
                    <p>Þú kláraðir öll orðin!</p>
                    <p style="color: #6b7280; margin-top: 1rem;">
                        Stigahlutfall: ${score}/${attempts} (${percentage}% rétt)
                    </p>
                    <button class="btn" onclick="resetMatching()">Spila aftur</button>
                </div>
            `;
            document.getElementById('completeScreen').classList.remove('hidden');
        }

        // Initialize
        shuffleFlashcards();
    </script>
</body>
</html>
