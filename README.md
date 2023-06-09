## git 的印象

1. 远程仓库 remote, 默认名称为 origin, 可以自定义为其他的。
2. 本地仓库
3. commit 确认的更改，包含文件的删除，文件的增加，文件的修改（一整个文件）, commit 多个或一个文件的修改集合。
4. 文本修改
5. stage, staging

编辑器修改 -> stage -> 本地仓库 -> 远端仓库。

远端仓库，比如 gitlab github。非本地的仓库。

## 常用命令

### git fetch

用于获取远端的信息，比如 分支信息。

### git pull

用于拉取代码，当远端修改过相同的行，可能会出现冲突。

### git push

用于推送代码，当远端出现分叉，一定会出现冲突。

1. 把本地仓库的 commit 推送到远程仓库

### git rebase

变更分支的位置。表现是一连串的 commit 被移动到了其他地方。

大概率会出现冲突。

有一个很好用的参数是 --onto X A B, 把 A (不包含 A) 到 B 的 commit ，迁移到以 X 为基础。

git rebase --onto 9 5 13



--- 
9 的修改

9 readme 10 -> hello arnold

9 readme 14 -> bad

---
10 的修改

10 readme 10 -> hello

10 readme 1 -> good

--- 
合并冲突解决

10 readme 10 -> hello arnold

10 readme 1 -> good

10 readme 14 -> bad

---

```mermaid
gitGraph
       commit id: "1"
       commit id: "2"
       branch origin/develop
       commit id: "3"
       commit id: "4"
       commit id: "5"
       branch develop
       commit id: "10"
       commit id: "11"
       commit id: "12"
       commit id: "13"
       checkout origin/develop
       commit id: "6"
       commit id: "7"
       commit id: "8"
       commit id: "9"
```

```mermaid
gitGraph
       commit id: "1"
       commit id: "2"
       branch origin/develop
       commit id: "3"
       commit id: "4"
       commit id: "5"
       checkout origin/develop
       commit id: "6"
       commit id: "7"
       commit id: "8"
       commit id: "9"
       branch develop
       commit id: "10"
       commit id: "11"
       commit id: "12"
       commit id: "13"
```

### git reset

### git reset

有三种参数

--hard 会丢弃所有的改动，比较危险。

--mixed 会把所有改动都列出来，从新的 commit 向旧的 commit reset 时，可以保留 commit 的改动。

--soft 与 --mixed 近似，但是 commit 的内容放在 stage 中。

```mermaid
gitGraph
       commit id: "1"
       commit id: "2"
       branch origin/develop
       commit id: "3"
       commit id: "4"
       commit id: "5"
       checkout origin/develop
       commit id: "6"
       commit id: "7"
       commit id: "8"
       commit id: "9"
       branch develop
       commit id: "10"
       commit id: "11 bad"
       commit id: "12 bad"
       commit id: "13 good"
```

```mermaid
gitGraph
       commit id: "1"
       commit id: "2"
       branch origin/develop
       commit id: "3"
       commit id: "4"
       commit id: "5"
       checkout origin/develop
       commit id: "6"
       commit id: "7"
       commit id: "8"
       commit id: "9"
       branch develop
       commit id: "10"
       commit id: "13 good"
```

### git add

把文件添加到 stage , 之后要确认 stage 中的改动。

### git commit

确认 stage 中的改动，并且给一个 commit msg。commit 之后，就可以把 commit 整个推送到远端。

### git merge
