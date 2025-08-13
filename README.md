<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Preguntados Marino: MRU</title>
  <style>
    body {
      background: linear-gradient(to bottom, #a8e0ff, #70cad1);
      font-family: 'Segoe UI', sans-serif;
      text-align: center;
      padding: 20px;
      color: #00334e;
      transition: background-color 0.5s ease;
    }
    .container {
      background: white;
      border-radius: 20px;
      padding: 30px;
      max-width: 700px;
      margin: auto;
      box-shadow: 0 0 15px rgba(0,0,0,0.2);
    }
    h1 {
      color: #0077b6;
    }
    button {
      font-size: 18px;
      margin: 10px;
      padding: 10px 20px;
      border-radius: 10px;
      border: none;
      cursor: pointer;
      transition: 0.3s;
    }
    .true-btn {
      background-color: #38b000;
      color: white;
    }
    .false-btn {
      background-color: #d90429;
      color: white;
    }
    .true-btn:hover, .false-btn:hover {
      opacity: 0.8;
    }
    .marine-icons {
      font-size: 24px;
    }
    #feedback {
      margin-top: 20px;
      font-weight: bold;
      color: white;
      padding: 10px;
      border-radius: 10px;
      min-height: 50px;
      transition: background-color 0.5s ease;
    }
    .illustration {
      font-size: 30px;
      margin: 10px;
    }
    button:disabled {
      opacity: 0.5;
      cursor: default;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1 class="marine-icons">⚓ Preguntados Marino: Movimiento Rectilíneo Uniforme 🐟</h1>
    <div class="illustration">🌊 🐚 🔱 🐡 🐬 🐙</div>
    <p id="question">Cargando pregunta...</p>
    <button class="true-btn" id="btnTrue" onclick="checkAnswer(true)">✔️ Verdadero</button>
    <button class="false-btn" id="btnFalse" onclick="checkAnswer(false)">❌ Falso</button>
    <p>Puntaje: <span id="score">0</span></p>
    <p id="feedback"></p>
    <div class="illustration">⚓ 🐟 🐠 🐡 🌊 🐬</div>
  </div>

<script>
  const questions = [
    { q: "En MRU, la velocidad permanece constante en magnitud y dirección.", a: true, e: "Correcto. Por eso se llama 'uniforme' y 'rectilíneo'." },
    { q: "En MRU, la aceleración es cero.", a: true, e: "Exacto. No hay cambio en la velocidad." },
    { q: "La fórmula principal del MRU es d = v * t.", a: true, e: "Sí. Distancia = velocidad × tiempo." },
    { q: "Si un auto va a 60 km/h durante 2 horas, recorre 120 km.", a: true, e: "Correcto. 60 × 2 = 120 km." },
    { q: "En MRU, la trayectoria es siempre curva.", a: false, e: "Incorrecto. En MRU es recta." },
    { q: "La velocidad negativa significa que el objeto está detenido.", a: false, e: "No. Solo significa que va en sentido opuesto." },
    { q: "En MRU, la gráfica posición-tiempo es una línea recta.", a: true, e: "Correcto. Es una línea recta con pendiente igual a la velocidad." },
    { q: "Si el tiempo aumenta, la distancia en MRU no cambia.", a: false, e: "No. A más tiempo, más distancia recorrida." },
    { q: "En MRU, el desplazamiento y la distancia siempre son iguales.", a: false, e: "Solo si no hay cambio de sentido." },
    { q: "MRU significa Movimiento Rectilíneo Uniforme.", a: true, e: "Exacto. No es 'relativamente uniforme'." },
    { q: "En MRU, la aceleración constante es distinta de cero.", a: false, e: "Falso. La aceleración es cero." },
    { q: "Si la velocidad es cero, no hay MRU.", a: true, e: "Correcto. Con velocidad cero, el objeto está en reposo." },
    { q: "La unidad de velocidad en el SI es el metro por segundo (m/s).", a: true, e: "Exacto. Aunque también se usa km/h." },
    { q: "En MRU, la velocidad media y la velocidad instantánea son iguales.", a: true, e: "Sí, porque la velocidad no cambia." },
    { q: "Si recorres 100 m en 10 s, tu velocidad es 10 m/s.", a: true, e: "Correcto. 100 ÷ 10 = 10 m/s." },
    { q: "En MRU, un gráfico velocidad-tiempo es una línea horizontal.", a: true, e: "Exacto. La velocidad no varía con el tiempo." },
    { q: "En MRU, la rapidez puede cambiar aunque la dirección sea la misma.", a: false, e: "No. Ni rapidez ni dirección cambian." },
    { q: "Un barco que navega en línea recta a velocidad constante está en MRU.", a: true, e: "Correcto." },
    { q: "Si un objeto está en MRU, su aceleración instantánea es cero.", a: true, e: "Exacto." },
    { q: "En MRU, se puede calcular el tiempo como t = d / v.", a: true, e: "Sí. Es la fórmula despejada." },
    { q: "La velocidad en MRU se puede medir en m/s o km/h.", a: true, e: "Correcto." },
    { q: "Un objeto en MRU cambia su velocidad con el tiempo.", a: false, e: "No. Se mantiene igual." },
    { q: "En MRU, el espacio recorrido en 1 hora es siempre el mismo.", a: true, e: "Sí, si la velocidad es constante." },
    { q: "En MRU, el área bajo la curva de velocidad-tiempo representa la distancia.", a: true, e: "Correcto." },
    { q: "La fórmula v = d / t solo sirve en MRU.", a: false, e: "También se usa en otros movimientos para calcular velocidad media." },
    { q: "Un ciclista que acelera está en MRU.", a: false, e: "Falso. Acelerar implica cambiar la velocidad." },
    { q: "En MRU, no hay fuerzas actuando sobre el objeto.", a: false, e: "Puede haber fuerzas equilibradas, pero no producen aceleración." },
    { q: "En MRU, el tiempo es directamente proporcional a la distancia recorrida.", a: true, e: "Correcto." },
    { q: "Un cohete en lanzamiento vertical está en MRU.", a: false, e: "No, porque acelera." },
    { q: "En MRU, si duplicas el tiempo, duplicas la distancia.", a: true, e: "Exacto." },
    { q: "En MRU, la pendiente de la gráfica posición-tiempo es la aceleración.", a: false, e: "Es la velocidad, no la aceleración." },
    { q: "La velocidad en MRU puede ser positiva o negativa.", a: true, e: "Sí, según el sentido del movimiento." },
    { q: "En MRU, la aceleración es positiva.", a: false, e: "No. Es cero." },
    { q: "Si un tren va a 100 km/h y recorre 50 km, lo hace en media hora.", a: true, e: "Correcto." },
    { q: "En MRU, la dirección de la velocidad cambia con el tiempo.", a: false, e: "No cambia." },
    { q: "En MRU, la trayectoria puede ser circular.", a: false, e: "No, siempre recta." },
    { q: "El MRU es un caso particular de movimiento más general.", a: true, e: "Sí, es un caso especial del movimiento rectilíneo." },
    { q: "En MRU, la velocidad angular es constante.", a: false, e: "MRU no trata de velocidad angular, sino lineal." },
    { q: "En MRU, la rapidez es la misma que el módulo de la velocidad.", a: true, e: "Correcto." },
    { q: "En MRU, no se puede ir hacia atrás.", a: false, e: "Sí se puede, con velocidad negativa." },
    { q: "En MRU, la velocidad puede medirse en cm/s.", a: true, e: "Sí, aunque no es habitual en física general." },
    { q: "En MRU, la aceleración depende de la masa.", a: false, e: "No depende de la masa, y además es cero." },
    { q: "En MRU, la energía cinética es constante.", a: true, e: "Correcto, porque la velocidad no cambia." },
    { q: "En MRU, el tiempo transcurrido no influye en la velocidad.", a: true, e: "Exacto." },
    { q: "Si un objeto está en MRU, no hay ninguna fuerza actuando.", a: false, e: "Puede haber fuerzas equilibradas." },
    { q: "En MRU, el objeto no tiene aceleración centrípeta.", a: true, e: "Correcto, porque no hay trayectoria curva." },
    { q: "En MRU, si la distancia recorrida es cero, el tiempo también debe ser cero.", a: true, e: "Sí, si la velocidad es constante y distinta de cero." },
    { q: "En MRU, la velocidad inicial y final son distintas.", a: false, e: "No, son iguales." },
    { q: "En MRU, si v = 0, la distancia no cambia con el tiempo.", a: true, e: "Correcto, está en reposo." },
    { q: "El MRU se puede representar con la ecuación x = x₀ + v·t.", a: true, e: "Sí, es la forma más general de la ecuación." }
  ];

  let current = 0;
  let score = 0;
  let timeoutId = null;

  // Generar tonos simples para acierto/error usando Web Audio API
  function playTone(frequency, duration) {
    const context = new (window.AudioContext || window.webkitAudioContext)();
    const oscillator = context.createOscillator();
    const gainNode = context.createGain();

    oscillator.type = 'sine';
    oscillator.frequency.setValueAtTime(frequency, context.currentTime);
    oscillator.connect(gainNode);
    gainNode.connect(context.destination);

    oscillator.start();
    gainNode.gain.exponentialRampToValueAtTime(0.0001, context.currentTime + duration / 1000);
    oscillator.stop(context.currentTime + duration / 1000);
  }

  function playCorrect() {
    playTone(880, 200); // tono agudo corto
  }

  function playWrong() {
    playTone(220, 400); // tono grave más largo
  }

  function loadQuestion() {
    document.body.style.backgroundColor = '';
    document.getElementById("question").innerText = questions[current].q;
    const fb = document.getElementById("feedback");
    fb.innerText = "";
    fb.style.backgroundColor = 'transparent';
    document.getElementById("btnTrue").disabled = false;
    document.getElementById("btnFalse").disabled = false;
  }

  function checkAnswer(userAnswer) {
    if(timeoutId) return; // evitar respuestas múltiples mientras se espera

    const correct = questions[current].a;
    const fb = document.getElementById("feedback");
    const body = document.body;

    if (userAnswer === correct) {
      score++;
      fb.style.backgroundColor = '#38b000'; // verde
      playCorrect();
    } else {
      fb.style.backgroundColor = '#d90429'; // rojo
      playWrong();
    }

    document.getElementById("score").innerText = score;
    fb.innerText = questions[current].e;

    document.getElementById("btnTrue").disabled = true;
    document.getElementById("btnFalse").disabled = true;

    current++;

    timeoutId = setTimeout(() => {
      timeoutId = null;
      if (current < questions.length) {
        loadQuestion();
      } else {
        document.getElementById("question").innerText = "¡Juego terminado!";
        fb.innerText = "Puntaje final: " + score + "/" + questions.length;
        fb.style.backgroundColor = '#005f73';
        document.getElementById("btnTrue").style.display = "none";
        document.getElementById("btnFalse").style.display = "none";
      }
    }, 5000);
  }

  loadQuestion();
</script>
</body>
</html>
