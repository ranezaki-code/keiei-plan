# keiei-plan プロジェクト固有ルール

## 編集後は自動で commit & push する

このリポジトリ（経営計画管理システム）は GitHub Pages で公開されているため、
`index.html` を編集したら **毎回必ず** 以下を自動で実行する。
ユーザーに確認を取らない（`次からも、そうしてください！` で合意済み）。

```bash
git add index.html
git commit -m "vX.Y: 変更内容を簡潔に記述

- 詳細1
- 詳細2

Co-Authored-By: Claude Opus 4.7 <noreply@anthropic.com>"
git push
```

### 手順

1. `index.html` 編集
2. `APP_VERSION` 定数（先頭付近）をバンプ（例: v18.0 → v18.1）
3. `git add index.html && git commit -m "..."` → `git push`
4. ユーザーには「push 完了。1〜2分後にハードリロード（⌘+Shift+R）してください」と案内

### バージョン番号の付け方

- 小さな修正・追加: マイナー（v18.0 → v18.1）
- 大きな機能追加・UI 刷新: メジャー（v18.x → v19.0）

### 注意

- `APP_VERSION` を変えればヘッダー表示は自動で同期される（v18.0 で対応済み）
- ハードコードされた `vX.Y` 文字列が残っていないか念のため `grep` で確認するとよい
- push を忘れると公開URLに反映されないので、ローカル確認だけで終わらせない
