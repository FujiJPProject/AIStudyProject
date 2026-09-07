# 第4段階：Transformer

[前の段階](03_第3段階_Neural_Network.md) ｜ [全体概要・目次](Readme.md) ｜ [次の段階](05_第5段階_Mini_GPT.md)

## この段階の位置づけ

| 項目                 | 内容                |
| :------------------- | :------------------ |
| 学習テーマ           | Transformer         |
| 最終的に理解するもの | LLMの中核となる構造 |
| 学習項目数           | 25項目              |

## 学習項目一覧

| 段階    | 学習テーマ  | 分野            | 項目                            | 学習する理由                                                                                              | 取得するべき内容                                                                                               |
| :------ | :---------- | :-------------- | :------------------------------ | :-------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------- |
| 第4段階 | Transformer | NLP基礎         | Token・Vocabulary・Tokenization | 文章をモデルが扱う単位へ分割し、各TokenをVocabulary内のIDへ対応付ける一連の入口を理解するため             | Token、Vocabulary、Token IDの関係を説明し、文章がID列へ変換される流れを説明できること                          |
| 第4段階 | Transformer | NLP基礎         | Special Token・Padding          | 系列の開始・終了などを表し、長さの異なるToken列を同じBatchで扱うため                                      | BOS、EOS、PAD、UNKの役割を説明し、Padding後のToken ID列を作成できること                                        |
| 第4段階 | Transformer | Embedding       | Token Embedding                 | 離散的なToken IDを、モデルが演算できる連続ベクトルへ変換するため                                          | Embedding行列からToken IDに対応するベクトルを取り出し、系列のTensor形状を説明できること                        |
| 第4段階 | Transformer | 位置表現        | 絶対位置表現                    | Attention単体では保持されないTokenの順序をEmbeddingへ与える基本方式を理解するため                         | 正弦波Positional Encodingと学習可能なPosition Embeddingの違い、およびToken Embeddingへの加え方を説明できること |
| 第4段階 | Transformer | Attention       | Query・Key・Value               | 各Tokenが「何を探すか」「何を示すか」「どの情報を渡すか」を一つのAttention計算として理解するため          | 入力からQ・K・Vを線形変換で作り、それぞれの役割と形状を説明できること                                          |
| 第4段階 | Transformer | Attention       | Self-Attention                  | 同じ系列からQ・K・Vを作り、各Tokenが系列内の情報を取り込む仕組みを理解するため                            | Self-Attentionと一般的なAttentionの違いを説明し、各Tokenが同じ系列のどの情報を参照するか説明できること         |
| 第4段階 | Transformer | Attention       | 双方向・因果Attention           | 目的に応じて、各Tokenが過去・未来のどこまで参照できるかを区別するため                                     | Encoderの双方向Attentionと、GPTの因果Attentionの参照範囲を図示・比較できること                                 |
| 第4段階 | Transformer | Attention       | Attention Score・Scaling        | QueryとKeyの内積で関連度を求め、次元が大きいときの値の増大をScalingで抑えるため                           | QKᵀの計算と形状を追い、√dₖで割る理由を説明できること                                                           |
| 第4段階 | Transformer | 位置表現        | 相対位置表現・RoPE              | Q・KとAttention ScoreへToken間の相対位置関係を反映する現代的な方式を理解するため                          | 絶対位置表現との違いを説明し、RoPEが位置に応じてQ・Kを回転させる考え方を説明できること                         |
| 第4段階 | Transformer | Attention       | Attention Mask                  | Padding位置や未来TokenをAttentionの参照対象から除外するため                                               | Padding MaskとCausal Maskを区別し、Softmax前のAttention Scoreへ適用できること                                  |
| 第4段階 | Transformer | Attention       | Softmax・Valueの加重和          | Mask適用後のAttention Scoreを合計1の重みへ変換し、Valueから参照結果を作るため                             | softmax(QKᵀ/√dₖ + Mask)Vの各計算とTensor形状を説明・実装できること                                             |
| 第4段階 | Transformer | Attention       | Cross-Attention                 | ある系列のQueryから別の系列が持つKey・Valueを参照する仕組みを理解するため                                 | Decoderの表現からQを作り、Encoder出力からK・Vを作る流れを説明できること                                        |
| 第4段階 | Transformer | Attention       | Multi-Head Attention            | 異なる線形射影を使う複数のHeadで、Token間の関係を複数の表現空間から捉えるため                             | Single-Headとの違いと、HeadごとにQ・K・Vを作る意味を説明できること                                             |
| 第4段階 | Transformer | Attention       | Q・K・VのTensor形状・Head分割   | Multi-Head Attentionを実装する際に、Batch、系列長、Head数、Head次元を正しく追跡するため                   | Q・K・Vを`(Batch, Seq, d_model)`から`(Batch, Head, Seq, d_head)`へ変形・転置できること                         |
| 第4段階 | Transformer | Attention       | Head結合・Output Projection     | 各Headの出力を結合し、後続Layerが扱うモデル次元へ戻すため                                                 | Headをconcatして`(Batch, Seq, d_model)`へ戻し、出力射影Wₒを適用できること                                      |
| 第4段階 | Transformer | 計算特性        | Attentionの計算量・メモリ量     | 系列長の二乗サイズとなるAttention Score行列が、長いContextの主要コストになるため                          | 標準Self-Attentionの計算量とAttention行列のメモリ量が、系列長に対して概ね二次で増える理由を説明できること      |
| 第4段階 | Transformer | Transformer構造 | Feed Forward Network            | Attentionで混ぜた各Tokenの特徴を、Tokenごとに同じMLPで変換するため                                        | モデル次元から中間次元への拡張・縮小と、GELU・SwiGLUを使う処理を説明できること                                 |
| 第4段階 | Transformer | Transformer構造 | Residual Connection             | Sub-layerの入力を出力へ加え、情報と勾配が深いBlockを通りやすくするため                                    | Attention・FFNの入出力形状が一致する理由と、Residual加算を説明・実装できること                                 |
| 第4段階 | Transformer | Transformer構造 | Layer Normalization・RMSNorm    | Tokenごとの特徴方向を正規化し、Transformerの学習を安定させる代表方式を比較するため                        | 正規化する軸を説明し、平均を引くLayerNormと二乗平均平方根を使うRMSNormの違いを説明できること                   |
| 第4段階 | Transformer | Transformer構造 | Pre-Norm・Post-Norm             | NormalizationをSub-layerとResidual Connectionのどこへ配置するかで計算順序と学習特性が変わるため           | Pre-NormとPost-Normの計算順序を図示し、Residual Connectionとの位置関係を説明できること                         |
| 第4段階 | Transformer | Transformer構造 | Transformer Block               | Multi-Head Attention、FFN、Residual Connection、Normalizationを一つの再利用可能な層としてまとめるため     | Transformer BlockのForward処理を順に説明し、各Tensorの形状を保って実装できること                               |
| 第4段階 | Transformer | Transformer種類 | Encoder-only Transformer        | 入力系列全体を双方向に参照し、系列の理解や表現生成に使う構造を理解するため                                | 双方向Self-Attentionを持つEncoder Blockの構成と主な用途を説明できること                                        |
| 第4段階 | Transformer | Transformer種類 | Encoder-Decoder Transformer     | Encoderの表現をDecoderがCross-Attentionで参照し、入力系列に条件付けた出力を生成する原典構造を理解するため | Encoder、Masked Self-Attentionを持つDecoder、Cross-Attentionの接続関係を説明できること                         |
| 第4段階 | Transformer | Transformer種類 | Decoder-only Transformer・GPT   | 因果Self-Attentionを持つBlockだけで、前のTokenから次のTokenを予測するGPTの構造へつなげるため              | 原典Transformer Decoderとの違いを説明し、通常Cross-Attentionを持たないGPT型Blockを構成できること               |
| 第4段階 | Transformer | 計算特性        | 効率的Attention・FlashAttention | 標準Attentionと同じ結果を保ちながら、GPUメモリ間の読み書きと中間保存を減らす考え方を理解するため          | FlashAttentionが近似Attentionではなく、Tilingと計算順序の工夫によるExact Attentionであることを説明できること   |

## 到達目標

Transformer内部の以下の処理を説明できる状態を目指す。

```text
Token
↓
Embedding
↓
Query / Key / Value
↓
Attention Score
↓
Softmax
↓
Self-Attention
↓
Multi-Head Attention
↓
Feed Forward Network
↓
Transformer Block
```

特に、

> Attentionとは、各Tokenが他のTokenをどの程度参照するべきかを計算する仕組みである。

と説明できることを重要な到達基準とする。

---

[前の段階](03_第3段階_Neural_Network.md) ｜ [全体概要・目次](Readme.md) ｜ [次の段階](05_第5段階_Mini_GPT.md)
