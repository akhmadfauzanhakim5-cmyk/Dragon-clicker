<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🐉 Dragon Clicker</title>

<style>
body{
    margin:0;
    font-family:Arial,sans-serif;
    background:linear-gradient(#6a5acd,#1b103d);
    color:white;
    text-align:center;
}

.container{
    max-width:700px;
    margin:auto;
    padding:20px;
}

h1{
    font-size:40px;
}

#egg{
    font-size:120px;
    cursor:pointer;
    transition:0.1s;
    user-select:none;
}

#egg:active{
    transform:scale(0.9);
}

.card{
    background:rgba(255,255,255,0.1);
    border-radius:15px;
    padding:15px;
    margin-top:20px;
}

button{
    padding:12px 20px;
    border:none;
    border-radius:10px;
    cursor:pointer;
    font-size:16px;
    margin:8px;
}

button:hover{
    transform:scale(1.05);
}

.upgrade{
    background:#ff9800;
    color:white;
}

.auto{
    background:#00bcd4;
    color:white;
}
</style>
</head>

<body>

<div class="container">

<h1>🐉 Dragon Clicker</h1>

<div id="egg">🥚</div>

<h2>🪙 Koin: <span id="coin">0</span></h2>
<h3>⭐ Level: <span id="level">1</span></h3>
<h3>⚔️ Power: <span id="power">1</span>/klik</h3>

<div class="card">
<h2>Upgrade</h2>

<button class="upgrade" onclick="buyPower()">
🔥 Upgrade Power (50 Koin)
</button>

<button class="auto" onclick="buyAuto()">
🤖 Auto Dragon (100 Koin)
</button>

</div>

</div>

<script>

let coin=0;
let power=1;
let level=1;
let auto=0;

const coinText=document.getElementById("coin");
const levelText=document.getElementById("level");
const powerText=document.getElementById("power");
const egg=document.getElementById("egg");

function update(){
    coinText.textContent=Math.floor(coin);
    level=Math.floor(coin/100)+1;
    levelText.textContent=level;
    powerText.textContent=power;

    localStorage.setItem("coin",coin);
    localStorage.setItem("power",power);
    localStorage.setItem("auto",auto);
}

egg.onclick=function(){

    coin+=power;

    egg.style.transform="scale(1.15)";

    setTimeout(()=>{
        egg.style.transform="scale(1)";
    },100);

    update();
}

function buyPower(){

    if(coin>=50){
        coin-=50;
        power++;
        update();
    }else{
        alert("Koin kurang!");
    }

}

function buyAuto(){

    if(coin>=100){
        coin-=100;
        auto++;
        update();
    }else{
        alert("Koin kurang!");
    }

}

setInterval(function(){

    coin+=auto;
    update();

},1000);

if(localStorage.getItem("coin")){
    coin=Number(localStorage.getItem("coin"));
    power=Number(localStorage.getItem("power"));
    auto=Number(localStorage.getItem("auto"));
    update();
}

update();

</script>

</body>
</html>
