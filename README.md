<!DOCTYPE html>
<html>
<head>
    <title>Text Translator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background-color: #f5f5f5;
            margin: 0;
        }
        .container {
            max-width: 500px;
            width: 100%;
            background-color: #a1a0a0;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            text-align: center;
        }
        h1 {
            color: #333;
        }
        textarea {
            width: 100%;
            height: 100px;
            padding: 10px;
            font-size: 16px;
            border: 1px solid #ddd;
            border-radius: 4px;
            resize: vertical;
            margin-bottom: 15px;
            box-sizing: border-box;
        }
        select {
            padding: 8px;
            font-size: 16px;
            border: 1px solid #ddd;
            border-radius: 4px;
            margin-right: 10px;
            transition: background-color 0.3s, border-color 0.3s;
        }
        select:hover {
            background-color: #f0f8ff; /* Light blue background on hover */
            border-color: #007bff; /* Blue border on hover */
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            color: #fff;
            background-color: #007bff;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #0056b3;
        }
        #output {
            margin-top: 20px;
            font-size: 18px;
            color: #333;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Text Translator</h1>
        <textarea id="textInput" placeholder="Enter text to translate..."></textarea>
        <select id="targetLang">
            <option value="it">Italian</option>
<option value="pt">Portuguese</option>
<option value="nl">Dutch</option>
<option value="ru">Russian</option>
<option value="zh-CN">Chinese (Simplified)</option>
<option value="ja">Japanese</option>
<option value="ko">Korean</option>
<option value="hi">Hindi</option>
<option value="ar">Arabic</option>
<option value="sv">Swedish</option>
<option value="no">Norwegian</option>
<option value="da">Danish</option>
<option value="fi">Finnish</option>
<option value="tr">Turkish</option>
<option value="pl">Polish</option>
<option value="he">Hebrew</option>
<option value="th">Thai</option>
<option value="cs">Czech</option>
<option value="el">Greek</option>
<option value="ro">Romanian</option>
<option value="hu">Hungarian</option>
<option value="uk">Ukrainian</option>
<option value="te">Telugu</option>
<option value="hi">Hindi</option>

        </select>
        <button onclick="translateText()">Translate</button>
        <p id="output"></p>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/ml5"></script>
    <script>
        function translateText() {
            const text = document.getElementById('textInput').value;
            const targetLang = document.getElementById('targetLang').value;

            fetch(`https://api.mymemory.translated.net/get?q=${text}&langpair=en|${targetLang}`)
                .then(response => response.json())
                .then(data => {
                    document.getElementById('output').innerText = `Translation: ${data.responseData.translatedText}`;
                });
        }
    </script>
</body>
</html>
