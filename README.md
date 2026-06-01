<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NEET 2027 — Nonu Kumar</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;1,400&family=IBM+Plex+Mono:wght@400;700&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box}

:root{
  --bg:#0b0b0d;
  --surface:#131316;
  --surface2:#18181c;
  --border:#252528;
  --border2:#2e2e33;
  --gold:#c8881a;
  --gold-hi:#e8a83a;
  --text:#ede6d6;
  --text-mid:#7a7468;
  --text-low:#3a3834;
  --radius:6px;
}

body{
  min-height:100vh;
  background:var(--bg);
  color:var(--text);
  font-family:'DM Sans',sans-serif;
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:center;
  padding:3rem 1.5rem;
  overflow-x:hidden;
}

/* ── Grain overlay ── */
body::after{
  content:'';
  position:fixed;inset:0;
  background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.035'/%3E%3C/svg%3E");
  pointer-events:none;z-index:0;
}

.container{position:relative;z-index:1;width:min(860px,100%)}

/* ── Fade-in animation ── */
@keyframes fadeUp{from{opacity:0;transform:translateY(16px)}to{opacity:1;transform:translateY(0)}}
.fade1{animation:fadeUp .7s ease both}
.fade2{animation:fadeUp .7s .15s ease both}
.fade3{animation:fadeUp .7s .3s ease both}
.fade4{animation:fadeUp .7s .45s ease both}
.fade5{animation:fadeUp .7s .6s ease both}

/* ── Header ── */
.header{text-align:center;margin-bottom:3rem}

.eyebrow{
  font-size:10px;letter-spacing:4px;text-transform:uppercase;
  color:var(--gold);font-weight:400;margin-bottom:1.2rem;display:block;
}

h1{
  font-family:'Playfair Display',serif;
  font-size:clamp(3rem,8vw,5.5rem);
  font-weight:400;line-height:.95;
  letter-spacing:-.02em;color:var(--text);
}
h1 em{font-style:italic;color:var(--gold)}

.student{
  font-size:13px;font-weight:400;letter-spacing:3px;
  text-transform:uppercase;color:var(--text-mid);
  margin-top:.9rem;
}

/* ── Divider ── */
.divider{
  width:100%;height:1px;
  background:linear-gradient(90deg,transparent,var(--border2),transparent);
  margin:2.5rem 0;
}

/* ── Main layout ── */
.main{
  display:grid;
  grid-template-columns:260px 1fr;
  gap:3rem;
  align-items:center;
  margin-bottom:2.5rem;
}

/* ── Clock panel ── */
.clock-panel{
  display:flex;flex-direction:column;align-items:center;
  gap:1.1rem;
}

.clock-ring{
  position:relative;width:240px;height:240px;
  border-radius:50%;
  border:1px solid var(--border2);
  background:var(--surface);
  display:flex;align-items:center;justify-content:center;
}

.clock-ring::before{
  content:'';position:absolute;inset:8px;
  border-radius:50%;border:1px solid var(--border);
}

svg.clock-face{width:200px;height:200px}

.digital-block{text-align:center}

.digital-time{
  font-family:'IBM Plex Mono',monospace;
  font-size:1.35rem;font-weight:700;
  color:var(--text);letter-spacing:2px;
  display:block;
}

.digital-date{
  font-size:10.5px;color:var(--text-mid);
  letter-spacing:1.5px;text-transform:uppercase;
  display:block;margin-top:.3rem;
}

/* ── Countdown ── */
.countdown-panel{
  display:flex;flex-direction:column;gap:1.5rem;
}

.cdown-label{
  font-size:10px;letter-spacing:3.5px;
  text-transform:uppercase;color:var(--text-mid);
}

.tiles{
  display:grid;grid-template-columns:repeat(4,1fr);
  gap:3px;
}

.tile{
  background:var(--surface);
  border:1px solid var(--border);
  display:flex;flex-direction:column;
  align-items:center;justify-content:center;
  padding:1.6rem .4rem;
  position:relative;overflow:hidden;
  transition:border-color .3s;
}
.tile:hover{border-color:var(--border2)}

.tile::after{
  content:'';position:absolute;
  top:0;left:0;right:0;height:1px;
  background:linear-gradient(90deg,transparent,var(--gold),transparent);
  opacity:0;transition:opacity .4s;
}
.tile:hover::after{opacity:1}

.tile-num{
  font-family:'IBM Plex Mono',monospace;
  font-size:clamp(1.7rem,3.5vw,2.7rem);
  font-weight:700;color:var(--text);
  line-height:1;transition:color .12s;
}
.tile-num.flash{color:var(--gold-hi)}

.tile-unit{
  font-size:9px;letter-spacing:2.5px;
  text-transform:uppercase;color:var(--text-mid);
  margin-top:.5rem;
}

.exam-note{font-size:12px;color:var(--text-mid);line-height:1.5}
.exam-note strong{color:var(--gold);font-weight:500}

/* ── Progress ── */
.progress-card{
  background:var(--surface);
  border:1px solid var(--border);
  padding:2rem 2.2rem;
  margin-bottom:2.5rem;
}

.prog-top{
  display:flex;justify-content:space-between;
  align-items:baseline;margin-bottom:1.4rem;
}

.prog-label{font-size:10px;letter-spacing:3px;text-transform:uppercase;color:var(--text-mid)}

.prog-pct{
  font-family:'IBM Plex Mono',monospace;
  font-size:2rem;font-weight:700;color:var(--gold);
  line-height:1;
}

.prog-track{height:2px;background:var(--border2);border-radius:1px;position:relative;overflow:visible}

.prog-fill{
  height:100%;border-radius:1px;
  background:linear-gradient(90deg,var(--gold),var(--gold-hi));
  transition:width 2s cubic-bezier(.4,0,.2,1);
  position:relative;
}
.prog-fill::after{
  content:'';position:absolute;
  right:-1px;top:-3px;
  width:8px;height:8px;border-radius:50%;
  background:var(--gold-hi);
  box-shadow:0 0 12px rgba(232,168,58,.6);
}

.prog-ends{
  display:flex;justify-content:space-between;
  margin-top:10px;font-size:10px;
  color:var(--text-low);letter-spacing:.5px;
}

/* ── Weeks strip ── */
.weeks-strip{
  display:flex;gap:8px;align-items:center;
  background:var(--surface2);
  border:1px solid var(--border);
  padding:.7rem 1.2rem;
  border-radius:var(--radius);
  margin-top:1.2rem;
  flex-wrap:wrap;
}
.weeks-strip span{font-size:11px;color:var(--text-mid);letter-spacing:.5px}
.weeks-strip b{color:var(--text);font-weight:500}

/* ── Quote ── */
.quote-section{text-align:center;padding:0 2rem}

.big-mark{
  font-family:'Playfair Display',serif;
  font-size:4rem;line-height:.4;
  color:var(--text-low);display:block;
  margin-bottom:1.2rem;
  user-select:none;
}

.quote-text{
  font-family:'Playfair Display',serif;
  font-style:italic;font-size:1.05rem;
  line-height:1.75;color:var(--text-mid);
  transition:opacity .5s;
  margin-bottom:.6rem;
}

.quote-author{
  font-size:10px;letter-spacing:3px;
  text-transform:uppercase;color:var(--text-low);
  transition:opacity .5s;
}

/* ── Footer ── */
.footer-note{
  font-size:10px;color:var(--text-low);
  letter-spacing:.5px;text-align:center;
  margin-top:2.5rem;
}

/* ── Responsive ── */
@media(max-width:620px){
  .main{grid-template-columns:1fr;gap:2.5rem}
  .clock-panel{order:-1}
  .clock-ring{width:200px;height:200px}
  svg.clock-face{width:160px;height:160px}
  .tiles{grid-template-columns:repeat(2,1fr)}
  .tile{padding:1.3rem .4rem}
  .progress-card{padding:1.5rem}
  .weeks-strip{justify-content:center}
}
</style>
</head>
<body>

<div class="container">

  <!-- Header -->
  <div class="header fade1">
    <span class="eyebrow">National Eligibility cum Entrance Test</span>
    <h1>NEET <em>2027</em></h1>
    <p class="student">Nonu Kumar</p>
  </div>

  <div class="divider fade2"></div>

  <!-- Main: Clock + Countdown -->
  <div class="main fade3">

    <!-- Analog clock -->
    <div class="clock-panel">
      <div class="clock-ring">
        <svg class="clock-face" viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg">

          <!-- minute ticks -->
          <g id="mticks"></g>
          <!-- hour ticks -->
          <g id="hticks"></g>
          <!-- hour numerals -->
          <g id="hnums"
             font-family="'IBM Plex Mono', monospace"
             font-size="10"
             fill="#3a3834"
             text-anchor="middle"
             dominant-baseline="central"></g>

          <!-- hour hand -->
          <line id="hh" x1="100" y1="100" x2="100" y2="60"
                stroke="#ede6d6" stroke-width="3"
                stroke-linecap="round"/>
          <!-- minute hand -->
          <line id="mh" x1="100" y1="100" x2="100" y2="44"
                stroke="#ede6d6" stroke-width="2"
                stroke-linecap="round"/>
          <!-- second hand -->
          <line id="sh" x1="100" y1="112" x2="100" y2="38"
                stroke="#c8881a" stroke-width="1"
                stroke-linecap="round"/>

          <!-- center -->
          <circle cx="100" cy="100" r="4.5" fill="#ede6d6"/>
          <circle cx="100" cy="100" r="1.8" fill="#c8881a"/>
        </svg>
      </div>

      <div class="digital-block">
        <span class="digital-time" id="dtime">--:--:--</span>
        <span class="digital-date" id="ddate">Loading…</span>
      </div>
    </div>

    <!-- Countdown -->
    <div class="countdown-panel">
      <p class="cdown-label">Time remaining until exam day</p>

      <div class="tiles">
        <div class="tile">
          <span class="tile-num" id="cd">000</span>
          <span class="tile-unit">Days</span>
        </div>
        <div class="tile">
          <span class="tile-num" id="ch">00</span>
          <span class="tile-unit">Hours</span>
        </div>
        <div class="tile">
          <span class="tile-num" id="cm">00</span>
          <span class="tile-unit">Mins</span>
        </div>
        <div class="tile">
          <span class="tile-num" id="cs">00</span>
          <span class="tile-unit">Secs</span>
        </div>
      </div>

      <div>
        <p class="exam-note">Exam date: <strong>May 2, 2027</strong> &nbsp;·&nbsp; approx. <strong><span id="wks">—</span> weeks</strong> away</p>
      </div>

      <div class="weeks-strip">
        <span>Preparation window &nbsp;</span>
        <b>Jan 1, 2026 → May 2, 2027</b>
        <span>&nbsp;·&nbsp; <span id="prog-days-left">—</span> days to go</span>
      </div>
    </div>
  </div>

  <!-- Progress bar -->
  <div class="progress-card fade4">
    <div class="prog-top">
      <span class="prog-label">Preparation progress</span>
      <span class="prog-pct" id="ppct">0%</span>
    </div>
    <div class="prog-track">
      <div class="prog-fill" id="pbar" style="width:0%"></div>
    </div>
    <div class="prog-ends">
      <span>Jan 1, 2026 — Start</span>
      <span>May 2, 2027 — NEET</span>
    </div>
  </div>

  <!-- Quote -->
  <div class="quote-section fade5">
    <span class="big-mark">&ldquo;</span>
    <p class="quote-text" id="qt">The secret of getting ahead is getting started.</p>
    <p class="quote-author" id="qa">Mark Twain</p>
  </div>

  <p class="footer-note">Official exam date subject to NTA announcement &nbsp;·&nbsp; All times local</p>

</div>

<script>
/* ── Build clock markers ── */
(function(){
  const cx=100, cy=100, R=90;
  const mG=document.getElementById('mticks');
  const hG=document.getElementById('hticks');
  const nG=document.getElementById('hnums');
  const ns='http://www.w3.org/2000/svg';

  for(let i=0;i<60;i++){
    const a=(i*6-90)*Math.PI/180;
    const isH=i%5===0;
    const r1=R, r2=R-(isH?9:4);
    const x1=cx+r1*Math.cos(a), y1=cy+r1*Math.sin(a);
    const x2=cx+r2*Math.cos(a), y2=cy+r2*Math.sin(a);
    const ln=document.createElementNS(ns,'line');
    ln.setAttribute('x1',x1);ln.setAttribute('y1',y1);
    ln.setAttribute('x2',x2);ln.setAttribute('y2',y2);
    if(isH){
      ln.setAttribute('stroke','#2e2e33');
      ln.setAttribute('stroke-width','2');
      hG.appendChild(ln);
    }else{
      ln.setAttribute('stroke','#222226');
      ln.setAttribute('stroke-width','1');
      mG.appendChild(ln);
    }
  }

  /* Hour numerals */
  const nR=74;
  for(let i=1;i<=12;i++){
    const a=(i*30-90)*Math.PI/180;
    const x=cx+nR*Math.cos(a), y=cy+nR*Math.sin(a);
    const t=document.createElementNS(ns,'text');
    t.setAttribute('x',x);t.setAttribute('y',y);
    t.textContent=i;
    nG.appendChild(t);
  }
})();

/* ── Helpers ── */
const pad=(n,l=2)=>String(n).padStart(l,'0');
const DEG=['Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday'];
const MON=['January','February','March','April','May','June','July','August','September','October','November','December'];

const TARGET=new Date('2027-05-02T08:00:00');

function setRot(id,deg){
  const el=document.getElementById(id);
  el.setAttribute('transform',`rotate(${deg},100,100)`);
}

let prevSec=-1;
function flash(id){
  const el=document.getElementById(id);
  el.classList.add('flash');
  setTimeout(()=>el.classList.remove('flash'),180);
}

/* ── Main tick ── */
function tick(){
  const now=new Date();

  /* Analog clock */
  const hh=now.getHours()%12;
  const mm=now.getMinutes();
  const ss=now.getSeconds();
  const ms=now.getMilliseconds();
  setRot('hh', (hh+mm/60)*30);
  setRot('mh', (mm+ss/60)*6);
  setRot('sh', (ss+ms/1000)*6);

  /* Digital */
  document.getElementById('dtime').textContent=`${pad(now.getHours())}:${pad(mm)}:${pad(ss)}`;
  document.getElementById('ddate').textContent=
    `${DEG[now.getDay()]}, ${now.getDate()} ${MON[now.getMonth()]} ${now.getFullYear()}`;

  /* Countdown */
  const diff=TARGET-now;
  if(diff>0){
    const days =Math.floor(diff/864e5);
    const hours=Math.floor((diff%864e5)/36e5);
    const mins =Math.floor((diff%36e5)/6e4);
    const secs =Math.floor((diff%6e4)/1e3);

    document.getElementById('cd').textContent=pad(days,3);
    document.getElementById('ch').textContent=pad(hours);
    document.getElementById('cm').textContent=pad(mins);
    document.getElementById('cs').textContent=pad(secs);
    document.getElementById('wks').textContent=Math.floor(days/7);
    document.getElementById('prog-days-left').textContent=days.toLocaleString();

    if(secs!==prevSec){flash('cs');prevSec=secs;}
    if(secs===0)flash('cm');
    if(secs===0&&mins===0)flash('ch');

    /* Progress */
    const start=new Date('2026-01-01');
    const pct=Math.max(0,Math.min(100,((now-start)/(TARGET-start))*100));
    document.getElementById('pbar').style.width=pct.toFixed(2)+'%';
    document.getElementById('ppct').textContent=pct.toFixed(1)+'%';
  }
}

tick();
setInterval(tick,50); /* 50ms for smooth hands */

/* ── Quotes ── */
const QS=[
  {t:'The secret of getting ahead is getting started.',a:'Mark Twain'},
  {t:'Hard work beats talent when talent doesn\'t work hard.',a:'Tim Notke'},
  {t:'Believe you can and you\'re halfway there.',a:'Theodore Roosevelt'},
  {t:'Medicine is learned at the bedside, not in the classroom.',a:'Sir William Osler'},
  {t:'Every expert was once a beginner.',a:'Helen Hayes'},
  {t:'Success is the sum of small efforts, repeated day in and day out.',a:'Robert Collier'},
  {t:'The good physician treats the disease; the great physician treats the patient.',a:'Sir William Osler'},
  {t:'In the middle of difficulty lies opportunity.',a:'Albert Einstein'},
  {t:'Dream big. Work hard. Stay focused.',a:'Anonymous'},
];
let qi=0;
const qt=document.getElementById('qt');
const qa=document.getElementById('qa');

setInterval(()=>{
  qt.style.opacity='0';qa.style.opacity='0';
  setTimeout(()=>{
    qi=(qi+1)%QS.length;
    qt.textContent=QS[qi].t;
    qa.textContent=QS[qi].a;
    qt.style.transition=qa.style.transition='opacity .7s';
    qt.style.opacity='1';qa.style.opacity='1';
  },600);
},9000);
</script>

</body>
</html>
