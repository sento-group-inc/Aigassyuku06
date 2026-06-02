# AI組織のCEOになるまでの旅 — Journey Guide

> このフォルダは、Claude Code または Codex との対話を通じて「AI社員チームのCEO」になるための段階的ガイドです。
> 合宿サイト（ツールの操作方法）と並行して使います。

---

## ゴール：「AI組織のCEOになった状態」とは

以下が全部 **YES** になっている状態です。

- [ ] AIに「うちの会社は…」「僕の役割は…」と説明せずに仕事を始められる
- [ ] 自分の文章をAIがレビューして「自社らしくない表現」を指摘できる
- [ ] Asanaのタスクを見てAIが自律でタスクを拾い、実行し、報告する
- [ ] 夜のうちにAIが宿題を終わらせていて、朝確認するだけでよい
- [ ] AIが間違えたら「AGENTS.mdに追記」してルール化できる

---

## 4つのセッション

| セッション | ゴール | 所要時間 | 生成するファイル |
|-----------|-------|---------|---------------|
| **Session 01** | 文脈エンジンを作る | 約60分 | AGENTS.md群（5ファイル） |
| **Session 02** | AI組織を設計する | 約45分 | SKILL.md群（3ファイル）+ 組織図 |
| **Session 03** | タスクを自動化する | 約30分 | handoffs/テンプレート + Asana連携 |
| **Session 04** | 自律運用ルールを決める | 約30分 | 権限設定 + 週次メンテ |

**合計: 約2.5〜3時間**

---

## セットアップ：このリポジトリを同期する（最初に1回だけ）

このガイド（`journey/`）は GitHub リポジトリ **`sento-group-inc/Aigassyuku06`** に入っています。
まず手元のMacにリポジトリを同期（clone）して、その中のファイルをAIに読ませます。

### Step 1: リポジトリをcloneする

ターミナルで、作業したい場所（例：デスクトップ）へ移動してから実行：

```
cd ~/Desktop
git clone https://github.com/sento-group-inc/Aigassyuku06.git
cd Aigassyuku06
```

### Step 2: このフォルダをCodex / Claude Codeで開く

- **Codex App**: 「フォルダを追加」から、今cloneした `Aigassyuku06` フォルダを開く
- **Claude Code**: ターミナルで `Aigassyuku06` フォルダに入って `claude` を起動
- **Cursor等のエディタ**: `Aigassyuku06` フォルダを開く

### Step 3: 最新に保つ（合宿当日の朝など）

講師がガイドを更新することがあります。最新版に揃えるには：

```
git pull
```

> Gitに不慣れでも大丈夫。上のコマンドをそのままコピペして、わからなければAIに「このコマンドは何をするの？」と聞いてください。

---

## 合宿での使い方

### Day 1 午前（9:30〜13:00）
→ **Session 01** を完了させる。これが全ての土台になる。

### Day 1 午後（13:00〜18:00）
→ **Session 02・03** を進める。合宿サイトの各セクションと並行。

### Day 1 夕方（18:00〜）
→ Session 04 を終わらせて、「明日発表できる状態」を作る。

### Day 2 朝（9:00〜10:00）
→ 各自のAI組織で実際に何かタスクをやらせ、結果を持って発表。

---

## セッションの始め方

同期した `Aigassyuku06` フォルダをCodex / Claude Codeで開いた状態で、以下の一文を入力するだけです：

```
このリポジトリの journey/Session01-context-engine.md を開いて読んで、その手順に沿って私を導いてください。
```

AIが同期したGitHubリポジトリ内のファイルを読んで、あなたへの質問から始めてくれます。

以降のセッションも同じ形式で始められます：

```
このリポジトリの journey/Session02-ai-org-design.md を開いて、前回作ったファイルを読んでから続けてください。
```

> ポイント: ガイド本体（journey/）は同期したリポジトリ、あなたが**作るファイル**（AGENTS.md等）は自分の作業フォルダ（codex-bunshin-os/）。読む場所と作る場所が分かれています。下の図を参照。

---

## ファイルが生成される場所

同期した `Aigassyuku06` フォルダの中に、あなた専用の **`codex-bunshin-os/`** サブフォルダを作り、そこに生成します。
（このフォルダは `.gitignore` 済みなので、あなたの会社情報がGitHubに上がることはありません。安心して書けます）

```
Aigassyuku06/                  ← 同期したリポジトリ（読む側）
├── journey/                   ← このガイド（講師が用意）
├── index.html / prep.html ...
└── codex-bunshin-os/          ← あなたが作る側（gitignore済み・GitHubに上がらない）
├── AGENTS.md              ← Session 01（AI組織の憲法・目次）
├── memory.md              ← Session 01（会社の長期記憶）
├── state.md               ← Session 01（今週の重点）
├── contexts/
│   ├── brand-voice.md     ← Session 01（口調・文体）
│   └── philosophy.md      ← Session 01（価値観・判断軸）
├── skills/
│   ├── director-agent/    ← Session 02
│   ├── brand-voice-reviewer/ ← Session 02
│   └── [業務名]/          ← Session 02
    ├── contexts/
    │   └── org-chart.md   ← Session 02（AI組織図）
    └── handoffs/
        ├── template-task.md   ← Session 03
        └── template-review.md ← Session 03
```

> セッション開始時に「`codex-bunshin-os/` フォルダを作って、その中にファイルを生成して」とAIに伝えればOK。各Sessionの手順にも書いてあります。

---

## 詰まったら

### AIが変な回答をしたとき
→ 「それは違います。〇〇です」と直接言って修正させてください。

### ファイルを作り直したいとき
→ 「AGENTS.mdを最初から作り直してください」と言えばOK。

### セッションが長くなりすぎたとき
→ 「今日のセッションをここで終了して、AGENTS.mdを保存してください」と言って区切る。
→ 次回は「journey/Session0X.md を読んで、前回の続きから始めてください」で再開。

---

## 関連リンク（常設）

- 合宿サイト本編: https://aigassyuku06.vercel.app/
- AGENTS.md解説: https://qiita.com/nogataka/items/ad15bfa383c98ae5cc36
- grill-me（AI Hero）: https://www.aihero.dev/my-grill-me-skill-has-gone-viral
