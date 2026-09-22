<!DOCTYPE html>
<html lang="uz">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Kundalik — Mundarija</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,600;1,9..144,500&family=Literata:ital,opsz@0,7..72;1,7..72&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>

  :root {
    --bg: #0d1117;
    --panel: #161b22;
    --panel-2: #1c2129;
    --border: #2a313c;
    --text: #e6edf3;
    --text-dim: #8b949e;
    --text-faint: #5b6472;

    --git: #58a6ff;
    --vr: #bc8cff;
    --think: #f0883e;
    --grace: #d4a72c;
    --poem: #f778ba;

    box-sizing: border-box;
    padding-top: env(safe-area-inset-top, 0px);
    padding-bottom: env(safe-area-inset-bottom, 0px);
  }

  :root[data-theme="light"] {
    --bg: #f6f8fa;
    --panel: #ffffff;
    --panel-2: #f0f2f5;
    --border: #d0d7de;
    --text: #1f2328;
    --text-dim: #57606a;
    --text-faint: #8c95a1;

    --git: #0969da;
    --vr: #8250df;
    --think: #bc4c00;
    --grace: #9a6700;
    --poem: #bf3989;
  }

  * { box-sizing: inherit; }
  html { scroll-behavior: smooth; scroll-padding-top: 24px; }

  body {
    margin: 0;
    background: var(--bg);
    color: var(--text);
    font-family: 'Literata', Georgia, serif;
    display: flex;
    min-height: 100vh;
    transition: background 0.3s ease, color 0.3s ease;
  }

  /* ---- Sidebar / Mundarija ---- */
  .toc {
    flex: none;
    width: 280px;
    background: var(--panel);
    border-right: 1px solid var(--border);
    padding: 28px 20px 28px calc(20px + env(safe-area-inset-left, 0px));
    position: sticky;
    top: 0;
    height: 100vh;
    overflow-y: auto;
  }

  .toc-brand {
    display: flex;
    align-items: center;
    gap: 8px;
    font-family: 'Fraunces', serif;
    font-weight: 600;
    font-size: 20px;
    margin-bottom: 4px;
  }
  .toc-brand .dot { color: var(--git); }

  .toc-sub {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 11px;
    color: var(--text-faint);
    margin-bottom: 24px;
    letter-spacing: 0.02em;
  }

  .toc-label {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 11px;
    color: var(--text-faint);
    text-transform: lowercase;
    margin: 0 0 12px;
  }

  .toc-list {
    list-style: none;
    margin: 0;
    padding: 0;
    border-left: 1px solid var(--border);
  }

  .toc-list li { position: relative; }

  .toc-list a {
    display: block;
    text-decoration: none;
    color: var(--text-dim);
    padding: 9px 0 9px 20px;
    font-size: 13.5px;
    line-height: 1.35;
    border-left: 2px solid transparent;
    margin-left: -1px;
    transition: color 0.15s ease, border-color 0.15s ease, background 0.15s ease;
  }

  .toc-list a::before {
    content: "";
    position: absolute;
    left: -4.5px;
    top: 16px;
    width: 7px;
    height: 7px;
    border-radius: 50%;
    background: var(--tag-color, var(--text-faint));
    border: 2px solid var(--panel);
  }

  .toc-list a:hover { color: var(--text); background: var(--panel-2); }

  .toc-date {
    display: block;
    font-family: 'IBM Plex Mono', monospace;
    font-size: 12px;
    color: var(--text);
  }

  .toc-tag {
    display: block;
    font-size: 11.5px;
    color: var(--tag-color, var(--text-faint));
    margin-top: 2px;
  }

  .toc-list a:target,
  .toc-list li.active a {
    border-left-color: var(--tag-color, var(--git));
    background: var(--panel-2);
    color: var(--text);
  }

  .theme-toggle {
    margin-top: 22px;
    display: inline-flex;
    align-items: center;
    gap: 6px;
    background: var(--panel-2);
    border: 1px solid var(--border);
    color: var(--text-dim);
    font-family: 'IBM Plex Mono', monospace;
    font-size: 11px;
    padding: 7px 11px;
    border-radius: 5px;
    cursor: pointer;
  }
  .theme-toggle:focus-visible { outline: 2px solid var(--git); outline-offset: 2px; }

  .toc-toggle {
    display: none;
  }

  /* ---- Main content ---- */
  main {
    flex: 1;
    min-width: 0;
    padding: 48px clamp(20px, 5vw, 64px) 96px;
    max-width: 820px;
  }

  header.hero {
    margin-bottom: 44px;
    padding-bottom: 28px;
    border-bottom: 1px solid var(--border);
  }

  .hero-eyebrow {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 12px;
    color: var(--git);
    margin: 0 0 12px;
  }

  h1 {
    font-family: 'Fraunces', serif;
    font-weight: 600;
    font-size: clamp(32px, 5.5vw, 46px);
    line-height: 1.08;
    margin: 0 0 14px;
    letter-spacing: -0.01em;
  }

  .hero-sub {
    color: var(--text-dim);
    font-size: 16.5px;
    line-height: 1.65;
    max-width: 52ch;
  }

  .entry {
    scroll-margin-top: 24px;
    background: var(--panel);
    border: 1px solid var(--border);
    border-left: 3px solid var(--tag-color, var(--border));
    border-radius: 6px;
    padding: 26px 28px;
    margin-bottom: 22px;
    transition: box-shadow 0.35s ease, border-color 0.35s ease;
  }

  .entry:target {
    box-shadow: 0 0 0 1px var(--tag-color, var(--git)), 0 10px 30px -12px var(--tag-color, var(--git));
  }

  .entry-meta {
    display: flex;
    align-items: center;
    gap: 12px;
    flex-wrap: wrap;
    margin-bottom: 14px;
  }

  .entry-date {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 13px;
    color: var(--text);
  }

  .entry-time {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 12px;
    color: var(--text-faint);
  }

  .entry-tag {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 11.5px;
    color: var(--tag-color, var(--text-dim));
    background: color-mix(in srgb, var(--tag-color, var(--text-dim)) 15%, transparent);
    border: 1px solid color-mix(in srgb, var(--tag-color, var(--text-dim)) 40%, transparent);
    padding: 2px 9px;
    border-radius: 20px;
  }

  .entry-body {
    font-size: 17.5px;
    line-height: 1.75;
    margin: 0;
  }

  .entry-note {
    margin-top: 16px;
    display: flex;
    gap: 10px;
    align-items: flex-start;
    background: var(--panel-2);
    border: 1px solid var(--border);
    border-radius: 5px;
    padding: 12px 14px;
  }

  .entry-note .box {
    flex: none;
    width: 13px;
    height: 13px;
    margin-top: 3px;
    border: 1.5px solid var(--text-faint);
    border-radius: 3px;
  }

  .entry-note p {
    margin: 0;
    font-size: 14.5px;
    line-height: 1.55;
    color: var(--text-dim);
    font-style: italic;
  }

  .poem-card p {
    font-family: 'Fraunces', serif;
    font-style: italic;
    font-weight: 500;
    font-size: clamp(18px, 3vw, 21px);
    line-height: 1.85;
    margin: 0 0 4px;
  }

  .poem-note {
    margin-top: 14px;
    font-family: 'IBM Plex Mono', monospace;
    font-size: 12px;
    color: var(--text-faint);
  }

  footer.end {
    margin-top: 40px;
    font-family: 'IBM Plex Mono', monospace;
    font-size: 12px;
    color: var(--text-faint);
  }

  /* ---- Mobile ---- */
  @media (max-width: 860px) {
    body { flex-direction: column; }
    .toc {
      position: sticky;
      top: 0;
      width: 100%;
      height: auto;
      max-height: 70px;
      overflow: hidden;
      z-index: 20;
      padding: 14px 18px;
      transition: max-height 0.25s ease;
    }
    .toc.open { max-height: 80vh; overflow-y: auto; }
    .toc-brand { margin-bottom: 0; }
    .toc-toggle {
      display: inline-flex;
      margin-left: auto;
      background: var(--panel-2);
      border: 1px solid var(--border);
      color: var(--text-dim);
      font-family: 'IBM Plex Mono', monospace;
      font-size: 11px;
      padding: 6px 10px;
      border-radius: 5px;
      cursor: pointer;
    }
    .toc-top-row { display: flex; align-items: center; gap: 10px; }
    .toc-sub, .toc-label, .toc-list, .theme-toggle { display: none; }
    .toc.open .toc-sub, .toc.open .toc-label, .toc.open .toc-list, .toc.open .theme-toggle { display: block; margin-top: 16px; }
    main { padding: 28px 18px 72px; }
  }
</style>
</head>
<body>

<nav class="toc" id="toc">
  <div class="toc-top-row">
    <div class="toc-brand"><span class="dot">●</span> Kundalik</div>
    <button class="toc-toggle" id="tocToggle" aria-expanded="false">mundarija</button>
  </div>
  <p class="toc-sub">Qarshi, O'zbekiston</p>

  <p class="toc-label">mundarija — kunni tanlang</p>
  <ul class="toc-list">
    <li><a href="#e1" style="--tag-color:var(--git)">
      <span class="toc-date">16.09.2026 · 22:26</span>
      <span class="toc-tag">Git &amp; do'stlik</span>
    </a></li>
    <li><a href="#e2" style="--tag-color:var(--vr)">
      <span class="toc-date">17.09.2026 · 12:34</span>
      <span class="toc-tag">Birinchi taassurot</span>
    </a></li>
    <li><a href="#e3" style="--tag-color:var(--think)">
      <span class="toc-date">21.09.2026 · 09:46</span>
      <span class="toc-tag">Mulohaza</span>
    </a></li>
    <li><a href="#e4" style="--tag-color:var(--grace)">
      <span class="toc-date">21.09.2026 · 20:56</span>
      <span class="toc-tag">Minnatdorchilik</span>
    </a></li>
    <li><a href="#e5" style="--tag-color:var(--poem)">
      <span class="toc-date">22.09.2026 · 11:39</span>
      <span class="toc-tag">She'r</span>
    </a></li>
  </ul>

  <button class="theme-toggle" id="themeToggle">◐ mavzu</button>
</nav>

<main>
  <header class="hero">
    <p class="hero-eyebrow">$ git log --author=men --oneline</p>
    <h1>Kunlarim izi</h1>
    <p class="hero-sub">Git, VR ko'zoynak, minnatdorchilik va bir parcha she'r — chapdagi mundarijadan sanani bossangiz, o'sha kunga to'g'ridan-to'g'ri o'tasiz.</p>
  </header>

  <article class="entry" id="e1" style="--tag-color:var(--git)">
    <div class="entry-meta">
      <span class="entry-date">16.09.2026</span>
      <span class="entry-time">22:26</span>
      <span class="entry-tag">Git &amp; do'stlik</span>
    </div>
    <p class="entry-body">Bugun kun juda ajoyib o'tti. Gitni o'rgandim. Adashim bilan Coca Cola ichdik. Juda ajoyib vaqt o'tdi.</p>
    <div class="entry-note">
      <span class="box"></span>
      <p>Ertaga 42.uz dan o'rganishni davom etaman.</p>
    </div>
  </article>

  <article class="entry" id="e2" style="--tag-color:var(--vr)">
    <div class="entry-meta">
      <span class="entry-date">17.09.2026</span>
      <span class="entry-time">12:34</span>
      <span class="entry-tag">Birinchi taassurot</span>
    </div>
    <p class="entry-body">Bugun men ilk marotaba VR ko'z oynakni taqib ko'rdim. Shunchaki BOOM ekan. Juda yaxshi taassurot oldim bundan.</p>
    <div class="entry-note">
      <span class="box"></span>
      <p>Kundan xulosam shuki, men ham kelajakda shunday VR ko'z oynak olmoqchiman va bu juda ajoyib.</p>
    </div>
  </article>

  <article class="entry" id="e3" style="--tag-color:var(--think)">
    <div class="entry-meta">
      <span class="entry-date">21.09.2026</span>
      <span class="entry-time">09:46</span>
      <span class="entry-tag">Mulohaza</span>
    </div>
    <p class="entry-body">Git ni chuqur o'rganishni davom etmoqdaman va o'rganganlarimni takrorlayapman. Hozir 3D o'qituvchi dars berayapti, ammo STARTUP to'g'risida hammaga aqlli gaplar aytayapti. Umrida bir qator ham kod yozmagan odam maktab o'quvchilariga aqllilik qilayapti. Nima ham derdik — nima bo'lsa ham o'qituvchini hurmat qilishimiz kerak.</p>
  </article>

  <article class="entry" id="e4" style="--tag-color:var(--grace)">
    <div class="entry-meta">
      <span class="entry-date">21.09.2026</span>
      <span class="entry-time">20:56</span>
      <span class="entry-tag">Minnatdorchilik</span>
    </div>
    <p class="entry-body">Ancha kayfiyatim ko'tarildi bugun, sababi eng yaqin insonim bilan gaplashdim. Soat 20:55 da "bugungi gaplarni tarixga muhrlayman" dedim va bugunni muhrladim. Allohdan nima so'rashni bilsangiz, u hammasini albatta berarkan. Bugun shunday bo'ldi.</p>
    <div class="entry-note">
      <span class="box"></span>
      <p>Hech qachon bilmagan, qilolmagan yoki qilib ko'rmagan ishing haqida aqllilik qilma. Chunki juda xunuk ko'rinar ekan chetdan.</p>
    </div>
  </article>

  <article class="entry poem-card" id="e5" style="--tag-color:var(--poem)">
    <div class="entry-meta">
      <span class="entry-date">22.09.2026</span>
      <span class="entry-time">11:39</span>
      <span class="entry-tag">She'r</span>
    </div>
    <p class="entry-body" style="margin-bottom:18px;">She'r yozgim keldi. Qofiyasi kelishmasa-da, o'zim yozdim. Bu she'rni qachon yozganimni bilmayman — ammo bugun topib oldim.</p>
    <p>Qulog'ingga pichirlashga so'zlar bisyor,</p>
    <p>Eshitasanmi tong otguncha meni, ey yor,</p>
    <p>Dilda aytolmagan izhorlarim bor,</p>
    <p>Eshit, gulim, so'zlarimga yog'masdan qor.</p>
    <p class="poem-note">— muallif noma'lum sana, 22-sentabrda topilgan</p>
  </article>

  <footer class="end">5 ta yozuv · davom etmoqda</footer>
</main>

<script>
  (function () {
    var root = document.documentElement;
    var themeBtn = document.getElementById('themeToggle');
    var tocToggle = document.getElementById('tocToggle');
    var toc = document.getElementById('toc');

    var stored = null;
    try { stored = localStorage.getItem('kundalik-theme'); } catch (e) {}
    if (stored === 'light' || stored === 'dark') root.setAttribute('data-theme', stored);

    function apply(mode) {
      root.setAttribute('data-theme', mode);
      themeBtn.textContent = (mode === 'light' ? '◑' : '◐') + ' mavzu';
      try { localStorage.setItem('kundalik-theme', mode); } catch (e) {}
    }
    apply(root.getAttribute('data-theme') === 'light' ? 'light' : 'dark');

    themeBtn.addEventListener('click', function () {
      apply(root.getAttribute('data-theme') === 'light' ? 'dark' : 'light');
    });

    tocToggle.addEventListener('click', function () {
      var open = toc.classList.toggle('open');
      tocToggle.setAttribute('aria-expanded', open);
    });

    toc.querySelectorAll('.toc-list a').forEach(function (a) {
      a.addEventListener('click', function () {
        toc.classList.remove('open');
        tocToggle.setAttribute('aria-expanded', 'false');
      });
    });
  })();
</script>

</body>
</html>
