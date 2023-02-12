# 仮想環境作成+Installation
0.必要があればインストールする
```
pip install virtualenv
```
1.仮想環境を作成
```
virtualenv my-env
```
2.仮想環境に入ってアクティベートしてpipインストール
```
cd my-env
```
```
source bin/activate
```
```
pip install django
```
以下でバージョン確認できる
```
django-admin --version
```
以下で使えるモジュールを確認できる
```
pip freez
```
# 雛形作成
1.適当なライブラリでdjangoの雛形を作成する
```
django-admin startproject my-project
```
2.作成したプロジェクトに入ってアプリケーションを作成する
```
python manage.py startapp my-app
```
# 動作確認
ローカルサーバーを起動してlocalhost上に表示できる
```
python manage.py runserver
```
# htmlファイルの作成
templateフォルダをmy-app直下に作成してそこに記述する

# 管理画面の設定
```
python manage.py createsuperuser
```
を実行して管理画面へアクセスするためのアカウントを作成する
```
ユーザー名:admin
メールアドレス:admin@example.com
password:password1234
```
同様にrunserverさせて`url+\admin`を入力することで管理画面にアクセスできる。
各ファイルの役割については[こちら](./file-cheatsheet.md)