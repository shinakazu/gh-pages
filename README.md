# gh-pages

GitHub Pages でホストする静的 Web アプリケーション集です。

## デプロイ

`main` ブランチへの push 時に GitHub Actions でビルド・デプロイされます。

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
