# GitHub 命令行

### 本地repo

* 设置姓名和邮箱

   ``` git config --global user.name "xxxx"```

   ```git config --global user.email "xxxx@yyy.zzz"```

* 创建并初始化本地空仓库

  ``` git init <repo_name>```

* 查看提交的状态

  ```git status```

* 暂存区中添加更改

  ```git add <file_name>```

* 记录一行提交信息

  ``` git commit -m "commit info"```

* 提交记录
 
  ``` git log```

* 忽略特定格式文件格式

   ```touch .gitignore  && vim .gitigonre ```

   ``` *.out *.py  # in .gitignore```

    原有创建的格式用 git rm --cached <file_name> 忽略
    [常用工程的ignore文件](https://github.com/github/gitignore)

* 回滚操作

  ``` git reset (--mixed --hard --soft ) HEAD~(可换)     #自己查询参数```

  ``` git commit --amend 轻微修改,不进行新的提交```

* 解决push冲突

   假设用户1修改了 xxx文件，并且push了，我这边再修改后push会提示拒绝，有冲突，查看冲突：

    git diff master origin/master

  建议将该文件备份，然后执行以下操作(备份，先拉取再合并）：

```bash
git pull
vim xxx  #对其进行更改
git add xxx
git commit "my work"
git push
```
### GitHub创建本地仓库缓存，在本地构建GitHub云端方法

 在机器a上执行

```git init --bare /home/hanxinle/xdisk.git```

则在该机建立了一个暂存区。

在机器b执行

```git clone hanxinle@xx.mm.yy.zz:/home/hanxinle/xdisk.git```

则将repo拉取到本地，在本地创建文件等更改后，执行add,commit,push操作，其它机器执行

```git clone hanxinle@xx.mm.yy.zz:/home/hanxinle/xdisk.git```

则可以在得到与机器 b 一致的 repo。

### 远程repo
  
* 查看分支
  
    ```git branch``` 
  
* 创建分支
  
     ```git branch <branch_name```
  
* 切换到分支
  
    ```git checkout <branch_name>```
  
* 创建并且切换
  
     ```git checkout -b <branch_name>```
  
* 分支合并(位于master)

  ```git merge <sub_branch_name>```
  
  同步后可以删除这个子分支
  
  ```git branch -d <sub_branch_name>```
  
* 分支同步

  ```git push origin <loacl_branch_name>```   将本地分支同步到服务器

* 分支删除与重命名
   
  ```git brach -D/-d  #删除 see git -h```
  
  远端分支重命名(创建本地分支-->同步到远端-->删除远端同名分支-->原本地分支重命名-->推送到远端)
  
  ```git checkout -b <local_branch>```
  
  ```git push origin <local_branch>```
  
  ```git push --delete origin <local_name>```
  
  ```git commit -m <local_name> <new_branch_name>```
  
  ```git push origin <new_branch_name>
  
   ```
  

* tag 管理

  网页端release中管理,和commit的哈希值相关.
  

### 免密操作

    生成公有\私有key

         
 ```ssh-keygen```
        
  
     一路回车,在.ssh文件夹中,id_rsa 为私有,id_rsa.pub 为公有,在github中点击右上角自己的头像,选择setting,在ssh相关设置
     
      
中,点击NEW SSH KEY,将id_rsa.pub的内容复制进来,此时push还是需要用户名密码,有两种方式可以免输入,一种
      
```vim .git/config```
          
      将 url=https:xxxxx 更改,它的值在网页端打开 github repo 的时候,选择 clone or download 按钮,会有 use ssh 一项,
            
点击这一项,复制url链接到 .git/config 文件替换 url=<url_value> 这一项.

      另一种方式是在clone 命令时,不要通过https命令操作,直接通过 上面这个ssh的url方式操作.
   
### fork后用upstream同步原始repo最新情况

* 首先 git clone 到本地

* 查看远端分支

   ```git remote -v```

* 添加 upstream 分支

   ```git remote add upstream git@xxxx.git```

* 将upstream版本拉到本地

   ```git fetch upstream```
   
* 再合并 upstream master

   ```git merge upstream/master```
   
* 最后push到远端

   ```git push origin master```
   
   
   
### repo 选项

   * Issue 
   
     bug提交
     
   * Projects 
   
     项目进度管理
     
   * Wiki 
   
     项目的介绍,可以制作网页,补充其它必要的文档,背景
   
   * Gist 
      
     代码\文档的片段

   
   




