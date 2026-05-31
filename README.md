<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NEET 2027 Countdown</title>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500&family=Space+Mono:wght@700&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box}

body{
  min-height:100vh;
  background:#f7f5f2;
  color:#1a1a1a;
  font-family:'Inter',sans-serif;
  display:flex;flex-direction:column;
  align-items:center;justify-content:center;
  padding:2rem;
}

/* top label */
.eyebrow{
  font-size:11px;letter-spacing:3px;text-transform:uppercase;
  color:#999;margin-bottom:1.2rem;
  font-weight:400;
}

/* main title */
h1{
  font-size:clamp(2.4rem,6vw,4rem);
  font-weight:300;letter-spacing:-.03em;
  color:#1a1a1a;line-height:1;
  margin-bottom:.35rem;
}
h1 strong{font-weight:500}

.student{
  font-size:18px;font-weight:500;letter-spacing:-.01em;
  color:#1a1a1a;margin-bottom:.4rem;
}
.date-label{
  font-size:13px;color:#aaa;
  margin-bottom:3.5rem;
  letter-spacing:.3px;
}

/* countdown */
.grid{
  display:flex;gap:2px;
  margin-bottom:3.5rem;
}
.cell{
  display:flex;flex-direction:column;align-items:center;
  padding:2rem 2.5rem;
  background:#fff;
  gap:.6rem;
  min-width:110px;
}
.cell:first-child{border-radius:8px 0 0 8px}
.cell:last-child{border-radius:0 8px 8px 0}

.num{
  font-family:'Space Mono',monospace;
  font-size:clamp(2rem,5vw,3.2rem);
  font-weight:700;
  color:#1a1a1a;
  line-height:1;
  transition:color .1s;
}
.num.flash{color:#c9952a}

.unit{
  font-size:10px;letter-spacing:2px;
  text-transform:uppercase;color:#bbb;
  font-weight:400;
}

/* progress */
.prog-section{
  width:min(480px,90vw);
  margin-bottom:3.5rem;
}
.prog-head{
  display:flex;justify-content:space-between;align-items:baseline;
  margin-bottom:10px;
}
.prog-title{font-size:12px;color:#aaa;letter-spacing:.5px}
.prog-pct{font-size:13px;color:#1a1a1a;font-weight:500}

.track{height:3px;background:#ebebeb;border-radius:2px;overflow:hidden}
.fill{
  height:100%;border-radius:2px;
  background:#1a1a1a;
  transition:width 2s cubic-bezier(.4,0,.2,1);
}

/* quote */
.quote-wrap{
  max-width:420px;text-align:center;
}
.quote{
  font-size:15px;line-height:1.7;
  color:#666;font-weight:300;
  font-style:italic;
  margin-bottom:.5rem;
  transition:opacity .5s;
}
.author{
  font-size:11px;letter-spacing:1.5px;
  text-transform:uppercase;color:#bbb;
  transition:opacity .5s;
}

/* note */
.note{
  position:fixed;bottom:1.2rem;
  font-size:10.5px;color:#ccc;
  letter-spacing:.3px;
}

@media(max-width:500px){
  .cell{padding:1.4rem 1.2rem;min-width:0;flex:1}
  .grid{width:100%}
}
</style>
</head>
<body>

<p class="eyebrow">National Eligibility cum Entrance Test</p>

<h1>NEET <strong>2027</strong></h1>
<p class="student">Nonu Kumar</p>
<p class="date-label">May 2, 2027 &nbsp;·&nbsp; <span id="weeks">—</span> weeks to go</p>

<div class="grid">
  <div class="cell">
    <span class="num" id="d">000</span>
    <span class="unit">Days</span>
  </div>
  <div class="cell">
    <span class="num" id="h">00</span>
    <span class="unit">Hours</span>
  </div>
  <div class="cell">
    <span class="num" id="m">00</span>
    <span class="unit">Mins</span>
  </div>
  <div class="cell">
    <span class="num" id="s">00</span>
    <span class="unit">Secs</span>
  </div>
</div>

<div class="prog-section">
  <div class="prog-head">
    <span class="prog-title">Preparation — Jan 2026 to May 2027</span>
    <span class="prog-pct" id="pct">0%</span>
  </div>
  <div class="track"><div class="fill" id="bar" style="width:0%"></div></div>
</div>

<div class="quote-wrap">
  <p class="quote" id="qt">"The secret of getting ahead is getting started."</p>
  <p class="author" id="qa">Mark Twain</p>
</div>

<p class="note">Date is approximate — official date subject to NTA announcement.</p>

<script>
const target = new Date('2027-05-02T08:00:00');
const pad = (n,l=2) => String(n).padStart(l,'0');

function flash(id){
  const el = document.getElementById(id);
  el.classList.add('flash');
  setTimeout(()=>el.classList.remove('flash'), 180);
}

let prevSec = -1;
function tick(){
  const now = new Date(), diff = target - now;
  if(diff <= 0) return;
  const days  = Math.floor(diff/864e5);
  const hours = Math.floor((diff%864e5)/36e5);
  const mins  = Math.floor((diff%36e5)/6e4);
  const secs  = Math.floor((diff%6e4)/1e3);

  document.getElementById('d').textContent = pad(days,3);
  document.getElementById('h').textContent = pad(hours);
  document.getElementById('m').textContent = pad(mins);
  document.getElementById('s').textContent = pad(secs);
  document.getElementById('weeks').textContent = Math.floor(days/7);

  if(secs !== prevSec){ flash('s'); prevSec = secs; }
  if(secs===0) flash('m');
  if(secs===0 && mins===0) flash('h');

  const start = new Date('2026-01-01');
  const pct = Math.max(0, Math.min(100, ((now-start)/(target-start))*100));
  document.getElementById('bar').style.width = pct.toFixed(1)+'%';
  document.getElementById('pct').textContent = pct.toFixed(0)+'%';
}

tick(); setInterval(tick, 1000);

const QS = [
  {t:'"The secret of getting ahead is getting started."', a:'Mark Twain'},
  {t:'"Hard work beats talent when talent doesn\'t work hard."', a:'Tim Notke'},
  {t:'"Believe you can and you\'re halfway there."', a:'Theodore Roosevelt'},
  {t:'"Medicine is learned at the bedside, not in the classroom."', a:'Sir William Osler'},
  {t:'"Every expert was once a beginner."', a:'Helen Hayes'},
  {t:'"Success is the sum of small efforts, repeated day in and day out."', a:'Robert Collier'},
  {t:'"Dream big. Work hard. Stay focused."', a:'Anonymous'},
];
let qi = 0;
const qt = document.getElementById('qt'), qa = document.getElementById('qa');
setInterval(()=>{
  qt.style.opacity='0'; qa.style.opacity='0';
  setTimeout(()=>{
    qi = (qi+1)%QS.length;
    qt.textContent = QS[qi].t;
    qa.textContent = QS[qi].a;
    qt.style.transition = qa.style.transition = 'opacity .7s';
    qt.style.opacity = '1'; qa.style.opacity = '1';
  }, 500);
}, 8000);
</script>
</body>
</html>
