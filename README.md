<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Morgan, Will You Be My Valentine?</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #ff758c, #ff7eb3);
      font-family: 'Arial', sans-serif;
      color: white;
      text-align: center;
      overflow: hidden;
    }

    .card {
      background: rgba(255, 255, 255, 0.15);
      padding: 40px 60px;
      border-radius: 20px;
      box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
      backdrop-filter: blur(8px);
      z-index: 2;
    }

    h1 {
      font-size: 2.5rem;
      margin-bottom: 30px;
    }

    .buttons {
      display: flex;
      gap: 30px;
      justify-content: center;
      position: relative;
    }

    button {
      font-size: 1.2rem;
      padding: 12px 30px;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      transition: transform 0.2s ease, box-shadow 0.2s ease;
    }

    #yesBtn {
      background-color: #2ecc71;
      color: white;
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
    }

    #yesBtn:hover {
      transform: scale(1.1);
    }

    #noBtn {
      background-color: #e74c3c;
      color: white;
      position: absolute;
    }

    .message {
      margin-top: 25px;
      font-size: 1.6rem;
      display: none;
    }

    /* Floating hearts */
    .heart {
      position: fixed;
      bottom: -20px;
      font-size: 20px;
      animation: floatUp linear forwards;
      opacity: 0.8;
    }

    @keyframes floatUp {
      from {
        transform: translateY(0) scale(1);
        opacity: 1;
      }
      to {
        transform: translateY(-110vh) scale(1.5);
        opacity: 0;
      }
    }

    /* Confetti */
    .confetti {
      position: fixed;
      top: -10px;
      width: 10px;
      height: 10px;
      animation: fall 3s linear forwards;
    }

    @keyframes fall {
      to {
        transform: translateY(110vh) rotate(360deg);
      }
    }
  </style>
</head>
<body>
  <div class="card">
    <h1>Morgan 💖<br>Will you be my Valentine?</h1>
    <div class="buttons">
      <button id="yesBtn">Yes 💕</button>
      <button id="noBtn">No 😅</button>
    </div>
    <div class="message" id="message">Yay Morgan! 💘 I knew you'd say yes! 🎉</div>
  </div>

  <!-- Romantic music -->
  <audio id="loveSong" preload="auto">
    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
  </audio>

  <script>
    const noBtn = document.getElementById('noBtn');
    const yesBtn = document.getElementById('yesBtn');
    const message = document.getElementById('message');
    const song = document.getElementById('loveSong');

    function moveNoButton() {
      const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
      const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
      noBtn.style.left = `${x}px`;
      noBtn.style.top = `${y}px`;
    }

    noBtn.addEventListener('mouseover', moveNoButton);
    noBtn.addEventListener('click', moveNoButton);

    // Floating hearts continuously
    setInterval(() => {
      const heart = document.createElement('div');
      heart.className = 'heart';
      heart.innerText = '💖';
      heart.style.left = Math.random() * 100 + 'vw';
      heart.style.animationDuration = 3 + Math.random() * 3 + 's';
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 6000);
    }, 300);

    function launchConfetti() {
      for (let i = 0; i < 120; i++) {
        const confetti = document.createElement('div');
        confetti.className = 'confetti';
        confetti.style.left = Math.random() * 100 + 'vw';
        confetti.style.backgroundColor = `hsl(${Math.random() * 360}, 100%, 70%)`;
        confetti.style.animationDuration = 2 + Math.random() * 2 + 's';
        document.body.appendChild(confetti);
        setTimeout(() => confetti.remove(), 4000);
      }
    }

    yesBtn.addEventListener('click', () => {
      message.style.display = 'block';
      song.currentTime = 0;
      song.play();
      launchConfetti();
    });
  </script>
</body>
</html>
