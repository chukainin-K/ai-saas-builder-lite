# AI SaaS Builder Lite

AI SaaS Builder Liteは、SaaS/アプリのアイデアを初期設計書に変えるCodex CLI向けAI組織プラグインです。

コンセプトは「アイデアをSaaS設計書に変えるAIチーム」。

ユーザーが1つのアイデアを入力すると、Orchestrator AgentがResearch AgentとDeveloper Agentに作業を分配し、SaaS開発の初期検討に使えるMarkdownレポートを作成します。

このLite版は、最初のMVPを決めるための無料公開版です。大きな事業計画や詳細な実装ではなく、「誰の、どの課題を、最初にどう検証するか」を短時間で整理することに集中します。

## 何ができるか

- ターゲットユーザーと課題の整理
- 既存代替手段、競合、差別化ポイントの仮説作成
- MVPで検証すべき仮説の整理
- MVP要件定義
- 技術スタックの初期提案
- データモデル案の作成
- 開発タスクと優先順位の分解
- 最終統合レポートの作成

## 作成される成果物

| ファイル | 内容 |
| --- | --- |
| `research-report.md` | 想定ユーザー、課題、既存代替手段、差別化、検証仮説、リスク |
| `product-spec.md` | MVPの目的、主要機能、非機能要件、技術スタック、データモデル案 |
| `development-tasks.md` | 実装ステップ、優先順位、タスク一覧、MVP外に回す項目 |
| `final-report.md` | Orchestrator Agentによる最終統合レポート |

## 想定ユーザー

- SaaSやアプリのアイデアを持っている個人開発者
- 事業アイデアを素早く整理したい起業準備中の人
- クライアント提案前に初期設計を作りたい開発者
- Codex CLIを使って企画から開発準備まで進めたい人

## 使い方

1. このリポジトリをCodex CLIで開きます。
2. 下の使用例のように、作りたいSaaS/アプリのアイデアを入力します。
3. Codexに`AGENTS.md`と`workflows/saas-builder-lite.md`に従って進めるよう依頼します。
4. `outputs/<idea-name>/`などの作業用ディレクトリにMarkdown成果物を作成します。

成果物の出力先を指定しない場合は、Codexに分かりやすい名前のディレクトリを作らせるのがおすすめです。

## Codex CLIでの使用例

```text
AI SaaS Builder Liteとして、以下のアイデアをSaaS設計書にしてください。

参照:
- AGENTS.md
- workflows/saas-builder-lite.md

アイデア:
ペットの健康状態を記録し、通院履歴やワクチン予定を管理できるアプリを作りたい。

出力:
- outputs/pet-health-app/research-report.md
- outputs/pet-health-app/product-spec.md
- outputs/pet-health-app/development-tasks.md
- outputs/pet-health-app/final-report.md
```

## サンプル入力

```text
個人クリエイターが請求書、納品物、契約期限をまとめて管理できるSaaSを作りたい。
```

## サンプル出力

```markdown
# Final Report

## アイデア概要
個人クリエイター向けに、請求書、納品物、契約期限を一元管理するSaaS。

## 想定ユーザー
- フリーランスデザイナー
- 動画編集者
- ライター
- 小規模制作チーム

## MVP
- 顧客管理
- 案件管理
- 請求書ステータス管理
- 契約期限リマインダー

## 技術スタック
- Frontend: Next.js
- Backend: Next.js API Routes
- Database: PostgreSQL
- Auth: Supabase Auth
- Hosting: Vercel
```

詳細なサンプルは`examples/pet-health-app.md`を参照してください。

## ディレクトリ構成

```text
ai-saas-builder-lite/
  AGENTS.md
  README.md
  agents/
    orchestrator.md
    researcher.md
    developer.md
  workflows/
    saas-builder-lite.md
  templates/
    idea-input.md
    research-report.md
    product-spec.md
    development-tasks.md
    final-report.md
  examples/
    pet-health-app.md
  .codex-plugin/
    plugin.json
```

## Lite版と将来のPro版の違い

| 項目 | Lite版 | 将来のPro版候補 |
| --- | --- | --- |
| Agent構成 | Orchestrator / Research / Developer | Designer / Marketing / Finance / QAなどを追加 |
| 調査 | 仮説ベースの市場、競合、課題整理 | 外部調査、引用、詳細な市場規模分析 |
| 要件定義 | MVP中心 | ロードマップ、権限設計、業務フローまで拡張 |
| 技術設計 | 初期構成案 | 詳細アーキテクチャ、セキュリティ、運用設計 |
| 開発計画 | タスク分解 | スプリント計画、見積もり、テスト計画 |
| 出力 | Markdown | Markdown、スライド、チケット、仕様書テンプレート |

## Lite版でやらないこと

- 実装コードの自動生成
- 詳細な市場規模調査
- 法務、会計、医療などの専門判断
- 本格的なUIデザインカンプ作成
- 課金、広告、営業施策の深掘り

## コントリビューション

改善提案やIssueは歓迎です。詳しくは`CONTRIBUTING.md`を参照してください。

## ライセンス

MIT Licenseです。詳しくは`LICENSE`を参照してください。
