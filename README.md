<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ahnaf Fauzan — Developer Profile</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;600;700&family=Syne:wght@400;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0e17;
    --bg2: #0f1521;
    --surface: #141c2e;
    --surface2: #1a2540;
    --border: #1e2d4a;
    --accent: #00d4ff;
    --accent2: #7c5cfc;
    --accent3: #00ff9d;
    --text: #e2e8f0;
    --muted: #64748b;
    --glow: 0 0 20px rgba(0,212,255,0.15);
  }
  * { margin: 0; padding: 0; box-sizing: border-box; }
  
  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'JetBrains Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Animated background grid */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: 
      linear-gradient(rgba(0,212,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,212,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .container {
    max-width: 860px;
    margin: 0 auto;
    padding: 60px 24px;
    position: relative;
    z-index: 1;
  }

  /* ── HERO ── */
  .hero {
    display: flex;
    align-items: center;
    gap: 32px;
    margin-bottom: 56px;
    animation: fadeUp 0.8s ease both;
  }
  .avatar-wrap {
    position: relative;
    flex-shrink: 0;
  }
  .avatar-ring {
    width: 96px; height: 96px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--accent), var(--accent2), var(--accent3));
    padding: 2px;
    animation: spin 8s linear infinite;
  }
  .avatar-inner {
    width: 100%; height: 100%;
    border-radius: 50%;
    background: var(--bg);
    display: flex; align-items: center; justify-content: center;
    font-size: 2.5rem;
    overflow: hidden;
  }
  .avatar-inner img {
    width: 100%; height: 100%;
    object-fit: cover;
    border-radius: 50%;
  }
  @keyframes spin {
    to { transform: rotate(360deg); }
  }
  .status-dot {
    position: absolute;
    bottom: 4px; right: 4px;
    width: 14px; height: 14px;
    background: var(--accent3);
    border-radius: 50%;
    border: 2px solid var(--bg);
    box-shadow: 0 0 8px var(--accent3);
    animation: pulse 2s ease infinite;
  }
  @keyframes pulse {
    0%,100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.6; transform: scale(0.85); }
  }
  .hero-text h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(1.6rem, 4vw, 2.2rem);
    font-weight: 800;
    line-height: 1.1;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .hero-text .tagline {
    color: var(--muted);
    font-size: 0.78rem;
    margin-top: 6px;
    letter-spacing: 0.08em;
    text-transform: uppercase;
  }
  .typing-wrap {
    margin-top: 12px;
    font-size: 0.9rem;
    color: var(--accent3);
    min-height: 1.4em;
  }
  .cursor {
    display: inline-block;
    width: 2px; height: 1em;
    background: var(--accent3);
    vertical-align: text-bottom;
    animation: blink 1s step-end infinite;
  }
  @keyframes blink { 50% { opacity: 0; } }

  /* ── SECTIONS ── */
  .section {
    margin-bottom: 48px;
    animation: fadeUp 0.8s ease both;
  }
  .section-header {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 20px;
  }
  .section-header svg { flex-shrink: 0; }
  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: 1rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.12em;
    color: var(--text);
  }
  .section-line {
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }

  /* ── ABOUT CARDS ── */
  .about-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 10px;
  }
  .about-item {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 12px 16px;
    display: flex;
    align-items: flex-start;
    gap: 10px;
    font-size: 0.8rem;
    color: var(--text);
    transition: border-color 0.2s, transform 0.2s, box-shadow 0.2s;
    cursor: default;
  }
  .about-item:hover {
    border-color: var(--accent);
    transform: translateY(-2px);
    box-shadow: var(--glow);
  }
  .about-icon { color: var(--accent); flex-shrink: 0; margin-top: 1px; }
  .about-label { color: var(--muted); font-size: 0.7rem; display: block; margin-bottom: 2px; }

  /* ── TECH STACK ── */
  .tech-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }
  .tech-chip {
    display: flex;
    align-items: center;
    gap: 8px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 7px 14px;
    font-size: 0.78rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.25s;
    text-decoration: none;
    color: var(--text);
  }
  .tech-chip img { width: 18px; height: 18px; object-fit: contain; }
  .tech-chip:hover {
    border-color: var(--accent);
    box-shadow: var(--glow);
    transform: translateY(-2px);
    color: var(--accent);
  }

  /* ── GITHUB STATS ── */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
    gap: 12px;
    margin-bottom: 16px;
  }
  .stat-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 18px 16px;
    text-align: center;
    transition: all 0.25s;
    cursor: default;
  }
  .stat-card:hover {
    border-color: var(--accent2);
    box-shadow: 0 0 20px rgba(124,92,252,0.15);
    transform: translateY(-3px);
  }
  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 1.8rem;
    font-weight: 800;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    line-height: 1;
  }
  .stat-label {
    color: var(--muted);
    font-size: 0.7rem;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    margin-top: 4px;
  }
  .github-images {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }
  .github-images img {
    width: 100%;
    border-radius: 10px;
    border: 1px solid var(--border);
    transition: border-color 0.2s, box-shadow 0.2s;
  }
  .github-images img:hover {
    border-color: var(--accent);
    box-shadow: var(--glow);
  }

  /* ── CONTACT ── */
  .contact-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }
  .contact-btn {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 10px 18px;
    border-radius: 8px;
    text-decoration: none;
    font-size: 0.8rem;
    font-weight: 600;
    border: 1px solid transparent;
    transition: all 0.25s;
    letter-spacing: 0.04em;
  }
  .contact-btn img { width: 18px; height: 18px; object-fit: contain; filter: brightness(10); }
  .contact-btn.linkedin { background: #0077b5; color: #fff; }
  .contact-btn.github   { background: #24292e; color: #fff; border-color: #444; }
  .contact-btn.email    { background: #d14836; color: #fff; }
  .contact-btn:hover { transform: translateY(-2px); opacity: 0.88; box-shadow: 0 4px 16px rgba(0,0,0,0.3); }

  /* ── QUOTE ── */
  .quote-block {
    background: var(--surface);
    border: 1px solid var(--border);
    border-left: 3px solid var(--accent);
    border-radius: 0 8px 8px 0;
    padding: 18px 20px;
    font-size: 0.85rem;
    color: var(--text);
    line-height: 1.6;
    position: relative;
  }
  .quote-block::before {
    content: '"';
    position: absolute;
    top: -8px; left: 12px;
    font-size: 3rem;
    color: var(--accent);
    opacity: 0.3;
    font-family: Georgia, serif;
    line-height: 1;
  }

  /* ── STAR CTA ── */
  .star-cta {
    text-align: center;
    margin-top: 48px;
    padding: 28px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
  }
  .star-cta p { color: var(--muted); font-size: 0.78rem; margin-top: 8px; }
  .star-btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 12px 28px;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    border-radius: 8px;
    color: #000;
    font-weight: 700;
    font-size: 0.85rem;
    text-decoration: none;
    transition: all 0.25s;
    letter-spacing: 0.04em;
  }
  .star-btn:hover { transform: scale(1.05); box-shadow: 0 4px 24px rgba(0,212,255,0.3); }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  .section:nth-child(1) { animation-delay: 0.1s; }
  .section:nth-child(2) { animation-delay: 0.2s; }
  .section:nth-child(3) { animation-delay: 0.3s; }
  .section:nth-child(4) { animation-delay: 0.4s; }
  .section:nth-child(5) { animation-delay: 0.5s; }

  @media (max-width: 560px) {
    .hero { flex-direction: column; text-align: center; }
    .avatar-wrap { margin: 0 auto; }
  }
</style>
</head>
<body>
<div class="container">

  <!-- HERO -->
  <div class="hero">
    <div class="avatar-wrap">
      <div class="avatar-ring">
        <div class="avatar-inner">
          <!-- Ganti src dengan URL foto kamu, atau hapus tag img jika tidak ada -->
          <img src="https://avatars.githubusercontent.com/ahnafojan" alt="Ahnaf Fauzan"
               onerror="this.parentElement.innerHTML='AF'">
        </div>
      </div>
      <div class="status-dot" title="Available for collaboration"></div>
    </div>
    <div class="hero-text">
      <h1>Halo, Saya Ahnaf Fauzan!</h1>
      <div class="tagline">Web &amp; Android Developer · Indonesia</div>
      <div class="typing-wrap">
        <span id="typed"></span><span class="cursor"></span>
      </div>
    </div>
  </div>

  <!-- ABOUT -->
  <div class="section">
    <div class="section-header">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="var(--accent)" stroke-width="2"><circle cx="12" cy="8" r="4"/><path d="M4 20c0-4 3.6-7 8-7s8 3 8 7"/></svg>
      <span class="section-title">Tentang Saya</span>
      <div class="section-line"></div>
    </div>
    <div class="about-grid">
      <div class="about-item">
        <span class="about-icon">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12"/><line x1="12" y1="16" x2="12.01" y2="16"/></svg>
        </span>
        <div>
          <span class="about-label">Fokus Saat Ini</span>
          Mengembangkan skill <strong>Web</strong> &amp; <strong>Android Development</strong>
        </div>
      </div>
      <div class="about-item">
        <span class="about-icon">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 2L2 7l10 5 10-5-10-5z"/><path d="M2 17l10 5 10-5"/><path d="M2 12l10 5 10-5"/></svg>
        </span>
        <div>
          <span class="about-label">Belajar</span>
          Teknologi terbaru &amp; best practices
        </div>
      </div>
      <div class="about-item">
        <span class="about-icon">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>
        </span>
        <div>
          <span class="about-label">Kolaborasi</span>
          Terbuka untuk proyek-proyek menarik
        </div>
      </div>
      <div class="about-item">
        <span class="about-icon">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/></svg>
        </span>
        <div>
          <span class="about-label">Diskusi</span>
          Tanya tentang <strong>programming</strong> atau teknologi
        </div>
      </div>
      <div class="about-item">
        <span class="about-icon">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="16 18 22 12 16 6"/><polyline points="8 6 2 12 8 18"/></svg>
        </span>
        <div>
          <span class="about-label">Fun Fact</span>
          Code yang baik = code yang mudah dibaca
        </div>
      </div>
    </div>
  </div>

  <!-- TECH STACK -->
  <div class="section">
    <div class="section-header">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="var(--accent)" stroke-width="2"><path d="M14.7 6.3a1 1 0 0 0 0 1.4l1.6 1.6a1 1 0 0 0 1.4 0l3.77-3.77a6 6 0 0 1-7.94 7.94l-6.91 6.91a2.12 2.12 0 0 1-3-3l6.91-6.91a6 6 0 0 1 7.94-7.94l-3.76 3.76z"/></svg>
      <span class="section-title">Tech Stack</span>
      <div class="section-line"></div>
    </div>
    <div class="tech-grid">
      <a class="tech-chip" href="https://developer.mozilla.org/en-US/docs/Web/JavaScript" target="_blank">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" alt="JavaScript"> JavaScript
      </a>
      <a class="tech-chip" href="https://www.python.org" target="_blank">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" alt="Python"> Python
      </a>
      <a class="tech-chip" href="https://www.php.net" target="_blank">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" alt="PHP"> PHP
      </a>
      <a class="tech-chip" href="https://kotlinlang.org" target="_blank">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/kotlin/kotlin-original.svg" alt="Kotlin"> Kotlin
      </a>
      <a class="tech-chip" href="https://developer.mozilla.org/en-US/docs/Web/HTML" target="_blank">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" alt="HTML5"> HTML5
      </a>
      <a class="tech-chip" href="https://developer.mozilla.org/en-US/docs/Web/CSS" target="_blank">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" alt="CSS3"> CSS3
      </a>
      <a class="tech-chip" href="https://reactjs.org" target="_blank">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" alt="React"> React
      </a>
      <a class="tech-chip" href="https://nodejs.org" target="_blank">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" alt="Node.js"> Node.js
      </a>
      <a class="tech-chip" href="https://git-scm.com" target="_blank">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" alt="Git"> Git
      </a>
    </div>
  </div>

  <!-- GITHUB STATS -->
  <div class="section">
    <div class="section-header">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="var(--accent)" stroke-width="2"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>
      <span class="section-title">GitHub Statistics</span>
      <div class="section-line"></div>
    </div>
    <div class="github-images">
      <img src="https://github-readme-stats.vercel.app/api?username=ahnafojan&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0f1521&title_color=00d4ff&icon_color=7c5cfc&text_color=e2e8f0&rank_icon=github" alt="GitHub Stats">
      <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=ahnafojan&layout=compact&theme=tokyonight&hide_border=true&bg_color=0f1521&title_color=00d4ff&text_color=e2e8f0" alt="Top Languages">
      <img src="https://github-readme-streak-stats.herokuapp.com/?user=ahnafojan&theme=tokyonight&hide_border=true&background=0f1521&ring=00d4ff&fire=7c5cfc&currStreakLabel=00ff9d" alt="GitHub Streak">
    </div>
  </div>

  <!-- TROPHIES -->
  <div class="section">
    <div class="section-header">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="var(--accent)" stroke-width="2"><path d="M6 9H4.5a2.5 2.5 0 0 1 0-5H6"/><path d="M18 9h1.5a2.5 2.5 0 0 0 0-5H18"/><path d="M4 22h16"/><path d="M10 14.66V17c0 .55-.47.98-.97 1.21C7.85 18.75 7 20.24 7 22"/><path d="M14 14.66V17c0 .55.47.98.97 1.21C16.15 18.75 17 20.24 17 22"/><path d="M18 2H6v7a6 6 0 0 0 12 0V2z"/></svg>
      <span class="section-title">GitHub Trophies</span>
      <div class="section-line"></div>
    </div>
    <img src="https://github-profile-trophy.vercel.app/?username=ahnafojan&theme=darkhub&no-frame=true&row=1&column=7&margin-w=4&margin-h=4" alt="Trophies" style="width:100%;border-radius:10px;border:1px solid var(--border);">
  </div>

  <!-- CONTRIBUTION ACTIVITY -->
  <div class="section">
    <div class="section-header">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="var(--accent)" stroke-width="2"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>
      <span class="section-title">Contribution Activity</span>
      <div class="section-line"></div>
    </div>
    <img src="https://github-readme-activity-graph.vercel.app/graph?username=ahnafojan&bg_color=0f1521&color=00d4ff&line=7c5cfc&point=00ff9d&area=true&hide_border=true" alt="Activity Graph" style="width:100%;border-radius:10px;border:1px solid var(--border);">
  </div>

  <!-- CONNECT -->
  <div class="section">
    <div class="section-header">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="var(--accent)" stroke-width="2"><path d="M18 8h1a4 4 0 0 1 0 8h-1"/><path d="M2 8h16v9a4 4 0 0 1-4 4H6a4 4 0 0 1-4-4V8z"/><line x1="6" y1="1" x2="6" y2="4"/><line x1="10" y1="1" x2="10" y2="4"/><line x1="14" y1="1" x2="14" y2="4"/></svg>
      <span class="section-title">Mari Terhubung</span>
      <div class="section-line"></div>
    </div>
    <div class="contact-grid">
      <a class="contact-btn linkedin" href="https://www.linkedin.com/in/ahnaf-fauzan-31553a299" target="_blank">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linkedin/linkedin-original.svg" alt="LinkedIn"> LinkedIn
      </a>
      <a class="contact-btn github" href="https://github.com/ahnafojan" target="_blank">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="white"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.3 3.44 9.8 8.2 11.38.6.1.82-.26.82-.58l-.01-2.24c-3.34.72-4.04-1.43-4.04-1.43-.55-1.38-1.33-1.75-1.33-1.75-1.09-.74.08-.73.08-.73 1.2.08 1.83 1.23 1.83 1.23 1.07 1.83 2.8 1.3 3.49 1 .1-.78.42-1.3.76-1.6-2.67-.3-5.47-1.33-5.47-5.93 0-1.31.47-2.38 1.24-3.22-.13-.3-.54-1.52.12-3.17 0 0 1.01-.32 3.3 1.23a11.5 11.5 0 0 1 3-.4c1.02 0 2.04.13 3 .4 2.28-1.55 3.29-1.23 3.29-1.23.66 1.65.25 2.87.12 3.17.77.84 1.24 1.91 1.24 3.22 0 4.61-2.81 5.63-5.48 5.92.43.37.81 1.1.81 2.22l-.01 3.29c0 .32.21.69.82.57C20.56 21.8 24 17.3 24 12c0-6.63-5.37-12-12-12z"/></svg>
        GitHub
      </a>
      <a class="contact-btn email" href="mailto:your.email@example.com" target="_blank">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
        Email
      </a>
    </div>
  </div>

  <!-- QUOTE -->
  <div class="quote-block">
    Coding is not just about writing code — it's about solving problems and creating impact!
  </div>

  <!-- STAR CTA -->
  <div class="star-cta">
    <a class="star-btn" href="https://github.com/ahnafojan" target="_blank">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg>
      Star Repository
    </a>
    <p>Jika kamu menyukai repository saya, berikan bintang ya!</p>
  </div>

</div>

<script>
  // Typing animation
  const phrases = [
    'Passionate Web Developer',
    'Android Enthusiast',
    'Problem Solver',
    'Open Source Contributor',
    'Lifelong Learner',
  ];
  let pi = 0, ci = 0, deleting = false;
  const el = document.getElementById('typed');
  function type() {
    const word = phrases[pi];
    if (!deleting) {
      el.textContent = word.slice(0, ++ci);
      if (ci === word.length) { deleting = true; setTimeout(type, 1800); return; }
    } else {
      el.textContent = word.slice(0, --ci);
      if (ci === 0) { deleting = false; pi = (pi + 1) % phrases.length; }
    }
    setTimeout(type, deleting ? 55 : 90);
  }
  type();

  // Scroll reveal
  const obs = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.style.opacity = '1';
        e.target.style.transform = 'translateY(0)';
      }
    });
  }, { threshold: 0.1 });
  document.querySelectorAll('.section').forEach(s => {
    s.style.opacity = '0';
    s.style.transform = 'translateY(24px)';
    s.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
    obs.observe(s);
  });
</script>
</body>
</html>
