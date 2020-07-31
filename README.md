# api-document-use-aglio
API Blueprint, aglioを使ったAPI Document

### 開発環境セットアップ

```bash
# dockerコンテナ構築・起動
docker-compose up --build

# Dockerfileを修正した場合は下記コマンドを実行
docker-compose build --no-cahe
docker-compose up
```

http://localhost:4000/
でAPIドキュメントサイトにアクセスできることを確認します。

# development flow

1. mdディレクトリ配下のmdファイルを修正すると自動的にweb側へ反映されるのでwebを確認しながらドキュメントを修正します。
2. index.htmlファイルは更新されないのでmdファイルを全て修正したら下記のコマンドを実行してhtmlファイルを生成します。
   ```bash
     # コンテナ内でhtmlを生成するコマンドを実行
     docker-compose exec aglio bash
     aglio --theme-variables default --theme-template triple -i index.md -o ../docs/index.html
    ```

# deploy flow (GitHub Pagesで公開)
```
# 以下のコマンドで gh-pagesブランチがなければ作成され、index.htmlのみpush されます。
1 master ブランチでcommit , push しておきます
2 ./deploy.sh を実行
3 https://yourusername.github.io/api-document-use-aglio/ にアクセスして公開されていることを確認
```

