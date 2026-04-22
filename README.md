<!DOCTYPE html>
<html lang="en" data-theme="dark">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Jeeva G — Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;600;700&family=Outfit:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
<style>

/* ============================================================ THEME */
[data-theme="dark"] {
  --bg: #080b12; --bg2: #0d1117; --panel: #111820; --card: #111820;
  --card-hover: #161e2d; --border: rgba(255,255,255,0.06);
  --border-hover: rgba(88,166,255,0.35); --text: #cdd9e5;
  --text-strong: #e6edf3; --muted: #4a5568; --muted2: #374151;
  --shadow: rgba(0,0,0,0.5); --tab-active-txt: #000;
  --toggle-bg: #1c2433; --toggle-border: rgba(255,255,255,0.1);
  --stat-num: #e6edf3; --tooltip-bg: #1c2433;
  --tooltip-border: rgba(255,255,255,0.1); --header-sub: #4a5568;
  --divider: rgba(255,255,255,0.05); --tag-bg: rgba(255,255,255,0.05);
  --tag-border: rgba(255,255,255,0.08); --hero-border: rgba(88,166,255,0.12);
  --project-card: #0f1620;
}
[data-theme="light"] {
  --bg: #f0f4f8; --bg2: #e8edf3; --panel: #ffffff; --card: #ffffff;
  --card-hover: #f8fafc; --border: rgba(0,0,0,0.08);
  --border-hover: rgba(37,99,235,0.4); --text: #1e293b;
  --text-strong: #0f172a; --muted: #94a3b8; --muted2: #cbd5e1;
  --shadow: rgba(0,0,0,0.12); --tab-active-txt: #ffffff;
  --toggle-bg: #e2e8f0; --toggle-border: rgba(0,0,0,0.08);
  --stat-num: #0f172a; --tooltip-bg: #1e293b;
  --tooltip-border: rgba(0,0,0,0.15); --header-sub: #94a3b8;
  --divider: rgba(0,0,0,0.06); --tag-bg: rgba(0,0,0,0.04);
  --tag-border: rgba(0,0,0,0.08); --hero-border: rgba(37,99,235,0.12);
  --project-card: #f8fafc;
}

/* ============================================================ RESET */
*,*::before,*::after { margin:0; padding:0; box-sizing:border-box; }
html { scroll-behavior:smooth; }
body {
  background:var(--bg); color:var(--text);
  font-family:'Outfit',sans-serif; min-height:100vh;
  display:flex; align-items:flex-start; justify-content:center;
  padding:48px 24px 80px;
  transition:background 0.35s ease,color 0.35s ease; position:relative;
}
body::before {
  content:''; position:fixed; inset:0;
  background:radial-gradient(ellipse 80% 50% at 50% -10%, rgba(88,166,255,0.07) 0%, transparent 60%),
             radial-gradient(ellipse 60% 40% at 80% 100%, rgba(57,208,216,0.05) 0%, transparent 60%);
  pointer-events:none; z-index:0;
}
.page { width:100%; max-width:940px; position:relative; z-index:1; }
a { color:inherit; text-decoration:none; }

/* ============================================================ THEME TOGGLE */
.theme-toggle {
  position:fixed; top:24px; right:24px; z-index:100;
  background:var(--toggle-bg); border:1px solid var(--toggle-border);
  border-radius:100px; padding:6px; display:flex; gap:4px;
  box-shadow:0 4px 20px var(--shadow); transition:background 0.3s,border 0.3s;
}
.theme-btn {
  width:36px; height:36px; border-radius:100px; border:none;
  background:transparent; cursor:pointer; display:flex;
  align-items:center; justify-content:center; font-size:16px;
  transition:all 0.2s ease; color:var(--muted);
}
.theme-btn:hover { background:var(--border); color:var(--text); }
.theme-btn.active { background:var(--text-strong); color:var(--bg); box-shadow:0 2px 8px var(--shadow); }

/* ============================================================ SECTION DIVIDER */
.section-divider {
  display:flex; align-items:center; gap:16px; margin:48px 0 32px;
}
.section-divider-line { flex:1; height:1px; background:var(--divider); }
.section-divider-label {
  font-family:'JetBrains Mono',monospace; font-size:11px;
  letter-spacing:0.2em; text-transform:uppercase; color:var(--muted);
  white-space:nowrap;
}

/* ============================================================ HERO */
.hero {
  display:grid; grid-template-columns:1fr auto;
  gap:32px; align-items:center;
  background:var(--panel); border:1px solid var(--hero-border);
  border-radius:20px; padding:36px 40px;
  margin-bottom:0;
  box-shadow:0 8px 40px var(--shadow);
  position:relative; overflow:hidden;
}
.hero::before {
  content:''; position:absolute; top:0; left:0; right:0; height:2px;
  background:linear-gradient(90deg, transparent, #58a6ff 40%, #39d0d8 60%, transparent);
}
.hero-left {}
.hero-eyebrow {
  font-family:'JetBrains Mono',monospace; font-size:11px;
  letter-spacing:0.22em; text-transform:uppercase; color:#58a6ff;
  margin-bottom:12px; display:flex; align-items:center; gap:8px;
}
.hero-eyebrow-dot { width:5px; height:5px; background:#58a6ff; border-radius:50%; box-shadow:0 0 6px #58a6ff; }
.hero h1 {
  font-size:clamp(30px,5vw,46px); font-weight:800; color:var(--text-strong);
  letter-spacing:-0.03em; line-height:1.1; margin-bottom:8px;
}
.hero h1 .accent {
  background:linear-gradient(135deg,#58a6ff,#39d0d8);
  -webkit-background-clip:text; -webkit-text-fill-color:transparent; background-clip:text;
}
.hero-role {
  font-size:15px; color:var(--muted); margin-bottom:20px; font-weight:400;
}
.hero-bio {
  font-size:14px; line-height:1.75; color:var(--text); max-width:480px;
  margin-bottom:24px; opacity:0.85;
}
.hero-tags { display:flex; flex-wrap:wrap; gap:8px; margin-bottom:28px; }
.hero-tag {
  font-family:'JetBrains Mono',monospace; font-size:10px;
  letter-spacing:0.06em; padding:5px 12px; border-radius:100px;
  border:1px solid var(--tag-border); background:var(--tag-bg);
  color:var(--muted); white-space:nowrap;
}
.hero-tag.highlight {
  border-color:rgba(88,166,255,0.3); color:#58a6ff;
  background:rgba(88,166,255,0.08);
}
.hero-links { display:flex; gap:10px; flex-wrap:wrap; }
.hero-link {
  display:flex; align-items:center; gap:7px;
  font-family:'JetBrains Mono',monospace; font-size:11px;
  padding:8px 16px; border-radius:8px;
  border:1px solid var(--border); background:var(--card);
  color:var(--text); transition:all 0.2s ease; cursor:pointer;
  letter-spacing:0.04em;
}
.hero-link:hover { border-color:rgba(88,166,255,0.4); color:#58a6ff; background:var(--card-hover); transform:translateY(-1px); }
.hero-link svg { width:14px; height:14px; opacity:0.8; flex-shrink:0; }
.hero-right {
  display:flex; flex-direction:column; align-items:center; gap:12px;
}
.hero-avatar {
  width:110px; height:110px; border-radius:50%;
  background:linear-gradient(135deg,rgba(88,166,255,0.15),rgba(57,208,216,0.1));
  border:2px solid rgba(88,166,255,0.2);
  display:flex; align-items:center; justify-content:center;
  font-size:40px; font-weight:800; color:#58a6ff;
  font-family:'Outfit',sans-serif; letter-spacing:-0.02em;
  flex-shrink:0; box-shadow:0 0 30px rgba(88,166,255,0.1);
}
.hero-badge {
  font-family:'JetBrains Mono',monospace; font-size:9px;
  letter-spacing:0.1em; padding:4px 12px; border-radius:100px;
  border:1px solid rgba(88,166,255,0.25); background:rgba(88,166,255,0.08);
  color:#58a6ff; white-space:nowrap; text-transform:uppercase;
}
.hero-location {
  font-family:'JetBrains Mono',monospace; font-size:10px;
  color:var(--muted); display:flex; align-items:center; gap:5px;
}

/* ============================================================ QUICK STATS */
.quick-stats {
  display:grid; grid-template-columns:repeat(4,1fr); gap:10px; margin-top:14px;
}
.qs-card {
  background:var(--panel); border:1px solid var(--border); border-radius:12px;
  padding:16px 12px; text-align:center; transition:all 0.2s ease;
}
.qs-card:hover { border-color:rgba(88,166,255,0.2); transform:translateY(-2px); }
.qs-icon { font-size:16px; margin-bottom:5px; }
.qs-num {
  font-family:'JetBrains Mono',monospace; font-size:20px; font-weight:700;
  color:var(--stat-num); margin-bottom:3px;
}
.qs-lbl { font-size:11px; color:var(--muted); }

/* ============================================================ PROJECTS */
.projects-grid { display:grid; grid-template-columns:1fr 1fr; gap:12px; }
.proj-card {
  background:var(--project-card); border:1px solid var(--border);
  border-radius:14px; padding:20px 22px;
  transition:all 0.25s ease; position:relative; overflow:hidden; cursor:default;
}
.proj-card::before {
  content:''; position:absolute; left:0; top:0; bottom:0; width:3px;
  background:var(--proj-color,#58a6ff); border-radius:3px 0 0 3px;
}
.proj-card:hover {
  border-color:var(--proj-color,rgba(88,166,255,0.3));
  background:var(--card-hover); transform:translateY(-3px);
  box-shadow:0 8px 28px var(--shadow);
}
.proj-header { display:flex; align-items:flex-start; justify-content:space-between; margin-bottom:8px; gap:10px; }
.proj-name { font-size:14px; font-weight:700; color:var(--text-strong); }
.proj-badge {
  font-family:'JetBrains Mono',monospace; font-size:9px; padding:3px 9px;
  border-radius:100px; background:rgba(255,186,0,0.12); color:#f0a500;
  border:1px solid rgba(255,186,0,0.2); white-space:nowrap; flex-shrink:0;
}
.proj-badge.normal { background:var(--tag-bg); color:var(--muted); border-color:var(--tag-border); }
.proj-desc { font-size:12.5px; color:var(--muted); line-height:1.65; }
.proj-tags { display:flex; flex-wrap:wrap; gap:5px; margin-top:12px; }
.proj-tag {
  font-family:'JetBrains Mono',monospace; font-size:9px; padding:3px 8px;
  border-radius:4px; background:var(--tag-bg); border:1px solid var(--tag-border);
  color:var(--muted);
}

/* ============================================================ GITHUB STREAK */
.streak-wrap {
  background:var(--panel); border:1px solid var(--border); border-radius:14px;
  padding:24px; text-align:center; overflow:hidden;
}
.streak-wrap img { max-width:100%; border-radius:8px; opacity:0.9; }
[data-theme="light"] .streak-wrap img { filter:invert(1) hue-rotate(180deg) brightness(0.85); }

/* ============================================================ SKILLS SECTION (original) */
.search-wrap { position:relative; max-width:320px; margin:0 auto 28px; }
.search-icon {
  position:absolute; left:14px; top:50%; transform:translateY(-50%);
  color:var(--muted); font-size:14px; pointer-events:none;
}
.search-input {
  width:100%; background:var(--panel); border:1px solid var(--border);
  border-radius:10px; padding:10px 14px 10px 38px;
  font-family:'JetBrains Mono',monospace; font-size:12px;
  color:var(--text); outline:none; transition:all 0.2s ease;
}
.search-input::placeholder { color:var(--muted); }
.search-input:focus { border-color:rgba(88,166,255,0.4); box-shadow:0 0 0 3px rgba(88,166,255,0.08); }
[data-theme="light"] .search-input { background:#fff; }

.tabs { display:flex; gap:6px; justify-content:center; margin-bottom:32px; flex-wrap:wrap; }
.tab {
  font-family:'JetBrains Mono',monospace; font-size:11px; letter-spacing:0.06em;
  padding:7px 18px; border-radius:100px; border:1px solid var(--border);
  background:var(--panel); color:var(--muted); cursor:pointer;
  transition:all 0.2s ease; text-transform:lowercase;
  display:flex; align-items:center; gap:6px;
}
.tab:hover { border-color:rgba(88,166,255,0.3); color:var(--text); background:var(--card-hover); }
.tab.active { background:#58a6ff; border-color:#58a6ff; color:var(--tab-active-txt); font-weight:700; box-shadow:0 2px 12px rgba(88,166,255,0.3); }
.tab-count { font-size:9px; opacity:0.7; background:rgba(255,255,255,0.15); padding:1px 5px; border-radius:100px; }
.tab.active .tab-count { background:rgba(0,0,0,0.15); }

.sort-row { display:flex; align-items:center; justify-content:flex-end; gap:8px; margin-bottom:16px; }
.sort-label { font-family:'JetBrains Mono',monospace; font-size:10px; color:var(--muted); letter-spacing:0.1em; text-transform:uppercase; }
.sort-btn {
  font-family:'JetBrains Mono',monospace; font-size:10px; padding:4px 12px;
  border-radius:6px; border:1px solid var(--border); background:var(--panel);
  color:var(--muted); cursor:pointer; transition:all 0.2s;
}
.sort-btn:hover,.sort-btn.active { border-color:rgba(88,166,255,0.3); color:#58a6ff; }

.skills-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(136px,1fr)); gap:10px; position:relative; }

.skill-card {
  background:var(--card); border:1px solid var(--border); border-radius:14px;
  padding:22px 14px 16px; text-align:center; cursor:default; position:relative;
  overflow:hidden; opacity:0; transform:translateY(14px) scale(0.97);
  animation:cardIn 0.45s cubic-bezier(0.4,0,0.2,1) forwards;
  transition:transform 0.25s cubic-bezier(0.4,0,0.2,1),border-color 0.25s,box-shadow 0.25s,background 0.25s,opacity 0.3s;
}
.skill-card::after {
  content:''; position:absolute; inset:0;
  background:radial-gradient(circle at 50% 0%,var(--glow-color,transparent) 0%,transparent 65%);
  opacity:0; transition:opacity 0.3s; border-radius:14px; pointer-events:none;
}
.skill-card:hover {
  transform:translateY(-5px) scale(1.025); background:var(--card-hover);
  box-shadow:0 12px 40px var(--shadow),0 0 0 1px var(--cat-color,#58a6ff) inset;
  border-color:var(--cat-color,#58a6ff); z-index:2;
}
.skill-card:hover::after { opacity:1; }
.skill-card:hover .skill-icon { transform:scale(1.15) rotate(-4deg); }
.skill-card:hover .skill-icon img { filter:brightness(1.15) drop-shadow(0 0 6px var(--cat-color,#58a6ff)); }
.skill-card:hover .prof-bar { box-shadow:0 0 8px var(--cat-color,#58a6ff); }
@keyframes cardIn { to { opacity:1; transform:translateY(0) scale(1); } }

.cat-dot { position:absolute; top:10px; right:10px; width:6px; height:6px; border-radius:50%; background:var(--cat-color); opacity:0.75; box-shadow:0 0 4px var(--cat-color); }
.skill-icon { width:52px; height:52px; margin:0 auto 13px; border-radius:12px; display:flex; align-items:center; justify-content:center; transition:transform 0.25s cubic-bezier(0.4,0,0.2,1); background:var(--icon-bg,rgba(255,255,255,0.04)); }
[data-theme="light"] .skill-icon { background:var(--icon-bg,rgba(0,0,0,0.04)); }
.skill-icon img { width:34px; height:34px; object-fit:contain; transition:filter 0.25s; }
.skill-icon .fallback { font-family:'Outfit',sans-serif; font-size:18px; font-weight:800; color:var(--cat-color); }
.skill-name { font-size:12px; font-weight:600; color:var(--text-strong); margin-bottom:8px; line-height:1.3; transition:color 0.3s; }
.prof-wrap { height:2px; background:var(--border); border-radius:2px; overflow:visible; margin-bottom:7px; position:relative; }
.prof-bar { height:100%; border-radius:2px; width:0%; background:var(--cat-color); transition:width 1s cubic-bezier(0.4,0,0.2,1),box-shadow 0.25s; position:relative; }
.prof-bar::after { content:''; position:absolute; right:0; top:50%; transform:translateY(-50%); width:5px; height:5px; border-radius:50%; background:var(--cat-color); box-shadow:0 0 4px var(--cat-color); opacity:0; transition:opacity 0.4s; }
.skill-card:hover .prof-bar::after { opacity:1; }
.prof-label { font-family:'JetBrains Mono',monospace; font-size:9px; color:var(--muted); letter-spacing:0.06em; }
.skill-tooltip { position:absolute; bottom:calc(100% + 10px); left:50%; transform:translateX(-50%) translateY(6px); background:var(--tooltip-bg); border:1px solid var(--tooltip-border); border-radius:8px; padding:7px 14px; font-family:'JetBrains Mono',monospace; font-size:10px; white-space:nowrap; color:var(--text-strong); pointer-events:none; opacity:0; transition:opacity 0.2s ease,transform 0.2s ease; z-index:20; box-shadow:0 4px 16px var(--shadow); }
.skill-tooltip::after { content:''; position:absolute; top:100%; left:50%; transform:translateX(-50%); border:4px solid transparent; border-top-color:var(--tooltip-border); }
.skill-card:hover .skill-tooltip { opacity:1; transform:translateX(-50%) translateY(0); }

.empty-state { grid-column:1/-1; text-align:center; padding:48px 20px; color:var(--muted); font-size:14px; display:none; }
.empty-state.show { display:block; }

.legend { display:flex; gap:20px; justify-content:center; flex-wrap:wrap; margin-top:22px; margin-bottom:4px; }
.legend-item { display:flex; align-items:center; gap:6px; font-family:'JetBrains Mono',monospace; font-size:10px; color:var(--muted); letter-spacing:0.06em; text-transform:lowercase; }
.legend-dot { width:7px; height:7px; border-radius:50%; box-shadow:0 0 5px currentColor; }

/* ============================================================ RESPONSIVE */
@media(max-width:700px) {
  .hero { grid-template-columns:1fr; padding:28px 24px; }
  .hero-right { flex-direction:row; justify-content:flex-start; }
  .projects-grid { grid-template-columns:1fr; }
  .quick-stats { grid-template-columns:repeat(2,1fr); }
  .skills-grid { grid-template-columns:repeat(3,1fr); gap:8px; }
  .theme-toggle { top:16px; right:16px; }
  body { padding:32px 16px 64px; }
  .sort-row { justify-content:center; }
}
@media(max-width:380px) { .skills-grid { grid-template-columns:repeat(2,1fr); } }

</style>
</head>
<body>

<!-- THEME TOGGLE -->
<div class="theme-toggle" role="group" aria-label="Theme selector">
  <button class="theme-btn active" id="btn-dark" title="Dark" onclick="setTheme('dark')">🌙</button>
  <button class="theme-btn" id="btn-light" title="Light" onclick="setTheme('light')">☀️</button>
</div>

<div class="page">

  <!-- ══════════════════════ HERO ══════════════════════ -->
  <div class="hero">
    <div class="hero-left">
      <div class="hero-eyebrow"><span class="hero-eyebrow-dot"></span>developer · india</div>
      <h1>Jeeva <span class="accent">G</span></h1>
      <div class="hero-role">Building Real-World Applications</div>
      <p class="hero-bio">
        I build software that solves real-world problems — focusing on practical,
        scalable solutions rather than academic projects. My work spans FinTech,
        AgriTech, RAG systems, and student-focused platforms.
      </p>
      <div class="hero-tags">
        <span class="hero-tag highlight">🏆 Hackathon Winner</span>
        <span class="hero-tag">M.Tech CSE · SSN</span>
        <span class="hero-tag">FinTech</span>
        <span class="hero-tag">AgriTech</span>
        <span class="hero-tag">RAG</span>
      </div>
      <div class="hero-links">
        <a class="hero-link" href="https://github.com/jeeva2470041" target="_blank">
          <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z"/></svg>
          GitHub
        </a>
        <a class="hero-link" href="https://www.linkedin.com/in/jeevain/" target="_blank">
          <svg viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
          LinkedIn
        </a>
        <a class="hero-link" href="https://jeeva-g.vercel.app/" target="_blank">
          <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-1 17.93c-3.95-.49-7-3.85-7-7.93 0-.62.08-1.21.21-1.79L9 15v1c0 1.1.9 2 2 2v1.93zm6.9-2.54c-.26-.81-1-1.39-1.9-1.39h-1v-3c0-.55-.45-1-1-1H8v-2h2c.55 0 1-.45 1-1V7h2c1.1 0 2-.9 2-2v-.41c2.93 1.19 5 4.06 5 7.41 0 2.08-.8 3.97-2.1 5.39z"/></svg>
          Portfolio
        </a>
        <a class="hero-link" href="mailto:priyagovinth2019@gmail.com">
          <svg viewBox="0 0 24 24" fill="currentColor"><path d="M20 4H4c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/></svg>
          Email
        </a>
      </div>
    </div>
    <div class="hero-right">
      <div class="hero-avatar">JG</div>
      <div class="hero-badge">🏆 Hackathon Winner</div>
      <div class="hero-location">📍 India</div>
    </div>
  </div>

  <!-- ══════════════════════ QUICK STATS ══════════════════════ -->
  <div class="quick-stats" style="margin-top:14px;">
    <div class="qs-card"><div class="qs-icon">⚡</div><div class="qs-num">20</div><div class="qs-lbl">Skills Listed</div></div>
    <div class="qs-card"><div class="qs-icon">🚀</div><div class="qs-num">7</div><div class="qs-lbl">Projects Built</div></div>
    <div class="qs-card"><div class="qs-icon">🏆</div><div class="qs-num">1st</div><div class="qs-lbl">Hackathon Place</div></div>
    <div class="qs-card"><div class="qs-icon">🎓</div><div class="qs-num">SSN</div><div class="qs-lbl">M.Tech CSE</div></div>
  </div>

  <!-- ══════════════════════ PROJECTS ══════════════════════ -->
  <div class="section-divider">
    <div class="section-divider-line"></div>
    <div class="section-divider-label">🚀 projects</div>
    <div class="section-divider-line"></div>
  </div>

  <div class="projects-grid">
    <div class="proj-card" style="--proj-color:#f0a500">
      <div class="proj-header">
        <div class="proj-name">PayTrace</div>
        <div class="proj-badge">🏆 Winner</div>
      </div>
      <div class="proj-desc">Smart expense tracking using SMS &amp; notification data. Built for the hackathon and took first place.</div>
      <div class="proj-tags">
        <span class="proj-tag">Python</span>
        <span class="proj-tag">Flutter</span>
        <span class="proj-tag">MLflow</span>
        <span class="proj-tag">FinTech</span>
      </div>
    </div>
    <div class="proj-card" style="--proj-color:#3fb950">
      <div class="proj-header">
        <div class="proj-name">AgriAssist</div>
        <div class="proj-badge normal">AgriTech</div>
      </div>
      <div class="proj-desc">AI-powered farmer support app with disease analysis and crop recommendation engine.</div>
      <div class="proj-tags">
        <span class="proj-tag">Flutter</span>
        <span class="proj-tag">Flask</span>
        <span class="proj-tag">Python</span>
        <span class="proj-tag">ML</span>
      </div>
    </div>
    <div class="proj-card" style="--proj-color:#39d0d8">
      <div class="proj-header">
        <div class="proj-name">EcoFeed</div>
        <div class="proj-badge normal">Social Impact</div>
      </div>
      <div class="proj-desc">NGO-based food redistribution platform with real-time location-based alerts for donors and recipients.</div>
      <div class="proj-tags">
        <span class="proj-tag">React</span>
        <span class="proj-tag">MongoDB</span>
        <span class="proj-tag">Flask</span>
      </div>
    </div>
    <div class="proj-card" style="--proj-color:#58a6ff">
      <div class="proj-header">
        <div class="proj-name">CampusShare</div>
        <div class="proj-badge normal">IIT KGP Hack</div>
      </div>
      <div class="proj-desc">Peer-to-peer student sharing platform built during the IIT Kharagpur hackathon.</div>
      <div class="proj-tags">
        <span class="proj-tag">Firebase</span>
        <span class="proj-tag">Flutter</span>
        <span class="proj-tag">Dart</span>
      </div>
    </div>
    <div class="proj-card" style="--proj-color:#bc8cff">
      <div class="proj-header">
        <div class="proj-name">Attendance System</div>
        <div class="proj-badge normal">Utility</div>
      </div>
      <div class="proj-desc">Real-time attendance tracking for students &amp; faculty — managing 100+ students via SQLite.</div>
      <div class="proj-tags">
        <span class="proj-tag">Python</span>
        <span class="proj-tag">SQLite</span>
        <span class="proj-tag">Flask</span>
      </div>
    </div>
    <div class="proj-card" style="--proj-color:#ff7b72">
      <div class="proj-header">
        <div class="proj-name">UniHub · Prep Platform</div>
        <div class="proj-badge normal">EdTech</div>
      </div>
      <div class="proj-desc">Centralized college resource app + daily role-based interview questions placement prep system.</div>
      <div class="proj-tags">
        <span class="proj-tag">React</span>
        <span class="proj-tag">MongoDB</span>
        <span class="proj-tag">Python</span>
      </div>
    </div>
  </div>

  <!-- ══════════════════════ SKILLS ══════════════════════ -->
  <div class="section-divider">
    <div class="section-divider-line"></div>
    <div class="section-divider-label">🛠 skills &amp; tech stack</div>
    <div class="section-divider-line"></div>
  </div>

  <!-- SEARCH -->
  <div class="search-wrap">
    <span class="search-icon">🔍</span>
    <input class="search-input" id="search" type="text" placeholder="search skills..." autocomplete="off" />
  </div>

  <!-- FILTER TABS -->
  <div class="tabs" id="tabs">
    <button class="tab active" data-filter="all">all <span class="tab-count" id="count-all">20</span></button>
    <button class="tab" data-filter="language">languages <span class="tab-count" id="count-language">0</span></button>
    <button class="tab" data-filter="framework">frameworks <span class="tab-count" id="count-framework">0</span></button>
    <button class="tab" data-filter="database">databases <span class="tab-count" id="count-database">0</span></button>
    <button class="tab" data-filter="tool">tools <span class="tab-count" id="count-tool">0</span></button>
  </div>

  <!-- SORT -->
  <div class="sort-row">
    <span class="sort-label">sort:</span>
    <button class="sort-btn active" data-sort="default">default</button>
    <button class="sort-btn" data-sort="az">a → z</button>
    <button class="sort-btn" data-sort="prof">proficiency</button>
  </div>

  <!-- GRID -->
  <div class="skills-grid" id="grid">
    <div class="empty-state" id="empty">No skills found for "<span id="empty-q"></span>"</div>
  </div>

  <!-- LEGEND -->
  <div class="legend" id="legend"></div>

  <!-- ══════════════════════ GITHUB STREAK ══════════════════════ -->
  <div class="section-divider">
    <div class="section-divider-line"></div>
    <div class="section-divider-label">📊 github activity</div>
    <div class="section-divider-line"></div>
  </div>
  <div class="streak-wrap">
    <img src="https://streak-stats.demolab.com?user=jeeva2470041&theme=dark&hide_border=true" alt="GitHub Streak Stats" />
  </div>

</div><!-- /page -->

<script>
/* ============================================================ DATA */
const CAT_COLORS = {
  language: '#58a6ff', framework: '#39d0d8', database: '#3fb950', tool: '#bc8cff',
};

const SKILLS = [
  // LANGUAGES
  { name:'Python',     cat:'language',  prof:90, tip:'Primary language — Flask, ML, automation', icon:'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg' },
  { name:'Dart',       cat:'language',  prof:80, tip:'Flutter apps — PayTrace, AgriAssist',       icon:'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/dart/dart-original.svg' },
  { name:'JavaScript', cat:'language',  prof:75, tip:'Web & frontend development',                icon:'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg' },
  { name:'HTML5',      cat:'language',  prof:85, tip:'Markup, structure & semantics',             icon:'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg' },
  { name:'CSS3',       cat:'language',  prof:78, tip:'Styling, animations & responsive layouts',  icon:'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg' },
  { name:'Java',       cat:'language',  prof:65, tip:'OOP fundamentals & data structures',        icon:'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg' },
  // FRAMEWORKS
  { name:'Flutter',    cat:'framework', prof:82, tip:'Cross-platform mobile — 3 apps built',      icon:'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/flutter/flutter-original.svg' },
  { name:'React',      cat:'framework', prof:72, tip:'Frontend UIs — EcoFeed, UniHub',            icon:'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg' },
  { name:'Flask',      cat:'framework', prof:78, tip:'REST APIs & Python backends',               icon:'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/flask/flask-original.svg' },
  { name:'MLflow',     cat:'framework', prof:60, tip:'ML experiment tracking — PayTrace',         icon:null },
  // DATABASES
  { name:'MySQL',      cat:'database',  prof:78, tip:'Relational data modelling',                  icon:'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg' },
  { name:'MongoDB',    cat:'database',  prof:72, tip:'NoSQL — EcoFeed, CampusShare',              icon:'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mongodb/mongodb-original.svg' },
  { name:'SQLite',     cat:'database',  prof:88, tip:'Attendance System — 100+ students',         icon:'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/sqlite/sqlite-original.svg' },
  { name:'Neo4j',      cat:'database',  prof:60, tip:'Graph database & relationship queries',     icon:'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/neo4j/neo4j-original.svg' },
  { name:'Firebase',   cat:'database',  prof:68, tip:'Real-time DB — CampusShare (IIT KGP)',      icon:'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/firebase/firebase-plain.svg' },
  // TOOLS
  { name:'Git',        cat:'tool',      prof:88, tip:'Version control on all projects',            icon:'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg' },
  { name:'GitHub',     cat:'tool',      prof:88, tip:'All 7 projects hosted & documented',        icon:'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg' },
  { name:'VS Code',    cat:'tool',      prof:92, tip:'Primary editor for all development',        icon:'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg' },
  { name:'Vercel',     cat:'tool',      prof:75, tip:'Portfolio at jeeva-g.vercel.app',           icon:'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/vercel/vercel-original.svg' },
  { name:'Postman',    cat:'tool',      prof:72, tip:'API testing & documentation',                icon:'https://www.vectorlogo.zone/logos/getpostman/getpostman-icon.svg' },
];

function profLabel(n) {
  if (n >= 88) return 'expert';
  if (n >= 78) return 'advanced';
  if (n >= 65) return 'proficient';
  return 'learning';
}

let currentFilter = 'all', currentSort = 'default', currentSearch = '';

function buildLegend() {
  const legend = document.getElementById('legend');
  Object.entries(CAT_COLORS).forEach(([cat, color]) => {
    const item = document.createElement('div');
    item.className = 'legend-item';
    item.innerHTML = `<span class="legend-dot" style="background:${color};color:${color}"></span>${cat}`;
    legend.appendChild(item);
  });
}

function updateCounts() {
  const cats = ['language','framework','database','tool'];
  const q = currentSearch.toLowerCase();
  cats.forEach(cat => {
    const count = SKILLS.filter(s => {
      const matchQ = !q || s.name.toLowerCase().includes(q) || s.tip.toLowerCase().includes(q);
      return matchQ && s.cat === cat;
    }).length;
    const el = document.getElementById(`count-${cat}`);
    if (el) el.textContent = count;
  });
  const allCount = SKILLS.filter(s => {
    const q2 = currentSearch.toLowerCase();
    return !q2 || s.name.toLowerCase().includes(q2) || s.tip.toLowerCase().includes(q2);
  }).length;
  const elAll = document.getElementById('count-all');
  if (elAll) elAll.textContent = allCount;
}

function render() {
  const grid = document.getElementById('grid');
  const empty = document.getElementById('empty');
  const q = currentSearch.toLowerCase();

  let filtered = SKILLS.filter(s => {
    const matchCat = currentFilter === 'all' || s.cat === currentFilter;
    const matchQ = !q || s.name.toLowerCase().includes(q) || s.tip.toLowerCase().includes(q);
    return matchCat && matchQ;
  });

  if (currentSort === 'az') filtered.sort((a,b) => a.name.localeCompare(b.name));
  if (currentSort === 'prof') filtered.sort((a,b) => b.prof - a.prof);

  Array.from(grid.children).forEach(c => { if (c !== empty) c.remove(); });

  if (filtered.length === 0) {
    empty.classList.add('show');
    document.getElementById('empty-q').textContent = currentSearch;
    updateCounts(); return;
  }
  empty.classList.remove('show');

  filtered.forEach((skill, i) => {
    const color = CAT_COLORS[skill.cat];
    const card = document.createElement('div');
    card.className = 'skill-card';
    card.style.setProperty('--cat-color', color);
    card.style.setProperty('--glow-color', color + '18');
    card.style.setProperty('--icon-bg', color + '15');
    card.style.animationDelay = `${i * 38}ms`;

    const iconHTML = skill.icon
      ? `<img src="${skill.icon}" alt="${skill.name}" loading="lazy" onerror="this.style.display='none';this.insertAdjacentHTML('afterend','<div class=\\'fallback\\' style=\\'color:${color}\\'>${skill.name.slice(0,2)}</div>')" />`
      : `<div class="fallback" style="color:${color}">${skill.name.slice(0,2)}</div>`;

    card.innerHTML = `
      <span class="cat-dot" style="background:${color};box-shadow:0 0 5px ${color}"></span>
      <div class="skill-tooltip">${skill.tip}</div>
      <div class="skill-icon">${iconHTML}</div>
      <div class="skill-name">${skill.name}</div>
      <div class="prof-wrap"><div class="prof-bar" data-w="${skill.prof}" style="background:${color}"></div></div>
      <div class="prof-label">${profLabel(skill.prof)}</div>
    `;
    grid.insertBefore(card, empty);

    requestAnimationFrame(() => {
      setTimeout(() => {
        const bar = card.querySelector('.prof-bar');
        if (bar) { bar.style.transition = 'width 1s cubic-bezier(0.4,0,0.2,1)'; bar.style.width = bar.dataset.w + '%'; }
      }, 80 + i * 38);
    });
  });

  updateCounts();
}

/* TABS */
document.getElementById('tabs').addEventListener('click', e => {
  const tab = e.target.closest('.tab');
  if (!tab) return;
  document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
  tab.classList.add('active');
  currentFilter = tab.dataset.filter;
  render();
});

/* SORT */
document.querySelectorAll('.sort-btn').forEach(btn => {
  btn.addEventListener('click', () => {
    document.querySelectorAll('.sort-btn').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    currentSort = btn.dataset.sort;
    render();
  });
});

/* SEARCH */
let searchTimer;
document.getElementById('search').addEventListener('input', e => {
  clearTimeout(searchTimer);
  searchTimer = setTimeout(() => {
    currentSearch = e.target.value.trim();
    currentFilter = 'all';
    document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
    document.querySelector('.tab[data-filter="all"]').classList.add('active');
    render();
  }, 200);
});

/* THEME */
function setTheme(theme) {
  document.documentElement.setAttribute('data-theme', theme);
  document.getElementById('btn-dark').classList.toggle('active', theme === 'dark');
  document.getElementById('btn-light').classList.toggle('active', theme === 'light');
  localStorage.setItem('theme', theme);
}
(function() { const saved = localStorage.getItem('theme') || 'dark'; setTheme(saved); })();

/* INIT */
buildLegend();
render();
</script>
</body>
</html>
