# ChatGPT・LLM開発を理解するための学習ロードマップ（全体概要・目次）

## 1. 最終的な目的

本ロードマップの最終的な目的は、ChatGPTのような大規模言語モデル（LLM）について、単に利用方法を知るだけではなく、**数学的な基礎からニューラルネットワーク、Transformer、GPT、Fine-tuning、ChatGPT型アプリケーション、LLMそのものの学習工程までを一連の仕組みとして理解できる状態になること**である。

最終的には、以下の流れをそれぞれ説明できることを目標とする。

```text
ユーザー
↓
ChatGPT型アプリケーション
↓
Prompt / Context / Memory
↓
RAG / Tool Calling / Agent
↓
LLM推論
↓
Fine-tuning済みLLM
↓
SFT / DPO / RLHF
↓
Pretraining
↓
GPT / Transformer
↓
Attention
↓
Neural Network
↓
行列・微分・確率
```

そのため、本ロードマップでは次の3つを最終到達目標とする。

### 1.1 理論を説明できる

以下について、それぞれの技術が「何をしているのか」「なぜ必要なのか」を説明できる。

- 機械学習
- Neural Network
- Backpropagation
- Transformer
- Attention
- GPT
- Tokenization
- Pretraining
- Fine-tuning
- SFT
- LoRA / QLoRA
- RAG
- Tool Calling
- AI Agent
- DPO
- RLHF
- LLM Evaluation
- 分散学習

### 1.2 小規模なモデルを自分で実装できる

ライブラリを利用するだけではなく、小規模な範囲で以下を実装できることを目標とする。

```text
データセット準備
↓
Tokenizer
↓
Embedding
↓
Self-Attention
↓
Transformer
↓
Mini GPT
↓
Pretraining
↓
文章生成
```

さらに既存のオープンLLMに対して、

```text
Base Model
↓
SFT
↓
LoRA / QLoRA
↓
評価
↓
独自用途向けLLM
```

という一連のFine-tuningを実施できる状態を目指す。

### 1.3 ChatGPT型システムを構築できる

最終的にはLLM単体ではなく、

```text
Web UI
↓
Backend API
↓
Prompt / Context
↓
RAG
↓
Memory
↓
Tool Calling
↓
Agent
↓
LLM
↓
Evaluation
↓
Security
```

まで含めた実用的なAIシステムを設計・構築できる状態を目標とする。

---

## 2. 学習段階の全体像

| 段階     | 学習テーマ                               | 最終的に理解するもの                        |
| :------- | :--------------------------------------- | :------------------------------------------ |
| 第1段階  | 最終段階までに必要な数学・プログラミング | AI・LLMを理解するために必要な数学と実装基礎 |
| 第2段階  | 機械学習基礎                             | AIが「学習する」とは何か                    |
| 第3段階  | Neural Network                           | Deep Learningがどのように学習するか         |
| 第4段階  | Transformer                              | LLMの中核となる構造                         |
| 第5段階  | Mini GPT                                 | GPTが文章を生成する仕組み                   |
| 第6段階  | Fine-tuning                              | 既存LLMを目的に合わせて調整する方法         |
| 第7段階  | ChatGPT型システム                        | LLMを実用的なAIサービスにする方法           |
| 最終段階 | Pretraining / SFT / DPO / RLHF           | LLMそのものを育てる一連の工程               |

---

## 段階別ファイル

| 順序 | 段階                                                                | 学習テーマ                               | 最終的に理解するもの                        | 学習項目数 |
| :--- | :------------------------------------------------------------------ | :--------------------------------------- | :------------------------------------------ | ---------: |
| 01   | [第1段階：数学・プログラミング](01_第1段階_数学・プログラミング.md) | 最終段階までに必要な数学・プログラミング | AI・LLMを理解するために必要な数学と実装基礎 |         46 |
| 02   | [第2段階：機械学習基礎](02_第2段階_機械学習基礎.md)                 | 機械学習基礎                             | AIが「学習する」とは何か                    |         36 |
| 03   | [第3段階：Neural Network](03_第3段階_Neural_Network.md)             | Neural Network                           | Deep Learningがどのように学習するか         |         34 |
| 04   | [第4段階：Transformer](04_第4段階_Transformer.md)                   | Transformer                              | LLMの中核となる構造                         |         30 |
| 05   | [第5段階：Mini GPT](05_第5段階_Mini_GPT.md)                         | Mini GPT                                 | GPTが文章を生成する仕組み                   |         26 |
| 06   | [第6段階：Fine-tuning](06_第6段階_Fine-tuning.md)                   | Fine-tuning                              | 既存LLMを目的に合わせて調整する方法         |         31 |
| 07   | [第7段階：ChatGPT型システム](07_第7段階_ChatGPT型システム.md)       | ChatGPT型システム                        | LLMを実用的なAIサービスにする方法           |         61 |
| 08   | [最終段階：LLM Training](08_最終段階_LLM_Training.md)               | Pretraining / SFT / DPO / RLHF           | LLMそのものを育てる一連の工程               |         73 |

## 5. 学習によって最終的に理解する全体構造

すべての段階を修了した場合、以下の関係を一続きの仕組みとして説明できる状態を目指す。

```text
【数学】

線形代数
微分
確率
↓
────────────────────

【Deep Learning】

Neural Network
↓
Backpropagation
↓
Optimization
↓
────────────────────

【LLMの構造】

Tokenization
↓
Embedding
↓
Attention
↓
Transformer
↓
GPT
↓
────────────────────

【LLMの基本学習】

Dataset
↓
Pretraining
↓
Base Model
↓
────────────────────

【指示応答能力の付与】

SFT
↓
Preference Learning
↓
DPO / RLHF
↓
Chat Model
↓
────────────────────

【実用システム】

Prompt
↓
Context
↓
RAG
↓
Memory
↓
Tool Calling
↓
Agent
↓
LLM Serving
↓
Evaluation
↓
Security
↓
────────────────────

【ユーザー】

ChatGPT型サービス
```

---

## 6. 個人学習における到達点

本ロードマップのすべてを個人で学習することは可能だが、実際に扱える規模には違いがある。

### 個人でも実践可能な領域

以下は個人PC、クラウドGPU、小規模なGPU環境などで十分経験できる。

- Python
- 数学
- 機械学習
- Neural Network
- Transformer
- Mini GPT
- Tokenizer Training
- 小規模Pretraining
- SFT
- LoRA
- QLoRA
- DPO
- 小規模なRLHF実験
- RAG
- Tool Calling
- Agent
- ChatGPT型Webサービス
- LLM Evaluation
- Quantization
- LLM Serving

### 小規模実験は可能だが大規模実践が難しい領域

- 大規模Pretraining
- 大規模RLHF
- 数十億〜数千億パラメータ規模の学習
- 数百〜数千GPUを使った分散学習
- 超大規模Dataset Pipeline
- フロンティアモデル規模のScaling実験

したがって、最終段階では、

> **小規模モデルでは実際に再現し、大規模LLMについては同じ原理がどのように拡張されるのかを理解する**

ことを現実的な到達目標とする。

---

## 7. 最終到達状態

このロードマップを完了した際の最終的な到達状態は、以下である。

### 理論

ChatGPT型AIについて、

> 「なぜ文章を生成できるのか」

を数学・ニューラルネットワーク・Transformer・GPTのレベルから説明できる。

### モデル開発

小規模なGPTについて、

```text
Tokenizer
↓
Transformer
↓
Pretraining
↓
SFT
↓
DPO
↓
Chat Model
```

を実際に構築できる。

### LLM活用

既存のオープンLLMについて、

```text
Base Model
↓
LoRA / QLoRA
↓
Fine-tuning
↓
Evaluation
```

を行える。

### AIアプリケーション開発

以下を組み合わせたChatGPT型AIサービスを構築できる。

- LLM
- Prompt
- RAG
- Memory
- Tool Calling
- Agent
- Backend
- Database
- Evaluation
- Security

### LLM研究・開発の理解

フロンティアLLMについて、

```text
Dataset
↓
Pretraining
↓
Scaling
↓
SFT
↓
Preference Learning
↓
DPO / RLHF
↓
Evaluation
↓
Inference
```

という開発工程全体を理解し、各工程で何が行われているかを技術的に説明できる。

---

## 8. 本ロードマップの最終ゴール

最終的には、

> **「ChatGPTを使える人」ではなく、「ChatGPTのようなAIがどのような理論・モデル・学習・システムによって成立しているのかを理解し、小規模な範囲では自分で再現・実装できる人」**

になることを本ロードマップのゴールとする。
