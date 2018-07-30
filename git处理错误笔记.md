# git处理错误笔记

## 1.

问题:

```
Permission denied (publickey). 
fatal: Could not read from remote respository.
```

解决方法:

```
git remote rm origin 
git remote add origin git@github.com:username/respository.git 
```

```
cd ~/.ssh
ssh-keygen 
```

`ls -a ~/.ssh`

`cat id_rsa.pub`

把里面的内容复制到github的下

(setting->ssh keys->add ssh key)

## 2.ERROR: Repository not found.

问题:

```
ERROR: Repository not found.
fatal: Could not read from remote repository.

 Please make sure you have the correct access rights
 and the repository exists.
```

解决方案:

```
git remote set-url origin git@github.com:xxxxxx/xxxxxx.git
```

## 3.提交错误:RT ! [rejected] master -> master (fetch first)

同步一下git库

`git pull origin master`

**注**:在github下新建一个库时,如果新建了一个readme文件一定要同步!!!