<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JOJO Game Portal - Earn Ready</title>
    <style>
        body { background: #0f0f0f; color: white; font-family: sans-serif; text-align: center; margin: 0; padding-bottom: 50px; }
        .header { background: linear-gradient(45deg, #1a1a1a, #00ff0033); padding: 20px; border-bottom: 3px solid #00ff00; }
        
        /* एडसेंस विज्ञापन स्टाइल */
        .ad-container {
            background: #1a1a1a;
            border: 1px dashed #555;
            margin: 15px auto;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #555;
            font-size: 12px;
            overflow: hidden;
        }
        .banner-ad { width: 320px; height: 50px; } /* मोबाइल बैनर */
        .square-ad { width: 300px; height: 250px; margin-top: 20px; } /* गेम ओवर होने पर */

        .section-title { color: #00ff00; margin-top: 25px; font-size: 1.2rem; text-transform: uppercase; }
        .game-list { display: flex; flex-wrap: wrap; justify-content: center; padding: 10px; }
        
        .card { 
            background: #1a1a1a; width: 110px; height: 140px; 
            margin: 10px; border-radius: 15px; border: 1px solid #333;
            display: flex; flex-direction: column; align-items: center; justify-content: center;
            cursor: pointer;
        }
        .icon { font-size: 40px; margin-bottom: 8px; }
        .play-tag { font-size: 10px; background: #00ff00; color: black; padding: 2px 8px; border-radius: 10px; margin-top: 5px; font-weight: bold; }

        /* Snake Game Screen */
        #snake-area { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: #000; z-index: 1000; overflow-y: auto; }
        canvas { background: #111; border: 3px solid #00ff00; border-radius: 10px; }
        .close-btn { background: #ff4444; color: white; border: none; padding: 12px 25px; margin: 20px; border-radius: 8px; }
        
        .controls { display: grid; grid-template-columns: repeat(3, 70px); gap: 10px; justify-content: center; margin-top: 15px; }
        .btn { width: 70px; height: 70px; background: #222; color: white; border: 2px solid #00ff00; border-radius: 50%; font-size: 28px; }
        .btn-up { grid-column: 2; }
    </style>
</head>
<body>

    <div class="header">
        <h1>JOJO गेम पोर्टल 🕹️</h1>
    </div>

    <div class="ad-container banner-ad">
        ADVERTISEMENT - TOP BANNER
        </div>

    <div class="section-title">मेरा खुद का गेम</div>
    <div class="game-list">
        <div class="card" onclick="startSnake()">
            <div class="icon">🐍</div>
            <span>Snake Game</span>
            <div class="play-tag">PLAY</div>
        </div>
    </div>

    <div class="ad-container" style="width: 90%; height: 100px; max-width: 728px;">
        ADVERTISEMENT - HORIZONTAL
    </div>

    <div class="section-title">मोबाइल ऐप्स</div>
    <div class="game-list">
        <div class="card" onclick="openApp('ludo')">
            <div class="icon">🎲</div>
            <span>Ludo King</span>
            <div class="play-tag">OPEN</div>
        </div>
        <div class="card" onclick="openApp('candy')">
            <div class="icon">🍬</div>
            <span>Candy Crush</span>
            <div class="play-tag">OPEN</div>
        </div>
    </div>

    <div id="snake-area">
        <button class="close-btn" onclick="stopGame()">X EXIT</button>
        
        <div class="ad-container banner-ad" style="margin-bottom: 10px;">
            GAME TOP AD
        </div>

        <div style="font-size: 20px; color: #00ff00;">Score: <span id="s-val">0</span> | Best: <span id="h-val">0</span></div>
        <canvas id="snakeCanvas" width="300" height="300"></canvas>
        
        <div class="controls">
            <button class="btn btn-up" onclick="setDir('UP')">↑</button>
            <button class="btn" onclick="setDir('LEFT')">←</button>
            <button class="btn" onclick="setDir('DOWN')">↓</button>
            <button class="btn" onclick="setDir('RIGHT')">→</button>
        </div>

        <div class="ad-container square-ad">
            ADVERTISEMENT - SQUARE
        </div>
    </div>

    <script>
        function openApp(game) {
            if(game === 'ludo') window.location.href = "market://details?id=com.ludo.king";
            else if(game === 'candy') window.location.href = "market://details?id=com.king.candycrushsaga";
        }

        let canvas = document.getElementById("snakeCanvas");
        let ctx = canvas.getContext("2d");
        let snake, food, d, gameInterval, score;
        const box = 20;
        let topScore = localStorage.getItem("jojoBest") || 0;
        document.getElementById("h-val").innerText = topScore;

        function startSnake() {
            document.getElementById("snake-area").style.display = "block";
            snake = [{ x: 140, y: 140 }];
            score = 0;
            document.getElementById("s-val").innerText = score;
            spawnFood();
            d = "RIGHT";
            if(gameInterval) clearInterval(gameInterval);
            gameInterval = setInterval(draw, 160);
        }

        function stopGame() {
            document.getElementById("snake-area").style.display = "none";
            clearInterval(gameInterval);
        }

        function spawnFood() {
            food = { x: Math.floor(Math.random()*14)*box, y: Math.floor(Math.random()*14)*box };
        }

        function setDir(dir) { 
            if(dir == "LEFT" && d != "RIGHT") d = "LEFT";
            if(dir == "UP" && d != "DOWN") d = "UP";
            if(dir == "RIGHT" && d != "LEFT") d = "RIGHT";
            if(dir == "DOWN" && d != "UP") d = "DOWN";
        }

        function draw() {
            ctx.fillStyle = "#111";
            ctx.fillRect(0, 0, 300, 300);
            for(let i=0; i<snake.length; i++) {
                ctx.fillStyle = (i==0) ? "#00ff00" : "#008800";
          
