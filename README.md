# repo
机器学习无线通信讨论班代码仓库

## 账号

1. 仓库管理员账号
2. 个人账号如果想修改仓库内容的话，需要联系管理员并被拉入成为仓库团队成员

## 仓库介绍

仓库建立和维护看这个 [github 仓库快速入门](https://docs.github.com/zh/repositories/creating-and-managing-repositories/quickstart-for-repositories)

了解git看这个[pro git](https://www.progit.cn/#_pro_git)

文件结构

```
project：多人协作的项目
paper：组会分享的文章等
individual：组内个人的项目，如不错的文章和代码等
```



**分支结构**

```
main          ─── 受保护的「分支」（仅管理员可合并）
│
├── dev       ─── 测试分支（全体可推送，需Pull Request合并），git clone的时候默认拉取的是dev分支的最新变化
│
└── feature  ─── 个人开发分支（每人独立分支，命名如 `feature-yourname`）
```

## 最佳实践

- 远程仓库`remote git`指的是github上的仓库
- 本地仓库`local git`指的是我们git clone到本地电脑所形成的仓库
- 工作区：我们修改文件和代码是在工作区修改的，修改完后我们会add和commit到本地仓库，最后再push到远程仓库。

1. 拉取仓库
   ```sh
   git clone https://github.com/MLWC123/repo.git
   ```

2. 创建个人分支并切换到自己的分支
   ```shell
   git branch feature-yourname
   git switch feature-yourname
   ```

   这个时候本地仓库就会出现feature-yourname这个新的分支。

3. 修改本地电脑工作区的文件和代码

4. 将工作区的这些修改保存到本地仓库
   ```sh
   git add .
   git commit -m "对作出修改的总结"
   ```

5. 将本地仓库的变化告知远程仓库
   ```sh
   git push origin feature-yourname
   ```

   远程仓库出现feature-yourname分支

上述步骤1~5是个人在仓库中修改文件or代码的基本流程。

接下来需要将个人修改的东西合并到远程仓库的dev分支中去。

由于dev分支是多人修改后都会合并的分支，为了避免冲突，推荐使用rebase来解决合并问题。

6. 切换到dev分支，并拉取dev分支的最新状态，将远程仓库dev分支的状态同步到本地仓库去
   ```sh
   git switch dev
   git pull origin dev
   ```

7. 查看当前所处的分支，切换到feature-yourname分支
   ```sh
   git branch
   git switch feature-yourname
   ```

8. 将个人的feature-yourname上的内容rebase到dev分支上
   ```sh
   git rebase dev
   ```

9. 将本地仓库的feature-yourname分支上的内容推送到远程仓库的feature-yourname分支上去

   ```sh
   git push -f origin feature-yourname
   ```

10. pull request

    在你的个人github账户上，可以选择将个人的feature-youname分支内容pull request到dev分支上

