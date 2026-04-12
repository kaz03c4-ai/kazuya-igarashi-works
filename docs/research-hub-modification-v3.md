# 研究母艦サイト — 修正指示書 v3（デザインリニューアル統合版）

これまでの修正指示書（v1, v2）は破棄し、この1本にすべてをまとめる。

---

## 概要

以下をすべて一括で対応する。

1. **レイアウト変更**: コンテンツ幅 640px → 860px
2. **フォントサイズ拡大**: 本文 16px、見出し 28px/18px/16px
3. **カード・背景色によるリッチ化**: 中核研究を2カラムカード、論文をカード化、読み手別入口を3カラムカード
4. **論文リンク統一**: TETA / GATE とも「日本語版 → · Zenodo ↗」パターン
5. **TETA 日本語論文 HTML の追加**: `teta-paper.html`
6. **「研究母艦」表現の修正**: 全ファイルから削除
7. **Overview 関係図**: SVG で差し替え
8. **リンク視認性の改善**: アンダーライン常時表示 + ホバー効果
9. **更新情報の追記**: 論文公開の行を追加

---

## ファイル操作

| ファイル | 操作 |
|---|---|
| `styles.css` | 全面書き換え |
| `index.html` | 全面書き換え |
| `overview.html` | 大幅修正（関係図 + デザイン統一） |
| `teta.html` | 大幅修正（論文リンク + デザイン統一） |
| `gate.html` | 修正（リンクテキスト統一 + デザイン統一） |
| `applications.html` | 修正（デザイン統一） |
| `teta-paper.html` | 新規作成 |
| `gate-paper.html` | 修正（「研究母艦」→「トップページ」） |
| `bizdev-book.html` | 修正不要（そのまま） |
| `book.html` | 修正不要 |
| `book_appendix.html` | 修正不要 |

---

## A. styles.css — 全面書き換え

```css
:root {
  --bg: #f5f7fb;
  --surface: #ffffff;
  --surface-alt: #f8f9fc;
  --text: #1c2430;
  --text-secondary: #5d6a7a;
  --text-tertiary: #8a94a3;
  --line: #dde4ee;
  --accent: #163a70;
  --accent-soft: #eef3fb;
  --info-bg: #f0f5ff;
  --info-border: #c5d5ed;
  --success-bg: #eef7ee;
  --success-text: #2d6a2e;
}

* { box-sizing: border-box; }
html, body { margin: 0; padding: 0; }

body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Yu Gothic", sans-serif;
  color: var(--text);
  background: var(--bg);
  line-height: 1.75;
  font-size: 16px;
}

.container {
  width: min(860px, calc(100% - 40px));
  margin: 0 auto;
}

/* --- ナビ --- */
.site-nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px 0;
  border-bottom: 1px solid var(--line);
  margin-bottom: 48px;
}
.site-nav .site-name {
  font-size: 15px;
  font-weight: 500;
  color: var(--text);
  text-decoration: none;
}
.site-nav .nav-links {
  display: flex;
  gap: 24px;
}
.site-nav .nav-links a {
  font-size: 14px;
  color: var(--text-secondary);
  text-decoration: none;
  border-bottom: none;
}
.site-nav .nav-links a:hover {
  color: var(--text);
}
.site-nav .nav-links a.current {
  color: var(--text);
  font-weight: 500;
}

/* --- リンク基本 --- */
a {
  color: var(--accent);
  text-decoration: none;
  border-bottom: 1px solid rgba(22, 58, 112, 0.2);
  transition: border-color 0.15s;
}
a:hover {
  border-bottom-color: var(--accent);
}

/* --- セクション --- */
.section {
  padding-top: 36px;
  border-top: 1px solid var(--line);
  margin-bottom: 52px;
}
.section-label {
  font-size: 13px;
  color: var(--text-tertiary);
  letter-spacing: 0.04em;
  margin: 0 0 24px;
}

/* --- カード --- */
.card {
  background: var(--surface);
  border: 1px solid var(--line);
  border-radius: 12px;
  padding: 24px;
  transition: border-color 0.15s;
}
.card-muted {
  background: var(--surface-alt);
}
.card-link {
  display: block;
  text-decoration: none;
  color: inherit;
  border-bottom: none;
}
.card-link:hover .card {
  border-color: var(--accent);
}
.card-link .card-arrow {
  color: var(--accent);
  font-size: 14px;
}

/* --- フィーチャードカード --- */
.card-featured {
  background: var(--info-bg);
  border-color: var(--info-border);
}

/* --- バッジ --- */
.badge {
  font-size: 11px;
  padding: 2px 10px;
  border-radius: 6px;
  display: inline-block;
}
.badge-preprint {
  background: var(--success-bg);
  color: var(--success-text);
}
.badge-guide {
  background: var(--surface);
  color: var(--accent);
  border: 1px solid var(--info-border);
}
.badge-status {
  background: var(--surface-alt);
  color: var(--text-tertiary);
  border: 1px solid var(--line);
}

/* --- 2カラムグリッド --- */
.grid-2 {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}
.grid-3 {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 14px;
}

/* --- ヒーローリンク --- */
.hero-links {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
  margin-top: 24px;
}
.hero-links a {
  font-size: 14px;
  padding: 10px 20px;
  border: 1px solid var(--line);
  border-radius: 8px;
  color: var(--text);
  transition: background-color 0.15s, border-color 0.15s;
}
.hero-links a:hover {
  background-color: var(--accent-soft);
  border-color: var(--accent);
  color: var(--accent);
}

/* --- 論文リンク --- */
.paper-links {
  font-size: 14px;
  display: flex;
  gap: 6px;
  align-items: center;
}
.link-sep {
  color: var(--text-tertiary);
  margin: 0 4px;
}

/* --- 更新情報 --- */
.update-item {
  display: flex;
  gap: 18px;
  font-size: 14px;
  line-height: 2.0;
}
.update-date {
  font-size: 13px;
  color: var(--text-tertiary);
  min-width: 64px;
  flex-shrink: 0;
}

/* --- ページナビ --- */
.page-nav {
  display: flex;
  justify-content: space-between;
  padding-top: 20px;
  border-top: 1px solid var(--line);
  margin-bottom: 24px;
}
.page-nav a {
  font-size: 14px;
  color: var(--text-secondary);
  border-bottom: none;
}
.page-nav a:hover {
  color: var(--accent);
}

/* --- フッター --- */
.site-footer {
  text-align: center;
  padding: 24px 0 48px;
  font-size: 13px;
  color: var(--text-tertiary);
}
.site-footer a {
  color: var(--text-tertiary);
  border-bottom: none;
}
.site-footer a:hover {
  color: var(--accent);
}

/* --- 論文ページ内リスト --- */
.paper-item {
  padding: 20px 24px;
  background: var(--surface);
  border: 1px solid var(--line);
  border-radius: 12px;
  margin-bottom: 12px;
}
.paper-header {
  display: flex;
  align-items: baseline;
  gap: 10px;
  flex-wrap: wrap;
  margin-bottom: 6px;
}
.paper-title {
  font-size: 16px;
  font-weight: 500;
  color: var(--text);
}
.paper-subtitle {
  font-size: 13px;
  color: var(--text-tertiary);
}
.paper-desc {
  font-size: 14px;
  color: var(--text-secondary);
  margin: 0 0 10px;
  line-height: 1.6;
}

/* --- テーマ一覧 --- */
.theme-item {
  font-size: 15px;
  line-height: 2.2;
}
.theme-label {
  font-weight: 500;
  color: var(--text);
}
.theme-desc {
  color: var(--text-secondary);
}

/* --- レスポンシブ --- */
@media (max-width: 700px) {
  .grid-2, .grid-3 { grid-template-columns: 1fr; }
  .site-nav { flex-direction: column; gap: 12px; align-items: flex-start; }
  .site-nav .nav-links { flex-wrap: wrap; gap: 16px; }
  .hero-links { flex-direction: column; }
  .hero-links a { text-align: center; }
}
```

---

## B. teta-paper.html — 新規作成

`docs/TETA_paper1.html` を `teta-paper.html` としてコピーし、`<body>` 直後に以下のバナーを挿入する:

```html
<div style="max-width:980px; margin:16px auto 0; padding:0 20px;">
  <div style="padding:10px 16px; background:#f0f4ff; border-radius:8px;
    font-family:-apple-system,BlinkMacSystemFont,'Hiragino Sans',sans-serif;
    font-size:13px; color:#475569; line-height:1.6;">
    本論文の正式版（英語）は
    <a href="https://doi.org/10.5281/ZENODO.19351996"
      target="_blank" rel="noopener"
      style="color:#163a70;">Zenodo（DOI: 10.5281/ZENODO.19351996）</a>
    で公開しています。
    <a href="index.html" style="color:#163a70; margin-left:12px;">← トップページに戻る</a>
  </div>
</div>
```

---

## C. gate-paper.html — 修正

「← 研究母艦に戻る」を「← トップページに戻る」に変更する。

確認コマンド: `grep -r "研究母艦" *.html` → 0件になること。

---

## D. index.html — 全面書き換え

以下の構造で書き直す。

```
ナビ（.site-nav）
ファーストビュー（h1 28px + サブコピー 16px + .hero-links）
セクション: 中核研究（.grid-2 カード × 2）
セクション: 公開物（論文カード × 2 + フィーチャードカード × 1）
セクション: 読み手別の入口（.grid-3 カード × 3）
セクション: 更新（.update-item × 3）
フッター
```

### ファーストビュー

```html
<div style="margin-bottom:52px;">
  <h1 style="font-size:28px; font-weight:500; margin:0 0 12px; line-height:1.3;">TETA + GATE Research Hub</h1>
  <p style="font-size:16px; color:var(--text-secondary); margin:0; line-height:1.7;">
    行動発現と実行可能性に関する理論研究、論文、読み物、<br>
    実務応用を整理・公開するサイトです。
  </p>
  <div class="hero-links">
    <a href="overview.html">研究全体を見る</a>
    <a href="teta.html">公開論文を見る</a>
    <a href="applications.html">実務応用を見る</a>
  </div>
</div>
```

### 中核研究

```html
<div class="section">
  <p class="section-label">中核研究</p>
  <div class="grid-2">
    <a href="teta.html" class="card-link">
      <div class="card card-muted">
        <p style="font-size:18px; font-weight:500; margin:0 0 6px;">TETA</p>
        <p style="font-size:13px; color:var(--text-tertiary); margin:0 0 8px;">Threshold Emergence Theory of Action</p>
        <p style="font-size:14px; color:var(--text-secondary); margin:0 0 12px; line-height:1.6;">
          行動発現を閾値・相転移・改善勾配の観点から捉える研究群。</p>
        <span class="card-arrow">詳しく見る →</span>
      </div>
    </a>
    <a href="gate.html" class="card-link">
      <div class="card card-muted">
        <p style="font-size:18px; font-weight:500; margin:0 0 6px;">GATE</p>
        <p style="font-size:13px; color:var(--text-tertiary); margin:0 0 8px;">Goal-Aligned Theory of Executability</p>
        <p style="font-size:14px; color:var(--text-secondary); margin:0 0 12px; line-height:1.6;">
          主体側の実行可能性、支援設計、前進条件を扱う研究群。</p>
        <span class="card-arrow">詳しく見る →</span>
      </div>
    </a>
  </div>
</div>
```

### 公開物

```html
<div class="section">
  <p class="section-label">公開物</p>

  <div class="paper-item">
    <div class="paper-header">
      <span class="paper-title">TETA Paper 1</span>
      <span class="badge badge-preprint">Preprint</span>
    </div>
    <p class="paper-desc">基礎理論編 — Core Theory and Structural Foundational Hypotheses</p>
    <div class="paper-links">
      <a href="teta-paper.html">日本語版 →</a>
      <span class="link-sep">·</span>
      <a href="https://doi.org/10.5281/ZENODO.19351996" target="_blank" rel="noopener">Zenodo ↗</a>
    </div>
  </div>

  <div class="paper-item">
    <div class="paper-header">
      <span class="paper-title">GATE 論文</span>
      <span class="badge badge-preprint">Preprint</span>
    </div>
    <p class="paper-desc">実行可能性の基礎構造 — Multivariable Theory of Goal-Aligned Executability</p>
    <div class="paper-links">
      <a href="gate-paper.html">日本語版 →</a>
      <span class="link-sep">·</span>
      <a href="https://doi.org/10.5281/ZENODO.19385395" target="_blank" rel="noopener">Zenodo ↗</a>
    </div>
  </div>

  <div class="card card-featured" style="margin-top:12px;">
    <div class="paper-header">
      <span style="font-size:18px; font-weight:500;">観測を打ち手に変える事業開発</span>
      <span class="badge badge-guide">Guide</span>
    </div>
    <p class="paper-desc" style="line-height:1.6;">
      事業開発の主要工程と打ち手設計を整理した実務向けテキスト。<br>
      顧客探索、仮説検証、PoC、社内合意、案件比較まで全34章。</p>
    <div class="paper-links">
      <a href="bizdev-book.html">書籍ページへ →</a>
      <span class="link-sep">·</span>
      <a href="book.html">本文を読む</a>
      <span class="link-sep">·</span>
      <a href="book_appendix.html">付録</a>
    </div>
  </div>
</div>
```

### 読み手別の入口

```html
<div class="section">
  <p class="section-label">読み手別の入口</p>
  <div class="grid-3">
    <a href="overview.html" class="card-link">
      <div class="card card-muted">
        <p style="font-size:15px; font-weight:500; margin:0 0 6px;">初めての方へ</p>
        <p style="font-size:13px; color:var(--text-secondary); margin:0 0 10px; line-height:1.5;">
          全体像と問題設定を知りたい方。</p>
        <span class="card-arrow">→ Overview</span>
      </div>
    </a>
    <a href="teta.html" class="card-link">
      <div class="card card-muted">
        <p style="font-size:15px; font-weight:500; margin:0 0 6px;">研究に興味がある方へ</p>
        <p style="font-size:13px; color:var(--text-secondary); margin:0 0 10px; line-height:1.5;">
          理論構造や論文を直接読みたい方。</p>
        <span class="card-arrow">→ TETA / GATE</span>
      </div>
    </a>
    <a href="applications.html" class="card-link">
      <div class="card card-muted">
        <p style="font-size:15px; font-weight:500; margin:0 0 6px;">実務応用を見たい方へ</p>
        <p style="font-size:13px; color:var(--text-secondary); margin:0 0 10px; line-height:1.5;">
          事業開発や支援設計への接続を見たい方。</p>
        <span class="card-arrow">→ Applications</span>
      </div>
    </a>
  </div>
</div>
```

### 更新

```html
<div class="section">
  <p class="section-label">更新</p>
  <div class="update-item"><span class="update-date">2026-04</span><span>GATE 論文プレプリント公開（Zenodo）</span></div>
  <div class="update-item"><span class="update-date">2026-03</span><span>TETA Paper 1 プレプリント公開（Zenodo）</span></div>
  <div class="update-item"><span class="update-date">2026-03</span><span>「観測を打ち手に変える事業開発」原典版 v1.1 公開</span></div>
</div>
```

### ナビ（全ページ共通）

```html
<nav class="site-nav">
  <a href="index.html" class="site-name">TETA + GATE Research Hub</a>
  <div class="nav-links">
    <a href="index.html" class="current">Home</a>
    <a href="overview.html">Overview</a>
    <a href="teta.html">TETA</a>
    <a href="gate.html">GATE</a>
    <a href="applications.html">Applications</a>
  </div>
</nav>
```

`class="current"` は各ページで該当するリンクに付与する。

### フッター（全ページ共通）

```html
<footer class="site-footer">
  <a href="overview.html">Overview</a> · <a href="teta.html">Papers</a> · <a href="applications.html">Applications</a> · <a href="mailto:kaz.03c4@gmail.com">Contact</a>
  <br>kaz.03c4@gmail.com
</footer>
```

---

## E. overview.html — 修正

### ページ見出し

```html
<h1 style="font-size:28px; font-weight:500; margin:0 0 12px;">Overview</h1>
<p style="font-size:16px; color:var(--text-secondary); margin:0 0 0; line-height:1.7;">
  このサイトは、TETA と GATE を中心に、理論研究、プレプリント、
  翻訳的読み物、実務応用を構造的に整理するための公開基盤です。
</p>
```

### 関係図

「（ここに関係図を配置）」プレースホルダを削除し、以下のインラインSVGで差し替える:

```html
<div class="section">
  <p class="section-label">研究プログラム全体像</p>
  <div class="card" style="padding:32px; text-align:center;">
    <svg viewBox="0 0 520 280" xmlns="http://www.w3.org/2000/svg"
      style="width:100%; max-width:520px; display:block; margin:0 auto;
      font-family:-apple-system,BlinkMacSystemFont,'Hiragino Sans',sans-serif;">
      <text x="260" y="20" text-anchor="middle" font-size="11" fill="#8a94a3" letter-spacing="0.05em">理論</text>
      <rect x="40" y="32" width="200" height="64" rx="6" fill="none" stroke="#dde4ee" stroke-width="1"/>
      <text x="140" y="58" text-anchor="middle" font-size="14" font-weight="500" fill="#1c2430">TETA</text>
      <text x="140" y="78" text-anchor="middle" font-size="12" fill="#5d6a7a">行動発現の閾値構造</text>
      <rect x="280" y="32" width="200" height="64" rx="6" fill="none" stroke="#dde4ee" stroke-width="1"/>
      <text x="380" y="58" text-anchor="middle" font-size="14" font-weight="500" fill="#1c2430">GATE</text>
      <text x="380" y="78" text-anchor="middle" font-size="12" fill="#5d6a7a">実行可能性の基礎構造</text>
      <line x1="240" y1="64" x2="280" y2="64" stroke="#dde4ee" stroke-width="1" stroke-dasharray="4,3"/>
      <line x1="140" y1="96" x2="140" y2="140" stroke="#dde4ee" stroke-width="1"/>
      <line x1="380" y1="96" x2="380" y2="140" stroke="#dde4ee" stroke-width="1"/>
      <line x1="260" y1="96" x2="260" y2="120" stroke="#dde4ee" stroke-width="1" stroke-dasharray="4,3"/>
      <text x="260" y="134" text-anchor="middle" font-size="10" fill="#8a94a3">補完的に接続</text>
      <text x="260" y="158" text-anchor="middle" font-size="11" fill="#8a94a3" letter-spacing="0.05em">展開</text>
      <rect x="20" y="170" width="150" height="52" rx="6" fill="none" stroke="#dde4ee" stroke-width="1"/>
      <text x="95" y="193" text-anchor="middle" font-size="12" font-weight="500" fill="#1c2430">Essays</text>
      <text x="95" y="210" text-anchor="middle" font-size="11" fill="#5d6a7a">翻訳的読み物</text>
      <rect x="185" y="170" width="150" height="52" rx="6" fill="none" stroke="#dde4ee" stroke-width="1"/>
      <text x="260" y="193" text-anchor="middle" font-size="12" font-weight="500" fill="#1c2430">Applications</text>
      <text x="260" y="210" text-anchor="middle" font-size="11" fill="#5d6a7a">実務応用</text>
      <rect x="350" y="170" width="150" height="52" rx="6" fill="none" stroke="#dde4ee" stroke-width="1"/>
      <text x="425" y="193" text-anchor="middle" font-size="12" font-weight="500" fill="#1c2430">Papers</text>
      <text x="425" y="210" text-anchor="middle" font-size="11" fill="#5d6a7a">論文・プレプリント</text>
      <line x1="95" y1="170" x2="140" y2="140" stroke="#dde4ee" stroke-width="1"/>
      <line x1="260" y1="170" x2="260" y2="148" stroke="#dde4ee" stroke-width="1"/>
      <line x1="425" y1="170" x2="380" y2="140" stroke="#dde4ee" stroke-width="1"/>
      <text x="260" y="248" text-anchor="middle" font-size="11" fill="#163a70">代表的成果物</text>
      <text x="260" y="268" text-anchor="middle" font-size="12" fill="#5d6a7a">観測を打ち手に変える事業開発</text>
      <line x1="260" y1="222" x2="260" y2="236" stroke="#163a70" stroke-width="1" stroke-dasharray="3,2"/>
    </svg>
  </div>
</div>
```

### 二つの中核研究

grid-2 のカード化。index.html の中核研究セクションと同じパターン。

### 翻訳と応用

「観測を打ち手に変える事業開発」の紹介は `.card-featured` を使う。

### 現在の公開物

カードは不要。テキストリストのまま。フォントサイズだけ 15px に上げる。

---

## F. teta.html — 修正

### ページ見出し

```html
<h1 style="font-size:28px; font-weight:500; margin:0 0 12px;">TETA</h1>
<p style="font-size:16px; color:var(--text-secondary); margin:0; line-height:1.7;">
  Threshold Emergence Theory of Action — 行動発現の閾値理論。<br>
  個別行動の発現条件を、閾値構造と相転移の観点から扱う理論研究群。
</p>
```

### Core papers

各論文を `.paper-item` カードで表示。

```html
<div class="section">
  <p class="section-label">Core papers</p>

  <div class="paper-item">
    <div class="paper-header">
      <span class="paper-title">Paper 1 — 基礎理論編</span>
      <span class="badge badge-preprint">Preprint</span>
    </div>
    <p class="paper-desc">基礎仮説 FH1–FH4、6変数の定義、識別原理、反証可能命題。</p>
    <div class="paper-links">
      <a href="teta-paper.html">日本語版を読む →</a>
      <span class="link-sep">·</span>
      <a href="https://doi.org/10.5281/ZENODO.19351996" target="_blank" rel="noopener">Zenodo（English / DOI）↗</a>
    </div>
  </div>

  <div class="paper-item">
    <div class="paper-header">
      <span class="paper-title">Paper 2 — 多重目的理論</span>
      <span class="badge badge-status">Working paper</span>
    </div>
    <p class="paper-desc">一行動・多目的の並列評価構造、Purpose Switching、非合理性の再解釈。</p>
  </div>

  <div class="paper-item">
    <div class="paper-header">
      <span class="paper-title">Paper 3 — 実装・実証編</span>
      <span class="badge badge-status">In preparation</span>
    </div>
    <p class="paper-desc">CIQによるインタビュー定量化、マルチドメイン検証。</p>
  </div>
</div>
```

### Why TETA matters

`.theme-item` で統一。

### Related applications

「観測を打ち手に変える事業開発」は `.card-featured` で強調。BizDev Studio は準備中表記のまま。

---

## G. gate.html — 修正

### Core theory

リンクテキストを TETA と統一:

```html
<div class="paper-links">
  <a href="gate-paper.html">日本語版を読む →</a>
  <span class="link-sep">·</span>
  <a href="https://doi.org/10.5281/ZENODO.19385395" target="_blank" rel="noopener">Zenodo（English / DOI）↗</a>
</div>
```

その他のセクションはフォントサイズと `.section` / `.section-label` クラスの統一のみ。

---

## H. applications.html — 修正

### Featured

「観測を打ち手に変える事業開発」を `.card-featured` で表示。リンクは3つ:

```html
<div class="paper-links">
  <a href="bizdev-book.html">書籍ページへ →</a>
  <span class="link-sep">·</span>
  <a href="book.html">本文を読む</a>
  <span class="link-sep">·</span>
  <a href="book_appendix.html">付録を読む</a>
</div>
```

### Other applied works

各項目を `.paper-item` カードで表示。BizDev Studio は `badge-status`（準備中）。

---

## I. 全ファイル横断チェック

実装完了後に以下を確認:

```bash
grep -r "研究母艦" *.html
# → 0件であること

grep -r 'href="#"' *.html
# → 0件であること

grep -r "640px" styles.css
# → 0件であること（860pxになっていること）
```

- 全ページでリンクにアンダーラインが見えること
- ホバーでアンダーラインが濃くなること（テキストリンク）
- ホバーでボーダーが変わること（カードリンク）
- TETA / GATE 両論文に「日本語版を読む → · Zenodo ↗」があること
- モバイル幅（375px）で見てもレイアウトが崩れないこと

---

## 実装順序

1. `styles.css` を全面書き換え
2. `teta-paper.html` を新規作成
3. `gate-paper.html` の「研究母艦」修正
4. `index.html` を全面書き換え
5. `overview.html` を修正
6. `teta.html` を修正
7. `gate.html` を修正
8. `applications.html` を修正
9. 全ファイル横断チェック

各ステップ完了後に確認を入れること。一括実装はしない。
