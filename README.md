<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>GLXN Community</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@600&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Orbitron', sans-serif;
      background: linear-gradient(120deg, #0f0f0f, #1a1a1a);
      color: #fff;
    }

    header {
      background-color: #111;
      padding: 20px 30px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      box-shadow: 0 4px 20px rgba(255, 0, 0, 0.3);
    }

    .counter {
      color: #00ffcc;
      font-size: 1em;
    }

    .nav {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
    }

    .nav a {
      background-color: #222;
      color: #ff4444;
      padding: 10px 18px;
      border-radius: 6px;
      text-decoration: none;
      font-weight: bold;
      transition: 0.3s ease;
      box-shadow: 0 0 6px rgba(255, 68, 68, 0.4);
    }

    .nav a:hover {
      background-color: #ff4444;
      color: #fff;
      box-shadow: 0 0 10px #ff4444;
    }

    h1 {
      font-size: 3.2em;
      color: #ff4444;
      text-align: center;
      margin-top: 50px;
      margin-bottom: 10px;
      text-shadow: 2px 2px 10px #ff0000;
    }

    h2 {
      text-align: center;
      color: #ff4444;
      margin-bottom: 15px;
      font-size: 2em;
    }

    .section {
      padding: 40px 25px;
      max-width: 900px;
      margin: 40px auto;
      background: rgba(255,255,255,0.05);
      border-radius: 15px;
      box-shadow: 0 0 15px rgba(255,0,0,0.2);
    }

    ul {
      list-style-type: none;
      padding: 0;
    }

    li {
      margin: 10px 0;
      font-size: 1.1em;
    }

    .btn {
      padding: 12px 20px;
      background-color: #ff4444;
      color: #fff;
      border: none;
      border-radius: 8px;
      font-weight: bold;
      cursor: pointer;
      margin: 8px;
      transition: 0.3s ease;
      box-shadow: 0 0 10px rgba(255, 68, 68, 0.5);
    }

    .btn:hover {
      background-color: #cc0000;
      box-shadow: 0 0 15px #ff4444;
    }

    #gameCanvas {
      display: none;
      background-color: #000;
      margin: 20px auto;
      border: 3px solid #ff0000;
      display: block;
    }

    #scoreDisplay {
      text-align: center;
      font-size: 20px;
      color: #00ffcc;
      margin-top: 10px;
    }

    footer {
      text-align: center;
      padding: 25px;
      color: #aaa;
      background-color: #111;
      font-size: 0.9em;
    }
  </style>
</head>
<body>

  <header>
    <div class="counter">Besucher: <span id="counterValue">Lädt...</span></div>
    <nav class="nav">
      <a href="#home">Start</a>
      <a href="#team">Unser Team</a>
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

  <div id="team" class="section">
    <h2>Unser Team</h2>
    <ul>
      <li><strong>Owner:</strong> Maxim</li>
      <li><strong>Stv Owner:</strong> Julian</li>
      <li><strong>Administratoren:</strong> Miku.Paul, 19.er</li>
      <li><strong>Test Admins:</strong> 33.er, Julian</li>
      <li><strong>Head Moderator:</strong> unknown</li>
      <li><strong>Senior Modi:</strong> Justrekt</li>
      <li><strong>Modi:</strong> 33er (Samy Zian)</li>
      <li><strong>Probe Modi:</strong> Müller</li>
    </ul>
  </div>

  <div id="partner" class="section">
    <h2>Unsere Partner</h2>
    <ul>
      <li>
        <a href="https://discord.gg/zmtlabs" target="_blank">Partner 1</a><br>
        <a href="https://discord.gg/SZRmRXBJdw" target="_blank">Partner 2</a><br>
        <a href="https://discord.gg/g4cgu9jUPr" target="_blank">Partner 3</a><br>
        <a href="https://discord.gg/9CEbXnxf" target="_blank">Partner 4</a>
      </li>
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
    <a href="https://discord.gg/glxn" class="btn" target="_blank">Discord</a>
    <a href="https://www.tiktok.com/@glxn.community" class="btn" target="_blank">TikTok</a>
  </div>

  <div id="spiel" class="section">
    <h2>Mini-Game: GLXN jagt Atac</h2>
    <div style="text-align:center;">
      <button class="btn" onclick="startGame()">Spiel starten</button>
      <button class="btn" onclick="jump()">Springen (Leertaste)</button>
    </div>
    <div id="scoreDisplay">Score: 0</div>
    <canvas id="gameCanvas" width="800" height="200"></canvas>
  </div>

  <footer>
    Website von Paul für die GLXN Community – 2025
  </footer>

  <script>
    fetch('https://api.countapi.xyz/hit/glxn-website-123/visits')
      .then(res => res.json())
      .then(data => {
        document.getElementById('counterValue').textContent = data.value;
      });

    const canvas = document.getElementById("gameCanvas");
    const ctx = canvas.getContext("2d");
    let bomb, atac, poops, gravity, jumpStrength, isJumping, score, scoreInterval, gameLoop;
    const poopImage = new Image(); poopImage.src = "https://i.imgur.com/0M7z3Xv.png";
    const atacImage = new Image(); atacImage.src = "https://i.imgur.com/k2lxMns.png";
    const bombImage = new Image(); bombImage.src = "https://i.imgur.com/3wLt9i2.png";
    const jumpSound = new Audio("https://actions.google.com/sounds/v1/cartoon/slide_whistle_to_drum.ogg");
    const hitSound = new Audio("https://actions.google.com/sounds/v1/cartoon/clang_and_wobble.ogg");
    const nukeSound = new Audio("https://actions.google.com/sounds/v1/alarms/nuclear_alarm.ogg");

    function resetGame() {
      bomb = { x: 50, y: 150, width: 30, height: 30, velocityY: 0 };
      atac = { x: 800, y: 150, width: 30, height: 30 };
      poops = [];
      gravity = 0.6;
      jumpStrength = -12;
      isJumping = false;
      score = 0;
      document.getElementById("scoreDisplay").textContent = "Score: 0";
    }

    function startGame() {
      canvas.style.display = "block";
      resetGame();
      clearInterval(gameLoop);
      clearInterval(scoreInterval);
      gameLoop = setInterval(updateGame, 20);
      scoreInterval = setInterval(() => {
        score++;
        document.getElementById("scoreDisplay").textContent = "Score: " + score;
      }, 500);
    }

    function jump() {
      if (!isJumping) {
        bomb.velocityY = jumpStrength;
        isJumping = true;
        jumpSound.play();
      }
    }

    document.addEventListener("keydown", function(e) {
      if (e.code === "Space") jump();
    });

    function spawnPoop() {
      poops.push({ x: 800, y: 165, width: 25, height: 15 });
    }

    setInterval(spawnPoop, 1500);

    function updateGame() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      bomb.velocityY += gravity;
      bomb.y += bomb.velocityY;
      if (bomb.y >= 150) {
        bomb.y = 150;
        isJumping = false;
      }
      atac.x -= 4 + Math.random() * 2;
      if (atac.x < -30) atac.x = 800;
      for (let i = 0; i < poops.length; i++) {
        poops[i].x -= 5;
      }
      ctx.drawImage(bombImage, bomb.x, bomb.y, bomb.width, bomb.height);
      ctx.drawImage(atacImage, atac.x, atac.y, atac.width, atac.height);
      for (let i = 0; i < poops.length; i++) {
        ctx.drawImage(poopImage, poops[i].x, poops[i].y, poops[i].width, poops[i].height);
      }

      for (let i = 0; i < poops.length; i++) {
        let p = poops[i];
        if (bomb.x < p.x + p.width && bomb.x + bomb.width > p.x &&
            bomb.y < p.y + p.height && bomb.y + bomb.height > p.y) {
          hitSound.play();
          clearInterval(gameLoop);
          clearInterval(scoreInterval);
          alert("Kackhaufen getroffen! Versuchs nochmal.");
          return;
        }
      }

      if (bomb.x < atac.x + atac.width && bomb.x + bomb.width > atac.x &&
          bomb.y < atac.y + atac.height && bomb.y + bomb.height > atac.y) {
        nukeSound.play();
        clearInterval(gameLoop);
        clearInterval(scoreInterval);
        alert("GENUKED BYE GLXN!");
      }
    }
  </script>
</body>
</html>

