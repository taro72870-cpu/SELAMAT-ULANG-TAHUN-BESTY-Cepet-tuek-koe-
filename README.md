<!doctype html>
<html lang="id">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Selamat Ulang Tahun 🎂</title>
<style>
  :root{
    --bg:#0b1020; --card:#0f1724; --accent:#ffcc00;
    --muted:rgba(255,255,255,0.85);
  }
  *{box-sizing:border-box}
  body{
    min-height:100vh;margin:0;display:flex;align-items:center;justify-content:center;
    font-family:system-ui,Segoe UI,Roboto,Arial; background:
    radial-gradient(circle at 10% 10%, #2b1a4a 0%, transparent 20%),
    linear-gradient(180deg,#07102a 0%, #0b1020 100%);
    color:white;padding:20px;
  }

  .stage{width:980px;max-width:96%;background:linear-gradient(180deg,rgba(255,255,255,0.02), rgba(255,255,255,0.01));
         border-radius:18px;padding:26px;box-shadow:0 12px 40px rgba(2,6,23,.7);position:relative;overflow:hidden}

  header{display:flex;align-items:center;justify-content:space-between;gap:12px}
  h1{font-size:36px;margin:0;letter-spacing:1px}
  h1 .name{display:block;color:var(--accent);font-weight:800;font-size:34px}
  p.lead{margin:6px 0 18px;color:var(--muted);opacity:.95}

  .controls{display:flex;gap:10px;align-items:center}
  button{background:var(--accent);border:0;padding:10px 14px;border-radius:10px;font-weight:700;color:#111;cursor:pointer}
  .btn-secondary{background:transparent;border:1px solid rgba(255,255,255,0.08);color:var(--muted)}
  .small{font-size:13px;padding:8px 10px}

  /* cake area */
  .center{display:flex;gap:28px;align-items:center;justify-content:center;flex-wrap:wrap}
  .cake-wrap{width:430px;max-width:90%;position:relative;padding:20px;display:flex;align-items:center;justify-content:center}
  /* cake layers */
  .cake{
    width:320px;height:220px;position:relative;border-radius:18px;padding-top:10px;
    display:flex;flex-direction:column;align-items:center;justify-content:flex-end;
  }
  .layer{
    width:86%;border-radius:12px;padding:18px 12px;margin:8px 0;box-shadow:0 6px 12px rgba(0,0,0,0.4);
    display:flex;align-items:center;justify-content:center;font-weight:700;color:#111;
  }
  .layer.top{background:linear-gradient(180deg,#ffd4d4,#ffb3b3);height:62px}
  .layer.mid{background:linear-gradient(180deg,#ffd6a8,#ffc48c);height:56px}
  .layer.bot{background:linear-gradient(180deg,#d6f7d9,#aef0b8);height:60px}

  /* frosting drips (decorative) */
  .drips{position:absolute;left:50%;transform:translateX(-50%);top:38px;width:84%;height:44px;pointer-events:none}
  .drip{position:absolute;background:rgba(255,255,255,0.85);border-radius:50% 50% 20% 20%/60% 60% 20% 20%;opacity:.95}

  /* candle */
  .candle-holder{position:absolute;top:10px;left:50%;transform:translateX(-50%);display:flex;gap:18px;z-index:20}
  .candle{width:18px;height:58px;border-radius:6px;display:flex;align-items:flex-start;justify-content:center;position:relative;box-shadow:0 6px 10px rgba(0,0,0,0.45)}
  .candle .wax{width:12px;height:46px;border-radius:6px;margin-top:6px;display:block;position:relative;overflow:visible}
  .stripe{position:absolute;left:2px;width:8px;height:4px;border-radius:2px;opacity:.95}
  /* colors for multiple candles */
  .c1 .wax{background:linear-gradient(180deg,#ffdeeb,#ffb3d2)}
  .c2 .wax{background:linear-gradient(180deg,#ffeec9,#ffd58a)}
  .c3 .wax{background:linear-gradient(180deg,#d9fff0,#9ff0d2)}
  .c4 .wax{background:linear-gradient(180deg,#dbe4ff,#aebcff)}

  /* flame */
  .flame{position:absolute;top:-18px;width:10px;height:20px;border-radius:50% 50% 50% 50%/60% 60% 40% 40%;transform-origin:center bottom;filter:drop-shadow(0 6px 8px rgba(255,160,60,0.25))}
  .inner{position:absolute;inset:2px;border-radius:inherit}
  .flame .core{width:6px;height:10px;background:linear-gradient(180deg,#fff59a,#ffd54a);left:50%;transform:translateX(-50%);top:4px;border-radius:50%}
  .flame .glow{position:absolute;inset:0;background:radial-gradient(circle at 40% 30%, rgba(255,220,110,0.9), rgba(255,120,40,0.06) 50%);border-radius:inherit;opacity:.95}

  /* flicker animation */
  @keyframes flicker {
    0%{transform:translateY(0) scale(1)}
    30%{transform:translateY(-1px) scale(1.03)}
    60%{transform:translateY(1px) scale(0.98)}
    100%{transform:translateY(0) scale(1)}
  }
  .flame{animation:flicker 0.12s infinite ease-in-out}

  /* text reveal */
  .message{margin-top:12px;text-align:center}
  .message p{font-weight:700;margin:6px 0 0;letter-spacing:0.6px}
  .message .wish{font-size:18px;opacity:.95}

  /* confetti */
  canvas.confetti{position:absolute;inset:0;pointer-events:none;z-index:5}

  /* responsive */
  @media (max-width:640px){
    h1{font-size:22px}
    .cake-wrap{width:100%}
  }
</style>
</head>
<body>
  <div class="stage" role="region" aria-label="Selamat Ulang Tahun">
    <canvas class="confetti"></canvas>

    <header>
      <div>
        <h1>SELAMAT ULANG TAHUN<br><span class="name" id="nameLabel">BESTY</span></h1>
        <p class="lead">Semoga sehat, panjang umur, dan semua impian tercapai 🎉</p>
      </div>
      <div class="controls">
        <button id="playBtn">▶️ Putar Lagu</button>
        <button id="stopBtn" class="btn-secondary small">⏹ Stop</button>
        <button id="blowBtn" class="small">🕯️ Tiup Lilin (Animasi)</button>
      </div>
    </header>

    <main class="center" aria-hidden="false">
      <div class="cake-wrap">
        <div class="cake" id="cake">
          <div class="drips" id="drips" aria-hidden="true">
            <div class="drip" style="left:6%;width:24px;height:28px;top:6px"></div>
            <div class="drip" style="left:28%;width:18px;height:22px;top:8px"></div>
            <div class="drip" style="left:54%;width:20px;height:26px;top:7px"></div>
            <div class="drip" style="left:74%;width:26px;height:30px;top:5px"></div>
          </div>

          <div class="candle-holder" id="candles">
            <div class="candle c1">
              <div class="wax"><span class="stripe" style="top:6px;background:rgba(255,255,255,0.5)"></span><span class="stripe" style="top:16px;background:rgba(255,255,255,0.25)"></span></div>
              <div class="flame" data-lit="1">
                <div class="glow" style="background:radial-gradient(circle at 40% 30%, rgba(255,220,110,0.95), rgba(255,120,40,0.06) 50%);border-radius:inherit"></div>
                <div class="core"></div>
              </div>
            </div>

            <div class="candle c2">
              <div class="wax"><span class="stripe" style="top:6px;background:rgba(255,255,255,0.45)"></span></div>
              <div class="flame" data-lit="1"><div class="glow"></div><div class="core"></div></div>
            </div>

            <div class="candle c3">
              <div class="wax"><span class="stripe" style="top:12px;background:rgba(255,255,255,0.5)"></span></div>
              <div class="flame" data-lit="1"><div class="glow"></div><div class="core"></div></div>
            </div>

            <div class="candle c4">
              <div class="wax"></div>
              <div class="flame" data-lit="1"><div class="glow"></div><div class="core"></div></div>
            </div>
          </div>

          <div class="layer top">🎂 Kue Ulang Tahun</div>
          <div class="layer mid">🍓 Lapisan Lezat</div>
          <div class="layer bot">✨ Doa & Harapan</div>
        </div>
      </div>

      <div class="message" style="max-width:380px">
        <p class="wish" id="wishText">Tiup lilinnya dan potong kuenya — selamat ulang tahun!</p>
      </div>
    </main>
  </div>

<script>
/* ===========================
   Nama: ubah di sini jika perlu
   =========================== */
const NAME = "BESTY"; // ganti sesuai nama
document.getElementById('nameLabel').textContent = NAME;

/* ===========================
   WebAudio: synth Happy Birthday melody
   =========================== */
let audioCtx = null;
let isPlaying = false;
let oscGainNodes = [];
let scheduled = [];
const tempo = 100; // BPM-ish for timing

// notes map (in Hz) — use A4 = 440
const noteFreq = (function(){
  const A4 = 440, A4_KEY = 69;
  function midiToFreq(n){ return A4 * Math.pow(2, (n - A4_KEY)/12); }
  // helper from note names
  const names = {"C":0,"C#":1,"D":2,"D#":3,"E":4,"F":5,"F#":6,"G":7,"G#":8,"A":9,"A#":10,"B":11};
  function parse(note){
    if(!note) return null;
    // e.g. G4, C5, (R = rest)
    if(note === "R") return null;
    const m = note.match(/^([A-G]#?)(\d+)$/);
    if(!m) return null;
    const name = m[1], octave = parseInt(m[2],10);
    const keyNumber = (octave + 1) * 12 + names[name];
    return midiToFreq(keyNumber);
  }
  return {parse};
})();

// melody for "Happy Birthday" (simple)
const melody = [
  // note, length (in beats)
  ["G4",1], ["G4",1], ["A4",2], ["G4",2], ["C5",2], ["B4",4],
  ["G4",1], ["G4",1], ["A4",2], ["G4",2], ["D5",2], ["C5",4],
  ["G4",1], ["G4",1], ["G5",2], ["E5",2], ["C5",2], ["B4",2], ["A4",4],
  ["F5",1], ["F5",1], ["E5",2], ["C5",2], ["D5",2], ["C5",4]
];

// Start audio
function ensureAudio(){
  if(!audioCtx){
    audioCtx = new (window.AudioContext || window.webkitAudioContext)();
  }
}

// play single tone using oscillator
function playTone(freq, startTime, duration){
  if(!freq) return;
  const ctx = audioCtx;
  const o = ctx.createOscillator();
  const g = ctx.createGain();
  o.type = 'sine';
  o.frequency.value = freq;
  g.gain.setValueAtTime(0.0001, startTime);
  g.gain.exponentialRampToValueAtTime(0.12, startTime + 0.01);
  g.gain.exponentialRampToValueAtTime(0.0001, startTime + duration - 0.02);
  o.connect(g); g.connect(ctx.destination);
  o.start(startTime);
  o.stop(startTime + duration);
  scheduled.push({osc:o,gain:g});
}

function playMelody(){
  if(isPlaying) return;
  ensureAudio();
  const beatSec = 60 / tempo;
  const now = audioCtx.currentTime + 0.05;
  let t = now;
  for(const [note, len] of melody){
    const f = noteFreq.parse(note);
    const dur = beatSec * len * 0.9;
    if(f){
      playTone(f, t, dur);
    }
    t += beatSec * len;
  }
  isPlaying = true;
  // stop flag after melody ends
  setTimeout(()=>{ isPlaying=false; }, (t - now) * 1000 + 100);
}

/* stop & clear scheduled */
function stopAudio(){
  if(!audioCtx) return;
  // best effort: close context
  try{
    audioCtx.close();
  }catch(e){}
  audioCtx = null;
  isPlaying = false;
}

/* ===========================
   Play/Stop button handlers
   =========================== */
document.getElementById('playBtn').addEventListener('click', ()=>{
  ensureAudio();
  // resume if suspended (some browsers)
  if(audioCtx.state === 'suspended') audioCtx.resume();
  playMelody();
});

document.getElementById('stopBtn').addEventListener('click', ()=>{
  stopAudio();
});

/* try autoplay once (will fail silently on browsers blocking autoplay) */
window.addEventListener('load', ()=>{
  try{
    ensureAudio();
    // attempt short muted resume to gain gesture-less context (may still be blocked)
    if(audioCtx.state === 'suspended' && typeof audioCtx.resume === 'function') audioCtx.resume();
    // auto-play melody (best-effort)
    // setTimeout(playMelody, 600);
  }catch(e){}
});

/* ===========================
   Candle blow: extinguish flames & confetti
   =========================== */
const blowBtn = document.getElementById('blowBtn');
const flames = Array.from(document.querySelectorAll('.flame'));
const wishText = document.getElementById('wishText');
blowBtn.addEventListener('click', ()=>{
  // extinguish
  for(const f of flames){
    f.dataset.lit = "0";
    f.style.opacity = "0";
    f.style.transform = "scale(.2) translateY(-6px)";
  }
  wishText.textContent = `Selamat Ulang Tahun, ${NAME}! 🎉 Potong kuenya dan rayakan!`;
  // small wind sound via oscillator (whoosh)
  ensureAudio();
  if(audioCtx) {
    const o = audioCtx.createOscillator(), g = audioCtx.createGain();
    o.type = 'triangle'; o.frequency.value = 180;
    g.gain.setValueAtTime(0.0001, audioCtx.currentTime);
    g.gain.exponentialRampToValueAtTime(0.08, audioCtx.currentTime + 0.02);
    g.gain.exponentialRampToValueAtTime(0.0001, audioCtx.currentTime + 0.35);
    o.connect(g); g.connect(audioCtx.destination);
    o.start(); o.stop(audioCtx.currentTime + 0.36);
  }
  // burst confetti
  launchConfetti();
});

/* ===========================
   Confetti canvas (simple)
   =========================== */
const confCanvas = document.querySelector('canvas.confetti');
const confCtx = confCanvas.getContext('2d');
let confettiPieces = [];
function resizeCanvas(){
  confCanvas.width = confCanvas.clientWidth * devicePixelRatio;
  confCanvas.height = confCanvas.clientHeight * devicePixelRatio;
  confCtx.scale(devicePixelRatio, devicePixelRatio);
}
window.addEventListener('resize', resizeCanvas);
resizeCanvas();

function rand(min,max){ return Math.random()*(max-min)+min }
function makeConfetti(n=80){
  confettiPieces = [];
  const cols = ['#ff4d6d','#ffd36b','#7afcff','#8e7eff','#ff8ad2','#4dffb1','#fff27a'];
  const W = confCanvas.clientWidth, H = confCanvas.clientHeight;
  for(let i=0;i<n;i++){
    confettiPieces.push({
      x: rand(W*0.2, W*0.8),
      y: rand(0, H*0.2),
      w: rand(6,12),
      h: rand(8,14),
      vx: rand(-3,3),
      vy: rand(1,6),
      rot: rand(0,360),
      vr: rand(-6,6),
      color: cols[Math.floor(rand(0,cols.length))]
    });
  }
}
function drawConfetti(){
  confCtx.clearRect(0,0,confCanvas.clientWidth, confCanvas.clientHeight);
  for(const p of confettiPieces){
    confCtx.save();
    confCtx.translate(p.x, p.y);
    confCtx.rotate(p.rot * Math.PI/180);
    confCtx.fillStyle = p.color;
    confCtx.fillRect(-p.w/2, -p.h/2, p.w, p.h);
    confCtx.restore();
    p.x += p.vx; p.y += p.vy; p.rot += p.vr*0.5;
  }
  confettiPieces = confettiPieces.filter(p=>p.y < confCanvas.clientHeight + 30);
  if(confettiPieces.length) requestAnimationFrame(drawConfetti);
}
function launchConfetti(){
  makeConfetti(140);
  drawConfetti();
}

/* ===========================
   small accessibility: let user change name quickly
   =========================== */
document.getElementById('nameLabel').addEventListener('click', ()=>{
  const newName = prompt("Ganti nama untuk ucapan:", NAME);
  if(newName && newName.trim().length){
    document.getElementById('nameLabel').textContent = newName.trim();
    wishText.textContent = `Tiup lilinnya dan potong kuenya — selamat ulang tahun, ${newName.trim()}!`;
  }
});

/* ===========================
   initial tiny animation: sparkles (optional)
   =========================== */
(function tinySparkles(){
  const cake = document.getElementById('cake');
  cake.animate([{transform:'translateY(0)'},{transform:'translateY(-4px)'},{transform:'translateY(0)'}], {duration:4200,iterations:Infinity,easing:'ease-in-out'});
})();
</script>
</body>
</html>
