# Inventory と Playbook 2 つのファイルを理解する

## ポイント

+ Inventory は ini を拡張した形式
+ Playbook YAML 形式
+ Ansible は名前空間が1つ
+ tasks は上から順番で実行

## Playbook

### モジュール

+ debug
  - デバッグ用メッセージ出力
+ script
  - スクリプトを転送して実行
+ shell
  - コマンド実行
+ file
  - ファイル・ディレクトリ作成
+ template
  - Jinja2というテンプレート原語を使って、変数をうめ込み、ファイル生成
+ unarchive
  - 圧縮ファイルを展開
+ apt
  - apt でパッケージインストール
  - yum, pkg もある
+ user
  - ユーザーを追加・削除する

## 動かしてみる

1回目の実行

```
$ ansible-playbook -i hosts web.yml

PLAY [web] *********************************************************************

TASK [setup] *******************************************************************
ok: [web02.example.com]
ok: [web01.example.com]

TASK [実行用ユーザーの作成] **************************************************************
changed: [web02.example.com]
changed: [web01.example.com]

TASK [ログディレクトリの作成] *************************************************************
changed: [web02.example.com]
changed: [web01.example.com]

TASK [nginxのインストール] ************************************************************
changed: [web02.example.com]
changed: [web01.example.com]

PLAY RECAP *********************************************************************
web01.example.com          : ok=4    changed=3    unreachable=0    failed=0
web02.example.com          : ok=4    changed=3    unreachable=0    failed=0
```

2回目の実行

1回目の実行でchangedだった箇所がokになっている。
冪等性があることの確認。

```
$ ansible-playbook -i hosts web.yml

PLAY [web] *********************************************************************

TASK [setup] *******************************************************************
ok: [web02.example.com]
ok: [web01.example.com]

TASK [実行用ユーザーの作成] **************************************************************
ok: [web02.example.com]
ok: [web01.example.com]

TASK [ログディレクトリの作成] *************************************************************
ok: [web01.example.com]
ok: [web02.example.com]

TASK [nginxのインストール] ************************************************************
ok: [web01.example.com]
ok: [web02.example.com]

PLAY RECAP *********************************************************************
web01.example.com          : ok=4    changed=0    unreachable=0    failed=0
web02.example.com          : ok=4    changed=0    unreachable=0    failed=0
```
