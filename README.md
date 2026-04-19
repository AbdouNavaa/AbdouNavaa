<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Abd Razak — Profile Card</title>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;700;800&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #f4f4f0;
      padding: 2rem;
      font-family: 'Syne', sans-serif;
    }

    .profile-card {
      background: #fff;
      border: 1px solid #e5e5e0;
      border-radius: 20px;
      overflow: hidden;
      max-width: 680px;
      width: 100%;
      box-shadow: 0 4px 32px rgba(0,0,0,0.07);
    }

    /* ── Hero ── */
    .hero {
      background: #0D0D0D;
      padding: 2rem 2rem 1.5rem;
      position: relative;
      overflow: hidden;
    }

    .hero::before {
      content: '';
      position: absolute;
      top: -40px; right: -40px;
      width: 200px; height: 200px;
      border-radius: 50%;
      border: 40px solid rgba(255,255,255,0.04);
    }

    .hero::after {
      content: '';
      position: absolute;
      bottom: -60px; left: 40%;
      width: 140px; height: 140px;
      border-radius: 50%;
      border: 30px solid rgba(255,255,255,0.03);
    }

    .badge {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      font-family: 'JetBrains Mono', monospace;
      font-size: 11px;
      color: #888;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      margin-bottom: 1rem;
    }

    .badge-dot {
      width: 6px; height: 6px;
      border-radius: 50%;
      background: #4ADE80;
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.4; }
    }

    .hero-name {
      font-size: 28px;
      font-weight: 800;
      color: #fff;
      line-height: 1.1;
      margin-bottom: 0.3rem;
      letter-spacing: -0.02em;
    }

    .hero-title {
      font-size: 13px;
      font-weight: 400;
      color: #666;
      font-family: 'JetBrains Mono', monospace;
      margin-bottom: 1.5rem;
    }

    .hero-title span { color: #4ADE80; }

    .contact-row {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
    }

    .contact-chip {
      display: inline-flex;
      align-items: center;
      gap: 5px;
      padding: 5px 10px;
      border-radius: 6px;
      border: 0.5px solid #2a2a2a;
      font-size: 11px;
      font-family: 'JetBrains Mono', monospace;
      color: #999;
      text-decoration: none;
      transition: border-color 0.15s, color 0.15s;
    }

    .contact-chip:hover {
      border-color: #444;
      color: #ccc;
    }

    /* ── Body ── */
    .body {
      padding: 1.5rem 2rem;
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1.5rem;
    }

    .section-label {
      font-family: 'JetBrains Mono', monospace;
      font-size: 10px;
      font-weight: 500;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: #aaa;
      margin-bottom: 0.75rem;
    }

    /* ── Currently learning ── */
    .currently-learning {
      background: #f7f7f5;
      border-radius: 12px;
      padding: 1rem 1.1rem;
      display: flex;
      align-items: flex-start;
      gap: 10px;
    }

    .flutter-icon {
      width: 32px; height: 32px;
      border-radius: 8px;
      background: #0554F2;
      display: flex; align-items: center; justify-content: center;
      flex-shrink: 0;
    }

    .currently-learning strong {
      display: block;
      font-size: 14px;
      font-weight: 500;
      color: #111;
      margin-bottom: 2px;
    }

    .currently-learning p {
      font-size: 12px;
      color: #888;
      line-height: 1.5;
    }

    /* ── Ask me ── */
    .ask-me {
      display: flex;
      flex-direction: column;
      gap: 6px;
    }

    .skill-tag {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      padding: 6px 10px;
      border-radius: 8px;
      font-size: 12px;
      font-weight: 500;
      width: fit-content;
    }

    .tag-react  { background: #EBF5FD; color: #0C6B99; }
    .tag-flutter { background: #EBF0FE; color: #0C3D99; }

    .tag-dot {
      width: 5px; height: 5px;
      border-radius: 50%;
      background: currentColor;
      opacity: 0.6;
    }

    /* ── Divider ── */
    .divider {
      grid-column: 1 / -1;
      height: 1px;
      background: #efefec;
      margin: 0 -2rem;
    }

    /* ── Skills ── */
    .skills-section { grid-column: 1 / -1; }

    .skills-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
    }

    .skill-pill {
      padding: 4px 10px;
      border: 1px solid #e5e5e0;
      border-radius: 20px;
      font-family: 'JetBrains Mono', monospace;
      font-size: 11px;
      color: #888;
    }

    .skill-pill.accent {
      border-color: #ccc;
      color: #111;
    }

    /* ── Stats ── */
    .stats-section {
      grid-column: 1 / -1;
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 8px;
    }

    .stat-card {
      background: #f7f7f5;
      border-radius: 10px;
      padding: 0.8rem 1rem;
    }

    .stat-number {
      font-size: 22px;
      font-weight: 800;
      color: #111;
      line-height: 1;
      margin-bottom: 3px;
      letter-spacing: -0.02em;
    }

    .stat-label {
      font-size: 11px;
      color: #aaa;
      font-family: 'JetBrains Mono', monospace;
    }
  </style>
</head>
<body>

<div class="profile-card">
  <!-- Hero -->
  <div class="hero">
    <div class="badge">
      <span class="badge-dot"></span>
      available for work
    </div>
    <div class="hero-name">Abd Razak<br>Mohamed Navaa</div>
    <div class="hero-title">software_engineer @ <span>Mauritania</span></div>
    <div class="contact-row">
      <a class="contact-chip" href="mailto:babana9977@gmail.com">
        <svg width="11" height="11" viewBox="0 0 16 16" fill="none">
          <rect x="1" y="3" width="14" height="10" rx="2" stroke="currentColor" stroke-width="1.5"/>
          <path d="M1 5l7 5 7-5" stroke="currentColor" stroke-width="1.5"/>
        </svg>
        babana9977@gmail.com
      </a>
      <a class="contact-chip" href="https://linkedin.com/in/abd-razak-babana-983336281" target="_blank">
        <svg width="11" height="11" viewBox="0 0 16 16" fill="none">
          <rect x="1" y="1" width="14" height="14" rx="2" stroke="currentColor" stroke-width="1.5"/>
          <path d="M4 7v5M4 4.5v.5M8 12V9c0-1.1.9-2 2-2s2 .9 2 2v3" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
        </svg>
        LinkedIn
      </a>
      <a class="contact-chip" href="https://medium.com/@babana9977" target="_blank">
        <svg width="11" height="11" viewBox="0 0 16 16" fill="none">
          <circle cx="4.5" cy="8" r="3.5" stroke="currentColor" stroke-width="1.5"/>
          <ellipse cx="11" cy="8" rx="2" ry="3.5" stroke="currentColor" stroke-width="1.5"/>
          <line x1="14.5" y1="4.5" x2="14.5" y2="11.5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
        </svg>
        Medium
      </a>
    </div>
  </div>

  <!-- Body -->
  <div class="body">

    <!-- Currently learning -->
    <div>
      <div class="section-label">currently learning</div>
      <div class="currently-learning">
        <div class="flutter-icon">
          <svg width="18" height="18" viewBox="0 0 48 48" fill="none">
            <path d="M28 4L9 23l6 6L40 4H28z" fill="white"/>
            <path d="M28 23l-6-6-13 13 6 6 13-13z" fill="rgba(255,255,255,0.6)"/>
            <path d="M15 36l6 6 13-13-6-6-13 13z" fill="white"/>
          </svg>
        </div>
        <div>
          <strong>Flutter &amp; Dart</strong>
          <p>cross-platform mobile development</p>
        </div>
      </div>
    </div>

    <!-- Ask me about -->
    <div>
      <div class="section-label">ask me about</div>
      <div class="ask-me">
        <span class="skill-tag tag-react"><span class="tag-dot"></span>React</span>
        <span class="skill-tag tag-flutter"><span class="tag-dot"></span>Flutter</span>
      </div>
    </div>

    <div class="divider"></div>

    <!-- Skills -->
    <div class="skills-section">
      <div class="section-label">languages &amp; tools</div>
      <div class="skills-grid">
        <span class="skill-pill accent">TypeScript</span>
        <span class="skill-pill accent">JavaScript</span>
        <span class="skill-pill accent">Python</span>
        <span class="skill-pill accent">Dart</span>
        <span class="skill-pill accent">Java</span>
        <span class="skill-pill">React</span>
        <span class="skill-pill">Next.js</span>
        <span class="skill-pill">Flutter</span>
        <span class="skill-pill">Node.js</span>
        <span class="skill-pill">Angular</span>
        <span class="skill-pill">Django</span>
        <span class="skill-pill">Laravel</span>
        <span class="skill-pill">Spring</span>
        <span class="skill-pill">Redux</span>
        <span class="skill-pill">GraphQL</span>
        <span class="skill-pill">Firebase</span>
        <span class="skill-pill">MongoDB</span>
        <span class="skill-pill">MySQL</span>
        <span class="skill-pill">PostgreSQL</span>
        <span class="skill-pill">Docker</span>
        <span class="skill-pill">Figma</span>
        <span class="skill-pill">Git</span>
        <span class="skill-pill">Tailwind</span>
        <span class="skill-pill">Sass</span>
        <span class="skill-pill">C / C++ / C#</span>
        <span class="skill-pill">Hadoop</span>
        <span class="skill-pill">Pandas</span>
      </div>
    </div>

    <div class="divider"></div>

    <!-- Stats -->
    <div class="stats-section">
      <div class="stat-card">
        <div class="stat-number">27+</div>
        <div class="stat-label">technologies</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">5+</div>
        <div class="stat-label">languages</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">MR</div>
        <div class="stat-label">Mauritania</div>
      </div>
    </div>

  </div>
</div>

</body>
</html>
