# 最終段階：LLM Training

[前の段階](07_第7段階_ChatGPT型システム.md) ｜ [全体概要・目次](00_全体概要・目次.md) ｜ [全体概要・目次](00_全体概要・目次.md)

## この段階の位置づけ

|項目|内容|
|:--|:--|
|学習テーマ|Pretraining / SFT / DPO / RLHF|
|最終的に理解するもの|LLMそのものを育てる一連の工程|
|学習項目数|73項目|

## 学習項目一覧

|段階|学習テーマ|分野|項目|学習する理由|取得するべき内容|
|:--|:--|:--|:--|:--|:--|
|最終段階|LLM Training|Pretraining|Corpus|LLMの知識源となる学習データを用意するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|出所・権利・個人情報・品質・時点・言語・分野構成を追跡できるCorpusを設計できること|
|最終段階|LLM Training|Pretraining|Tokenizer Training|モデル専用Vocabularyを作るため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|Tokenizerをゼロから学習できること|
|最終段階|LLM Training|Pretraining|Data Pipeline|巨大なデータを効率的に学習へ供給するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|Streaming・Shard・決定的Shuffle・Packing・Worker間分配・再開位置を含む分散Data Pipelineを設計できること|
|最終段階|LLM Training|Pretraining|Next Token Prediction|LLMの基本能力を獲得させるため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|事前学習目的関数を説明・実装できること|
|最終段階|LLM Training|Pretraining|Checkpoint|長時間学習を安全に継続するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|Model・Optimizer・Scheduler・Scaler・RNG・Data位置・分散ShardをAtomicに保存し、同条件で再開できること|
|最終段階|LLM Training|Pretraining|Learning Rate Schedule|大規模学習を安定させるため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|Warmup・Decayなどを設定できること|
|最終段階|LLM Training|データ処理|Web Corpus|大量の自然言語データを確保するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|取得許可・Robots・License・PII・Malware・Spam・Snapshot時点を考慮してWebデータ収集を統制できること|
|最終段階|LLM Training|データ処理|Deduplication|重複学習と暗記を抑えるため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|大規模重複除去の必要性を説明できること|
|最終段階|LLM Training|データ処理|Filtering|低品質・有害データを減らすため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|Rule・Classifier・Heuristicを組み合わせ、品質・安全性・Bias・誤除外のTrade-offをSample監査で評価できること|
|最終段階|LLM Training|データ処理|Language Detection|多言語Corpusを整理するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|言語別にデータを分類できること|
|最終段階|LLM Training|データ処理|Data Mixture|分野・言語の学習比率を制御するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|Dataset Mixtureを設計できること|
|最終段階|LLM Training|データ処理|Benchmark Contamination|評価データを学習してしまう問題を防ぐため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|データ汚染を検出・回避できること|
|最終段階|LLM Training|Scaling|Model Size|モデル規模と性能の関係を理解するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|固定Compute下のTraining Token数・Architecture・Memory・推論Costとの均衡を踏まえてParameter数を設計できること|
|最終段階|LLM Training|Scaling|Data Size|学習データ量と性能の関係を理解するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|有効Training Token数・重複・品質・Epoch数をModel SizeとComputeへ対応付けて説明できること|
|最終段階|LLM Training|Scaling|Compute|計算量と性能の関係を理解するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|FLOPs・Hardware効率・時間・CostのBudget内でModel SizeとToken数を共同最適化する考え方を説明できること|
|最終段階|LLM Training|分散学習|Data Parallelism|複数GPUで学習データを分散するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|Data Parallelの動作を説明できること|
|最終段階|LLM Training|分散学習|Tensor Parallelism|巨大モデルの層を複数GPUへ分割するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|Tensor Parallelを説明できること|
|最終段階|LLM Training|分散学習|Pipeline Parallelism|モデルの層をGPU間で分割するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|Pipeline Parallelの利点と欠点を説明できること|
|最終段階|LLM Training|分散学習|FSDP|モデル状態を分散保持するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|FSDPの基本原理を説明できること|
|最終段階|LLM Training|分散学習|ZeRO|巨大モデルのメモリ消費を削減するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|ZeRO Stageの概念を説明できること|
|最終段階|LLM Training|分散学習|Gradient Accumulation|小さいGPUメモリで大きいBatchを再現するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|勾配蓄積を実装できること|
|最終段階|LLM Training|分散学習|Mixed Precision|高速化とメモリ削減を行うため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|FP32・FP16・BF16・FP8、Accumulation精度、Master Weight、Loss Scaling、Hardware対応を区別して設計できること|
|最終段階|LLM Training|SFT|Instruction Dataset|Base Modelを指示に従えるようにするため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|SFT用Datasetを設計できること|
|最終段階|LLM Training|SFT|Chat Template|会話形式をモデルへ統一的に与えるため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|Chat Templateを設計・適用できること|
|最終段階|LLM Training|Preference Learning|Chosen・Rejected|回答品質の好みをモデルへ学ばせるため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|Preference Datasetを構築できること|
|最終段階|LLM Training|Preference Learning|Reward Signal|どの回答が望ましいか数値化するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|相対Preference・学習Reward・Rule・Verifierによる報酬を区別し、DPOで明示的Reward Modelが不要な理由を説明できること|
|最終段階|LLM Training|DPO|Reference Model|元モデルから過度に離れないよう比較するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|Reference Modelの役割を説明できること|
|最終段階|LLM Training|DPO|Preference Optimization|人間が好む回答を直接学習するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|Preference分類Loss・Reference比・Beta・Offline Data・長さBiasを含め、Reward ModelとOn-policy RLを省くDPOの仕組みを説明できること|
|最終段階|LLM Training|RLHF|Reinforcement Learning|報酬を用いてモデル行動を最適化するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|RLの基本構造をLLMに対応付けて説明できること|
|最終段階|LLM Training|RLHF|Reward Model|人間の好みを数値化するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|Reward Modelの役割を説明できること|
|最終段階|LLM Training|RLHF|Policy|最適化対象となるLLMを理解するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|PolicyとしてのLLMを説明できること|
|最終段階|LLM Training|RLHF|PPO|Rewardを用いてLLMを更新する方法を理解するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|On-policy生成・Value Model・Clipping・Advantage推定を用いる更新を説明し、PPOを他のRLHF手法と比較できること|
|最終段階|LLM Training|RLHF|KL Penalty|元モデルからの過度な逸脱を抑えるため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|KL制約の目的を説明できること|
|最終段階|LLM Training|Evaluation|Knowledge Evaluation|モデルの知識能力を評価するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|知識系Benchmarkを評価できること|
|最終段階|LLM Training|Evaluation|Reasoning Evaluation|推論性能を評価するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|推論タスクによる比較評価ができること|
|最終段階|LLM Training|Evaluation|Math Evaluation|数学能力を評価するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|数学問題によるモデル比較ができること|
|最終段階|LLM Training|Evaluation|Coding Evaluation|コード生成能力を評価するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|Coding Benchmarkを利用できること|
|最終段階|LLM Training|Evaluation|Instruction Following|指示遵守能力を評価するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|指示への適合度を評価できること|
|最終段階|LLM Training|Evaluation|Safety Evaluation|危険・不適切な出力を検証するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|Safety評価セットを設計・利用できること|
|最終段階|LLM Training|Evaluation|Robustness|入力変化に対する安定性を確認するため。LLMの大規模学習工程を設計・評価するための中核要素として必要であるため|モデルの頑健性を評価できること|
|最終段階|LLM Training|データガバナンス|Data Provenance・License・Privacy|学習Dataの利用根拠と削除可能性を追跡するため。大規模Corpusの品質だけでは、権利・Privacy・再現性・削除要求に対応できないため|Source、License、Consent、PII処理、取得時点、変換履歴、除外要求をDataset単位で記録できること|
|最終段階|LLM Training|データ処理|Text Normalization・Document Parsing|Webや文書のNoiseを除き、意味構造を保ったTextへ変換するため。Tokenization前の抽出・正規化不良は品質低下や重複判定の失敗を全Corpusへ広げるため|Encoding、Unicode、Boilerplate、Markup、表、Code、文書境界を検証しながら正規化できること|
|最終段階|LLM Training|データ処理|Data Quality Audit・Sampling|自動Filter後のData分布と誤判定を検証するため。自動Scoreだけでは、除去し過ぎ、残存Noise、言語・分野Biasを発見できないため|層化Sample、人手Rubric、Source別統計、False Positive・Negativeを用いて品質を監査できること|
|最終段階|LLM Training|Tokenizer|Tokenizer評価・Vocabulary設計|語彙が対象言語とDomainを効率よく表現できるか確認するため。Tokenizerを学習できても、語彙品質とModel計算量への影響を評価する項目が不足している|Fertility、Byte Fallback、未知文字、数字・Code、多言語、Special TokenをCorpus別に評価できること|
|最終段階|LLM Training|Pretraining|Model Architecture・Configuration|学習対象Modelの容量、安定性、計算量を定義するため。DataとComputeを決めても、ArchitectureとConfigがなければParameter数、Memory、Checkpoint互換性を再現できないため|Layer数、Hidden Size、Head、FFN、位置表現、Norm、Vocabulary、Dense・MoEを一貫したConfigとして設計できること|
|最終段階|LLM Training|Pretraining|Optimizer・Regularization・Gradient Clipping|大規模学習の更新量と発散Riskを制御するため。Learning Rate Scheduleだけでは更新則、正則化、勾配爆発への対策を定義できないため|Optimizer、Beta、Epsilon、Weight Decay、Gradient Norm、Clip閾値を選定・監視できること|
|最終段階|LLM Training|Pretraining|Validation Loss・Perplexity|未知Dataへの予測性能と過学習を追跡するため。Training Lossだけでは汎化、Data Mixtureの偏り、Checkpoint選択を判断できないため|固定Validation SetでToken-weighted Lossを算出し、Perplexity、Domain別差、Tokenizer差の限界を説明できること|
|最終段階|LLM Training|Pretraining|Training Stability・Loss Spike|高Costな学習の異常を早期検知し、安全に回復するため。大規模学習では小さな異常が多数Nodeへ波及し、未検知のまま大きなComputeを失うため|Loss、Gradient Norm、Activation、NaN・Inf、Throughputを監視し、原因をData・数値精度・通信へ切り分けられること|
|最終段階|LLM Training|Pretraining|Curriculum・Sequence Length Schedule|学習初期のCostと難易度を調整し、長いContextへ段階的に移行するため。全期間を同一分布・最大長で学習する以外の効率化と安定化手段が既存項目にないため|Data難易度、Domain、Sequence LengthのScheduleと分布変化を評価できること|
|最終段階|LLM Training|Scaling|Scaling Laws・Compute-optimal Design|限られたComputeをModelとDataへ適切に配分するため。Model Size、Data Size、Computeの個別理解を、実際の設計判断へ統合する項目が必要である|Pilot結果からLossのScaling傾向を推定し、Parameter数、Token数、FLOPsの候補を比較できること|
|最終段階|LLM Training|Scaling|Mixture of Experts|全Tokenで全Parameterを使わずModel容量を拡張するため。Dense Model以外の主要なScaling設計と、疎活性化固有の学習課題が不足している|Router、Top-k Expert、Load Balance、Capacity、Expert Parallelism、推論CostのTrade-offを説明できること|
|最終段階|LLM Training|Scaling|Pilot Run・Scaling Extrapolation|本番学習前にHyperparameterと予算の妥当性を確認するため。一度きりの大規模Runへ直接進むと、設定不良の検出が遅くCost損失が大きいため|小規模RunからLoss、Memory、Throughput、通信、Failure率を測り、本番規模へ外挿できること|
|最終段階|LLM Training|分散学習|Collective Communication・Interconnect|分散方式の通信CostとTopology制約を理解するため。並列方式の名称だけでは、通信がBottleneckになる理由と配置方針を設計できないため|All-reduce、All-gather、Reduce-scatter、Point-to-pointをBandwidth・Latency・Node境界と対応付けられること|
|最終段階|LLM Training|分散学習|Activation Checkpointing|Activation Memoryを再計算と引き換えに削減するため。Model StateのShardingだけでは長系列・大Batch時のActivation Memoryを十分に抑えられないため|保存するLayer粒度を選び、Memory削減量と追加Computeを測定できること|
|最終段階|LLM Training|分散学習|Sequence・Context Parallelism|長い系列のActivationとAttention計算をDevice間へ分割するため。Tensor・Pipeline Parallelismだけでは長Context時に増大する系列方向のMemoryを扱いにくいため|Sequence軸の分割、通信、Mask、Position、他Parallelismとの組合せを説明できること|
|最終段階|LLM Training|分散学習|Expert Parallelism|MoEのExpertを複数Deviceへ配置するため。MoEではDense Modelと異なる通信Patternと負荷偏りが学習効率を左右するため|Token Dispatch、All-to-all、Load Imbalance、Capacity Overflowを測定・対策できること|
|最終段階|LLM Training|分散学習|Parallelism Composition・Topology Mapping|複数の並列方式をCluster構成へ合わせて組み合わせるため。実際の大規模学習では単一方式だけでなく、Memoryと通信に応じた複合Parallelismが必要である|Data、Tensor、Pipeline、Sequence、Expert軸のGridを設計し、高速Link内外へ配置できること|
|最終段階|LLM Training|分散学習|Profiler・MFU・Throughput|GPUが有効計算へ使われている割合とBottleneckを測るため。学習が動作するだけでは、同じCostで十分なTokenを処理できているか判断できないため|Tokens毎秒、Step時間、MFU、通信待ち、Data待ち、Kernel時間をProfileし改善できること|
|最終段階|LLM Training|分散学習|Fault Tolerance・Elastic Resume|Node障害やPreemptionから大規模Runを復旧するため。多数Nodeを長期間使う学習では部分障害が避けにくく、手動復旧だけでは時間と再現性を失うため|障害検知、Atomic Checkpoint、Rank再構成、Data位置復元、再試行上限を設計・Testできること|
|最終段階|LLM Training|SFT|Loss Masking・Packing|会話Dataの学習対象Tokenと計算効率を制御するため。Instruction DatasetとChat Templateだけでは、どのTokenを学習し例同士を分離するか定まらないため|User・System TokenをMaskし、Assistant応答だけのLoss、複数例Packing、EOS境界を正しく実装できること|
|最終段階|LLM Training|Preference Learning|Preference Annotation Quality|選好Labelの一貫性と目的への適合を確保するため。Chosen・Rejectedが存在しても、Label品質が低ければReward Modelと直接選好最適化の双方が誤誘導されるため|Rubric、Annotator一致度、Tie、Noise、位置・長さBias、品質監査を設計できること|
|最終段階|LLM Training|Post-training|Rejection Sampling・Best-of-N|複数候補から高品質応答を選びSFTや評価へ利用するため。Gradient更新以外の基本的な応答改善・Data生成手法が既存項目にないため|候補生成、Score、重複除去、Selection Bias、推論Costを設計できること|
|最終段階|LLM Training|Preference Learning|RLAIF・AI Feedback|人手以外のFeedbackを補助的に利用するため。大規模なPreference Data作成ではAI Feedbackも使われるが、誤りやBiasを自己増幅させない統制が必要である|AI Judge、Rubric、Constitution、Calibration、人手監査、Bias増幅Riskを説明できること|
|最終段階|LLM Training|Post-training|Online RL・Offline Preference Optimization|Policyが生成した新Dataで学ぶ方式と固定Dataで学ぶ方式を選ぶため。DPOとPPOを個別に知るだけでは、Data生成と更新方式の根本的な違いを選択できないため|On-policy・Off-policy、探索、分布Shift、安定性、Cost、Reward Model要否を比較できること|
|最終段階|LLM Training|RLHF|GRPO|Value Modelを使わずGroup内相対RewardからPolicyを更新する方式を理解するため。PPO以外の代表的なOn-policy最適化方式を比較し、用途に応じて選ぶ項目が不足している|Group Sampling、相対Advantage、Clipping、KL、Verifier Reward、Costと安定性をPPOと比較できること|
|最終段階|LLM Training|Reward Design|Process Reward・Outcome Reward|最終結果だけでなく途中過程へFeedbackを与える設計を理解するため。ReasoningやTool利用では最終正誤だけで、どの中間行動を改善すべきか特定しにくいため|Step単位と最終回答のReward、Credit Assignment、Verifier信頼性、Gaming Riskを比較できること|
|最終段階|LLM Training|Reward Design|Reward Hacking・Specification Gaming|Proxy Rewardだけを攻略する望ましくない最適化を検出するため。Reward最適化は定義外の望ましくない行動を増やす可能性があり、独立評価と監査が必要である|Reward上昇と人手品質の乖離、Length・Format Hack、Evaluator Exploitを監視し対策できること|
|最終段階|LLM Training|Evaluation|Multilingual Evaluation|言語ごとの能力差と安全性の不均衡を把握するため。英語中心のBenchmarkだけでは、多言語Corpusで学習したModelの品質とRiskを判断できないため|高資源・低資源言語、翻訳依存、文化差、Tokenizer効率を分けて評価できること|
|最終段階|LLM Training|Evaluation|Long-context Evaluation|長い入力での検索、保持、統合能力とCostを測るため。Context Lengthの上限値だけでは、情報位置や入力長による実効性能低下を捉えられないため|位置、長さ、Distractor、複数根拠、長文生成、Latency・Memoryを変えて評価できること|
|最終段階|LLM Training|Evaluation|Calibration・Uncertainty・Abstention|予測の確信度と誤りRiskを利用判断へつなげるため。Accuracyが同じModelでも誤答時の過信や不明時の応答方針に大きな差があるため|Confidenceと正答率の対応、選択的回答、棄権、Threshold、Calibration Errorを評価できること|
|最終段階|LLM Training|Evaluation|Memorization・Privacy Extraction|学習Dataの再現と個人・機密情報漏洩Riskを測るため。Deduplicationだけでは、学習後Modelが稀な系列を記憶・露出するRiskを評価できないため|Canary、Membership Inference、Prompt Extraction、近似一致を用い、Data削除・公開判断へ接続できること|
|最終段階|LLM Training|Evaluation|Statistical Significance・Reproducible Harness|小さなScore差を偶然や実装差と区別するため。単一RunのBenchmark値だけではModel差の確度と再現性を判断できないため|Seed、Prompt、Sampling、Metric版を固定し、信頼区間、複数Run、Paired比較を実行できること|
|最終段階|LLM Training|ガバナンス|Data・Model LineageとModel Card|学習成果の由来、制約、評価、公開条件を追跡するため。再現、監査、Rollback、利用者への説明には、Dataから公開Modelまでの一貫した履歴が必要である|Dataset版、Code Commit、Config、Checkpoint、Post-training手順、評価結果、既知の限界を文書化できること|

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

[前の段階](07_第7段階_ChatGPT型システム.md) ｜ [全体概要・目次](00_全体概要・目次.md) ｜ [全体概要・目次](00_全体概要・目次.md)
