:root {
  --bg: #f5f7fb;
  --surface: #ffffff;
  --text: #1c2430;
  --muted: #5d6a7a;
  --line: #dde4ee;
  --accent: #163a70;
  --accent-soft: #eef3fb;
}

* { box-sizing: border-box; }
html, body { margin: 0; padding: 0; }
body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Yu Gothic", sans-serif;
  color: var(--text);
  background: var(--bg);
  line-height: 1.75;
}

.container {
  width: min(1040px, calc(100% - 32px));
  margin: 0 auto;
}

.site-header {
  background: linear-gradient(180deg, #17345d 0%, #224b84 100%);
  color: white;
  padding: 56px 0 40px;
}

.eyebrow {
  margin: 0 0 8px;
  font-size: 0.88rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  opacity: 0.9;
}

h1 {
  margin: 0;
  font-size: clamp(2rem, 4vw, 3rem);
  line-height: 1.2;
}

.subtitle {
  margin: 16px 0 0;
  font-size: 1.05rem;
  color: rgba(255,255,255,0.92);
}

.meta-row {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
  margin-top: 18px;
  font-size: 0.95rem;
  color: var(--muted);
}
.site-header .meta-row { color: rgba(255,255,255,0.86); }

.main-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 20px;
  padding: 28px 0 48px;
}

.card, .book-article {
  background: var(--surface);
  border: 1px solid var(--line);
  border-radius: 16px;
  padding: 24px;
  box-shadow: 0 10px 30px rgba(16, 36, 66, 0.05);
}

.card h2, .book-article h2 {
  margin-top: 0;
  font-size: 1.2rem;
}

.link-list {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
}

.primary-link, .secondary-link {
  display: inline-block;
  padding: 12px 16px;
  border-radius: 10px;
  text-decoration: none;
  font-weight: 600;
}

.primary-link {
  background: var(--accent);
  color: white;
}
.secondary-link {
  background: var(--accent-soft);
  color: var(--accent);
}

.note, code {
  color: var(--muted);
}

.site-footer {
  padding: 24px 0 48px;
  color: var(--muted);
}

.book-container {
  width: min(860px, calc(100% - 32px));
  margin: 24px auto 48px;
}

.back-link {
  margin: 0 0 16px;
}

.back-link a {
  color: var(--accent);
  text-decoration: none;
}

.book-header {
  padding-bottom: 18px;
  border-bottom: 1px solid var(--line);
  margin-bottom: 20px;
}

@media (max-width: 640px) {
  .site-header { padding-top: 40px; }
  .card, .book-article { padding: 20px; }
}
