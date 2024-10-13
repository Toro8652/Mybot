<!DOCTYPE html>
<html lang="km">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>លំហាត់គណិតវិទ្យា</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #e0f7fa; /* ពណ៌ខ្លីៗ */
            text-align: center;
            padding: 20px;
        }
        h1 {
            font-size: 40px;
            color: #00695c; /* ពណ៌ខៀវ */
            margin-bottom: 20px;
        }
        .question {
            font-size: 28px;
            margin: 20px 0;
            background-color: #ffffff; /* បន្ទះសម្រាប់សំណួរ */
            border-radius: 10px;
            padding: 15px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }
        .answer {
            font-size: 24px;
            margin: 10px 0;
        }
        .result {
            font-size: 28px;
            color: green;
            margin-top: 20px;
        }
        .error {
            font-size: 28px;
            color: red;
            margin-top: 20px;
        }
        input[type="number"] {
            padding: 10px;
            font-size: 20px;
            border-radius: 5px;
            border: 1px solid #aaa;
            margin-right: 10px;
        }
        button {
            padding: 10px 20px;
            font-size: 20px;
            color: #fff;
            background-color: #00796b; /* ពណ៌បៃតង */
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #004d40; /* ពណ៌ខ្មៅ */
        }
        #next {
            display: none;
            margin-top: 20px;
        }
        .confetti {
            display: none;
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 100%;
            pointer-events: none;
        }
    </style>
</head>
<body>

<h1>លំហាត់គណិតវិទ្យា</h1>
<div id="quiz"></div>
<div>
    <input type="number" id="answer" placeholder="បញ្ចូលចម្លើយ" />
    <button onclick="submitAnswer()">បញ្ចូនចម្លើយ</button>
</div>
<div id="result" class="result"></div>
<div id="error" class="error"></div>
<div id="next">
    <button onclick="nextQuestion()">ទៅលំហាត់បន្ទាប់</button>
</div>

<!-- ផ្នែកបន្ថែមសម្រាប់ការបង្ហាញភាពរីករាយ -->
<div class="confetti" id="confetti">
    <img src="https://example.com/confetti.png" alt="Confetti" style="width: 100%; height: auto;">
</div>

<script>
    const questions = [
        { question: "1 + 1 =", answer: 2 },
        { question: "2 + 2 =", answer: 4 },
        { question: "3 + 5 =", answer: 8 },
        { question: "4 + 4 =", answer: 8 },
        { question: "5 + 8 =", answer: 13 }
        
    ]; 
 
    let currentQuestion = 0;
    let score = 0;

    function loadQuestion() {
        document.getElementById("quiz").innerHTML = `<div class="question">${questions[currentQuestion].question}</div>`;
        document.getElementById("answer").value = '';
        document.getElementById("result").innerText = '';
        document.getElementById("error").innerText = '';
        document.getElementById("next").style.display = 'none';
        document.getElementById("confetti").style.display = 'none'; // hide confetti
    }

    function submitAnswer() {
        const userAnswer = parseInt(document.getElementById("answer").value);
        if (userAnswer === questions[currentQuestion].answer) {
            score++;
            document.getElementById("result").innerText = "ចម្លើយត្រឹមត្រូវ!"
            document.getElementbyid("next").style.display = 'block';
            showConfetti(); // show confetti for correct answer
        } else {
            document.getElementById("error").innerText = "ចម្លើយមិនត្រឹមត្រូវ! សូមព្យាយាមម្ដងទៀត។";
        }
    }

    function nextQuestion() {
        currentQuestion++;
        if (currentQuestion < questions.length) {
            loadQuestion();
        } else {
            document.getElementById("quiz").innerHTML = `<h2>ការបញ្ចប់! ពិន្ទុរបស់អ្នកគឺ: ${score}/${questions.length}</h2>`;
            document.getElementById("answer").style.display = 'none';
            document.getElementById("next").style.display = 'none';
        }
    }

    function showConfetti() {
        document.getElementById("confetti").style.display = 'block';
        setTimeout(() => {
            document.getElementById("confetti").style.display = 'none';
        }, 2000); // hide confetti after 2 seconds
    }

    loadQuestion();
</script>

</body>

 
