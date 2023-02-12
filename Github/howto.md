# ブランチを用いた開発手順
## 前提
- ローカルにgitが入っている
- プログラム本体を`git clone`等でローカルに持ってきている
- 現在のブランチで未push状態の変更がない
- 該当ディレクトリ内で`origin`がリモートの対象リポジトリの内容になっている。以下で確認可能
```
git remote -v
```

## リモートでブランチを切ってそれをローカルに持って行く
1. 対象リポジトリhome画面でcodeタグを選択し，mainと書かれたドロップダウンを開いて自分の作りたいbranch名を設定する。一般に新機能追加なら`feature`，修正なら`fix`を名前に含めるのが一般的らしい。参照は[こちら](https://docs.github.com/ja/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-and-deleting-branches-within-your-repository)

以降ローカルで作業

2. ローカルにgithub(リモートリポジトリ)の内容を反映する。`git fetch`でリモートから引っ張ってくる操作。`-prune`オプションでリモートでの変更内容全ての意。
```
git fetch --prune
```

3. ローカルにgithub(リモートリポジトリ)の内容を持ってきて同時に作成したローカルブランチに移動する。ここで現ブランチで未pushの変更があるとエラーを吐く場合ｇある。
```
git checkout -b <作りたいローカルブランチ名> origin/<さっき作ったリモートブランチ名>
```

## 変更をリモートにpush
1. これだけ。引っ張ってくる時点でローカルとリモートのブランチが紐付くのでこれで良い。
```
git add .
```
```
git commit -m "message"
```
```
git push orogin <Pushするブランチ名>
```