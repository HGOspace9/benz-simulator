# あそこにベンツがシュミレーター

タバコに費やした金額を「ベンツ換算」と「等価アイテムリスト」で見せる、単体HTMLのジョーク寄り啓発サイトです。

- `index.html` … サイト本体(HTML/CSS/JS 単体ファイル、外部依存なし)
- `robots.txt` … クロール許可設定
- `sitemap.xml` … 簡易サイトマップ
- `ads.txt.template` … Google AdSense審査通過後に使うテンプレート

## 公開までの流れ

このリポジトリはローカルで完結しており、まだどこにもデプロイされていません。
以下の順に進めると、実際にGoogle検索から見つかる・広告が出せる状態になります。

### 1. GitHub Pagesで公開する(無料・おすすめ)

```bash
# このフォルダで、GitHub上に新しいリポジトリを作成してpushする
gh repo create <お好きなリポジトリ名> --public --source=. --remote=origin --push

# GitHubのリポジトリ画面 → Settings → Pages で
# Branch: main / フォルダ: / (root) を選択して保存
# 数分後に https://<ユーザー名>.github.io/<リポジトリ名>/ で公開されます
```

独自ドメインを使いたい場合は、リポジトリ直下に `CNAME` ファイル(中身は `example.com` のようにドメイン名のみ)
を追加し、ドメイン管理画面でGitHub Pages宛のDNS設定(Aレコード or CNAMEレコード)を行ってください。
詳細: https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site

### 2. 公開後、URLを各ファイルに反映する

`index.html` 内の `og:url` と `canonical`、`sitemap.xml` の `<loc>`、`robots.txt` の `Sitemap:` にある
`https://example.com/` を、実際に公開されたURLへ置き換えてください。

### 3. Google Search Consoleに登録する(無料)

1. https://search.google.com/search-console にアクセスし、公開したURLをプロパティとして追加
2. 所有権確認(HTMLタグ方式が簡単です。発行されたmetaタグを `index.html` の `<head>` に追加)
3. 左メニューの「サイトマップ」から `sitemap.xml` のURLを送信
4. これで数日〜1週間程度でGoogle検索結果に載り始めます(何もしなくても数週間〜数ヶ月で自動的に載ることもあります)

### 4. Google AdSenseに申請する(審査あり・ご自身のアカウントが必要)

1. https://www.google.com/adsense/ から申し込み(サイトURLと運営者情報が必要です)
2. 審査には「独自ドメインでの公開」「ある程度のコンテンツ量」「規約違反がないこと」などが求められ、
   数日〜数週間かかることがあります。すぐに審査に出さず、しばらく運用してから申請すると通りやすいと言われています
3. 審査通過後、管理画面で発行される `data-ad-client`(publisher ID)と広告ユニットのコードを、
   `index.html` 内の3箇所(`<!-- Google AdSense 広告コード -->` とコメントされている部分)に貼り付けてください
   コメントアウトを外すのを忘れないようにご注意ください
4. `ads.txt.template` の `pub-0000000000000000` を実際のpublisher IDに置き換え、`ads.txt` にリネームして
   サイトのルートに配置してください

### 5. 注意事項

- AdSenseの審査・アカウント登録は本人のみが行える手続きです。第三者による代理申請は規約違反となるため、
  必ずご主人様ご自身のGoogleアカウントで行ってください
- `index.html` 内の金額(タバコ1箱の目安価格・ベンツの目安価格・等価アイテムの目安価格)は、
  いずれも参考値であり、実勢価格を保証するものではありません。時期によって見直しをおすすめします
