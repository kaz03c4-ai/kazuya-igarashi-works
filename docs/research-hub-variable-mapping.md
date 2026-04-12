# 事例と研究変数の対応ページ — 新規作成指示

---

## 概要

作品中の事例を、TETA / GATE の研究変数に対応づけた補助ページを新設する。
各作品3例ずつ、計6例でスタートする。

---

## ファイル操作

| ファイル | 操作 |
|---|---|
| `variable-mapping.html` | 新規作成 |
| `applications.html` | 修正（リンク追加） |

---

## A. variable-mapping.html の作成

サイト共通の styles.css を読み込み、共通ナビ・フッターを含める。
デザインは他のページと統一する。

### ページ構造

```
ナビ（共通）
ページ見出し
注記（冒頭の断り書き）
セクション: 観測を打ち手に変える事業開発（3例）
セクション: 挑戦の重さと世界の広さ（3例）
セクション: 変数の凡例
ページナビ（← Applications / Home →）
フッター（共通）
```

### ページ見出し

```html
<h1 style="font-size:28px; font-weight:500; margin:0 0 12px;">事例と研究変数の対応</h1>
<p style="font-size:16px; color:var(--text-secondary); margin:0; line-height:1.7;">
  各作品に登場する事例や場面を、TETA / GATE の研究変数に読み替えたとき、<br>
  どのような対応が見えるかを整理した補助ページです。
</p>
```

### 注記（冒頭の断り書き）

ページ見出しの直後に、card スタイルで配置:

```html
<div class="card card-muted" style="margin:24px 0 48px; padding:20px 24px;">
  <p style="font-size:14px; color:var(--text-secondary); margin:0; line-height:1.7;">
    ここでの対応は、作品中の事例を研究上の変数へ読み替えたものであり、
    実測値や唯一の解釈を示すものではありません。
    一つの事例に対して複数の変数が関わりうるため、主対応と副対応に分けて記載しています。
  </p>
</div>
```

### セクション1: 観測を打ち手に変える事業開発

```html
<div class="section">
  <p class="section-label">観測を打ち手に変える事業開発</p>
  <p style="font-size:13px; color:var(--text-tertiary); margin:0 0 20px;">
    主な理論基盤：<a href="teta.html">TETA</a>（主） / <a href="gate.html">GATE</a>（補）
  </p>

  <!-- 事例1 -->
  <div class="card" style="margin-bottom:16px; padding:24px;">
    <p style="font-size:15px; font-weight:500; margin:0 0 6px;">
      技術はあるがテーマにならない
    </p>
    <p style="font-size:13px; color:var(--text-tertiary); margin:0 0 12px;">
      表面的な症状：探索初期で停止、対象が絞れない
    </p>
    <div style="display:grid; grid-template-columns:1fr 1fr; gap:16px; margin-bottom:12px;">
      <div>
        <p style="font-size:12px; color:var(--text-tertiary); margin:0 0 4px;">主対応（TETA）</p>
        <p style="font-size:14px; color:var(--text-secondary); margin:0; line-height:1.6;">
          R（報酬認識）が局所閾値を超えていない。技術の価値は存在するが、
          顧客にとっての期待報酬として認識される形に翻訳されていない。
        </p>
      </div>
      <div>
        <p style="font-size:12px; color:var(--text-tertiary); margin:0 0 4px;">副対応（GATE）</p>
        <p style="font-size:14px; color:var(--text-secondary); margin:0; line-height:1.6;">
          担当者側の課題複雑性（K）が高く、対象設定の起動閾値（T）を超えにくい。
          探索の切り口と最初の一手の設計が不足している。
        </p>
      </div>
    </div>
    <p style="font-size:13px; color:var(--text-secondary); margin:0; padding-top:12px; border-top:1px solid var(--line);">
      <span style="font-weight:500;">読み方：</span>
      対象の魅力不足ではなく、価値の翻訳不全（R未充足）と探索設計の不在（課題複雑性）が停止を生んでいる。
    </p>
  </div>

  <!-- 事例2 -->
  <div class="card" style="margin-bottom:16px; padding:24px;">
    <p style="font-size:15px; font-weight:500; margin:0 0 6px;">
      顧客は前向きだが進まない
    </p>
    <p style="font-size:13px; color:var(--text-tertiary); margin:0 0 12px;">
      表面的な症状：反応は良いが案件化しない、次のステップに進まない
    </p>
    <div style="display:grid; grid-template-columns:1fr 1fr; gap:16px; margin-bottom:12px;">
      <div>
        <p style="font-size:12px; color:var(--text-tertiary); margin:0 0 4px;">主対応（TETA）</p>
        <p style="font-size:14px; color:var(--text-secondary); margin:0; line-height:1.6;">
          L（損失予期）や C（確定コスト）が閾値を塞いでいる。
          判断条件・実行条件が未整理で、前進の閾値 T を越えられない。
        </p>
      </div>
      <div>
        <p style="font-size:12px; color:var(--text-tertiary); margin:0 0 4px;">副対応（TETA）</p>
        <p style="font-size:14px; color:var(--text-secondary); margin:0; line-height:1.6;">
          主因の見立てが不在で、打ち手が拡散している。
          R は一定程度認識されているが、L/C のどちらが主因かの切り分けがなされていない。
        </p>
      </div>
    </div>
    <p style="font-size:13px; color:var(--text-secondary); margin:0; padding-top:12px; border-top:1px solid var(--line);">
      <span style="font-weight:500;">読み方：</span>
      「前向きさ」は R の充足を示しているが、前進しないのは L/C/判断条件が閾値を塞いでいるため。
      観測を切り分けて主因候補を仮置きすることが次の一手になる。
    </p>
  </div>

  <!-- 事例3 -->
  <div class="card" style="margin-bottom:16px; padding:24px;">
    <p style="font-size:15px; font-weight:500; margin:0 0 6px;">
      担当者が動けず、案件も進まない
    </p>
    <p style="font-size:13px; color:var(--text-tertiary); margin:0 0 12px;">
      表面的な症状：案件の停滞と担当者の停滞が重なっている
    </p>
    <div style="display:grid; grid-template-columns:1fr 1fr; gap:16px; margin-bottom:12px;">
      <div>
        <p style="font-size:12px; color:var(--text-tertiary); margin:0 0 4px;">主対応（GATE）</p>
        <p style="font-size:14px; color:var(--text-secondary); margin:0; line-height:1.6;">
          担当者の残余容量 R(t) が低下し、背景流出 D(t) が大きい。
          複数案件を抱えた並列過負荷、または支援不足による孤立が起動閾値を上げている。
        </p>
      </div>
      <div>
        <p style="font-size:12px; color:var(--text-tertiary); margin:0 0 4px;">副対応（TETA）</p>
        <p style="font-size:14px; color:var(--text-secondary); margin:0; line-height:1.6;">
          案件側も T（閾値）が高止まりしており、
          担当者が動けないことで観測が止まり、L/C の切り分けが進まない悪循環。
        </p>
      </div>
    </div>
    <p style="font-size:13px; color:var(--text-secondary); margin:0; padding-top:12px; border-top:1px solid var(--line);">
      <span style="font-weight:500;">読み方：</span>
      案件の構造問題（TETA）と担当者の実行可能性問題（GATE）が連動している。
      本書第28〜30章が扱う「人も止まる」構造がこれに該当し、
      案件支援と人の前進支援を分けて整理する必要がある。
    </p>
  </div>
</div>
```

### セクション2: 挑戦の重さと世界の広さ

```html
<div class="section">
  <p class="section-label">挑戦の重さと世界の広さ</p>
  <p style="font-size:13px; color:var(--text-tertiary); margin:0 0 20px;">
    主な理論基盤：<a href="gate.html">GATE</a>（主） / <a href="teta.html">TETA</a>（補）
  </p>

  <!-- 事例4 -->
  <div class="card" style="margin-bottom:16px; padding:24px;">
    <p style="font-size:15px; font-weight:500; margin:0 0 6px;">
      失敗が怖くて踏み出せない
    </p>
    <p style="font-size:13px; color:var(--text-tertiary); margin:0 0 12px;">
      表面的な症状：着手回避、過剰な先延ばし
    </p>
    <div style="display:grid; grid-template-columns:1fr 1fr; gap:16px; margin-bottom:12px;">
      <div>
        <p style="font-size:12px; color:var(--text-tertiary); margin:0 0 4px;">主対応（GATE）</p>
        <p style="font-size:14px; color:var(--text-secondary); margin:0; line-height:1.6;">
          再起可能性の認識が低く、評価軸が単一化している。
          選択肢が見えていないため、一回の試行に全人格的な重みが乗る。
          報酬予測（Wr）も低下し、起動閾値（T）が上昇している。
        </p>
      </div>
      <div>
        <p style="font-size:12px; color:var(--text-tertiary); margin:0 0 4px;">副対応（TETA）</p>
        <p style="font-size:14px; color:var(--text-secondary); margin:0; line-height:1.6;">
          L（損失予期）が主観的に増幅されている。
          世界が狭い状態では、損失の相対的影響が大きくなり、
          R が一定あっても L が閾値を塞ぐ。
        </p>
      </div>
    </div>
    <p style="font-size:13px; color:var(--text-secondary); margin:0; padding-top:12px; border-top:1px solid var(--line);">
      <span style="font-weight:500;">読み方：</span>
      挑戦の重さは意志の弱さではなく、主観的な損失期待と再起不能感が重さを増やしている。
      世界を広げる（分岐・選択肢・再起可能性の認識を増やす）ことが、L を間接的に緩和する。
    </p>
  </div>

  <!-- 事例5 -->
  <div class="card" style="margin-bottom:16px; padding:24px;">
    <p style="font-size:15px; font-weight:500; margin:0 0 6px;">
      始める前から疲れている
    </p>
    <p style="font-size:13px; color:var(--text-tertiary); margin:0 0 12px;">
      表面的な症状：着手前の消耗感、漠然とした重さ
    </p>
    <div style="display:grid; grid-template-columns:1fr 1fr; gap:16px; margin-bottom:12px;">
      <div>
        <p style="font-size:12px; color:var(--text-tertiary); margin:0 0 4px;">主対応（GATE）</p>
        <p style="font-size:14px; color:var(--text-secondary); margin:0; line-height:1.6;">
          背景流出 D(t) が大きい。未分化な不安、未完了課題、漠然とした懸念が
          明示的な作業の前から残余容量 R(t) を消耗させている。
          感情ノイズ（N）も処理効率を悪化させている。
        </p>
      </div>
      <div>
        <p style="font-size:12px; color:var(--text-tertiary); margin:0 0 4px;">副対応（GATE）</p>
        <p style="font-size:14px; color:var(--text-secondary); margin:0; line-height:1.6;">
          課題複雑性（K）が高く、着手前の認知負荷が大きい。
          外部化（X）が不足しており、頭の中だけで抱えている状態。
          判断軸を外に置くだけで起動閾値が下がりうる。
        </p>
      </div>
    </div>
    <p style="font-size:13px; color:var(--text-secondary); margin:0; padding-top:12px; border-top:1px solid var(--line);">
      <span style="font-weight:500;">読み方：</span>
      「疲れている」は能力不足ではなく、背景流出と未分化な認知負荷による消耗。
      外に書き出し、避けたい状態を具体化するだけで、実質的な負荷が下がる。
    </p>
  </div>

  <!-- 事例6 -->
  <div class="card" style="margin-bottom:16px; padding:24px;">
    <p style="font-size:15px; font-weight:500; margin:0 0 6px;">
      一度うまくいかないと、次に進めなくなる
    </p>
    <p style="font-size:13px; color:var(--text-tertiary); margin:0 0 12px;">
      表面的な症状：失敗後の長期停止、全面撤退
    </p>
    <div style="display:grid; grid-template-columns:1fr 1fr; gap:16px; margin-bottom:12px;">
      <div>
        <p style="font-size:12px; color:var(--text-tertiary); margin:0 0 4px;">主対応（GATE）</p>
        <p style="font-size:14px; color:var(--text-secondary); margin:0; line-height:1.6;">
          レジリエンス（Res）が低く、一度の中断から復帰しにくい。
          分岐が見えていないため、失敗が「観測結果」ではなく
          「最終判定」として処理されている。
        </p>
      </div>
      <div>
        <p style="font-size:12px; color:var(--text-tertiary); margin:0 0 4px;">副対応（TETA）</p>
        <p style="font-size:14px; color:var(--text-secondary); margin:0; line-height:1.6;">
          失敗経験により T（閾値）が上昇し、次回の発現が困難になる。
          本来は T のヒステリシス効果で再挑戦が容易になるはずだが、
          世界が狭い状態ではこの効果が働きにくい。
        </p>
      </div>
    </div>
    <p style="font-size:13px; color:var(--text-secondary); margin:0; padding-top:12px; border-top:1px solid var(--line);">
      <span style="font-weight:500;">読み方：</span>
      「次に進めない」は、失敗そのものの問題より、次の分岐が見えていない構造の問題。
      挑戦→観測→再設計のループが設計されていれば、失敗は次の一手を生む材料になる。
    </p>
  </div>
</div>
```

### セクション3: 変数の凡例

```html
<div class="section">
  <p class="section-label">変数の凡例</p>
  <div class="grid-2">
    <div class="card" style="padding:20px;">
      <p style="font-size:15px; font-weight:500; margin:0 0 10px;">
        TETA の主要変数
      </p>
      <div style="font-size:14px; color:var(--text-secondary); line-height:2.0;">
        <div><span style="font-weight:500;">R</span> — 期待報酬（瞬間的な報酬認識）</div>
        <div><span style="font-weight:500;">L</span> — 損失予期（不確実な損失の主観的予期）</div>
        <div><span style="font-weight:500;">C</span> — 確定コスト（既知の負荷・費用）</div>
        <div><span style="font-weight:500;">D</span> — 駆動因子（緊急性・欠乏感）</div>
        <div><span style="font-weight:500;">T</span> — 動的閾値（行動発現の心理的閾値）</div>
        <div><span style="font-weight:500;">K</span> — 禁忌ゲート（絶対的制約）</div>
      </div>
      <p style="font-size:13px; margin:12px 0 0;">
        <a href="teta.html">TETA について →</a>
      </p>
    </div>
    <div class="card" style="padding:20px;">
      <p style="font-size:15px; font-weight:500; margin:0 0 10px;">
        GATE の主要変数
      </p>
      <div style="font-size:14px; color:var(--text-secondary); line-height:2.0;">
        <div><span style="font-weight:500;">T</span> — 起動閾値（着手に必要な要求強度）</div>
        <div><span style="font-weight:500;">R(t)</span> — 残余容量（今使える可処分資源）</div>
        <div><span style="font-weight:500;">D(t)</span> — 背景流出（持続的な資源漏出）</div>
        <div><span style="font-weight:500;">Q(t)</span> — 回復流量（単位時間あたりの回復量）</div>
        <div><span style="font-weight:500;">K</span> — 課題複雑性（分岐数・不確実性）</div>
        <div><span style="font-weight:500;">N</span> — 感情ノイズ（不安・反すう等の混入）</div>
        <div><span style="font-weight:500;">X</span> — 外部化率（負荷の外部委託度）</div>
        <div><span style="font-weight:500;">Wr</span> — 報酬予測（報われる期待の強さ）</div>
        <div><span style="font-weight:500;">Res</span> — レジリエンス（崩れた後の戻りやすさ）</div>
      </div>
      <p style="font-size:13px; margin:12px 0 0;">
        <a href="gate.html">GATE について →</a>
      </p>
    </div>
  </div>
</div>
```

### ページナビ

```html
<div class="page-nav">
  <a href="applications.html">← Applications</a>
  <a href="index.html">Home →</a>
</div>
```

---

## B. applications.html の修正

### 理論との対応セクションの末尾にリンクを追加

「理論との対応」セクションの最後に以下を追加:

```html
<div style="margin-top:20px;">
  <a href="variable-mapping.html">事例と研究変数の対応を見る →</a>
</div>
```

### 各作品の説明に1行追加

「観測を打ち手に変える事業開発」の paper-links の後に:

```html
<p style="font-size:13px; color:var(--text-secondary); margin:8px 0 0;">
  実務上の停滞事例を、TETA/GATE 上の見立てに接続して読める
  → <a href="variable-mapping.html">事例と変数の対応</a>
</p>
```

「挑戦の重さと世界の広さ」の paper-links の後に:

```html
<p style="font-size:13px; color:var(--text-secondary); margin:8px 0 0;">
  エッセイ内の具体例を、GATE を中心とした変数群との対応で読める
  → <a href="variable-mapping.html">事例と変数の対応</a>
</p>
```

---

## 実装順序

1. `variable-mapping.html` を新規作成
2. `applications.html` にリンクを追加（3箇所）
3. リンク動作確認

各ステップ完了後に確認を入れること。
