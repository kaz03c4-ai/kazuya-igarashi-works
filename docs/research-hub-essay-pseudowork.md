# Research Hub エッセイ追加指示書：「ブルシットジョブの手前にあるもの」

本指示書は、Research Hub（GitHub Pages サイト）に新規エッセイ `essay-pseudowork.html` を追加するための実装指示である。

---

## 1. 概要

### 対象リポジトリ
`kazuya-igarashi-works`（GitHub Pages）

### 作成するファイル
`essay-pseudowork.html`（リポジトリルート直下）

### 作業内容
1. エッセイ HTML ファイルの作成
2. Research Hub の既存ページからのリンク追加
3. max-width の統一（既存エッセイとの整合）

---

## 2. HTML ファイルの作成

### テンプレート
`essay-bivalence-source.html`（二面性エッセイ）の CSS 構造をベースにする。ただし以下の点を変更する。

### CSS の要点

```css
article {
  max-width: 760px;  /* 二面性エッセイと統一 */
}
```

既存の `essay-challenge.html` は `max-width: 720px` だが、本エッセイは二面性エッセイ（760px）に合わせる。

### CSS 変数（二面性エッセイと同じ）
```css
:root {
  --bg: #ffffff;
  --ink: #1a1a1a;
  --muted: #5a5a5a;
  --line: #d9d9d9;
  --soft: #f7f7f5;
  --soft-2: #fbfbfa;
  --accent: #4b5563;
  --table-head: #f2f2ef;
}
```

### 必要な CSS クラス（二面性エッセイから継承）
- `article` — 本文コンテナ
- `header` — タイトル周り
- `.subtitle` — 副題
- `nav.toc` — 目次ボックス（リンク付き）
- `.lead` — 導入テキストボックス
- `h2`, `h3` — 見出し（h2 に border-bottom）
- `.appendix-head` — 付録セクションの区切り線（上部）
- `.note`, `.appendix-note` — 補足ボックス（今回は不使用だが CSS に含めておく）
- `footer` — 末尾のメタ情報

### 今回のエッセイ固有の追加クラス
- `.references` — 参考文献セクション用

```css
.references {
  margin-top: 2.5em;
  padding-top: 1.2em;
  border-top: 1px solid var(--line);
}
.references h2 {
  border-bottom: none;
  margin-top: 0;
  padding-bottom: 0;
}
.references ul {
  list-style: none;
  padding-left: 0;
  margin: 0.8em 0 0;
}
.references li {
  margin-bottom: 0.7em;
  font-size: 0.93em;
  line-height: 1.7;
  padding-left: 2em;
  text-indent: -2em;
  color: var(--ink);
}
```

### header の構成
今回は `p.series` は**不要**（前2篇のように対をなすエッセイではない独立篇）。

```html
<header>
  <h1>ブルシットジョブの手前にあるもの</h1>
  <p class="subtitle">— なぜ会社では「仕事っぽい何か」が増殖するのか</p>
</header>
```

### 目次（nav.toc）の構成
アンカーリンク付き。付録は ol 内に入れ子 ol で表示する。

```html
<nav class="toc">
  <p>目次</p>
  <ol>
    <li><a href="#sec0">導入</a></li>
    <li><a href="#sec1">ブルシットジョブの手前にあるもの</a></li>
    <li><a href="#sec2">なぜ人は仕事っぽい何かを作るのか</a></li>
    <li><a href="#sec3">なぜそれは止まりにくいのか</a></li>
    <li><a href="#sec4">観測できても、打ち手には変わらない</a></li>
    <li><a href="#sec5">結語</a></li>
    <li><a href="#appendix">付録</a>
      <ol>
        <li><a href="#appA">付録A　先行研究との関係</a></li>
        <li><a href="#appB">付録B　概念整理</a></li>
        <li><a href="#appC">付録C　実務への接続</a></li>
        <li><a href="#appD">付録D　見分けるための視点</a></li>
      </ol>
    </li>
  </ol>
</nav>
```

### 導入セクション
導入は `.lead` ボックスには入れず、通常の本文として `<h2 id="sec0">導入</h2>` の下に置く。

理由：二面性エッセイでは `.lead` は冒頭の要約的パラグラフに使っていたが、今回のエッセイは導入が具体的な情景描写から始まる構成であり、要約的な `.lead` ボックスではなく通常の本文として流した方が読み味が合う。

### 本文セクション
各節は `<h2 id="secN">` で始める。

**太字の処理：** 原稿中の `**テキスト**` は `<strong>テキスト</strong>` に変換する。

### 付録セクション
付録の開始位置に `<div class="appendix-head" id="appendix"></div>` を置く。
各付録は `<h2 id="appX">付録X　タイトル</h2>` で始める。
付録 A 内の各項目は `<h3>` で区切る。

### 付録 C の箇条書き
付録 C に含まれる5項目の箇条書き（主因の特定、可動点の把握…）は `<ul class="compact">` で出力する。

### 参考文献セクション
付録 D の後に置く。

```html
<section class="references">
  <h2>参考文献</h2>
  <ul>
    <li>Alvesson, M. &amp; Spicer, A. (2012). A Stupidity-Based Theory of Organizations. <em>Journal of Management Studies</em>, 49(7), 1194–1220.</li>
    <li>Graeber, D. (2018). <em>Bullshit Jobs: A Theory</em>. Simon &amp; Schuster.（邦訳：デヴィッド・グレーバー『ブルシット・ジョブ――クソどうでもいい仕事の理論』岩波書店, 2020）</li>
    <li>Meyer, J. W. &amp; Rowan, B. (1977). Institutionalized Organizations: Formal Structure as Myth and Ceremony. <em>American Journal of Sociology</em>, 83(2), 340–363.</li>
    <li>Nørmark, D. &amp; Jensen, A. F. (2021). <em>Pseudowork: How We Ended Up Being Busy Doing Nothing</em>. Greystone Books.（原著デンマーク語版 2018）</li>
    <li>Spicer, A. (2020). Playing the Bullshit Game: How Empty and Misleading Communication Takes Over Organizations. <em>Organization Theory</em>, 1(1).</li>
  </ul>
</section>
```

### footer
```html
<footer>
  本稿は、組織内で生成される「仕事っぽい何か」の構造を扱う独立エッセイである。筆者の既著『観測を打ち手に変える事業開発』および TETA/GATE 研究プログラムとの理論的接続は、付録で整理している。
</footer>
```

---

## 3. 本文の全文

以下のテキストをそのまま HTML 化する。改行位置は `<p>` タグで区切る。原稿中の `**テキスト**` は `<strong>` に変換する。

**重要：** 本文は前のメッセージで確定済みの最終版をそのまま使う。このファイル内には本文を含めない。Claude Code 実行時に、直前の会話で確定した原稿全文（導入〜結語、付録A〜D、参考文献）を HTML 化すること。

原稿は以下の構造を持つ：

```
導入（h2#sec0）
  - 2つの具体例（ナレッジ共有会、改善WG）
  - 「あとから生成された」という論点提示

1. ブルシットジョブの手前にあるもの（h2#sec1）
  - グレーバー紹介 (Graeber, 2018)
  - 第三のルート
  - Nørmark & Jensen, Pseudowork 紹介

2. なぜ人は仕事っぽい何かを作るのか（h2#sec2）
  - 暇と役割の空白
  - 評価不安
  - 存在意義不安
  - 雇用不安（深い層として）
  - 個人合理性 → 組織非合理性の定式化
  - 価値創出の演出

3. なぜそれは止まりにくいのか（h2#sec3）
  - 建前上は善に見える
  - Meyer & Rowan (1977) への言及
  - 完全な無意味ではない
  - 総量の問題
  - 止めること＝主催者否定
  - 価値創出と価値創出の演出の区別

4. 観測できても、打ち手には変わらない（h2#sec4）
  - ミニケース（会議半減の号令）
  - 精神論と一律削減への流れ
  - 構造変換レイヤーの不足
  - 事業開発との同型性

5. 結語（h2#sec5）

付録A 先行研究との関係（h2#appA）
  - h3: 1〜5 の各項目
  - h3: まとめ

付録B 概念整理（h2#appB）

付録C 実務への接続（h2#appC）
  - ul.compact で5項目

付録D 見分けるための視点（h2#appD）
  - 問い1〜4

参考文献（section.references）
footer
```

---

## 4. Research Hub 既存ページへのリンク追加

### 4-1. Applications ページ（`applications.html`）

エッセイ一覧セクションに以下を追加する。既存の2エッセイ（挑戦の重さと世界の広さ、世界の広さがもつ二面性）の下に置く。

追加するカード/リンクの内容：
- タイトル：「ブルシットジョブの手前にあるもの」
- 副題：「なぜ会社では『仕事っぽい何か』が増殖するのか」
- リンク先：`essay-pseudowork.html`
- 説明文（短め）：「組織内で生成される擬似仕事の構造と、観測を打ち手に変換する視点への接続」

**注意：** Applications ページのエッセイセクションの HTML 構造を確認し、既存エッセイと同じ形式で追加すること。

### 4-2. Home ページ（`index.html`）

Home ページにエッセイへの言及がある場合は、同様にリンクを追加する。ただし、Home ページの構成によっては不要の場合もある。実装時に確認すること。

---

## 5. max-width の統一について

既知の問題として、2つの既存エッセイで `max-width` が異なる：
- `essay-challenge.html`: 720px
- `essay-bivalence.html`（`essay-bivalence-source.html`）: 760px

本エッセイは **760px** で作成する。

**既存エッセイの修正は本指示書のスコープ外とする。** 別途、3エッセイの max-width を統一する作業が必要になるが、それは独立した作業として行う。

---

## 6. 実装時の注意事項

### やること
- `essay-pseudowork.html` を二面性エッセイの CSS 構造に合わせて作成する
- TOC のアンカーリンクが全て正しく動作することを確認する
- Applications ページにリンクを追加する
- `&` は `&amp;` にエスケープする（参考文献、本文中の「Alvesson & Spicer」など）
- `<em>` でイタリック表記する書籍・雑誌名

### やらないこと
- 既存エッセイの max-width 修正（別作業）
- Research Hub の他のページ（Overview, TETA, GATE）への変更
- 新しい CSS ファイルの分離（インラインスタイルのまま）

---

## 7. 確認項目

実装完了後、以下を確認する：
1. `essay-pseudowork.html` が正しく表示される
2. 目次の全アンカーリンクが正しい位置にジャンプする
3. Applications ページから正しくリンクされている
4. モバイル表示（max-width: 640px）でレイアウトが崩れない
5. 付録セクションの区切り線（`.appendix-head`）が表示されている
6. 参考文献セクションが正しく表示されている
7. footer が表示されている
