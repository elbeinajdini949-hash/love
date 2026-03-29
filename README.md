<!DOCTYPE html>
<html>
<head>
<title>For My Love ❤️</title>

<style>
body{
    margin:0;
    font-family: Arial;
    background: linear-gradient(135deg,#ff9a9e,#fad0c4);
    overflow:hidden;
    text-align:center;
}

.container{
    position:relative;
    top:35vh;
}

button{
    padding:12px 25px;
    font-size:18px;
    border:none;
    border-radius:10px;
    cursor:pointer;
    position:relative;
}

.yes{background:#ff4d6d;color:white;}
.no{background:#ccc;position:absolute;}

#message{
    display:none;
    font-size:26px;
    width:70%;
    margin:auto;
    color:#333;
}

/* floating hearts */
.heart{
    position:fixed;
    bottom:-20px;
    animation:float 6s linear infinite;
}

@keyframes float{
    0%{transform:translateY(0);opacity:1;}
    100%{transform:translateY(-100vh);opacity:0;}
}

/* explosion hearts */
.explosion{
    position:fixed;
    font-size:20px;
    animation:explode 1s ease-out forwards;
}

@keyframes explode{
    0%{transform:scale(0);opacity:1;}
    100%{transform:translate(var(--x),var(--y)) scale(2);opacity:0;}
}
</style>
</head>

<body>

<div class="container" id="question">
<h2>Before opening this page...</h2>
<p>Are you my girlfriend? 💕</p>

<button class="yes" onclick="openLove()">Yes</button>
<button class="no" id="noBtn">No</button>
</div>

<div id="message">
<h1>Hi my love ❤️</h1>
<p id="quote"></p>
</div>

<audio id="music" loop>
<source src="song.mp3" type="audio/mp3">
</audio>

<script>

const text = "Out of all the beautiful things in this world, nothing compares to you. Your body is like a work of art to me. Every curve, every movement, every little detail about you is breathtaking. When I look at you I see perfection, and I realize how lucky I am to have someone as beautiful and amazing as you in my life.";

let i = 0;

function typeWriter(){
    if(i < text.length){
        document.getElementById("quote").innerHTML += text.charAt(i);
        i++;
        setTimeout(typeWriter,40);
    }
}

function openLove(){

document.getElementById("question").style.display="none";
document.getElementById("message").style.display="block";

document.getElementById("music").play();

typeWriter();
startHearts();
heartExplosion();

}

/* running NO button */
const noBtn = document.getElementById("noBtn");

noBtn.addEventListener("mouseover", () => {
    noBtn.style.left = Math.random()*80 + "vw";
    noBtn.style.top = Math.random()*80 + "vh";
});

/* floating hearts */
function startHearts(){
setInterval(() => {
let heart = document.createElement("div");
heart.className="heart";
heart.innerHTML="❤️";

heart.style.left = Math.random()*100+"vw";
heart.style.fontSize = (15 + Math.random()*25)+"px";

document.body.appendChild(heart);

setTimeout(()=>{heart.remove();},6000);

},300);
}

/* heart explosion */
function heartExplosion(){
for(let i=0;i<30;i++){
    let heart = document.createElement("div");
    heart.className="explosion";
    heart.innerHTML="❤️";

    let x = (Math.random()-0.5)*400 + "px";
    let y = (Math.random()-0.5)*400 + "px";

    heart.style.setProperty('--x', x);
    heart.style.setProperty('--y', y);

    heart.style.left="50%";
    heart.style.top="50%";

    document.body.appendChild(heart);

    setTimeout(()=>heart.remove(),1000);
}
}

</script>

</body>
</html>
