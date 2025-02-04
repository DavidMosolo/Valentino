# Valentino
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Be My Valentine?</title>
    <style>
        body {
            text-align: center;
            font-family: Arial, sans-serif;
            background-color: #ffe6e6;
            overflow: hidden;
            margin: 0;
            transition: background-color 2s, color 2s;
        }
        #container {
            margin-top: 50px;
        }
        #bear {
            width: 200px;
        }
        .buttons {
            margin-top: 20px;
        }
        button {
            font-size: 20px;
            padding: 10px 20px;
            margin: 10px;
            cursor: pointer;
            border: none;
            border-radius: 5px;
        }
        #yes_my_love {
            background-color: #4CAF50;
            color: white;
        }
        #im_sorry_babe {
            background-color: #ff4d4d;
            color: white;
        }
        #back_button {
            background-color: #808080;
            color: white;
        }
        #confettiCanvas {
            position: absolute;
            top: 0;
            left: 0;
            pointer-events: none;
        }
    </style>
</head>
<body>
    <canvas id="confettiCanvas"></canvas>
    <div id="container">
        <h1>Will you be my Valentine? ❤️</h1>
        <img id="bear" src="https://pngimg.com/uploads/teddy_bear/teddy_bear_PNG77.png" alt="Cute Teddy Bear">
        <div class="buttons">
            <button id="yes_my_love">Yes my love</button>
            <button id="im_sorry_babe">I'm sorry babe</button>
        </div>
    </div>
    <script>
        const canvas = document.getElementById('confettiCanvas');
        const ctx = canvas.getContext('2d');
        let confettiArray = [];
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        function Confetti() {
            this.x = Math.random() * canvas.width;
            this.y = -10;
            this.size = Math.random() * 5 + 5;
            this.speedY = Math.random() * 3 + 2;
            this.speedX = Math.random() * 2 - 1;
            this.color = ['#ff0', '#f00', '#0f0', '#00f', '#f0f'][Math.floor(Math.random() * 5)];
        }

        Confetti.prototype.update = function() {
            this.x += this.speedX;
            this.y += this.speedY;

            if (this.y > canvas.height) {
                this.y = -10;
                this.x = Math.random() * canvas.width;
            }

            if (this.x > canvas.width || this.x < 0) {
                this.speedX = -this.speedX;
            }

            this.draw();
        };

        Confetti.prototype.draw = function() {
            ctx.fillStyle = this.color;
            ctx.beginPath();
            ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
            ctx.fill();
        };

        function createConfetti() {
            for (let i = 0; i < 100; i++) {
                confettiArray.push(new Confetti());
            }
        }

        function animateConfetti() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            confettiArray.forEach(confetti => confetti.update());
            requestAnimationFrame(animateConfetti);
        }

        function stopConfetti() {
            confettiArray = [];
            ctx.clearRect(0, 0, canvas.width, canvas.height);
        }

        document.getElementById('yes_my_love').addEventListener('click', function() {
            document.getElementById('container').innerHTML = '<h1>Yay! 🎉</h1><img src="https://th.bing.com/th/id/OIP.hRZXJfQJ9kvkHZw1nD96_gHaJZ?w=156&h=180&c=7&r=0&o=5&pid=1.7" style="width:200px;"><p>You made me the happiest person!</p><button id="back_button">Back</button>';
            createConfetti();
            animateConfetti();

            document.getElementById('back_button').addEventListener('click', function() {
                stopConfetti();
                document.getElementById('container').innerHTML = `<h1>Will you be my Valentine? ❤️</h1><img id="bear" src="https://pngimg.com/uploads/teddy_bear/teddy_bear_PNG77.png" alt="Cute Teddy Bear"><div class="buttons"><button id="yes_my_love">Yes my love</button><button id="im_sorry_babe">I'm sorry babe</button></div>`;
                addEventListeners();
            });
        });

        document.getElementById('im_sorry_babe').addEventListener('click', function() {
            document.body.style.transition = "background-color 2s, color 2s";
            document.body.style.backgroundColor = "black";
            document.body.style.color = "white";
            document.getElementById('container').style.transition = "color 2s";
            document.getElementById('container').style.color = "red";
            document.getElementById('container').innerHTML = '<h1>Wa nyela nfana! 🤨</h1><p>U rata kapa u sa nyake, you\'re my Valentine!</p><img src="https://th.bing.com/th/id/OIP.NrOtUbx1qq7qyTDxsU9bVgHaHD?w=206&h=196&c=7&r=0&o=5&pid=1.7" style="width:200px;"><p>There\'s no escape 😈</p><p>tlao tseye</p><button id="back_button">Back</button>';

            document.getElementById('back_button').addEventListener('click', function() {
                stopConfetti();
                document.body.style.backgroundColor = "#ffe6e6";
                document.body.style.color = "black";
                document.getElementById('container').style.color = "black";
                document.getElementById('container').innerHTML = `<h1>Will you be my Valentine? ❤️</h1><img id="bear" src="https://pngimg.com/uploads/teddy_bear/teddy_bear_PNG77.png" alt="Cute Teddy Bear"><div class="buttons"><button id="yes_my_love">Yes my love</button><button id="im_sorry_babe">I'm sorry babe</button></div>`;
                addEventListeners();
            });
        });

        function addEventListeners() {
            document.getElementById('yes_my_love').addEventListener('click', function() {
                document.getElementById('container').innerHTML = '<h1>Yay! 🎉</h1><img src="https://th.bing.com/th/id/OIP.hRZXJfQJ9kvkHZw1nD96_gHaJZ?w=156&h=180&c=7&r=0&o=5&pid=1.7" style="width:200px;"><p>You made me the happiest person!</p><button id="back_button">Back</button>';
                createConfetti();
                animateConfetti();
                document.getElementById('back_button').addEventListener('click', function() {
                    stopConfetti();
                    document.getElementById('container').innerHTML = `<h1>Will you be my Valentine? ❤️</h1><img id="bear" src="https://pngimg.com/uploads/teddy_bear/teddy_bear_PNG77.png" alt="Cute Teddy Bear"><div class="buttons"><button id="yes_my_love">Yes my love</button><button id="im_sorry_babe">I'm sorry babe</button></div>`;
                    addEventListeners();
                });
            });

            document.getElementById('im_sorry_babe').addEventListener('click', function() {
                document.body.style.transition = "background-color 2s, color 2s";
                document.body.style.backgroundColor = "black";
                document.body.style.color = "white";
                document.getElementById('container').style.transition = "color 2s";
                document.getElementById('container').style.color = "red";
                document.getElementById('container').innerHTML = '<h1>Wa nyela nfana! 🤨</h1><p>U rata kapa u sa nyake, you\'re my Valentine!</p><img src="https://th.bing.com/th/id/OIP.NrOtUbx1qq7qyTDxsU9bVgHaHD?w=206&h=196&c=7&r=0&o=5&pid=1.7" style="width:200px;"><p>There\'s no escape 😈</p><p>tlao tseye</p><button id="back_button">Back</button>';

                document.getElementById('back_button').addEventListener('click', function() {
                    stopConfetti();
                    document.body.style.backgroundColor = "#ffe6e6";
                    document.body.style.color = "black";
                    document.getElementById('container').style.color = "black";
                    document.getElementById('container').innerHTML = `<h1>Will you be my Valentine? ❤️</h1><img id="bear" src="https://pngimg.com/uploads/teddy_bear/teddy_bear_PNG77.png" alt="Cute Teddy Bear"><div class="buttons"><button id="yes_my_love">Yes my love</button><button id="im_sorry_babe">I'm sorry babe</button></div>`;
                    addEventListeners();
                });
            });
        }

        addEventListeners();
    </script>
</body>
</html>
