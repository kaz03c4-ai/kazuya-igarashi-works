# Overview 関係図の差し替え指示

---

## 概要

overview.html の「研究プログラム全体像」セクションを、HTML/CSS ベースの関係図に差し替える。
既存のプレースホルダ「（ここに関係図を配置）」およびその下のテキストグリッド（理論/展開の2列）を削除し、以下の HTML で置き換える。

---

## 削除対象

「研究プログラム全体像」セクション内の以下をすべて削除:
- 「（ここに関係図を配置）」のテキスト
- もしSVG図が入っていればそれも削除
- 理論 / 展開 の2列テキストグリッド

---

## 差し替えるHTML

以下を「研究プログラム全体像」の section-label 直後に配置する。

```html
<!-- 研究プログラム全体像 -->
<div style="margin-bottom:8px;">
  <div style="display:flex; gap:16px; margin-bottom:8px;">
    <div style="flex:1; background:var(--surface-alt); border-left:4px solid #1e3a5f; padding:20px;">
      <div style="font-size:16px; font-weight:500; margin-bottom:4px; color:#1e3a5f;">TETA</div>
      <div style="font-size:13px; color:var(--text-secondary); margin-bottom:6px;">行動発現の閾値理論</div>
      <div style="font-size:12px; color:var(--text-tertiary);">R · L · C · D · T · K</div>
    </div>
    <div style="flex:1; background:var(--surface-alt); border-left:4px solid #6b4c1e; padding:20px;">
      <div style="font-size:16px; font-weight:500; margin-bottom:4px; color:#6b4c1e;">GATE</div>
      <div style="font-size:13px; color:var(--text-secondary); margin-bottom:6px;">実行可能性の基礎理論</div>
      <div style="font-size:12px; color:var(--text-tertiary);">特性 · 状態 · 文脈変数</div>
    </div>
  </div>

  <div style="text-align:center; font-size:12px; color:var(--text-tertiary); padding:6px 0;">補完的に接続</div>

  <div style="width:1px; height:20px; background:var(--line); margin:0 auto;"></div>
  <div style="height:3px; background:var(--line); margin:0 40px; border-radius:2px;"></div>
  <div style="display:flex; justify-content:space-around; padding:0 60px;">
    <div style="width:1px; height:20px; background:var(--line);"></div>
    <div style="width:1px; height:20px; background:var(--line);"></div>
    <div style="width:1px; height:20px; background:var(--line);"></div>
  </div>

  <div style="text-align:center; font-size:12px; color:var(--text-tertiary); margin-bottom:12px;">両理論から展開</div>

  <div style="display:flex; gap:12px; margin-bottom:20px;">
    <div style="flex:1; background:var(--surface-alt); border:1px solid var(--line); border-radius:8px; padding:14px 16px; text-align:center;">
      <div style="font-size:14px; font-weight:500; margin-bottom:2px;">Papers</div>
      <div style="font-size:12px; color:var(--text-tertiary);">論文 · プレプリント</div>
    </div>
    <div style="flex:1; background:var(--surface-alt); border:1px solid var(--line); border-radius:8px; padding:14px 16px; text-align:center;">
      <div style="font-size:14px; font-weight:500; margin-bottom:2px;">Essays</div>
      <div style="font-size:12px; color:var(--text-tertiary);">翻訳的読み物</div>
    </div>
    <div style="flex:1; background:var(--surface-alt); border:1px solid var(--line); border-radius:8px; padding:14px 16px; text-align:center;">
      <div style="font-size:14px; font-weight:500; margin-bottom:2px;">Applications</div>
      <div style="font-size:12px; color:var(--text-tertiary);">実務応用</div>
    </div>
  </div>

  <div style="display:flex; gap:12px; margin-bottom:8px;">
    <div style="flex:1; display:flex; flex-direction:column; gap:8px;">
      <div style="padding:10px 14px; border:1px solid var(--line); border-radius:6px; background:var(--surface);">
        <div style="font-size:13px; color:var(--text-secondary);">TETA Paper 1</div>
      </div>
      <div style="padding:10px 14px; border:1px solid var(--line); border-radius:6px; background:var(--surface);">
        <div style="font-size:13px; color:var(--text-secondary);">GATE 論文</div>
      </div>
    </div>
    <div style="flex:1; display:flex; flex-direction:column; gap:8px;">
      <div style="padding:10px 14px; border:1px solid var(--line); border-radius:6px; background:var(--surface);">
        <div style="font-size:13px; color:var(--text-secondary);">挑戦の重さと世界の広さ</div>
      </div>
    </div>
    <div style="flex:1; display:flex; flex-direction:column; gap:8px;">
      <div style="padding:12px 14px; border-left:3px solid #1e3a5f; background:var(--surface); border-top:1px solid var(--line); border-right:1px solid var(--line); border-bottom:1px solid var(--line);">
        <div style="font-size:14px; font-weight:500; color:var(--text);">観測を打ち手に変える事業開発</div>
      </div>
      <div style="padding:10px 14px; border:1px solid var(--line); border-radius:6px; background:var(--surface);">
        <div style="font-size:13px; color:var(--text-tertiary);">BizDev Studio（準備中）</div>
      </div>
    </div>
  </div>

  <div style="margin-top:24px; padding:16px 20px; background:var(--surface-alt); border-radius:8px;">
    <div style="font-size:12px; color:var(--text-tertiary); margin-bottom:12px;">各成果物の主な理論基盤</div>
    <div style="display:flex; gap:24px; margin-bottom:10px; font-size:12px;">
      <div style="display:flex; align-items:center; gap:6px;">
        <span style="width:10px; height:10px; background:#1e3a5f; border-radius:2px; display:inline-block;"></span>
        <span style="color:var(--text-secondary);">TETA</span>
      </div>
      <div style="display:flex; align-items:center; gap:6px;">
        <span style="width:10px; height:10px; background:#6b4c1e; border-radius:2px; display:inline-block;"></span>
        <span style="color:var(--text-secondary);">GATE</span>
      </div>
    </div>
    <div style="font-size:13px; line-height:2.0; color:var(--text-secondary);">
      <div style="display:flex; align-items:center; gap:8px;">
        <span>観測を打ち手に変える事業開発</span>
        <span style="font-size:11px; padding:1px 8px; background:#1e3a5f; color:#fff; border-radius:3px;">主</span>
        <span style="font-size:11px; padding:1px 8px; border:1px solid #6b4c1e; color:#6b4c1e; border-radius:3px;">補</span>
      </div>
      <div style="display:flex; align-items:center; gap:8px;">
        <span>挑戦の重さと世界の広さ</span>
        <span style="font-size:11px; padding:1px 8px; background:#6b4c1e; color:#fff; border-radius:3px;">主</span>
        <span style="font-size:11px; padding:1px 8px; border:1px solid #1e3a5f; color:#1e3a5f; border-radius:3px;">補</span>
      </div>
    </div>
  </div>
</div>
```

---

## CSS変数の確認

上記 HTML は styles.css で定義済みの以下の変数を使用している:
- `--surface-alt` = `#f8f9fc`
- `--surface` = `#ffffff`
- `--text` = `#1c2430`
- `--text-secondary` = `#5d6a7a`
- `--text-tertiary` = `#8a94a3`
- `--line` = `#dde4ee`

もし `--surface-alt` が未定義の場合は styles.css の `:root` に追加する:
```css
--surface-alt: #f8f9fc;
```

---

## レスポンシブ

styles.css の既存メディアクエリ `@media (max-width: 700px)` 内に追加不要。
`display:flex` + `gap` の構成なので、極端に狭い画面では自然に縦方向に折り返すが、
もし崩れる場合は以下を追加:

```css
@media (max-width: 700px) {
  /* 関係図のレスポンシブ対応が必要な場合のみ */
}
```

基本的には追加不要の見込み。

---

## 実装手順

1. overview.html の「研究プログラム全体像」セクション内の既存コンテンツを削除
2. 上記 HTML を section-label の直後に挿入
3. `--surface-alt` が styles.css に定義されているか確認、なければ追加
4. ブラウザで表示確認
