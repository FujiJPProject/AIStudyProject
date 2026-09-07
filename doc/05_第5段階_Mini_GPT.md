# 第5段階：Mini GPT

[前の段階](04_第4段階_Transformer.md) ｜ [全体概要・目次](00_全体概要・目次.md) ｜ [次の段階](06_第6段階_Fine-tuning.md)

## この段階の位置づけ

|項目|内容|
|:--|:--|
|学習テーマ|Mini GPT|
|最終的に理解するもの|GPTが文章を生成する仕組み|
|学習項目数|26項目|

## 学習項目一覧

|段階|学習テーマ|分野|項目|学習する理由|取得するべき内容|
|:--|:--|:--|:--|:--|:--|
|第5段階|Mini GPT|Tokenizer|Character Tokenization|最小構成でToken化を理解するため。小規模GPTを一貫して実装・学習・評価するために必要であるため|文字単位Tokenizerを実装できること|
|第5段階|Mini GPT|Tokenizer|BPE|実用LLMで使われるTokenizationを理解するため。小規模GPTを一貫して実装・学習・評価するために必要であるため|BPEの基本原理を説明できること|
|第5段階|Mini GPT|Tokenizer|SentencePiece（BPE・Unigram）|言語非依存のTokenizationを理解するため。小規模GPTを一貫して実装・学習・評価するために必要であるため|SentencePieceがBPEやUnigramを実装するTokenizer学習ツールであり、単一のToken化アルゴリズムではないことを説明できること|
|第5段階|Mini GPT|GPT構造|Decoder-only Transformer|GPTの基本構造だから。小規模GPTを一貫して実装・学習・評価するために必要であるため|Decoder-onlyモデルを構築できること|
|第5段階|Mini GPT|GPT構造|Causal Mask|未来のTokenを参照させないため。小規模GPTを一貫して実装・学習・評価するために必要であるため|Causal Attentionの必要性を説明できること|
|第5段階|Mini GPT|GPT構造|Autoregressive Model|前のTokenから次Tokenを生成するため。小規模GPTを一貫して実装・学習・評価するために必要であるため|自己回帰生成を説明できること|
|第5段階|Mini GPT|Language Modeling|Next Token Prediction|GPTの事前学習目的そのものだから。小規模GPTを一貫して実装・学習・評価するために必要であるため|次Token予測の学習方法を説明できること|
|第5段階|Mini GPT|Language Modeling|Context Length|モデルが参照できる範囲を理解するため。小規模GPTを一貫して実装・学習・評価するために必要であるため|Context Windowの意味を説明できること|
|第5段階|Mini GPT|Language Modeling|Cross Entropy Loss|次Token予測を最適化するため。小規模GPTを一貫して実装・学習・評価するために必要であるため|各位置のLogitと1 Token先へずらしたLabelを対応付け、Token単位のLossをBatch・系列方向へ集約できること|
|第5段階|Mini GPT|文章生成|Greedy Decoding|最も基本的な生成方式を理解するため。小規模GPTを一貫して実装・学習・評価するために必要であるため|最大確率Tokenを逐次選択できること|
|第5段階|Mini GPT|文章生成|Temperature|出力のランダム性を調整するため。小規模GPTを一貫して実装・学習・評価するために必要であるため|Temperatureによる確率分布変化を説明できること|
|第5段階|Mini GPT|文章生成|Top-k|候補Tokenを限定するため。小規模GPTを一貫して実装・学習・評価するために必要であるため|Top-k Samplingを実装できること|
|第5段階|Mini GPT|文章生成|Top-p|累積確率で候補を選択するため。小規模GPTを一貫して実装・学習・評価するために必要であるため|Nucleus Samplingを説明できること|
|第5段階|Mini GPT|実装|Dataset作成|GPT学習用データを準備するため。小規模GPTを一貫して実装・学習・評価するために必要であるため|連続Token列をWindowへ分割し、入力・Labelを1 TokenずらしてTrain・Validationデータを作成できること|
|第5段階|Mini GPT|実装|Training Loop|GPTを実際に学習させるため。小規模GPTを一貫して実装・学習・評価するために必要であるため|Token Batch、Forward、Loss、Backward、更新、Validation Loss、Gradient Clipping、Checkpointを含むGPT学習Loopを実装できること|
|第5段階|Mini GPT|実装|Text Generation|学習済みモデルから文章を生成するため。小規模GPTを一貫して実装・学習・評価するために必要であるため|自作GPTから文章を出力できること|
|第5段階|Mini GPT|Tokenizer|Byte・Unicode処理|日本語や未知文字を壊さず、任意のテキストをToken化する考え方を理解するため。文字単位Tokenizerから実用的な多言語・未知文字対応へ進むための前提が不足している|文字・Unicode code point・UTF-8 byteの違いと、Byte-level Tokenizationの利点を説明できること|
|第5段階|Mini GPT|Tokenizer|encode・decode・Special Token ID|文字列とToken ID列を双方向に変換し、系列境界を扱うため。Tokenizerの名称だけでは、モデル入出力へ接続する実装契約と特殊Token管理を確認できないため|encode・decodeを実装し、BOS・EOS・PAD・UNKなどのIDをVocabularyと整合させられること|
|第5段階|Mini GPT|GPT構造|Model Configuration・Parameter数|Mini GPTの規模と計算量を制御するため。モデル規模を変更して学習可能な範囲へ調整し、各Hyperparameterの関係を理解する項目が不足している|Vocabulary Size、Context Length、d_model、Head数、Layer数、FFN次元を設定し、Parameter数を概算できること|
|第5段階|Mini GPT|GPT構造|Language Model Head・Logits|各位置の隠れ表現からVocabulary全体の予測スコアを作るため。Transformer Blockの出力を次Token確率へ変換する出口が既存項目に明示されていない|最終NormとLinear層からBatch・系列長・Vocabulary SizeのLogitを出力できること|
|第5段階|Mini GPT|GPT構造|Weight Tying|入力Embeddingと出力Projectionの重みを共有するため。GPT系モデルでよく使われる入力・出力Embedding間の関係が不足している|重み共有の実装方法と、Parameter数・表現学習への影響を説明できること|
|第5段階|Mini GPT|Language Modeling|Input・Label ShiftとTeacher Forcing|系列全位置の次Token予測を並列に学習するため。Next Token Predictionを実際のTensorへ落とす中心処理が既存項目では曖昧である|入力Tokenと1位置先のLabelを対応付け、学習時は正解Prefix全体を入力することを説明・実装できること|
|第5段階|Mini GPT|評価|Validation Loss・Perplexity|学習の進行と未知テキストへの予測性能を評価するため。生成例の主観評価だけでは、言語モデルの学習状態と過学習を定量的に判断できないため|Validation Lossを計算し、Perplexityとの関係と限界を説明できること|
|第5段階|Mini GPT|実装|Checkpoint・学習再開|学習状態を保存し、中断後も同じ条件から再開するため。Mini GPTの学習実験を安全に継続し、最良状態を再利用する仕組みが不足している|Model、Optimizer、Step、設定を保存し、Checkpointから学習を再開できること|
|第5段階|Mini GPT|文章生成|EOS・生成終了条件|生成を適切な長さと条件で停止するため。Text GenerationにはToken選択だけでなく、安全に終了する制御が必要だが明示されていない|EOS検出、最大生成Token数、Context Length上限による停止を実装できること|
|第5段階|Mini GPT|検証|小規模BatchへのOverfit Test|モデル、Loss、勾配、Datasetの実装がつながっていることを確認するため。学習が進まない原因をモデル能力と実装不具合に切り分ける実践的な検証手順が不足している|ごく小さいBatchを意図的に暗記させ、Lossが十分下がるかで実装を診断できること|

## 到達目標

小規模なGPTを自分で構築する。

```text
文章
↓
Tokenizer
↓
Token ID
↓
Embedding
↓
Transformer Block
↓
Next Token Prediction
↓
Cross Entropy
↓
Training
↓
文章生成
```

最終的には、自作したGPTモデルを学習させ、文章を生成できることを目標とする。

---

[前の段階](04_第4段階_Transformer.md) ｜ [全体概要・目次](00_全体概要・目次.md) ｜ [次の段階](06_第6段階_Fine-tuning.md)
