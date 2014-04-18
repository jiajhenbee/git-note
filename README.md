git-note
========

## 名詞

* commit

* branch


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

# 相當於底下三個步驟：

git fetch origin
git checkout master
git merge origin/master
```

### Push (TBD)

```
```
