# バージョン管理

## Git
- [サルでもわかるGit入門 〜バージョン管理を使いこなそう〜 | どこでもプロジェクト管理バックログ](https://backlog.com/ja/git-tutorial/)
- [Gitのコミットメッセージを後から変更する方法をわかりやすく書いてみた](https://www.granfairs.com/blog/staff/git-commit-fix)

## 特定ファイルの変更履歴をみる

```
$ git log -p file/to/path
```

参考サイト
- http://shuzo-kino.hateblo.jp/entry/2014/05/22/222251

### まだgitに追跡されていないファイルを除外する.
参考サイト
- http://tbpgr.hatenablog.com/entry/20130610/1370873259

### 既にgitに追跡されているファイルを除外する/戻す.
外す: git update-index --skip-worktree path/to/file

戻す: git update-index --no-skip-worktree path/to/file

除外済みファイルを一覧表示する: git ls-files -v

参考サイト
- https://qiita.com/usamik26/items/56d0d3ba7a1300625f92
- https://qiita.com/nishina555/items/9c4ab955083c770c1f61
