# git基础学习 

## Git有什么作用？

> Git是一个免费的、开源的分布式版本控制系统，用于追踪代码的改动，记录每个文件的修改历史，包括修改内容、作者、时间等，并允许开发者在不同的开发线（分支）上进行并行开发。它最主要的优势在于，所有的这些数据都是本地存储的，使得开发者即使在没有网络连接的情况下也能进行工作

## 配置git

```
git config --global user.name "Acting" //配置用户名

git config --global user.email 2864094036@qq.com //配置邮箱

git config --global credential.help store //无需密码登录

git config --global --list //查看配置信息
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)global 全局配置 所有仓库生效

system 系统配置 对所有用户生效

## 创建仓库

方式一 在本地创建仓库 git init

方式二 在远程服务器克隆一个已经存在的仓库 git clone

git add 添加到暂存区 

git commit 提交

git log查看提交信息 --oneline 简洁提交记录

## 回退撤销操作

git reset --soft 保存工作区和暂存区

git reset --hard 丢弃工作区和暂存区

git reset --mixed 只保留工作区 丢弃暂存区



## git diff

查看差异

git diff  工作区vs暂存区

git diff HEAD 工作区 vs 本地仓库

git diff -

git diff HEAD~ HEAD 比较当前版本与之前版本

git diff HEAD~n HEAD 比较当前版本与之前第n个版本



git rm 删除文件

git rm -cached 仅删除版本库中文件



## gitignore忽略文件

### 基本规则

1. **每一行一个规则**：`.gitignore` 文件中的每一行都定义了一个匹配规则。
2. **匹配模式**：可以使用通配符来匹配文件名或目录名。
3. **注释**：以 `#` 开头的行是注释，会被 Git 忽略。

### 通配符

- `*`：匹配任意字符（不包括目录分隔符）。
- `?`：匹配任意单个字符（不包括目录分隔符）。
- `[abc]`：匹配方括号中列出的任意一个字符。
- `**`：匹配多级目录和文件。
- `{}`：可以组合多个模式，例如 `{*.log,*.txt}`

Java开发在`.gitignore`文件中一般会存放以下几类文件：

1. **编译生成的文件**：包括由Java编译器生成的`.class`文件，以及可能由其他工具生成的如`.jar`、`.o`、`.pyc`等文件。这些文件通常不需要提交到版本控制系统中，因为它们是由源代码编译得到的，且可能会非常大。
2. **构建产物和输出**：包括由构建工具（如Maven、Gradle等）生成的目录和文件，如`target/`、`build/`、`dist/`等。这些文件通常是运行代码的结果，但在版本控制中跟踪它们并不必要。
3. **配置文件**：一些集成开发环境（IDE）如Eclipse、IntelliJ IDEA、NetBeans等生成的配置文件，如`.project`、`.classpath`、`.idea/`、`*.iml`等。这些文件可能包含特定于开发环境的设置，因此不应该提交到版本控制系统中。
4. **日志文件**：包括`*.log`文件和`logs/`目录等。这些文件通常包含运行时生成的日志信息，对于版本控制来说并不是必需的。
5. **临时文件**：如`*.swp`、`*~`、`*.tmp`等。这些文件是编辑过程中产生的临时文件，不需要提交到版本控制系统中。
6. **用户特定文件**：如`.metadata/`等。这些文件包含特定于用户的设置和元数据，不应该提交到版本控制系统中。
7. **敏感信息**：如密码、API密钥、访问令牌等敏感信息。这些信息应该避免存储在版本控制系统中，以防止泄露和安全风险





## 分支操作基本命令

git branch 查看当前所有分支 星号所在位置就是当前分支

git branch 分支名 自定义创建新的分支

git switch 分支名 切换分支

git merge 分支名 合并该分支名到当前分支

git log --graph --oneline --decorate --all 查看分支图

git branch -d 分支名   删除分支 如果该分支没有被合并 需要将小写d改为大写D

分支冲突

git diff 查看冲突内容

起别名

alias 别名="操作命令"



merge 不会破坏分支提交历史 方便回溯查看 会产生额外的提交节点 分支图比较复杂

rebase 形成线性历史 比较直观干净 会改变提交历史 （避免在共享分支使用）



## git分支管理和工作流模型

main  主线分支     最新稳定

hotfix 问题修复分支

develop 开发分支 

feature 功能分支

release 预发布分支



github flow模型