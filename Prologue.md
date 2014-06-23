# 名詞解釋

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

### Status

* 查看目前 branch 中所有檔案的狀態

### Staging

* Stage 是 `git commit` 之前的暫存狀態，只有追蹤的變更會被記錄到 commit 中


### Commit

* 提交每一次的新增/修改/刪減
* 一個 commit 是一個版本，每一個版本有一個獨特的編號，例如 `cf04c98...`
* commit 所記錄的是「和前一個版本之間的差異」，而不是新增一個版本都重新儲存一份完整的專案內容，所以 git 的記錄方式非常節省空間
* commit 內除了記錄了哪些檔案有變動，也包含了變更的時間，和變更的作者

> 例如一個專案的版本變化如下，每個 ◎ 就是一個 commit

```
  ◎  -->  ◎  -->  ◎  -->  ◎
  v1      v2       v3       v4
```

> Commit v1 是專案開始的狀態，commit v2 記錄的是「相較於 v1 改了哪些東西」，commit v3 記錄的是「相較於 v2 改了哪些東西」，所以將 v1 + v2 + v3 + v4 的 commit 內容疊加起來就是目前專案的狀態。正因為這些版本的歷史記錄是連續的，所以在這個連續線段上的任何一個記錄點上都有辦法還原當時專案的狀態。


### Diff

* 比較現在最新標籤和前一次 commit 的差異


### Log

* 檢視 `commit` 的歷史記錄，提交的作者、時間及 commit 訊息，由新到舊排列顯示
 

### histtory(hist)

* 檢視 `commit` 的在分之上的歷史記錄，有簡易的 UI 輸出分支的動線


### branch

* 列出目前本地的分支

### checkout

* 移動標簽位置或是分支

### Merge

* 把 `某個分支` 的變更合併到目前的 branch 上，新增一個併在一起的 commit

### Pull Request

* **Pull Request** 是 GitHub 提供的功能，通知一起協作的成員有某個 branch 的變更要 merge 進另外一個 branch

### Remote

* 遠端 repository


### Fetch

* 新增並更新所有遠端分支

### Pull

* 新增並更新所有遠端分支，並同步在本機上


### Push

* 將本機端所變動的 commit 推到遠端並同步


