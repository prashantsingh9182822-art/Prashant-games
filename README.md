<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JOJO गेम पोर्टल - Play & Earn</title>
    <style>
        body { background: #0f0f0f; color: white; font-family: sans-serif; text-align: center; margin: 0; padding-bottom: 50px; }
        .header { background: linear-gradient(45deg, #1a1a1a, #00ff0033); padding: 20px; border-bottom: 3px solid #00ff00; }
        
        .section-title { color: #00ff00; margin-top: 25px; font-size: 1.1rem; text-transform: uppercase; letter-spacing: 1px; }
        .game-list { display: flex; flex-wrap: wrap; justify-content: center; padding: 10px; gap: 15px; }
        
        /* कार्ड स्टाइल */
        .card { 
            background: #1a1a1a; width: 105px; padding: 15px 5px;
            border-radius: 15px; border: 1px solid #333;
            display: flex; flex-direction: column; align-items: center; cursor: pointer;
        }
        .card:active { transform: scale(0.95); border-color: #00ff00; }
        .icon { font-size: 40px; margin-bottom: 8px; }
        .game-name { font-size: 12px; font-weight: bold; margin-bottom: 5px; }
        .play-tag { font-size: 9px; background: #00ff00; color: black; padding: 3px 8px; border-radius: 10px; font-weight: bold; }
        .web-tag { background: #00dbff; } /* वेब गेम्स के लिए अलग रंग */

        /* गेम दिखाने के लिए फुल स्क्रीन विंडो */
        #webgame-container { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: #000; z-index: 2000; }
        #game-frame { width: 100%; height: calc(100% - 60px); border: none; }
        .close-bar { height: 60px; background: #222; display: flex; justify-content: space-between; align-items: center; padding: 0 20px; border-bottom: 2px solid #ff4444; }

        /* स्नेक गेम पॉपअप */
        #snake-area { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: #000; z-index: 1000; padding-top: 20px; }
        canvas { background: #111; border: 3px solid #00ff00; border-radius: 10px; display: block; margin: 0 auto; }
        .controls { display: grid; grid-template-columns: repeat(3, 70px); gap: 10px; justify-content: center; margin-top: 20px; }
        .btn { width: 70px; height: 70px; background: #222; color: white; border: 2px solid #00ff00; border-radius: 50%; font-size: 25px; }
    </style>
</head>
<body>

    <div class="header">
        <h1>JOJO गेम पोर्टल 🕹️</h1>
    </div>

    <div class="section-title">🌐 ऑनलाइन खेलें (बिना डाउनलोड)</div>
    <div class="game-list">
        <div class="card" onclick="openWebGame('https://www.gamepix.com/live/ludo-legend')">
            <div class="icon">🎲</div>
            <span class="game-name">Ludo Web</span>
            <div class="play-tag web-tag">WEB PLAY</div>
        </div>
        <div class="card" onclick="openWebGame('https://www.gamepix.com/live/candy-riddles')">
            <div class="icon">🍬</div>
            <span class="game-name">Candy Web</span>
            <div class="play-tag web-tag">WEB span>
            <div class="play-tag web-tag">WEB PLAY</div>
        </div>
    </div>

    <div class="section-title">🐍 मेरा स्पेशल गेम</div>
    <div class="game-list">
        <div class="card" onclick="startSnake()">
            <div class="icon">🐍</div>
            <span class="game-name">Snake Lite</span>
            <div class="play-tag">PLAY NOW</div>
        </div>
    </div>

    <div class="section-title">📱 मोबाइल ऐप्स खोलें</div>
    <div class="game-list">
        <div class="card" onclick="launchApp('ludo')">
            <div class="icon">🎲</div>
            <span class="game-name">Ludo King</span>
            <div class="play-tag">OPEN APP</div>
        </div>
        <div class="card" onclick="launchApp('candy')">
            <div class="icon">🍬</div>
            <span class="game-name">Candy Crush</span>
            <div class="play-tag">OPEN APP</div>
        </div>
    </div>

    <div id="webgame-container">
        <div class="close-bar">
            <span style="color:#00ff00; font-weight:bold;">JOJO WEB GAME</span>
            <button onclick="closeWebGame()" style="background:#ff4444; color:white; border:none; padding:8px 15px; border-radius:5px; font-weight:bold;">✕ EXIT</button>
        </div>
        <iframe id="game-frame" src=""></iframe>
    </div>

    <div id="snake-area">
        <button onclick="stopGame()" style="background:#ff4444; color:white; padding:10px 25px; border:none; border-radius:20px; margin-bottom:10px; font-weight:bold;">✕ EXIT</button>
        <div style="font-size:20px; color:#00ff00; margin-bottom:10px;">Score: <span id="s-val">0</span></div>
        <canvas id="snakeCanvas" width="300" height="300"></canvas>
        <div class="controls">
            <button class="btn" style="grid-column:2" onclick="setDir('UP')">▲</button>
            <button class="btn" onclick="setDir('LEFT')">◀</button>
            <button class="btn" onclick="setDir('DOWN')">▼</button>
            <button class="btn" onclick="setDir('RIGHT')">▶</button>
        </div>
    </div>

<script>
    // वेब गेम कंट्रोल
    function openWebGame(url) {
        document.getElementById("game-frame").src = url;
        document.getElementById("webgame-container").style.display = "block";
    }
    function closeWebGame() {
        document.getElementById("webgame-container").style.display = "none";
        document.getElementById("game-frame").src = "";
    }

    // ऐप कंट्रोल
    function launchApp(game) {
        let pkg = (game === 'ludo') ? "com.ludo.king" : "com.king.candycrushsaga";
        window.location.href = "intent://#Intent;package=" + pkg + ";end";
        setTimeout(() => { window.location.href = "https://play.google.com/store/apps/details?id=" + pkg; }, 1000);
    }

    // स्नेक गेम लॉजिक
    const canvas = document.getElementById("snakeCanvas");
    const ctx = canvas.getContext("2d");
    const box = 20;
    let snake, food, d, gameInterval, score;

    function startSnake() {
        document.getElementById("snake-area").style.display = "block";
        snake = [{ x: 8 * box, y: 8 * box }];
        score = 0; d = "RIGHT"; spawnFood();
        if(gameInterval) clearInterval(gameInterval);
        gameInterval = setInterval(draw, 160);
    }
    function stopGame() { document.getElementById("snake-area").style.display = "none"; clearInterval(gameInterval); }
    function spawnFood() { food = { x: Math.floor(Math.random()*14)*box, y: Math.floor(Math.random()*14)*box }; }
    function setDir(dir) { if(dir=="LEFT"&&d!="RIGHT")d="LEFT"; if(dir=="UP"&&d!="DOWN")d="UP"; if(dir=="RIGHT"&&d!="LEFT")d="RIGHT"; if(dir=="DOWN"&&d!="UP")d="DOWN"; }

    function draw() {
        ctx.fillStyle = "#111"; ctx.fillRect(0,0,300,300);
        for(let i=0; i<snake.length; i++) {
            ctx.fillStyle = (i==0) ? "#00ff00" : "#008800";
            ctx.fillRect(snake[i].x, snake[i].y, box-2, box-2);
        }
        ctx.fillStyle = "red"; ctx.fillRect(food.x, food.y, box-2, box-2);
        let sX = snake[0].x; let sY = snake[0].y;
        if(d=="LEFT") sX-=box; if(d=="UP") sY-=box; if(d=="RIGHT") sX+=box; if(d=="DOWN") sY+=box;
        if(sX==food.x && sY==food.y) { score++; document.getElementById("s-val").innerText=score; spawnFood(); } else { snake.pop(); }
        let head = {x:sX, y:sY};
        if(sX<0||sX>=300||sY<0||sY>=300||snake.some(s=>s.x==head.x&&s.y==head.y)) { stopGame(); alert("Game Over!"); }
        snake.unshift(head);
    }
</script>
</body>
</html>
