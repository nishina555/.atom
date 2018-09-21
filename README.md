# .atom

## How to start
すでにatomをインストールしており、ホームに.atomというディレクトリができている前提です。
```
cd ~
mv .atom .atom_bk
git clone https://github.com/nishina555/.atom
cd ~/.atom_bk
mv blob-store compile-cache packages recovery storage ~/.atom
cd ~/.atom
apm install --packages-file packages.txt
```

## Create installed packages list
```
apm list --installed --bare > packages.txt
```

## Install packages
```
apm install --packages-file packages.txt
```

## Tips
### shortcut
- プロジェクト内のファイル検索: ctrl + shift + f
- ファイルの検索: ctrl + t
- ディレクトリ画面のトグル操作: ctrl + \
- ターミナルを新しいタブで起動(packages -> tearm3): ctrl + alt + T
- 矩形選択:
  - #ドラッグして行を選択 -> shift + alt + 矢印
  - #shiftとctrlを両方押して矢印
  - alt押す -> ドラッグ
- ターミナル関係(platformio-ide-terminalを利用)
    - 起動 ctrl + `
    - 新規作成 command + shift + t
    - 削除 command + shift + x
    - 移動 command + shift + j(or k)
- フォルダーを開く: command + shift + o
- 新規atomでフォルダーを開く: shift + o
- ファイルを開く: command + o
- ツリーviewのトグル: command + \
- ツリーでの操作
  - 新規ファイル作成: a
  - ファイル名編集: m
  - ファイル削除: deleteキー
  - 新規フォルダ: shift + a
  - コピー: d
- ハイライト対象のファイル変更(Edit -> Select Grammer)
  - ctrl + shift + L
### plugin
- git-plus: Cmd-Shift-H
- script: Cmd + i
- atom-runner(scriptよりいいかも): ctrl + r
- atom-beautify: ctrl + alt + b
### replace
- 全ての行頭に文字を追加する(正規表現にチェックをつける)
    - 置換前: ^
    - 置換後: XXXX
- 全ての行頭に文字を挿入する(正規表現にチェックをつける)
    - 置換前: ^(.)
    - 置換後: XXXX $1
- 全ての行末に文字を挿入する(正規表現にチェックをつける)
    - 置換前: $
    - 置換後: XXXX
- 行削除
    - 置換前: ^\n
    - 置換後: 空白

### autocomplete-rubyのrsenseのパスを設定する
rsenseをrbenvにてインストールし、rsenseのパスを設定する。
rbenvのrubyを使う理由は、デフォルトだとsudoじゃないとgemがインストールできないので。
```
$ gem install rsense
ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /Library/Ruby/Gems/2.0.0 directory.
-> rbenvのrubyを使うようにする

$ rbenv versions
-> デフォルトでは以下のようになっている
* system (set by /Users/toshiharu-nishina/.rbenv/version)
  2.2
  2.2.6
  2.3.3
  2.4
  2.4.1
$ rbenv global 2.3.3
$ ruby --version
->2.3.3 ならOK

### もしrubyのバージョンがアップデートされないならrehashする
$ rbenv rehash

$ rbenv versions
  system
  2.2
  2.2.6
  2.3
* 2.3.3 (set by /Users/toshiharu-nishina/.rbenv/version)
$ gem install rsense
-> インストールできるはず

$ gem environment
-> /Users/nishina/.rbenv/versions/2.3.0/bin/rsense
のようなものを設定する
```
