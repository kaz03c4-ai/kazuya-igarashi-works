# Applications ページ修正 — エッセイ追加 + 理論基盤ラベル

---

## 概要

1. 「挑戦の重さと世界の広さ」を Applications に追加
2. 各成果物に「主な理論基盤：TETA（主）/ GATE（補）」のラベルを付与
3. 下部の「理論との対応」を書き換え

---

## applications.html の修正

### Featured セクション — 「観測を打ち手に変える事業開発」にラベル追加

現在の説明文の末尾（paper-links の直前）に、理論基盤ラベルを追加:

```html
<p style="font-size:13px; color:var(--text-tertiary); margin:8px 0 12px;">
  主な理論基盤：<a href="teta.html">TETA</a>（主） / <a href="gate.html">GATE</a>（補）
</p>
```

### Featured セクションの後に — エッセイカードを追加

「観測を打ち手に変える事業開発」の card-featured の後、Other applied works セクションの前に、エッセイ用のセクションを追加:

```html
<div class="section">
  <p class="section-label">Essays</p>
  <div class="paper-item">
    <div class="paper-header">
      <span class="paper-title">挑戦の重さと世界の広さ</span>
      <span class="badge badge-guide">Essay</span>
    </div>
    <p class="paper-desc" style="line-height:1.6;">
      挑戦が重く感じられる構造を、世界の広さ（選択肢・分岐・再起可能性）の観点から解きほぐし、
      賭けから探索へと転換するための設計的な見方を提示する読み物。
    </p>
    <p style="font-size:13px; color:var(--text-tertiary); margin:8px 0 12px;">
      主な理論基盤：<a href="gate.html">GATE</a>（主） / <a href="teta.html">TETA</a>（補）
    </p>
    <div class="paper-links">
      <a href="essay-challenge.html">読む →</a>
    </div>
  </div>
</div>
```

### Other applied works セクション — BizDev Studio にラベル追加

BizDev Studio の説明文の後に:

```html
<p style="font-size:13px; color:var(--text-tertiary); margin:8px 0 0;">
  主な理論基盤：<a href="teta.html">TETA</a> + <a href="gate.html">GATE</a>
</p>
```

### 理論との対応セクション — 書き換え

現在の内容をすべて以下に差し替え:

```html
<div class="section">
  <p class="section-label">理論との対応</p>
  <p style="font-size:15px; color:var(--text-secondary); margin:0 0 16px; line-height:1.7;">
    各成果物は、TETA と GATE を同じ比重で使っているわけではありません。
    事業開発寄りの成果物は主に TETA、人の実行可能性や支援設計を扱う成果物は主に GATE を土台とし、
    必要に応じて相互補完的に接続しています。
  </p>
  <div style="font-size:14px; color:var(--text-secondary); line-height:2.2;">
    <div>事業開発（観測→打ち手の変換）← <a href="teta.html">TETA</a> を主軸</div>
    <div>挑戦・実行可能性（構造的な見立てと再設計）← <a href="gate.html">GATE</a> を主軸</div>
    <div>ツール・デモ ← <a href="teta.html">TETA</a> + <a href="gate.html">GATE</a> の統合</div>
  </div>
</div>
```

---

## ページ全体のセクション順序（確認用）

修正後の applications.html のセクション順序:

1. ページ見出し
2. **Featured** — 観測を打ち手に変える事業開発（理論ラベル付き）
3. **Essays** — 挑戦の重さと世界の広さ（理論ラベル付き）★ 新規
4. **Other applied works** — BizDev Studio（理論ラベル付き）/ 人材開発向け資料 / 支援ツール
5. **理論との対応** — 書き換え済み
6. ページナビ
7. フッター

---

## 実装順序

1. applications.html の Featured セクションに理論ラベル追加
2. Essays セクションを新規追加
3. BizDev Studio に理論ラベル追加
4. 理論との対応セクションを書き換え
5. リンク動作確認（essay-challenge.html / teta.html / gate.html）
