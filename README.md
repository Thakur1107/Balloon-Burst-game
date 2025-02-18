# Balloon-Burst-game
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Balloon Burst Game</title>
    <style>
        body {
            text-align: center;
            background-image: url('https://assets.onecompiler.app/439crk4mq/439evny2n/Symbol%203%20copy.png');
            background-size: cover;
            background-position: center;
        }
        #pump {
            display: block;
            width: 100px;
            height: 100px;
            background-image: url('https://assets.onecompiler.app/439crk4mq/439e4qkbf/Symbol%2028.png');
            background-size: cover;
            background-color: transparent;
            border: none;
            cursor: pointer;
            position: fixed;
            bottom: 20px;
            right: 20px;
        }
        #balloonContainer {
            position: fixed;
            bottom: 20px;
            width: 100%;
            display: flex;
            justify-content: center;
        }
        .balloon {
            position: absolute;
            transition: transform 0.1s linear;
        }
    </style>
</head>
<body>
    <button id="pump"></button>
    <div id="balloonContainer"></div>
    
    <script>
        const pump = document.getElementById("pump");
        const balloonContainer = document.getElementById("balloonContainer");

        const balloonImages = [
            "https://assets.onecompiler.app/439crk4mq/439cs3e38/Symbol%20100001.png",
            "https://assets.onecompiler.app/439crk4mq/439cs3e38/Symbol%20100003.png",
            "https://assets.onecompiler.app/439crk4mq/439dx8naj/Symbol%20100001.png",
            "https://assets.onecompiler.app/439crk4mq/439dx8naj/Symbol%20100002.png",
            "https://assets.onecompiler.app/439crk4mq/439dx8naj/Symbol%20100005.png",
            "https://assets.onecompiler.app/439crk4mq/439dx8naj/Symbol%20100004.png",
            "https://assets.onecompiler.app/439crk4mq/439dx8naj/Symbol%20100003.png"
        ];

        function createBalloon() {
            let img = document.createElement("img");
            img.src = balloonImages[Math.floor(Math.random() * balloonImages.length)];
            img.classList.add("balloon");
            img.style.width = "30px";
            img.style.height = "30px";
            img.style.left = ${window.innerWidth / 2}px;
            img.style.bottom = "20px";
            balloonContainer.appendChild(img);
            animateBalloon(img);
        }

        function animateBalloon(balloon) {
            let positionY = 20;
            let positionX = Math.random() * window.innerWidth;
            let size = 30;
            let velocityX = (Math.random() - 0.5) * 4;
            function move() {
                if (positionY < window.innerHeight - 100 && size < 120) {
                    positionY += 5;
                    positionX += velocityX;
                    size += 2;
                    balloon.style.bottom = ${positionY}px;
                    balloon.style.left = ${positionX}px;
                    balloon.style.width = ${size}px;
                    balloon.style.height = ${size}px;
                    requestAnimationFrame(move);
                } else {
                    balloon.remove();
                    
                }
            }
            move();
        }

        pump.addEventListener("click", createBalloon);
    </script>
</body>
</html>
