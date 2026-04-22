<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Iza Mahendra — Frontend Developer & Designer</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:ital,wght@0,300;0,400;1,300&display=swap" rel="stylesheet" />
<style>
  :root {
    --bg: #0a0a0f;
    --surface: #111118;
    --card: #16161f;
    --border: #1e1e2e;
    --accent: #7c6af5;
    --accent2: #f5a96a;
    --accent3: #52e0c0;
    --text: #e8e6f0;
    --muted: #7a7890;
    --glow: rgba(124, 106, 245, 0.3);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
    position: relative;
  }

  /* Ambient background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background:
      radial-gradient(ellipse 60% 40% at 15% 10%, rgba(124,106,245,0.12) 0%, transparent 60%),
      radial-gradient(ellipse 40% 50% at 85% 80%, rgba(82,224,192,0.08) 0%, transparent 55%),
      radial-gradient(ellipse 50% 30% at 70% 20%, rgba(245,169,106,0.06) 0%, transparent 50%);
    pointer-events: none;
    z-index: 0;
  }

  /* Grid texture */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(255,255,255,0.015) 1px, transparent 1px),
      linear-gradient(90deg, rgba(255,255,255,0.015) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .wrapper {
    max-width: 820px;
    margin: 0 auto;
    padding: 48px 24px 80px;
    position: relative;
    z-index: 1;
  }

  /* ── HERO ── */
  .hero {
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 32px;
    align-items: start;
    margin-bottom: 60px;
    padding: 48px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 20px;
    position: relative;
    overflow: hidden;
    animation: fadeUp 0.7s ease both;
  }

  .hero::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--accent), var(--accent3), transparent);
    animation: shimmer 3s ease-in-out infinite;
  }

  @keyframes shimmer {
    0%, 100% { opacity: 0.6; }
    50% { opacity: 1; }
  }

  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-size: 11px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--accent);
    background: rgba(124,106,245,0.1);
    border: 1px solid rgba(124,106,245,0.25);
    padding: 5px 14px;
    border-radius: 999px;
    margin-bottom: 20px;
    width: fit-content;
  }

  .hero-badge::before {
    content: '';
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--accent3);
    animation: pulse 2s ease infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.5; transform: scale(0.8); }
  }

  .hero h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(32px, 5vw, 52px);
    font-weight: 800;
    line-height: 1.1;
    letter-spacing: -0.03em;
    margin-bottom: 16px;
  }

  .hero h1 .name-iza {
    color: var(--text);
  }

  .hero h1 .name-last {
    background: linear-gradient(135deg, var(--accent), var(--accent3));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-sub {
    font-size: 13px;
    color: var(--muted);
    line-height: 1.7;
    max-width: 420px;
    margin-bottom: 32px;
  }

  .hero-sub strong {
    color: var(--accent2);
    font-weight: 400;
  }

  .hero-avatar {
    width: 100px;
    height: 100px;
    border-radius: 16px;
    background: linear-gradient(135deg, var(--accent), var(--accent3));
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Syne', sans-serif;
    font-size: 36px;
    font-weight: 800;
    color: white;
    letter-spacing: -0.04em;
    flex-shrink: 0;
    position: relative;
    box-shadow: 0 0 40px var(--glow);
  }

  .hero-avatar::after {
    content: '🇮🇩';
    position: absolute;
    bottom: -8px;
    right: -8px;
    font-size: 20px;
    background: var(--card);
    border-radius: 8px;
    padding: 2px 4px;
    border: 1px solid var(--border);
  }

  /* ── INFO CHIPS ── */
  .chips {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .chip {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-size: 12px;
    color: var(--muted);
    background: rgba(255,255,255,0.03);
    border: 1px solid var(--border);
    padding: 8px 16px;
    border-radius: 10px;
    transition: border-color 0.2s, color 0.2s;
    text-decoration: none;
  }

  .chip:hover {
    border-color: var(--accent);
    color: var(--text);
  }

  .chip .icon { font-size: 14px; }

  /* ── SECTION LABEL ── */
  .section-label {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 20px;
    animation: fadeUp 0.7s ease both;
  }

  .section-label span {
    font-family: 'Syne', sans-serif;
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--muted);
  }

  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* ── SOCIAL LINKS ── */
  .socials-section {
    margin-bottom: 48px;
    animation: fadeUp 0.7s ease 0.1s both;
  }

  .socials-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
    gap: 12px;
  }

  .social-card {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 16px 20px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    text-decoration: none;
    color: var(--text);
    transition: all 0.25s ease;
    position: relative;
    overflow: hidden;
  }

  .social-card::before {
    content: '';
    position: absolute;
    inset: 0;
    opacity: 0;
    transition: opacity 0.25s;
  }

  .social-card:hover::before { opacity: 1; }
  .social-card:hover { transform: translateY(-2px); border-color: transparent; }

  .social-card.linkedin { --c: #0e76a8; }
  .social-card.instagram { --c: #e84393; }
  .social-card.tiktok { --c: #ffffff; }
  .social-card.gmail { --c: #ea4335; }

  .social-card:hover {
    box-shadow: 0 0 0 1px var(--c), 0 8px 32px rgba(0,0,0,0.3);
  }

  .social-icon {
    width: 36px; height: 36px;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 18px;
    background: rgba(255,255,255,0.05);
    flex-shrink: 0;
  }

  .social-info { min-width: 0; }

  .social-name {
    font-family: 'Syne', sans-serif;
    font-size: 13px;
    font-weight: 600;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  .social-handle {
    font-size: 11px;
    color: var(--muted);
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  /* ── TECH STACK ── */
  .tech-section {
    margin-bottom: 48px;
    animation: fadeUp 0.7s ease 0.2s both;
  }

  .tech-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
    gap: 10px;
  }

  .tech-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 10px;
    padding: 20px 12px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    font-size: 12px;
    color: var(--muted);
    text-align: center;
    cursor: default;
    transition: all 0.25s ease;
    position: relative;
    overflow: hidden;
  }

  .tech-item:hover {
    border-color: var(--accent);
    color: var(--text);
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(0,0,0,0.3), 0 0 0 1px var(--accent);
  }

  .tech-icon {
    width: 40px; height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 10px;
  }

  .tech-icon img {
    width: 32px; height: 32px;
    object-fit: contain;
  }

  .tech-name {
    font-family: 'Syne', sans-serif;
    font-size: 11px;
    font-weight: 600;
  }

  /* ── STATS ── */
  .stats-section {
    animation: fadeUp 0.7s ease 0.3s both;
  }

  .stats-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
    margin-bottom: 16px;
  }

  .stat-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    overflow: hidden;
  }

  .stat-card img {
    width: 100%;
    height: auto;
    display: block;
    filter: brightness(0.95);
  }

  .stat-card-wide {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    overflow: hidden;
  }

  .stat-card-wide img {
    width: 100%;
    height: auto;
    display: block;
    filter: brightness(0.95);
  }

  /* ── FOOTER ── */
  .footer {
    margin-top: 60px;
    padding-top: 32px;
    border-top: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 12px;
    animation: fadeUp 0.7s ease 0.4s both;
  }

  .footer-left {
    font-size: 12px;
    color: var(--muted);
  }

  .footer-left strong {
    color: var(--accent);
    font-weight: 400;
  }

  .footer-stats {
    display: flex;
    gap: 16px;
  }

  .footer-stat {
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: 12px;
    color: var(--muted);
    background: var(--card);
    border: 1px solid var(--border);
    padding: 6px 14px;
    border-radius: 999px;
    text-decoration: none;
    transition: color 0.2s;
  }

  .footer-stat:hover { color: var(--text); }

  /* ── ABOUT GRID ── */
  .about-section {
    margin-bottom: 48px;
    animation: fadeUp 0.7s ease 0.05s both;
  }

  .about-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 12px;
  }

  .about-item {
    display: flex;
    align-items: flex-start;
    gap: 14px;
    padding: 20px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    transition: border-color 0.2s;
  }

  .about-item:hover { border-color: rgba(124,106,245,0.4); }

  .about-emoji {
    font-size: 20px;
    flex-shrink: 0;
    margin-top: 2px;
  }

  .about-text {
    font-size: 12px;
    line-height: 1.7;
    color: var(--muted);
  }

  .about-text a {
    color: var(--accent);
    text-decoration: none;
    border-bottom: 1px solid transparent;
    transition: border-color 0.2s;
  }

  .about-text a:hover { border-color: var(--accent); }

  .about-text strong {
    color: var(--text);
    font-weight: 400;
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 600px) {
    .hero { grid-template-columns: 1fr; padding: 32px 24px; }
    .hero-avatar { display: none; }
    .stats-grid { grid-template-columns: 1fr; }
    .about-grid { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>
<div class="wrapper">

  <!-- HERO -->
  <div class="hero">
    <div>
      <div class="hero-badge">✦ Available for collaboration</div>
      <h1>
        <span class="name-iza">Iza </span><br>
        <span class="name-last">Mahendra</span>
      </h1>
      <p class="hero-sub">
        <strong>Frontend Developer</strong> & <strong>Graphic Designer</strong> crafting digital experiences from Indonesia — building with React, Next.js, and an eye for design.
      </p>
      <div class="chips">
        <span class="chip"><span class="icon">🏢</span> Indonesia</span>
        <span class="chip"><span class="icon">⚛️</span> React · Next.js</span>
        <span class="chip"><span class="icon">🎨</span> Figma · Photoshop</span>
        <span class="chip"><span class="icon">😄</span> he/him</span>
      </div>
    </div>
    <div class="hero-avatar">IM</div>
  </div>

  <!-- ABOUT -->
  <div class="about-section">
    <div class="section-label"><span>About</span></div>
    <div class="about-grid">
      <div class="about-item">
        <span class="about-emoji">⚛️</span>
        <p class="about-text">Diving deep into <a href="https://reactjs.org">React</a> & <a href="https://nextjs.org">Next.js</a> — building performant, modern web applications.</p>
      </div>
      <div class="about-item">
        <span class="about-emoji">🎨</span>
        <p class="about-text">Passionate about <strong>Graphic Design</strong> — turning ideas into visuals with Figma, Adobe Photoshop & more.</p>
      </div>
      <div class="about-item">
        <span class="about-emoji">♻️</span>
        <p class="about-text">Open to <strong>collaboration</strong> on frontend and design projects. Let's build something great together.</p>
      </div>
      <div class="about-item">
        <span class="about-emoji">💬</span>
        <p class="about-text">Feel free to <strong>ask me anything</strong> — always happy to connect, share, and learn.</p>
      </div>
    </div>
  </div>

  <!-- SOCIAL LINKS -->
  <div class="socials-section">
    <div class="section-label"><span>Let's connect</span></div>
    <div class="socials-grid">
      <a class="social-card linkedin" href="https://www.linkedin.com/in/iza-mahendra/" target="_blank">
        <div class="social-icon">💼</div>
        <div class="social-info">
          <div class="social-name">LinkedIn</div>
          <div class="social-handle">Iza Mahendra</div>
        </div>
      </a>
      <a class="social-card instagram" href="https://instagram.com/izamhn" target="_blank">
        <div class="social-icon">📸</div>
        <div class="social-info">
          <div class="social-name">Instagram</div>
          <div class="social-handle">@izamhn</div>
        </div>
      </a>
      <a class="social-card tiktok" href="https://tiktok.com/@izamhn" target="_blank">
        <div class="social-icon">🎵</div>
        <div class="social-info">
          <div class="social-name">TikTok</div>
          <div class="social-handle">@izamhn</div>
        </div>
      </a>
      <a class="social-card gmail" href="mailto:izamahendra868@gmail.com" target="_blank">
        <div class="social-icon">✉️</div>
        <div class="social-info">
          <div class="social-name">Email</div>
          <div class="social-handle">izamahendra868</div>
        </div>
      </a>
    </div>
  </div>

  <!-- TECH STACK -->
  <div class="tech-section">
    <div class="section-label"><span>Tech & Tools</span></div>
    <div class="tech-grid">
      <div class="tech-item">
        <div class="tech-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" alt="React" /></div>
        <span class="tech-name">React</span>
      </div>
      <div class="tech-item">
        <div class="tech-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nextjs/nextjs-original.svg" alt="Next.js" style="filter:invert(1)" /></div>
        <span class="tech-name">Next.js</span>
      </div>
      <div class="tech-item">
        <div class="tech-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" alt="JavaScript" /></div>
        <span class="tech-name">JavaScript</span>
      </div>
      <div class="tech-item">
        <div class="tech-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" alt="HTML5" /></div>
        <span class="tech-name">HTML5</span>
      </div>
      <div class="tech-item">
        <div class="tech-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" alt="CSS3" /></div>
        <span class="tech-name">CSS3</span>
      </div>
      <div class="tech-item">
        <div class="tech-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/figma/figma-original.svg" alt="Figma" /></div>
        <span class="tech-name">Figma</span>
      </div>
      <div class="tech-item">
        <div class="tech-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/photoshop/photoshop-plain.svg" alt="Photoshop" /></div>
        <span class="tech-name">Photoshop</span>
      </div>
      <div class="tech-item">
        <div class="tech-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" alt="Git" /></div>
        <span class="tech-name">Git</span>
      </div>
      <div class="tech-item">
        <div class="tech-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg" alt="VS Code" /></div>
        <span class="tech-name">VS Code</span>
      </div>
    </div>
  </div>

  <!-- STATS -->
  <div class="stats-section">
    <div class="section-label"><span>Statistics</span></div>
    <div class="stats-grid">
      <div class="stat-card">
        <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=iza1205&layout=compact&langs_count=6&theme=transparent&hide_border=true&title_color=7c6af5&text_color=e8e6f0&bg_color=16161f" alt="Top Languages" />
      </div>
      <div class="stat-card">
        <img src="https://github-readme-stats.vercel.app/api?username=iza1205&show_icons=true&count_private=true&hide=contribs&theme=transparent&hide_border=true&title_color=7c6af5&text_color=e8e6f0&icon_color=52e0c0&bg_color=16161f" alt="GitHub Stats" />
      </div>
    </div>
    <div class="stat-card-wide">
      <img src="https://github-readme-streak-stats.herokuapp.com/?user=iza1205&theme=transparent&hide_border=true&ring=7c6af5&fire=f5a96a&currStreakLabel=7c6af5&sideLabels=7a7890&currStreakNum=e8e6f0&sideNums=e8e6f0&dates=7a7890&background=16161f" alt="Streak Stats" />
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    <div class="footer-left">
      Crafted with ❤️ by <strong>Iza Mahendra</strong> · Indonesia 🇮🇩
    </div>
    <div class="footer-stats">
      <a class="footer-stat" href="https://github.com/iza1205" target="_blank">
        <img src="https://komarev.com/ghpvc/?username=iza1205&color=7c6af5&label=Views&style=flat" alt="Profile Views" height="16" style="border-radius:4px" />
      </a>
      <a class="footer-stat" href="https://github.com/iza1205?tab=followers" target="_blank">
        <img src="https://img.shields.io/github/followers/iza1205?label=Followers&style=flat&color=7c6af5&labelColor=111118" alt="Followers" height="16" style="border-radius:4px" />
      </a>
    </div>
  </div>

</div>
</body>
</html>
