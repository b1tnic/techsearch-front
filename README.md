# Qiita記事に自然言語ができるWebアプリ[techsearch](https://techserch.net/)のフロントエンドのソースレポジトリ
(**記事データの著作権の都合でQiita様より使用許諾が下りなかったため、現在は検索をした際にダミーデータが返ってくるようになっています。**)
<img width="710" height="375" alt="techsearch-demo" src="https://github.com/user-attachments/assets/dce16817-209b-4bbb-bde9-121acbd26b2a" />
<img width="700" height="470" alt="techsearch-demo2" src="https://github.com/user-attachments/assets/140f65e2-5c57-4102-9fd9-44cdc989bd16" />


## ディレクトリ構成
```
.
├── public
├── src/
│   ├── assets
│   ├── components/
│   │   ├── molecules/
│   │   │   ├── Article 検索ページの記事結果
│   │   │   ├── IntroduceBox サイト説明ページの説明
│   │   │   ├── Term 利用規約ページの各利用規約
│   │   │   ├── TerminalBody 検索ページのターミナルコンポーネントの体部分
│   │   │   └── TerminalHead 検索ページのターミナルコンポーネントの頭部分
│   │   ├── organisms/
│   │   │   ├── Header ヘッダー
│   │   │   ├── Introduce サイト説明ページメインコンテンツ
│   │   │   ├── Sidebar サイドバー
│   │   │   ├── Terminal 検索ページメインコンテンツ
│   │   │   └── Terms 利用規約ページメインコンテンツ
│   │   └── templates/
│   │       ├── AboutPageTemplate サイト説明ページのテンプレート
│   │       ├── HomePageTemplate 検索ページのテンプレート
│   │       └── TermsPageTemplate 利用規約ページのテンプレート
│   ├── pages/
│   │   ├── AboutPage サイト説明ページ
│   │   ├── HomePage 検索ページ
│   │   └── TermsPage 利用規約ページ
│   └── router
└── package.json
```

## 技術要件
言語：TypeScript

フレームワーク：Vue

ライブラリ：Vite、Iconify、vue-router、marked、axios

### 開発環境の立ち上げ

```sh
npm run dev
```

### 実行ファイルのビルド

```sh
npm run build
```
