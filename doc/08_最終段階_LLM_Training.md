# 最終段階：LLM Training

[前の段階](07_第7段階_ChatGPT型システム.md) ｜ [全体概要・目次](Readme.md)

## この段階の位置づけ

| 項目                 | 内容                           |
| :------------------- | :----------------------------- |
| 学習テーマ           | Pretraining / SFT / DPO / RLHF |
| 最終的に理解するもの | LLMそのものを育てる一連の工程  |
| 学習項目数           | 67項目                         |

## 学習項目一覧

| 段階     | 学習テーマ   | 分野                | 項目                                            | 学習する理由                                                                            | 取得するべき内容                                                                                                                                      |
| :------- | :----------- | :------------------ | :---------------------------------------------- | :-------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------- |
| 最終段階 | LLM Training | データガバナンス    | Data Provenance・License                        | 学習Dataの出所と利用根拠を収集前から追跡し、学習・公開の可否を判断するため              | Source、取得時点、License、利用条件、変換履歴、再配布条件をDataset単位で記録できること                                                                |
| 最終段階 | LLM Training | データガバナンス    | Privacy・Consent・Deletion                      | 個人・機密情報を適切に扱い、同意撤回や除外要求を学習工程へ反映するため                  | PII検出・最小化、Consent、Retention、除外List、削除要求と派生Datasetへの伝播を設計できること                                                          |
| 最終段階 | LLM Training | データ処理          | Corpus・Web Corpus                              | LLMの知識源となる大規模Dataを、目的に合う構成と統制の下で収集するため                   | Web・Code・書籍などのSource構成を決め、取得許可、Robots、Snapshot、Malware・Spam対策を含むCorpus収集を設計できること                                  |
| 最終段階 | LLM Training | データ処理          | Document Parsing                                | HTML、PDF、Codeなどの原文から、文書構造を保ったTextとMetadataを抽出するため             | 本文、見出し、表、Code、文書境界を抽出し、Boilerplateや解析失敗を検出できること                                                                       |
| 最終段階 | LLM Training | データ処理          | Text Normalization                              | 表記揺れやEncoding上のNoiseを整え、後続の重複判定とTokenizationを安定させるため         | Encoding、Unicode、空白、制御文字の正規化規則を定め、意味を壊していないか検証できること                                                               |
| 最終段階 | LLM Training | データ処理          | Language Detection                              | 多言語Corpusを言語別に把握し、FilterとData Mixtureへ利用するため                        | 文書・区間単位で言語と信頼度を推定し、短文・混在言語・Codeでの誤判定を評価できること                                                                  |
| 最終段階 | LLM Training | データ処理          | Filtering                                       | 低品質・有害・不正なDataを減らし、Corpusの学習効率と安全性を高めるため                  | Rule、Classifier、Heuristicを組み合わせ、品質・安全性・Bias・誤除外のTrade-offを評価できること                                                        |
| 最終段階 | LLM Training | データ処理          | Deduplication                                   | 重複による学習比率の偏り、暗記、評価汚染を抑えるため                                    | 文書・段落・近似一致の重複を大規模に検出し、Source優先度と除去単位を決められること                                                                    |
| 最終段階 | LLM Training | データ処理          | Benchmark Contamination                         | 評価Dataの学習混入による過大評価を防ぐため                                              | BenchmarkのPrompt・回答とCorpusの完全一致・近似一致を検査し、除外規則と検査時点を記録できること                                                       |
| 最終段階 | LLM Training | データ処理          | Data Quality Audit・Sampling                    | 自動処理後のData分布、残存Noise、誤除外を人手と統計で確認するため                       | Source・言語・分野別の層化Sample、人手Rubric、False Positive・Negativeを用いて品質を監査できること                                                    |
| 最終段階 | LLM Training | データ処理          | Data Mixture                                    | 言語、分野、品質、Sourceごとの学習比率を目的に合わせて制御するため                      | 有効Token数、Sampling Weight、Temperature Sampling、Epoch数を考慮してMixtureを設計できること                                                          |
| 最終段階 | LLM Training | Tokenizer           | Vocabulary設計                                  | 対象言語・Domainを効率よく表現し、ModelのVocabulary Sizeと計算量を決めるため            | BPE・Unigramなどの方式、Vocabulary Size、Byte Fallback、Special Token、正規化規則を選べること                                                         |
| 最終段階 | LLM Training | Pretraining         | Tokenizer Training                              | 設計したCorpusとVocabulary条件からModel専用Tokenizerを作成するため                      | 代表性のあるSampleを用いてTokenizerを学習し、Vocabulary、Merge Rule、Special Token設定を再現可能に保存できること                                      |
| 最終段階 | LLM Training | Tokenizer           | Tokenizer評価                                   | 学習したTokenizerが対象言語・Domainを適切な粒度で表現できるか確認するため               | Fertility、圧縮率、未知文字、Byte Fallback、数字・Code、多言語、往復変換をCorpus別に評価できること                                                    |
| 最終段階 | LLM Training | Pretraining         | Next Token Prediction                           | 入力Token列から次Tokenを予測する事前学習目的を理解するため                              | ShiftしたInput・Label、Causal Mask、Cross Entropy、Padding除外を説明し、小規模Modelで実装できること                                                   |
| 最終段階 | LLM Training | Pretraining         | Model Architecture・Configuration               | 学習対象Modelの容量、安定性、計算量、成果物互換性を定義するため                         | Layer数、Hidden Size、Attention Head、FFN、位置表現、Norm、Vocabularyを一貫したConfigとして設計できること                                             |
| 最終段階 | LLM Training | Scaling             | Model Size・Data Size・Compute                  | Parameter数、Training Token数、計算量を同じ予算問題として捉えるため                     | Model Size、Data品質・重複・Epoch、FLOPs、時間、Hardware効率、Costの相互関係を説明できること                                                          |
| 最終段階 | LLM Training | Scaling             | Scaling Laws・Compute-optimal Design            | 限られたComputeをModelとDataへ効率よく配分するため                                      | 複数規模のLoss傾向からParameter数・Token数・FLOPsの候補を比較し、外挿の仮定と不確実性を説明できること                                                 |
| 最終段階 | LLM Training | Scaling             | Mixture of Experts                              | Tokenごとに一部のExpertだけを使い、計算量を抑えながらModel容量を拡張するため            | Router、Top-k Expert、Load Balance Loss、Capacity、Expert利用率、Dense Modelとの推論Cost差を説明できること                                            |
| 最終段階 | LLM Training | Pretraining         | Optimizer・Learning Rate Schedule               | 大規模学習の更新則とStepごとの更新量を一体として設計するため                            | Optimizer、Beta、Epsilon、Warmup、Peak Learning Rate、Decay、Training Token数との関係を設定できること                                                 |
| 最終段階 | LLM Training | Pretraining         | Regularization・Gradient Clipping               | 過学習と勾配爆発を抑え、安定した更新を維持するため                                      | Weight Decay、Dropout、Gradient Normを監視し、適切なClip閾値と正則化強度を選べること                                                                  |
| 最終段階 | LLM Training | 分散学習            | Gradient Accumulation                           | Micro Batchを複数回蓄積し、Memoryを抑えて大きな実効Batchを作るため                      | Micro Batch、Accumulation Step、Data Parallel数から実効Batch Sizeを計算し、Loss Scalingと同期頻度を設定できること                                     |
| 最終段階 | LLM Training | 分散学習            | Mixed Precision                                 | 数値安定性を保ちながらMemory使用量と学習時間を削減するため                              | FP32・FP16・BF16・FP8、Accumulation精度、Master Weight、Loss Scaling、Hardware対応を区別して設計できること                                            |
| 最終段階 | LLM Training | 分散学習            | Activation Checkpointing                        | 保存するActivationを減らし、再計算と引き換えに長系列・大Batchを扱うため                 | CheckpointするLayer粒度を選び、Memory削減量、追加Compute、乱数状態への影響を測定できること                                                            |
| 最終段階 | LLM Training | Pretraining         | Validation Loss・Perplexity                     | 未知Dataへの予測性能、過学習、Domain間の偏りを学習中に追跡するため                      | 固定Validation SetでToken-weighted Lossを算出し、Perplexity、Domain別差、Tokenizer差による比較限界を説明できること                                    |
| 最終段階 | LLM Training | Pretraining         | Checkpoint                                      | 長時間の学習を中断から再開し、後続の評価・Post-trainingへ成果物を渡すため               | Model、Optimizer、Scheduler、Scaler、RNG、Data位置を整合した状態でAtomicに保存し、同条件で再開できること                                              |
| 最終段階 | LLM Training | 分散学習            | Collective Communication・Interconnect          | 分散学習で発生する通信とCluster Topologyの制約を理解するため                            | All-reduce、All-gather、Reduce-scatter、All-to-all、Point-to-pointをBandwidth、Latency、Node境界と対応付けられること                                  |
| 最終段階 | LLM Training | 分散学習            | Data Parallelism                                | Model Replicaへ異なるDataを与え、勾配を同期してThroughputを高めるため                   | Replica、Distributed Sampler、Gradient同期、Global Batch Size、同期箇所を説明できること                                                               |
| 最終段階 | LLM Training | 分散学習            | FSDP・ZeRO                                      | Parameter、Gradient、Optimizer StateのSharding方式を比較してMemoryを削減するため        | FSDPのSharding StrategyとZeROのStageを、保持するModel State、通信、Offload、Checkpointの観点で比較できること                                          |
| 最終段階 | LLM Training | 分散学習            | Tensor Parallelism                              | 一つのLayer内の行列演算をDevice間へ分割し、単一Deviceに載らないModelを学習するため      | Column・Row方向の分割、Collective通信、Attention・FFNへの適用を説明できること                                                                         |
| 最終段階 | LLM Training | 分散学習            | Pipeline Parallelism                            | 連続するLayer群をStageとしてDeviceへ配置し、Modelを分割するため                         | Micro Batch、Pipeline Schedule、Bubble、Stage間通信、Load Balanceの利点と欠点を説明できること                                                         |
| 最終段階 | LLM Training | 分散学習            | Sequence・Context Parallelism                   | 長い系列のActivationとAttention計算をSequence軸でDevice間へ分割するため                 | Sequence軸の分割、通信、Causal Mask、Position、他Parallelismとの組合せを説明できること                                                                |
| 最終段階 | LLM Training | 分散学習            | Expert Parallelism                              | MoEのExpertをDevice間へ配置し、選択されたTokenを担当Expertへ送るため                    | Token Dispatch、All-to-all、Load Imbalance、Capacity Overflowを測定・対策できること                                                                   |
| 最終段階 | LLM Training | 分散学習            | Parallelism Composition・Topology Mapping       | 各並列方式をModelとClusterの構造に合わせて組み合わせるため                              | Data、Tensor、Pipeline、Sequence、Expert軸のProcess Gridを設計し、高速Link内外へ通信量に応じて配置できること                                          |
| 最終段階 | LLM Training | Pretraining         | Data Pipeline                                   | 処理済みの巨大Corpusを複数Workerへ重複なく継続供給するため                              | Streaming、Shard、決定的Shuffle、Packing、Worker間分配、Prefetch、再開位置を含む分散Data Pipelineを設計できること                                     |
| 最終段階 | LLM Training | 分散学習            | Profiler・MFU・Throughput                       | 計算、通信、Data供給のBottleneckを測り、同じCostで処理できるToken数を増やすため         | Tokens毎秒、Step時間、MFU、通信待ち、Data待ち、Kernel時間をProfileし、改善前後を比較できること                                                        |
| 最終段階 | LLM Training | Pretraining         | Curriculum・Sequence Length Schedule            | 学習初期の難易度とCostを抑え、分野・難易度・系列長を段階的に変えるため                  | Data難易度、Domain、Sequence LengthのScheduleを設計し、分布変化と最終性能への影響を評価できること                                                     |
| 最終段階 | LLM Training | 分散学習            | Fault Tolerance・Elastic Resume                 | Node障害やPreemptionから分散Runを再現可能に復旧するため                                 | 障害検知、分散Checkpoint、Rank再構成、Data位置復元、再試行上限、復旧Testを設計できること                                                              |
| 最終段階 | LLM Training | Pretraining         | Training Stability・Loss Spike                  | 高CostなRunの発散や性能異常を早期検知し、原因を切り分けるため                           | Loss、Gradient Norm、Activation、NaN・Inf、Throughputを監視し、Data・数値精度・Optimizer・通信・障害復旧の異常を診断できること                        |
| 最終段階 | LLM Training | Scaling             | Pilot Run・Scaling Extrapolation                | 本番Run前に全構成を小規模で検証し、性能・予算・障害率を外挿するため                     | 小規模RunからLoss、Memory、Throughput、通信、Data供給、Failure率を測り、本番規模の候補を比較できること                                                |
| 最終段階 | LLM Training | SFT                 | Instruction Dataset                             | Base Modelへ指示追従と望ましい応答形式を学習させるため                                  | Task、指示、入力、応答、拒否例の構成と品質基準を定め、Train・Validationを分離できること                                                               |
| 最終段階 | LLM Training | SFT                 | Chat Template                                   | 会話のRoleとSpecial TokenをModelが想定するToken列へ変換するため                         | System・User・AssistantのMessageをTemplateへ適用し、BOS・EOSなどの重複を避けられること                                                                |
| 最終段階 | LLM Training | SFT                 | Loss Masking                                    | 会話中のどのTokenを正解として学習するか制御するため                                     | System・User Tokenをignore indexへ置き換え、Assistant応答だけ、または全TokenのLossを目的に応じて設定・確認できること                                  |
| 最終段階 | LLM Training | SFT                 | Packing                                         | 短い学習例を一つのSequenceへ詰め、Paddingと計算の浪費を減らすため                       | 複数例をEOSで分離し、Attention・Position・Label境界を壊さずにPackingできること                                                                        |
| 最終段階 | LLM Training | Preference Learning | Chosen・Rejected・Preference Annotation Quality | 同じPromptへの回答間の好みを、一貫した基準で学習Dataへ変換するため                      | Chosen・Rejected Pair、Rubric、Tie、Annotator一致度、Noise、位置・長さBias、品質監査を設計できること                                                  |
| 最終段階 | LLM Training | Preference Learning | Reward Signal                                   | 望ましい応答・行動を学習Algorithmへ伝えるFeedbackの種類を理解するため                   | 相対Preference、Reward Model Score、Rule、Verifier、人手評価を区別し、目的に合うSignalを選べること                                                    |
| 最終段階 | LLM Training | Post-training       | Rejection Sampling・Best-of-N                   | 複数候補から高品質応答を選び、推論結果や追加学習Dataを改善するため                      | 候補生成、Score、重複除去、Selection Bias、推論Cost、SFTへの再利用を設計できること                                                                    |
| 最終段階 | LLM Training | Preference Learning | RLAIF・AI Feedback                              | 人手Feedbackを補助し、Preference Dataと評価を拡張するため                               | AI Judge、Rubric、Constitution、Calibration、人手監査、Model間の相関、Bias自己増幅Riskを説明できること                                                |
| 最終段階 | LLM Training | Post-training       | Online RL・Offline Preference Optimization      | Policyが生成する新Dataで学ぶ方式と、固定Preference Dataで学ぶ方式を選ぶため             | On-policy・Off-policy、探索、分布Shift、安定性、Cost、Reward Model要否を比較できること                                                                |
| 最終段階 | LLM Training | RLHF                | Reinforcement Learning・Policy                  | LLM生成を逐次意思決定として捉え、Rewardで最適化する基礎を理解するため                   | State、Action、Trajectory、Reward、PolicyをToken生成へ対応付け、SFTとの違いを説明できること                                                           |
| 最終段階 | LLM Training | RLHF                | Reward Model                                    | 人間のPreferenceから、Promptと応答に対するScalar Rewardを学習するため                   | Pairwise PreferenceからReward Modelを学習し、Validation、Calibration、分布Shiftを評価できること                                                       |
| 最終段階 | LLM Training | Reward Design       | Process Reward・Outcome Reward                  | 途中の推論Stepと最終結果のどちらへFeedbackを与えるか設計するため                        | Step単位と最終回答のReward、Credit Assignment、Verifier信頼性、Annotation Costを比較できること                                                        |
| 最終段階 | LLM Training | DPO                 | Reference Model・Preference Optimization        | 固定Preference Pairから、望ましい回答の相対確率を直接高めるDPOを理解するため            | PolicyとReference Modelの対数確率比、Beta、Preference Loss、Offline Data、長さBiasを説明し、明示的Reward ModelやOn-policy生成を省く点を比較できること |
| 最終段階 | LLM Training | RLHF                | PPO・KL Penalty                                 | On-policy生成のRewardを用いてPolicyを更新しつつ、元Modelからの過度な逸脱を抑えるため    | Policy・Value Model、Advantage、Clipping、KL Penalty、Rollout、更新Batchの関係を説明できること                                                        |
| 最終段階 | LLM Training | RLHF                | GRPO                                            | Value Modelを使わず、同一Promptの回答Group内で相対Advantageを求めてPolicyを更新するため | Group Sampling、相対Advantage、Clipping、KL、Verifier Reward、Zero-variance Groupを説明し、PPOとCost・安定性を比較できること                          |
| 最終段階 | LLM Training | Reward Design       | Reward Hacking・Specification Gaming            | ModelがProxy Rewardの抜け道だけを学ぶ望ましくない最適化を検出するため                   | Reward上昇と人手品質の乖離、Length・Format Hack、Evaluator Exploit、分布外挙動を独立評価で監視・対策できること                                        |
| 最終段階 | LLM Training | Evaluation          | Knowledge・Reasoning・Math・Coding Evaluation   | Modelの主要能力を同じ評価設計の下で分野別に比較するため                                 | 知識、推論、数学、CodeのBenchmarkを選び、Metric、Prompt形式、実行環境、Data汚染を統制して評価できること                                               |
| 最終段階 | LLM Training | Evaluation          | Instruction Following                           | 指示の内容・形式・制約へどの程度従えるか評価するため                                    | 単一・複数制約、競合する指示、拒否すべき指示を含む評価Setと採点基準を設計できること                                                                   |
| 最終段階 | LLM Training | Evaluation          | Multilingual Evaluation                         | 言語ごとの能力差と安全性の不均衡を把握するため                                          | 高資源・低資源言語、翻訳依存、文化差、Tokenizer効率を分け、言語別Scoreを評価できること                                                                |
| 最終段階 | LLM Training | Evaluation          | Long-context Evaluation                         | 長い入力での検索、保持、複数根拠の統合能力とCostを測るため                              | 情報位置、入力長、Distractor、複数根拠、長文生成、Latency・Memoryを変えて評価できること                                                               |
| 最終段階 | LLM Training | Evaluation          | Safety Evaluation                               | 危険・違法・有害な要求への応答と、過剰拒否を評価するため                                | Threat Modelに基づくSafety評価Setを作り、Attack Success、適切な拒否、有用性低下を測定できること                                                       |
| 最終段階 | LLM Training | Evaluation          | Robustness                                      | 表記・順序・長さなどの入力変化や分布Shiftに対する安定性を確認するため                   | Paraphrase、Typo、難読化、Noise、Prompt順序、分布外Dataを用いて性能変動を評価できること                                                               |
| 最終段階 | LLM Training | Evaluation          | Calibration・Uncertainty・Abstention            | Modelの確信度と誤りRiskを、回答・棄権の判断へつなげるため                               | Confidenceと正答率、Calibration Error、選択的回答、Threshold、棄権時のRisk・Coverageを評価できること                                                  |
| 最終段階 | LLM Training | Evaluation          | Memorization・Privacy Extraction                | 学習Dataの再現と個人・機密情報の抽出Riskを学習後に測るため                              | Canary、Membership Inference、Prompt Extraction、完全・近似一致を用い、Data削除と公開判断へ接続できること                                             |
| 最終段階 | LLM Training | Evaluation          | Statistical Significance・Reproducible Harness  | 小さなScore差を偶然や評価実装差と区別するため                                           | Seed、Prompt、Sampling、Metric・Dataset版、実行環境を固定し、信頼区間、複数Run、Paired比較を実行できること                                            |
| 最終段階 | LLM Training | ガバナンス          | Data・Model Lineage                             | Corpusから公開Modelまでの由来を追跡し、再現・監査・Rollbackを可能にするため             | Dataset版、Code Commit、Tokenizer、Config、Checkpoint、SFT・Preference・RL手順、評価結果を一貫したLineageとして記録できること                         |
| 最終段階 | LLM Training | ガバナンス          | Model Card                                      | Modelの用途、評価結果、制約、Risk、公開条件を利用者へ伝えるため                         | 概要、Training Dataの範囲、意図した用途、禁止用途、Metric、既知の限界、Safety・Privacy上の注意を文書化できること                                      |

## 到達目標

LLMをゼロから育てる全工程を理解する。

```text
大量のテキストデータ
↓
データ処理
↓
Tokenizer Training
↓
Pretraining
↓
Base Model
↓
SFT
↓
Instruction Model
↓
Preference Dataset
↓
DPO / RLHF
↓
Chat Model
↓
Evaluation
↓
Deployment
```

小規模なモデルについては、実際にこれらの工程を再現できることを目標とする。

---

[前の段階](07_第7段階_ChatGPT型システム.md) ｜ [全体概要・目次](Readme.md)
