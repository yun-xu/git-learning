## 1. add submodule

```
git submodule add http://10.4.132.141:3000/god_eyes/core_lib.git
```
---
## 2. update submodule
Suppose that you have been added submodule
```
git submodule init    // 初始化你的本地配置文件
git submodule update  // 这样就会把submodule的内容clone下来
```
---
## 3. sync submodule
```
git submodule sync  // 暂时不用
```
---
## 4. delete submodule
```
rm .gitmodule   或删除.gitmodule中一个或几个module的信息

git rm --cached submodule_name  例：git rm --cached test1  ※

git add .

git commit -m "test"

git push
```
---