<!DOCTYPE html>  
<html lang="en">

<head>
<meta charset="UTF-8">
<title>Will You Be My Valentine ❤️</title>

<link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">

<style>
*{margin:0;padding:0;box-sizing:border-box}

body{
 height:100vh;
 background:linear-gradient(270deg,#ff9a9e,#fad0c4,#fbc2eb);
 background-size:600% 600%;
 animation:bgMove 15s ease infinite;
 font-family:'Poppins',sans-serif;
 overflow:hidden;
 color:#fff;
}

@keyframes bgMove{
 0%{background-position:0% 50%}
 50%{background-position:100% 50%}
 100%{background-position:0% 50%}
}

.container{
 height:100vh;
 display:flex;
 flex-direction:column;
 align-items:center;
 justify-content:center;
 text-align:center;
}

.title{
 font-family:'Great Vibes',cursive;
 font-size:4rem;
 margin-bottom:15px;
}

.card{
 background:rgba(255,255,255,0.18);
 backdrop-filter:blur(15px);
 padding:35px;
 border-radius:25px;
 width:90%;
 max-width:430px;
}

#question{
 font-size:1.6rem;
 min-height:100px;
 transition:0.4s;
}

.left-love{
 position:absolute;
 left:20px;
 top:40%;
 text-align:left;
 width:60%;
}

.slide{
 animation: slideIn 0.45s ease;
}

@keyframes slideIn{
 from{opacity:0; transform:translateX(-25px);}
 to{opacity:1; transform:translateX(0);}
}

button{
 border:none;
 padding:12px 28px;
 border-radius:30px;
 color:#fff;
 font-size:1rem;
 cursor:pointer;
 position:absolute;
 bottom:60px;
}

#yesBtn{background:#ff4d6d; left:35%}
#noBtn{background:#444; left:55%}

footer{
 position:absolute;
 bottom:15px;
 width:100%;
 text-align:center;
 opacity:0.85;
}

#finalLove{
 position:fixed;
 inset:0;
 display:flex;
 align-items:center;
 justify-content:center;
 font-family:'Great Vibes',cursive;
 font-size:4.2rem;
 background:rgba(0,0,0,0.35);
 opacity:0;
 pointer-events:none;
 transition:opacity 1s ease;
 z-index:9999;
}
#finalLove.show{opacity:1}
</style>

</head>

<body>

<audio id="loveSong" preload="auto">
 <source src="https://pagalfree.com/musics/128-Tu%20Chahiye%20-%20Bajrangi%20Bhaijaan%20128%20Kbps.mp3" type="audio/mpeg">
</audio>

<div id="finalLove">I love you so much ❤️</div>

<div class="container">
 <h1 class="title" id="title">Hey you ❤️</h1>

 <div class="card">
  <p id="question">Will you be my Valentine? 💌</p>
 </div>

 <button id="yesBtn">Yes 💖</button>
 <button id="noBtn">No 🙈</button>
</div>

<footer>Made with endless love 💕</footer>

<script>
const steps=[
 "Sure? 😏",
 "Pakka na? 🤭",
 "Soch lo… last chance 😜",
 "Okay then… 💕",
 "I LOVE YOU ❤️🫶"
];

// 🎵 PERFECT SYNCED LYRICS
const syncedLyrics=[
 { time: 0.0, text: "Dil ko teri maujoodgi 💫" },
 { time: 4.0, text: "Ka ehsaas yun chahiye ❤️" },
 { time: 7.5, text: "Tu chahiye, tu chahiye 🥰" },
 { time: 10.6, text: "Shaam-o-subah tu chahiye 💕" },
 { time: 14.6, text: "Tu chahiye, tu chahiye ❤️" },
 { time: 18.5, text: "Har martaba tu chahiye 💖" }
];

let stepIndex=0;
let lyricIndex=0;
const syncOffset = 41.9;

const yes=document.getElementById("yesBtn");
const no=document.getElementById("noBtn");
const q=document.getElementById("question");
const song=document.getElementById("loveSong");
const finalLove=document.getElementById("finalLove");
const title=document.getElementById("title");

function animateText(text){
 q.classList.remove("slide");
 void q.offsetWidth;
 q.innerText=text;
 q.classList.add("slide");
}

yes.onclick=()=>{
 if(stepIndex < steps.length){
  animateText(steps[stepIndex]);
  stepIndex++;
  return;
 }

 title.style.display="none";
 q.classList.add("left-love");

 song.currentTime = syncOffset;
 song.play();

 song.ontimeupdate = () => {
  const t = song.currentTime - syncOffset;

  if(lyricIndex < syncedLyrics.length && t >= syncedLyrics[lyricIndex].time){
    animateText(syncedLyrics[lyricIndex].text);
    lyricIndex++;
  }

  if(song.currentTime > 65){
   finalLove.classList.add("show");
  }
 };

 yes.style.display="none";
 no.style.display="none";
};

function moveNo(){
 no.style.left=Math.random()*70+"%";
 no.style.bottom=Math.random()*200+"px";
}

no.onmouseover=moveNo;
no.onclick=moveNo;

</script>

</body>
</html>
