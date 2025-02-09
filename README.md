<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Be My Valentine?</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #ffccd5;
            font-family: Arial, sans-serif;
            text-align: center;
            overflow: hidden;
            transition: background 3s ease-in-out, color 3s ease-in-out;
        }
        .container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }
        h1 {
            color: #e63946;
        }
        .buttons {
            margin-top: 20px;
        }
        button {
            padding: 10px 20px;
            font-size: 18px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin: 5px;
        }
        .yes {
            background-color: #ff4d6d;
            color: white;
        }
        .no {
            background-color: #6c757d;
            color: white;
        }
        .back {
            display: none;
            background-color: #007bff;
            color: white;
        }
        .confetti {
            position: fixed;
            width: 10px;
            height: 10px;
            background-color: red;
            opacity: 0.7;
            animation: fall 3s linear infinite;
        }
        @keyframes fall {
            0% { transform: translateY(-100vh) rotate(0deg); }
            100% { transform: translateY(100vh) rotate(360deg); }
        }
        .message {
            display: none;
            text-align: center;
            font-size: 2rem;
            color: red;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 80%;
        }
        .scary-image {
            width: 150px; /* Reduced size */
            height: auto;
        }
        .teddy-image {
            width: 200px; /* Teddy bear image size */
            height: auto;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="container" id="mainContainer">
        <h1>Will you be my Valentine? ❤️</h1>
        <div class="buttons">
            <button class="yes" onclick="showLove()">Yes</button>
            <button class="no" onclick="showRejection()">No</button>
        </div>
    </div>
    <div class="message" id="loveMessage">
        <p>You made my heart happy! ❤️🥰</p>
        <img class="teddy-image" src="https://th.bing.com/th/id/OIP.hLfdQpjb4VqpWozzbiXe7gHaEK?w=1920&h=1080&rs=1&pid=ImgDetMain" alt="Teddy Bear">
        <button class="back" onclick="goBack()">Back</button>
    </div>
    <div class="message" id="rejection">
        <p>wa nyela nfana, u rata or u sa rate you are my valentine</p>
        <p>tla u tseye</p>
        <img class="scary-image" src="https://static.vecteezy.com/system/resources/previews/003/734/971/original/evil-teddy-bear-vector.jpg" alt="Scary Valentine Image">
        <button class="back" onclick="goBack()">Back</button>
    </div>
    <script>
        function showLove() {
            createConfetti();
            document.querySelector(".container").style.display = "none";
            document.getElementById("loveMessage").style.display = "block";
            document.querySelector(".back").style.display = "block";
        }
        function createConfetti() {
            for (let i = 0; i < 100; i++) {
                let confetti = document.createElement("div");
                confetti.classList.add("confetti");
                confetti.style.left = Math.random() * window.innerWidth + "px";
                confetti.style.backgroundColor = `hsl(${Math.random() * 360}, 100%, 70%)`;
                confetti.style.animationDuration = (Math.random() * 2 + 1) + "s";
                document.body.appendChild(confetti);
            }
        }
        function showRejection() {
            document.body.style.backgroundColor = "black";
            document.body.style.color = "red";
            document.querySelector(".container").style.display = "none";
            document.getElementById("rejection").style.display = "block";
            document.querySelector(".back").style.display = "block";
        }
        function goBack() {
            document.body.style.backgroundColor = "#ffccd5";
            document.body.style.color = "black";
            document.getElementById("loveMessage").style.display = "none";
            document.getElementById("rejection").style.display = "none";
            document.querySelector(".container").style.display = "block";
            document.querySelector(".back").style.display = "none";
            let confettiElements = document.querySelectorAll(".confetti");
            confettiElements.forEach(element => element.remove());
        }
    </script>
</body>
</html>
