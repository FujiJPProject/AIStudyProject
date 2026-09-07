# 第3段階：Neural Network

[前の段階](02_第2段階_機械学習基礎.md) ｜ [全体概要・目次](00_全体概要・目次.md) ｜ [次の段階](04_第4段階_Transformer.md)

## この段階の位置づけ

|項目|内容|
|:--|:--|
|学習テーマ|Neural Network|
|最終的に理解するもの|Deep Learningがどのように学習するか|
|学習項目数|34項目|

## 学習項目一覧

|段階|学習テーマ|分野|項目|学習する理由|取得するべき内容|
|:--|:--|:--|:--|:--|:--|
|第3段階|Neural Network|ニューラルネット基礎|Neuron|ニューラルネットの最小構成単位を理解するため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|入力・重み・バイアス・出力の関係を説明できること|
|第3段階|Neural Network|ニューラルネット基礎|Weight|モデルが学習する対象を理解するため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|Weightが入力へ与える影響を説明できること|
|第3段階|Neural Network|ニューラルネット基礎|Bias|線形変換の自由度を高めるため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|Biasの役割を説明できること|
|第3段階|Neural Network|ニューラルネット基礎|Layer|複数段階の特徴変換を理解するため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|Input・Hidden・Output Layerを説明できること|
|第3段階|Neural Network|活性化関数|Sigmoid|非線形性の基本を理解するため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|Sigmoidの特徴を説明できること|
|第3段階|Neural Network|活性化関数|ReLU|Deep Learningで広く使われるため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|ReLUの特徴と問題点を説明できること|
|第3段階|Neural Network|活性化関数|GELU|Transformerで利用されるため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|GELUの特徴を説明できること|
|第3段階|Neural Network|活性化関数|SiLU|現代LLMでも利用されるため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|SiLUの特徴を説明できること|
|第3段階|Neural Network|学習処理|Forward Propagation|入力から予測を生成する流れを理解するため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|Forward処理を数式・コードで追跡できること|
|第3段階|Neural Network|学習処理|Computational Graph|複雑な計算と微分の依存関係を理解するため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|計算グラフを追えること|
|第3段階|Neural Network|学習処理|Backpropagation|ニューラルネット学習の中心原理だから。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|誤差が各パラメータへ伝播する仕組みを説明できること|
|第3段階|Neural Network|学習処理|Automatic Differentiation|PyTorchの自動微分を理解するため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|autogradが何をしているか説明できること|
|第3段階|Neural Network|PyTorch|Tensor|PyTorchの基本データ構造だから。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|Tensorの生成・形状変更・演算に加え、dtype・device・requires_grad・detachを扱えること|
|第3段階|Neural Network|PyTorch|nn.Module|モデルを構築する基本クラスだから。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|独自モデルクラスを実装できること|
|第3段階|Neural Network|PyTorch|nn.Linear|ニューラルネットの線形変換を実装するため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|全結合層を利用・説明できること|
|第3段階|Neural Network|PyTorch|loss.backward|Backpropagationを実行するため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|勾配計算の流れを理解できること|
|第3段階|Neural Network|PyTorch|optimizer.step|モデルパラメータを更新するため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|zero_grad→Forward→Loss→Backward→optimizer.stepの順序で1回の学習Stepを実装できること|
|第3段階|Neural Network|学習技法|Batch|複数データを効率的に学習するため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|Batch Sizeが勾配推定のばらつき・メモリ使用量・計算効率・学習率へ与える影響を説明できること|
|第3段階|Neural Network|学習技法|Epoch|データセットを何回学習したか管理するため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|EpochとIterationの違いを説明できること|
|第3段階|Neural Network|学習技法|Weight Initialization|学習の安定性を高めるため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|対称性を避ける理由を説明し、活性化関数に応じてXavier・He初期化を使い分けられること|
|第3段階|Neural Network|学習技法|Normalizationの種類|学習を安定させるため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|データ正規化・BatchNorm・LayerNorm・RMSNormの対象軸と目的を区別し、Transformerで使う方式を説明できること|
|第3段階|Neural Network|学習技法|Dropout|過学習を抑制するため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|Dropoutの仕組みを説明できること|
|第3段階|Neural Network|学習技法|Gradient Clipping|勾配爆発を抑えるため。Transformer以降のモデル構造と学習処理を理解・実装する前提として必要であるため|勾配を制限する理由を説明できること|
|第3段階|Neural Network|ニューラルネット基礎|Multi-Layer Perceptron|複数のLinear層と活性化関数を組み合わせる基本モデルを理解するため。個々のNeuronとLayerから、実際に学習可能なネットワークへ組み立てる中間概念が不足している|MLPを数式とPyTorchの両方で構築し、非線形な関係を学習させられること|
|第3段階|Neural Network|活性化関数|Softmax|複数のスコアを確率分布へ変換するため。多クラス分類と次Token予測をニューラルネットの出力層へ接続する項目が不足している|Softmaxの出力が合計1になることと、Logit・確率・Cross Entropyの関係を説明できること|
|第3段階|Neural Network|活性化関数|Gated Linear Unit・SwiGLU|情報を通す量を学習可能なGateで制御するため。SiLU単体から現代LLMで一般的なGated FFNへつなぐ項目が不足している|GLUの基本構造と、SiLUを使うSwiGLUがLLMのFFNで果たす役割を説明できること|
|第3段階|Neural Network|学習処理|勾配消失・勾配爆発|深いネットワークで学習が不安定になる原因を理解するため。活性化関数、初期化、Normalization、Residual、Gradient Clippingの必要性を統合して理解する項目がない|層をまたぐ勾配が小さくなる・大きくなる条件と代表的な対策を説明できること|
|第3段階|Neural Network|PyTorch|nn.Parameter・パラメータ登録|Optimizerが更新するTensorをモデルへ登録する仕組みを理解するため。通常のTensorと学習対象Parameterの違いが既存項目に含まれていない|nn.Parameter、parameters、state_dictの関係を説明し、学習対象を確認できること|
|第3段階|Neural Network|PyTorch|Dataset・DataLoader|データをBatch単位で学習処理へ供給するため。簡単なモデルを実際のデータで学習させる入出力パイプラインが不足している|Datasetを定義し、DataLoaderでBatch化・Shuffleして反復できること|
|第3段階|Neural Network|PyTorch|optimizer.zero_grad|前回の勾配を意図せず次の更新へ加算しないため。loss.backwardとoptimizer.stepの間を正しく構成するための必須操作が既存項目にない|PyTorchでは勾配が蓄積されることを説明し、適切な位置で勾配を初期化できること|
|第3段階|Neural Network|PyTorch|Device・dtype管理|CPU・GPUと数値精度を意識してTensorとモデルを配置するため。GPU学習時のdevice不一致やdtype不一致を防ぐ基本操作が不足している|モデルとTensorを同じdeviceへ移し、用途に応じたdtypeを確認・設定できること|
|第3段階|Neural Network|PyTorch|train・eval・推論モード|学習時と評価時でDropoutなどの動作を正しく切り替えるため。学習結果を正しく評価・推論するために必要なモード切替が既存項目にない|model.train、model.eval、no_gradまたはinference_modeを適切に使えること|
|第3段階|Neural Network|PyTorch|Training Loop|データ取得からパラメータ更新までを一続きで実装するため。個別APIは列挙されているが、簡単なニューラルネットを学習させる全体手順が明示されていない|Batch取得、Forward、Loss、zero_grad、Backward、stepを正しい順序で実装できること|
|第3段階|Neural Network|PyTorch|state_dict・モデル保存|学習済みモデルを保存し、評価や再学習に利用するため。実験の継続、最良モデルの評価、後続段階のCheckpoint理解に必要な基本操作が不足している|モデルとOptimizerのstate_dictを保存・読み込みできること|

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

[前の段階](02_第2段階_機械学習基礎.md) ｜ [全体概要・目次](00_全体概要・目次.md) ｜ [次の段階](04_第4段階_Transformer.md)
