<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<title>Subitize — Plain Dice Trainer</title>
<meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="default">
<link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 80 80'%3E%3Crect rx='16' width='80' height='80' fill='%23000'/%3E%3Ccircle cx='40' cy='40' r='10' fill='%23fff'/%3E%3C/svg%3E">
<style>
:root{
  --bg:#0b0b0c; --fg:#ffffff; --muted:#94a3b8; --accent:#7c3aed;
  --ok:#16a34a; --bad:#ef4444; --panel:#111827; --btn:#1f2937; --btnfg:#e5e7eb;
  --pad:14px; --radius:14px;
}
@media (prefers-color-scheme: light){
  :root{ --bg:#ffffff; --fg:#0b0b0c; --muted:#475569; --panel:#f3f4f6; --btn:#e5e7eb; --btnfg:#111827; }
}
*{ box-sizing:border-box; -webkit-tap-highlight-color: transparent; }
html,body{ height:100%; margin:0; background:var(--bg); color:var(--fg); font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, "Helvetica Neue", Arial; }
.app{ max-width:1000px; margin:0 auto; padding:var(--pad); display:flex; flex-direction:column; gap:var(--pad); }
.header{ display:flex; align-items:center; gap:12px; justify-content:space-between; }
.title{ font-weight:800; letter-spacing:.2px; }
.controls{ display:flex; gap:8px; flex-wrap:wrap; }
button{ background:var(--btn); color:var(--btnfg); border:none; border-radius:12px; padding:12px 14px; font-size:16px; }
button:active{ transform: translateY(1px) scale(.99); }
button[disabled]{ opacity:.5 }
.row{ display:flex; gap:var(--pad); flex-wrap:wrap; }
.panel{ background:var(--panel); border-radius:var(--radius); padding:var(--pad); box-shadow:0 6px 24px rgba(0,0,0,.18); }

.canvasWrap{
  position:relative; width:100%; aspect-ratio:1 / 1; display:flex; align-items:center; justify-content:center;
  flex: 2 1 0; min-width:260px;
}
#stage{ width:100%; height:100%; display:block; background:transparent; border-radius:12px; touch-action:manipulation; }
.feedback{ position:absolute; inset:auto 0 6% 0; text-align:center; font-weight:700; font-size:18px; }
.feedback.ok{ color:var(--ok) } .feedback.bad{ color:var(--bad) }

.side{ flex: 1 1 0; min-width:260px; }
.keypad{ display:grid; grid-template-columns: repeat(6, minmax(0,1fr)); gap:10px; }
.key{ padding:16px; border-radius:12px; background:var(--btn); text-align:center; font-size:18px; }
.key:active{ transform: translateY(1px) scale(.98); }

.small{ font-size:12px; color:var(--muted) }
.flex{ display:flex; gap:10px; flex-wrap:wrap; align-items:center; }
.grow{ flex:1 }
.range{ width:100% }
.statgrid{ display:grid; grid-template-columns: repeat(2, minmax(0,1fr)); gap:10px; }
.kv{ padding:10px; border-radius:10px; background:var(--btn); }
.kv b{ display:block; font-size:13px; color:var(--muted); margin-bottom:8px; }
.kv span{ font-size:18px; font-weight:700; }
.hr{ height:1px; background:rgba(255,255,255,.08); margin:8px 0 }
.disclaimer{ font-size:12px; color:var(--muted) }

@media (max-width: 820px){
  .row{ flex-direction: column; }
  .keypad{ grid-template-columns: repeat(4, minmax(0,1fr)); }
  .statgrid{ grid-template-columns:1fr }
}
</style>
</head>
<body>
<div class="app">
  <div class="header">
    <div class="title">🎲 Subitize — Plain Dice</div>
    <div class="controls">
      <button id="btnPlay">Play ▶</button>
      <button id="btnPractice">Practice</button>
      <button id="btnResults">Results</button>
      <button id="btnSettings">Settings</button>
      <button id="btnInfo">Info</button>
    </div>
  </div>

  <div id="gamePanel" class="panel">
    <div class="row">
      <div class="canvasWrap grow">
        <canvas id="stage" width="900" height="900"></canvas>
        <div id="feedback" class="feedback"></div>
      </div>
      <div class="side grow">
        <div class="kv"><b>Trial</b><span id="trialCounter">—</span></div>
        <div class="kv"><b>Streak</b><span id="streak">0</span></div>
        <div class="kv"><b>Last RT</b><span id="lastRT">—</span></div>
        <div class="hr"></div>
        <div class="keypad" id="keypad"></div>
        <div class="small">Keyboard: 1–9, 0=10, –=11, =/+ =12</div>
      </div>
    </div>
  </div>

  <div id="resultsPanel" class="panel" hidden>
    <div class="row">
      <div class="grow">
        <div class="statgrid">
          <div class="kv"><b>Accuracy</b><span id="accOverall">—</span></div>
          <div class="kv"><b>Median RT</b><span id="rtOverall">—</span></div>
          <div class="kv"><b>Best Streak</b><span id="bestStreak">—</span></div>
          <div class="kv"><b>By Number</b><span id="byNumber">—</span></div>
        </div>
        <div class="hr"></div>
        <div class="flex">
          <button id="btnExport" class="grow">Export CSV</button>
          <button id="btnReset">Reset Data</button>
        </div>
        <div class="disclaimer">Data saves locally in your browser. CSV downloads to Files on iPhone.</div>
      </div>
    </div>
  </div>

  <div id="settingsPanel" class="panel" hidden>
    <div class="row">
      <div class="grow">
        <b>Settings (simple)</b>
        <div class="hr"></div>
        <div class="flex"><span class="grow">Number range</span>
          <label>Min <input id="minN" type="number" value="1" min="1" max="12" style="width:64px"></label>
          <label>Max <input id="maxN" type="number" value="12" min="1" max="12" style="width:64px"></label>
        </div>
        <div class="flex">
          <label class="flex" style="gap:6px"><input type="checkbox" id="chkAudio"> Soft sounds</label>
          <label class="flex" style="gap:6px"><input type="checkbox" id="chkBig"> Big canvas</label>
        </div>
        <div class="small">Play mode keeps dots visible until you answer (we time you). Practice mode shows the answer label.</div>
      </div>
    </div>
  </div>

  <div id="infoPanel" class="panel" hidden>
    <b>Why this subitizing game?</b>
    <div class="hr"></div>
    <div class="small" style="line-height:1.4">
      <p><b>Subitizing</b> is instantly recognizing the number of items without counting. Most people can subitize about 1–4; with practice and good layouts, many recognize higher numbers quickly by chunking familiar patterns.</p>
      <p>This trainer uses <b>canonical, easy-to-recognize dice formations</b> for 1–6 and <b>high-clarity chunked patterns</b> for 7–12 (like 3×3 and 3×4 blocks or a clean 10-frame + 1). The goal is to test and celebrate fast, pattern-based number sense—useful for early numeracy and for people who naturally perceive quantities at a glance.</p>
      <p>Play mode measures reaction time and accuracy while keeping the dots visible so you can focus on recognition rather than racing a hidden timer. Practice mode is gentle and shows the answer label.</p>
    </div>
  </div>
</div>

<script>
/*** =============== Simple Subitizing (1–12, plain dice) =============== */

/* utils */
const $ = s => document.querySelector(s);
const clamp=(v,a,b)=>Math.max(a,Math.min(b,v));
const median = arr => { if(!arr.length) return NaN; const s=[...arr].sort((a,b)=>a-b), m=Math.floor(s.length/2); return s.length%2?s[m]:(s[m-1]+s[m])/2; };
const choice = arr => arr[Math.floor(Math.random()*arr.length)];
const now = () => performance.now();

/* storage */
const VERSION='subitize_plain_v1';
const DB={load(){try{return JSON.parse(localStorage.getItem(VERSION)||'{}')}catch{return{}}}, save(o){localStorage.setItem(VERSION,JSON.stringify(o))}, reset(){localStorage.removeItem(VERSION)}};
let state=Object.assign({
  minN:1, maxN:12, audio:false, big:false,
  trials:[], bestStreak:0
}, DB.load());

/* audio (optional) */
let ctxAudio=null;
function ensureAudio(){ if(!state.audio) return; try{ if(!ctxAudio) ctxAudio=new (window.AudioContext||window.webkitAudioContext)(); }catch{} }
function beep(freq=700,dur=90,type='sine',gain=0.0009){
  if(!state.audio||!ctxAudio) return;
  const o=ctxAudio.createOscillator(), g=ctxAudio.createGain();
  o.type=type; o.frequency.value=freq; g.gain.value=gain;
  o.connect(g); g.connect(ctxAudio.destination); o.start(); setTimeout(()=>o.stop(),dur);
}
const beepOk=()=>beep(700,90,'sine',0.0009);
const beepBad=()=>beep(180,120,'square',0.0012);

/* single plain theme */
const Theme={ bg: getComputedStyle(document.documentElement).getPropertyValue('--bg').trim() || '#0b0b0c',
              fg: getComputedStyle(document.documentElement).getPropertyValue('--fg').trim() || '#ffffff' };

/* canvas / renderer */
const canvas = document.getElementById('stage');
const ctx = canvas.getContext('2d');
let dpr=1, cssW=0, cssH=0, animId=null, animTime=0;

function resizeCanvas(){
  const rect = canvas.getBoundingClientRect();
  dpr = Math.max(1, window.devicePixelRatio||1);
  cssW = rect.width || canvas.clientWidth || 300;
  cssH = rect.height || canvas.clientHeight || 300;
  canvas.width = Math.round(cssW * dpr);
  canvas.height= Math.round(cssH * dpr);
  ctx.setTransform(dpr,0,0,dpr,0,0);
}
window.addEventListener('resize', resizeCanvas, {passive:true});
window.addEventListener('orientationchange', resizeCanvas);

function drawBackground(){
  if(!cssW||!cssH) resizeCanvas();
  ctx.clearRect(0,0,cssW,cssH);
  ctx.fillStyle = Theme.bg;
  ctx.fillRect(0,0,cssW,cssH);
}
function drawPip(x,y,r){
  ctx.save(); ctx.translate(x,y);
  ctx.fillStyle=Theme.fg;
  ctx.beginPath(); ctx.arc(0,0,r,0,Math.PI*2); ctx.fill();
  ctx.restore();
}
function dotRadiusForCount(n,w,h){
  const base = Math.min(w,h)/12;
  if(n<=3) return base*1.0;
  if(n<=6) return base*0.9;
  if(n<=9) return base*0.8;
  if(n<=12) return base*0.75;
  return base*0.7;
}
function drawArray(points){
  drawBackground();
  const n = points.length;
  const r = dotRadiusForCount(n, cssW, cssH);
  const scale = Math.min(cssW, cssH) * (state.big ? 0.48 : 0.44);
  for(const p of points){
    const x = cssW/2 + p.x*scale;
    const y = cssH/2 - p.y*scale;
    drawPip(x,y,r);
  }
}

/* easiest layouts 1–12 (single variant each) */
const Layouts = (function(){
  const L={}, dot=(x,y)=>({x,y});
  // Dice-standard 1–6
  L[1]=[[dot(0,0)]];
  L[2]=[[dot(-.5,-.5), dot(.5,.5)]];
  L[3]=[[dot(-.6,.6), dot(0,0), dot(.6,-.6)]];
  L[4]=[[dot(-.6,.6),dot(.6,.6),dot(-.6,-.6),dot(.6,-.6)]];
  L[5]=[[dot(-.6,.6),dot(.6,.6),dot(0,0),dot(-.6,-.6),dot(.6,-.6)]];
  L[6]=[[dot(-.6,.6),dot(.6,.6),dot(-.6,0),dot(.6,0),dot(-.6,-.6),dot(.6,-.6)]];
  // 7–9: simple chunks (6 + clear addition, 3×3 block)
  L[7]=[ L[6][0].concat([dot(0,0)]) ]; // 6 + center
  L[8]=[[ // two neat rows of 4
    dot(-.6,.5),dot(-.2,.5),dot(.2,.5),dot(.6,.5),
    dot(-.6,-.5),dot(-.2,-.5),dot(.2,-.5),dot(.6,-.5)
  ]];
  L[9]=[[ // 3×3 block
    dot(-.6,.6),dot(0,.6),dot(.6,.6),
    dot(-.6,0),dot(0,0),dot(.6,0),
    dot(-.6,-.6),dot(0,-.6),dot(.6,-.6)
  ]];
  // 10: ten-frame (5×2), 11: ten-frame + one centered below, 12: always 3×4 block
  function tenFrame10(){
    const xs=[-0.8,-0.4,0,0.4,0.8], ys=[0.45,-0.45], arr=[];
    for(let r=0;r<2;r++) for(let c=0;c<5;c++) arr.push(dot(xs[c], ys[r]));
    return arr; // 10
  }
  function grid3x4(){ // 12 as clean 3×4
    const xs=[-0.6,0,0.6], ys=[0.6,0.2,-0.2,-0.6], arr=[];
    for(const y of ys) for(const x of xs) arr.push(dot(x,y)); return arr;
  }
  L[10]=[ tenFrame10() ];
  L[11]=[ tenFrame10().concat([dot(0,-0.95)]) ]; // centered, clearly separate row
  L[12]=[ grid3x4() ];
  return L;
})();

/* game logic */
const Modes={ PLAY:'Play', PRACTICE:'Practice' };
let mode=Modes.PLAY, trialActive=false, targetN=0, tStart=0, streak=0, total=0;

function setMode(m){ mode=m; }
function randN(){
  const min=+$('#minN').value, max=+$('#maxN').value;
  return Math.floor(Math.random()*(max-min+1))+min;
}
function nextArray(n){ return Layouts[n][0]; } // single “easiest” variant only

function startTrial(){
  trialActive=true; targetN=randN();
  const pts = nextArray(targetN);
  drawArray(pts);
  $('#trialCounter').textContent = String(++total);
  $('#lastRT').textContent = '—';
  tStart = now();

  // In Practice, show a faint label
  if(mode===Modes.PRACTICE){
    const fb=$('#feedback'); fb.className='feedback'; fb.textContent=`(${targetN})`;
    fb.style.opacity=.6;
  } else {
    $('#feedback').textContent='';
  }
}
function endTrial(){ trialActive=false; setTimeout(()=>startTrial(), 250); }

function recordTrial(resp, correct, rt){
  state.trials.push({ts:Date.now(), n:targetN, resp, correct, rt});
  state.bestStreak = Math.max(state.bestStreak||0, streak);
  DB.save(state);
}

function handleAnswer(n){
  if(!trialActive) return;
  const rt = Math.round(now()-tStart);
  const ok = (n===targetN);
  if(ok){ streak++; if(state.audio) beepOk(); } else { streak=0; if(state.audio) beepBad(); }
  $('#streak').textContent = String(streak);
  $('#lastRT').textContent = ok ? `${rt} ms` : `× (${targetN})`;
  const fb=$('#feedback'); fb.className='feedback ' + (ok?'ok':'bad'); fb.textContent = ok ? '✓' : `✗ (${targetN})`;
  recordTrial(n, ok, rt);
  endTrial();
}

/* results & csv */
function computeStats(){
  const T=state.trials; if(!T.length) return {acc:'—', rt:'—', best: state.bestStreak||0, by:'—'};
  const acc=(T.filter(t=>t.correct).length/T.length*100).toFixed(1)+'%';
  const rt = Math.round(median(T.filter(t=>t.correct).map(t=>t.rt))) + ' ms';
  const byN={}; for(const t of T){ byN[t.n] ||= {c:0, ok:0, rts:[]}; byN[t.n].c++; if(t.correct){ byN[t.n].ok++; byN[t.n].rts.push(t.rt);} }
  const parts=Object.keys(byN).sort((a,b)=>a-b).map(n=>{
    const s=byN[n], a=((s.ok/s.c)*100)|0, mrt=Math.round(median(s.rts)||NaN);
    return `${n}:${a}%${Number.isFinite(mrt)?`,${mrt}ms`:''}`;
  });
  return {acc, rt, best: state.bestStreak||0, by: parts.join(' • ')||'—'};
}
function renderResults(){
  const s=computeStats();
  $('#accOverall').textContent=s.acc; $('#rtOverall').textContent=s.rt;
  $('#bestStreak').textContent=s.best; $('#byNumber').textContent=s.by;
}
function exportCSV(){
  const rows=[['timestamp','n','response','correct','rt_ms']];
  for(const t of state.trials){ rows.push([t.ts,t.n,t.resp,t.correct?1:0,t.rt]); }
  const csv = rows.map(r=>r.join(',')).join('\n');
  const blob=new Blob([csv],{type:'text/csv;charset=utf-8;'});
  const a=document.createElement('a'); a.href=URL.createObjectURL(blob); a.download='subitize_plain_results.csv';
  document.body.appendChild(a); a.click(); setTimeout(()=>{ URL.revokeObjectURL(a.href); a.remove(); }, 80);
}

/* UI */
function show(id){
  for(const pid of ['gamePanel','resultsPanel','settingsPanel','infoPanel']) document.getElementById(pid).hidden=true;
  document.getElementById(id).hidden=false;
}
function buildKeypad(){
  const kp=$('#keypad'); kp.innerHTML='';
  const max = +$('#maxN').value;
  for(let i=1;i<=max;i++){
    const b=document.createElement('button'); b.className='key'; b.textContent=String(i);
    b.addEventListener('click',()=>handleAnswer(i)); kp.appendChild(b);
  }
}

$('#btnPlay').onclick=()=>{ setMode(Modes.PLAY); show('gamePanel'); startTrial(); };
$('#btnPractice').onclick=()=>{ setMode(Modes.PRACTICE); show('gamePanel'); startTrial(); };
$('#btnResults').onclick=()=>{ renderResults(); show('resultsPanel'); };
$('#btnSettings').onclick=()=>{ show('settingsPanel'); };
$('#btnInfo').onclick=()=>{ show('infoPanel'); };

$('#btnExport').onclick=()=>exportCSV();
$('#btnReset').onclick=()=>{ if(confirm('Reset all saved data?')){ DB.reset(); state.trials=[]; state.bestStreak=0; location.reload(); } };

$('#minN').onchange=$('#maxN').onchange=()=>{ 
  const min=+$('#minN').value, max=+$('#maxN').value;
  $('#minN').value=clamp(min,1,12); $('#maxN').value=clamp(max,1,12);
  buildKeypad();
};
$('#chkAudio').onchange=e=>{ state.audio=e.target.checked; DB.save(state); ensureAudio(); };
$('#chkBig').onchange=e=>{ state.big=e.target.checked; DB.save(state); drawBackground(); };

document.addEventListener('keydown',e=>{
  const map={ '1':1,'2':2,'3':3,'4':4,'5':5,'6':6,'7':7,'8':8,'9':9,'0':10,'-':11,'=':12,'+':12 };
  if(map[e.key]) handleAnswer(map[e.key]);
  if(e.key==='Escape'){ show('settingsPanel'); }
});

/* boot */
function applyStateToUI(){
  $('#minN').value=state.minN; $('#maxN').value=state.maxN;
  $('#chkAudio').checked=state.audio; $('#chkBig').checked=state.big;
  buildKeypad(); drawBackground();
}
animTime=0; resizeCanvas(); applyStateToUI(); show('gamePanel'); startTrial();
</script>
</body>
</html>
