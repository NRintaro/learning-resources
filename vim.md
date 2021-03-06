# Vim

- [vim-jp » vim-users.jp](https://vim-jp.org/vim-users-jp/)
- [vim-jp » Vim script事始め](https://vim-jp.org/tips/start_vimscript.html)
- [スパルタンVim(著者:KoRoN/香り屋)](http://files.kaoriya.net/docs/SpartanVim/SpartanVim-1.0-online.pdf)
- [Vim script と vimrc の正しい書き方＠nagoya.vim #1](https://www.slideshare.net/cohama/vim-script-vimrc-nagoyavim-1)
- [vimrcをgithub管理して、簡単にvim環境構築](http://www.kurisankaku.xyz/entry/2016/04/19/201957)
- [Vimをもっと上手に! 新たな旋風、Neovimで自堕落なVim力に喝を入れる。 | 東京上野のWeb制作会社LIG](https://liginc.co.jp/409849)
- [【図解Vim】mapとnoremap - ここぽんのーと](https://cocopon.me/blog/2013/10/vim-map-noremap/)
- [Vim のすゝめ - Vim を最小限の設定で使う | 株式会社創夢 — SOUM/misc](https://www.soum.co.jp/misc/vim-no-susume/1/)
- [モテる男のVim script短期集中講座](https://mattn.kaoriya.net/software/vim/20111202085236.htm)
- [Effective Modern Vim scripting](https://docs.google.com/presentation/d/e/2PACX-1vQKaWJY8w6QJpebvuzg334RfLDbQHv4-J_06yFxdTzLrrjhE_y5iuzA-JxCCuFdUAZQB2QQsidF_mys/pub?start=false&loop=false&delayms=3000&slide=id.p)
- [上達したいVim初心者のための設定・プラグインの見つけ方、学び方〈エディタ実践入門〉](https://employment.en-japan.com/engineerhub/entry/2019/01/28/103000)
- [閉じ括弧の自動入力(thincaの場合)](https://thinca.hatenablog.com/entry/20081005/1223206388)
- [15年目のVim | POSTD](https://postd.cc/vim3/)
- [Vim-Galore : Vimについて知っておくべき全てのこと (5/5)](https://postd.cc/vim-galore-5/)
- [最後に改行がないファイルが作れない #152](https://github.com/vim-jp/issues/issues/152)
- [なぜ gcc はファイルの最後に改行がないと警告を出すのか？](http://hiroakiuno.hatenablog.com/entry/20070409/p1)


## めも

忘れそうな機能をめもしとく。

### デフォルト設定でvimを起動

```
vim -u NONE –N
```

これを実行すると、vimrcなし（つまりデフォルトの設定）で、かつ非互換モード（viのデフォルトではなく、Vimのデフォルトを使うようになります）でVimが起動されます（起動時にロードするものの組み合わせに関しては、:h --noplugin を参照してください）。

### very magic

```
aaa
bbaaaba
caaaa
aaaaaaa
```

から単語として`aaa`のみを検索するには、コマンドモードで

```
:/\v<aaa>
```

とする。

### :normalと:execute

この2つのコマンドは、一般的にVimスクリプトで使用されます。

`:normal`コマンドを使うと、コマンドラインからノーマルモードへのマッピングを行うことができます。例えば、`:normal! 4j`はカーソルを4行下に移動させます（”!”を付けると”j”へのカスタムマッピングは行われません）。

`:normal`は範囲も指定できるので、`:%norm! Iabc`とすると、全ての行の先頭に “abc”が追加されることを忘れないでください。

`:execute`コマンドを使うと、式と一緒にコマンドを実行できます。C言語のソースファイルを編集していて、そのヘッダファイルに切り替えたい場合は、次のように記述します。

```
:execute 'edit' fnamemodify(expand('%'), ':r') . '.h'
```
2つのコマンドは、よく一緒に使われます。カーソルを”n”行下に移動させたい場合は、次のように記述します。

```
:let n = 4
:execute 'normal!' n . 'j'
```
