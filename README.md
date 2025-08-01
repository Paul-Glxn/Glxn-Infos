<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>GLXN Community</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@600&display=swap" rel="stylesheet">
  <style>
    /* Grund-Setup */
    * {
      box-sizing: border-box;
    }

    body, html {
      margin: 0;
      padding: 0;
      height: 100%;
      font-family: 'Orbitron', sans-serif;
      background-color: #000;
      color: #00ff00;
      overflow-x: hidden;
      position: relative;
    }

    /* Matrix Code Hintergrund */
    canvas#matrix {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 0;
      background: #000;
    }

    header {
      position: relative;
      background-color: #111;
      padding: 20px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      box-shadow: 0 4px 20px rgba(0, 255, 0, 0.3);
      z-index: 10;
    }

    .counter {
      color: #00ff00;
      font-size: 1em;
    }

    .nav {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      z-index: 10;
    }

    .nav a {
      background-color: #002200;
      color: #00ff00;
      padding: 10px 18px;
      border-radius: 6px;
      text-decoration: none;
      font-weight: bold;
      transition: 0.3s ease;
      box-shadow: 0 0 6px rgba(0, 255, 0, 0.4);
    }

    .nav a:hover {
      background-color: #00ff00;
      color: #000;
      box-shadow: 0 0 10px #00ff00;
    }

    .section {
      position: relative;
      z-index: 10;
      padding: 40px 25px;
      max-width: 900px;
      margin: 40px auto;
      background: rgba(0, 40, 0, 0.75);
      border-radius: 15px;
      box-shadow: 0 0 15px rgba(0, 255, 0, 0.5);
      color: #00ff00;
    }

    h1, h2 {
      color: #00ff00;
      text-align: center;
      margin-bottom: 20px;
      text-shadow: 0 0 15px #00ff00;
    }

    h1 {
      font-size: 3em;
      margin-top: 30px;
    }

    ul {
      list-style: none;
      padding: 0;
      margin: 0;
    }

    li {
      margin: 10px 0;
      font-size: 1.1em;
    }

    .btn {
      padding: 12px 20px;
      background-color: #007700;
      color: #00ff00;
      border: none;
      border-radius: 8px;
      font-weight: bold;
      cursor: pointer;
      margin: 8px;
      transition: 0.3s ease;
      box-shadow: 0 0 10px rgba(0, 255, 0, 0.5);
    }

    .btn:hover {
      background-color: #00ff00;
      color: #000;
      box-shadow: 0 0 15px #00ff00;
    }

    #gameCanvas {
      display: none;
      background-color: #000;
      margin: 20px auto;
      border: 3px solid #00ff00;
    }

    #scoreDisplay {
      text-align: center;
      font-size: 20px;
      color: #00ff00;
      margin-top: 10px;
    }

    footer {
      position: relative;
      z-index: 10;
      text-align: center;
      padding: 25px;
      color: #0f0;
      background-color: #111;
      font-size: 0.9em;
      text-shadow: 0 0 10px #00ff00;
    }

    .btn-group {
      text-align: center;
      margin-bottom: 10px;
    }

    /* Hacker-Style Effekte für den Intro-Text */
    @keyframes flicker {
      0%, 19%, 21%, 23%, 25%, 54%, 56%, 100% {
        opacity: 1;
        text-shadow:
          0 0 5px #00ff00,
          0 0 10px #00ff00,
          0 0 20px #00ff00,
          0 0 40px #00ff00;
      }
      20%, 22%, 24%, 55% {
        opacity: 0.6;
        text-shadow: none;
      }
    }

    @keyframes typing {
      from { width: 0 }
      to { width: 100% }
    }

    @keyframes blinkCaret {
      50% { border-color: transparent; }
    }

    .hacker-text {
      color: #00ff00;
      font-weight: bold;
      font-family: 'Courier New', Courier, monospace;
      font-size: 1.2em;
      white-space: nowrap;
      overflow: hidden;
      border-right: 3px solid #00ff00;
      width: 100%;
      max-width: 900px;
      margin: 0 auto 20px auto;
      text-shadow:
        0 0 5px #00ff00,
        0 0 10px #00ff00,
        0 0 20px #00ff00,
        0 0 40px #00ff00;
      animation: typing 4s steps(80, end), blinkCaret 0.75s step-end infinite, flicker 3s infinite;
    }

    .hacker-text p {
      margin: 0;
      white-space: normal;
      overflow: visible;
      border: none;
      animation: none;
      text-shadow:
        0 0 5px #00ff00,
        0 0 10px #00ff00,
        0 0 20px #00ff00,
        0 0 40px #00ff00;
      animation: flicker 3s infinite;
    }

    .hacker-link {
      color: #00ff00;
      text-decoration: underline;
    }
  </style>
</head>
<body>

  <canvas id="matrix"></canvas>

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

  <div id="home" class="section">
    <div class="hacker-text">
      🌌 GLXN – Die Chaos-Community, die du nicht vergessen wirst.<br>
      Du willst keine 0815-Server mehr? Bei uns gibt’s Action, Projekte, Minecraft-Server, Tech-Talks und den gewissen Hauch von Anarchie.<br>
      💣 Projekte. Memes. Server. Events. Uncut.<br>
      Wir machen, worauf wir Bock haben – und schreiben unsere eigenen Regeln.<br>
      📽️ Filmreif - Was wir noch so Bieten können? Nukes, Grieving, Leaking,<br>
      🔗 Tritt GLXN bei – nicht für jeden, aber vielleicht genau für dich.<br>
      <a href="https://discord.gg/Ads6YgRpKG" target="_blank" class="hacker-link">https://discord.gg/Ads6YgRpKG</a><br>
      <strong>@everyone</strong>
    </div>
    <h1>Willkommen bei GLXN</h1>
    <p style="text-align:center;">Lustig und Vertrauenshaft – deine Community für Events & Giveaways.</p>
  </div>

  <div id="partner" class="section">
    <h2>Unsere Partner</h2>
    <ul>
      <li><a href="https://discord.gg/zmtlabs" target="_blank" style="color:#00ff00;">Partner 1</a></li>
      <li><a href="https://discord.gg/SZRmRXBJdw" target="_blank" style="color:#00ff00;">Partner 2</a></li>
      <li><a href="https://discord.gg/g4cgu9jUPr" target="_blank" style="color:#00ff00;">Partner 3</a></li>
    </ul>
  </div>

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

  <div id="links" class="section">
    <h2>Unsere Links</h2>
    <div class="btn-group">
      <a href="https://discord.gg/glxn" class="btn" target="_blank">Discord</a>
      <a href="https://www.tiktok.com/@glxn.community" class="btn" target="_blank">TikTok</a>
    </div>
  </div>

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

    // Matrix Code Hintergrund
    const matrixCanvas = document.getElementById('matrix');
    const matrixCtx = matrixCanvas.getContext('2d');

    let width = window.innerWidth;
    let height = window.innerHeight;
    matrixCanvas.width = width;
    matrixCanvas.height = height;

    const letters = '0123456789ABCDEF'.split('');
    const fontSize = 16;
    const columns = Math.floor(width / fontSize);
    const drops = new Array(columns).fill(1);

    function drawMatrix() {
      matrixCtx.fillStyle = 'rgba(0, 0, 0, 0.1)';
      matrixCtx.fillRect(0, 0, width, height);

      matrixCtx.fillStyle = '#00ff00';
      matrixCtx.font = fontSize + 'px monospace';

      for (let i = 0; i < drops.length; i++) {
        const text = letters[Math.floor(Math.random() * letters.length)];
        matrixCtx.fillText(text, i * fontSize, drops[i] * fontSize);

        if (drops[i] * fontSize > height && Math.random() > 0.975) {
          drops[i] = 0;
        }
        drops[i]++;
      }
    }

    setInterval(drawMatrix, 35);

    window.addEventListener('resize', () => {
      width = window.innerWidth;
      height = window.innerHeight;
      matrixCanvas.width = width;
      matrixCanvas.height = height;
    });

    // Mini-Game Script
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');
    let score = 0;
    let gameRunning = false;

    const player = {
      x: 50,
      y: 150,
      width: 30,
      height: 30,
      dy: 0,
      gravity: 1,
      jumpForce: -15,
      grounded: false,
    };

    const obstacle = {
      x: canvas.width,
      y: 165,
      width: 30,
      height: 30,
    };

    function drawPlayer() {
      ctx.fillStyle = '#00ff00';
      ctx.fillRect(player.x, player.y, player.width, player.height);
    }

    function drawObstacle() {
      ctx.fillStyle = '#ff0000';
      ctx.fillRect(obstacle.x, obstacle.y, obstacle.width, obstacle.height);
    }

    function resetGame() {
      score = 0;
      obstacle.x = canvas.width;
      player.y = 150;
      player.dy = 0;
      gameRunning = false;
      canvas.style.display = 'none';
      document.getElementById('scoreDisplay').textContent = 'Score: 0';
    }

    function startGame() {
      if (gameRunning) return;
      gameRunning = true;
      score = 0;
      obstacle.x = canvas.width;
      player.y = 150;
      player.dy = 0;
      canvas.style.display = 'block';
      requestAnimationFrame(gameLoop);
    }

    function jump() {
      if (!gameRunning || !player.grounded) return;
      player.dy = player.jumpForce;
      player.grounded = false;
    }

    function gameLoop() {
      if (!gameRunning) return;
      ctx.clearRect(0, 0, canvas.width, canvas.height);

      // Spieler Schwerkraft & Bewegung
      player.dy += player.gravity;
      player.y += player.dy;
      if (player.y >= 150) {
        player.y = 150;
        player.grounded = true;
        player.dy = 0;
      }

      // Hindernis Bewegung
      obstacle.x -= 7;
      if (obstacle.x + obstacle.width < 0) {
        obstacle.x = canvas.width + Math.random() * 300;
        score++;
        document.getElementById('scoreDisplay').textContent = 'Score: ' + score;
      }

      // Kollisionserkennung
      if (
        player.x < obstacle.x + obstacle.width &&
        player.x + player.width > obstacle.x &&
        player.y < obstacle.y + obstacle.height &&
        player.y + player.height > obstacle.y
      ) {
        alert('Game Over! Dein Score: ' + score);
        resetGame();
        return;
      }

      drawPlayer();
      drawObstacle();

      requestAnimationFrame(gameLoop);
    }

  </script>

</body>
</html>
