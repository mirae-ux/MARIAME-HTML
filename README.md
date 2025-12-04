# MARIAME-HTML
Japprend a deployer un projet html sur github
Code html pour un quizz sur la santé :

<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz Santé</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            color: #333;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            flex-direction: column;
        }
        .quiz-container {
            background-color: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            max-width: 600px;
            width: 100%;
        }
        h1 {
            text-align: center;
            color: #2c3e50;
        }
        .question {
            margin-bottom: 20px;
        }
        .options {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        .option {
            background-color: #3498db;
            color: #fff;
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
            text-align: center;
            transition: background-color 0.3s;
        }
        .option:hover {
            background-color: #2980b9;
        }
        .score {
            text-align: center;
            font-size: 1.2em;
            margin-top: 20px;
            color: #27ae60;
        }
        .hidden {
            display: none;
        }
    </style>
</head>
<body>
    <div class="quiz-container">
        <h1>Quiz Santé</h1>
        <div id="quiz"></div>
        <div class="score">
            Score : <span id="score">0</span> / 20
        </div>
    </div>

    <script>
        const questions = [
            {
                question: "Quel est l'organe responsable de la filtration du sang ?",
                options: ["Cœur", "Poumon", "Rein", "Foie"],
                answer: "Rein"
            },
            {
                question: "Quelle vitamine est produite par la peau sous l'effet du soleil ?",
                options: ["Vitamine A", "Vitamine C", "Vitamine D", "Vitamine E"],
                answer: "Vitamine D"
            },
            {
                question: "Quel est le rôle principal des globules rouges ?",
                options: ["Combattre les infections", "Transporter l'oxygène", "Coaguler le sang", "Produire des anticorps"],
                answer: "Transporter l'oxygène"
            },
            // Ajoutez 17 autres questions ici...
        ];

        let currentQuestionIndex = 0;
        let score = 0;

        const quizContainer = document.getElementById('quiz');
        const scoreDisplay = document.getElementById('score');

        function displayQuestion() {
            const question = questions[currentQuestionIndex];
            quizContainer.innerHTML = `
                <div class="question">${question.question}</div>
                <div class="options">
                    ${question.options.map(option => `
                        <div class="option" onclick="checkAnswer('${option}')">${option}</div>
                    `).join('')}
                </div>
            `;
        }

        function checkAnswer(selectedOption) {
            const question = questions[currentQuestionIndex];
            if (selectedOption === question.answer) {
                score++;
                scoreDisplay.textContent = score;
            }
            currentQuestionIndex++;
            if (currentQuestionIndex < questions.length) {
                displayQuestion();
            } else {
                endQuiz();
            }
        }

        function endQuiz() {
            quizContainer.innerHTML = `
                <div class="question">Quiz terminé !</div>
                <div class="score">Votre score final est : ${score} / 20</div>
            `;
        }

        displayQuestion();
    </script>
</body>
</html>
