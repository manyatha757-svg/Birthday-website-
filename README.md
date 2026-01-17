<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Unlock Your Birthday 🎂</title>

  <!-- Cute font -->
  <link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@500;600;700&display=swap" rel="stylesheet">

  <style>
    body {
      background: linear-gradient(135deg, #fde68a, #fbcfe8, #bfdbfe);
      font-family: 'Quicksand', sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      overflow: hidden;
    }

    .box {
      background: white;
      padding: 32px;
      border-radius: 26px;
      width: 340px;
      text-align: center;
      box-shadow: 0 15px 35px rgba(0,0,0,0.15);
      z-index: 2;
    }

    h2 {
      color: #f59e0b;
    }

    h1 {
      color: #ec4899;
    }

    p {
      color: #374151;
      line-height: 1.5;
    }

    input {
      padding: 11px;
      width: 85%;
      border-radius: 14px;
      border: 1px solid #d1d5db;
      margin-top: 12px;
      font-size: 14px;
      font-family: 'Quicksand', sans-serif;
    }

    button {
      margin-top: 16px;
      padding: 10px 26px;
      border: none;
      border-radius: 999px;
      background: #fbcfe8;
      cursor: pointer;
      font-size: 14px;
      font-family: 'Quicksand', sans-serif;
    }

    button:hover {
      background: #f9a8d4;
    }

    .msg {
      margin-top: 14px;
      font-size: 13px;
      color: #ef4444;
    }

    /* CONFETTI */
    .confetti {
      position: fixed;
      width: 10px;
      height: 10px;
      top: -10px;
      animation: fall linear infinite;
    }

    @keyframes fall {
      to {
        transform: translateY(110vh) rotate(360deg);
      }
    }
  </style>
</head>
<body>

<div class="box" id="game">
  <h2>Riddle 1 🧩✨</h2>
  <p>What comes once in a minute, twice in a moment, but never in a thousand years?</p>
  <input id="answer" placeholder="type your answer 💭">
  <button onclick="check()">Submit 🚀</button>
  <p class="msg" id="msg"></p>
</div>

<script>
let level = 1;

function check() {
  const ans = document.getElementById("answer").value.toLowerCase().trim();
  const msg = document.getElementById("msg");

  if (level === 1 && (ans === "m" || ans === "letter m")) {
    level = 2;
    next(
      "Riddle 2 🧠💥",
      "What is the next number in the sequence?\n1, 1, 2, 3, 5, 8, ?"
    );
  }

  else if (level === 2 && ans === "13") {
    level = 3;
    next(
      "Riddle 3 🤓✨",
      "What is Sheldon’s favorite number?"
    );
  }

  else if (level === 3 && ans === "73") {
    level = 4;
    next(
      "Riddle 4 💄✨",
      "What is Penny’s last name in the early seasons?"
    );
  }

  else if (level === 4 && ans === "teller") {
    celebrate();
    document.getElementById("game").innerHTML = `
      <h1>🎉 Happy 18th 🎉</h1>
      <p>
        🥳 Bazinga!! You cracked them all 😌!!<br><br>
        🎂 Happiesttt birthday Ashweeeeeen !!! 💖<br>
        ✨ Always be your gorgeous self you are ✨<br><br>
         (Thank you for everything!!!<br>
        and sorry because you have a dumb bestfriend..) 😭💗
      </p>`;
  }

  else {
    if (level === 2) {
      msg.innerText = "Sheldon’s already judging you… 👀";
    } else if (level === 4) {
      msg.innerText = "The answer’s Teller 😌";
    } else {
      msg.innerText = "nopeee… try again 👀";
    }
  }
}

function next(title, text) {
  document.querySelector("h2").innerText = title;
  document.querySelector("p").innerText = text;
  document.getElementById("answer").value = "";
  document.getElementById("msg").innerText = "";
}

function celebrate() {
  for (let i = 0; i < 80; i++) {
    const conf = document.createElement("div");
    conf.className = "confetti";
    conf.style.left = Math.random() * 100 + "vw";
    conf.style.background = `hsl(${Math.random()*360}, 100%, 70%)`;
    conf.style.animationDuration = (Math.random() * 3 + 2) + "s";
    document.body.appendChild(conf);
  }
}
</script>

</body>
</html>
