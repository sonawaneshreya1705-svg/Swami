<!DOCTYPE html>
<html>
<head>
<title>A Quiet Thought</title>

<style>
body{
  margin:0;
  height:100vh;
  background:linear-gradient(-45deg,#0f2027,#203a43,#2c5364,#4b006e,#6a0572,#ff5f6d,#ffc371);
  background-size:800% 800%;
  animation:bgMove 30s ease infinite;
  display:flex;
  justify-content:center;
  align-items:center;
  font-family:'Segoe UI',sans-serif;
  overflow:hidden;
  color:white;
}

/* Background Animation */
@keyframes bgMove{
  0%{background-position:0% 50%}
  25%{background-position:50% 75%}
  50%{background-position:100% 50%}
  75%{background-position:50% 25%}
  100%{background-position:0% 50%}
}

/* START SCREEN */
.start{
  position:absolute;
  inset:0;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  background:rgba(0,0,0,0.35);
  backdrop-filter:blur(12px);
  z-index:5;
  transition:opacity 1.5s ease;
}

.start.hide{
  opacity:0;
  pointer-events:none;
}

.start h2{
  font-weight:400;
  letter-spacing:1px;
  opacity:0.85;
}

.start p{
  margin-top:10px;
  font-size:14px;
  opacity:0.6;
  animation:pulse 2s infinite;
}

@keyframes pulse{
  0%{opacity:0.4}
  50%{opacity:0.8}
  100%{opacity:0.4}
}

/* CINEMATIC OVERLAY */
.overlay{
  position:absolute;
  inset:0;
  backdrop-filter:blur(10px);
  animation:softClear 4s ease forwards;
}

@keyframes softClear{
  from{backdrop-filter:blur(16px)}
  to{backdrop-filter:blur(6px)}
}

/* CONTENT */
.container{
  width:90%;
  max-width:520px;
  text-align:center;
  transform:scale(1.12);
  animation:cinemaZoom 7s ease forwards;
  z-index:2;
  opacity:0;
}

@keyframes cinemaZoom{
  from{transform:scale(1.12)}
  to{transform:scale(1)}
}

.line{
  font-size:18px;
  opacity:0;
  margin:18px 0;
  transition:opacity 2s ease, color 2s ease;
}

/* Show line effect */
.line.show{
  opacity:1;
}

/* Glow effect for romantic emphasis */
.glow{
  text-shadow:0 0 14px rgba(255,255,255,0.6);
  animation:glowPulse 2.5s ease-in-out infinite;
}

@keyframes glowPulse{
  0%,100%{text-shadow:0 0 12px rgba(255,255,255,0.6), 0 0 20px rgba(255,182,193,0.5);}
  50%{text-shadow:0 0 20px rgba(255,255,255,0.8), 0 0 35px rgba(255,105,180,0.7);}
}

/* Shimmer effect across all lines */
@keyframes shimmer{
  0%{background-position:-100% 0;}
  100%{background-position:200% 0;}
}
.line.shimmer{
  display:inline-block;
  background:linear-gradient(90deg, rgba(255,255,255,0.2), rgba(255,255,255,0.6), rgba(255,255,255,0.2));
  background-size:200% 100%;
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
  animation:shimmer 3s linear infinite;
}

/* FLOATING HEART PARTICLES */
.particle{
  position:absolute;
  bottom:-20px;
  font-size:14px;
  opacity:0.7;
  animation:floatHeart 14s linear infinite;
  color:rgba(255,105,180,0.8);
  text-shadow:0 0 8px #ff69b4, 0 0 12px #ffb6c1;
}

@keyframes floatHeart{
  from{transform:translateY(0) rotate(0deg);}
  to{transform:translateY(-120vh) rotate(360deg);}
}
</style>
</head>

<body>

<!-- START -->
<div class="start" id="start" onclick="begin()">
  <h2>For a quiet moment…</h2>
  <p>tap anywhere</p>
</div>

<div class="overlay"></div>

<div class="container" id="content">
  <div class="line">Helloo bubs..🥰</div>
  <div class="line">I don’t know when it started, but talking to you feels comforting.🤍</div>
  <div class="line shimmer">Tumhi bolta teva mann automatically calm hott..😌</div>
  <div class="line">Tumcha message ala ki smile yete, quietly..😊</div>
  <div class="line shimmer">With you, emotions don’t feel heavy..</div>
  <div class="line">You make small moments feel meaningful..💫</div>
  <div class="line glow">I don’t feel awkward being slightly romantic with you..🥰</div>
  <div class="line">Tumcha presence hi enough ahe..💖</div>
  <div class="line shimmer">Bass evadh ch sangaych ahe ki tumhi ahat tr sarv better feel hott</div>
  <div class="line">Thank you so much for coming into my life..🫶🏻</div>
  <div class="line glow">I love you so muchhh..😘</div>
  <div class="line glow">Miss bhi bahut kar rahi hu apko..🥺</div>


<script>
let lines=document.querySelectorAll(".line");
let i=0;

function begin(){
  document.getElementById("start").classList.add("hide");
  document.getElementById("content").style.opacity=1;
  showLines();
}

function showLines(){
  if(i<lines.length){
    lines[i].classList.add("show");
    i++;
    setTimeout(showLines,2100);
  }
}

// HEART PARTICLES
function heartParticles(){
  let p=document.createElement("div");
  p.className="particle";
  p.innerHTML="❤️";
  p.style.left=Math.random()*100+"vw";
  p.style.fontSize=(14 + Math.random()*20) + "px";
  p.style.opacity=(0.4 + Math.random()*0.6);
  document.body.appendChild(p);
  setTimeout(()=>p.remove(),14000);
}
setInterval(heartParticles,800);
</script>

</body>
</html>
