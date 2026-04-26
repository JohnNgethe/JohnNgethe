<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>John Ngethe — GitHub Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0a0a0f;
    --surface: #111118;
    --border: #1e1e2e;
    --accent: #7c6af7;
    --accent2: #38d9a9;
    --accent3: #f9a825;
    --text: #e8e6f0;
    --muted: #6b6880;
    --glow: rgba(124, 106, 247, 0.18);
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Syne', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* === ANIMATED GRID BACKGROUND === */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(124,106,247,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(124,106,247,0.04) 1px, transparent 1px);
    background-size: 48px 48px;
    z-index: 0;
    animation: gridDrift 20s linear infinite;
  }

  @keyframes gridDrift {
    0%   { background-position: 0 0; }
    100% { background-position: 48px 48px; }
  }

  /* === FLOATING ORBS === */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(90px);
    opacity: 0.18;
    z-index: 0;
    animation: orbFloat 12s ease-in-out infinite alternate;
  }
  .orb-1 { width: 400px; height: 400px; background: var(--accent); top: -100px; left: -100px; animation-duration: 14s; }
  .orb-2 { width: 300px; height: 300px; background: var(--accent2); bottom: -80px; right: -80px; animation-duration: 10s; animation-delay: -4s; }
  .orb-3 { width: 200px; height: 200px; background: var(--accent3); top: 40%; left: 60%; animation-duration: 16s; animation-delay: -8s; }

  @keyframes orbFloat {
    0%   { transform: translate(0, 0) scale(1); }
    100% { transform: translate(30px, 40px) scale(1.1); }
  }

  /* === WRAPPER === */
  .wrapper {
    position: relative;
    z-index: 1;
    max-width: 780px;
    margin: 0 auto;
    padding: 60px 24px 80px;
  }

  /* === HERO === */
  .hero {
    text-align: center;
    margin-bottom: 64px;
    opacity: 0;
    animation: fadeUp 0.8s ease forwards 0.2s;
  }

  .avatar-ring {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 90px; height: 90px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    margin-bottom: 24px;
    animation: spin 8s linear infinite;
    position: relative;
  }
  .avatar-ring::before {
    content: '';
    position: absolute;
    inset: 3px;
    border-radius: 50%;
    background: var(--bg);
  }
  .avatar-inner {
    position: relative;
    z-index: 1;
    font-size: 36px;
    line-height: 1;
  }

  @keyframes spin {
    0%   { box-shadow: 0 0 0 0 var(--glow); }
    50%  { box-shadow: 0 0 30px 8px var(--glow); }
    100% { box-shadow: 0 0 0 0 var(--glow); }
  }

  .hero h1 {
    font-size: clamp(2.2rem, 5vw, 3.2rem);
    font-weight: 800;
    letter-spacing: -0.03em;
    line-height: 1.1;
    background: linear-gradient(135deg, #fff 30%, var(--accent) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 12px;
  }

  .hero p {
    font-family: 'DM Mono', monospace;
    font-size: 0.85rem;
    color: var(--accent2);
    letter-spacing: 0.05em;
    opacity: 0.85;
    margin-bottom: 32px;
  }
  .hero p::before { content: '> '; opacity: 0.5; }

  /* === BADGE LINKS === */
  .badges {
    display: flex;
    justify-content: center;
    gap: 12px;
    flex-wrap: wrap;
  }

  .badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 10px 20px;
    border-radius: 8px;
    font-family: 'DM Mono', monospace;
    font-size: 0.78rem;
    font-weight: 500;
    letter-spacing: 0.04em;
    text-decoration: none;
    border: 1px solid var(--border);
    background: var(--surface);
    color: var(--text);
    transition: all 0.25s ease;
    position: relative;
    overflow: hidden;
  }
  .badge::after {
    content: '';
    position: absolute;
    inset: 0;
    opacity: 0;
    transition: opacity 0.25s;
  }
  .badge:hover { transform: translateY(-2px); border-color: currentColor; }
  .badge:hover::after { opacity: 1; }

  .badge-linkedin { color: #4dabf7; }
  .badge-linkedin::after { background: linear-gradient(135deg, rgba(77,171,247,0.08), transparent); }
  .badge-email { color: #f06595; }
  .badge-email::after { background: linear-gradient(135deg, rgba(240,101,149,0.08), transparent); }
  .badge-github { color: var(--accent); }
  .badge-github::after { background: linear-gradient(135deg, rgba(124,106,247,0.08), transparent); }

  .badge svg { width: 16px; height: 16px; flex-shrink: 0; }

  /* === DIVIDER === */
  .divider {
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--border), transparent);
    margin: 48px 0;
  }

  /* === SECTIONS === */
  .section {
    opacity: 0;
    animation: fadeUp 0.7s ease forwards;
    margin-bottom: 48px;
  }
  .section:nth-child(1) { animation-delay: 0.4s; }
  .section:nth-child(2) { animation-delay: 0.55s; }
  .section:nth-child(3) { animation-delay: 0.7s; }
  .section:nth-child(4) { animation-delay: 0.85s; }

  .section-label {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  .section-title {
    font-size: 1.5rem;
    font-weight: 700;
    margin-bottom: 14px;
    letter-spacing: -0.02em;
  }

  .section p {
    font-size: 0.95rem;
    line-height: 1.75;
    color: #b0adc5;
  }

  /* === TECH STACK === */
  .tech-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .tech-pill {
    display: inline-flex;
    align-items: center;
    gap: 7px;
    padding: 7px 14px;
    border-radius: 6px;
    border: 1px solid var(--border);
    background: var(--surface);
    font-family: 'DM Mono', monospace;
    font-size: 0.78rem;
    color: var(--muted);
    transition: all 0.2s ease;
    cursor: default;
  }
  .tech-pill:hover {
    border-color: var(--accent);
    color: var(--text);
    background: rgba(124,106,247,0.08);
    transform: translateY(-1px);
  }
  .tech-pill .dot {
    width: 7px; height: 7px;
    border-radius: 50%;
    background: var(--accent2);
    flex-shrink: 0;
  }

  /* === WHAT I DO === */
  .do-list {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }
  @media (max-width: 500px) { .do-list { grid-template-columns: 1fr; } }

  .do-item {
    display: flex;
    align-items: flex-start;
    gap: 12px;
    padding: 16px;
    border-radius: 10px;
    border: 1px solid var(--border);
    background: var(--surface);
    font-size: 0.88rem;
    color: #b0adc5;
    line-height: 1.4;
    transition: border-color 0.2s, background 0.2s;
  }
  .do-item:hover {
    border-color: var(--accent);
    background: rgba(124,106,247,0.05);
  }
  .do-item .icon {
    font-size: 1.1rem;
    flex-shrink: 0;
    margin-top: 1px;
  }

  /* === CONTACT === */
  .contact-list {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .contact-item {
    display: flex;
    align-items: center;
    gap: 14px;
    padding: 14px 18px;
    border-radius: 10px;
    border: 1px solid var(--border);
    background: var(--surface);
    text-decoration: none;
    color: var(--text);
    font-size: 0.88rem;
    transition: all 0.2s ease;
  }
  .contact-item:hover {
    transform: translateX(4px);
    border-color: var(--accent);
    background: rgba(124,106,247,0.06);
  }
  .contact-item .ci-icon { font-size: 1.1rem; }
  .contact-item .ci-label {
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    color: var(--muted);
    margin-right: auto;
    letter-spacing: 0.04em;
  }
  .contact-item .ci-value { color: #b0adc5; }
  .contact-item .ci-arrow {
    color: var(--accent);
    font-size: 0.85rem;
    opacity: 0;
    transition: opacity 0.2s, transform 0.2s;
    transform: translateX(-4px);
  }
  .contact-item:hover .ci-arrow { opacity: 1; transform: translateX(0); }

  /* === FOOTER === */
  .footer {
    text-align: center;
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    color: var(--muted);
    margin-top: 64px;
    opacity: 0;
    animation: fadeUp 0.7s ease forwards 1.1s;
  }
  .footer span { color: var(--accent); }

  /* === ANIMATIONS === */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* === TYPING CURSOR === */
  .cursor {
    display: inline-block;
    width: 2px; height: 1em;
    background: var(--accent2);
    margin-left: 2px;
    vertical-align: middle;
    animation: blink 1s step-end infinite;
  }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

  /* === STATUS DOT === */
  .status {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    color: var(--accent2);
    margin-bottom: 20px;
  }
  .status-dot {
    width: 8px; height: 8px;
    border-radius: 50%;
    background: var(--accent2);
    animation: pulse 2s ease infinite;
  }
  @keyframes pulse {
    0%,100% { box-shadow: 0 0 0 0 rgba(56,217,169,0.4); }
    50%      { box-shadow: 0 0 0 6px rgba(56,217,169,0); }
  }
</style>
</head>
<body>

<div class="orb orb-1"></div>
<div class="orb orb-2"></div>
<div class="orb orb-3"></div>

<div class="wrapper">

  <!-- HERO -->
  <div class="hero">
    <div class="avatar-ring">
      <span class="avatar-inner">👋</span>
    </div>

    <div class="status">
      <span class="status-dot"></span>
      Available for new opportunities
    </div>

    <h1>Hi, I'm John Ngethe</h1>
    <p>Building reliable, user-friendly systems that solve real problems<span class="cursor"></span></p>

    <div class="badges">
      <a class="badge badge-linkedin" href="https://www.linkedin.com/in/johnngethe307" target="_blank">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
        LinkedIn
      </a>
      <a class="badge badge-email" href="mailto:johngethe77@yahoo.com">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 01-2.06 0L2 7"/></svg>
        Email
      </a>
      <a class="badge badge-github" href="https://github.com/JohnNgethe" target="_blank">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.374 0 0 5.373 0 12c0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23A11.509 11.509 0 0112 5.803c1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576C20.566 21.797 24 17.3 24 12c0-6.627-5.373-12-12-12z"/></svg>
        GitHub
      </a>
    </div>
  </div>

  <div class="divider"></div>

  <!-- ABOUT -->
  <div class="section">
    <div class="section-label">01 — About</div>
    <div class="section-title">Who I Am</div>
    <p>I'm a software developer focused on designing, developing, and maintaining web applications that are efficient, reliable, and easy to use. I enjoy solving real-world problems and building practical technology solutions that support the people who use them every day.</p>
  </div>

  <div class="divider"></div>

  <!-- TECH STACK -->
  <div class="section">
    <div class="section-label">02 — Stack</div>
    <div class="section-title">Tech I Work With</div>
    <div class="tech-grid">
      <span class="tech-pill"><span class="dot"></span>C# / ASP.NET</span>
      <span class="tech-pill"><span class="dot"></span>JavaScript</span>
      <span class="tech-pill"><span class="dot"></span>Next.js</span>
      <span class="tech-pill"><span class="dot"></span>Node.js</span>
      <span class="tech-pill"><span class="dot"></span>Bootstrap</span>
      <span class="tech-pill"><span class="dot"></span>SQL Server</span>
      <span class="tech-pill"><span class="dot"></span>MySQL</span>
      <span class="tech-pill"><span class="dot"></span>PostgreSQL</span>
      <span class="tech-pill"><span class="dot"></span>Entity Framework</span>
      <span class="tech-pill"><span class="dot"></span>Dynamics NAV</span>
      <span class="tech-pill"><span class="dot"></span>Vercel</span>
      <span class="tech-pill"><span class="dot"></span>Supabase</span>
    </div>
  </div>

  <div class="divider"></div>

  <!-- WHAT I DO -->
  <div class="section">
    <div class="section-label">03 — Services</div>
    <div class="section-title">What I Do</div>
    <div class="do-list">
      <div class="do-item"><span class="icon">🌐</span>Web application development</div>
      <div class="do-item"><span class="icon">🔧</span>System support & maintenance</div>
      <div class="do-item"><span class="icon">📈</span>Business process improvement</div>
      <div class="do-item"><span class="icon">🐛</span>Troubleshooting & issue resolution</div>
    </div>
  </div>

  <div class="divider"></div>

  <!-- CONTACT -->
  <div class="section">
    <div class="section-label">04 — Contact</div>
    <div class="section-title">Get In Touch</div>
    <div class="contact-list">
      <a class="contact-item" href="mailto:johngethe77@yahoo.com">
        <span class="ci-icon">📧</span>
        <span class="ci-label">EMAIL</span>
        <span class="ci-value">johngethe77@yahoo.com</span>
        <span class="ci-arrow">→</span>
      </a>
      <a class="contact-item" href="https://www.linkedin.com/in/johnngethe307" target="_blank">
        <span class="ci-icon">🔗</span>
        <span class="ci-label">LINKEDIN</span>
        <span class="ci-value">linkedin.com/in/johnngethe307</span>
        <span class="ci-arrow">→</span>
      </a>
      <a class="contact-item" href="https://github.com/JohnNgethe" target="_blank">
        <span class="ci-icon">💻</span>
        <span class="ci-label">GITHUB</span>
        <span class="ci-value">github.com/JohnNgethe</span>
        <span class="ci-arrow">→</span>
      </a>
    </div>
  </div>

  <div class="footer">
    crafted with <span>♥</span> · john ngethe · <span>2025</span>
  </div>

</div>
</body>
</html>
