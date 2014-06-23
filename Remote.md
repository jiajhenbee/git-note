遠端同步版本進度
=============


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
