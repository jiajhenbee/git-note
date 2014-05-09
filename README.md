git-note
========
### 注意
* 一個專案不允許有雙重 git 管理（在 git 專案裡面包了其他的 git 專案） 
* 若出現雙重管理則解法如下：

> 1. 為求保險，先把架目錄下有 git 管理的資料夾複製到它地備份
> 2. `cd “資料夾”` 進資料夾
> 3. `rm -rfv .gitignore .git` 刪除資料夾裡面的 git `.git` 的目錄
> 4. `cd ..` 回上一層資料夾
> 5. `git status` 確認資料有否正確
> 6. `commit`


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

```
git commit --amend
```
* 更動最後一次 commit 或 push 
> 最常發生在太早送出 commit 或忘了加入某些檔案、或 commit 訊息有誤


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

> 在這個情況下 git 會顯示類似的訊息：

```
You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b new_branch_name

HEAD is now at 8c8952e...
```

> 這表示現在的位置並不在任何 branch (標籤)上，即使是 checkout 標籤所標示的同一個 commit 編號也會發生。不在 branch 上的狀態並不影響「查看 (checkout) 某一個版本」這個動作，唯一的影響是：如果不是在 branch 上新增的 commits，一旦 checkout 其他版本，就會找不到剛才新增的 commits (因為不會顯示在線圖上)

```
git checkout -b 新的分支名稱

# 相當於底下兩個步驟

git branch 新的分支名稱
git checkout 新的分支名稱
```

> 習慣上 `git checkout '任意 commit 編號'` (或 `git checkout head~3`) 會用來查看某個版本的樣子，如果要新增變更就會搭配 `git checkout -b 新的分支名稱` 一起使用。

## Merge

### Merge

```
git merge 某個分支
```

* 把 `某個分支` 的變更合併到目前的 branch 上，新增一個併在一起的 commit

例如在 `master` 上執行 `git merge topic`：


```
      A---B---C  ← topic
     /
D---E---F---G  ← master
```

就會把 `topic` 上不同於 `master` 的 (A、B、C) 變更合併到 `master` 上，記錄成一個新的 commit `H`，這時候 `master` 標籤原本在 `G`，因為新增了 commit 所以移動到 `H`；而因為 merge 的動作並不是在 `topic` branch 上進行，所以 `topic` 標籤維持在 `C` commit 上。

```
      A---B---C  ← topic
     /         \
D---E---F---G---H  ← master
```

### Fast-Forward

如果 `topic` 是基於 `master` 上的版本繼續新增的變更，而且 `master` 上在 `topic` 分支分出去後沒有額外的變化 (上移個示意圖的 F、G commits)，這時候在 `master`上執行 `git merge topic`：

```
D---E---A---B---C
    ↑           ↑
  master      topic
```

就會直接把 `master` 移動到 `topic` 上，稱為 **fast-forward**

```
D---E---A---B---C ← master
                ↑
              topic
```

### --no-ff

```
git merge --no-ff 某個分支
```

如果在上述的情況下希望多增加一個 commit 記錄進度完成，可以加上 `--no-ff` 產生比較好看的版本線圖 (在 `master` 上執行 `git merge --no-ff topic`)：

```
      A---B---C  ← topic
     /         \
D---E-----------H  ← master
```

> 這時候 `topic` 的進度就算完成了，可以用 `git -d topic` 刪掉這個 branch (標籤)

### Pull Request

* **Pull Request** 是 GitHub 提供的功能，通知一起協作的成員有某個 branch 的變更要 merge 進另外一個 branch
* 在 GitHub 頁面上會顯示這個要 merge 進來的變更有哪些 commits，所有加總起來的變更內容 (diff)
* 如果沒有這些變更和要合併的一個分支內容沒有衝突 (conflicts)，GitHub 頁面也提供了 merge 按鈕；如果有衝突就要手動解決後把新增的 commit push 上去

> Pull Request 預設的 merge 方式是 `--no-ff`，所以在版本線圖上可以很清楚的區分進度的變化


## Conflicts (TBD)



## Rebase (TBD)


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
* -p 
> 比較遠端與本雞的差別。`git pull` 和 `git fetch` 不會清除已經被刪掉的 branch，所以要用 `git fetch -p`。

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
* 將本機端所變動的 commit 推到遠端並同步

> push 時不用切到特定位置即可推 origin，但 pull 則需注意自己的位置

```
git push -u origin master
```
* `-u` [...]
