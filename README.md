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
hugo --cleanDestinationDir

# 2. Gitにコミット
git add .
git commit -m "新しい記事を追加"

# 3. GitHubにプッシュ
git push origin main
```

→ NetlifyがGitHubと連携していれば**自動でデプロイ**される

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
