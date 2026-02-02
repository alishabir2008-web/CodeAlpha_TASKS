Task 1: Language Translation Tool
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🌍 Language Translator</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #e0e6ff 0%, #f0e6ff 100%);
            color: #333;
            min-height: 100vh;
        }
        header {
            background: #4a148c;
            color: white;
            padding: 20px;
            text-align: center;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        header h1 { margin: 0; font-size: 2.5em; }
        header p { margin: 5px 0; font-size: 1.2em; }
        .container {
            max-width: 600px;
            margin: 20px auto;
            background: white;
            border-radius: 10px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.1);
            overflow: hidden;
        }
        .panel {
            padding: 20px;
            border-bottom: 1px solid #e0e0e0;
        }
        .panel:last-child { border-bottom: none; }
        .lang-select {
            display: flex;
            align-items: center;
            margin-bottom: 10px;
            justify-content: space-between;
        }
        select {
            padding: 8px 12px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 14px;
            background: white;
            flex: 1;
            margin: 0 5px;
        }
        .swap-btn {
            background: #9c27b0;
            color: white;
            border: none;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .swap-btn:hover { background: #7b1fa2; }
        textarea {
            width: 100%;
            height: 150px;
            border: 1px solid #ddd;
            border-radius: 5px;
            outline: none;
            font-size: 16px;
            resize: none;
            padding: 10px;
            background: #fafafa;
        }
        .controls {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 10px;
        }
        .left-controls { display: flex; gap: 10px; }
        .right-controls { display: flex; gap: 10px; }
        button {
            background: none;
            border: none;
            cursor: pointer;
            font-size: 18px;
            color: #666;
            padding: 8px;
            border-radius: 5px;
        }
        button:hover { background: #f1f3f4; }
        .mic-btn { color: #2196f3; }
        .speak-btn { color: #2196f3; }
        .copy-btn { color: #2196f3; }
        .clear-btn { color: #f44336; }
        .translate-btn {
            background: linear-gradient(45deg, #2196f3, #9c27b0);
            color: white;
            border: none;
            padding: 12px 24px;
            font-size: 16px;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
            margin: 20px 0;
        }
        .translate-btn:hover { background: linear-gradient(45deg, #1976d2, #7b1fa2); }
        .phrases {
            padding: 20px;
            background: #f8f9fa;
            border-top: 1px solid #e0e0e0;
        }
        .phrases h3 { margin: 0 0 10px; color: #4a148c; }
        .phrase-list {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 10px;
        }
        .phrase-item {
            background: white;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            cursor: pointer;
            font-size: 14px;
            transition: background 0.3s;
        }
        .phrase-item:hover { background: #e1f5fe; }
        footer {
            text-align: center;
            padding: 20px;
            background: #4a148c;
            color: white;
            font-size: 14px;
        }
    </style>
</head>
<body>
    <header>
        <h1><i class="fas fa-globe"></i> Language Translator</h1>
        <p>Translate languages instantly and professionally</p>
    </header>
    <div class="container">
        <div class="panel">
            <div class="lang-select">
                <select id="srcLang">
                    <option value="auto">Detect language</option>
                    <option value="en">🇺🇸 English</option>
                    <option value="es">🇪🇸 Spanish</option>
                    <option value="fr">🇫🇷 French</option>
                    <option value="de">🇩🇪 German</option>
                    <option value="it">🇮🇹 Italian</option>
                    <option value="pt">🇵🇹 Portuguese</option>
                    <option value="ru">🇷🇺 Russian</option>
                    <option value="ja">🇯🇵 Japanese</option>
                    <option value="ko">🇰🇷 Korean</option>
                    <option value="zh">🇨🇳 Chinese</option>
                    <option value="ar">🇸🇦 Arabic</option>
                    <option value="hi">🇮🇳 Hindi</option>
                </select>
                <button class="swap-btn" onclick="swapLanguages()"><i class="fas fa-exchange-alt"></i></button>
                <select id="destLang">
                    <option value="en">🇺🇸 English</option>
                    <option value="es">🇪🇸 Spanish</option>
                    <option value="fr">🇫🇷 French</option>
                    <option value="de">🇩🇪 German</option>
                    <option value="it">🇮🇹 Italian</option>
                    <option value="pt">🇵🇹 Portuguese</option>
                    <option value="ru">🇷🇺 Russian</option>
                    <option value="ja">🇯🇵 Japanese</option>
                    <option value="ko">🇰🇷 Korean</option>
                    <option value="zh">🇨🇳 Chinese</option>
                    <option value="ar">🇸🇦 Arabic</option>
                    <option value="hi">🇮🇳 Hindi</option>
                </select>
            </div>
            <textarea id="inputText" placeholder="Enter text to translate"></textarea>
            <div class="controls">
                <div class="left-controls">
                    <button class="mic-btn" onclick="voiceInput()"><i class="fas fa-microphone"></i></button>
                    <button class="speak-btn" onclick="speakInput()"><i class="fas fa-volume-up"></i></button>
                </div>
                <div class="right-controls">
                    <button class="copy-btn" onclick="copyInput()"><i class="fas fa-copy"></i></button>
                    <button class="clear-btn" onclick="clearInput()"><i class="fas fa-times"></i></button>
                </div>
            </div>
        </div>
        <div class="panel">
            <textarea id="outputText" placeholder="Translation will appear here" readonly></textarea>
            <div class="controls">
                <div class="left-controls">
                    <button class="speak-btn" onclick="speakTranslation()"><i class="fas fa-volume-up"></i></button>
                </div>
                <div class="right-controls">
                    <button class="copy-btn" onclick="copyToClipboard()"><i class="fas fa-copy"></i></button>
                </div>
            </div>
        </div>
        <button class="translate-btn" onclick="translateText()">Translate</button>
        <div class="phrases">
            <h3>Quick phrases for travelers</h3>
            <div class="phrase-list">
                <div class="phrase-item" onclick="loadPhrase('Where is the airport?', 'en')">Where is the airport?</div>
                <div class="phrase-item" onclick="loadPhrase('¿Dónde está el aeropuerto?', 'es')">¿Dónde está el aeropuerto?</div>
                <div class="phrase-item" onclick="loadPhrase('Où est l\'aéroport?', 'fr')">Où est l'aéroport?</div>
                <div class="phrase-item" onclick="loadPhrase('I need a taxi.', 'en')">I need a taxi.</div>
                <div class="phrase-item" onclick="loadPhrase('Necesito un taxi.', 'es')">Necesito un taxi.</div>
            </div>
        </div>
    </div>
    <footer>
        <p>&copy; 2023 Language Translator. Powered by MyMemory API.</p>
    </footer>

    <script>
        async function translateText() {
            const text = document.getElementById('inputText').value.trim();
            const srcLang = document.getElementById('srcLang').value;
            const destLang = document.getElementById('destLang').value;
            const output = document.getElementById('outputText');
            
            if (!text) {
                output.value = '';
                return;
            }
            
            output.value = 'Translating...';
            
            try {
                let langpair = srcLang === 'auto' ? `${destLang}` : `${srcLang}|${destLang}`;
                const response = await fetch(`https://api.mymemory.translated.net/get?q=${encodeURIComponent(text)}&langpair=${langpair}`);
                const data = await response.json();
                const translatedText = data.responseData.translatedText;
                output.value = translatedText;
            } catch (error) {
                output.value = `Error: ${error.message}`;
            }
        }
        
        function swapLanguages() {
            const src = document.getElementById('srcLang');
            const dest = document.getElementById('destLang');
            const temp = src.value;
            src.value = dest.value;
            dest.value = temp;
            const input = document.getElementById('inputText');
            const output = document.getElementById('outputText');
            const tempText = input.value;
            input.value = output.value;
            output.value = tempText;
        }
        
        function clearInput() {
            document.getElementById('inputText').value = '';
            document.getElementById('outputText').value = '';
        }
        
        function copyInput() {
            const text = document.getElementById('inputText').value.trim();
            if (text) {
                navigator.clipboard.writeText(text).then(() => {
                    alert('Input copied!');
                });
            }
        }
        
        function copyToClipboard() {
            const text = document.getElementById('outputText').value.trim();
            if (text && text !== 'Translating...' && !text.startsWith('Error:')) {
                navigator.clipboard.writeText(text).then(() => {
                    alert('Translation copied!');
                });
            }
        }
        
        function speakInput() {
            const text = document.getElementById('inputText').value.trim();
            if (text) {
                const utterance = new SpeechSynthesisUtterance(text);
                utterance.lang = document.getElementById('srcLang').value;
                window.speechSynthesis.speak(utterance);
            }
        }
        
        function speakTranslation() {
            const text = document.getElementById('outputText').value.trim();
            if (text && text !== 'Translating...' && !text.startsWith('Error:')) {
                const utterance = new SpeechSynthesisUtterance(text);
                utterance.lang = document.getElementById('destLang').value;
                window.speechSynthesis.speak(utterance);
            }
        }
        
        function voiceInput() {
            alert('Voice input feature: Speak into your microphone (simulated). In a real app, this would use Web Speech API.');
        }
        
        function loadPhrase(phrase, lang) {
            document.getElementById('inputText').value = phrase;
            document.getElementById('srcLang').value = lang;
        }
    </script>
</body>
</html>
