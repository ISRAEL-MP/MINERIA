# SOCIEDAD Y MINERIA
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Examen de Matemáticas</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            padding: 10px;
        }
        .question {
            margin-bottom: 15px;
        }
        .submit-btn {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 10px 15px;
            cursor: pointer;
            font-size: 16px;
        }
        .submit-btn:hover {
            background-color: #45a049;
        }
        .result {
            margin-top: 20px;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <h1>Examen de Matemáticas</h1>
    <form id="examForm">
        <div class="question">
            <label>1. ¿Cuánto es 5 + 3?</label><br>
            <input type="radio" name="q1" value="6"> 6<br>
            <input type="radio" name="q1" value="8"> 8<br>
            <input type="radio" name="q1" value="10"> 10<br>
        </div>
        <div class="question">
            <label>2. ¿Cuánto es 9 × 2?</label><br>
            <input type="radio" name="q2" value="18"> 18<br>
            <input type="radio" name="q2" value="20"> 20<br>
            <input type="radio" name="q2" value="22"> 22<br>
        </div>
        <button type="button" class="submit-btn" onclick="checkAnswers()">Enviar</button>
    </form>
    <div id="result" class="result"></div>

    <script>
        function checkAnswers() {
            let score = 0;
            const totalQuestions = 2;

            const q1 = document.querySelector('input[name="q1"]:checked');
            const q2 = document.querySelector('input[name="q2"]:checked');

            if (q1 && q1.value === "8") score++;
            if (q2 && q2.value === "18") score++;

            const resultDiv = document.getElementById('result');
            resultDiv.innerHTML = `Obtuviste ${score} de ${totalQuestions} preguntas correctas.`;
        }
    </script>
</body>
</html>
