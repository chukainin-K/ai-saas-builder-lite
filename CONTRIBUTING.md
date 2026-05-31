# Contributing

AI SaaS Builder Liteへの改善提案を歓迎します。

このリポジトリはv0.1のLite版として、シンプルなAI組織テンプレートを保つことを優先します。

## 方針

- 日本語ユーザーが初見で使える文章にする
- Lite版ではOrchestrator / Research / Developerの3Agentに留める
- 実装コード生成ではなく、SaaS初期設計書の作成に集中する
- Pro版候補は追加してよいが、Lite版の標準ワークフローに混ぜすぎない
- テンプレートの項目を増やす場合は、MVP検証に必要な理由を明確にする

## 変更時の確認

Pull Requestや大きな変更前には、以下を確認してください。

- READMEだけで使い方が分かる
- AGENTS.mdだけでCodex CLIが作業順序を判断できる
- 各Agentの責務が重複しすぎていない
- `examples/pet-health-app.md`が最新のテンプレートと大きくズレていない
- Lite版として過剰な機能追加になっていない

## Issueの例

- READMEの分かりにくい箇所
- Agent指示の曖昧な箇所
- テンプレートの不足項目
- サンプル出力の改善案
- Pro版に回すべき拡張案
