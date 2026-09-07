# 第5段階：Mini GPT

[前の段階](04_第4段階_Transformer.md) ｜ [全体概要・目次](Readme.md) ｜ [次の段階](06_第6段階_Fine-tuning.md)

## この段階の位置づけ

| 項目                 | 内容                      |
| :------------------- | :------------------------ |
| 学習テーマ           | Mini GPT                  |
| 最終的に理解するもの | GPTが文章を生成する仕組み |
| 学習項目数           | 21項目                    |

## 学習項目一覧

| 段階    | 学習テーマ | 分野              | 項目                                        | 学習する理由                                                                                                  | 取得するべき内容                                                                                                                                                      |
| :------ | :--------- | :---------------- | :------------------------------------------ | :------------------------------------------------------------------------------------------------------------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 第5段階 | Mini GPT   | Tokenizer         | Character Tokenization                      | 最小構成のTokenizerを自作し、文字とToken IDの対応を具体的に理解するため                                       | 学習テキストから文字Vocabularyを作り、文字単位のencode・decodeを実装できること                                                                                        |
| 第5段階 | Mini GPT   | Tokenizer         | Byte・Unicode処理                           | 日本語や未知文字を壊さず扱うために、文字と実際のByte列の違いを理解するため                                    | Unicode code point、UTF-8 byte、文字の違いを説明し、Byte-level Tokenizationの利点と系列長への影響を説明できること                                                     |
| 第5段階 | Mini GPT   | Tokenizer         | BPE                                         | 文字・Byte単位から頻出する並びをSubwordへまとめ、Vocabulary Sizeと系列長を調整する仕組みを理解するため        | BPEのPair集計、Merge規則の学習、Token化を小規模データで実装できること                                                                                                 |
| 第5段階 | Mini GPT   | Tokenizer         | SentencePiece（BPE・Unigram）               | 言語固有の事前分割へ依存せず、Raw TextからSubword Tokenizerを学習する方法を理解するため                       | SentencePieceがBPEとUnigramを選択できるTokenizer学習ツールであることを説明し、両方式の違いを説明できること                                                            |
| 第5段階 | Mini GPT   | Tokenizer         | encode・decode・Special Token ID            | Tokenizerとモデルの間で文字列とToken ID列を双方向に変換し、系列境界を一貫して扱うため                         | encode・decodeを実装し、BOS、EOS、PAD、UNKなどのIDをVocabularyと整合させられること                                                                                    |
| 第5段階 | Mini GPT   | Language Modeling | Autoregressive Model・Next Token Prediction | 過去のToken列を条件として次Tokenの確率を学ぶ、GPTの学習目的と生成原理を一体として理解するため                 | 系列確率の自己回帰分解とNext Token Predictionの関係を説明できること                                                                                                   |
| 第5段階 | Mini GPT   | Language Modeling | Context Length                              | 各予測で参照できる過去Token数と、モデル入力の最大長を理解するため                                             | Context Windowの意味を説明し、長さを超えた系列の分割または切り詰め方を説明できること                                                                                  |
| 第5段階 | Mini GPT   | Language Modeling | Input・Label ShiftとTeacher Forcing         | 系列内の全位置についてNext Token Predictionを並列に学習するTensorを作るため                                   | 入力Tokenと1位置先のLabelを対応付け、学習時は正解Prefixをまとめて入力することを説明・実装できること                                                                   |
| 第5段階 | Mini GPT   | 実装              | Dataset作成                                 | 連続Token列から、Context Lengthに収まる学習用の入力・Label組を反復して供給するため                            | Token列をWindowへ分割し、Input・Label Shiftを適用したTrain・Validation Datasetを作成できること                                                                        |
| 第5段階 | Mini GPT   | GPT構造           | Model Configuration・Parameter数            | 手元の計算資源で学習可能なMini GPTの規模を設計するため                                                        | Vocabulary Size、Context Length、d_model、Head数、Layer数、FFN次元を設定し、主要部分のParameter数を概算できること                                                     |
| 第5段階 | Mini GPT   | GPT構造           | Decoder-only Transformer・Causal Mask       | 第4段階で学んだTransformer Blockを、未来Tokenを参照しないGPT本体として組み立てるため                          | Token・Position表現、Causal Self-Attention、FFN、Residual、NormからDecoder-onlyモデルを実装できること                                                                 |
| 第5段階 | Mini GPT   | GPT構造           | Language Model Head・Logits                 | 各位置の隠れ表現をVocabulary全体の次Token予測Scoreへ変換するため                                              | 最終NormalizationとLinear層から`(Batch, Seq, Vocabulary Size)`のLogitsを出力できること                                                                                |
| 第5段階 | Mini GPT   | GPT構造           | Weight Tying                                | 入力EmbeddingとLanguage Model HeadのWeightを共有し、入力表現と出力予測を対応付けながらParameter数を抑えるため | Weight Tyingを実装し、共有しない場合とのParameter数の違いを説明できること                                                                                             |
| 第5段階 | Mini GPT   | Language Modeling | Cross Entropy Loss                          | 各位置のLogitsと次Token Labelを比較し、モデル全体を学習する単一のLossへ集約するため                           | LogitsとLabelの形状をLoss関数へ渡せる形へ変換し、Paddingなどの無効Labelを除外して平均Lossを計算できること                                                             |
| 第5段階 | Mini GPT   | 評価              | Validation Loss・Perplexity                 | 未知テキストへの次Token予測性能と過学習を定量的に確認するため                                                 | 学習時と分離してValidation Lossを計算し、Perplexityが平均Negative Log-Likelihoodの指数であることと、Tokenizerが異なるモデル間では単純比較しにくいことを説明できること |
| 第5段階 | Mini GPT   | 実装              | Training Loop                               | Dataset、モデル、Loss、Optimizerを接続し、Mini GPTを反復学習・評価するため                                    | Token Batch取得、Forward、Loss、zero_grad、Backward、Gradient Clipping、更新、定期的なValidationを含むLoopを実装できること                                            |
| 第5段階 | Mini GPT   | 検証              | 小規模BatchへのOverfit Test                 | 本格学習の前に、モデル、Dataset、Loss、勾配更新が正しく接続されているか確認するため                           | 固定したごく小さいBatchを意図的に暗記させ、Loss低下と予測結果から実装不具合を切り分けられること                                                                       |
| 第5段階 | Mini GPT   | 実装              | Checkpoint・学習再開                        | 長時間の学習を中断・再開し、最良のValidation結果を持つ状態を再利用するため                                    | Model、Optimizer、Step、設定、Tokenizer情報を保存し、同じ条件で学習または推論を再開できること                                                                         |
| 第5段階 | Mini GPT   | 文章生成          | Text Generation・Greedy Decoding            | 学習済みモデルへ現在のToken列を入力し、最大確率の次Tokenを追加する基本生成Loopを理解するため                  | 末尾位置のLogitsから最大値のTokenを選択し、入力へ追加して逐次生成できること                                                                                           |
| 第5段階 | Mini GPT   | 文章生成          | Sampling（Temperature・Top-k・Top-p）       | 確率分布の鋭さと候補集合を調整し、Greedy Decoding以外の生成を比較するため                                     | Temperature Scaling、Top-k、Top-pを順に適用してSamplingし、各設定が多様性へ与える影響を説明できること                                                                 |
| 第5段階 | Mini GPT   | 文章生成          | EOS・生成終了条件                           | 生成Loopが無制限に続いたりContext Lengthを超えたりすることを防ぐため                                          | EOS検出、最大生成Token数、Context Length上限による終了条件を実装できること                                                                                            |

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

[前の段階](04_第4段階_Transformer.md) ｜ [全体概要・目次](Readme.md) ｜ [次の段階](06_第6段階_Fine-tuning.md)
