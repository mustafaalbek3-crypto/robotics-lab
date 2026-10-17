[3D Spatial Frames Lab (1).html](https://github.com/user-attachments/files/33599004/3D.Spatial.Frames.Lab.1.html)
 name=viewport content="width=device-width,initial-scale=1,viewport-fit=cover"><style>:root{color-scheme:light;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}html{scroll-padding-top:env(safe-area-inset-top,0px)}body{margin:0;padding:0;font:14px -apple-system,BlinkMacSystemFont,sans-serif;background:#fff;color:#000}img{max-width:100%}[hidden]:not([hidden=until-found i]){display:none!important}</style>

<html lang="en" dir="ltr">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>3D Spatial Frames Lab</title>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;600;700&display=swap" rel="stylesheet">
<style>
:root{--bg:#fff;--panel:#fff;--soft:#f3f6f5;--ink:#16302f;--mute:#667c79;--line:#dce4e2;--x:#e03b3b;--y:#2f9e4f;--z:#2f6fe0;--acc:#16302f;--or:#d9820f}
*{box-sizing:border-box}
body{margin:0;background:#fff;color:var(--ink);font:400 15px/1.6 "IBM Plex Sans",system-ui,sans-serif}
.app{display:grid;grid-template-columns:1fr;gap:14px;padding:12px;padding-top:calc(12px + env(safe-area-inset-top,0px));max-width:1400px;margin:0 auto}
#side{min-width:0}
#view{position:relative;order:-1;height:52vh;min-height:300px;border-radius:14px;background:#fff;border:1px solid var(--line);overflow:hidden}
@media (min-width:900px){
 .app{grid-template-columns:410px 1fr;align-items:start}
 #view{order:0;position:sticky;top:12px;height:calc(100vh - 64px)}
 #side{max-height:calc(100vh - 64px);overflow-y:auto;padding-inline-end:6px}
}
canvas{width:100%;height:100%;display:block;touch-action:none}
#hint{position:absolute;inset-inline:0;bottom:6px;text-align:center;font-size:12px;color:var(--mute);pointer-events:none}
.hd{display:flex;align-items:center;gap:12px;margin:0 0 8px}
.hd h1{font-size:22px;font-weight:700;margin:0;line-height:1.25}
.sub{font-size:12px;color:var(--mute)}
.bar{display:flex;height:4px;border-radius:4px;overflow:hidden;margin:0 0 12px}.bar i{flex:1}
.bar i:nth-child(1){background:var(--x)}.bar i:nth-child(2){background:var(--y)}.bar i:nth-child(3){background:var(--z)}
.sec{display:flex;align-items:center;gap:8px;font-size:12px;font-weight:600;color:var(--mute);margin:14px 0 6px}
.sec b{display:inline-grid;place-items:center;width:20px;height:20px;border-radius:50%;background:var(--acc);color:#fff;font-size:11px}
.seg{display:flex;flex-wrap:wrap;gap:6px;margin:0 0 6px}
.seg button{flex:1 1 auto;padding:8px 8px;border:1px solid var(--line);background:#fff;color:var(--ink);border-radius:10px;font:inherit;font-size:13px;cursor:pointer}
.seg button[aria-pressed="true"]{background:var(--acc);color:#fff;border-color:var(--acc)}
.note{font-size:13px;color:var(--mute);margin:0 0 8px}
fieldset{border:1px solid var(--line);background:#fff;border-radius:14px;margin:0 0 10px;padding:6px 12px 10px;box-shadow:0 1px 2px rgba(22,48,47,.05)}
legend{font-weight:600;padding:0 6px}
fieldset.fa{border-inline-start:5px solid #0e9aa7}fieldset.fb{border-inline-start:5px solid #e8890c}
.guide{background:var(--soft);border:1px solid var(--line);border-radius:12px;padding:6px 12px;margin:0;font-size:13px}.guide summary{font-weight:600;cursor:pointer}.guide ol{margin:6px 0 2px;padding-inline-start:18px}
.sw{display:inline-block;width:12px;height:12px;border-radius:50%;margin-inline-end:6px;vertical-align:middle}
.row{display:grid;grid-template-columns:24px 1fr 78px;align-items:center;gap:8px;margin-top:4px}
.row b{font-size:15px;text-align:center}
.row input[type=number]{width:100%;padding:5px 6px;border:1px solid var(--line);border-radius:8px;background:var(--soft);color:var(--ink);font:inherit;font-size:13px;font-variant-numeric:tabular-nums;text-align:right}
input[type=range]{width:100%;height:30px}
.rx{accent-color:var(--x)}.ry{accent-color:var(--y)}.rz{accent-color:var(--z)}
.cx{color:var(--x)}.cy{color:var(--y)}.cz{color:var(--z)}
.mat{display:grid;gap:4px;max-width:340px;margin:8px auto;text-align:center;font-variant-numeric:tabular-nums}
.mat span{padding:5px 0;border-radius:8px;background:var(--soft);font-size:14px}
.m3 span:nth-child(3n+1),.m4 span:nth-child(4n+1){color:var(--x)}
.m3 span:nth-child(3n+2),.m4 span:nth-child(4n+2){color:var(--y)}
.m3 span:nth-child(3n),.m4 span:nth-child(4n+3){color:var(--z)}
.m4 span:nth-child(4n){color:var(--or)}
.kv{display:flex;justify-content:space-between;gap:8px;margin:4px 0;font-size:14px}
.kv b{font-variant-numeric:tabular-nums;font-weight:600}
.reset{width:100%;padding:10px;border-radius:10px;border:1px solid var(--line);background:#fff;color:var(--ink);font:inherit;cursor:pointer}
.ft{text-align:center;font-size:12px;line-height:1.7;color:#6f8582;padding:6px 12px 14px;padding-bottom:calc(14px + env(safe-area-inset-bottom,0px))}
.ft b{color:var(--ink);font-weight:600}
.chk{display:flex;gap:8px;align-items:flex-start;font-size:13px;margin:8px 0}.chk input{margin-top:4px}
button:focus-visible,input:focus-visible{outline:2px solid var(--z);outline-offset:2px}
</style>
</head>
<body>
<div class="app">
<aside id="side">
<div class="hd">
<svg width="44" height="44" viewBox="0 0 42 42" aria-hidden="true"><g stroke-width="3" stroke-linecap="round"><line x1="10" y1="32" x2="34" y2="32" stroke="#e03b3b"/><line x1="10" y1="32" x2="10" y2="9" stroke="#2f6fe0"/><line x1="10" y1="32" x2="25" y2="19" stroke="#2f9e4f"/></g><polygon points="34,27.5 40,32 34,36.5" fill="#e03b3b"/><polygon points="5.5,10 10,3 14.5,10" fill="#2f6fe0"/><polygon points="21,18 29,15.5 27,23.5" fill="#2f9e4f"/><circle cx="10" cy="32" r="3.5" fill="#16302f"/></svg>
<div><h1>3D Spatial Frames Lab</h1><div class="sub">Robotics I · Lecture 2: Spatial Description</div></div>
</div>
<div class="bar"><i></i><i></i><i></i></div>
<details class="guide" open><summary>What to try</summary><ol>
<li>“Frame” tab: move and rotate the frame and watch the matrix R. Each column is the direction of one frame axis.</li>
<li>Switch between “About world axes” and “About frame axes” with the same angles; the results differ.</li>
<li>“Compare A &amp; B” tab: see T = A⁻¹·B, the pose of B as seen from A.</li>
<li>“Point” tab: q is fixed inside the frame while P moves in the world.</li>
<li>“Fixed vs Euler” tab: apply the same three angles both ways, step by step, and compare the two results.</li>
<li>Type exact values (angles in degrees) in the boxes next to the sliders.</li></ol></details>
<div class="sec"><b>1</b>Choose a section</div>
<div class="seg" id="tabs" role="group" aria-label="Sections"></div>
<p class="note" id="tabNote"></p>
<div id="modeBox"><div class="sec"><b>2</b>Rotation type</div>
<div class="seg" id="modeSeg" role="group" aria-label="Rotation type">
<button id="mWorld" aria-pressed="true">About world axes</button>
<button id="mLocal" aria-pressed="false">About frame axes</button>
</div>
<p class="note" id="modeNote"></p></div>
<div class="sec"><b>3</b>Frame controls</div>
<div id="ctl"></div>
<div class="sec"><b>4</b>Results</div>
<fieldset><legend id="outT">Results</legend><div id="out" aria-live="polite"></div></fieldset>
<button class="reset" id="reset">Reset</button>
</aside>
<div id="view"><canvas id="c"></canvas><div id="hint">Drag to orbit, pinch or scroll to zoom</div></div>
</div>
<footer class="ft">By <b>Mustafa Albek</b><br>Under the supervision of <b>Mr. Yazan Shaker</b></footer>
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script>
(function(){
var COL={x:0xe03b3b,y:0x2f9e4f,z:0x2f6fe0},T=THREE;
var cv=document.getElementById('c'),view=document.getElementById('view');
var renderer=new T.WebGLRenderer({canvas:cv,antialias:true,alpha:true});
renderer.setPixelRatio(Math.min(devicePixelRatio||1,2));
var scene=new T.Scene(),cam=new T.PerspectiveCamera(45,1,0.1,200);cam.up.set(0,0,1);
scene.add(new T.AmbientLight(0xffffff,0.75));
var dl=new T.DirectionalLight(0xffffff,0.6);dl.position.set(3,-4,6);scene.add(dl);
var grid=new T.GridHelper(14,14,0xb9c8c5,0xdbe4e2);grid.rotation.x=Math.PI/2;scene.add(grid);

/* text sprites */
function mkText(cw,ch,sx,sy){
  var c=document.createElement('canvas');c.width=cw;c.height=ch;var g=c.getContext('2d');g.direction='ltr';
  var tex=new T.CanvasTexture(c);
  var sp=new T.Sprite(new T.SpriteMaterial({map:tex,transparent:true,depthTest:false}));sp.scale.set(sx,sy,1);sp.renderOrder=10;
  return{sp:sp,draw:function(lines,col,fs,border){
    g.clearRect(0,0,cw,ch);
    if(border){var r=14,x=3,y=3,w=cw-6,h=ch-6;g.beginPath();g.moveTo(x+r,y);g.arcTo(x+w,y,x+w,y+h,r);g.arcTo(x+w,y+h,x,y+h,r);g.arcTo(x,y+h,x,y,r);g.arcTo(x,y,x+w,y,r);g.closePath();
      g.fillStyle='rgba(255,255,255,0.93)';g.fill();g.lineWidth=4;g.strokeStyle=border;g.stroke();}
    g.fillStyle=col;g.font='600 '+fs+'px sans-serif';g.textAlign='center';g.textBaseline='middle';
    var n=lines.length;lines.forEach(function(t,i){g.fillText(t,cw/2,ch*(i+0.5)/n+2);});
    tex.needsUpdate=true;}};
}
function label(t,color,sz){
  var c=document.createElement('canvas');c.width=c.height=64;
  var g=c.getContext('2d');g.font='bold 48px sans-serif';g.textAlign='center';g.textBaseline='middle';
  g.fillStyle='#'+color.toString(16).padStart(6,'0');g.fillText(t,32,34);
  var s=new T.Sprite(new T.SpriteMaterial({map:new T.CanvasTexture(c),transparent:true,depthTest:false}));
  s.scale.set(sz,sz,1);return s;
}
function badge(t,col,sz){
  var c=document.createElement('canvas');c.width=c.height=128;var g=c.getContext('2d');
  g.fillStyle='#'+col.toString(16).padStart(6,'0');g.beginPath();g.arc(64,64,58,0,7);g.fill();
  g.lineWidth=7;g.strokeStyle='#ffffff';g.stroke();
  g.fillStyle='#fff';g.font='bold 78px sans-serif';g.textAlign='center';g.textBaseline='middle';g.fillText(t,64,68);
  var s=new T.Sprite(new T.SpriteMaterial({map:new T.CanvasTexture(c),transparent:true,depthTest:false}));s.scale.set(sz,sz,1);return s;}
function frame(len,th,op,hc,bt){
  var g=new T.Group();
  [['x',0,0,-Math.PI/2],['y',0,0,0],['z',Math.PI/2,0,0]].forEach(function(a){
    var m=new T.MeshStandardMaterial({color:COL[a[0]],transparent:op<1,opacity:op});
    var arm=new T.Group();
    var cy=new T.Mesh(new T.CylinderGeometry(th,th,len,16),m);cy.position.y=len/2;
    var co=new T.Mesh(new T.ConeGeometry(th*2.6,len*0.16,20),m);co.position.y=len*1.08;
    var lb=label(a[0].toUpperCase(),COL[a[0]],len*0.3);lb.position.y=len*1.32;lb.material.opacity=op;
    arm.add(cy,co,lb);arm.rotation.set(a[1],a[2],a[3]);g.add(arm);
  });
  g.add(new T.Mesh(new T.SphereGeometry(th*2.2,20,20),new T.MeshStandardMaterial({color:hc||0x888888,transparent:op<1,opacity:op})));
  if(bt){var rg=new T.Mesh(new T.RingGeometry(len*0.34,len*0.4,48),new T.MeshBasicMaterial({color:hc,transparent:true,opacity:.55,side:T.DoubleSide,depthWrite:false}));g.add(rg);
    var b=badge(bt,hc,len*0.5);b.position.set(-len*0.3,-len*0.3,len*0.3);g.add(b);g.userData.badge=b;}
  return g;
}
scene.add(frame(6,0.05,0.3));

/* numbered world grid */
function tick(txt,col,x,y,z){var t=mkText(64,64,0.4,0.4);t.draw([txt],col,40);t.sp.position.set(x,y,z);scene.add(t.sp);}
for(var i=-7;i<=7;i++){if(!i)continue;tick(String(i),'#d46a6a',i,-0.35,0);tick(String(i),'#4fae6c',-0.35,i,0);}
for(var k=1;k<=5;k++)tick(String(k),'#5b87e0',-0.35,-0.35,k);
tick('0','#6b7f7c',-0.35,-0.35,0);

var CA=0x0e9aa7,CB=0xe8890c;
var fA=frame(2.6,0.09,1,CA,'A'),fB=frame(2.6,0.09,1,CB,'B');scene.add(fA,fB);
var fF=frame(2.6,0.09,1,CA,'F'),fE=frame(2.6,0.09,1,CB,'E'),gF=frame(2.6,0.03,0.35),gE=frame(2.6,0.03,0.35);
fF.position.set(0,-3,0);gF.position.set(0,-3,0);fE.position.set(0,3,0);gE.position.set(0,3,0);
scene.add(fF,fE,gF,gE);fF.visible=fE.visible=gF.visible=gE.visible=false;
var P=new T.Mesh(new T.SphereGeometry(0.16,20,20),new T.MeshStandardMaterial({color:0xf0a020}));scene.add(P);
function mkLine(c,dash){var g=new T.BufferGeometry();g.setAttribute('position',new T.BufferAttribute(new Float32Array(6),3));
  var l=new T.Line(g,dash?new T.LineDashedMaterial({color:c,dashSize:.15,gapSize:.1}):new T.LineBasicMaterial({color:c}));l.frustumCulled=false;scene.add(l);return l;}
var lnA=mkLine(0xf0a020,false),lnO=mkLine(0x8aa3a0,true);
function setLn(l,a,b){var p=l.geometry.attributes.position.array;p.set([a.x,a.y,a.z,b.x,b.y,b.z]);l.geometry.attributes.position.needsUpdate=true;l.computeLineDistances();}

/* numbers on frames: info box + staircase x,y,z */
function mkInfo(){var t=mkText(520,130,3.2,0.8);scene.add(t.sp);return t;}
var infoA=mkInfo(),infoB=mkInfo();
var infoP=mkText(420,80,2.4,0.46);scene.add(infoP.sp);
var SC=['#e03b3b','#2f9e4f','#2f6fe0'];
function mkStair(){var o={lines:[],labs:[]};[0xe03b3b,0x2f9e4f,0x2f6fe0].forEach(function(c){o.lines.push(mkLine(c,true));var t=mkText(160,64,0.95,0.38);scene.add(t.sp);o.labs.push(t);});return o;}
var stA=mkStair(),stB=mkStair();
function V(a){return new T.Vector3(a[0],a[1],a[2]);}
function updStair(st,x,y,z,vis){
  var p=[[0,0,0],[x,y*0+x,0],[x,y,0],[x,y,z]];p[1]=[x,0,0];
  var d=[x,y,z],nm=['x','y','z'],off=[[0,0,.25],[.3,0,.25],[.45,0,0]];
  for(var i=0;i<3;i++){
    var show=vis&&Math.abs(d[i])>0.02;
    setLn(st.lines[i],V(p[i]),V(p[i+1]));st.lines[i].visible=show;st.labs[i].sp.visible=show;
    if(show){st.labs[i].draw([nm[i]+' = '+d[i].toFixed(1)],SC[i],34,SC[i]);
      st.labs[i].sp.position.set((p[i][0]+p[i+1][0])/2+off[i][0],(p[i][1]+p[i+1][1])/2+off[i][1],(p[i][2]+p[i+1][2])/2+off[i][2]);}
  }
}
function updInfo(info,pre,o,border){
  var n=function(v){return (+v).toFixed(1);};
  info.draw(['p = ('+n(S[pre+'x'])+', '+n(S[pre+'y'])+', '+n(S[pre+'z'])+')','θ = ('+S[pre+'rx']+'°, '+S[pre+'ry']+'°, '+S[pre+'rz']+'°)'],'#16302f',34,border);
  info.sp.position.set(o.x,o.y,o.z-1.6);
}

var th=0.9,ph=1.1,rad=15;
function place(){cam.position.set(rad*Math.sin(ph)*Math.cos(th),rad*Math.sin(ph)*Math.sin(th),rad*Math.cos(ph));cam.lookAt(0,0,1);}
var pts={},last=0;
cv.addEventListener('pointerdown',function(e){cv.setPointerCapture(e.pointerId);pts[e.pointerId]=[e.clientX,e.clientY];});
function up(e){delete pts[e.pointerId];last=0;}
cv.addEventListener('pointerup',up);cv.addEventListener('pointercancel',up);
cv.addEventListener('pointermove',function(e){
  var p=pts[e.pointerId];if(!p)return;var ids=Object.keys(pts);
  if(ids.length===1){th-=(e.clientX-p[0])*0.01;ph=Math.min(3,Math.max(0.2,ph-(e.clientY-p[1])*0.01));}
  pts[e.pointerId]=[e.clientX,e.clientY];
  if(ids.length===2){var a=pts[ids[0]],b=pts[ids[1]],d=Math.hypot(a[0]-b[0],a[1]-b[1]);if(last)rad=Math.min(40,Math.max(5,rad*last/d));last=d;}
  place();
});
cv.addEventListener('wheel',function(e){e.preventDefault();rad=Math.min(40,Math.max(5,rad*(1+e.deltaY*0.001)));place();},{passive:false});
function resize(){var w=view.clientWidth,h=view.clientHeight;renderer.setSize(w,h,false);cam.aspect=w/h;cam.updateProjectionMatrix();}
addEventListener('resize',resize);
if(window.ResizeObserver)new ResizeObserver(resize).observe(view);

function el(i){return document.getElementById(i);}
function f(n){return (Math.abs(n)<0.005?0:n).toFixed(2);}
function vec(v){return '('+f(v.x)+', '+f(v.y)+', '+f(v.z)+')';}
function kv(a,b){return '<div class="kv"><span>'+a+'</span><b>'+b+'</b></div>';}
function mat(m,n){var e=m.elements,h='<div class="mat m'+n+'" style="grid-template-columns:repeat('+n+',1fr)">';
  for(var r=0;r<n;r++)for(var c=0;c<n;c++)h+='<span>'+f(e[c*4+r])+'</span>';return h+'</div>';}

var DEF={Ax:0,Ay:0,Az:0,Arx:0,Ary:0,Arz:0,Bx:2,By:1,Bz:0.5,Brx:0,Bry:0,Brz:40,qx:1,qy:0.5,qz:0.5,Ex:60,Ey:30,Ez:45};
var S=Object.assign({},DEF),tab='f',world=true,D=Math.PI/180,erev=false;
var TABS=[['f','Frame'],['c','Compare A & B'],['p','Point'],['e','Fixed vs Euler']];
var NOTE={
 f:'Move and rotate the frame and watch the rotation matrix. The x, y, z offsets appear on the dashed lines, and the position and angles in the box below the frame.',
 c:'T = A⁻¹·B is frame B as seen from A. The last column is the position of B in A’s coordinates, and the 3×3 block is the relative rotation. Frame A has a teal ring, frame B an orange ring.',
 p:'The point q is defined inside the frame; its world position is P = T·q. Move the frame and see P move while q stays fixed. The distance |q| from the frame origin never changes.',
 e:'The same three angles (a about X, b about Y, c about Z) are applied in the same order in two ways. Fixed angles rotate about the fixed world axes (the faint ghost axes). Euler angles rotate about the axes of the frame as it moves. Press Play (or any step button) to watch each rotation happen smoothly; the colored bar through each frame is the axis it is turning about, and the two frames diverge after step 1. Tick the box to see the equivalence: Euler X→Y→Z with (a, b, c) equals fixed Z→Y→X with (c, b, a).'};
var MN={w:'Order: rotate about fixed X, then Y, then Z: R = Rz·Ry·Rx.',l:'Rotation about the moving frame axes: R = Rx·Ry·Rz (like robot joints).'};
function rot(a,b,c){
  var X=new T.Matrix4().makeRotationX(a*D),Y=new T.Matrix4().makeRotationY(b*D),Z=new T.Matrix4().makeRotationZ(c*D);
  return world?Z.multiply(Y).multiply(X):X.multiply(Y).multiply(Z);
}
function M(p){p=p||'A';return new T.Matrix4().makeTranslation(S[p+'x'],S[p+'y'],S[p+'z']).multiply(rot(S[p+'rx'],S[p+'ry'],S[p+'rz']));}
var sc=new T.Vector3();
function row(s){
  var ang=!!s[5];
  return '<div class="row"><b class="c'+s[6]+'">'+s[1]+'</b><input class="r'+s[6]+'" type="range" data-id="'+s[0]+'" min="'+s[2]+'" max="'+s[3]+'" step="'+s[4]+'" value="'+S[s[0]]+'" aria-label="'+s[1]+' slider"><input type="number" data-n="'+s[0]+'" data-ang="'+(ang?1:0)+'" step="'+(ang?1:0.1)+'" value="'+S[s[0]]+'" aria-label="'+s[1]+(ang?' angle in degrees':' value')+'"></div>';
}
function grp(t,l,cls,col){return '<fieldset class="'+(cls||'')+'"><legend>'+(col?'<i class="sw" style="background:'+col+'"></i>':'')+t+'</legend>'+l.map(row).join('')+'</fieldset>';}
function pos(p,t,c,col){return grp(t,[[p+'x','X',-4,4,.1,'','x'],[p+'y','Y',-4,4,.1,'','y'],[p+'z','Z',-4,4,.1,'','z']],c,col);}
function rt(p,t,c,col){return grp(t,[[p+'rx','X (deg)',-180,180,1,'°','x'],[p+'ry','Y (deg)',-180,180,1,'°','y'],[p+'rz','Z (deg)',-180,180,1,'°','z']],c,col);}
var FS=['R = I','R = Rx','R = Ry·Rx','R = Rz·Ry·Rx'],FR=['R = I','R = Rz','R = Ry·Rz','R = Rx·Ry·Rz'],ES=['R = I','R = Rx','R = Rx·Ry','R = Rx·Ry·Rz'];
function eCtl(){
  var names=['Start','1 · X','2 · Y','3 · Z'],cur=Math.round(ep);
  return '<div class="seg" id="steps">'+names.map(function(n,i){return '<button data-step="'+i+'" aria-pressed="'+(i===cur&&!anim)+'">'+n+'</button>';}).join('')+'<button id="play">'+(anim?'⏸ Pause':'▶ Play')+'</button></div>'+
   '<label class="chk"><input type="checkbox" id="rev"'+(erev?' checked':'')+'><span>Apply fixed angles in reverse order (Z, Y, X)</span></label>'+
   grp('Angles in degrees: a (X), b (Y), c (Z)',[['Ex','X',-180,180,1,'°','x'],['Ey','Y',-180,180,1,'°','y'],['Ez','Z',-180,180,1,'°','z']]);
}
/* continuous animation: ep goes 0..3, each whole number is one finished rotation step */
var ep=3,anim=null;
var axG=new T.CylinderGeometry(0.05,0.05,9,12);
var axF=new T.Mesh(axG,new T.MeshBasicMaterial({color:0xe03b3b,transparent:true,opacity:.6}));
var axE=new T.Mesh(axG,new T.MeshBasicMaterial({color:0xe03b3b,transparent:true,opacity:.6}));
scene.add(axF,axE);axF.visible=axE.visible=false;
function setAx(m,o,dir,col){m.position.copy(o);m.quaternion.setFromUnitVectors(new T.Vector3(0,1,0),dir);m.material.color.setHex(col);}
function sm(u){return u*u*(3-2*u);}
function rotAx(ax,rad){var m=new T.Matrix4();return ax==='x'?m.makeRotationX(rad):ax==='y'?m.makeRotationY(rad):m.makeRotationZ(rad);}
function unit(ax){return ax==='x'?new T.Vector3(1,0,0):ax==='y'?new T.Vector3(0,1,0):new T.Vector3(0,0,1);}
function eMats(p){
  var k=Math.min(Math.floor(p+1e-9),2),u=p>=3?1:Math.max(0,p-k),us=sm(u);
  var fo=erev?['z','y','x']:['x','y','z'],fd=erev?[S.Ez,S.Ey,S.Ex]:[S.Ex,S.Ey,S.Ez],eo=['x','y','z'],ed=[S.Ex,S.Ey,S.Ez];
  var F=new T.Matrix4(),E=new T.Matrix4(),i;
  for(i=0;i<k;i++){F=rotAx(fo[i],fd[i]*D).multiply(F);E=E.clone().multiply(rotAx(eo[i],ed[i]*D));}
  var Eaxis=unit(eo[k]).applyMatrix4(E),Faxis=unit(fo[k]);
  var Fp=rotAx(fo[k],fd[k]*D*us).multiply(F),Ep=E.clone().multiply(rotAx(eo[k],ed[k]*D*us));
  return{F:Fp,E:Ep,k:k,fa:fo[k],ea:eo[k],fv:Faxis,ev:Eaxis,fdeg:fd[k]*us,edeg:ed[k]*us,ftot:fd[k],etot:ed[k]};
}
function dispStep(){return ep<=1e-9?0:Math.min(3,Math.ceil(ep-1e-9));}
function eUpdate(){
  var m=eMats(ep),F=m.F,E=m.E,n=dispStep();
  fF.quaternion.setFromRotationMatrix(F);fE.quaternion.setFromRotationMatrix(E);
  setAx(axF,fF.position,m.fv,COL[m.fa]);setAx(axE,fE.position,m.ev,COL[m.ea]);
  var r=F.clone().transpose().multiply(E).elements;
  var ang=Math.acos(Math.max(-1,Math.min(1,(r[0]+r[5]+r[10]-1)/2)))/D;
  var fax=erev?['Z','Y','X']:['X','Y','Z'],eax=['X','Y′','Z″'],fs=erev?FR:FS;
  el('outT').textContent='Fixed angles vs Euler angles';
  el('out').innerHTML='<div class="kv"><span style="color:#0e9aa7;font-weight:600">F · Fixed angles</span><span>'+fs[n]+'</span></div>'+mat(F,3)+
    '<div class="kv"><span style="color:#d9820f;font-weight:600">E · Euler angles</span><span>'+ES[n]+'</span></div>'+mat(E,3)+
    kv('Step '+n+' · Fixed rotates about (world)',n?fax[n-1]:'—')+kv('Step '+n+' · Euler rotates about (moving)',n?eax[n-1]:'—')+
    kv('Angle turned, Fixed / Euler',n?(Math.round(m.fdeg)+'° / '+Math.round(m.edeg)+'°'):'—')+
    kv('Orientation difference F vs E',f(ang)+'°')+
    '<p class="note">'+(n===0?'Both frames start identical.':ang<0.05?'Same orientation at this moment.':'Different orientations: same angles, different order of composition.')+' The colored bar through each frame is the axis it is turning about right now.</p>';
}
function syncSteps(){var cur=anim?anim.to:Math.round(ep);el('ctl').querySelectorAll('[data-step]').forEach(function(b){b.setAttribute('aria-pressed',!anim&&+b.dataset.step===cur);});var pl=el('play');if(pl)pl.textContent=anim?'⏸ Pause':'▶ Play';}
function stopPlay(){anim=null;ep=Math.round(ep);}
function animateTo(to,from){
  var fr=from===undefined?ep:from;
  if(fr===to){anim=null;ep=to;syncSteps();update();return;}
  ep=fr;anim={from:fr,to:to,t0:performance.now(),dur:Math.abs(to-fr)*1900};syncSteps();update();
}
function play(){animateTo(3,0);}
function tickAnim(){
  if(!anim)return;
  var fr=(performance.now()-anim.t0)/anim.dur;
  if(fr>=1){ep=anim.to;anim=null;syncSteps();}else ep=anim.from+(anim.to-anim.from)*fr;
  if(tab==='e')eUpdate();
}
function build(){stopPlay();
  var h=tab==='e'?eCtl():pos('A','Frame A position','fa','#0e9aa7')+rt('A','Frame A rotation (degrees)','fa','#0e9aa7')+(tab==='c'?pos('B','Frame B position','fb','#e8890c')+rt('B','Frame B rotation (degrees)','fb','#e8890c'):'')+(tab==='p'?grp('Point q in the frame',[['qx','X',-4,4,.1,'','x'],['qy','Y',-4,4,.1,'','y'],['qz','Z',-4,4,.1,'','z']]):'');
  el('ctl').innerHTML=h;
  el('ctl').querySelectorAll('input[type=range]').forEach(function(i){i.addEventListener('input',function(){
    S[i.dataset.id]=parseFloat(i.value);el('ctl').querySelector('[data-n="'+i.dataset.id+'"]').value=i.value;update();});});
  el('ctl').querySelectorAll('input[type=number]').forEach(function(n){
    n.addEventListener('input',function(){var v=parseFloat(n.value);if(isNaN(v))return;S[n.dataset.n]=v;
      el('ctl').querySelector('[data-id="'+n.dataset.n+'"]').value=v;update();});
    n.addEventListener('change',function(){var v=parseFloat(n.value);if(isNaN(v))v=0;
      if(n.dataset.ang==='1'){v=((v+180)%360+360)%360-180;}
      S[n.dataset.n]=v;n.value=v;el('ctl').querySelector('[data-id="'+n.dataset.n+'"]').value=v;update();});});
  el('tabNote').textContent=NOTE[tab];
  el('modeBox').style.display=tab==='e'?'none':'';
  el('ctl').querySelectorAll('[data-step]').forEach(function(b){b.onclick=function(){animateTo(+b.dataset.step);};});
  var rv=el('rev');if(rv)rv.onchange=function(){erev=rv.checked;update();};
  var pl=el('play');if(pl)pl.onclick=function(){if(anim){anim=null;syncSteps();update();}else play();};
  el('tabs').querySelectorAll('button').forEach(function(b){b.setAttribute('aria-pressed',b.dataset.t===tab);});
  update();
}
function update(){
  el('modeNote').textContent=world?MN.w:MN.l;
  var MA=M(),MB=M('B'),oA=new T.Vector3().setFromMatrixPosition(MA),oB=new T.Vector3().setFromMatrixPosition(MB),o='';
  MA.decompose(fA.position,fA.quaternion,sc);MB.decompose(fB.position,fB.quaternion,sc);
  fB.visible=tab==='c';fA.userData.badge.visible=tab!=='f';
  var isE=tab==='e';fA.visible=!isE;fF.visible=fE.visible=gF.visible=gE.visible=isE;axF.visible=axE.visible=isE;
  P.visible=lnA.visible=tab==='p';lnO.visible=tab==='p'||tab==='c';
  infoB.sp.visible=tab==='c';infoP.sp.visible=tab==='p';
  updInfo(infoA,'A',oA,'#0e9aa7');infoA.sp.visible=!isE;updStair(stA,S.Ax,S.Ay,S.Az,!isE);
  if(tab==='c'){updInfo(infoB,'B',oB,'#e8890c');}
  updStair(stB,S.Bx,S.By,S.Bz,tab==='c');
  if(isE){eUpdate();return;}
  if(tab==='f'){
    el('outT').textContent='Rotation matrix R';
    o=mat(MA,3)+kv('Position p',vec(oA))+'<p class="note">Each column is the direction of one frame axis in world coordinates.</p>';
  }else if(tab==='c'){
    var r=MA.clone().invert().multiply(MB),e=r.elements,pb=new T.Vector3(e[12],e[13],e[14]);
    var ang=Math.acos(Math.max(-1,Math.min(1,(e[0]+e[5]+e[10]-1)/2)))/D;
    setLn(lnO,oA,oB);
    el('outT').textContent='B relative to A';
    o=mat(r,4)+kv('Position of B in A',vec(pb))+kv('Distance between origins |p|',f(pb.length()))+kv('Relative rotation angle',f(ang)+'°')+'<p class="note">The dashed line joins the origins of A and B.</p>';
  }else{
    var q=new T.Vector3(S.qx,S.qy,S.qz),Pw=q.clone().applyMatrix4(MA);
    P.position.copy(Pw);setLn(lnA,oA,Pw);setLn(lnO,new T.Vector3(),Pw);
    infoP.draw(['P = ('+f(Pw.x)+', '+f(Pw.y)+', '+f(Pw.z)+')'],'#16302f',38,'#f0a020');infoP.sp.position.set(Pw.x,Pw.y,Pw.z+0.6);
    el('outT').textContent='P = T·q';
    o=mat(MA,4)+kv('q in the frame',vec(q))+kv('P in the world',vec(Pw))+
      kv('Distance from frame origin |q|',f(q.length()))+kv('Distance from world origin |P|',f(Pw.length()))+
      '<p class="note">The orange line runs from the frame origin to the point; the dashed line from the world origin. d = √(x² + y² + z²).</p>';
  }
  el('out').innerHTML=o;
}
TABS.forEach(function(t){var b=document.createElement('button');b.textContent=t[1];b.dataset.t=t[0];
  b.onclick=function(){tab=t[0];build();};el('tabs').appendChild(b);});
function setMode(w){world=w;el('mWorld').setAttribute('aria-pressed',w);el('mLocal').setAttribute('aria-pressed',!w);update();}
el('mWorld').onclick=function(){setMode(true);};el('mLocal').onclick=function(){setMode(false);};
el('reset').onclick=function(){S=Object.assign({},DEF);ep=3;anim=null;erev=false;world=true;setMode(true);build();};
resize();place();build();setMode(true);
(function loop(){tickAnim();renderer.render(scene,cam);requestAnimationFrame(loop);})();
})();
</script>
</body>
</html>


