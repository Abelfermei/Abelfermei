<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora de RPM y Velocidad de Avance</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            margin-top: 50px;
            padding: 20px;
        }
        select, input, button {
            margin: 10px;
            padding: 10px;
            font-size: 16px;
        }
        #result {
            font-size: 20px;
            margin-top: 20px;
            color: #4CAF50;
        }
    </style>
</head>
<body>
    <h1>Calculadora de RPM y Velocidad de Avance</h1>
    <label for="material">Selecciona el material:</label>
    <select id="material">
        <option value="aluminio">Aluminio</option>
        <option value="acero">Acero</option>
        <option value="plastico">Plástico</option>
    </select>

    <label for="diametro">Diámetro de la broca (mm):</label>
    <input type="number" id="diametro" placeholder="Ej. 6" required>

    <label for="espesor">Espesor del material (mm):</label>
    <input type="number" id="espesor" placeholder="Ej. 6" required>

    <button onclick="calcular()">Calcular</button>

    <div id="result"></div>

    <script>
        function calcular() {
            const material = document.getElementById("material").value;
            const diametro = parseFloat(document.getElementById("diametro").value);
            const espesor = parseFloat(document.getElementById("espesor").value);

            if (isNaN(diametro) || isNaN(espesor)) {
                alert("Por favor, ingresa valores válidos.");
                return;
            }

            let rpm, avance;

            // Establecer valores predeterminados para diferentes materiales
            if (material === "aluminio") {
                rpm = 3000 / diametro;
                avance = 0.1 * diametro;
            } else if (material === "acero") {
                rpm = 2000 / diametro;
                avance = 0.05 * diametro;
            } else if (material === "plastico") {
                rpm = 3500 / diametro;
                avance = 0.2 * diametro;
            }

            // Mostrar los resultados
            document.getElementById("result").innerHTML = `
                RPM recomendadas: ${rpm.toFixed(2)}<br>
                Velocidad de avance: ${avance.toFixed(2)} mm/min
            `;
        }
    </script>
</body>
</html>
