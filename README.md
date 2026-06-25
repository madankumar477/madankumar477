
<style>
  @import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;700&family=Orbitron:wght@400;700;900&display=swap');

  * { margin:0; padding:0; box-sizing:border-box; }

  .root {
    background: #060010;
    color: #e0e0f0;
    font-family: 'JetBrains Mono', monospace;
    min-height: 100vh;
    position: relative;
    overflow: hidden;
  }

  /* Scanlines overlay */
  .root::after {
    content: '';
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(0,0,0,0.08) 2px, rgba(0,0,0,0.08) 4px);
    pointer-events: none;
    z-index: 100;
  }

  /* Grid bg */
  .grid-bg {
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,240,255,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,240,255,0.04) 1px, transparent 1px);
    background-size: 40px 40px;
    z-index: 0;
    pointer-events: none;
  }

  /* Glowing orbs */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(80px);
    pointer-events: none;
    z-index: 0;
  }
  .orb1 { width:320px; height:320px; background:rgba(255,0,180,0.18); top:-80px; left:-60px; }
  .orb2 { width:280px; height:280px; background:rgba(0,200,255,0.15); top:60px; right:-40px; }
  .orb3 { width:200px; height:200px; background:rgba(180,0,255,0.12); bottom:100px; left:30%; }

  .content {
    position: relative;
    z-index: 1;
    max-width: 860px;
    margin: 0 auto;
    padding: 20px 14px 30px;
  }

  /* ── HERO ── */
  .hero {
    border: 1px solid #ff00b444;
    border-radius: 12px;
    background: rgba(255,0,180,0.04);
    padding: 0;
    margin-bottom: 16px;
    overflow: hidden;
    position: relative;
  }
  .hero::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, transparent, #ff00b4, #00f0ff, #ff00b4, transparent);
    animation: shimmer 3s linear infinite;
  }
  @keyframes shimmer { from{background-position:-200% 0} to{background-position:200% 0} }

  .hero-bar {
    background: rgba(0,0,0,0.5);
    padding: 9px 16px;
    display: flex;
    align-items: center;
    gap: 8px;
    border-bottom: 1px solid #ff00b422;
  }
  .dot { width:11px; height:11px; border-radius:50%; }
  .dr { background:#ff3b5c; box-shadow:0 0 6px #ff3b5c; }
  .dy { background:#ffd700; box-shadow:0 0 6px #ffd700; }
  .dg { background:#00ff90; box-shadow:0 0 6px #00ff90; }
  .bar-title { font-size:11px; color:#555580; margin-left:6px; }

  .hero-body { padding: 22px 26px 26px; }

  .prompt-line { font-size:12px; color:#555580; margin-bottom:6px; }
  .prompt-line .p { color:#ff00b4; }
  .prompt-line .cmd { color:#00f0ff; }

  .hero-name {
    font-family: 'Orbitron', sans-serif;
    font-size: 26px;
    font-weight: 900;
    letter-spacing: 2px;
    line-height: 1.1;
    margin: 10px 0 4px;
    background: linear-gradient(90deg, #ff00b4, #00f0ff, #bf00ff);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    filter: drop-shadow(0 0 20px rgba(255,0,180,0.4));
  }

  .hero-handle {
    font-size: 13px;
    color: #555580;
    margin-bottom: 10px;
  }
  .hero-handle span { color: #00f0ff; }

  .hero-role {
    font-size: 13px;
    color: #a0a0c0;
    margin-bottom: 16px;
    line-height: 1.6;
  }
  .hero-role .hl-pink { color: #ff00b4; font-weight: 700; }
  .hero-role .hl-blue { color: #00f0ff; }
  .hero-role .hl-purple { color: #bf00ff; }

  .badge-row { display:flex; flex-wrap:wrap; gap:8px; }
  .badge {
    font-size: 11px;
    padding: 4px 12px;
    border-radius: 20px;
    font-weight: 500;
    position: relative;
    cursor: default;
    transition: all 0.2s;
  }
  .badge:hover { transform: translateY(-2px); }
  .bp { background: rgba(255,0,180,0.1); color: #ff00b4; border: 1px solid #ff00b455; box-shadow: 0 0 8px rgba(255,0,180,0.2); }
  .bb { background: rgba(0,240,255,0.1); color: #00f0ff; border: 1px solid #00f0ff55; box-shadow: 0 0 8px rgba(0,240,255,0.2); }
  .bv { background: rgba(191,0,255,0.1); color: #bf00ff; border: 1px solid #bf00ff55; box-shadow: 0 0 8px rgba(191,0,255,0.2); }

  /* ── SNAKE ── */
  .snake-wrap {
    border: 1px solid #00f0ff33;
    border-radius: 12px;
    overflow: hidden;
    margin-bottom: 16px;
    position: relative;
  }
  .snake-header {
    background: rgba(0,0,0,0.6);
    border-bottom: 1px solid #00f0ff22;
    padding: 8px 14px;
    font-size: 11px;
    color: #555580;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .snake-header .live {
    width: 7px; height: 7px; border-radius: 50%;
    background: #ff00b4;
    box-shadow: 0 0 8px #ff00b4;
    animation: blink 1.2s infinite;
  }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0.2} }
  .snake-header span { color: #ff00b4; }
  canvas#snk {
    display: block; width: 100%; height: 110px;
    background: #060010;
  }

  /* ── LIVE STATUS ── */
  .live-card {
    border: 1px solid #ff00b444;
    border-radius: 10px;
    background: rgba(255,0,180,0.05);
    padding: 13px 18px;
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 14px;
    position: relative;
    overflow: hidden;
  }
  .live-card::before {
    content: '';
    position: absolute;
    left: 0; top: 0; bottom: 0;
    width: 3px;
    background: linear-gradient(180deg, #ff00b4, #bf00ff);
    box-shadow: 0 0 12px #ff00b4;
  }
  .pulse-ring {
    width: 12px; height: 12px;
    border-radius: 50%;
    background: #ff00b4;
    flex-shrink: 0;
    box-shadow: 0 0 0 0 rgba(255,0,180,0.6);
    animation: sonar 1.8s infinite;
  }
  @keyframes sonar {
    0% { box-shadow: 0 0 0 0 rgba(255,0,180,0.6); }
    70% { box-shadow: 0 0 0 12px rgba(255,0,180,0); }
    100% { box-shadow: 0 0 0 0 rgba(255,0,180,0); }
  }
  .live-text { font-size: 12px; color: #9090b0; line-height: 1.6; }
  .live-text .lp { color: #ff00b4; font-weight: 700; }
  .live-text .lb { color: #00f0ff; }
  .live-text .lv { color: #bf00ff; }

  /* ── STATS ── */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 12px;
    margin-bottom: 16px;
  }
  .stat {
    border-radius: 10px;
    padding: 14px 14px;
    text-align: center;
    position: relative;
    overflow: hidden;
    border: 1px solid transparent;
  }
  .stat.sp { background: rgba(255,0,180,0.07); border-color: #ff00b433; }
  .stat.sb { background: rgba(0,240,255,0.07); border-color: #00f0ff33; }
  .stat.sv { background: rgba(191,0,255,0.07); border-color: #bf00ff33; }
  .stat.sg { background: rgba(0,255,144,0.07); border-color: #00ff9033; }

  .stat-num {
    font-family: 'Orbitron', sans-serif;
    font-size: 22px;
    font-weight: 900;
  }
  .stat.sp .stat-num { color: #ff00b4; text-shadow: 0 0 12px rgba(255,0,180,0.6); }
  .stat.sb .stat-num { color: #00f0ff; text-shadow: 0 0 12px rgba(0,240,255,0.6); }
  .stat.sv .stat-num { color: #bf00ff; text-shadow: 0 0 12px rgba(191,0,255,0.6); }
  .stat.sg .stat-num { color: #00ff90; text-shadow: 0 0 12px rgba(0,255,144,0.6); }

  .stat-lbl { font-size: 10px; color: #555580; margin-top: 4px; text-transform: uppercase; letter-spacing: 0.06em; }

  /* ── SKILLS ── */
  .skills-box {
    border: 1px solid #00f0ff22;
    border-radius: 10px;
    background: rgba(0,0,20,0.5);
    padding: 16px 18px;
    margin-bottom: 16px;
  }
  .sec-title {
    font-size: 11px;
    color: #00f0ff;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-bottom: 14px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .sec-title::after { content:''; flex:1; height:1px; background: linear-gradient(90deg, #00f0ff33, transparent); }

  .skrow { margin-bottom: 11px; }
  .skinfo { display:flex; justify-content:space-between; margin-bottom:5px; }
  .skname { font-size: 12px; color: #c0c0e0; }
  .skpct { font-size: 11px; }
  .skpct.cp { color: #ff00b4; }
  .skpct.cb { color: #00f0ff; }
  .skpct.cv { color: #bf00ff; }
  .skpct.cg { color: #00ff90; }

  .skbar { height: 5px; background: #111130; border-radius: 3px; overflow: hidden; }
  .skfill { height: 100%; border-radius: 3px; transition: width 1.6s cubic-bezier(0.4,0,0.2,1); width: 0%; position: relative; }
  .skfill::after {
    content: '';
    position: absolute;
    right: 0; top: 0; bottom: 0;
    width: 20px;
    background: rgba(255,255,255,0.4);
    filter: blur(4px);
  }
  .fp { background: linear-gradient(90deg, #bf00ff, #ff00b4); }
  .fb { background: linear-gradient(90deg, #0040ff, #00f0ff); }
  .fv { background: linear-gradient(90deg, #ff00b4, #bf00ff); }
  .fg { background: linear-gradient(90deg, #00f0ff, #00ff90); }
  .fo { background: linear-gradient(90deg, #00ff90, #00f0ff); }

  /* ── PROJECTS ── */
  .proj-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
    margin-bottom: 16px;
  }
  .pcard {
    border-radius: 10px;
    padding: 14px 16px;
    border: 1px solid #222250;
    background: rgba(0,0,20,0.5);
    transition: all 0.25s;
    position: relative;
    overflow: hidden;
    cursor: default;
  }
  .pcard::before {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0; height: 2px;
    opacity: 0;
    transition: opacity 0.25s;
  }
  .pcard:hover { border-color: #ff00b466; transform: translateY(-2px); box-shadow: 0 8px 30px rgba(255,0,180,0.12); }
  .pcard:hover::before { opacity: 1; background: linear-gradient(90deg, #ff00b4, #00f0ff); }

  .pcard.wip { border-color: #00f0ff44; }
  .pcard.wip:hover { border-color: #00f0ff88; box-shadow: 0 8px 30px rgba(0,240,255,0.12); }

  .pname { font-size: 13px; color: #00f0ff; font-weight: 700; margin-bottom: 6px; }
  .pname .wip-tag { font-size: 10px; color: #ffd700; background: rgba(255,215,0,0.12); border: 1px solid #ffd70044; padding: 1px 7px; border-radius: 20px; margin-left: 8px; }
  .pdesc { font-size: 11px; color: #6060a0; line-height: 1.55; margin-bottom: 10px; }
  .ptags { display:flex; flex-wrap:wrap; gap:5px; }
  .ptag { font-size: 10px; padding: 2px 8px; border-radius: 20px; background: rgba(255,0,180,0.08); color: #ff00b4; border: 1px solid #ff00b433; }
  .ptag.bt { background: rgba(0,240,255,0.08); color: #00f0ff; border-color: #00f0ff33; }
  .ptag.vt { background: rgba(191,0,255,0.08); color: #bf00ff; border-color: #bf00ff33; }

  /* ── FOOTER ── */
  .footer {
    text-align: center;
    font-size: 11px;
    color: #333360;
    padding-top: 6px;
  }
  .footer .fp { color: #ff00b466; }
  .footer .fb { color: #00f0ff66; }

  @media (max-width: 520px) {
    .stats-grid { grid-template-columns: repeat(2,1fr); }
    .proj-grid { grid-template-columns: 1fr; }
    .hero-name { font-size: 20px; }
  }
</style>

<div class="root">
  <div class="grid-bg"></div>
  <div class="orb orb1"></div>
  <div class="orb orb2"></div>
  <div class="orb orb3"></div>

  <div class="content">

    <!-- HERO -->
    <div class="hero">
      <div class="hero-bar">
        <div class="dot dr"></div><div class="dot dy"></div><div class="dot dg"></div>
        <span class="bar-title">~/madankumar477 — cyberdeck v2.0</span>
      </div>
      <div class="hero-body">
        <div class="prompt-line"><span class="p">▶</span> <span class="cmd">init profile --user=madankumar477</span></div>
        <div class="hero-name">E MADAN KUMAR</div>
        <div class="hero-handle">@madankumar477 <span>// github.com/madankumar477</span></div>
        <div class="hero-role">
          <span class="hl-pink">Robotics &amp; AI Engineer</span> · B.E. DSCE Bengaluru<br>
          <span class="hl-blue">Intern</span> @ <span class="hl-purple">ATI Motors</span> — New Product Initiative (NPI)<br>
          Building machines that <span class="hl-pink">see</span>, <span class="hl-blue">think</span>, and <span class="hl-purple">move</span>.
        </div>
        <div class="badge-row">
          <span class="badge bp">⚡ ROS2 Humble</span>
          <span class="badge bb">🤖 Python</span>
          <span class="badge bv">👁️ OpenCV</span>
          <span class="badge bp">🦾 Dobot API</span>
          <span class="badge bb">📡 Arduino</span>
          <span class="badge bv">🔧 Embedded</span>
        </div>
      </div>
    </div>

    <!-- SNAKE -->
    <div class="snake-wrap">
      <div class="snake-header">
        <div class="live"></div>
        <span>contribution_snake.exe</span> — eating the grid live
      </div>
      <canvas id="snk" width="860" height="110"></canvas>
    </div>

    <!-- LIVE STATUS -->
    <div class="live-card">
      <div class="pulse-ring"></div>
      <div class="live-text">
        <span class="lp">[ ONLINE ]</span> Currently interning at <span class="lb">ATI Motors</span> as <span class="lv">New Product Initiative (NPI)</span> engineer ·
        Parallel: building autonomous <span class="lp">mobile manipulator</span> with ROS2 (sim → real-world deployment)
      </div>
    </div>

    <!-- STATS -->
    <div class="stats-grid">
      <div class="stat sp">
        <div class="stat-num">05</div>
        <div class="stat-lbl">Projects</div>
      </div>
      <div class="stat sb">
        <div class="stat-num">12+</div>
        <div class="stat-lbl">Tech Stack</div>
      </div>
      <div class="stat sv">
        <div class="stat-num">06</div>
        <div class="stat-lbl">Certs</div>
      </div>
      <div class="stat sg">
        <div class="stat-num">3+</div>
        <div class="stat-lbl">Industries</div>
      </div>
    </div>

    <!-- SKILLS -->
    <div class="skills-box">
      <div class="sec-title">// skill_matrix</div>
      <div class="skrow">
        <div class="skinfo"><span class="skname">Python &amp; ROS2 (Humble)</span><span class="skpct cp">85%</span></div>
        <div class="skbar"><div class="skfill fp" id="s1"></div></div>
      </div>
      <div class="skrow">
        <div class="skinfo"><span class="skname">OpenCV / Computer Vision</span><span class="skpct cb">80%</span></div>
        <div class="skbar"><div class="skfill fb" id="s2"></div></div>
      </div>
      <div class="skrow">
        <div class="skinfo"><span class="skname">Arduino / Embedded (MPU6050)</span><span class="skpct cv">75%</span></div>
        <div class="skbar"><div class="skfill fv" id="s3"></div></div>
      </div>
      <div class="skrow">
        <div class="skinfo"><span class="skname">Gazebo / RViz / Simulation</span><span class="skpct cg">70%</span></div>
        <div class="skbar"><div class="skfill fg" id="s4"></div></div>
      </div>
      <div class="skrow">
        <div class="skinfo"><span class="skname">Linux / Git / C++ basics</span><span class="skpct cb">65%</span></div>
        <div class="skbar"><div class="skfill fo" id="s5"></div></div>
      </div>
    </div>

    <!-- PROJECTS -->
    <div class="sec-title" style="font-size:11px;color:#ff00b4;letter-spacing:.1em;text-transform:uppercase;margin-bottom:12px;display:flex;align-items:center;gap:10px;">
      // featured_projects
      <span style="flex:1;height:1px;background:linear-gradient(90deg,#ff00b433,transparent);display:block"></span>
    </div>
    <div class="proj-grid">
      <div class="pcard">
        <div class="pname">👁️ Gesture-Arm Control</div>
        <div class="pdesc">Vision-based robotic arm control mapping hand landmarks to robot coordinates for pick-and-place tasks.</div>
        <div class="ptags">
          <span class="ptag">Python</span><span class="ptag bt">OpenCV</span><span class="ptag vt">Dobot API</span>
        </div>
      </div>
      <div class="pcard">
        <div class="pname">🤝 Twin Robot Mirror</div>
        <div class="pdesc">ROS2 leader-follower system with real-time pose sharing and synchronized motion replication.</div>
        <div class="ptags">
          <span class="ptag bt">ROS2</span><span class="ptag">Python</span><span class="ptag vt">Dobot API</span>
        </div>
      </div>
      <div class="pcard">
        <div class="pname">♿ Gesture Wheelchair</div>
        <div class="pdesc">IMU-based wheelchair controller using real-time hand tilt gestures via MPU6050 sensor.</div>
        <div class="ptags">
          <span class="ptag bt">Arduino</span><span class="ptag">MPU6050</span><span class="ptag vt">L293</span>
        </div>
      </div>
      <div class="pcard wip">
        <div class="pname">🚀 Mobile Manipulator <span class="wip-tag">WIP</span></div>
        <div class="pdesc">Autonomous nav + manipulation — ROS2 localization, planning &amp; control. Sim → real deployment.</div>
        <div class="ptags">
          <span class="ptag bt">ROS2</span><span class="ptag bt">Nav Stack</span><span class="ptag">Python</span>
        </div>
      </div>
    </div>

    <div class="footer">
      <span class="fp">▲</span> built in Bengaluru, India · open to robotics &amp; automation roles <span class="fb">▲</span>
    </div>
  </div>
</div>

<script>
(function(){
  const canvas = document.getElementById('snk');
  const ctx = canvas.getContext('2d');
  const W = canvas.width, H = canvas.height;
  const CELL = 11;
  const COLS = Math.floor(W/CELL), ROWS = Math.floor(H/CELL);

  // Build contribution-style grid
  let grid = [];
  for(let r=0;r<ROWS;r++){
    for(let c=0;c<COLS;c++){
      let v = Math.random();
      let lvl = v<0.08?4 : v<0.2?3 : v<0.38?2 : v<0.55?1 : 0;
      grid.push({r,c,lvl,eaten:false});
    }
  }

  function cellColor(lvl, eaten){
    if(eaten) return '#060010';
    const cols = ['#0d0a1a','#1a0040','#4a0080','#9000cc','#cc00ff'];
    return cols[lvl] || cols[0];
  }

  // Snake
  let hc = 3, hr = Math.floor(ROWS/2);
  let body = [];
  for(let i=0;i<8;i++) body.unshift({c:hc-i,r:hr});
  let dir = {dc:1,dr:0};
  let target = null;

  function findTarget(){
    let candidates = grid.filter(g=>g.lvl>0&&!g.eaten);
    // prefer nearby
    let nearby = candidates.filter(g=>Math.abs(g.c-hc)<50&&Math.abs(g.r-hr)<5);
    let pool = nearby.length ? nearby : candidates;
    return pool.length ? pool[Math.floor(Math.random()*Math.min(pool.length,8))] : null;
  }

  function steer(){
    if(!target||target.eaten) target = findTarget();
    if(!target) return;
    let dc = target.c-hc, dr = target.r-hr;
    if(Math.abs(dc)>=Math.abs(dr)) dir={dc:dc>0?1:-1,dr:0};
    else dir={dc:0,dr:dr>0?1:-1};
  }

  let tick=0;
  function step(){
    tick++;
    if(tick%3===0) steer();
    let nc=hc+dir.dc, nr=hr+dir.dr;
    if(nc<0)nc=COLS-1; if(nc>=COLS)nc=0;
    if(nr<0)nr=ROWS-1; if(nr>=ROWS)nr=0;
    hc=nc; hr=nr;
    body.unshift({c:hc,r:hr});
    if(body.length>20) body.pop();
    let cell=grid.find(g=>g.c===hc&&g.r===hr);
    if(cell&&cell.lvl>0&&!cell.eaten) cell.eaten=true;
  }

  function draw(){
    ctx.fillStyle='#060010';
    ctx.fillRect(0,0,W,H);

    // grid cells
    for(let cell of grid){
      let x=cell.c*CELL+2, y=cell.r*CELL+2;
      ctx.fillStyle=cellColor(cell.lvl,cell.eaten);
      ctx.beginPath();
      ctx.roundRect(x,y,CELL-3,CELL-3,2);
      ctx.fill();
      if(!cell.eaten&&cell.lvl>2){
        ctx.strokeStyle='rgba(200,0,255,0.2)';
        ctx.lineWidth=0.5;
        ctx.stroke();
      }
    }

    // snake body
    for(let i=body.length-1;i>=0;i--){
      let seg=body[i];
      let x=seg.c*CELL+1, y=seg.r*CELL+1;
      let t=1-i/body.length;
      if(i===0){
        ctx.fillStyle='#ff00b4';
        ctx.shadowColor='#ff00b4';
        ctx.shadowBlur=12;
      } else {
        let r=Math.round(255*t);
        let b=Math.round(255*(1-t*0.5));
        ctx.fillStyle=`rgba(${r},0,${b},${0.2+t*0.75})`;
        ctx.shadowBlur=0;
      }
      ctx.beginPath();
      ctx.roundRect(x,y,CELL-1,CELL-1,3);
      ctx.fill();
      ctx.shadowBlur=0;
    }

    // eyes on head
    ctx.fillStyle='#fff';
    let hx=hc*CELL+1, hy=hr*CELL+1;
    let ex1=hx+3, ey1=hy+3;
    let ex2=hx+3, ey2=hy+7;
    if(dir.dc>0){ex1=hx+8;ey1=hy+3;ex2=hx+8;ey2=hy+7;}
    if(dir.dr>0){ex1=hx+3;ey1=hy+8;ex2=hx+7;ey2=hy+8;}
    if(dir.dr<0){ex1=hx+3;ey1=hy+2;ex2=hx+7;ey2=hy+2;}
    ctx.beginPath();ctx.arc(ex1,ey1,1.5,0,Math.PI*2);ctx.fill();
    ctx.beginPath();ctx.arc(ex2,ey2,1.5,0,Math.PI*2);ctx.fill();

    // glowing trail at head
    ctx.beginPath();
    ctx.arc(hc*CELL+CELL/2,hr*CELL+CELL/2,CELL*0.8,0,Math.PI*2);
    ctx.fillStyle='rgba(255,0,180,0.06)';
    ctx.fill();
  }

  let last=0;
  function loop(ts){
    if(ts-last>75){step();draw();last=ts;}
    requestAnimationFrame(loop);
  }
  draw();
  requestAnimationFrame(loop);

  // skill bars
  setTimeout(()=>{
    const data=[['s1','85%'],['s2','80%'],['s3','75%'],['s4','70%'],['s5','65%']];
    data.forEach(([id,w])=>{
      const el=document.getElementById(id);
      if(el)el.style.width=w;
    });
  },400);
})();
</script>
