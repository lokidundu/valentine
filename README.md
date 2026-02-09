# valentine<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Will You Be My Valentine? ❤️</title>
  <style>
    body {
      margin: 0;
      min-height: 100vh;
      background: linear-gradient(135deg, #ff758c, #ff7eb3);
      font-family: 'Segoe UI', sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      color: white;
      text-align: center;
      padding: 20px;
    }

    .card {
      background: rgba(255,255,255,0.18);
      padding: 35px;
      border-radius: 20px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.3);
      width: 100%;
      max-width: 500px;
    }

    h1 {
      margin-bottom: 15px;
    }

    .heart {
      font-size: 3rem;
      animation: beat 1s infinite;
      margin-bottom: 20px;
    }

    @keyframes beat {
      0%,100% { transform: scale(1); }
      50% { transform: scale(1.2); }
    }

    button {
      padding: 12px 25px;
      border: none;
      border-radius: 25px;
      font-size: 1rem;
      cursor: pointer;
      transition: 0.3s;
      margin: 5px;
    }

    #yesBtn {
      background: white;
      color: #ff4d6d;
    }

    #yesBtn:hover {
      transform: scale(1.1);
      background: #ffe6ec;
    }

    #noBtn {
      background: #ff4d6d;
      color: white;
      position: absolute;
    }

    .question {
      margin: 15px 0;
      text-align: left;
    }

    textarea {
      width: 100%;
      border-radius: 10px;
      border: none;
      padding: 10px;
      font-family: inherit;
      resize: none;
      margin-top: 5px;
    }

    .saveBtn {
      background: white;
      color: #ff4d6d;
      margin-top: 20px;
    }

    footer {
      margin-top: 15px;
      font-size: 0.9rem;
      opacity: 0.9;
    }
  </style>
</head>
<body>

<audio id="music" loop>
  <source src="love.mp3" type="audio/mpeg">
</audio>

<div class="card" id="card">
  <h1>Will you be my Valentine? 💘</h1>
  <div class="heart">❤️</div>

  <button id="yesBtn" onclick="yesClicked()">Yes 💕</button>
  <button id="noBtn" onmouseover="moveNo()">No 🙈</button>

  <footer>Made with love 💌</footer>
</div>

<script>
  function yesClicked() {
    document.getElementById("music").play();

    document.getElementById("card").innerHTML = `
      <h1>My Love Letter 💖</h1>
      <p>Answer these from your heart 💕</p>

      ${createQuestion("💖 What was the moment you first felt something special about us?")}
      ${createQuestion("🌸 What’s your favorite memory of us together?")}
      ${createQuestion("😊 What do you love the most about me?")}
      ${createQuestion("💕 How do I make you feel when you’re with me?")}
      ${createQuestion("🌼 What little things about me make you smile?")}
      ${createQuestion("✈️ If we could go anywhere together right now, where would you choose?")}
      ${createQuestion("🎶 What song reminds you of us?")}
      ${createQuestion("✨ What’s one dream you want us to achieve together?")}
      ${createQuestion("💗 What’s your favorite way for me to show my love?")}
      ${createQuestion("💞 What makes our relationship different from everything else?")}

      <button class="saveBtn" onclick="saveLetter()">Save My Love Letter 💌</button>
      <footer>Forever yours ❤️</footer>
    `;
  }

  function createQuestion(text) {
    return `
      <div class="question">
        <strong>${text}</strong>
        <textarea rows="2" placeholder="Type your answer here..."></textarea>
      </div>
    `;
  }

  function saveLetter() {
    const answers = document.querySelectorAll("textarea");
    let letter = "💌 My Love Letter 💖\n\n";

    answers.forEach((a, i) => {
      letter += (i+1) + ". " + a.previousElementSibling.innerText + "\n";
      letter += a.value + "\n\n";
    });

    const blob = new Blob([letter], { type: "text/plain" });
    const link = document.createElement("a");
    link.href = URL.createObjectURL(blob);
    link.download = "My_Love_Letter.txt";
    link.click();
  }

  function moveNo() {
    const noBtn = document.getElementById("noBtn");
    const x = Math.random() * 250 - 125;
    const y = Math.random() * 150 - 75;
    noBtn.style.transform = `translate(${x}px, ${y}px)`;
  }
</script>

</body>
</html>
