# 各ファイルの使い方
## setting.py
アプリケーションの定義とかが書いてある
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
urlpatternsにパスを追加することでfront pageのviews.pyを呼び出す
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