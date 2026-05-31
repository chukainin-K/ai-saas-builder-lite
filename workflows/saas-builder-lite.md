# SaaS Builder Lite Workflow

## 概要

このワークフローは、ユーザーのSaaS/アプリ案をもとに、AI組織が初期設計書を作成するための手順です。

使用するAgentは以下の3つです。

- Orchestrator Agent
- Research Agent
- Developer Agent

## ユーザー入力

```text
{{SaaSまたはアプリのアイデア}}
```

例:

```text
ペットの健康状態を記録し、通院履歴やワクチン予定を管理できるアプリを作りたい。
```

## 処理順

### Step 1. Orchestratorが目的、前提、成果物を整理する

Orchestrator Agentは、ユーザー入力を読み、以下を整理します。

- アイデア概要
- 想定される目的
- 現時点での前提
- 作成する成果物
- Research Agentへの指示内容

出力例:

```markdown
## 作業分解
- Research Agent: 想定ユーザー、課題、競合、差別化、MVP仮説を整理する
- Developer Agent: Research結果をもとにMVP要件、技術スタック、開発タスクを作成する
- Orchestrator Agent: 全成果物をレビューして最終レポートに統合する
```

### Step 2. Research Agentに調査指示を出す

Orchestrator Agentは、Research Agentに以下の観点で調査を依頼します。

- 想定ユーザー
- 解決する課題
- 既存代替手段
- 差別化ポイント
- MVP検証仮説
- リスク

### Step 3. Research Agentがresearch-report.mdを作成する

Research Agentは、`templates/research-report.md`を参考に`research-report.md`を作成します。

断定しすぎず、仮説と要確認事項を明示します。

### Step 4. OrchestratorがResearch結果を確認する

Orchestrator Agentは、Research結果を確認します。

確認観点:

- ターゲットユーザーが具体的か
- 解決課題が機能ではなく困りごととして書かれているか
- 既存代替手段が整理されているか
- MVP検証仮説が開発につながる粒度になっているか
- リスクが明示されているか

### Step 5. Developer Agentに要件定義と開発計画を依頼する

Orchestrator Agentは、Research結果を渡し、Developer Agentに以下を依頼します。

- MVPの目的
- 主要機能
- 非機能要件
- 技術スタック
- データモデル案
- 実装ステップ
- 優先順位

### Step 6. Developer Agentが成果物を作成する

Developer Agentは、以下を作成します。

- `product-spec.md`
- `development-tasks.md`

MVPに必要な最小構成を優先し、不要な複雑化を避けます。

### Step 7. Orchestratorがfinal-report.mdを作成する

Orchestrator Agentは、Research AgentとDeveloper Agentの成果物を統合し、`final-report.md`を作成します。

最終レポートには以下を含めます。

- アイデア概要
- 想定ユーザーと課題
- 差別化ポイント
- MVP方針
- 主要機能
- 技術スタック
- 開発ステップ
- リスクと対応方針
- 次にやること

## 成果物

```text
outputs/<idea-name>/research-report.md
outputs/<idea-name>/product-spec.md
outputs/<idea-name>/development-tasks.md
outputs/<idea-name>/final-report.md
```

ユーザーが出力先を指定した場合は、その指定を優先します。

## Lite版の判断基準

- 初期検証に必要なものだけを作る
- 多機能化より、1つの強い課題解決を優先する
- 自動化やAI機能は、MVPの価値に直結する場合のみ含める
- Pro版向けの高度な分析、営業、財務、法務、デザイン詳細は深掘りしない
