# Codex分身OS 合宿サイト

2026年6月9日-10日のAI合宿用の静的HTML講義サイトです。

## 構成

- `index.html` — 講義サイト本体
- `prep.html` — 事前準備とAGENTS.md / CLAUDE.md用語プライマー
- `schedule.html` — 合宿2日間のスケジュール
- `repos.html` — 便利なGitHubリポジトリ一覧
- `IMAGES-TODO.md` — 追加スクリーンショット撮影メモ
- `assets/images/20260528-codex-setup/` — Codexセットアップ用スクリーンショット
- `assets/images/20260312gogcli/` — gogcli / Google Sheets連携用スクリーンショット
- `vercel.json` — Vercel静的配信用の最小設定

## ローカル確認

### 手順
HTMLをブラウザで確認します。

### コマンド（このブロックをそのまま貼る）

```bash
python3 -m http.server 8000
```

置き換え不要: なし

### 想定する出力（例）

```text
例:
Serving HTTP on :: port 8000
```

ブラウザで `http://localhost:8000` を開いてください。

## Vercel公開

1. <https://vercel.com/new> を開く
2. GitHubアカウントでログイン/登録
3. `sento-group-inc/Aigassyuku06` をImport
4. Framework PresetはOtherまたは未選択
5. Build Commandは空
6. Output Directoryも空
7. Deploy

以後は `main` ブランチにpushすると自動で再デプロイされます。

## GitHub反映

### 手順
変更をGitHubにpushします。

### 1. 変更確認

```bash
git status
```

### 2. ステージに追加

```bash
git add .
```

### 3. コミット

```bash
git commit -m "Update AI camp lecture site"
```

### 4. push

```bash
git push origin main
```

置き換え不要: なし

### 想定する出力（例）

```text
例:
[main xxxxxxx] Add Codex bunshin OS lecture site
 16 files changed
```
