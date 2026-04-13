# osoriocelis6.github.io
Invitación matrimonio 1
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Nuestra Boda</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Inter', sans-serif;
      background: linear-gradient(to bottom, #0f1c2e, #1f3a5f);
      color: #f5efe6;
    }

    header {
      text-align: center;
      padding: 80px 20px;
    }

    h1 {
      font-family: 'Playfair Display', serif;
      font-size: 3rem;
      margin-bottom: 10px;
      color: #f5efe6;
    }

    h2 {
      font-family: 'Playfair Display', serif;
      text-align: center;
      margin-bottom: 20px;
    }

    section {
      padding: 40px 20px;
      max-width: 900px;
      margin: auto;
    }

    .card {
      background: rgba(255,255,255,0.05);
      border-radius: 20px;
      padding: 30px;
      backdrop-filter: blur(10px);
      box-shadow: 0 10px 30px rgba(0,0,0,0.3);
    }

    .gallery {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 10px;
    }

    .gallery img {
      width: 100%;
      max-width: 250px;
      border-radius: 12px;
      transition: transform 0.3s;
    }

    .gallery img:hover {
      transform: scale(1.05);
    }

    iframe {
      width: 100%;
      height: 300px;
      border-radius: 12px;
      border: none;
    }

    form {
      display: flex;
      flex-direction: column;
      gap: 12px;
    }

    input, select {
      padding: 12px;
      border-radius: 10px;
      border: none;
      font-size: 15px;
    }

    button {
      padding: 12px;
      border-radius: 10px;
      border: none;
      background: #c8d9f0;
      color: #1f3a5f;
      font-weight: bold;
      cursor: pointer;
      transition: 0.3s;
    }

    button:hover {
      background: #a9c3e6;
    }

    .countdown {
      font-size: 1.2rem;
      margin-top: 20px;
      letter-spacing: 1px;
    }

  </style>
</head>
<body>

<header>
  <h1>Juan & María</h1>
  <p>Nos casamos</p>
  <p>20 de Marzo 2027 · 20:00 hrs</p>
  <div class="countdown" id="countdown"></div>
</header>

<section>
  <div class="card">
    <h2>Nuestra Historia</h2>
    <p>Un pequeño texto romántico sobre ustedes...</p>
  </div>
</section>

<section>
  <div class="card">
    <h2>Galería</h2>
    <div class="gallery">
      <img src="foto1.jpg">
      <img src="foto2.jpg">
      <img src="foto3.jpg">
    </div>
  </div>
</section>

<section>
  <div class="card">
    <h2>Ubicación</h2>
    <iframe src="https://www.google.com/maps?q=hotel+wedding+location&output=embed"></iframe>
  </div>
</section>

<section>
  <div class="card">
    <h2>Confirmación</h2>
    <form id="rsvpForm">
      <input type="text" name="nombre" placeholder="Nombre" required>
      <input type="email" name="email" placeholder="Correo" required>
      <select name="asistencia">
        <option value="si">Sí asistiré</option>
        <option value="no">No podré asistir</option>
      </select>
      <select name="menu">
        <option value="clasico">Menú clásico</option>
        <option value="vegetariano">Menú vegetariano</option>
      </select>
      <button type="submit">Confirmar asistencia</button>
    </form>
  </div>
</section>

<script>
  // Cuenta regresiva
  const targetDate = new Date("March 20, 2027 20:00:00").getTime();

  setInterval(() => {
    const now = new Date().getTime();
    const diff = targetDate - now;

    const days = Math.floor(diff / (1000 * 60 * 60 * 24));
    const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);

    document.getElementById("countdown").innerText =
      days + " días " + hours + " hrs";
  }, 1000);

  // Formulario
  document.getElementById("rsvpForm").addEventListener("submit", function(e) {
    e.preventDefault();

    const data = new FormData(this);
    const obj = {};
    data.forEach((value, key) => obj[key] = value);

    fetch("https://script.google.com/macros/s/TU_SCRIPT_ID/exec", {
      method: "POST",
      body: JSON.stringify(obj)
    })
    .then(() => alert("¡Confirmación enviada!") )
    .catch(() => alert("Error al enviar"));
  });
</script>

</body>
</html>

