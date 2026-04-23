<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Mehr Birthday</title>

<style>
body {
    margin: 0;
    font-family: 'Segoe UI', sans-serif;
    text-align: center;
    background: linear-gradient(to right, #ffdde1, #ee9ca7);
    color: #333;
    overflow: hidden;
}

.container {
    padding: 50px;
    position: relative;
    z-index: 2;
}

button {
    padding: 15px 30px;
    margin: 10px;
    font-size: 18px;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    background: #ff6f91;
    color: white;
    transition: 0.3s;
}

button:hover { background: #ff3e6c; }

input {
    padding: 10px;
    font-size: 16px;
    border-radius: 8px;
    border: none;
    margin-top: 20px;
}

.hidden { display: none; }

.decor {
    font-size: 40px;
    margin: 20px 0;
}

/* Floating hearts */
.hearts span {
    position: absolute;
    bottom: -50px;
    font-size: 20px;
    animation: floatUp 8s linear infinite;
    opacity: 0.7;
}

@keyframes floatUp {
    0% { transform: translateY(0) scale(1); opacity: 0.7; }
    100% { transform: translateY(-100vh) scale(1.5); opacity: 0; }
}

/* Click burst hearts */
.burst {
    position: absolute;
    font-size: 18px;
    pointer-events: none;
    animation: burstAnim 800ms ease-out forwards;
}

@keyframes burstAnim {
    0% {
        transform: translate(0,0) scale(1);
        opacity: 1;
    }
    100% {
        transform: translate(var(--x), var(--y)) scale(1.8);
        opacity: 0;
    }
}
</style>
</head>

<body>

<div class="hearts" id="hearts"></div>

<div class="container" id="page1">
    <h1>Are u MEHR?</h1>
    <button onclick="goToPassword()">YES</button>
    <button onclick="alert('Access Denied 😜')">NO</button>
</div>

<div class="container hidden" id="page2">
    <h2>Enter Password 🔐</h2>
    <input type="password" id="password" placeholder="Enter password">
    <br>
    <button onclick="checkPassword()">Submit</button>
</div>

<div class="container hidden" id="page3">
    <h1>MEHR KA BIRTHDAY 🎂</h1>

    <div class="decor">🌸🌺🌼🎂🍰🍭🍬🍩🍦🍨</div>

    <p style="max-width:700px;margin:auto;font-size:18px;line-height:1.6;">
        I don't know where to start 😅 but <br>
        I will try to express what I feel (I am not good at it) <br><br>

        I know tujhe bohot log mile hoge joh tujhe paragraph likhe coz u look beautiful 🥰🥰. 
        When I didn't know you, I also thought that you are a girl who has attitude or ego, 
        but after I spent some time with you (not much but still), you are one of the nicest 
        person I have ever met. You are so humble and nice. Behind that beautiful face, 
        you also have a very kind heart. I hope/wish this friendship never ends 😭 <br><br>

        And till now you helped me a lot — thank you for all of this 💛 <br><br>

        <b>AND LAST BUT NOT THE LEAST</b> <br><br>

        🎉 HAPPY BIRTHDAY MEHE 🎂🍮🥮🍧🍦🍨🥛🍶🍹🍸🫗🥃🍷🍬🍿
    </p>

    <div class="decor">🌷🌹💐🎂🍰🍫🍪🍩🍭</div>
</div>

<script>
function goToPassword() {
    document.getElementById('page1').classList.add('hidden');
    document.getElementById('page2').classList.remove('hidden');
}

function checkPassword() {
    var pass = document.getElementById('password').value;
    if (pass === "Justin") {
        document.getElementById('page2').classList.add('hidden');
        document.getElementById('page3').classList.remove('hidden');
    } else {
        alert("Wrong password 😅");
    }
}

/* Floating hearts generator */
function createHearts() {
    const container = document.getElementById('hearts');

    setInterval(() => {
        const heart = document.createElement('span');
        heart.innerHTML = Math.random() > 0.5 ? '❤️' : '🌸';
        heart.style.left = Math.random() * 100 + 'vw';
        heart.style.fontSize = (15 + Math.random() * 25) + 'px';
        heart.style.animationDuration = (5 + Math.random() * 5) + 's';

        container.appendChild(heart);

        setTimeout(() => heart.remove(), 8000);
    }, 300);
}
createHearts();

/* Click burst effect */
document.addEventListener("click", function(e) {
    for (let i = 0; i < 8; i++) {
        const burst = document.createElement("span");
        burst.className = "burst";
        burst.innerHTML = Math.random() > 0.5 ? "❤️" : "🌸";

        burst.style.left = e.clientX + "px";
        burst.style.top = e.clientY + "px";

        const x = (Math.random() - 0.5) * 150 + "px";
        const y = (Math.random() - 0.5) * 150 + "px";

        burst.style.setProperty("--x", x);
        burst.style.setProperty("--y", y);

        document.body.appendChild(burst);

        setTimeout(() => burst.remove(), 800);
    }
});
</script>

</body>
</html>
