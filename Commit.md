儲存變更
=======

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
git add -u [檔案或資料夾]
```
* 更新已存在的檔案

```
git reset 檔案名稱
```
* [ 還原資料到前一次版本，而更改過的版本將不會存檔 ]
* `@`等於 HEAD
* 例如 : `git reset Head^` 等於 `git reset @^` ， `git reset @~2`

> 可以用 `.` 代表目前資料夾內所有的內容，例如 `git add .` 是把所有檔案加入追蹤


### Commit

```
git commit [-m "commit 說明"]
```
* 提交每一次的新增/修改/刪減
* 加入 `-m` 參數直接在後面加上說明文字，不用開啟編輯器
* 加上 `-a` 相當於在 commit 之前執行 `git add .`

```
git commit --amend
```
* 更動最近一個 commit

> 最常發生在太早 commit 忘了加入某些檔案、或 commit 訊息有誤

```
git reset head^
```
* 取消最近一個 commit，保留 commit 更改的內容，`git status` 會顯示有紅色的變更

```
git reset head^
```
* 取消最近一個 commit，保留 commit 更改的內容並且留在 staged 暫存區，`git status` 會顯示變更是綠色

```
git reset --hard head^
```
* 放棄最近一個 commit，丟掉整個 commit 的內容


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

