<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>GLXN Community</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background-color: #0a0a0a;
      color: #ffffff;
    }

    header {
      background-color: #111;
      padding: 10px 20px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
    }

    .nav {
      display: flex;
      flex-wrap: wrap;
      gap: 15px;
    }

    .nav a {
      color: #ffffff;
      text-decoration: none;
      font-weight: bold;
      padding: 8px 12px;
      border-radius: 5px;
      background-color: #1a1a1a;
      transition: background 0.3s;
    }

    .nav a:hover {
      background-color: #cc0000;
    }

    .counter {
      color: #00ffcc;
      font-weight: bold;
    }

    h1, h2 {
      text-align: center;
      color: #ff4444;
    }

    .section {
      padding: 40px 20px;
      max-width: 900px;
      margin: auto;
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
      padding: 10px 20px;
      background-color: #00ffcc;
      color: #000;
      border: none;
      border-radius: 5px;
      font-weight: bold;
      cursor: pointer;
      margin: 5px;
    }

    #gameCanvas {
      display: none;
      background-color: #222;
      margin: 20px auto;
      border: 2px solid #ff0000;
    }

    footer {
      text-align: center;
      padding: 20px;
      color: #888;
      background-color: #111;
    }
  </style>
</head>
<body>

  <header>
    <div class="counter">Besucher: <span id="counterValue">Lädt...</span></div>
    <nav class="nav">
      <a href="#home">Start</a>
      <a href="#team">Unser Team</a>
      <a href="#partner">Unsere Partner</a>
      <a href="#regeln">Regeln</a>
      <a href="#links">Unsere Links</a>
      <a href="#spiel">Spiel</a>
    </nav>
  </header>

  <div id="home" class="section">
    <h1>Willkommen bei GLXN</h1>
    <p style="text-align:center;">Lustig und Vertrauenshaft – deine Community für Events & Giveaways.</p>
  </div>

  <div id="team" class="section">
    <h2>UNSER TEAM</h2>
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
    <h2>UNSERE PARTNER</h2>
    <ul>
      <li>Partner 1</li>
      <li>Partner 2</li>
      <li>Partner 3</li>
      <!-- Du kannst später Logos oder Links ergänzen -->
    </ul>
  </div>

  <div id="regeln" class="section">
    <h2>REGELN</h2>
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
    <h2>UNSERE LINKS</h2>
    <a href="https://discord.gg/glxn" class="btn" target="_blank">Discord</a>
    <a href="https://www.tiktok.com/@glxn.community" class="btn" target="_blank">TikTok</a>
  </div>

  <div id="spiel" class="section">
    <h2>Mini-Game: Glxn jagt Atac</h2>
    <button class="btn" onclick="startGame()">Spiel starten</button>
    <button class="btn" onclick="jump()">Springen</button><br><br>
    <canvas id="gameCanvas" width="600" height="200"></canvas>
  </div>

  <footer>
    Website von Paul für die GLXN Community – 2025
  </footer>

  <script>
    // Besucherzähler
    fetch('https://api.countapi.xyz/hit/glxn-website-123/visits')
      .then(response => response.json())
      .then(data => {
        document.getElementById('counterValue').innerText = data.value;
      })
      .catch(() => {
        document.getElementById('counterValue').innerText = "nicht verfügbar";
      });

    // Mini-Game
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');
    let bomb, atac, poop, gravity, gameLoop, jumping, jumpStrength;

    function resetGameObjects() {
      bomb = { x: 50, y: 150, width: 20, height: 20, velocityY: 0 };
      atac = { x: 600, y: 150, width: 20, height: 20 };
      poop = { x: 400, y: 160, width: 20, height: 10 };
      gravity = 0.6;
      jumping = false;
      jumpStrength = -10;
    }

    function startGame() {
      canvas.style.display = "block";
      resetGameObjects();
      clearInterval(gameLoop);
      gameLoop = setInterval(updateGame, 20);
    }

    function jump() {
      if (!jumping) {
        bomb.velocityY = jumpStrength;
        jumping = true;
      }
    }

    function updateGame() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);

      // Update Positionen
      bomb.velocityY += gravity;
      bomb.y += bomb.velocityY;

      if (bomb.y >= 150) {
        bomb.y = 150;
        jumping = false;
      }

      atac.x -= 5;
      poop.x -= 5;

      if (atac.x < -20) atac.x = 600;
      if (poop.x < -20) poop.x = 600;

      // Kollision
      if (
        bomb.x < atac.x + atac.width &&
        bomb.x + bomb.width > atac.x &&
        bomb.y < atac.y + atac.height &&
        bomb.y + bomb.height > atac.y
      ) {
        clearInterval(gameLoop);
        alert("GENUKED BYE GLXN!");
        canvas.style.display = "none";
      }

      if (
        bomb.x < poop.x + poop.width &&
        bomb.x + bomb.width > poop.x &&
        bomb.y < poop.y + poop.height &&
        bomb.y + bomb.height > poop.y
      ) {
        clearInterval(gameLoop);
        alert("Kackhaufen getroffen! Nochmal versuchen!");
        canvas.style.display = "none";
      }

      // Zeichnen
      ctx.fillStyle = "#ff0000";
      ctx.fillRect(bomb.x, bomb.y, bomb.width, bomb.height);

      ctx.fillStyle = "#00ff00";
      ctx.fillRect(atac.x, atac.y, atac.width, atac.height);

      ctx.fillStyle = "#964B00";
      ctx.fillRect(poop.x, poop.y, poop.width, poop.height);
    }
  </script>
</body>
</html>
