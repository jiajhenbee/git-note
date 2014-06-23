關於 Merge
=========

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

就會把 `topic` 上不同於 `master` 的 (A、B、C) 變更合併到 `master` 上，記錄成一個新的 commit `H`，這時候 `master` 標籤原本在 `G`，因為新增了 commit 所以移動到 `H`；而因為 merge 的動作並不是在 `topic` branch 上進行，所以 `topic` 標籤維持在 commit `C` 上。

```
      A---B---C  ← topic
     /         \
D---E---F---G---H  ← master
```

### Fast-Forward

如果 `topic` 是基於 `master` 上的版本繼續新增的變更，而且 `master` 上在 `topic` 分支分出去後沒有額外的變化 (沒有上一個示意圖的 commits F、G)，這時候在 `master`上執行 `git merge topic`：

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
* 加上 `-p` 檢查在遠端已經刪掉的 branch 是不是還留在本機的記錄上

> `git pull` 和 `git fetch` 不會清除已經被刪掉的 branch，所以要用 `git fetch -p`。

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
