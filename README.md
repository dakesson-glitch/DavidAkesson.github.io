# <!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>David Akesson</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700;900&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --green:       #1a3a2a;
      --green-mid:   #2c5f42;
      --gold:        #d4a017;
      --gold-light:  #f0c84a;
      --cream:       #f5f0e8;
      --dark:        #0e1f16;
      --text:        #1c1c1c;
      --muted:       #5a6b5e;
    }

    html { scroll-behavior: smooth; }

    body {
      font-family: 'Inter', sans-serif;
      background: var(--cream);
      color: var(--text);
      overflow-x: hidden;
    }

    /* ── NAV ── */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 0 48px;
      height: 64px;
      background: rgba(14, 31, 22, 0.95);
      backdrop-filter: blur(8px);
      border-bottom: 1px solid rgba(212, 160, 23, 0.3);
    }

    .nav-logo {
      font-family: 'Playfair Display', serif;
      font-size: 1.1rem;
      font-weight: 700;
      color: var(--gold);
      letter-spacing: 0.05em;
      text-decoration: none;
    }

    .nav-links {
      display: flex;
      gap: 36px;
      list-style: none;
    }

    .nav-links a {
      color: rgba(245, 240, 232, 0.8);
      text-decoration: none;
      font-size: 0.85rem;
      font-weight: 500;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      transition: color 0.2s;
    }

    .nav-links a:hover { color: var(--gold); }

    /* ── HERO ── */
    #home {
      min-height: 100vh;
      display: grid;
      grid-template-columns: 1fr 1fr;
      padding-top: 64px;
    }

    .hero-left {
      background: var(--green);
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: 80px 56px 80px 72px;
      position: relative;
      overflow: hidden;
    }

    /* diagonal gold accent — the signature element */
    .hero-left::before {
      content: '';
      position: absolute;
      top: -80px;
      right: -40px;
      width: 6px;
      height: 160%;
      background: linear-gradient(180deg, var(--gold) 0%, var(--gold-light) 50%, var(--gold) 100%);
      transform: rotate(12deg);
      transform-origin: top center;
      opacity: 0.6;
    }

    .hero-left::after {
      content: '';
      position: absolute;
      top: -80px;
      right: -60px;
      width: 2px;
      height: 160%;
      background: var(--gold);
      transform: rotate(12deg);
      transform-origin: top center;
      opacity: 0.3;
    }

    .hero-eyebrow {
      font-size: 0.75rem;
      font-weight: 600;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 20px;
    }

    .hero-name {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2.8rem, 5vw, 4.2rem);
      font-weight: 900;
      color: var(--cream);
      line-height: 1.05;
      margin-bottom: 24px;
    }

    .hero-tagline {
      font-size: 1rem;
      color: rgba(245, 240, 232, 0.7);
      line-height: 1.7;
      max-width: 400px;
      margin-bottom: 40px;
    }

    .hero-flags {
      display: flex;
      align-items: center;
      gap: 12px;
      margin-bottom: 40px;
    }

    .flag-bar {
      width: 32px;
      height: 20px;
      border-radius: 3px;
      overflow: hidden;
      display: flex;
      flex-direction: column;
      flex-shrink: 0;
    }

    .flag-gh { background: linear-gradient(to bottom, #006b3f 33%, #fcd116 33%, #fcd116 66%, #ce1126 66%); }
    /* Ghana: red/gold/green — rendered as stripes */
    .flag-gh {
      background: none;
    }
    .flag-gh .s1 { background: #ce1126; flex: 1; }
    .flag-gh .s2 { background: #fcd116; flex: 1; position: relative; display: flex; align-items: center; justify-content: center; }
    .flag-gh .s2::after { content: '★'; color: #000; font-size: 9px; line-height: 1; }
    .flag-gh .s3 { background: #006b3f; flex: 1; }

    .flag-us { background: none; }
    .flag-us .s1 { background: #bf0a30; flex: 1; }
    .flag-us .s2 { background: #fff; flex: 1; }
    .flag-us .s3 { background: #bf0a30; flex: 1; }

    .flag-label {
      font-size: 0.75rem;
      color: rgba(245, 240, 232, 0.55);
      letter-spacing: 0.05em;
    }

    .hero-cta {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      background: var(--gold);
      color: var(--dark);
      text-decoration: none;
      font-weight: 600;
      font-size: 0.85rem;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      padding: 14px 28px;
      transition: background 0.2s, transform 0.2s;
      width: fit-content;
    }

    .hero-cta:hover { background: var(--gold-light); transform: translateX(4px); }

    .hero-right {
      position: relative;
      overflow: hidden;
      background: var(--dark);
    }

    .hero-right img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      object-position: center top;
      opacity: 0.85;
      display: block;
    }

    /* overlay gradient on photo */
    .hero-right::after {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(to right, var(--green) 0%, transparent 30%);
    }

    /* ── SECTION SHARED ── */
    section {
      padding: 100px 72px;
    }

    .section-label {
      font-size: 0.7rem;
      font-weight: 600;
      letter-spacing: 0.25em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 12px;
    }

    .section-title {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2rem, 3.5vw, 3rem);
      font-weight: 700;
      color: var(--green);
      line-height: 1.1;
      margin-bottom: 48px;
    }

    .divider {
      width: 48px;
      height: 3px;
      background: var(--gold);
      margin-bottom: 48px;
    }

    /* ── INTRO / ABOUT STRIP ── */
    #about {
      background: var(--green);
      color: var(--cream);
      padding: 80px 72px;
    }

    #about .section-title { color: var(--cream); }

    .about-grid {
      display: grid;
      grid-template-columns: 1.4fr 1fr;
      gap: 64px;
      align-items: start;
    }

    .about-text p {
      font-size: 1.05rem;
      line-height: 1.85;
      color: rgba(245, 240, 232, 0.85);
    }

    .about-text p + p { margin-top: 20px; }

    .about-sidebar {
      display: flex;
      flex-direction: column;
      gap: 28px;
    }

    .info-block {}

    .info-block h4 {
      font-size: 0.7rem;
      font-weight: 600;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 8px;
    }

    .info-block p, .info-block li {
      font-size: 0.92rem;
      color: rgba(245, 240, 232, 0.75);
      line-height: 1.6;
    }

    .info-block ul { list-style: none; }
    .info-block li::before { content: '— '; color: var(--gold); }

    /* ── TEAK BADGE ── */
    .teak-strip {
      background: var(--cream);
      padding: 48px 72px;
      display: flex;
      align-items: center;
      gap: 40px;
      border-top: 3px solid var(--gold);
      border-bottom: 3px solid var(--gold);
    }

    .teak-strip img {
      width: 80px;
      height: auto;
      object-fit: contain;
    }

    .teak-text h3 {
      font-family: 'Playfair Display', serif;
      font-size: 1.3rem;
      color: var(--green);
      margin-bottom: 6px;
    }

    .teak-text p {
      font-size: 0.9rem;
      color: var(--muted);
      line-height: 1.6;
      max-width: 600px;
    }

    /* ── RESUME ── */
    #resume {
      background: var(--cream);
    }

    .resume-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 48px;
    }

    .resume-col h3 {
      font-family: 'Playfair Display', serif;
      font-size: 1.15rem;
      font-weight: 700;
      color: var(--green);
      border-left: 3px solid var(--gold);
      padding-left: 14px;
      margin-bottom: 28px;
    }

    .resume-item {
      margin-bottom: 28px;
      padding-left: 17px;
      border-left: 1px solid rgba(26,58,42,0.15);
    }

    .resume-item h4 {
      font-weight: 600;
      font-size: 0.95rem;
      color: var(--text);
      margin-bottom: 4px;
    }

    .resume-item .meta {
      font-size: 0.78rem;
      color: var(--gold);
      font-weight: 600;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      margin-bottom: 6px;
    }

    .resume-item p, .resume-item li {
      font-size: 0.88rem;
      color: var(--muted);
      line-height: 1.65;
    }

    .resume-item ul { list-style: none; }
    .resume-item li::before { content: '· '; color: var(--gold); font-weight: bold; }

    /* ── SKILLS ── */
    #skills {
      background: var(--dark);
      color: var(--cream);
    }

    #skills .section-title { color: var(--cream); }

    .skills-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 32px;
    }

    .skill-card {
      background: rgba(255,255,255,0.04);
      border: 1px solid rgba(212, 160, 23, 0.2);
      padding: 32px 28px;
      transition: border-color 0.2s, transform 0.2s;
    }

    .skill-card:hover {
      border-color: var(--gold);
      transform: translateY(-4px);
    }

    .skill-card .card-icon {
      font-size: 1.8rem;
      margin-bottom: 16px;
    }

    .skill-card h3 {
      font-family: 'Playfair Display', serif;
      font-size: 1.1rem;
      color: var(--gold);
      margin-bottom: 14px;
    }

    .skill-card ul {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 8px;
    }

    .skill-card li {
      font-size: 0.88rem;
      color: rgba(245, 240, 232, 0.7);
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .skill-card li::before {
      content: '';
      width: 6px;
      height: 6px;
      background: var(--gold);
      border-radius: 50%;
      flex-shrink: 0;
    }

    /* ── FOOTER ── */
    footer {
      background: var(--dark);
      border-top: 1px solid rgba(212, 160, 23, 0.3);
      padding: 32px 72px;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    footer .logo {
      font-family: 'Playfair Display', serif;
      font-size: 1rem;
      color: var(--gold);
      font-weight: 700;
    }

    footer p {
      font-size: 0.8rem;
      color: rgba(245, 240, 232, 0.4);
    }

    /* ── RESPONSIVE ── */
    @media (max-width: 900px) {
      nav { padding: 0 24px; }
      .nav-links { gap: 20px; }

      #home { grid-template-columns: 1fr; min-height: auto; }
      .hero-left { padding: 80px 32px 60px; }
      .hero-right { height: 55vw; }

      section, #about { padding: 64px 32px; }
      .teak-strip { padding: 36px 32px; flex-direction: column; align-items: flex-start; }

      .about-grid,
      .resume-grid,
      .skills-grid { grid-template-columns: 1fr; gap: 32px; }

      footer { flex-direction: column; gap: 8px; padding: 24px 32px; text-align: center; }
    }

    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after { transition: none !important; }
      html { scroll-behavior: auto; }
    }

    /* ── FADE-IN ANIMATION ── */
    .fade-in {
      opacity: 0;
      transform: translateY(20px);
      transition: opacity 0.6s ease, transform 0.6s ease;
    }

    .fade-in.visible {
      opacity: 1;
      transform: none;
    }
  </style>
</head>
<body>

  <!-- NAV -->
  <nav>
    <a href="#home" class="nav-logo">David Akesson</a>
    <ul class="nav-links">
      <li><a href="#home">Home</a></li>
      <li><a href="#about">About</a></li>
      <li><a href="#resume">Resume</a></li>
      <li><a href="#skills">Skills</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <section id="home">
    <div class="hero-left">
      <p class="hero-eyebrow">New York City · 10th Grade</p>
      <h1 class="hero-name">David<br>Akesson</h1>
      <p class="hero-tagline">
        Student, athlete, and TEAK Fellow at The Browning School — driven by science, shaped by sport, and rooted in two cultures.
      </p>
      <div class="hero-flags">
        <div class="flag-bar flag-gh">
          <div class="s1"></div>
          <div class="s2"></div>
          <div class="s3"></div>
        </div>
        <span class="flag-label">Ghanaian–American · Ga &amp; English</span>
      </div>
      <a href="#about" class="hero-cta">Learn More →</a>
    </div>
    <div class="hero-right">
      <!--
        PHOTO INSTRUCTIONS:
        Replace the src below with the path to your basketball photo.
        If you upload it to your GitHub repo, use: src="basketball.jpg"
        Make sure the file is in the same folder as index.html.
      -->
      <img src="basketball.jpg" alt="David Akesson running through a tunnel of teammates in his Browning basketball jersey" />
    </div>
  </section>

  <!-- ABOUT -->
  <section id="about">
    <div class="fade-in">
      <p class="section-label">Who I Am</p>
      <h2 class="section-title">About Me</h2>
    </div>
    <div class="about-grid fade-in">
      <div class="about-text">
        <p>
          My name is David Akesson, and I am a 10th grade student at The Browning School in New York City. I am passionate about science, athletics, and giving back to my community. As a TEAK Fellow since 2022, I have had the opportunity to push myself academically and develop leadership skills that carry into everything I do — from captaining sports teams to editing newsletters.
        </p>
        <p>
          Outside the classroom, I compete on the soccer and basketball teams, and I am always looking for opportunities to grow, collaborate, and make an impact. My goal is to pursue a college education in a STEM-related field, where I can combine my curiosity for science with real-world problem solving.
        </p>
        <p>
          I was born into a Ghanaian family and speak Ga fluently alongside English. That dual identity — New York City kid and proud son of Ghana — shapes how I see the world and how I show up for my community.
        </p>
      </div>
      <div class="about-sidebar">
        <div class="info-block">
          <h4>School</h4>
          <p>The Browning School, New York City<br>Expected Graduation: June 2027</p>
        </div>
        <div class="info-block">
          <h4>Athletics</h4>
          <ul>
            <li>JV Soccer Captain</li>
            <li>Varsity Soccer</li>
            <li>JV Basketball Captain</li>
          </ul>
        </div>
        <div class="info-block">
          <h4>Interests</h4>
          <ul>
            <li>Biology &amp; STEM Research</li>
            <li>Computer Science</li>
            <li>Community Leadership</li>
          </ul>
        </div>
        <div class="info-block">
          <h4>Languages</h4>
          <p>English · Ga (fluent)</p>
        </div>
      </div>
    </div>
  </section>

  <!-- TEAK STRIP -->
  <div class="teak-strip fade-in">
    <!--
      TEAK LOGO INSTRUCTIONS:
      Replace src below with path to your TEAK logo image.
      If uploaded to your repo: src="teak.png"
    -->
    <img src="teak.png" alt="TEAK Fellowship logo" />
    <div class="teak-text">
      <h3>TEAK Fellowship — 20th Cohort</h3>
      <p>
        Member since 6th grade. TEAK has challenged me through rigorous summer institutes and afterschool enrichment, building the academic and leadership foundation I bring to everything I do.
      </p>
    </div>
  </div>

  <!-- RESUME -->
  <section id="resume">
    <div class="fade-in">
      <p class="section-label">Background</p>
      <h2 class="section-title">Resume</h2>
      <div class="divider"></div>
    </div>
    <div class="resume-grid fade-in">
      <div class="resume-col">
        <h3>Education &amp; Programs</h3>

        <div class="resume-item">
          <h4>The Browning School</h4>
          <p class="meta">New York City · Expected June 2027</p>
          <p>College-preparatory school in Manhattan. Coursework includes Biology, Chemistry, Latin III, Pre-Calculus, and Computer Science.</p>
        </div>

        <div class="resume-item">
          <h4>TEAK Fellowship</h4>
          <p class="meta">Member since 2022 · 20th Cohort</p>
          <p>Rigorous academic enrichment program. Summer institutes, leadership development, and college access support.</p>
        </div>

        <h3 style="margin-top:40px;">Leadership &amp; Activities</h3>

        <div class="resume-item">
          <h4>BSU — Black Student Union</h4>
          <p class="meta">Member &amp; Newsletter Editor</p>
          <p>Co-produce a monthly newsletter featuring community shoutouts and school highlights.</p>
        </div>

        <div class="resume-item">
          <h4>BSC — Black Student Coalition</h4>
          <p class="meta">Member</p>
          <p>Participate in networking events, college tours, and community-building initiatives.</p>
        </div>
      </div>

      <div class="resume-col">
        <h3>Athletics</h3>

        <div class="resume-item">
          <h4>JV Basketball Captain</h4>
          <p class="meta">The Browning School</p>
          <p>Led the team to an 11–9 record — the best JV season in recent school history.</p>
        </div>

        <div class="resume-item">
          <h4>JV Soccer Captain</h4>
          <p class="meta">The Browning School</p>
          <p>Captained one of the most successful recent JV soccer seasons at Browning.</p>
        </div>

        <div class="resume-item">
          <h4>Varsity Soccer</h4>
          <p class="meta">The Browning School</p>
          <p>Promoted from JV to varsity — recognition of consistent performance and leadership.</p>
        </div>

        <h3 style="margin-top:40px;">Projects</h3>

        <div class="resume-item">
          <h4>Biology Bahamas Research</h4>
          <p class="meta">Field Research Project</p>
          <p>Investigated the relationship between coral health, water depth, and shore distance. Collected and analyzed field data.</p>
        </div>

        <div class="resume-item">
          <h4>Student Council Campaign</h4>
          <p class="meta">Instagram Campaign · 2025</p>
          <ul>
            <li>Ran for class representative</li>
            <li>Built an Instagram campaign from scratch</li>
            <li>Grew account to 47 followers with 1.5k post views</li>
          </ul>
        </div>
      </div>
    </div>
  </section>

  <!-- SKILLS -->
  <section id="skills">
    <div class="fade-in">
      <p class="section-label">What I Bring</p>
      <h2 class="section-title">Skills</h2>
      <div class="divider"></div>
    </div>
    <div class="skills-grid fade-in">
      <div class="skill-card">
        <div class="card-icon">💻</div>
        <h3>Technical</h3>
        <ul>
          <li>Python (Intro CS)</li>
          <li>GitHub &amp; version control</li>
          <li>Data collection &amp; analysis</li>
          <li>Basic HTML/CSS</li>
        </ul>
      </div>

      <div class="skill-card">
        <div class="card-icon">📚</div>
        <h3>Academic</h3>
        <ul>
          <li>Biology &amp; Chemistry</li>
          <li>History &amp; Social Studies</li>
          <li>Latin III</li>
          <li>Pre-Calculus</li>
        </ul>
      </div>

      <div class="skill-card">
        <div class="card-icon">🤝</div>
        <h3>Leadership</h3>
        <ul>
          <li>Team captaincy</li>
          <li>Communication</li>
          <li>Community organizing</li>
          <li>Newsletter editing</li>
        </ul>
      </div>

      <div class="skill-card">
        <div class="card-icon">🌍</div>
        <h3>Languages</h3>
        <ul>
          <li>English (native)</li>
          <li>Ga (fluent)</li>
        </ul>
      </div>

      <div class="skill-card">
        <div class="card-icon">⚽</div>
        <h3>Athletics</h3>
        <ul>
          <li>Soccer (JV Captain + Varsity)</li>
          <li>Basketball (JV Captain)</li>
          <li>Track &amp; Field</li>
          <li>Team strategy &amp; film study</li>
        </ul>
      </div>

      <div class="skill-card">
        <div class="card-icon">🔬</div>
        <h3>Research</h3>
        <ul>
          <li>Field data collection</li>
          <li>Scientific writing</li>
          <li>Lab technique</li>
          <li>Environmental biology</li>
        </ul>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <span class="logo">David Akesson</span>
    <p>The Browning School · TEAK Fellow · New York City</p>
    <p>© 2026</p>
  </footer>

  <script>
    // Intersection Observer for fade-in animations
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible');
        }
      });
    }, { threshold: 0.1 });

    document.querySelectorAll('.fade-in').forEach(el => observer.observe(el));
  </script>
</body>
</html>
