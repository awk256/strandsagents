
**Apache Strands Agent（ストランズ・エージェント）** は、AWS主導で開発された**オープンソースのAIエージェントSDK**で、2025年5月16日に一般公開されました。  
PythonまたはTypeScriptで、**ツール連携（Tool Use）**や**マルチエージェント（Multi-Agent）**の構築を直感的に行える**軽量なフレームワーク**です。

**「もっとシンプルに、そして人間のように自律的に動くエージェントを作りたい」** という開発者の想いから生まれ、**LangChainの対抗馬**としても注目を集めています。


![[strands_agent_technical_guide.png|400]]
*「図解」Strandsエージェント徹底解説*


本サイト（**「図解」Strandsエージェント徹底解説**）は、筆者が **Strands Agent** を学習する過程で記録したメモをベースに構成しています。  
これは、筆者のこれまでの執筆経験から、**膨大な知識体系を短期間で習得するには、「一冊の本を書くようにまとめるアプローチ」が最も効果的**であると考えているためです。

本サイトの内容が、Strandsを学ぶ皆様の一助となれば幸いです。  
ただし、**筆者の感性に基づいて要約・再構成した内容が含まれているため、掲載内容やサンプルコードをご利用の際は、ご自身の判断と責任にてお願いいたします**。

また、**掲載されている情報は出典を明記いただければ、自由にご活用いただけます**。  
内容は随時更新・変更される可能性がありますので、あらかじめご了承ください。

**2026年1月1日**

---
### 著者プロフィール
#### 李 昌桓（LEE CHANFUAN）
- **[クリエーションライン株式会社](https://www.creationline.com) 在籍
- **現代的なデータ基盤構築のソリューション・アーキテクト、リードエンジニアとして活動中
- **代表的なプロジェクト：
	- **大手通信キャリアのデータウェアハウス構築のDBA・バックエンドの開発
	- **Donso Factory IoTのデータモダナイゼーション
	 - **ヨドバシカメラのデータモダナイゼーション
	 - **モノタロウのデータモダナイゼーションなど  

#### 著書
- **Amazon Cloudテクニカルガイド ― EC2/S3からVPCまで徹底解析
- **Amazon Elastic MapReduceテクニカルガイド ― クラウド型Hadoopで実現する大規模分散処理
- **Cypherクエリー言語の事例で学ぶ グラフデータベース Neo4j
- **Neo4jを使うグラフ型データベース入門（共著）
- **RDB技術者のためのNoSQLガイド（共著）
- **図解Strandsエージェント徹底解説

---

### 掲載内容について

**図解Strandsエージェント徹底解説**は、Strandsエージェント及びAWSの公式ドキュメント、Githubのサンプルコードをベースにしています。

- [Strandsエージェントの公式ドキュメント/](https://strandsagents.com/latest/documentation/docs/)
- [StrandsエージェントのGithub](https://github.com/strands-agents/)
- [Amazon Bedrodk AgentCore Samples](https://github.com/awslabs/amazon-bedrock-agentcore-samples)
- [Amazon Bedrock AgentCore Developer Guide](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/what-is-bedrock-agentcore.html)
### 章立てについて

#### 📌 「+」がついてタイトル

公式ドキュメントに載ってない、**筆者の創意工夫によるページには「タイトル+」** にして区分しています。

### 目次

#### 10.基本構成
```dataview
LIST
FROM "AI/Strands Agents/10.基本構成"
```

#### 20.安全性とセキュリティ
```dataview
LIST
FROM "AI/Strands Agents/20.安全性とセキュリティ"
```

#### 30.可観測性とセキュリティ
```dataview
LIST
FROM "AI/Strands Agents/30.可観測性とデバック"
```

#### 40.評価SDK
```dataview
LIST
FROM "AI/Strands Agents/40.評価SDK"
```

#### 50.デプロイ
```dataview
LIST
FROM "AI/Strands Agents/50.デプロイ"
```

#### 60.実行環境
```dataview
LIST
FROM "AI/Strands Agents/60.実行環境"
```

#### 70.サンプルコード
```dataview
LIST
FROM "AI/Strands Agents/70.サンプルコード"
```

#### 80.Amazon Bedrok AgentCore


```dataview
LIST
FROM "AI/Strands Agents/80.Amazon Bedrok AgentCore"
```