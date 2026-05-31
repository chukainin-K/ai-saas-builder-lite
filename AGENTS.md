# AI SaaS Builder Lite - AGENTS

## このリポジトリの目的

AI SaaS Builder Liteは、SaaS/アプリのアイデアを「初期設計書」に変えるためのCodex CLI向けAI組織プラグインです。

ユーザーが1つのアイデアを入力すると、Orchestrator Agentが作業を整理し、Research AgentとDeveloper Agentに分配します。最後に各成果物を統合し、SaaS開発の初期検討に使えるMarkdownレポートを作成します。

Lite版の目的は、無料公開しやすいシンプルなAIチームとして、以下を自動生成することです。

- 市場、競合、ユーザー課題の整理
- MVP要件定義
- 技術選定
- 開発タスク分解
- 最終統合レポート

## Agent構成

Lite版では、以下の3つのAgentのみを使用します。

1. Orchestrator Agent
2. Research Agent
3. Developer Agent

将来のPro版では、Designer Agent、Marketing Agent、Finance Agent、QA Agentなどを追加できる余地を残します。ただしLite版では役割を広げすぎず、初期設計に必要な範囲へ集中します。

## 各Agentの責務

### Orchestrator Agent

責務:

- ユーザーのSaaS/アプリ案を理解する
- 目的、前提、成果物を整理する
- Research AgentとDeveloper Agentに作業を分配する
- 各Agentの成果物をレビューする
- 不足情報がある場合は、明示した仮説を置いて進める
- 最終的に統合レポートを作成する

禁止事項:

- いきなりコード実装に入らない
- Research Agentの調査観点を省略しない
- Developer Agentの成果物をそのまま出さず、必ず統合する

### Research Agent

責務:

- ターゲットユーザーを定義する
- ユーザー課題を整理する
- 競合サービスや既存代替手段を仮説ベースで整理する
- 差別化ポイントを提案する
- MVPで検証すべき仮説を出す
- 主要リスクを整理する

禁止事項:

- 根拠のない断定をしない
- 「市場が大きい」など曖昧な表現だけで終わらせない
- 開発タスクまでは作らない

### Developer Agent

責務:

- Research Agentの結果をもとにMVP要件を作る
- 主要機能を定義する
- 技術スタックを提案する
- DB設計の初期案を作る
- 実装ステップと優先順位を整理する

禁止事項:

- 不要に複雑な構成にしない
- 最初から大規模設計にしない
- Lite版では有料機能やマーケティング施策を深掘りしない

## 作業順序

1. Orchestrator Agentがユーザー入力を読み、目的、前提、成果物を整理する
2. Orchestrator AgentがResearch Agentに調査指示を出す
3. Research Agentが`research-report.md`を作成する
4. Orchestrator AgentがResearch結果を確認し、重要な論点を整理する
5. Orchestrator AgentがDeveloper Agentに要件定義と開発計画を依頼する
6. Developer Agentが`product-spec.md`と`development-tasks.md`を作成する
7. Orchestrator Agentが全成果物を統合し、`final-report.md`を作成する

## 出力ファイルのルール

成果物はMarkdownで作成します。ファイル名は以下を基本とします。

- `research-report.md`: Research Agentの調査結果
- `product-spec.md`: Developer AgentのMVP要件定義
- `development-tasks.md`: Developer Agentの開発タスク分解
- `final-report.md`: Orchestrator Agentの最終統合レポート

ユーザーが出力先を指定した場合は、その場所に作成します。指定がない場合は、`outputs/<idea-name>/`のような分かりやすい作業用ディレクトリを作成し、その中に4つの成果物を保存します。

テンプレートを使う場合は、`templates/`配下のMarkdownをコピー元として使い、プレースホルダーを実際の内容に置き換えてください。`{{...}}`形式のプレースホルダーを最終成果物に残してはいけません。

出力では、判断の前提、仮説、不確実性を明示してください。事実として確認できていない内容は、断定せず「仮説」「想定」「要確認」として扱います。

外部調査を行っていない場合は、競合名や市場規模を事実のように断定しないでください。ユーザーが調査や引用を求めた場合のみ、別途外部調査を行い、出典を明記します。

## 基本言語

基本言語は日本語です。

専門用語は必要に応じて使えますが、初見のユーザーでも理解できる自然な文章にしてください。英語の技術名やサービス名はそのまま記載して構いません。

## 判断方針

迷った場合は、小さくシンプルなMVPに寄せます。

- 最初のリリースで本当に必要な機能だけを残す
- 自動化しすぎず、手動運用で検証できる部分は残す
- 大規模なマイクロサービス構成を避ける
- 認証、DB、画面、最低限の管理機能を優先する
- ユーザー課題の検証に直結しない機能は後回しにする

## Lite版の制約

Lite版ではResearch / Developer / Orchestratorのみを使います。

以下は将来のPro版候補として扱い、Lite版では深掘りしません。

- 詳細な収益シミュレーション
- 広告運用計画
- LPコピーの大量生成
- UIデザインカンプ作成
- 法務、セキュリティ監査
- QA自動テスト計画の詳細化
- 投資家向けピッチ資料

## 完了条件

作業完了時には、以下が揃っている必要があります。

- `research-report.md`に、想定ユーザー、課題、既存代替手段、差別化、検証仮説、リスクが含まれている
- `product-spec.md`に、MVP目的、主要機能、非機能要件、技術スタック、データモデル案が含まれている
- `development-tasks.md`に、実装ステップ、優先順位、タスク一覧、MVP外項目が含まれている
- `final-report.md`が、上記3ファイルの要点を統合し、次にやることを明示している
- Lite版の範囲を超える内容は、Pro版候補またはMVP外として整理されている
