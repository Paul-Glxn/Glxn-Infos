<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>GLXN Community</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@600&display=swap" rel="stylesheet" />
  <style>
    /* Grund-Reset */
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    body, html {
      height: 100%;
      background: black;
      color: #00ff00;
      font-family: 'Orbitron', sans-serif;
      overflow-x: hidden;
      /* Platz machen für das fixe Menü */
      padding-top: 70px;
    }

    /* Fixed Header */
    header {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      background-color: rgba(0, 17, 0, 0.9);
      padding: 15px 25px;
      display: flex;
      justify-content: center;
      z-index: 1000;
      box-shadow: 0 0 15px #00ff00aa;
    }

    /* Navigation */
    .nav {
      display: flex;
      gap: 12px;
    }
    .nav a {
      color: #00ff00;
      background-color: #003300;
      padding: 8px 16px;
      border-radius: 6px;
      text-decoration: none;
      font-weight: bold;
      box-shadow: 0 0 6px #00ff00aa;
      transition: background-color 0.3s, box-shadow 0.3s;
    }
    .nav a:hover {
      background-color: #00ff00;
      color: #000;
      box-shadow: 0 0 15px #00ff00;
    }

    /* Matrix-Hintergrund */
    #matrixCanvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 0;
      background: black;
    }

    /* Sektionen */
    .section {
      max-width: 900px;
      margin: 40px auto;
      padding: 30px 20px;
      background: rgba(0, 40, 0, 0.6);
      border-radius: 12px;
      box-shadow: 0 0 20px #00ff00aa;
      color: #00ff00;
      z-index: 1;
      position: relative;
    }
    h1, h2 {
      text-align: center;
      color: #00ff00;
      text-shadow: 0 0 10px #00ff00;
      margin-bottom: 20px;
    }
    h1 { font-size: 2.8em; }
    h2 { font-size: 2em; }

    .btn-group {
      text-align: center;
      margin: 20px 0;
    }
    .btn {
      background-color: #00ff00;
      color: #000;
      padding: 10px 20px;
      border: none;
      border-radius: 8px;
      font-weight: bold;
      cursor: pointer;
      box-shadow: 0 0 10px #00ff00aa;
      transition: background-color 0.3s, box-shadow 0.3s;
      font-family: 'Orbitron', sans-serif;
      margin: 0 8px;
    }
    .btn:hover {
      background-color: #009900;
      box-shadow: 0 0 20px #00ff00;
    }

    /* Mini-Game Canvas */
    #gameCanvas {
      display: none;
      margin: 20px auto;
      background: #000;
      border: 3px solid #00ff00;
      border-radius: 8px;
      box-shadow: 0 0 15px #00ff00aa;
      max-width: 100%;
      height: 200px;
    }
    #scoreDisplay {
      text-align: center;
      font-family: monospace;
      font-size: 1.2em;
      color: #00ff00;
      text-shadow: 0 0 8px #00ff00;
      margin-top: 10px;
    }

    /* Footer */
    footer {
      text-align: center;
      padding: 20px;
      background-color: rgba(0, 17, 0, 0.9);
      color: #004400;
      font-family: monospace;
      font-size: 0.9em;
      box-shadow: inset 0 0 15px #00ff00aa;
      margin-top: 40px;
      z-index: 1;
      position: relative;
    }
  </style>
</head>
<body>

  <!-- Matrix-Hintergrund -->
  <canvas id="matrixCanvas"></canvas>

  <!-- Fixiertes Menü -->
  <header>
    <nav class="nav">
      <a href="#home">Start</a>
      <a href="#partner">Partner</a>
      <a href="#regeln">Regeln</a>
      <a href="#links">Links</a>
      <a href="#spiel">Spiel</a>
    </nav>
  </header>

  <!-- Start-Sektion mit Intro-Text -->
  <div id="home" class="section">
    <h1>🌌 GLXN – Die Chaos-Community, die du nicht vergessen wirst.</h1>
    <p>Du willst keine 0815-Server mehr? Bei uns gibt’s Action, Projekte, Minecraft-Server, Tech-Talks und den gewissen Hauch von Anarchie.</p>
    <p>💣 Projekte. Memes. Server. Events. Uncut.</p>
    <p>Wir machen, worauf wir Bock haben – und schreiben unsere eigenen Regeln.</p>
    <p>📽️ Filmreif – Was wir noch so bieten können? Nukes, Grieving, Leaking.</p>
    <p>🔗 Tritt GLXN bei – nicht für jeden, aber vielleicht genau für dich.</p>
    <p><a href="https://discord.gg/Ads6YgRpKG" target="_blank" style="color:#00ff00; text-decoration:underline;">https://discord.gg/Ads6YgRpKG</a></p>
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

  <!-- Footer -->
  <footer>
    Website von Paul für die GLXN Community – 2025
  </footer>

  <script>
    // MATRIX-EFFEKT
    const matrixCanvas = document.getElementById('matrixCanvas');
    const ctx = matrixCanvas.getContext('2d');
    let w = matrixCanvas.width = window.innerWidth;
    let h = matrixCanvas.height = window.innerHeight;
    const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789@#$%^&*'.split('');
    const fontSize = 18;
    const columns = Math.floor(w / fontSize);
    const drops = Array(columns).fill(1);

    function draw() {
      ctx.fillStyle = 'rgba(0, 0, 0, 0.1)';
      ctx.fillRect(0, 0, w, h);
      ctx.fillStyle = '#00ff00';
      ctx.font = fontSize + 'px monospace';
      drops.forEach((y, i) => {
        const text = letters[Math.floor(Math.random() * letters.length)];
        ctx.fillText(text, i * fontSize, y * fontSize);
        drops[i] = (y * fontSize > h && Math.random() > 0.975) ? 0 : y + 1;
      });
    }
    setInterval(draw, 50);
    window.addEventListener('resize', () => {
      w = matrixCanvas.width = window.innerWidth;
      h = matrixCanvas.height = window.innerHeight;
    });

    // MINI-GAME
    const canvas = document.getElementById('gameCanvas');
    const ctxGame = canvas.getContext('2d');
    let player = { x:50, y:150, w:30, h:50, dy:0, gravity:0.8, jump:-15, onGround:true };
    let obstacles = [], score=0, running=false, frame=0;

    function startGame() {
      if(running) return;
      running = true;
      obstacles = []; score = 0; frame = 0;
      player.y = 150; player.dy = 0; player.onGround = true;
      canvas.style.display = 'block';
      document.getElementById('scoreDisplay').textContent = 'Score: 0';
      requestAnimationFrame(loop);
    }
    function jump() {
      if(player.onGround && running) {
        player.dy = player.jump;
        player.onGround = false;
      }
    }
    function loop() {
      ctxGame.clearRect(0,0,canvas.width,canvas.height);
      player.dy += player.gravity;
      player.y += player.dy;
      if(player.y >= 150) { player.y = 150; player.onGround=true; player.dy=0; }
      ctxGame.fillStyle = '#00ff00';
      ctxGame.fillRect(player.x, player.y, player.w, player.h);

      if(frame % 90 === 0) obstacles.push({ x: canvas.width, y:170, w:20, h:30 });
      obstacles.forEach((ob,i) => {
        ob.x -= 6;
        ctxGame.fillStyle = '#ff0000';
        ctxGame.fillRect(ob.x, ob.y, ob.w, ob.h);
        if(player.x < ob.x+ob.w && player.x+player.w>ob.x && player.y<ob.y+ob.h && player.y+player.h>ob.y) {
          running = false; alert('Game Over! Dein Score: '+score); canvas.style.display='none'; return;
        }
        if(ob.x+ob.w<0) { obstacles.splice(i,1); score++; document.getElementById('scoreDisplay').textContent='Score: '+score; }
      });
      frame++;
      if(running) requestAnimationFrame(loop);
    }
    window.addEventListener('keydown', e => { if(e.code==='Space') jump(); });
  </script>
</body>
</html>
