<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Hamed Mohamed | AI Automation Engineer</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:ital,wght@0,300;0,400;0,500;1,400&family=DM+Sans:ital,wght@0,300;0,400;0,500;0,600;1,400&display=swap" rel="stylesheet" />
  <style>
    :root {
      --bg: #080a0d;
      --surface: #0e1117;
      --card: #111620;
      --border: #1c2333;
      --border-light: #252d40;
      --accent: #4fffb0;
      --accent-dim: rgba(79,255,176,0.10);
      --accent-glow: rgba(79,255,176,0.22);
      --blue: #5ba4ff;
      --text: #dde4f0;
      --muted: #5d6b85;
      --sub: #8796b2;
    }
    * { margin: 0; padding: 0; box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body { background: var(--bg); color: var(--text); font-family: 'DM Sans', sans-serif; font-size: 15px; line-height: 1.7; overflow-x: hidden; }

    /* NAV */
    nav { position: fixed; top: 0; left: 0; right: 0; z-index: 200; display: flex; align-items: center; justify-content: space-between; padding: 18px 48px; background: rgba(8,10,13,0.9); backdrop-filter: blur(24px); border-bottom: 1px solid var(--border); }
    .nav-logo { font-family: 'Syne', sans-serif; font-weight: 800; font-size: 17px; color: var(--accent); text-decoration: none; letter-spacing: -0.3px; }
    .nav-links { display: flex; gap: 28px; align-items: center; }
    .nav-links a { color: var(--muted); text-decoration: none; font-size: 13px; transition: color 0.2s; }
    .nav-links a:hover { color: var(--text); }
    .nav-cta { padding: 8px 20px; border: 1px solid var(--accent) !important; border-radius: 4px; color: var(--accent) !important; font-size: 12px !important; letter-spacing: 0.06em; text-transform: uppercase; transition: all 0.2s !important; }
    .nav-cta:hover { background: var(--accent) !important; color: #000 !important; }

    /* HERO */
    .hero { min-height: 100vh; display: grid; grid-template-columns: 1fr 320px; align-items: center; gap: 60px; max-width: 1140px; margin: 0 auto; padding: 130px 40px 80px; }
    .hero-badge { display: inline-flex; align-items: center; gap: 8px; font-family: 'DM Mono', monospace; font-size: 11px; letter-spacing: 0.14em; text-transform: uppercase; color: var(--accent); margin-bottom: 24px; opacity: 0; animation: rise 0.6s 0.1s forwards; }
    .hero-badge::before { content: ''; display: block; width: 20px; height: 1px; background: var(--accent); }
    h1 { font-family: 'Syne', sans-serif; font-weight: 800; font-size: clamp(44px, 5.5vw, 76px); line-height: 1.0; letter-spacing: -2.5px; margin-bottom: 20px; opacity: 0; animation: rise 0.7s 0.25s forwards; }
    h1 em { color: var(--accent); font-style: normal; }
    .hero-desc { font-size: 15px; color: var(--sub); max-width: 520px; line-height: 1.85; margin-bottom: 36px; opacity: 0; animation: rise 0.7s 0.4s forwards; }

    .hero-contacts { display: flex; flex-wrap: wrap; gap: 10px; margin-bottom: 32px; opacity: 0; animation: rise 0.7s 0.5s forwards; }
    .contact-pill { display: inline-flex; align-items: center; gap: 6px; padding: 7px 14px; border-radius: 100px; background: var(--card); border: 1px solid var(--border-light); font-family: 'DM Mono', monospace; font-size: 11px; color: var(--sub); text-decoration: none; transition: all 0.2s; }
    .contact-pill:hover { border-color: var(--accent); color: var(--accent); }

    .hero-btns { display: flex; gap: 12px; flex-wrap: wrap; opacity: 0; animation: rise 0.7s 0.6s forwards; }
    .btn { display: inline-flex; align-items: center; gap: 8px; padding: 13px 26px; border-radius: 5px; font-family: 'DM Mono', monospace; font-size: 12px; letter-spacing: 0.07em; text-transform: uppercase; text-decoration: none; font-weight: 500; transition: all 0.22s; border: none; cursor: pointer; }
    .btn-primary { background: var(--accent); color: #000; }
    .btn-primary:hover { background: #72ffbf; transform: translateY(-2px); box-shadow: 0 8px 28px var(--accent-glow); }
    .btn-outline { background: transparent; color: var(--text); border: 1px solid var(--border-light); }
    .btn-outline:hover { border-color: var(--accent); color: var(--accent); transform: translateY(-2px); }

    /* PHOTO */
    .photo-zone { opacity: 0; animation: rise 0.8s 0.5s forwards; }
    .photo-frame { width: 280px; height: 280px; border-radius: 16px; background: var(--card); border: 2px dashed var(--border-light); display: flex; flex-direction: column; align-items: center; justify-content: center; cursor: pointer; overflow: hidden; transition: all 0.3s; position: relative; }
    .photo-frame:hover { border-color: var(--accent); background: rgba(79,255,176,0.03); }
    .photo-frame img { width: 100%; height: 100%; object-fit: cover; display: none; }
    .photo-frame img.show { display: block; }
    .photo-placeholder { text-align: center; padding: 20px; }
    .photo-placeholder .pi { font-size: 38px; margin-bottom: 10px; opacity: 0.35; }
    .photo-placeholder p { font-family: 'DM Mono', monospace; font-size: 10px; color: var(--muted); letter-spacing: 0.08em; line-height: 1.7; }
    .photo-placeholder.hidden { display: none; }
    .photo-change { position: absolute; inset: 0; background: rgba(8,10,13,0.75); display: none; align-items: center; justify-content: center; border-radius: 14px; }
    .photo-frame:hover .photo-change { display: flex; }
    .photo-change span { font-family: 'DM Mono', monospace; font-size: 11px; color: var(--accent); letter-spacing: 0.08em; text-transform: uppercase; }
    #photoInput { display: none; }
    .photo-hint { text-align: center; margin-top: 8px; font-family: 'DM Mono', monospace; font-size: 10px; color: var(--muted); letter-spacing: 0.08em; }

    /* BACKGROUND */
    .glow { position: fixed; border-radius: 50%; filter: blur(100px); pointer-events: none; z-index: -1; }
    .g1 { width: 500px; height: 500px; background: rgba(79,255,176,0.035); top: 0; right: -100px; animation: drift 10s ease-in-out infinite alternate; }
    .g2 { width: 350px; height: 350px; background: rgba(91,164,255,0.03); bottom: 200px; left: -80px; animation: drift 14s ease-in-out infinite alternate-reverse; }

    /* STATS */
    .stats-strip { background: var(--surface); border-top: 1px solid var(--border); border-bottom: 1px solid var(--border); }
    .stats-inner { max-width: 1140px; margin: 0 auto; padding: 32px 40px; display: grid; grid-template-columns: repeat(4, 1fr); }
    .stat { padding: 0 28px; border-right: 1px solid var(--border); }
    .stat:first-child { padding-left: 0; } .stat:last-child { border-right: none; }
    .stat-num { font-family: 'Syne', sans-serif; font-weight: 800; font-size: 38px; color: var(--accent); line-height: 1; margin-bottom: 4px; }
    .stat-lbl { font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); }

    /* SECTIONS */
    .section { max-width: 1140px; margin: 0 auto; padding: 80px 40px; }
    .section-head { display: flex; align-items: center; gap: 16px; margin-bottom: 52px; }
    .section-tag { font-family: 'DM Mono', monospace; font-size: 11px; letter-spacing: 0.14em; text-transform: uppercase; color: var(--accent); white-space: nowrap; }
    .section-rule { flex: 1; height: 1px; background: var(--border); }
    h2 { font-family: 'Syne', sans-serif; font-weight: 800; font-size: 36px; letter-spacing: -1px; margin-bottom: 12px; }

    /* SKILLS */
    .skills-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(178px, 1fr)); gap: 12px; }
    .skill-pill { background: var(--card); border: 1px solid var(--border); border-radius: 8px; padding: 18px 20px; transition: all 0.25s; }
    .skill-pill:hover { border-color: var(--border-light); transform: translateY(-3px); box-shadow: 0 12px 36px rgba(0,0,0,0.5); }
    .skill-pill .s-cat { font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.08em; text-transform: uppercase; color: var(--accent); margin-bottom: 5px; }
    .skill-pill .s-name { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 14px; }

    /* CERTS */
    .certs-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(255px, 1fr)); gap: 16px; }
    .cert-card { background: var(--card); border: 1px solid var(--border); border-radius: 10px; padding: 26px; transition: all 0.25s; position: relative; overflow: hidden; }
    .cert-card::after { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 2px; background: linear-gradient(90deg, var(--accent), transparent); transform: scaleX(0); transform-origin: left; transition: transform 0.3s; }
    .cert-card:hover::after { transform: scaleX(1); }
    .cert-card:hover { border-color: var(--border-light); transform: translateY(-3px); box-shadow: 0 16px 48px rgba(0,0,0,0.5); }
    .cert-icon { font-size: 28px; margin-bottom: 12px; }
    .cert-name { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 15px; margin-bottom: 6px; line-height: 1.35; }
    .cert-issuer { font-family: 'DM Mono', monospace; font-size: 11px; color: var(--accent); letter-spacing: 0.04em; }

    /* PROJECTS */
    .projects-bg { background: var(--surface); border-top: 1px solid var(--border); border-bottom: 1px solid var(--border); }
    .project-card { background: var(--card); border: 1px solid var(--border); border-radius: 12px; padding: 36px; margin-bottom: 24px; transition: border-color 0.25s, box-shadow 0.25s; display: grid; grid-template-columns: 1fr 340px; gap: 40px; align-items: start; }
    .project-card:hover { border-color: var(--border-light); box-shadow: 0 20px 60px rgba(0,0,0,0.5); }
    .project-card:last-child { margin-bottom: 0; }
    .proj-num { font-family: 'Syne', sans-serif; font-weight: 800; font-size: 52px; color: var(--border); line-height: 1; margin-bottom: 14px; transition: color 0.3s; }
    .project-card:hover .proj-num { color: var(--border-light); }
    .proj-title { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 19px; line-height: 1.3; margin-bottom: 12px; }
    .proj-desc { font-size: 14px; color: var(--sub); line-height: 1.85; margin-bottom: 20px; }
    .proj-tags { display: flex; flex-wrap: wrap; gap: 7px; margin-bottom: 20px; }
    .tag { padding: 4px 10px; border-radius: 3px; font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.07em; text-transform: uppercase; background: rgba(79,255,176,0.07); border: 1px solid rgba(79,255,176,0.18); color: var(--accent); }
    .tag-b { background: rgba(91,164,255,0.07); border-color: rgba(91,164,255,0.18); color: var(--blue); }
    .proj-link { color: var(--accent); text-decoration: none; font-family: 'DM Mono', monospace; font-size: 12px; display: inline-flex; align-items: center; gap: 6px; transition: gap 0.2s; }
    .proj-link:hover { gap: 12px; }

    /* VIDEO ZONE */
    .video-zone {}
    .video-frame { width: 100%; aspect-ratio: 16/9; border-radius: 10px; background: var(--bg); border: 2px dashed var(--border-light); display: flex; flex-direction: column; align-items: center; justify-content: center; overflow: hidden; transition: all 0.3s; position: relative; }
    .video-frame.clickable { cursor: pointer; }
    .video-frame.clickable:hover { border-color: var(--accent); background: rgba(79,255,176,0.03); }
    .vid-placeholder { text-align: center; padding: 16px; }
    .vid-icon { font-size: 36px; margin-bottom: 10px; opacity: 0.3; }
    .vid-text { font-family: 'DM Mono', monospace; font-size: 10px; color: var(--muted); letter-spacing: 0.08em; line-height: 1.7; text-transform: uppercase; }
    .video-frame iframe, .video-frame video { width: 100%; height: 100%; border: none; border-radius: 8px; object-fit: cover; }
    .loom-row { margin-top: 10px; display: flex; gap: 8px; }
    .loom-input { flex: 1; padding: 9px 13px; background: var(--bg); border: 1px solid var(--border-light); border-radius: 5px; color: var(--text); font-family: 'DM Mono', monospace; font-size: 11px; outline: none; transition: border-color 0.2s; }
    .loom-input::placeholder { color: var(--muted); }
    .loom-input:focus { border-color: var(--accent); }
    .loom-btn { padding: 9px 13px; background: var(--accent); border: none; border-radius: 5px; color: #000; font-family: 'DM Mono', monospace; font-size: 11px; font-weight: 600; cursor: pointer; transition: background 0.2s; display: inline-flex; align-items: center; }
    .loom-btn:hover { background: #72ffbf; }
    .vid-file-inp { display: none; }

    /* EDUCATION */
    .edu-card { background: var(--card); border: 1px solid var(--border); border-radius: 12px; padding: 32px; display: flex; align-items: center; gap: 28px; }
    .edu-icon { font-size: 48px; }
    .edu-degree { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 18px; margin-bottom: 6px; }
    .edu-school { font-size: 15px; color: var(--sub); margin-bottom: 4px; }
    .edu-detail { font-family: 'DM Mono', monospace; font-size: 12px; color: var(--accent); }

    /* RECOMMENDATIONS */
    .rec-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 16px; }
    .rec-card { background: var(--card); border: 1px solid var(--border); border-radius: 10px; padding: 26px; transition: all 0.25s; }
    .rec-card:hover { border-color: var(--border-light); transform: translateY(-2px); }
    .rec-num { font-family: 'Syne', sans-serif; font-weight: 800; font-size: 32px; color: var(--border-light); line-height: 1; margin-bottom: 10px; }
    .rec-title { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 15px; margin-bottom: 8px; }
    .rec-body { font-size: 13px; color: var(--sub); line-height: 1.75; }
    .rec-badge { display: inline-block; margin-top: 12px; padding: 3px 10px; background: var(--accent-dim); border: 1px solid rgba(79,255,176,0.2); border-radius: 3px; font-family: 'DM Mono', monospace; font-size: 10px; color: var(--accent); letter-spacing: 0.07em; text-transform: uppercase; }

    /* CTA */
    .cta-wrap { background: var(--card); border-top: 1px solid var(--border); border-bottom: 1px solid var(--border); }
    .cta-inner { max-width: 1140px; margin: 0 auto; padding: 80px 40px; display: flex; justify-content: space-between; align-items: center; gap: 40px; flex-wrap: wrap; }
    .cta-text h2 { font-size: 44px; margin-bottom: 10px; }
    .cta-text p { color: var(--sub); font-size: 15px; }
    .cta-actions { display: flex; gap: 14px; flex-wrap: wrap; }

    footer { max-width: 1140px; margin: 0 auto; padding: 36px 40px; display: flex; justify-content: space-between; align-items: center; border-top: 1px solid var(--border); }
    .foot-left { font-family: 'DM Mono', monospace; font-size: 12px; color: var(--muted); }
    .foot-links { display: flex; gap: 20px; }
    .foot-links a { color: var(--muted); text-decoration: none; font-family: 'DM Mono', monospace; font-size: 12px; transition: color 0.2s; }
    .foot-links a:hover { color: var(--accent); }

    @keyframes rise { from { opacity: 0; transform: translateY(22px); } to { opacity: 1; transform: translateY(0); } }
    @keyframes drift { from { transform: translate(0,0); } to { transform: translate(20px,30px); } }
    ::-webkit-scrollbar { width: 4px; }
    ::-webkit-scrollbar-track { background: var(--bg); }
    ::-webkit-scrollbar-thumb { background: var(--border-light); border-radius: 2px; }
    ::-webkit-scrollbar-thumb:hover { background: var(--accent); }

    @media (max-width: 900px) {
      nav { padding: 16px 20px; }
      .nav-links { display: none; }
      .hero { grid-template-columns: 1fr; gap: 36px; padding: 110px 20px 60px; }
      h1 { font-size: 42px; letter-spacing: -1.5px; }
      .photo-frame { width: 200px; height: 200px; }
      .stats-inner { grid-template-columns: repeat(2,1fr); gap: 28px; padding: 28px 20px; }
      .stat { border-right: none; padding: 0; }
      .section { padding: 60px 20px; }
      .project-card { grid-template-columns: 1fr; }
      .cta-inner { flex-direction: column; }
      footer { flex-direction: column; gap: 16px; text-align: center; }
    }
  </style>
</head>
<body>

<div class="glow g1"></div>
<div class="glow g2"></div>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">HM.</a>
  <div class="nav-links">
    <a href="#skills">Skills</a>
    <a href="#certs">Certs</a>
    <a href="#projects">Projects</a>
    <a href="#edu">Education</a>
    <a href="#contact" class="nav-cta">Hire Me</a>
  </div>
</nav>

<!-- HERO -->
<div class="hero">
  <div>
    <div class="hero-badge">Available · Giza, Egypt · Working globally</div>
    <h1>AI Automation<br/><em>Engineer</em>.</h1>
    <p class="hero-desc">I build intelligent automation systems with n8n, Make, Python & AI — connecting your tools, eliminating manual work, and scaling your operations without bloated costs.</p>

    <div class="hero-contacts">
      <a href="mailto:hamedmahamed00@gmail.com" class="contact-pill">✉ hamedmahamed00@gmail.com</a>
      <a href="https://wa.me/201159077093" target="_blank" class="contact-pill">💬 +20 115 907 7093</a>
      <a href="http://www.linkedin.com/in/hamed-mohamed-812b4b230" target="_blank" class="contact-pill">🔗 LinkedIn</a>
      <a href="https://www.upwork.com/freelancers/~017146fe881c329b56" target="_blank" class="contact-pill">💼 Upwork</a>
    </div>

    <div class="hero-btns">
      <a href="https://www.upwork.com/freelancers/~017146fe881c329b56" target="_blank" class="btn btn-primary">↗ Hire on Upwork</a>
      <a href="#projects" class="btn btn-outline">View Projects →</a>
    </div>
  </div>

  <!-- PHOTO UPLOAD -->
  <div class="photo-zone">
    <div class="photo-frame" id="photoFrame" onclick="document.getElementById('photoInput').click()">
      <img id="photoImg" alt="Hamed Mohamed" />
      <div class="photo-placeholder" id="photoPH">
        <div class="pi">📷</div>
        <p>Click to upload<br/>your photo</p>
      </div>
      <div class="photo-change"><span>Change Photo</span></div>
    </div>
    <input type="file" id="photoInput" accept="image/*" />
    <p class="photo-hint">CLICK TO ADD PHOTO</p>
  </div>
</div>

<!-- STATS -->
<div class="stats-strip">
  <div class="stats-inner">
    <div class="stat"><div class="stat-num">100%</div><div class="stat-lbl">Job Success</div></div>
    <div class="stat"><div class="stat-num">4+</div><div class="stat-lbl">Projects Built</div></div>
    <div class="stat"><div class="stat-num">4d</div><div class="stat-lbl">Avg Delivery</div></div>
    <div class="stat"><div class="stat-num">4</div><div class="stat-lbl">Certifications</div></div>
  </div>
</div>

<!-- SKILLS -->
<div class="section" id="skills">
  <div class="section-head"><span class="section-tag">// 01 — Skills</span><div class="section-rule"></div></div>
  <h2>What I Work With</h2>
  <p style="color:var(--sub);margin-bottom:40px;font-size:14px;max-width:520px;line-height:1.85;">From self-hosted n8n instances to Python scripts, VBA macros, and AI prompt chains — I use the right tool for every problem.</p>
  <div class="skills-grid">
    <div class="skill-pill"><div class="s-cat">Automation</div><div class="s-name">n8n</div></div>
    <div class="skill-pill"><div class="s-cat">Automation</div><div class="s-name">Make (Integromat)</div></div>
    <div class="skill-pill"><div class="s-cat">Integration</div><div class="s-name">API Integration</div></div>
    <div class="skill-pill"><div class="s-cat">Programming</div><div class="s-name">Python</div></div>
    <div class="skill-pill"><div class="s-cat">Office Automation</div><div class="s-name">VBA Excel</div></div>
    <div class="skill-pill"><div class="s-cat">Platform</div><div class="s-name">Antigravity</div></div>
    <div class="skill-pill"><div class="s-cat">AI</div><div class="s-name">Prompt Integration</div></div>
    <div class="skill-pill"><div class="s-cat">Data & Cloud</div><div class="s-name">Google Workspace</div></div>
    <div class="skill-pill"><div class="s-cat">CMS & Forms</div><div class="s-name">WordPress + CFF</div></div>
    <div class="skill-pill"><div class="s-cat">Webhooks</div><div class="s-name">REST APIs</div></div>
    <div class="skill-pill"><div class="s-cat">AI Agents</div><div class="s-name">LLM Orchestration</div></div>
    <div class="skill-pill"><div class="s-cat">File Transfer</div><div class="s-name">HTTP Streaming</div></div>
  </div>
</div>

<!-- CERTIFICATIONS -->
<div style="background:var(--surface);border-top:1px solid var(--border);border-bottom:1px solid var(--border);">
  <div class="section" id="certs">
    <div class="section-head"><span class="section-tag">// 02 — Certifications</span><div class="section-rule"></div></div>
    <h2>Credentials</h2>
    <p style="color:var(--sub);margin-bottom:40px;font-size:14px;">Formally certified across automation, data, supply chain, and innovation disciplines.</p>
    <div class="certs-grid">
      <div class="cert-card"><div class="cert-icon">⚡</div><div class="cert-name">AI Automation Foundation using n8n</div><div class="cert-issuer">n8n.io · Automation Engineering</div></div>
      <div class="cert-card"><div class="cert-icon">📊</div><div class="cert-name">Data Analysis with Professional Skills</div><div class="cert-issuer">ALX Africa · Professional Development</div></div>
      <div class="cert-card"><div class="cert-icon">🏭</div><div class="cert-name">Supply Chain Fundamentals</div><div class="cert-issuer">Massachusetts Institute of Technology (MIT)</div></div>
      <div class="cert-card"><div class="cert-icon">🏆</div><div class="cert-name">L'Oréal Brandstorm Innovation</div><div class="cert-issuer">L'Oréal · Global Innovation Challenge</div></div>
    </div>
  </div>
</div>

<!-- PROJECTS -->
<div class="projects-bg" id="projects">
  <div class="section">
    <div class="section-head"><span class="section-tag">// 03 — Portfolio</span><div class="section-rule"></div></div>
    <h2>Live Projects</h2>
    <p style="color:var(--sub);margin-bottom:40px;font-size:14px;max-width:520px;line-height:1.85;">Real systems built for real clients. Paste a Loom/YouTube link or upload a video below each project.</p>

    <!-- P1 -->
    <div class="project-card">
      <div>
        <div class="proj-num">01</div>
        <div class="proj-title">WordPress → n8n → Google Drive File Ingestion Pipeline</div>
        <div class="proj-desc">End-to-end document pipeline for a global supply chain firm. Employees in China and Europe submit file URLs via CFF forms auto-populated from a live Google Sheets ORDERS database. n8n catches the webhook and streams zip archives directly into structured Google Drive folders (company → order → raw_pictures) via HTTP Streaming — zero memory overhead, no disk touch.</div>
        <div class="proj-tags">
          <span class="tag">n8n</span><span class="tag">WordPress</span><span class="tag">CFF Dwbooster</span>
          <span class="tag tag-b">Google Drive</span><span class="tag tag-b">Google Sheets</span>
          <span class="tag">HTTP Streaming</span><span class="tag">Webhooks</span>
        </div>
        <a href="https://www.upwork.com/freelancers/~017146fe881c329b56?p=2015143001937068032" target="_blank" class="proj-link">View on Upwork ↗</a>
      </div>
      <div class="video-zone">
        <div class="video-frame clickable" id="vf1" onclick="handleFrameClick(1)">
          <div class="vid-placeholder" id="vp1"><div class="vid-icon">▶</div><div class="vid-text">Add demo video<br/>or Loom link</div></div>
          <iframe id="vif1" style="display:none;" allowfullscreen></iframe>
        </div>
        <div class="loom-row">
          <input class="loom-input" id="li1" placeholder="Paste Loom / YouTube link…" />
          <button class="loom-btn" onclick="applyLink(1)">Load</button>
          <label class="loom-btn" for="vfi1" title="Upload video file">📁</label>
          <input type="file" class="vid-file-inp" id="vfi1" accept="video/*" onchange="loadFile(1,this)" />
        </div>
      </div>
    </div>

    <!-- P2 -->
    <div class="project-card">
      <div>
        <div class="proj-num">02</div>
        <div class="proj-title">Multi-Platform File Transfer & Cloud Storage Automation</div>
        <div class="proj-desc">Researched and built custom download strategies for WeTransfer, Wenshushu, and FromSmash — each needing a different API or URL-parsing approach to bypass redirects and stream files directly to cloud storage, eliminating disk usage and server overhead entirely.</div>
        <div class="proj-tags">
          <span class="tag">n8n</span><span class="tag tag-b">WeTransfer API</span>
          <span class="tag tag-b">Wenshushu</span><span class="tag tag-b">FromSmash</span>
          <span class="tag">File Streaming</span><span class="tag">REST APIs</span>
        </div>
        <a href="https://www.upwork.com/freelancers/~017146fe881c329b56?p=1988319437552893952" target="_blank" class="proj-link">View on Upwork ↗</a>
      </div>
      <div class="video-zone">
        <div class="video-frame clickable" id="vf2">
          <div class="vid-placeholder" id="vp2"><div class="vid-icon">▶</div><div class="vid-text">Add demo video<br/>or Loom link</div></div>
          <iframe id="vif2" style="display:none;" allowfullscreen></iframe>
        </div>
        <div class="loom-row">
          <input class="loom-input" id="li2" placeholder="Paste Loom / YouTube link…" />
          <button class="loom-btn" onclick="applyLink(2)">Load</button>
          <label class="loom-btn" for="vfi2">📁</label>
          <input type="file" class="vid-file-inp" id="vfi2" accept="video/*" onchange="loadFile(2,this)" />
        </div>
      </div>
    </div>

    <!-- P3 -->
    <div class="project-card">
      <div>
        <div class="proj-num">03</div>
        <div class="proj-title">Database-Driven Dynamic Form System</div>
        <div class="proj-desc">Live Google Sheets → WordPress sync using CFF's DS Record & DS Field. Dropdown menus auto-populate from the ORDERS database on every page load. On submission, n8n writes results back to the correct Sheets column — a fully closed-loop data system with no manual maintenance.</div>
        <div class="proj-tags">
          <span class="tag">CFF Dwbooster</span><span class="tag tag-b">Google Sheets</span>
          <span class="tag">DS Record</span><span class="tag">DS Field</span>
          <span class="tag">n8n</span><span class="tag">WordPress</span>
        </div>
        <a href="https://www.upwork.com/freelancers/~017146fe881c329b56?p=1954261074681040896" target="_blank" class="proj-link">View on Upwork ↗</a>
      </div>
      <div class="video-zone">
        <div class="video-frame clickable" id="vf3">
          <div class="vid-placeholder" id="vp3"><div class="vid-icon">▶</div><div class="vid-text">Add demo video<br/>or Loom link</div></div>
          <iframe id="vif3" style="display:none;" allowfullscreen></iframe>
        </div>
        <div class="loom-row">
          <input class="loom-input" id="li3" placeholder="Paste Loom / YouTube link…" />
          <button class="loom-btn" onclick="applyLink(3)">Load</button>
          <label class="loom-btn" for="vfi3">📁</label>
          <input type="file" class="vid-file-inp" id="vfi3" accept="video/*" onchange="loadFile(3,this)" />
        </div>
      </div>
    </div>

    <!-- P4 -->
    <div class="project-card">
      <div>
        <div class="proj-num">04</div>
        <div class="proj-title">Async Cross-Timezone Business Workflow Automation</div>
        <div class="proj-desc">Fully asynchronous data processing and routing pipeline for distributed teams across China and international offices. No real-time calls required — clean data flows, Loom screencast deliverables, and tight deadlines met consistently.</div>
        <div class="proj-tags">
          <span class="tag">n8n</span><span class="tag tag-b">Make</span>
          <span class="tag tag-b">Google Workspace</span><span class="tag">Loom</span><span class="tag">Webhooks</span>
        </div>
        <a href="https://www.upwork.com/freelancers/~017146fe881c329b56?p=1954276385171197952" target="_blank" class="proj-link">View on Upwork ↗</a>
      </div>
      <div class="video-zone">
        <div class="video-frame clickable" id="vf4">
          <div class="vid-placeholder" id="vp4"><div class="vid-icon">▶</div><div class="vid-text">Add demo video<br/>or Loom link</div></div>
          <iframe id="vif4" style="display:none;" allowfullscreen></iframe>
        </div>
        <div class="loom-row">
          <input class="loom-input" id="li4" placeholder="Paste Loom / YouTube link…" />
          <button class="loom-btn" onclick="applyLink(4)">Load</button>
          <label class="loom-btn" for="vfi4">📁</label>
          <input type="file" class="vid-file-inp" id="vfi4" accept="video/*" onchange="loadFile(4,this)" />
        </div>
      </div>
    </div>
  </div>
</div>

<!-- EDUCATION -->
<div class="section" id="edu">
  <div class="section-head"><span class="section-tag">// 04 — Education</span><div class="section-rule"></div></div>
  <h2>Academic Background</h2>
  <p style="color:var(--sub);margin-bottom:36px;font-size:14px;">Engineering foundation — analytical thinking applied to automation problems.</p>
  <div class="edu-card">
    <div class="edu-icon">🎓</div>
    <div>
      <div class="edu-degree">Bachelor of Engineering — Mechanical Design & Production Engineering</div>
      <div class="edu-school">Cairo University · Faculty of Engineering</div>
      <div class="edu-detail">Giza, Egypt</div>
    </div>
  </div>
</div>

<!-- RECOMMENDATIONS -->
<div style="background:var(--surface);border-top:1px solid var(--border);border-bottom:1px solid var(--border);">
  <div class="section" id="recommendations">
    <div class="section-head"><span class="section-tag">// 05 — Strengthen Your Profile</span><div class="section-rule"></div></div>
    <h2>Recommended Next Steps</h2>
    <p style="color:var(--sub);margin-bottom:40px;font-size:14px;max-width:560px;line-height:1.85;">The highest-impact actions to make your profile stand out and win more clients on Upwork and beyond.</p>
    <div class="rec-grid">
      <div class="rec-card">
        <div class="rec-num">01</div>
        <div class="rec-title">Record Loom Demos for Every Project</div>
        <div class="rec-body">A 2–3 min screencast showing your workflow in action converts skeptical clients instantly. Upload them using the video zones in the Projects section above. This is your single biggest differentiator.</div>
        <span class="rec-badge">Highest Impact</span>
      </div>
      <div class="rec-card">
        <div class="rec-num">02</div>
        <div class="rec-title">Quantify Your Results</div>
        <div class="rec-body">Replace "built automation" with "eliminated 5hrs/week of manual work" or "reduced processing time by 80%." Specific numbers make proposals 3x more compelling — even estimates count.</div>
        <span class="rec-badge">High Impact</span>
      </div>
      <div class="rec-card">
        <div class="rec-num">03</div>
        <div class="rec-title">Publish n8n Workflow Templates</div>
        <div class="rec-body">Share anonymized workflow JSON files on the n8n community forum or GitHub Gists. This builds domain authority, attracts inbound clients, and signals real expertise beyond your resume.</div>
        <span class="rec-badge">Authority Building</span>
      </div>
      <div class="rec-card">
        <div class="rec-num">04</div>
        <div class="rec-title">Collect Your First 5 Reviews</div>
        <div class="rec-body">On Upwork, the first 5 reviews unlock everything. Consider taking 1–2 smaller, quick jobs to build social proof. A single 5-star review multiplies future hire probability significantly.</div>
        <span class="rec-badge">Trust Signal</span>
      </div>
      <div class="rec-card">
        <div class="rec-num">05</div>
        <div class="rec-title">Pick a Niche Vertical</div>
        <div class="rec-body">Generalists compete on price; specialists compete on value. Consider "AI Automation for Supply Chain" or "n8n Expert for E-commerce Teams." Your MIT cert makes supply chain a natural fit.</div>
        <span class="rec-badge">Positioning</span>
      </div>
      <div class="rec-card">
        <div class="rec-num">06</div>
        <div class="rec-title">Write a LinkedIn Case Study</div>
        <div class="rec-body">Turn your WordPress → n8n → GDrive project into a LinkedIn article: the problem, your approach, the outcome. Case studies attract direct inbound leads that bypass Upwork fees entirely.</div>
        <span class="rec-badge">Visibility</span>
      </div>
    </div>
  </div>
</div>

<!-- CTA -->
<div class="cta-wrap" id="contact">
  <div class="cta-inner">
    <div class="cta-text">
      <h2>Ready to automate?</h2>
      <p>Let's eliminate manual work and scale your operations with intelligent systems.</p>
    </div>
    <div class="cta-actions">
      <a href="https://www.upwork.com/freelancers/~017146fe881c329b56" target="_blank" class="btn btn-primary">↗ Hire on Upwork</a>
      <a href="https://wa.me/201159077093" target="_blank" class="btn btn-outline">💬 WhatsApp</a>
      <a href="mailto:hamedmahamed00@gmail.com" class="btn btn-outline">✉ Email</a>
      <a href="http://www.linkedin.com/in/hamed-mohamed-812b4b230" target="_blank" class="btn btn-outline">🔗 LinkedIn</a>
    </div>
  </div>
</div>

<footer>
  <div class="foot-left">© 2025 Hamed Mohamed · AI Automation Engineer · Giza, Egypt</div>
  <div class="foot-links">
    <a href="https://www.upwork.com/freelancers/~017146fe881c329b56" target="_blank">Upwork</a>
    <a href="http://www.linkedin.com/in/hamed-mohamed-812b4b230" target="_blank">LinkedIn</a>
    <a href="https://wa.me/201159077093" target="_blank">WhatsApp</a>
    <a href="mailto:hamedmahamed00@gmail.com">Email</a>
  </div>
</footer>

<script>
// PHOTO
document.getElementById('photoInput').addEventListener('change', function() {
  const f = this.files[0]; if (!f) return;
  const r = new FileReader();
  r.onload = e => {
    const img = document.getElementById('photoImg');
    img.src = e.target.result;
    img.classList.add('show');
    document.getElementById('photoPH').classList.add('hidden');
  };
  r.readAsDataURL(f);
});

// VIDEO EMBED
function getEmbed(url) {
  if (!url) return null;
  // Loom
  const lm = url.match(/loom\.com\/share\/([a-zA-Z0-9]+)/);
  if (lm) return 'https://www.loom.com/embed/' + lm[1];
  // YouTube
  const yt = url.match(/(?:youtube\.com\/watch\?v=|youtu\.be\/|youtube\.com\/shorts\/)([a-zA-Z0-9_-]{11})/);
  if (yt) return 'https://www.youtube.com/embed/' + yt[1] + '?autoplay=0';
  return null;
}

function showEmbed(n, src) {
  const vf = document.getElementById('vf'+n);
  const vp = document.getElementById('vp'+n);
  const vi = document.getElementById('vif'+n);
  vp.style.display = 'none';
  vi.src = src; vi.style.display = 'block';
  vf.classList.remove('clickable');
  vf.style.border = '1px solid var(--border-light)';
  vf.onclick = null;
}

function applyLink(n) {
  const val = document.getElementById('li'+n).value.trim();
  const embed = getEmbed(val);
  if (embed) showEmbed(n, embed);
  else alert('Please enter a valid Loom or YouTube URL.');
}

function loadFile(n, inp) {
  const f = inp.files[0]; if (!f) return;
  const vf = document.getElementById('vf'+n);
  const vp = document.getElementById('vp'+n);
  const vi = document.getElementById('vif'+n);
  vi.style.display = 'none';
  const existing = vf.querySelector('video');
  if (existing) existing.remove();
  const vid = document.createElement('video');
  vid.src = URL.createObjectURL(f);
  vid.controls = true;
  vid.style.cssText = 'width:100%;height:100%;border-radius:8px;';
  vf.appendChild(vid);
  vp.style.display = 'none';
  vf.classList.remove('clickable');
  vf.style.border = '1px solid var(--border-light)';
  vf.onclick = null;
}

function handleFrameClick(n) {
  const vp = document.getElementById('vp'+n);
  if (vp && vp.style.display !== 'none') {
    document.getElementById('li'+n).focus();
  }
}

// Enter key on loom inputs
for (let i = 1; i <= 4; i++) {
  document.getElementById('li'+i).addEventListener('keydown', e => {
    if (e.key === 'Enter') applyLink(i);
  });
}
</script>
</body>
</html>
