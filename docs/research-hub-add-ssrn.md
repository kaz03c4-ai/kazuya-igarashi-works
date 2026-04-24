# Research Hub に SSRN 情報を追加する

## 目的

両論文が SSRN 上で DISTRIBUTED 状態になったため、Research Hub 上の論文リンク箇所すべてに SSRN（Abstract ID 併記）を並記する。既存の Zenodo リンクは維持し、その横に SSRN を追加する形。

## 確定情報

| 論文 | SSRN Abstract ID | SSRN URL |
|------|------------------|----------|
| TETA Paper 1 | `6502984` | `https://ssrn.com/abstract=6502984` |
| GATE 論文    | `6509525` | `https://ssrn.com/abstract=6509525` |

リンク表示形式：
- TETA: `SSRN (6502984) ↗`
- GATE: `SSRN (6509525) ↗`

すべての SSRN リンクに `target="_blank" rel="noopener"` を付ける。

---

## Stage 1. 現状把握

まず Zenodo が参照されている全ファイルを洗い出す：

```bash
grep -rn "zenodo\|ZENODO" --include="*.html"
```

出てきたファイル一覧を Stage 2 以降の更新対象のベースラインとする。

**ここで一度止めて、grep 結果を確認してから次へ進むこと。**

---

## Stage 2. 論文一覧ページ（index / teta / gate）

### 対象

- `index.html` の「公開物」セクションにある paper-item（TETA と GATE の2つ）
- `teta.html` 内の TETA Paper 1 リンク箇所
- `gate.html` 内の GATE 論文リンク箇所

### 変更パターン

既存の paper-item は以下の構造になっているはず（セパレータのクラス名はファイルによって `.link-sep` もしくは生の中黒 `·` のいずれか）：

```html
<a href="teta-paper.html">日本語版を読む →</a>
<span class="link-sep">·</span>
<a href="https://doi.org/10.5281/ZENODO.19351996" target="_blank" rel="noopener">Zenodo ↗</a>
```

これを以下に変える（**Zenodo の直後に SSRN を追加**）：

```html
<a href="teta-paper.html">日本語版を読む →</a>
<span class="link-sep">·</span>
<a href="https://doi.org/10.5281/ZENODO.19351996" target="_blank" rel="noopener">Zenodo ↗</a>
<span class="link-sep">·</span>
<a href="https://ssrn.com/abstract=6502984" target="_blank" rel="noopener">SSRN (6502984) ↗</a>
```

GATE 側は `ZENODO.19385395` の直後に `SSRN (6509525)` を追加する。

### 作業順

1. `index.html` の TETA paper-item 更新 → 保存 → ブラウザ確認
2. `index.html` の GATE paper-item 更新 → 保存 → ブラウザ確認
3. `teta.html` の TETA Paper 1 リンク箇所を更新 → 保存 → ブラウザ確認
4. `gate.html` の GATE 論文リンク箇所を更新 → 保存 → ブラウザ確認

### 禁則

- 既存の Zenodo リンクは削除も改変もしない
- リンク順は「日本語版 → Zenodo → SSRN」を厳守（SSRN を冒頭や中間に入れない）
- セパレータ（`·`）の見た目が既存と揃うよう、既存と同じクラス／マークアップを使う

**Stage 2 完了時点で一度止めて、index / teta / gate の3ページがすべて正しく表示されることを確認すること。**

---

## Stage 3. teta-paper.html / gate-paper.html の xref バナー

### 対象

各論文 HTML の冒頭にある xref バナー（現状「正式版は Zenodo（DOI: …）で公開しています」といった一文の箇所）。

### 変更パターン

現状が単一リンクの場合：

```html
<p class="xref">
  本文の正式版（英語・PDF）は <a href="https://doi.org/10.5281/ZENODO.19351996" target="_blank" rel="noopener">Zenodo</a> で公開しています。
</p>
```

これを Zenodo / SSRN 並記に変える：

```html
<p class="xref">
  本文の正式版（英語・PDF）は <a href="https://doi.org/10.5281/ZENODO.19351996" target="_blank" rel="noopener">Zenodo</a> および <a href="https://ssrn.com/abstract=6502984" target="_blank" rel="noopener">SSRN (6502984)</a> で公開しています。
</p>
```

`gate-paper.html` が存在する場合、Zenodo DOI は `ZENODO.19385395`、SSRN Abstract ID は `6509525` に差し替える。

### 注意点

- バナー文面が若干違っていても、目的は「Zenodo と SSRN の両方を並列で案内する」こと
- 論文本文（Abstract 以降）には手を入れない

**Stage 3 完了時点で一度止めて、論文 HTML 冒頭のバナー表示を確認すること。**

---

## Stage 4. overview.html / about.html

### overview.html

「公開状況」「公開物」相当のセクション、または既存の論文言及箇所に、両論文が Zenodo / SSRN の両方で公開されていることを一文添える：

```html
<p>
  いずれの論文も Zenodo および SSRN でプレプリントとして公開している。
  SSRN Abstract ID は TETA Paper 1 が <code>6502984</code>、GATE 論文が <code>6509525</code>。
</p>
```

該当セクションが存在しない場合は、既存の論文説明の文末に1文として追加するのでも可。

### about.html

「外部リンク」「Links」等のセクションがある場合、Zenodo や ORCID と並んで SSRN Author Page（または各論文の Abstract URL）を追加する。SSRN Author Page の URL が未確定なら、今回は論文単位の URL のみ `overview.html` に記載し、`about.html` の修正はスキップしてよい。

---

## Stage 5. 横断チェック

### grep

```bash
# Zenodo が参照されているすべての箇所
grep -rn "zenodo.org\|ZENODO\." --include="*.html"

# SSRN リンクの総数（TETA と GATE で分けて確認）
grep -rn "ssrn.com/abstract=6502984" --include="*.html"
grep -rn "ssrn.com/abstract=6509525" --include="*.html"
```

Zenodo が出てくる行の近傍すべてに SSRN が並んでいること。抜け漏れがあれば Stage 2〜4 に戻って補う。

### 目視確認

- index.html / teta.html / gate.html すべての paper-item に SSRN リンクが並記されている
- teta-paper.html（と gate-paper.html があれば）の xref バナーで Zenodo + SSRN 両方が案内されている
- SSRN リンクの Abstract ID は TETA=6502984、GATE=6509525 で正しい
- すべての SSRN リンクに `target="_blank"` と `rel="noopener"` が付いている
- モバイル幅（375px）で、3リンク並記が改行しても読めること（折り返しは許容）
- リンクカラー・下線スタイルが既存の Zenodo リンクと同一（スタイル追加は不要のはず）

### コミット

Stage 2〜4 は独立しているので、段階ごとに分けてコミットしてよい：

```
Stage 2: add SSRN links to paper listings (index / teta / gate)
Stage 3: add SSRN to xref banner in teta-paper.html (and gate-paper.html if present)
Stage 4: mention SSRN publication in overview.html
```

---

## 実装順序まとめ

1. Stage 1: grep で現状把握 → **停止して確認**
2. Stage 2: 論文一覧3ページを更新 → **停止して確認**
3. Stage 3: 論文 HTML の xref バナー更新 → **停止して確認**
4. Stage 4: overview.html（必要に応じて about.html）更新 → **停止して確認**
5. Stage 5: grep + 目視で最終確認

各ステージ完了時に必ず停止点を入れ、独断で一括実装しないこと。
