# quizz**
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>LoveFlix Original 💕</title>
<style>
  body {
    margin: 0;
    font-family: Arial, Helvetica, sans-serif;
    background: radial-gradient(circle at top, #141414, #000);
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }

  .card {
    width: 90%;
    max-width: 500px;
    background: #181818;
    border-radius: 12px;
    padding: 30px;
    box-shadow: 0 0 40px rgba(255,0,0,0.3);
    animation: fadeIn 1s ease;
  }

  h1 {
    color: #e50914;
    text-align: center;
    margin-bottom: 10px;
  }

  .question {
    font-size: 20px;
    margin: 20px 0;
    text-align: center;
  }

  input {
    width: 100%;
    padding: 12px;
    border-radius: 6px;
    border: none;
    font-size: 16px;
    margin-bottom: 15px;
  }

  button {
    width: 100%;
    padding: 12px;
    border: none;
    border-radius: 6px;
    background: #e50914;
    color: white;
    font-size: 16px;
    cursor: pointer;
  }

  button:hover {
    background: #ff1f2d;
  }

  .progress {
    text-align: center;
    font-size: 14px;
    opacity: 0.7;
  }

  @keyframes fadeIn {
    from { opacity: 0; transform: scale(0.95); }
    to { opacity: 1; transform: scale(1); }
  }
</style>
</head>
<body>

<div class="card" id="card">
  <h1>LoveFlix 💕</h1>
  <div class="progress" id="progress"></div>
  <div class="question" id="question"></div>
  <input type="text" id="answer" placeholder="Type your answer here…" />
  <button onclick="submitAnswer()">Next ▶</button>
</div>

<script>
const quizData = [
  { q: "What is my favorite color?", a: "red" },
  { q: "Who is my favorite person?", a: "rani" },
  { q: "What sport do I love the most?", a: "football" },
  { q: "What is my dream vacation place?", a: "bali" },
  { q: "What car brand do I love?", a: "mercedes" }
];

// Shuffle questions
quizData.sort(() => Math.random() - 0.5);

let current = 0;

function loadQuestion() {
  document.getElementById("progress").innerText =
    `Episode ${current + 1} of 5`;
  document.getElementById("question").innerText =
    quizData[current].q;
  document.getElementById("answer").value = "";
}

function submitAnswer() {
  const userAnswer =
    document.getElementById("answer").value.trim().toLowerCase();

  if (userAnswer !== quizData[current].a) {
    document.getElementById("card").innerHTML = `
      <h1>💔 Series Cancelled</h1>
      <p style="text-align:center">
        Oops… that was the wrong answer 😢<br><br>
        But don’t worry — love always gets a sequel 💕
      </p>`;
    return;
  }

  current++;
  if (current === quizData.length) {
    winSeries();
  } else {
    loadQuestion();
  }
}

function winSeries() {
  document.getElementById("card").innerHTML = `
    <h1>🎉 YOU WON 🎉</h1>
    <p style="text-align:center;font-size:18px">
      You passed every episode 💖<br><br>
      🛍️ <b>You have won a SHOPPING SPREE!</b> 🛍️<br><br>
      💳 Card to be used: <b>WAYNE’S</b><br><br>
      I love you 😘💕
    </p>
    <div style="text-align:center;font-size:40px">
      🐱💞🐱
    </div>
  `;
}

loadQuestion();
</script>

</body>
</html>
