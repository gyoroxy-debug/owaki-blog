# 大脇貴仁のブログ - 操作マニュアル

## 📁 ディレクトリ構造

```
owaki-blog/
├── content/
│   └── posts/          ← 【重要】ここに記事（.md）を保存
├── static/
│   └── images/         ← 【重要】ここに画像（.jpg, .png）を保存
├── themes/
│   └── minimal-owaki/  ← テーマファイル（触らない）
├── hugo.toml           ← サイト設定
└── netlify.toml        ← Netlify設定
```

---

## ✍️ 記事の投稿方法

### 1. AI（Gemini）が生成した `.md` ファイルを準備

例: `my-article.md`

```markdown
---
title: "記事のタイトル"
date: 2025-10-26
draft: false
---

記事本文...

※ 免責事項とLPリンクも含まれている
```

### 2. ファイルを配置

```bash
# 記事ファイルを保存
content/posts/my-article.md

# 使用する画像を保存
static/images/photo1.jpg
static/images/photo2.jpg
```

### 3. 記事内で画像を参照

```markdown
![説明文](/images/photo1.jpg)
```

---

## 🎥 YouTube埋め込み

記事に直接iframeを書く:

```markdown
<iframe width="100%" height="auto" style="aspect-ratio: 16/9;" 
src="https://www.youtube.com/embed/動画ID" 
frameborder="0" allowfullscreen></iframe>
```

---

## 🐦 X（Twitter）埋め込み

記事に埋め込みコードを貼り付け:

```markdown
<blockquote class="twitter-tweet">
  <a href="https://twitter.com/user/status/..."></a>
</blockquote>
<script async src="https://platform.twitter.com/widgets.js"></script>
```

---

## 🚀 公開方法（Ver. 1.0 手動公開）

### ローカルでプレビュー

```bash
cd /home/claude/owaki-blog
hugo server
```

ブラウザで `http://localhost:1313` を開く

### 本番公開

```bash
# 1. 静的ファイルをビルド
hugo --gc --minify

# 2. Gitにコミット
git add .
git commit -m "新しい記事を追加"

# 3. GitHubにプッシュ
git push origin main
```

→ **Cloudflare Pages**がGitHubと連携していれば**自動でデプロイ**される

---

## ☁️ Cloudflare Pages 初回セットアップ手順

### 1. GitHubにリポジトリを作成

1. GitHub（https://github.com）にログイン
2. 「New repository」をクリック
3. リポジトリ名: `owaki-blog`
4. Public/Private どちらでもOK
5. 「Create repository」

### 2. ローカルからGitHubにプッシュ

```bash
cd /home/claude/owaki-blog

# リモートリポジトリを追加
git remote add origin https://github.com/あなたのユーザー名/owaki-blog.git

# ブランチ名をmainに変更
git branch -M main

# プッシュ
git push -u origin main
```

### 3. Cloudflare Pagesでプロジェクト作成

1. Cloudflare Dashboard（https://dash.cloudflare.com/）にログイン
2. 左メニューから「Workers & Pages」を選択
3. 「Create application」→「Pages」→「Connect to Git」
4. GitHubアカウントを連携
5. リポジトリ「owaki-blog」を選択

### 4. ビルド設定

以下の設定を入力:

- **フレームワークプリセット**: Hugo
- **ビルドコマンド**: `hugo --gc --minify`
- **ビルド出力ディレクトリ**: `public`
- **環境変数**:
  - `HUGO_VERSION` = `0.123.7`
  - `HUGO_ENV` = `production`

### 5. カスタムドメイン設定

1. プロジェクトの「Custom domains」タブ
2. 「Set up a custom domain」をクリック
3. ドメイン入力: `blog.bokunosaiseikeikaku.icu`
4. DNS設定を指示に従って更新

---

## 🔄 記事更新の流れ（セットアップ後）

1. 記事ファイル（.md）を `content/posts/` に保存
2. 画像ファイルを `static/images/` に保存
3. ローカルでプレビュー: `hugo server`
4. Git操作:
   ```bash
   git add .
   git commit -m "記事追加: タイトル"
   git push origin main
   ```
5. Cloudflare Pagesが**自動ビルド・デプロイ**（約1-2分）
6. `https://blog.bokunosaiseikeikaku.icu` で公開完了

---

## 🔧 トラブルシューティング

### 画像が表示されない
- ファイル名を確認（大文字小文字も区別される）
- パスが `/images/ファイル名.jpg` になっているか確認

### 記事が表示されない
- `draft: false` になっているか確認
- `date` が未来の日付になっていないか確認

### YouTubeが表示されない
- 埋め込みコードのURLが正しいか確認
- `https://www.youtube.com/embed/動画ID` の形式を使用

---

## 📞 サポート

質問がある場合は、技術チーム（Claude）に連絡してください。
