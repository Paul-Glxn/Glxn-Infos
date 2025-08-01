<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>GLXN Community</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@600&display=swap" rel="stylesheet" />
  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: 'Orbitron', sans-serif;
      background: linear-gradient(120deg, #0f0f0f, #1a1a1a);
      color: #00ff00;
      overflow-x: hidden;
      padding-top: 70px; /* Platz für fixiertes Menü */
      background-color: black;
    }

    header {
      background-color: #001100cc;
      padding: 15px 25px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      box-shadow: 0 0 15px #00ff00aa;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      z-index: 1000;
    }

    .nav {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
    }

    .nav a {
      background-color: #002200;
      color: #00ff00;
      padding: 10px 18px;
      border-radius: 6px;
      text-decoration: none;
      font-weight: bold;
      transition: 0.3s ease;
      box-shadow: 0 0 6px #00ff00aa;
      font-family: monospace;
    }

    .nav a:hover {
      background-color: #00ff00;
      color: #000;
      box-shadow: 0 0 12px #00ff00;
    }

    .section {
      padding: 40px 25px;
      max-width: 900px;
      margin: 40px auto;
      background: rgba(0, 255, 0, 0.05);
      border-radius: 15px;
      box-shadow: 0 0 15px #00ff00aa;
      font-family: monospace;
      color: #00ff00;
      text-shadow: 0 0 5px #00ff00aa;
    }

    h1, h2 {
      color: #00ff00;
      text-align: center;
      margin-bottom: 20px;
      text-shadow: 0 0 20px #00ff00;
    }

    h1 {
      font-size: 3em;
      margin-top: 0;
    }

    p, li {
      font-size: 1.1em;
      line-height: 1.5em;
    }

    ul {
      list-style: none;
      padding: 0;
      margin: 0;
    }

    li {
      margin: 10px 0;
    }

    a.discord-link {
      color: #00ff00;
      font-weight: bold;
      text-decoration: underline;
      cursor: pointer;
    }

    a.discord-link:hover {
      color: #00aa00;
    }

    #matrixCanvas {
      position: fixed;
      top: 0;
      left: 0;
      z-index: 0;
      pointer-events: none;
    }

    #gameCanvas {
      display: none;
      background-color: #000;
      margin: 20px auto;
      border: 3px solid #00ff00;
      display: block;
    }

    #scoreDisplay {
      text-align: center;
      font-size: 20px;
      color: #00ff00;
      margin-top: 10px;
      font-family: monospace;
      text-shadow: 0 0 10px #00ff00;
    }

    .btn {
      padding: 12px 20px;
      background-color: #00ff00;
      color: #000;
      border: none;
      border-radius: 8px;
      font-weight: bold;
      cursor: pointer;
      margin: 8px;
      transition: 0.3s ease;
      box-shadow: 0 0 10px #00ff00;
      font-family: monospace;
    }

    .btn:hover {
      background-color: #00aa00;
      box-shadow: 0 0 15px #00ff00;
    }

    .btn-group {
      text-align: center;
      margin-bottom: 10px;
    }

    footer {
      text-align: center;
      padding: 25px;
      color: #004400;
      background-color: #001100;
      font-size: 0.9em;
      font-family: monospace;
      text-shadow: 0 0 5px #00ff00aa;
    }
  </style>
</head>
<body>

  <canvas id="matrixCanvas"></canvas>

  <header>
    <nav class="nav">
      <a href="#home">Start</a>
      <a href="#partner">Partner</a>
      <a href="#regeln">Regeln</a>
      <a href="#links">Links</a>
      <a href="#spiel">Spiel</a>
    </nav>
  </header>

  <div id="home" class="section">
    <h1>🌌 GLXN – Die Chaos-Community, die du nicht vergessen wirst.</h1>
    <p>Du willst keine 0815-Server mehr? Bei uns gibt’s Action, Projekte, Minecraft-Server, Tech-Talks und den gewissen Hauch von Anarchie.</p>
    <p>💣 Projekte. Memes. Server. Events. Uncut.</p>
    <p>Wir machen, worauf wir Bock haben – und schreiben unsere eigenen Regeln.</p>
    <p>📽️ Filmreif - Was wir noch so Bieten können? Nukes, Grieving, Leaking.</p>
    <p>🔗 Tritt GLXN bei – nicht für jeden, aber vielleicht genau für dich.</p>
    <p><a href="https://discord.gg/Ads6YgRpKG" target="_blank" class="discord-link">https://discord.gg/Ads6YgRpKG</a></p>
  </div>

  <div id="partner" class="section">
    <h2>Unsere Partner</h2>
    <ul>
      <li><a href="https://discord.gg/zmtlabs" target="_blank">Partner 1</a></li>
      <li><a href="https://discord.gg/SZRmRXBJdw" target="_blank">Partner 2</a></li>
      <li><a href="https://discord.gg/g4cgu9jUPr" target="_blank">Partner 3</a></li>
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
    // Matrix Hintergrund
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
      jumpStrength: -15,
      onGround: true,
    };

    let obstacles = [];
    let score = 0;
    let gameRunning = false;
    let gameInterval;

    function startGame() {
      if(gameRunning) return;
      gameRunning = true;
      score = 0;
      obstacles = [];
      player.y = 150;
      player.dy = 0;
      player.onGround = true;
      gameCanvas.style.display = 'block';
      gameInterval = setInterval(gameLoop, 20);
    }

    function jump() {
      if(player.onGround) {
        player.dy = player.jumpStrength;
        player.onGround = false;
      }
    }

    function gameLoop() {
      ctxGame.clearRect(0, 0, gameCanvas.width, gameCanvas.height);

      // Spieler Bewegung
      player.dy += player.gravity;
      player.y += player.dy;
      if(player.y > 150) {
        player.y = 150;
        player.dy = 0;
        player.onGround = true;
      }

      // Hindernisse erzeugen
      if(Math.random() < 0.02) {
        obstacles.push({x: gameCanvas.width, y: 170, width: 20, height: 30});
      }

      // Hindernisse bewegen
      for(let i = obstacles.length -1; i >= 0; i--) {
        obstacles[i].x -= 5;
        if(obstacles[i].x + obstacles[i].width < 0) {
          obstacles.splice(i, 1);
          score++;
          document.getElementById('scoreDisplay').textContent = 'Score: ' + score;
        } else {
          // Kollisionscheck
          if (
            player.x < obstacles[i].x + obstacles[i].width &&
            player.x + player.width > obstacles[i].x &&
            player.y + player.height > obstacles[i].y &&
            player.y < obstacles[i].y + obstacles[i].height
          ) {
            endGame();
          }
        }
      }

      // Spieler zeichnen
      ctxGame.fillStyle = '#00ff00';
      ctxGame.fillRect(player.x, player.y, player.width, player.height);
      // Hindernisse zeichnen
      ctxGame.fillStyle = '#ff0000';
      obstacles.forEach(obs => {
        ctxGame.fillRect(obs.x, obs.y, obs.width, obs.height);
      });
    }

    function endGame() {
      gameRunning = false;
      clearInterval(gameInterval);
      alert('Game Over! Dein Score: ' + score);
      gameCanvas.style.display = 'none';
      document.getElementById('scoreDisplay').textContent = 'Score: 0';
    }
  </script>
</body>
</html>
