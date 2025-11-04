<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Encuesta Sedentarismo Completa</title>
<script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-pink-100 flex items-center justify-center min-h-screen p-4">

<div class="bg-white rounded-3xl shadow-xl p-8 w-full max-w-lg">
  <h1 class="text-3xl font-bold text-center text-purple-600 mb-6">🛋️ Encuesta de Sedentarismo 🏃‍♀️</h1>

  <form id="encuesta" class="space-y-4">

    <div>
      <label class="block font-semibold">👤 Nombre:</label>
      <input type="text" id="nombre" class="w-full border rounded px-3 py-2" required>
    </div>

    <div>
      <label class="block font-semibold">🎂 Edad:</label>
      <input type="number" id="edad" class="w-full border rounded px-3 py-2" required>
    </div>

    <div>
      <label class="block font-semibold">🚻 Género:</label>
      <select id="genero" class="w-full border rounded px-3 py-2">
        <option value="Femenino">Femenino</option>
        <option value="Masculino">Masculino</option>
        <option value="Otro">Otro</option>
      </select>
    </div>

    <div>
      <label class="block font-semibold">🛋️ Horas sentado al día:</label>
      <select id="horas" class="w-full border rounded px-3 py-2">
        <option value="1">Menos de 2 horas</option>
        <option value="2">2 a 4 horas</option>
        <option value="3">4 a 6 horas</option>
        <option value="4">Más de 6 horas</option>
      </select>
    </div>

    <div>
      <label class="block font-semibold">🏃‍♂️ Frecuencia de ejercicio por semana:</label>
      <select id="ejercicio" class="w-full border rounded px-3 py-2">
        <option value="4">Ninguna</option>
        <option value="3">1-2 veces</option>
        <option value="2">3-4 veces</option>
        <option value="1">5 o más veces</option>
      </select>
    </div>

    <div>
      <label class="block font-semibold">💃 Tiempo en actividades activas al día:</label>
      <select id="activa" class="w-full border rounded px-3 py-2">
        <option value="4">Ninguno</option>
        <option value="3">Menos de 30 minutos</option>
        <option value="2">30 minutos a 1 hora</option>
        <option value="1">Más de 1 hora</option>
      </select>
    </div>

    <div>
      <label class="block font-semibold">❓ ¿Sientes que pasas demasiado tiempo sentado?</label>
      <select id="sentido" class="w-full border rounded px-3 py-2">
        <option value="2">Sí 🛋️</option>
        <option value="1">No 🏃</option>
      </select>
    </div>

    <div>
      <label class="block font-semibold">📱 Horas usando pantallas al día:</label>
      <select id="pantalla" class="w-full border rounded px-3 py-2">
        <option value="1">Menos de 2 horas</option>
        <option value="2">2 a 4 horas</option>
        <option value="3">4 a 6 horas</option>
        <option value="4">Más de 6 horas</option>
      </select>
    </div>

    <div>
      <label class="block font-semibold">🍕 Comidas rápidas o poco saludables por semana:</label>
      <select id="comida" class="w-full border rounded px-3 py-2">
        <option value="1">Nunca</option>
        <option value="2">1-2 veces</option>
        <option value="3">3-5 veces</option>
        <option value="4">Casi todos los días</option>
      </select>
    </div>

    <div>
      <label class="block font-semibold">🛏️ Horas de sueño por noche:</label>
      <select id="sueño" class="w-full border rounded px-3 py-2">
        <option value="1">Más de 8 horas</option>
        <option value="2">6-8 horas</option>
        <option value="3">4-6 horas</option>
        <option value="4">Menos de 4 horas</option>
      </select>
    </div>

    <div>
      <label class="block font-semibold">🏠 Movimiento dentro de casa o trabajo:</label>
      <select id="movimiento" class="w-full border rounded px-3 py-2">
        <option value="1">Sí, constantemente</option>
        <option value="2">Algunas veces</option>
        <option value="3">Raramente</option>
        <option value="4">Nunca</option>
      </select>
    </div>

    <button type="button" onclick="calcularSedentarismo()" class="w-full bg-purple-500 text-white font-bold py-2 px-4 rounded hover:bg-purple-600 transition mt-2">Enviar</button>

  </form>

  <div id="resultado" class="mt-6 text-center text-xl font-bold text-pink-600"></div>
</div>

<script>
function calcularSedentarismo() {
  const valores = [
    parseInt(document.getElementById('horas').value),
    parseInt(document.getElementById('ejercicio').value),
    parseInt(document.getElementById('activa').value),
    parseInt(document.getElementById('sentido').value),
    parseInt(document.getElementById('pantalla').value),
    parseInt(document.getElementById('comida').value),
    parseInt(document.getElementById('sueño').value),
    parseInt(document.getElementById('movimiento').value)
  ];

  const puntaje = valores.reduce((a,b) => a + b, 0);

  let mensaje = "";
  // 8 niveles de sedentarismo
  if (puntaje <= 8) mensaje = "🏃‍♀️ Nivel 1: Muy activo";
  else if (puntaje <= 11) mensaje = "🏃 Nivel 2: Activo";
  else if (puntaje <= 14) mensaje = "🙂 Nivel 3: Poco sedentario";
  else if (puntaje <= 17) mensaje = "😐 Nivel 4: Medio sedentario";
  else if (puntaje <= 20) mensaje = "😴 Nivel 5: Sedentario moderado";
  else if (puntaje <= 23) mensaje = "🛋️ Nivel 6: Sedentario";
  else if (puntaje <= 26) mensaje = "🛋️💤 Nivel 7: Muy sedentario";
  else mensaje = "💀 Nivel 8: Extremadamente sedentario";

  document.getElementById('resultado').innerText = mensaje;
}
</script>

</body>
</html>
