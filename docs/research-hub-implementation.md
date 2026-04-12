# TETA + GATE Research Hub — 実装指示書

## 概要

既存の GitHub Pages サイト（「観測を打ち手に変える事業開発」書籍ランディング）を、TETA / GATE の研究母艦サイトへ転換する。既存の `book.html` / `book_appendix.html` は変更せず、新しいトップページと各セクションページを追加する。

---

## ファイル構成

```
/
├── index.html              ← 新規作成（Home）
├── overview.html            ← 新規作成
├── teta.html                ← 新規作成
├── gate.html                ← 新規作成
├── applications.html        ← 新規作成
├── bizdev-book.html         ← 旧 index.html をリネーム（書籍ページ）
├── book.html                ← 既存のまま（本文）
├── book_appendix.html       ← 既存のまま（付録）
├── styles.css               ← 新規作成（共通スタイル）
└── README.md
```

### 移行手順

1. 現在の `index.html` を `bizdev-book.html` にリネーム
2. `bizdev-book.html` 内のリンクは変更不要（`book.html` / `book_appendix.html` への相対リンクはそのまま動く）
3. `book.html` / `book_appendix.html` 内の「← トップページに戻る」リンクの `href` を `index.html` → `bizdev-book.html` に変更
4. 新しい `index.html`（Home）を作成
5. 各セクションページを作成

---

## デザイン方針

### トーン

- 研究者の個人サイト。装飾を削ぎ落とし、テキストと余白で構成する
- カード・バッジ・色付きアイコンは使わない
- セクション区切りは薄い水平線 + 小さなラベル（12px, グレー, letter-spacing あり）
- 強調は font-weight: 500 のみ。色での強調は最小限（リンク色のみ）
- 本文は 13–14px。見出しは 22px / 15px / 14px の3段階

### レイアウト

- コンテンツ幅: `max-width: 640px; margin: 0 auto;`
- セクション間: `border-top: 0.5px solid` + `padding-top: 28px` + `margin-bottom: 40px`
- 全体のパディング: 左右 20px
- レスポンシブ: 単一カラム。グリッドは使わない

### カラー

```css
:root {
  --bg: #f5f7fb;
  --surface: #ffffff;
  --text: #1c2430;
  --text-secondary: #5d6a7a;
  --text-tertiary: #8a94a3;
  --line: #dde4ee;
  --accent: #163a70;
  --accent-soft: #eef3fb;
}
```

### フォント

```css
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Yu Gothic", sans-serif;
line-height: 1.75;
```

---

## 共通コンポーネント

### グローバルナビ（ヘッダー）

全ページ共通。シンプルなテキストナビ。

```
[TETA + GATE Research Hub]     Home  Overview  TETA  GATE  Applications
```

- サイト名は左寄せ、ナビリンクは右寄せ
- 現在のページはやや濃い色、他はグレー
- モバイルではナビリンクを折り返すだけでよい（ハンバーガー不要）
- フォントサイズ: サイト名 14px / ナビリンク 13px
- パディング: 16px 0
- 下部に `border-bottom: 0.5px solid var(--line)`

### ページ前後リンク（フッター）

各ページ下部に配置。

```
← Overview                                          GATE →
```

- `font-size: 12px; color: var(--text-tertiary)`
- `display: flex; justify-content: space-between`

### サイトフッター

全ページ共通。ページ前後リンクの下に配置。

```
Overview · Papers · Applications · About · Contact
kaz.03c4@gmail.com
```

- `font-size: 12px; color: var(--text-tertiary); text-align: center`
- `padding: 24px 0 48px`

---

## ページ別仕様

---

### 1. Home（index.html）

#### Section 1: ファーストビュー

```
見出し:     TETA + GATE Research Hub
サブコピー:  行動発現と実行可能性に関する理論研究、論文、読み物、
            実務応用を整理・公開するサイトです。
```

リンク3つ（テキストリンク、ボタンではない）:
- 研究全体を見る → overview.html
- 公開論文を見る → teta.html（最小実装版では Papers ページ未作成のため）
- 実務応用を見る → applications.html

余白: `margin-bottom: 48px`（他セクションより大きく取る）

#### Section 2: 中核研究

ラベル: `中核研究`

2項目を縦に並べる（横並びにしない）:

```
TETA — 行動発現の閾値理論
行動発現を閾値・相転移・改善勾配の観点から捉える研究群。→

GATE — 実行可能性の基礎理論
主体側の実行可能性、支援設計、前進条件を扱う研究群。→
```

- タイトル: 15px, font-weight: 500
- 説明: 13px, text-secondary
- 矢印リンク: text-info色、タイトル末尾ではなく説明文末尾に配置
- リンク先: teta.html / gate.html

#### Section 3: 公開物

ラベル: `公開物`

3項目を縦に並べる:

```
TETA Paper 1                                    Preprint
基礎理論編 — Core Theory and Structural Foundational Hypotheses

GATE 論文                                        Preprint
実行可能性の基礎構造 — Multivariable Theory of Executability

│ 観測を打ち手に変える事業開発                      Guide
│ 事業開発の主要工程と打ち手設計を整理した実務向けテキスト。全34章。
│ 書籍ページへ → · 読む
```

- 上2件: タイトル 14px 500 + ステータス 11px tertiary を横並び（flex, baseline揃え）
- 3件目: `border-left: 2px solid var(--accent)` + `padding-left: 16px` で差別化
  - 「書籍ページへ →」→ bizdev-book.html
  - 「読む」→ book.html
- Paper 1, GATE 論文のリンク先は、最小実装版では teta.html / gate.html 内の該当セクションへ

#### Section 4: 読み手別の入口

ラベル: `読み手別の入口`

インラインの3行:

```
初めての方 — 全体像と問題設定を知りたい方 → Overview
研究に興味がある方 — 理論構造や論文を直接読みたい方 → TETA / GATE
実務応用を見たい方 — 事業開発や支援設計への接続を見たい方 → Applications
```

- 各行: カテゴリ名を 500 + text-primary、説明を text-secondary、リンクを text-info
- line-height: 2.2

#### Section 5: 更新情報

ラベル: `更新`

```
2026-03  「観測を打ち手に変える事業開発」原典版 v1.1 公開
```

- 日付部分: 12px, tertiary, `min-width: 60px`
- 内容部分: 13px, secondary
- 今後、論文公開時に行を追加する想定

#### Section 6: フッター

共通フッターを配置。

---

### 2. Overview（overview.html）

#### Section 1: 冒頭

```
見出し: Overview
本文:   このサイトは、TETA と GATE を中心に、理論研究、プレプリント、
       翻訳的読み物、実務応用を構造的に整理するための公開基盤です。
```

#### Section 2: 研究プログラム全体像

ラベル: `研究プログラム全体像`

2列の構造（border で区切り、カードではない）:

```
理論                        │ 展開
TETA — 行動発現              │ Essays — 翻訳的読み物
GATE — 実行可能性            │ Applications — 実務応用
```

- 上部に「（ここに関係図を配置）」のプレースホルダを置く
- 関係図は後日 SVG で差し替え可能な構造にしておく（div で囲む）
- 2列部分: `display: grid; grid-template-columns: 1fr 1fr`、右列に `padding-left: 16px; border-left`

#### Section 3: 二つの中核研究

ラベル: `二つの中核研究`

```
TETA — 行動発現の閾値理論
個別行動の発現条件を、閾値構造・相転移・改善勾配として捉える。
顧客の「動かなさ」や意思決定の停滞を、温度感ではなく構造条件として扱うための理論。

GATE — 実行可能性の基礎理論
主体の前進条件、実行可能性、支援設計を扱う。
意志力・やる気・集中・気力を単一能力ではなく、多変数の実行可能性として再定義する。
```

#### Section 4: 翻訳と応用

ラベル: `翻訳と応用`

```
Essays / Readings
理論研究の周辺にある翻訳的文章、研究的エッセイ。

Applications / Practice
理論を事業開発、人材開発、支援設計へ接続した成果物。
│ 代表的成果物：観測を打ち手に変える事業開発
│ — TETA と GATE の考え方を、事業開発実務における観測整理と打ち手設計へ接続した応用テキスト。
```

- 「観測を打ち手に変える事業開発」部分は `border-left: 2px solid var(--accent)` + `padding-left: 16px`

#### Section 5: 現在の公開物

ラベル: `現在の公開物`

```
Papers — TETA Paper 1, GATE 論文
Guide  — 観測を打ち手に変える事業開発
Demo   — BizDev Studio（準備中）
```

#### ページ前後リンク

```
← Home                                              TETA →
```

---

### 3. TETA（teta.html）

#### Section 1: 冒頭

```
見出し:  TETA
サブ:    Threshold Emergence Theory of Action — 行動発現の閾値理論。
        個別行動の発現条件を、閾値構造と相転移の観点から扱う理論研究群。
```

#### Section 2: Core papers

ラベル: `Core papers`

```
Paper 1 — 基礎理論編                                Preprint
基礎仮説 FH1–FH4、6変数の定義、識別原理、反証可能命題。
読む →

Paper 2 — 多重目的理論                              Working paper
一行動・多目的の並列評価構造、Purpose Switching、非合理性の再解釈。

Paper 3 — 実装・実証編                              In preparation
CIQによるインタビュー定量化、マルチドメイン検証。
```

- Paper 1 のみリンクあり（「読む →」）
- Paper 2, 3 はリンクなし（ステータス表示のみ）
- 「読む →」のリンク先: 論文 HTML ファイルへの直リンク（後日設定）

#### Section 3: Why TETA matters

ラベル: `Why TETA matters`

```
解釈可能性 — 行動の構造を6変数に分解し、因果的な説明を生成できる。
改善勾配   — どこを動かせば行動が発現しやすくなるかを示せる。
介入設計への接続 — 理論を実務上の打ち手設計に接続できる。
```

- 各行: キーワード 500 + text-primary、説明 text-secondary
- line-height: 2.0

#### Section 4: Research notes

ラベル: `Research notes`

```
（今後、関連ノートや補助資料をここに追加）
```

- プレースホルダテキスト: 13px, tertiary
- 後日コンテンツ追加時に差し替え

#### Section 5: Related applications

ラベル: `Related applications`

```
観測を打ち手に変える事業開発 — 事業開発への応用
BizDev Studio — デモ実装（準備中）
```

- 「観測を打ち手に変える事業開発」→ bizdev-book.html
- 「BizDev Studio」→ リンクなし（準備中）

#### ページ前後リンク

```
← Overview                                          GATE →
```

---

### 4. GATE（gate.html）

#### Section 1: 冒頭

```
見出し:  GATE
サブ:    Goal-Aligned Theory of Executability — 実行可能性の基礎理論。
        主体が「なぜ実行できるのか／できないのか」を、多変数の構造として扱う理論研究群。
```

#### Section 2: Core theory

ラベル: `Core theory`

```
基礎論文                                            Preprint
意志力・やる気・集中・気力を、実行可能性を規定する多変数構造として再定義する。
読む →
```

- リンク先: 論文 HTML ファイルへの直リンク（後日設定）

#### Section 3: Research themes

ラベル: `Research themes`

```
実行可能性 — 実行不能の構造分解、ボトルネック診断
支援設計   — 状態把握から介入仮説への接続
人材開発   — 能力不足ではなく構造的停滞として捉える
組織運営   — チーム・組織レベルでの実行可能性
挑戦設計   — 挑戦を構造・設計の問題として扱う
```

#### Section 4: Related essays

ラベル: `Related essays`

```
挑戦性に関する翻訳的読み物を掲載予定。
```

- プレースホルダテキスト: 13px, secondary
- タイトルは出さない

#### Section 5: Related applications

ラベル: `Related applications`

```
人材開発 — 実行可能性の観点からの育成支援
組織支援 — チーム状態の構造把握
```

- いずれもリンクなし（準備中コンテンツ）

#### ページ前後リンク

```
← TETA                                        Applications →
```

---

### 5. Applications（applications.html）

#### Section 1: 冒頭

```
見出し:  Applications
サブ:    TETA と GATE の理論群を、事業開発、人材開発、支援設計へ
        接続した成果物をまとめています。
```

#### Section 2: Featured

ラベル: `Featured`

左ボーダー付き、やや大きめの表示:

```
│ 観測を打ち手に変える事業開発
│ 事業開発の主要工程を一つの流れとして扱い、現場で得られる観測を
│ 打ち手へ変換するための実務向けテキスト。顧客探索、仮説検証、PoC、
│ 社内合意、案件比較まで全34章。
│
│ Type: Guide　Domain: Business Development　Status: Published
│
│ 書籍ページへ → · 本文を読む · 付録を読む
```

- タイトル: 18px, 500
- 説明: 13px, secondary, line-height: 1.7
- メタ情報: 13px, tertiary（ラベル）+ secondary（値）
- リンク:
  - 書籍ページへ → bizdev-book.html
  - 本文を読む → book.html
  - 付録を読む → book_appendix.html
- `border-left: 2px solid var(--accent); padding: 20px`

#### Section 3: Other applied works

ラベル: `Other applied works`

```
BizDev Studio                                    準備中
「観測を打ち手に変える事業開発」の現場実装としてのWebサービス。
アイデア投稿から詰まり診断・打ち手推薦まで。

人材開発向け資料                                  準備中
GATE の考え方を人材育成・1on1・エンゲージメント支援に接続する資料群。

支援ツール                                       構想中
質問票デモ、概念図、事業開発マップなどの補助ツール。
```

- BizDev Studio: リンクなし（準備中）
- 他2件もリンクなし

#### Section 4: 理論との対応

ラベル: `理論との対応`

```
事業開発 ← TETA（行動発現の構造分解）
人材開発 ← GATE（実行可能性の構造分解）
両者は補完的な理論基盤として接続している。
```

- TETA / GATE はリンク（teta.html / gate.html）
- 最終行: 12px, tertiary

#### ページ前後リンク

```
← GATE                                              Home →
```

---

## bizdev-book.html への変更

旧 `index.html` をリネーム後、以下を変更する。

1. ヘッダー上部に研究母艦への戻りリンクを追加:

```html
<div style="...">
  <a href="index.html">← TETA + GATE Research Hub</a>
</div>
```

2. eyebrow テキストを維持（`Business Development Textbook`）
3. 他の内容は変更しない

---

## book.html / book_appendix.html への変更

1. 「← トップページに戻る」のリンク先を `bizdev-book.html` に変更
2. 他の内容は変更しない

---

## 実装上の注意

- JavaScript は不要。静的 HTML + CSS のみで構成する
- styles.css を共通ファイルとして全ページから読み込む
- 各ページ固有のスタイルがある場合は `<style>` タグでページ内に書く
- 既存の book.html / book_appendix.html のスタイルには手を加えない（それぞれ自己完結している）
- GitHub Pages のデフォルト（Jekyll なし）で動作する構成にする
- `.nojekyll` ファイルをルートに置く（すでにあれば不要）

---

## 実装順序

1. `styles.css` を作成（共通スタイル定義）
2. 旧 `index.html` → `bizdev-book.html` リネーム + 戻りリンク追加
3. `book.html` / `book_appendix.html` のリンク修正
4. `index.html`（Home）を新規作成
5. `overview.html` を作成
6. `teta.html` を作成
7. `gate.html` を作成
8. `applications.html` を作成
9. 各ページ間のリンクを検証

各ステップの完了後に確認を入れること。一括実装はしない。
