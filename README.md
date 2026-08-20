<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Developer Portfolio</title>
  <style>
    :root {
      --bg: #0d1117;
      --card: #161b22;
      --border: #30363d;
      --text: #c9d1d9;
      --accent: #58a6ff;
    }
    body {
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
      background: var(--bg);
      color: var(--text);
      margin: 0;
      padding: 2rem 1rem;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    .profile-header {
      text-align: center;
      max-width: 600px;
    }
    .avatar {
      width: 120px;
      height: 120px;
      border-radius: 50%;
      border: 3px solid var(--accent);
    }
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 1rem;
      width: 100%;
      max-width: 900px;
      margin-top: 2rem;
    }
    .card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 1.25rem;
      text-decoration: none;
      color: inherit;
      transition: transform 0.2s, border-color 0.2s;
    }
    .card:hover {
      transform: translateY(-3px);
      border-color: var(--accent);
    }
    .card h3 {
      margin: 0 0 0.5rem 0;
      color: var(--accent);
    }
    .meta {
      font-size: 0.85rem;
      color: #8b949e;
      margin-top: 1rem;
    }
  </style>
</head>
<body>
  <div class="profile-header">
    <img id="avatar" class="avatar" src="" alt="Avatar" />
    <h1 id="name" style="margin: 0.5rem 0 0.2rem;"></h1>
    <p id="bio" style="color: #8b949e;"></p>
    <a id="github-link" href="#" target="_blank" style="color: var(--accent);">View GitHub Profile →</a>
  </div>

  <div id="repos" class="grid"></div>

  <script>
    const USERNAME = 'bhosalepranali2005-web';

    async function loadProfile() {
      // 1. Fetch user data
      const userRes = await fetch(`https://api.github.com/users/${USERNAME}`);
      const user = await userRes.json();

      document.getElementById('avatar').src = user.avatar_url;
      document.getElementById('name').textContent = user.name || user.login;
      document.getElementById('bio').textContent = user.bio || 'Developer';
      document.getElementById('github-link').href = user.html_url;

      // 2. Fetch public repos sorted by updated date
      const reposRes = await fetch(`https://api.github.com/users/${USERNAME}/repos?sort=updated&per_page=6`);
      const repos = await reposRes.json();

      const container = document.getElementById('repos');
      container.innerHTML = repos.map(repo => `
        <a class="card" href="${repo.html_url}" target="_blank">
          <h3>${repo.name}</h3>
          <p style="font-size: 0.9rem; margin: 0;">${repo.description || 'No description provided.'}</p>
          <div class="meta">
            ★ ${repo.stargazers_count} | ⑂ ${repo.forks_count} ${repo.language ? `| ${repo.language}` : ''}
          </div>
        </a>
      `).join('');
    }

    loadProfile();
  </script>
</body>
</html>
