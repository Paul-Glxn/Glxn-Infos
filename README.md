<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>GLXN Community - Hacker Style</title>
  <link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&display=swap" rel="stylesheet" />
  <style>
    /* Matrix Code Background */
    body, html {
      margin: 0; padding: 0; height: 100%;
      background: black;
      overflow-x: hidden;
      font-family: 'Share Tech Mono', monospace;
      color: #00ff00;
      position: relative;
      z-index: 1;
    }

    canvas#matrix {
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      z-index: 0;
      background: black;
      display: block;
    }

    header {
      background: rgba(0, 0, 0, 0.85);
      border-bottom: 2px solid #00ff00;
      padding: 20px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      color: #00ff00;
      box-shadow: 0 0 10px #00ff00;
      position: relative;
      z-index: 2;
    }

    .counter {
      font-size: 1.1em;
    }

    nav.nav {
      display: flex;
      gap: 15px;
      flex-wrap: wrap;
    }

    nav.nav a {
      color: #00ff00;
      text-decoration: none;
      font-weight: bold;
      border: 1.5px solid #00ff00;
      padding: 8px 16px;
      border-radius: 6px;
      transition: background-color 0.3s, color 0.3s;
      box-shadow: 0 0 10px #00ff00;
    }

    nav.nav a:hover {
      background-color: #00ff00;
      color: #000;
      box-shadow: 0 0 20px #00ff00;
    }

    .section {
      max-width: 900px;
      margin: 50px auto;
      padding: 30px 25px;
      background: rgba(0, 0, 0, 0.75);
      border: 1.5px solid #00ff00;
      border-radius: 12px;
      box-shadow: 0 0 15px #00ff00;
      position: relative;
      z-index: 2;
    }

    h1, h2 {
      text-align: center;
      color: #00ff00;
      text-shadow: 0 0 10px #00ff00;
      margin-bottom: 25px;
    }

    h1 {
      font-size: 3.2em;
    }

    p, li {
      font-size: 1.15em;
      line-height: 1.5em;
    }

    ul {
      list-style-type: none;
      padding-left: 0;
    }

    ul li::before {
      content: "› ";
      color: #00ff00;
    }

    .btn-group {
      text-align: center;
      margin: 25px 0;
    }

    .btn {
      background-color: transparent;
      border: 1.5px solid #00ff00;
      color: #00ff00;
      font-family: 'Share Tech Mono', monospace;
      font-weight: bold;
      padding: 12px 24px;
      margin: 10px;
      border-radius: 8px;
      cursor: pointer;
      transition: background-color 0.3s, color 0.3s, box-shadow 0.3s;
      box-shadow: 0 0 8px #00ff00;
    }

    .btn:hover {
      background-color: #00ff00;
      color: black;
      box-shadow: 0 0 20px #00ff00;
    }

    #gameCanvas {
      display: none;
      background-color: black;
      margin: 20px auto;
      border: 3px solid #00ff00;
      border-radius: 10px;
      box-shadow: 0 0 20px #00ff00;
    }

    #scoreDisplay {
      text-align: center;
      font-size: 1.3em;
      color: #00ff00;
      margin-top: 10px;
      font-weight: bold;
      text-shadow: 0 0 10px #00ff00;
    }

    footer {
      text-align: center;
      padding: 25px;
      color: #004400;
      background-color: #000;
      font-size: 0.9em;
      border-top: 2px solid #00ff00;
      position: relative;
      z-index: 2;
      text-shadow: 0 0 8px #00ff00;
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
    <h1>Willkommen bei GLXN</h1>
    <p style="text-align:center;">Lustig und Vertrauenshaft – deine Community für Events & Giveaways.</p>
  </div>

  <div id="partner" class="section">
    <h2>Unsere Partner</h2>
    <ul>
      <li><a href="https://discord.gg/zmtlabs" target="_blank" style="color:#00ff00; text-decoration:underline;">Partner 1</a></li>
      <li><a href="https://discord.gg/SZRmRXBJdw" target="_blank" style="color:#00ff00; text-decoration:underline;">Partner 2</a></li>
      <li><a href="https://discord.gg/g4cgu9jUPr" target="_blank" style="color:#00ff00; text-decoration:underline;">Partner 3</a></li>
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

    // Matrix Code Animation
    const matrixCanvas = document.getElementById('matrix');
    const matrixCtx = matrixCanvas.getContext('2d');

    // Set canvas full screen
    matrixCanvas.width = window.innerWidth;
    matrixCanvas.height = window.innerHeight;

    const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789@#$%^&*()*&^%+-/~{[|`]}';
    const fontSize = 18;
    const columns = Math.floor(matrixCanvas.width / fontSize);
    const drops = [];

    for (let i = 0; i < columns; i++) {
      drops[i] = Math.random() * matrixCanvas.height;
    }

    function drawMatrix() {
      matrixCtx.fillStyle = 'rgba(0, 0, 0, 0.05)';
      matrixCtx.fillRect(0, 0, matrixCanvas.width, matrixCanvas.height);

      matrixCtx.fillStyle = '#0F0';
      matrixCtx.font = fontSize + 'px monospace';

      for (let i = 0; i < drops.length; i++) {
        const text = letters.charAt(Math.floor(Math.random() * letters.length));
        matrixCtx.fillText(text, i * fontSize, drops[i] * fontSize);

        if (drops[i] * fontSize > matrixCanvas.height && Math.random() > 0.975) {
          drops[i] = 0;
        }
        drops[i] += 1;
      }
    }

    setInterval(drawMatrix, 35);

    // Game Variables and Logic
    const canvas = document.getElementById("gameCanvas");
    const ctx = canvas.getContext("2d");

    // Since no images are allowed, let's replace them with simple shapes/colors for the game
    // Bomb = green square, Atac = red square, Poops = gray squares

    const jumpSound = new Audio("https://actions.google.com/sounds/v1/cartoon/slide_whistle_to_drum.ogg");
    const hitSound = new Audio("https://actions.google.com/sounds/v1/cartoon/clang_and_wobble.ogg");
    const nukeSound = new Audio("https://actions.google.com/sounds/v1/alarms/nuclear_alarm.ogg");

    let bomb, atac, poops = [], gravity = 0.6, jumpStrength = -12, isJumping = false;
    let score = 0, gameLoop, scoreInterval, poopSpawner;

    function resetGame() {
      bomb = { x: 50, y: 150, width: 30, height: 30, velocityY: 0 };
      atac = { x: 800, y: 150, width: 30, height: 30 };
      poops = [];
      isJumping = false;
      score = 0;
      document.getElementById("scoreDisplay").textContent = "Score: 0";
    }

    function startGame() {
      canvas.style.display = "block";
      resetGame();
      clearInterval(gameLoop);
      clearInterval(scoreInterval);
      clearInterval(poopSpawner);

      gameLoop = setInterval(updateGame, 20);
      scoreInterval = setInterval(() => {
        score++;
        document.getElementById("scoreDisplay").textContent = "Score: " + score;
      }, 500);
      poopSpawner = setInterval(() => {
        poops.push({ x: 800, y: 165, width: 25, height: 15 });
      }, 1500);
    }

    function jump() {
      if (!isJumping) {
        bomb.velocityY = jumpStrength;
        isJumping = true;
        jumpSound.play();
      }
    }

    document.addEventListener("keydown", e => {
      if (e.code === "Space") jump();
    });

    canvas.addEventListener("click", () => jump()); // Touch/Click Support

    function updateGame() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);

      // Bomb (green square)
      bomb.velocityY += gravity;
      bomb.y += bomb.velocityY;
      if (bomb.y >= 150) {
        bomb.y = 150;
        isJumping = false;
      }
      ctx.fillStyle = "#00ff00";
      ctx.fillRect(bomb.x, bomb.y, bomb.width, bomb.height);

      // Atac (red square)
      atac.x -= 5;
      if (atac.x < -30) atac.x = 800;
      ctx.fillStyle = "#ff0000";
      ctx.fillRect(atac.x, atac.y, atac.width, atac.height);

      // Poops (gray squares)
      poops.forEach(p => p.x -= 6);
      poops = poops.filter(p => p.x > -30);
      ctx.fillStyle = "#555555";
      poops.forEach(p => ctx.fillRect(p.x, p.y, p.width, p.height));

      // Collision detection
      for (let p of poops) {
        if (checkCollision(bomb, p)) {
          hitSound.play();
          endGame("💩 Kackhaufen getroffen!");
          return;
        }
      }

      if (checkCollision(bomb, atac)) {
        nukeSound.play();
        endGame("💥 GENUKED BYE GLXN!");
      }
    }

    function checkCollision(a, b) {
      return (
        a.x < b.x + b.width &&
        a.x + a.width > b.x &&
        a.y < b.y + b.height &&
        a.y + a.height > b.y
      );
    }

    function endGame(message) {
      clearInterval(gameLoop);
      clearInterval(scoreInterval);
      clearInterval(poopSpawner);
      alert(message);
    }

    // Resize matrix canvas on window resize
    window.addEventListener('resize', () => {
      matrixCanvas.width = window.innerWidth;
      matrixCanvas.height = window.innerHeight;
    });
  </script>
</body>
</html>
p
