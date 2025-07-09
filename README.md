<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Animated Intro</title>
  <style>
    body, html {
      margin: 0;
      padding: 0;
      height: 100%;
      overflow: hidden;
      background-color: black;
    }
    .video-background {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      z-index: -1;
      pointer-events: none;
    }
    .video-background iframe {
      width: 100%;
      height: 100%;
    }
    .title {
      font-size: 4rem;
      font-family: 'Arial', sans-serif;
      text-align: center;
      color: #7e0303;
      text-shadow: 3px 3px 5px rgba(0, 0, 0, 0.7);
      position: absolute;
      top: 45%;
      left: 50%;
      transform: translate(-50%, -50%);
      opacity: 0;
      animation: fadeIn 2s ease-out forwards, slideUp 2s ease-in-out 2.5s forwards;
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: translate(-50%, -60%) scale(0.8); }
      to { opacity: 1; transform: translate(-50%, -50%) scale(1); }
    }
    @keyframes slideUp {
      from { transform: translate(-50%, -50%); opacity: 1; }
      to { transform: translate(-50%, -200%); opacity: 0; }
    }
    .footer {
      position: absolute;
      bottom: 10px;
      left: 50%;
      transform: translateX(-50%);
      color: #FFFFFF;
      font-size: 1rem;
      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7);
    }
  </style>
</head>
<body>
  <div class="video-background">
    <iframe 
      src="https://www.youtube.com/embed/psGD5LiHffQ?autoplay=1&mute=1&loop=1&playlist=psGD5LiHffQ&controls=0&showinfo=0&modestbranding=1" 
      frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
  </div>
  <div class="title" id="introText"></div>
  <script>
    const messages = [
      "Hi, I'm Matthew",
      "I'm a Discord developer on Top Life server"
    ];
    let index = 0;
    const textEl = document.getElementById('introText');

    function showNext() {
      textEl.textContent = messages[index];
      textEl.style.animation = 'none';
      // trigger reflow to restart animation
      void textEl.offsetWidth;
      textEl.style.animation = 'fadeIn 2s ease-out forwards, slideUp 2s ease-in-out 2.5s forwards';
      index = (index + 1) % messages.length;
    }

    // show first immediately
    showNext();
    // change every 4 seconds
    setInterval(showNext, 4000);
  </script>
  <div class="footer">Developer Matthew</div>
</body>
</html>
