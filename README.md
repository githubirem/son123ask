    <!DOCTYPE html>
      <html lang="en">

    <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Knowledge Storm</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #fff;
            color: #333;
            margin: 0;
            padding: 0;
        }
        
        header {
            background-color: #FFC0CB;
            color: #fff;
            padding: 1em 0;
            text-align: center;
        }
        
        nav {
            background-color: #fff;
            border-bottom: 2px solid #FFC0CB;
            padding: 1em 0;
            text-align: center;
        }
        
        nav a {
            color: #FFC0CB;
            margin: 0 15px;
            text-decoration: none;
            font-weight: bold;
        }
        
        .container {
            padding: 2em;
        }
        
        footer {
            background-color: #FFC0CB;
            color: #fff;
            text-align: center;
            padding: 1em 0;
            position: fixed;
            width: 100%;
            bottom: 0;
        }
        
        .game {
            background-color: rgba(255, 255, 255, 0.98);
            border: 2px solid #FFC0CB;
            border-radius: 5px;
            padding: 1em;
            margin: 2em 0;
        }
        
        .game h2 {
            color: #FFC0CB;
        }
        
        .question {
            margin-bottom: 1em;
        }
        
        .options {
            list-style-type: none;
            padding: 0;
        }
        
        .options li {
            margin-bottom: 0.5em;
        }
        
        .options button {
            background-color: #FFC0CB;
            color: #fff;
            border: none;
            padding: 10px;
            width: 100%;
            cursor: pointer;
            border-radius: 5px;
        }
        
        .options button:hover {
            background-color: #69e1ff;
        }
        
        #result {
            margin-top: 1em;
            font-weight: bold;
        }
        
        #feedback {
            text-align: center;
            margin-top: 1em;
        }
        
        #feedback img {
            max-width: 100px;
        }
        
        #timer {
            font-size: 1.5em;
            text-align: center;
            margin-top: 1em;
        }
        
        .progress-bar {
            display: flex;
            margin: 1em 0;
        }
        
        .progress-bar .bar-segment {
            flex: 1;
            height: 20px;
            margin: 0 2px;
            background-color: #ccc;
            border-radius: 3px;
        }
        
        .progress-bar .bar-segment.correct {
            background-color: #4CAF50;
        }
        
        .progress-bar .bar-segment.incorrect {
            background-color: #f44336;
        }
    </style>
    </head>

      <body>

    <header>
        <h1>Knowledge Storm</h1>
    </header>

    <nav>
        <a href="#home">Home</a>
        <a href="#about">About Me</a>
        <a href="#projects">My Projects</a>
        <a href="#contact">Contact</a>
    </nav>

    <div class="container" id="home">
        <section>
            <h2>Welcome!</h2>
            <p>On this webpage, you will find a game consisting of 25 questions. These questions have been prepared by Irem Erendor. Test your knowledge and have fun by answering the questions!</p>
        </section>

        <section id="about">
            <h2>About Me</h2>
            <p>Hello, I am Irem Erendor, the creator of the game "Knowledge Storm ." I developed this game using C++ and I am happy to share it with you here.</p>
        </section>

        <section id="projects">
            <h2>My Projects</h2>
            <div class="game">
                <h2>25-Question Game</h2>
                <div id="category-selection">
                    <label for="category">Choose a category:</label>
                    <select id="category" onchange="loadQuestion()">
                    <option value="mixed">Mixed</option>
                    <option value="cars">Cars</option>
                    <option value="sport">Sport</option>
                    <option value="social">Social Knowledge</option>
                </select>
                </div>
                <div id="game-container">
                    <!-- The game will load here -->
                </div>
                <div class="progress-bar" id="progress-bar"></div>
                <div id="result"></div>
                <div id="feedback"></div>
                <div id="timer">15</div>
            </div>
        </section>

        <section id="contact">
            <h2>Contact</h2>
            <p>To get in touch with me, <a href="mailto:irem.erendor@bilgiedu.net">send an email</a>.</p>
        </section>
    </div>

    <footer>
        <p>&copy; 2024 Know and Continue. All rights reserved. Created for the GAME 310 final project, not for commercial use.</p>
    </footer>

    <script>
        const questions = {
            mixed: [{
                question: "What is the capital of France?",
                options: ["Paris", "London", "Berlin", "Madrid"],
                answer: 0
            }, {
                question: "What is the speed of light in m/s?",
                options: ["299792458", "150000000", "300000000", "100000000"],
                answer: 0
            }, {
                question: "What is 2 + 2?",
                options: ["3", "4", "5", "6"],
                answer: 1
            }, {
                question: "What is the largest planet in our solar system?",
                options: ["Earth", "Mars", "Jupiter", "Saturn"],
                answer: 2
            }, {
                question: "In which year did the Titanic sink?",
                options: ["1912", "1914", "1916", "1918"],
                answer: 0
            }, {
                question: "Who wrote 'To Kill a Mockingbird'?",
                options: ["Harper Lee", "Mark Twain", "Ernest Hemingway", "F. Scott Fitzgerald"],
                answer: 0
            }, {
                question: "What is the smallest prime number?",
                options: ["1", "2", "3", "5"],
                answer: 1
            }, {
                question: "What is the chemical symbol for water?",
                options: ["HO", "H2O", "O2", "CO2"],
                answer: 1
            }, {
                question: "What is the square root of 64?",
                options: ["6", "7", "8", "9"],
                answer: 2
            }, {
                question: "Who painted the Mona Lisa?",
                options: ["Vincent van Gogh", "Pablo Picasso", "Leonardo da Vinci", "Claude Monet"],
                answer: 2
            }, {
                question: "What is the fastest land animal?",
                options: ["Lion", "Tiger", "Cheetah", "Leopard"],
                answer: 2
            }, {
                question: "What is the largest mammal?",
                options: ["Elephant", "Blue Whale", "Giraffe", "Orca"],
                answer: 1
            }, {
                question: "What element does 'O' represent on the periodic table?",
                options: ["Osmium", "Oxygen", "Oganesson", "Oxonium"],
                answer: 1
            }, {
                question: "Who discovered penicillin?",
                options: ["Marie Curie", "Alexander Fleming", "Isaac Newton", "Albert Einstein"],
                answer: 1
            }, {
                question: "What is the capital of Japan?",
                options: ["Beijing", "Seoul", "Bangkok", "Tokyo"],
                answer: 3
            }, {
                question: "How many continents are there?",
                options: ["5", "6", "7", "8"],
                answer: 2
            }, {
                question: "What is the boiling point of water in Celsius?",
                options: ["90", "100", "110", "120"],
                answer: 1
            }, {
                question: "Who wrote 'Romeo and Juliet'?",
                options: ["Charles Dickens", "William Shakespeare", "Jane Austen", "Mark Twain"],
                answer: 1
            }, {
                question: "What is the hardest natural substance?",
                options: ["Gold", "Iron", "Diamond", "Silver"],
                answer: 2
            }, {
                question: "What is the currency of the United Kingdom?",
                options: ["Euro", "Dollar", "Pound", "Franc"],
                answer: 2
            }, {
                question: "Which planet is known as the Red Planet?",
                options: ["Earth", "Mars", "Jupiter", "Saturn"],
                answer: 1
            }, {
                question: "Who was the first President of the United States?",
                options: ["Abraham Lincoln", "Thomas Jefferson", "John Adams", "George Washington"],
                answer: 3
            }, {
                question: "What is the longest river in the world?",
                options: ["Amazon", "Nile", "Mississippi", "Yangtze"],
                answer: 1
            }, {
                question: "In which year did World War II end?",
                options: ["1942", "1943", "1945", "1946"],
                answer: 2
            }, {
                question: "What is the capital of Italy?",
                options: ["Venice", "Florence", "Milan", "Rome"],
                answer: 3
            }],
            cars: [{
                question: "Which part of a vehicle's engine carries out the combustion process?",
                options: ["Cylinder", "Gearbox", "Differential", "Carburetor"],
                answer: 0
            }, {
                question: "Which car company owns the luxury brand 'Bentley'?",
                options: ["BMW", "Audi", "Volkswagen", "Mercedes-Benz"],
                answer: 2
            }, {
                question: "Which car model is known as the first mass-produced car?",
                options: ["Model T", "Beetle", "Civic", "Corolla"],
                answer: 0
            }, {
                question: "What is the name of the first car ever made?",
                options: ["Model T", "Benz Patent-Motorwagen", "Rolls-Royce", "Ferrari 250"],
                answer: 1
            }, {
                question: "What does 'SUV' stand for?",
                options: ["Special Utility Vehicle", "Sport Utility Vehicle", "Standard Utility Vehicle", "Super Utility Vehicle"],
                answer: 1
            }, {
                question: "Which car manufacturer produces the 'Mustang'?",
                options: ["Chevrolet", "Dodge", "Ford", "Toyota"],
                answer: 2
            }, {
                question: "What is the name of Tesla's fully electric sedan?",
                options: ["Model X", "Model Y", "Model 3", "Model S"],
                answer: 3
            }, {
                question: "Which car brand uses a prancing horse as its logo?",
                options: ["Porsche", "Lamborghini", "Ferrari", "Maserati"],
                answer: 2
            }, {
                question: "What is the top speed of the Bugatti Chiron?",
                options: ["300 km/h", "420 km/h", "490 km/h", "520 km/h"],
                answer: 2
            }, {
                question: "Which company manufactures the 'Civic' model?",
                options: ["Toyota", "Nissan", "Honda", "Mazda"],
                answer: 2
            }, {
                question: "In which country is the headquarters of the car manufacturer BMW located?",
                options: ["Germany", "France", "Italy", "United States"],
                answer: 0
            }],
            sport: [{
                question: "Which sport is basketball associated with?",
                options: ["Football", "Basketball", "Volleyball", "Tennis"],
                answer: 1
            }, {
                question: "How many players are there in each football team?",
                options: ["9", "10", "11", "12"],
                answer: 2
            }, {
                question: "Wimbledon is associated with which sport?",
                options: ["Golf", "Basketball", "Tennis", "Swimming"],
                answer: 2
            }, {
                question: "F1 races are a part of which sport?",
                options: ["Athletics", "Formula 1", "Cycling", "Sailing"],
                answer: 1
            }, {
                question: "Which country won the 2018 FIFA World Cup?",
                options: ["Germany", "Brazil", "France", "Croatia"],
                answer: 2
            }, {
                question: "Which NBA team has won the most championships?",
                options: ["Los Angeles Lakers", "Boston Celtics", "Chicago Bulls", "Golden State Warriors"],
                answer: 1
            }, {
                question: "How often are the Olympic Games held?",
                options: ["Every 2 years", "Every 3 years", "Every 4 years", "Every 5 years"],
                answer: 2
            }, {
                question: "The term 'sprint' is associated with which sport?",
                options: ["Swimming", "Athletics", "Football", "Basketball"],
                answer: 1
            }, {
                question: "What is a 'Grand Slam' in tennis?",
                options: ["The highest score in a match", "Winning all four major tennis tournaments in a single year", "Winning a single tournament", "The best player award"],
                answer: 1
            }, {
                question: "Which football club is Lionel Messi most associated with?",
                options: ["Real Madrid", "Barcelona", "Manchester United", "Paris Saint-Germain"],
                answer: 1
            }, {
                question: "In which sport is Michael Jordan famous?",
                options: ["Football", "Tennis", "Basketball", "Athletics"],
                answer: 2
            }, {
                question: "Tour de France is associated with which sport?",
                options: ["Running", "Cycling", "Skiing", "Motor sports"],
                answer: 1
            }, {
                question: "In which year were the first modern Olympic Games held?",
                options: ["1896", "1900", "1912", "1920"],
                answer: 0
            }, {
                question: "In football, what is a 'hat-trick'?",
                options: ["Making three assists", "Scoring three goals", "Receiving three yellow cards", "Playing three matches"],
                answer: 1
            }, {
                question: "In basketball, what is it called when a player carries the ball while dribbling?",
                options: ["Double dribble", "Travel", "Carry", "Block"],
                answer: 2
            }],
            social: {
                easy: [{
                    question: "What is the abbreviation for the World Health Organization?",
                    options: ["WHO", "UNICEF", "NATO", "UNESCO"],
                    answer: 0
                }, {
                    question: "Which one is the largest island country in the world?",
                    options: ["Japan", "United Kingdom", "Indonesia", "Australia"],
                    answer: 3
                }, {
                    question: "Which planet is the largest in the Solar System?",
                    options: ["Mars", "Venus", "Jupiter", "Uranus"],
                    answer: 2
                }, {
                    question: "Which country's flag features a white mountain?",
                    options: ["Switzerland", "Japan", "Norway", "Canada"],
                    answer: 0
                }, {
                    question: "Which one is not a structure listed as a UNESCO World Heritage Site?",
                    options: ["Eiffel Tower", "Acropolis", "Stonehenge", "Great Wall of China"],
                    answer: 3
                }],
                medium: [{
                    question: "Which one is not a play by the English writer William Shakespeare?",
                    options: ["Hamlet", "Romeo and Juliet", "Macbeth", "The Brothers Karamazov"],
                    answer: 3
                }, {
                    question: "In Greek mythology, who was the goddess of wisdom and warfare?",
                    options: ["Aphrodite", "Artemis", "Athena", "Hera"],
                    answer: 2
                }, {
                    question: "Which city is located on two continents?",
                    options: ["Rome", "Cairo", "Istanbul", "Sydney"],
                    answer: 2
                }, {
                    question: "What is the capital city of Canada?",
                    options: ["Toronto", "Vancouver", "Ottawa", "Montreal"],
                    answer: 2
                }, {
                    question: "Which country in the Middle East has the 'Nile River'?",
                    options: ["Saudi Arabia", "Egypt", "Iraq", "Syria"],
                    answer: 1
                }],
                hard: [{
                    question: "Which country in Europe is entirely independent from the continent?",
                    options: ["Iceland", "Norway", "Switzerland", "Ireland"],
                    answer: 0
                }, {
                    question: "What is the longest river in the world?",
                    options: ["Nile River", "Amazon River", "Yangtze River", "Mississippi River"],
                    answer: 1
                }, {
                    question: "In which museum is Leonardo da Vinci's 'Mona Lisa' displayed?",
                    options: ["British Museum (London)", "Louvre Museum (Paris)", "Metropolitan Museum of Art (New York)", "Vatican Museums (Rome)"],
                    answer: 1
                }, {
                    question: "In which country's flag do the colors green, white, red, and black appear?",
                    options: ["Pakistan", "Libya", "Albania", "Oman"],
                    answer: 3
                }, {
                    question: "BM Security Council veto-wielding permanent members are which countries?",
                    options: ["USA, China, France, UK, Russia", "Germany, Brazil, India, Japan, South Africa", "Australia, Canada, Italy, Mexico, Spain", "Turkey, Indonesia, Nigeria, Pakistan, Argentina"],
                    answer: 0
                }]
            }
        };

        let currentQuestionIndex = 0;
        let currentCategory = 'mixed';
        let currentDifficulty = 'easy';
        let timer;
        let timeLeft = 15;
        let score = 0;

        function loadQuestion() {
            currentCategory = document.getElementById('category').value;
            currentQuestionIndex = 0;
            currentDifficulty = 'easy';
            score = 0;
            document.getElementById('result').innerText = '';
            document.getElementById('feedback').innerHTML = '';
            loadNextQuestion();
            createProgressBar();
        }

        function loadNextQuestion() {
            clearTimeout(timer);
            timeLeft = 15;
            document.getElementById('timer').innerText = timeLeft;
            startTimer();

            let questionData;
            if (currentCategory === 'social') {
                if (currentQuestionIndex < questions[currentCategory].easy.length) {
                    questionData = questions[currentCategory].easy[currentQuestionIndex];
                } else if (currentQuestionIndex < questions[currentCategory].easy.length + questions[currentCategory].medium.length) {
                    currentDifficulty = 'medium';
                    questionData = questions[currentCategory].medium[currentQuestionIndex - questions[currentCategory].easy.length];
                } else {
                    currentDifficulty = 'hard';
                    questionData = questions[currentCategory].hard[currentQuestionIndex - questions[currentCategory].easy.length - questions[currentCategory].medium.length];
                }
            } else {
                questionData = questions[currentCategory][currentQuestionIndex];
            }

            if (!questionData) {
                document.getElementById('result').innerText = `Game over! Your score is ${score}/${currentQuestionIndex}.`;
                document.getElementById('game-container').innerHTML = '';
                clearTimeout(timer);
                return;
            }

            const questionText = `<p class="question">${questionData.question}</p>`;
            const options = questionData.options.map((option, index) => `<li><button onclick="checkAnswer(${index})">${option}</button></li>`).join('');
            const optionsList = `<ul class="options">${options}</ul>`;

            document.getElementById('game-container').innerHTML = questionText + optionsList;
        }

        function checkAnswer(selectedIndex) {
            clearTimeout(timer);
            let correctAnswer;
            if (currentCategory === 'social') {
                correctAnswer = questions[currentCategory][currentDifficulty][currentQuestionIndex].answer;
            } else {
                correctAnswer = questions[currentCategory][currentQuestionIndex].answer;
            }
            const isCorrect = selectedIndex === correctAnswer;
            updateProgressBar(currentQuestionIndex, isCorrect);
            if (isCorrect) {
                score++;
                document.getElementById('result').innerText = 'Correct!';
                document.getElementById('feedback').innerHTML = '<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRORLtnhhLLtQNzdpNMnKHn5eMyOL_qMYmIm0tYf0OjAwM4TYz65I2BC6JK&s=10" alt="Correct">';
            } else {
                document.getElementById('result').innerText = `Incorrect! The correct answer was ${correctAnswer + 1}.`;
                document.getElementById('feedback').innerHTML = '<img src="https://e7.pngegg.com/pngimages/385/780/png-clipart-red-x-illustration-x-mark-check-mark-wrong-sign-angle-symmetry-thumbnail.png" alt="Incorrect">';
            }
            currentQuestionIndex++;
            setTimeout(loadNextQuestion, 2000);
        }

        function startTimer() {
            timer = setInterval(() => {
                if (timeLeft <= 0) {
                    clearInterval(timer);
                    checkAnswer(-1);
                } else {
                    document.getElementById('timer').innerText = --timeLeft;
                }
            }, 1000);
        }

        function createProgressBar() {
            const progressBar = document.getElementById('progress-bar');
            progressBar.innerHTML = '';
            for (let i = 0; i < 25; i++) {
                const segment = document.createElement('div');
                segment.className = 'bar-segment';
                progressBar.appendChild(segment);
            }
        }

        function updateProgressBar(index, isCorrect) {
            const segments = document.querySelectorAll('.bar-segment');
            if (segments[index]) {
                segments[index].classList.add(isCorrect ? 'correct' : 'incorrect');
            }
        }

        document.addEventListener('DOMContentLoaded', (event) => {
            loadQuestion();
        });
    </script>

            </body>

      </html>
