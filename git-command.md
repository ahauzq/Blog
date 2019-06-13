## git command

### 针对于一些新人或者对 git 命令不熟悉的人，还是有必要学习一下 git 命令，好的 git 命令使用习惯有助于代码的维护

####先说下规范
#####Commit Message 规范

格式

-   feat: 新功能（feature）
-   fix: 修补问题
-   docs: 更新文档
-   refactor: 重构（即不是新增功能，也不是修改 bug 的代码变动）
-   chore: bump version to \${版本号}
-   test: 增加测试
-   style: 格式变更（不影响代码运行的变动）

请确保所有的 commit log 都能表达清楚本地提交的内容。
请不要将多次修改用一次提交，混淆 commit log 的表意

例如 修复了一个 bug 在 commit 时

<pre><code>
    git commit -m'fix:修复客户详情编辑客户信息时时间转换未生效的bug'
</code></pre>

#####分支命名规范

-   feature：feature/\${开发分支，多个单词用中划线 “-” 分隔,例如：feature/order}
-   dev：feature/\${提测分支，master 拉出,多个单词用中划线 “-” 分隔,例如：dev/order}
-   release：refactor/\${预发分支，master 拉出,多个单词用中划线 “-” 分隔,例如：release/order}
-   hotfix：hotfix/\${修复事项，master 拉出,多个单词用中划线 “-” 分隔,例如：hotfix/order}

例如 创建一个新功能客户详情的开发分支

<pre><code>
    git checkout -b feature/customer-detail
</code></pre>

Tag
发布新版本后一定要打 tag，格式 0.1.6，并且添加详细的发布说明。

####TODO 如何创建一个 git 项目 gitlab 和 github 的 git 命令其实是一致的，以 gitlab 为例

####拉取项目

#### Create a new repository

<pre><code>
    git clone git@git.souche-inc.com:zhouqing/zqtest.git
    cd zqtest
    touch README.md
    git add README.md
    git commit -m "add README"
    git push -u origin master
</code></pre>

#### Existing folder

<pre><code>
    cd existing_folder
    git init
    git remote add origin git@git.souche-inc.com:zhouqing/zqtest.git
    git add .
    git commit -m "Initial commit"
    git push -u origin master
</code></pre>

#### Existing Git repository

<pre><code>
    cd existing_repo
    git remote rename origin old-origin
    git remote add origin git@git.souche-inc.com:zhouqing/zqtest.git
    git push -u origin --all
    git push -u origin --tags
</code></pre>

####一些实用的操作命令
####git help

<pre><code>
    git help
</code></pre>

####拉取代码

<pre><code>
    git clone git@git.souche-inc.com:zhouqing/zqtest.git
</code></pre>

####切换分支

#####新建一个分支

<pre><code>
    git checkout -b feature/customer-detail
</code></pre>

#####切换一个已有分支

<pre><code>
    git checkout feature/customer-detail
</code></pre>

#####查看本地分支

<pre><code>
    git branch
</code></pre>

#####查看远程分支

<pre><code>
    git branch -r
</code></pre>

#####查看本地和远程的所有分支

<pre><code>
    git branch -a
</code></pre>

#####删除本地分支

<pre><code>
    git branch -d <分支名>
</code></pre>

#####删除远程分支

<pre><code>
    git push origin --delete <分支名>
</code></pre>

#####更新远程分支列表

<pre><code>
    git remote update origin -p
</code></pre>


####git commit 提交

<pre><code>
    git commit -m'feat:本次新功能提交的备注信息'
</code></pre>

######增补提交. 会使用与当前提交节点相同的父节点进行一次新的提交,旧的提交将会被取消.

<pre><code>
    git commit --amend
</code></pre>

####代码回滚

######HEAD 指向当前最近的一次提交等价于 git log 中的 commit_id 的值

<pre><code>
    git reset HEAD^
</code></pre>

######回滚提交记录，但是文件不改动，取消了之前 commit 和 add 的操作

<pre><code>
    git reset --mixed id <==> git reset id
</code></pre>

######回退到某个版本，只回退了 commit 的信息，不会恢复到 index file 一级。如果还要提交，直接 commit 即可

<pre><code>
    git reset --soft id
</code></pre>

#####彻底回退到某个版本，本地的源码也会变为上一个版本的内容，撤销的 commit 的会丢失；

<pre><code>
    git reset --hard id
</code></pre>

####A 分支未提交代码 转移到 B 分支

<pre><code>
    - 在A分支执行git stash缓存改动的代码
    git stash

    - 切换到B分支
    git checkout B

    - B分支同步A分支代码，可能要解决冲突
    git pull origin A

    取出缓存
    git stash pop

    代码就轻松从A分支转移到B分支
</code></pre>

####A 分支已 commit 代码 转移到 B 分支

<pre><code>
    - 回滚代码commit记录
    git reset HEAD^ 或者 git reset commit_id 

    - 在A分支执行git stash缓存改动的代码
    git stash

    - 切换到B分支
    git checkout B

    - B分支同步A分支代码，可能要解决冲突
    git pull origin A

    取出缓存
    git stash pop

    代码就轻松从A分支转移到B分支
</code></pre>
