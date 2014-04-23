git-note
========

## 名詞

### repository

* 裝載 git 記錄的盒子
* 分為本機 (local) 和遠端 (remote) 兩種類型
* 不同盒子之間可以互相同步

### commit

* 檔案儲存的狀態，包含儲存哪些檔案，儲存的時間，儲存變更的作者

### branch

* 一個有名稱的標籤，會隨著 commit 增加而移動
* 這個標籤之前的所有 commits 串起來的連線稱為一個分支 (branch)
* 每個專案預設的 branch 名稱叫做 `master`

### remote

* 遠端 repository


## 指令動作

### Status

```
git status
```

功能：查看目前 branch 中所有檔案的狀態

### Staging (TBD)

```
git add fileName
```

```
git reset fileName
```

### Commit

```
git commit -m "commit 說明"
```

功能：提交每一次的新增/修改/刪減

### Remote (TBD)

```
```

### Fetch & Pull

```
git fetch origin [-p]
```

功能：將遠端的 origin marster 主支下載最新的版本到本機

```
git pull origin master
```

功能：將 origin marster 下載最新的版本到本機並合併

> `git pull` 相當於 `git fetch` + `git merge`

```
git pull origin master

# 相當於底下兩個步驟：

git fetch origin
git merge origin/master
```

### Push (TBD)

```
```

