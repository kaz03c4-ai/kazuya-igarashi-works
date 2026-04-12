# 研究母艦サイト — 修正指示書 v2（統合版）

前回の修正が一部未適用のため、すべてをこの1本にまとめ直す。

---

## 追加ファイル

| ファイル | 操作 | 元ファイル |
|---|---|---|
| `teta-paper.html` | 新規追加 | `docs/TETA_paper1.html` をコピーし冒頭にバナーを追加 |
| `gate-paper.html` | 既存修正 | 冒頭バナーの「研究母艦」を修正 |

---

## A. 「研究母艦」表現の修正

全ファイルを `grep -r "研究母艦"` で検索し、すべて修正する。

- `gate-paper.html`: 「← 研究母艦に戻る」→「← トップページに戻る」
- `teta-paper.html`（新規作成時）: 同様に「← トップページに戻る」
- その他のファイルにもあれば同様に修正

---

## B. 論文リンクの統一構成

両論文とも、以下の統一パターンにする:

```
日本語版を読む →     Zenodo（English / DOI）↗
```

### TETA Paper 1

- Zenodo DOI: `https://doi.org/10.5281/ZENODO.19351996`
- 日本語 HTML: `teta-paper.html`

**teta-paper.html の作成手順:**

1. `docs/TETA_paper1.html` を `teta-paper.html` としてコピー
2. `<body>` 直後に以下のバナーを挿入:

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

**teta.html の修正:**

Core papers セクションの Paper 1 を以下に変更:

```html
<div class="paper-item">
  <div class="paper-header">
    <span class="paper-title">Paper 1 — 基礎理論編</span>
    <span class="paper-status">Preprint</span>
  </div>
  <p class="paper-desc">基礎仮説 FH1–FH4、6変数の定義、識別原理、反証可能命題。</p>
  <div class="paper-links">
    <a href="teta-paper.html">日本語版を読む →</a>
    <span class="link-sep">·</span>
    <a href="https://doi.org/10.5281/ZENODO.19351996" target="_blank" rel="noopener">Zenodo（English / DOI）↗</a>
  </div>
</div>
```

**index.html の公開物セクション:**

TETA Paper 1 のリンク先を `teta-paper.html` に変更し、Zenodo リンクも併記:

```html
<a href="teta-paper.html">日本語版 →</a>
<span class="link-sep">·</span>
<a href="https://doi.org/10.5281/ZENODO.19351996" target="_blank" rel="noopener">Zenodo ↗</a>
```

### GATE 論文

- Zenodo DOI: `https://doi.org/10.5281/ZENODO.19385395`
- 日本語 HTML: `gate-paper.html`（既存）

**gate-paper.html の修正:**

冒頭バナーを修正:
- 「← 研究母艦に戻る」→「← トップページに戻る」

**gate.html は現状で OK**（すでに `gate-paper.html` + Zenodo リンクが接続済み）。
ただし、リンクテキストを TETA と統一する:

```html
<a href="gate-paper.html">日本語版を読む →</a>
<span class="link-sep">·</span>
<a href="https://doi.org/10.5281/ZENODO.19385395" target="_blank" rel="noopener">Zenodo（English / DOI）↗</a>
```

**index.html の公開物セクション:**

GATE 論文も同じパターンに統一:

```html
<a href="gate-paper.html">日本語版 →</a>
<span class="link-sep">·</span>
<a href="https://doi.org/10.5281/ZENODO.19385395" target="_blank" rel="noopener">Zenodo ↗</a>
```

---

## C. Overview の関係図

overview.html の「（ここに関係図を配置）」プレースホルダを削除し、以下のインラインSVGで差し替える。

```html
<svg viewBox="0 0 520 280" xmlns="http://www.w3.org/2000/svg"
  style="width:100%; max-width:520px; display:block; margin:0 auto 16px;
  font-family:-apple-system,BlinkMacSystemFont,'Hiragino Sans',sans-serif;">

  <text x="260" y="20" text-anchor="middle"
    font-size="11" fill="#8a94a3" letter-spacing="0.05em">理論</text>

  <rect x="40" y="32" width="200" height="64" rx="6"
    fill="none" stroke="#dde4ee" stroke-width="1"/>
  <text x="140" y="58" text-anchor="middle"
    font-size="14" font-weight="500" fill="#1c2430">TETA</text>
  <text x="140" y="78" text-anchor="middle"
    font-size="12" fill="#5d6a7a">行動発現の閾値構造</text>

  <rect x="280" y="32" width="200" height="64" rx="6"
    fill="none" stroke="#dde4ee" stroke-width="1"/>
  <text x="380" y="58" text-anchor="middle"
    font-size="14" font-weight="500" fill="#1c2430">GATE</text>
  <text x="380" y="78" text-anchor="middle"
    font-size="12" fill="#5d6a7a">実行可能性の基礎構造</text>

  <line x1="240" y1="64" x2="280" y2="64" stroke="#dde4ee" stroke-width="1"
    stroke-dasharray="4,3"/>
  <line x1="140" y1="96" x2="140" y2="140" stroke="#dde4ee" stroke-width="1"/>
  <line x1="380" y1="96" x2="380" y2="140" stroke="#dde4ee" stroke-width="1"/>
  <line x1="260" y1="96" x2="260" y2="120" stroke="#dde4ee" stroke-width="1"
    stroke-dasharray="4,3"/>
  <text x="260" y="134" text-anchor="middle"
    font-size="10" fill="#8a94a3">補完的に接続</text>

  <text x="260" y="158" text-anchor="middle"
    font-size="11" fill="#8a94a3" letter-spacing="0.05em">展開</text>

  <rect x="20" y="170" width="150" height="52" rx="6"
    fill="none" stroke="#dde4ee" stroke-width="1"/>
  <text x="95" y="193" text-anchor="middle"
    font-size="12" font-weight="500" fill="#1c2430">Essays</text>
  <text x="95" y="210" text-anchor="middle"
    font-size="11" fill="#5d6a7a">翻訳的読み物</text>

  <rect x="185" y="170" width="150" height="52" rx="6"
    fill="none" stroke="#dde4ee" stroke-width="1"/>
  <text x="260" y="193" text-anchor="middle"
    font-size="12" font-weight="500" fill="#1c2430">Applications</text>
  <text x="260" y="210" text-anchor="middle"
    font-size="11" fill="#5d6a7a">実務応用</text>

  <rect x="350" y="170" width="150" height="52" rx="6"
    fill="none" stroke="#dde4ee" stroke-width="1"/>
  <text x="425" y="193" text-anchor="middle"
    font-size="12" font-weight="500" fill="#1c2430">Papers</text>
  <text x="425" y="210" text-anchor="middle"
    font-size="11" fill="#5d6a7a">論文・プレプリント</text>

  <line x1="95" y1="170" x2="140" y2="140" stroke="#dde4ee" stroke-width="1"/>
  <line x1="260" y1="170" x2="260" y2="148" stroke="#dde4ee" stroke-width="1"/>
  <line x1="425" y1="170" x2="380" y2="140" stroke="#dde4ee" stroke-width="1"/>

  <text x="260" y="248" text-anchor="middle"
    font-size="11" fill="#163a70">代表的成果物</text>
  <text x="260" y="268" text-anchor="middle"
    font-size="12" fill="#5d6a7a">観測を打ち手に変える事業開発</text>
  <line x1="260" y1="222" x2="260" y2="236" stroke="#163a70" stroke-width="1"
    stroke-dasharray="3,2"/>
</svg>
```

---

## D. 見やすさの改善（styles.css の修正）

現在のサイトはテキストだけが並んでいて、構造の区切りやリンクの存在が分かりにくい。
以下の改善を styles.css に加える。

### D-1. リンクの視認性

```css
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

/* ナビ・フッター内はアンダーライン不要 */
.site-nav a,
.site-footer a,
.page-nav a {
  border-bottom: none;
}
.site-nav a:hover,
.site-footer a:hover {
  opacity: 0.7;
}
```

### D-2. ブロックリンク（中核研究・論文カードに使用）

Home の TETA/GATE 紹介と、公開物の論文リスト項目をブロックリンク化する。

```css
/* --- ブロックリンク --- */
.block-link {
  display: block;
  text-decoration: none;
  color: inherit;
  border-bottom: none;
  padding: 14px 18px;
  margin-left: -18px;
  margin-right: -18px;
  border-radius: 8px;
  border: 1px solid transparent;
  transition: background-color 0.15s, border-color 0.15s;
}
.block-link:hover {
  background-color: #f0f4fb;
  border-color: var(--line);
}
.block-link h3,
.block-link .paper-title {
  color: var(--text);
}
```

### D-3. 論文項目のスタイル

```css
/* --- 論文アイテム --- */
.paper-item {
  padding: 14px 0;
  border-bottom: 1px solid var(--line);
}
.paper-item:last-child {
  border-bottom: none;
}
.paper-header {
  display: flex;
  align-items: baseline;
  gap: 10px;
  flex-wrap: wrap;
}
.paper-title {
  font-size: 15px;
  font-weight: 500;
  color: var(--text);
}
.paper-status {
  font-size: 11px;
  color: var(--text-tertiary);
  padding: 2px 8px;
  border: 1px solid var(--line);
  border-radius: 4px;
}
.paper-desc {
  font-size: 13px;
  color: var(--text-secondary);
  margin: 4px 0 8px;
}
.paper-links {
  font-size: 13px;
}
.paper-links a {
  /* リンクスタイルは上の a の基本を継承 */
}
.link-sep {
  color: var(--text-tertiary);
  margin: 0 6px;
}
```

### D-4. セクションラベルの強化

```css
/* --- セクションラベル --- */
.section-label {
  font-size: 12px;
  color: var(--text-tertiary);
  letter-spacing: 0.04em;
  margin: 0 0 14px;
  padding-bottom: 6px;
  border-bottom: 1px solid var(--line);
  /* ラベル自体にも薄い下線を入れて区切りを明確にする */
}
```

### D-5. 「観測を打ち手に変える事業開発」の強調枠

```css
/* --- フィーチャード項目 --- */
.featured-item {
  border-left: 3px solid var(--accent);
  padding: 16px 20px;
  background: #fafbfe;
  border-radius: 0 8px 8px 0;
  margin: 8px 0;
}
.featured-item .paper-title,
.featured-item h3 {
  font-size: 16px;
}
```

### D-6. ファーストビューのリンクをボタン風に

Home のファーストビュー3リンクを少し目立たせる。

```css
/* --- ファーストビューのリンク --- */
.hero-links {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
  margin-top: 16px;
}
.hero-links a {
  font-size: 13px;
  padding: 8px 16px;
  border: 1px solid var(--line);
  border-radius: 6px;
  border-bottom: 1px solid var(--line); /* a の基本スタイルを上書き */
  color: var(--accent);
  transition: background-color 0.15s, border-color 0.15s;
}
.hero-links a:hover {
  background-color: #f0f4fb;
  border-color: var(--accent);
}
```

### D-7. 更新情報のスタイル

```css
/* --- 更新情報 --- */
.update-item {
  display: flex;
  gap: 14px;
  font-size: 13px;
  line-height: 1.8;
}
.update-date {
  font-size: 12px;
  color: var(--text-tertiary);
  min-width: 60px;
  flex-shrink: 0;
}
.update-text {
  color: var(--text-secondary);
}
```

---

## E. 各 HTML ファイルの修正

上記のスタイルを使うために、各ページの HTML 構造を微修正する。具体的には:

### index.html

1. ファーストビューの3リンクを `<div class="hero-links">` で囲む
2. 中核研究セクションの TETA / GATE を `<a class="block-link" href="...">` で囲む
   - 「→」の単独リンクを削除し、ブロック全体をリンクにする
3. 公開物セクションの論文項目に `.paper-item` `.paper-header` `.paper-links` クラスを付与
4. 「観測を打ち手に変える事業開発」を `.featured-item` で囲む
5. 更新情報を `.update-item` `.update-date` `.update-text` で構成
6. TETA Paper 1 / GATE 論文のリンクを B節の統一パターンに変更
7. 更新情報に論文公開の行を追記:
   ```
   2026-04  GATE 論文プレプリント公開（Zenodo）
   2026-03  TETA Paper 1 プレプリント公開（Zenodo）
   2026-03  「観測を打ち手に変える事業開発」原典版 v1.1 公開
   ```

### overview.html

1. 関係図プレースホルダを C節の SVG に差し替え

### teta.html

1. Paper 1 の「読む →」を B節の統一パターンに変更
2. 論文項目に `.paper-item` クラスを付与

### gate.html

1. 論文リンクテキストを B節の統一パターンに変更（テキスト統一のみ）

### gate-paper.html

1. 「← 研究母艦に戻る」→「← トップページに戻る」

### teta-paper.html

1. 新規作成（B節参照）

---

## F. 全ファイル横断チェック

実装完了後に以下を確認:

1. `grep -r "研究母艦" *.html` → 0件であること
2. `grep -r 'href="#"' *.html` → 0件であること（未接続リンクの解消）
3. 全ページでリンクにホバーするとアンダーラインまたは背景変化があること
4. TETA / GATE 両方の論文ページに「日本語版を読む →」「Zenodo ↗」の2リンクがあること

---

## 実装順序

1. styles.css にセクション D の CSS を追加
2. teta-paper.html を新規作成（docs/TETA_paper1.html + バナー追加）
3. gate-paper.html の「研究母艦」修正
4. index.html の修正（HTML構造 + リンク + 更新情報）
5. overview.html の修正（関係図SVG）
6. teta.html の修正（論文リンク + クラス付与）
7. gate.html の修正（リンクテキスト統一）
8. 全ファイル横断チェック（セクション F）

各ステップ完了後に確認を入れること。
