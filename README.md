# Gestión de Proyectos
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
        <div class="timer" id="timer">Tiempo restante: 05:00</div>

        <!-- Preguntas -->
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
        
        <button type="button" class="submit-btn" id="submitButton" onclick="checkAnswers()">Enviar</button>
    </form>
    <div id="result" class="result"></div>

    <script>
        // Control del temporizador
        let timeLeft = 300; // 5 minutos en segundos
        const timerElement = document.getElementById('timer');
        const submitButton = document.getElementById('submitButton');

        const timer = setInterval(() => {
            const minutes = Math.floor(timeLeft / 60);
            const seconds = timeLeft % 60;
            timerElement.textContent = `Tiempo restante: ${minutes}:${seconds < 10 ? '0' + seconds : seconds}`;
            timeLeft--;

            if (timeLeft < 0) {
                clearInterval(timer);
                timerElement.textContent = "Tiempo agotado.";
                submitButton.disabled = true;
            }
        }, 1000);

        // Función para verificar respuestas
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
// Detecta si el usuario intenta salir de la pestaña
document.addEventListener("visibilitychange", () => {
  if (document.hidden) {
    alert("Has salido del examen. Tu sesión será invalidada.");
    // Aquí puedes llamar a una función para invalidar el examen
    terminarExamen();
  }
});

function terminarExamen() {
  // Lógica para eliminar o finalizar el examen
  console.log("Examen terminado por abandonar la página.");
  window.location.href = "pagina-final.html"; // Redirige o finaliza
}
