<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JOJO गेम पोर्टल - Play Free Online Games</title>
    
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-XXXXXXXXXXXXXXXX" crossorigin="anonymous"></script>

    <style>
        body { background: #0f0f0f; color: white; font-family: 'Segoe UI', sans-serif; text-align: center; margin: 0; padding-bottom: 50px; }
        .header { background: linear-gradient(45deg, #1a1a1a, #00ff0033); padding: 30px; border-bottom: 3px solid #00ff00; }
        
        /* एडसेंस विज्ञापन के लिए जगह */
        .ad-space { background: #1a1a1a; margin: 20px auto; width: 90%; max-width: 728px; min-height: 90px; border: 1px dashed #444; display: flex; align-items: center; justify-content: center; color: #555; font-size: 14px; }

        .section-title { color: #00ff00; margin-top: 30px; font-size: 1.2rem; text-transform: uppercase; letter-spacing: 2px; font-weight: bold; }
        .game-list { display: flex; flex-wrap: wrap; justify-content: center; padding: 20px; gap: 20px; }
        
        .card { 
            background: #1a1a1a; width: 120px; padding: 20px 10px;
            border-radius: 20px; border: 1px solid #333;
            display: flex; flex-direction: column; align-items: center; cursor: pointer; transition: 0.4s;
        }
        .card:hover { border-color: #00ff00; transform: translateY(-10px); box-shadow: 0 10px 20px rgba(0,255,0,0.2); }
        .icon { font-size: 45px; margin-bottom: 10px; }
        .game-name { font-size: 14px; font-weight: bold; margin-bottom: 8px; }
        .play-tag { font-size: 10px; background: #00ff00; color: black; padding: 4px 10px; border-radius: 12px; font-weight: bold; }

        /* कंटेंट एरिया (AdSense Approval के लिए जरूरी) */
        .content-area { text-align: left; max-width: 800px; margin: 30px auto; padding: 25px; background: #151515; border-radius: 15px; color: #bbb; line-height: 1.8; border: 1px solid #222; }
        .content-area h2 { color: #00ff00; }

        /* गेम विंडो */
        #webgame-container { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: #000; z-index: 2000; }
        #game-frame { width: 100%; height: calc(100% - 60px); border: none; }
        .close-bar { height: 60px; background: #222; display: flex; justify-content: space-between; align-items: center; padding: 0 25px; border-bottom: 2px solid #ff4444; }

        footer { margin-top: 60px; padding: 40px 20px; background: #111; border-top: 1px solid #333; font-size: 14px; color: #888; }
        footer a { color: #00ff00; text-decoration: none; margin: 0 15px; font-weight: 600; }
    </style>
</head>
<body>

    <div class="header">
        <h1>JOJO गेम पोर्टल 🕹️</h1>
        <p style="color: #888;">बिना डाउनलोड किए फ्री ऑनलाइन गेम्स खेलें</p>
    </div>

    <div class="ad-space">ADVERTISEMENT</div>

    <div class="content-area">
        <h2>JOJO गेम पोर्टल पर आपका स्वागत है</h2>
        <p>क्या आप बिना किसी ऐप को डाउनलोड किए सीधे अपने ब्राउज़र पर गेम खेलना चाहते हैं? <b>JOJO गेम पोर्टल</b> आपको बेहतरीन गेमिंग अनुभव प्रदान करता है। यहाँ आप <b>Ludo, Pac-Man</b> और कई मजेदार गेम्स मुफ्त में खेल सकते हैं। ये सभी गेम्स मोबाइल और कंप्यूटर पर बहुत स्मूथ चलते हैं।</p>
    </div>

    <div class="section-title">🌐 टॉप ऑनलाइन गेम्स</div>
    <div class="game-list" id="dynamic-game-list">
        </div>

    <div class="ad-space">ADVERTISEMENT</div>

    <div class="section-title">🐍 स्पेशल गेम्स</div>
    <div class="game-list">
        <div class="card" onclick="alert('Snake Game Starting...')">
            <div class="icon">🐍</div>
            <span class="game-name">Snake Lite</span>
            <div class="play-tag">PLAY NOW</div>
        </div>
    </div>

        <footer>
        <p>&copy; 2026 JOJO Gaming Portal - All Rights Reserved</p>
        
        <p>संपर्क करें: <a href="mailto:prashantsingh9182822@gmail.com" style="color: #00ff00; margin: 0;">prashantsingh9182822@gmail.com</a></p>

        <div style="margin-top: 15px;">
            <a href="about.html">About Us</a>
            <a href="privacy.html">Privacy Policy</a>
            <a href="contact.html">Contact Us</a>
        </div>
    </footer>


    <div id="webgame-container">
        <div class="close-bar">
            <span id="current-game-title" style="color:#00ff00; font-weight:bold;">GAME LOADING...</span>
            <button onclick="closeWebGame()" style="background:#ff4444; color:white; border:none; padding:10px 20px; border-radius:8px; font-weight:bold; cursor:pointer;">✕ EXIT</button>
        </div>
        <iframe id="game-frame" src="" allow="autoplay; fullscreen; keyboard" allowfullscreen="true"></iframe>

    </div>

<script>
    // अपडेटेड गेम लिस्ट - जो आपकी साइट के अंदर 100% चलेगी
const myGames = [
    { 
        name: "Subway Surfers", 
        icon: "🏃", 
        // पोकी की जगह गेमपिक्स का लिंक, जो ब्लॉक नहीं होता
        url: "https://www.gamepix.com/live/subway-surfers" 
    },
    { 
        name: "Ludo Legend", 
        icon: "🎲", 
        url: "https://www.gamepix.com/live/ludo-legend" 
    },
    { 
        name: "Candy Riddle", 
        icon: "🍬", 
        url: "https://www.gamepix.com/live/candy-riddles" 
    },
    { 
        name: "Moto X3M", 
        icon: "🏍️", 
        url: "https://www.gamepix.com/live/moto-x3m" 
    },
    { 
        name: "Pac-Man", 
        icon: "🍕", 
        url: "https://www.google.com/logos/2010/pacman10-i.html" 
    }
];

// बेहतर डायरेक्ट ओपन फंक्शन
function openWebGame(url, title) {
    const container = document.getElementById("webgame-container");
    const frame = document.getElementById("game-frame");
    const titleText = document.getElementById("current-game-title");
    
    // स्क्रीन को साफ़ करें और लोडिंग दिखाएं
    titleText.innerText = "लोड हो रहा है: " + title + "...";
    frame.src = url; 
    
    // गेम विंडो खोलें
    container.style.display = "block";
    document.body.style.overflow = "hidden";

    // जब गेम पूरी तरह लोड हो जाए
    frame.onload = function() {
        titleText.innerText = title;
    };
}
    }

    function openWebGame(url, title) {
        document.getElementById("current-game-title").innerText = title;
        document.getElementById("game-frame").src = url;
        document.getElementById("webgame-container").style.display = "block";
        document.body.style.overflow = "hidden";
    }

    function closeWebGame() {
        document.getElementById("webgame-container").style.display = "none";
        document.getElementById("game-frame").src = "";
        document.body.style.overflow = "auto";
    }

    window.onload = loadGames;
</script>

</body>
</html>
