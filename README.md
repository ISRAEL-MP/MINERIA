<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Examen de Matemáticas</title>
</head>
<body>
    <h1>Examen de Matemáticas</h1>
    <form id="examForm" method="POST" action="http://localhost:3000/send-results">
        <label for="name">Apellidos y Nombres:</label><br>
        <input type="text" id="name" name="name" placeholder="Escribe tus apellidos y nombres" required><br><br>

        <label>1. ¿Cuánto es 5 + 6?</label><br>
        <input type="radio" name="q1" value="6"> 6<br>
        <input type="radio" name="q1" value="8"> 8<br>
        <input type="radio" name="q1" value="11"> 11<br><br>

        <label>2. ¿Cuánto es 9 × 2?</label><br>
        <input type="radio" name="q2" value="18"> 18<br>
        <input type="radio" name="q2" value="20"> 20<br>
        <input type="radio" name="q2" value="22"> 22<br><br>

        <button type="submit">Enviar</button>
    </form>
</body>
</html>
