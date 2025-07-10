# cmsn
<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <title>🎂 Sinh nhật Kiều Anh 🎂</title>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      background: radial-gradient(circle, #1a001a, #000);
      overflow: hidden;
      height: 100vh;
      color: #ffccff;
      font-family: 'Segoe UI', sans-serif;
    }

    .center {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      font-size: 60px;
      font-weight: bold;
      opacity: 0;
      animation: fadeIn 1s ease forwards;
      text-align: center;
      text-shadow: 0 0 10px #ff00cc, 0 0 20px #ff99cc;
      z-index: 2;
    }

    @keyframes fadeIn {
      to {
        opacity: 1;
      }
    }

    .confetti {
      position: absolute;
      width: 8px;
      height: 8px;
      background: pink;
      top: -10px;
      animation: fall linear infinite;
      opacity: 0.8;
      border-radius: 50%;
      z-index: 0;
    }

    @keyframes fall {
      to {
        transform: translateY(110vh) rotate(360deg);
        opacity: 0;
      }
    }
  </style>
</head>
<body>

  <div id="text" class="center"></div>

  <script>
    const messages = [
      "3", "2", "1",
      "🎉 Happy Birthday 🎉",
      "💖 Kiều Anh 💖",
      "🎂 10 - 07 - 2005 🎂",
      "✨ Chúc chị tuổi mới xinh đẹp, thành công! ✨"
    ];

    const textEl = document.getElementById('text');

    let index = 0;
    function showNext() {
      textEl.style.opacity = 0;
      setTimeout(() => {
        textEl.innerHTML = messages[index];
        textEl.style.animation = 'none';
        void textEl.offsetWidth;
        textEl.style.animation = 'fadeIn 1s ease forwards';
        index++;
        if (index < messages.length) {
          setTimeout(showNext, 2000);
        }
      }, 500);
    }

    showNext();

    function createConfetti() {
      const confetti = document.createElement('div');
      confetti.classList.add('confetti');
      confetti.style.left = Math.random() * 100 + 'vw';
      confetti.style.animationDuration = 2 + Math.random() * 3 + 's';
      confetti.style.background = ['#ff99cc', '#ff66cc', '#ff3399'][Math.floor(Math.random() * 3)];
      document.body.appendChild(confetti);
      setTimeout(() => confetti.remove(), 6000);
    }

    setInterval(createConfetti, 100);
  </script>

</body>
</html>
