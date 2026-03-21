# gh-pages

GitHub Pages でホストする静的 Web アプリケーション集です。

## インデックスページ

ルートの `index.html` は各アプリへのリンクを一覧表示するランディングページです。アプリを追加した場合は `<li>` を追加してください。

## デプロイ

GitHub Actions（`.github/workflows/deploy.yml`）で GitHub Pages にデプロイされます。

### 自動デプロイ

`main` ブランチへの push 時に自動でデプロイが実行されます。

### 手動デプロイ

GitHub Actions の `workflow_dispatch` に対応しているため、手動でもデプロイできます。

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
