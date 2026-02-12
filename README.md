<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JOJO गेम पोर्टल - 100+ फ्री गेम्स</title>
    <style>
        body { background: #0a0a0a; color: white; font-family: 'Segoe UI', sans-serif; text-align: center; margin: 0; }
        .header { background: linear-gradient(45deg, #111, #00ff0022); padding: 40px 20px; border-bottom: 2px solid #00ff00; }
        
        .game-grid { 
            display: grid; grid-template-columns: repeat(auto-fill, minmax(140px, 1fr)); 
            gap: 15px; padding: 20px; max-width: 1200px; margin: 0 auto; min-height: 400px;
        }
        
        .game-card { 
            background: #1a1a1a; padding: 15px; border-radius: 15px; 
            border: 1px solid #333; cursor: pointer; transition: 0.3s ease;
        }
        .game-card:hover { border-color: #00ff00; transform: scale(1.05); }
        .game-icon { font-size: 40px; margin-bottom: 10px; display: block; }
        .game-name { font-size: 14px; font-weight: bold; }

        /* Footer Section */
        footer { background: #111; padding: 40px 20px; border-top: 1px solid #333; margin-top: 50px; }
        .footer-links { margin-bottom: 20px; }
        .footer-links a { color: #888; text-decoration: none; margin: 0 15px; font-size: 14px; transition: 0.3s; }
        .footer-links a:hover { color: #00ff00; }
        .contact-email { color: #00ff00; font-weight: bold; text-decoration: none; }
        .copyright { font-size: 12px; color: #555; margin-top: 20px; }

        /* Modal (Privacy/About के लिए) */
        #modal-overlay { 
            display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; 
            background: rgba(0,0,0,0.9); z-index: 20000; overflow-y: auto; padding: 40px 20px;
        }
        .modal-content { background: #1a1a1a; max-width: 700px; margin: 0 auto; padding: 30px; border-radius: 15px; text-align: left; line-height: 1.6; border: 1px solid #444; }
        .close-modal { float: right; cursor: pointer; color: #ff4444; font-weight: bold; }

        /* गेम प्लेयर */
        #player-window { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: black; z-index: 10000; }
        #game-iframe { width: 100%; height: calc(100% - 50px); border: none; }
        .nav-bar { height: 50px; background: #111; display: flex; justify-content: space-between; align-items: center; padding: 0 20px; border-bottom: 1px solid #00ff00; }
    </style>
</head>
<body>

    <div class="header">
        <h1>JOJO गेम पोर्टल 🕹️</h1>
        <p>बिना डाउनलोड किए सबसे बेहतरीन गेम्स</p>
    </div>

    <div class="game-grid" id="game-container"></div>

    <footer>
        <div class="footer-links">
            <a href="javascript:void(0)" onclick="showInfo('about')">About Us</a>
            <a href="javascript:void(0)" onclick="showInfo('privacy')">Privacy Policy</a>
            <a href="javascript:void(0)" onclick="showInfo('contact')">Contact Us</a>
        </div>
        <p>संपर्क करें: <a href="mailto:prashantsingh9182822@gmail.com" class="contact-email">prashantsingh9182822@gmail.com</a></p>
        <div class="copyright">© 2026 JOJO Gaming Portal - All Rights Reserved</div>
    </footer>

    <div id="modal-overlay">
        <div class="modal-content">
            <span class="close-modal" onclick="closeModal()">✕ बंद करें</span>
            <div id="modal-body"></div>
        </div>
    </div>

    <div id="player-window">
        <div class="nav-bar">
            <span id="playing-title" style="color:#00ff00;">Loading...</span>
            <button onclick="exitGame()" style="background:#ff4444; color:white; border:none; padding:8px; border-radius:5px; cursor:pointer;">Exit X</button>
        </div>
        <iframe id="game-iframe" src=""></iframe>
    </div>

    <script>
        const games = [
            { name: "Subway Surfers", icon: "🏃", url: "https://www.gamepix.com/live/subway-surfers" },
            { name: "Ludo Legend", icon: "🎲", url: "https://www.gamepix.com/live/ludo-legend" },
            { name: "Moto X3M", icon: "🏍️", url: "https://www.gamepix.com/live/moto-x3m" },
            { name: "Temple Run 2", icon: "🗿", url: "https://www.gamepix.com/live/temple-run-2" },
            { name: "Candy Riddles", icon: "🍬", url: "https://www.gamepix.com/live/candy-riddles" }
        ];

        const container = document.getElementById("game-container");
        games.forEach(game => {
            const card = document.createElement("div");
            card.className = "game-card";
            card.onclick = () => {
                document.getElementById("game-iframe").src = game.url;
                document.getElementById("player-window").style.display = "block";
                document.getElementById("playing-title").innerText = game.name;
            };
            card.innerHTML = `<span class="game-icon">${game.icon}</span><span class="game-name">${game.name}</span>`;
            container.appendChild(card);
        });

        function exitGame() {
            document.getElementById("player-window").style.display = "none";
            document.getElementById("game-iframe").src = "";
        }

        function showInfo(type) {
            const modal = document.getElementById("modal-overlay");
            const body = document.getElementById("modal-body");
            modal.style.display = "block";
            
            if(type === 'about') {
                body.innerHTML = "<h2>About Us</h2><p>JOJO गेम पोर्टल एक फ्री गेमिंग प्लेटफार्म है जहाँ आप बिना डाउनलोड किए टॉप गेम्स खेल सकते हैं। हमारा लक्ष्य गेमिंग को आसान और सुलभ बनाना है।</p>";
            } else if(type === 'privacy') {
                body.innerHTML = "<h2>Privacy Policy</h2><p>हम आपकी गोपनीयता का सम्मान करते हैं। यह साइट कुकीज़ का उपयोग अनुभव सुधारने के लिए करती है। हम आपका व्यक्तिगत डेटा बिना अनुमति के किसी तीसरे पक्ष को साझा नहीं करते।</p>";
            } else if(type === 'contact') {
                body.innerHTML = "<h2>Contact Us</h2><p>किसी भी सुझाव या शिकायत के लिए हमें ईमेल करें:<br><br><b>Email:</b> prashantsingh9182822@gmail.com</p>";
            }
        }

        function closeModal() { document.getElementById("modal-overlay").style.display = "none"; }
    </script>
</body>
</html>
