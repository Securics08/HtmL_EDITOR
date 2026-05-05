<!DOCTYPE html>
<html lang="hu">

<head>
  <meta charset="UTF-8">
  <title>Securics-911-STABLE-V121-F5-Fix</title>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Monoton&family=Pinyon+Script&family=Nabla&family=Bungee+Shade&family=Ewert&family=Vast+Shadow&family=Creepster&family=Lobster&family=Righteous&family=Faster+One&family=Special+Elite&family=Orbitron&family=Pacifico&family=Press+Start+2P&family=Permanent+Marker&family=Sacramento&family=Silkscreen&family=Codystar&family=Megrim&family=Fredericka+the+Great&family=UnifrakturMaguntia&family=Wallpoet&family=Syncopate&family=Fascinate+Inline&family=Nosifer&family=Rubik+Glitch&family=Bangers&family=Alumni+Sans+Inline+One&family=Iceberg&family=Glass+Antiqua&family=Kranky&family=Great+Vibes&family=Bruno+Ace+SC&family=VT323&family=Montserrat&family=Nunito&family=Oswald&family=Playfair+Display&family=Spectral&family=Ultra&family=Varela+Round&family=Alegreya&family=Roboto+Serif&family=Roboto+Mono&family=Bungee+Spice&family=Shadows+Into+Light&family=Indie+Flower&family=Dancing+Script&family=Caveat&family=Satisfy&family=Kaushan+Script&family=Yellowtail&family=Courgette&family=Amatic+SC&family=Bebas+Neue&family=Abril+Fatface&family=Patua+One&family=Fredoka+One&family=Limelight&family=Stalinist+One&family=Black+Ops+One&family=Shojumaru&family=Metal+Mania&family=Sancreek&family=Rye&family=Butcherman&family=Frijole&family=Eater&family=Aclonica&family=Michroma&family=Audiowide&family=Quantico&family=Russo+One&family=Squada+One&family=Allura&family=Alex+Brush&family=Cookie&family=Grand+Hotel&family=Parisienne&family=Rochester&family=Tangerine&family=Zeyada&family=Architects+Daughter&family=Covered+By+Your+Grace&family=Gloria+Hallelujah&family=Handlee&family=Patrick+Hand&family=Reenie+Beanie&family=Rock+Salt&family=Coming+Soon&family=Boogaloo&family=Carter+One&family=Chango&family=Cherry+Cream+Soda&family=Chewy&family=Fugaz+One&family=Luckiest+Guy&family=Titan+One&family=Yeseva+One&family=Marcellus&family=Cinzel&family=Forum&family=Cormorant+Garamond&display=swap" rel="stylesheet">
  <style>
    body { margin: 0; background: #0a0a0a; color: #fff; font-family: Arial, sans-serif; transition: background 0.3s; }
    .container { display: flex; height: 100vh; }
    .sidebar { width: 60px; background: #111; padding: 10px; box-sizing: border-box; overflow-y: auto; }
    .color-btn { width: 100%; height: 24px; margin-bottom: 6px; border: none; cursor: pointer; outline: none; border-radius: 4px; box-shadow: 0 0 5px rgba(255,255,255,0.2); }
    .main { flex: 1; padding: 10px; box-sizing: border-box; display: flex; flex-direction: column; }
    .toolbar { display: flex; flex-wrap: wrap; gap: 10px; margin-bottom: 10px; align-items: center; }
    .toolbar select, .toolbar input, .toolbar button { padding: 6px; border-radius: 4px; border: 1px solid #333; background: #111; color: #fff; outline: none; }
    body.light-mode { background: #e0e0e0; color: #000; }
    .light-mode #captureArea { background: #ffffff !important; border-color: #ccc; }
    #captureArea { flex: 1; background: #050505; border: 1px solid #333; border-radius: 6px; display: flex; flex-direction: column; overflow-y: auto; position: relative; }
    #editorHeader { padding: 10px; font-size: 18px; min-height: 20px; border-bottom: 1px dashed #333; outline: none; }
    .editor { flex: 1; padding: 10px; overflow-y: auto; font-size: 20px; white-space: pre-wrap; outline: none; line-height: 1.2; }
    
    /* NEON SZÍNEK */
    .neon-black { color: #000000 !important; text-shadow: none !important; }
    .neon-orange { color: #ff6600 !important; text-shadow: 0 0 5px #ff6600, 0 0 10px #ff6600 !important; }
    .neon-yellow { color: #ffff00 !important; text-shadow: 0 0 5px #ffff00, 0 0 10px #ffff00 !important; }
    .neon-darkred { color: #7a001f !important; text-shadow: 0 0 5px #7a001f, 0 0 10px #7a001f !important; }
    .neon-cyan { color: #00f6ff !important; text-shadow: 0 0 5px #00f6ff, 0 0 10px #00f6ff !important; }
    .neon-blue { color: #00aaff !important; text-shadow: 0 0 5px #00aaff, 0 0 10px #00aaff !important; }
    .neon-deepblue { color: #0080ff !important; text-shadow: 0 0 5px #0080ff, 0 0 10px #0080ff !important; }
    .neon-magenta { color: #ff00ff !important; text-shadow: 0 0 5px #ff00ff, 0 0 10px #ff00ff !important; }
    .neon-pink { color: #ff33ff !important; text-shadow: 0 0 5px #ff33ff, 0 0 10px #ff33ff !important; }
    .neon-green { color: #00ff00 !important; text-shadow: 0 0 5px #00ff00, 0 0 10px #00ff00 !important; }
    .neon-lightgreen { color: #00ff66 !important; text-shadow: 0 0 5px #00ff66, 0 0 10px #00ff66 !important; }
    .neon-lime { color: #33ff33 !important; text-shadow: 0 0 5px #33ff33, 0 0 10px #33ff33 !important; }
    .neon-mint { color: #00ff99 !important; text-shadow: 0 0 5px #00ff99, 0 0 10px #00ff99 !important; }
    .neon-purple { color: #8000ff !important; text-shadow: 0 0 5px #8000ff, 0 0 10px #8000ff !important; }
    .neon-red { color: #ff0000 !important; text-shadow: 0 0 5px #ff0000, 0 0 10px #ff0000 !important; }
    .neon-white { color: #ffffff !important; text-shadow: 0 0 5px #ffffff, 0 0 10px #ffffff !important; }

    body.glow-off [class*="neon-"] { text-shadow: none !important; }
    .saved-panel { width: 250px; background: #222; padding: 15px; overflow-y: auto; }
    .label-red { color: #ff4444; font-weight: bold; }
    .label-yellow { color: #ffff00; }
    .label-green { color: #00ff00; }
    .label-cyan { color: #00f6ff; }
  </style>
</head>

<body>
  <div class="container">
    <div class="sidebar">
      <button class="color-btn" style="background:#000; border:1px solid #444;" onmousedown="applyColorAndSet(event, 'neon-black')"></button>
      <button class="color-btn" style="background:#ff6600" onmousedown="applyColorAndSet(event, 'neon-orange')"></button>
      <button class="color-btn" style="background:#ffff00" onmousedown="applyColorAndSet(event, 'neon-yellow')"></button>
      <button class="color-btn" style="background:#7a001f" onmousedown="applyColorAndSet(event, 'neon-darkred')"></button>
      <button class="color-btn" style="background:#00f6ff" onmousedown="applyColorAndSet(event, 'neon-cyan')"></button>
      <button class="color-btn" style="background:#00aaff" onmousedown="applyColorAndSet(event, 'neon-blue')"></button>
      <button class="color-btn" style="background:#ff00ff" onmousedown="applyColorAndSet(event, 'neon-magenta')"></button>
      <button class="color-btn" style="background:#00ff00" onmousedown="applyColorAndSet(event, 'neon-green')"></button>
      <button class="color-btn" style="background:#fff" onmousedown="applyColorAndSet(event, 'neon-white')"></button>
    </div>

    <div class="main">
      <div style="background: #1a1a1a; padding: 10px; border-radius: 8px; margin-bottom: 10px; display: flex; justify-content: space-between; align-items: center;">
        <div class="neon-cyan" style="font-family: 'Orbitron'; font-size: 20px;">SECURICS-911-PNG-V121</div>
        <button onclick="localStorage.clear(); location.reload();" style="background:red; color:white; border:none; padding:5px 10px; cursor:pointer;">MEMORY RESET</button>
      </div>

      <div class="toolbar">
        <select id="fontSelect" onchange="setFont()">
          <option value="Arial">Arial</option>
          <option value="Orbitron">Orbitron (Sci-fi)</option>
          <option value="Monoton">Monoton</option>
          <option value="Special Elite">Typewriter</option>
          <option value="Creepster">Horror</option>
          <option value="Pacifico">Pacifico</option>
        </select>
        <input type="range" id="sizeRange" min="10" max="150" value="24" oninput="setSize(this.value)"> <span id="sizeValue">24</span>px
        <button onclick="toggleGlow()">Glow ON/OFF</button>
        <button onclick="toggleTheme()">🌓 Dark/Light</button>
        <button onclick="newNote()">+ Új lap</button>
      </div>

      <div class="toolbar">
        <button onclick="saveToDB()" style="background:#0080ff">MENTÉS BÖNGÉSZŐBE</button>
        <button onclick="downloadPNG(false)">PNG MENTÉS</button>
        <button onclick="downloadPNG(true)">ÁTLÁTSZÓ PNG</button>
      </div>

      <div id="savePath" style="font-family: monospace; font-size: 13px; margin-bottom: 10px;">
        <div><span class="label-red">Utolsó művelet:</span> <span id="statusMsg" class="label-green">Készenlét</span></div>
        <div><span class="label-red">Aktív Neon:</span> <span id="activeColorDisplay" class="label-cyan">neon-white</span></div>
      </div>

      <div id="captureArea">
        <div id="editorHeader" contenteditable="true">Cím helye...</div>
        <div id="editor" class="editor" contenteditable="true">Írj ide...</div>
      </div>
    </div>

    <div class="saved-panel">
      <h3 class="neon-magenta">Mentett listák</h3>
      <div id="savedList"></div>
    </div>
  </div>

  <script>
    const editor = document.getElementById("editor");
    const editorHeader = document.getElementById("editorHeader");
    const activeColorDisplay = document.getElementById("activeColorDisplay");
    
    // F5-BIZTOS SZÍNKEZELÉS
    let activeColorClass = localStorage.getItem("selectedNeonColor") || "neon-white";

    function applyColorAndSet(event, colorClass) {
      if (event) event.preventDefault();
      activeColorClass = colorClass;
      localStorage.setItem("selectedNeonColor", colorClass); // ELMENTJÜK
      activeColorDisplay.innerText = colorClass;

      const selection = window.getSelection();
      if (!selection.rangeCount) return;
      const range = selection.getRangeAt(0);
      const span = document.createElement("span");
      span.className = colorClass;

      if (range.collapsed) {
        span.innerHTML = "&#8203;"; 
        range.insertNode(span);
        range.setStartAfter(span);
        range.collapse(true);
        selection.removeAllRanges();
        selection.addRange(range);
      } else {
        span.appendChild(range.extractContents());
        range.insertNode(span);
      }
    }

    // Alapértelmezett beállítások betöltéskor
    window.onload = () => {
      activeColorDisplay.innerText = activeColorClass;
      loadFromDB();
    };

    function setFont() { editor.style.fontFamily = document.getElementById("fontSelect").value; }
    function setSize(v) { editor.style.fontSize = v + "px"; document.getElementById("sizeValue").innerText = v; }
    function toggleGlow() { document.body.classList.toggle("glow-off"); }
    function toggleTheme() { document.body.classList.toggle("light-mode"); }
    function newNote() { editor.innerHTML = ""; editorHeader.innerText = "Új jegyzet"; }

    // PNG Mentés
    async function downloadPNG(trans) {
      const area = document.getElementById("captureArea");
      const canvas = await html2canvas(area, { 
        backgroundColor: trans ? null : "#050505",
        scale: 2 
      });
      const a = document.createElement("a");
      a.download = `neon_note_${Date.now()}.png`;
      a.href = canvas.toDataURL("image/png");
      a.click();
      document.getElementById("statusMsg").innerText = "PNG Mentve!";
    }

    // IndexedDB Mentés (Böngésző memória)
    let db;
    const req = indexedDB.open("NeonDB", 1);
    req.onupgradeneeded = e => { e.target.result.createObjectStore("notes", { keyPath: "id", autoIncrement: true }); };
    req.onsuccess = e => { db = e.target.result; loadFromDB(); };

    function saveToDB() {
      const tx = db.transaction("notes", "readwrite");
      tx.objectStore("notes").add({ 
        title: editorHeader.innerText, 
        content: editor.innerHTML, 
        date: new Date().toLocaleString() 
      });
      tx.oncomplete = () => { 
        document.getElementById("statusMsg").innerText = "Adatbázisba mentve!";
        loadFromDB(); 
      };
    }

    function loadFromDB() {
      const list = document.getElementById("savedList");
      list.innerHTML = "";
      db.transaction("notes").objectStore("notes").getAll().onsuccess = e => {
        e.target.result.forEach(note => {
          const div = document.createElement("div");
          div.style = "border-bottom:1px solid #444; padding:5px; cursor:pointer; font-size:12px;";
          div.innerHTML = `<span class="label-yellow">${note.title}</span><br><small>${note.date}</small>`;
          div.onclick = () => {
            editorHeader.innerText = note.title;
            editor.innerHTML = note.content;
          };
          list.appendChild(div);
        });
      };
    }
  </script>
</body>
</html>
