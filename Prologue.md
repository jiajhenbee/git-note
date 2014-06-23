# 名詞解釋


### commit

* 一個 commit 是一個版本，每一個版本有一個獨特的編號，例如 `cf04c98...`

### branch

* branch 的概念可以比喻為「用來命名進度的標籤」
*  
這個標籤之前的所有 commits 串起來的連線稱為一個分支 (branch)

### repository

* 裝載 git 記錄的盒子
* 分為本機 (local) 和遠端 (remote) 兩種類型
* 不同盒子之間可以互相同步


### remote

* 遠端 repository



## 儲存變更

### Status

* 查看目前 branch 中所有檔案的狀態

### Staging

* Stage 是 `git commit` 之前的暫存狀態，只有追蹤的變更會被記錄到 commit 中


### Commit

* 提交每一次的新增/修改/刪減


### Diff

* 比較現在最新標籤和前一次 commit 的差異


### Log

```
git log
```
* [ ... ]

```
git hist
```
* [ ... ]


## 支線


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


