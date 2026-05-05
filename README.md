<!DOCTYPE html>
<html lang="hu">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HTML Szerkesztő - Átméretezhető panelek</title>
    <style>
        * {
            box-sizing: border-box;
        }
        body {
            margin: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f1f1f1;
            display: flex;
            flex-direction: column;
            height: 100vh;
            overflow: hidden;
        }
        /* Felső menüsor */
        .header {
            background-color: #ffffff;
            padding: 10px 20px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            border-bottom: 1px solid #ddd;
            z-index: 10;
        }
        .button-group {
            display: flex;
            gap: 10px;
        }
        .btn-run {
            background-color: #04AA6D;
            color: white;
            border: none;
            padding: 10px 25px;
            font-size: 16px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
        }
        .btn-run:hover {
            background-color: #059862;
        }
        .btn-clear {
            background-color: #f44336;
            color: white;
            border: none;
            padding: 10px 25px;
            font-size: 16px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
        }
        .btn-clear:hover {
            background-color: #da190b;
        }
        /* Szerkesztő konténer */
        .main-container {
            display: flex;
            flex: 1;
            background-color: #e5e5e5;
            position: relative;
            overflow: hidden;
        }
        .pane {
            background-color: white;
            display: flex;
            flex-direction: column;
            overflow: hidden;
            min-width: 100px;
        }
        #leftPane {
            width: 50%;
        }
        #rightPane {
            flex: 1;
        }
        /* Az elválasztó sáv */
        .resizer {
            width: 10px;
            cursor: col-resize;
            background-color: #e5e5e5;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .resizer:hover {
            background-color: #ccc;
        }
        textarea {
            width: 100%;
            height: 100%;
            border: none;
            padding: 15px;
            font-family: 'Courier New', Courier, monospace;
            font-size: 15px;
            resize: none;
            outline: none;
        }
        iframe {
            width: 100%;
            height: 100%;
            border: none;
            background-color: white;
        }
        .pane-label {
            background-color: #f8f8f8;
            padding: 5px 15px;
            font-size: 12px;
            color: #555;
            border-bottom: 1px solid #eee;
            text-transform: uppercase;
            user-select: none;
        }
        .dragging iframe {
            pointer-events: none;
        }
    </style>
</head>
<body id="body">

    <div class="header">
        <div class="button-group">
            <button class="btn-run" onclick="runCode()">Fuss &gt;</button>
            <button class="btn-clear" onclick="clearCode()">Törlés</button>
        </div>
        <div style="font-size: 14px; color: #666;">
            Interaktív HTML Szerkesztő
        </div>
    </div>

    <div class="main-container" id="container">
        <div class="pane" id="leftPane">
            <div class="pane-label">Forráskód</div>
            <textarea id="htmlCode" spellcheck="false" oninput="saveCode()"><!DOCTYPE html>
<html>
<head>
<style>
  body { font-family: sans-serif; text-align: center; }
  h1 { color: #04AA6D; }
</style>
</head>
<body>

<h1>Sikeres futtatás!</h1>
<p>Próbáld meg elhúzni a középső szürke sávot.</p>

</body>
</html></textarea>
        </div>

        <div class="resizer" id="dragBar"></div>

        <div class="pane" id="rightPane">
            <div class="pane-label">Eredmény</div>
            <iframe id="resultFrame"></iframe>
        </div>
    </div>

    <script>
        const leftPane = document.getElementById('leftPane');
        const dragBar = document.getElementById('dragBar');
        const container = document.getElementById('container');
        const body = document.getElementById('body');
        const editor = document.getElementById('htmlCode');

        let isDragging = false;

        function saveCode() {
            localStorage.setItem('savedHtmlCode', editor.value);
        }

        function clearCode() {
            if (confirm("Biztosan törölni akarod a projektet?")) {
                editor.value = "";
                localStorage.removeItem('savedHtmlCode');
                runCode();
            }
        }

        dragBar.addEventListener('mousedown', function(e) {
            isDragging = true;
            body.classList.add('dragging');
        });

        document.addEventListener('mousemove', function(e) {
            if (!isDragging) return;
            let containerOffsetLeft = container.offsetLeft;
            let pointerRelativeXpos = e.clientX - containerOffsetLeft;
            let newWidth = Math.max(100, Math.min(pointerRelativeXpos, container.clientWidth - 100));
            leftPane.style.width = newWidth + 'px';
        });

        document.addEventListener('mouseup', function() {
            if (isDragging) {
                isDragging = false;
                body.classList.remove('dragging');
            }
        });

        function runCode() {
            const htmlCode = editor.value;
            const frame = document.getElementById('resultFrame').contentWindow.document;
            frame.open();
            frame.write(htmlCode);
            frame.close();
        }

        window.onload = function() {
            const savedData = localStorage.getItem('savedHtmlCode');
            if (savedData) {
                editor.value = savedData;
            }
            runCode();
        };
    </script>

</body>
</html>
