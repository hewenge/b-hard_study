**git参考文档**
1. [Git的使用.md](https://github.com/qianguyihao/Web/blob/master/00-%E5%89%8D%E7%AB%AF%E5%B7%A5%E5%85%B7/02-Git%E7%9A%84%E4%BD%BF%E7%94%A8.md)
2. [廖学峰git介绍](https://www.liaoxuefeng.com/wiki/896043488029600/900003767775424)

**重要概念**
1. 工作区
正常工作的目录，比如当前b-hard-study目录
2. 版本库
工作区里面的.git目录，称为版本库
3. 暂存区和分支
版本库里面有暂存区和默认创建的master分支。
4. git add 命令就是把文件添加到暂存区
5. git commit就是往分支上提交修改。

**git免密登录配置**
```
git config --global user.name "smyhvae"

git config --global user.email "smyhvae@163.com"
```

**git常用命令**
```
git checkout -b dev  // 一个命令完成创建到切换
git branch dev        // 创建分支
git checkout dev      // 切换分支
git checkout -d dev   // 删除分支
git merge dev         // 合并dev分支到当前分支
git merge --no-ff -m "merge with no-ff" dev // 合并分支没有采用Fast forward，即合并时会生成一个新的commit，从历史中能看出分支信息
git checkout -- file  // 撤销工作区的修改
git reset HEAD <file> // 撤销暂存区的修改
git log --pretty=oneline // 查看日志
git reflog     // 查看命令，包括回退命令
git reset --hard 1094a // 回退版本
git tag <tagname>      // 用于新建一个标签
git tag -a <tagname> -m "blablabla..." // 可以指定标签信息
git tag                // 可以查看所有标签
git push origin <tagname>  // 可以推送一个本地标签；
git push origin --tags     // 可以推送全部未推送过的本地标签；
git tag -d <tagname>       // 可以删除一个本地标签
git push origin :refs/tags/<tagname> // 可以删除一个远程标签
```


