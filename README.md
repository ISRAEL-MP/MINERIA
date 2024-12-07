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
        .question, .user-info {
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
        .result, .timer {
            margin-top: 20px;
            font-size: 18px;
        }
        .timer {
            font-weight: bold;
            color: red;
        }
    </style>
</head>
<body>
    <h1>Examen de Matemáticas</h1>
    <form id="examForm">
        <!-- Información del usuario -->
        <div class="user-info">
            <label for="name">Apellidos y Nombres:</label><br>
            <input type="text" id="name" name="name" placeholder="Escribe tus apellidos y nombres" required style="width: 100%; padding: 8px;">
        </div>

        <!-- Temporizador -->
        <div class="timer" id="timer">Tiempo restante: 10:00</div>

        <!-- Preguntas -->
        <div class="question">
            <label>1. ¿Cuánto es 5 + 6?</label><br>
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
        
        <button type="button" class="submit-btn" id="submitButton" onclick="checkAnswers()">Enviar</button>
    </form>
    <div id="result" class="result"></div>

    <script>
        // Variables globales
        let timeLeft = 600; // 10 minutos en segundos
        let focusLossCount = 0; // Contador de pérdida de foco
        const maxFocusLoss = 3; // Límite permitido
        const timerElement = document.getElementById('timer');
        const submitButton = document.getElementById('submitButton');

        // Temporizador
        const timer = setInterval(() => {
            const minutes = Math.floor(timeLeft / 60);
            const seconds = timeLeft % 60;
            timerElement.textContent = `Tiempo restante: ${minutes}:${seconds < 10 ? '0' + seconds : seconds}`;
            timeLeft--;

            if (timeLeft < 0) {
                clearInterval(timer);
                timerElement.textContent = "Tiempo agotado.";
                terminarExamen("Tiempo agotado.");
            }
        }, 1000);

        // Detectar cambio de pestaña
        document.addEventListener("visibilitychange", () => {
            if (document.hidden) {
                focusLossCount++;
                alert(`Has salido del examen ${focusLossCount} vez/veces. Límite permitido: ${maxFocusLoss}.`);
                if (focusLossCount > maxFocusLoss) {
                    terminarExamen("Examen terminado por salir de la página.");
                }
            }
        });

        // Finalizar examen
        function terminarExamen(mensaje) {
            alert(mensaje);
            checkAnswers();
            submitButton.disabled = true; // Evita múltiples envíos
        }

        // Verificar respuestas
        function checkAnswers() {
            const name = document.getElementById('name').value.trim();
            if (!name) {
                alert("Por favor, ingresa tus apellidos y nombres.");
                return;
            }

            let score = 0;
            const totalQuestions = 2;

            const q1 = document.querySelector('input[name="q1"]:checked');
            const q2 = document.querySelector('input[name="q2"]:checked');

            if (q1 && q1.value === "8") score++;
            if (q2 && q2.value === "18") score++;

            const resultDiv = document.getElementById('result');
            resultDiv.innerHTML = `${name}, obtuviste ${score} de ${totalQuestions} preguntas correctas.`;
        }
    </script>
</body>
</html>
