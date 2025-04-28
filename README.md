# repo
机器学习无线通信讨论班代码仓库

## 账号

1. 仓库管理员账号
2. 个人账号如果想修改仓库内容的话，需要联系管理员并被拉入成为仓库团队成员

## 仓库介绍

仓库建立和维护看这个 [github 仓库快速入门](https://docs.github.com/zh/repositories/creating-and-managing-repositories/quickstart-for-repositories)

了解git看这个[pro git](https://www.progit.cn/#_pro_git)

**分支结构**

main          ─── 受保护的「分支」（仅管理员可合并）
│
├── dev       ─── 测试分支（全体可推送，需Pull Request合并），git clone的时候默认拉取的是dev分支的最新变化
│
└── feature  ─── 个人开发分支（每人独立分支，命名如 `feature-yourname`）

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
   git commit -m "对这些修改的介绍"
   ```

5. 将本地仓库的变化告知远程仓库
   ```sh
   git push origin feature-yourname
   ```

   远程仓库出现feature-name分支
