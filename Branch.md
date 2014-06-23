分支的相關操作
============

### branch

```
git branch
```

* 列出目前本地的分支

```
git branch 分支名稱(標籤名稱)
```
* 開新分支

```
git branch -d 分支名稱(標籤名稱)
```
* 刪除分支

> commits 連線的尾端如果沒有 branch (標籤)標記，就不會出現在版本線圖上，所以刪掉 branch 就等於遺失了這些 commits (版本)

* 如果刪除 branch 會造成目前線圖上的 commits 遺失 (通常是 branch 還沒有 merge 的情況) `-d` 的刪除方式會顯示警告
* 要強制刪除還未 merge 的 branch 需要改用 `git branch -D 分支名稱`

### checkout

`checkout` 的功能是把專案的內容恢復成某個版本的狀態

```
git checkout 分支名稱(標籤名稱)
```
* 切換到任意到分支（標籤）的位置，檔案的內容會還原成專案進行到該 commit 版本所記錄的樣子

```
git checkout '任意 commit 編號'
```
* 切換到任意 commit 的狀態
* 在這個情況下 git 會顯示類似的訊息：

```
You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b new_branch_name

HEAD is now at 8c8952e...
```

這表示現在的位置並不在任何 branch (標籤)上，即使是 checkout 標籤所標示的同一個 commit 編號也會發生。不在 branch 上的狀態並不影響「查看 (checkout) 某一個版本」這個動作，唯一的影響是：如果不是在 branch 上新增的 commits，一旦 checkout 其他版本，就會找不到剛才新增的 commits (因為不會顯示在線圖上)

```
git checkout -b 新的分支名稱

# 相當於底下兩個步驟

git branch 新的分支名稱
git checkout 新的分支名稱
```

習慣上 `git checkout '任意 commit 編號'` (或 `git checkout head~3`) 會用來查看某個版本的樣子，如果要新增變更就會搭配 `git checkout -b 新的分支名稱` 一起使用。

```
git reset --hard '任意 commit 編號'
```

* `git checkout` 只是切換過去某個版本查看內容
* `git reset --hard` 則可以把 branch 標籤移動到任何 commit 上