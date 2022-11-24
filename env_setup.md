# ワークスペース内での環境変数の反映

ターミナルごとに `source devel/setup.bash` を行わなくていいようにする

## ■ direnv 導入

### 1. go のインストール


```bash
$ sudo apt update
$ sudo apt install golang-go
$ go version
# バージョン 1.8 より前になっていた場合、以下を実行（1.8 以降が必要）
$ sudo add-apt-repository ppa:longsleep/golang-backports
$ sudo apt-get update
$ sudo apt-get install golang-go
```

### 2. direnv のインストール

```bash
$ git clone https://github.com/direnv/direnv
$ cd direnv
$ sudo make install
```

~/.bashrcに下記を追記後、`source ~/.bashrc`

```bash
export EDITOR=vi
eval "$(direnv hook bash)"
```

## ■ direnv 初回使用時

クローンしたこのプロジェクトのディレクトリで以下を実行

```bash
$ direnv allow
```

## ■ 参考

- [ROSで移動したワークスペースごとに自動でsetup.bashを読み込むための環境構築](https://qiita.com/kazuki21057/items/fe40192beced06b2e723)
