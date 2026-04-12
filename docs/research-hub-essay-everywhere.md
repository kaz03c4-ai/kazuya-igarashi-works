# エッセイの各ページ掲載 + Applications カード整理

---

## A. index.html — 公開物セクションにエッセイを追加

「観測を打ち手に変える事業開発」の card-featured の直後に、同じ形式でエッセイを追加する。
ただしエッセイは card-featured（青背景）ではなく、通常の paper-item カードでよい。

GATE論文カードの直後、「観測を打ち手に変える事業開発」の直前に挿入:

```html
<div class="paper-item">
  <div class="paper-header">
    <span class="paper-title">挑戦の重さと世界の広さ</span>
    <span class="badge badge-guide">Essay</span>
  </div>
  <p class="paper-desc">挑戦の重さを意志の弱さではなく、世界の広さと条件設計の問題として捉え直す読み物。</p>
  <div class="paper-links">
    <a href="essay-challenge.html">読む →</a>
  </div>
</div>
```

つまり公開物セクションの並び順は:
1. TETA Paper 1（Preprint）
2. GATE 論文（Preprint）
3. **挑戦の重さと世界の広さ（Essay）** ← 追加
4. 観測を打ち手に変える事業開発（Guide / card-featured）

---

## B. overview.html — Essays セクションの修正

Essays / Readings のテキストの後にエッセイカードを追加する（research-hub-essay.md で指示済みの場合はそのまま）。
まだ未実装の場合は以下を追加:

```html
<div class="paper-item" style="margin-top:12px;">
  <div class="paper-header">
    <span class="paper-title">挑戦の重さと世界の広さ</span>
    <span class="badge badge-guide">Essay</span>
  </div>
  <p class="paper-desc">GATE に関わる翻訳的読み物。挑戦の重さを構造の問題として捉え直す。</p>
  <div class="paper-links">
    <a href="essay-challenge.html">読む →</a>
  </div>
</div>
```

---

## C. applications.html — カード構造の整理

### 問題

現在のカード内に、説明文・理論基盤ラベル・リンク・変数対応リンクが混在して読みにくい。

### 方針

各カードは **3行で完結** させる:
1. タイトル + バッジ
2. 説明文（1〜2行）
3. リンク

理論基盤ラベルと変数対応リンクは、カード内ではなくセクション下部の「理論との対応」にまとめる。

### Featured セクション — 書き換え

```html
<div class="section">
  <p class="section-label">Guides & Essays</p>

  <div class="card card-featured" style="margin-bottom:16px;">
    <div class="paper-header">
      <span style="font-size:18px; font-weight:500;">観測を打ち手に変える事業開発</span>
      <span class="badge badge-guide">Guide</span>
    </div>
    <p class="paper-desc">
      事業開発の主要工程と打ち手設計を整理した実務向けテキスト。全34章。
    </p>
    <div class="paper-links">
      <a href="bizdev-book.html">書籍ページへ →</a>
      <span class="link-sep">·</span>
      <a href="book.html">本文を読む</a>
      <span class="link-sep">·</span>
      <a href="book_appendix.html">付録</a>
    </div>
  </div>

  <div class="paper-item">
    <div class="paper-header">
      <span class="paper-title">挑戦の重さと世界の広さ</span>
      <span class="badge badge-guide">Essay</span>
    </div>
    <p class="paper-desc">
      挑戦の重さを意志の弱さではなく、世界の広さと条件設計の問題として捉え直す読み物。
    </p>
    <div class="paper-links">
      <a href="essay-challenge.html">読む →</a>
    </div>
  </div>
</div>
```

### Other applied works セクション — シンプルに

```html
<div class="section">
  <p class="section-label">Other applied works</p>

  <div class="paper-item">
    <div class="paper-header">
      <span class="paper-title">BizDev Studio</span>
      <span class="badge badge-status">準備中</span>
    </div>
    <p class="paper-desc">
      「観測を打ち手に変える事業開発」の現場実装としてのWebサービス。
    </p>
  </div>

  <div class="paper-item">
    <div class="paper-header">
      <span class="paper-title">人材開発向け資料</span>
      <span class="badge badge-status">準備中</span>
    </div>
    <p class="paper-desc">
      GATE の考え方を人材育成・1on1・エンゲージメント支援に接続する資料群。
    </p>
  </div>

  <div class="paper-item">
    <div class="paper-header">
      <span class="paper-title">支援ツール</span>
      <span class="badge badge-status">構想中</span>
    </div>
    <p class="paper-desc">
      質問票デモ、概念図、事業開発マップなどの補助ツール。
    </p>
  </div>
</div>
```

### 理論との対応セクション — 書き換え

理論ラベルと変数対応リンクはここに集約する:

```html
<div class="section">
  <p class="section-label">理論との対応</p>
  <p style="font-size:15px; color:var(--text-secondary); margin:0 0 20px; line-height:1.7;">
    各成果物は、TETA と GATE を同じ比重で使っているわけではありません。
    事業開発寄りの成果物は主に TETA、人の実行可能性や支援設計を扱う成果物は主に GATE を土台とし、
    必要に応じて相互補完的に接続しています。
  </p>
  <div style="font-size:14px; color:var(--text-secondary); line-height:2.4;">
    <div>観測を打ち手に変える事業開発 — <a href="teta.html">TETA</a>（主）/ <a href="gate.html">GATE</a>（補）</div>
    <div>挑戦の重さと世界の広さ — <a href="gate.html">GATE</a>（主）/ <a href="teta.html">TETA</a>（補）</div>
    <div>BizDev Studio — <a href="teta.html">TETA</a> + <a href="gate.html">GATE</a></div>
  </div>
  <div style="margin-top:20px;">
    <a href="variable-mapping.html">事例と研究変数の対応を見る →</a>
  </div>
</div>
```

---

## 実装順序

1. index.html にエッセイカード追加
2. overview.html にエッセイカード追加（未実装の場合）
3. applications.html を書き換え（Guides & Essays / Other / 理論との対応）
4. リンク動作確認
