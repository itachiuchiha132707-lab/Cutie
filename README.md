# Cutie
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Happy Birthday Rashi 💖</title>

<!-- Libraries -->
<script src="https://cdn.tailwindcss.com"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

<!-- Fonts -->
<link href="https://api.fontshare.com/v2/css?f[]=satoshi@400,500,700&f[]=playfair-display@700&display=swap" rel="stylesheet"/>

<style>
:root{
--bg:#0c0a09;
--pink:#ec4899;
--red:#f43f5e;
}
body{
margin:0;
font-family:'Satoshi',sans-serif;
background:var(--bg);
color:#f3f4f6;
overflow:hidden;
}
#aurora{
position:fixed; inset:0; z-index:0; opacity:.6;
background:
radial-gradient(at 20% 20%, hsla(333,70%,55%,.4), transparent 50%),
radial-gradient(at 80% 20%, hsla(282,82%,54%,.3), transparent 50%),
radial-gradient(at 20% 80%, hsla(210,89%,60%,.3), transparent 50%),
radial-gradient(at 80% 80%, hsla(35,90%,60%,.3), transparent 50%);
animation:flow 25s linear infinite;
}
@keyframes flow{
0%{transform:rotate(0deg) scale(1.2);}
50%{transform:rotate(180deg) scale(1.35);}
100%{transform:rotate(360deg) scale(1.2);}
}
#canvas{position:fixed; inset:0; z-index:1;}
#app{display:grid; place-items:center; height:100vh; padding:1rem; z-index:2; position:relative;}

.step{
position:absolute; top:50%; left:50%;
transform:translate(-50%,-50%) scale(.95);
opacity:0;
pointer-events:none;
width:100%;
max-width:850px;
background:rgba(30,30,30,.5);
backdrop-filter:blur(16px);
border:1px solid rgba(255,255,255,.1);
border-radius:1.5rem;
box-shadow:0 20px 50px rgba(0,0,0,.4);
padding:2rem;
text-align:center;
transition:.6s;
}
.step.active{opacity:1; transform:translate(-50%,-50%) scale(1); pointer-events:auto;}

.text-gradient{
font-family:'Playfair Display',serif;
background:linear-gradient(90deg,#f9a8d4,#f472b6,#fff);
-webkit-background-clip:text;
-webkit-text-fill-color:transparent;
}

.btn{
background:linear-gradient(90deg,var(--pink),var(--red));
padding:.8rem 2.5rem;
border-radius:999px;
font-weight:700;
color:white;
box-shadow:0 0 20px rgba(236,72,153,.4);
transition:.3s;
}
.btn:hover{transform:translateY(-4px) scale(1.05); box-shadow:0 0 35px rgba(236,72,153,.7);}
.btn:active{transform:scale(.97);}

.heartbeat{animation:beat 1.5s infinite;}
@keyframes beat{0%,100%{transform:scale(1);}50%{transform:scale(1.2);}}

/* Progress */
#progressTrack{
position:fixed; top:20px; left:50%; transform:translateX(-50%);
width:70%; max-width:350px; height:6px;
background:rgba(255,255,255,.1);
border-radius:10px; backdrop-filter:blur(8px); z-index:10;
}
#progress{height:100%; width:0%; border-radius:10px;
background:linear-gradient(90deg,var(--pink),var(--red)); transition:.6s;}

/* Bento */
.bento{display:grid; grid-template-columns:repeat(3,1fr); gap:1rem;}
.bento div{background:rgba(255,255,255,.05); padding:1rem; border-radius:1rem; border:1px solid rgba(255,255,255,.1);}
.bento div:hover{transform:translateY(-5px);}
.span2{grid-column:span 2;}
@media(max-width:768px){.bento{grid-template-columns:1fr;} .span2{grid-column:span 1;}}

/* Polaroid */
#polaroid{perspective:1000px;}
#p-inner{transition:.5s;}
#polaroid:hover #p-inner{transform:rotateY(10deg) rotateX(5deg) scale(1.05);}

.finalText{opacity:0; transform:translateY(20px);}
</style>
</head>

<body>
<div id="aurora"></div>
<div id="canvas"></div>

<div id="progressTrack"><div id="progress"></div></div>

<div id="app">
<main class="relative w-full h-full">

<!-- STEP 1 -->
<section id="s1" class="step active">
<div class="text-7xl mb-6 heartbeat">❤️</div>
<h1 class="text-gradient text-5xl mb-4">Hey Rashi,</h1>
<p class="mb-8 text-gray-300">I built a little world for you, just to bring a smile to your face on your special day.</p>
<button class="btn" onclick="next()">Let's Begin</button>
</section>

<!-- STEP 2 -->
<section id="s2" class="step">
<div class="text-7xl mb-4">🎉</div>
<h2 class="text-gradient text-5xl mb-4">Happy Birthday!</h2>
<p class="mb-8 text-gray-300">Another year of you making the world brighter. Your existence is a gift.</p>
<button class="btn" onclick="next()">There's more...</button>
</section>

<!-- STEP 3 -->
<section id="s3" class="step">
<h2 class="text-gradient text-4xl mb-6">Things I Adore About You</h2>
<div class="bento mb-8">
<div class="span2"><h3>✨ Your Kindness</h3><p>Your warmth is rare and beautiful.</p></div>
<div><h3>😊 That Smile</h3><p>Pure magic.</p></div>
<div class="span2"><h3>🌟 Your Energy</h3><p>You make life exciting.</p></div>
</div>
<button class="btn" onclick="next()">Remember this?</button>
</section>

<!-- STEP 4 -->
<section id="s4" class="step">
<h2 class="text-gradient text-4xl mb-6">That One Time...</h2>
<div id="polaroid" class="mb-6">
<div id="p-inner" class="bg-white p-3 pb-14 rounded-lg shadow-xl">
<img src="https://i.ibb.co/6Z6XgCg/crush.webp" class="w-full h-72 object-cover"/>
<p class="text-black mt-3 italic font-semibold">Our favorite memory.</p>
</div>
</div>
<p class="mb-8 text-gray-300">Every moment with you feels like a movie scene I'd replay forever.</p>
<button class="btn" onclick="next()">One last thing...</button>
</section>

<!-- STEP 5 -->
<section id="s5" class="step">
<div class="text-7xl mb-4">🎂</div>
<h2 class="text-gradient text-4xl mb-4">My Wish For You</h2>
<p class="mb-6 text-gray-300">May this year bring love, success, and happiness beyond imagination.</p>
<p id="final" class="finalText text-pink-300 font-bold text-xl">Happy Birthday Rashi ❤️</p>
<button id="celebrate" class="btn" onclick="celebrate()">Celebrate!</button>
</section>

</main>
</div>

<script>
let step=1,total=5;
function next(){
document.getElementById("s"+step).classList.remove("active");
step++;
document.getElementById("s"+step).classList.add("active");
document.getElementById("progress").style.width=((step-1)/(total-1))*100+"%";
}

/* 🎉 Finale */
function celebrate(){
document.getElementById("celebrate").style.display="none";
gsap.to("#final",{opacity:1,y:0,duration:1});

let duration=5000,end=Date.now()+duration;
let interval=setInterval(()=>{
if(Date.now()>end)return clearInterval(interval);
confetti({particleCount:50,spread:360,origin:{y:0.6}});
},250);

hearts.forEach(h=>{
gsap.to(h.position,{y:h.position.y+80,duration:4});
gsap.to(h.material,{opacity:0,duration:4});
});
}

/* 💖 Three.js Floating Hearts */
let scene=new THREE.Scene();
let camera=new THREE.PerspectiveCamera(75,innerWidth/innerHeight,0.1,1000);
camera.position.z=30;
let renderer=new THREE.WebGLRenderer({alpha:true});
renderer.setSize(innerWidth,innerHeight);
document.getElementById("canvas").appendChild(renderer.domElement);

let light=new THREE.AmbientLight(0xffffff,1); scene.add(light);

let shape=new THREE.Shape();
shape.moveTo(25,25);
shape.bezierCurveTo(25,25,20,0,0,0);
shape.bezierCurveTo(-30,0,-30,35,-30,35);
shape.bezierCurveTo(-30,55,-10,77,25,95);
shape.bezierCurveTo(60,77,80,55,80,35);
shape.bezierCurveTo(80,35,80,0,50,0);
shape.bezierCurveTo(35,0,25,25,25,25);
let geo=new THREE.ExtrudeGeometry(shape,{depth:8,bevelEnabled:true});
let hearts=[];
for(let i=0;i<22;i++){
let mat=new THREE.MeshPhongMaterial({color:0xff4d6d,transparent:true,opacity:.7});
let h=new THREE.Mesh(geo,mat);
let s=Math.random()*0.04+0.02;
h.scale.set(s,s,s);
h.position.set((Math.random()-.5)*60,(Math.random()-.5)*60,(Math.random()-.5)*20);
scene.add(h); hearts.push(h);
}
function animate(){
requestAnimationFrame(animate);
hearts.forEach(h=>{h.rotation.x+=.003; h.rotation.y+=.003;});
renderer.render(scene,camera);
}
animate();
</script>
</body>
</html>
