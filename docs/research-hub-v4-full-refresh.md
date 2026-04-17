# 研究母艦サイト 総合改修指示書 v4

以下の4点を一括で対応する。

1. **視認性強化デザインへの刷新**（styles.css全面書き換え + 全ページHTML調整）
2. **先行研究との差分セクション追加**（TETA / GATE ページ）
3. **エッセイ冒頭の理論対応バッジ追加**（3本のエッセイ）
4. **TETA Paper 1 の「読む →」リンク修正**（`#` → `teta-paper.html`）

---

# A. styles.css — 視認性強化版への書き換え

## A-1. Google Fonts 追加

各HTMLの `<head>` に Noto Sans JP を追加する。

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@400;500;600;700&display=swap" rel="stylesheet">
```

## A-2. styles.css の主要変更点

`:root` のカラーを更新:

```css
:root {
  --bg: #ffffff;
  --surface: #ffffff;
  --surface-alt: #f8f9fc;
  --text: #1a1a1c;
  --text-secondary: #333333;
  --text-tertiary: #595959;
  --text-muted: #767676;
  --line: #dde4ee;
  --line-strong: #c5cee0;
  --accent: #163a70;
  --accent-soft: #eef3fb;
  --success-bg: #e8f3ea;
  --success-text: #1b6b2e;
}
```

body のフォント設定を変更:

```css
body {
  font-family: 'Noto Sans JP', -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Yu Gothic", sans-serif;
  color: var(--text);
  background: var(--bg);
  line-height: 1.8;
  font-size: 17px;
}
```

見出しの階層を明瞭化:

```css
h1 {
  font-size: 32px;
  font-weight: 700;
  letter-spacing: -0.01em;
  line-height: 1.4;
  margin: 0 0 14px;
  color: var(--text);
}
h2 {
  font-size: 22px;
  font-weight: 700;
  line-height: 1.5;
  color: var(--text);
}
h3 {
  font-size: 18px;
  font-weight: 600;
  line-height: 1.5;
  color: var(--text);
}
```

リンクを常時アンダーライン表示:

```css
a {
  color: var(--accent);
  text-decoration: underline;
  text-underline-offset: 3px;
  transition: opacity 0.15s;
}
a:hover {
  opacity: 0.7;
}

/* ナビ・フッター・カード全体リンクはアンダーライン不要 */
.site-nav a,
.site-footer a,
.page-nav a,
.card-link,
.hero-links a {
  text-decoration: none;
}
```

ナビのタイポグラフィ強化:

```css
.site-nav {
  padding: 16px 0;
  border-bottom: 1px solid var(--line);
  margin-bottom: 40px;
}
.site-nav .site-name {
  font-size: 15px;
  font-weight: 600;
  color: var(--text);
}
.site-nav .nav-links a {
  font-size: 14px;
  color: var(--text-tertiary);
  font-weight: 400;
}
.site-nav .nav-links a.current {
  color: var(--text);
  font-weight: 500;
}
```

カードの刷新:

```css
.card {
  background: var(--surface);
  border: 1px solid var(--line);
  border-radius: 12px;
  padding: 28px;
  transition: border-color 0.15s;
}
.card-muted {
  background: var(--surface-alt);
}
.card-featured {
  background: var(--accent-soft);
  border: 1px solid var(--line);
  border-left: 4px solid var(--accent);
  border-radius: 0 12px 12px 0;
  padding: 26px 28px;
}
```

バッジのコントラスト強化:

```css
.badge-preprint {
  font-size: 11px;
  padding: 3px 10px;
  background: var(--success-bg);
  color: var(--success-text);
  border-radius: 4px;
  font-weight: 500;
}
.badge-guide {
  font-size: 11px;
  padding: 3px 10px;
  background: var(--accent);
  color: #ffffff;
  border-radius: 4px;
  font-weight: 500;
}
.badge-essay {
  font-size: 11px;
  padding: 3px 10px;
  background: var(--surface-alt);
  color: var(--text-tertiary);
  border: 1px solid var(--line);
  border-radius: 4px;
}
.badge-status {
  font-size: 11px;
  padding: 3px 10px;
  background: var(--surface-alt);
  color: var(--text-muted);
  border: 1px solid var(--line);
  border-radius: 4px;
}
```

paper-item カードの刷新:

```css
.paper-item {
  padding: 22px 24px;
  background: var(--surface);
  border: 1px solid var(--line);
  border-radius: 12px;
  margin-bottom: 14px;
}
.paper-title {
  font-size: 17px;
  font-weight: 600;
  color: var(--text);
}
.paper-desc {
  font-size: 15px;
  color: var(--text-secondary);
  margin: 0 0 12px;
  line-height: 1.7;
}
.paper-links {
  font-size: 14px;
}
```

ヒーローリンク（ボタンではなくテキストリンクに戻す）:

```css
.hero-links {
  display: flex;
  gap: 20px;
  flex-wrap: wrap;
  margin-top: 24px;
}
.hero-links a {
  font-size: 15px;
  color: var(--accent);
  text-decoration: underline;
  text-underline-offset: 3px;
  padding: 0;
  border: none;
  border-radius: 0;
  font-weight: 500;
}
.hero-links a:hover {
  opacity: 0.7;
  background: transparent;
}
```

---

# B. TETA / GATE ページに「先行研究との差分」セクションを追加

## B-1. teta.html

`Why TETA matters` セクションの直後、`Research notes` の直前に以下を追加:

```html
<div class="section">
  <p class="section-label">先行研究との関係</p>
  <div class="card card-muted">
    <p style="font-size:15px; color:var(--text-secondary); margin:0 0 12px; line-height:1.8;">
      TETA は、離散選択モデルや期待効用理論など行動を連続確率として扱う既存モデルに対し、
      行動を「相転移として発現する構造現象」として再定義する点に特徴がある。
      Granovetter の閾値モデルや Decision Field Theory と理論的系譜を共有しつつ、
      非行動・失敗・停滞を含めた行動構造の<span style="font-weight:500; color:var(--text);">分解可能性と仮説更新可能性</span>を
      理論の主目的とする。
    </p>
    <p style="font-size:14px; color:var(--text-tertiary); margin:0; line-height:1.7;">
      詳細は <a href="teta-paper.html">Paper 1</a> の Related Work 節を参照。
    </p>
  </div>
</div>
```

## B-2. gate.html

`Research themes` セクションの直後、`Related essays` の直前に以下を追加:

```html
<div class="section">
  <p class="section-label">先行研究との関係</p>
  <div class="card card-muted">
    <p style="font-size:15px; color:var(--text-secondary); margin:0 0 12px; line-height:1.8;">
      GATE は、行動変容の輪（COM-B; Michie et al.）、自己制御のサイバネティック枠組み
      （Carver &amp; Scheier）、認知エネルギー的枠組み（Hockey）と理論的射程を共有する。
      ただし、これらの理論を置き換えるのではなく、
      <span style="font-weight:500; color:var(--text);">目標整合的な非自動的処理の実行可能性</span>
      という観点から横断的に再配置する上位枠組みとして位置づけられる。
      起動閾値、並列保持容量、持続容量、残余容量、背景流出といった内部変数への分解により、
      「始められない」「続かない」といった曖昧な訴えを構造的に切り分けることを可能にする。
    </p>
    <p style="font-size:14px; color:var(--text-tertiary); margin:0; line-height:1.7;">
      詳細は <a href="gate-paper.html">GATE 論文</a> の関連研究節を参照。
    </p>
  </div>
</div>
```

---

# C. TETA Paper 1 の「読む →」リンク修正

## teta.html 内

Core papers セクションの Paper 1 の `<a href="#">読む →</a>` を、既存の統一パターンに揃える:

```html
<div class="paper-links">
  <a href="teta-paper.html">日本語版を読む →</a>
  <span class="link-sep">·</span>
  <a href="https://doi.org/10.5281/ZENODO.19351996" target="_blank" rel="noopener">Zenodo（English / DOI）↗</a>
</div>
```

（既に Home の公開物セクションでは同じパターンになっているはず。teta.html 側だけ未修正の状態。）

---

# D. エッセイ冒頭の理論対応バッジ追加

各エッセイHTMLの冒頭バナー（Zenodoリンク等が入っているバナー）の直下に、理論対応を示すバッジを追加する。

## D-1. essay-challenge.html

既存バナーの直後に以下を挿入:

```html
<div style="max-width:720px; margin:8px auto 0; padding:0 24px;">
  <div style="padding:12px 16px; background:#f8f9fc; border-left:3px solid #6b4c1e;
    font-family:'Noto Sans JP', -apple-system, BlinkMacSystemFont, 'Hiragino Sans', sans-serif;
    font-size:13px; color:#595959; line-height:1.7;">
    <span style="font-weight:600; color:#1a1a1c;">理論との対応：</span>
    GATE の「世界の広さ（選択肢・分岐・再起可能性の認識）」と
    TETA の L（損失予期）の主観的増幅に関わる読み物。
    → <a href="variable-mapping.html" style="color:#163a70;">事例と変数の対応</a>
  </div>
</div>
```

## D-2. essay-bivalence.html

```html
<div style="max-width:720px; margin:8px auto 0; padding:0 24px;">
  <div style="padding:12px 16px; background:#f8f9fc; border-left:3px solid #6b4c1e;
    font-family:'Noto Sans JP', -apple-system, BlinkMacSystemFont, 'Hiragino Sans', sans-serif;
    font-size:13px; color:#595959; line-height:1.7;">
    <span style="font-weight:600; color:#1a1a1c;">理論との対応：</span>
    GATE の文脈変数（課題複雑性・感情ノイズ・背景流出）と、
    世界の広さが同時にもたらす価値と負荷の二面性を扱う読み物。
    → <a href="variable-mapping.html" style="color:#163a70;">事例と変数の対応</a>
  </div>
</div>
```

## D-3. essay-pseudowork.html

```html
<div style="max-width:720px; margin:8px auto 0; padding:0 24px;">
  <div style="padding:12px 16px; background:#f8f9fc; border-left:3px solid #1e3a5f;
    font-family:'Noto Sans JP', -apple-system, BlinkMacSystemFont, 'Hiragino Sans', sans-serif;
    font-size:13px; color:#595959; line-height:1.7;">
    <span style="font-weight:600; color:#1a1a1c;">理論との対応：</span>
    TETA の観測不全（何が主因かの見立て不在）と、
    GATE の外部化不足・課題複雑性に関わる読み物。
    → <a href="variable-mapping.html" style="color:#163a70;">事例と変数の対応</a>
  </div>
</div>
```

注: ボーダー色の使い分けは、各エッセイの主たる理論基盤（TETA=ネイビー `#1e3a5f` / GATE=ダークゴールド `#6b4c1e`）に揃えている。

---

# E. Noto Sans JP の読み込み（全ページ）

A-1 で示した `<link>` タグを以下すべての `<head>` に追加する:

- index.html
- overview.html
- teta.html
- gate.html
- applications.html
- variable-mapping.html

エッセイ3本と論文HTMLは既存のスタイルを維持する（独自の `font-family` を持っているため、無理に変えない）。ただし冒頭バナーのフォント指定は上記 D セクション内で明示済み。

---

# F. 実装順序

1. styles.css の書き換え（A セクション）
2. 全ページに Noto Sans JP の `<link>` 追加（E セクション）
3. ブラウザ確認（視認性の変化を確認）
4. teta.html に Paper 1 リンク修正 + 先行研究セクション追加（B-1, C）
5. gate.html に先行研究セクション追加（B-2）
6. 各エッセイに理論対応バッジ追加（D-1, D-2, D-3）
7. 全ページ動作確認

各ステップ完了後に確認を入れること。
