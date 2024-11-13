# VsCode

<br>
http和ssh两种方式git提交：

https://blog.csdn.net/Bin_niB/article/details/135915738?ops_request_misc=&request_id=&biz_id=102&utm_term=vscode%E4%B8%8Agithub%E5%B8%90%E5%8F%B7%E9%85%8D%E7%BD%AE&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-135915738.142^v100^pc_search_result_base7&spm=1018.2226.3001.4187



注意：github使用token进行http提交，不用密码

1. git remote set-url origin  https://<your_token>@github.com/<USERNAME>/<REPO>.git

2. git config user.password "<your_token>"


<br><br><br>



# 一、git基本信息
    1. git status       查看git当前状态
    	 rm -rf .git  		删除git
    
    2. git init         初始化git项目
    
    3. git config       git配置相关操作
        3.1. 查看git当前所有配置的位置
             git config --list --show-origin      
        3.2. 设置用户信息
            git config --global user.name "XXX"
            git config --global user.email xxx@XX.com
    
    4. git help  查看git命令行使用方法
        4.1. git help status
        4.2. git status --help
        
    5. git diff 比较文件的差异化
    
    6. git log 查看刚刚提交的版本信息
    	 q  查看信息后退出log
    
    7. git branch 查看分支 同git status
    	 git branch feature/6-6         创建分支
    	 git checkout feature/6-6       切换分支
    	 git checkout -b feature/8-8    新建并切换到分支
    	 (在main分支下，git merge feature/6-6, 即可将6-6合并到main)
    	 git branch -d 分支名  删除分支
    	 git branch -D 分支名  强制删除分支
    	 git push origin --delete 分支名   删除远程分支
    	 
    8. 首次推送本地的 main 分支到远程的 origin/main 分支时：  origin可以任意命名
    	 git push -u origin main  
    	 之后只需要执行：
    	 git push   就会默认推送到 origin/main，不需要再指定分支名称。
    	 （或者每次输入：git push origin main)
    	 git push origin main --force  强制推送
    
    9. git pull origin main			拉取远程仓库到本地
    
    10. git remote -v 		查看远程仓库链接地址
    		git remote set-url origin 地址		修改关联的远程仓库origin的地址
    		
<br>
=======================================================
<br><br><br>

# 二、git提交代码

【基本流程】 修改文件 -》 暂存区 -》 提交更新

【注意】删除git后要重新添加token密码：git config user.password "<your_token>"

    git init 初始化
    git add .   提交所有git代码（后面加一个点）  提交到暂存区
    git commit -m "feat:project init"   提交到本地数据库中
    git remote add origin http地址（SSH地址）     本地关联线上仓库
    git push origin main  推送
    
    
    …or create a new repository on the command line
    echo "# managerment-fe" >> README.md
    git init
    git add README.md
    git commit -m "first commit"
    git branch -M main
    git remote add origin https://github.com/Kroo-S/managerment-fe.git
    git push -u origin main
    
    
    …or push an existing repository from the command line
    git remote add origin https://github.com/Kroo-S/managerment-fe.git
    git branch -M main
    git push -u origin main
    
    
    同一个本地提交不同远程仓库会出现问题：
    1. 方法 1：拉取远程变更并合并（推荐）
    	 git pull origin main --rebase
    	 git push origin main
    
    2. 方法 2：强制推送（谨慎使用）
    	 git push origin main --force
    
    3. 方法 3：创建一个合并提交（不使用 rebase）
    	 git pull origin main
    	 git push origin main
    
    
<br>
=======================================================
<br><br><br>


# 三、Token http提交方式

**生成 Personal Access Token**：如果你还没有 GitHub Token，或者不记得你之前生成的，可以按照以下步骤生成一个新的 token：

​	**· **登录 GitHub，进入 **Settings** > **Developer settings** > **Personal access tokens** > **Tokens (classic)**。

​	**· **点击 **Generate new token**，选择适当的权限（例如 repo）。

<img src="https://github.com/user-attachments/assets/c05453f8-4b0c-4a41-b8bd-91baba4dd325" alt="image-20241113165257979" width=30% />



1. 通过指令修改密码为token
  git config user.password "<your_token>"

2. 把token直接添加远程仓库链接中，这样就可以避免同一个仓库每次提交代码都要输入token

​	git remote set-url origin  https://<your_token>@github.com/<USERNAME>/<REPO>.git

​	<your_token>:换成你自己得到的token
​	<USERNAME>:你自己的GitHub的用户名
​	<REPO>:你自己的仓库名称



3. 输入密码为电脑开机密码
<img width="429" alt="59fac1f7092e4da08086021aa3d74a6d" src="https://github.com/user-attachments/assets/a5c1097e-8643-4ea6-8c58-8d5ba4bb6d9c">




<br>
=======================================================
<br><br><br>


# 四、SSH提交方式

1. git init

2. git config --global user.name "your name"

3. git config --global user.email "email@email.com"

4. ssh-keygen -t rsa -C “email@email.com"     本地生产密钥对

<img width="464" alt="image-20241113165030754" src="https://github.com/user-attachments/assets/7e2b9016-ceaf-4a71-a86b-50ae2669e8e7">


<br><br><br>

5. github关联ssh   <img width="363" alt="image-20241113165434348" src="https://github.com/user-attachments/assets/d14f9326-7e65-42be-923b-1649d8b88c34">


6. git remote add origin git@github.com:mmm-cong/test.git   关联ssh地址

7. ...... 待完成......




<br>
=======================================================
<br><br><br>



# 五、VSCode相关问题

Q1:VSCode提交代码后，一直转：

https://blog.csdn.net/Er_Studying_Bai/article/details/128088429?ops_request_misc=&request_id=&biz_id=102&utm_term=vscode上传github代码，提交后一直加载&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-128088429.142^v87^control_2,239^v2^insert_chatgpt&spm=1018.2226.3001.4187


Q2:VSCode代码提交

https://www.bilibili.com/video/BV1dK411p7RF/?spm_id_from=333.337.search-card.all.click&vd_source=6ffa2e348a638cae44b435eff005e657

<br>
=====================================================================
<br><br><br>


# 六、Github用户名更改

https://blog.csdn.net/weixin_44285445/article/details/107833418?ops_request_misc=&request_id=&biz_id=102&utm_term=github%E7%94%A8%E6%88%B7%E5%90%8D%E6%9B%B4%E6%94%B9&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-107833418.142^v87^insert_down28,239^v2^insert_chatgpt&spm=1018.2226.3001.4187

<br><br><br>
​    
# 七、VSCode更新Github仓库代码
    1. git push -f    强制本地代码覆盖github

<br><br><br>

# 八、.gitignore

1. node_module





# 九、gitee和github互传
