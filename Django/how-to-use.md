# 仮想環境作成+Installation
0.必要があればインストールする
```
pip install virtualenv
```
1.仮想環境を作成
```
virtualenv my-env
```
2.仮想環境に入ってpipインストール
```
cd my-env
```
```
pip install django
```
以下でバージョン確認できる
```
django-admin --version
```
# 雛形作成
3.djangoの雛形を作成する
```
django-admin startproject my-project
```