# 最初のAnsible

ssh 接続先でディレクトリを作成する。

## ポイント

Ansible を動かすためには2つのファイルが必要。

+ Inventory
  - 対象ホスト, アクセスに必要な情報
  - inventory = 目録、棚卸し表
+ Playbook
  - 実行する内容
  - playbook = 脚本

## メモ

### `vagrant ssh-config`

```
vagrant ssh-config --host 192.168.33.10 >> ~/.ssh/config
```

vagrant の ssh のログイン設定ができる。

### `-k` をつけるとsshのパスワード聞かれる
