<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Roadmap – Automated Web Agency</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@700;800&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a0f;
    --surface: #111118;
    --border: #1e1e2e;
    --accent: #00ff88;
    --accent2: #ff6b35;
    --accent3: #7c3aed;
    --accent4: #06b6d4;
    --accent5: #f59e0b;
    --text: #e2e8f0;
    --muted: #64748b;
    --white: #ffffff;
    --red: #ff4d4d;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* BG noise texture */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 0;
  }

  .container {
    max-width: 960px;
    margin: 0 auto;
    padding: 60px 24px 80px;
    position: relative;
    z-index: 1;
  }

  /* Header */
  .header {
    text-align: center;
    margin-bottom: 72px;
  }

  .header .tag {
    display: inline-block;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--accent);
    border: 1px solid var(--accent);
    padding: 4px 12px;
    border-radius: 2px;
    margin-bottom: 20px;
    animation: fadeDown 0.6s ease both;
  }

  .header h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(32px, 6vw, 56px);
    font-weight: 800;
    line-height: 1.05;
    letter-spacing: -0.02em;
    color: var(--white);
    animation: fadeDown 0.6s 0.1s ease both;
  }

  .header h1 span {
    color: var(--accent);
  }

  .header p {
    margin-top: 16px;
    color: var(--muted);
    font-size: 15px;
    font-weight: 300;
    animation: fadeDown 0.6s 0.2s ease both;
  }

  /* Timeline */
  .timeline {
    position: relative;
  }

  .timeline::before {
    content: '';
    position: absolute;
    left: 28px;
    top: 0;
    bottom: 0;
    width: 1px;
    background: linear-gradient(to bottom, transparent, var(--border) 5%, var(--border) 95%, transparent);
  }

  .phase {
    display: flex;
    gap: 32px;
    margin-bottom: 40px;
    animation: fadeUp 0.5s ease both;
  }

  .phase:nth-child(1) { animation-delay: 0.1s; }
  .phase:nth-child(2) { animation-delay: 0.2s; }
  .phase:nth-child(3) { animation-delay: 0.3s; }
  .phase:nth-child(4) { animation-delay: 0.4s; }
  .phase:nth-child(5) { animation-delay: 0.5s; }

  .phase-dot {
    flex-shrink: 0;
    width: 56px;
    height: 56px;
    border-radius: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 0.05em;
    position: relative;
    z-index: 1;
  }

  .phase-dot::after {
    content: '';
    position: absolute;
    inset: -1px;
    border-radius: 13px;
    z-index: -1;
    opacity: 0.3;
    filter: blur(8px);
  }

  .p1 .phase-dot { background: #001a0e; color: var(--accent); border: 1px solid var(--accent); }
  .p1 .phase-dot::after { background: var(--accent); }

  .p2 .phase-dot { background: #1a0d00; color: var(--accent2); border: 1px solid var(--accent2); }
  .p2 .phase-dot::after { background: var(--accent2); }

  .p3 .phase-dot { background: #12002a; color: #a78bfa; border: 1px solid var(--accent3); }
  .p3 .phase-dot::after { background: var(--accent3); }

  .p4 .phase-dot { background: #001318; color: var(--accent4); border: 1px solid var(--accent4); }
  .p4 .phase-dot::after { background: var(--accent4); }

  .p5 .phase-dot { background: #1a1200; color: var(--accent5); border: 1px solid var(--accent5); }
  .p5 .phase-dot::after { background: var(--accent5); }

  .phase-content {
    flex: 1;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 24px 28px;
    position: relative;
    overflow: hidden;
  }

  .phase-content::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
  }

  .p1 .phase-content::before { background: var(--accent); }
  .p2 .phase-content::before { background: var(--accent2); }
  .p3 .phase-content::before { background: var(--accent3); }
  .p4 .phase-content::before { background: var(--accent4); }
  .p5 .phase-content::before { background: var(--accent5); }

  .phase-header {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    gap: 12px;
    margin-bottom: 16px;
    flex-wrap: wrap;
  }

  .phase-title-group {}

  .phase-label {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    margin-bottom: 4px;
  }

  .p1 .phase-label { color: var(--accent); }
  .p2 .phase-label { color: var(--accent2); }
  .p3 .phase-label { color: #a78bfa; }
  .p4 .phase-label { color: var(--accent4); }
  .p5 .phase-label { color: var(--accent5); }

  .phase-title {
    font-family: 'Syne', sans-serif;
    font-size: 20px;
    font-weight: 700;
    color: var(--white);
  }

  .phase-badge {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    padding: 4px 10px;
    border-radius: 4px;
    white-space: nowrap;
    flex-shrink: 0;
  }

  .p1 .phase-badge { background: #001a0e; color: var(--accent); border: 1px solid #003d1e; }
  .p2 .phase-badge { background: #1a0d00; color: var(--accent2); border: 1px solid #3d1e00; }
  .p3 .phase-badge { background: #12002a; color: #a78bfa; border: 1px solid #2d0060; }
  .p4 .phase-badge { background: #001318; color: var(--accent4); border: 1px solid #00303d; }
  .p5 .phase-badge { background: #1a1200; color: var(--accent5); border: 1px solid #3d2d00; }

  .phase-desc {
    font-size: 13px;
    color: var(--muted);
    margin-bottom: 16px;
    font-style: italic;
  }

  .tasks {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 8px;
    margin-bottom: 16px;
  }

  @media (max-width: 600px) {
    .tasks { grid-template-columns: 1fr; }
  }

  .task {
    display: flex;
    align-items: flex-start;
    gap: 8px;
    font-size: 13px;
    color: #94a3b8;
    line-height: 1.4;
  }

  .task-num {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    flex-shrink: 0;
    margin-top: 2px;
    opacity: 0.5;
  }

  .milestone {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 10px 14px;
    border-radius: 8px;
    font-size: 13px;
    font-weight: 500;
    margin-top: 4px;
  }

  .p1 .milestone { background: #001a0e; color: var(--accent); }
  .p2 .milestone { background: #1a0d00; color: var(--accent2); }
  .p3 .milestone { background: #12002a; color: #a78bfa; }
  .p4 .milestone { background: #001318; color: var(--accent4); }
  .p5 .milestone { background: #1a1200; color: var(--accent5); }

  .milestone-icon { font-size: 14px; }

  /* Tech stack section */
  .stack-section {
    margin-top: 56px;
    animation: fadeUp 0.5s 0.6s ease both;
  }

  .stack-section h2 {
    font-family: 'Syne', sans-serif;
    font-size: 22px;
    font-weight: 700;
    color: var(--white);
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .stack-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
    gap: 12px;
  }

  .stack-item {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 16px;
    text-align: center;
  }

  .stack-item .icon { font-size: 22px; margin-bottom: 8px; }
  .stack-item .name {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    color: var(--muted);
    letter-spacing: 0.05em;
    text-transform: uppercase;
  }
  .stack-item .val {
    font-size: 12px;
    color: var(--text);
    margin-top: 2px;
    font-weight: 500;
  }

  /* Revenue targets */
  .revenue-section {
    margin-top: 48px;
    animation: fadeUp 0.5s 0.7s ease both;
  }

  .revenue-section h2 {
    font-family: 'Syne', sans-serif;
    font-size: 22px;
    font-weight: 700;
    color: var(--white);
    margin-bottom: 20px;
  }

  .revenue-bars {
    display: flex;
    flex-direction: column;
    gap: 14px;
  }

  .rev-row {
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .rev-label {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--muted);
    width: 60px;
    flex-shrink: 0;
  }

  .rev-bar-wrap {
    flex: 1;
    height: 28px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 6px;
    overflow: hidden;
    position: relative;
  }

  .rev-bar {
    height: 100%;
    border-radius: 5px;
    display: flex;
    align-items: center;
    padding-left: 12px;
    font-size: 12px;
    font-weight: 500;
    font-family: 'Space Mono', monospace;
    transition: width 1s cubic-bezier(0.23, 1, 0.32, 1);
  }

  .rev-bar.b1 { width: 20%; background: linear-gradient(90deg, #001a0e, #003d1e); color: var(--accent); }
  .rev-bar.b2 { width: 50%; background: linear-gradient(90deg, #12002a, #2d0060); color: #a78bfa; }
  .rev-bar.b3 { width: 100%; background: linear-gradient(90deg, #001318, #00303d); color: var(--accent4); }

  .rev-val {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--text);
    width: 80px;
    flex-shrink: 0;
    text-align: right;
  }

  /* Footer */
  .footer {
    margin-top: 64px;
    text-align: center;
    animation: fadeUp 0.5s 0.8s ease both;
  }

  .footer .brand {
    font-family: 'Syne', sans-serif;
    font-size: 18px;
    font-weight: 800;
    color: var(--red);
    letter-spacing: -0.01em;
  }

  .footer .brand span { color: var(--white); }

  .footer p {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    color: var(--muted);
    margin-top: 6px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
  }

  @keyframes fadeDown {
    from { opacity: 0; transform: translateY(-16px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }
</style>
</head>
<body>
<div class="container">

  <!-- Header -->
  <div class="header">
    <div class="tag">KHAI WEB AGENCY · 2026</div>
    <h1>Automated Web Agency<br><span>Roadmap</span></h1>
    <p>WhatsApp → AI → Website → QRIS · Full automation pipeline</p>
  </div>

  <!-- Timeline -->
  <div class="timeline">

    <!-- FASE 1 -->
    <div class="phase p1">
      <div class="phase-dot">F·01</div>
      <div class="phase-content">
        <div class="phase-header">
          <div class="phase-title-group">
            <div class="phase-label">Fase 1</div>
            <div class="phase-title">Fondasi</div>
          </div>
          <div class="phase-badge">Minggu 1–2</div>
        </div>
        <div class="phase-desc">Goal: OpenClaw jalan + bisa ngobrol via WhatsApp</div>
        <div class="tasks">
          <div class="task"><span class="task-num">01</span> Setup VPS (DigitalOcean/Vultr $6/bln)</div>
          <div class="task"><span class="task-num">02</span> Install Node.js 22+ di VPS</div>
          <div class="task"><span class="task-num">03</span> Install & onboard OpenClaw</div>
          <div class="task"><span class="task-num">04</span> Connect WhatsApp via Baileys</div>
          <div class="task"><span class="task-num">05</span> Setup Claude Anthropic API key</div>
          <div class="task"><span class="task-num">06</span> Test kirim-terima pesan via WA</div>
        </div>
        <div class="milestone">
          <span class="milestone-icon">✅</span>
          Milestone: Bot bisa balas pesan WhatsApp
        </div>
      </div>
    </div>

    <!-- FASE 2 -->
    <div class="phase p2">
      <div class="phase-dot">F·02</div>
      <div class="phase-content">
        <div class="phase-header">
          <div class="phase-title-group">
            <div class="phase-label">Fase 2</div>
            <div class="phase-title">Core Engine</div>
          </div>
          <div class="phase-badge">Minggu 3–4</div>
        </div>
        <div class="phase-desc">Goal: Bot bisa generate website dari input client</div>
        <div class="tasks">
          <div class="task"><span class="task-num">01</span> Buat skill: website-generator</div>
          <div class="task"><span class="task-num">02</span> Logic terima screenshot / link Canva</div>
          <div class="task"><span class="task-num">03</span> Vision AI analisis → generate HTML/CSS/JS</div>
          <div class="task"><span class="task-num">04</span> Auto-deploy preview ke Vercel via API</div>
          <div class="task"><span class="task-num">05</span> Bot kirim preview link ke client</div>
          <div class="task"><span class="task-num">06</span> Handle revisi 1–2x otomatis</div>
        </div>
        <div class="milestone">
          <span class="milestone-icon">✅</span>
          Milestone: Screenshot → dapat preview website
        </div>
      </div>
    </div>

    <!-- FASE 3 -->
    <div class="phase p3">
      <div class="phase-dot">F·03</div>
      <div class="phase-content">
        <div class="phase-header">
          <div class="phase-title-group">
            <div class="phase-label">Fase 3</div>
            <div class="phase-title">Payment Flow</div>
          </div>
          <div class="phase-badge">Minggu 5–6</div>
        </div>
        <div class="phase-desc">Goal: Sistem bayar otomatis via QRIS</div>
        <div class="tasks">
          <div class="task"><span class="task-num">01</span> Daftar Midtrans / Xendit (gratis)</div>
          <div class="task"><span class="task-num">02</span> Buat skill: payment-handler</div>
          <div class="task"><span class="task-num">03</span> Client approve → bot generate QRIS</div>
          <div class="task"><span class="task-num">04</span> Setup webhook payment confirmed</div>
          <div class="task"><span class="task-num">05</span> Bot kirim final link + zip file otomatis</div>
          <div class="task"><span class="task-num">06</span> Test end-to-end full flow</div>
        </div>
        <div class="milestone">
          <span class="milestone-icon">✅</span>
          Milestone: Full flow order → bayar otomatis
        </div>
      </div>
    </div>

    <!-- FASE 4 -->
    <div class="phase p4">
      <div class="phase-dot">F·04</div>
      <div class="phase-content">
        <div class="phase-header">
          <div class="phase-title-group">
            <div class="phase-label">Fase 4</div>
            <div class="phase-title">Polish & Launch</div>
          </div>
          <div class="phase-badge">Minggu 7–8</div>
        </div>
        <div class="phase-desc">Goal: Siap dipakai client beneran</div>
        <div class="tasks">
          <div class="task"><span class="task-num">01</span> Buat script promo WA (copywriting)</div>
          <div class="task"><span class="task-num">02</span> Setup auto-reply untuk FAQ</div>
          <div class="task"><span class="task-num">03</span> Buat katalog harga & portofolio</div>
          <div class="task"><span class="task-num">04</span> Soft launch ke circle pertama</div>
          <div class="task"><span class="task-num">05</span> Collect testimoni & screenshot hasil</div>
          <div class="task"><span class="task-num">06</span> Bug fix & edge case handling</div>
        </div>
        <div class="milestone">
          <span class="milestone-icon">✅</span>
          Milestone: 5 order pertama masuk
        </div>
      </div>
    </div>

    <!-- FASE 5 -->
    <div class="phase p5">
      <div class="phase-dot">F·05</div>
      <div class="phase-content">
        <div class="phase-header">
          <div class="phase-title-group">
            <div class="phase-label">Fase 5</div>
            <div class="phase-title">Scale Up</div>
          </div>
          <div class="phase-badge">Bulan 3+</div>
        </div>
        <div class="phase-desc">Goal: 50–100 order/bulan, revenue Rp 5–10 juta</div>
        <div class="tasks">
          <div class="task"><span class="task-num">01</span> Upgrade ke WA Business API (Fonnte)</div>
          <div class="task"><span class="task-num">02</span> Tambah tier harga & template library</div>
          <div class="task"><span class="task-num">03</span> Sistem referral (refer = diskon)</div>
          <div class="task"><span class="task-num">04</span> Expand: Instagram DM, Telegram</div>
          <div class="task"><span class="task-num">05</span> Pertimbangkan hire VA</div>
          <div class="task"><span class="task-num">06</span> Analytics & monitoring dashboard</div>
        </div>
        <div class="milestone">
          <span class="milestone-icon">✅</span>
          Milestone: Revenue Rp 5–10 juta/bulan
        </div>
      </div>
    </div>

  </div>

  <!-- Tech Stack -->
  <div class="stack-section">
    <h2>🛠 Tech Stack</h2>
    <div class="stack-grid">
      <div class="stack-item">
        <div class="icon">🦞</div>
        <div class="name">Agent</div>
        <div class="val">OpenClaw</div>
      </div>
      <div class="stack-item">
        <div class="icon">🧠</div>
        <div class="name">LLM</div>
        <div class="val">Claude Sonnet</div>
      </div>
      <div class="stack-item">
        <div class="icon">💬</div>
        <div class="name">Chat</div>
        <div class="val">WhatsApp</div>
      </div>
      <div class="stack-item">
        <div class="icon">🌐</div>
        <div class="name">Deploy</div>
        <div class="val">Vercel API</div>
      </div>
      <div class="stack-item">
        <div class="icon">💳</div>
        <div class="name">Payment</div>
        <div class="val">Midtrans QRIS</div>
      </div>
      <div class="stack-item">
        <div class="icon">🖥</div>
        <div class="name">Server</div>
        <div class="val">DigitalOcean</div>
      </div>
    </div>
  </div>

  <!-- Revenue Targets -->
  <div class="revenue-section">
    <h2>📈 Target Revenue</h2>
    <div class="revenue-bars">
      <div class="rev-row">
        <div class="rev-label">Bln 1–2</div>
        <div class="rev-bar-wrap">
          <div class="rev-bar b1">20 order</div>
        </div>
        <div class="rev-val">~Rp 1,9 jt</div>
      </div>
      <div class="rev-row">
        <div class="rev-label">Bln 3–4</div>
        <div class="rev-bar-wrap">
          <div class="rev-bar b2">50 order</div>
        </div>
        <div class="rev-val">~Rp 4,8 jt</div>
      </div>
      <div class="rev-row">
        <div class="rev-label">Bln 5+</div>
        <div class="rev-bar-wrap">
          <div class="rev-bar b3">100 order</div>
        </div>
        <div class="rev-val">~Rp 10 jt</div>
      </div>
    </div>
  </div>

  <!-- Footer -->
  <div class="footer">
    <div class="brand">RAN <span>GROUP</span></div>
    <p>Automated Web Agency · Built with OpenClaw + Claude AI</p>
  </div>

</div>
</body>
</html>
