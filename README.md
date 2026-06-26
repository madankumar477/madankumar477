<svg viewBox="0 0 860 620" xmlns="http://www.w3.org/2000/svg" width="860" height="620">
  <defs>
    <!-- Fonts via foreignObject trick — SVG uses system monospace fallback -->

    <!-- Background grid pattern -->
    <pattern id="grid" width="40" height="40" patternUnits="userSpaceOnUse">
      <path d="M 40 0 L 0 0 0 40" fill="none" stroke="rgba(0,240,255,0.04)" stroke-width="1"/>
    </pattern>

    <!-- Shimmer gradient animation -->
    <linearGradient id="shimmer" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" stop-color="transparent"/>
      <stop offset="40%" stop-color="#ff00b4"/>
      <stop offset="60%" stop-color="#00f0ff"/>
      <stop offset="100%" stop-color="transparent"/>
      <animateTransform attributeName="gradientTransform" type="translate" from="-1 0" to="1 0" dur="3s" repeatCount="indefinite"/>
    </linearGradient>

    <!-- Name gradient -->
    <linearGradient id="nameGrad" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" stop-color="#ff00b4"/>
      <stop offset="50%" stop-color="#00f0ff"/>
      <stop offset="100%" stop-color="#bf00ff"/>
    </linearGradient>

    <!-- Skill bar gradients -->
    <linearGradient id="sk1" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" stop-color="#bf00ff"/><stop offset="100%" stop-color="#ff00b4"/>
    </linearGradient>
    <linearGradient id="sk2" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" stop-color="#0040ff"/><stop offset="100%" stop-color="#00f0ff"/>
    </linearGradient>
    <linearGradient id="sk3" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" stop-color="#ff00b4"/><stop offset="100%" stop-color="#bf00ff"/>
    </linearGradient>
    <linearGradient id="sk4" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" stop-color="#00f0ff"/><stop offset="100%" stop-color="#00ff90"/>
    </linearGradient>
    <linearGradient id="sk5" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" stop-color="#00ff90"/><stop offset="100%" stop-color="#00f0ff"/>
    </linearGradient>

    <!-- Orb blur filters -->
    <filter id="blur80">
      <feGaussianBlur stdDeviation="40"/>
    </filter>
    <filter id="glow">
      <feGaussianBlur stdDeviation="3" result="blur"/>
      <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>

    <!-- Snake segment gradient -->
    <linearGradient id="snakeGrad" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" stop-color="rgba(191,0,255,0.3)"/>
      <stop offset="100%" stop-color="#ff00b4"/>
    </linearGradient>

    <style>
      @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0.2} }
      @keyframes sonar {
        0%   { r: 6; opacity: 0.8; }
        70%  { r: 14; opacity: 0; }
        100% { r: 6; opacity: 0; }
      }
      @keyframes barGrow1 { from{width:0} to{width:663} }
      @keyframes barGrow2 { from{width:0} to{width:624} }
      @keyframes barGrow3 { from{width:0} to{width:585} }
      @keyframes barGrow4 { from{width:0} to{width:546} }
      @keyframes barGrow5 { from{width:0} to{width:507} }
      @keyframes snakeMove {
        0%   { transform: translateX(0); }
        100% { transform: translateX(780px); }
      }
      @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.6} }
      @keyframes shimmerBar {
        0%   { x: -30; opacity:0; }
        50%  { opacity:0.5; }
        100% { x: 820; opacity:0; }
      }

      .live-dot { animation: blink 1.2s infinite; }
      .sonar-ring { animation: sonar 1.8s infinite; }
      .bar1 { animation: barGrow1 1.6s cubic-bezier(0.4,0,0.2,1) 0.4s both; }
      .bar2 { animation: barGrow2 1.6s cubic-bezier(0.4,0,0.2,1) 0.55s both; }
      .bar3 { animation: barGrow3 1.6s cubic-bezier(0.4,0,0.2,1) 0.7s both; }
      .bar4 { animation: barGrow4 1.6s cubic-bezier(0.4,0,0.2,1) 0.85s both; }
      .bar5 { animation: barGrow5 1.6s cubic-bezier(0.4,0,0.2,1) 1.0s both; }
    </style>
  </defs>

  <!-- ── BG ── -->
  <rect width="860" height="620" fill="#060010"/>
  <rect width="860" height="620" fill="url(#grid)"/>

  <!-- Orbs -->
  <circle cx="-20" cy="-30" r="160" fill="rgba(255,0,180,0.18)" filter="url(#blur80)"/>
  <circle cx="900" cy="80"  r="140" fill="rgba(0,200,255,0.15)"  filter="url(#blur80)"/>
  <circle cx="400" cy="540" r="100" fill="rgba(180,0,255,0.12)"  filter="url(#blur80)"/>

  <!-- Scanlines (subtle) -->
  <rect width="860" height="620" fill="url(#scanlines)" opacity="0.04"/>

  <!-- ══════════════════════════════════════════════ -->
  <!-- HERO CARD -->
  <!-- ══════════════════════════════════════════════ -->
  <rect x="10" y="10" width="840" height="178" rx="12" fill="rgba(255,0,180,0.04)" stroke="#ff00b444" stroke-width="1"/>
  <!-- shimmer top border -->
  <rect x="10" y="10" width="840" height="2" rx="1" fill="url(#shimmer)"/>

  <!-- title bar -->
  <rect x="10" y="10" width="840" height="32" rx="12" fill="rgba(0,0,0,0.5)"/>
  <rect x="10" y="30" width="840" height="12" fill="rgba(0,0,0,0.5)"/>
  <rect x="10" y="10" width="840" height="32" fill="none" stroke="#ff00b422" stroke-width="0" />
  <line x1="10" y1="42" x2="850" y2="42" stroke="#ff00b422" stroke-width="1"/>
  <!-- dots -->
  <circle cx="30" cy="26" r="5.5" fill="#ff3b5c" filter="url(#glow)"/>
  <circle cx="48" cy="26" r="5.5" fill="#ffd700" filter="url(#glow)"/>
  <circle cx="66" cy="26" r="5.5" fill="#00ff90" filter="url(#glow)"/>
  <text x="82" y="30" font-family="monospace" font-size="11" fill="#555580">~/madankumar477 — cyberdeck v2.0</text>

  <!-- prompt -->
  <text x="36" y="68" font-family="monospace" font-size="12" fill="#ff00b4">▶</text>
  <text x="50" y="68" font-family="monospace" font-size="12" fill="#00f0ff">init profile --user=madankumar477</text>

  <!-- name -->
  <text x="36" y="100" font-family="monospace" font-size="26" font-weight="900" letter-spacing="2" fill="url(#nameGrad)" filter="url(#glow)">E MADAN KUMAR</text>

  <!-- handle -->
  <text x="36" y="120" font-family="monospace" font-size="13" fill="#555580">@madankumar477 <tspan fill="#00f0ff">// github.com/madankumar477</tspan></text>

  <!-- role lines -->
  <text x="36" y="140" font-family="monospace" font-size="13">
    <tspan fill="#ff00b4" font-weight="700">Robotics &amp; AI Engineer</tspan>
    <tspan fill="#a0a0c0"> · B.E. DSCE Bengaluru</tspan>
  </text>
  <text x="36" y="157" font-family="monospace" font-size="13">
    <tspan fill="#00f0ff">Intern</tspan>
    <tspan fill="#a0a0c0"> @ </tspan>
    <tspan fill="#bf00ff">ATI Motors</tspan>
    <tspan fill="#a0a0c0"> — New Product Initiative (NPI)</tspan>
  </text>
  <text x="36" y="174" font-family="monospace" font-size="13" fill="#a0a0c0">Building machines that <tspan fill="#ff00b4">see</tspan>, <tspan fill="#00f0ff">think</tspan>, and <tspan fill="#bf00ff">move</tspan>.</text>

  <!-- badges -->
  <!-- badge 1 -->
  <rect x="36" y="184" width="98" height="20" rx="10" fill="rgba(255,0,180,0.1)" stroke="#ff00b455" stroke-width="1"/>
  <text x="85" y="198" font-family="monospace" font-size="11" fill="#ff00b4" text-anchor="middle">⚡ ROS2 Humble</text>
  <!-- badge 2 -->
  <rect x="142" y="184" width="76" height="20" rx="10" fill="rgba(0,240,255,0.1)" stroke="#00f0ff55" stroke-width="1"/>
  <text x="180" y="198" font-family="monospace" font-size="11" fill="#00f0ff" text-anchor="middle">🤖 Python</text>
  <!-- badge 3 -->
  <rect x="226" y="184" width="76" height="20" rx="10" fill="rgba(191,0,255,0.1)" stroke="#bf00ff55" stroke-width="1"/>
  <text x="264" y="198" font-family="monospace" font-size="11" fill="#bf00ff" text-anchor="middle">👁️ OpenCV</text>
  <!-- badge 4 -->
  <rect x="310" y="184" width="84" height="20" rx="10" fill="rgba(255,0,180,0.1)" stroke="#ff00b455" stroke-width="1"/>
  <text x="352" y="198" font-family="monospace" font-size="11" fill="#ff00b4" text-anchor="middle">🦾 Dobot API</text>
  <!-- badge 5 -->
  <rect x="402" y="184" width="78" height="20" rx="10" fill="rgba(0,240,255,0.1)" stroke="#00f0ff55" stroke-width="1"/>
  <text x="441" y="198" font-family="monospace" font-size="11" fill="#00f0ff" text-anchor="middle">📡 Arduino</text>
  <!-- badge 6 -->
  <rect x="488" y="184" width="82" height="20" rx="10" fill="rgba(191,0,255,0.1)" stroke="#bf00ff55" stroke-width="1"/>
  <text x="529" y="198" font-family="monospace" font-size="11" fill="#bf00ff" text-anchor="middle">🔧 Embedded</text>

  <!-- ══════════════════════════════════════════════ -->
  <!-- SNAKE SECTION -->
  <!-- ══════════════════════════════════════════════ -->
  <rect x="10" y="210" width="840" height="128" rx="12" fill="#060010" stroke="#00f0ff33" stroke-width="1"/>
  <!-- snake header -->
  <rect x="10" y="210" width="840" height="28" rx="12" fill="rgba(0,0,0,0.6)"/>
  <rect x="10" y="226" width="840" height="12" fill="rgba(0,0,0,0.6)"/>
  <line x1="10" y1="238" x2="850" y2="238" stroke="#00f0ff22" stroke-width="1"/>
  <circle cx="28" cy="224" r="3.5" fill="#ff00b4" class="live-dot" filter="url(#glow)"/>
  <text x="40" y="228" font-family="monospace" font-size="11" fill="#ff00b4">contribution_snake.exe</text>
  <text x="198" y="228" font-family="monospace" font-size="11" fill="#555580"> — eating the grid live</text>

  <!-- Contribution grid (static representation) -->
  <g transform="translate(12, 242)">
    <!-- Row of contribution cells - 5 rows x 78 cols approximation using groups -->
    <!-- Row 0 -->
    <g fill="#0d0a1a">
      <rect x="2"   y="2"  width="8" height="8" rx="2"/>
      <rect x="13"  y="2"  width="8" height="8" rx="2"/>
      <rect x="24"  y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="35"  y="2"  width="8" height="8" rx="2"/>
      <rect x="46"  y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="57"  y="2"  width="8" height="8" rx="2"/>
      <rect x="68"  y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="79"  y="2"  width="8" height="8" rx="2"/>
      <rect x="90"  y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="101" y="2"  width="8" height="8" rx="2"/>
      <rect x="112" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="123" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="134" y="2"  width="8" height="8" rx="2"/>
      <rect x="145" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="156" y="2"  width="8" height="8" rx="2"/>
      <rect x="167" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="178" y="2"  width="8" height="8" rx="2"/>
      <rect x="189" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="200" y="2"  width="8" height="8" rx="2"/>
      <rect x="211" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="222" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="233" y="2"  width="8" height="8" rx="2"/>
      <rect x="244" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="255" y="2"  width="8" height="8" rx="2"/>
      <rect x="266" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="277" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="288" y="2"  width="8" height="8" rx="2"/>
      <rect x="299" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="310" y="2"  width="8" height="8" rx="2"/>
      <rect x="321" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="332" y="2"  width="8" height="8" rx="2"/>
      <rect x="343" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="354" y="2"  width="8" height="8" rx="2"/>
      <rect x="365" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="376" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="387" y="2"  width="8" height="8" rx="2"/>
      <rect x="398" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="409" y="2"  width="8" height="8" rx="2"/>
      <rect x="420" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="431" y="2"  width="8" height="8" rx="2"/>
      <rect x="442" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="453" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="464" y="2"  width="8" height="8" rx="2"/>
      <rect x="475" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="486" y="2"  width="8" height="8" rx="2"/>
      <rect x="497" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="508" y="2"  width="8" height="8" rx="2"/>
      <rect x="519" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="530" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="541" y="2"  width="8" height="8" rx="2"/>
      <rect x="552" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="563" y="2"  width="8" height="8" rx="2"/>
      <rect x="574" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="585" y="2"  width="8" height="8" rx="2"/>
      <rect x="596" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="607" y="2"  width="8" height="8" rx="2"/>
      <rect x="618" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="629" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="640" y="2"  width="8" height="8" rx="2"/>
      <rect x="651" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="662" y="2"  width="8" height="8" rx="2"/>
      <rect x="673" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="684" y="2"  width="8" height="8" rx="2"/>
      <rect x="695" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="706" y="2"  width="8" height="8" rx="2"/>
      <rect x="717" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="728" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="739" y="2"  width="8" height="8" rx="2"/>
      <rect x="750" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="761" y="2"  width="8" height="8" rx="2"/>
      <rect x="772" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="783" y="2"  width="8" height="8" rx="2"/>
      <rect x="794" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="805" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="816" y="2"  width="8" height="8" rx="2"/>
      <rect x="827" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
    </g>
    <!-- Rows 1–4 (same pattern, shifted y) -->
    <use href="#row0" y="11"/>
    <g fill="#0d0a1a" transform="translate(0,11)">
      <rect x="2"   y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="13"  y="2"  width="8" height="8" rx="2"/>
      <rect x="24"  y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="35"  y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="46"  y="2"  width="8" height="8" rx="2"/>
      <rect x="57"  y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="68"  y="2"  width="8" height="8" rx="2"/>
      <rect x="79"  y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="90"  y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="101" y="2"  width="8" height="8" rx="2"/>
      <rect x="112" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="123" y="2"  width="8" height="8" rx="2"/>
      <rect x="134" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="145" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="156" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="167" y="2"  width="8" height="8" rx="2"/>
      <rect x="178" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="189" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="200" y="2"  width="8" height="8" rx="2"/>
      <rect x="211" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="222" y="2"  width="8" height="8" rx="2"/>
      <rect x="233" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="244" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="255" y="2"  width="8" height="8" rx="2"/>
      <rect x="266" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="277" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="288" y="2"  width="8" height="8" rx="2"/>
      <rect x="299" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="310" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="321" y="2"  width="8" height="8" rx="2"/>
      <rect x="332" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="343" y="2"  width="8" height="8" rx="2"/>
      <rect x="354" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="365" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="376" y="2"  width="8" height="8" rx="2"/>
      <rect x="387" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="398" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="409" y="2"  width="8" height="8" rx="2"/>
      <rect x="420" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="431" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="442" y="2"  width="8" height="8" rx="2"/>
      <rect x="453" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="464" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="475" y="2"  width="8" height="8" rx="2"/>
      <rect x="486" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="497" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="508" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="519" y="2"  width="8" height="8" rx="2"/>
      <rect x="530" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="541" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="552" y="2"  width="8" height="8" rx="2"/>
      <rect x="563" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="574" y="2"  width="8" height="8" rx="2"/>
      <rect x="585" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="596" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="607" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="618" y="2"  width="8" height="8" rx="2"/>
      <rect x="629" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="640" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="651" y="2"  width="8" height="8" rx="2"/>
      <rect x="662" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="673" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="684" y="2"  width="8" height="8" rx="2"/>
      <rect x="695" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="706" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="717" y="2"  width="8" height="8" rx="2"/>
      <rect x="728" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="739" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="750" y="2"  width="8" height="8" rx="2"/>
      <rect x="761" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="772" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="783" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="794" y="2"  width="8" height="8" rx="2"/>
      <rect x="805" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="816" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="827" y="2"  width="8" height="8" rx="2"/>
    </g>
    <!-- rows 2,3,4 mirrored patterns -->
    <g fill="#0d0a1a" transform="translate(0,22)">
      <rect x="2"   y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="13"  y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="24"  y="2"  width="8" height="8" rx="2"/>
      <rect x="35"  y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="46"  y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="57"  y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="68"  y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="79"  y="2"  width="8" height="8" rx="2"/>
      <rect x="90"  y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="101" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="112" y="2"  width="8" height="8" rx="2"/>
      <rect x="123" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="134" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="145" y="2"  width="8" height="8" rx="2"/>
      <rect x="156" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="167" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="178" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="189" y="2"  width="8" height="8" rx="2"/>
      <rect x="200" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="211" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="222" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="233" y="2"  width="8" height="8" rx="2"/>
      <rect x="244" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="255" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="266" y="2"  width="8" height="8" rx="2"/>
      <rect x="277" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="288" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="299" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="310" y="2"  width="8" height="8" rx="2"/>
      <rect x="321" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="332" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="343" y="2"  width="8" height="8" rx="2"/>
      <rect x="354" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="365" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="376" y="2"  width="8" height="8" rx="2"/>
      <rect x="387" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="398" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="409" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="420" y="2"  width="8" height="8" rx="2"/>
      <rect x="431" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="442" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="453" y="2"  width="8" height="8" rx="2"/>
      <rect x="464" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="475" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="486" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="497" y="2"  width="8" height="8" rx="2"/>
      <rect x="508" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="519" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="530" y="2"  width="8" height="8" rx="2"/>
      <rect x="541" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="552" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="563" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="574" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="585" y="2"  width="8" height="8" rx="2"/>
      <rect x="596" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="607" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="618" y="2"  width="8" height="8" rx="2"/>
      <rect x="629" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="640" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="651" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="662" y="2"  width="8" height="8" rx="2"/>
      <rect x="673" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="684" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="695" y="2"  width="8" height="8" rx="2"/>
      <rect x="706" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="717" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="728" y="2"  width="8" height="8" rx="2"/>
      <rect x="739" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="750" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="761" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
      <rect x="772" y="2"  width="8" height="8" rx="2" fill="#cc00ff"/>
      <rect x="783" y="2"  width="8" height="8" rx="2"/>
      <rect x="794" y="2"  width="8" height="8" rx="2" fill="#1a0040"/>
      <rect x="805" y="2"  width="8" height="8" rx="2" fill="#4a0080"/>
      <rect x="816" y="2"  width="8" height="8" rx="2"/>
      <rect x="827" y="2"  width="8" height="8" rx="2" fill="#9000cc"/>
    </g>
    <!-- Snake body animated -->
    <g>
      <!-- Snake segments sliding across middle row -->
      <rect x="2" y="36" width="9" height="9" rx="3" fill="#ff00b4" filter="url(#glow)">
        <animate attributeName="x" from="2" to="827" dur="8s" repeatCount="indefinite"/>
      </rect>
      <rect x="-9" y="36" width="9" height="9" rx="3" fill="rgba(220,0,180,0.85)">
        <animate attributeName="x" from="-9" to="816" dur="8s" repeatCount="indefinite"/>
      </rect>
      <rect x="-20" y="36" width="9" height="9" rx="3" fill="rgba(180,0,200,0.7)">
        <animate attributeName="x" from="-20" to="805" dur="8s" repeatCount="indefinite"/>
      </rect>
      <rect x="-31" y="36" width="9" height="9" rx="3" fill="rgba(140,0,220,0.55)">
        <animate attributeName="x" from="-31" to="794" dur="8s" repeatCount="indefinite"/>
      </rect>
      <rect x="-42" y="36" width="9" height="9" rx="3" fill="rgba(100,0,230,0.4)">
        <animate attributeName="x" from="-42" to="783" dur="8s" repeatCount="indefinite"/>
      </rect>
      <rect x="-53" y="36" width="9" height="9" rx="3" fill="rgba(80,0,240,0.28)">
        <animate attributeName="x" from="-53" to="772" dur="8s" repeatCount="indefinite"/>
      </rect>
      <!-- eyes on head -->
      <circle cx="8" cy="38" r="1.5" fill="white">
        <animate attributeName="cx" from="8" to="833" dur="8s" repeatCount="indefinite"/>
      </circle>
      <circle cx="8" cy="44" r="1.5" fill="white">
        <animate attributeName="cx" from="8" to="833" dur="8s" repeatCount="indefinite"/>
      </circle>
    </g>
  </g>

  <!-- ══════════════════════════════════════════════ -->
  <!-- LIVE STATUS -->
  <!-- ══════════════════════════════════════════════ -->
  <rect x="10" y="350" width="840" height="46" rx="10" fill="rgba(255,0,180,0.05)" stroke="#ff00b444" stroke-width="1"/>
  <!-- left accent bar -->
  <rect x="10" y="350" width="3" height="46" rx="1" fill="url(#shimmer)"/>
  <!-- sonar pulse -->
  <circle cx="32" cy="373" r="6" fill="#ff00b4">
    <animate attributeName="r" values="6;14;6" dur="1.8s" repeatCount="indefinite"/>
    <animate attributeName="opacity" values="0.8;0;0.8" dur="1.8s" repeatCount="indefinite"/>
  </circle>
  <circle cx="32" cy="373" r="5" fill="#ff00b4"/>
  <text x="50" y="369" font-family="monospace" font-size="12">
    <tspan fill="#ff00b4" font-weight="700">[ ONLINE ]</tspan>
    <tspan fill="#9090b0"> Currently interning at </tspan>
    <tspan fill="#00f0ff">ATI Motors</tspan>
    <tspan fill="#9090b0"> as </tspan>
    <tspan fill="#bf00ff">NPI</tspan>
    <tspan fill="#9090b0"> engineer</tspan>
  </text>
  <text x="50" y="385" font-family="monospace" font-size="12" fill="#9090b0">Parallel: building autonomous <tspan fill="#ff00b4">mobile manipulator</tspan> with ROS2 (sim → real)</text>

  <!-- ══════════════════════════════════════════════ -->
  <!-- STATS -->
  <!-- ══════════════════════════════════════════════ -->
  <!-- Projects -->
  <rect x="10"   y="408" width="200" height="52" rx="10" fill="rgba(255,0,180,0.07)" stroke="#ff00b433" stroke-width="1"/>
  <text x="110"  y="432" font-family="monospace" font-size="22" font-weight="900" fill="#ff00b4" text-anchor="middle" filter="url(#glow)">05</text>
  <text x="110"  y="450" font-family="monospace" font-size="10" fill="#555580" text-anchor="middle" letter-spacing="1">PROJECTS</text>
  <!-- Tech Stack -->
  <rect x="220"  y="408" width="200" height="52" rx="10" fill="rgba(0,240,255,0.07)" stroke="#00f0ff33" stroke-width="1"/>
  <text x="320"  y="432" font-family="monospace" font-size="22" font-weight="900" fill="#00f0ff" text-anchor="middle" filter="url(#glow)">12+</text>
  <text x="320"  y="450" font-family="monospace" font-size="10" fill="#555580" text-anchor="middle" letter-spacing="1">TECH STACK</text>
  <!-- Certs -->
  <rect x="430"  y="408" width="200" height="52" rx="10" fill="rgba(191,0,255,0.07)" stroke="#bf00ff33" stroke-width="1"/>
  <text x="530"  y="432" font-family="monospace" font-size="22" font-weight="900" fill="#bf00ff" text-anchor="middle" filter="url(#glow)">06</text>
  <text x="530"  y="450" font-family="monospace" font-size="10" fill="#555580" text-anchor="middle" letter-spacing="1">CERTS</text>
  <!-- Industries -->
  <rect x="640"  y="408" width="210" height="52" rx="10" fill="rgba(0,255,144,0.07)" stroke="#00ff9033" stroke-width="1"/>
  <text x="745"  y="432" font-family="monospace" font-size="22" font-weight="900" fill="#00ff90" text-anchor="middle" filter="url(#glow)">3+</text>
  <text x="745"  y="450" font-family="monospace" font-size="10" fill="#555580" text-anchor="middle" letter-spacing="1">INDUSTRIES</text>

  <!-- ══════════════════════════════════════════════ -->
  <!-- SKILL MATRIX -->
  <!-- ══════════════════════════════════════════════ -->
  <rect x="10" y="472" width="840" height="136" rx="10" fill="rgba(0,0,20,0.5)" stroke="#00f0ff22" stroke-width="1"/>
  <text x="26" y="492" font-family="monospace" font-size="11" fill="#00f0ff" letter-spacing="1">// SKILL_MATRIX</text>
  <line x1="160" y1="488" x2="840" y2="488" stroke="#00f0ff33" stroke-width="1"/>

  <!-- Skill rows -->
  <!-- s1: Python & ROS2 85% -->
  <text x="26" y="511" font-family="monospace" font-size="12" fill="#c0c0e0">Python &amp; ROS2 (Humble)</text>
  <text x="840" y="511" font-family="monospace" font-size="11" fill="#ff00b4" text-anchor="end">85%</text>
  <rect x="26" y="515" width="780" height="5" rx="3" fill="#111130"/>
  <rect x="26" y="515" width="0"   height="5" rx="3" fill="url(#sk1)" class="bar1">
    <animate attributeName="width" from="0" to="663" dur="1.6s" begin="0.4s" fill="freeze"/>
  </rect>

  <!-- s2: OpenCV 80% -->
  <text x="26" y="533" font-family="monospace" font-size="12" fill="#c0c0e0">OpenCV / Computer Vision</text>
  <text x="840" y="533" font-family="monospace" font-size="11" fill="#00f0ff" text-anchor="end">80%</text>
  <rect x="26" y="537" width="780" height="5" rx="3" fill="#111130"/>
  <rect x="26" y="537" width="0"   height="5" rx="3" fill="url(#sk2)">
    <animate attributeName="width" from="0" to="624" dur="1.6s" begin="0.55s" fill="freeze"/>
  </rect>

  <!-- s3: Arduino 75% -->
  <text x="26" y="555" font-family="monospace" font-size="12" fill="#c0c0e0">Arduino / Embedded (MPU6050)</text>
  <text x="840" y="555" font-family="monospace" font-size="11" fill="#bf00ff" text-anchor="end">75%</text>
  <rect x="26" y="559" width="780" height="5" rx="3" fill="#111130"/>
  <rect x="26" y="559" width="0"   height="5" rx="3" fill="url(#sk3)">
    <animate attributeName="width" from="0" to="585" dur="1.6s" begin="0.7s" fill="freeze"/>
  </rect>

  <!-- s4: Gazebo 70% -->
  <text x="26" y="577" font-family="monospace" font-size="12" fill="#c0c0e0">Gazebo / RViz / Simulation</text>
  <text x="840" y="577" font-family="monospace" font-size="11" fill="#00ff90" text-anchor="end">70%</text>
  <rect x="26" y="581" width="780" height="5" rx="3" fill="#111130"/>
  <rect x="26" y="581" width="0"   height="5" rx="3" fill="url(#sk4)">
    <animate attributeName="width" from="0" to="546" dur="1.6s" begin="0.85s" fill="freeze"/>
  </rect>

  <!-- s5: Linux/Git 65% -->
  <text x="26" y="599" font-family="monospace" font-size="12" fill="#c0c0e0">Linux / Git / C++ basics</text>
  <text x="840" y="599" font-family="monospace" font-size="11" fill="#00f0ff" text-anchor="end">65%</text>
  <rect x="26" y="603" width="780" height="5" rx="3" fill="#111130"/>
  <rect x="26" y="603" width="0"   height="5" rx="3" fill="url(#sk5)">
    <animate attributeName="width" from="0" to="507" dur="1.6s" begin="1.0s" fill="freeze"/>
  </rect>

</svg>
