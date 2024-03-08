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
            width: 100%; /* Adjusted width */
        }
        .bottom-image {
            position: fixed;
            bottom: 60px;
            left: 50%;
            transform: translateX(-50%);
            width: 200px; /* Adjust width as needed */
            z-index: 1; /* Ensure image is above canvas */
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
            const hours = now.getUTCHours() + 1; // Add 1 hour for the central time zone
            const minutes = now.getUTCMinutes();
            const seconds = now.getUTCSeconds();
            const timeString = `${hours < 10 ? '0' : ''}${hours}:${minutes < 10 ? '0' : ''}${minutes}:${seconds < 10 ? '0' : ''}${seconds}`;
            document.getElementById('clock').textContent = timeString;
        }
        
        setInterval(updateTime, 1000);
    </script>
</body>
</html>