git-note
========

## 名詞

### commit

* 一個 commit 是一個版本，每一個版本有一個獨特的編號，例如 `cf04c98...`
* commit 所記錄的是「和前一個版本之間的差異」，而不是新增一個版本都重新儲存一份完整的專案內容，所以 git 的記錄方式非常節省空間
* commit 內除了記錄了哪些檔案有變動，也包含了變更的時間，和變更的作者

> 例如一個專案的版本變化如下，每個 ◎ 就是一個 commit

```
  ◎  -->  ◎  -->  ◎  -->  ◎
  v1      v2       v3       v4
```

> Commit v1 是專案開始的狀態，commit v2 記錄的是「相較於 v1 改了哪些東西」，commit v3 記錄的是「相較於 v2 改了哪些東西」，所以將 v1 + v2 + v3 + v4 的 commit 內容疊加起來就是目前專案的狀態。正因為這些版本的歷史記錄是連續的，所以在這個連續線段上的任何一個記錄點上都有辦法還原當時專案的狀態。


### branch

* 一個有名稱的標籤，會隨著 commit 增加而移動
* 這個標籤之前的所有 commits 串起來的連線稱為一個分支 (branch)
* 每個專案預設的 branch 名稱叫做 `master`

### repository

* 裝載 git 記錄的盒子
* 分為本機 (local) 和遠端 (remote) 兩種類型
* 不同盒子之間可以互相同步

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
* `@`等於 HEAD
* 例如 : `git reset Head^` 等於 `git reset @^` ， `git reset @~2`

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

### Diff

```
git diff commit A commit B
```
```
git diff HEAD
```
* [ ... ]

### Log

```
git log
```
* [ ... ]




## 分支的相關操作

### branch (TBD)
```
git branch 分支名稱(標簽名稱)
```
```
git branch -d 分支名稱(標簽名稱) 
```

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

```
git remote add
```

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
* -p [ ... ]


```
git pull origin master
```

* 將遠端 `origin` 下載最新的版本到本機，並把遠端的 `master` branch 合併到目前 branch 上
* 要注意執行的時候位於哪個 branch( ex: master / other branch)

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


```
git push -u origin master
```
* `-u` [...]
