# 第7段階：ChatGPT型システム

[前の段階](06_第6段階_Fine-tuning.md) ｜ [全体概要・目次](Readme.md) ｜ [次の段階](08_最終段階_LLM_Training.md)

## この段階の位置づけ

| 項目                 | 内容                              |
| :------------------- | :-------------------------------- |
| 学習テーマ           | ChatGPT型システム                 |
| 最終的に理解するもの | LLMを実用的なAIサービスにする方法 |
| 学習項目数           | 55項目                            |

## 学習項目一覧

| 段階    | 学習テーマ        | 分野               | 項目                                              | 学習する理由                                                                                | 取得するべき内容                                                                                                                        |
| :------ | :---------------- | :----------------- | :------------------------------------------------ | :------------------------------------------------------------------------------------------ | :-------------------------------------------------------------------------------------------------------------------------------------- |
| 第7段階 | ChatGPT型システム | モデル連携         | Model・API選定とVersion管理                       | 用途に合う能力、Context Length、Tool対応、Latency、Costを持つModelと提供方式を選ぶため      | Model ID・Snapshot、対応機能、Data取扱条件、Fallback、Deprecationを比較し、固定・移行・Rollback方針を決められること                     |
| 第7段階 | ChatGPT型システム | Prompt Engineering | System Prompt・Few-shot                           | Modelの役割・制約と望ましい入出力例を一体として設計し、応答を安定させるため                 | 命令階層と信頼境界を踏まえてSystem Promptを設計し、必要な場合に代表例・境界例をFew-shotとして追加できること                             |
| 第7段階 | ChatGPT型システム | Prompt Engineering | Structured Output                                 | Model出力を後続Programから安全に解析するため                                                | Schemaで型、必須項目、列挙値、追加Propertyを制約し、構造の妥当性と内容の正しさを分けて検証できること                                    |
| 第7段階 | ChatGPT型システム | Prompt Engineering | Prompt・設定のVersion管理                         | Prompt変更による品質差を再現し、Regressionの原因を追跡するため                              | Prompt、Model、Sampling設定、Structured Output Schema、Tool定義をVersion化し、評価結果と対応付けられること                              |
| 第7段階 | ChatGPT型システム | Context Management | Context Window管理・要約・Compaction              | 有限のContextへ必要な情報を収め、長い会話でも重要情報を維持するため                         | Token数を計測し、優先順位付け、Truncation、構造化要約、Compactionを使い分け、圧縮前後の情報欠落を検証できること                         |
| 第7段階 | ChatGPT型システム | Inference          | GPU・VRAM                                         | LLM推論の計算基盤と、Model・Context・同時Request数を制約するMemoryを理解するため            | CPUとGPUの違いを説明し、Model Weightと実行時に必要な領域からModel Sizeと必要VRAMを概算できること                                        |
| 第7段階 | ChatGPT型システム | Inference          | KV Cache                                          | 生成済みTokenのKey・Valueを再利用してAutoregressive推論を高速化するため                     | KV Cacheが計算量、Context Length、Batch Size、VRAMに与える影響を説明できること                                                          |
| 第7段階 | ChatGPT型システム | Inference          | Batch Inference・Continuous Batching              | 複数Requestをまとめ、GPU利用率とThroughputを高める方法を比較するため                        | 固定Batchと、完了したSequenceを入れ替えるContinuous Batchingの違いを説明し、LatencyとのTrade-offを評価できること                        |
| 第7段階 | ChatGPT型システム | Backend            | REST API・FastAPI                                 | LLM機能をHTTP経由で提供する基本InterfaceをPythonで実装するため                              | Resource、Method、Status Code、Request・Response Schemaを設計し、FastAPIでEndpoint、Validation、Error Responseを実装できること          |
| 第7段階 | ChatGPT型システム | Backend            | Database                                          | User、会話、Message、実行状態、評価結果を永続化するため                                     | Entity間の関係、Transaction、Index、Migrationを設計し、必要なDataを保存・取得できること                                                 |
| 第7段階 | ChatGPT型システム | Backend            | Authentication                                    | Requestの送信者が誰であるかを確認するため                                                   | Session、API Key、OAuth・OIDCなどの方式を比較し、Credential検証とUser Identityの確立を実装できること                                    |
| 第7段階 | ChatGPT型システム | Backend            | Authorization                                     | 認証済みのUserがどの会話、Dataset、Tool、操作へアクセスできるか制御するため                 | Role・Scope・Resource Ownershipを用いて認可Policyを設計し、Backendと下流Systemで毎回強制できること                                      |
| 第7段階 | ChatGPT型システム | Security           | Secrets Management                                | LLM・Tool・DatabaseのCredentialをCode、Client、Prompt、Logへ露出させないため                | 環境別のSecret保管、最小権限、Rotation、漏洩時の失効、Log Redactionを実装できること                                                     |
| 第7段階 | ChatGPT型システム | Backend            | API連携・Timeout・Retry・Rate Limit・Idempotency  | LLMや外部Serviceの一時障害・制限・重複実行に耐えるため                                      | 認証、入出力Validation、Timeout、Retry可能なErrorの分類、指数Backoff、Rate Limit、Idempotency Key、Fallbackを組み合わせて実装できること |
| 第7段階 | ChatGPT型システム | Backend            | Streaming・中断処理                               | 最初のTokenを早く表示し、不要な生成とCostを途中で止めるため                                 | Streaming EventをUIへ転送し、切断、Cancel、部分出力、再接続、Errorを一貫して処理できること                                              |
| 第7段階 | ChatGPT型システム | Memory             | Conversation History                              | 会話を永続化しつつ、Modelへ渡すContextを用途に応じて選択するため                            | 保存する履歴と投入する履歴を分け、Message順序、Tool履歴、Token Budget、要約との対応を管理できること                                     |
| 第7段階 | ChatGPT型システム | RAG                | Chunking                                          | 長い文書を意味のある検索単位へ分割するため                                                  | 文書構造、意味境界、Chunk Size、Overlap、Metadata、検索後のContext再構成を考慮してChunkingを設計できること                              |
| 第7段階 | ChatGPT型システム | RAG                | Embedding Model                                   | Queryと文書を意味検索に利用できるVectorへ変換するため                                       | 対象言語・Domain・次元・類似度尺度を確認し、同じEmbedding Modelと前処理でQuery・ChunkをVector化できること                               |
| 第7段階 | ChatGPT型システム | RAG                | Vector Database                                   | EmbeddingとMetadataを保存し、近似最近傍検索を実行するため                                   | Collection・Index、距離尺度、Metadata、Upsert・Deleteを設計し、Top-k検索を実装できること                                                |
| 第7段階 | ChatGPT型システム | RAG                | Ingestion・Index Lifecycle                        | 文書の追加・更新・削除を検索Indexへ継続的に反映するため                                     | 取得、Parse、Chunk、Embedding、Index、Version、再Index、削除を冪等なPipelineとして設計できること                                        |
| 第7段階 | ChatGPT型システム | RAG                | Semantic・Keyword・Hybrid Search・Metadata Filter | 質問と文書の性質に応じて、意味類似、完全一致、属性条件を組み合わせるため                    | Vector・Keyword検索の長所と弱点を説明し、Score統合と日付・種類・Tenant・権限によるFilterを実装・比較できること                          |
| 第7段階 | ChatGPT型システム | RAG                | Query Rewrite・Multi-query                        | 会話的で曖昧な質問を検索に適した表現へ変換し、Recallを改善するため                          | 会話Contextを補完したQueryと複数の検索Queryを生成し、検索結果を統合・重複除去できること                                                 |
| 第7段階 | ChatGPT型システム | RAG                | Reranking                                         | 一次検索で得た候補をQueryとの関連度で再評価し、生成へ渡すContextの精度を高めるため          | Cross-encoderやRerankerを用いて候補を再順位付けし、候補数・精度・LatencyのTrade-offを評価できること                                     |
| 第7段階 | ChatGPT型システム | RAG                | Access-control-aware Retrieval                    | Userが閲覧可能な文書だけを検索・生成へ利用するため                                          | 認可情報を検索前Filterへ反映し、取得後にも文書・Chunk単位で権限を再検証できること                                                       |
| 第7段階 | ChatGPT型システム | RAG                | Citation・Source Attribution                      | 回答中の主張を根拠へ結び付け、利用者が検証できるようにするため                              | 取得Chunkと主張を対応付け、Source Link、文書Version、該当箇所を提示し、引用が根拠を実際に支持するか検証できること                       |
| 第7段階 | ChatGPT型システム | Memory             | Long-term Memory                                  | 必要な情報をSessionを超えて保持し、後の会話で再利用するため                                 | 保存対象、抽出根拠、信頼度、検索、更新、競合、誤記憶訂正を含む長期MemoryのLifecycleを設計できること                                     |
| 第7段階 | ChatGPT型システム | Memory             | Retention・Consent・Deletion                      | 長期Memoryや履歴を必要以上に保持せず、Userの選択とPrivacy要件を反映するため                 | 保存目的、保存期間、同意、Export、訂正、削除、削除伝播、Auditの要件を設計できること                                                     |
| 第7段階 | ChatGPT型システム | Tool Calling       | Function Calling                                  | Modelの出力を、Applicationが管理する外部機能の呼出しへ接続するため                          | Tool Schemaの提示、Tool選択、引数Validation、実行、結果返却、複数回呼出しまでのProtocolを実装できること                                 |
| 第7段階 | ChatGPT型システム | Security           | Output Validation・Sanitization                   | Model出力をHTML、SQL、Code、Tool引数として利用する際のInjectionや不正操作を防ぐため         | Schema検証、Escape、Parameterize、Allowlist、Sandboxを適用し、Model出力を命令として無条件に実行しないこと                               |
| 第7段階 | ChatGPT型システム | Agent              | WorkflowとAgentの使い分け                         | 決定的な処理とModel判断が必要な処理を分離し、不要な自律性を避けるため                       | 固定Workflow、State Machine、LLM Agentを再現性、柔軟性、Cost、Riskから選択できること                                                    |
| 第7段階 | ChatGPT型システム | Agent              | Tool Selection                                    | 目的と現在の状態に応じて、利用可能なToolから適切なものを選ばせるため                        | Tool名・説明・Schema・選択条件を設計し、不要・権限外のToolを候補から除外できること                                                      |
| 第7段階 | ChatGPT型システム | Agent              | Planning                                          | 複雑なTaskを実行可能なStepへ分解し、順序と依存関係を決めるため                              | 目標、制約、前提条件、完了条件を基にPlanを作り、実行結果に応じて更新できること                                                          |
| 第7段階 | ChatGPT型システム | Agent              | State Management                                  | 複数Stepにまたがる入力、判断、Tool結果、進捗を一貫して保持するため                          | State Schemaと状態遷移を定義し、再開、重複実行、並行更新を考慮して永続化できること                                                      |
| 第7段階 | ChatGPT型システム | Agent              | 停止条件・Loop・実行Budget                        | Agentの無限Loopと過剰なTool利用を防ぎ、処理を確実に収束させるため                           | 最大Step、時間、Token、Cost、Retry回数、成功・失敗・部分完了の終了状態を定義できること                                                  |
| 第7段階 | ChatGPT型システム | Agent              | Tool結果Validation・Error Recovery                | 不正・不完全なTool結果や外部障害を後続判断へ連鎖させないため                                | Schema・意味・権限を検証し、Error分類、Retry、代替Tool、部分完了、Compensationを設計できること                                          |
| 第7段階 | ChatGPT型システム | Agent              | Human-in-the-loop・Approval                       | 送信、購入、削除、権限変更などの高影響操作を実行前に人が確認するため                        | 承認対象、変更内容のPreview、承認者、Timeout、拒否、取消可能性を設計し、承認結果を記録できること                                        |
| 第7段階 | ChatGPT型システム | 運用               | Token・Cost・Latency Budget                       | Context、検索、生成、Tool実行の資源使用量をSystem全体で制御するため                         | 入力・出力Token、検索件数、Tool回数、処理時間、金額に上限を設定し、超過時の縮退処理を定められること                                     |
| 第7段階 | ChatGPT型システム | Security           | Prompt Injection・Jailbreak                       | User入力や外部文書による命令乗っ取りと、安全Policy回避のRiskをまとめて理解するため          | 直接・間接Prompt InjectionとJailbreakの関係を説明し、外部Dataの分離、最小権限、出力検証、承認を組み合わせた多層防御を設計できること     |
| 第7段階 | ChatGPT型システム | Security           | Data Leakage                                      | Prompt、RAG、Memory、Log、Cache、Tool、Model Providerを通じた機密情報流出を防ぐため         | Data Flowと信頼境界を可視化し、送信・保存・表示ごとの最小化、Access Control、暗号化、Redactionを設計できること                          |
| 第7段階 | ChatGPT型システム | Security           | Tool Abuse                                        | Agentへ与えた機能・権限・自律性が危険な操作へ使われることを防ぐため                         | Toolの機能、権限、自律性を最小化し、破壊的・高影響操作へ認可、承認、Sandbox、監査を適用できること                                       |
| 第7段階 | ChatGPT型システム | Security           | Guardrails・Moderation                            | 用途外・有害・機密性の高い入出力を検知し、Policyに従って処理するため                        | Policy分類、PII検出、拒否、変換、Human Escalationを設計し、誤検知と見逃しを評価できること                                               |
| 第7段階 | ChatGPT型システム | Security           | Tenant Isolation                                  | 複数User・組織のData、Cache、Memory、Credentialが混在することを防ぐため                     | Database、Vector Store、Cache、Log、Tool CredentialでTenant境界を強制し、越境Access Testを実施できること                                |
| 第7段階 | ChatGPT型システム | Security           | Supply Chain・依存関係管理                        | Model、Dataset、Package、Tool、MCPなど外部Componentの改ざん・脆弱性・更新Riskを管理するため | 出所、Version、署名・Hash、既知脆弱性、権限、更新内容を確認し、固定・検証・Rollbackできること                                           |
| 第7段階 | ChatGPT型システム | 運用               | Cache                                             | 重複するPrompt、検索、生成、Embedding処理を減らしてLatencyとCostを抑えるため                | Cache Key、TTL、無効化、Data Version、Tenant・権限境界、非決定的出力の扱いを設計できること                                              |
| 第7段階 | ChatGPT型システム | 運用               | Logging・Metrics・Tracing                         | Request全体を通してModel、RAG、Tool、Agentの失敗箇所を追跡するため                          | Request・Trace ID、Latency、Token、検索結果、Tool Call、状態遷移、Error、評価結果を相関付け、機密情報を除いて観測できること             |
| 第7段階 | ChatGPT型システム | 運用               | Audit Log                                         | 高影響操作とSecurity Eventについて、後から変更主体と経緯を確認するため                      | 誰が、いつ、どの権限で、何を入力し、どのToolが何を変更したかを改ざん耐性とRetentionを考慮して記録できること                             |
| 第7段階 | ChatGPT型システム | 評価               | Golden Dataset・Regression Test                   | Prompt、Model、RAG、Tool変更による品質低下を継続的に検出するため                            | 代表例、境界例、既知の失敗例を期待結果・採点基準とともにVersion化し、変更前後で評価を再実行できること                                   |
| 第7段階 | ChatGPT型システム | 評価               | Human Evaluation                                  | 自動指標では測りにくい有用性、正確性、明瞭さ、安全性を評価するため                          | 評価Rubric、評価者への指示、Blind比較、一致度、自由記述を設計し、再現可能な人手評価を実施できること                                     |
| 第7段階 | ChatGPT型システム | 評価               | LLM-as-a-Judge                                    | 人手評価を補助しながら大量の回答を同じ基準で評価するため                                    | 位置・長さ・文体Bias、Judgeの誤り、基準漏洩を考慮し、人手評価との相関、再現性、Calibrationを検証できること                              |
| 第7段階 | ChatGPT型システム | 評価               | Hallucination Evaluation                          | 生成内容が提示された根拠や外部事実と矛盾していないか測るため                                | 根拠整合性、外部事実性、引用正確性、不明時の棄権を分け、検証可能なDatasetと基準で評価できること                                         |
| 第7段階 | ChatGPT型システム | 評価               | RAG Evaluation                                    | RAGの失敗を検索段階と生成段階へ分けて特定するため                                           | Recall・Precision・RankingなどのRetrieval指標と、Context Relevance・Groundedness・Answer Qualityを個別に評価できること                  |
| 第7段階 | ChatGPT型システム | 評価               | Trace Evaluation                                  | 最終回答だけでなく、検索、Tool選択、引数、状態遷移の妥当性を評価するため                    | TraceへStep単位の基準を適用し、不要・危険・失敗した経路とRegression箇所を特定できること                                                 |
| 第7段階 | ChatGPT型システム | 評価               | Latency・Cost・Reliability・SLO                   | 品質以外の実用性を継続的に測り、運用目標を定めるため                                        | Percentile Latency、Error率、Availability、Token Cost、ThroughputのSLI・SLOとAlert条件を設定できること                                  |
| 第7段階 | ChatGPT型システム | 評価               | Red Team・Adversarial Test                        | 通常の評価では見つけにくい安全性・権限・堅牢性の弱点を発見するため                          | Prompt Injection、権限逸脱、Data抽出、Tool悪用、長文・難読化入力を含む攻撃的Testを継続実行し、対策後に再検証できること                  |
| 第7段階 | ChatGPT型システム | 運用               | Incident Response                                 | 監視・評価・通報で発見した問題の影響を封じ込め、復旧と再発防止を行うため                    | 検知、分類、停止、Credential失効、Data保全、通知、復旧、事後分析、改善追跡の手順と責任者を定義できること                                |

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

[前の段階](06_第6段階_Fine-tuning.md) ｜ [全体概要・目次](Readme.md) ｜ [次の段階](08_最終段階_LLM_Training.md)
