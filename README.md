# MINERIA
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Abrir Google desde HTML</title>
</head>
<body>

<button onclick="abrirGoogle()">Abrir Google</button>

<script>
    function abrirGoogle() {
        // URL de Google
        var urlGoogle = "https://www.google.com";

        // Abrir Google en una nueva pestaña o ventana
        window.open(urlGoogle, '_blank');
    }
</script>

</body>
</html>
