


# git

OK、超シンプルに手順だけ。

### どの認証で押す？

- **SSH**：`git@github.com:awk256/strandsagents.git`（事前にSSH鍵登録が必要）
    
- **HTTPS**：`https://github.com/awk256/strandsagents.git`（PAT＝個人アクセストークン推奨）
    

---

### 新規フォルダから初回プッシュ


```bash
cd /path/to/your/local/strandsagents
git init
git add .
git commit -m "Initial commit"
git branch -M main
# どちらか一方を使う
git remote add origin git@github.com:awk256/strandsagents.git
# git remote add origin https://github.com/awk256/strandsagents.git
git push -u origin main
```


### 既存ローカルリポをそのリモートへ

```bash
cd /path/to/your/local/strandsagents
git remote -v
# origin が無ければ追加、有れば差し替え
git remote add origin git@github.com:awk256/strandsagents.git || \
git remote set-url origin git@github.com:awk256/strandsagents.git
# 既存が master なら main にリネーム（任意）
git branch -M main
git push -u origin main
```

### よくあるハマり

- **認証失敗（HTTPS）**：パスワードではなく **Personal Access Token** を入力  
    （GitHub → Settings → Developer settings → Personal access tokens）
    
- **鍵が無い（SSH）**：`ssh-keygen -t ed25519` → 公開鍵を GitHub に登録 → `ssh -T git@github.com` で疎通
    
- **大きいファイル**：100MB超は **Git LFS** を利用（`git lfs install && git lfs track "<pattern>"`）
    
- **.gitignore**：言語向けテンプレを追加（例：Python の `__pycache__/`, Node の `node_modules/` など）
    

必要なら、あなたの環境（SSH/HTTPSどちらか、既存ブランチ名）に合わせて**コマンドを1本化**して出します。どちらでいきます？（仮：SSH）


### Python/Node/一般向けの最小
```

cat > .gitignore << 'EOF'
# OS
.DS_Store
Thumbs.db

# Node
node_modules/
npm-debug.log*

# Python
__pycache__/
*.py[cod]
.env

# Others
dist/
build/
*.log
EOF
```

### Power Shellコマンド

```
# 隠しファイル込みで一覧
ls -Force       # または  Get-ChildItem -Force

# .git フォルダの存在確認
Test-Path .git

# リポジトリ判定（.git の実体パスが出ればOK）
git rev-parse --git-dir

```

### 追跡解除（ワーキングツリーのファイルは残る）
git rm -r --cached -- Tips.md

### テンプレート１

概要
概念図（縦型のmermaid）
- 箇条書き形式の概念図の説明
実装のポイント
まとめ


### テンプレート２

概要
概念図(縦型のmermaid)
- 箇条書き形式の概念図の説明
実行のポイント
サンプルコード
まとめ



### aws bedrock list-foundation-models

```
aws bedrock list-foundation-models --region us-east-1 --query "modelSummaries[*].modelId" --output table

---------------------------------------------------
|              ListFoundationModels               |
+-------------------------------------------------+
|  nvidia.nemotron-nano-12b-v2                    |
|  anthropic.claude-sonnet-4-20250514-v1:0        |
|  anthropic.claude-haiku-4-5-20251001-v1:0       |
|  openai.gpt-oss-120b-1:0                        |
|  stability.stable-creative-upscale-v1:0         |
|  qwen.qwen3-next-80b-a3b                        |
|  amazon.nova-2-multimodal-embeddings-v1:0       |

```

### pipパッケージの一覧確認 
uv pip list

###  ファイルの場所を確認
python -c "import strands.session; print(strands.session.__file__)"

### 中身（メソッド名など）を一覧表示
python -c "import strands.session; print(dir(strands.session.FileSessionManager))"


### strandsパッケージの中にどんなサブモジュールがあるか一覧表示
find /home/ubuntu/.venv/lib/python3.12/site-packages/strands -maxdepth 2 -type d
/home/ubuntu/.venv/lib/python3.12/site-packages/strands
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/__pycache__
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/telemetry
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/telemetry/__pycache__
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/handlers
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/handlers/__pycache__
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/agent
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/agent/__pycache__
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/agent/conversation_manager
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/experimental
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/experimental/__pycache__
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/experimental/steering
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/experimental/hooks
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/experimental/tools
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/experimental/bidi
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/models
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/models/__pycache__
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/types
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/types/__pycache__
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/hooks
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/hooks/__pycache__
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/session
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/session/__pycache__
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/event_loop
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/event_loop/__pycache__
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/multiagent
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/multiagent/a2a
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/tools
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/tools/__pycache__
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/tools/mcp
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/tools/structured_output
/home/ubuntu/.venv/lib/python3.12/site-packages/strands/tools/executors



### 「図解 Strandsエージェント徹底解説」表紙イメージ

#### 1. キービジュアルのコンセプト

未来的なUI、思考の可視化、ツール連携をテーマに、AIの「知性」とプログラムの「構造」が融合する様子を表現します。

**【メインイメージ】**  
中央に、光り輝く複雑なネットワーク図が描かれた**「透明な脳」**のようなオブジェクトを配置。これは、AIの思考プロセスとStrandsエージェントの内部構造を象徴。

---

#### 2. 要素と配置

- **最前面**:
    
    - **タイトル**: 「図解 Strandsエージェント徹底解説」
        
        - フォント: 視認性が高く、少し未来的なゴシック体
            
        - 色: 白または明るいシルバー（背景と高コントラスト）
            
    - **サブタイトル**: 「A next-generation framework for operating AI.」
        
        - フォント: タイトルよりやや小さめで統一感をもたせる
            
        - 色: タイトルと同系色で、やや落ち着いたトーン
            
- **中央（透明な脳の内部）**:
    
    - **思考の可視化**: 半透明の多角形と線が複雑に絡み合った光るネットワーク構造
        
    - **アイコン**: 各所に以下の小アイコンを配置し概念を可視化
        
        - ⚙️ ツール連携
            
        - 🧠 AIの思考
            
        - 📜 システムプロンプト
            
        - 🔗 状態管理（State）
            
        - 🌐 グローバルアクセス
            
- **背景**:
    
    - **色**: 深いネイビーやダークパープルのグラデーション（サイバーパンク風）
        
    - **パターン**: 微細なグリッドやデジタルノイズで技術書らしさを演出
        
- **下部/隅**:
    
    - **著者名**: 李 昌桓
        
    - **キーワード（新バージョン）**:  
        `Amazon Bedrock AgentCore・Runtime・Gateway・Memory・Observability・Evaluations`  
        → 小さな文字で背景に馴染むように分散配置
        

---

#### 3. 全体的なトーンと雰囲気

- **先進的で知的**: 最新AI技術にふさわしい洗練された表紙
    
- **視覚的理解**: 図解中心で直感的に内容を掴める印象
    
- **信頼性**: 実務に即した堅実な技術情報を伝える安心感