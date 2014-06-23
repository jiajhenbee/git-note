Git 狀況劇
=========

### 我把資料夾複製到專案中，commit 之後又改了一些東西，卻發現 `git diff` 沒有顯示修改的內容，反而出現 `dirty`：

```
-Subproject commit ea3b189e5e5664b669df816ae11a3ddc9218b91a
+Subproject commit ea3b189e5e5664b669df816ae11a3ddc9218b91a-dirty
```



### 雙重 git 管理 
* 一個專案有雙重 git 管理（在 git 專案裡面包了其他的 git 專案） 
* 若出現雙重管理則解法如下：

> 1. 為求保險，先把架目錄下有 git 管理的資料夾複製到它地備份
> 2. `cd “資料夾”` 進資料夾
> 3. `rm -rfv .gitignore .git` 刪除資料夾裡面的 git `.git` 的目錄
> 4. `cd ..` 回上一層資料夾
> 5. `git status` 確認資料有否正確
> 6. `commit`

