
<!-- BEGIN-->
# 『図解Strandsエージェント徹底解説』
---


**[Strands Agent(Apache License 2.0)](https://github.com/strands-agents/samples/blob/main/LICENSE)** は、AWS主導で開発されたオープンソースのAIエージェントSDKで、2025年5月16日に一般公開されました。 

**Strands（ストランズ）** は、PythonまたはTypeScriptで、ツール連携（Tool Use）やマルチエージェントの構築を直感的に行える軽量なフレームワークです。

「もっとシンプルに、そして人間のように自律的に動くエージェントを作りたい」 という開発者の想いから生まれ、LangChainの対抗馬としても注目を集めています。

<img src="images/strands_agent_technical_guide.png" width="400" alt="図解Strandsエージェント徹底解説">



本サイト（『**図解 Strandsエージェント徹底解説**』）は、筆者が Strandsを学習する過程で記録してきたメモをもとに構成しています。

一見すると手間のかかる方法に思えるかもしれませんが、これまでの執筆経験から、膨大な知識体系を短期間で習得するには、「一冊の本を書くようにまとめるアプローチ」が最も効果的であると考えています。

**『図解 Strandsエージェント徹底解説』** が、Strandsエージェントを学ぼうとする皆様の一助となれば幸いです。

なお、筆者の主観による要約や再構成を含んでいるため、掲載内容やサンプルコードの利用にあたっては、ご自身の判断と責任にてお願いいたします。

内容は適宜更新・修正される可能性がありますので、あらかじめご了承ください。


**初めにことばがあった。ことばは神とともにあった。ことばは神であった。**
**（『新改訳聖書』ヨハネの福音書 1:1）** 


2026年1月1日
<br><br>


### 著者プロフィール
---
#### 李 昌桓（LEE CHANFUAN）

- [クリエーションライン株式会社](https://www.creationline.com) に在籍
- 現代的なデータ基盤構築を専門とするソリューションアーキテクト、リードエンジニアとして活動中
- 代表的なプロジェクト:
	- 大手通信キャリアにおけるDWH基盤の設計・構築
	- Donso Factory IoT、ヨドバシカメラ、モノタロウなどにおけるデータモダナイゼーションを推進

#### 著書

- Amazon Cloudテクニカルガイド ― EC2/S3からVPCまで徹底解析、インプレスジャパン、2010
- Amazon Elastic MapReduceテクニカルガイド ― クラウド型Hadoopで実現する大規模分散処理、インプレスジャパン、2012
- Cypherクエリー言語の事例で学ぶ グラフデータベース Neo4j、インプレスR&D、2015
- Neo4jを使うグラフ型データベース入門（共著）、リックテレコム、2016
- RDB技術者のためのNoSQLガイド（共著）、秀和システム新社、2016
- 図解 Strandsエージェント徹底解説、2026（Web公開）  
 ※本書は紙での出版予定はありません。
<br>

### 掲載内容について
---
**『図解 Strandsエージェント徹底解説』** は、基本的に Strands エージェントおよび AWS の公式ドキュメント、ならびに GitHub 上のサンプルコードをベースに構成しています。  
掲載しているサンプルコードの中には、筆者の創意工夫によって独自に作成したものも含まれており、その場合はタイトルの末尾に「＋」を付けて区別しています。

- [Strands User Guide/](https://strandsagents.com/latest/documentation/docs/)
- [Strands Githubs](https://github.com/strands-agents/)
- [Strands Samples](https://github.com/strands-agents/samples)
- [ Strands Python API](https://strandsagents.com/latest/documentation/docs/api-reference/python/agent/agent/)
- [Amazon Bedrock AgentCore Developer Guide](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/what-is-bedrock-agentcore.html)
- [Amazon Bedrock AgentCore Samples](https://github.com/awslabs/amazon-bedrock-agentcore-samples)
<br>

### 著作権・ライセンス
---
本サイトの著作権は著者に帰属します。

 - AI学習・研究目的: 出典を明記の上、自由にご利用いただけます。
 - 営利・二次利用: 無断転載や有償イベントでの利用は禁止します。
 - 改変: 自由ですが、すべて自己責任となります。

 詳細は [LICENSE](LICENSE.md) ファイルをご確認ください。
　<br>

### 章立てについて
---
#### 📌構成
-  [メジャー番号]-[マイナ番号]-[リビジョン番号]
-   [章]-[節]-[項]の構成、又は[章]-[項]の構成
<br>

### 目次 
---
#### 10.基本構成
- [10-00-000.AIエージェントとは](10.基本構成/10-00-000.AIエージェントとは.md)  
- [10-10-010.エージェントループ](10.基本構成/10-10-010.エージェントループ.md)  
- [10-10-020.ステート](10.基本構成/10-10-020.ステート.md)  
- [10-10-030.セッション管理](10.基本構成/10-10-030.セッション管理.md)  
- [10-10-040.プロンプト](10.基本構成/10-10-040.プロンプト.md)  
- [10-10-050.フック](10.基本構成/10-10-050.フック.md)  
- [10-10-060.構造化出力](10.基本構成/10-10-060.構造化出力.md)  
- [10-10-070.会話管理](10.基本構成/10-10-070.会話管理.md)  
- [10-20-010.ツール](10.基本構成/10-20-010.ツール.md)  
- [10-30-010.モデルプロバイダー](10.基本構成/10-30-010.モデルプロバイダー.md)  
- [10-40-010.ストリーミング](10.基本構成/10-40-010.ストリーミング.md)  
- [10-50-010.マルチエージェントパターン](10.基本構成/10-50-010.マルチエージェントパターン.md)  
- [10-50-011.補足](10.基本構成/10-50-011.補足.md)  
- [10-50-020.Agent2Agent(A2A)](10.基本構成/10-50-020.Agent2Agent(A2A).md)  
- [10-50-030.ツール化エージェント](10.基本構成/10-50-030.ツール化エージェント.md)  
- [10-50-040.スウォーム](10.基本構成/10-50-040.スウォーム.md)  
- [10-50-050.グラフ](10.基本構成/10-50-050.グラフ.md)  
- [10-50-060.ワークフロー](10.基本構成/10-50-060.ワークフロー.md)  
- [10-50-070.マルチエージェントの概念](10.基本構成/10-50-070.マルチエージェントの概念.md)  
- [10-60-010.インタラプト](10.基本構成/10-60-010.インタラプト.md)  
　
#### 20.安全性とセキュリティ
- [20-00.安全性とセキュリティの概念](20.安全性とセキュリティ/20-00.安全性とセキュリティの概念.md)  
- [20-10.責任あるAI](20.安全性とセキュリティ/20-10.責任あるAI.md)  
- [20-20.ガードレール](20.安全性とセキュリティ/20-20.ガードレール.md)  
- [20-30.プロンプトエンジニアリング](20.安全性とセキュリティ/20-30.プロンプトエンジニアリング.md)  
- [20-40.個人情報の秘匿化](20.安全性とセキュリティ/20-40.個人情報の秘匿化.md)  
　
#### 30.可観測性とセキュリティ
- [30-00.可観測性とデバックの概念](30.可観測性とデバック/30-00.可観測性とデバックの概念.md)  
- [30-10.メトリック](30.可観測性とデバック/30-10.メトリック.md)  
- [30-20.トレース](30.可観測性とデバック/30-20.トレース.md)  
- [30-30.ログ](30.可観測性とデバック/30-30.ログ.md)  
　
#### 40.評価SDK
- [40-00.評価SDKの概念](40.評価SDK/40-00.評価SDKの概念.md)
　
#### 50.デプロイ
- [50-00.デプロイの概念](50.デプロイ/50-00.デプロイの概念.md)
　
#### 60.実行環境
- [60-00.事前準備](60.実行環境/60-00.事前準備.md)
　
#### 70.サンプルコード
- [70-00-000.サンプルコードについて](70.サンプルコード/70-00-000.サンプルコードについて.md)  
- [70-10-010.シンプルエージェント](70.サンプルコード/70-10-010.シンプルエージェント.md)  
- [70-10-020.レシピボットエージェント](70.サンプルコード/70-10-020.レシピボットエージェント.md)
- [70-10-030.一括生成型エージェントの尻取りゲーム＋](70.サンプルコード/70-10-030.一括生成型エージェントの尻取りゲーム＋.md)
- [70-10-031.外部審判ツール付きエージェントの尻取りゲーム＋](70.サンプルコード/70-10-031.外部審判ツール付きエージェントの尻取りゲーム＋.md)
- [70-10-032.マルチエージェント対戦型の尻取りゲーム＋](70.サンプルコード/70-10-032.マルチエージェント対戦型の尻取りゲーム＋.md)
- [70-10-040-Ollmaファイルオペレーション](70.サンプルコード/70-10-040-Ollmaファイルオペレーション.md)
- [70-20-010.外部ツール連携](70.サンプルコード/70-20-010.外部ツール連携.md)
- [70-20-020.ファイル操作](70.サンプルコード/70-20-020.ファイル操作.md)
- [70-20-040.親子関係ワークフロー](70.サンプルコード/70-20-040.親子関係ワークフロー.md)
- [70-20-050.ナレッジベースワークフロー](70.サンプルコード/70-20-050.ナレッジベースワークフロー.md)
- [70-20-060.構造化出力](70.サンプルコード/70-20-060.構造化出力.md)
- [70-20-070.マルチエージェント](70.サンプルコード/70-20-070.マルチエージェント.md)
- [70-20-080.グラフエージェント](70.サンプルコード/70-20-080.グラフエージェント.md)
- [70-20-081.実行結果](70.サンプルコード/70-20-081.実行結果.md)
- [70-20-090.メタツーリング](70.サンプルコード/70-20-090.メタツーリング.md)
- [70-20-091.実行結果](70.サンプルコード/70-20-091.実行結果.md)
- [70-20-100.MCPサーバ](70.サンプルコード/70-20-100.MCPサーバ.md)
- [70-20-110.マルチモーダル](70.サンプルコード/70-20-110.マルチモーダル.md)
- [70-20-120.ネイティブスウォーム](70.サンプルコード/70-20-120.ネイティブスウォーム.md)
- [70-20-121.実行結果](70.サンプルコード/70-20-121.実行結果.md)
- [70-30-010.朝まで生テレビーベーシンク版＋](70.サンプルコード/70-30-010.朝まで生テレビーベーシンク版＋.md)
- [70-30-011.朝まで生テレビーAgentCore版＋](70.サンプルコード/70-30-011.朝まで生テレビーAgentCore版＋.md)
- [70-30-012.朝まで生テレビー短期記憶版＋](70.サンプルコード/70-30-012.朝まで生テレビー短期記憶版＋.md)
- [70-30-013.短期記憶の検索＋](70.サンプルコード/70-30-013.短期記憶の検索＋.md)
- [70-30-020.朝まで生テレビー長期記憶版＋](70.サンプルコード/70-30-020.朝まで生テレビー長期記憶版＋.md)
- [70-30-021.長期記憶の検索＋](70.サンプルコード/70-30-021.長期記憶の検索＋.md)
- [70-90-010.TexToSQL＋](70.サンプルコード/70-90-010.TexToSQL＋.md)
- [70-90-011.実行結果](70.サンプルコード/70-90-011.実行結果.md)
-  [70-90-020.足立区粗大ごみ判定＋](70.サンプルコード/70-90-020.足立区粗大ごみ判定＋.md)
-  [70-90-021.画像から判定＋](70.サンプルコード/70-90-021.画像から判定＋.md)

#### 80.Bedrok AgentCore
- [80-00-000.AgentCoreとは](80.AmazonBedrockAgentCore/80-00-000.AgentCoreとは.md)  
- [80-10-010.ゲートウェイ](80.AmazonBedrockAgentCore/80-10-010.ゲートウェイ.md)  
- [80-10-012.ターゲット](80.AmazonBedrockAgentCore/80-10-012.ターゲット.md)  
- [80-10-020.ポリシー](80.AmazonBedrockAgentCore/80-10-020.ポリシー.md)  
- [80-10-030.メモリ(記憶)](80.AmazonBedrockAgentCore/80-10-030.メモリ(記憶).md)  
- [80-10-031.短期記憶](80.AmazonBedrockAgentCore/80-10-031.短期記憶.md)  
- [80-10-032.長期記憶(オプション)](80.AmazonBedrockAgentCore/80-10-032.長期記憶(オプション).md)  
- [80-10-040.アイデンティティ](80.AmazonBedrockAgentCore/80-10-040.アイデンティティ.md)  
- [80-10-050.ブラウザー](80.AmazonBedrockAgentCore/80-10-050.ブラウザー.md)  
- [80-10-060.コードインタープリター](80.AmazonBedrockAgentCore/80-10-060.コードインタープリター.md)  
- [80-20-010.ラインタイム](80.AmazonBedrockAgentCore/80-20-010.ランタイム.md) 
- [80-30-010.可観測性](80.AmazonBedrockAgentCore/80-30-010.可観測性.md)  
- [80-30-020.評価](80.AmazonBedrockAgentCore/80-30-020.評価.md) 
　
#### 80.Bedrock Knowledge Base
- [81-00.BedrockKnowldegeBaseとは](81.BedrockKnowledgeBase/81-00.BedrockKnowldegeBaseとは.md)
- [81-11.プロビジョニング](81.BedrockKnowledgeBase/81-11.プロビジョニング.md)
　

<!-- END -->

<br>

# 以下、本文からの抜粋を紹介します。
---
- 10-00-000.Strandsエージェントとは
- 70-20-070.マルチエージェント
- 70-30-012.朝まで生テレビーAgentCore版＋
- 70-90-020.足立区粗大ごみ判定＋
- 70-90-021.画像から判定＋


詳細は[図解Strandsエージェント徹底解説](https://github.com/awk256/strandsagents)を参照してください。

<br>

# 10.基本構成
# 10-00-000.Strandsエージェントとは
---

<!-- BEGIN-->

**Apache Strands Agents（通称 Strands Agent）** は、AWS 主導で開発されたオープンソースの AI エージェント開発フレームワークで、2025年5月16日に一般公開されました。実体は Python や TypeScript のライブラリであり、Python パッケージをインストールすればすぐにコーディングを開始し、AIエージェントの開発を行えます。Claude Code などの支援ツールを活用して、アシストを受けながら進めることも可能です。

AI時代においてなぜフレームワークが必要かといえば、多様なAIを自律的に動かしながら、期待通りに制御するには、やはりコーディングが最も確実な手段だからです。ただし、そのコーディング手法は従来の開発スタイルとは大きく異なる点も多くあります。なお、Python の構文自体はシンプルで、初心者でも十分に扱えるレベルです。

# AIエージェントの本質と課題

AIエージェントは、単なる「チャットボット」ではありません。

AIエージェントとは、**「自律的に目標を理解し、環境に合わせて適切なツールを選択・実行し、試行錯誤しながら完遂する動的なシステム」** であると言えます。

しかし、この「複雑なタスク」を実務レベルで実行しようとすると、従来の開発手法では以下の問題に直面します。

- **制御のブラックボックス化**: モデルが自律的に動くほど、なぜその行動をとったのか、どこで失敗したのかの追跡（可観測性）が困難になる。
    
- **コードのスパゲッティ化**: 状態管理やツール実行の例外処理を「Chain（連鎖）」として記述しすぎると、拡張や修正が不可能になる。

# AIエージェント開発フレームワークの役割

### 「脳（AI）」に「手足（ツール）」を繋ぐ

AIモデル単体では、外部のシステム（DB、API、検索）を操作できません。 フレームワークは、AIが理解できる形式でツールを提示し、安全に実行させるための　**「共通インターフェース」**　を提供します。これがないと、接続コードをすべて自作することになり膨大な手間がかかります。

###  「迷子」を防いで「完遂」させる

複雑なタスクを頼むと、AIは途中で何をすべきか忘れたり、同じことを繰り返したりします（無限ループ）。 フレームワークは、**「思考 → 実行 → 確認」という正しい手順（型）**　をエージェントに叩き込み、ゴールまで脱線させないための「レールの役割」を果たします。

### 「記憶（コンテキスト）」を一貫させる

一連の業務には、過去の経緯や現在の進捗状況の保持が不可欠です。 フレームワークは、**「セッション管理」**　という仕組みを提供し、エージェントが「さっき何を調べて、今はどの段階か」を常に把握できるようにします。

<br>

# Strands Agents(ストランズエージェント)とは

**Strandsエージェント** は、Amazon Bedrockなどの強力な基盤モデル（LLM）を「手足」となるツールや「記憶」となるセッションと組み合わせ、自律的にタスクを遂行させるためのフレームワークです。

なぜAIエージェント開発フレームワーク（Apache Strandsなど）が必要なのか、3つのポイントでシンプルにまとめます。

- **フレームワークなし**：バラバラの部品（AI、ツール、履歴）を、その都度つぎはぎで繋ぐ作業が必要。
    
- **フレームワークあり**：Strandsという「型」に流し込むだけで、**「動く、壊れにくい、拡張しやすい」**　システムが手に入る。


現在、AIを活用しようとすると、次々に新しいツールや概念が登場し、それぞれの役割や位置づけが、ITエンジニアでさえ把握しきれない状況になりつつあります。

「Claude を使えば十分なのか？」「Amazon Bedrock とは何が違う？」「LangChain や Strands Agents はどこで使うべきか？」

こうした疑問に明確に答えるためには、各技術の関連性を正しく理解することが重要です。そこで本書では、AIエージェントを構成するテクノロジー群を **5つのレイヤー** に分類し、体系的に整理しました。



```mermaid
graph TD
    %% 最上位：タスクとユーザー
    subgraph Execution_Layer [実行タスクレイヤー]
        Task1[画像分析/RAG検索/回答作成]
    end

    %% 第二層：フレームワーク（オーケストレーション）
    subgraph Framework_Layer [開発フレームワークレイヤー]
        direction TB
        LangChain[LangChain]
        Strands{{Strands Agents}}
        CrewAI[CrewAI]
    end

    %% 第三層：開発支援・IDE・AIコーディング
    subgraph Dev_Tools [開発・コーディング支援レイヤー]
        devTools[Claude Code/Codex/GitLab Duo/Q Developer]
    end

    %% 第四層：プラットフォーム・SDK
    subgraph Platform_Layer [実行基盤レイヤー]
        platformLayer[Amazon AgentCore/Azure AutoGen/Google ADK]
    end

    %% 第五層：基盤モデルプロバイダー（脳）
    subgraph Model_Layer [基盤モデル・LLMレイヤー]
		modelLayer[Amazon Bedrock/Anthropic/OpenAI/Azure OpenAI/Google Vertex AI]
    end

    %% 関連付け
    Execution_Layer --> Strands
    Strands -.-> Dev_Tools
    Strands --> Platform_Layer
    Platform_Layer --> Model_Layer
    Dev_Tools --> Model_Layer

    %% 強調スタイル
    style Strands fill:#FF9900,stroke:#333,stroke-width:4px,color:#fff
    style Execution_Layer fill:#f9f9f9,stroke-dasharray: 5 5
```

- **実行タスクレイヤー**: 具体的な業務目的の定義
    
- **開発フレームワークレイヤー**: 推論プロセスと実行の司令塔（オーケストレーション）
    
- **開発・コーディング支援レイヤー**: エージェント構築と実装の効率化
    
- **実行基盤レイヤー**: 安全で堅牢な実行環境とインフラの提供
    
- **基盤モデル・LLMレイヤー**: 思考・判断を司る「知能」の提供


## AIエージェント開発フレームワークの比較


現在、多くのフレームワークが存在しますが、Apache Strandsは「現場での使いやすさと堅牢性」において際立っています。

| **特徴**   | **LangChain**    | **CrewAI**      | **Apache Strands**       |
| -------- | ---------------- | --------------- | ------------------------ |
| **主な対象** | LLM 全般、RAG、Chain | 複数エージェントの共同作業   | **Bedrock 最適化、堅牢な単体・連携** |
| **複雑さ**  | 非常に高い（多機能すぎ）     | 中（役割分担に特化）      | **シンプルかつ軽量（DX重視）**       |
| **設計思想** | 汎用的な部品の結合        | 役割（Role）ベースの自動化 | **推論の透過性と開発のしやすさ**       |
| **信頼性**  | 破壊的変更が多い         | 抽象度が高く挙動が見えにくい  | **AWS内での実績に基づいた安定性**     |

>[注]
筆者が Strands エージェントに出会ったきっかけは、Amazon Bedrock AgentCore を徹底的に使いこなすためでした。当初は AgentCore の動作確認を目的にサンプルコードを探していただけでしたが、触っていくうちに **Strands エージェントのマルチエージェント実装のシンプルさ** に驚かされました。
AI時代の到来とともに LangChain にも取り組んできましたが、次第に機能は肥大化し、構造も複雑に。何より、**マルチエージェントの設計・実装という観点では、大きな進展を感じることができませんでした**。おそらく、プログラマが本業ではない筆者にとって、LangChain の敷居は少々高かったのだと思います。
そんな中、ちょうど諦めかけていたタイミングで出会ったのが Strands エージェントでした。しかも AgentCore 自体が Strands エージェントをベースにしているため、理解もスムーズに進みました。**まさに一振りで二兎を得たような体験**でした。

## Strandsエージェント誕生の背景：LangChainへの「対抗馬」

AIエージェント開発が普及し始めた初期、主流だったのは **LangChain** などの「連鎖型（Chain）」フレームワークでした。しかし、これらは複雑なタスクにおいて「コードが肥大化しすぎる」「エージェントの動きが制御しにくい」といった課題を抱えていました。

Strandsエージェントは、これらの課題を解決するために **「もっとシンプルに、かつ人間のように自律的に動くエージェントを作りたい」**  という開発者の想いから、モダンなアーキテクチャとして設計されました。

## 年表ベースの流れ

- 2023 年初頭
    
    - ReAct 論文公開をきっかけに、Amazon Q Developer チームが内部向けの AI エージェント実装を開始し、複雑なオーケストレーションや JSON パースなどを自前で抱えた仕組みを作り込んでいた。
    
- 2023〜2024 年
    
    - Q Developer や AWS 内部サービス（AWS Glue、VPC Reachability Analyzer など）で使うエージェント基盤として「Strands」の原型が育ち、モデルのプランニング能力を最大限活かす設計思想が固まっていった。​
        
- 2025 年 5 月 16 日（2025 年度）
    
    - 「Strands Agents」としてオープンソース SDK として正式リリース。Python ベースで、モデル・ツール・プロンプトの 3 要素からエージェントを定義する形が明示される。​
        
- 2025 年後半（2025 年 12 月 3 日 など）
    
    - TypeScript サポート（プレビュー）やマルチエージェント連携、エッジデバイス対応、Strands Steering / Evaluations などが順次追加され、言語・機能面で急速に拡張。

##  コアコンセプト：自律性とスケーラビリティ

Strandsエージェントは、単一のエージェントを賢くするだけでなく、**「複数のエージェントが協力して働く（マルチエージェント）」**　ことを前提に設計されています。

- **プロンプト主導型**: コードでガチガチに制御するのではなく、LLMの推論能力を最大限に活かす設計（Swarmパターンなど）を重視。
    
- **イベント駆動**: エージェントの動作をイベント（思考、ツール実行、発言）として捉え、非同期で効率的に処理する仕組みを導入しました。
    

## 現在：エンタープライズ対応とエコシステムの拡大

現在、Strandsエージェントは単なる実験的フレームワークを超え、ビジネス現場での利用を見据えた進化を遂げています。

- **Amazon Bedrockとの密接な連携**: AWS環境でClaudeなどの強力なモデルをセキュアに動かすための最適化が進んでいます。
    
- **MCP（Model Context Protocol）の統合**: 外部ツールやデータとエージェントを瞬時に接続するための標準プロトコルをいち早く取り入れ、拡張性を飛躍的に高めました。
    
## Strandsエージェントが目指すもの

Strandsエージェントを一言で表すと、**「複雑なエージェント・オーケストレーションを、誰でも簡単に、かつプロフェッショナルな品質で実装できるようにすること」** にあります。

Strandsエージェントの基本構成を、**「個別のエージェント構成」** と **「マルチエージェントの連携」** の2つの視点で図解します。

<img src="../images/strands_agent_concept.png" width="600" alt="Strandsエージェント">


## 単一エージェント（Agent）の基本構造

Strandsのエージェントは、LLM（脳）、Tool（手足）、Session（記憶）の3つのコンポーネントで構成されます。

```mermaid
graph LR
    subgraph Agent [Strands Agent]
        direction TB
        LLM[基盤モデル<br/>Bedrock / Anthropic]
        Tool["ツール群 (@tool)<br/>Web検索 / API / DB"]
        Session["セッション管理<br/>File / Redis"]
    end

    User([ユーザー]) -- "指示" --> LLM
    LLM -- "推論" --> Tool
    Tool -- "結果" --> LLM
    LLM <--> Session
    LLM -- "回答" --> User
```

- **Model (LLM)**: エージェントの「脳」です。`system_prompt` によって「あなたはジャーナリストです」といった人格や振る舞いが定義されます。
    
- **Tools**: エージェントが外部世界とやり取りするための「手足」です。Pythonの関数に `@tool` デコレータをつけるだけで実装できます。
    
- **Session Manager**: エージェントの「記憶（文脈）」を司ります。会話履歴を保存し、再起動後も以前の会話を覚えている状態を作ります。
    
## マルチエージェントの連携パターン

複数のエージェントが協力して働く場合、Strandsでは主に**「オーケストレーション型」**と**「Swarm（メッシュ）型」**の2つの構成が取られます。

### オーケストレーション型（指揮者パターン）

一人のマネージャーが、部下の専門家エージェントに仕事を割り振る中央集権的な構造です。

```mermaid
graph TD
    Manager[マネージャーエージェント]
    SubA[調査エージェント]
    SubB[執筆エージェント]
    
    Manager -- "調査を依頼" --> SubA
    SubA -- "事実を報告" --> Manager
    Manager -- "執筆を指示" --> SubB
    SubB -- "原稿を納品" --> Manager
```

### Swarm型（自律ハンドオフ・メッシュ）

マネージャーを置かず、エージェント同士が「ここからは君の領分だ」と自律的にバトンを渡し合う構造です。


```mermaid
graph LR
    Triage[受付エージェント] -- "ハンドオフ" --> Researcher[調査員]
    Researcher -- "ハンドオフ" --> Writer[ライター]
    Writer -- "差し戻し" --> Researcher
```

## Strandsの実装における重要なポイント

- **ステートフル（状態保持）**: `state` オブジェクトをエージェント間で共有することで、チーム全体で「今何が起きているか」という情報を同期できます。
    
- **イベントループ**: Strandsは内部で非同期のイベントループを回しており、モデルの推論とツールの実行を効率よく制御します。
    
- **MCP (Model Context Protocol) 対応**: 外部のツールサーバーから動的にツールを取得して、エージェントを即座に強化できる柔軟性を持っています。
    

<!-- END -->

<br>

# 70.サンプルコード

# 70-00-000.サンプルコードについて
---

<!--BEGIN-->

ここで紹介しているサンプルコードは、Amazon Bedrock AgentCore および Strands エージェントの公式ドキュメントや GitHub を参考に、筆者が再構成したもの、あるいは創意工夫により独自に作成したもの（タイトル末尾に「＋」を付記）です。

すべて筆者の環境で動作確認済みです。

- [Strands User Guide/](https://strandsagents.com/latest/documentation/docs/)
- [Strands Githubs](https://github.com/strands-agents/)
- [Strands Samples](https://github.com/strands-agents/samples)
- [ Strands Python API](https://strandsagents.com/latest/documentation/docs/api-reference/python/agent/agent/)
- [Amazon Bedrock AgentCore Developer Guide](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/what-is-bedrock-agentcore.html)
- [Amazon Bedrock AgentCore Samples](https://github.com/awslabs/amazon-bedrock-agentcore-samples)

# 節の構成について
---
- **10:基礎編**
- **20:マルチエージェント&応用編**
- **30:Amazon Bedrock AgentCore編**
- **90:PoC編**

<!--END-->

<br>

# 70-20-070.マルチエージェント
---

>[注]
ここでは、オーケストレーション型のマルチエージェント構成の技術検証を目的とし、AIエージェントによるチーム（編集長・調査担当・執筆担当）を組成しています。
この構成を通じて、AI技術のトレンドに関する調査・分析レポートを自動生成させる実験を行っています。

<!--BEGIN-->
# 概要

マルチエージェントパターンは、特定の役割に特化した複数のエージェントを組み合わせ、一つの「組織」として動作させる設計手法です。 一人の万能なアシスタントにすべてを任せるのではなく、各ステップに専門家を配置することで、推論の迷走を防ぎ、大規模で複雑な業務プロセスを高い精度で完結させることが可能になります。

```mermaid
sequenceDiagram
    autonumber
    actor User as ユーザー
    participant Manager as 編集長 (Manager)
    participant Researcher as 調査担当 (Researcher)
    participant Web as インターネット
    participant Writer as 執筆担当 (Writer)

    User->>Manager: 1. 記事作成の依頼
    
    rect rgb(249, 249, 249)
        Note over Manager, Researcher: 調査フェーズ
        Manager->>Researcher: 2. 必要な情報の調査を指示
        Researcher->>Web: 3. API経由で検索実行
        Web-->>Researcher: 4. 最新データの返却
        Researcher-->>Manager: 5. 調査報告を提出
    end

    rect rgb(230, 230, 255)
        Note over Manager, Writer: 執筆フェーズ
        Manager->>Writer: 6. 調査データを元に執筆指示
        Writer-->>Manager: 7. 記事原稿を提出
    end

    Manager-->>User: 8. 最終成果物を返却
```


### 司令塔による一元管理

**編集長（Manager）**は、ユーザーの意図を汲み取り、それを実行可能な小さなタスクに分解する役割を担います。各専門家の進捗を管理し、最終的なアウトプットの品質に責任を持つため、複雑なタスクでも一貫性を保つことができます。

### 専門特化されたスキル実行

**調査担当（Researcher）**はインターネット検索に特化し、**執筆担当（Writer）**は文章作成に特化しています。このように機能を分離することで、「検索しながら書く」という負荷の高い作業によるミスを防ぎ、それぞれのAIモデルの能力を最大限に引き出します。

### 外部情報の取り込みと統合

**インターネット（Web）**　から得られた最新の「事実」を調査担当が持ち帰り、それを編集長が執筆担当に「素材」として渡します。このバトンパスにより、AIの学習データに含まれていない今日現在のニュースやトレンドを反映した、極めて鮮度の高い成果物を生成することが可能になります。


# マルチエージェントとエージェントワークフロー


マルチエージェントとエージェントワークフローは、どちらも「複数の知能を組み合わせる」という点では共通していますが、その　**「制御の仕組み」と「自由度」**　に決定的な違いがあります。

一言で言えば、**「自律的なチーム」か「厳格な手順書」**　かという違いです。

### マルチエージェント：自律的な「組織」

マルチエージェントは、親エージェント（司令塔）が「今は調査が必要だから、リサーチ担当を呼ぼう」と、**その場の判断でツール（子エージェント）を使い分ける**パターンです。

- **動作イメージ**: 編集長が部下のライターや校閲者に、必要に応じて仕事を振るイメージ。
    
- **メリット**: ユーザーの曖昧な依頼に対して、AIが自ら解決策を組み立てられます。
    
### エージェントワークフロー：厳格な「工場」

エージェントワークフローは、Strandsの「グラフ構造」などを用いて、**「ステップ1が終わったら必ずステップ2へ進む」という順序をあらかじめ固定**するパターンです。

- **動作イメージ**: 工場のラインのように、前工程の成果物が次工程へ自動的に運ばれるイメージ。
    
- **メリット**: 業務プロセスが標準化されており、誰がいつ実行しても同じ品質のプロセスを辿ることが保証されます。

>[注]
マルチエージェントには、エージェント同士が対等かつ自律的に連携する「分散協調型」と、中央の制御ロジックが各エージェントを指揮する「指令型（オーケストレーション型）」の2つの構成スタイルがあります。
たとえば、エージェントワークフローのように、中央のロジックが複数のエージェントを順番に呼び出して処理を進める構成も、れっきとしたマルチエージェント構成です。
このように、「自律型」だけでなく「指令型」もマルチエージェントに含まれると考えると、「マルチエージェント＝自律分散」あるいは「ワークフロー＝単なる制御構成」といった理解は、やや狭義に過ぎるように思われます。

# サンプルコード

このサンプルでは、リサーチを行うエージェントと、その結果を元に執筆するエージェントを「ツール」として統括エージェントに持たせています。

[multi_agent.py]
```
import os
from strands import Agent, tool
from strands.models import BedrockModel

# モデル設定
model = BedrockModel(
    region_name="us-east-1", 
    model_id="us.anthropic.claude-sonnet-4-20250514-v1:0"
)

# --- 外部検索ツールの定義 ---
@tool
def search_internet(query: str):
    """
    最新のニュースや技術動向をインターネットで検索します。
    検索が必要な具体的なクエリを入力してください。
    """
    # 実際にはここに Tavily や SerpApi 等の呼び出しを記述します
    # 今回はシミュレーションとして、検索結果（最新データ）が返ったと仮定します
    return f"【検索結果】2025年末現在、AIエージェントはStrands SDKのようなマルチエージェント構成が主流となっています..."

# --- 専門家エージェントの定義 ---

# 1. 調査担当（検索ツールを装備）
researcher = Agent(
    model=model,
    system_prompt="あなたは調査のプロです。検索ツールを使い、正確な最新事実を収集してください。",
    tools=[search_internet] # 検索する「手足」を与える
)

# 2. 執筆担当
writer = Agent(
    model=model,
    system_prompt="あなたは技術ライターです。調査結果に基づき、読者を惹きつける記事を書いてください。"
)

# --- 親エージェントから呼び出すためのツール化 ---

@tool
def call_researcher(topic: str):
    """最新の事実確認や調査が必要な場合に呼び出します。"""
    return researcher(topic)

@tool
def call_writer(notes: str):
    """調査結果を元に記事の執筆を依頼する場合に呼び出します。"""
    return writer(notes)

# --- 統括エージェント（マネージャー） ---

manager = Agent(
    model=model,
    system_prompt="""
あなたは編集長です。
1. まず調査担当に最新情報の検索と収集を依頼してください。
2. 収集された情報を元に、ライターに記事執筆を指示してください。
""",
    tools=[call_researcher, call_writer]
)

# 実行
print(manager("2025年のAIエージェントのトレンドについて、最新情報を調べて記事を書いて。"))
```

# 実行

```

python multi_agent.py

編集長として、最新のAIエージェント技術について調査担当に事実確認を依頼し、その後ライターに記事作成を依頼いたします。

まず、調査担当に最新のAIエージェント技術について調査を依頼します。
Tool #1: call_researcher
# 最新のAIエージェント技術に関する調査報告

## 1. 2024年の主要なAIエージェント技術の進歩

### **Function Calling機能の大幅強化**
- GPT-4 Turboでfunction callingの精度が向上（95%以上の適切な関数選択率）
- 並列関数呼び出しサポートにより、複数タスクの同時実行が可能
- Claude 3でも同様のツール使用機能が実装

### **ReAct（Reasoning and Acting）パラダイムの普及**
- 推論と行動を交互に行うフレームワークが標準化
- Chain-of-Thought（CoT）推論との組み合わせで、より複雑なタスク処理が可能
- 成功率が従来手法比で30-40%向上

### **メモリ機能の実装**
- 長期記憶（Long-term Memory）機能により、セッション間での情報保持が実現
- RAG（Retrieval-Augmented Generation）との統合でより精密な情報検索

・・・中略

## まとめ

2024年のAIエージェント技術は、Function Callingの成熟、マルチエージェントシステムの実用化、そして企業レベルでの本格導入という3つの大きな転換点を迎えています。技術的な課題は残るものの、実際のビジネス価値創出が明確に示されており、今後さらなる普及が予想されます。

特に注目すべきは、単純なタスク自動化から、複雑な意思決定支援や創造的業務への適用範囲の拡大です。2025年には、より高度な推論能力と安全性を備えたAIエージェントの登場が期待されています。調査結果が得られましたので、次にライターに記事作成を依頼いたします。
Tool #2: call_writer
# AIエージェント技術の革命的進歩：2024年を振り返る企業導入戦略レポート

## はじめに：AIエージェントが切り拓く新たなビジネスフロンティア

2024年は、AIエージェント技術にとって真の「実用化元年」となりました。これまでデモンストレーション段階に留まっていた技術が、企業の現場で実際のビジネス価値を生み出し始めています。この変革の背景には、技術的ブレークスルーと市場の成熟が同時に進行した結果があります。

・・・中略

## 🚀 技術革新の三本柱：2024年の画期的進歩

### **Function Calling機能：AIエージェントの"手足"が進化**

2024年最大のブレークスルーの一つが、Function Calling機能の飛躍的向上です。GPT-4 Turboでは95%以上という驚異的な関数選択精度を実現し、AIエージェントが「考える」だけでなく「行動する」能力を大幅に強化しました。

特に注目すべきは並列関数呼び出し機能です。従来のシーケンシャルな処理から、複数タスクの同時実行へと進化したことで、エージェントの処理効率は格段に向上しています。これは単なる技術改善ではなく、AIエージェントの活用領域を根本的に拡大する変革です。

### **ReActパラダイム：思考と行動の革新的融合**

ReAct（Reasoning and Acting）フレームワークの普及により、AIエージェントは人間のような「考えながら行動する」能力を獲得しました。従来のChain-of-Thought推論と組み合わせることで、複雑なタスクの成功率が30-40%も向上しています。

この技術は、単純な質問応答から複雑な問題解決へと、AIエージェントの適用範囲を大幅に押し上げました。企業の現場では、これまで人間にしか解決できなかった複雑な業務プロセスの自動化が現実のものとなっています。

### **メモリ機能：継続的学習の実現**

長期記憶機能の実装により、AIエージェントはセッション間での情報保持が可能になりました。RAG技術との統合により、より精密で文脈を理解した情報検索が実現し、真の意味での「学習するエージェント」が誕生しています。

・・・中略

## 🛠️ プラットフォーム戦争：覇権をかけた激烈な競争

### **OpenAI Assistants API：圧倒的なエコシステム構築力**

OpenAIは2024年版AssistantsAPIで、単なるAPIプロバイダーから包括的なエージェントプラットフォームへと進化しました。Code Interpreterによるデータ分析機能、512MBまでのファイル処理能力、そしてカスタムGPTsとの統合により、企業レベルでの本格的な導入を可能にしています。

Shopify、Zapier、Intercomといった大手企業の採用は、その実用性の高さを物語っています。価格設定も入力$0.01/1K tokens、出力$0.03/1K tokensと、企業導入を意識した戦略的価格となっています。

### **LangChain：オープンソースエコシステムの雄**

85,000を超えるGitHub Starsが示すように、LangChainは開発者コミュニティで圧倒的な支持を獲得しています。2024年の最大の進歩は、LangGraphの導入による状態管理型エージェント構築の実現です。150以上の外部サービス連携により、企業の既存システムとの統合が大幅に簡素化されました。

・・・中略

## ⚠️ 課題と展望：次なるフロンティアへ

### **現在の技術的課題：克服すべきハードル**

幻覚問題、セキュリティリスク、コスト・パフォーマンスという三つの主要課題は、AIエージェント技術の更なる普及に向けて解決すべき重要な課題です。特にプロンプトインジェクション攻撃や権限昇格の脆弱性は、企業レベルでの導入において深刻な懸念材料となっています。

### **未来への展望：技術革新の方向性**

小型モデルの活用、エッジコンピューティング、専門ドメイン特化という三つの方向性が、今後の技術発展を牽引すると予想されます。特に7B-13Bパラメータモデルでのエージェント実装は、導入コストの大幅削減を可能にし、中小企業への普及を加速させるでしょう。

---

## 🏢 企業戦略分析：巨人たちの覇権争い

### **Google vs Microsoft：プラットフォーム戦争の激化**

GoogleのDuet AI for WorkspaceとMicrosoftの365 Copilotは、企業向けAIエージェント市場での覇権をかけた激しい競争を繰り広げています。両社とも既存の生産性ツールとの統合を重視し、ユーザーの移行コストを最小化する戦略を取っています。

### **オープンソース vs プロプライエタリ：開発哲学の対立**

AnthropicのConstitutional AIによる安全性重視のアプローチと、MetaのLlama 2/3ベースのオープンソース戦略は、AIエージェント開発における二つの哲学を代表しています。この対立は、今後の技術発展方向を決定する重要な要因となるでしょう。

---

## 📊 結論：2025年への戦略的示唆

2024年のAIエージェント技術の進歩は、単なる技術革新を超えて、ビジネスプロセスの根本的変革を促しています。Function Calling機能の成熟、マルチエージェントシステムの実用化、企業レベルでの本格導入という三つの転換点は、今後のビジネス戦略立案において重要な考慮要素となります。

特に注目すべきは、単純なタスク自動化から複雑な意思決定支援や創造的業務への適用範囲の拡大です。これは、人間とAIの役割分担の再定義を意味し、企業の組織構造や人材戦略にも大きな影響を与えるでしょう。

2025年には、より高度な推論能力と安全性を備えたAIエージェントの登場が期待されます。企業は今こそ、この技術革新の波に乗り遅れることなく、戦略的なAIエージェント導入計画を策定すべき時期に来ています。技術の進歩を単に受動的に受け入れるのではなく、自社のビジネスモデル変革の機会として積極的に活用する企業が、次の時代の勝者となるでしょう。編集長として、調査担当による詳細な事実確認とライターによる記事作成を完了いたしました。

・・・中略

## カバー範囲：

- Function Calling、ReAct、メモリ機能などの技術革新
- OpenAI、LangChain、AutoGPTなどの主要プラットフォーム
- マルチエージェントシステムの進展
- 実際のビジネス活用事例（Intercom、HubSpot、GitHub等）
- 技術的課題と今後の展望
- Google、Microsoft、Anthropic等の企業戦略

この記事は、技術者から経営者まで幅広い読者層に対して、AIエージェント技術の現状と未来への洞察を提供する内容となっております。
```

# まとめ:どちらを選ぶべきか

### マルチエージェントを選ぶべき時:**
    
    解決までの手順が一つではなく、AIに「状況判断」を任せたい場合（例：汎用的なコンサルティング、複雑な問題解決）。
    
### エージェントワークフローを選ぶべき時:**
    
    「まず契約書を読み、次にリスクを抽出し、最後に要約を作る」といった、失敗が許されない定型業務を自動化したい場合。

Strands SDKでは、これらを組み合わせて「ワークフローの中の特定ステップで、マルチエージェントに判断を任せる」といった高度なハイブリッド構成も可能です。

<!--END-->

<br>

# 70-30-012.朝まで生テレビーAgentCore版＋
---

>[注]
本企画では、AIエージェントを擬人化し、かつての伝説的な討論番組を再現しています。司会役は、カリスマジャーナリスト「田原総一朗」氏を模したエージェント。対するは、総理大臣、専門家3名、一般市民2名といった役割を持つエージェントたちです。テーマは「台湾有事の問題」。各エージェントがそれぞれの立場から白熱した議論を繰り広げます。その内容は、AgentCoreの短期記憶と長期記憶として保存されます。
この試みの目的は、マルチエージェント構成や、AgentCore の Gateway・Lambda・短期記憶・長期記憶といった各機能の技術検証にあります。
田原総一朗さんをご存知の方には、懐かしさも感じられるのではないでしょうか。

<!--BEGIN-->

ここでは、伝説的な討論番組『朝まで生テレビ！』をマルチエージェントシステムとして再現しています。

このシステムを、マルチエージェントのパターンや処理方式の観点から整理・解説します。

# 概要

**マルチエージェント討論システム**をAWS AgentCore基盤で実現します。司会者1名＋パネリスト6名の計7つのAIエージェントが、MCPプロトコル経由でツールを使用しながら自律的に討論を進行します。セッション状態はS3に永続化され、中断・再開が可能です。



```mermaid
sequenceDiagram
    autonumber
    participant Local as ローカル (debate_battle.py)
    participant Auth as Cognito (認証)
    participant GW as Gateway (MCP互換)
    participant Lambda as Lambda (Tool群)
    participant Bedrock as Bedrock (Claude)
    participant S3 as S3 (永続化)

    Local->>Auth: 1. トークン取得リクエスト
    Auth-->>Local: JWT (認証トークン) 返却
    
    Local->>GW: 2. MCP接続 & ツール利用リクエスト
    par 外部知識の取得
        GW->>Lambda: 3. ニュース検索 (L1)
        GW->>Lambda: 3. 人格データ取得 (L2)
    end
    Lambda-->>Local: 検索・人格データの提供

    rect rgb(240, 240, 240)
        Note over Local, Bedrock: 討論フェーズ
        Local->>Bedrock: 4. 司会者・パネリストの推論実行
        Bedrock-->>Local: 各エージェントの発言
    end

    Local->>S3: 5. セッション情報の永続化保存
```

### ローカルとクラウドのセキュアな境界線

**ローカル環境**で「田原総一朗」風の司会者や6名のパネリストという複雑な実行環境を回しつつ、**Cognito認証**を介してクラウドへアクセスする構成です。これにより、ビジネスレベルのセキュリティ（JWTによる権限管理）を保ちながら、手元のスクリプトで自由度の高い討論制御を可能にしています。

### MCP互換ゲートウェイによる機能拡張

**Gateway (MCP互換)** を置くことで、ローカルのエージェントがクラウド上の **Lambda関数** をあたかも自分のローカルツールのように呼び出せるようになります。最新ニュース（L1）や特定の人格データ（L2）を動的に取り込むことで、討論の内容にリアルタイムな事実と深いキャラクター性を与えています。

### 基盤モデルと状態の永続化

推論の心臓部には **Bedrock (Claude Sonnet)** を採用し、高度な文脈理解に基づいた討論を実現しています。また、議論のログや現在のステータスを **S3** に保存することで、万が一ローカル実行が中断してもクラウド側からセッションを復旧できる、堅牢なデータ設計（ステートフルな管理）となっています。

# プロビジョニング

## Lambda作成

[lsearch_taiwan_news.py]
- **Function name: search_taiwan_news**
- **Runtime: Python 3.12**
- **Architectur: x86_64**
- **Execution role: Create a new role with basic Lambda permissions**
```
"""
Lambda: search_taiwan_news
台湾有事の最新ニュースを取得するツール
"""
import json

def lambda_handler(event, context):
    # AgentCoreからのツール名検証
    tool_name = ""
    if hasattr(context, "client_context") and context.client_context:
        custom = getattr(context.client_context, "custom", {}) or {}
        tool_name = custom.get("bedrockAgentCoreToolName", "")
    
    if "___" in tool_name:
        tool_name = tool_name.split("___", 1)[1]
    
    if tool_name and tool_name != "search_taiwan_news":
        return {"statusCode": 400, "body": json.dumps({"error": "wrong tool"})}
    
    query = event.get("query", "台湾有事")
    
    news_data = {
        "query": query,
        "timestamp": "2025-01-02T00:00:00Z",
        "articles": [
            {"title": "中国軍が台湾周辺で大規模軍事演習を実施", "source": "Reuters"},
            {"title": "米国が台湾への武器売却を承認", "source": "AP"},
            {"title": "日本政府が南西諸島の防衛強化を発表", "source": "NHK"},
            {"title": "台湾海峡の緊張が高まる中、各国が外交努力", "source": "BBC"},
            {"title": "半導体サプライチェーンへの影響懸念", "source": "Bloomberg"}
        ],
        "summary": """【台湾有事 最新情報】
1. 中国軍が台湾周辺で軍事演習を実施
2. 米国が台湾への武器売却を承認
3. 日本政府が南西諸島の防衛強化を発表
4. 台湾海峡の緊張が高まる中、各国が外交努力
5. 半導体サプライチェーンへの影響懸念"""
    }
    
    return {"statusCode": 200, "body": json.dumps(news_data, ensure_ascii=False)}
```
- Function ARN: arn:aws:lambda:us-east-1:010928207344:function:search_taiwan_news

[search_taiwan_news.json]
```
{
  "name": "search_taiwan_news",
  "description": "台湾有事に関する最新ニュースと情報を検索・取得する。討論の準備や最新情報の確認に使用。",
  "inputSchema": {
    "type": "object",
    "properties": {
      "query": {
        "type": "string",
        "description": "検索クエリ（例: 台湾有事、中国軍事演習）",
        "default": "台湾有事"
      }
    },
    "required": []
  }
}
```


[search_tahara_personality.py]
- **Function name: search_tahara_personality**
- **Runtime: Python 3.12**
- **Architectur: x86_64**
- **Execution role: Create a new role with basic Lambda permissions**

```
"""
Lambda: search_tahara_personality
田原総一朗の性格・スタイル情報を取得するツール
"""
import json

def lambda_handler(event, context):
    tool_name = ""
    if hasattr(context, "client_context") and context.client_context:
        custom = getattr(context.client_context, "custom", {}) or {}
        tool_name = custom.get("bedrockAgentCoreToolName", "")
    
    if "___" in tool_name:
        tool_name = tool_name.split("___", 1)[1]
    
    if tool_name and tool_name != "search_tahara_personality":
        return {"statusCode": 400, "body": json.dumps({"error": "wrong tool"})}
    
    personality_data = {
        "name": "田原総一朗",
        "famous_program": "朝まで生テレビ！",
        "famous_phrases": [
            "ちょっと待って！",
            "それは違う！",
            "要するに何が言いたいの？"
        ],
        "summary": """【田原総一朗の特徴】
- 1934年生まれのジャーナリスト
- 「朝まで生テレビ！」の司会で有名
- 「ちょっと待って！」「それは違う！」が口癖
- 鋭い質問で政治家の本音を引き出す
- 曖昧な回答には容赦なく突っ込む
- 「要するに何が言いたいの？」と核心を突く"""
    }
    
    return {"statusCode": 200, "body": json.dumps(personality_data, ensure_ascii=False)}
```
- Function ARN: arn:aws:lambda:us-east-1:010928207344:function:search_tahara_personality

[search_tahara_personality.json]
```
{
  "name": "search_tahara_personality",
  "description": "田原総一朗の性格、司会スタイル、口癖などの情報を取得する。司会者エージェントの人格設定に使用。",
  "inputSchema": {
    "type": "object",
    "properties": {
      "detail_level": {
        "type": "string",
        "description": "情報の詳細度（standard/detailed）",
        "enum": ["standard", "detailed"],
        "default": "standard"
      }
    },
    "required": []
  }
}
```

## 🚪 AgentCore Gateway 作成手順

### 🛠 Gateway 作成と設定

> ※ この検証では VPC の設定はスキップしています。

1. **Amazon Bedrock > AgentCore > Gateways > Create gateway** をクリック
    
2. 以下の設定を入力：
    
### 🔐 基本設定

- **Gateway name**: `gateway-quick-start-d41057`
- **Inbound Auth type**: `Use JSON Web Tokens (JWT)`
- **JWT schema configuration**: `JWT schema configuration`
- **IAM Permissions**: `Create and use a new service role`
- **Service role name**: `AmazonBedrockAgentCoreGatewayDefaultServiceRole1767347537681`（デフォルト）  

	→または `My Service Role Name`（任意）

### 🎯 ターゲット設定（Lambda 関数）

#### ✅ ターゲット 1

- **Target name**: `target-quick-start-f1f98c`（デフォルト名）
- **Target Type**: `Lambda ARN`
- **Lambda ARN**:  
    `arn:aws:lambda:us-east-1:<My Account ID>:function:search_taiwan_news`
- **Target schema**: `Define an inline schema`
- **Inline schema editor** に以下を貼り付け：

```json
// ← [search_taiwan_news.json] の内容をここに貼り付け
```

#### ➕ ターゲット 2 を追加

- **Target name**: `target-quick-start-cd3847`（デフォルト名）
- **Lambda ARN**:  
    `arn:aws:lambda:us-east-1:<My Account ID>:function:search_tahara_personality`
- **Target schema**: `Define an inline schema`
- **Inline schema editor** に以下を貼り付け：

```json
// ← [search_tahara_personality.json] の内容をここに貼り付け
```

### 📦 Gateway 作成

- **[Create gateway]** をクリックして完了
    
### 📋 作成後に控えておくべき情報

- **Gateway Resource URL**
```
https://gateway-quick-start-d41057-bojslcregg.gateway.bedrock-agentcore.us-east-1.amazonaws.com/mcp
```
   
→ `.env` 用変数：`AGENTCORE_GATEWAY_ENDPOINT`
    
- **Discovery URL**
```
https://cognito-idp.us-east-1.amazonaws.com/us-east-1_6EiNfrH8r/.well-known/openid-configuration
```
    
→ `.env` 用変数：`COGNITO_DISCOVERY_URL`

## S3バケット作成

```
$ aws s3 mb s3://debate-sessions-bucket-123 --region us-east-1
make_bucket: debate-sessions-bucket-123

$ aws s3 ls --region us-east-1 | grep debate-sessions-bucket-123
2026-01-02 21:17:04 debate-sessions-bucket-123
```

## コード作成

[debate_battle_agentcore.py]
```
"""
田原総一朗の討論バトル - AWS AgentCore版
Strands Agents + AgentCore Gateway + S3セッション管理
"""
import os
import json
import signal
import sys
import base64
from datetime import datetime
from dataclasses import dataclass
import boto3
import requests
from botocore.exceptions import ClientError
from dotenv import load_dotenv
from mcp.client.streamable_http import streamablehttp_client
from strands import Agent
from strands.tools.mcp import MCPClient
from strands.models import BedrockModel

load_dotenv()

# =============================================================================
# 設定
# =============================================================================
@dataclass
class Config:
    # Cognito
    cognito_client_id: str
    cognito_client_secret: str
    cognito_discovery_url: str
    cognito_custom_scope: str
    # AgentCore
    gateway_endpoint: str
    # Bedrock
    model_id: str
    region: str
    max_tokens: int
    # S3
    s3_bucket: str
    s3_prefix: str
    # Debate
    topic: str
    session_id: str

    @classmethod
    def from_env(cls) -> "Config":
        return cls(
            cognito_client_id=os.getenv("COGNITO_CLIENT_ID", ""),
            cognito_client_secret=os.getenv("COGNITO_CLIENT_SECRET", ""),
            cognito_discovery_url=os.getenv("COGNITO_DISCOVERY_URL", ""),
            cognito_custom_scope=os.getenv("COGNITO_CUSTOM_SCOPE", ""),
            gateway_endpoint=os.getenv("AGENTCORE_GATEWAY_ENDPOINT", ""),
            model_id=os.getenv("BEDROCK_MODEL_ID", "us.anthropic.claude-sonnet-4-20250514-v1:0"),
            region=os.getenv("AWS_DEFAULT_REGION", "us-east-1"),
            max_tokens=int(os.getenv("BEDROCK_MAX_TOKENS", "4096")),
            s3_bucket=os.getenv("S3_SESSION_BUCKET", ""),
            s3_prefix=os.getenv("S3_SESSION_PREFIX", "debate_sessions"),
            topic=os.getenv("DEBATE_TOPIC", "台湾有事の問題"),
            session_id=os.getenv("DEBATE_SESSION_ID", "default"),
        )

    def validate(self) -> list[str]:
        required = {
            "COGNITO_CLIENT_ID": self.cognito_client_id,
            "COGNITO_CLIENT_SECRET": self.cognito_client_secret,
            "COGNITO_DISCOVERY_URL": self.cognito_discovery_url,
            "COGNITO_CUSTOM_SCOPE": self.cognito_custom_scope,
            "AGENTCORE_GATEWAY_ENDPOINT": self.gateway_endpoint,
            "S3_SESSION_BUCKET": self.s3_bucket,
        }
        return [k for k, v in required.items() if not v]

# =============================================================================
# パネリスト定義
# =============================================================================
PANELISTS = {
    "tanaka": {"name": "田中", "role": "日本国首相",
        "prompt": "あなたは日本国の首相・田中です。日米同盟を重視し、外交的解決を優先。発言は100文字以内。"},
    "minami": {"name": "南", "role": "歴史専門家",
        "prompt": "あなたは歴史専門家・南です。「歴史的に見ると...」が口癖。発言は100文字以内。"},
    "kanemoto": {"name": "金本", "role": "経済専門家",
        "prompt": "あなたは経済専門家・金本です。「経済的損失は...」が口癖。発言は100文字以内。"},
    "tsuyoshi": {"name": "強", "role": "軍事専門家",
        "prompt": "あなたは軍事専門家・強です。「軍事的には...」が口癖。発言は100文字以内。"},
    "taira": {"name": "平", "role": "平和主義市民",
        "prompt": "あなたは平和主義者・平です。戦争絶対反対の立場。発言は100文字以内。"},
    "taka": {"name": "タカ", "role": "タカ派市民",
        "prompt": "あなたはタカ派市民・タカです。国防強化を主張。発言は100文字以内。"},
}
SPEAKER_ORDER = ["tanaka", "minami", "kanemoto", "tsuyoshi", "taira", "taka"]
...中略
```


# 実行

```
$ python -u debate_battle_agentcore.py

============================================================
  田原総一朗の討論バトル (AWS AgentCore版)
============================================================

[INFO] テーマ: 台湾有事の問題 / セッション: session_001 / バケット: debate-sessions-bucket-123

============================================================
【討論会準備中...】
============================================================
[DEBUG] token_endpoint: https://my-domain-94xxrnfq.auth.us-east-1.amazoncognito.com/oauth2/token
[DEBUG] scope: gateway-quick-start-d41057/genesis-gateway:invoke
[DEBUG] Status: 200
[DEBUG] Response: {"access_token":"eyJraWQiOiIxczZGUFNhR0srWllqSWhuenZqNVBsRXE3RFllaENLbittNDZHV1lIUWxZPSIsImFsZyI6IlJTMjU2In0.eyJzdWIiOiIzb29mOWhza3BvZnNoOGdwcXNvMDRzdDY5NiIsInRva2VuX3VzZSI6ImFjY2VzcyIsInNjb3BlIjoiZ2F0ZXdheS1xdWljay1zdGFydC1kNDEwNTdcL2dlbmVzaXMtZ2F0ZXdheTppbnZva2UiLCJhdXRoX3RpbWUiOjE3NjczNTk1MzYsImlzcyI6Imh0dHBzOlwvXC9jb2duaXRvLWlkcC51cy1lYXN0LTEuYW1hem9uYXdzLmNvbVwvdXMtZWFzdC0xXzZFaU5mckg4ciIsImV4cCI6MTc2NzM2MzEzNiwiaWF0IjoxNzY3MzU5NTM2LCJ2ZXJzaW9uIjoyLCJqdGkiOiI1MzlkOTc3MS01YTE1LTQ3ODktOGVmNy1iMzJmMmQ1MTIyZGYiLCJjbGllbnRfaWQiOiIzb29mOWhza3BvZnNoOGdwcXNvMDRzdDY5NiJ9.fYMw-4rxCT7xHB-QosTFCx8JwdbBfs5oT-IjYFwssqMpVrlPZyf6Zus4EBUP-F7zL4lSIzXV0mcfLIzRTu3IvbOrW-JKpH3uHFiODzHFjgPaWV8GlY57UH5mQCC4p1_slEUpzNx8MgKsr7bABNlW4bPiWAJVpQL4OEjXIBm5yfrmLrMJ7bvFgIJKSMhPTaV0lRnJKLcnnkHRAmZBikuBfgdt3IvwhdPHGOSFRCoxtc5hLLRJWaL6NjgNPJlai3uSEGBO0keXbjbqAq9cUKn9DXAal-qhXx6YBElldqcMXFDiekXXXbwdOEpQDhNa4swFZP5R-5HlxuPoUp7_HJCPOw","expires_in":3600,"token_type":"Bearer"}
[DEBUG] Tool: <strands.tools.mcp.mcp_agent_tool.MCPAgentTool object at 0x7fb9fb0f6cc0>
[DEBUG] Tool attrs: ['__abstractmethods__', '__annotations__', '__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getstate__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__slots__', '__str__', '__subclasshook__', '__weakref__', '_abc_impl', '_agent_tool_name', '_is_dynamic', 'get_display_properties', 'is_dynamic', 'mark_dynamic', 'mcp_client', 'mcp_tool', 'stream', 'supports_hot_reload', 'timeout', 'tool_name', 'tool_spec', 'tool_type']

【討論会開始】テーマ: 台湾有事の問題
（Ctrl+C でサマリー表示して終了）
============================================================

田原: さあ、今日は台湾有事について徹底的に議論しましょう！

習近平は「平和統一」と言いながら軍事力を増強し続けている。一方でアメリカは台湾関係法で台湾防衛を示唆している。そして我々日本は、台湾海峡から僅か110キロしか離れていない与那国島を抱えているんです！

もし台湾有事が起きたら、日本は本当にアメリカと一緒に戦うのか？それとも傍観するのか？皆さん、遠慮なくどんどん発言してください！まず、この問題をどう捉えているか聞かせてもらいましょう！

田原: 田中首相！あなたに直球で聞きます！

台湾有事が現実になった時、日本はどう対応するんですか？「台湾の平和と安定は日本の安全保障に直結する」と政府は繰り返し言っていますが、具体的にはどういうことなんですか？

自衛隊は出動するのか？それとも後方支援に留まるのか？国民には「有事の際の覚悟」を求めるなら、まず総理自身が明確な方針を示すべきでしょう！

曖昧な答弁はダメですよ！国民の生命がかかっているんです。田中首相、はっきり答えてください！

田中: 重大な質問として真摯に受け止めます。台湾有事は仮定の話ですが、まず外交による平和的解決に全力を尽くします。万が一の場合は、憲法と国際法に基づき、日米同盟の枠組みで対応を検討します。自衛隊の具体的行動は状況次第ですが、国民の安全を最優先に判断いたします。
----------------------------------------
田原: 南さん！歴史の専門家として聞きたい！

台湾問題の根本を理解するには歴史を知る必要がありますよね。1949年の中華民国政府の台湾移転から、1972年の日中国交正常化、そして現在まで。

中国は「台湾は中国の不可分の領土」と主張し続けているが、実際には台湾は一度も中華人民共和国に統治されたことがない。この歴史的事実をどう見るべきなんですか？

そして過去の台湾海峡危機を見ると、アメリカの関与が戦争を防いできた。今回もその歴史が繰り返されるのか？南さん、歴史家の視点で分析してください！

南: 歴史的に見ると、この問題は「正統性の継承」をめぐる複雑な構造ですね。

1949年以降、両岸は事実上の分断統治が続いており、中華人民共和国による台湾統治の実績はゼロ。しかし中国は清朝からの歴史的継承を根拠にしています。

歴史的に見ると、1954年、1958年、1996年の台湾海峡危機では確かに米軍の関与が抑制効果を発揮しました。ただし現在の中国の軍事力は当時とは比較にならないレベル。

歴史的教訓として、パワーバランスの変化が地域安定に決定的影響を与える点は注目すべきでしょうね。
・・・中略

```

<--END-->

<br>

# 70-90-020.足立区粗大ごみ判定＋
---

>[注]
本企画は、Amazon Bedrock Knowledge Base の技術検証を目的としています。
実際の「足立区のごみ品目情報」をナレッジベースとして活用し、Amazon Nova による画像解析で品目を特定。その上で、ごみの正しい出し方を提示する一連のプロセスを検証しています。


<!--BEGIN-->

# 検証ユースケース：粗大ごみ受付をAIでアシストする

筆者は東京都足立区在住で、年に2回の**粗大ごみ持ち込み（無料）サービス**を活用しています。  
しかし、**事前のWeb申し込み手続き**に毎回苦労しています。

### 課題点

- 申請時に**正確な品目名が分からない** 
    
- 分かっていても、**PDF資料（10ページ前後）を参照するのが面倒**
    
- 結果として、**途中で挫折し、結局電話で案内員に頼る**ことが多い
	- 実は、Web申し込みは一回も成功してない
    
### 検証アイデア

この課題に対し、以下のような構成で **Amazon Bedrock の Knowledge Base 機能**を活用し、**自然言語で質問できるAIサポートエージェント**を構築・検証してみたいと考えています。

### 技術構成のイメージ

- **ドキュメントソース**：足立区の粗大ごみ品目PDF一覧（例：PDF→テキスト抽出してベクトル化）
    
- **ベクトル検索**：Amazon Bedrock Knowledge Base を利用
    
- **フロント**：自然文で「この椅子は粗大ごみ扱い？」「マットレスは何と分類される？」などと聞ける
    
- **推論**：Claude / TitanなどのLLMで応答生成
    
- **目的**：誰でも迷わず申し込みできる案内システム
    



```mermaid
sequenceDiagram
    participant User as ユーザー
    participant AI as AIコンシェルジュ
    participant KB as Knowledge Base

    User->>AI: 画像を渡す
    AI->>User: 1. 候補から番号で選んでください
    User->>AI: 「1」を入力
    AI->>User: 2. サイズは 30cm 以上ですか？ (1.はい 2.いいえ)
    User->>AI: 「1」を入力
    AI->>KB: 確定した品目とサイズで検索
    KB-->>AI: 正解データを返却
    AI-->>User: 捨て方を回答
```

- **画像解析が主役ではない**: 画像はあくまで「候補を出すため」に使い、最終的な決定はユーザーに**番号**で選ばせます。
    
- **間違いが起きない**: ユーザーが選んだ番号に基づいてKB（ナレッジベース）を引くので、誤判定のまま進むことがありません。
    
- **サイズも番号**: テキスト入力ではなく `1` か `2` を選ばせることで、処理を確実にしています。

# 実装のポイント

### 「Coding不要」でできる範囲（Amazon Bedrock Knowledge Bases を使用）

以下のプロセスは、AWSコンソール上の設定だけで完結します。

- **PDFのベクトル化**: S3に置いたPDFを読み込み、AIが検索しやすい形式（ベクトル）に変換してデータベース（OpenSearch等）に保存する。
- **検索機能のテスト**: AWSコンソール上のテストウィンドウで、質問を投げるとPDFから回答が返ってくるか確認する。
- **プロンプトの設定**: AIに「ごみ分別の専門家として回答してください」といった役割を与える。

これだけで「PDFの内容に基づいて回答するAI」の心臓部は完成します。

### 「Coding（開発）」が必要になる範囲

実際に「システム」として動かすには、以下の部分で少しプログラミングが必要になります。

- **「写真」を送る部分**: ユーザーがアップロードした画像をAI（Novaなど）に渡し、「これは何のごみか？」を特定させる命令を送る処理。
- **処理のつなぎ込み（オーケストレーション）**:

    1. 写真を解析して「電子レンジ」と特定する。
    2. その「電子レンジ」という言葉でRAGに検索をかける。
    3. 両方の結果をまとめてユーザーに表示する。

- **ユーザーインターフェース (UI)**: LINEボットやWeb画面など、ユーザーが写真を送る口を作る部分。


# ナレッジベース作成

詳細は [81-11.プロビジョニング](../81.BedrockKnowledgeBase/81-11.プロビジョニング.md)をご参照ください。  
ここでは **Amazon Bedrock Knowledge Base** を使用しており、**ベクトルストアには Amazon OpenSearch Serverless** を採用しています。

<!--END-->

<br>

# 70-90-021.画像から判定＋
---

<!--BEGIN-->

# 概要


ここでは、**画像から粗大ごみの品目を自動判別**する仕組みを検証しています。

### 処理の流れ

1. **画像を解析して品目名称を特定**
    
2. **ナレッジベースから該当するごみ品目情報を検索し、出し方を判定**
    
3. **判定結果を返却**
    

<img src="../images/gomifile.jpeg" width="400" alt="石油ストーブ">


```mermaid
sequenceDiagram
    participant U as ユーザー
    participant M as マネージャー (Nova Pro)
    participant T as ツール群 (画像解析/対話/判定)
    participant KB as Knowledge Base (RAG)

    U->>M: 画像パス or 品目名を入力
    
    alt 画像あり
        M->>T: analyze_image (画像解析)
        T-->>M: 解析結果 (品目候補・材質など)
    else 画像なし
        M->>M: 入力されたテキストを品目として保持
    end

    loop 情報が揃うまで
        M->>T: generate_contextual_question (動的な質問)
        T-->>U: 「材質は？」や「30cm以上？」と質問
        U->>T: 番号 または テキストで回答
        T-->>M: 回答データをセッションに格納
    end

    M->>T: apply_disposal_rules (ロジック判定)
    T-->>M: 分別区分 (粗大ごみ/燃やす等) を確定

    M->>KB: search_garbage_rule (詳細検索)
    KB-->>M: 自治体特有の出し方・注意点

    M->>T: output_disposal_instructions
    T-->>U: 最終的な「捨て方ガイド」を表示
``` 


### 動的な質問ループ (loop): 
単に順番に質問するのではなく、`generate_contextual_question` が現在のセッション（材質が不明か、サイズが不明か）を見て、その時々に最適な質問をユーザーに投げる様子を表しています。
    
### ツールを介した情報の蓄積: 
マネージャー(M)自身がすべてを覚えるのではなく、ツール(T)を実行するたびに `session_state` が更新され、判定の精度が上がっていく流れです。
    
### 判定とRAGの組み合わせ: 
プログラム内の `determine_disposal_method`（ロジック判定）で大枠の区分を決め、その後に `Knowledge Base`（RAG）で具体的な自治体のルールを補完する「ハイブリッド検索」の形を表現しています。


# Amazon Nova

今回のサンプルコードで画像の解析は、Amazon Novaを使用しています。

**Amazon Nova**は、2024年末にAmazon（AWS）が発表した、自社開発の最新AIモデルシリーズです。  
画像・音声・テキストといった複数のモダリティを理解・処理できる**マルチモーダルモデル**として設計されており、高精度な画像解析をはじめとする幅広いタスクに対応します。

これまでのClaude（Anthropic）やLlama（Meta）といった他社モデルの提供に加え、Amazonが「自社のインフラに最も最適化した脳」としてリリースしました。

### 3つの主な特徴

1. 圧倒的なコストパフォーマンス
    
    同等性能の他社モデルと比較して、利用料金が非常に安く設定されています。大量の画像やテキストを処理する業務システムに最適です。
    
2. マルチモーダル（画像・動画・テキスト）対応
    
    今回のように「画像を見て中身を特定する」といった処理をネイティブにこなせます。
    
3. AWSサービスとの深い親和性
    
    Amazon自身が作っているため、Knowledge BasesやS3、Lambdaとの連携が非常にスムーズで、処理速度も高速です。
    

### Novaファミリーのラインナップ

用途に合わせて3つのサイズがあります。

|**モデル名**|**特徴**|**今回のシステムでの役割**|
|---|---|---|
|**Nova Pro**|最も賢い万能モデル|複雑な画像解析と、RAGを使った正確な回答。|
|**Nova Lite**|高速・低コストなモデル|スピーディなチャット応答や、大量の画像処理。|
|**Nova Micro**|超高速・テキスト専用|シンプルな要約や分類。|

一言で言えば、**「AWSユーザーにとって、最も安くて速くて使い勝手が良い、Amazon純正のAI」**　です。

# サンプルコード

このサンプルコードでは、多様な判定条件に対応するため、また品目特定に失敗した場合にも備えて、**複数の「ツール化エージェント」**　を実装しています。

特に、**画像から品目名の特定ができなかった場合には、「二十質問形式」でユーザーに問いかけながら、段階的に品目名を絞り込む**ような対話フローを採用しています。  
これにより、曖昧な情報や不完全な入力からでも、柔軟にごみ品目の特定を試みることができます。

>[注]実際には、**画像が不鮮明だったり、画像解析で品目の特定ができなかった場合に「二十質問形式」に切り替えるフロー**が用意されていますが、現時点ではその挙動がやや不十分です。  
質問の精度や分岐ロジックに課題があり、ユーザー体験としても洗練されていないため、今後の改善ポイントと考えています。


[image_to_garbage_info_l1.py]
```
import os
import json
import base64
import boto3
from strands import Agent, tool
from strands.models import BedrockModel

# --- 設定 ---
KNOWLEDGE_BASE_ID = "3GC22IOMHK"
REGION = "us-east-1"
MODEL_ID = "amazon.nova-pro-v1:0"

bedrock_agent_runtime = boto3.client("bedrock-agent-runtime", region_name=REGION)
bedrock_runtime = boto3.client("bedrock-runtime", region_name=REGION)
model = BedrockModel(region_name=REGION, model_id=MODEL_ID)

# =============================================================================
# 判定ロジック用データ
# =============================================================================

# 収集不可品目
UNCOLLECTABLE = {
    "区収集不可": [
        "石", "オートバイ", "タイヤ", "ピアノ", "消火器", "ガスボンベ",
        "コンクリートブロック", "耐火金庫", "砂", "土", "バッテリー",
        "注射針", "石油類", "灯油", "ガソリン", "塗料", "レンガ",
        "花火", "マッチ", "モバイルバッテリー"
    ],
    "家電リサイクル": [
        "テレビ", "ブラウン管テレビ", "液晶テレビ", "プラズマテレビ",
        "エアコン", "冷蔵庫", "冷凍庫", "洗濯機", "衣類乾燥機"
    ],
    "PCリサイクル": ["パソコン", "ノートパソコン", "デスクトップパソコン"],
    "モバイルリサイクル": ["携帯電話", "スマートフォン"]
}
・・・中略
```

# 実行

### 鮮明な画像の場合

```
python image_to_garbage_info.py

============================================================
  足立区 ごみ分別AIコンシェルジュ v2.0
============================================================

画像ファイルのパスを入力するか、品目名を直接入力してください。
終了するには 'quit' と入力してください。

[あなた] images/gomifile.jpeg
<thinking> まずは画像解析ツールを使用して、画像から品目の特徴を抽出します。 </thinking>

Tool #1: analyze_image
<thinking> 画像解析が成功したので、次に収集不可品目チェックを行います。電気ヒーターは家電リサイクル法の対象品目です。 </thinking>
Tool #2: apply_disposal_rules
<thinking> 電気ヒーターは収集可能で、粗大ごみとして処分する必要があります。詳細な分別ルールを検索します。 </thinking>
Tool #3: search_garbage_rule
<thinking> 電気ヒーターの詳細な分別ルールが検索できたので、最終的な処分方法を出力します。 </thinking>
Tool #4: output_disposal_instructions

============================================================
【 電気ヒーター 】の捨て方
============================================================

■ 基本情報
  材質: プラスチック
  サイズ: small
  特記事項: 温度設定可能, タイマー機能あり, 省エネモード搭載

■ 分別区分
  【粗大ごみ】
  手数料: 400円
  備考: 30cm角以上のため粗大ごみ

■ 詳細情報
  電気ヒーターは、30cm角未満のものは材質に応じて出してください。30cm角以上のものは粗大ごみとして扱われ、手数料は400円です。プラスチック製の電気ヒーターの場合は、プラスチック分別回収の対象となります。注意点としては、汚れが落ちない場合は燃やすごみとして出してください。

============================================================
電気ヒーターの捨て方は以下になります。

- 30cm角未満のものは材質に応じて出してください。
- 30cm角以上のものは粗大ごみとして扱われ、手数料は400円です。
- プラスチック製の電気ヒーターの場合は、プラスチック分別回収の対象となります。
- 注意点としては、汚れが落ちない場合は燃やすごみとして出してください。

処分方法が確認できました。他にご不明点があれば、お気軽にお尋ねください。
[あなた] quit

ご利用ありがとうございました。
```

<!--END-->


# 80-00-000.AgentCoreとは
---

<!--BEGIN-->


AWS Bedrock AgentCoreは、AIエージェントをプロトタイプから「エンタープライズ品質の商用環境」へ移行させるための、**フルマネージドな実行基盤スイート**です。

一言で言えば、**「どんなフレームワーク（Strands Agent, LangGraph, CrewAI等）で書かれたエージェントでも、セキュアにデプロイ・運用できるインフラ基盤」** です。

# 概要

これまでの「Amazon Bedrock Agents」がノーコード/ローコードなエージェント構築サービスだったのに対し、**AgentCore**はプログラマブルで自由度の高い「基盤（Platform）」を提供します。

- **フレームワークに依存しない:** 好きなSDKやライブラリでエージェントを書けます。
    
- **モデルに依存しない:** Bedrock上のモデルだけでなく、外部モデルも利用可能です。
    
- **運用に特化:** セキュリティ、メモリ管理、API連携、観測性を「部品（コンポーネント）」として提供します。
    

以下、AgentCoreを構成するサービスと、それらがどのように連携するかを示します。

```mermaid
graph LR
    subgraph "Development"
        F[ Any Model & Framework<br/> CrewAI / LangGraph / Strands / etc. ]
    end

    subgraph "AgentCore Control Plane"
        Identity[Identity: Auth & IdP]
        Eval[Evaluations: Quality Signals]
        Obs[Observability: OTEL Tracing]
    end

    subgraph "Data & Execution (Runtime)"
        R{{"Runtime (Serverless Micro-VM)"}}
        Memory[(Memory: STM/LTM)]
        Policy{{"Policy: Cedar/Guardrails"}}
        
        subgraph "Extended Capabilities"
            CI[Code Interpreter]
            BR[Browser]
        end
    end

    subgraph "External Integrations (Gateway)"
        G[Gateway: MCP Hub]
        G --> T[APIs / Lambda / Salesforce / Slack]
    end

    F --> R
    R <--> Memory
    R --> Policy
    Policy --> G
    R --> CI
    R --> BR
    R --> Obs
    Obs --> Eval
    Identity --> R
```


| **カテゴリ** | **要素**               | **核心機能と統合対象**                                                                                                |
| -------- | -------------------- | ------------------------------------------------------------------------------------------------------------ |
| **実行基盤** | **Runtime**          | **セキュアなサーバーレス実行環境。** 高速なコールドスタートとセッション分離を実現。CrewAI, LangGraph等のOSSフレームワーク、Bedrock内外（OpenAI, Gemini等）のモデルに対応。 |
| **記憶**   | **Memory**           | **文脈を理解する記憶。** 短期（会話）と長期（セッション跨ぎ）の記憶を管理。StrandsやLlamaIndexと連携し、エージェント間での記憶共有や経験学習が可能。                        |
| **接続**   | **Gateway**          | **ツール統合のハブ。** APIやLambdaをMCP規格に変換。SalesforceやSlackなどの既存サービスを数行のコードでAIツール化。                                   |
| **認証**   | **Identity**         | **アイデンティティ管理。** Cognito, Okta, Azure Entra ID等の既存IdPと連携し、ユーザー移行なしで安全な認証フローを構築。                               |
| **拡張機能** | **Code Interpreter** | **分離されたサンドボックス。** Python, JS, TSを実行し、複雑な計算やデータ処理の精度を向上。                                                      |
| **操作**   | **Browser**          | **クラウド型ブラウザ環境。** Playwright等を使用し、エージェントがWebサイトの閲覧、フォーム入力、情報抽出を安全に実行。                                         |
| **観測性**  | **Observability**    | **統合デバッグビュー。** OpenTelemetry (OTEL)形式でトレースとログを出力。パフォーマンスのボトルネックを可視化。                                         |
| **評価**   | **Evaluations**      | **データ駆動型の品質評価。** セッションやトレースに基づき、タスク完遂率や信頼性を測定。結果はCloudWatch連携のObservabilityで確認可能。                            |
| **統制**   | **Policy**           | **決定論的な境界制御。** 自然言語またはCedar言語で「どのツールを、いつ、誰が使えるか」を定義。Gatewayでの実行前に介入し、ビジネスルールを強制。                             |

# 実装のポイント：要素間の関係性

- **「信頼」のチェーン (Identity → Runtime → Policy):** ユーザーが既存のIdP（Identity）でログインし、隔離された環境（Runtime）でエージェントが動きます。エージェントが外部ツールを呼ぶ際、Policyがその行動がルールに沿っているか（Cedar言語等で）即座に判定します。
    
- **「成長」のサイクル (Observability → Evaluations → Memory):** エージェントの全挙動はOTEL形式で記録（Observability）され、それが評価エンジン（Evaluations）で分析されます。良かった行動やユーザーの反応はMemoryとして蓄積され、次回のセッションに活かされます。
    
- **「拡張」の柔軟性 (Gateway + Browser/Code Interpreter):** 自社APIはGateway経由で、Web上の情報はBrowser経由で、複雑なロジックはCode Interpreterで処理します。これらはすべて「ツール」としてエージェントに提供されます。
    
>[注]
開発において、これらすべての要素を**一度に**使用する必要があるわけではありません。

# 開発・デプロイのステップ

ドキュメントにある「Toolkit」を使用した開発の全体的な流れは以下の通りです。

- **Toolkitの導入:** `bedrock-agentcore-starter-toolkit` をインストール。
    
-  **プロジェクト作成:** CLI（`agentcore create`）を使用して、テンプレートからプロジェクトを生成。
    
- **エージェント実装:** 好きなフレームワーク（Strands Agents, LangGraph等）でビジネスロジックを記述。
    
- **デプロイ:** `bedrock-agentcore-app` クラスを使用して、数行のコードでAWS上のRuntimeへデプロイ。
    
- **運用:** コンソールやAPIを通じて、メモリの最適化やポリシー（ガードレール）の適用を行う。
    
# まとめ

AgentCoreは、 「自由にエージェントを開発しつつ、企業が必要とするセキュリティ、ガバナンス、信頼性を後付けではなく基盤として提供する」*ための仕組みです。

これにより開発者は、サーバーの管理や複雑なデータベース設計、セキュリティの実装に時間を取られることなく、**「いかに賢いエージェントを作るか」** という本質的な開発に集中できるようになります。


# 節の構成について
- **10:基本構成**
- **20:ランタイム**
- **30:可観測性&評価**

<!--END-->

詳細は[図解Strandsエージェント徹底解説](https://github.com/awk256/strandsagents)を参照してください。



