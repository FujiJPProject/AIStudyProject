# 第6段階：Fine-tuning

[前の段階](05_第5段階_Mini_GPT.md) ｜ [全体概要・目次](Readme.md) ｜ [次の段階](07_第7段階_ChatGPT型システム.md)

## この段階の位置づけ

| 項目                 | 内容                                |
| :------------------- | :---------------------------------- |
| 学習テーマ           | Fine-tuning                         |
| 最終的に理解するもの | 既存LLMを目的に合わせて調整する方法 |
| 学習項目数           | 28項目                              |

## 学習項目一覧

| 段階    | 学習テーマ  | 分野             | 項目                                  | 学習する理由                                                                               | 取得するべき内容                                                                                                                                                                  |
| :------ | :---------- | :--------------- | :------------------------------------ | :----------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 第6段階 | Fine-tuning | Fine-tuning      | SFT                                   | 教師ありデータを用いてBase Modelの振る舞いを目的に合わせる基本工程を理解するため           | Language Modeling・Prompt-Completion・会話形式の違いと、入力・正解・Loss対象の関係を説明できること                                                                                |
| 第6段階 | Fine-tuning | Fine-tuning      | Full Fine-tuning・PEFT                | 更新するParameterの範囲によって、必要な計算資源・表現力・成果物が変わるため                | 全Parameterを更新するFull Fine-tuningと、一部の追加Parameterを学習するPEFTの仕組み・長所・制約を比較し、目的と資源に応じて選択できること                                          |
| 第6段階 | Fine-tuning | ガバナンス       | Model・Dataset License                | ModelやDatasetを学習・再配布・商用利用できるか、作業開始前に判断するため                   | Model Card・Dataset Card・Licenseを確認し、利用目的、派生成果物、再配布、表示義務などの条件を記録できること                                                                       |
| 第6段階 | Fine-tuning | ガバナンス       | 個人情報・機密情報・安全性            | 学習データへの不適切な情報の混入と、調整後Modelによる有害な出力を防ぐため                  | 個人・機密情報と有害データを検査・除去し、想定用途、公開範囲、安全性評価を定められること                                                                                          |
| 第6段階 | Fine-tuning | Hugging Face     | transformers                          | 既存のModelとTokenizerを同じInterfaceで読み込み、Fine-tuningの土台を作るため               | 対象Modelに対応するClass、Tokenizer、Config、Model Revisionを確認し、読み込み・推論できること                                                                                     |
| 第6段階 | Fine-tuning | Hugging Face     | datasets                              | 学習データを再現可能な処理手順で読み込み、変換するため                                     | Datasetの読み込み、選択、分割、map・filterによる加工、保存ができること                                                                                                            |
| 第6段階 | Fine-tuning | データセット設計 | Data Cleaning・Deduplication          | 不正・低品質・重複データによる誤学習、偏り、評価汚染を抑えるため                           | 欠損、文字化け、異常値、低品質例を検査し、完全一致・近似重複を検出して除去できること                                                                                              |
| 第6段階 | Fine-tuning | データセット設計 | Dataset Balance                       | 特定のTask・分野・応答形式への過度な偏りを抑えるため                                       | Datasetの分布と構成比を可視化し、SamplingやWeightingによって調整できること                                                                                                        |
| 第6段階 | Fine-tuning | データセット設計 | Train・Validation・Test分割と汚染防止 | 学習、Hyperparameter調整、最終評価を分離し、未知データへの性能を測るため                   | 同一・類似例や同一会話を分割間に跨がせず、Benchmark・Testとの重複を検査できること                                                                                                 |
| 第6段階 | Fine-tuning | データセット設計 | Formatting                            | 元データをSFTの学習目的に合う一定のSchemaへ変換するため                                    | Language Modeling・Prompt-Completion・会話形式を区別し、text、prompt・completion、messagesなどのSchemaへ変換できること                                                            |
| 第6段階 | Fine-tuning | データセット設計 | Chat Template                         | 会話のroleと内容を、対象Modelが学習時に想定したToken列へ変換するため                       | TokenizerのChat TemplateとSpecial Tokenを確認し、重複Tokenを避けて会話データへ適用できること                                                                                      |
| 第6段階 | Fine-tuning | データセット設計 | Truncation・Packing                   | Context Lengthを超える例を安全に処理し、短い例による計算の浪費を減らすため                 | 最大系列長、切り詰め位置、EOS境界、Padding、複数例のPackingを設計できること                                                                                                       |
| 第6段階 | Fine-tuning | 損失設計         | Label Masking・Completion Loss        | Promptを含む全Tokenと、Completion・Assistant部分だけのどちらを学習対象にするか制御するため | 対象外Labelをignore indexへ置き換え、Dataset形式と目的に応じてLoss対象Tokenを設定・確認できること                                                                                 |
| 第6段階 | Fine-tuning | 資源計画         | VRAM・学習可能Parameter数の見積り     | Hardware上で実行可能なModel、学習方式、Batch Sizeを学習開始前に選ぶため                    | Model Weight、学習可能Parameter、Gradient、Optimizer State、ActivationのMemoryを概算し、Full・LoRA・QLoRAを比較できること                                                         |
| 第6段階 | Fine-tuning | LoRA             | Low-Rank Adaptation                   | Base Weightを凍結し、少数の追加Parameterだけで効率よく適応させる仕組みを理解するため       | 低Rank行列による更新の表現、学習可能Parameterが減る理由、Full Fine-tuningとの違いを説明できること                                                                                 |
| 第6段階 | Fine-tuning | LoRA             | Rank・Alpha・Target Module            | LoRAの容量、更新のScale、適用範囲を相互に関連する基本設定として選ぶため                    | RankとAlphaの関係を説明し、Model Architectureの層名を確認してAttention射影やLinear層からTarget Moduleを選択できること                                                             |
| 第6段階 | Fine-tuning | LoRA             | LoRA Dropout・modules_to_save         | Adapterを正則化し、LoRA対象外でも追加学習・保存が必要な層を扱うため                        | LoRA Dropoutを設定し、必要に応じてEmbeddingや出力Headなどをmodules_to_saveへ指定できること                                                                                        |
| 第6段階 | Fine-tuning | 量子化           | 8bit Quantization                     | WeightやOptimizer StateのMemoryを削減する選択肢と、その用途の違いを理解するため            | 8bit Weight量子化、8bit Optimizer、推論、PEFT学習を区別し、量子化Base Weightの学習上の制約を説明できること                                                                        |
| 第6段階 | Fine-tuning | 量子化           | 4bit Quantization                     | より少ないVRAMで大規模なBase Modelを読み込み、QLoRAへ進むため                              | NF4・FP4、Compute dtype、Double Quantization、品質とHardwareの制約を区別して4bit量子化を設定できること                                                                            |
| 第6段階 | Fine-tuning | QLoRA            | QLoRA                                 | 4bit量子化したBase ModelとLoRAを組み合わせ、限られたVRAMでFine-tuningするため              | 凍結した4bit Base Modelを通して勾配を伝え、LoRA Adapterだけを更新する構造を説明・実装できること                                                                                   |
| 第6段階 | Fine-tuning | 学習設定         | Learning Rate・Batch・Epoch・Warmup   | 学習の安定性、収束、過学習を左右する主要Hyperparameterを一体として設計するため             | 実効Batch SizeとGradient Accumulation、学習率、Epoch、Warmup、Schedulerの関係を説明し、初期値と探索範囲を決められること                                                           |
| 第6段階 | Fine-tuning | 学習効率化       | Mixed Precision                       | 数値表現を使い分けて計算速度とVRAM効率を改善しつつ、数値不安定性を避けるため               | Hardware対応を確認し、fp32・fp16・bf16の精度範囲と安定性を比較して設定できること                                                                                                  |
| 第6段階 | Fine-tuning | 学習効率化       | Gradient Checkpointing                | Activationの一部を再計算する代わりに、学習時のVRAM使用量を削減するため                     | Memory削減と計算時間増加のTrade-offを説明し、Modelと学習設定で有効化できること                                                                                                    |
| 第6段階 | Fine-tuning | Hugging Face     | Trainer・TRL SFTTrainer               | 設計済みのDataset、Loss、PEFT、学習設定を一つの学習Loopへ統合するため                      | Trainer・TrainingArguments・Data Collator・Callbackの役割を理解し、SFT固有のChat Template、Packing、Completion Loss、PEFT連携が必要な場合にSFTTrainerを選んで学習・評価できること |
| 第6段階 | Fine-tuning | LoRA             | Adapter保存・読込・Merge              | 学習成果を小さなAdapterとして管理し、再利用や推論用成果物へ変換するため                    | Adapterを保存・読み込みし、対応するBase ModelとRevisionを記録し、必要に応じてMerge・Unmergeできること                                                                             |
| 第6段階 | Fine-tuning | 実験管理         | Checkpoint・実験追跡・再現性          | 学習を再開し、複数条件を公平に比較して採用Modelの由来を追跡するため                        | Config、Seed、Code・Dataset・ModelのVersion、Metric、Log、Checkpointを一体で保存し、実験を再現できること                                                                          |
| 第6段階 | Fine-tuning | 評価             | Base Modelとの比較評価                | Fine-tuningが目的性能を改善し、既存能力や安全性を過度に損なっていないか判断するため        | 同一のPrompt、生成設定、評価Datasetを用いてBase ModelとFine-tuned Modelを比較し、目的指標と副作用を評価できること                                                                 |
| 第6段階 | Fine-tuning | 評価             | Overfitting・Catastrophic Forgetting  | 少量Datasetの暗記や、Base Modelが持つ一般能力の低下を検出・抑制するため                    | Train・Validationの差、重複を除いた生成例、目的外Task・一般Benchmarkを用いて過学習と破壊的忘却を評価し、Data・正則化・学習量を調整できること                                      |

## 到達目標

既存のLLMを目的に合わせて調整できることを目標とする。

```text
Base Model
↓
Instruction Dataset
↓
SFT
↓
LoRA / QLoRA
↓
Fine-tuned Model
↓
Evaluation
```

特に、

- Full Fine-tuning
- LoRA
- QLoRA
- SFT

の違いを説明し、目的に応じて使い分けられる状態を目指す。

---

[前の段階](05_第5段階_Mini_GPT.md) ｜ [全体概要・目次](Readme.md) ｜ [次の段階](07_第7段階_ChatGPT型システム.md)
