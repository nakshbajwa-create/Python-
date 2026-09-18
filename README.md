# Python-
Python project 1
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport"
      content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">

<title>Naksh Game Studio</title>

<style>
*{
    box-sizing:border-box;
    margin:0;
    padding:0;
}

:root{
    --bg:#080b12;
    --panel:#101521;
    --panel2:#151b29;
    --border:#273044;
    --text:#f4f7fb;
    --muted:#8e9ab0;
    --accent:#6c63ff;
    --accent2:#8f87ff;
    --danger:#ff5577;
    --success:#42d392;
}

body{
    font-family:Inter,system-ui,Arial,sans-serif;
    background:var(--bg);
    color:var(--text);
    overflow:hidden;
}

/* APP */

.app{
    height:100vh;
    display:flex;
    flex-direction:column;
}

/* TOPBAR */

.topbar{
    height:64px;
    background:#0c1019;
    border-bottom:1px solid var(--border);
    display:flex;
    align-items:center;
    justify-content:space-between;
    padding:0 16px;
    z-index:20;
}

.logo{
    display:flex;
    align-items:center;
    gap:10px;
    font-weight:800;
    font-size:18px;
}

.logoIcon{
    width:35px;
    height:35px;
    border-radius:10px;
    background:linear-gradient(135deg,#6c63ff,#a66cff);
    display:grid;
    place-items:center;
    font-size:18px;
}

.topActions{
    display:flex;
    gap:8px;
}

button{
    border:0;
    color:white;
    background:var(--panel2);
    border:1px solid var(--border);
    padding:9px 13px;
    border-radius:9px;
    cursor:pointer;
    font-weight:600;
}

button:hover{
    border-color:#4b5875;
}

.primary{
    background:var(--accent);
    border-color:var(--accent);
}

.primary:hover{
    background:var(--accent2);
}

.danger{
    background:#3b1722;
    color:#ff8ca3;
}

/* MAIN */

.main{
    flex:1;
    display:grid;
    grid-template-columns:230px 1fr 300px;
    min-height:0;
}

/* LEFT */

.sidebar{
    background:var(--panel);
    border-right:1px solid var(--border);
    padding:14px;
    overflow:auto;
}

.sectionTitle{
    color:var(--muted);
    font-size:11px;
    text-transform:uppercase;
    letter-spacing:1px;
    margin:9px 4px;
}

.toolGrid{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:8px;
}

.tool{
    min-height:70px;
    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    gap:6px;
    background:#131927;
}

.tool span{
    font-size:23px;
}

.tool small{
    color:#aeb8c9;
}

.sceneList{
    display:flex;
    flex-direction:column;
    gap:5px;
}

.sceneItem{
    padding:10px;
    border-radius:8px;
    background:#131927;
    border:1px solid transparent;
    font-size:13px;
}

.sceneItem.active{
    border-color:var(--accent);
    background:#191c35;
}

/* CENTER */

.workspace{
    position:relative;
    background:
      radial-gradient(circle at center,#151b2a 0,#090c13 65%);
    overflow:hidden;
    display:flex;
    align-items:center;
    justify-content:center;
}

.canvasWrap{
    position:relative;
    box-shadow:
      0 20px 70px rgba(0,0,0,.6),
      0 0 0 1px #30394e;
}

#gameCanvas{
    display:block;
    background:#101725;
    image-rendering:auto;
}

.canvasLabel{
    position:absolute;
    top:-30px;
    left:0;
    color:#7e8aa0;
    font-size:12px;
}

.playOverlay{
    position:absolute;
    inset:0;
    pointer-events:none;
}

/* RIGHT */

.inspector{
    background:var(--panel);
    border-left:1px solid var(--border);
    padding:14px;
    overflow:auto;
}

.card{
    background:#131927;
    border:1px solid var(--border);
    border-radius:10px;
    padding:12px;
    margin-bottom:10px;
}

.card h3{
    font-size:13px;
    margin-bottom:11px;
}

label{
    display:block;
    color:var(--muted);
    font-size:11px;
    margin:9px 0 5px;
}

input,select,textarea{
    width:100%;
    background:#0c111b;
    color:white;
    border:1px solid var(--border);
    border-radius:7px;
    padding:9px;
    outline:none;
}

input:focus,
select:focus,
textarea:focus{
    border-color:var(--accent);
}

.row{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:8px;
}

/* BOTTOM */

.bottom{
    height:42px;
    background:#0c1019;
    border-top:1px solid var(--border);
    display:flex;
    align-items:center;
    justify-content:space-between;
    padding:0 13px;
    color:var(--muted);
    font-size:11px;
}

.statusDot{
    display:inline-block;
    width:7px;
    height:7px;
    border-radius:50%;
    background:var(--success);
    margin-right:5px;
}

/* AI */

.aiButton{
    position:absolute;
    right:18px;
    bottom:18px;
    width:55px;
    height:55px;
    border-radius:50%;
    background:linear-gradient(135deg,#6c63ff,#a06cff);
    font-size:22px;
    box-shadow:0 8px 30px rgba(108,99,255,.35);
    z-index:5;
}

.aiPanel{
    position:absolute;
    right:18px;
    bottom:85px;
    width:min(370px,calc(100% - 36px));
    height:460px;
    background:#0d121d;
    border:1px solid #35405a;
    border-radius:15px;
    box-shadow:0 20px 60px rgba(0,0,0,.6);
    display:none;
    flex-direction:column;
    overflow:hidden;
    z-index:10;
}

.aiPanel.open{
    display:flex;
}

.aiHeader{
    padding:14px;
    border-bottom:1px solid var(--border);
    display:flex;
    justify-content:space-between;
}

.aiMessages{
    flex:1;
    padding:12px;
    overflow:auto;
}

.msg{
    padding:10px;
    border-radius:10px;
    margin-bottom:8px;
    font-size:13px;
    line-height:1.45;
}

.ai{
    background:#171d2b;
}

.user{
    background:#28234c;
    margin-left:30px;
}

.aiInput{
    display:flex;
    gap:7px;
    padding:10px;
    border-top:1px solid var(--border);
}

.aiInput input{
    flex:1;
}

/* TOAST */

.toast{
    position:fixed;
    left:50%;
    bottom:65px;
    transform:translateX(-50%) translateY(20px);
    background:#151c2a;
    border:1px solid #39455e;
    padding:11px 17px;
    border-radius:9px;
    opacity:0;
    pointer-events:none;
    transition:.25s;
    z-index:100;
}

.toast.show{
    opacity:1;
    transform:translateX(-50%) translateY(0);
}

/* MOBILE */

@media(max-width:900px){

    .main{
        grid-template-columns:75px 1fr;
    }

    .sidebar{
        padding:7px;
    }

    .toolGrid{
        grid-template-columns:1fr;
    }

    .tool{
        min-height:58px;
    }

    .tool small{
        font-size:8px;
    }

    .inspector{
        position:absolute;
        right:0;
        top:64px;
        bottom:42px;
        width:290px;
        transform:translateX(100%);
        transition:.25s;
        z-index:15;
    }

    .inspector.open{
        transform:translateX(0);
    }

    #gameCanvas{
        max-width:calc(100vw - 90px);
        max-height:calc(100vh - 150px);
    }

    .topbar{
        padding:0 8px;
    }

    .topActions button{
        padding:7px;
        font-size:11px;
    }
}
</style>
</head>

<body>

<div class="app">

<header class="topbar">

    <div class="logo">
        <div class="logoIcon">🎮</div>
        Naksh Game Studio
    </div>

    <div class="topActions">
        <button onclick="newProject()">＋ New</button>
        <button onclick="saveProject()">💾 Save</button>
        <button onclick="loadProject()">📂 Load</button>
        <button class="primary" onclick="togglePlay()">▶ Play</button>
        <button class="primary" onclick="downloadGame()">⬇ Export</button>
    </div>

</header>

<div class="main">

<!-- LEFT SIDEBAR -->

<aside class="sidebar">

<div class="sectionTitle">Create</div>

<div class="toolGrid">

<button class="tool" onclick="addObject('player')">
<span>🧑</span>
<small>Player</small>
</button>

<button class="tool" onclick="addObject('enemy')">
<span>👾</span>
<small>Enemy</small>
</button>

<button class="tool" onclick="addObject('platform')">
<span>🟫</span>
<small>Platform</small>
</button>

<button class="tool" onclick="addObject('coin')">
<span>🪙</span>
<small>Coin</small>
</button>

<button class="tool" onclick="addObject('goal')">
<span>🏁</span>
<small>Goal</small>
</button>

<button class="tool" onclick="addObject('text')">
<span>🔤</span>
<small>Text</small>
</button>

</div>

<div class="sectionTitle">Scene</div>

<div id="sceneList" class="sceneList"></div>

</aside>


<!-- WORKSPACE -->

<section class="workspace">

<div class="canvasWrap">

<div class="canvasLabel">
Scene 1 • 960 × 540
</div>

<canvas id="gameCanvas"
        width="960"
        height="540"></canvas>

</div>


<button class="aiButton" onclick="toggleAI()">🤖</button>


<div id="aiPanel" class="aiPanel">

<div class="aiHeader">
<strong>AI Game Assistant</strong>
<button onclick="toggleAI()">×</button>
</div>

<div id="aiMessages" class="aiMessages">

<div class="msg ai">
👋 Hi! I'm your Game Creation Assistant.<br><br>
Tell me what you want to build, for example:
<br><br>
• "Make a platform game"
<br>
• "Add an enemy"
<br>
• "How do I make the player jump?"
<br>
• "Make coins give points"
</div>

</div>

<div class="aiInput">

<input id="aiInput"
       placeholder="Ask your AI assistant..."
       onkeydown="if(event.key==='Enter')askAI()">

<button class="primary" onclick="askAI()">Send</button>

</div>

</div>

</section>


<!-- INSPECTOR -->

<aside id="inspector" class="inspector">

<div class="card">

<h3>Object Inspector</h3>

<div id="noSelection">
Select an object from the game.
</div>

<div id="objectEditor" style="display:none">

<label>Name</label>
<input id="objName" oninput="updateSelected()">

<div class="row">

<div>
<label>X</label>
<input id="objX" type="number" oninput="updateSelected()">
</div>

<div>
<label>Y</label>
<input id="objY" type="number" oninput="updateSelected()">
</div>

</div>

<div class="row">

<div>
<label>Width</label>
<input id="objW" type="number" oninput="updateSelected()">
</div>

<div>
<label>Height</label>
<input id="objH" type="number" oninput="updateSelected()">
</div>

</div>

<label>Type</label>
<select id="objType" onchange="updateSelected()">
<option value="player">Player</option>
<option value="enemy">Enemy</option>
<option value="platform">Platform</option>
<option value="coin">Coin</option>
<option value="goal">Goal</option>
<option value="text">Text</option>
</select>

<label>Color</label>
<input id="objColor"
       type="color"
       onchange="updateSelected()">

<label>Speed</label>
<input id="objSpeed"
       type="number"
       oninput="updateSelected()">

<br>

<button class="danger" onclick="deleteSelected()">
🗑 Delete Object
</button>

<button onclick="duplicateSelected()">
⧉ Duplicate
</button>

</div>

</div>


<div class="card">

<h3>Game Settings</h3>

<label>Game Title</label>
<input id="gameTitle"
       value="My Awesome Game">

<label>Background</label>
<input id="bgColor"
       type="color"
       value="#101725"
       onchange="draw()">

<label>Gravity</label>
<input id="gravity"
       type="number"
       value="0.5"
       step="0.1">

</div>


<div class="card">

<h3>Controls</h3>

<p style="font-size:12px;color:#8e9ab0;line-height:1.6">
← → / A D : Move<br>
Space / W / ↑ : Jump<br>
P : Pause
</p>

</div>

</aside>

</div>


<footer class="bottom">

<div>
<span class="statusDot"></span>
Ready
</div>

<div>
2D Game Engine • Local Project
</div>

</footer>

</div>


<div id="toast" class="toast"></div>


<script>

/* =====================================================
   GAME ENGINE
===================================================== */

const canvas = document.getElementById("gameCanvas");
const ctx = canvas.getContext("2d");

let objects = [];
let selected = null;
let playing = false;

let keys = {};

let particles = [];

let gameState = {
    score:0,
    coins:0,
    health:100
};


/* =====================================================
   OBJECT CREATION
===================================================== */

function addObject(type){

    const data = {

        id:Date.now()+Math.random(),

        type:type,

        name:type.charAt(0).toUpperCase()+type.slice(1),

        x:100 + Math.random()*400,

        y:100 + Math.random()*250,

        w: type==="platform" ? 180 : 45,

        h: type==="platform" ? 25 : 45,

        color:
            type==="player" ? "#5f8cff" :
            type==="enemy" ? "#ff5577" :
            type==="platform" ? "#765f45" :
            type==="coin" ? "#ffd84d" :
            type==="goal" ? "#42d392" :
            "#ffffff",

        speed:
            type==="enemy" ? 2 : 4,

        velocityY:0

    };

    if(type==="text"){
        data.w=220;
        data.h=40;
    }

    objects.push(data);

    selected=data;

    updateSceneList();
    updateInspector();
    draw();

    toast(type+" added");
}


/* =====================================================
   SCENE LIST
===================================================== */

function updateSceneList(){

    const list=document.getElementById("sceneList");

    list.innerHTML="";

    objects.forEach((o,index)=>{

        const div=document.createElement("div");

        div.className="sceneItem"+
            (o===selected ? " active":"");

        div.textContent=
            (index+1)+"  "+o.name+" ("+o.type+")";

        div.onclick=()=>{

            selected=o;

            updateSceneList();
            updateInspector();
            draw();

        };

        list.appendChild(div);

    });
}


/* =====================================================
   INSPECTOR
===================================================== */

function updateInspector(){

    const editor=document.getElementById("objectEditor");
    const none=document.getElementById("noSelection");

    if(!selected){

        editor.style.display="none";
        none.style.display="block";

        return;
    }

    editor.style.display="block";
    none.style.display="none";

    document.getElementById("objName").value=selected.name;
    document.getElementById("objX").value=Math.round(selected.x);
    document.getElementById("objY").value=Math.round(selected.y);
    document.getElementById("objW").value=selected.w;
    document.getElementById("objH").value=selected.h;
    document.getElementById("objType").value=selected.type;
    document.getElementById("objColor").value=selected.color;
    document.getElementById("objSpeed").value=selected.speed;

}


function updateSelected(){

    if(!selected)return;

    selected.name=document.getElementById("objName").value;

    selected.x=Number(document.getElementById("objX").value);

    selected.y=Number(document.getElementById("objY").value);

    selected.w=Number(document.getElementById("objW").value);

    selected.h=Number(document.getElementById("objH").value);

    selected.type=document.getElementById("objType").value;

    selected.color=document.getElementById("objColor").value;

    selected.speed=Number(document.getElementById("objSpeed").value);

    updateSceneList();

    draw();

}


/* =====================================================
   DELETE / DUPLICATE
===================================================== */

function deleteSelected(){

    if(!selected)return;

    objects=objects.filter(o=>o!==selected);

    selected=null;

    updateSceneList();
    updateInspector();
    draw();

    toast("Object deleted");
}


function duplicateSelected(){

    if(!selected)return;

    const copy={
        ...selected,
        id:Date.now()+Math.random(),
        x:selected.x+25,
        y:selected.y+25,
        name:selected.name+" Copy"
    };

    objects.push(copy);

    selected=copy;

    updateSceneList();
    updateInspector();
    draw();
}


/* =====================================================
   DRAW ENGINE
===================================================== */

function draw(){

    ctx.fillStyle=
        document.getElementById("bgColor").value;

    ctx.fillRect(0,0,canvas.width,canvas.height);


    /* grid */

    ctx.strokeStyle="rgba(255,255,255,.035)";
    ctx.lineWidth=1;

    for(let x=0;x<canvas.width;x+=40){

        ctx.beginPath();
        ctx.moveTo(x,0);
        ctx.lineTo(x,canvas.height);
        ctx.stroke();

    }

    for(let y=0;y<canvas.height;y+=40){

        ctx.beginPath();
        ctx.moveTo(0,y);
        ctx.lineTo(canvas.width,y);
        ctx.stroke();

    }


    objects.forEach(drawObject);


    if(playing){

        ctx.fillStyle="white";
        ctx.font="bold 18px Arial";

        ctx.fillText(
            "SCORE: "+gameState.score,
            20,
            30
        );

        ctx.fillText(
            "❤️ "+gameState.health,
            20,
            55
        );

        ctx.fillText(
            "🪙 "+gameState.coins,
            20,
            80
        );

    }

}


function drawObject(o){

    ctx.save();

    if(o.type==="player"){

        ctx.fillStyle=o.color;

        ctx.fillRect(
            o.x,
            o.y,
            o.w,
            o.h
        );

        ctx.fillStyle="white";

        ctx.fillRect(
            o.x+10,
            o.y+10,
            8,
            8
        );

        ctx.fillRect(
            o.x+27,
            o.y+10,
            8,
            8
        );

    }

    else if(o.type==="enemy"){

        ctx.fillStyle=o.color;

        ctx.beginPath();

        ctx.arc(
            o.x+o.w/2,
            o.y+o.h/2,
            o.w/2,
            0,
            Math.PI*2
        );

        ctx.fill();

        ctx.fillStyle="white";

        ctx.beginPath();

        ctx.arc(
            o.x+14,
            o.y+17,
            5,
            0,
            Math.PI*2
        );

        ctx.arc(
            o.x+31,
            o.y+17,
            5,
            0,
            Math.PI*2
        );

        ctx.fill();

    }

    else if(o.type==="platform"){

        ctx.fillStyle=o.color;

        ctx.fillRect(
            o.x,
            o.y,
            o.w,
            o.h
        );

    }

    else if(o.type==="coin"){

        ctx.fillStyle=o.color;

        ctx.beginPath();

        ctx.arc(
            o.x+o.w/2,
            o.y+o.h/2,
            o.w/2,
            0,
            Math.PI*2
        );

        ctx.fill();

        ctx.fillStyle="#9a6c00";
        ctx.font="bold 20px Arial";
        ctx.fillText("★",o.x+12,o.y+29);

    }

    else if(o.type==="goal"){

        ctx.fillStyle=o.color;

        ctx.fillRect(
            o.x+15,
            o.y,
            6,
            o.h
        );

        ctx.beginPath();

        ctx.moveTo(o.x+20,o.y);
        ctx.lineTo(o.x+55,o.y+15);
        ctx.lineTo(o.x+20,o.y+30);

        ctx.fill();

    }

    else if(o.type==="text"){

        ctx.fillStyle=o.color;

        ctx.font="bold 26px Arial";

        ctx.fillText(
            o.name,
            o.x,
            o.y+28
        );

    }


    /* selection */

    if(o===selected && !playing){

        ctx.strokeStyle="#8f87ff";
        ctx.lineWidth=2;
        ctx.setLineDash([6,4]);

        ctx.strokeRect(
            o.x-5,
            o.y-5,
            o.w+10,
            o.h+10
        );

        ctx.setLineDash([]);

    }

    ctx.restore();

}


/* =====================================================
   MOUSE / TOUCH OBJECT SELECTION
===================================================== */

function canvasPosition(e){

    const rect=canvas.getBoundingClientRect();

    const scaleX=canvas.width/rect.width;
    const scaleY=canvas.height/rect.height;

    let clientX,clientY;

    if(e.touches){

        clientX=e.touches[0].clientX;
        clientY=e.touches[0].clientY;

    }else{

        clientX=e.clientX;
        clientY=e.clientY;

    }

    return {

        x:(clientX-rect.left)*scaleX,
        y:(clientY-rect.top)*scaleY

    };

}


let dragging=false;
let dragOffset={x:0,y:0};


function pointerDown(e){

    if(playing)return;

    const p=canvasPosition(e);

    for(let i=objects.length-1;i>=0;i--){

        const o=objects[i];

        if(
            p.x>=o.x &&
            p.x<=o.x+o.w &&
            p.y>=o.y &&
            p.y<=o.y+o.h
        ){

            selected=o;

            dragging=true;

            dragOffset.x=p.x-o.x;
            dragOffset.y=p.y-o.y;

   

