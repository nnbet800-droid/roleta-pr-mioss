<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>Super Roleta Premiada</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body {
  font-family: Arial, sans-serif;
  background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
  color: #fff;
  text-align: center;
  padding: 20px;
}

.box {
  background: #111;
  border-radius: 12px;
  padding: 25px;
  max-width: 420px;
  margin: auto;
  box-shadow: 0 0 20px rgba(0,0,0,0.6);
}

h1 {
  color: #ffd700;
}

.pointer {
  width: 0;
  height: 0;
  border-left: 15px solid transparent;
  border-right: 15px solid transparent;
  border-bottom: 30px solid #ffd700;
  margin: auto;
}

#wheel {
  width: 300px;
  height: 300px;
  border-radius: 50%;
  margin: 20px auto;
  border: 8px solid #ffd700;
  position: relative;
  transition: transform 4s cubic-bezier(.17,.67,.32,1.34);
}

.segment {
  position: absolute;
  width: 50%;
  height: 50%;
  top: 50%;
  left: 50%;
  transform-origin: 0% 0%;
  text-align: right;
  padding-right: 10px;
  font-size: 12px;
  font-weight: bold;
}

button {
  background: #ff9800;
  border: none;
  color: #000;
  font-weight: bold;
  padding: 15px 25px;
  border-radius: 8px;
  cursor: pointer;
  font-size: 16px;
}

#resultado {
  margin-top: 20px;
  font-size: 18px;
  font-weight: bold;
  color: #00ff99;
}

.whatsapp {
  display: none;
  margin-top: 15px;
  background: #25d366;
  padding: 15px;
  border-radius: 8px;
  color: #000;
  text-decoration: none;
  font-weight: bold;
}
</style>
</head>

<body>

<div class="box">
  <h1>🎰 SUPER ROLETA PREMIADA</h1>
  <p>Gire a roleta e concorra a prêmios 💰</p>

  <div class="pointer"></div>
  <div id="wheel"></div>

  <button onclick="girar()" id="btn">👉 GIRAR A ROLETA</button>

  <div id="resultado"></div>
  <a id="whats" class="whatsapp" target="_blank">💬 RECEBER NO WHATSAPP</a>
</div>

<script>
const premios = [
  "BANCA 25",
  "BANCA 20",
  "2 DIAS BANCA 15",
  "2 DIAS BANCA 10",
  "TENTE NOVAMENTE",
  "TENTE NOVAMENTE",
  "TENTE NOVAMENTE"
];

const cores = [
  "#ff9800","#4caf50","#2196f3",
  "#9c27b0","#f44336","#607d8b","#795548"
];

const wheel = document.getElementById("wheel");

premios.forEach((p, i) => {
  const seg = document.createElement("div");
  seg.className = "segment";
  seg.style.transform = `rotate(${i * (360/premios.length)}deg)`;
  seg.style.color = "#fff";
  seg.innerHTML = p;
  wheel.appendChild(seg);
  wheel.style.background = `conic-gradient(${cores.join(",")})`;
});

let girou = false;

function girar() {
  if (girou) return;
  girou = true;

  const grau = Math.floor(3600 + Math.random() * 360);
  wheel.style.transform = `rotate(${grau}deg)`;

  const premio = premios[Math.floor(Math.random() * premios.length)];

  setTimeout(() => {
    document.getElementById("resultado").innerHTML =
      `🎉 VOCÊ GANHOU:<br>${premio}`;

    const msg = encodeURIComponent(
      `Oi! Ganhei na Super Roleta 🎰\nMeu prêmio foi: ${premio}`
    );

    const wpp = document.getElementById("whats");
    wpp.href = `https://wa.me/5598985941895?text=${msg}`;
    wpp.style.display = "block";
  }, 4200);
}
</script>

</body>
</html>
