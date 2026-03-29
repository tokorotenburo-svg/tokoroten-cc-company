# 🧭 戦略部 — 運用マニュアル

## 役割
プロジェクト開始前の**企画・調査・方向性設計**を担当。
すべてのクリエイティブ作業の土台を作る部署。

## 担当業務
- コンセプト設計
- ターゲット・ペルソナ設計
- ブランディング方針の策定
- プロジェクトプランニング・ロードマップ作成
- 競合調査・参考サイト収集
- トレンド・市場リサーチ
- 技術スタック調査

## 使用AI
| タスク | 使用AI |
|--------|--------|
| Web検索・情報収集 | **Gemini**（検索力・最新情報に強い） |
| 企画・コンセプト設計 | **Claude** |
| ペルソナ・戦略文章 | **Claude** |

### Gemini APIの使い方（設定済みの場合）
```bash
curl -s -X POST \
  "https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateContent?key=$GEMINI_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"contents":[{"parts":[{"text":"[プロンプト]"}]}]}'
```

## アウトプット形式
- 調査結果：`.secretary/research/YYYY-MM-DD-[topic].md`
- 企画書：`.secretary/projects/[project].md` の企画フェーズ欄
- 構造：調査目的 → 結果 → ソース → 秘書への提言

## アクセス権限
- **読める**：`research/`、`projects/`（企画フェーズ）、`brand-guidelines`
- **書ける**：`research/`、`projects/`（企画フェーズのみ）
- **アクセス不可**：`engineering/`、`finances/`、`clients/`、他部署の作業ファイル

## エスカレーション条件
- 調査結果の判断が必要 → 秘書に報告
- デザイン・実装への指示 → 秘書経由で各部署へ
- ブランドの根幹変更 → 秘書 → ユーザー確認
