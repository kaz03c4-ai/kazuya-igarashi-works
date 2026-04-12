# 研究母艦サイト — 修正指示書

前回の実装指示書（`docs/research-hub-implementation.md`）に対する修正・追加です。

---

## 修正1: リンクの視認性を改善する

### 問題

リンクが本文と同じ見た目で、どこが押せるか分からない。

### 対応

`styles.css` に以下を追加・修正する。

```css
/* リンクの基本スタイル */
a {
  color: var(--accent);
  text-decoration: none;
  border-bottom: 1px solid transparent;
  transition: border-color 0.15s;
}

a:hover {
  border-bottom-color: var(--accent);
}

/* ナビ内のリンクはボーダー不要 */
.site-nav a,
.page-nav a,
.site-footer a {
  border-bottom: none;
}

/* セクション内のリンク: 常にアンダーラインを薄く表示 */
.section-content a {
  border-bottom: 1px solid rgba(22, 58, 112, 0.25);
}
.section-content a:hover {
  border-bottom-color: var(--accent);
}

/* 矢印リンク（→）をより目立たせる */
.arrow-link {
  font-weight: 500;
  border-bottom: none;
}
.arrow-link:hover {
  opacity: 0.7;
}
```

### 各ページの修正

**「→」だけがリンクの箇所を修正する。** タイトル全体または説明文全体をリンクにして、末尾に → を付ける形にする。

例（Home の中核研究セクション）:

修正前:
```html
<h3>TETA — 行動発現の閾値理論</h3>
<p>行動発現を閾値・相転移・改善勾配の観点から捉える研究群。<a href="teta.html">→</a></p>
```

修正後:
```html
<a href="teta.html" class="block-link">
  <h3>TETA — 行動発現の閾値理論</h3>
  <p>行動発現を閾値・相転移・改善勾配の観点から捉える研究群。<span class="arrow">→</span></p>
</a>
```

block-link のスタイル:
```css
.block-link {
  display: block;
  text-decoration: none;
  color: inherit;
  border-bottom: none;
  padding: 12px 16px;
  margin: -12px -16px;
  border-radius: 8px;
  transition: background-color 0.15s;
}
.block-link:hover {
  background-color: var(--accent-soft);
}
.block-link h3 {
  color: var(--text);
}
.block-link .arrow {
  color: var(--accent);
  margin-left: 4px;
}
```

**この block-link パターンを適用する箇所:**
- Home: 中核研究セクションの TETA / GATE（2箇所）
- Home: 公開物セクションの TETA Paper 1 / GATE 論文（2箇所）
- Overview: 二つの中核研究の TETA / GATE（2箇所）

**テキストリンクにアンダーラインを付ける箇所（.section-content で囲む）:**
- Home: ファーストビューの3つのリンク
- Home: 読み手別の入口
- Home: 「観測を打ち手に変える事業開発」の「書籍ページへ →」「読む」
- 各ページ: Related applications 内のリンク
- Overview: 翻訳と応用セクション内のリンク
- Overview: 現在の公開物セクション内のリンク

---

## 修正2: Overview の関係図を SVG で作成する

### 問題

「（ここに関係図を配置）」がそのまま表示されている。

### 対応

プレースホルダを以下の SVG に差し替える。インラインSVGで直接 overview.html に埋め込む。

```svg
<svg viewBox="0 0 520 280" xmlns="http://www.w3.org/2000/svg"
  style="width:100%; max-width:520px; display:block; margin:0 auto 16px;">

  <!-- 上段: 理論 -->
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

  <!-- 接続線 -->
  <line x1="140" y1="96" x2="140" y2="140" stroke="#dde4ee" stroke-width="1"/>
  <line x1="380" y1="96" x2="380" y2="140" stroke="#dde4ee" stroke-width="1"/>
  <line x1="260" y1="96" x2="260" y2="120" stroke="#dde4ee" stroke-width="1"
    stroke-dasharray="4,3"/>
  <text x="260" y="134" text-anchor="middle"
    font-size="10" fill="#8a94a3">補完的に接続</text>

  <!-- 下段: 展開 -->
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

  <!-- 下段の接続線 -->
  <line x1="95" y1="170" x2="140" y2="140" stroke="#dde4ee" stroke-width="1"/>
  <line x1="260" y1="170" x2="260" y2="148" stroke="#dde4ee" stroke-width="1"/>
  <line x1="425" y1="170" x2="380" y2="140" stroke="#dde4ee" stroke-width="1"/>

  <!-- 代表成果物 -->
  <text x="260" y="248" text-anchor="middle"
    font-size="11" fill="#163a70">代表的成果物</text>
  <text x="260" y="268" text-anchor="middle"
    font-size="12" fill="#5d6a7a">観測を打ち手に変える事業開発</text>
  <line x1="260" y1="222" x2="260" y2="236" stroke="#163a70" stroke-width="1"
    stroke-dasharray="3,2"/>

</svg>
```

このSVGの配置場所: overview.html のプレースホルダ「（ここに関係図を配置）」を削除し、上記SVGで差し替える。その下にある2列グリッド（理論 / 展開）は残す。

---

## 修正3: 論文リンクを接続する

### TETA Paper 1（英語）→ Zenodo DOI にリンク

**対象箇所（全ページ）:**

1. **teta.html** の Core papers セクション
   - 「読む →」の `href` を `https://doi.org/10.5281/ZENODO.19351996` に変更
   - `target="_blank" rel="noopener"` を追加
   - リンクテキストを `Zenodo で読む →` に変更

2. **index.html** の公開物セクション
   - 「TETA Paper 1」のリンク先を `https://doi.org/10.5281/ZENODO.19351996` に変更
   - `target="_blank" rel="noopener"` を追加

### GATE 論文（日本語）→ リポジトリに HTML 配置 + Zenodo DOI 併記

1. **GATE 論文 HTML をリポジトリに追加:**
   - ファイル名: `gate-paper.html`
   - ファイル: 添付の `executability_theory_GATE.html` をコピー
   - **冒頭に正式版への誘導を追加する。** `<body>` 直後、`.container` の前に以下を挿入:

   ```html
   <div style="max-width:980px; margin:16px auto 0; padding:0 20px;">
     <div style="padding:10px 16px; background:#f0f4ff; border-radius:8px;
       font-family:-apple-system,BlinkMacSystemFont,'Hiragino Sans',sans-serif;
       font-size:13px; color:#475569; line-height:1.6;">
       本論文の正式版は
       <a href="https://doi.org/10.5281/ZENODO.19385395"
         target="_blank" rel="noopener"
         style="color:#163a70;">Zenodo（DOI: 10.5281/ZENODO.19385395）</a>
       で公開しています。
       <a href="index.html" style="color:#163a70; margin-left:12px;">← 研究母艦に戻る</a>
     </div>
   </div>
   ```

2. **gate.html** の Core theory セクション
   - 「読む →」の `href` を `gate-paper.html` に変更
   - Zenodo リンクを併記:
   ```
   読む → · Zenodo（DOI）↗
   ```
   「Zenodo（DOI）↗」のリンク先: `https://doi.org/10.5281/ZENODO.19385395`
   `target="_blank" rel="noopener"` を追加

3. **index.html** の公開物セクション
   - 「GATE 論文」のリンク先を `gate-paper.html` に変更

---

## 修正4: TETA Paper 1 にも研究母艦への戻りリンクを追加

TETA Paper 1 は HTML をリポジトリに置かないが、
**将来的に HTML 版を追加する場合**は GATE 論文と同じパターンで冒頭に正式版リンク + 戻りリンクを入れること。

---

## 修正5: 更新情報セクションに論文公開を追記

### index.html の更新セクション

```
2026-04  GATE 論文プレプリント公開（Zenodo）
2026-03  TETA Paper 1 プレプリント公開（Zenodo）
2026-03  「観測を打ち手に変える事業開発」原典版 v1.1 公開
```

新しいものが上に来る降順。

---

## ファイル追加

| ファイル | 操作 |
|---|---|
| `gate-paper.html` | 新規追加（添付の `executability_theory_GATE.html` + 冒頭追記） |

---

## 実装順序

1. `styles.css` のリンクスタイル修正
2. `gate-paper.html` をリポジトリに追加
3. `index.html` の修正（リンク視認性 + 論文リンク + 更新情報）
4. `overview.html` の修正（関係図SVG差し替え）
5. `teta.html` の修正（Paper 1 リンク接続）
6. `gate.html` の修正（論文リンク接続）
7. 全ページのリンク動作確認

各ステップ完了後に確認を入れること。
