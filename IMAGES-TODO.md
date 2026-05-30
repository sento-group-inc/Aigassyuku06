# IMAGES-TODO

合宿サイト第2次改修で、あとから差し込むスクリーンショット一覧。
APIキー、PAT、メールアドレス、個人名、ワークスペース名が映る場合は必ずマスクする。

| ファイル名 | 差し込み先 | 撮る画面 | 参考URL | 注意 |
|---|---|---|---|---|
| `asana-my-apps.png` | `index.html` Section 09 Asana | AsanaのManage Developer Apps画面 | https://app.asana.com/0/my-apps | ワークスペース名・メールアドレスを隠す |
| `asana-create-token.png` | `index.html` Section 09 Asana | Create new tokenの入力画面 | https://app.asana.com/0/my-apps | PAT実値は絶対に映さない |
| `ngrok-authtoken.png` | `index.html` Section 14 ngrok | ngrokのAuthtoken取得画面 | https://dashboard.ngrok.com/get-started/your-authtoken | token文字列を隠す |
| `agent-browser-snapshot.png` | `index.html` Section 18 agent-browser | `agent-browser snapshot -i` の出力例 | https://github.com/vercel-labs/agent-browser | ローカルパスや個人名を隠す |
| `prep-codex-app-download.png` | `prep.html` Codex準備 | Codex App公式ページのダウンロード導線 | https://developers.openai.com/codex/app/ | 公式ページのみ撮る |
| `prep-vercel-github-login.png` | `prep.html` アカウント準備 | VercelのContinue with GitHub画面 | https://vercel.com/signup | 個人アカウント情報を映さない |
| `homebrew-terminal-open.png` | `prep.html` Step 1 Homebrew | Spotlight（⌘+Space）で「terminal」と検索している画面 | — | 個人名・ファイル名を映さない |
| `homebrew-site.png` | `prep.html` Step 1 Homebrew | brew.sh 公式サイトのコピーボタン位置がわかる画面 | https://brew.sh/ | そのまま撮影OK |
| `homebrew-install-running.png` | `prep.html` Step 1 Homebrew | ターミナルでインストールコマンドが実行中の画面 | — | パスワードは必ず隠す。実行中のプログレス表示が理想 |
| `composio-dashboard.png` | `prep.html` Step 7 Composio | Composioダッシュボードのトップ画面 | https://dashboard.composio.dev/ | APIキーを完全に隠す。接続ツール一覧が見えると良い |
| `composio-apikey.png` | `prep.html` Step 7 Composio | Composio APIキー取得画面 | https://dashboard.composio.dev/ | キーの実値は隠す。ページ上の取得UIがわかる画面 |
| `composio-tools.png` | `prep.html` Step 7 Composio | Composioの接続ツール一覧（GitHub/Asana/Slack等が並ぶ画面） | https://dashboard.composio.dev/ | 個人情報なし。ツール一覧がわかる画面 |

## 配置先

撮影後は `assets/images/v2/` に保存し、HTML側の `<!-- IMG: ... -->` コメントを `figure` に置き換える。

例:

```html
<figure>
  <img src="assets/images/v2/asana-my-apps.png" alt="Asana Developer Apps画面" loading="lazy">
  <figcaption>AsanaのDeveloper AppsからPersonal Access Tokenを作成する。</figcaption>
</figure>
```
