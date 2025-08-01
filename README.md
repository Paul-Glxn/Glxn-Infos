<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>GLXN Community</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@600&display=swap" rel="stylesheet" />
  <style>
    /* Grundstyles */
    * {
      box-sizing: border-box;
    }
    body, html {
      margin: 0;
      padding: 0;
      height: 100%;
      background: black;
      font-family: 'Orbitron', sans-serif;
      color: #00ff00;
      overflow-x: hidden;
      position: relative;
      z-index: 0;
    }

    /* Matrix Canvas im Hintergrund */
    #matrixCanvas {
      position: fixed;
      top: 0; left: 0;
      width: 100%;
      height: 100%;
      z-index: -1;
      background: black;
    }

    /* Hacker Text Bereich */
    .hacker-text {
      max-width: 900px;
      margin: 40px auto 20px auto;
      padding: 20px;
      background: rgba(0, 0, 0, 0.75);
      border: 2px solid #00ff00;
      border-radius: 12px;
      box-shadow:
        0 0 10px #00ff00,
        0 0 20px #00ff00,
        0 0 30px #00ff00;
      font-family: 'Courier New', Courier, monospace;
      font-size: 1.3em;
      line-height: 1.4em;
      text-shadow:
        0 0 5px #00ff00,
        0 0 10px #00ff00,
        0 0 20px #00ff00;
    }

    .hacker-text .typing {
      white-space: nowrap;
      overflow: hidden;
      border-right: 3px solid #00ff00;
      animation: typing 5s steps(80, end), blinkCaret 0.75s step-end infinite, flicker 3s infinite;
      font-weight: bold;
      font-size: 1.5em;
      margin-bottom: 15px;
    }

    .hacker-text p {
      margin: 8px 0;
      animation: flicker 3s infinite;
    }

    .hacker-link {
      color: #00ff00;
      font-weight: bold;
      text-decoration: underline;
    }

    .hacker-link:hover {
      color: #66ff66;
    }

    /* Animationen */
    @keyframes typing {
      from { width: 0 }
      to { width: 100% }
    }
    @keyframes blinkCaret {
      50% { border-color: transparent }
      100% { border-color: #00ff00 }
    }
    @keyframes flicker {
      0%, 100% { opacity: 1; text-shadow:
        0 0 5px #00ff00,
        0 0 10px #00ff00,
        0 0 20px #00ff00; }
      50% { opacity: 0.85; text-shadow:
        0 0 3px #009900,
        0 0 6px #009900,
        0 0 10px #009900; }
    }

    /* Navigation */
    header {
      background-color: #001100cc;
      padding: 15px 25px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      box-shadow: 0 0 15px #00ff00aa;
      position: sticky;
      top: 0;
      z-index: 10;
    }

    .counter {
      font-size: 1em;
      color: #00ffcc;
      font-family: monospace;
      text-shadow: 0 0 5px #00ffcc;
    }

    .nav {
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
    }

    .nav a {
      background-color: #003300;
      color: #00cc00;
      padding: 10px 18px;
      border-radius: 8px;
      text-decoration: none;
      font-weight: bold;
      box-shadow: 0 0 6px #00cc00aa;
      transition: background-color 0.3s ease, box-shadow 0.3s ease;
    }

    .nav a:hover {
      background-color: #00cc00;
      color: black;
      box-shadow: 0 0 15px #00ff00;
    }

    /* Sektionen */
    .section {
      max-width: 900px;
      margin: 40px auto;
      padding: 30px 25px;
      background: rgba(0, 50, 0, 0.6);
      border-radius: 15px;
      box-shadow: 0 0 20px #00ff00aa;
      color: #00ff00;
      text-shadow: 0 0 5px #00ff00bb;
    }

    h1, h2 {
      color: #00ff00;
      text-align: center;
      text-shadow:
        0 0 10px #00ff00,
        0 0 20px #00ff00;
    }

    h1 {
      font-size: 3em;
      margin-bottom: 15px;
    }
    h2 {
      font-size: 2em;
      margin-bottom: 20px;
    }

    ul {
      list-style: none;
      padding: 0;
      margin: 0;
      font-size: 1.1em;
    }
    li {
      margin: 10px 0;
    }

    .btn-group {
      text-align: center;
      margin: 15px 0;
    }

    .btn {
      background-color: #00cc00;
      color: black;
      border: none;
      padding: 12px 24px;
      font-weight: bold;
      border-radius: 10px;
      cursor: pointer;
      box-shadow: 0 0 10px #00ff00aa;
      transition: background-color 0.3s ease, box-shadow 0.3s ease;
      margin: 0 10px;
      font-family: 'Orbitron', monospace;
    }

    .btn:hover {
      background-color: #009900;
      box-shadow: 0 0 20px #00ff00;
      color: #ccffcc;
    }

    /* Mini-Game Canvas */
    #gameCanvas {
      display: none;
      background-color: #000;
      margin: 20px auto;
      border: 3px solid #00ff00;
      border-radius: 10px;
      box-shadow: 0 0 15px #00ff00;
      display: block;
      max-width: 100%;
      height: 200px;
    }

    #scoreDisplay {
      text-align: center;
      font-size: 20px;
      color: #00ffcc;
      margin-top: 10px;
      font-family: monospace;
      text-shadow: 0 0 6px #00ffcc;
    }

    footer {
      text-align: center;
      padding: 20px;
      color: #006600cc;
      background-color: #001100cc;
      font-size: 0.9em;
      font-family: monospace;
      box-shadow: inset 0 0 15px #00ff00aa;
    }

  </style>
</head>
<body>

  <!-- Matrix Hintergrund -->
  <canvas id="matrixCanvas"></canvas>

  <header>
    <div class="counter">Besucher: <span id="counterValue">Lädt...</span></div>
    <nav class="nav">
      <a href="#home">Start</a>
      <a href="#partner">Partner</a>
      <a href="#regeln">Regeln</a>
      <a href="#links">Links</a>
      <a href="#spiel">Spiel</a>
    </nav>
  </header>

  <!-- Hacker Text oben -->
  <div class="hacker-text" id="home">
    <div class="typing">🌌 GLXN – Die Chaos-Community, die du nicht vergessen wirst.</div>
    <p>Du willst keine 0815-Server mehr? Bei uns gibt’s Action, Projekte, Minecraft-Server, Tech-Talks und den gewissen Hauch von Anarchie.</p>
    <p>💣 Projekte. Memes. Server. Events. Uncut.</p>
    <p>Wir machen, worauf wir Bock haben – und schreiben unsere eigenen Regeln.</p>
    <p>📽️ Filmreif - Was wir noch so Bieten können? Nukes, Grieving, Leaking,</p>
    <p>🔗 Tritt GLXN bei – nicht für jeden, aber vielleicht genau für dich.</p>
    <p><a href="https://discord.gg/Ads6YgRpKG" target="_blank" class="hacker-link">https://discord.gg/Ads6YgRpKG</a></p>
    <p><strong>@everyone</strong></p>
  </div>

  <!-- Partner -->
  <div id="partner" class="section">
    <h2>Unsere Partner</h2>
    <ul>
      <li><a href="https://discord.gg/zmtlabs" target="_blank" style="color:#00ff00;">Partner 1</a></li>
      <li><a href="https://discord.gg/SZRmRXBJdw" target="_blank" style="color:#00ff00;">Partner 2</a></li>
      <li><a href="https://discord.gg/g4cgu9jUPr" target="_blank" style="color:#00ff00;">Partner 3</a></li>
    </ul>
  </div>

  <!-- Regeln -->
  <div id="regeln" class="section">
    <h2>Regeln</h2>
    <ul>
      <li>✅ Respektvoller Umgang</li>
      <li>🚫 Keine Beleidigungen</li>
      <li>🔗 Keine Links posten</li>
      <li>📵 Keine Nummern oder Adressen ohne Erlaubnis</li>
      <li>✊ Kein Rassismus oder Diskriminierung</li>
      <li>🎉 Spaß haben ist Pflicht!</li>
    </ul>
  </div>

  <!-- Links -->
  <div id="links" class="section">
    <h2>Unsere Links</h2>
    <div class="btn-group">
      <a href="https://discord.gg/glxn" class="btn" target="_blank">Discord</a>
      <a href="https://www.tiktok.com/@glxn.community" class="btn" target="_blank">TikTok</a>
    </div>
  </div>

  <!-- Mini-Game -->
  <div id="spiel" class="section">
    <h2>Mini-Game: GLXN jagt Server</h2>
    <div class="btn-group">
      <button class="btn" onclick="startGame()">Spiel starten</button>
      <button class="btn" onclick="jump()">Springen</button>
    </div>
    <div id="scoreDisplay">Score: 0</div>
    <canvas id="gameCanvas" width="800" height="200"></canvas>
  </div>

  <footer>
    Website von Paul für die GLXN Community – 2025
  </footer>

  <script>
    // Besucherzähler
    fetch('https://api.countapi.xyz/hit/glxn-website-123/visits')
      .then(res => res.json())
      .then(data => document.getElementById('counterValue').textContent = data.value)
      .catch(() => document.getElementById('counterValue').textContent = "nicht verfügbar");

    // MATRIX BACKGROUND EFFECT
    const matrixCanvas = document.getElementById('matrixCanvas');
    const ctxMatrix = matrixCanvas.getContext('2d');

    let w = matrixCanvas.width = window.innerWidth;
    let h = matrixCanvas.height = window.innerHeight;

    const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789@#$%^&*()*&^%'.split('');
    const fontSize = 18;
    const columns = Math.floor(w / fontSize);
    const drops = new Array(columns).fill(1);

    function drawMatrix() {
      ctxMatrix.fillStyle = 'rgba(0, 0, 0, 0.05)';
      ctxMatrix.fillRect(0, 0, w, h);

      ctxMatrix.fillStyle = '#00ff00';
      ctxMatrix.font = fontSize + 'px monospace';

      for(let i = 0; i < drops.length; i++) {
        const text = letters[Math.floor(Math.random() * letters.length)];
        ctxMatrix.fillText(text, i * fontSize, drops[i] * fontSize);

        if(drops[i] * fontSize > h && Math.random() > 0.975) {
          drops[i] = 0;
        }
        drops[i]++;
      }
    }

    setInterval(drawMatrix, 50);

    window.addEventListener('resize', () => {
      w = matrixCanvas.width = window.innerWidth;
      h = matrixCanvas.height = window.innerHeight;
    });

    // MINI-GAME: Einfaches Springen und Punkte sammeln
    const gameCanvas = document.getElementById('gameCanvas');
    const ctxGame = gameCanvas.getContext('2d');

    let player = {
      x: 50,
      y: 150,
      width: 30,
      height: 50,
      dy: 0,
      gravity: 0.8,
      jumpPower: -15,
      onGround: true
    };

    let obstacles = [];
    let gameRunning = false;
    let score = 0;
    let frame = 0;

    function startGame() {
      obstacles = [];
      score = 0;
      frame = 0;
      player.y = 150;
      player.dy = 0;
      player.onGround = true;
      gameRunning = true;
      gameCanvas.style.display = 'block';
      document.getElementById('scoreDisplay').textContent = 'Score: 0';
      requestAnimationFrame(gameLoop);
    }

    function jump() {
      if(player.onGround && gameRunning) {
        player.dy = player.jumpPower;
        player.onGround = false;
      }
    }

    function gameLoop() {
      ctxGame.clearRect(0, 0, gameCanvas.width, gameCanvas.height);

      // Boden zeichnen
      ctxGame.fillStyle = '#003300';
      ctxGame.fillRect(0, 190, gameCanvas.width, 10);

      // Spieler Bewegung
      player.dy += player.gravity;
      player.y += player.dy;

      if(player.y >= 150) {
        player.y = 150;
        player.dy = 0;
        player.onGround = true;
      }

      // Spieler zeichnen
      ctxGame.fillStyle = '#00ff00';
      ctxGame.fillRect(player.x, player.y, player.width, player.height);

      // Hindernisse erzeugen
      if(frame % 90 === 0) {
        obstacles.push({
          x: gameCanvas.width,
          y: 170,
          width: 20,
          height: 20
        });
      }

      // Hindernisse bewegen und zeichnen
      for(let i = obstacles.length -1; i >= 0; i--) {
        let ob = obstacles[i];
        ob.x -= 6;

        ctxGame.fillStyle = '#cc0000';
        ctxGame.fillRect(ob.x, ob.y, ob.width, ob.height);

        // Kollisionsprüfung
        if(player.x < ob.x + ob.width &&
          player.x + player.width > ob.x &&
          player.y < ob.y + ob.height &&
          player.y + player.height > ob.y) {
          gameRunning = false;
          alert('Game Over! Dein Score: ' + score);
          gameCanvas.style.display = 'none';
          return;
        }

        // Punkte wenn Hindernis weg ist
        if(ob.x + ob.width < 0) {
          obstacles.splice(i, 1);
          score++;
          document.getElementById('scoreDisplay').textContent = 'Score: ' + score;
        }
      }

      frame++;
      if(gameRunning) requestAnimationFrame(gameLoop);
    }

    // Tasten-Event fürs Springen
    window.addEventListener('keydown', e => {
      if(e.code === 'Space') {
        jump();
      }
    });
  </script>

</body>
</html>
