# 常用git命令

* 提交分支baozi_v1.1到远程服务
>git push origin baozi_v1.1
* 切换到android分支
>git checkout android
* 合并分支baozi_v1.1到当前分支
>git merge baozi_v1.1
* 创建分支baozi_dev3.0.0
>git branch baozi_dev3.0.0
* 拉取分支baozi_v1.1
>git pull origin baozi_v1.1
* 获取新创建的分支
>git fetch 获取新创建的分支

* 在本地项目所在目录按以下步骤操作
>git init<br>
git add README.md<br>
git commit -m "first commit"<br>
git remote add origin https://github.com/baoziguo/SeeMovie.git<br>
git pull origin master<br>
git push -u origin master<br>

* 但到第四步出现了以下问题

>Administrator@USER-20140819FI /d/git_dir/git_play_repo (master)
$ git remote add origin https://github.com/baoziguo/SeeMovie.git
fatal: remote origin already exists.
* 解决办法如下：

>1、先输入$ git remote rm origin<br>
2、再输入$ git remote add origin git@github.com:dengzhaotai/vlc_play.git 就不会报错了！

* 给版本号为3.5.3的APP打TAG
>git tag v3.5.3
* 远程推送tag
>git push --tags

* 同一个项目关联两个或多个远程仓库
>https://github/baoziguo/Sky.git github上的<br>
git@gitee.com/baoziguo/Sky.git 码云上的<br>
git remote add origin https://github/baoziguo/Sky.git<br>
git remote set-url --add origin git@gitee.com/baoziguo/Sky.git<br>
git push 还是 git push origin 还是 git push origin -all都可以！！！

* 查看本地仓库关联的远程
>git remote -v<br>
输出如下结果：<br>
origin  https://github/baoziguo/Sky.git (fetch)<br>
origin  https://github/baoziguo/Sky.git (push)<br>
origin  git@gitee.com/baoziguo/Sky.git (push)<br>
执行git pull或者git fetch这些拉取远程仓库的命令时，拉的都是带有fetch的这个，而git push这些命令，2个远程仓库都会执行到<br>
ps:看到git地址后面括号里的，其实就能明白意思了，就是告诉我们，github这个git远程仓库，既能被push又能被pull或者fetch，而码云上的只能被push。

* 长期存储密码
>git config --global credential.helper store

* 清除存储密码
>git config --system --unset credential.helper

* git克隆某一个分支最近的10次commit
>git clone -b exchange_dev --single-branch --depth 10 https://github.com/rylink/wallet-android.git

* git clone --depth=1 后获取其他分支
>1.先转换存储库为完整存储库
git pull --unshallow或git fetch  --unshallow
2.修改.git文件夹内config文件的[remote "origin"]节的内容
fetch = +refs/heads/master:refs/remotes/origin/master中的master改成*或git config remote.origin.fetch "+refs/heads/*:refs/remotes/origin/*"
3. 然后执行以下命令获取所有分支
git fetch -pv
