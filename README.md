<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Tuan Anh — Developer</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link href="https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&family=Geist+Mono:wght@300;400;500&family=Geist:wght@300;400;500&display=swap" rel="stylesheet"/>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0c0c0b;
    --bg2: #131312;
    --bg3: #1a1a18;
    --line: rgba(255,255,255,0.07);
    --line2: rgba(255,255,255,0.13);
    --text: #e8e6df;
    --muted: #6b6960;
    --accent: #c9b97a;
    --accent2: #7a9bc9;
    --accent3: #9bc97a;
    --serif: 'Instrument Serif', Georgia, serif;
    --mono: 'Geist Mono', monospace;
    --sans: 'Geist', system-ui, sans-serif;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--sans);
    font-size: 15px;
    line-height: 1.7;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* noise overlay */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 0;
    opacity: 0.6;
  }

  .wrap {
    position: relative;
    z-index: 1;
    max-width: 760px;
    margin: 0 auto;
    padding: 80px 32px 120px;
  }

  /* ── HERO ── */
  .hero {
    margin-bottom: 80px;
    opacity: 0;
    transform: translateY(24px);
    animation: rise 0.8s cubic-bezier(0.16,1,0.3,1) 0.1s forwards;
  }

  .eyebrow {
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .eyebrow::before {
    content: '';
    display: inline-block;
    width: 28px;
    height: 1px;
    background: var(--muted);
  }

  h1 {
    font-family: var(--serif);
    font-size: clamp(52px, 8vw, 80px);
    font-weight: 400;
    line-height: 1.0;
    letter-spacing: -0.02em;
    color: var(--text);
    margin-bottom: 28px;
  }
  h1 em {
    font-style: italic;
    color: var(--accent);
  }

  .hero-desc {
    font-size: 16px;
    color: var(--muted);
    max-width: 480px;
    line-height: 1.75;
    margin-bottom: 32px;
  }

  .hero-stack {
    font-family: var(--mono);
    font-size: 12px;
    color: var(--muted);
    letter-spacing: 0.04em;
    border-left: 1px solid var(--line2);
    padding-left: 16px;
  }

  /* ── SECTION ── */
  .section {
    margin-bottom: 72px;
    opacity: 0;
    transform: translateY(20px);
    animation: rise 0.7s cubic-bezier(0.16,1,0.3,1) forwards;
  }
  .section:nth-child(2) { animation-delay: 0.25s; }
  .section:nth-child(3) { animation-delay: 0.4s; }
  .section:nth-child(4) { animation-delay: 0.55s; }
  .section:nth-child(5) { animation-delay: 0.65s; }

  .section-header {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-bottom: 32px;
  }
  .section-label {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--muted);
  }
  .section-line {
    flex: 1;
    height: 1px;
    background: var(--line);
  }

  /* ── PROJECT CARDS ── */
  .projects { display: flex; flex-direction: column; gap: 2px; }

  .project {
    border: 1px solid var(--line);
    border-radius: 2px;
    padding: 28px 32px;
    background: var(--bg2);
    transition: border-color 0.2s, background 0.2s;
    cursor: default;
    position: relative;
    overflow: hidden;
  }
  .project::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 3px;
    height: 100%;
    opacity: 0;
    transition: opacity 0.2s;
  }
  .project:nth-child(1)::before { background: var(--accent); }
  .project:nth-child(2)::before { background: var(--accent2); }
  .project:nth-child(3)::before { background: var(--accent3); }

  .project:hover {
    border-color: var(--line2);
    background: var(--bg3);
  }
  .project:hover::before { opacity: 1; }

  .proj-top {
    display: flex;
    align-items: baseline;
    justify-content: space-between;
    gap: 16px;
    margin-bottom: 12px;
    flex-wrap: wrap;
  }

  .proj-name {
    font-family: var(--serif);
    font-size: 22px;
    font-weight: 400;
    color: var(--text);
    text-decoration: none;
    transition: color 0.15s;
  }
  .proj-name:hover { color: var(--accent); }

  .proj-links {
    display: flex;
    gap: 12px;
    align-items: center;
  }
  .proj-link {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--muted);
    text-decoration: none;
    border: 1px solid var(--line2);
    padding: 4px 10px;
    border-radius: 2px;
    transition: color 0.15s, border-color 0.15s;
  }
  .proj-link:hover { color: var(--text); border-color: var(--muted); }

  .proj-desc {
    font-size: 14px;
    color: var(--muted);
    line-height: 1.75;
    margin-bottom: 16px;
    max-width: 560px;
  }
  .proj-desc em {
    font-style: italic;
    color: #a09880;
  }

  .proj-stack {
    font-family: var(--mono);
    font-size: 11px;
    color: #4a4840;
    letter-spacing: 0.04em;
  }

  /* ── STACK GRID ── */
  .stack-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
    gap: 2px;
  }

  .stack-item {
    background: var(--bg2);
    border: 1px solid var(--line);
    padding: 20px 24px;
    border-radius: 2px;
  }
  .stack-cat {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 10px;
  }
  .stack-tags {
    font-size: 13px;
    color: #8a8778;
    line-height: 1.8;
  }

  /* ── LEARNING ── */
  .learning-list {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }
  .learn-tag {
    font-family: var(--mono);
    font-size: 12px;
    color: var(--muted);
    border: 1px solid var(--line2);
    padding: 6px 14px;
    border-radius: 2px;
    letter-spacing: 0.04em;
    transition: color 0.15s, border-color 0.15s;
  }
  .learn-tag:hover { color: var(--text); border-color: var(--muted); }

  /* ── FOOTER ── */
  .footer {
    margin-top: 80px;
    padding-top: 32px;
    border-top: 1px solid var(--line);
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 16px;
  }

  .footer-quote {
    font-family: var(--serif);
    font-style: italic;
    font-size: 16px;
    color: var(--muted);
    max-width: 380px;
  }

  .footer-links {
    display: flex;
    gap: 20px;
  }
  .footer-link {
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--muted);
    text-decoration: none;
    transition: color 0.15s;
  }
  .footer-link:hover { color: var(--text); }

  /* ── ANIM ── */
  @keyframes rise {
    to { opacity: 1; transform: translateY(0); }
  }

  @media (max-width: 600px) {
    .wrap { padding: 48px 20px 80px; }
    h1 { font-size: 44px; }
    .project { padding: 20px; }
    .proj-top { flex-direction: column; gap: 8px; }
  }
</style>
</head>
<body>
<div class="wrap">

  <!-- HERO -->
  <header class="hero">
    <div class="eyebrow">Junior Web Developer · Vũng Tàu, VN</div>
    <h1>Tuan<br><em>Anh</em></h1>
    <p class="hero-desc">
      Xây dựng hệ thống web thực tế — backend logic rõ ràng, frontend dễ mở rộng, code có kiến trúc.<br>
      Luôn hỏi: <em style="font-style:italic;color:#a09880">"Nếu scale thì sao?"</em>
    </p>
    <div class="hero-stack">React · TypeScript · ASP.NET Core · MongoDB · SignalR</div>
  </header>

  <!-- PROJECTS -->
  <section class="section">
    <div class="section-header">
      <span class="section-label">Projects</span>
      <div class="section-line"></div>
    </div>

    <div class="projects">

      <div class="project">
        <div class="proj-top">
          <a class="proj-name" href="https://github.com/Tuananh-Clu/Aurelia_E-commerce" target="_blank">Aurelia E-Commerce</a>
          <div class="proj-links">
            <a class="proj-link" href="https://github.com/Tuananh-Clu/Aurelia_E-commerce" target="_blank">GitHub</a>
            <a class="proj-link" href="https://aureliashop.vercel.app" target="_blank">Live ↗</a>
          </div>
        </div>
        <p class="proj-desc">
          Mua quần áo online mà không biết size vừa hay không — Aurelia giải quyết bằng cách bật camera lên, đo vai ngực eo hông bằng AI, rồi gợi ý size ngay tại trang sản phẩm. Phía sau là cả một hệ thống: shop nhận đơn theo khoảng cách kho, khách tích điểm lên hạng từ Bronze đến Royal, thông báo đẩy realtime khi đơn thay đổi trạng thái.
        </p>
        <div class="proj-stack">React · Vite · ASP.NET Core .NET 9 · MongoDB · SignalR · MediaPipe Pose</div>
      </div>

      <div class="project">
        <div class="proj-top">
          <a class="proj-name" href="https://github.com/Tuananh-Clu/Movie_Booking" target="_blank">Movie Booking</a>
          <div class="proj-links">
            <a class="proj-link" href="https://github.com/Tuananh-Clu/Movie_Booking" target="_blank">GitHub</a>
            <a class="proj-link" href="https://ap-cinema.vercel.app" target="_blank">Live ↗</a>
          </div>
        </div>
        <p class="proj-desc">
          Cái cảm giác chọn đúng ghế giữa rạp, cạnh người bạn muốn ngồi cùng — dự án này mô phỏng lại đúng trải nghiệm đó. Từ lịch chiếu, sơ đồ ghế, thanh toán mock, đến dashboard admin theo dõi doanh thu từng phim từng rạp.
        </p>
        <div class="proj-stack">React · TypeScript · ASP.NET Core · MongoDB · JWT</div>
      </div>

      <div class="project">
        <div class="proj-top">
          <a class="proj-name" href="https://github.com/Tuananh-Clu/Raidexi" target="_blank">Raidexi</a>
          <div class="proj-links">
            <a class="proj-link" href="https://github.com/Tuananh-Clu/Raidexi" target="_blank">GitHub</a>
          </div>
        </div>
        <p class="proj-desc">
          Size M của Zara không phải size M của Uniqlo. Raidexi đứng ở giữa — đo số đo cơ thể từ webcam, hiểu bảng size của từng brand, rồi nói thẳng: <em>cái này vừa, cái kia sẽ hơi bó phần vai</em>. Gemini AI viết nhận xét, backend tính fit score, người dùng chỉ cần chọn.
        </p>
        <div class="proj-stack">Next.js · ASP.NET Core .NET 10 · PostgreSQL · MongoDB · MediaPipe · Gemini</div>
      </div>

    </div>
  </section>

  <!-- STACK -->
  <section class="section">
    <div class="section-header">
      <span class="section-label">Stack</span>
      <div class="section-line"></div>
    </div>
    <div class="stack-grid">
      <div class="stack-item">
        <div class="stack-cat">Frontend</div>
        <div class="stack-tags">React · Next.js<br>TypeScript · Vite<br>TailwindCSS</div>
      </div>
      <div class="stack-item">
        <div class="stack-cat">Backend</div>
        <div class="stack-tags">ASP.NET Core · C#<br>SignalR · JWT<br>OAuth2</div>
      </div>
      <div class="stack-item">
        <div class="stack-cat">Database</div>
        <div class="stack-tags">MongoDB<br>PostgreSQL · MySQL</div>
      </div>
      <div class="stack-item">
        <div class="stack-cat">Tools</div>
        <div class="stack-tags">Git · Postman<br>Vercel · Docker<br><em style="font-style:italic;font-size:11px;color:#4a4840">learning...</em></div>
      </div>
    </div>
  </section>

  <!-- LEARNING -->
  <section class="section">
    <div class="section-header">
      <span class="section-label">Currently learning</span>
      <div class="section-line"></div>
    </div>
    <div class="learning-list">
      <span class="learn-tag">Clean Architecture</span>
      <span class="learn-tag">Domain-Driven Design</span>
      <span class="learn-tag">Docker</span>
      <span class="learn-tag">CI / CD</span>
      <span class="learn-tag">OAuth2 / OpenID Connect</span>
      <span class="learn-tag">Performance Optimization</span>
    </div>
  </section>

  <!-- FOOTER -->
  <footer class="footer section">
    <p class="footer-quote">
      Mục tiêu: developer hiểu hệ thống,<br>không chỉ biết framework.
    </p>
    <div class="footer-links">
      <a class="footer-link" href="https://github.com/Tuananh-Clu" target="_blank">GitHub</a>
      <a class="footer-link" href="https://www.facebook.com/tuan.anh.827144" target="_blank">Facebook</a>
      <a class="footer-link" href="mailto:yianh798@gmail.com">Email</a>
    </div>
  </footer>

</div>
</body>
</html>
