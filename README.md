<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Selamat Ulang Tahun BESTY 🎉</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      overflow: hidden;
      background: linear-gradient(45deg, #ff9a9e, #fad0c4, #fbc2eb, #a6c1ee);
      background-size: 400% 400%;
      animation: gradient 10s ease infinite;
      text-align: center;
      font-family: 'Comic Sans MS', cursive;
      color: white;
    }

    @keyframes gradient {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    h1 {
      font-size: 3em;
      margin-top: 80px;
      text-shadow: 2px 2px 8px #00000050;
      animation: pop 1.5s infinite alternate;
    }

    @keyframes pop {
      from { transform: scale(1); }
      to { transform: scale(1.1); }
    }

    .cake {
      position: relative;
      margin: 50px auto;
      width: 150px;
      height: 120px;
    }

    .layer {
      position: absolute;
      background: #ff6f91;
      border-radius: 10px;
    }

    .layer:nth-child(1) {
      bottom: 0;
      width: 150px;
      height: 50px;
      background: #ff6f91;
    }

    .layer:nth-child(2) {
      bottom: 50px;
      width: 120px;
      height: 40px;
      left: 15px;
      background: #ff9671;
    }

    .layer:nth-child(3) {
      bottom: 90px;
      width: 90px;
      height: 30px;
      left: 30px;
      background: #ffc75f;
    }

    .candle {
      position: absolute;
      width: 10px;
      height: 40px;
      background: #fff;
      top: -40px;
      left: 70px;
      border-radius: 3px;
    }

    .flame {
      position: absolute;
      width: 15px;
      height: 15px;
      background: orange;
      border-radius: 50%;
      top: -15px;
      left: -2px;
      animation: flicker 0.2s infinite alternate;
    }

    @keyframes flicker {
      from { transform: scale(1) rotate(0deg); opacity: 1; }
      to { transform: scale(1.2) rotate(10deg); opacity: 0.8; }
    }

    .balloon {
      position: absolute;
      width: 50px;
      height: 60px;
      background: red;
      border-radius: 50%;
      animation: float 8s linear infinite;
    }

    @keyframes float {
      0% { transform: translateY(100vh) scale(1); opacity: 1; }
      100% { transform: translateY(-120vh) scale(1.2); opacity: 0.8; }
    }

    .message {
      font-size: 1.8em;
      margin-top: 30px;
      animation: fadeIn 3s ease forwards;
      opacity: 0;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(30px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body>

  <h1>🎉 Selamat Ulang Tahun BESTY 🎂</h1>

  <div class="cake">
    <div class="layer"></div>
    <div class="layer"></div>
    <div class="layer"></div>
    <div class="candle">
      <div class="flame"></div>
    </div>
  </div>

  <div class="message">Semoga panjang umur, sehat selalu, dan makin bahagia! 💖</div>

  <audio autoplay loop>
    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
  </audio>

  <script>
    // Generate balloons
    for (let i = 0; i < 20; i++) {
      let balloon = document.createElement("div");
      balloon.classList.add("balloon");
      balloon.style.left = Math.random() * 100 + "vw";
      balloon.style.background = `hsl(${Math.random() * 360}, 80%, 60%)`;
      balloon.style.animationDuration = 6 + Math.random() * 5 + "s";
      document.body.appendChild(balloon);
    }
  </script>
</body>
</html>
