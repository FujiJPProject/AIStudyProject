# 第6段階：Fine-tuning

[前の段階](05_第5段階_Mini_GPT.md) ｜ [全体概要・目次](00_全体概要・目次.md) ｜ [次の段階](07_第7段階_ChatGPT型システム.md)

## この段階の位置づけ

|項目|内容|
|:--|:--|
|学習テーマ|Fine-tuning|
|最終的に理解するもの|既存LLMを目的に合わせて調整する方法|
|学習項目数|31項目|

## 学習項目一覧

|段階|学習テーマ|分野|項目|学習する理由|取得するべき内容|
|:--|:--|:--|:--|:--|:--|
|第6段階|Fine-tuning|Hugging Face|transformers|既存LLMを利用するため。限られた計算資源で安全かつ再現可能にモデルを調整するために必要であるため|モデル・Tokenizerを読み込み利用できること|
|第6段階|Fine-tuning|Hugging Face|datasets|大規模データセットを扱うため。限られた計算資源で安全かつ再現可能にモデルを調整するために必要であるため|Datasetの読み込み・加工ができること|
|第6段階|Fine-tuning|Hugging Face|Trainer|学習処理を効率的に構築するため。限られた計算資源で安全かつ再現可能にモデルを調整するために必要であるため|Trainer・TrainingArguments・Data Collator・評価・Callbackの役割を理解し、SFTTrainerと使い分けて学習できること|
|第6段階|Fine-tuning|Hugging Face|PEFT|省メモリFine-tuningを行うため。限られた計算資源で安全かつ再現可能にモデルを調整するために必要であるため|PEFTの目的を説明できること|
|第6段階|Fine-tuning|Fine-tuning|Full Fine-tuning|全パラメータ調整の仕組みを理解するため。限られた計算資源で安全かつ再現可能にモデルを調整するために必要であるため|Full Fine-tuningとPEFTを比較できること|
|第6段階|Fine-tuning|Fine-tuning|SFT|指示応答能力を追加するため。限られた計算資源で安全かつ再現可能にモデルを調整するために必要であるため|Language Modeling・Prompt-Completion・会話形式の学習データと、各形式でLossを計算する範囲を説明・設定できること|
|第6段階|Fine-tuning|LoRA|Low-Rank Adaptation|少ない追加パラメータで学習するため。限られた計算資源で安全かつ再現可能にモデルを調整するために必要であるため|LoRAの基本原理を説明できること|
|第6段階|Fine-tuning|LoRA|Rank|LoRAの表現力とメモリ量を調整するため。限られた計算資源で安全かつ再現可能にモデルを調整するために必要であるため|Rank変更の影響を理解できること|
|第6段階|Fine-tuning|LoRA|Alpha|LoRA更新量を調整するため。限られた計算資源で安全かつ再現可能にモデルを調整するために必要であるため|AlphaとRankの比によるScalingがLoRAの更新量へ与える影響を説明できること|
|第6段階|Fine-tuning|LoRA|Target Module|Fine-tuning対象層を指定するため。限られた計算資源で安全かつ再現可能にモデルを調整するために必要であるため|Model Architectureの層名を確認し、Attention射影または全Linear層などから学習容量を考慮してTarget Moduleを選べること|
|第6段階|Fine-tuning|量子化|8bit Quantization|モデルのメモリ消費を削減するため。限られた計算資源で安全かつ再現可能にモデルを調整するために必要であるため|Weight量子化・8-bit Optimizer・推論・PEFT学習を区別し、量子化Base Weightの制約を説明できること|
|第6段階|Fine-tuning|量子化|4bit Quantization|より小さいGPUでLLMを扱うため。限られた計算資源で安全かつ再現可能にモデルを調整するために必要であるため|NF4・FP4、Compute dtype、Double Quantization、品質・Hardware制約を区別して4bit量子化を設定できること|
|第6段階|Fine-tuning|QLoRA|QLoRA|量子化モデルを効率的にFine-tuningするため。限られた計算資源で安全かつ再現可能にモデルを調整するために必要であるため|凍結した4bit量子化Base Modelを通して勾配を伝え、LoRA Adapterのみを学習する構造とNF4・Double Quantizationを説明・実装できること|
|第6段階|Fine-tuning|データセット設計|Data Cleaning|誤ったデータによる性能低下を防ぐため。限られた計算資源で安全かつ再現可能にモデルを調整するために必要であるため|不要・不正データを除去できること|
|第6段階|Fine-tuning|データセット設計|Deduplication|重複データによる偏りを防ぐため。限られた計算資源で安全かつ再現可能にモデルを調整するために必要であるため|重複データを検出・削除できること|
|第6段階|Fine-tuning|データセット設計|Formatting|モデル形式に適した学習データを作るため。限られた計算資源で安全かつ再現可能にモデルを調整するために必要であるため|Language Modeling・Prompt-Completion・会話形式を、role・content、Special Token、Chat Templateと整合する形式へ変換できること|
|第6段階|Fine-tuning|データセット設計|Dataset Balance|特定分野への偏りを防ぐため。限られた計算資源で安全かつ再現可能にモデルを調整するために必要であるため|データ構成比を評価・調整できること|
|第6段階|Fine-tuning|Hugging Face|TRL・SFTTrainer|会話形式やPrompt-Completion形式のSFTを適切に実行するため。汎用Trainerだけでは、Chat Template適用、Packing、Completion LossなどSFT固有の処理が分かりにくいため|SFTTrainerへModel、Dataset、SFTConfig、PEFT設定を渡し、学習・評価できること|
|第6段階|Fine-tuning|データセット設計|Chat Template|会話のroleとSpecial Tokenを対象Modelが期待するToken列へ変換するため。同じ会話内容でもModelごとに制御Tokenが異なり、形式不一致が性能を大きく損なうため|TokenizerのChat Templateを確認し、重複Special Tokenを避けて会話データへ適用できること|
|第6段階|Fine-tuning|損失設計|Label Masking・Completion Loss|Prompt部分を学習対象にするか、Assistant回答だけを学習するか制御するため。Dataset形式だけでは、どのTokenに対して誤差を計算するかが定まらないため|不要なLabelをignore indexへ置き換え、学習目的に応じてLoss対象Tokenを設定できること|
|第6段階|Fine-tuning|データセット設計|Truncation・Packing|Context Lengthを効率よく使い、長すぎる例を安全に処理するため。系列長の処理を誤ると重要な回答部分の欠落や、Paddingによる計算浪費が起きるため|最大系列長、切り詰め方、短い例のPacking、EOS境界を設計できること|
|第6段階|Fine-tuning|データセット設計|Train・Validation・Test分割と汚染防止|学習調整と最終評価を分離し、評価例の暗記を防ぐため。Fine-tuning Datasetと評価DatasetのLeakageを防ぐ項目が明示されていない|類似例・同一会話を跨がせずに分割し、BenchmarkやTestとの重複を検査できること|
|第6段階|Fine-tuning|学習設定|Learning Rate・Batch・Epoch・Warmup|Base Modelを壊さず、限られたデータから安定して学習するため。Fine-tuningの成否を左右する主要Hyperparameterと相互関係が既存項目にない|実効Batch Size、Gradient Accumulation、学習率、Epoch、Warmup、Schedulerを一体として設定できること|
|第6段階|Fine-tuning|学習効率化|Mixed Precision・Gradient Checkpointing|VRAMを抑えながら大きなModelや系列を学習するため。LoRAや量子化以外の主要な省Memory手段が不足している|bf16・fp16の選択、Gradient Checkpointingの計算時間とMemoryのTrade-offを説明・設定できること|
|第6段階|Fine-tuning|LoRA|LoRA Dropout・modules_to_save|Adapterの正則化と、LoRA対象外でも学習・保存すべき層を制御するため。Rank、Alpha、Target Moduleだけでは実用的なLoRA設定と保存対象を十分に扱えないため|LoRA Dropoutを設定し、必要に応じてEmbeddingや分類Headなどを保存対象へ含められること|
|第6段階|Fine-tuning|LoRA|Adapter保存・読込・Merge|用途別Adapterを管理し、推論形式へ変換するため。学習後の成果物管理とDeploymentへ接続する工程が既存項目にない|Adapterだけを保存・読み込みし、Base Modelとの組合せを記録し、必要に応じてMergeできること|
|第6段階|Fine-tuning|資源計画|VRAM・学習可能Parameter数の見積り|手元のHardwareで実行可能な方式と設定を選ぶため。手法名だけでは実行前にOOMの可能性や現実的なModel Sizeを判断できないため|Model Weight、Optimizer State、Gradient、ActivationのMemoryを概算し、Full・LoRA・QLoRAを比較できること|
|第6段階|Fine-tuning|評価|Base Modelとの比較評価|Fine-tuningが目的性能を改善し、一般能力を過度に損なっていないか確認するため。学習Lossだけでは調整の有効性を判断できず、元Modelからの変化を測る基準が必要である|同一Prompt・設定でBaseとFine-tuned Modelを比較し、目的指標と副作用を評価できること|
|第6段階|Fine-tuning|評価|Overfitting・Catastrophic Forgetting|少量データへの暗記や既存能力の損失を検出するため。特定用途への改善と汎用能力低下のTrade-offを判断する項目が不足している|Train・Validation差、生成例、一般Benchmarkを用いて過学習と破壊的忘却を評価・対策できること|
|第6段階|Fine-tuning|実験管理|Checkpoint・実験追跡・再現性|複数条件を比較し、学習を再開・再現できるようにするため。Fine-tuning結果を比較可能にし、採用Modelの由来を追跡する仕組みが不足している|Config、Seed、Dataset版、Model Revision、Metric、Checkpointを一体で記録できること|
|第6段階|Fine-tuning|ガバナンス|License・個人情報・安全性|ModelとDatasetを適法かつ安全に利用・公開するため。技術的に学習できても、権利・Privacy・安全上の制約を満たさなければ実運用できないため|利用条件、再配布条件、個人・機密情報、有害データ、公開範囲を確認し、記録できること|

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

[前の段階](05_第5段階_Mini_GPT.md) ｜ [全体概要・目次](00_全体概要・目次.md) ｜ [次の段階](07_第7段階_ChatGPT型システム.md)
