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

.container { padding: 50px; position: relative; z-index: 2; }

button {
    padding: 15px 30px;
    margin: 10px;
    font-size: 18px;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    background: #ff6f91;
    color: white;
}

input {
    padding: 10px;
    font-size: 16px;
    border-radius: 8px;
    border: none;
    margin-top: 20px;
}

.hidden { display: none; }

.hearts span {
    position: absolute;
    bottom: -50px;
    animation: floatUp 8s linear infinite;
}

@keyframes floatUp {
    100% { transform: translateY(-100vh); opacity: 0; }
}

.burst {
    position: absolute;
    pointer-events: none;
    animation: burst 0.8s forwards;
}

@keyframes burst {
    to {
        transform: translate(var(--x), var(--y));
        opacity: 0;
    }
}
</style>
</head>

<body>

<div id="hearts"></div>

<div id="page1">
    <h1>Are u MEHR?</h1>
    <button onclick="goToPassword()">YES</button>
    <button onclick="alert('Access Denied 😜')">NO</button>
</div>

<div id="page2" class="hidden">
    <h2>Enter Password 🔐</h2>
    <input type="password" id="password">
    <br>
    <button onclick="checkPassword()">Submit</button>
</div>

<div id="page3" class="hidden">
    <h1>MEHR KA BIRTHDAY 🎂</h1>
    <p>🎉 HAPPY BIRTHDAY MEHE 🎂❤️</p>
</div>

<script>
function goToPassword() {
    page1.style.display = "none";
    page2.style.display = "block";
}

function checkPassword() {
    if (password.value === "Justin") {
        page2.style.display = "none";
        page3.style.display = "block";
    } else {
        alert("Wrong password");
    }
}

/* floating hearts */
setInterval(() => {
    let h = document.createElement("span");
    h.innerHTML = Math.random() > 0.5 ? "❤️" : "🌸";
    h.style.left = Math.random()*100 + "vw";
    document.body.appendChild(h);
    setTimeout(()=>h.remove(),8000);
},300);

/* click burst */
document.onclick = e => {
    for(let i=0;i<6;i++){
        let b = document.createElement("span");
        b.className="burst";
        b.innerHTML="❤️";
        b.style.left=e.clientX+"px";
        b.style.top=e.clientY+"px";
        b.style.setProperty("--x",(Math.random()*100-50)+"px");
        b.style.setProperty("--y",(Math.random()*100-50)+"px");
        document.body.appendChild(b);
        setTimeout(()=>b.remove(),800);
    }
};
</script>

</body>
</html>
