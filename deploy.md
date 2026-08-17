# デプロイ手順（齊藤の同意後に実行）

## GitHub Pages（推奨）

```bash
cd /c/Users/keita/dev/ar-photo-demo
git init -b main
git add index.html video.mp4 targets.mind marker.jpg deploy.md
git commit -m "AR写真デモ 初版"
gh repo create ar-photo-demo --public --source=. --push
gh api -X POST repos/{owner}/ar-photo-demo/pages -f "source[branch]=main" -f "source[path]=/"
# 数分後に https://<ユーザー名>.github.io/ar-photo-demo/ で公開
```

- WebAR はカメラ利用のため **HTTPS 必須** → GitHub Pages はそのまま満たす
- 非公開にしたい場合: `--public` を `--private` に…はPages無料枠では不可（公開リポジトリが必要）。非公開配信は Cloudflare Pages 側で

## Cloudflare Pages（代替・1行）

`npx wrangler pages deploy /c/Users/keita/dev/ar-photo-demo --project-name ar-photo-demo`（wranglerログイン要・URLは *.pages.dev）
