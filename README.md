<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Pranali Bhosale | Engineering Portfolio</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;600;800&family=JetBrains+Mono:wght@400;600&display=swap" rel="stylesheet">
  
  <style>
    :root {
      --bg: #0b0f19;
      --card-bg: rgba(22, 27, 34, 0.75);
      --border: rgba(255, 255, 255, 0.08);
      --accent: #58a6ff;
      --accent-glow: rgba(88, 166, 255, 0.15);
      --purple: #bc8cff;
      --text: #e6edf3;
      --muted: #8b949e;
      --radius: 12px;
    }

    * { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      font-family: 'Plus Jakarta Sans', sans-serif;
      background-color: var(--bg);
      color: var(--text);
      line-height: 1.6;
      background-image: 
        radial-gradient(at 0% 0%, rgba(88, 166, 255, 0.08) 0px, transparent 50%),
        radial-gradient(at 100% 100%, rgba(188, 140, 255, 0.08) 0px, transparent 50%);
      background-attachment: fixed;
      padding: 3rem 1.5rem;
    }

    .container {
      max-width: 1050px;
      margin: 0 auto;
    }

    /* Hero Section */
    .hero {
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      padding-bottom: 3.5rem;
      border-bottom: 1px solid var(--border);
    }

    .avatar-wrapper {
      position: relative;
      margin-bottom: 1.5rem;
    }

    .avatar {
      width: 130px;
      height: 130px;
      border-radius: 50%;
      border: 3px solid var(--accent);
      box-shadow: 0 0 25px var(--accent-glow);
    }

    .badge-status {
      position: absolute;
      bottom: 6px;
      right: 6px;
      background: #238636;
      border: 2px solid var(--bg);
      width: 18px;
      height: 18px;
      border-radius: 50%;
    }

    h1 {
      font-size: 2.5rem;
      font-weight: 800;
      letter-spacing: -0.03em;
      margin-bottom: 0.4rem;
    }

    .subtitle {
      font-family: 'JetBrains Mono', monospace;
      color: var(--accent);
      font-size: 1rem;
      margin-bottom: 1rem;
    }

    .bio {
      max-width: 650px;
      color: var(--muted);
      font-size: 1.05rem;
      margin-bottom: 1.5rem;
    }

    .social-links {
      display: flex;
      gap: 1rem;
      flex-wrap: wrap;
    }

    .btn {
      padding: 0.6rem 1.25rem;
      border-radius: var(--radius);
      text-decoration: none;
      font-weight: 600;
      font-size: 0.9rem;
      transition: all 0.2s ease;
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
    }

    .btn-primary {
      background: var(--accent);
      color: #0d1117;
    }

    .btn-primary:hover {
      background: #79c0ff;
      transform: translateY(-2px);
    }

    .btn-secondary {
      background: rgba(255, 255, 255, 0.05);
      color: var(--text);
      border: 1px solid var(--border);
    }

    .btn-secondary:hover {
      background: rgba(255, 255, 255, 0.1);
      transform: translateY(-2px);
    }

    /* Section Headings */
    .section-title {
      font-size: 1.5rem;
      font-weight: 700;
      margin: 3.5rem 0 1.5rem 0;
      display: flex;
      align-items: center;
      gap: 0.75rem;
    }

    .section-title::after {
      content: '';
      flex: 1;
      height: 1px;
      background: var(--border);
    }

    /* Skills Grid */
    .skills-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 1rem;
    }

    .skill-card {
      background: var(--card-bg);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 1.25rem;
      backdrop-filter: blur(8px);
    }

    .skill-card h3 {
      font-size: 1rem;
      color: var(--purple);
      margin-bottom: 0.75rem;
    }

    .tag-container {
      display: flex;
      flex-wrap: wrap;
      gap: 0.4rem;
    }

    .tag {
      font-size: 0.78rem;
      font-family: 'JetBrains Mono', monospace;
      background: rgba(255, 255, 255, 0.04);
      padding: 0.25rem 0.6rem;
      border-radius: 6px;
      border: 1px solid var(--border);
    }

    /* Dynamic Repos Grid */
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(310px, 1fr));
      gap: 1.25rem;
    }

    .card {
      background: var(--card-bg);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 1.5rem;
      text-decoration: none;
      color: inherit;
      backdrop-filter: blur(8px);
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
    }

    .card:hover {
      transform: translateY(-4px);
      border-color: var(--accent);
      box-shadow: 0 8px 24px rgba(0,0,0,0.35);
    }

    .card h3 {
      font-size: 1.15rem;
      color: var(--accent);
      margin-bottom: 0.5rem;
      word-break: break-word;
    }

    .card p {
      font-size: 0.9rem;
      color: var(--muted);
      margin-bottom: 1.25rem;
      flex-grow: 1;
    }

    .meta {
      font-size: 0.8rem;
      color: var(--muted);
      font-family: 'JetBrains Mono', monospace;
      display: flex;
      gap: 1rem;
      align-items: center;
    }

    .lang-dot {
      display: inline-block;
      width: 8px;
      height: 8px;
      border-radius: 50%;
      background: var(--purple);
      margin-right: 4px;
    }
  </style>
</head>
<body>

  <div class="container">
    <!-- Header / Bio -->
    <header class="hero">
      <div class="avatar-wrapper">
        <img id="avatar" class="avatar" src="https://github.com/bhosalepranali2005.png" alt="Pranali Bhosale" />
        <span class="badge-status" title="Open to Opportunities"></span>
      </div>
      <h1 id="name">Pranali Pravin Bhosale</h1>
      <p class="subtitle">Electronics & Telecommunication Engineer | IoT & Embedded AI</p>
      <p id="bio" class="bio">
        Passionate about bridging hardware intelligence and modern software architectures. Exploring Swarm IoT, Embedded Systems, and AI-driven automation.
      </p>
      <div class="social-links">
        <a id="github-link" class="btn btn-primary" href="https://github.com/bhosalepranali2005" target="_blank">
          GitHub Profile ↗
        </a>
        <a class="btn btn-secondary" href="mailto:your-email@example.com">
          Contact Me
        </a>
      </div>
    </header>

    <!-- Technical Stack Section -->
    <h2 class="section-title">Core Competencies</h2>
    <div class="skills-grid">
      <div class="skill-card">
        <h3>Hardware & Embedded</h3>
        <div class="tag-container">
          <span class="tag">ESP32</span>
          <span class="tag">LPC2148</span>
          <span class="tag">STM32</span>
          <span class="tag">Swarm IoT</span>
          <span class="tag">SCADA / DCS</span>
        </div>
      </div>
      <div class="skill-card">
        <h3>AI & Computer Vision</h3>
        <div class="tag-container">
          <span class="tag">YOLO Models</span>
          <span class="tag">OpenCV</span>
          <span class="tag">TensorFlow</span>
          <span class="tag">scikit-learn</span>
        </div>
      </div>
      <div class="skill-card">
        <h3>Software & Tools</h3>
        <div class="tag-container">
          <span class="tag">Python</span>
          <span class="tag">C / Embedded C</span>
          <span class="tag">React</span>
          <span class="tag">Node.js</span>
          <span class="tag">Git</span>
        </div>
      </div>
    </div>

    <!-- Pinned / Public Repositories -->
    <h2 class="section-title">Featured Projects & Repositories</h2>
    <div id="repos" class="grid">
      <!-- Repositories loaded via JavaScript -->
    </div>
  </div>

  <script>
    const USERNAME = 'bhosalepranali2005';

    async function fetchGitHubData() {
      try {
        // Fetch User Info
        const userRes = await fetch(`https://api.github.com/users/${USERNAME}`);
        if (userRes.ok) {
          const user = await userRes.json();
          if (user.bio) document.getElementById('bio').textContent = user.bio;
          if (user.name) document.getElementById('name').textContent = user.name;
        }

        // Fetch Repositories
        const reposRes = await fetch(`https://api.github.com/users/${USERNAME}/repos?sort=pushed&per_page=6`);
        if (!reposRes.ok) throw new Error('Failed to fetch repositories');
        
        const repos = await reposRes.json();
        const container = document.getElementById('repos');

        container.innerHTML = repos
          .filter(repo => !repo.fork)
          .slice(0, 6)
          .map(repo => `
            <a class="card" href="${repo.html_url}" target="_blank">
              <div>
                <h3>${repo.name}</h3>
                <p>${repo.description || 'Smart hardware, automation, and algorithmic engineering repository.'}</p>
              </div>
              <div class="meta">
                ${repo.language ? `<span><span class="lang-dot"></span>${repo.language}</span>` : ''}
                <span>★ ${repo.stargazers_count}</span>
                <span>⑂ ${repo.forks_count}</span>
              </div>
            </a>
          `).join('');
      } catch (err) {
        document.getElementById('repos').innerHTML = `
          <p style="color: var(--muted); grid-column: 1 / -1;">
            Unable to load live repositories directly. Check back soon or visit GitHub directly.
          </p>
        `;
      }
    }

    fetchGitHubData();
  </script>
</body>
</html>
