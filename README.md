# temperament-assessment
Color Me Understood - Learn your dominant temperament
[color_me_understood_assessment_mixed.index.html](https://github.com/user-attachments/files/22390125/color_me_understood_assessment_mixed.index.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Color Me Understood – 2–3 Minute Temperament Assessment (Mixed Order)</title>
<style>
  :root {
    --red:#D64541;
    --yellow:#F7C844;
    --blue:#3B82F6;
    --green:#22A06B;
    --text:#1f2937;
    --muted:#6b7280;
    --bg:#ffffff;
    --card:#f9fafb;
  }
  *{box-sizing:border-box}
  body{margin:0;font-family:system-ui,-apple-system,Segoe UI,Roboto,Helvetica,Arial; background:var(--bg); color:var(--text);}
  header{padding:16px 16px 8px; text-align:center; background:linear-gradient(180deg,#fff, #f7f7fb)}
  h1{font-size:1.25rem;margin:0 0 6px}
  p{margin:4px 0 0; color:var(--muted); font-size:.95rem}
  .container{max-width:760px;margin:0 auto;padding:16px}
  .card{background:var(--card);border-radius:16px;padding:12px 14px;margin:12px 0; box-shadow:0 1px 2px rgba(0,0,0,.05)}
  .scale{display:flex;gap:6px;margin-top:8px;flex-wrap:wrap}
  .scale label{flex:1 1 calc(25% - 6px);background:#fff;border:1px solid #e5e7eb;padding:10px;border-radius:10px;text-align:center;font-size:.9rem;cursor:pointer}
  .scale input{display:none}
  .scale input:checked + span{font-weight:700}
  .q{font-weight:600;margin-bottom:6px}
  button{appearance:none;border:none;background:#111;color:#fff;border-radius:12px;padding:14px 16px;font-size:1rem;font-weight:700;cursor:pointer}
  .btns{display:flex;gap:10px;flex-wrap:wrap;margin:16px 0}
  .btn-secondary{background:#e5e7eb;color:#111}
  .results{display:none;margin-top:10px}
  .grid{display:grid;grid-template-columns:1fr 1fr; gap:10px}
  @media (max-width:640px){ .grid{grid-template-columns:1fr} }
  .meter{height:12px;border-radius:999px;background:#e5e7eb;overflow:hidden}
  .fill{height:100%}
  .fill.red{background:var(--red)}
  .fill.yellow{background:var(--yellow)}
  .fill.blue{background:var(--blue)}
  .fill.green{background:var(--green)}
  .pill{display:inline-block;padding:4px 10px;border-radius:999px;background:#111;color:#fff;font-size:.85rem;font-weight:700}
  .tip{font-size:.9rem;color:var(--muted)}
  footer{padding:24px;text-align:center;color:var(--muted);font-size:.85rem}
  .small{font-size:.85rem;color:var(--muted)}
  .instructions{font-size:.95rem}
</style>
</head>
<body>
<header>
  <h1>Color Me Understood</h1>
  <p>2–3 Minute Temperament Assessment</p>
  <p class="small">Questions appear in random order each time. No color labels are shown.</p>
</header>

<div class="container">
  <div class="card instructions">
    <p><strong>How to take it:</strong> For each statement, pick what’s true of you <em>most of the time</em>. Scoring happens automatically — you’ll see your <strong>dominant</strong> (primary) and <strong>secondary</strong> results at the end.</p>
    <p class="small">Scale: 0 = Not me · 1 = Sometimes · 2 = Often · 3 = Very true</p>
  </div>

  <form id="form" class="card">
    <div id="questions"></div>
    <div class="btns">
      <button type="button" id="scoreBtn">See My Results</button>
      <button type="reset" class="btn-secondary">Reset</button>
    </div>
  </form>

  <div id="results" class="results card">
    <h2 style="margin:6px 0 10px;font-size:1.15rem;">Your Results</h2>
    <div class="grid">
      <div>
        <div>Yellow (Sanguine): <span id="scoreY" class="pill" style="background:var(--yellow);color:#111">0</span></div>
        <div class="meter"><div id="barY" class="fill yellow" style="width:0%"></div></div>
      </div>
      <div>
        <div>Red (Choleric): <span id="scoreR" class="pill" style="background:var(--red)">0</span></div>
        <div class="meter"><div id="barR" class="fill red" style="width:0%"></div></div>
      </div>
      <div>
        <div>Blue (Melancholic): <span id="scoreB" class="pill" style="background:var(--blue)">0</span></div>
        <div class="meter"><div id="barB" class="fill blue" style="width:0%"></div></div>
      </div>
      <div>
        <div>Green (Phlegmatic): <span id="scoreG" class="pill" style="background:var(--green)">0</span></div>
        <div class="meter"><div id="barG" class="fill green" style="width:0%"></div></div>
      </div>
    </div>

    <div style="margin-top:12px">
      <div id="summary" style="font-weight:700"></div>
      <p class="tip">Tip: Your dominant color is your primary communication style; your secondary color explains your “backup” style. No color is better than another—each has strengths and struggles.</p>
    </div>

    <div class="card" style="margin-top:12px">
      <h3 style="margin:0 0 8px;font-size:1rem">Quick Communication Tips</h3>
      <ul style="margin:0 0 0 18px; padding:0">
        <li><strong>Yellow</strong>: Start with people and possibilities; keep it upbeat and brief.</li>
        <li><strong>Red</strong>: Be direct, bottom-line, and respect their time.</li>
        <li><strong>Blue</strong>: Provide details, rationale, and time to process.</li>
        <li><strong>Green</strong>: Be calm, supportive, and avoid sudden changes.</li>
      </ul>
    </div>
  </div>

  <div class="card">
    <p class="small">Privacy: This tool scores locally in your browser and does not send data anywhere.</p>
  </div>
</div>

<footer>
  © 2025 — Color Me Understood
</footer>

<script>
(function(){
  // Define the question bank with hidden color keys
  const qbank = [
    { id:'q1',  color:'Y', text:'I bring energy and get people talking.' },
    { id:'q2',  color:'Y', text:'I think out loud and brainstorm easily.' },
    { id:'q3',  color:'Y', text:'I’m spontaneous and comfortable meeting new people.' },
    { id:'q4',  color:'Y', text:'I persuade and inspire more than I analyze details.' },
    { id:'q5',  color:'R', text:'I take charge quickly and decide with confidence.' },
    { id:'q6',  color:'R', text:'I’m comfortable with conflict if it helps us move forward.' },
    { id:'q7',  color:'R', text:'I focus on results and efficiency over process.' },
    { id:'q8',  color:'R', text:'I’d rather make a quick call than wait for consensus.' },
    { id:'q9',  color:'B', text:'I value accuracy, quality, and well-thought-out plans.' },
    { id:'q10', color:'B', text:'I prefer clear expectations and time to prepare.' },
    { id:'q11', color:'B', text:'I notice risks and ask careful questions before acting.' },
    { id:'q12', color:'B', text:'I’m thorough and detail-oriented, sometimes to a fault.' },
    { id:'q13', color:'G', text:'I stay calm and steady when others are stressed.' },
    { id:'q14', color:'G', text:'I’m patient, loyal, and people know they can count on me.' },
    { id:'q15', color:'G', text:'I avoid unnecessary conflict and prefer harmony.' },
    { id:'q16', color:'G', text:'I’m consistent and supportive rather than attention-seeking.' }
  ];

  // Fisher–Yates shuffle
  function shuffle(arr){
    for(let i=arr.length-1;i>0;i--){
      const j = Math.floor(Math.random() * (i+1));
      [arr[i],arr[j]] = [arr[j],arr[i]];
    }
    return arr;
  }

  function render(){
    const container = document.getElementById('questions');
    container.innerHTML = '';
    const shuffled = shuffle(qbank.slice());
    shuffled.forEach((q, idx)=>{
      const wrap = document.createElement('div');
      wrap.className = 'qwrap';
      const qEl = document.createElement('div');
      qEl.className = 'q';
      qEl.textContent = (idx+1) + '. ' + q.text;
      wrap.appendChild(qEl);

      const scale = document.createElement('div');
      scale.className = 'scale';
      // name must stay consistent for scoring; use q.id
      for(let v=0; v<=3; v++){
        const label = document.createElement('label');
        const input = document.createElement('input');
        input.type = 'radio';
        input.name = q.id;
        input.value = String(v);
        const span = document.createElement('span');
        span.textContent = String(v);
        label.appendChild(input);
        label.appendChild(span);
        scale.appendChild(label);
      }
      wrap.appendChild(scale);
      container.appendChild(wrap);
    });
  }

  function getVal(name){
    const el = document.querySelector('input[name="'+name+'"]:checked');
    return el ? parseInt(el.value,10) : 0;
  }

  function score(){
    // Sum by color using the qbank as source of truth
    const maxPerColor = 12; // 4 q * 3 max
    const totals = {Y:0,R:0,B:0,G:0};
    qbank.forEach(q=>{
      totals[q.color] += getVal(q.id);
    });
    const pct = s => Math.round((s/maxPerColor)*100);
    // Update UI
    document.getElementById('results').style.display='block';
    document.getElementById('scoreY').textContent = totals.Y;
    document.getElementById('scoreR').textContent = totals.R;
    document.getElementById('scoreB').textContent = totals.B;
    document.getElementById('scoreG').textContent = totals.G;
    document.getElementById('barY').style.width = pct(totals.Y)+'%';
    document.getElementById('barR').style.width = pct(totals.R)+'%';
    document.getElementById('barB').style.width = pct(totals.B)+'%';
    document.getElementById('barG').style.width = pct(totals.G)+'%';
    // Determine dominant and secondary (handle ties)
    const entries = Object.entries(totals).sort((a,b)=>b[1]-a[1]);
    const topVal = entries[0][1];
    const tiedTop = entries.filter(e=>e[1]===topVal).map(e=>e[0]);
    let summary = '';
    const labels = {Y:'Yellow (Sanguine)',R:'Red (Choleric)',B:'Blue (Melancholic)',G:'Green (Phlegmatic)'};
    if(tiedTop.length>1){
      summary = 'You have a tie for dominant: ' + tiedTop.map(c=>labels[c]).join(' & ');
    }else{
      const dominant = labels[entries[0][0]];
      const secondary = labels[entries[1][0]];
      summary = 'Dominant: ' + dominant + ' • Secondary: ' + secondary;
    }
    document.getElementById('summary').textContent = summary;
    window.scrollTo({top:document.body.scrollHeight, behavior:'smooth'});
  }

  document.getElementById('scoreBtn').addEventListener('click', score);
  document.getElementById('form').addEventListener('reset', ()=>{
    setTimeout(()=>{ render(); document.getElementById('results').style.display='none'; },0);
  });

  // Initial render
  render();
})();
</script>
</body>
</html>
