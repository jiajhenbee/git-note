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


## 開始新的專案

```
git clone https://github.com/jiajhenbee/git-note.git
```

* 把 `https://github.com/jiajhenbee/git-note.git` 上 (已經存在) 的專案下載下來到 `git-note` 資料夾
* 預設的 remote 名稱是 `origin`

```
git init
```

* 在目前資料夾開始一個全新的專案
* remote 初始狀態是空的，還未設定


## 儲存變更

### Status

```
git status
```

* 查看目前 branch 中所有檔案的狀態

### Staging

> Stage 是 `git commit` 之前的暫存狀態，只有追蹤的變更會被記錄到 commit 中

```
git add 檔案名稱
```
* [ 新增資料到由 git 管理的資料夾裡 ]

```
git reset 檔案名稱
```
* [ 還原資料到前一次版本，而更改過的版本將不會存檔 ]

> 可以用 `.` 代表目前資料夾內所有的內容，例如 `git add .` 是把所有檔案加入追蹤


### Commit

```
git commit
git commit -m "commit 說明"
```

* 提交每一次的新增/修改/刪減
* 加入 `-m` 參數直接在後面加上說明文字，不用開啟編輯器

```
git reset --hard head^
```

* [ ... ]


## 分支的相關操作

### branch (TBD)

### checkout (TBD)


## Merge & Rebase

### Merge (TBD)

### Rebase (TBD)


## 同步

### Remote

```
git remote -v
```

* 看目前跟哪些遠端 repository 同步

### Fetch & Pull

git 的記錄分為本機 (local) 和遠端（remote）兩種，可以想像成兩張描圖紙上面的線圖，重疊在一起。

* 當我在 local 的描圖紙上增加新的線段，然後要把這些新的線段描繪到 remote 的描圖紙上分享給別人，這個動作叫 `push`
* 當別人更新了 remote 的描圖紙，我想要拿回來描繪在 local 的描圖紙上，這個動作叫 `pull`

> 因為兩張描圖紙要能重疊在一起才能描繪，所以重複的線段必須一模一樣才能順利的描繪需要同步的部分

```
git fetch origin [-p]
```

* 將遠端 `origin` 最新的狀態下載到本機
* 下載下來之後本機上會出現例如 `origin/branch-name` 的 branch，表示這個是 `origin` 上的 branch，已經下載到本機上
* 這時候如果執行 `git checkout branch-name` 就會在這個 branch 上建立一個同名的 local branch

```
git pull origin master
```

* 將遠端 `origin` 下載最新的版本到本機，並把遠端的 `master` branch 合併到目前 branch 上
* 要注意執行的時候位於哪個 branch

> `git pull` 相當於 `git fetch` + `git merge`

```
git pull origin master

# 相當於底下兩個步驟：

git fetch origin
git merge origin/master
```

### Push

```
git push origin master
```

* [ ... ]

