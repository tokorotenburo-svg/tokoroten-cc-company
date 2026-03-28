---
created: "2026-03-22"
type: handover
status: active
---

# 引き継ぎ：ポートフォリオ作業（2026-03-22）

## 今日やったこと

- ポートフォリオのコンテンツ一覧を作成（`.secretary/projects/portfolio-content-list.md`）
- ページ構成・各作品の掲載情報・Aboutコンテンツを整理
- 現行のindex.htmlを確認し、フリーランス向けへの改修ポイントを洗い出した

---

## 次にやること（優先順位順）

### 1. キャッチコピーを決める（TOP）
- 現状：「好きな時に、好きな人と、好きなことを。」→ 就活向き
- 方針：「Designer / Planner」感が出る言葉 + ユーモア・個性も残す
- 「と」「接続詞」の哲学をTOPのコピーで全開にしていい場所

### 2. ナビゲーションにServicesを追加
- 現状：トップ / つくったもの / とっとっと / お問い合わせ
- 追加：**Services**（提供サービス・料金）
- 全ページにCTAを置く（最終ゴール：Contactへの誘導）

### 3. Servicesページを新規作成
- デザイン系サービス（Webデザイン・コーディング・ブランディング・グラフィック）
- **なんでも相談セクション**（靴磨きから運転代行でも。ユーモアとして）
- 料金は「要相談」「まずは気軽に相談を」

### 4. About（とっとっと）文章を書き直す
- 就活向けの志望動機っぽい文体 → フリーランス向けに
- 肩書き：**Designer / Planner**
- 自己紹介の一発目：「初めまして。楽しいこととプリンが好きです。」
- 「と」の哲学はそのまま活かす

### 5. Works整理（後回しでOK）
- 掲載作品の取捨選択はportfolio-content-listで整理済み
- Prism Loreはクライアントに掲載交渉が必要

---

## 現行サイトの構成メモ

```
index.html
├── header（ナビ・SNSリンク）
├── mainvisual（キャッチコピー）
├── section#works（つくったもの・4作品）
├── section#play（遊び心セクション）← そのまま活かす
├── section#about（とっとっと）
│   ├── Design と
│   ├── Me と
│   └── You と
└── section#contact（はなしましょ）
```

---

## 確定済み情報

| 項目 | 内容 |
|------|------|
| 肩書き | Designer / Planner |
| 自己紹介 | 「初めまして。楽しいこととプリンが好きです。」 |
| SNS | Instagram / X：inoue_yu_design |
| 顔写真 | 既存写真から選ぶ（Figmaデザイン前に用意） |
| Prism Lore | 掲載交渉必要（止まった企画・初共同作品） |
| インターン作品 | 掲載確定（詳細非公開） |

---

## 作業環境メモ

- ポートフォリオファイル：`/Users/tokoroten/Downloads/portfolio/Web/inoueyuto-portfolio/`
- .secretaryはホームディレクトリにシンボリックリンク済み（`~/.secretary`）
- どのディレクトリで開いても同じ.secretaryが使える
