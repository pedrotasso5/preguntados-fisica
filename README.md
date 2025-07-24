<!DOCTYPE html><html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Preguntados Marino - Física MRU</title>
  <style>
    body {
      font-family: 'Comic Sans MS', cursive, sans-serif;
      background: linear-gradient(#a0e7e5, #b4f8c8);
      margin: 0;
      padding: 0;
      color: #003f5c;
    }
    .container {
      max-width: 700px;
      margin: auto;
      background: rgba(255, 255, 255, 0.9);
      padding: 30px;
      border-radius: 20px;
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.3);
      text-align: center;
    }
    h1 {
      color: #008891;
      margin-bottom: 20px;
      font-size: 2em;
    }
    .question {
      font-size: 1.3em;
      margin: 20px 0;
    }
    .btn {
      padding: 12px 25px;
      margin: 10px;
      font-size: 1em;
      border: none;
      border-radius: 15px;
      cursor: pointer;
      transition: transform 0.2s;
    }
    .btn:hover {
      transform: scale(1.1);
    }
    .btn-true {
      background-color: #00c9a7;
      color: white;
    }
    .btn-false {
      background-color: #f45b69;
      color: white;
    }
    .score {
      font-size: 1.2em;
      margin-top: 20px;
    }
    .final {
      font-size: 1.5em;
      font-weight: bold;
      color: #145374;
    }
    .ocean-symbols {
      font-size: 2rem;
      margin-top: 30px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>⚓️🐟 Preguntados Marino: MRU 🔱🐚</h1>
    <div class="question" id="question">Cargando pregunta...</div>
    <button class="btn btn-true" onclick="answer(true)">✅ Verdadero</button>
    <button class="btn btn-false" onclick="answer(false)">❌ Falso</button>
    <div class="score" id="score">Puntaje: 0</div>
    <div class="final" id="final"></div>
    <div class="ocean-symbols">⚓ 🐟 🐚 🧜‍♂️ 🔱 🐬 🌊</div>
  </div>  <script>
    const questions = [
      { text: "En MRU, la velocidad es constante.", correct: true },
      { text: "MRU significa Movimiento Rápido Uniforme.", correct: false },
      { text: "La aceleración en MRU es cero.", correct: true },
      { text: "En MRU, la distancia y el desplazamiento siempre son iguales si el movimiento es en línea recta.", correct: true },
      { text: "En MRU, se usa la fórmula x = x₀ + v·t.", correct: true },
      { text: "La pendiente del gráfico posición-tiempo en MRU representa la aceleración.", correct: false },
      { text: "Si la velocidad es negativa en MRU, el objeto se mueve en sentido contrario.", correct: true },
      { text: "Un objeto en MRU recorre distancias diferentes en cada segundo.", correct: false },
      { text: "Si el gráfico de posición vs tiempo es una línea curva, se trata de un MRU.", correct: false },
      { text: "Un auto a 60 km/h durante 2 horas recorre 120 km, eso es un ejemplo de MRU.", correct: true },
      { text: "En MRU no se necesita conocer la aceleración para describir el movimiento.", correct: true },
      { text: "La unidad de velocidad en el SI es m/s.", correct: true },
      { text: "En MRU, el tiempo influye en la aceleración.", correct: false },
      { text: "Un objeto con velocidad cero está en MRU.", correct: true },
      { text: "Si un objeto cambia de velocidad está en MRU.", correct: false },
      { text: "La fórmula de la velocidad media en MRU es Δx/Δt.", correct: true },
      { text: "El gráfico de velocidad vs tiempo en MRU es una línea horizontal.", correct: true },
      { text: "El MRU solo ocurre si no hay ninguna fuerza actuando.", correct: false },
      { text: "La velocidad escalar y la velocidad vectorial siempre coinciden en MRU unidimensional.", correct: true },
      { text: "El MRU puede describirse con un gráfico velocidad-tiempo inclinado.", correct: false }
    ];

    let current = 0;
    let score = 0;

    function loadQuestion() {
      if (current < questions.length) {
        document.getElementById("question").innerText = questions[current].text;
      } else {
        document.getElementById("question").style.display = "none";
        document.querySelector(".btn-true").style.display = "none";
        document.querySelector(".btn-false").style.display = "none";
        document.getElementById("final").innerText = `🐬 ¡Juego terminado! Puntaje final: ${score} / ${questions.length}`;
      }
    }

    function answer(userAnswer) {
      if (questions[current].correct === userAnswer) {
        score++;
      }
      current++;
      document.getElementById("score").innerText = `Puntaje: ${score}`;
      loadQuestion();
    }

    loadQuestion();
  </script></body>
</html>
