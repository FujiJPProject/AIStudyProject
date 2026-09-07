# 第7段階：ChatGPT型システム

[前の段階](06_第6段階_Fine-tuning.md) ｜ [全体概要・目次](00_全体概要・目次.md) ｜ [次の段階](08_最終段階_LLM_Training.md)

## この段階の位置づけ

|項目|内容|
|:--|:--|
|学習テーマ|ChatGPT型システム|
|最終的に理解するもの|LLMを実用的なAIサービスにする方法|
|学習項目数|61項目|

## 学習項目一覧

|段階|学習テーマ|分野|項目|学習する理由|取得するべき内容|
|:--|:--|:--|:--|:--|:--|
|第7段階|ChatGPT型システム|Prompt Engineering|System Prompt|AIの役割・制約を設定するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|命令階層を踏まえ、信頼できる指示と外部入力を分離し、変更可能なPolicyとしてSystem Promptを設計できること|
|第7段階|ChatGPT型システム|Prompt Engineering|Few-shot|例示によって出力を誘導するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|Few-shot Promptを設計できること|
|第7段階|ChatGPT型システム|Prompt Engineering|Structured Output|後続システムでAI出力を利用するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|Schemaで型・必須項目・列挙値を制約・検証し、構造の妥当性と内容の正しさを分けて確認できること|
|第7段階|ChatGPT型システム|Context Management|Context Window管理|長い会話や文書を効率的に扱うため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|Token数を計測し、優先順位付け・Truncation・要約・Compaction・検索による再投入を使い分け、情報欠落を検証できること|
|第7段階|ChatGPT型システム|RAG|Embedding Model|文章を検索可能なベクトルへ変換するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|Embeddingを生成・利用できること|
|第7段階|ChatGPT型システム|RAG|Vector Database|Embeddingを保存・検索するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|Vector DBを利用できること|
|第7段階|ChatGPT型システム|RAG|Chunking|長文書を検索単位へ分割するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|文書構造・意味境界・Chunk Size・Overlap・Metadata・検索後のContext再構成を考慮してChunkingを設計できること|
|第7段階|ChatGPT型システム|RAG|Semantic Search|意味的に近い情報を検索するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|Vector検索を実装し、Keyword検索・Hybrid検索・Metadata Filterとの使い分けを評価できること|
|第7段階|ChatGPT型システム|RAG|Reranking|検索候補の精度を改善するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|検索結果を再順位付けできること|
|第7段階|ChatGPT型システム|Tool Calling|Function Calling|LLMから外部機能を利用させるため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|Tool Schema、Tool選択、引数Validation、実行、結果返却、複数回呼出しまでのProtocolを実装できること|
|第7段階|ChatGPT型システム|Tool Calling|API連携|外部サービスとLLMを接続するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|認証・Timeout・Retry・Rate Limit・Idempotency・入出力Validation・Fallbackを含めてAPI連携を実装できること|
|第7段階|ChatGPT型システム|Agent|Tool Selection|状況に応じて適切なToolを選択させるため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|Tool選択ロジックを設計できること|
|第7段階|ChatGPT型システム|Agent|Planning|複雑な作業を複数Stepへ分解するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|タスクを計画・実行するAgentを設計できること|
|第7段階|ChatGPT型システム|Agent|State Management|複数Stepにまたがる状態を保持するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|Agent状態を管理できること|
|第7段階|ChatGPT型システム|Memory|Conversation History|会話の継続性を持たせるため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|履歴の永続化とModelへ投入するContextを分け、選択・要約・Token Budget・Tool履歴を管理できること|
|第7段階|ChatGPT型システム|Memory|Long-term Memory|セッションを超えて情報を保持するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|保存対象・抽出根拠・同意・信頼度・更新・削除・検索・誤記憶訂正を含む長期記憶Lifecycleを設計できること|
|第7段階|ChatGPT型システム|Backend|REST API|LLM機能を他システムへ提供するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|APIを設計・実装できること|
|第7段階|ChatGPT型システム|Backend|FastAPI|PythonでAI Backendを構築するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|FastAPIでLLM APIを構築できること|
|第7段階|ChatGPT型システム|Backend|Authentication・Authorization|ユーザーアクセスを制御するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|本人確認と、Dataset・会話・Toolごとの権限制御を分離して設計できること|
|第7段階|ChatGPT型システム|Backend|Database|ユーザー・会話・ログを保存するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|DBへ永続化できること|
|第7段階|ChatGPT型システム|Inference|GPU|LLM推論の計算基盤を理解するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|GPUとCPUの違いを説明できること|
|第7段階|ChatGPT型システム|Inference|VRAM|モデルをGPUへ載せる制約を理解するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|モデルサイズとVRAMの関係を概算できること|
|第7段階|ChatGPT型システム|Inference|KV Cache|LLM推論を高速化するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|KV Cacheの役割を説明できること|
|第7段階|ChatGPT型システム|Inference|Batch Inference|複数リクエストを効率的に処理するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|Batch処理の利点を説明できること|
|第7段階|ChatGPT型システム|Inference|Continuous Batching|LLM Servingのスループットを向上させるため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|Continuous Batchingを説明できること|
|第7段階|ChatGPT型システム|評価|Human Evaluation|自動指標では測れない品質を評価するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|人手評価基準を設計できること|
|第7段階|ChatGPT型システム|評価|LLM-as-a-Judge|大量の回答を効率よく評価するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|位置・長さ・文体Bias、Judgeの誤り、基準漏洩を考慮し、人手評価との相関と再現性を検証できること|
|第7段階|ChatGPT型システム|評価|Hallucination Evaluation|誤情報生成を検出するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|根拠整合性・外部事実性・引用正確性・不明時の棄権を分けて評価できること|
|第7段階|ChatGPT型システム|評価|RAG Evaluation|検索と生成を分離して評価するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|Retrieval・Answerを個別に評価できること|
|第7段階|ChatGPT型システム|Security|Prompt Injection|外部入力による命令乗っ取りを防ぐため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|攻撃例と防御策を説明できること|
|第7段階|ChatGPT型システム|Security|Jailbreak|安全制約の回避攻撃を理解するため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|Prompt Injectionとの重なりと違いを説明し、Policy回避を目的とする入力への多層的な対策を設計できること|
|第7段階|ChatGPT型システム|Security|Data Leakage|機密情報流出を防ぐため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|Prompt・RAG・Memory・Log・Cache・Tool引数・Model Provider送信を含むData Flow全体の境界とアクセス制御を設計できること|
|第7段階|ChatGPT型システム|Security|Tool Abuse|Agentによる危険な外部操作を防ぐため。ChatGPT型システムを安全・安定して構築・運用するために必要であるため|Toolの機能・権限・自律性を最小化し、破壊的・高影響操作への承認・監査を設計できること|
|第7段階|ChatGPT型システム|モデル連携|Model・API選定とVersion管理|品質、Latency、Cost、機能要件に合うModelを選び、更新による変化を管理するため。Model更新がPrompt、Tool Calling、出力品質、Costへ影響するため、固定・移行・Rollbackの設計が必要である|Model IDとSnapshot、対応機能、Fallback、Deprecationを記録し、変更前後を評価できること|
|第7段階|ChatGPT型システム|Prompt Engineering|Prompt・設定のVersion管理|Prompt変更を再現可能にし、品質差の原因を追跡するため。Promptをソースコード外で場当たり的に変更すると、Regressionの原因を追跡できないため|Prompt、Model、Sampling設定、Tool定義をVersion化し、評価結果と対応付けられること|
|第7段階|ChatGPT型システム|Backend|Streaming・中断処理|最初のTokenを早く表示し、利用者が不要な生成を停止できるようにするため。Chat型UIの体感Latencyと不要なCostを抑える基本機能が既存項目にない|Streaming EventをUIへ転送し、切断・Cancel・部分出力・Errorを処理できること|
|第7段階|ChatGPT型システム|Backend|Timeout・Retry・Rate Limit・Idempotency|外部APIの一時障害や重複実行へ耐えるため。LLM・Tool APIは失敗や制限が起きるため、単純な再実行では二重処理や障害連鎖を招く|指数Backoff、Retry可能なErrorの判定、Rate Limit、Idempotency Keyを設計できること|
|第7段階|ChatGPT型システム|運用|Token・Cost・Latency Budget|利用者体験と費用を予測可能に保つため。品質だけを最適化すると、長いContextやAgent LoopによってCostとLatencyが制御不能になるため|入力・出力Token、検索件数、Tool回数、処理時間に上限を設定し、利用量を計測できること|
|第7段階|ChatGPT型システム|運用|Cache|重複する検索・生成・Embedding処理を減らすため。LatencyとCostを下げられる一方、古い回答や他UserのData混入を防ぐ設計が必要である|Cache Key、TTL、無効化、権限境界、非決定的出力の扱いを設計できること|
|第7段階|ChatGPT型システム|運用|Logging・Metrics・Tracing|Model、RAG、Tool、Agentのどこで失敗したか追跡するため。最終回答だけではAgentやRAGの内部失敗を診断できず、品質改善とIncident調査が困難になるため|Request ID、Latency、Token、検索結果、Tool Call、Error、評価結果を相関付けて観測できること|
|第7段階|ChatGPT型システム|RAG|Ingestion・Index Lifecycle|文書の追加・更新・削除を検索Indexへ正しく反映するため。初回登録だけでなく、原文更新や削除後も古いChunkを残さない運用が必要である|取得、Parse、Chunk、Embedding、Index、Version、再Index、削除の流れを設計できること|
|第7段階|ChatGPT型システム|RAG|Hybrid Search・Metadata Filter|意味類似度だけでは弱い固有名詞検索と権限制御を補うため。Semantic Search単独では完全一致、鮮度、文書属性、Access条件を十分に扱えないため|Vector・Keyword Scoreを組み合わせ、日付・種類・Tenant・権限で候補を絞り込めること|
|第7段階|ChatGPT型システム|RAG|Query Rewrite・Multi-query|会話的で曖昧な質問を検索に適したQueryへ変換するため。Userの表現と文書中の表現が異なる場合のRecall改善手段が不足している|会話Contextを補完した検索Queryを作り、複数Queryの結果を統合・重複除去できること|
|第7段階|ChatGPT型システム|RAG|Access-control-aware Retrieval|Userが閲覧可能な文書だけを検索・生成へ利用するため。回答段階で隠すだけでは、権限外DataがContextやLogへ流入する可能性があるため|検索前Filterと取得後検証を用い、文書・Chunk単位の権限を強制できること|
|第7段階|ChatGPT型システム|RAG|Citation・Source Attribution|回答の根拠を利用者が確認できるようにするため。RAGで情報を取得しても、どの主張をどのSourceが支えるか確認できなければ信頼性を評価しにくいため|取得したChunkと回答中の主張を対応付け、Source Link・版・該当箇所を提示・検証できること|
|第7段階|ChatGPT型システム|Agent|WorkflowとAgentの使い分け|決定的処理とModel判断が必要な処理を分離するため。すべてをAgentへ委ねると挙動が不安定になり、単純処理までCostとRiskが増えるため|固定Workflow、State Machine、LLM AgentをRisk・再現性・柔軟性から選択できること|
|第7段階|ChatGPT型システム|Agent|停止条件・Loop・実行Budget|Agentが無限Loopや過剰なTool利用へ陥ることを防ぐため。PlanningとStateだけでは、失敗時に処理が収束する保証がないため|最大Step、時間、Token、Cost、Retry回数、終了状態を定義できること|
|第7段階|ChatGPT型システム|Agent|Tool結果Validation・Error Recovery|Toolの失敗や不正な結果から安全に回復するため。Tool出力を無条件に信頼すると、誤Dataや外部障害が後続判断と操作へ連鎖するため|Schema検証、Error分類、Retry、代替Tool、部分完了、Compensationを設計できること|
|第7段階|ChatGPT型システム|Agent|Human-in-the-loop・Approval|高影響操作を実行前に人が確認できるようにするため。送信、購入、削除、権限変更などをModel判断だけで実行させない境界が必要である|承認対象、確認画面、変更内容、取消可能性、Timeout後の扱いを設計できること|
|第7段階|ChatGPT型システム|Memory|要約・Compaction|長い会話をContext上限内へ圧縮しつつ重要情報を保つため。Conversation Historyを全件投入し続ける方式はToken・Cost・Latency上の限界があるため|保持すべき事実、未解決Task、決定、Sourceを構造化して要約し、原履歴へ参照を残せること|
|第7段階|ChatGPT型システム|Memory|Retention・Consent・Deletion|個人情報を必要以上に長く保存せず、利用者の選択を反映するため。長期Memoryには利便性だけでなくPrivacyと誤記憶のRiskが伴うため|保存目的、保存期間、同意、Export、訂正、削除、Auditを設計できること|
|第7段階|ChatGPT型システム|評価|Golden Dataset・Regression Test|Prompt・Model・RAG変更による品質低下を継続的に検出するため。一度の評価だけでは、依存ModelやPrompt更新後の品質を保証できないため|代表例、境界例、失敗例をVersion化し、変更前後で自動・人手評価を再実行できること|
|第7段階|ChatGPT型システム|評価|Trace Evaluation|最終回答だけでなく、検索・Tool選択・引数・状態遷移を評価するため。Agentは正しい最終回答でも危険・非効率な経路を取ることがあり、結果だけの評価では見逃すため|Agent TraceへStep単位の基準を適用し、失敗原因とRegression箇所を特定できること|
|第7段階|ChatGPT型システム|評価|Latency・Cost・Reliability・SLO|品質以外の実用性を定量評価するため。高品質でも遅い、高価、失敗しやすいSystemは実用要件を満たさないため|Percentile Latency、Error率、Availability、Token Cost、Throughputの目標とAlertを設定できること|
|第7段階|ChatGPT型システム|評価|Red Team・Adversarial Test|通常入力では見つからない安全性と堅牢性の弱点を発見するため。平均的な評価Datasetだけでは悪意ある入力や稀な高影響Failureを十分に検出できないため|Prompt Injection、権限逸脱、Data抽出、長文・変形入力を含む攻撃的Testを継続実行できること|
|第7段階|ChatGPT型システム|Security|Output Validation・Sanitization|Model出力をCode、HTML、SQL、Tool引数として安全に利用するため。Structured Outputでも内容が安全とは限らず、不適切な出力処理が別のInjectionや実行被害につながるため|許可Schema、Escape、Parameterize、Allowlist、Sandboxを用い、出力を命令として無条件実行しないこと|
|第7段階|ChatGPT型システム|Security|Guardrails・Moderation|不適切な入力・出力を検知し、用途に応じて処理を制限するため。System Promptだけでは安全Policyを安定して強制できず、多層の制御と評価が必要である|Policy分類、PII検出、拒否、Escalation、誤検知・見逃しの評価を設計できること|
|第7段階|ChatGPT型システム|Security|Secrets Management|API KeyやCredentialをPrompt、Log、Clientへ露出させないため。Toolや外部APIを使うSystemではCredential漏洩が実際のData・操作権限の侵害につながるため|環境別Secret保管、最小権限、Rotation、漏洩時の失効、Log Redactionを実装できること|
|第7段階|ChatGPT型システム|Security|Supply Chain・依存関係管理|Model、Dataset、Package、Tool、MCPなど外部ComponentのRiskを管理するため。ChatGPT型Systemは多くの外部Componentへ依存し、一つの改ざんや更新が全体へ影響するため|出所、Version、署名・Hash、脆弱性、権限、更新内容を確認し、固定・Rollbackできること|
|第7段階|ChatGPT型システム|Security|Tenant Isolation|複数User・組織のDataと権限を混在させないため。認証済みでも、検索・Cache・Memoryの設計ミスにより別UserのDataが漏れる可能性があるため|Database、Vector Store、Cache、Log、Tool CredentialでTenant境界を強制し、越境Testを行えること|
|第7段階|ChatGPT型システム|運用|Audit Log・Incident Response|高影響操作とSecurity Eventを追跡し、問題発生時に封じ込めるため。予防策だけではすべてのFailureを防げず、検知後の対応と説明責任が必要である|誰が、いつ、何を入力し、どのToolが何を変更したか記録し、停止・失効・通知・復旧手順を定義できること|

## 到達目標

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

[前の段階](06_第6段階_Fine-tuning.md) ｜ [全体概要・目次](00_全体概要・目次.md) ｜ [次の段階](08_最終段階_LLM_Training.md)
