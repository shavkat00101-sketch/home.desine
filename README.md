<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Architect Platform – All in One</title>

<style>
/* ===== CSS ===== */
body{
  margin:0;
  font-family:Arial, sans-serif;
  background:#0e0e0e;
  color:#fff;
}
.container{
  max-width:900px;
  margin:auto;
  padding:20px;
}
h1{text-align:center;}
input,select,button{
  width:100%;
  padding:10px;
  margin:6px 0;
  font-size:16px;
}
button{
  background:#00c896;
  border:none;
  cursor:pointer;
  font-weight:bold;
}
.cards{
  margin-top:20px;
}
.card{
  background:#1b1b1b;
  padding:15px;
  margin-bottom:10px;
  border:1px solid #333;
}
#viewer{
  margin-top:30px;
  height:300px;
  background:#000;
  position:relative;
}
#hint{
  position:absolute;
  top:10px;
  left:10px;
  background:rgba(0,0,0,0.6);
  padding:8px;
  font-size:14px;
}
</style>
</head>

<body>
<div class="container">
<h1>🏠 Architect Platform</h1>

<input id="budget" type="number" placeholder="Budget ($)">
<input id="rooms" type="number" placeholder="Minimum rooms">

<button onclick="filterHouses()">Find Houses</button>

<div class="cards" id="result"></div>

<h2>360° House View</h2>
<div id="viewer">
  <div id="hint">Drag to look around</div>
</div>
</div>

<script src="https://cdn.jsdelivr.net/npm/three@0.150.1/build/three.min.js"></script>

<script>
/* ===== JAVASCRIPT ===== */

// ===== DATA (fake DB) =====
const houses = [
 {id:1,title:"Modern Alpha",price:80000,rooms:3,area:120},
 {id:2,title:"Classic Beta",price:60000,rooms:2,area:90},
 {id:3,title:"Luxury Gamma",price:120000,rooms:5,area:220},
 {id:4,title:"Compact Delta",price:50000,rooms:2,area:75},
];

// ===== FILTER FUNCTION =====
function filterHouses(){
  const budget = Number(document.getElementById("budget").value);
  const rooms  = Number(document.getElementById("rooms").value);
  const box = document.getElementById("result");
  box.innerHTML = "";

  const filtered = houses.filter(h =>
    (!budget || h.price <= budget) &&
    (!rooms || h.rooms >= rooms)
  );

  if(filtered.length === 0){
    box.innerHTML = "<p>No houses found</p>";
    return;
  }

  filtered.forEach(h=>{
    box.innerHTML += `
      <div class="card">
        <b>${h.title}</b><br>
        Price: $${h.price}<br>
        Rooms: ${h.rooms}<br>
        Area: ${h.area} m²
      </div>
    `;
  });
}

// ===== 360 VIEW =====
let scene = new THREE.Scene();
let camera = new THREE.PerspectiveCamera(75, 900/300, 1, 1000);
camera.position.set(0,0,0.1);

let renderer = new THREE.WebGLRenderer();
renderer.setSize(900,300);
document.getElementById("viewer").appendChild(renderer.domElement);

let geometry = new THREE.SphereGeometry(500,60,40);
geometry.scale(-1,1,1);

// demo texture (gradient)
let canvas = document.createElement("canvas");
canvas.width = canvas.height = 512;
let ctx = canvas.getContext("2d");
let grd = ctx.createLinearGradient(0,0,512,512);
grd.addColorStop(0,"#444");
grd.addColorStop(1,"#111");
ctx.fillStyle = grd;
ctx.fillRect(0,0,512,512);

let texture = new THREE.CanvasTexture(canvas);
let material = new THREE.MeshBasicMaterial({map:texture});
let sphere = new THREE.Mesh(geometry, material);
scene.add(sphere);

let isDown=false, lon=0, lat=0;
renderer.domElement.addEventListener("mousedown",()=>isDown=true);
window.addEventListener("mouseup",()=>isDown=false);
window.addEventListener("mousemove",e=>{
  if(!isDown) return;
  lon += e.movementX*0.1;
  lat -= e.movementY*0.1;
});

function animate(){
  requestAnimationFrame(animate);
  lat = Math.max(-85,Math.min(85,lat));
  let phi = THREE.MathUtils.degToRad(90-lat);
  let theta = THREE.MathUtils.degToRad(lon);
  camera.lookAt(
    500*Math.sin(phi)*Math.cos(theta),
    500*Math.cos(phi),
    500*Math.sin(phi)*Math.sin(theta)
  );
  renderer.render(scene,camera);
}
animate();
</script>
</body>
</html>
