# repo

机器学习无线通信讨论班代码仓库

## 账号

1. 仓库管理员账号
2. 需要有一个github的账号，如果想提交文件到github仓库的话，需要联系管理员拉入成为仓库的成员，这样才能修改github仓库的内容

## 仓库介绍

仓库建立和维护看这个 [github 仓库快速入门](https://docs.github.com/zh/repositories/creating-and-managing-repositories/quickstart-for-repositories)

了解git看这个[pro git](https://www.progit.cn/#_pro_git)

**文件结构**

```sh
project：多人协作的项目
paper：组会分享的文章等
individual：个人其它想要共享的东西可以放在这个文件夹中
```

**分支结构**

```sh
main          ─── 受保护的「分支」（仅管理员可合并）
│
├── dev       ─── 测试分支（全体可推送，需Pull Request合并），从github上git clone到本地电脑的时候默认拉取的是dev分支的最新变化
│
└── feature  ─── 个人分支（每人独立分支，命名如 `feature-yourname`）
```

## 最佳实践

- 远程仓库：指的是在云端github上的仓库
- 本地仓库：指的是我们git clone到本地电脑所形成的仓库
- 工作区：我们修改文件和代码是在工作区修改的，修改完后我们会add和commit到本地仓库，最后再push到远程仓库。

下载安装好git后，运行下面的命令设置用户信息，这样提交或修改项目的时候可以通过历史记录清楚知道是谁提交的。
```sh

git config --global user.name "yourname"
git config --global user.email xxxx@qq.com
```

1. 拉取该仓库

2. 创建个人分支并切换到自己的分支
   由于是团队共同修改一个仓库里的东西，因此每个人在修改仓库的内容时，都应该新创建一个分支，然后在这个分支上修改内容。

```shell
git branch feature-yourname   创建新分支
git switch feature-yourname   切换到该新分支
```


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

6. 切换到feature-yourname分支

```sh
git branch  查看当前是在哪个分支
git switch feature-yourname
```

8. 将个人的feature-yourname上的内容rebase到dev分支上
在个人分支上，将dev分支的改动放上去

   ```sh
   git rebase dev
   ```

9. 推送
将本地仓库的feature-yourname分支上的内容推送到远程仓库的feature-yourname分支上去

```sh
git push -f origin feature-yourname
```

10.  pull request
在你的个人github账户上，可以选择将个人的feature-youname分支内容pull request到dev分支上。

11. 删除个人分支（选择性操作）
个人修改的内容就完全合并到仓库的核心分支上后，可以删除个人分支，避免仓库分支杂乱。
```sh
git branch -d feature-yourname
git push origin --delete feature-yourname
```


