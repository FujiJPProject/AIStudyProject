# 第3段階：Neural Network

[前の段階](02_第2段階_機械学習基礎.md) ｜ [全体概要・目次](Readme.md) ｜ [次の段階](04_第4段階_Transformer.md)

## この段階の位置づけ

| 項目                 | 内容                                |
| :------------------- | :---------------------------------- |
| 学習テーマ           | Neural Network                      |
| 最終的に理解するもの | Deep Learningがどのように学習するか |
| 学習項目数           | 27項目                              |

## 学習項目一覧

| 段階    | 学習テーマ     | 分野                 | 項目                         | 学習する理由                                                                                           | 取得するべき内容                                                                                                     |
| :------ | :------------- | :------------------- | :--------------------------- | :----------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------- |
| 第3段階 | Neural Network | ニューラルネット基礎 | Neuron・Weight・Bias         | ニューラルネットの最小単位を、入力の重み付き和とBiasから出力を作る一つの計算として理解するため         | Neuronの式を書き、WeightとBiasが出力へ与える影響を説明できること                                                     |
| 第3段階 | Neural Network | ニューラルネット基礎 | Layer                        | 複数のNeuronをまとめた処理単位と、ネットワーク内での役割を理解するため                                 | Input・Hidden・Output Layerを区別し、各Layerの入出力形状を説明できること                                             |
| 第3段階 | Neural Network | 活性化関数           | Sigmoid・Softmax             | Logitを二値確率または多クラス確率分布へ変換する出力関数を比較して理解するため                          | SigmoidとSoftmaxの用途を区別し、Logit・確率・Cross Entropyとの関係を説明できること                                   |
| 第3段階 | Neural Network | 活性化関数           | ReLU                         | 線形変換を重ねるだけでは表現できない非線形な関係を学習しやすくするため                                 | ReLUの式と特徴を説明し、Dead ReLUが起きる条件を説明できること                                                        |
| 第3段階 | Neural Network | 活性化関数           | GELU・SiLU                   | 入力を滑らかにGateする活性化関数を比較し、Transformerや現代LLMで使われる非線形変換へつなげるため       | ReLUとの違い、およびGELUとSiLUの出力特性と主な用途を説明できること                                                   |
| 第3段階 | Neural Network | ニューラルネット基礎 | Multi-Layer Perceptron       | Linear変換と活性化関数を層状に組み合わせ、非線形な関係を表現する基本モデルを理解するため               | MLPの入出力形状と各層の計算を数式で追い、NumPyでForward処理を実装できること                                          |
| 第3段階 | Neural Network | 活性化関数           | Gated Linear Unit・SwiGLU    | MLPの情報経路を学習可能なGateで制御する仕組みを理解し、TransformerのFeed Forward Networkへ接続するため | GLUの基本構造と、SiLUを使うSwiGLUの計算・役割を説明できること                                                        |
| 第3段階 | Neural Network | 学習処理             | Forward Propagation          | 入力を各Layerへ順に通して予測とLossを求める流れを理解するため                                          | MLPのForward処理を数式とNumPyコードの両方で追跡できること                                                            |
| 第3段階 | Neural Network | 学習処理             | Computational Graph          | Forward処理を演算の依存関係として表し、どの経路で微分するかを理解するため                              | 演算から計算グラフを描き、入力・中間値・出力の依存関係をたどれること                                                 |
| 第3段階 | Neural Network | 学習処理             | Backpropagation              | Lossから各パラメータまで計算グラフを逆向きにたどり、連鎖律で勾配を求めるため                           | 簡単なMLPについて勾配を手計算し、誤差が各パラメータへ伝わる流れを説明できること                                      |
| 第3段階 | Neural Network | 学習技法             | Batch・Iteration・Epoch      | データを分割して更新する単位と、データセット全体を反復する回数を一体として管理するため                 | Batch Size、Iteration、Epochの関係を計算し、Batch Sizeが勾配のばらつき・メモリ・計算効率へ与える影響を説明できること |
| 第3段階 | Neural Network | 学習処理             | 勾配消失・勾配爆発           | 深いネットワークで層をまたぐ勾配が小さくなる、または大きくなる原因を理解するため                       | 活性化関数、Weight、層数が勾配へ与える影響と、代表的な対策を説明できること                                           |
| 第3段階 | Neural Network | 学習技法             | Weight Initialization        | 初期値の対称性を避け、層を進む信号と勾配の大きさを保ちやすくするため                                   | ゼロ初期化の問題を説明し、活性化関数に応じてXavier・He初期化を使い分けられること                                     |
| 第3段階 | Neural Network | 学習技法             | Batch Normalization          | Mini-batchの統計量を使って中間表現を正規化し、学習を安定させる仕組みを理解するため                     | BatchNormが正規化する軸、学習可能なScale・Shift、学習時と推論時の動作差を説明できること                              |
| 第3段階 | Neural Network | 学習技法             | Layer Normalization・RMSNorm | 各標本内の特徴方向を正規化する方式を学び、Batchへ依存しないTransformer向けの正規化へつなげるため       | BatchNormとの対象軸の違いと、LayerNorm・RMSNormの計算上の違いを説明できること                                        |
| 第3段階 | Neural Network | 学習技法             | Dropout                      | 学習時に一部の出力を確率的に無効化し、特定の特徴への過度な依存を抑えるため                             | Dropoutの学習時と推論時の動作差、および過学習を抑える考え方を説明できること                                          |
| 第3段階 | Neural Network | 学習技法             | Gradient Clipping            | Backpropagationで得た勾配が大きくなりすぎた場合に更新を安定させるため                                  | 値によるClippingとNormによるClippingを区別し、適用する位置を説明できること                                           |
| 第3段階 | Neural Network | PyTorch              | Tensorの基本操作             | NumPyで扱った多次元配列をPyTorchのモデル入力・出力・パラメータとして扱うため                           | Tensorを生成し、形状変更、Indexing、要素ごとの演算、行列積を実行できること                                           |
| 第3段階 | Neural Network | PyTorch              | Dataset・DataLoader          | 学習データを標本単位で保持し、ShuffleしたMini-batchとして反復可能にするため                            | Datasetを定義し、DataLoaderでBatch化・Shuffleして入力とラベルを取得できること                                        |
| 第3段階 | Neural Network | PyTorch              | nn.Module・nn.Linear         | LayerとMLPの概念を、PyTorchがパラメータを追跡できるモデルとして実装するため                            | nn.Moduleを継承し、nn.Linearと活性化関数を組み合わせたMLPを実装できること                                            |
| 第3段階 | Neural Network | PyTorch              | nn.Parameter・パラメータ登録 | 通常のTensorと、Optimizerが更新する学習対象を区別するため                                              | nn.Parameter、Moduleの属性、parameters・named_parametersの関係を説明し、登録された学習対象を確認できること           |
| 第3段階 | Neural Network | PyTorch              | Device・dtype管理            | Tensorとモデルを同じ計算装置・数値型へ配置し、不一致によるエラーを防ぐため                             | CPU・利用可能なAccelerator間でTensorとモデルを移動し、用途に応じてdtypeを確認・変換できること                        |
| 第3段階 | Neural Network | 学習処理             | Automatic Differentiation    | Tensorの演算履歴から勾配計算を自動化し、手計算したBackpropagationをPyTorchで実行するため               | BackpropagationとAutomatic Differentiationの関係を説明し、requires_grad、grad、grad_fn、detachの役割を説明できること |
| 第3段階 | Neural Network | PyTorch              | zero_grad・backward・step    | 1回の学習Stepで必要な勾配の初期化、計算、パラメータ更新を正しい順序で一体として理解するため            | 勾配が既定で蓄積されることを説明し、zero_grad→Forward→Loss→backward→stepを実装できること                             |
| 第3段階 | Neural Network | PyTorch              | Training Loop                | DataLoaderからのBatch取得と学習StepをEpoch単位で反復し、モデルを学習させるため                         | Batch取得、Device転送、Forward、Loss、勾配計算、更新を含むTraining Loopを実装できること                              |
| 第3段階 | Neural Network | PyTorch              | train・eval・推論モード      | DropoutやBatchNormの動作を学習・評価で切り替え、不要な勾配計算を止めるため                             | model.train、model.eval、no_gradまたはinference_modeを適切に使い分けられること                                       |
| 第3段階 | Neural Network | PyTorch              | state_dict・モデル保存       | 学習済みパラメータとOptimizer状態を保存し、評価・再開・後続段階のCheckpointに利用するため              | モデルとOptimizerのstate_dictを保存・読み込みし、推論または学習を再開できること                                      |

## 到達目標

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

[前の段階](02_第2段階_機械学習基礎.md) ｜ [全体概要・目次](Readme.md) ｜ [次の段階](04_第4段階_Transformer.md)
