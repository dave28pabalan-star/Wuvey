<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>wuv wuv</title>
<style>
* { box-sizing: border-box; margin:0; padding:0; }

body {
  margin: 0;
  height: 100vh;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(135deg, #ff758c, #ff7eb3);
  font-family: Arial, Helvetica, sans-serif;
}

/* ENVELOPE */
.envelope {
  width: 260px;
  height: 180px;
  background: #ff4d6d;
  position: relative;
  border-radius: 10px;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
}

.envelope::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 0;
  height: 0;
  border-left: 130px solid transparent;
  border-right: 130px solid transparent;
  border-top: 90px solid #ff6f91;
}

.envelope span {
  position: absolute;
  bottom: 20px;
  width: 100%;
  text-align: center;
  color: white;
  font-size: 18px;
  font-weight: bold;
}

/* HIDDEN CLASS */
.hidden { display: none; }

/* CARD */
.card {
  background: rgba(255, 255, 255, 0.25);
  padding: 30px;
  border-radius: 20px;
  text-align: center;
  width: 320px;
  color: white;
  box-shadow: 0 10px 30px rgba(0,0,0,0.25);
  z-index: 10;
}

#valentineGif {
  width: 250px; /* adjusted size */
  height: auto;
  margin-bottom: 20px;
  border-radius: 15px;
}

h1 {
  margin-bottom: 25px;
}

.buttonContainer {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin-top: 15px;
  position: relative;
}

button {
  padding: 12px 28px;
  font-size: 16px;
  border: none;
  border-radius: 25px;
  cursor: pointer;
  transition: transform 0.2s ease;
}

#yesBtn {
  background-color: #ff4d6d;
  color: white;
}

#noBtn {
  background-color: white;
  color: #ff4d6d;
  position: relative;
}

#message {
  display: none;
  margin-top: 18px;
  font-size: 15px;
  background: white;       /* white background */
  color: #333;             /* dark text for readability */
  text-align: justify;     /* justified text */
  padding: 15px 20px;
  border-radius: 12px;
  max-height: 250px;       /* scrollable if content is long */
  overflow-y: auto;
  box-shadow: 0 5px 15px rgba(0,0,0,0.1);
  line-height: 1.6;
}

#wuv {
  width: 200px;
  height: 200px;
  object-fit: cover;
  border-radius: 12px; /* optional, remove if you want sharp square */
}

/* Floating hearts */
.heart {
  position: absolute;
  bottom: -20px;
  font-size: 20px;
  animation: floatUp 6s linear infinite;
}

@keyframes floatUp {
  from { transform: translateY(0); opacity: 1; }
  to { transform: translateY(-110vh); opacity: 0; }
}

/* Confetti */
.confetti {
  position: absolute;
  width: 8px;
  height: 14px;
  top: -20px;
  animation: fall 3s linear infinite;
}

@keyframes fall {
  to { transform: translateY(110vh) rotate(360deg); opacity: 0; }
}
</style>
</head>
<body>

<!-- Background Music -->
<audio id="bgMusic" loop autoplay>
  <source src="Taylor Swift - Sweet Nothing (Instrumental).mp3" type="audio/mpeg">
</audio>

<!-- ENVELOPE -->
<div id="envelope" class="envelope">
  <span>OPEN 💌</span>
</div>

<!-- CARD -->
<div class="card hidden">
    <img id="valentineGif" src="https://c.tenor.com/0XRsTAxjMwwAAAAC/tenor.gif" alt="Valentine GIF">
  <h1>Will you be my Valentine? 💖</h1>

  <div class="buttonContainer">
    <button id="yesBtn">Yes 😍</button>
    <button id="noBtn">No 😅</button>
  </div>

<div id="message">
  <img id="wuv" src="wuv.jpg">
  <p>Yayy ! I love you so much💕</p>
  <p>Happy motmot and advance happy valentines🌹</p>
  <p>Mwaaaaaaaaaaaaaaaaaaa 😘</p>
</div>


  </div>
</div>

<script>
const envelope = document.getElementById("envelope");
const card = document.querySelector(".card");
const noBtn = document.getElementById("noBtn");
const yesBtn = document.getElementById("yesBtn");
const message = document.getElementById("message");
const music = document.getElementById("bgMusic");

// OPEN ENVELOPE -> SHOW CARD
envelope.addEventListener("click", () => {
  envelope.classList.add("hidden");
  card.classList.remove("hidden");
});

// Move "No" button
noBtn.addEventListener("mouseover", () => {
  const x = Math.random() * 600 - 400; 
  const y = Math.random() * 200 - 100;
  noBtn.style.transform = `translate(${x}px, ${y}px)`;
});

// YES button action
yesBtn.addEventListener("click", () => {
  // Hide question and buttons
  document.querySelector("h1").style.display = "none"; // hides "Will you be my Valentine?"
  yesBtn.style.display = "none"; // hides YES button
  noBtn.style.display = "none";  // hides NO button
  
  // Show message
  message.style.display = "block";

  // Play music and start confetti
  music.play();
  startConfetti();
});


// Floating hearts
function createHeart() {
  const heart = document.createElement("div");
  heart.className = "heart";
  heart.innerHTML = "💖";
  heart.style.left = Math.random() * 100 + "vw";
  heart.style.fontSize = Math.random() * 20 + 15 + "px";
  heart.style.animationDuration = Math.random() * 3 + 4 + "s";
  document.body.appendChild(heart);
  setTimeout(() => heart.remove(), 7000);
}
setInterval(createHeart, 400);

// Confetti generator
function startConfetti() {
  setInterval(() => {
    const confetti = document.createElement("div");
    confetti.className = "confetti";
    const colors = ["#ff4d6d", "#ffd166", "#06d6a0", "#4dabf7", "#ffffff"];
    confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
    confetti.style.left = Math.random() * 100 + "vw";
    confetti.style.animationDuration = Math.random() * 2 + 2 + "s";
    document.body.appendChild(confetti);
    setTimeout(() => confetti.remove(), 4000);
  }, 150);
}
</script>

</body>
</html>
