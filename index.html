<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Vista explosionada · Teensy 4.1 Audio</title>
<style>
:root{color-scheme:dark;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px);--bg:#07090c;--fg:#e8edf2;--dim:#7d8895;--acc:#4fd1a5}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
html,body{height:100%;margin:0;background:var(--bg);color:var(--fg);font-family:"Manrope",system-ui,sans-serif;overflow:hidden}
canvas{display:block;width:100%;height:100%;touch-action:none}
#ui{position:fixed;left:0;right:0;bottom:calc(env(safe-area-inset-bottom,0px) + 16px);display:flex;gap:10px;justify-content:center;pointer-events:none}
button{pointer-events:auto;font:600 14px "Manrope",system-ui,sans-serif;color:var(--fg);background:#121820cc;border:1px solid #2a3440;border-radius:999px;padding:10px 18px;cursor:pointer;backdrop-filter:blur(6px)}
button:hover{border-color:var(--acc)}button:focus-visible{outline:2px solid var(--acc);outline-offset:2px}
#title{position:fixed;left:20px;top:calc(env(safe-area-inset-top,0px) + 16px);pointer-events:none}
#title b{font-size:18px;font-weight:700;letter-spacing:.01em}
#title span{display:block;font-size:12px;color:var(--dim);margin-top:2px}
.lb{position:fixed;left:0;top:0;font-size:12px;font-weight:500;color:var(--fg);white-space:nowrap;pointer-events:none;padding:3px 8px;border-left:2px solid var(--acc);background:#0b1016b3;transition:opacity .3s}
.nolb .lb{display:none}#ui{flex-wrap:wrap;padding:0 12px}
@media(max-width:600px){.lb{font-size:10px;padding:2px 5px}#title{left:14px}#title b{font-size:15px}#title span{font-size:11px;max-width:62vw}button{padding:9px 14px;font-size:13px}}
</style>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Manrope:wght@500;600;700&display=swap">
</head>
<body>
<canvas id="c"></canvas>
<div id="title"><b>Teensy 4.1 · Audio · Sensores</b><span>Carcasa 9 × 6 × 2,25 cm · arrastra para girar · rueda o pellizco para acercar</span></div>
<div id="ui"><button id="b1">Pausar</button><button id="b2">Armar / desarmar</button><button id="b3">Etiquetas</button></div>
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script>
const cv=document.getElementById('c');
const R=new THREE.WebGLRenderer({canvas:cv,antialias:true});
const mob=matchMedia('(pointer:coarse)').matches;R.setPixelRatio(Math.min(devicePixelRatio,mob?1.5:2));
R.outputEncoding=THREE.sRGBEncoding;R.toneMapping=THREE.ACESFilmicToneMapping;R.toneMappingExposure=1.15;
R.shadowMap.enabled=true;R.shadowMap.type=THREE.PCFSoftShadowMap;
const S=new THREE.Scene();S.background=new THREE.Color(0x07090c);S.fog=new THREE.Fog(0x07090c,30,70);
function CT(c){const t=new THREE.CanvasTexture(c);t.encoding=THREE.sRGBEncoding;t.anisotropy=8;return t}
let dust;const cam=new THREE.PerspectiveCamera(35,1,.1,100);

// entorno de estudio (softboxes) para reflejos metálicos
(function(){const c=document.createElement('canvas');c.width=512;c.height=256;const g=c.getContext('2d');
const gr=g.createLinearGradient(0,0,0,256);gr.addColorStop(0,'#2a3644');gr.addColorStop(.5,'#10151c');gr.addColorStop(1,'#05070a');g.fillStyle=gr;g.fillRect(0,0,512,256);
g.fillStyle='#fff';g.fillRect(40,40,130,70);g.fillRect(300,30,110,90);g.fillRect(450,60,50,60);g.fillStyle='#bfe9ff';g.fillRect(200,20,60,40);g.fillStyle='#9fe8d0';g.fillRect(230,150,60,30);g.fillStyle='#ffd9b0';g.fillRect(120,140,50,24);
const t=new THREE.CanvasTexture(c);t.mapping=THREE.EquirectangularReflectionMapping;t.encoding=THREE.sRGBEncoding;
const p=new THREE.PMREMGenerator(R);S.environment=p.fromEquirectangular(t).texture;})();

const key=new THREE.DirectionalLight(0xffffff,1.6);key.position.set(6,10,6);key.castShadow=true;key.shadow.mapSize.set(mob?2048:4096,mob?2048:4096);key.shadow.bias=-.0003;key.shadow.normalBias=.02;key.shadow.radius=3;
Object.assign(key.shadow.camera,{left:-12,right:12,top:12,bottom:-12,near:1,far:45});S.add(key);
const rim=new THREE.DirectionalLight(0x4fd1a5,1.2);rim.position.set(-8,3,-6);S.add(rim);
S.add(new THREE.HemisphereLight(0x8aa4c0,0x05070a,.35));const fill=new THREE.DirectionalLight(0xbcd4ff,.5);fill.position.set(-6,-4,8);S.add(fill);

const M=(c,r=.5,m=0,o={})=>new THREE.MeshStandardMaterial(Object.assign({color:c,roughness:r,metalness:m},o));
const mPCB=M(0x0f6b3c,.45,.1),mPCB2=M(0x0b5a33,.45,.1),mGold=M(0xd9a93a,.25,1),mSil=M(0xc8cdd2,.28,1),mBlk=M(0x111213,.4,.2),mChip=M(0x1a1c20,.3,.5);
function box(w,h,d,m,x=0,y=0,z=0){const o=new THREE.Mesh(new THREE.BoxGeometry(w,h,d),m);o.position.set(x,y,z);o.castShadow=o.receiveShadow=true;return o}
function cyl(r,h,m,x=0,y=0,z=0,s=32){const o=new THREE.Mesh(new THREE.CylinderGeometry(r,r,h,s),m);o.position.set(x,y,z);o.castShadow=o.receiveShadow=true;return o}
function padsRow(g,n,x,z0,dz,y){for(let i=0;i<n;i++)g.add(cyl(.05,.075,mGold,x,y,z0+i*dz,12))}

// Teensy 4.1
function teensy(){const g=new THREE.Group();g.add(box(1.8,.08,6.1,mPCB));
g.add(box(1.15,.1,1.15,mChip,0,.09,.2));g.add(box(.55,.05,.55,mChip,0,.08,-1.3));
g.add(box(1.0,.22,.95,mSil,0,.14,-2.55));g.add(box(.7,.16,.5,mSil,0,.12,2.85));g.add(box(.18,.08,.18,M(0xdcd2b8,.6),.5,.1,-.9));
padsRow(g,24,-.78,-2.8,.235,.05);padsRow(g,24,.78,-2.8,.235,.05);
for(let i=0;i<8;i++){g.add(box(.14,.06,.12,M(0x8a7a5a,.5,.3),-.3+(i%4)*.2,.07,1.1+Math.floor(i/4)*.3))}return g}
// Audio shield
function shield(){const g=new THREE.Group();g.add(box(2.9,.08,2.9,mPCB2));
g.add(box(.5,.06,.5,mChip,-.2,.07,.1));g.add(box(.95,.14,1.0,mSil,.75,.1,-.3));
g.add(box(.9,.5,.8,mBlk,-.5,.28,1.4));g.add(cyl(.17,.5,mBlk,-.5,.3,1.65).rotateX(Math.PI/2));
[[-1.25,-1.25],[1.25,-1.25],[1.25,1.25]].forEach(([x,z])=>{const r=cyl(.2,.09,mGold,x,.01,z);g.add(r)});
padsRow(g,12,-1.0,-1.25,.2,.05);padsRow(g,12,1.0,-1.25,.2,.05);
for(let i=0;i<10;i++)g.add(box(.1,.05,.18,M(0xb9b9b0,.4,.6),-.9+i*.12,.07,-.8));return g}
// Batería LiPo
function battery(){const g=new THREE.Group();g.add(box(5,.5,7.6,M(0xb9bec4,.3,.95)));
g.add(box(5.02,.52,.6,M(0xe0a020,.6,0),0,0,3.5));g.add(box(2.4,.01,1.4,M(0xf2f2f2,.7,0),0,.255,.3));g.add(box(.8,.012,.5,M(0x111111,.9,0),.6,.26,.3));
[0xc0302a,0x111111].forEach((c,i)=>{const cur=new THREE.CatmullRomCurve3([new THREE.Vector3(-.1+i*.2,0,-3.8),new THREE.Vector3(-.12+i*.2,.08,-4),new THREE.Vector3(-.1+i*.2,0,-4.15)]);const t=new THREE.Mesh(new THREE.TubeGeometry(cur,12,.04,8),M(c,.6));t.castShadow=true;g.add(t)});
g.add(box(.5,.2,.2,M(0xf1ede0,.6),0,0,-4.2));return g}
// Micrófono I2S
function mic(){const g=new THREE.Group();g.add(cyl(.72,.06,M(0x151518,.35,.3),0,0,0,48));g.add(cyl(.74,.04,mGold,0,-.01,0,48));
g.add(box(.42,.14,.3,mSil,0,.1,0));g.add(cyl(.05,.03,mBlk,0,.18,0));
for(let i=-1;i<=1;i++){g.add(cyl(.05,.5,mGold,i*.25,-.3,.45,10))}g.add(box(.9,.14,.2,M(0xe8c21a,.6),0,-.1,.45));
for(let i=0;i<6;i++){const a=i/6*6.28;g.add(cyl(.04,.07,mGold,Math.cos(a)*.55,.0,Math.sin(a)*.55,10))}return g}
// Potenciómetro
function pot(){const g=new THREE.Group();g.add(cyl(.5,.35,M(0xb6a24a,.35,.9),0,0,0,40));
g.add(cyl(.12,1.1,mSil,0,.75,0,40));g.add(cyl(.2,.1,mSil,0,.25,0,6));
const k=cyl(.14,.9,mSil,0,.9,0,40);g.add(k);g.add(box(.9,.12,.6,M(0xc47a1a,.5,0),0,-.2,.4));
for(let i=-1;i<=1;i++)g.add(cyl(.045,.55,mGold,i*.28,-.4,.4,10));g.add(cyl(.4,.32,M(0xf2f2f0,.3,0),0,1.35,0,48));g.add(box(.05,.02,.2,M(0x2ecc71,.4,0,{emissive:0x1faa55}),0,1.52,.2));return g}
// Pulsador
function button(){const g=new THREE.Group();g.add(box(.75,.3,.75,M(0xaab0b6,.35,.9)));g.add(cyl(.2,.28,mBlk,0,.28,0,32));
[[-1,-1],[1,-1],[-1,1],[1,1]].forEach(([x,z])=>{g.add(cyl(.045,.4,mGold,x*.3,-.25,z*.4,8));g.add(cyl(.06,.04,mBlk,x*.3,.16,z*.3,12))});return g}
// Componentes nuevos
const LC=[0x2ecc71,0x3b6cff,0xffc21a,0xff3030];let ledM,ledG,ledL;
function leds(){const g=new THREE.Group();g.add(box(.5,.06,.5,M(0x0c0c0e,.4,.2)));
ledM=M(LC[0],.15,0,{emissive:LC[0],emissiveIntensity:.9});
g.add(cyl(.1,.25,ledM,0,.15,0,20));const d=new THREE.Mesh(new THREE.SphereGeometry(.1,20,12,0,6.283,0,1.6),ledM);d.position.set(0,.27,0);g.add(d);
g.add(cyl(.02,.3,mGold,-.12,-.15,0,8),cyl(.02,.3,mGold,.12,-.15,0,8));
const gc=document.createElement('canvas');gc.width=gc.height=64;const gq=gc.getContext('2d'),gg=gq.createRadialGradient(32,32,0,32,32,32);gg.addColorStop(0,'rgba(255,255,255,1)');gg.addColorStop(.3,'rgba(255,255,255,.35)');gg.addColorStop(1,'rgba(255,255,255,0)');gq.fillStyle=gg;gq.fillRect(0,0,64,64);
ledG=new THREE.Sprite(new THREE.SpriteMaterial({map:new THREE.CanvasTexture(gc),color:LC[0],transparent:true,blending:THREE.AdditiveBlending,depthWrite:false}));ledG.scale.set(1.3,1.3,1);ledG.position.y=.4;g.add(ledG);
ledL=new THREE.PointLight(LC[0],.9,3.5);ledL.position.y=.5;g.add(ledL);return g}
function lanyardW(){const g=new THREE.Group(),l=lanyard();l.rotation.y=-Math.PI/2;g.add(l);return g}
function lanyard(){const g=new THREE.Group();
 const P=[];for(let k=0;k<28;k++){const q=k/28*6.2832;P.push(new THREE.Vector3(-.2-5.5*(1-Math.cos(q)),.25*Math.sin(2*q),3.5*Math.sin(q)*Math.sin(q/2)))}
 const c=new THREE.CatmullRomCurve3(P,true),N=160,pos=[],idx=[],uv=[],up=new THREE.Vector3(0,1,0);
 for(let i=0;i<=N;i++){const t=(i/N)%1,p=c.getPointAt(t),tg=c.getTangentAt(t),w=new THREE.Vector3().crossVectors(up,tg).normalize().multiplyScalar(.13);
  pos.push(p.x+w.x,p.y+w.y,p.z+w.z,p.x-w.x,p.y-w.y,p.z-w.z);uv.push(0,i/N*100,1,i/N*100);if(i<N){const a=i*2;idx.push(a,a+1,a+2,a+1,a+3,a+2)}}
 const geo=new THREE.BufferGeometry();geo.setAttribute('position',new THREE.Float32BufferAttribute(pos,3));geo.setIndex(idx);geo.setAttribute('uv',new THREE.Float32BufferAttribute(uv,2));geo.computeVertexNormals();
 const wc=document.createElement('canvas');wc.width=wc.height=32;const wq=wc.getContext('2d');for(let y=0;y<32;y++)for(let x=0;x<32;x++){const v=((x+y)%8<4)?240:208;wq.fillStyle='rgb('+v+','+v+','+(v-2)+')';wq.fillRect(x,y,1,1)}
 const wt=CT(wc);wt.wrapS=wt.wrapT=THREE.RepeatWrapping;
 const m=new THREE.Mesh(geo,M(0xffffff,.9,0,{side:THREE.DoubleSide,map:wt,bumpMap:wt,bumpScale:.6}));m.castShadow=true;g.add(m);
 g.add(new THREE.Mesh(new THREE.TorusGeometry(.12,.025,10,28),mSil),box(.22,.03,.22,mSil,-.16,0,0),cyl(.07,.04,mSil,-.3,.04,0,16));return g}
function usbc(){const g=new THREE.Group();g.add(box(1,.06,.9,mPCB2));g.add(box(.9,.26,.55,mSil,0,.16,.2));g.add(box(.7,.12,.3,mBlk,0,.16,.42));
for(let i=0;i<4;i++)g.add(cyl(.04,.3,mGold,-.3+i*.2,-.1,-.3,8));return g}
function sw(){const g=new THREE.Group();g.add(box(.5,.35,.9,mBlk));g.add(box(.3,.2,.3,mSil,.3,0,.2));for(let i=0;i<3;i++)g.add(cyl(.03,.3,mGold,-.1,-.3,-.3+i*.3,8));return g}
function micV(){const g=new THREE.Group(),m=mic();m.rotation.x=-Math.PI/2;g.add(m);return g}
function btnSide(){const g=new THREE.Group(),b=button();b.rotation.z=-Math.PI/2;g.add(b);return g}

// Carcasa blanca 9 × 6 × 2,25 cm
const mCase=new THREE.MeshPhysicalMaterial({color:0xf3f3f0,roughness:.3,clearcoat:.8,clearcoatRoughness:.12}),mCase2=M(0xdcdcd8,.4,0),mDk=M(0x0d0d0f,.5,0);
const CW=6,CD=9,CR=1.1,WT=.14,SEAM=1.5,TOP=2.25;
{const c=document.createElement('canvas');c.width=c.height=128;const q=c.getContext('2d'),d=q.createImageData(128,128);for(let i=0;i<d.data.length;i+=4){const v=120+Math.random()*30;d.data[i]=d.data[i+1]=d.data[i+2]=v;d.data[i+3]=255}q.putImageData(d,0,0);const t=new THREE.CanvasTexture(c);t.wrapS=t.wrapT=THREE.RepeatWrapping;t.repeat.set(2,2);mCase.bumpMap=t;mCase.bumpScale=.4}
function rr(w,d,r){const s=new THREE.Shape(),x=-w/2,y=-d/2;s.moveTo(x+r,y);s.lineTo(x+w-r,y);s.quadraticCurveTo(x+w,y,x+w,y+r);s.lineTo(x+w,y+d-r);s.quadraticCurveTo(x+w,y+d,x+w-r,y+d);s.lineTo(x+r,y+d);s.quadraticCurveTo(x,y+d,x,y+d-r);s.lineTo(x,y+r);s.quadraticCurveTo(x,y,x+r,y);return s}
function ex(sh,h,y){const g=new THREE.ExtrudeGeometry(sh,{depth:h,bevelEnabled:true,bevelSize:.03,bevelThickness:.03,bevelSegments:3,curveSegments:24});g.rotateX(-Math.PI/2);const m=new THREE.Mesh(g,mCase);m.position.y=y;m.castShadow=m.receiveShadow=true;return m}
function ring(){const r=rr(CW,CD,CR);r.holes.push(rr(CW-2*WT,CD-2*WT,CR-WT));return r}
function decal(g,m,x,y,z,ry){m.position.set(x,y,z);m.rotation.y=ry||0;g.add(m)}
function caseBase(){const g=new THREE.Group();g.add(ex(rr(CW,CD,CR),.12,0),ex(ring(),SEAM-.15,.12));
 [-1.2,1.2].forEach(x=>decal(g,new THREE.Mesh(new THREE.CircleGeometry(.09,20),mDk),x,1.1,-CD/2-.045,Math.PI));
 decal(g,new THREE.Mesh(new THREE.CircleGeometry(.13,24),mDk),-.5,1.08,CD/2+.045);
 decal(g,box(.7,.2,.04,mDk),2.1,.96,CD/2+.03);
 decal(g,box(.07,.34,.55,mCase2),CW/2+.04,1.2,.8);
 decal(g,box(.05,.28,.95,mDk),CW/2+.03,.85,-.8);decal(g,box(.1,.2,.4,mCase),CW/2+.05,.85,-.55);
 [[-2.2,-3.6],[2.2,-3.6],[-2.2,3.6],[2.2,3.6]].forEach(([x,z])=>g.add(cyl(.32,.08,M(0x2a2b2e,.9,0),x,-.07,z,24)));
 return g}
function caseLid(){const g=new THREE.Group(),top=rr(CW,CD,CR);
 [[-2,1,.17],[2,-1.5,.12]].forEach(([x,z,r])=>{const p=new THREE.Path();p.absarc(x,-z,r,0,6.2832,true);top.holes.push(p)});
 g.add(ex(ring(),TOP-.14-.06-SEAM,SEAM+.03),ex(top,.14,TOP-.14));
 const lc=document.createElement('canvas');lc.width=64;lc.height=200;const q=lc.getContext('2d');q.fillStyle='#0e0e12';q.fillRect(0,0,64,200);q.fillStyle='#e8e8ee';q.font='600 26px Manrope,sans-serif';q.translate(32,100);q.rotate(-Math.PI/2);q.textAlign='center';q.textBaseline='middle';q.fillText('5000mAh',0,0);
 const lab=new THREE.Mesh(new THREE.PlaneGeometry(.5,1.6),M(0xffffff,.3,0,{map:CT(lc)}));lab.rotation.x=-Math.PI/2;lab.position.set(2,2.285,.75);g.add(lab);
 const ey=new THREE.Mesh(new THREE.TorusGeometry(.25,.05,10,28),mSil);ey.rotation.x=Math.PI/2;ey.position.set(0,1.9,-4.9);g.add(ey,box(.3,.1,.45,mCase,0,1.9,-4.65));
 g.traverse(o=>{o.castShadow=false});return g}

const mBlue=M(0x1b5fcc,.4,.1),mTan=M(0xb59a6a,.5,.2);
function tp4056(){const g=new THREE.Group();g.add(box(1.5,.08,2.6,mBlue));
 g.add(box(.9,.32,.7,mSil,0,.2,-.95),box(.7,.1,.04,mBlk,0,.2,-1.32));
 g.add(box(.45,.1,.35,mChip,0,.09,.1),box(.4,.08,.3,mChip,.3,.08,.8),box(.15,.06,.15,mChip,-.4,.07,.9),box(.2,.07,.2,mTan,-.4,.075,.2));
 [0xff3030,0x2ecc71].forEach((c,i)=>g.add(box(.14,.05,.1,M(c,.3,0,{emissive:c,emissiveIntensity:.6}),-.55,.07,.3+i*.2)));
 for(let i=0;i<8;i++)g.add(box(.12,.05,.07,i%2?mChip:mTan,-.55+(i%4)*.35,.07,-.2+Math.floor(i/4)*.5));
 [[-.55,1.1],[.55,1.1],[-.55,-1.1],[.55,-1.1]].forEach(([x,z])=>g.add(cyl(.12,.1,mGold,x,.01,z,16)));return g}
function mt3608(){const g=new THREE.Group();g.add(box(1.5,.08,3.6,mBlue));
 g.add(box(.85,.32,.85,M(0x1a1b1f,.35,.5),0,.2,.6),box(.6,.3,.6,M(0x1c4fd0,.5,0),0,.19,-.9),cyl(.08,.06,mGold,0,.37,-.9,12));
 g.add(box(.4,.1,.2,mBlk,0,.09,1.4),box(.2,.06,.2,mChip,.1,.07,-.2),box(.12,.1,.2,mTan,-.3,.09,-.2),box(.12,.1,.2,mTan,.4,.09,-.3));
 [[-.5,1.55],[.5,1.55],[-.5,-1.55],[.5,-1.55]].forEach(([x,z])=>g.add(cyl(.13,.1,mGold,x,.01,z,16)));return g}
function pcb(){const g=new THREE.Group(),W=5.2,D=7.2;g.add(box(W,.08,D,M(0x0f6b3c,.45,.1)));
 const c=document.createElement('canvas');c.width=520;c.height=720;const q=c.getContext('2d');q.fillStyle='#0f6b3c';q.fillRect(0,0,520,720);
 let sd=7;const rnd=()=>(sd=(sd*16807)%2147483647)/2147483647;q.lineCap='round';q.lineJoin='round';
 for(let i=0;i<70;i++){let x=40+rnd()*440,y=40+rnd()*640;q.strokeStyle='#37b374';q.lineWidth=4;q.beginPath();q.moveTo(x,y);
  for(let k=0;k<3;k++){const l=30+rnd()*90,d=Math.floor(rnd()*3);if(d==0)x+=l;else if(d==1)y+=l;else{x+=l*.7;y+=l*.7}q.lineTo(x,y)}q.stroke();q.fillStyle='#d9a93a';q.beginPath();q.arc(x,y,5,0,6.3);q.fill()}
 [[25,25],[495,25],[25,695],[495,695]].forEach(([x,y])=>{q.fillStyle='#d9a93a';q.beginPath();q.arc(x,y,16,0,6.3);q.fill();q.fillStyle='#07140d';q.beginPath();q.arc(x,y,8,0,6.3);q.fill()});
 q.strokeStyle='#e9efe9';q.lineWidth=2;q.strokeRect(10,10,500,700);q.fillStyle='#e9efe9';q.font='600 18px sans-serif';q.fillText('MAIN PCB · v1.0',150,62);
 const top=new THREE.Mesh(new THREE.PlaneGeometry(W,D),M(0xffffff,.4,.1,{map:CT(c)}));top.rotation.x=-Math.PI/2;top.position.y=.041;g.add(top);
 for(let i=0;i<22;i++)g.add(box(.18,.06,.1,M(i%3?0x1b1b1d:0xb59a6a,.5,.2),-2.3+rnd()*4.6,.07,-3.3+rnd()*4.2));
 [[-1.3,-3],[1.5,-2.6],[1.7,-.6]].forEach(([x,z])=>g.add(box(.55,.08,.55,mChip,x,.08,z)));return g}

const world=new THREE.Group();S.add(world);
const floor=new THREE.Mesh(new THREE.CircleGeometry(14,64),new THREE.ShadowMaterial({opacity:.35}));floor.rotation.x=-Math.PI/2;floor.position.y=-6.4;floor.receiveShadow=true;world.add(floor);
{const c=document.createElement('canvas');c.width=c.height=256;const q=c.getContext('2d'),gr=q.createRadialGradient(128,128,0,128,128,128);gr.addColorStop(0,'rgba(79,209,165,.35)');gr.addColorStop(.5,'rgba(79,209,165,.08)');gr.addColorStop(1,'rgba(79,209,165,0)');q.fillStyle=gr;q.fillRect(0,0,256,256);
 const gl=new THREE.Mesh(new THREE.PlaneGeometry(26,26),new THREE.MeshBasicMaterial({map:CT(c),transparent:true,depthWrite:false,blending:THREE.AdditiveBlending}));gl.rotation.x=-Math.PI/2;gl.position.y=-6.35;world.add(gl);
 const n=220,ps=new Float32Array(n*3);for(let i=0;i<n;i++){ps[i*3]=(Math.random()-.5)*28;ps[i*3+1]=(Math.random()-.5)*20;ps[i*3+2]=(Math.random()-.5)*28}
 const pg=new THREE.BufferGeometry();pg.setAttribute('position',new THREE.BufferAttribute(ps,3));dust=new THREE.Points(pg,new THREE.PointsMaterial({color:0xcfe9ff,size:.06,transparent:true,opacity:.45,depthWrite:false}));S.add(dust)}
const parts=[
 {n:'Carcasa blanca · base',o:caseBase(),a:[0,0,0],e:[0,-5.2,0],lo:new THREE.Vector3(3.3,.8,0)},
 {n:'Batería LiPo 3,7 V · 5000 mAh',o:battery(),a:[0,.38,0],e:[0,-3.4,0]},
 {n:'PCB principal',o:pcb(),a:[0,.66,0],e:[0,-2.5,0]},
 {n:'Cargador TP4056 USB-C',o:tp4056(),a:[1.8,.74,-2.5],e:[4.3,-2.5,-2.2]},
 {n:'Elevador de voltaje MT3608',o:mt3608(),a:[-1.8,.74,-2],e:[-4.4,-2.2,-2.2]},
 {n:'Teensy Audio Shield · Jack 3,5 mm',o:shield(),a:[0,.78,2.55],e:[0,-1.6,2.55]},
 {n:'Teensy 4.1',o:teensy(),a:[0,1.02,.9],e:[0,.3,.9]},
 {n:'Micrófono INMP441 · 1',o:micV(),a:[1.2,1.1,-4.2],e:[3.4,1.3,-4.6]},
 {n:'Micrófono INMP441 · 2',o:micV(),a:[-1.2,1.1,-4.2],e:[-3.4,1.9,-4.6]},
 {n:'Regulador de volumen',o:pot(),a:[-2,1.1,1],e:[-4.6,1.6,1]},
 {n:'LED de estado',o:leds(),a:[2,1.85,-1.5],e:[3.8,3.2,-1.5]},
 {n:'Botón de modos',o:btnSide(),a:[2.5,1.2,.8],e:[4.6,2.4,1.2]},
 {n:'Interruptor de encendido',o:sw(),a:[2.5,.85,-.8],e:[4.6,.4,-1.4]},
 {n:'Cinta blanca (lanyard)',o:lanyardW(),a:[0,1.9,-5.15],e:[0,4.2,-3]},
 {n:'Carcasa blanca · tapa',o:caseLid(),a:[0,0,0],e:[0,4,0],lo:new THREE.Vector3(3.3,2.2,0)}
];
parts.forEach((p,i)=>{p.o.position.set(...p.a);p.ph=i*1.7;world.add(p.o);
 const d=document.createElement('div');d.className='lb';d.textContent=p.n;document.body.appendChild(d);p.l=d;
 const pts=[new THREE.Vector3(...p.a),new THREE.Vector3(...p.e)];p.line=new THREE.Line(new THREE.BufferGeometry().setFromPoints(pts),new THREE.LineDashedMaterial({color:0x4fd1a5,dashSize:.15,gapSize:.12,transparent:true,opacity:.35}));
 p.line.computeLineDistances();world.add(p.line)});

let rotY=-.6,rotX=.28,dist=28,paused=false,manual=null,tm=0,drag=false,lx=0,ly=0,idle=0;
const ss=x=>x*x*(3-2*x),cl=x=>Math.max(0,Math.min(1,x));
function size(){const w=innerWidth,h=innerHeight;R.setSize(w,h,false);cam.aspect=w/h;cam.fov=w<h?55:35;cam.updateProjectionMatrix()}
addEventListener('resize',size);size();
const ptr=new Map();let pd=0;
cv.addEventListener('pointerdown',e=>{ptr.set(e.pointerId,[e.clientX,e.clientY]);drag=true;lx=e.clientX;ly=e.clientY;idle=0;cv.setPointerCapture(e.pointerId);if(ptr.size==2){const [a,b]=[...ptr.values()];pd=Math.hypot(a[0]-b[0],a[1]-b[1])}});
const up=e=>{ptr.delete(e.pointerId);drag=ptr.size==1;if(ptr.size==1){const [a]=[...ptr.values()];lx=a[0];ly=a[1]}};
cv.addEventListener('pointerup',up);cv.addEventListener('pointercancel',up);
cv.addEventListener('pointermove',e=>{if(!ptr.has(e.pointerId))return;ptr.set(e.pointerId,[e.clientX,e.clientY]);
 if(ptr.size==2){const [a,b]=[...ptr.values()],d=Math.hypot(a[0]-b[0],a[1]-b[1]);if(d>0){dist=Math.max(12,Math.min(44,dist*pd/d));pd=d}return}
 rotY+=(e.clientX-lx)*.008;rotX=Math.max(-.2,Math.min(1.2,rotX+(e.clientY-ly)*.006));lx=e.clientX;ly=e.clientY});
cv.addEventListener('wheel',e=>{dist=Math.max(12,Math.min(44,dist+e.deltaY*.01));e.preventDefault()},{passive:false});
document.getElementById('b1').onclick=e=>{paused=!paused;e.target.textContent=paused?'Reanudar':'Pausar'};
document.getElementById('b2').onclick=()=>{const cur=manual===null?cycleE(tm):manual;manual=cur>.5?0:1;tm=manual?3:9};
document.getElementById('b3').onclick=()=>document.body.classList.toggle('nolb');
function cycleE(t){const c=t%14;if(c<2)return 0;if(c<5)return ss((c-2)/3);if(c<9)return 1;if(c<12)return 1-ss((c-9)/3);return 0}
const clock=new THREE.Clock(),V=new THREE.Vector3();let eNow=0,eTarget=0;
function frame(){const dt=Math.min(clock.getDelta(),.05);
 if(!paused){tm+=dt;idle+=dt;if(!drag&&idle>1)rotY+=dt*.15}
 const tgt=manual===null?cycleE(tm):manual;eNow+=(tgt-eNow)*Math.min(1,dt*(manual===null?30:2.2));
 const T=clock.elapsedTime;{const c=LC[Math.floor(T/1.5)%4];ledM.color.setHex(c);ledM.emissive.setHex(c);ledG.material.color.setHex(c);ledL.color.setHex(c);dust.rotation.y=T*.01}
 parts.forEach((p,i)=>{const k=ss(cl(eNow*1.8-i*.06));
  p.o.position.set(p.a[0]+(p.e[0]-p.a[0])*k,p.a[1]+(p.e[1]-p.a[1])*k+Math.sin(T*.9+p.ph)*.12*k,p.a[2]+(p.e[2]-p.a[2])*k);
  p.o.rotation.set(Math.sin(T*.6+p.ph)*.08*k,Math.sin(T*.4+p.ph)*.35*k,Math.cos(T*.5+p.ph)*.06*k);
  p.line.material.opacity=.4*k;p.l.style.opacity=.25+.75*k});
 world.rotation.y=rotY;
 const dd=dist*(cam.aspect<1?1.15:1);cam.position.set(0,dd*Math.sin(rotX)*.6+1.5,dd*Math.cos(rotX)*.9+dd*.3);cam.lookAt(-2.5,.8+eNow*.4,0);
 world.updateMatrixWorld();
 parts.forEach(p=>{V.copy(p.o.position).add(p.lo||new THREE.Vector3(0,.4,0));V.applyMatrix4(world.matrixWorld).project(cam);
  p.l.style.transform=`translate(${(V.x*.5+.5)*innerWidth+14}px,${(-V.y*.5+.5)*innerHeight-10}px)`});
 R.render(S,cam);requestAnimationFrame(frame)}
if(matchMedia('(prefers-reduced-motion: reduce)').matches){paused=true;document.getElementById('b1').textContent='Reanudar'}
frame();
</script>
</body>
</html>
