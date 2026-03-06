# エージェント一覧

このワークスペースは、株式投資分析を**マルチエージェント・オーケストレーターパターン**で実行します。

## アーキテクチャ

```
ユーザ
  │
  ▼
stock-orchestrator（統括）
  │
  ├─ 1. macro-economist（マクロ経済分析）
  │
  ├─ 2. sector-analyst（セクター分析）
  │
  ├─ 3. stock-screener（銘柄スクリーニング）
  │
  ├─ 4. fundamental-analyst（ファンダメンタル分析）
  │
  ├─ 5. risk-manager（リスク評価）
  │
  └─ 6. portfolio-strategist（ポートフォリオ構築）
```

## エージェント詳細

| エージェント | ファイル | 役割 |
|-------------|---------|------|
| **stock-orchestrator** | `.github/agents/stock-orchestrator.agent.md` | 全体統括。6つの専門エージェントを順次呼び出し結果を統合する |
| **macro-economist** | `.github/agents/macro-economist.agent.md` | マクロ経済環境の分析（指数・金利・為替・イベント） |
| **sector-analyst** | `.github/agents/sector-analyst.agent.md` | 有望セクターの特定（ローテーション・テーマ分析） |
| **stock-screener** | `.github/agents/stock-screener.agent.md` | 定量スクリーニングによる候補銘柄選定 |
| **fundamental-analyst** | `.github/agents/fundamental-analyst.agent.md` | 個別銘柄の深掘り分析（財務・カタリスト・リスク） |
| **risk-manager** | `.github/agents/risk-manager.agent.md` | リスク評価・ポジションサイジング・損切りルール設定 |
| **portfolio-strategist** | `.github/agents/portfolio-strategist.agent.md` | 最終ポートフォリオ構築（コア・サテライト戦略） |

## 使い方

### フル分析

`stock-orchestrator` エージェントを選択して「おすすめの銘柄を教えて」「ポートフォリオを提案して」等のリクエストを入力してください。オーケストレーターが6つのエージェントを順次呼び出して統合結果を返します。

### 個別エージェントの直接利用

特定のフェーズだけ実行したい場合は、対応するエージェントを直接選択して利用できます:

- マクロ環境だけ確認したい → `macro-economist`
- 特定銘柄のリスクを評価したい → `risk-manager`
- 既に銘柄が決まっていて詳細分析したい → `fundamental-analyst`
