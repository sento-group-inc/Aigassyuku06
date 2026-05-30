# Handoff: AI合宿サイト 第2次改修（Claude → Codex）

- **From**: claude (team=wajima)
- **To**: codex (team=wajima)
- **Date**: 2026-05-30
- **対象repo**: `/Users/wajimayuki/Cursor/Aigassyuku06/`
- **公開URL**: https://aigassyuku06.vercel.app/
- **元plan（Claude private）**: `/Users/wajimayuki/.claude/plans/file-users-wajimayuki-cursor-aigassyuku0-zippy-eclipse.md`（このhandoffに全文転記済みなので参照不要）

和島承認済み。**実装はCodexが全部やる**。Claudeはオーケストレーションのみ（コード編集しない）。
本ファイル単独で実装できるよう自己完結で書く。

---

## 現状（第1次改修済み）

- `index.html` — Section 00-14。Mermaid 9図。CLIは1コマンド1ブロック化済み。`--max:1180px`。
  - flow nav: 00全体像 / 01なぜ作る / 02深掘り(grill) / 03Codex / 04引っ越し / 05AGENTS / 06MCP / 07Skill化 / 08gogcli / 09GAS / 10NotebookLM / 11Vercel / 12起動維持 / 13育てる / 14Agent作成
- `schedule.html` — 2日間。Mermaid。`--max:900px`。
- `repos.html` — リポジトリ表。`--max:1100px`。
- `.claude/launch.json` — `python3 -m http.server 8787`（preview用）。
- デザイン変数: `--accent:#0f766e` / `--ink:#17211d` / `--radius:8px` 等。Mermaid themeVariables は accent系・fontSize 13px。

---

## 守るルール（既存踏襲）

1. **CLIは1コマンド1ブロック**（複数コマンドを1つの `<pre>` にまとめない。誤コピー防止）。
2. **参考リンクは常設**（`.resource` ボックスに `target="_blank" rel="noopener"`）。
3. Mermaid themeVariables は全ページ統一。**fontSize は 13px→15px に上げる**。
4. APIキー/PAT/パスワードは必ずプレースホルダ（`YOUR_XXX`）。AIに代行入力させない旨を明記。
5. 和島文体: 煽り禁止・体言止め単独行禁止・絵文字本文禁止。

---

## 実装タスク（item順）

### item 1: 全体像の縦化
`index.html` Section 00 の Mermaid 2図を `flowchart LR` → `flowchart TB`。
- ツール連携図: Claude Code→Codex→AGENTS→MCP→Skill→gogcli→Vercel→継続改善 を上から下。
- 2日間タイムライン: `subgraph` 横並びをやめ `flowchart TB`。Day1ノード群を縦、その下にDay2。改行 `\n` 維持。
- `schedule.html` の全体フロー図も `direction TB` 統一（横スクロール回避）。
- Mermaid fontSize 15px に。

### item 2: フル幅レイアウト（4ページ共通）
- `--max`: index/schedule/repos/prep すべて **1480px**。
- index `.layout` の左TOCを 248px→280px、本文は `minmax(0,1fr)`。
- `.hero-inner` `.flow` `.layout` `footer` の左右padding を `clamp(16px,4vw,40px)`。
- 920px以下のレスポンシブは現状維持。

### item 3 + 9: prep.html 新規（事前準備 + 用語プライマー）
index と同じデザイン言語。構成:
1. なぜ事前準備か（午前をセットアップで溶かさない）。
2. **用語プライマー（item9）**:
   - AGENTS.md = AIエージェント向けREADME。複数ツール共通(Cursor/Copilot/Codex CLI)。Linux Foundation AAIF標準。
   - CLAUDE.md = Claude Code専用。`@import`・Planモード等ツール固有。
   - 共通指示→AGENTS.md / ツール固有→CLAUDE.md。シンボリックリンクで互換。
   - 用語表: インストラクション・バジェット(150-200指示が限界) / Context Rot(トークン増で検索性能劣化) / Progressive Disclosure(段階的開示)。
   - 参考(常設): https://qiita.com/nogataka/items/ad15bfa383c98ae5cc36 / https://qiita.com/dai_chi/items/61019c602c2c40dade07
3. インストール(1コマンド1ブロック): Homebrew→Node.js→Git→Codex App(https://note.com/munakata_souri/n/n4aacfa6d9729)→(任意)Claude Code→ngrok→agent-browser。
4. アカウント作成(リンクのみ・代行しない): ChatGPT(Codex) / GitHub / Vercel / Asana / ngrok。
5. 事前チェックリスト(checkbox)。

### item 4: agmsg デュアル運用セクション（index 新規 `#agmsg`）
- 何ができるか: 同teamにClaude CodeとCodexをjoinし `/agmsg send` で相互にタスクを渡す。「Claudeで計画→Codexで実行」を口頭説明なしで往復。
- セットアップ(1コマンド1ブロック):
  - `~/.agents/skills/agmsg/scripts/join.sh <team> <name> claude-code "$(pwd)"`
  - `~/.agents/skills/agmsg/scripts/join.sh <team> <name> codex "$(pwd)"`
  - `/agmsg` 受信 / `/agmsg send <agent> "<msg>"` 送信 / `/agmsg team` 名簿
- Mermaid TB: Claude(計画)→agmsg→Codex(実行)→agmsg→Claude(レビュー)
- 注記: チーム名/エージェント名は自分で決める。スクリプト直接編集しない。

### item 5: Asana セクション（index 新規 `#asana`）+ IMAGES-TODO.md
手順:
1. https://asana.com/ でアカウント作成(各自・代行しない)。
2. 右上プロフィール→My Settings→Apps→Manage Developer Apps（https://app.asana.com/0/my-apps ）。
3. + Create new token→名前→規約同意→Create→Copy（1回しか表示されない）。
4. PAT注記: パスワード同様。`Authorization: Bearer <PAT>`。
5. Codex依頼例(PATは `YOUR_ASANA_PAT`): 「このPATでAsana APIに接続し、〇〇プロジェクトにタスクを5件登録して」。
**IMAGES-TODO.md(新規)** — インターン向け。表で: ファイル名候補 / 配置先(どのHTMLのどのセクション) / 何の画面か / 取得元URL。
例: asana-my-apps.png / asana-create-token.png / ngrok-authtoken.png / agent-browser-snapshot.png。
HTML側は `<!-- IMG: asana-my-apps.png ここに挿入予定 -->` のプレースホルダコメントを置く。

### item 6+7: ngrok セクション + 会社方針HTML公開演習（index 新規 `#ngrok`、Vercel後）
- インストール(1コマンド1ブロック):
  - `brew install --cask ngrok`
  - トークン取得: https://dashboard.ngrok.com/get-started/your-authtoken
  - `ngrok config add-authtoken YOUR_NGROK_TOKEN`
  - `ngrok http 8000`（`python3 -m http.server 8000` を外部URL化）
- 演習: Codexに「自社のバリュー/方針を1枚HTMLにして」→ローカルサーバ→ngrokでURL共有。
- なぜMarkdownよりHTMLか（https://note.com/kudoucraft/n/n69e5650a4302 常設リンク）:
  1.情報密度(表/CSS/SVG/インタラクティブ) 2.視覚的明瞭さ・モバイル対応 3.共有が容易(URL一発) 4.双方向操作 5.文脈活用 6.エンゲージメント向上
- Vercel(恒久)とngrok(一時・即時共有)の使い分けを1行。

### item 8: agent-browser セクション（index 新規 `#agent-browser`、Section14後）
- 何ができるか: AIエージェント用ブラウザ操作CLI(Rust)。公開URL自体をAIに読ませながら進める。`https://aigassyuku06.vercel.app/` をAIに読ませて「次どこ？」を聞ける。
- インストール(1コマンド1ブロック):
  - `npm install -g agent-browser`
  - `agent-browser install`（Chrome for Testing取得）
  - (代替) `brew install agent-browser`
- 使い方:
  - `agent-browser open https://aigassyuku06.vercel.app/`
  - `agent-browser snapshot -i`（要素を `@e1` 等で取得）
  - `agent-browser click @e1` / 変化後に再snapshot
  - `--json` で機械可読
- 参考(常設): https://github.com/vercel-labs/agent-browser
- Mermaid TB: 公開URL→open→snapshot→AIが現在地把握→次の手を提案。

### ナビ再設計
- prep/schedule/repos は flow nav 外（ヒーロー直下 page-nav と TOC下部に集約）。
- index 本編に追加: `#agmsg` `#asana` `#ngrok` `#agent-browser`。
- flow nav 番号振り直し（00-18程度）。`grid-template-columns: repeat(N,...)` の N 更新。
- TOC（左サイドバー）も同期。全ページ相互リンク。
- index Section 05(AGENTS) 冒頭に「用語は prep.html 参照」1行リンク。

---

## 検証
- `python3 -m http.server 8787` でローカル確認。Mermaid が**縦**でレンダリング。
- 全ページ幅が広がっている(--max 1480)。
- prep.html / 新セクションが相互リンク、flow nav/TOC一致。
- CLIブロックが1コマンド1ブロック維持。
- IMAGES-TODO.md と HTML内プレースホルダコメントが対応。

---

## item 10（Claude側で別途実施・Codexは批評を返す）
和島の指示: 「もっと良い講義資料にするために何が必要か」を**和島の認識の範囲外**から。
epoché（判断停止）→前提の脱構築→最重要前提を1つ→異圏(制度/他業界/海外/歴史)の**固有名詞**で覆す→崩れる構造と最も不協和な事例がなぜ成立するか。同方向の追認・形而上的一般論は禁止。
（別メッセージで送る。Codexは独自の圏外視点で返答すること。Claudeの叩き台に同調しない。）
