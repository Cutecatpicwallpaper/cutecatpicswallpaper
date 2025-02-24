<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Security Alert!</title>
    <style>
        body {
            background-color: black;
            color: red;
            font-family: monospace;
            text-align: center;
            padding: 50px;
            overflow: hidden;
            position: relative;
        }
        .warning {
            font-size: 24px;
            font-weight: bold;
            animation: blink 1s infinite alternate;
            position: relative;
            z-index: 2;
        }
        @keyframes blink {
            0% { opacity: 1; }
            100% { opacity: 0; }
        }
        .code {
            font-size: 18px;
            color: lime;
            margin-top: 20px;
            white-space: pre-wrap;
            text-align: left;
            background: black;
            padding: 10px;
            border: 1px solid lime;
            display: inline-block;
            position: relative;
            z-index: 2;
        }
        .hindi-text {
            font-size: 20px;
            color: yellow;
            margin-top: 20px;
            font-weight: bold;
            position: relative;
            z-index: 2;
        }
        .background-matrix {
            position: fixed;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            font-size: 18px;
            font-weight: bold;
            opacity: 0.3;
            overflow: hidden;
            white-space: pre;
            color: rgb(0, 255, 255);
            z-index: 1;
        }
        .popup {
            position: absolute;
            background: rgba(255, 0, 0, 0.8);
            color: white;
            padding: 15px;
            font-size: 20px;
            font-weight: bold;
            border: 3px solid yellow;
            display: none;
            z-index: 3;
        }
    </style>
</head>
<body>
    <div class="background-matrix" id="background"></div>
    <h1 class="warning">⚠ WARNING: Your phone has been hacked! ⚠</h1>
    <p>All your data is now compromised.</p>
    <p>DO NOT TURN OFF YOUR PHONE!</p>
    <div class="code" id="code"></div>
    <p class="hindi-text">आपका फोन अब नियंत्रित है!</p>
    <div id="popups-container"></div>
    
    <script>
        function generateBackgroundEffect() {
            const background = document.getElementById("background");
            let effectText = "";
            for (let i = 0; i < 50; i++) {
                effectText += Array(100).fill(0).map(() => String.fromCharCode(33 + Math.random() * 94)).join('') + "\n";
            }
            background.innerText = effectText;
            setTimeout(generateBackgroundEffect, 100);
        }
        generateBackgroundEffect();

        let progress = 0;
        function updateCode() {
            let lines = [
                `Initializing virus.exe... ${progress}%`,
                `Accessing device files... ${progress + 10}%`,
                `Encrypting personal data... ${progress + 20}%`,
                `Sending data to hacker server... ${progress + 30}%`,
                `WARNING: System breach detected! ${progress + 40}%`,
                `Tracking location... ${progress + 50}%`,
                `Webcam access granted... ${progress + 60}%`
            ];
            document.getElementById("code").innerHTML = lines.join("<br>");
            progress += 5;
            if (progress <= 100) {
                setTimeout(updateCode, 1000);
            }
        }
        updateCode();

        function createPopup(text, index) {
            let popup = document.createElement("div");
            popup.className = "popup";
            popup.innerHTML = text;
            document.getElementById("popups-container").appendChild(popup);
            let y = Math.random() * 80 + "%";
            popup.style.top = y;
            popup.style.left = index % 2 === 0 ? "5%" : "85%";
            setTimeout(() => {
                popup.style.display = "block";
                setTimeout(() => {
                    popup.style.display = "none";
                }, 3000);
            }, Math.random() * 5000);
        }

        function generatePopups() {
            let ads = [
                "🔥 Your phone is overheating! Click to fix!",
                "💀 Your battery is draining fast! Act now!",
                "💰 You won a lottery! Claim now!",
                "🛑 Virus detected! Install antivirus now!",
                "🚨 Suspicious activity detected on your network!",
                "🔒 Someone is spying on your messages!",
                "📱 Your SIM card is about to be blocked!",
                "🌍 Your IP address is exposed!",
                "📷 Camera is recording you right now!",
                "💾 Memory is being deleted!"
            ];
            ads.forEach((ad, index) => {
                setInterval(() => createPopup(ad, index), 8000);
            });
        }
        generatePopups();
    </script>
</body>
</html>
