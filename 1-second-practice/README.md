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
