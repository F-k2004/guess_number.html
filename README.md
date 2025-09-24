<!-- guess_number.html -->
<!DOCTYPE html>
<html lang="fa">
<head>
  <meta charset="UTF-8">
  <title>🎲 بازی حدس عدد</title>
  <style>
    body {
      ont-family: sans-serif;
      background: linear-gradient(135deg, #fbc2eb, #a6c1ee);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      text-align: center;
    }
    h1 {
      margin-bottom: 10px;
    }
    input {
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 8px;
      text-align: center;
      width: 80px;
      font-size: 18px;
    }
    button {
      padding: 8px 16px;
      margin: 10px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      background: #333;
      color: white;
      transition: 0.3s;
    }
    button:hover {
      background: #555;
    }
    #message {
      font-size: 18px;
      margin-top: 10px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <h1>🎲 بازی حدس عدد</h1>
  <p>یک عدد بین 1 تا 100 انتخاب کن!</p>
  <input type="number" id="guess" min="1" max="100">
  <button onclick="checkGuess()">حدس بزن</button>
  <button onclick="resetGame()">بازی جدید</button>
  <div id="message"></div>

  <script>
    let secretNumber, attempts;
    resetGame();

    function resetGame() {
      secretNumber = Math.floor(Math.random() * 100) + 1;
      attempts = 0;
      document.getElementById("message").textContent = "بازی شروع شد!";
      document.getElementById("guess").value = "";
    }

    function checkGuess() {
      const guess = parseInt(document.getElementById("guess").value);
      if (!guess || guess < 1 || guess > 100) {
        document.getElementById("message").textContent = "⚠️ لطفاً عددی بین 1 تا 100 وارد کن!";
        return;
      }
      attempts++;
      if (guess === secretNumber) {
        document.getElementById("message").textContent = `🎉 آفرین! عدد درست ${secretNumber} بود. تعداد تلاش‌ها: ${attempts}`;
      } else if (guess > secretNumber) {
        document.getElementById("message").textContent = "⬇️ عدد کوچکتر است!";
      } else {
        document.getElementById("message").textContent = "⬆️ عدد بزرگتر است!";
      }
    }
  </script>
</body>
</html>
