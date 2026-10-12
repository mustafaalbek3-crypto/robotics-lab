<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>مختبر الفريمات XYZ</title>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Arabic:wght@400;600&display=swap" rel="stylesheet">
<style>
:root{--bg:#eef2f1;--panel:#fff;--ink:#16302f;--mute:#5d7573;--line:#cddad8;--x:#e03b3b;--y:#2f9e4f;--z:#2f6fe0;--acc:#16302f;--or:#d9820f;
box-sizing:border-box}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#10211f;--panel:#182d2b;--ink:#e6f0ee;--mute:#92aeab;--line:#2c4744;--acc:#e6f0ee;--or:#f0a020}}
:root[data-theme="dark"]{--bg:#10211f;--panel:#182d2b;--ink:#e6f0ee;--mute:#92aeab;--line:#2c4744;--acc:#e6f0ee;--or:#f0a020}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font:400 15px/1.7 "IBM Plex Sans Arabic",system-ui,sans-serif}
.app{display:grid;grid-template-columns:1fr;gap:12px;padding:12px;padding-top:calc(12px + env(safe-area-inset-top,0px));padding-bottom:calc(12px + env(safe-area-inset-bottom,0px));max-width:1400px;margin:0 auto}
#side{min-width:0}
#view{position:relative;order:-1;height:50vh;min-height:290px;border-radius:14px;background:var(--panel);border:1px solid var(--line);overflow:hidden}
@media (min-width:900px){
 .app{grid-template-columns:380px 1fr;align-items:start}
 #view{order:0;position:sticky;top:12px;height:calc(100vh - 24px)}
 #side{max-height:calc(100vh - 24px);overflow-y:auto;padding-inline-end:4px}
}
canvas{width:100%;height:100%;display:block;touch-action:none}
#hint{position:absolute;inset-inline:0;bottom:6px;text-align:center;font-size:12px;color:var(--mute);pointer-events:none}
h1{font-size:19px;margin:0 0 8px}
.seg{display:flex;gap:6px;margin:8px 0}
.seg button{flex:1;padding:8px 4px;border:1px solid var(--line);background:var(--panel);color:var(--ink);border-radius:10px;font:inherit;font-size:13px}
.seg button[aria-pressed="true"]{background:var(--acc);color:var(--bg);border-color:var(--acc)}
.note{font-size:13px;color:var(--mute);margin:0 0 10px}
fieldset{border:1px solid var(--line);background:var(--panel);border-radius:14px;margin:0 0 10px;padding:6px 12px 10px}
legend{font-weight:600;padding:0 6px}
fieldset.fa{border-inline-start:5px solid #0e9aa7}fieldset.fb{border-inline-start:5px solid #e8890c}
.guide{background:var(--panel);border:1px solid var(--line);border-radius:12px;padding:6px 12px;margin:0 0 10px;font-size:13px}.guide summary{font-weight:600;cursor:pointer}.guide ol{margin:6px 0 2px;padding-inline-start:18px}.sw{display:inline-block;width:12px;height:12px;border-radius:50%;margin-inline-end:6px;vertical-align:middle}
.row{display:grid;grid-template-columns:28px 1fr 56px;align-items:center;gap:8px;margin-top:4px}
.row b{font-size:16px;text-align:center}
.row output{direction:ltr;text-align:left;font-variant-numeric:tabular-nums;font-size:13px}
input[type=range]{width:100%;direction:ltr;height:30px}
.rx{accent-color:var(--x)}.ry{accent-color:var(--y)}.rz{accent-color:var(--z)}
.cx{color:var(--x)}.cy{color:var(--y)}.cz{color:var(--z)}
.mat{direction:ltr;display:grid;gap:4px;max-width:340px;margin:8px auto;text-align:center;font-variant-numeric:tabular-nums}
.mat span{padding:5px 0;border-radius:8px;background:var(--bg);font-size:14px}
.m3 span:nth-child(3n+1),.m4 span:nth-child(4n+1){color:var(--x)}
.m3 span:nth-child(3n+2),.m4 span:nth-child(4n+2){color:var(--y)}
.m3 span:nth-child(3n),.m4 span:nth-child(4n+3){color:var(--z)}
.m4 span:nth-child(4n){color:var(--or)}
.kv{display:flex;justify-content:space-between;gap:8px;margin:4px 0;font-size:14px}
.kv b{direction:ltr;font-variant-numeric:tabular-nums;font-weight:600}
.reset{width:100%;padding:10px;border-radius:10px;border:1px solid var(--line);background:var(--panel);color:var(--ink);font:inherit}
button:focus-visible,input:focus-visible{outline:2px solid var(--z);outline-offset:2px}
</style>
</head>
<body>
<div class="app">
<aside id="side">
<h1>مختبر الفريمات XYZ</h1>
<p class="note" style="margin-bottom:6px">Robotics I · المحاضرة 2: الوصف المكاني (Spatial Description)</p>
<details class="guide" open><summary>ماذا تجرّب؟</summary><ol>
<li>تبويب «فريم»: حرّك الفريم وأدره، وراقب مصفوفة R. كل عمود فيها هو اتجاه أحد محاور الفريم.</li>
<li>بدّل بين «حول محاور العالم» و«حول محاور الفريم» بنفس الزوايا، ولاحظ أن النتيجة تختلف.</li>
<li>تبويب «مقارنة A و B»: انظر T = A⁻¹·B وموقع B كما يراه A.</li>
<li>تبويب «نقطة»: النقطة q ثابتة داخل الفريم، وP تتحرك في العالم.</li></ol></details>
<div class="seg" id="tabs" role="group" aria-label="الأقسام"></div>
<p class="note" id="tabNote"></p>
<div class="seg" id="modeSeg" role="group" aria-label="نوع الدوران">
<button id="mWorld" aria-pressed="true">حول محاور العالم</button>
<button id="mLocal" aria-pressed="false">حول محاور الفريم</button>
</div>
<p class="note" id="modeNote"></p>
<div id="ctl"></div>
<fieldset><legend id="outT">النتائج</legend><div id="out" aria-live="polite"></div></fieldset>
<button class="reset" id="reset">إعادة الضبط</button>
</aside>
<div id="view"><canvas id="c"></canvas><div id="hint">اسحب للتدوير، وبإصبعين أو بالعجلة للتقريب</div></div>
</div>
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script>
(function(){
var COL={x:0xe03b3b,y:0x2f9e4f,z:0x2f6fe0},T=THREE;
var cv=document.getElementById('c'),view=document.getElementById('view');
var renderer=new T.WebGLRenderer({canvas:cv,antialias:true,alpha:true});
renderer.setPixelRatio(Math.min(devicePixelRatio||1,2));
var scene=new T.Scene(),cam=new T.PerspectiveCamera(45,1,0.1,100);cam.up.set(0,0,1);
scene.add(new T.AmbientLight(0xffffff,0.7));
var dl=new T.DirectionalLight(0xffffff,0.6);dl.position.set(3,-4,6);scene.add(dl);
var grid=new T.GridHelper(8,8,0x8aa3a0,0x8aa3a0);grid.rotation.x=Math.PI/2;
grid.material.transparent=true;grid.material.opacity=0.25;scene.add(grid);

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
    var co=new T.Mesh(new T.ConeGeometry(th*2.4,len*0.22,20),m);co.position.y=len*1.11;
    var lb=label(a[0].toUpperCase(),COL[a[0]],0.5);lb.position.y=len*1.45;lb.material.opacity=op;
    arm.add(cy,co,lb);arm.rotation.set(a[1],a[2],a[3]);g.add(arm);
  });
  g.add(new T.Mesh(new T.SphereGeometry(th*2.2,20,20),new T.MeshStandardMaterial({color:hc||0x888888,transparent:op<1,opacity:op})));
  if(bt){var rg=new T.Mesh(new T.RingGeometry(len*0.42,len*0.5,48),new T.MeshBasicMaterial({color:hc,transparent:true,opacity:.55,side:T.DoubleSide,depthWrite:false}));g.add(rg);
    var b=badge(bt,hc,0.8);b.position.set(-0.45,-0.45,0.45);g.add(b);g.userData.badge=b;}
  return g;
}
scene.add(frame(2,0.04,0.28));
var CA=0x0e9aa7,CB=0xe8890c;
var fA=frame(1.5,0.07,1,CA,'A'),fB=frame(1.5,0.07,1,CB,'B');scene.add(fA,fB);
var P=new T.Mesh(new T.SphereGeometry(0.12,20,20),new T.MeshStandardMaterial({color:0xf0a020}));scene.add(P);
function mkLine(c,dash){var g=new T.BufferGeometry();g.setAttribute('position',new T.BufferAttribute(new Float32Array(6),3));
  var l=new T.Line(g,dash?new T.LineDashedMaterial({color:c,dashSize:.15,gapSize:.1}):new T.LineBasicMaterial({color:c}));l.frustumCulled=false;scene.add(l);return l;}
var lnA=mkLine(0xf0a020,false),lnO=mkLine(0x8aa3a0,true);
function setLn(l,a,b){var p=l.geometry.attributes.position.array;p.set([a.x,a.y,a.z,b.x,b.y,b.z]);l.geometry.attributes.position.needsUpdate=true;l.computeLineDistances();}

var th=0.9,ph=1.1,rad=9;
function place(){cam.position.set(rad*Math.sin(ph)*Math.cos(th),rad*Math.sin(ph)*Math.sin(th),rad*Math.cos(ph));cam.lookAt(0,0,0.5);}
var pts={},last=0;
cv.addEventListener('pointerdown',function(e){cv.setPointerCapture(e.pointerId);pts[e.pointerId]=[e.clientX,e.clientY];});
cv.addEventListener('pointerup',function(e){delete pts[e.pointerId];last=0;});
cv.addEventListener('pointermove',function(e){
  var p=pts[e.pointerId];if(!p)return;var ids=Object.keys(pts);
  if(ids.length===1){th-=(e.clientX-p[0])*0.01;ph=Math.min(3,Math.max(0.2,ph-(e.clientY-p[1])*0.01));}
  pts[e.pointerId]=[e.clientX,e.clientY];
  if(ids.length===2){var a=pts[ids[0]],b=pts[ids[1]],d=Math.hypot(a[0]-b[0],a[1]-b[1]);if(last)rad=Math.min(18,Math.max(4,rad*last/d));last=d;}
  place();
});
cv.addEventListener('wheel',function(e){e.preventDefault();rad=Math.min(18,Math.max(4,rad*(1+e.deltaY*0.001)));place();},{passive:false});
function resize(){var w=view.clientWidth,h=view.clientHeight;renderer.setSize(w,h,false);cam.aspect=w/h;cam.updateProjectionMatrix();}
addEventListener('resize',resize);

function el(i){return document.getElementById(i);}
function f(n){return (Math.abs(n)<0.005?0:n).toFixed(2);}
function vec(v){return '('+f(v.x)+', '+f(v.y)+', '+f(v.z)+')';}
function kv(a,b){return '<div class="kv"><span>'+a+'</span><b>'+b+'</b></div>';}
function mat(m,n){var e=m.elements,h='<div class="mat m'+n+'" style="grid-template-columns:repeat('+n+',1fr)">';
  for(var r=0;r<n;r++)for(var c=0;c<n;c++)h+='<span>'+f(e[c*4+r])+'</span>';return h+'</div>';}

var DEF={Ax:0,Ay:0,Az:0,Arx:0,Ary:0,Arz:0,Bx:2,By:1,Bz:0.5,Brx:0,Bry:0,Brz:40,qx:1,qy:0.5,qz:0.5};
var S=Object.assign({},DEF),tab='f',world=true,D=Math.PI/180;
var TABS=[['f','فريم'],['c','مقارنة A و B'],['p','نقطة مع الفريم']];
var NOTE={
 f:'حرّك الفريم وأدره، وراقب مصفوفة الدوران.',
 c:'T = A⁻¹·B تصف الفريم B كما يراه A. العمود الأخير هو موقع B في إحداثيات A، والجزء 3×3 هو الدوران النسبي. الفريم A بحلقة فيروزية والفريم B بحلقة برتقالية.',
 p:'النقطة q معرّفة داخل الفريم، وموقعها في العالم P = T·q. حرّك الفريم وانظر كيف تتحرك P بينما q ثابتة. المسافة من أصل الفريم |q| لا تتغير.'};
var MN={w:'الترتيب: دوران حول X ثم Y ثم Z الثابتة: R = Rz·Ry·Rx.',l:'الدوران حول محاور الفريم المتحركة: R = Rx·Ry·Rz (كمفاصل الروبوت).'};
function rot(a,b,c){
  var X=new T.Matrix4().makeRotationX(a*D),Y=new T.Matrix4().makeRotationY(b*D),Z=new T.Matrix4().makeRotationZ(c*D);
  return world?Z.multiply(Y).multiply(X):X.multiply(Y).multiply(Z);
}
function M(p){p=p||'A';return new T.Matrix4().makeTranslation(S[p+'x'],S[p+'y'],S[p+'z']).multiply(rot(S[p+'rx'],S[p+'ry'],S[p+'rz']));}
var sc=new T.Vector3();
function row(s){
  return '<div class="row"><b class="c'+s[6]+'">'+s[1]+'</b><input class="r'+s[6]+'" type="range" data-id="'+s[0]+'" min="'+s[2]+'" max="'+s[3]+'" step="'+s[4]+'" value="'+S[s[0]]+'" aria-label="'+s[1]+'"><output>'+(s[5]?S[s[0]]+'°':(+S[s[0]]).toFixed(1))+'</output></div>';
}
function grp(t,l,cls,col){return '<fieldset class="'+(cls||'')+'"><legend>'+(col?'<i class="sw" style="background:'+col+'"></i>':'')+t+'</legend>'+l.map(row).join('')+'</fieldset>';}
function pos(p,t,c,col){return grp(t,[[p+'x','X',-3,3,.1,'','x'],[p+'y','Y',-3,3,.1,'','y'],[p+'z','Z',-3,3,.1,'','z']],c,col);}
function rt(p,t,c,col){return grp(t,[[p+'rx','X',-180,180,1,'°','x'],[p+'ry','Y',-180,180,1,'°','y'],[p+'rz','Z',-180,180,1,'°','z']],c,col);}
function build(){
  var h=pos('A','إزاحة الفريم A','fa','#0e9aa7')+rt('A','دوران الفريم A','fa','#0e9aa7')+(tab==='c'?pos('B','إزاحة الفريم B','fb','#e8890c')+rt('B','دوران الفريم B','fb','#e8890c'):'')+(tab==='p'?grp('النقطة q داخل الفريم',[['qx','X',-3,3,.1,'','x'],['qy','Y',-3,3,.1,'','y'],['qz','Z',-3,3,.1,'','z']]):'');
  el('ctl').innerHTML=h;
  el('ctl').querySelectorAll('input').forEach(function(i){i.addEventListener('input',function(){
    S[i.dataset.id]=parseFloat(i.value);var o=i.nextElementSibling;o.textContent=o.textContent.indexOf('°')>-1?i.value+'°':(+i.value).toFixed(1);update();});});
  el('tabNote').textContent=NOTE[tab];
  el('tabs').querySelectorAll('button').forEach(function(b){b.setAttribute('aria-pressed',b.dataset.t===tab);});
  update();
}
function update(){
  el('modeNote').textContent=world?MN.w:MN.l;
  var MA=M(),oA=new T.Vector3().setFromMatrixPosition(MA),o='';
  MA.decompose(fA.position,fA.quaternion,sc);
  var MB=M('B');MB.decompose(fB.position,fB.quaternion,sc);
  fB.visible=tab==='c';fA.userData.badge.visible=tab!=='f';
  P.visible=lnA.visible=tab==='p';lnO.visible=tab==='p'||tab==='c';
  if(tab==='f'){
    el('outT').textContent='مصفوفة الدوران R';
    o=mat(MA,3)+kv('الموقع p',vec(oA))+'<p class="note">كل عمود هو اتجاه أحد محاور الفريم في إحداثيات العالم.</p>';
  }else if(tab==='c'){
    var oB=new T.Vector3().setFromMatrixPosition(MB),r=MA.clone().invert().multiply(MB),e=r.elements,pb=new T.Vector3(e[12],e[13],e[14]);
    var ang=Math.acos(Math.max(-1,Math.min(1,(e[0]+e[5]+e[10]-1)/2)))/D;
    setLn(lnO,oA,oB);
    el('outT').textContent='B بالنسبة إلى A';
    o=mat(r,4)+kv('موقع B في A',vec(pb))+kv('المسافة بين الأصلين |p|',f(pb.length()))+kv('زاوية الدوران النسبي',f(ang)+'°')+'<p class="note">الخط المتقطع يصل بين أصلي A وB.</p>';
  }else{
    var q=new T.Vector3(S.qx,S.qy,S.qz),Pw=q.clone().applyMatrix4(MA);
    P.position.copy(Pw);setLn(lnA,oA,Pw);setLn(lnO,new T.Vector3(),Pw);
    el('outT').textContent='P = T·q';
    o=mat(MA,4)+kv('q داخل الفريم',vec(q))+kv('P في العالم',vec(Pw))+
      kv('المسافة من أصل الفريم |q|',f(q.length()))+kv('المسافة من أصل العالم |P|',f(Pw.length()))+
      '<p class="note">الخط البرتقالي من أصل الفريم إلى النقطة، والمتقطع من أصل العالم. d = √(x² + y² + z²).</p>';
  }
  el('out').innerHTML=o;
}
TABS.forEach(function(t){var b=document.createElement('button');b.textContent=t[1];b.dataset.t=t[0];
  b.onclick=function(){tab=t[0];build();};el('tabs').appendChild(b);});
function setMode(w){world=w;el('mWorld').setAttribute('aria-pressed',w);el('mLocal').setAttribute('aria-pressed',!w);update();}
el('mWorld').onclick=function(){setMode(true);};el('mLocal').onclick=function(){setMode(false);};
el('reset').onclick=function(){S=Object.assign({},DEF);world=true;setMode(true);build();};
resize();place();build();setMode(true);
(function loop(){renderer.render(scene,cam);requestAnimationFrame(loop);})();
})();
</script>
</body>
</html>
