---
created: "2026-03-29"
type: research
tags: [design, portfolio, dark, SF, cyberpunk, GSAP]
---

# ダーク×SF系ポートフォリオ デザインリサーチ

## 1. 参照サイト分析

### 1-1. oniguili.jp

| 項目 | 内容 |
|------|------|
| フレームワーク | Astro |
| アニメーション | `astroFadeInOut` / `astroSlideFromRight` / `astroSlideFromLeft` によるページ遷移 |
| FV構成 | 「ONIGUILI」大型ロゴ + "お に ぎ り"の視覚的分割表現 |
| ブレンドモード | `mix-blend-mode: plus-lighter` による加算合成で透明感を演出 |
| ローディング | `sessionStorage` で初回訪問を判定し、段階的コンテンツ読み込み |

**参考にできる点:**
- 日本語ブランド名を英語表記と組み合わせてアイデンティティとして昇華する手法
- 初回訪問時のローディング演出（sessionStorage活用）
- 加算合成（plus-lighter）による透明感のあるビジュアル表現

---

### 1-2. yuto-takahashi.com

| 項目 | 内容 |
|------|------|
| 背景色 | `#141414` / `#101010` |
| テキスト色 | `#fff` / `#dadada` |
| アクセント | `#710f29`（ワインレッド）/ `#b93224`（オレンジレッド） |
| フォント（欧文） | `ogg-roman` / `ogg-italic`（カスタム） |
| レイアウト | `73vw` コンテナ幅 / 100vh フルスクリーンセクション |
| カーソル | カスタムカーソル（8px小円 + 48px大円）のマウスストーカー |
| テクスチャ | GIFノイズ（opacity: 0.05）を背景に重ねた質感表現 |
| 文字効果 | `-webkit-text-stroke` でSVGストローク文字（透明文字を輪郭表示） |

**参考にできる点:**
- ノイズテクスチャの微細な重ね（0.05以下のopacity）が質感を加える
- SVGストローク文字による透明テキストアウトライン演出
- GIFノイズで「生っぽい」質感を低コストで実現

---

### 1-3. junkata.com

**備考:** SSL証明書エラーにより直接アクセス不可（2026-03-29時点）

**判明している特徴:**
- React + Three.js構成
- Awwwards Nominee（ノミネート）獲得
- インタラクティブな3D要素を含む設計

---

## 2. ダーク系ポートフォリオ事例（12件）

### Yanchen Portfolio
- **特徴:** ブラック＆ホワイトのミニマル / GSAP Animation / Locomotive Scroll
- **参考:** モノクロ×タイポグラフィ主体ポートフォリオの最高峰

### Obys Agency（https://obys.agency/）
- **特徴:** フルスクリーン+視差スクロール / マグネティックカーソル / セクション番号付き構成
- **参考:** ローディングからFVへのシームレス移行、番号付きセクション構成

### Ashfall Studio（https://ashfall.studio/）
- **受賞:** Awwwards SOTD（2024年7月）
- **カラー:** `#fffefb`（オフホワイト）/ `#212121`（ダークチャコール）/ `#eaffb0`（ライムグリーン）
- **参考:** ←このカラー構造が温白×墨黒×黄色と近い。最良の参照先。
- **技術:** clip-path / スティッキースクロール / 6〜8列グリッド

### SALT AND PEPPER（https://snp.agency/）
- **受賞:** Awwwards SOTD（2024年9月）/ FWA / CSSDA
- **特徴:** インタラクティブ粒子流体シミュレーション / Three.js 3Dギャラリー / セクション番号ナビ

### Roman Jean-Elie Portfolio
- **特徴:** 折り畳みシェーダー効果 / ポータルシステム / スクロール速度連動テキストひずみ
- **参考:** スクリーン自体を変形させるという設計思想

### Keita Yamada Portfolio（https://p5aholic.me/）
- **特徴:** Three.js + GLSL / Light/Dark/Monospacedの3テーマ切り替え / WebGLバックグラウンド

### Lusion Labs（https://labs.lusion.co/）
- **特徴:** 実験的インタラクション17作品 / 「実験室」としてのフレーミング手法
- **参考:** ポートフォリオを「ショーケース」でなく「実験場」として見せるアプローチ

### DEGENESIS（https://degenesis.com/）
- **特徴:** ゲーム世界観をWebで表現したダークSF系 / Nuxt.js
- **参考:** フィクション的世界観をWebに落とし込む手法（デッドデッドデーモンズ的）

### Samsy Ninja（https://samsy.ninja/）
- **受賞:** カンヌライオンズを含む国際50賞以上
- **特徴:** 3D対話型グラフィックス / 計算デザイン / WebGLシェーダーインタラクション

---

## 3. FV構成パターン

### Pattern A: タイポグラフィ主体型
大型タイトルテキストがFVほぼ全面を占める。名前・肩書き・キャッチが3層構造。
```css
.hero-title {
  font-size: clamp(4rem, 15vw, 18rem);
  line-height: 0.9;
  letter-spacing: -0.04em;
}
```

### Pattern B: ビジュアル主体型
過去の制作物（モックアップ・グリッド）をFVに配置。テキストはオーバーレイで最小限。

### Pattern C: アニメーション主体型（← ところてんはここ）
ローディングがそのままFVへシームレス移行。「と」3D押し出しはこのパターン。
```javascript
const tl = gsap.timeline();
tl
  .to(toChar.rotation, { y: Math.PI * 2, duration: 1.2, ease: "power3.out" })
  .to(toChar.position, { z: 2, duration: 0.8, ease: "back.out(1.7)" }, "-=0.5")
  .to(overlay, { opacity: 0, duration: 0.6 }, "-=0.3")
  .from(".hero-title", { y: 60, opacity: 0, stagger: 0.08, duration: 0.8 }, "-=0.2");
```

### Pattern D: フルスクリーン固定型（Stickyセクション）
100vh単位でセクションがpin。スクロールでシーンが切り替わる。
```javascript
ScrollTrigger.create({
  trigger: section,
  start: "top top",
  end: "+=100%",
  pin: true,
  pinSpacing: false,
});
```

---

## 4. SF感を出すデザインテクニック

### ノイズ・グレイン質感
```css
.noise-overlay {
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 9999;
  opacity: 0.04; /* 0.03〜0.06が自然 */
  mix-blend-mode: overlay;
}
/* SVGフィルター: baseFrequency 0.65=細粒子 / 0.2=粗粒子 */
```

### スキャンライン効果（CRTモニター感）
```css
.scanlines {
  background: repeating-linear-gradient(
    0deg, transparent, transparent 2px,
    rgba(0,0,0,0.03) 2px, rgba(0,0,0,0.03) 4px
  );
}
```

### グロー（発光）効果
```css
.glow-text {
  color: #FFF000;
  text-shadow:
    0 0 10px rgba(255,240,0,0.8),
    0 0 30px rgba(255,240,0,0.4),
    0 0 60px rgba(255,240,0,0.2);
}
```

### グリッチ・クロマティックアベレーション
```css
@keyframes glitch {
  20% {
    clip-path: inset(40% 0 50% 0);
    transform: translate(2px, 0);
    color: #FFF000; /* 黄色に化ける瞬間 */
  }
}
```

### ストローク文字（アウトラインテキスト）
```css
.outline-text {
  -webkit-text-stroke: 1px var(--color-warm-white);
  color: transparent;
  font-size: clamp(6rem, 18vw, 22rem);
}
```

### clip-pathリビール演出
```javascript
gsap.from(".reveal-text", {
  clipPath: "inset(100% 0% 0% 0%)",
  duration: 1.2,
  ease: "power4.out",
  stagger: 0.1,
});
```

---

## 5. ところてんポートフォリオへの応用

### カラーCSS変数設計
```css
:root {
  --color-ink:        #0D0C09;
  --color-warm:       #F0EDE4;
  --color-yellow:     #FFF000;
  --color-gray:       #7A7772;
  --color-yellow-glow: rgba(255,240,0,0.3);

  --font-display-en:  'Ten Oldstyle', Georgia, serif;
  --font-display-ja:  '貂明朝', serif;
  --font-body-en:     'Neue Haas Grotesk', sans-serif;
  --font-body-ja:     'FOT-筑紫ゴシック Pro', sans-serif;
}
```

### 黄色の使いどころ（1色アクセントのルール）
- CTAボタンの背景またはボーダー
- ナビゲーションのアクティブ状態
- セクション番号（01. 02. 03.）
- ホバー時のアンダーライン
- ローディング「と」のグロー色
- **使わないこと：** 本文テキスト / 大面積の背景

### FV設計案（推奨: Pattern A × C の組み合わせ）
```
[ローディング 2.5秒]
  └→ 「と」の3D押し出し（Three.js）
      └→ 背景に墨黒、温白の「TOKOROTEN」が現れる

[FV]
  ├─ 左: TOKOROTEN / ところてん（大型）
  ├─ 右: "Web Designer & Planner"
  ├─ 下: スクロールインジケーター（黄色ライン）
  └─ 背景: #0D0C09 + ノイズオーバーレイ（opacity: 0.04）
```

### セクション構成案
```
01. HERO    → 「と」ローディング後のタイポグラフィFV
02. WORKS   → ダーク背景のプロジェクトグリッド（hover時に黄色タグ）
03. ABOUT   → 左:ポートレート / 右:プロフィール
04. SKILLS  → タイポグラフィのみ（スキルをキーワードで羅列）
05. CONTACT → 黄色CTAボタン × 墨黒背景
```

### 「本気の箱×ゆるいもの」の表現案

| 「本気」の部分 | 「ゆるい」部分 |
|-------------|-------------|
| 墨黒×温白の厳格な配色 | 黄色の唐突な登場 |
| Ten Oldstyle / 貂明朝の格調あるフォント | コピーの文体（敬語×ため口の混在） |
| グリッドに沿ったレイアウト | ところどころ外れる要素 |
| GSAPの滑らかなアニメーション | 「と」の3D演出という唐突な遊び |
| ノイズテクスチャの精緻な制御 | グリッチエフェクトのランダムな介入 |

### Figma設計前チェックリスト
- [ ] カラートークン定義（5色 × 透過バリエーション）
- [ ] タイポグラフィスケール設定（clamp()対応）
- [ ] グリッドシステム決定（12列 / ガター24px / マージン40–80px）
- [ ] コンポーネント一覧（カード・ボタン・ナビ・タグ）
- [ ] アニメーション仕様書（イージング・デュレーション）
- [ ] ローディングシーケンスのストーリーボード
- [ ] ブレイクポイント設計（1440 / 1024 / 768 / 390px）

---

## 参考リンク
- [Awwwards Portfolio Winners](https://www.awwwards.com/websites/winner_category_portfolio/)
- [Ashfall Studio](https://ashfall.studio/) ← 最良の参照先
- [Obys Agency](https://obys.agency/)
- [Lusion Labs](https://labs.lusion.co/)
- [GSAP ScrollTrigger Docs](https://gsap.com/docs/v3/Plugins/ScrollTrigger/)
- [Codrops 3D Scroll Text Animation](https://tympanus.net/codrops/2025/11/04/creating-3d-scroll-driven-text-animations-with-css-and-gsap/)
- [Top 100 Creative Portfolios 2025 - Muzli](https://muz.li/blog/top-100-most-creative-and-unique-portfolio-websites-of-2025/)
