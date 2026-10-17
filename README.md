# SNBV-_-SERGIO-NICOL-S-BERLANGA-VILLARREAL-
theking@kingdomofmurabba.org
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <meta name="theme-color" content="#07090e">
  <meta name="apple-mobile-web-app-capable" content="yes">
  <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
  <title>The_App™ | KINGDOM OF MURABBA™</title>

  <!-- PWA Manifest Injection -->
  <link rel="manifest" href="data:application/manifest+json;utf-8,%7B%22name%22%3A%22The_App%E2%84%A2%20KINGDOM%20OF%20MURABBA%E2%84%A2%22%2C%22short_name%22%3A%22Murabba%E2%84%A2%22%2C%22start_url%22%3A%22.%22%2C%22display%22%3A%22standalone%22%2C%22background_color%22%3A%22%2307090e%22%2C%22theme_color%22%3A%22%23dfb15b%22%7D">

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@700;900&family=JetBrains+Mono:wght@400;600;700;800&display=swap" rel="stylesheet">

  <style>
    :root {
      --gold: #dfb15b;
      --gold-bright: #ffd978;
      --gold-dark: #825f1b;
      --yellow-guard: #ffe600;
      --bg: #07090e;
      --panel-bg: rgba(13, 17, 23, 0.92);
      --panel-border: rgba(223, 177, 91, 0.30);
      --cyan: #00f0ff;
      --laser: #ff3366;
      --text-muted: #a6b7cd;
      --text: #f0f6fc;
      --font-mono: 'JetBrains Mono', monospace;
      --font-cinzel: 'Cinzel', serif;
    }

    * { box-sizing: border-box; margin: 0; padding: 0; user-select: none; }

    body {
      background-color: var(--bg);
      color: var(--text);
      font-family: var(--font-mono);
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      overflow-x: hidden;
      background-image: 
        radial-gradient(circle at 50% 0%, rgba(223, 177, 91, 0.15) 0%, transparent 60%),
        linear-gradient(rgba(255, 255, 255, 0.02) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255, 255, 255, 0.02) 1px, transparent 1px);
      background-size: 100% 100%, 32px 32px, 32px 32px;
    }

    /* CRT scanlines */
    .crt-overlay {
      position: fixed;
      inset: 0;
      background: linear-gradient(rgba(18, 16, 16, 0) 50%, rgba(0, 0, 0, 0.28) 50%);
      background-size: 100% 3px;
      z-index: 1000;
      pointer-events: none;
      opacity: 0.5;
    }

    /* Top App Navigation */
    .app-header {
      background: rgba(7, 9, 14, 0.95);
      border-bottom: 1px solid var(--panel-border);
      padding: 0.75rem 1.5rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      position: sticky;
      top: 0;
      z-index: 200;
      backdrop-filter: blur(12px);
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 0.6rem;
      font-family: var(--font-cinzel);
      font-size: 1.15rem;
      color: var(--gold-bright);
      font-weight: 900;
      letter-spacing: 0.12em;
    }

    .tag-app {
      font-family: var(--font-mono);
      font-size: 0.65rem;
      padding: 2px 6px;
      border: 1px solid var(--gold);
      color: var(--gold);
      border-radius: 3px;
    }

    /* Tab Switcher */
    .tab-nav {
      display: flex;
      gap: 0.4rem;
      background: rgba(0, 0, 0, 0.5);
      padding: 3px;
      border-radius: 6px;
      border: 1px solid rgba(255, 255, 255, 0.1);
    }

    .tab-btn {
      background: transparent;
      border: none;
      color: var(--text-muted);
      padding: 0.45rem 0.85rem;
      font-family: var(--font-mono);
      font-size: 0.72rem;
      font-weight: 700;
      cursor: pointer;
      border-radius: 4px;
      transition: all 0.2s ease;
    }

    .tab-btn:hover { color: #fff; }
    .tab-btn.active {
      background: var(--gold);
      color: #000;
      box-shadow: 0 0 10px rgba(223, 177, 91, 0.4);
    }

    /* App Views */
    .app-viewport {
      flex: 1;
      max-width: 1400px;
      width: 100%;
      margin: 0 auto;
      padding: 1.5rem;
    }

    .view-section {
      display: none;
    }

    .view-section.active {
      display: block;
      animation: fadeIn 0.25s cubic-bezier(0.16, 1, 0.3, 1);
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(6px); }
      to { opacity: 1; transform: translateY(0); }
    }

    /* Layout Grids */
    .grid-nexus {
      display: grid;
      grid-template-columns: 360px 1fr;
      gap: 1.5rem;
    }

    @media (max-width: 992px) {
      .grid-nexus { grid-template-columns: 1fr; }
      .app-header { flex-direction: column; gap: 0.75rem; }
      .tab-nav { width: 100%; justify-content: space-around; }
    }

    .panel {
      background: var(--panel-bg);
      border: 1px solid var(--panel-border);
      border-radius: 6px;
      padding: 1.25rem;
      box-shadow: 0 10px 30px rgba(0,0,0,0.5);
    }

    .panel-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 1px solid var(--panel-border);
      padding-bottom: 0.6rem;
      margin-bottom: 1rem;
    }

    .panel-title {
      font-family: var(--font-cinzel);
      font-size: 0.95rem;
      color: var(--gold);
      letter-spacing: 0.08em;
    }

    /* 3D Wireframe Cube */
    .cube-container {
      height: 160px;
      display: flex;
      justify-content: center;
      align-items: center;
      perspective: 700px;
    }

    .cube {
      width: 80px;
      height: 80px;
      position: relative;
      transform-style: preserve-3d;
      animation: spinCube 16s infinite linear;
    }

    @keyframes spinCube {
      from { transform: rotateX(20deg) rotateY(0deg); }
      to { transform: rotateX(20deg) rotateY(360deg); }
    }

    .face {
      position: absolute;
      width: 80px;
      height: 80px;
      border: 1px solid var(--gold);
      background: rgba(223, 177, 91, 0.08);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 0.65rem;
      font-weight: 700;
      color: var(--gold-bright);
      box-shadow: inset 0 0 10px rgba(223, 177, 91, 0.2);
    }

    .front  { transform: translateZ(40px); }
    .back   { transform: rotateY(180deg) translateZ(40px); }
    .right  { transform: rotateY(90deg) translateZ(40px); }
    .left   { transform: rotateY(-90deg) translateZ(40px); }
    .top    { transform: rotateX(90deg) translateZ(40px); }
    .bottom { transform: rotateX(-90deg) translateZ(40px); }

    /* Guard Badge */
    .guard-card {
      background: linear-gradient(135deg, rgba(255, 230, 0, 0.12), transparent);
      border: 1px solid var(--yellow-guard);
      padding: 0.8rem;
      border-radius: 4px;
      text-align: center;
      margin: 1rem 0;
    }

    /* Radar Canvas */
    .radar-box {
      width: 100%;
      height: 250px;
      background: #020407;
      border: 1px solid var(--panel-border);
      border-radius: 4px;
      position: relative;
      overflow: hidden;
    }

    #radarCanvas { width: 100%; height: 100%; display: block; }

    /* Tables & Search */
    .search-input {
      width: 100%;
      background: rgba(0,0,0,0.4);
      border: 1px solid var(--panel-border);
      color: #fff;
      padding: 0.6rem 0.8rem;
      border-radius: 4px;
      font-family: var(--font-mono);
      font-size: 0.8rem;
      margin-bottom: 1rem;
      outline: none;
    }

    .search-input:focus { border-color: var(--cyan); }

    .data-table {
      width: 100%;
      border-collapse: collapse;
      font-size: 0.78rem;
    }

    .data-table th {
      text-align: left;
      padding: 0.65rem;
      border-bottom: 1px solid var(--panel-border);
      color: var(--gold);
    }

    .data-table td {
      padding: 0.6rem 0.65rem;
      border-bottom: 1px solid rgba(255,255,255,0.04);
    }

    /* Terminal Console */
    .terminal {
      background: #020306;
      border: 1px solid rgba(255,255,255,0.1);
      border-radius: 4px;
      padding: 0.85rem;
      font-size: 0.75rem;
      color: #8be9fd;
      height: 220px;
      overflow-y: auto;
      white-space: pre-wrap;
      line-height: 1.5;
    }

    /* Interactive Action Buttons */
    .btn {
      background: linear-gradient(180deg, rgba(223, 177, 91, 0.22), rgba(130, 95, 27, 0.32));
      border: 1px solid var(--gold);
      color: var(--gold-bright);
      padding: 0.55rem 1rem;
      font-family: var(--font-mono);
      font-size: 0.74rem;
      font-weight: 700;
      letter-spacing: 0.05em;
      cursor: pointer;
      border-radius: 4px;
      transition: all 0.2s ease;
    }

    .btn:hover { background: var(--gold); color: #000; }

    /* Totem Grid Cards */
    .totem-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 1.25rem;
    }

    .totem-card {
      background: rgba(0,0,0,0.3);
      border: 1px solid rgba(255,255,255,0.08);
      border-left: 4px solid var(--gold);
      border-radius: 0 4px 4px 0;
      padding: 1.2rem;
      cursor: pointer;
      transition: all 0.2s ease;
    }

    .totem-card:hover, .totem-card.active {
      background: rgba(223, 177, 91, 0.12);
      border-left-color: var(--cyan);
      transform: translateY(-2px);
    }
  </style>
</head>
<body>

  <div class="crt-overlay"></div>

  <!-- Header & App Navigation -->
  <header class="app-header">
    <div class="brand">
      KINGDOM OF MURABBA™
      <span class="tag-app">The_App™</span>
    </div>

    <nav class="tab-nav" role="tablist">
      <button class="tab-btn active" data-tab="tab-nexus">NEXUS</button>
      <button class="tab-btn" data-tab="tab-coalition">COALITION (221)</button>
      <button class="tab-btn" data-tab="tab-totems">TÓTEMS (A–G)</button>
      <button class="tab-btn" data-tab="tab-comms">SLACK [320]</button>
    </nav>
  </header>

  <!-- Viewport Area -->
  <main class="app-viewport">
    
    <!-- VIEW 1: NEXUS -->
    <section id="tab-nexus" class="view-section active">
      <div class="grid-nexus">
        
        <!-- Left: Core Structure -->
        <div class="panel">
          <div class="panel-header">
            <span class="panel-title">Mukaab Architectural Nexus</span>
            <span style="font-size: 0.65rem; color: var(--gold);">Φ = 1.618036</span>
          </div>

          <div class="cube-container">
            <div class="cube">
              <div class="face front">SNBV™</div>
              <div class="face back">Φ 1.618</div>
              <div class="face right">MURABBA</div>
              <div class="face left">460,000E</div>
              <div class="face top">KINGDOM</div>
              <div class="face bottom">LASER</div>
            </div>
          </div>

          <div class="guard-card">
            <div style="color: var(--yellow-guard); font-weight: 800; font-size: 0.8rem;">
              GUARDIA D'ÈLITE MURABBA™
            </div>
            <div style="font-size: 0.72rem; color: #fff; font-weight: bold;">"CASCHI GIALLI"™</div>
            <div style="color: var(--gold-bright); letter-spacing: 0.4rem; margin: 4px 0;">[ ⤃ ⤇ ⤅ ⤉ ⤄ ]</div>
            <div style="font-size: 0.65rem; color: var(--text-muted);">FIELD MARSHAL: SNBV™</div>
          </div>

          <div style="display: flex; gap: 0.5rem; flex-wrap: wrap; margin-top: 1rem;">
            <button class="btn" style="flex: 1;" onclick="triggerPulse()">Transmit Pulse</button>
            <button class="btn" style="flex: 1;" onclick="copyAppManifesto()">Copy Payload</button>
          </div>
        </div>

        <!-- Right: Radar & Live Telemetry -->
        <div>
          <div class="panel">
            <div class="panel-header">
              <span class="panel-title">Sovereign Radar Sweep</span>
              <span style="font-size: 0.7rem; color: var(--cyan);">SECTOR: RIYADH NEXUS</span>
            </div>
            <div class="radar-box">
              <canvas id="radarCanvas"></canvas>
            </div>
          </div>

          <div class="panel" style="margin-top: 1.25rem;">
            <div class="panel-header">
              <span class="panel-title">The_App™ Live Stream</span>
              <span style="font-size: 0.65rem; color: var(--gold-bright);">PORT: 320</span>
            </div>
            <div class="terminal" id="termLog"></div>
          </div>
        </div>

      </div>
    </section>

    <!-- VIEW 2: COALITION (221 NATIONS) -->
    <section id="tab-coalition" class="view-section">
      <div class="panel">
        <div class="panel-header">
          <span class="panel-title">221 Países Sovereign Matrix</span>
          <span style="font-size: 0.7rem; color: var(--cyan);">TIERRA • MAR • AIRE • ARTILLERY</span>
        </div>

        <input type="text" class="search-input" id="coalitionFilter" placeholder="Filtrar por dominio, territorio o especificación táctica...">

        <table class="data-table">
          <thead>
            <tr>
              <th>Dominio / Territorio</th>
              <th>Nodos</th>
              <th>Clasificación Operativa</th>
            </tr>
          </thead>
          <tbody id="coalitionTableBody">
            <!-- Rendered by JS -->
          </tbody>
        </table>
      </div>
    </section>

    <!-- VIEW 3: TÓTEMS (A–G) -->
    <section id="tab-totems" class="view-section">
      <div class="totem-grid" id="totemGrid">
        <!-- Rendered by JS -->
      </div>
    </section>

    <!-- VIEW 4: COMMS 320 -->
    <section id="tab-comms" class="view-section">
      <div class="panel">
        <div class="panel-header">
          <span class="panel-title">Secure Slack Bridge: kingofmurabba.slack.com:320</span>
          <span style="font-size: 0.7rem; color: var(--yellow-guard);">STATUS: CONNECTED</span>
        </div>
        <p style="font-size: 0.75rem; color: var(--text-muted); margin-bottom: 1rem;">
          Direct communication channel with Caschi Gialli Elite Units and High Marshal Sergio Nicolás Berlanga Villarreal.
        </p>
        <div class="terminal" style="height: 320px;" id="commsLog"></div>
        <div style="display: flex; gap: 0.5rem; margin-top: 1rem;">
          <input type="text" class="search-input" id="commsInput" placeholder="Enter encrypted dispatch to Field Marshal..." style="margin-bottom: 0;">
          <button class="btn" onclick="sendComms()">Transmit</button>
        </div>
      </div>
    </section>

  </main>

  <script>
    /* =========================================================================
       1. NAVIGATION ROUTER
       ========================================================================= */
    const tabButtons = document.querySelectorAll('.tab-btn');
    const viewSections = document.querySelectorAll('.view-section');

    tabButtons.forEach(btn => {
      btn.addEventListener('click', () => {
        tabButtons.forEach(b => b.classList.remove('active'));
        viewSections.forEach(v => v.classList.remove('active'));

        btn.classList.add('active');
        const targetView = document.getElementById(btn.dataset.tab);
        if (targetView) targetView.classList.add('active');

        if (btn.dataset.tab === 'tab-nexus') resizeRadar();
      });
    });

    /* =========================================================================
       2. COALITION DATABASE MODULE
       ========================================================================= */
    const coalitionData = [
      { realm: "Kingdom of Saudi Arabia", nodes: "1", spec: "GRANDEZA + LÁSER", code: "KSA" },
      { realm: "Kingdom of UAE", nodes: "7", spec: "TECNIFICADO", code: "UAE" },
      { realm: "Kingdom of Egypt", nodes: "7", spec: "PODER + 460,000E (PURO & ÚNICO)", code: "EGY" },
      { realm: "Kingdom of Oriente Medio", nodes: "14 + 1*", spec: "GRANDEZA + PODER + EMIRATO ISLÁMICO", code: "ME" },
      { realm: "Kingdom of Unity (UK)", nodes: "3", spec: "BRITISH ARMY + ROYAL NAVY + RAF (ULTRA MAR)", code: "UK" },
      { realm: "República de Irlanda (Sur)", nodes: "1", spec: "Óglaigh na hÉireann [INFANTERÍA]", code: "IRL" },
      { realm: "The Commonwealth", nodes: "56", spec: "HEAD OF STATE SOVEREIGNTY", code: "CW" },
      { realm: "European Union", nodes: "27", spec: "HEAD OF STATE COUNCIL", code: "EU" },
      { realm: "African Union", nodes: "56", spec: "STRATEGIC ALLIANCE BRIGADES", code: "AU" },
      { realm: "United Nations Coalition", nodes: "102", spec: "GLOBAL TREATY FORCES", code: "UN" },
      { realm: "Vatican City", nodes: "1", spec: "HEAD OF STATE | [GUARDIA SUIZA]", code: "VAT" },
      { realm: "Panama City & Moldavia", nodes: "2", spec: "HEAD OF STATE JURISDICTIONS", code: "PAN/MDA" }
    ];

    const tableBody = document.getElementById('coalitionTableBody');
    const filterInput = document.getElementById('coalitionFilter');

    function renderTable(items) {
      tableBody.innerHTML = '';
      items.forEach(row => {
        const tr = document.createElement('tr');
        tr.innerHTML = `
          <td><strong>${row.realm}</strong></td>
          <td style="color:var(--gold-bright); font-weight:bold;">${row.nodes}</td>
          <td><span style="color:var(--cyan);">${row.spec}</span></td>
        `;
        tableBody.appendChild(tr);
      });
    }
    renderTable(coalitionData);

    filterInput.addEventListener('input', (e) => {
      const q = e.target.value.toLowerCase();
      const filtered = coalitionData.filter(d => 
        d.realm.toLowerCase().includes(q) || 
        d.spec.toLowerCase().includes(q)
      );
      renderTable(filtered);
    });

    /* =========================================================================
       3. TOTEM SYSTEM MODULE (A–G)
       ========================================================================= */
    const totems = [
      { id: "A", title: "TÓTEM SUPREMO SEXTA EXPANSIÓN", holder: "SERGIO NICOLÁS BERLANGA VILLARREAL™", desc: "Highest node of harmonic expansion across the kingdom structure." },
      { id: "B", title: "TÓTEM DE LA MAGNITUD INFINITA", holder: "SERGIO NICOLÁS BERLANGA VILLARREAL™", desc: "Infinite scalar magnitude governing all territory dynamics." },
      { id: "C", title: "TÓTEM DE SOBERANÍA PLANETARIA", holder: "SERGIO NICOLÁS BERLANGA VILLARREAL™", desc: "Absolute planetary sovereign consensus across 221 realms." },
      { id: "D", title: "TÓTEM DE LA TRIPLE EXPANSIÓN", holder: "SERGIO NICOLÁS BERLANGA VILLARREAL™", desc: "Triadic operational geometry: Monarquía, Influencia, Tecnología." },
      { id: "E", title: "TÓTEM INFINITO (SLACK 320)", holder: "MAR. SNBV™ Φ = 1.618036", desc: "Frequency link to kingofmurabba.slack.com on port 320." },
      { id: "F", title: "TÓTEM INFINITO VECTOR", holder: "SERGIO NICOLÁS BERLANGA VILLARREAL™", desc: "Vectorial authority across land, air, and ultra-maritime artillery." },
      { id: "G", title: "TÓTEM CHEk0 CORE", holder: "\"CHEk0 Berlanga\"™", desc: "Personalized core identity and field marshal command key." }
    ];

    const totemGrid = document.getElementById('totemGrid');
    totems.forEach(t => {
      const card = document.createElement('div');
      card.className = 'totem-card';
      card.innerHTML = `
        <div style="font-size:0.75rem; color:var(--gold-bright); font-weight:800;">TÓTEM ${t.id}</div>
        <div style="font-size:0.9rem; font-weight:bold; margin: 4px 0;">${t.title}</div>
        <div style="font-size:0.75rem; color:var(--cyan); margin-bottom:6px;">${t.holder}</div>
        <div style="font-size:0.7rem; color:var(--text-muted);">${t.desc}</div>
      `;
      card.addEventListener('click', () => {
        document.querySelectorAll('.totem-card').forEach(c => c.classList.remove('active'));
        card.classList.add('active');
        logStream(`TOTEM ${t.id} ENGAGED: ${t.title}`);
      });
      totemGrid.appendChild(card);
    });

    /* =========================================================================
       4. TELEMETRY & COMMS STREAM
       ========================================================================= */
    const termLog = document.getElementById('termLog');
    const commsLog = document.getElementById('commsLog');

    function logStream(msg) {
      const ts = new Date().toISOString().split('T')[1].slice(0, 8);
      termLog.textContent += (termLog.textContent ? '\n' : '') + `[${ts}Z] ${msg}`;
      termLog.scrollTop = termLog.scrollHeight;
    }

    function logComms(user, msg) {
      const ts = new Date().toISOString().split('T')[1].slice(0, 8);
      commsLog.textContent += (commsLog.textContent ? '\n' : '') + `[${ts}] <${user}>: ${msg}`;
      commsLog.scrollTop = commsLog.scrollHeight;
    }

    logStream("The_App™ initialized. System architecture online.");
    logStream("Caschi Gialli defense ready [ ⤃ ⤇ ⤅ ⤉ ⤄ ].");
    logComms("SYS", "Channel kingofmurabba.slack.com:320 verified.");
    logComms("FIELD_MARSHAL", "The_App™ active. All 221 vectors synchronized.");

    function sendComms() {
      const inp = document.getElementById('commsInput');
      if (!inp.value.trim()) return;
      logComms("OPERATOR", inp.value);
      const text = inp.value;
      inp.value = '';
      setTimeout(() => {
        logComms("SNBV_BOT", `Echo acknowledged: "${text}". Command confirmed.`);
      }, 400);
    }

    function triggerPulse() {
      logStream("PULSE: Global telemetry sweep broadcast to 221 realms.");
    }

    function copyAppManifesto() {
      const payload = `The_App™ KINGDOM_OF_MURABBA™ | SNBV™ Φ = 1.618036 http://kingofmurabba.slack.com 320 }`;
      navigator.clipboard.writeText(payload).then(() => {
        logStream("PAYLOAD: Sovereign signature copied to clipboard.");
      });
    }

    /* =========================================================================
       5. RADAR SYSTEM
       ========================================================================= */
    const canvas = document.getElementById('radarCanvas');
    const ctx = canvas.getContext('2d');
    let angle = 0;

    function resizeRadar() {
      const rect = canvas.getBoundingClientRect();
      const dpr = window.devicePixelRatio || 1;
      canvas.width = rect.width * dpr;
      canvas.height = rect.height * dpr;
      ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
    }
    window.addEventListener('resize', resizeRadar);
    setTimeout(resizeRadar, 100);

    function drawRadar() {
      const rect = canvas.getBoundingClientRect();
      const w = rect.width;
      const h = rect.height;
      if (!w || !h) return;

      const cx = w / 2;
      const cy = h / 2;
      const r = Math.min(cx, cy) * 0.9;

      ctx.clearRect(0, 0, w, h);

      // Rings
      ctx.strokeStyle = "rgba(223, 177, 91, 0.18)";
      ctx.lineWidth = 1;
      for (let i = 1; i <= 3; i++) {
        ctx.beginPath();
        ctx.arc(cx, cy, (r / 3) * i, 0, Math.PI * 2);
        ctx.stroke();
      }

      // Sweep
      ctx.save();
      ctx.translate(cx, cy);
      ctx.rotate(angle);

      ctx.beginPath();
      ctx.moveTo(0, 0);
      ctx.arc(0, 0, r, 0, 0.4);
      ctx.closePath();
      ctx.fillStyle = "rgba(223, 177, 91, 0.25)";
      ctx.fill();

      ctx.beginPath();
      ctx.moveTo(0, 0);
      ctx.lineTo(r, 0);
      ctx.strokeStyle = "rgba(255, 217, 120, 0.85)";
      ctx.stroke();

      ctx.restore();

      angle += 0.025;
      requestAnimationFrame(drawRadar);
    }
    requestAnimationFrame(drawRadar);
  </script>
</body>
</html>
