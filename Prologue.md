<<<<<<< HEAD

# 名詞解釋


### commit

* 一個 commit 是一個版本，每一個版本有一個獨特的編號，例如 `cf04c98...`
* commit 所記錄的是「和前一個版本之間的差異」，而不是新增一個版本都重新儲存一份完整的專案內容，所以 git 的記錄方式非常節省空間
* commit 內除了記錄了哪些檔案有變動，也包含了變更的時間，和變更的作者

> 例如一個專案的版本變化如下，每個 ◎ 就是一個 commit


### branch

* branch 的概念可以比喻為「用來命名進度的標籤」
* 這個標籤標記在 commit 上，而且會隨著新增 commit（版本）而移動到最新的 commit 上
* 這個標籤之前的所有 commits 串起來的連線稱為一個分支 (branch)
* 每個專案預設的 branch 名稱叫做 `master`
* 新增一個 branch 的意思是在目前的 commit（版本）上標記一個新的標籤，表示要從目前這個版本開始一連串新的進度

> 因為 branch 的標記是在一連串 commits 中最新的那一個上，所以代表了這一連串 (版本) 修改的最新進度。


### repository

* 裝載 git 記錄的盒子
* 分為本機 (local) 和遠端 (remote) 兩種類型
* 不同盒子之間可以互相同步

### remote

* 遠端 repository

## 儲存變更

### Status

```
git status
```

* 查看目前 branch 中所有檔案的狀態

### Staging

> Stage 是 `git commit` 之前的暫存狀態，只有追蹤的變更會被記錄到 commit 中


### Commit

```
git commit [-m "commit 說明"]
```
* 提交每一次的新增/修改/刪減
* 加入 `-m` 參數直接在後面加上說明文字，不用開啟編輯器
* 加上 `-a` 相當於在 commit 之前執行 `git add .`


### Diff

```
git diff commit A commit B
```
```
git diff HEAD
```
* [ 比較現在最新標籤和前一次 commit 的差異]


### Log

```
git log
```
* [ ... ]

```
git hist
```
* [ ... ]


## 分支的相關操作

### branch

列出目前本地的分支

### checkout

`checkout` 的功能是把專案的內容恢復成某個版本的狀態

### Merge

```
git merge 某個分支
```

* 把 `某個分支` 的變更合併到目前的 branch 上，新增一個併在一起的 commit

### Fast-Forward

如果 `topic` 是基於 `master` 上的版本繼續新增的變更，而且 `master` 上在 `topic` 分支分出去後沒有額外的變化 (沒有上一個示意圖的 commits F、G)，這時候在 `master`上執行 `git merge topic`：

### --no-ff

```
git merge --no-ff 某個分支
```

如果在上述的情況下希望多增加一個 commit 記錄進度完成，可以加上 `--no-ff` 產生比較好看的版本線圖 (在 `master` 上執行 `git merge --no-ff topic`)：

### Pull Request

* **Pull Request** 是 GitHub 提供的功能，通知一起協作的成員有某個 branch 的變更要 merge 進另外一個 branch
* 在 GitHub 頁面上會顯示這個要 merge 進來的變更有哪些 commits，所有加總起來的變更內容 (diff)
* 如果沒有這些變更和要合併的一個分支內容沒有衝突 (conflicts)，GitHub 頁面也提供了 merge 按鈕；如果有衝突就要手動解決後把新增的 commit push 上去

> Pull Request 預設的 merge 方式是 `--no-ff`，所以在版本線圖上可以很清楚的區分進度的變化


### Remote

```
git remote -v
```
* 看目前跟哪些遠端 repository 同步

```
git remote add
```

### Fetch & Pull

git 的記錄分為本機 (local) 和遠端（remote）兩種，可以想像成兩張描圖紙上面的線圖，重疊在一起。

* 當我在 local 的描圖紙上增加新的線段，然後要把這些新的線段描繪到 remote 的描圖紙上分享給別人，這個動作叫 `push`
* 當別人更新了 remote 的描圖紙，我想要拿回來描繪在 local 的描圖紙上，這個動作叫 `pull`

> 因為兩張描圖紙要能重疊在一起才能描繪，所以重複的線段必須一模一樣才能順利的描繪需要同步的部分


### Push

```
git push origin master
```
* 將本機端所變動的 commit 推到遠端並同步

> push 時不用切到特定位置即可推 origin，但 pull 則需注意自己的位置

```
git push -u origin master
```
* `-u` [...]
=======
在開始之前
========

## 名詞解釋

## 開始新的專案
>>>>>>> origin/separate-topics
