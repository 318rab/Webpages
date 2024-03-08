<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Music Player with Falling Stars</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background-color: black;
            overflow: hidden;
            color: white;
            font-size: 24px;
            text-align: center;
            padding-top: 20px;
        }
        #clock {
            position: fixed;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 1;
        }
        canvas {
            display: block;
            position: fixed;
            top: 0;
            left: 0;
            z-index: -1;
        }
        .music-player {
            text-align: center;
            color: white;
            padding: 20px;
        }
        iframe {
            width: 100%;
        }
        .bottom-image {
            position: fixed;
            bottom: 60px;
            left: 50%;
            transform: translateX(-50%);
            width: 200px;
            z-index: 1;
        }
    </style>
</head>
<body>
    <div class="music-player">
        <h2>Runnin' Game Volumes 1-6</h2>
        <iframe width="560" height="315" src="https://www.youtube.com/embed/videoseries?list=PLz57IEpLJ0nHtVCojBe1icavopU2Oa-Uf&si=GQAkEkx5lHYU3uKf" frameborder="0" allowfullscreen></iframe>
    </div>
    <canvas id="starfield"></canvas>
    <!-- Central time zone clock -->
    <div id="clock"></div>
    <!-- Inserted the provided image code here -->
    <img src="https://api.qrserver.com/v1/create-qr-code/?color=000000&amp;bgcolor=FFFFFF&amp;data=https%3A%2F%2Fyoutube.com%2F%40YFR_Rab%3Fsi%3DAe6lLoT_6Dl63Fj2&amp;qzone=1&amp;margin=0&amp;size=400x400&amp;ecc=L" alt="qr code" class="bottom-image">
    <script>
        // JavaScript code for the clock
        function updateTime() {
            const now = new Date();
            const hours = now.getHours(); // Get hours without adding 1 for the central time zone
            const minutes = now.getUTCMinutes();
            const seconds = now.getUTCSeconds();
            const timeString = `${hours < 10 ? '0' : ''}${hours}:${minutes < 10 ? '0' : ''}${minutes}:${seconds < 10 ? '0' : ''}${seconds}`;
            document.getElementById('clock').textContent = timeString;
        }
        
        setInterval(updateTime, 1000);
        
        // Falling Stars Animation
        var canvas = document.getElementById("starfield");
        var ctx = canvas.getContext("2d");

        // Set canvas size to window dimensions
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        // Generate random stars
        var stars = [];
        for (var i = 0; i < 200; i++) {
            stars.push({
                x: Math.random() * canvas.width,
                y: Math.random() * canvas.height,
                size: Math.random() * 3
            });
        }

        // Draw stars
        function draw() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.fillStyle = "white";
            for (var i = 0; i < stars.length; i++) {
                var star = stars[i];
                ctx.fillRect(star.x, star.y, star.size, star.size);
            }
        }

        // Update stars position
        function update() {
            for (var i = 0; i < stars.length; i++) {
                var star = stars[i];
                star.y += 1;
                if (star.y > canvas.height) {
                    star.y = 0;
                    star.x = Math.random() * canvas.width;
                }
            }
        }

        // Animation loop
        function loop() {
            requestAnimationFrame(loop);
            update();
            draw();
        }

        // Start animation
        loop();
    </script>
</body>
</html>