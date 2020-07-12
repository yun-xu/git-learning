## 1. Purpose
>在游戏开发过程中,设计资源占用了很大一部分空间. 像png,psd等文件是二进制(blob)的,体积也很庞大.但git的diff/patch等是基于文件行的.对于二进制文件来说. git需要存储每次commit的改动.每次当二进制文件修改,发生变化的时候. 都会产生额外的提交量.导致clone和pull的数据量大增.在线仓库的体积也会迅速增长.

![avatar](/img/lfs.png)

---

## 2. How to use
### (1) add LFS
```
git lfs track //查看现有的文件追踪模式
git lfs track "cat.png" //进行大文件跟踪
//之后会生成一个<.gitattributes>的文件,
//自动生成的文件，需一并提交到 Git，否则 Clone 项目的时候 Git LFS 不起作用
git add .gitattributes 
git add cat.png
git commit -m "xxx"
git push
```
### (2) clone to local repository
```
git lfs clone <url>
```
### (3) delete LFS
>开启 LFS 的项目，当 Push 大文件之后，在 GitLab Web 页面上是删除不了的，需要通过接口删除该文件使用本地的命令删除文件并push
```
git rm file
git commit -m
git push
```

### (4) untrack LFS
```
git lfs untrack "*.psd"
```
### (5) clone the repository without LFS
```
GIT_LFS_SKIP_SMUDGE=1 git clone https://github.com/user/repo.git
# 或
git -c filter.lfs.smudge= -c filter.lfs.required=false clone https://github.com/user/repo.git
注：GIT_LFS_SKIP_SMUDGE=1 及 git -c filter.lfs.smudge= -c filter.lfs.required=false 
# 同样使用于其他 git 命令，如 checkout, reset 等。
```