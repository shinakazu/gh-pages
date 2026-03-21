# gh-pages

GitHub Pages でホストする静的 Web アプリケーション集です。

## インデックスページ

ルートの `index.html` は各アプリへのリンクを一覧表示するランディングページです。アプリを追加した場合は `<li>` を追加してください。

## デプロイ

GitHub Actions（`.github/workflows/deploy.yml`）で GitHub Pages にデプロイされます。

### 初回デプロイ（手動）

初回はサイトが存在しないため、`workflow_dispatch`（手動実行）でデプロイする必要があります。push だけではデプロイされません。

### push 時の自動デプロイ

`main` ブランチへの push 時、GitHub Pages サイトが既にデプロイ済み（`built` 状態）であれば自動でデプロイが実行されます。サイトが未構築の場合は push してもデプロイされないため、意図せずサイトが公開されることはありません。

### 手動デプロイ

`workflow_dispatch` による手動デプロイはサイトの状態に関係なく常に実行できます。

**GUI から:**

1. リポジトリの **Actions** タブを開く
2. 左側から **Deploy to GitHub Pages** ワークフローを選択
3. **Run workflow** ボタンをクリックし、ブランチを選択して実行

**CLI から:**

```bash
gh workflow run deploy.yml --ref main
```

### デプロイの無効化・再有効化

```bash
# GitHub Pages を無効化（非公開にする）
gh api -X DELETE repos/<owner>/<repo>/pages

# GitHub Pages を再有効化（Actions 経由）
gh api -X POST repos/<owner>/<repo>/pages -f build_type=workflow
```

## アプリケーション

| アプリ | パス | 説明 |
|---|---|---|
| [TODO App](todo/) | `/todo/` | シンプルな TODO アプリ（HTML / CSS / JS） |

## ローカルでの確認

任意の静的ファイルサーバーで確認できます。

```bash
python3 -m http.server 8000
```

ブラウザで `http://localhost:8000/todo/` を開いてください。