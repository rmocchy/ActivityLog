# 各ファイルの使い方
## setting.py
アプリケーションの定義とかが書いてある。

INSTALLED_APPSに作成するアプリケーションフォルダをインストールする必要がある
```
INSTALLED_APPS={
    ...,
    ...,
    'my-app', 
}
```
ちなみにデフォルトのDBはsqlite3
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}
```
## urls.py
ルーターの役割

urlpatternsにパスを追加することでfrontpageのviews.pyを呼び出す

デフォルトの`admin/`パスは管理画面に繋がってる←めっちゃ便利！
```
urlpatterns = [
    path('admin', admin.site.urls),
    path('',my-frontpage),
]
```

## views.py
DBの内容とhtmlを呼び出してサーバーに持っていく役割
```
def my-frontpage(request):
    return render(request, 'home/frontpage.html', dict-fromDB)
#renderのhtmlのpathはtemplateに対する相対パス
```

## models.py
DBの構造をここで指定する。gRPCのprotoとほとんど同じ。
```
python manage.py makemigrations
```
を実行すると`migrations/`直下にmigration履歴が残る。

続いて
```
python manage.py migrate
```
を実行すれば設定した情報をDBとして使えるようになる。

## admin.py
管理画面でできることを設定できる。例えば`admin.site.register(Obj)`で対象オブジェクトについて要素を追加することができる。


## ***.htmlファイルの記述の補足
`{{% Pythonのコード %}}`で記述する。

例)DB要素のリスト表示←endforの記述を忘れずに
```
{{% for item in items %}}
<div>
...
</div>
{{% endfor %}}
```