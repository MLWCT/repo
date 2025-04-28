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

在远程仓库中提交自己分享的东西的简易流程：
（推荐完全按照下面的流程进行）

1. 拉取仓库
   将远程仓库的东西下载到本地电脑上
```sh
git clone https://github.com/MLWC123/repo.git
```

2. 创建个人分支并切换到自己的分支
   由于是团队共同修改一个仓库里的东西，因此每个人在修改仓库的内容时，都应该新创建一个分支，然后在这个分支上修改内容。

```shell
git branch feature-yourname   创建新分支
git switch feature-yourname   切换到该新分支
```


3. 修改内容
此时是在`工作区`修改内容的

4. 将工作区的这些修改保存到本地仓库

```sh
git add .
git commit -m "对作出修改的总结"
```

5. 将本地仓库的变化告知远程仓库
远程仓库出现feature-yourname分支

```sh
git push origin feature-yourname
```

上述步骤1~5是建立了个人分支feature-yourname，并将本地电脑个人分支的改动同步到远程仓库个人分支

接下来需要将每个人的个人分支改动的内容都保存到同一个核心的分支，这里本仓库使用的是dev分支

由于dev分支是多人修改后都会合并的分支，为了避免冲突，需要先在本地仓库更新远程仓库dev分支的最新变动

5. 更新dev分支改动状态
拉取dev分支的最新状态，将远程仓库dev分支的状态同步到本地仓库去。
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

11. 删除分支
   pull request后成功将feature-yourname分支的内容都合并到dev分支后，如果后续的一段时间不再使用，可以使用一下命令删除你建立的分支，可以简化仓库的分支管理。

   ```sh
   git branch -d feature-yourname
   ```

