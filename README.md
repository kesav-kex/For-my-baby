<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>For my wifey</title>
  <style>
    body {
      margin: 0; padding: 0;
      background: linear-gradient(135deg, #ffdde1, #ee9ca7);
      font-family: 'Segoe UI', sans-serif;
      display: flex;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      overflow: hidden;
      position: relative;
    }
    .message-box {
      background: white;
      padding: 2rem;
      border-radius: 20px;
      box-shadow: 0 0 30px rgba(0,0,0,0.1);
      max-width: 400px;
      text-align: center;
      animation: fadeIn 2s ease;
      z-index: 10;
      position: relative;
    }
    .message-box h1 {
      color: #ff4b91;
      font-size: 2rem;
      margin-bottom: 1rem;
    }
    .message-box p {
      font-size: 1.1rem;
      color: #444;
      line-height: 1.6;
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: scale(0.9); }
      to { opacity: 1; transform: scale(1); }
    }

    /* Heart & Love emoji styles */
    .floating {
      position: absolute;
      font-size: 24px;
      user-select: none;
      animation-name: fall;
      animation-timing-function: linear;
      animation-iteration-count: infinite;
      pointer-events: none;
      opacity: 0.9;
      will-change: transform;
    }
    @keyframes fall {
      0% {
        transform: translateY(-10vh) rotate(0deg);
        opacity: 1;
      }
      100% {
        transform: translateY(110vh) rotate(360deg);
        opacity: 0;
      }
    }
  </style>
</head>
<body>

  <div class="message-box" role="main" aria-label="Love message">
    <h1>Dear wifey ❤️</h1>
    <p>
      I need you to run to me when things get hard, babie.<br><br>
      No matter how tough life gets, let’s promise to hold each other close — never letting go.<br><br>
      You and me, vavee… we’ll grow together, laugh together, cry together, and love harder every day.<br><br>
      I’ll be your safe place. Your peace. Your forever.<br><br>
      My love for you will never fade. Not in this life or any other.<br><br>
      I love you so, so much — with every beat of my heart.<br><br>
      Always yours,<br>
      <strong>Keshu 💘</strong>
    </p>
  </div>

  <!-- Audio music -->
  <audio id="bg-music" autoplay loop muted>
    <source src="https://cdn.pixabay.com/download/audio/2022/03/29/audio_5b5101793a.mp3?filename=romantic-melody-7124.mp3" type="audio/mpeg" />
    Your browser does not support the audio element.
  </audio>

  <script>
    // Array of emojis for floating
    const emojis = ['❤️', '💖', '💕', '❣️', '💘', '💝'];

    // Function to create a floating emoji
    function createFloatingEmoji() {
      const span = document.createElement('span');
      span.classList.add('floating');

      // Randomly choose heart shape or emoji
      const useHeartShape = Math.random() < 0.5;
      if (useHeartShape) {
        // Create a styled heart div for the classic heart shape
        span.textContent = emojis[Math.floor(Math.random() * emojis.length)];
      } else {
        // Just use emoji from array
        span.textContent = emojis[Math.floor(Math.random() * emojis.length)];
      }

      // Random horizontal position
      span.style.left = Math.random() * 100 + 'vw';

      // Random size between 18px and 30px
      span.style.fontSize = (18 + Math.random() * 12) + 'px';

      // Random animation duration between 6 and 12 seconds
      const duration = 6 + Math.random() * 6;
      span.style.animationDuration = duration + 's';

      // Random animation delay (so they don't all start together)
      span.style.animationDelay = '-' + Math.random() * duration + 's';

      document.body.appendChild(span);

      // Remove after animation finishes to keep DOM clean
      setTimeout(() => {
        span.remove();
      }, duration * 1000);
    }

    // Create lots of hearts and love emojis falling continuously
    setInterval(createFloatingEmoji, 200);

    // Unmute audio on first user interaction (required for autoplay with sound)
    function enableSound() {
      const audio = document.getElementById('bg-music');
      if(audio.muted) {
        audio.muted = 1;
        audio.volume = 0.7; // set volume to comfortable level
      }
      window.removeEventListener('click', enableSound);
      window.removeEventListener('touchstart', enableSound);
    }
    window.addEventListener('click', enableSound);
    window.addEventListener('touchstart', enableSound);
  </script>

</body>
</html>
