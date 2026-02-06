<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Be My Valentine?</title>

  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">

  <style>
    body {
      margin: 0;
      height: 100vh;
      background: #800020;
      display: flex;
      justify-content: center;
      align-items: center;
      font-family: 'Poppins', sans-serif;
      overflow: hidden;
    }

    #app {
      width: 100%;
      height: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
    }

    .card {
      background: #fff;
      padding: 40px 50px;
      border-radius: 20px;
      text-align: center;
      box-shadow: 0 20px 40px rgba(0,0,0,0.3);
      width: 320px;
      z-index: 2;
    }

    h1 {
      color: #800020;
      margin-bottom: 30px;
    }

    .buttons {
      position: relative;
      height: 80px;
    }

    button {
      padding: 12px 28px;
      border: none;
      border-radius: 30px;
      font-size: 18px;
      cursor: pointer;
      position: absolute;
      transition: transform 0.25s ease;
    }

    #yesBtn {
      background: #800020;
      color: white;
      left: 50%;
      transform: translateX(-120%);
    }

    #noBtn {
      background: #ddd;
      left: 50%;
      transform: translateX(20%);
    }

    .heart {
      position: absolute;
      bottom: -20px;
      font-size: 24px;
      animation: floatUp linear infinite;
      opacity: 0.9;
      pointer-events: none;
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
  </style>
</head>

<body>

<div id="app">
  <div class="card">
    <h1>Will you be my Valentine? 🥺</h1>
    <div class="buttons">
      <button id="yesBtn">Yes 💘</button>
      <button id="noBtn">No 😭</button>
    </div>
  </div>
</div>

<script>
  const app = document.getElementById("app");
  const noBtn = document.getElementById("noBtn");
  const yesBtn = document.getElementById("yesBtn");

  let noScale = 1;
  let yesScale = 1;
  let posX = 0;
  let posY = 0;

  function moveNo() {
    posX = Math.random() * 220 - 110;
    posY = Math.random() * 120 - 60;
    noBtn.style.transform = `translate(${posX}px, ${posY}px) scale(${noScale})`;
  }

  noBtn.addEventListener("mouseenter", moveNo);
  noBtn.addEventListener("touchstart", moveNo);

  noBtn.addEventListener("click", () => {
    noScale = Math.max(0.4, noScale - 0.15);
    yesScale += 0.15;
    noBtn.style.transform = `translate(${posX}px, ${posY}px) scale(${noScale})`;
    yesBtn.style.transform = `translateX(-120%) scale(${yesScale})`;
  });

  yesBtn.addEventListener("click", () => {
    app.innerHTML = `
      <div style="
        width:100%;
        height:100%;
        display:flex;
        justify-content:center;
        align-items:center;
        text-align:center;
        background:#800020;
      ">
        <div style="
          background:white;
          padding:40px;
          border-radius:20px;
          font-size:2.5rem;
          color:#800020;
        ">
          YAYYY 💖🥰<br><br>
          My Kiddoo!!! 🎀<br>
          You’re my Valentineee!!! 💝💕
        </div>
      </div>
    `;
    createHearts();
  });

  function createHearts() {
    setInterval(() => {
      const heart = document.createElement("div");
      heart.className = "heart";
      heart.textContent = "❤️";
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.animationDuration = Math.random() * 3 + 4 + "s";
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 7000);
    }, 300);
  }
</script>

</body>
</html>
