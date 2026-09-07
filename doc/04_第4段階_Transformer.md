# 第4段階：Transformer

[前の段階](03_第3段階_Neural_Network.md) ｜ [全体概要・目次](00_全体概要・目次.md) ｜ [次の段階](05_第5段階_Mini_GPT.md)

## この段階の位置づけ

|項目|内容|
|:--|:--|
|学習テーマ|Transformer|
|最終的に理解するもの|LLMの中核となる構造|
|学習項目数|30項目|

## 学習項目一覧

|段階|学習テーマ|分野|項目|学習する理由|取得するべき内容|
|:--|:--|:--|:--|:--|:--|
|第4段階|Transformer|NLP基礎|Token|文章をモデルが扱う単位へ分解するため。GPTの構造とSelf-Attentionの計算を理解・実装するために必要であるため|Tokenの意味を説明できること|
|第4段階|Transformer|NLP基礎|Vocabulary|モデルが扱えるToken集合を理解するため。GPTの構造とSelf-Attentionの計算を理解・実装するために必要であるため|Vocabulary Sizeの意味を説明できること|
|第4段階|Transformer|NLP基礎|Tokenization|文字列を数値列へ変換するため。GPTの構造とSelf-Attentionの計算を理解・実装するために必要であるため|文章からToken IDへの変換を説明できること|
|第4段階|Transformer|Embedding|Token Embedding|Tokenをベクトルへ変換するため。GPTの構造とSelf-Attentionの計算を理解・実装するために必要であるため|Embedding層の役割を説明できること|
|第4段階|Transformer|Embedding|Positional Encoding|Transformerに単語順序を与えるため。GPTの構造とSelf-Attentionの計算を理解・実装するために必要であるため|正弦波・学習可能な絶対位置・相対位置・RoPEの違いと外挿特性を説明できること|
|第4段階|Transformer|Attention|Query|参照したい情報を表現するため。GPTの構造とSelf-Attentionの計算を理解・実装するために必要であるため|Queryの役割を説明できること|
|第4段階|Transformer|Attention|Key|参照対象の特徴を表現するため。GPTの構造とSelf-Attentionの計算を理解・実装するために必要であるため|Keyの役割を説明できること|
|第4段階|Transformer|Attention|Value|実際に取り出す情報を表現するため。GPTの構造とSelf-Attentionの計算を理解・実装するために必要であるため|Valueの役割を説明できること|
|第4段階|Transformer|Attention|Scaled Dot-Product Attention|Attentionの中心計算を理解するため。GPTの構造とSelf-Attentionの計算を理解・実装するために必要であるため|Attention(Q,K,V)を説明できること|
|第4段階|Transformer|Attention|Softmax|Attention Scoreを重みへ変換するため。GPTの構造とSelf-Attentionの計算を理解・実装するために必要であるため|Scoreが重みへ変換される仕組みを説明できること|
|第4段階|Transformer|Attention|Self-Attention|文章内Token同士を関連付けるため。GPTの構造とSelf-Attentionの計算を理解・実装するために必要であるため|各Tokenが他Tokenを参照する仕組みを説明できること|
|第4段階|Transformer|Attention|Multi-Head Attention|複数の観点からToken関係を捉えるため。GPTの構造とSelf-Attentionの計算を理解・実装するために必要であるため|複数Headを使う意味を説明できること|
|第4段階|Transformer|Transformer構造|Feed Forward Network|Attention後の特徴変換を行うため。GPTの構造とSelf-Attentionの計算を理解・実装するために必要であるため|各Tokenへ同じMLPを適用する仕組みと、次元の拡張・縮小、GELU・SwiGLUの役割を説明できること|
|第4段階|Transformer|Transformer構造|Residual Connection|深いネットワークを安定して学習するため。GPTの構造とSelf-Attentionの計算を理解・実装するために必要であるため|Residual接続の意味を説明できること|
|第4段階|Transformer|Transformer構造|Layer Normalization|学習を安定化するため。GPTの構造とSelf-Attentionの計算を理解・実装するために必要であるため|正規化する軸を説明し、Pre-Norm・Post-Normの配置差とRMSNormとの違いを説明できること|
|第4段階|Transformer|Transformer構造|Transformer Block|LLMの基本構成単位を理解するため。GPTの構造とSelf-Attentionの計算を理解・実装するために必要であるため|Attention・FFN・Residual・Normの関係を説明できること|
|第4段階|Transformer|Transformer種類|Encoder|入力理解中心のTransformerを理解するため。GPTの構造とSelf-Attentionの計算を理解・実装するために必要であるため|Encoder構造の特徴を説明できること|
|第4段階|Transformer|Transformer種類|Transformer Decoder・GPT Decoder-only|GPTの中心構造を理解するため。GPTの構造とSelf-Attentionの計算を理解・実装するために必要であるため|原典Transformer DecoderのMasked Self-Attention・Cross-Attentionと、通常Cross-Attentionを持たないGPTのDecoder-only Blockを区別できること|
|第4段階|Transformer|Transformer種類|Encoder-Decoder|翻訳などの構造を理解するため。GPTの構造とSelf-Attentionの計算を理解・実装するために必要であるため|Encoder出力をDecoderがCross-Attentionで参照し、条件付き生成を行う流れを説明できること|
|第4段階|Transformer|NLP基礎|Special Token・Padding|長さの異なる系列をBatch化し、会話や文書の境界を表すため。TokenとVocabularyだけでは、実際のBatch入力や生成の開始・終了を表現する方法が不足している|BOS、EOS、PADなどの役割と、Paddingされた系列を同じ長さへそろえる方法を説明できること|
|第4段階|Transformer|Attention|Attention Mask|参照してよいTokenと参照してはいけないTokenを制御するため。Self-Attentionの参照範囲を制御する必須要素が既存項目に含まれていない|Padding MaskとCausal Maskの目的を区別し、Softmax前のScoreへ適用できること|
|第4段階|Transformer|Attention|Q・K・VのTensor形状|Batch、Head、系列長、Head次元を追跡してAttentionを実装するため。概念説明だけでは実装時の形状不一致を防げず、Multi-Head Attentionをコードへ落とせないため|Q・K・Vを複数Headへ分割・転置し、Attention出力を元の形状へ戻せること|
|第4段階|Transformer|Attention|Head結合・Output Projection|複数Headの出力を統合してモデル次元へ戻すため。Multi-Head Attentionの生成後に必要な統合処理が既存項目から抜けている|Headのconcatと出力射影Wₒの役割・形状を説明し、実装できること|
|第4段階|Transformer|Attention|双方向・因果Attention|目的に応じてTokenの参照方向を変えるため。EncoderとDecoderの違いを構造名だけでなく、情報参照可能範囲として理解する項目が不足している|Encoderの双方向AttentionとGPTの因果Attentionの参照範囲を比較・説明できること|
|第4段階|Transformer|Attention|Cross-Attention|別の系列が持つ情報を参照して出力を生成するため。Encoder-Decoder型を成立させる主要機構が既存項目に明示されていない|Decoder側の表現からQueryを作り、Encoder出力からKey・Valueを作る流れを説明できること|
|第4段階|Transformer|Embedding|RoPE・相対位置表現|Token間の相対的な位置関係をAttentionへ組み込むため。現代のDecoder-only LLMで広く使われる位置表現へ接続する具体項目が不足している|RoPEの目的と、絶対位置Embedding・相対位置方式との違いを概念的に説明できること|
|第4段階|Transformer|Transformer構造|Pre-Norm・Post-Norm|NormalizationをSub-layerの前後どちらへ置くかで学習特性が変わることを理解するため。LayerNormの名称だけではTransformer Block内での配置とResidualとの関係を理解できないため|両構成の計算順序を図示し、深いモデルの学習安定性との関係を説明できること|
|第4段階|Transformer|Transformer構造|RMSNorm|平均を引かず二乗平均平方根で正規化する方式を理解するため。現代的なLLM構造を読む際に頻出する正規化方式が既存項目にない|LayerNormとの計算上の違いと、現代LLMで採用される理由を概念的に説明できること|
|第4段階|Transformer|計算特性|Attentionの計算量・メモリ量|Context Lengthが計算資源へ与える影響を理解するため。長いContextが学習・推論コストを急増させる構造的理由を学ぶ項目が不足している|標準Self-Attentionが系列長に対して概ね二次で増える理由を説明できること|
|第4段階|Transformer|計算特性|効率的Attention・FlashAttention|Attentionの結果を保ちながらメモリアクセスや中間保存を効率化する考え方を理解するため。実用的なTransformer学習・推論で重要なAttention効率化への接続が不足している|FlashAttentionが近似ではなく計算順序とメモリ利用を改善する手法であることを説明できること|

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

[前の段階](03_第3段階_Neural_Network.md) ｜ [全体概要・目次](00_全体概要・目次.md) ｜ [次の段階](05_第5段階_Mini_GPT.md)
