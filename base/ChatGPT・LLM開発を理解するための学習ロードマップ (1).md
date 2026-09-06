# ChatGPT・LLM開発を理解するための学習ロードマップ

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

# 2. 学習段階の全体像

|段階|学習テーマ|最終的に理解するもの|
|:--|:--|:--|
|第1段階|最終段階までに必要な数学・プログラミング|AI・LLMを理解するために必要な数学と実装基礎|
|第2段階|機械学習基礎|AIが「学習する」とは何か|
|第3段階|Neural Network|Deep Learningがどのように学習するか|
|第4段階|Transformer|LLMの中核となる構造|
|第5段階|Mini GPT|GPTが文章を生成する仕組み|
|第6段階|Fine-tuning|既存LLMを目的に合わせて調整する方法|
|第7段階|ChatGPT型システム|LLMを実用的なAIサービスにする方法|
|最終段階|Pretraining / SFT / DPO / RLHF|LLMそのものを育てる一連の工程|

---

# 3. 学習項目一覧

|段階|学習テーマ|分野|項目|学習する理由|取得するべき内容|判断|判断理由|
|:--|:--|:--|:--|:--|:--|:--|:--|
|第1段階|プログラミング基礎|Python基礎|変数・型|AI実装の基本となるデータを扱うため|数値・文字列・真偽値などを適切に扱えること|維持|配列、Tensor、学習設定などを扱う前提であり、最初に習得する粒度として適切であるため|
|第1段階|プログラミング基礎|Python基礎|条件分岐|処理条件によって動作を変更するため|if文を使って条件に応じた処理を書けること|維持|データ前処理、学習条件、生成条件などの制御に不可欠であるため|
|第1段階|プログラミング基礎|Python基礎|繰り返し処理|大量のデータを反復処理するため|for・whileを使った反復処理ができること|維持|データ処理と学習ループを理解・実装する直接的な前提であるため|
|第1段階|プログラミング基礎|Python基礎|関数|処理を再利用可能な単位に分割するため|関数を定義して引数・戻り値を扱えること|維持|モデル処理やデータ処理を分割し、再利用可能にする基礎であるため|
|第1段階|プログラミング基礎|Python基礎|クラス|PyTorchなどのモデル構造を理解するため|クラス・インスタンス・継承の基本を理解できること|維持|PyTorchのnn.Moduleを継承したモデル実装に直接必要であるため|
|第1段階|プログラミング基礎|データ構造|list|学習データや処理結果をまとめて扱うため|リストの追加・削除・検索・反復ができること|維持|データセット、Token列、評価結果などを扱う基本構造であるため|
|第1段階|プログラミング基礎|データ構造|dict|設定値や構造化データを扱うため|キーと値によるデータ管理ができること|維持|モデル設定、学習データ、APIのJSON表現などで頻繁に使うため|
|第1段階|プログラミング基礎|NumPy|配列|数値計算の基本単位を理解するため|NumPy配列を生成・操作できること|維持|Tensorを学ぶ前に多次元配列と形状の概念を体験する基礎として有効であるため|
|第1段階|プログラミング基礎|NumPy|ベクトル演算|機械学習で大量の数値を効率よく計算するため|ベクトルの加減算・積などを実装できること|修正|「積」が要素積、スカラー倍、内積のどれを指すか曖昧なため、それぞれを区別する習得内容へ具体化する必要がある|
|第1段階|プログラミング基礎|NumPy|行列演算|ニューラルネットの中心処理を理解するため|行列積や転置をコードで実行できること|維持|Linear層とAttentionの主要計算をコードで理解する前提になるため|
|第1段階|プログラミング基礎|開発環境|Jupyter Notebook|AI実験を対話的に行うため|Notebook上でコード・結果・説明を管理できること|維持|計算結果を確認しながら数学と実装を対応付ける学習環境として適切であるため|
|第1段階|プログラミング基礎|開発環境|pip・仮想環境|ライブラリ依存関係を管理するため|Python環境を分離してライブラリを導入できること|維持|PyTorchや周辺ライブラリのバージョン競合を避け、再現可能な環境を作るために必要である|
|第1段階|プログラミング基礎|開発管理|Git|実験やソースコードの変更履歴を管理するため|commit・branch・mergeの基本操作ができること|修正|ローカル履歴だけでなく、clone、add、status、push、pullを含む一連の基本操作まで習得対象にする必要がある|
|第1段階|数学基礎|線形代数|スカラー|ベクトルや行列の構成要素を理解するため|単一数値とベクトル・行列の違いを説明できること|維持|Tensorの階数や形状を理解する出発点として必要であるため|
|第1段階|数学基礎|線形代数|ベクトル|単語や特徴量が数値列として表現されるため|ベクトルの意味と基本演算を理解できること|維持|Embedding、重み、勾配を理解する基本単位であるため|
|第1段階|数学基礎|線形代数|行列|ニューラルネットの重み計算に使われるため|行列の形状と演算の意味を説明できること|維持|Linear層とAttentionを形状を含めて理解するために不可欠である|
|第1段階|数学基礎|線形代数|テンソル|Deep Learningでは多次元配列を扱うため|スカラー・ベクトル・行列・テンソルの関係を説明できること|維持|Batch、系列長、Headなど複数軸を持つLLMのデータ表現に直接つながるため|
|第1段階|数学基礎|線形代数|内積|Attentionや類似度計算の基礎となるため|2つのベクトルの内積と意味を説明できること|維持|Attention Scoreとベクトル類似度を理解する中核的な前提であるため|
|第1段階|数学基礎|線形代数|行列積|ニューラルネットとTransformerの主要計算だから|行列積を手計算・コードの両方で扱えること|維持|ニューラルネットとTransformerの計算を形状付きで追跡するために不可欠である|
|第1段階|数学基礎|線形代数|転置|AttentionのQKᵀなどで必要になるため|転置による行列形状の変化を理解できること|維持|QKᵀの計算と行列形状の整合性を理解するために直接必要である|
|第1段階|数学基礎|線形代数|ノルム|ベクトルの大きさや正規化を理解するため|代表的なノルムの意味を説明できること|修正|L1・L2ノルムを具体化し、ベクトルの正規化とLayer Normalizationを混同しない習得内容にする必要がある|
|第1段階|数学基礎|線形代数|線形変換|ニューラルネットのLinear層を理解するため|行列が入力ベクトルを変換する意味を説明できること|維持|重み行列が特徴表現を別の空間へ写す意味を理解するために必要である|
|第1段階|数学基礎|線形代数|固有値・固有ベクトル|高度な線形代数や次元解析の理解に役立つため|固有値・固有ベクトルの概念を説明できること|削除|本ロードマップで扱うNeural Network、Transformer、GPTの必須理解に直接つながらず、第1段階の負荷を増やすため。発展学習へ移すのが適切である|
|第1段階|数学基礎|微積分|関数|モデルを入力から出力への写像として理解するため|関数の入力・出力関係を説明できること|維持|モデル、損失関数、活性化関数を共通の枠組みで捉える前提になるため|
|第1段階|数学基礎|微積分|微分|誤差を減らす方向を求めるため|微分が変化率を表すことを理解できること|維持|最適化とBackpropagationを理解する最小限の数学であるため|
|第1段階|数学基礎|微積分|偏微分|多数のパラメータを持つモデルを最適化するため|複数変数に対する微分を理解できること|維持|多数の重みを個別に更新する仕組みを理解するために必要である|
|第1段階|数学基礎|微積分|連鎖律|Backpropagationの数学的基礎だから|合成関数の微分を理解できること|維持|層をまたいで勾配を伝えるBackpropagationの中心原理であるため|
|第1段階|数学基礎|微積分|勾配|モデルパラメータの更新方向を求めるため|Gradientの意味を説明できること|維持|Gradient Descentとパラメータ更新をベクトルとして理解するために不可欠である|
|第1段階|数学基礎|確率・統計|確率|LLMが次Tokenの確率を出力するため|基本的な確率計算ができること|維持|次Token確率と生成結果の不確実性を理解する出発点になるため|
|第1段階|数学基礎|確率・統計|条件付き確率|ある条件下での出力確率を理解するため|条件付き確率を説明できること|維持|文脈を条件とした次Token確率という言語モデルの定義に直結するため|
|第1段階|数学基礎|確率・統計|確率分布|LLM出力がTokenごとの確率分布だから|確率分布の意味を説明できること|維持|Softmax出力、Sampling、Temperatureを理解する前提になるため|
|第1段階|数学基礎|確率・統計|期待値|確率的結果の平均的性質を理解するため|期待値を計算・説明できること|維持|損失や報酬の平均的な振る舞いを理解するために必要である|
|第1段階|数学基礎|確率・統計|分散・標準偏差|データのばらつきを評価するため|分散・標準偏差を計算できること|維持|データ分布、初期化、正規化の考え方を理解する基礎になるため|
|第1段階|数学基礎|確率・統計|最尤推定|機械学習の学習原理と関係するため|尤度を最大化する考え方を説明できること|維持|正解Tokenの確率を高める言語モデル学習を統計的に説明するために必要である|
|第1段階|数学基礎|確率・統計|対数尤度|Cross EntropyやLanguage Modelingを理解するため|対数尤度の意味を説明できること|維持|確率の積を和へ変換し、負の対数尤度とCross Entropyを結び付けるために必要である|
|第1段階|数学基礎|確率・統計|サンプリング|LLMの文章生成方式を理解するため|確率分布から値を選択する意味を説明できること|維持|確率分布からTokenを選ぶ生成処理を理解する直接的な前提であるため|
|第1段階|プログラミング基礎|Python基礎|モジュール・パッケージ・import|複数ファイルや外部ライブラリを組み合わせて実装するため|標準・外部・自作モジュールをimportし、コードを適切に分割できること|追加|PyTorchやHugging Faceを利用し、自作コードを複数ファイルへ分割するための必須操作が不足している|
|第1段階|プログラミング基礎|データ入出力|ファイル・JSON・CSV|学習データ、設定、評価結果を読み書きするため|テキスト、JSON、CSVを読み込み、必要な形式へ変換して保存できること|追加|後続のDataset作成、API連携、評価結果の保存に共通して必要だが既存項目に含まれていない|
|第1段階|プログラミング基礎|Python基礎|例外処理|データや外部処理の失敗を検知し、安全に対処するため|try・exceptを使い、想定される例外を処理できること|追加|データ処理、API、学習処理のエラー原因を把握し、処理を安全に停止・継続する基礎が不足している|
|第1段階|プログラミング基礎|NumPy|形状・軸・Indexing・Broadcasting|Tensor計算の形状を追跡し、効率的に配列を操作するため|shape、axis、slicing、reshape、broadcastingを説明・実装できること|追加|LLM実装で頻発する次元不一致を防ぎ、Batch・系列長・特徴量の各軸を理解する項目が不足している|
|第1段階|プログラミング基礎|開発環境|コマンドライン・Linux基礎|学習スクリプト、環境構築、GPU環境を操作するため|パス移動、ファイル操作、コマンド実行、環境変数の基本を扱えること|追加|クラウドGPUや多くの機械学習開発環境はLinuxのコマンドライン操作を前提とするため|
|第1段階|プログラミング基礎|開発品質|デバッグ|実装ミスや形状不一致の原因を特定するため|エラーメッセージ、ログ、ブレークポイント、shape確認を使って原因を切り分けられること|追加|モデル実装では構文理解だけでなく、計算途中の値と形状を追う能力が不可欠であるため|
|第1段階|プログラミング基礎|開発品質|基本的なテスト|前処理や数値計算の期待動作を継続的に確認するため|小さな入力例とassertを使い、関数の入出力を検証できること|追加|Tokenizer、データ変換、モデル部品を段階的に実装する際の検証方法が不足している|
|第1段階|数学基礎|基礎数学|指数・対数|Softmax、対数尤度、Cross Entropyの式を理解するため|指数法則と対数法則を使い、確率計算との関係を説明できること|追加|既存の対数尤度を理解する前提となる指数・対数そのものが明示されていない|
|第1段階|数学基礎|数式読解|総和記号・添字・ベクトル表記|論文や実装資料の数式を処理単位へ分解して読むため|Σ、添字、ベクトル・行列の表記を具体的な計算へ置き換えられること|追加|数学概念が列挙されていても、Transformerや損失関数の式を読むための表記法が不足している|
|第1段階|数学基礎|情報理論|エントロピー・KLダイバージェンス|予測の不確実性と確率分布間の差を理解するため|エントロピーとKLダイバージェンスの意味を説明し、簡単な分布で計算できること|追加|Cross Entropy、DPO、RLHFのKL Penaltyを一貫して理解する数学的前提が不足している|
|第1段階|数学基礎|数値計算|浮動小数点と数値安定性|Softmaxや学習時の桁あふれ・丸め誤差を理解するため|浮動小数点の有限精度と、最大値減算など基本的な安定化の理由を説明できること|追加|実装結果が数式どおりにならない代表的原因を理解する項目がなく、後のMixed Precisionにもつながるため|
|第2段階|機械学習基礎|機械学習概論|AI・機械学習・Deep Learning|各技術の包含関係を理解するため|AI・ML・DLの違いを説明できること|維持|後続の技術を包含関係と役割の違いから整理する出発点として適切であるため|
|第2段階|機械学習基礎|学習方式|教師あり学習|LLM以前の基本的な学習概念を理解するため|入力と正解データから学習する仕組みを説明できること|維持|入力、正解、損失を用いる基本的な学習サイクルを理解するために必要である|
|第2段階|機械学習基礎|学習方式|教師なし学習|ラベルなしデータから構造を学習する方法を理解するため|教師なし学習の目的を説明できること|修正|LLMの事前学習で中心となる自己教師あり学習と混同しやすいため、両者の違いを明示する必要がある|
|第2段階|機械学習基礎|学習方式|強化学習|後のRLHFを理解する基礎となるため|状態・行動・報酬の関係を説明できること|維持|最終段階のRLHFで用いる状態、行動、方策、報酬の基礎に直接つながるため|
|第2段階|機械学習基礎|回帰|線形回帰|最も基本的な予測モデルから学習原理を理解するため|線形モデルの学習・予測ができること|維持|予測、損失、勾配、更新という一連の学習を最小構成で実装できるため|
|第2段階|機械学習基礎|分類|ロジスティック回帰|分類と確率出力を理解するため|二値分類モデルを構築できること|維持|分類スコアを確率へ変換し、交差エントロピーで学習する基礎として有効である|
|第2段階|機械学習基礎|分類|多クラス分類|複数候補から1つを選ぶ問題を理解するため|多クラス分類の考え方を説明できること|維持|語彙中の多数のToken候補から次Tokenを選ぶ問題へつながるため|
|第2段階|機械学習基礎|損失関数|MSE|予測誤差を数値化する基本を学ぶため|平均二乗誤差の意味を説明できること|維持|損失関数と最適化の関係を回帰問題で直感的に理解するために適切である|
|第2段階|機械学習基礎|損失関数|Cross Entropy|LLM学習で中心的に使われるため|Cross Entropyの意味を説明できること|維持|分類と次Token予測の中心的な損失であり、LLM学習へ直接つながるため|
|第2段階|機械学習基礎|損失関数|Negative Log Likelihood|言語モデルの確率的学習を理解するため|正解データの確率を高める学習との関係を説明できること|修正|Cross Entropyとの重複に見えるため、正解分布がone-hotの場合の関係と、入力が確率か対数確率かを明示する必要がある|
|第2段階|機械学習基礎|最適化|Gradient Descent|学習時のパラメータ更新原理を理解するため|勾配降下法を説明・実装できること|維持|勾配の反対方向へ重みを更新するという機械学習の基本原理であるため|
|第2段階|機械学習基礎|最適化|SGD|Deep Learningの基本的な最適化法だから|ミニバッチを使った更新を理解できること|修正|厳密な確率的勾配降下法は1標本更新を指す一方、実務ではミニバッチSGDを指すことが多いため、両者を区別する必要がある|
|第2段階|機械学習基礎|最適化|Momentum|勾配降下を安定・高速化する方法を理解するため|Momentumの役割を説明できること|維持|過去の更新方向を蓄積する考え方がAdamの一次モーメント推定の理解につながるため|
|第2段階|機械学習基礎|最適化|Adam|Deep Learningで広く利用されるため|Adamの特徴を説明できること|維持|勾配の一次・二次モーメントを利用する代表的な最適化法として必要である|
|第2段階|機械学習基礎|最適化|AdamW|Transformer・LLMで標準的に利用されるため|AdamとAdamWの違いを理解できること|維持|Weight Decayを勾配更新から分離するLLM学習の標準的な考え方を理解するために必要である|
|第2段階|機械学習基礎|最適化|Learning Rate|学習速度と安定性を左右するため|学習率変更の影響を説明できること|維持|値が大きすぎる場合の発散と小さすぎる場合の停滞を含め、学習挙動を判断する中心要素であるため|
|第2段階|機械学習基礎|評価|Train・Validation・Test|学習と評価を適切に分離するため|データセット分割の目的を説明できること|維持|未知データへの汎化性能を正しく測り、調整用データと最終評価データを分離するために不可欠である|
|第2段階|機械学習基礎|評価|Accuracy|分類性能を評価するため|Accuracyを計算できること|維持|分類評価の基準となり、クラス不均衡時の限界も理解する土台になるため|
|第2段階|機械学習基礎|評価|Precision|誤検出を重視する評価を理解するため|Precisionの意味を説明できること|維持|偽陽性の影響が大きいタスクで評価指標を選ぶために必要である|
|第2段階|機械学習基礎|評価|Recall|見逃しを重視する評価を理解するため|Recallの意味を説明できること|維持|偽陰性の影響が大きいタスクで評価指標を選ぶために必要である|
|第2段階|機械学習基礎|評価|F1 Score|PrecisionとRecallを統合して評価するため|F1 Scoreの意味を説明できること|維持|PrecisionとRecallの均衡を単一指標で比較する基本として適切である|
|第2段階|機械学習基礎|汎化|Overfitting|訓練データへの過適合を理解するため|過学習を発見し対策を考えられること|維持|訓練損失だけではモデル品質を判断できない理由を理解するために不可欠である|
|第2段階|機械学習基礎|汎化|Underfitting|モデル能力不足を理解するため|未学習状態の原因を説明できること|修正|Underfittingは単なる未学習ではなく、モデル容量不足、特徴不足、正則化過多、学習不足などで訓練データにも適合できない状態として説明する必要がある|
|第2段階|機械学習基礎|汎化|Bias・Variance|モデル誤差の性質を理解するため|Bias-Varianceの考え方を説明できること|維持|UnderfittingとOverfittingを統一的に捉え、モデル容量やデータ量の影響を考えるために有効である|
|第2段階|機械学習基礎|学習要素|特徴量・ラベル|モデルへ与える入力と正解情報を区別するため|特徴量、目的変数、ラベルの役割を説明し、データを入力と正解へ分けられること|追加|教師あり学習、回帰、分類を学ぶ前提となる用語とデータ構造が既存項目に明示されていない|
|第2段階|機械学習基礎|モデル基礎|パラメータ・ハイパーパラメータ|学習で更新される値と人が設定する値を区別するため|重み・バイアスと、学習率・Batch Sizeなどの違いを説明できること|追加|学習対象と学習条件を混同すると、最適化や実験結果を正しく解釈できないため|
|第2段階|機械学習基礎|学習方式|自己教師あり学習|ラベルを人手で付けず、データ自身から学習目標を作る仕組みを理解するため|入力の一部から正解を生成する考え方と、教師なし学習との違いを説明できること|追加|GPTのNext Token PredictionによるPretrainingを理解する中心概念が不足している|
|第2段階|機械学習基礎|データ前処理|標準化・正規化|特徴量の尺度をそろえ、学習を安定させるため|標準化とMin-Max正規化の違いを説明し、訓練データの統計量を使って変換できること|追加|数値特徴量の尺度が最適化へ与える影響と、Validation・Testへの正しい適用方法を学ぶ項目が不足している|
|第2段階|機械学習基礎|損失関数|損失関数・評価指標の違い|学習の最適化対象と、モデル品質の判断基準を区別するため|LossとMetricが一致しない場合を説明し、目的に応じて使い分けられること|追加|AccuracyやF1を学習時のLossと混同しないための整理が必要である|
|第2段階|機械学習基礎|評価|Baseline|複雑なモデルの改善効果を比較可能にするため|単純な規則、平均予測、多数派予測などのBaselineを設定できること|追加|比較対象がなければモデルの性能向上や実装の妥当性を判断できないため|
|第2段階|機械学習基礎|評価|混同行列|分類結果を正解・誤りの種類に分けて理解するため|TP、FP、FN、TNを求め、Accuracy、Precision、Recallとの関係を説明できること|追加|既存の分類指標を暗記ではなく一貫した構造として理解する項目が不足している|
|第2段階|機械学習基礎|評価|Data Leakage|評価に使う情報が学習へ混入する問題を防ぐため|前処理、特徴量作成、データ分割で起きるLeakageを発見・回避できること|追加|見かけ上高い評価値を出す代表的な失敗を防ぎ、後のBenchmark Contamination理解にもつながるため|
|第2段階|機械学習基礎|汎化|正則化・Weight Decay|モデルの複雑さを抑えて汎化性能を高めるため|L1・L2正則化とWeight Decayの目的を説明し、簡単なモデルへ適用できること|追加|Overfittingへの主要な対策であり、既存のAdamWを正しく理解する前提も不足している|
|第2段階|機械学習基礎|汎化|Early Stopping|Validation性能の悪化を検知して過学習を抑えるため|監視指標、patience、最良Checkpointの保存を設定できること|追加|Overfittingを発見した後に取る代表的な実践手段が既存項目にない|
|第2段階|機械学習基礎|実験管理|再現性・Random Seed|実験条件をそろえ、結果を比較できるようにするため|乱数Seed、データ分割、設定値を記録し、再実行可能な実験を構成できること|追加|初期値やデータ順による変動を考慮しないと、手法間の差を正しく判断できないため|
|第2段階|機械学習基礎|実験管理|ハイパーパラメータ調整|学習率や正則化強度などをValidation結果に基づいて選ぶため|探索対象と評価基準を定め、Testデータを使わずに設定を比較できること|追加|モデル選択と最終評価を分離し、恣意的な調整やTestデータへの過適合を防ぐ項目が不足している|
|第3段階|Neural Network|ニューラルネット基礎|Neuron|ニューラルネットの最小構成単位を理解するため|入力・重み・バイアス・出力の関係を説明できること|維持|線形変換と活性化関数を最小単位で捉え、層構造へつなげる導入として適切であるため|
|第3段階|Neural Network|ニューラルネット基礎|Weight|モデルが学習する対象を理解するため|Weightが入力へ与える影響を説明できること|維持|学習によって更新される主要パラメータであり、線形変換と特徴抽出を理解する前提であるため|
|第3段階|Neural Network|ニューラルネット基礎|Bias|線形変換の自由度を高めるため|Biasの役割を説明できること|維持|入力がゼロの場合も出力を調整できる理由とAffine変換を理解するために必要である|
|第3段階|Neural Network|ニューラルネット基礎|Layer|複数段階の特徴変換を理解するため|Input・Hidden・Output Layerを説明できること|維持|モデルを入力層、隠れ層、出力層の組合せとして把握する基本概念であるため|
|第3段階|Neural Network|活性化関数|Sigmoid|非線形性の基本を理解するため|Sigmoidの特徴を説明できること|維持|二値分類の確率出力と、LLMのGated構造で使われる制御の考え方につながるため|
|第3段階|Neural Network|活性化関数|Tanh|代表的な非線形関数を理解するため|TanhとSigmoidの違いを説明できること|削除|本ロードマップの中心であるTransformer・GPTの必須理解には直接つながらず、Sigmoid、ReLU、GELU、SiLUで必要な比較を行えるため。RNNの発展学習へ移すのが適切である|
|第3段階|Neural Network|活性化関数|ReLU|Deep Learningで広く使われるため|ReLUの特徴と問題点を説明できること|維持|非線形性、勾配消失の緩和、Dead ReLUを通じて活性化関数の役割を理解しやすいため|
|第3段階|Neural Network|活性化関数|GELU|Transformerで利用されるため|GELUの特徴を説明できること|維持|GPT系TransformerのFeed Forward Networkで採用される代表的な活性化関数であるため|
|第3段階|Neural Network|活性化関数|SiLU|現代LLMでも利用されるため|SiLUの特徴を説明できること|維持|SwiGLUなど現代的なLLMのGated FFNを理解する前提になるため|
|第3段階|Neural Network|学習処理|Forward Propagation|入力から予測を生成する流れを理解するため|Forward処理を数式・コードで追跡できること|維持|入力から予測とLossまでの計算を追跡する、学習処理の前半として不可欠である|
|第3段階|Neural Network|学習処理|Computational Graph|複雑な計算と微分の依存関係を理解するため|計算グラフを追えること|維持|Forwardの各演算とBackwardの微分経路を対応付けるために必要である|
|第3段階|Neural Network|学習処理|Backpropagation|ニューラルネット学習の中心原理だから|誤差が各パラメータへ伝播する仕組みを説明できること|維持|連鎖律によって各パラメータの勾配を求めるニューラルネット学習の中心原理であるため|
|第3段階|Neural Network|学習処理|Automatic Differentiation|PyTorchの自動微分を理解するため|autogradが何をしているか説明できること|維持|手計算のBackpropagationとPyTorchによる勾配計算を結び付けるために必要である|
|第3段階|Neural Network|PyTorch|Tensor|PyTorchの基本データ構造だから|Tensorの生成・形状変更・演算ができること|修正|生成・形状・演算だけでなく、dtype、device、requires_grad、detachを含めないと学習コードを正しく理解できないため|
|第3段階|Neural Network|PyTorch|nn.Module|モデルを構築する基本クラスだから|独自モデルクラスを実装できること|維持|層とパラメータを登録し、forwardを定義するPyTorchモデル実装の中心であるため|
|第3段階|Neural Network|PyTorch|nn.Linear|ニューラルネットの線形変換を実装するため|全結合層を利用・説明できること|維持|ニューラルネットとTransformerの射影層を構成する基本部品であるため|
|第3段階|Neural Network|PyTorch|loss.backward|Backpropagationを実行するため|勾配計算の流れを理解できること|維持|計算グラフを逆向きにたどり、各Parameterのgradへ勾配を蓄積する処理を理解するために必要である|
|第3段階|Neural Network|PyTorch|optimizer.step|モデルパラメータを更新するため|1回の学習ステップを実装できること|修正|optimizer.stepだけでは勾配初期化、Forward、Loss、Backwardとの実行順序が分からないため、1学習Step全体の中で説明する必要がある|
|第3段階|Neural Network|学習技法|Batch|複数データを効率的に学習するため|Batch Sizeの役割を説明できること|修正|計算効率だけでなく、勾配推定のばらつき、メモリ使用量、学習率との関係まで含める必要がある|
|第3段階|Neural Network|学習技法|Epoch|データセットを何回学習したか管理するため|EpochとIterationの違いを説明できること|維持|学習量を表す基本単位であり、Batch、Iteration、学習履歴を対応付けるために必要である|
|第3段階|Neural Network|学習技法|Weight Initialization|学習の安定性を高めるため|初期値が学習へ与える影響を理解できること|修正|初期値の影響だけでなく、対称性の回避とXavier・He初期化を活性化関数に応じて使い分ける内容が必要である|
|第3段階|Neural Network|学習技法|Normalization|学習を安定させるため|Normalizationの目的を説明できること|修正|データの正規化、BatchNorm、LayerNorm、RMSNormは対象軸と目的が異なるため、Transformerで使う方式を区別する必要がある|
|第3段階|Neural Network|学習技法|Dropout|過学習を抑制するため|Dropoutの仕組みを説明できること|維持|学習時と推論時の動作差を含む代表的な正則化手法として必要である|
|第3段階|Neural Network|学習技法|Gradient Clipping|勾配爆発を抑えるため|勾配を制限する理由を説明できること|維持|深いモデルの学習安定化と大きな勾配への実践的対策を理解するために有効である|
|第3段階|Neural Network|ニューラルネット基礎|Multi-Layer Perceptron|複数のLinear層と活性化関数を組み合わせる基本モデルを理解するため|MLPを数式とPyTorchの両方で構築し、非線形な関係を学習させられること|追加|個々のNeuronとLayerから、実際に学習可能なネットワークへ組み立てる中間概念が不足している|
|第3段階|Neural Network|活性化関数|Softmax|複数のスコアを確率分布へ変換するため|Softmaxの出力が合計1になることと、Logit・確率・Cross Entropyの関係を説明できること|追加|多クラス分類と次Token予測をニューラルネットの出力層へ接続する項目が不足している|
|第3段階|Neural Network|活性化関数|Gated Linear Unit・SwiGLU|情報を通す量を学習可能なGateで制御するため|GLUの基本構造と、SiLUを使うSwiGLUがLLMのFFNで果たす役割を説明できること|追加|SiLU単体から現代LLMで一般的なGated FFNへつなぐ項目が不足している|
|第3段階|Neural Network|学習処理|勾配消失・勾配爆発|深いネットワークで学習が不安定になる原因を理解するため|層をまたぐ勾配が小さくなる・大きくなる条件と代表的な対策を説明できること|追加|活性化関数、初期化、Normalization、Residual、Gradient Clippingの必要性を統合して理解する項目がない|
|第3段階|Neural Network|PyTorch|nn.Parameter・パラメータ登録|Optimizerが更新するTensorをモデルへ登録する仕組みを理解するため|nn.Parameter、parameters、state_dictの関係を説明し、学習対象を確認できること|追加|通常のTensorと学習対象Parameterの違いが既存項目に含まれていない|
|第3段階|Neural Network|PyTorch|Dataset・DataLoader|データをBatch単位で学習処理へ供給するため|Datasetを定義し、DataLoaderでBatch化・Shuffleして反復できること|追加|簡単なモデルを実際のデータで学習させる入出力パイプラインが不足している|
|第3段階|Neural Network|PyTorch|optimizer.zero_grad|前回の勾配を意図せず次の更新へ加算しないため|PyTorchでは勾配が蓄積されることを説明し、適切な位置で勾配を初期化できること|追加|loss.backwardとoptimizer.stepの間を正しく構成するための必須操作が既存項目にない|
|第3段階|Neural Network|PyTorch|Device・dtype管理|CPU・GPUと数値精度を意識してTensorとモデルを配置するため|モデルとTensorを同じdeviceへ移し、用途に応じたdtypeを確認・設定できること|追加|GPU学習時のdevice不一致やdtype不一致を防ぐ基本操作が不足している|
|第3段階|Neural Network|PyTorch|train・eval・推論モード|学習時と評価時でDropoutなどの動作を正しく切り替えるため|model.train、model.eval、no_gradまたはinference_modeを適切に使えること|追加|学習結果を正しく評価・推論するために必要なモード切替が既存項目にない|
|第3段階|Neural Network|PyTorch|Training Loop|データ取得からパラメータ更新までを一続きで実装するため|Batch取得、Forward、Loss、zero_grad、Backward、stepを正しい順序で実装できること|追加|個別APIは列挙されているが、簡単なニューラルネットを学習させる全体手順が明示されていない|
|第3段階|Neural Network|PyTorch|state_dict・モデル保存|学習済みモデルを保存し、評価や再学習に利用するため|モデルとOptimizerのstate_dictを保存・読み込みできること|追加|実験の継続、最良モデルの評価、後続段階のCheckpoint理解に必要な基本操作が不足している|
|第4段階|Transformer|NLP基礎|Token|文章をモデルが扱う単位へ分解するため|Tokenの意味を説明できること|維持|文字列とモデル内部の離散的な入力単位を結び付ける基本概念であるため|
|第4段階|Transformer|NLP基礎|Vocabulary|モデルが扱えるToken集合を理解するため|Vocabulary Sizeの意味を説明できること|維持|Embedding行列と出力層の大きさ、未知語や分割粒度との関係を理解するために必要である|
|第4段階|Transformer|NLP基礎|Tokenization|文字列を数値列へ変換するため|文章からToken IDへの変換を説明できること|維持|自然言語をEmbeddingへ入力できるToken ID列へ変換する入口として不可欠である|
|第4段階|Transformer|Embedding|Token Embedding|Tokenをベクトルへ変換するため|Embedding層の役割を説明できること|維持|離散的なToken IDを学習可能な連続ベクトルへ変換する中核処理であるため|
|第4段階|Transformer|Embedding|Positional Encoding|Transformerに単語順序を与えるため|位置情報が必要な理由を説明できること|修正|正弦波方式だけでなく、学習可能な絶対位置、相対位置、RoPEなど複数方式と外挿特性を区別する必要がある|
|第4段階|Transformer|Attention|Query|参照したい情報を表現するため|Queryの役割を説明できること|維持|各Tokenが何を探すかを表す射影としてAttentionの意味を理解するために必要である|
|第4段階|Transformer|Attention|Key|参照対象の特徴を表現するため|Keyの役割を説明できること|維持|Queryと照合される索引表現としてAttention Scoreの計算に不可欠である|
|第4段階|Transformer|Attention|Value|実際に取り出す情報を表現するため|Valueの役割を説明できること|維持|Attention重みに基づいて集約される内容表現として出力計算を理解するために必要である|
|第4段階|Transformer|Attention|Dot Product|QueryとKeyの関連度を計算するため|内積と関連度の関係を説明できること|削除|内積は第1段階ですでに扱い、この段階ではScaled Dot-Product Attentionの内部計算として学べるため、単独行は重複になる|
|第4段階|Transformer|Attention|Scaled Dot-Product Attention|Attentionの中心計算を理解するため|Attention(Q,K,V)を説明できること|維持|QKᵀ、スケーリング、Mask、Softmax、Vの重み付き和を一連の式として理解する中核項目であるため|
|第4段階|Transformer|Attention|Softmax|Attention Scoreを重みへ変換するため|Scoreが重みへ変換される仕組みを説明できること|維持|ScoreをToken間で比較可能な重みへ変換し、Vを加重平均する仕組みに直接必要である|
|第4段階|Transformer|Attention|Self-Attention|文章内Token同士を関連付けるため|各Tokenが他Tokenを参照する仕組みを説明できること|維持|同一系列からQ・K・Vを作り、文脈依存表現を生成するTransformerの中心機構であるため|
|第4段階|Transformer|Attention|Multi-Head Attention|複数の観点からToken関係を捉えるため|複数Headを使う意味を説明できること|維持|表現空間をHeadごとに分割し、異なる関係を並列に捉える仕組みを理解するために必要である|
|第4段階|Transformer|Transformer構造|Feed Forward Network|Attention後の特徴変換を行うため|FFNの役割を説明できること|修正|単なるAttention後処理ではなく、Tokenごとに同じMLPを適用すること、次元拡張・縮小、GELUやSwiGLUを含めて説明する必要がある|
|第4段階|Transformer|Transformer構造|Residual Connection|深いネットワークを安定して学習するため|Residual接続の意味を説明できること|維持|元の表現を各Sub-layerの出力へ加え、情報と勾配の経路を保つために不可欠である|
|第4段階|Transformer|Transformer構造|Layer Normalization|学習を安定化するため|LayerNormの役割を説明できること|修正|正規化する軸を明示し、Pre-Norm・Post-Normの配置差と現代LLMで多いRMSNormとの違いまで扱う必要がある|
|第4段階|Transformer|Transformer構造|Transformer Block|LLMの基本構成単位を理解するため|Attention・FFN・Residual・Normの関係を説明できること|維持|主要部品を一つの反復可能なBlockとして統合し、層を積み重ねる構造を理解する到達点として適切である|
|第4段階|Transformer|Transformer種類|Encoder|入力理解中心のTransformerを理解するため|Encoder構造の特徴を説明できること|維持|双方向Self-Attentionを使う表現学習とDecoder系モデルとの違いを理解するために必要である|
|第4段階|Transformer|Transformer種類|Decoder|GPTの中心構造を理解するため|Decoder構造の特徴を説明できること|修正|原典TransformerのDecoderはMasked Self-AttentionとCross-Attentionを持つ一方、GPTのDecoder-only Blockは通常Cross-Attentionを持たないため、両者を区別する必要がある|
|第4段階|Transformer|Transformer種類|Encoder-Decoder|翻訳などの構造を理解するため|Encoder-Decoder型との違いを説明できること|修正|「違い」だけでは曖昧なため、Encoder出力をDecoderがCross-Attentionで参照して条件付き生成する流れまで習得内容に含める必要がある|
|第4段階|Transformer|NLP基礎|Special Token・Padding|長さの異なる系列をBatch化し、会話や文書の境界を表すため|BOS、EOS、PADなどの役割と、Paddingされた系列を同じ長さへそろえる方法を説明できること|追加|TokenとVocabularyだけでは、実際のBatch入力や生成の開始・終了を表現する方法が不足している|
|第4段階|Transformer|Attention|Attention Mask|参照してよいTokenと参照してはいけないTokenを制御するため|Padding MaskとCausal Maskの目的を区別し、Softmax前のScoreへ適用できること|追加|Self-Attentionの参照範囲を制御する必須要素が既存項目に含まれていない|
|第4段階|Transformer|Attention|Q・K・VのTensor形状|Batch、Head、系列長、Head次元を追跡してAttentionを実装するため|Q・K・Vを複数Headへ分割・転置し、Attention出力を元の形状へ戻せること|追加|概念説明だけでは実装時の形状不一致を防げず、Multi-Head Attentionをコードへ落とせないため|
|第4段階|Transformer|Attention|Head結合・Output Projection|複数Headの出力を統合してモデル次元へ戻すため|Headのconcatと出力射影Wₒの役割・形状を説明し、実装できること|追加|Multi-Head Attentionの生成後に必要な統合処理が既存項目から抜けている|
|第4段階|Transformer|Attention|双方向・因果Attention|目的に応じてTokenの参照方向を変えるため|Encoderの双方向AttentionとGPTの因果Attentionの参照範囲を比較・説明できること|追加|EncoderとDecoderの違いを構造名だけでなく、情報参照可能範囲として理解する項目が不足している|
|第4段階|Transformer|Attention|Cross-Attention|別の系列が持つ情報を参照して出力を生成するため|Decoder側の表現からQueryを作り、Encoder出力からKey・Valueを作る流れを説明できること|追加|Encoder-Decoder型を成立させる主要機構が既存項目に明示されていない|
|第4段階|Transformer|Embedding|RoPE・相対位置表現|Token間の相対的な位置関係をAttentionへ組み込むため|RoPEの目的と、絶対位置Embedding・相対位置方式との違いを概念的に説明できること|追加|現代のDecoder-only LLMで広く使われる位置表現へ接続する具体項目が不足している|
|第4段階|Transformer|Transformer構造|Pre-Norm・Post-Norm|NormalizationをSub-layerの前後どちらへ置くかで学習特性が変わることを理解するため|両構成の計算順序を図示し、深いモデルの学習安定性との関係を説明できること|追加|LayerNormの名称だけではTransformer Block内での配置とResidualとの関係を理解できないため|
|第4段階|Transformer|Transformer構造|RMSNorm|平均を引かず二乗平均平方根で正規化する方式を理解するため|LayerNormとの計算上の違いと、現代LLMで採用される理由を概念的に説明できること|追加|現代的なLLM構造を読む際に頻出する正規化方式が既存項目にない|
|第4段階|Transformer|計算特性|Attentionの計算量・メモリ量|Context Lengthが計算資源へ与える影響を理解するため|標準Self-Attentionが系列長に対して概ね二次で増える理由を説明できること|追加|長いContextが学習・推論コストを急増させる構造的理由を学ぶ項目が不足している|
|第4段階|Transformer|計算特性|効率的Attention・FlashAttention|Attentionの結果を保ちながらメモリアクセスや中間保存を効率化する考え方を理解するため|FlashAttentionが近似ではなく計算順序とメモリ利用を改善する手法であることを説明できること|追加|実用的なTransformer学習・推論で重要なAttention効率化への接続が不足している|
|第5段階|Mini GPT|Tokenizer|Character Tokenization|最小構成でToken化を理解するため|文字単位Tokenizerを実装できること|維持|語彙作成、encode、decodeを少ないコードで実装でき、Token化の全工程を把握しやすいため|
|第5段階|Mini GPT|Tokenizer|BPE|実用LLMで使われるTokenizationを理解するため|BPEの基本原理を説明できること|維持|頻出する隣接単位を反復的に結合するSubword Tokenizationの代表的原理であるため|
|第5段階|Mini GPT|Tokenizer|SentencePiece|言語非依存のTokenizationを理解するため|SentencePieceの役割を説明できること|修正|SentencePieceはBPEやUnigramを実装するTokenizer学習ツールであり、単一のToken化アルゴリズムではないことを明示する必要がある|
|第5段階|Mini GPT|GPT構造|Decoder-only Transformer|GPTの基本構造だから|Decoder-onlyモデルを構築できること|維持|Causal Self-AttentionとFFNを積層して次Tokenを予測するGPTの中心構造であるため|
|第5段階|Mini GPT|GPT構造|Causal Mask|未来のTokenを参照させないため|Causal Attentionの必要性を説明できること|維持|学習時に正解となる未来Tokenが入力から漏れることを防ぎ、生成時と同じ条件を保つために不可欠である|
|第5段階|Mini GPT|GPT構造|Autoregressive Model|前のTokenから次Tokenを生成するため|自己回帰生成を説明できること|維持|系列確率を条件付き確率の積へ分解し、1 Tokenずつ生成するGPTの基本原理であるため|
|第5段階|Mini GPT|Language Modeling|Next Token Prediction|GPTの事前学習目的そのものだから|次Token予測の学習方法を説明できること|維持|入力系列の各位置から次Tokenを予測する自己教師あり学習目標としてGPTの能力獲得に直結するため|
|第5段階|Mini GPT|Language Modeling|Context Length|モデルが参照できる範囲を理解するため|Context Windowの意味を説明できること|維持|学習サンプルの長さ、位置表現、Attention計算量、生成時の入力上限を決めるために必要である|
|第5段階|Mini GPT|Language Modeling|Cross Entropy Loss|次Token予測を最適化するため|Token予測とCross Entropyの関係を説明できること|修正|各位置のLogitと1 Token先へずらしたLabelの対応、Token単位のLoss、Batch・系列方向の集約まで明示する必要がある|
|第5段階|Mini GPT|文章生成|Greedy Decoding|最も基本的な生成方式を理解するため|最大確率Tokenを逐次選択できること|維持|確率分布から常に最大値を選ぶ決定的生成を、Sampling方式との比較基準にできるため|
|第5段階|Mini GPT|文章生成|Temperature|出力のランダム性を調整するため|Temperatureによる確率分布変化を説明できること|維持|Logitの尺度を変えて分布の鋭さと多様性を調整する仕組みを理解するために必要である|
|第5段階|Mini GPT|文章生成|Top-k|候補Tokenを限定するため|Top-k Samplingを実装できること|維持|低確率Tokenを除外し、候補数で探索範囲を制御する代表的な生成手法であるため|
|第5段階|Mini GPT|文章生成|Top-p|累積確率で候補を選択するため|Nucleus Samplingを説明できること|維持|分布の形に応じて候補数を動的に変える生成方法としてTop-kとの違いを理解するために必要である|
|第5段階|Mini GPT|文章生成|Sampling|確率的な文章生成を理解するため|確率分布からTokenを選択できること|削除|確率分布からのサンプリングは第1段階で扱い、この段階ではTemperature、Top-k、Top-pで具体的に実装できるため単独行は重複になる|
|第5段階|Mini GPT|実装|Dataset作成|GPT学習用データを準備するため|テキストから学習データを生成できること|修正|単なるテキスト変換ではなく、連続Token列のWindow分割、入力・Labelの1 Token Shift、Train・Validation分割まで含める必要がある|
|第5段階|Mini GPT|実装|Training Loop|GPTを実際に学習させるため|Forward・Loss・Backward・Updateを実装できること|修正|第3段階の一般的なLoopとの差を明確にし、Token Batch、Validation Loss、Gradient Clipping、Checkpointを含むGPT学習Loopとして具体化する必要がある|
|第5段階|Mini GPT|実装|Text Generation|学習済みモデルから文章を生成するため|自作GPTから文章を出力できること|維持|Promptのencodeから自己回帰生成、decodeまでMini GPTの全構成要素を接続する最終成果であるため|
|第5段階|Mini GPT|Tokenizer|Byte・Unicode処理|日本語や未知文字を壊さず、任意のテキストをToken化する考え方を理解するため|文字・Unicode code point・UTF-8 byteの違いと、Byte-level Tokenizationの利点を説明できること|追加|文字単位Tokenizerから実用的な多言語・未知文字対応へ進むための前提が不足している|
|第5段階|Mini GPT|Tokenizer|encode・decode・Special Token ID|文字列とToken ID列を双方向に変換し、系列境界を扱うため|encode・decodeを実装し、BOS・EOS・PAD・UNKなどのIDをVocabularyと整合させられること|追加|Tokenizerの名称だけでは、モデル入出力へ接続する実装契約と特殊Token管理を確認できないため|
|第5段階|Mini GPT|GPT構造|Model Configuration・Parameter数|Mini GPTの規模と計算量を制御するため|Vocabulary Size、Context Length、d_model、Head数、Layer数、FFN次元を設定し、Parameter数を概算できること|追加|モデル規模を変更して学習可能な範囲へ調整し、各Hyperparameterの関係を理解する項目が不足している|
|第5段階|Mini GPT|GPT構造|Language Model Head・Logits|各位置の隠れ表現からVocabulary全体の予測スコアを作るため|最終NormとLinear層からBatch・系列長・Vocabulary SizeのLogitを出力できること|追加|Transformer Blockの出力を次Token確率へ変換する出口が既存項目に明示されていない|
|第5段階|Mini GPT|GPT構造|Weight Tying|入力Embeddingと出力Projectionの重みを共有するため|重み共有の実装方法と、Parameter数・表現学習への影響を説明できること|追加|GPT系モデルでよく使われる入力・出力Embedding間の関係が不足している|
|第5段階|Mini GPT|Language Modeling|Input・Label ShiftとTeacher Forcing|系列全位置の次Token予測を並列に学習するため|入力Tokenと1位置先のLabelを対応付け、学習時は正解Prefix全体を入力することを説明・実装できること|追加|Next Token Predictionを実際のTensorへ落とす中心処理が既存項目では曖昧である|
|第5段階|Mini GPT|評価|Validation Loss・Perplexity|学習の進行と未知テキストへの予測性能を評価するため|Validation Lossを計算し、Perplexityとの関係と限界を説明できること|追加|生成例の主観評価だけでは、言語モデルの学習状態と過学習を定量的に判断できないため|
|第5段階|Mini GPT|実装|Checkpoint・学習再開|学習状態を保存し、中断後も同じ条件から再開するため|Model、Optimizer、Step、設定を保存し、Checkpointから学習を再開できること|追加|Mini GPTの学習実験を安全に継続し、最良状態を再利用する仕組みが不足している|
|第5段階|Mini GPT|文章生成|EOS・生成終了条件|生成を適切な長さと条件で停止するため|EOS検出、最大生成Token数、Context Length上限による停止を実装できること|追加|Text GenerationにはToken選択だけでなく、安全に終了する制御が必要だが明示されていない|
|第5段階|Mini GPT|検証|小規模BatchへのOverfit Test|モデル、Loss、勾配、Datasetの実装がつながっていることを確認するため|ごく小さいBatchを意図的に暗記させ、Lossが十分下がるかで実装を診断できること|追加|学習が進まない原因をモデル能力と実装不具合に切り分ける実践的な検証手順が不足している|
|第6段階|Fine-tuning|Hugging Face|transformers|既存LLMを利用するため|モデル・Tokenizerを読み込み利用できること|維持|Pretrained Model、Tokenizer、設定、生成・学習APIを共通インターフェースで扱う中核ライブラリであるため|
|第6段階|Fine-tuning|Hugging Face|datasets|大規模データセットを扱うため|Datasetの読み込み・加工ができること|維持|読み込み、map、filter、shuffle、splitなどFine-tuning用データ処理の基盤として必要である|
|第6段階|Fine-tuning|Hugging Face|Trainer|学習処理を効率的に構築するため|Trainerを使って学習できること|修正|TrainerだけでなくTrainingArguments、Data Collator、評価、Callbackの役割を含め、SFTTrainerとの使い分けを明示する必要がある|
|第6段階|Fine-tuning|Hugging Face|PEFT|省メモリFine-tuningを行うため|PEFTの目的を説明できること|維持|Base Modelの大部分を凍結し、少数の追加・選択パラメータだけを学習する枠組みとして実用上重要である|
|第6段階|Fine-tuning|Fine-tuning|Full Fine-tuning|全パラメータ調整の仕組みを理解するため|Full Fine-tuningとPEFTを比較できること|維持|学習可能Parameter数、VRAM、保存容量、性能、破壊的忘却の観点でPEFTと比較する基準になるため|
|第6段階|Fine-tuning|Fine-tuning|SFT|指示応答能力を追加するため|Instruction-Responseデータで学習できること|修正|SFTはInstruction-Responseだけに限らず、Language Modeling、Prompt-Completion、会話形式を扱うため、対象形式とLoss範囲を正確に説明する必要がある|
|第6段階|Fine-tuning|LoRA|Low-Rank Adaptation|少ない追加パラメータで学習するため|LoRAの基本原理を説明できること|維持|Base Weightを凍結し、低Rank行列の積による更新量だけを学習するPEFTの代表手法であるため|
|第6段階|Fine-tuning|LoRA|Rank|LoRAの表現力とメモリ量を調整するため|Rank変更の影響を理解できること|維持|学習可能Parameter数、Adapter容量、計算・メモリ量を直接左右する主要Hyperparameterであるため|
|第6段階|Fine-tuning|LoRA|Alpha|LoRA更新量を調整するため|Alphaの役割を説明できること|修正|Alpha単独ではなく、通常のScalingであるAlphaとRankの比が更新量へ与える影響として説明する必要がある|
|第6段階|Fine-tuning|LoRA|Target Module|Fine-tuning対象層を指定するため|適切なTarget Moduleを設定できること|修正|層名はModel Architectureごとに異なり、Attention射影だけか全Linear層かで学習容量も変わるため、Model構造を確認して選ぶ手順が必要である|
|第6段階|Fine-tuning|量子化|8bit Quantization|モデルのメモリ消費を削減するため|8bit量子化の利点と制約を説明できること|修正|Weight量子化、8-bit Optimizer、推論、PEFT学習を区別し、量子化したBase Weightそのものを通常の方法で全Parameter学習するわけではない点を明示する必要がある|
|第6段階|Fine-tuning|量子化|4bit Quantization|より小さいGPUでLLMを扱うため|4bit量子化を利用できること|修正|単なる4-bit化ではなく、NF4・FP4、Compute dtype、Double Quantization、品質とHardware制約を区別して設定できる内容が必要である|
|第6段階|Fine-tuning|QLoRA|QLoRA|量子化モデルを効率的にFine-tuningするため|QLoRAでモデルをFine-tuningできること|修正|凍結した4-bit量子化Base Modelを通して勾配を伝え、LoRA Adapterだけを学習する構造と、NF4・Double Quantizationなどの要素を説明する必要がある|
|第6段階|Fine-tuning|データセット設計|Data Cleaning|誤ったデータによる性能低下を防ぐため|不要・不正データを除去できること|維持|誤答、文字化け、不完全会話、有害内容などの低品質例は学習結果へ直接反映されるため|
|第6段階|Fine-tuning|データセット設計|Deduplication|重複データによる偏りを防ぐため|重複データを検出・削除できること|維持|同一・類似例の過剰学習、評価Leakage、特定表現への偏りを抑えるために必要である|
|第6段階|Fine-tuning|データセット設計|Formatting|モデル形式に適した学習データを作るため|Instruction形式などにデータ変換できること|修正|標準形式と会話形式、Prompt-Completion、role・content、Special Token、Chat Templateの整合まで含める必要がある|
|第6段階|Fine-tuning|データセット設計|Dataset Balance|特定分野への偏りを防ぐため|データ構成比を評価・調整できること|維持|用途、言語、難易度、回答形式、安全性の構成比がFine-tuned Modelの振る舞いへ影響するため|
|第6段階|Fine-tuning|Hugging Face|TRL・SFTTrainer|会話形式やPrompt-Completion形式のSFTを適切に実行するため|SFTTrainerへModel、Dataset、SFTConfig、PEFT設定を渡し、学習・評価できること|追加|汎用Trainerだけでは、Chat Template適用、Packing、Completion LossなどSFT固有の処理が分かりにくいため|
|第6段階|Fine-tuning|データセット設計|Chat Template|会話のroleとSpecial Tokenを対象Modelが期待するToken列へ変換するため|TokenizerのChat Templateを確認し、重複Special Tokenを避けて会話データへ適用できること|追加|同じ会話内容でもModelごとに制御Tokenが異なり、形式不一致が性能を大きく損なうため|
|第6段階|Fine-tuning|損失設計|Label Masking・Completion Loss|Prompt部分を学習対象にするか、Assistant回答だけを学習するか制御するため|不要なLabelをignore indexへ置き換え、学習目的に応じてLoss対象Tokenを設定できること|追加|Dataset形式だけでは、どのTokenに対して誤差を計算するかが定まらないため|
|第6段階|Fine-tuning|データセット設計|Truncation・Packing|Context Lengthを効率よく使い、長すぎる例を安全に処理するため|最大系列長、切り詰め方、短い例のPacking、EOS境界を設計できること|追加|系列長の処理を誤ると重要な回答部分の欠落や、Paddingによる計算浪費が起きるため|
|第6段階|Fine-tuning|データセット設計|Train・Validation・Test分割と汚染防止|学習調整と最終評価を分離し、評価例の暗記を防ぐため|類似例・同一会話を跨がせずに分割し、BenchmarkやTestとの重複を検査できること|追加|Fine-tuning Datasetと評価DatasetのLeakageを防ぐ項目が明示されていない|
|第6段階|Fine-tuning|学習設定|Learning Rate・Batch・Epoch・Warmup|Base Modelを壊さず、限られたデータから安定して学習するため|実効Batch Size、Gradient Accumulation、学習率、Epoch、Warmup、Schedulerを一体として設定できること|追加|Fine-tuningの成否を左右する主要Hyperparameterと相互関係が既存項目にない|
|第6段階|Fine-tuning|学習効率化|Mixed Precision・Gradient Checkpointing|VRAMを抑えながら大きなModelや系列を学習するため|bf16・fp16の選択、Gradient Checkpointingの計算時間とMemoryのTrade-offを説明・設定できること|追加|LoRAや量子化以外の主要な省Memory手段が不足している|
|第6段階|Fine-tuning|LoRA|LoRA Dropout・modules_to_save|Adapterの正則化と、LoRA対象外でも学習・保存すべき層を制御するため|LoRA Dropoutを設定し、必要に応じてEmbeddingや分類Headなどを保存対象へ含められること|追加|Rank、Alpha、Target Moduleだけでは実用的なLoRA設定と保存対象を十分に扱えないため|
|第6段階|Fine-tuning|LoRA|Adapter保存・読込・Merge|用途別Adapterを管理し、推論形式へ変換するため|Adapterだけを保存・読み込みし、Base Modelとの組合せを記録し、必要に応じてMergeできること|追加|学習後の成果物管理とDeploymentへ接続する工程が既存項目にない|
|第6段階|Fine-tuning|資源計画|VRAM・学習可能Parameter数の見積り|手元のHardwareで実行可能な方式と設定を選ぶため|Model Weight、Optimizer State、Gradient、ActivationのMemoryを概算し、Full・LoRA・QLoRAを比較できること|追加|手法名だけでは実行前にOOMの可能性や現実的なModel Sizeを判断できないため|
|第6段階|Fine-tuning|評価|Base Modelとの比較評価|Fine-tuningが目的性能を改善し、一般能力を過度に損なっていないか確認するため|同一Prompt・設定でBaseとFine-tuned Modelを比較し、目的指標と副作用を評価できること|追加|学習Lossだけでは調整の有効性を判断できず、元Modelからの変化を測る基準が必要である|
|第6段階|Fine-tuning|評価|Overfitting・Catastrophic Forgetting|少量データへの暗記や既存能力の損失を検出するため|Train・Validation差、生成例、一般Benchmarkを用いて過学習と破壊的忘却を評価・対策できること|追加|特定用途への改善と汎用能力低下のTrade-offを判断する項目が不足している|
|第6段階|Fine-tuning|実験管理|Checkpoint・実験追跡・再現性|複数条件を比較し、学習を再開・再現できるようにするため|Config、Seed、Dataset版、Model Revision、Metric、Checkpointを一体で記録できること|追加|Fine-tuning結果を比較可能にし、採用Modelの由来を追跡する仕組みが不足している|
|第6段階|Fine-tuning|ガバナンス|License・個人情報・安全性|ModelとDatasetを適法かつ安全に利用・公開するため|利用条件、再配布条件、個人・機密情報、有害データ、公開範囲を確認し、記録できること|追加|技術的に学習できても、権利・Privacy・安全上の制約を満たさなければ実運用できないため|
|第7段階|ChatGPT型システム|Prompt Engineering|System Prompt|AIの役割・制約を設定するため|System Promptを設計できること|修正|単一のPrompt文ではなく、命令階層、信頼できる指示と外部入力の分離、変更可能なPolicyとして設計する必要がある|
|第7段階|ChatGPT型システム|Prompt Engineering|Few-shot|例示によって出力を誘導するため|Few-shot Promptを設計できること|維持|説明だけで指定しにくい判断基準、出力形式、境界事例を具体例で示す基本手法として有効である|
|第7段階|ChatGPT型システム|Prompt Engineering|Structured Output|後続システムでAI出力を利用するため|JSON等の構造化出力を設計できること|修正|JSONらしい文字列ではなくSchemaで制約し、型・必須項目・列挙値を検証することと、内容の正しさは別途検証が必要な点を含める必要がある|
|第7段階|ChatGPT型システム|Context Management|Context Window管理|長い会話や文書を効率的に扱うため|Context消費を考慮して情報を選択できること|修正|Token数の計測、優先順位付け、Truncation、要約、Compaction、検索による再投入と、情報欠落の検証まで扱う必要がある|
|第7段階|ChatGPT型システム|RAG|Embedding Model|文章を検索可能なベクトルへ変換するため|Embeddingを生成・利用できること|維持|検索対象とQueryを同じベクトル空間へ写し、意味的類似度を計算するRAGの基礎であるため|
|第7段階|ChatGPT型システム|RAG|Vector Database|Embeddingを保存・検索するため|Vector DBを利用できること|維持|Embedding、本文、Metadataを関連付け、近傍検索と更新を行うRAGの保存・検索基盤であるため|
|第7段階|ChatGPT型システム|RAG|Chunking|長文書を検索単位へ分割するため|適切なChunk Sizeを設計できること|修正|固定Sizeだけでなく、文書構造、意味境界、Overlap、Metadata、検索後のContext再構成を含めて設計する必要がある|
|第7段階|ChatGPT型システム|RAG|Semantic Search|意味的に近い情報を検索するため|ベクトル類似度検索を実装できること|修正|Vector検索だけでなく、Keyword検索、Hybrid検索、Metadata Filterとの使い分けと評価まで含める必要がある|
|第7段階|ChatGPT型システム|RAG|Reranking|検索候補の精度を改善するため|検索結果を再順位付けできること|維持|高速な一次検索と高精度な再評価を分離し、限られたContextへ有用な根拠を選ぶために必要である|
|第7段階|ChatGPT型システム|Tool Calling|Function Calling|LLMから外部機能を利用させるため|Tool schemaを設計できること|修正|Schema定義に加え、Tool選択、引数Validation、実行、Tool結果の返却、複数回呼出しまでのProtocol全体を実装する必要がある|
|第7段階|ChatGPT型システム|Tool Calling|API連携|外部サービスとLLMを接続するため|LLMからAPIを安全に呼び出せること|修正|認証、Timeout、Retry、Rate Limit、Idempotency、入力・出力Validation、外部障害時のFallbackまで含める必要がある|
|第7段階|ChatGPT型システム|Agent|Tool Selection|状況に応じて適切なToolを選択させるため|Tool選択ロジックを設計できること|維持|利用可能なTool、適用条件、禁止条件を定義し、不要・危険な呼出しを減らす中心能力であるため|
|第7段階|ChatGPT型システム|Agent|Planning|複雑な作業を複数Stepへ分解するため|タスクを計画・実行するAgentを設計できること|維持|依存関係を持つ作業を小さなStepへ分け、観測結果に応じて次の処理を選ぶために必要である|
|第7段階|ChatGPT型システム|Agent|State Management|複数Stepにまたがる状態を保持するため|Agent状態を管理できること|維持|計画、Tool結果、承認待ち、失敗、再開位置を明示的な状態として管理するために不可欠である|
|第7段階|ChatGPT型システム|Memory|Conversation History|会話の継続性を持たせるため|履歴を適切に保持・投入できること|修正|履歴の永続化とModelへ毎回投入するContextは別であり、選択・要約・Token Budget・Tool履歴を含めて管理する必要がある|
|第7段階|ChatGPT型システム|Memory|Long-term Memory|セッションを超えて情報を保持するため|長期記憶の保存・検索方式を設計できること|修正|保存対象、抽出根拠、利用者同意、信頼度、更新、削除、検索、誤記憶の訂正までLifecycleとして設計する必要がある|
|第7段階|ChatGPT型システム|Backend|REST API|LLM機能を他システムへ提供するため|APIを設計・実装できること|維持|UIとModel・RAG・Tool実行を分離し、認証や監視を適用できる安定した境界として必要である|
|第7段階|ChatGPT型システム|Backend|FastAPI|PythonでAI Backendを構築するため|FastAPIでLLM APIを構築できること|維持|PythonのAIライブラリと統合しやすく、型付きAPIと非同期処理を学ぶ具体的な実装手段として適切である|
|第7段階|ChatGPT型システム|Backend|Authentication|ユーザーアクセスを制御するため|認証・認可を設計できること|修正|本人確認であるAuthenticationと、Dataset・会話・Toolごとの権限制御であるAuthorizationを分離して設計する必要がある|
|第7段階|ChatGPT型システム|Backend|Database|ユーザー・会話・ログを保存するため|DBへ永続化できること|維持|会話、User設定、権限、Memory、評価、監査情報を一貫して永続化する基盤であるため|
|第7段階|ChatGPT型システム|Inference|GPU|LLM推論の計算基盤を理解するため|GPUとCPUの違いを説明できること|維持|行列演算の並列性、Memory帯域、Costを踏まえて推論基盤を選ぶために必要である|
|第7段階|ChatGPT型システム|Inference|VRAM|モデルをGPUへ載せる制約を理解するため|モデルサイズとVRAMの関係を概算できること|維持|Weight、KV Cache、Activation、BatchがMemoryへ与える影響を見積もる前提になるため|
|第7段階|ChatGPT型システム|Inference|KV Cache|LLM推論を高速化するため|KV Cacheの役割を説明できること|維持|生成済みTokenのKey・Valueを再計算せず、自己回帰Decodeを高速化する中心機構であるため|
|第7段階|ChatGPT型システム|Inference|Batch Inference|複数リクエストを効率的に処理するため|Batch処理の利点を説明できること|維持|複数入力をまとめて処理し、GPU利用率とThroughputを高める基本手法であるため|
|第7段階|ChatGPT型システム|Inference|Continuous Batching|LLM Servingのスループットを向上させるため|Continuous Batchingを説明できること|維持|生成長の異なるRequestを動的に入替え、GPUの待ち時間を減らす実用的Serving技術であるため|
|第7段階|ChatGPT型システム|評価|Human Evaluation|自動指標では測れない品質を評価するため|人手評価基準を設計できること|維持|有用性、自然さ、安全性など自動指標で捉えにくい品質を、Rubricと一致度を用いて評価するために必要である|
|第7段階|ChatGPT型システム|評価|LLM-as-a-Judge|大量の回答を効率よく評価するため|LLM評価器を利用・検証できること|修正|位置・長さ・文体などのBias、Judge自身の誤り、基準漏洩を考慮し、人手評価との相関と再現性を検証する必要がある|
|第7段階|ChatGPT型システム|評価|Hallucination Evaluation|誤情報生成を検出するため|Hallucination評価方法を設計できること|修正|単一のHallucination率ではなく、根拠整合性、外部事実性、引用正確性、不明時の棄権を分けて評価する必要がある|
|第7段階|ChatGPT型システム|評価|RAG Evaluation|検索と生成を分離して評価するため|Retrieval・Answerを個別に評価できること|維持|検索のRecall・Precisionと、回答のFaithfulness・Relevanceを分離し、失敗箇所を特定するために必要である|
|第7段階|ChatGPT型システム|Security|Prompt Injection|外部入力による命令乗っ取りを防ぐため|攻撃例と防御策を説明できること|維持|User入力だけでなく、Web・文書・Tool結果に含まれる間接的命令がAgent動作へ影響する主要Riskであるため|
|第7段階|ChatGPT型システム|Security|Jailbreak|安全制約の回避攻撃を理解するため|Jailbreakの性質と対策を説明できること|修正|Prompt Injectionとの重なりを認識しつつ、Policy回避を目的とする入力として区別し、単一Promptでは完全防御できない点を含める必要がある|
|第7段階|ChatGPT型システム|Security|Data Leakage|機密情報流出を防ぐため|データ境界とアクセス制御を設計できること|修正|Promptだけでなく、RAG、Memory、Log、Cache、Tool引数、Model Providerへの送信を含むData Flow全体で制御する必要がある|
|第7段階|ChatGPT型システム|Security|Tool Abuse|Agentによる危険な外部操作を防ぐため|Tool権限や承認フローを設計できること|修正|Excessive Agencyとして、Tool機能・権限・自律性を最小化し、破壊的・高影響操作へ承認と監査を設ける必要がある|
|第7段階|ChatGPT型システム|モデル連携|Model・API選定とVersion管理|品質、Latency、Cost、機能要件に合うModelを選び、更新による変化を管理するため|Model IDとSnapshot、対応機能、Fallback、Deprecationを記録し、変更前後を評価できること|追加|Model更新がPrompt、Tool Calling、出力品質、Costへ影響するため、固定・移行・Rollbackの設計が必要である|
|第7段階|ChatGPT型システム|Prompt Engineering|Prompt・設定のVersion管理|Prompt変更を再現可能にし、品質差の原因を追跡するため|Prompt、Model、Sampling設定、Tool定義をVersion化し、評価結果と対応付けられること|追加|Promptをソースコード外で場当たり的に変更すると、Regressionの原因を追跡できないため|
|第7段階|ChatGPT型システム|Backend|Streaming・中断処理|最初のTokenを早く表示し、利用者が不要な生成を停止できるようにするため|Streaming EventをUIへ転送し、切断・Cancel・部分出力・Errorを処理できること|追加|Chat型UIの体感Latencyと不要なCostを抑える基本機能が既存項目にない|
|第7段階|ChatGPT型システム|Backend|Timeout・Retry・Rate Limit・Idempotency|外部APIの一時障害や重複実行へ耐えるため|指数Backoff、Retry可能なErrorの判定、Rate Limit、Idempotency Keyを設計できること|追加|LLM・Tool APIは失敗や制限が起きるため、単純な再実行では二重処理や障害連鎖を招く|
|第7段階|ChatGPT型システム|運用|Token・Cost・Latency Budget|利用者体験と費用を予測可能に保つため|入力・出力Token、検索件数、Tool回数、処理時間に上限を設定し、利用量を計測できること|追加|品質だけを最適化すると、長いContextやAgent LoopによってCostとLatencyが制御不能になるため|
|第7段階|ChatGPT型システム|運用|Cache|重複する検索・生成・Embedding処理を減らすため|Cache Key、TTL、無効化、権限境界、非決定的出力の扱いを設計できること|追加|LatencyとCostを下げられる一方、古い回答や他UserのData混入を防ぐ設計が必要である|
|第7段階|ChatGPT型システム|運用|Logging・Metrics・Tracing|Model、RAG、Tool、Agentのどこで失敗したか追跡するため|Request ID、Latency、Token、検索結果、Tool Call、Error、評価結果を相関付けて観測できること|追加|最終回答だけではAgentやRAGの内部失敗を診断できず、品質改善とIncident調査が困難になるため|
|第7段階|ChatGPT型システム|RAG|Ingestion・Index Lifecycle|文書の追加・更新・削除を検索Indexへ正しく反映するため|取得、Parse、Chunk、Embedding、Index、Version、再Index、削除の流れを設計できること|追加|初回登録だけでなく、原文更新や削除後も古いChunkを残さない運用が必要である|
|第7段階|ChatGPT型システム|RAG|Hybrid Search・Metadata Filter|意味類似度だけでは弱い固有名詞検索と権限制御を補うため|Vector・Keyword Scoreを組み合わせ、日付・種類・Tenant・権限で候補を絞り込めること|追加|Semantic Search単独では完全一致、鮮度、文書属性、Access条件を十分に扱えないため|
|第7段階|ChatGPT型システム|RAG|Query Rewrite・Multi-query|会話的で曖昧な質問を検索に適したQueryへ変換するため|会話Contextを補完した検索Queryを作り、複数Queryの結果を統合・重複除去できること|追加|Userの表現と文書中の表現が異なる場合のRecall改善手段が不足している|
|第7段階|ChatGPT型システム|RAG|Access-control-aware Retrieval|Userが閲覧可能な文書だけを検索・生成へ利用するため|検索前Filterと取得後検証を用い、文書・Chunk単位の権限を強制できること|追加|回答段階で隠すだけでは、権限外DataがContextやLogへ流入する可能性があるため|
|第7段階|ChatGPT型システム|RAG|Citation・Source Attribution|回答の根拠を利用者が確認できるようにするため|取得したChunkと回答中の主張を対応付け、Source Link・版・該当箇所を提示・検証できること|追加|RAGで情報を取得しても、どの主張をどのSourceが支えるか確認できなければ信頼性を評価しにくいため|
|第7段階|ChatGPT型システム|Agent|WorkflowとAgentの使い分け|決定的処理とModel判断が必要な処理を分離するため|固定Workflow、State Machine、LLM AgentをRisk・再現性・柔軟性から選択できること|追加|すべてをAgentへ委ねると挙動が不安定になり、単純処理までCostとRiskが増えるため|
|第7段階|ChatGPT型システム|Agent|停止条件・Loop・実行Budget|Agentが無限Loopや過剰なTool利用へ陥ることを防ぐため|最大Step、時間、Token、Cost、Retry回数、終了状態を定義できること|追加|PlanningとStateだけでは、失敗時に処理が収束する保証がないため|
|第7段階|ChatGPT型システム|Agent|Tool結果Validation・Error Recovery|Toolの失敗や不正な結果から安全に回復するため|Schema検証、Error分類、Retry、代替Tool、部分完了、Compensationを設計できること|追加|Tool出力を無条件に信頼すると、誤Dataや外部障害が後続判断と操作へ連鎖するため|
|第7段階|ChatGPT型システム|Agent|Human-in-the-loop・Approval|高影響操作を実行前に人が確認できるようにするため|承認対象、確認画面、変更内容、取消可能性、Timeout後の扱いを設計できること|追加|送信、購入、削除、権限変更などをModel判断だけで実行させない境界が必要である|
|第7段階|ChatGPT型システム|Memory|要約・Compaction|長い会話をContext上限内へ圧縮しつつ重要情報を保つため|保持すべき事実、未解決Task、決定、Sourceを構造化して要約し、原履歴へ参照を残せること|追加|Conversation Historyを全件投入し続ける方式はToken・Cost・Latency上の限界があるため|
|第7段階|ChatGPT型システム|Memory|Retention・Consent・Deletion|個人情報を必要以上に長く保存せず、利用者の選択を反映するため|保存目的、保存期間、同意、Export、訂正、削除、Auditを設計できること|追加|長期Memoryには利便性だけでなくPrivacyと誤記憶のRiskが伴うため|
|第7段階|ChatGPT型システム|評価|Golden Dataset・Regression Test|Prompt・Model・RAG変更による品質低下を継続的に検出するため|代表例、境界例、失敗例をVersion化し、変更前後で自動・人手評価を再実行できること|追加|一度の評価だけでは、依存ModelやPrompt更新後の品質を保証できないため|
|第7段階|ChatGPT型システム|評価|Trace Evaluation|最終回答だけでなく、検索・Tool選択・引数・状態遷移を評価するため|Agent TraceへStep単位の基準を適用し、失敗原因とRegression箇所を特定できること|追加|Agentは正しい最終回答でも危険・非効率な経路を取ることがあり、結果だけの評価では見逃すため|
|第7段階|ChatGPT型システム|評価|Latency・Cost・Reliability・SLO|品質以外の実用性を定量評価するため|Percentile Latency、Error率、Availability、Token Cost、Throughputの目標とAlertを設定できること|追加|高品質でも遅い、高価、失敗しやすいSystemは実用要件を満たさないため|
|第7段階|ChatGPT型システム|評価|Red Team・Adversarial Test|通常入力では見つからない安全性と堅牢性の弱点を発見するため|Prompt Injection、権限逸脱、Data抽出、長文・変形入力を含む攻撃的Testを継続実行できること|追加|平均的な評価Datasetだけでは悪意ある入力や稀な高影響Failureを十分に検出できないため|
|第7段階|ChatGPT型システム|Security|Output Validation・Sanitization|Model出力をCode、HTML、SQL、Tool引数として安全に利用するため|許可Schema、Escape、Parameterize、Allowlist、Sandboxを用い、出力を命令として無条件実行しないこと|追加|Structured Outputでも内容が安全とは限らず、不適切な出力処理が別のInjectionや実行被害につながるため|
|第7段階|ChatGPT型システム|Security|Guardrails・Moderation|不適切な入力・出力を検知し、用途に応じて処理を制限するため|Policy分類、PII検出、拒否、Escalation、誤検知・見逃しの評価を設計できること|追加|System Promptだけでは安全Policyを安定して強制できず、多層の制御と評価が必要である|
|第7段階|ChatGPT型システム|Security|Secrets Management|API KeyやCredentialをPrompt、Log、Clientへ露出させないため|環境別Secret保管、最小権限、Rotation、漏洩時の失効、Log Redactionを実装できること|追加|Toolや外部APIを使うSystemではCredential漏洩が実際のData・操作権限の侵害につながるため|
|第7段階|ChatGPT型システム|Security|Supply Chain・依存関係管理|Model、Dataset、Package、Tool、MCPなど外部ComponentのRiskを管理するため|出所、Version、署名・Hash、脆弱性、権限、更新内容を確認し、固定・Rollbackできること|追加|ChatGPT型Systemは多くの外部Componentへ依存し、一つの改ざんや更新が全体へ影響するため|
|第7段階|ChatGPT型システム|Security|Tenant Isolation|複数User・組織のDataと権限を混在させないため|Database、Vector Store、Cache、Log、Tool CredentialでTenant境界を強制し、越境Testを行えること|追加|認証済みでも、検索・Cache・Memoryの設計ミスにより別UserのDataが漏れる可能性があるため|
|第7段階|ChatGPT型システム|運用|Audit Log・Incident Response|高影響操作とSecurity Eventを追跡し、問題発生時に封じ込めるため|誰が、いつ、何を入力し、どのToolが何を変更したか記録し、停止・失効・通知・復旧手順を定義できること|追加|予防策だけではすべてのFailureを防げず、検知後の対応と説明責任が必要である|
|最終段階|LLM Training|Pretraining|Corpus|LLMの知識源となる学習データを用意するため|大量テキストCorpusを構成できること|修正|量だけでなく、出所、権利、個人情報、品質、時点、言語・分野構成を追跡できるCorpusとして定義する必要がある|
|最終段階|LLM Training|Pretraining|Tokenizer Training|モデル専用Vocabularyを作るため|Tokenizerをゼロから学習できること|維持|語彙、特殊Token、圧縮効率、多言語性能がModelの入力表現と計算効率を左右するため|
|最終段階|LLM Training|Pretraining|Data Pipeline|巨大なデータを効率的に学習へ供給するため|読み込み・Shuffle・Batch化を設計できること|修正|Streaming、Shard、決定的Shuffle、Packing、Worker間分配、再開位置を含む分散Data Pipelineとして扱う必要がある|
|最終段階|LLM Training|Pretraining|Next Token Prediction|LLMの基本能力を獲得させるため|事前学習目的関数を説明・実装できること|維持|Causal Language Modelingの自己教師あり目的であり、系列全位置の次Token予測から基盤能力を学習するため|
|最終段階|LLM Training|Pretraining|Checkpoint|長時間学習を安全に継続するため|学習状態の保存・復元ができること|修正|ModelだけでなくOptimizer、Scheduler、Scaler、RNG、Data位置、分散ShardをAtomicに保存し、同条件で再開する必要がある|
|最終段階|LLM Training|Pretraining|Learning Rate Schedule|大規模学習を安定させるため|Warmup・Decayなどを設定できること|維持|Warmup、Peak Learning Rate、Decay、最小学習率は初期不安定性と収束品質を左右する主要設定であるため|
|最終段階|LLM Training|データ処理|Web Corpus|大量の自然言語データを確保するため|Webデータ利用時の特徴を説明できること|修正|大量性だけでなく、取得許可、Robots、License、PII、Malware、Spam、Snapshot時点を含む収集統制が必要である|
|最終段階|LLM Training|データ処理|Deduplication|重複学習と暗記を抑えるため|大規模重複除去の必要性を説明できること|維持|完全一致と近似重複を文書・部分列単位で除き、暗記、偏り、評価汚染を抑えるために必要である|
|最終段階|LLM Training|データ処理|Filtering|低品質・有害データを減らすため|品質フィルタリング基準を設計できること|修正|Rule、Classifier、Heuristicを組み合わせ、品質・安全性・Biasと誤除外のTrade-offをSample監査で評価する必要がある|
|最終段階|LLM Training|データ処理|Language Detection|多言語Corpusを整理するため|言語別にデータを分類できること|維持|言語識別のConfidenceとCode-switchを扱い、言語別MixtureとTokenizer評価へ接続するために必要である|
|最終段階|LLM Training|データ処理|Data Mixture|分野・言語の学習比率を制御するため|Dataset Mixtureを設計できること|維持|Source、言語、分野、品質のSampling Weightが能力配分と過学習へ直接影響するため|
|最終段階|LLM Training|データ処理|Benchmark Contamination|評価データを学習してしまう問題を防ぐため|データ汚染を検出・回避できること|維持|問題文だけでなく解答・派生版・近似表現を学習前に照合し、評価の独立性を保つために不可欠である|
|最終段階|LLM Training|Scaling|Model Size|モデル規模と性能の関係を理解するため|Parameter数の意味を説明できること|修正|Parameter数を単独で扱わず、固定Compute下のTraining Token数、Architecture、Memory、推論Costとの均衡で設計する必要がある|
|最終段階|LLM Training|Scaling|Data Size|学習データ量と性能の関係を理解するため|データ量が学習へ与える影響を説明できること|修正|生のDocument量ではなく有効Training Token数、重複、品質、Epoch数をModel SizeとComputeに対応付ける必要がある|
|最終段階|LLM Training|Scaling|Compute|計算量と性能の関係を理解するため|モデル・データ・Computeの関係を説明できること|修正|FLOPs、Hardware効率、時間、CostのBudget内でModel SizeとToken数を共同最適化するScaling設計として扱う必要がある|
|最終段階|LLM Training|分散学習|Data Parallelism|複数GPUで学習データを分散するため|Data Parallelの動作を説明できること|維持|各Rankが異なるMini-batchを処理し、勾配同期によって同一Modelを更新する基本分散方式であるため|
|最終段階|LLM Training|分散学習|Tensor Parallelism|巨大モデルの層を複数GPUへ分割するため|Tensor Parallelを説明できること|維持|Attention・MLP内の行列演算を分割し、単一Deviceに収まらない層を学習する主要なModel Parallel方式であるため|
|最終段階|LLM Training|分散学習|Pipeline Parallelism|モデルの層をGPU間で分割するため|Pipeline Parallelの利点と欠点を説明できること|維持|層群とMicro-batchを段階的に実行し、Memory分散とPipeline BubbleのTrade-offを理解するために必要である|
|最終段階|LLM Training|分散学習|FSDP|モデル状態を分散保持するため|FSDPの基本原理を説明できること|維持|Parameter、Gradient、Optimizer StateをData-parallel RankへShardし、必要時にCollective通信で復元する方式として重要である|
|最終段階|LLM Training|分散学習|ZeRO|巨大モデルのメモリ消費を削減するため|ZeRO Stageの概念を説明できること|維持|Optimizer State、Gradient、Parameterの冗長な複製を段階的に除くMemory最適化の基礎であるため|
|最終段階|LLM Training|分散学習|Gradient Accumulation|小さいGPUメモリで大きいBatchを再現するため|勾配蓄積を実装できること|維持|Micro-batchを複数回処理して実効Batchを増やし、Memory、通信頻度、最適化挙動を調整するため|
|最終段階|LLM Training|分散学習|Mixed Precision|高速化とメモリ削減を行うため|FP32・FP16・BF16の使い分けを説明できること|修正|FP16・BF16に加えてFP8、Accumulation精度、Master Weight、Loss Scaling、Hardware対応を分けて設計する必要がある|
|最終段階|LLM Training|SFT|Instruction Dataset|Base Modelを指示に従えるようにするため|SFT用Datasetを設計できること|維持|指示、入力、望ましい応答、Safety例の品質と構成がPost-training後の振る舞いを直接規定するため|
|最終段階|LLM Training|SFT|Chat Template|会話形式をモデルへ統一的に与えるため|Chat Templateを設計・適用できること|維持|Role、区切り、Special Token、Generation Promptを学習時と推論時で一致させるために不可欠である|
|最終段階|LLM Training|Preference Learning|Chosen・Rejected|回答品質の好みをモデルへ学ばせるため|Preference Datasetを構築できること|維持|同一Promptへの比較応答と選好LabelはReward ModelやDPO系目的関数の基本入力になるため|
|最終段階|LLM Training|Preference Learning|Reward Signal|どの回答が望ましいか数値化するため|PreferenceとRewardの関係を説明できること|修正|相対Preference、学習Reward、Rule・Verifierによる報酬を区別し、DPOでは明示的Reward Modelが不要な点も扱う必要がある|
|最終段階|LLM Training|DPO|Reference Model|元モデルから過度に離れないよう比較するため|Reference Modelの役割を説明できること|維持|ChosenとRejectedの尤度比を基準Policyと比較し、最適化の基準点を与えるDPOの中核要素であるため|
|最終段階|LLM Training|DPO|Preference Optimization|人間が好む回答を直接学習するため|DPOの基本原理を説明できること|修正|Preference分類Loss、Reference比、Beta、Offline Data、長さBiasを含め、Reward ModelとOn-policy RLを省く仕組みとして理解する必要がある|
|最終段階|LLM Training|RLHF|Reinforcement Learning|報酬を用いてモデル行動を最適化するため|RLの基本構造をLLMに対応付けて説明できること|維持|Promptを状態、Token生成を行動、応答をTrajectory、Rewardを目的としてPolicy更新へ対応付ける基礎であるため|
|最終段階|LLM Training|RLHF|Reward Model|人間の好みを数値化するため|Reward Modelの役割を説明できること|維持|比較Labelから応答Scoreを学び、RL Policyへ最適化信号を与える標準的RLHF Pipelineの構成要素であるため|
|最終段階|LLM Training|RLHF|Policy|最適化対象となるLLMを理解するため|PolicyとしてのLLMを説明できること|維持|Contextに対する次Token分布が逐次行動を定め、応答全体の確率と更新対象を構成するため|
|最終段階|LLM Training|RLHF|PPO|Rewardを用いてLLMを更新する方法を理解するため|PPOの基本的な更新原理を説明できること|修正|RLHFと同義ではなく、On-policy生成、Value Model、Clipping、Advantage推定を用いる選択肢の一つとして他手法と比較する必要がある|
|最終段階|LLM Training|RLHF|KL Penalty|元モデルからの過度な逸脱を抑えるため|KL制約の目的を説明できること|維持|Reward最大化による分布崩壊や不自然な出力を抑え、Reference Policy付近で能力と整合性を保つため|
|最終段階|LLM Training|Evaluation|Knowledge Evaluation|モデルの知識能力を評価するため|知識系Benchmarkを評価できること|維持|分野、時点、言語を分けた知識課題で正答率と汚染Riskを測る基礎評価であるため|
|最終段階|LLM Training|Evaluation|Reasoning Evaluation|推論性能を評価するため|推論タスクによる比較評価ができること|維持|多段推論課題を用い、最終回答だけでなくPrompt感度、安定性、汚染を含めて能力を比較するため|
|最終段階|LLM Training|Evaluation|Math Evaluation|数学能力を評価するため|数学問題によるモデル比較ができること|維持|数値・記号・証明・文章題など異なる数学能力を、実行可能な検証とともに評価するため|
|最終段階|LLM Training|Evaluation|Coding Evaluation|コード生成能力を評価するため|Coding Benchmarkを利用できること|維持|生成CodeをSandboxで実行し、Unit Test、Pass率、Security、複数言語を測る実践的評価が必要であるため|
|最終段階|LLM Training|Evaluation|Instruction Following|指示遵守能力を評価するため|指示への適合度を評価できること|維持|形式、制約、優先順位、拒否境界への適合を測り、知識正答率とは別の能力を確認するため|
|最終段階|LLM Training|Evaluation|Safety Evaluation|危険・不適切な出力を検証するため|Safety評価セットを設計・利用できること|維持|通常・敵対的入力に対する有害応答、過剰拒否、回避可能性を用途別Policyで測るために必要である|
|最終段階|LLM Training|Evaluation|Robustness|入力変化に対する安定性を確認するため|モデルの頑健性を評価できること|維持|言い換え、Typo、長さ、順序、分布外入力に対する性能変動とFailure Patternを把握するため|
|最終段階|LLM Training|データガバナンス|Data Provenance・License・Privacy|学習Dataの利用根拠と削除可能性を追跡するため|Source、License、Consent、PII処理、取得時点、変換履歴、除外要求をDataset単位で記録できること|追加|大規模Corpusの品質だけでは、権利・Privacy・再現性・削除要求に対応できないため|
|最終段階|LLM Training|データ処理|Text Normalization・Document Parsing|Webや文書のNoiseを除き、意味構造を保ったTextへ変換するため|Encoding、Unicode、Boilerplate、Markup、表、Code、文書境界を検証しながら正規化できること|追加|Tokenization前の抽出・正規化不良は品質低下や重複判定の失敗を全Corpusへ広げるため|
|最終段階|LLM Training|データ処理|Data Quality Audit・Sampling|自動Filter後のData分布と誤判定を検証するため|層化Sample、人手Rubric、Source別統計、False Positive・Negativeを用いて品質を監査できること|追加|自動Scoreだけでは、除去し過ぎ、残存Noise、言語・分野Biasを発見できないため|
|最終段階|LLM Training|Tokenizer|Tokenizer評価・Vocabulary設計|語彙が対象言語とDomainを効率よく表現できるか確認するため|Fertility、Byte Fallback、未知文字、数字・Code、多言語、Special TokenをCorpus別に評価できること|追加|Tokenizerを学習できても、語彙品質とModel計算量への影響を評価する項目が不足している|
|最終段階|LLM Training|Pretraining|Model Architecture・Configuration|学習対象Modelの容量、安定性、計算量を定義するため|Layer数、Hidden Size、Head、FFN、位置表現、Norm、Vocabulary、Dense・MoEを一貫したConfigとして設計できること|追加|DataとComputeを決めても、ArchitectureとConfigがなければParameter数、Memory、Checkpoint互換性を再現できないため|
|最終段階|LLM Training|Pretraining|Optimizer・Regularization・Gradient Clipping|大規模学習の更新量と発散Riskを制御するため|Optimizer、Beta、Epsilon、Weight Decay、Gradient Norm、Clip閾値を選定・監視できること|追加|Learning Rate Scheduleだけでは更新則、正則化、勾配爆発への対策を定義できないため|
|最終段階|LLM Training|Pretraining|Validation Loss・Perplexity|未知Dataへの予測性能と過学習を追跡するため|固定Validation SetでToken-weighted Lossを算出し、Perplexity、Domain別差、Tokenizer差の限界を説明できること|追加|Training Lossだけでは汎化、Data Mixtureの偏り、Checkpoint選択を判断できないため|
|最終段階|LLM Training|Pretraining|Training Stability・Loss Spike|高Costな学習の異常を早期検知し、安全に回復するため|Loss、Gradient Norm、Activation、NaN・Inf、Throughputを監視し、原因をData・数値精度・通信へ切り分けられること|追加|大規模学習では小さな異常が多数Nodeへ波及し、未検知のまま大きなComputeを失うため|
|最終段階|LLM Training|Pretraining|Curriculum・Sequence Length Schedule|学習初期のCostと難易度を調整し、長いContextへ段階的に移行するため|Data難易度、Domain、Sequence LengthのScheduleと分布変化を評価できること|追加|全期間を同一分布・最大長で学習する以外の効率化と安定化手段が既存項目にないため|
|最終段階|LLM Training|Scaling|Scaling Laws・Compute-optimal Design|限られたComputeをModelとDataへ適切に配分するため|Pilot結果からLossのScaling傾向を推定し、Parameter数、Token数、FLOPsの候補を比較できること|追加|Model Size、Data Size、Computeの個別理解を、実際の設計判断へ統合する項目が必要である|
|最終段階|LLM Training|Scaling|Mixture of Experts|全Tokenで全Parameterを使わずModel容量を拡張するため|Router、Top-k Expert、Load Balance、Capacity、Expert Parallelism、推論CostのTrade-offを説明できること|追加|Dense Model以外の主要なScaling設計と、疎活性化固有の学習課題が不足している|
|最終段階|LLM Training|Scaling|Pilot Run・Scaling Extrapolation|本番学習前にHyperparameterと予算の妥当性を確認するため|小規模RunからLoss、Memory、Throughput、通信、Failure率を測り、本番規模へ外挿できること|追加|一度きりの大規模Runへ直接進むと、設定不良の検出が遅くCost損失が大きいため|
|最終段階|LLM Training|分散学習|Collective Communication・Interconnect|分散方式の通信CostとTopology制約を理解するため|All-reduce、All-gather、Reduce-scatter、Point-to-pointをBandwidth・Latency・Node境界と対応付けられること|追加|並列方式の名称だけでは、通信がBottleneckになる理由と配置方針を設計できないため|
|最終段階|LLM Training|分散学習|Activation Checkpointing|Activation Memoryを再計算と引き換えに削減するため|保存するLayer粒度を選び、Memory削減量と追加Computeを測定できること|追加|Model StateのShardingだけでは長系列・大Batch時のActivation Memoryを十分に抑えられないため|
|最終段階|LLM Training|分散学習|Sequence・Context Parallelism|長い系列のActivationとAttention計算をDevice間へ分割するため|Sequence軸の分割、通信、Mask、Position、他Parallelismとの組合せを説明できること|追加|Tensor・Pipeline Parallelismだけでは長Context時に増大する系列方向のMemoryを扱いにくいため|
|最終段階|LLM Training|分散学習|Expert Parallelism|MoEのExpertを複数Deviceへ配置するため|Token Dispatch、All-to-all、Load Imbalance、Capacity Overflowを測定・対策できること|追加|MoEではDense Modelと異なる通信Patternと負荷偏りが学習効率を左右するため|
|最終段階|LLM Training|分散学習|Parallelism Composition・Topology Mapping|複数の並列方式をCluster構成へ合わせて組み合わせるため|Data、Tensor、Pipeline、Sequence、Expert軸のGridを設計し、高速Link内外へ配置できること|追加|実際の大規模学習では単一方式だけでなく、Memoryと通信に応じた複合Parallelismが必要である|
|最終段階|LLM Training|分散学習|Profiler・MFU・Throughput|GPUが有効計算へ使われている割合とBottleneckを測るため|Tokens毎秒、Step時間、MFU、通信待ち、Data待ち、Kernel時間をProfileし改善できること|追加|学習が動作するだけでは、同じCostで十分なTokenを処理できているか判断できないため|
|最終段階|LLM Training|分散学習|Fault Tolerance・Elastic Resume|Node障害やPreemptionから大規模Runを復旧するため|障害検知、Atomic Checkpoint、Rank再構成、Data位置復元、再試行上限を設計・Testできること|追加|多数Nodeを長期間使う学習では部分障害が避けにくく、手動復旧だけでは時間と再現性を失うため|
|最終段階|LLM Training|SFT|Loss Masking・Packing|会話Dataの学習対象Tokenと計算効率を制御するため|User・System TokenをMaskし、Assistant応答だけのLoss、複数例Packing、EOS境界を正しく実装できること|追加|Instruction DatasetとChat Templateだけでは、どのTokenを学習し例同士を分離するか定まらないため|
|最終段階|LLM Training|Preference Learning|Preference Annotation Quality|選好Labelの一貫性と目的への適合を確保するため|Rubric、Annotator一致度、Tie、Noise、位置・長さBias、品質監査を設計できること|追加|Chosen・Rejectedが存在しても、Label品質が低ければReward Modelと直接選好最適化の双方が誤誘導されるため|
|最終段階|LLM Training|Post-training|Rejection Sampling・Best-of-N|複数候補から高品質応答を選びSFTや評価へ利用するため|候補生成、Score、重複除去、Selection Bias、推論Costを設計できること|追加|Gradient更新以外の基本的な応答改善・Data生成手法が既存項目にないため|
|最終段階|LLM Training|Preference Learning|RLAIF・AI Feedback|人手以外のFeedbackを補助的に利用するため|AI Judge、Rubric、Constitution、Calibration、人手監査、Bias増幅Riskを説明できること|追加|大規模なPreference Data作成ではAI Feedbackも使われるが、誤りやBiasを自己増幅させない統制が必要である|
|最終段階|LLM Training|Post-training|Online RL・Offline Preference Optimization|Policyが生成した新Dataで学ぶ方式と固定Dataで学ぶ方式を選ぶため|On-policy・Off-policy、探索、分布Shift、安定性、Cost、Reward Model要否を比較できること|追加|DPOとPPOを個別に知るだけでは、Data生成と更新方式の根本的な違いを選択できないため|
|最終段階|LLM Training|RLHF|GRPO|Value Modelを使わずGroup内相対RewardからPolicyを更新する方式を理解するため|Group Sampling、相対Advantage、Clipping、KL、Verifier Reward、Costと安定性をPPOと比較できること|追加|PPO以外の代表的なOn-policy最適化方式を比較し、用途に応じて選ぶ項目が不足している|
|最終段階|LLM Training|Reward Design|Process Reward・Outcome Reward|最終結果だけでなく途中過程へFeedbackを与える設計を理解するため|Step単位と最終回答のReward、Credit Assignment、Verifier信頼性、Gaming Riskを比較できること|追加|ReasoningやTool利用では最終正誤だけで、どの中間行動を改善すべきか特定しにくいため|
|最終段階|LLM Training|Reward Design|Reward Hacking・Specification Gaming|Proxy Rewardだけを攻略する望ましくない最適化を検出するため|Reward上昇と人手品質の乖離、Length・Format Hack、Evaluator Exploitを監視し対策できること|追加|Reward最適化は定義外の望ましくない行動を増やす可能性があり、独立評価と監査が必要である|
|最終段階|LLM Training|Evaluation|Multilingual Evaluation|言語ごとの能力差と安全性の不均衡を把握するため|高資源・低資源言語、翻訳依存、文化差、Tokenizer効率を分けて評価できること|追加|英語中心のBenchmarkだけでは、多言語Corpusで学習したModelの品質とRiskを判断できないため|
|最終段階|LLM Training|Evaluation|Long-context Evaluation|長い入力での検索、保持、統合能力とCostを測るため|位置、長さ、Distractor、複数根拠、長文生成、Latency・Memoryを変えて評価できること|追加|Context Lengthの上限値だけでは、情報位置や入力長による実効性能低下を捉えられないため|
|最終段階|LLM Training|Evaluation|Calibration・Uncertainty・Abstention|予測の確信度と誤りRiskを利用判断へつなげるため|Confidenceと正答率の対応、選択的回答、棄権、Threshold、Calibration Errorを評価できること|追加|Accuracyが同じModelでも誤答時の過信や不明時の応答方針に大きな差があるため|
|最終段階|LLM Training|Evaluation|Memorization・Privacy Extraction|学習Dataの再現と個人・機密情報漏洩Riskを測るため|Canary、Membership Inference、Prompt Extraction、近似一致を用い、Data削除・公開判断へ接続できること|追加|Deduplicationだけでは、学習後Modelが稀な系列を記憶・露出するRiskを評価できないため|
|最終段階|LLM Training|Evaluation|Statistical Significance・Reproducible Harness|小さなScore差を偶然や実装差と区別するため|Seed、Prompt、Sampling、Metric版を固定し、信頼区間、複数Run、Paired比較を実行できること|追加|単一RunのBenchmark値だけではModel差の確度と再現性を判断できないため|
|最終段階|LLM Training|ガバナンス|Data・Model LineageとModel Card|学習成果の由来、制約、評価、公開条件を追跡するため|Dataset版、Code Commit、Config、Checkpoint、Post-training手順、評価結果、既知の限界を文書化できること|追加|再現、監査、Rollback、利用者への説明には、Dataから公開Modelまでの一貫した履歴が必要である|

---

# 4. 各段階の到達目標

## 第1段階：数学・プログラミング

以下を説明・実装できることを目標とする。

- Pythonで基本的なプログラムを書ける
- NumPyでベクトル・行列を扱える
- ベクトル・行列・テンソルの違いを説明できる
- 微分・偏微分・勾配を説明できる
- 確率分布を説明できる
- 行列積・内積の意味を説明できる

---

## 第2段階：機械学習基礎

次の学習サイクルを説明できることを目標とする。

```text
入力データ
↓
モデル
↓
予測
↓
正解と比較
↓
Loss
↓
Gradient
↓
Parameter Update
```

最終的には、

> 機械学習とは、データを使い、損失関数が小さくなるようモデルのパラメータを最適化することである。

と説明できる状態を目指す。

---

## 第3段階：Neural Network

以下の流れをコードと概念の両方から理解する。

```text
Input
↓
Linear
↓
Activation
↓
Layer
↓
Prediction
↓
Loss
↓
Backpropagation
↓
Gradient
↓
Weight Update
```

PyTorchを利用して簡単なニューラルネットワークを構築・学習できることを到達目標とする。

---

## 第4段階：Transformer

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

## 第5段階：Mini GPT

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

## 第6段階：Fine-tuning

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

## 第7段階：ChatGPT型システム

LLMを単体で使うのではなく、実用的なサービスへ組み込めることを目標とする。

```text
ユーザー
↓
Web UI
↓
Backend
↓
Prompt / Context
↓
RAG
↓
Memory
↓
Agent
↓
Tool Calling
↓
LLM
↓
評価
↓
回答
```

この段階では、

> 良いAIシステムを作るには、LLMそのものの性能だけではなく、検索・データ・Context・Tool・評価・Securityも重要である。

ことを理解する。

---

## 最終段階：LLM Training

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

# 5. 学習によって最終的に理解する全体構造

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

# 6. 個人学習における到達点

本ロードマップのすべてを個人で学習することは可能だが、実際に扱える規模には違いがある。

## 個人でも実践可能な領域

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

## 小規模実験は可能だが大規模実践が難しい領域

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

# 7. 最終到達状態

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

# 8. 本ロードマップの最終ゴール

最終的には、

> **「ChatGPTを使える人」ではなく、「ChatGPTのようなAIがどのような理論・モデル・学習・システムによって成立しているのかを理解し、小規模な範囲では自分で再現・実装できる人」**

になることを本ロードマップのゴールとする。
