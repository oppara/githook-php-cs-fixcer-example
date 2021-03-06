#  githook-php-cs-fixcer-example

Git のコミットフックで PHP-CS-Fixer を実行する。

`core.hooksPath`オプションでプロジェクトの Git フックのディレクトリを指定し、
Git の機能だけで フックのコードをバージョン管理し、プロジェクトのセットアップ時に Git フックの設定をできるようにする。

## プロジェクトでの設定方法

`composer.json`の`scripts.pre-command-run`で、core.hooksPath を設定する。

```
"scripts": {
  "pre-command-run": [
    "git config --local core.hooksPath .githooks"
  ]
}
```

何かしらの composer のコマンドを実行すると`pre-command-run`スクリプトが実行されて、`.githooks`ディレクトリが Git フックとして扱われる。


## Docker 使う場合

```
docker run --rm -it -w /app -v ${PWD}:/app oskarstark/php-cs-fixer-ga:latest /path/to/target
```

## 参考

- [Git - githooks Documentation](https://git-scm.com/docs/githooks)
- [追加の依存パッケージなしでプロジェクトごとのGitコミットフックを設定する方法 | Web Scratch](https://efcl.info/2021/08/21/git-precommit-hook/)
- [PHP-CS-FixerとGit フックで治安保持活動 - Qiita](https://qiita.com/Hiro2525/items/6b8e37766820f9aed1f0)
