# OTOBOKE BEAVER テストサイト + Decap CMS

Decap CMSを使った簡易テストサイトです。

## 📁 ファイル構成

```
otoboke-test/
├── index.html          # トップページ
├── admin/
│   ├── index.html      # CMS管理画面
│   └── config.yml      # CMS設定ファイル ★重要
├── content/
│   ├── lives/          # ライブ情報（Markdown）
│   ├── news/           # ニュース（Markdown）
│   ├── pages/          # 固定ページ
│   └── settings/       # サイト設定
├── images/
│   └── uploads/        # アップロード画像
├── netlify.toml        # Netlify設定
└── package.json
```

## 🚀 セットアップ手順

### 1. GitHubリポジトリ作成

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/YOUR_USERNAME/otoboke-beaver.git
git push -u origin main
```

### 2. Netlifyでデプロイ

1. [Netlify](https://app.netlify.com/) にログイン
2. 「Add new site」→「Import an existing project」
3. GitHubを選択し、リポジトリを接続
4. デプロイ設定はそのままで「Deploy」

### 3. Netlify Identity設定（認証用）

1. Netlify管理画面 → Site settings → Identity
2. 「Enable Identity」をクリック
3. Registration → 「Invite only」に変更
4. Services → Git Gateway → 「Enable Git Gateway」

### 4. 管理者を招待

1. Identity → 「Invite users」
2. メールアドレスを入力して招待

## 📱 使い方

### 管理画面にアクセス

```
https://YOUR-SITE.netlify.app/admin/
```

### ライブ情報を追加

1. サイドバー「ライブ情報」を選択
2. 「新規作成」をクリック
3. 日付・会場などを入力
4. 「公開」ボタンで保存

### ニュースを投稿

1. サイドバー「ニュース」を選択
2. 「新規作成」をクリック
3. タイトル・本文を入力
4. 「公開」ボタンで保存

## ⚙️ config.yml の主な設定

```yaml
# コレクション（コンテンツの種類）
collections:
  - name: "lives"        # ライブ情報
  - name: "news"         # ニュース
  - name: "pages"        # 固定ページ
  - name: "settings"     # サイト設定
```

### フィールドの追加例

```yaml
fields:
  - label: "新しい項目"
    name: "new_field"
    widget: "string"      # テキスト入力
    required: false       # 任意項目
```

## 🔧 ローカルでテスト

```bash
# Decap CMS ローカルサーバー
npx decap-server

# 別ターミナルで
npx serve . -p 3000
```

ブラウザで `http://localhost:3000/admin/` を開く

## 📝 注意事項

- 本番環境では `config.yml` の `local_backend: true` を削除してください
- 画像はGitHubに保存されるため、大容量ファイルには注意
- ステージング環境として Netlify の Deploy Preview を活用できます

## 🔗 参考リンク

- [Decap CMS 公式ドキュメント](https://decapcms.org/docs/)
- [Netlify Identity 設定ガイド](https://docs.netlify.com/visitor-access/identity/)
