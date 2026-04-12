# 研究母艦サイト — 著者情報追加（v3 追加修正）

v3 実装済みの状態に対する小修正。

---

## 修正1: overview.html に著者セクションを追加

ページ末尾（ページナビの直前）に以下のセクションを追加する。

```html
<div class="section">
  <p class="section-label">Author</p>
  <div class="card" style="padding:28px;">
    <p style="font-size:17px; font-weight:500; margin:0 0 4px;">五十嵐 和也（Kazuya Igarashi）</p>
    <p style="font-size:14px; color:var(--text-secondary); margin:0 0 16px;">Independent Researcher</p>
    <p style="font-size:14px; color:var(--text-secondary); margin:0 0 16px; line-height:1.7;">
      行動発現と実行可能性に関する理論研究を行う独立研究者。<br>
      事業開発と組織運営の実務経験を背景に、現場で繰り返し観察される<br>
      「情報はあるが打ち手に変わらない」停滞構造の理論化に取り組んでいる。
    </p>
    <div style="font-size:14px; display:flex; gap:8px; align-items:center; flex-wrap:wrap;">
      <a href="https://orcid.org/0009-0004-7324-0694" target="_blank" rel="noopener">ORCID</a>
      <span class="link-sep">·</span>
      <a href="https://zenodo.org/search?q=metadata.creators.person_or_org.name%3A%22Igarashi%2C+Kazuya%22" target="_blank" rel="noopener">Zenodo</a>
      <span class="link-sep">·</span>
      <a href="https://www.linkedin.com/in/igarashi-kazuya-34816161/" target="_blank" rel="noopener">LinkedIn</a>
    </div>
  </div>
</div>
```

---

## 修正2: 全ページのフッターを更新

現在のフッター:
```html
<footer class="site-footer">
  <a href="overview.html">Overview</a> · <a href="teta.html">Papers</a> · <a href="applications.html">Applications</a> · <a href="mailto:kaz.03c4@gmail.com">Contact</a>
  <br>kaz.03c4@gmail.com
</footer>
```

以下に変更（全ページ共通）:
```html
<footer class="site-footer">
  <div style="margin-bottom:10px;">
    <a href="overview.html">Overview</a> · <a href="teta.html">Papers</a> · <a href="applications.html">Applications</a>
  </div>
  <div style="margin-bottom:6px;">
    Kazuya Igarashi / 五十嵐 和也 — Independent Researcher
  </div>
  <div>
    <a href="https://orcid.org/0009-0004-7324-0694" target="_blank" rel="noopener">ORCID</a> ·
    <a href="https://zenodo.org/search?q=metadata.creators.person_or_org.name%3A%22Igarashi%2C+Kazuya%22" target="_blank" rel="noopener">Zenodo</a> ·
    <a href="https://www.linkedin.com/in/igarashi-kazuya-34816161/" target="_blank" rel="noopener">LinkedIn</a> ·
    <a href="mailto:kaz.03c4@gmail.com">Contact</a>
  </div>
</footer>
```

対象ファイル:
- index.html
- overview.html
- teta.html
- gate.html
- applications.html

---

## 実装順序

1. overview.html に Author セクション追加
2. 全5ページのフッター更新
3. 確認: 全ページのフッターが統一されていること
