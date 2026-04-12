# エッセイ「挑戦の重さと世界の広さ」追加指示

---

## 概要

GATE に関連する翻訳的読み物「挑戦の重さと世界の広さ — 賭けから探索へ」をサイトに追加する。

---

## ファイル操作

| ファイル | 操作 |
|---|---|
| `essay-challenge.html` | 新規作成（`docs/essay-challenge-source.html` をベースに冒頭バナー追加） |
| `gate.html` | 修正（Related essays のプレースホルダを実リンクに差し替え） |
| `overview.html` | 修正（Essays セクションにリンク追加） |
| `index.html` | 修正（更新情報に1行追記） |

---

## A. essay-challenge.html の作成

`docs/essay-challenge-source.html` を `essay-challenge.html` としてコピーし、`<body>` 直後に以下のバナーを挿入する:

```html
<div style="max-width:720px; margin:16px auto 0; padding:0 24px;">
  <div style="padding:10px 16px; background:#f0f4ff; border-radius:8px;
    font-family:-apple-system,BlinkMacSystemFont,'Hiragino Sans',sans-serif;
    font-size:13px; color:#475569; line-height:1.6;">
    本稿は GATE（実行可能性の基礎理論）に関わる翻訳的読み物です。
    <a href="gate.html" style="color:#163a70;">GATE について →</a>
    <a href="index.html" style="color:#163a70; margin-left:12px;">← トップページに戻る</a>
  </div>
</div>
```

注意: バナーの `max-width` はエッセイ本文の `article` と同じ `720px` に合わせる。

---

## B. gate.html の修正

### Related essays セクション

現在:
```
挑戦性に関する翻訳的読み物を掲載予定。
```

以下に差し替え:

```html
<div class="paper-item">
  <div class="paper-header">
    <span class="paper-title">挑戦の重さと世界の広さ</span>
    <span class="badge badge-guide">Essay</span>
  </div>
  <p class="paper-desc">
    挑戦が重く感じられる構造を、世界の広さ（選択肢・分岐・再起可能性）の観点から解きほぐし、
    賭けから探索へと転換するための設計的な見方を提示する。GATE の考え方を一般向けに翻訳した読み物。
  </p>
  <div class="paper-links">
    <a href="essay-challenge.html">読む →</a>
  </div>
</div>
```

---

## C. overview.html の修正

### Essays / Readings セクション

現在:
```
理論研究の周辺にある翻訳的文章、研究的エッセイ。
```

以下に差し替え:

```html
<p style="font-size:15px; color:var(--text-secondary); margin:0 0 12px; line-height:1.7;">
  理論研究の周辺にある翻訳的文章、研究的エッセイ。
</p>
<div class="paper-item">
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

## D. index.html の修正

### 更新情報セクション

先頭に1行追加:

```html
<div class="update-item"><span class="update-date">2026-04</span><span>エッセイ「挑戦の重さと世界の広さ」公開</span></div>
```

---

## 実装順序

1. `docs/essay-challenge-source.html` を `essay-challenge.html` としてコピー + バナー追加
2. `gate.html` の Related essays 修正
3. `overview.html` の Essays セクション修正
4. `index.html` の更新情報追記
5. リンク動作確認（essay-challenge.html → gate.html / index.html への戻りリンク）

各ステップ完了後に確認を入れること。
