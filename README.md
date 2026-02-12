<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JOJO गेम पोर्टल - Play & Earn</title>
    <style>
        body { background: #0f0f0f; color: white; font-family: sans-serif; text-align: center; margin: 0; padding-bottom: 50px; }
        .header { background: linear-gradient(45deg, #1a1a1a, #00ff0033); padding: 20px; border-bottom: 3px solid #00ff00; }
        
        /* एडसेंस विज्ञापन स्लॉट */
        .ad-space { background: #1a1a1a; margin: 15px auto; width: 90%; max-width: 728px; min-height: 90px; border: 1px dashed #444; display: flex; align-items: center; justify-content: center; color: #555; font-size: 12px; }

        .section-title { color: #00ff00; margin-top: 25px; font-size: 1.1rem; text-transform: uppercase; letter-spacing: 1px; }
        .game-list { display: flex; flex-wrap: wrap; justify-content: center; padding: 10px; gap: 15px; }
        
        .card { 
            background: #1a1a1a; width: 105px; padding: 15px 5px;
            border-radius: 15px; border: 1px solid #333;
            display: flex; flex-direction: column; align-items: center; cursor: pointer; transition: 0.3s;
        }
        .card:hover { border-color: #00ff00; transform: translateY(-5px); }
        .icon { font-size: 40px; margin-bottom: 8px; }
        .game-name { font-size: 12px; font-weight: bold; margin-bottom: 5px; }
        .play-tag { font-size: 9px; background: #00ff00; color: black; padding: 3px 8px; border-radius: 10px; font-weight: bold; }
        .web-tag { background: #00dbff; }

        /* कंटेंट एरिया (AdSense अप्रूवल के लिए) */
        .content-area { text-align: left; max-width: 700px; margin: 20px auto; padding: 0 20px; color: #bbb; line-height: 1.6; }

        /* फुल स्क्रीन गेम विंडो */
        #webgame-container { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: #000; z-index: 2000; }
        #game-frame { width: 100%; height: calc(100% - 60px); border: none; }
        .close-bar { height: 60px; background: #222; display: flex; justify-content: space-between; align-items: center; padding: 0 20px; border-bottom: 2px solid #ff4444; }

        footer { margin-top: 40px; padding: 20px; border-top: 1px solid #333; font-size: 13px; color: #666; }
        footer a { color: #00ff00; text-decoration: none; margin: 0 10px; }
    </style>
</head>
<body>

    <div class="header">
        <h1>JOJO गेम पोर्टल 🕹️</h1>
    </div>

    <div class="ad-space">ADVERTISEMENT (ADSENSE CODE)</div>

    <div class="content-area">
        <h2 style="color:#00ff00">बिना डाउनलोड किए गेम खेलें</h2>
        <p>JOJO पोर्टल पर आपका स्वागत है। यहाँ आप दुनिया के मशहूर गेम्स मुफ्त में खेल सकते हैं।</p>
    </div>

    <div class="section-title">🌐 ऑनलाइन गेम्स</div>
    <div class="game-list" id="dynamic-game-list"></div>

    <div class="ad-space">ADVERTISEMENT (ADSENSE CODE)</div>

    <div class="section-title">🐍 स्पेशल गेम्स</div>
    <div class="game-list">
        <div class="card" onclick="alert('Snake Game Start!')">
            <div class="icon">🐍</div>
            <span class="game-name">Snake Lite</span>
            <div class="play-tag">PLAY NOW</div>
        </div>
    </div>

    <footer>
        <p>&copy; 2026 JOJO Gaming Portal</p>
        <a href="#">About Us</a> | <a href="#">Privacy Policy</a> | <a href="#">Contact Us</a>
    </footer>

    <div id="webgame-container">
        <div class="close-bar">
            <span id="current-game-title" style="color:#00ff00; font-weight:bold;">LOADING...</span>
            <button onclick="closeWebGame()" style="background:#ff4444; color:white; border:none; padding:8px 15px; border-radius:5px; font-weight:bold; cursor:pointer;">✕ EXIT</button>
        </div>
        <iframe id="game-frame" src=""></iframe>
    </div>

<script>
    // --- यहाँ से आप नए गेम जोड़ सकते हैं ---
    const myGames = [
        { name: "Ludo Legend", icon: "🎲", url: "https://www.gamepix.com/live/ludo-legend" },
        { name: "Candy Riddle", icon: "🍬", url: "https://www.gamepix.com/live/candy-riddles" },
        { name: "Pac-Man", icon: "🍕", url: "https://www.google.com/logos/2010/pacman10-i.html" },
        { name: "Bubble Shooter", icon: "🔵", url: "https://www.gamepix.com/live/bubble-shooter" } // नया गेम जोड़ना आसान है!
    ];

    // गेम्स को लोड करने का फंक्शन
    function loadGames() {
        const list = document.getElementById("dynamic-game-list");
        myGames.forEach(game => {
            const gameCard = `
                <div class="card" onclick="openWebGame('${game.url}', '${game.name}')">
                    <div class="icon">${game.icon}</div>
                    <span class="game-name">${game.name}</span>
                    <div class="play-tag web-tag">WEB PLAY</div>
                </div>`;
            list.innerHTML += gameCard;
        });
    }

    function openWebGame(url, title) {
        document.getElementById("current-game-title").innerText = title;
        document.getElementById("game-frame").src = url;
        document.getElementById("webgame-container").style.display = "block";
    }

    function closeWebGame() {
        document.getElementById("webgame-container").style.display = "none";
        document.getElementById("game-frame").src = "";
    }

    // पेज खुलते ही गेम्स लोड करें
    window.onload = loadGames;
</script>

</body>
</html>
