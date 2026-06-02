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

Codex または Claude Code を開いて、以下の一文を入力するだけです：

```
journey/Session01-context-engine.md を読んで、ここから始めてください。
```

AIがファイルを読んで、あなたへの質問から始めてくれます。

---

## ファイルが生成される場所

各セッションが作るファイルは、あなたの **作業フォルダ（codex-bunshin-os/）** 内に保存されます。

```
codex-bunshin-os/
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
│   └── org-chart.md       ← Session 02（AI組織図）
└── handoffs/
    ├── template-task.md   ← Session 03
    └── template-review.md ← Session 03
```

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
