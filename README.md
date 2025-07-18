<!DOCTYPE html>
<div id="visitCounter" style="padding: 10px; background: #111; color: #00ffcc; font-weight: bold; font-size: 1.1em;">
  Besucher: <span id="counterValue">Lädt...</span>
</div>

<html lang="de">
  
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>GLXN Community</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #0a0a0a, #002b36);
      color: #ffffff;
      text-align: center;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: 40px 20px;
    }

    h1 {
      font-size: 3em;
      margin: 0 0 20px 0;
      text-shadow: 0 0 8px #00ffcc;
    }

    .btn {
      display: inline-block;
      margin: 15px 15px;
      padding: 15px 35px;
      font-size: 1.3em;
      background-color: #00ffcc;
      color: #000;
      border: none;
      border-radius: 12px;
      text-decoration: none;
      box-shadow: 0 4px 15px rgba(0, 255, 204, 0.5);
      transition: background-color 0.3s ease, transform 0.2s ease;
      font-weight: bold;
      cursor: pointer;
    }

    .btn:hover {
      background-color: #00cfa1;
      transform: scale(1.05);
      box-shadow: 0 6px 20px rgba(0, 207, 161, 0.7);
    }

    .info {
      margin: 25px auto 40px;
      max-width: 650px;
      font-size: 1.1em;
      color: #a0d8d3;
      line-height: 1.9em;
      padding: 0 15px;
      background: rgba(0, 255, 204, 0.1);
      border-radius: 12px;
      box-shadow: 0 0 15px #00ffcc33;
    }

    hr {
      margin: 30px auto;
      width: 60%;
      border: none;
      border-top: 1px solid #00504d;
    }

    footer {
      font-size: 0.85em;
      color: #444444aa;
      margin-top: auto;
      padding: 20px 0 10px;
      font-style: italic;
      letter-spacing: 0.05em;
    }
  </style>
</head>
<body>

  <!-- Haupttitel -->
  <h1>GLXN – DEIN COMMUNITY SERVER</h1>

  <!-- Buttons -->
  <a href="https://discord.gg/glxn" class="btn" target="_blank" rel="noopener">Zum Discord</a>
  
  <a href="https://www.tiktok.com/@glxn.community" class="btn" target="_blank" rel="noopener">Zu unserem TikTok</a>

  <!-- Info-Block -->
  <div class="info">
    <p>Dieser Discord wurde von <strong>Maxim</strong> gegründet.</p>
    <p><strong>Julian</strong> ist der Stv. Owner.</p>
    <p>Mit fast <strong>1.500 Membern</strong> ist GLXN eine starke Community.</p>
    <hr />
    <p>Außerdem sind wir <strong>Maxim und Julian</strong> jederzeit erreichbar und für jeden da.</p>
    <p>Wir sind bereit für <strong>Partnerschaften</strong>.</p>
    <p>Wir machen <strong>coole Events</strong> und veranstalten <strong>Giveaways</strong>.</p>
    <p>Wir freuen uns auf jedes neue Mitglied und suchen neue teamietglieder</strong>.</p>
  </div>

  <!-- Unser Team -->
  <section class="team-section">
    <h2>UNSER TEAM</h2>
    <p><strong>Owner:</strong> Maxim</p>
    <p><strong>Stv owner:</strong> Julian</p>
    <p><strong>Administratoren:</strong> Miku.Paul, 19.er</p>
    <p><strong>Test Admins:</strong> 33.er, Julian</p>
    <p><strong>Head Moderator:</strong> unknown</p>
    <p><strong>Senior Modi:</strong> Justrekt</p>
    <p><strong>Modi:</strong> 33er (Samy Zian)</p>
    <p><strong>Probe Modi:</strong> Müller</p>
  </section>

  <!-- Footer -->
  <footer>
    Website designed by Paul
  </footer>
  <script>
    (() => {
      <!-- GLXN Bombe Runner Mini-Spiel -->
  <section class="game-runner" tabindex="0" aria-label="Glxn Bombe Runner Spiel">
    <div class="game-title">Glxn Bombe Runner - Atac's Abenteuer</div>

    <button id="startBtn" class="btn" style="margin-bottom: 15px; font-size:1.4em; padding:10px 30px; background:#00ffcc; color:#000;">
      Spiel starten
    </button>
      const canvas = document.getElementById('gameCanvas');
      const ctx = canvas.getContext('2d');

      const groundHeight = 20;
      const gravity = 0.8;
      const jumpStrength = 15;
      const elfWidth = 40;
      const elfHeight = 60;
      const poopWidth = 30;
      const poopHeight = 20;

      let elf = {
        x: 50,
        y: canvas.height - groundHeight - elfHeight,
        vy: 0,
        width: elfWidth,
        height: elfHeight,
        jumping: false
      };

      let obstacles = [];
      let gameSpeed = 5;
      let frameCount = 0;
      let gameOver = false;

      const messageDiv = document.getElementById('gameMessage');
      const jumpBtn = document.getElementById('jumpBtn');

      function resetGame() {
        elf.y = canvas.height - groundHeight - elf.height;
        elf.vy = 0;
        elf.jumping = false;
        obstacles = [];
        frameCount = 0;
        gameSpeed = 5;
        gameOver = false;
        messageDiv.style.display = 'none';
      }

      function createObstacle() {
        obstacles.push({
          x: canvas.width,
          y: canvas.height - groundHeight - poopHeight,
          width: poopWidth,
          height: poopHeight,
          color: '#7b4f00'
        });
      }

      function drawElf() {
        ctx.fillStyle = '#00ffcc';
        // Kopf
        ctx.beginPath();
        ctx.ellipse(elf.x + elf.width / 2, elf.y + elf.height * 0.25, elf.width / 2.8, elf.height / 3.2, 0, 0, Math.PI * 2);
        ctx.fill();

        // Körper
        ctx.fillRect(elf.x + elf.width * 0.2, elf.y + elf.height * 0.25, elf.width * 0.6, elf.height * 0.6);

        // Augen
        ctx.fillStyle = '#000';
        ctx.beginPath();
        ctx.ellipse(elf.x + elf.width * 0.4, elf.y + elf.height * 0.2, 4, 6, 0, 0, Math.PI * 2);
        ctx.ellipse(elf.x + elf.width * 0.6, elf.y + elf.height * 0.2, 4, 6, 0, 0, Math.PI * 2);
        ctx.fill();

        // Ohren (Spitze)
        ctx.fillStyle = '#00ffcc';
        ctx.beginPath();
        ctx.moveTo(elf.x + 5, elf.y + elf.height * 0.25);
        ctx.lineTo(elf.x + 15, elf.y + elf.height * 0.05);
        ctx.lineTo(elf.x + 25, elf.y + elf.height * 0.25);
        ctx.fill();
      }

      function drawObstacle(ob) {
        ctx.fillStyle = ob.color;
        ctx.fillRect(ob.x, ob.y, ob.width, ob.height);
        // Kackhaufen: kleine Hügel zeichnen
        ctx.beginPath();
        ctx.moveTo(ob.x, ob.y);
        ctx.bezierCurveTo(ob.x + ob.width / 3, ob.y - 10, ob.x + 2 * ob.width / 3, ob.y + 10, ob.x + ob.width, ob.y);
        ctx.fill();
      }

      function update() {
        if (gameOver) return;

        frameCount++;

        // Elf Bewegung
        elf.vy += gravity;
        elf.y += elf.vy;

        if (elf.y > canvas.height - groundHeight - elf.height) {
          elf.y = canvas.height - groundHeight - elf.height;
          elf.vy = 0;
          elf.jumping = false;
        }

        // Hindernisse erzeugen
        if (frameCount % 90 === 0) {
          createObstacle();
        }

        // Hindernisse bewegen
        obstacles.forEach((ob, idx) => {
          ob.x -= gameSpeed;
          if (ob.x + ob.width < 0) obstacles.splice(idx, 1);
        });

        // Kollision prüfen
        for (let ob of obstacles) {
          if (
            elf.x < ob.x + ob.width &&
            elf.x + elf.width > ob.x &&
            elf.y + elf.height > ob.y
          ) {
            gameOver = true;
            messageDiv.style.display = 'block';
          }
        }

        // Canvas leeren
        ctx.clearRect(0, 0, canvas.width, canvas.height);

        // Boden zeichnen
        ctx.fillStyle = '#004d4d';
        ctx.fillRect(0, canvas.height - groundHeight, canvas.width, groundHeight);

        // Elf und Hindernisse zeichnen
        drawElf();
        obstacles.forEach(drawObstacle);

        if (!gameOver) {
          requestAnimationFrame(update);
        }
      }

      // Event Listener für Leertaste
      window.addEventListener('keydown', (e) => {
        if ((e.code === 'Space' || e.key === ' ') && !gameOver && !elf.jumping) {
          elf.vy = -jumpStrength;
          elf.jumping = true;
        }
      });

      // Event Listener für SPRINGEN Button
      jumpBtn.addEventListener('click', () => {
        if (!gameOver && !elf.jumping) {
          elf.vy = -jumpStrength;
          elf.jumping = true;
        }
      });

      resetGame();
      update();
    })();
  </script>
</body>
</html>



