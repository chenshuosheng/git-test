### 1. 分布式版本控制工具  VS  集中式版本控制工具


- #### 集中式：Subversion、CVS

​	优点：维护简单

​	缺点：中央服务器单点故障

- #### 分布式：Git

​	优点：解决了集中式版本控制系统的缺陷

		1. 服务器在断网的情况下也可以进行开发(因为版本控制是在本地进行的)；
		2. 每个客户端保存的都是整个完整项目(包含历史记录)，更加安全



区别：

​		集中式的版本控制系统，每次在写代码时都需要从服务器中拉取一份下来，并且如果服务器丢失了，那么所有的就都丢失了，**本机客户端仅保存当前的版本信息**，换句话说，**集中式就是把代码放在一个服务器上集中管理**，你的所有回滚等操作都需要服务器的支持。

​		分布式的版本控制系统，每个人的电脑都是服务器，当从主仓库拉取一份代码下来后，**本地电脑就是服务器**，无需担心主仓库被删或者找不到的情况，可以自由在本地回滚/提交，当想把自己的代码提交到主仓库时，只需要合并推送到主仓库就可以了，同时可以把自己的代码新建一份仓库分享给其它人。

​		集中式的版本控制系统都有一个主版本号，所有的版本迭代都以这个版本号为主，而分布式因为每个客户端都是服务器，git没有固定的版本号，但是有一个由哈希算法算出的id，用来回滚用的，同时也有一个**master仓库，这个仓库是一切分支仓库的主仓库**，<u>我们可以推送提交到其它仓库并合并到主仓库上，主仓库的版本号会迭代一次，我们客户端上的git版本号无论迭代多少次，都跟master无关，只有合并时，master才会迭代一次</u>。





### 2. 工作机制 & 远程库

<img src="https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121145650885.png" alt="image-20240121145650885" style="zoom: 50%;" />





<img src="https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121150019604.png" alt="image-20240121150019604" style="zoom: 80%;" />



### 3. 常用命令

<img src="https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121151517831.png" alt="image-20240121151517831" style="zoom:80%;" />



- #### git config --global  参数名 参数值(全局配置)

<img src="https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121152323969.png" alt="image-20240121152323969" style="zoom:80%;" />





- #### git config --global --list(查看全局配置)

![image-20240121152150031](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121152150031.png)



- #### git init(将当前目录作为本地库，自动生成.git文件夹，默认生成的分支为主分支：master)



- #### git status(查看本地库状态)

![image-20240121154120139](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121154120139.png)



<img src="https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121153029612.png" alt="image-20240121153029612" style="zoom:80%;" />



- #### git add 文件名(添加文件到暂存区)

  <img src="https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121160536289.png" alt="image-20240121160536289" style="zoom:80%;" />



- #### git commit(提交文件到本地仓库)

- #### git reflog(查看简略提交信息) 

- #### git log(查看详细提交信息) 

  <img src="https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121161522776.png" alt="image-20240121161522776" style="zoom:80%;" />

<img src="https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121161645980.png" alt="image-20240121161645980" style="zoom:80%;" />



本地文件已经没有需要提交的内容了

![image-20240121162151556](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121162151556.png)



再次修改 ----> add ---->  commit  ---->  log

![image-20240121162622112](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121162622112.png)



- #### git commit -m “备注内容” 文件名(添加备注提交)

![image-20240121163037459](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121163037459.png)



- #### git commit --amend(修改上次提交的注释)

  github last写成了gihub last

![image-20240122091147516](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240122091147516.png)



<img src="https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240122091443307.png" alt="image-20240122091443307" style="zoom:67%;" />



![image-20240122091609340](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240122091609340.png)





第二天发现**无法直接push**

- #### git add all(提交所有，包含删除信息)

- #### git add .(提交所有修改，不包含删除信息)

![image-20240122092522212](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240122092522212.png)



<img src="https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240122092719500.png" alt="image-20240122092719500" style="zoom:67%;" />



- #### git reset --hard 版本号(版本穿梭)

  <img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20240121165143757.png" alt="image-20240121165143757" style="zoom:80%;" />



vi命令--插入模式（Insert Mode）相关的快捷键：

​		i：在当前光标位置前插入文本

​		a：在当前光标位置后插入文本

​		o：在当前行下方插入一个新行

​		O：在当前行上方插入一个新行，并进入插入模式

​		ESC：退出编辑

​		shift + “:”，输入wq，保存文件



cat 文件名：查看文件内容

tail -n 数值(m) 文件名：查看文件倒数m条数据



### 4. 分支

- #### git branch 分支名(新增分支)

- #### git branch -v(查看分支详情)

- #### git checkout 分支名(切换分支)

- #### git checkout -b 分支名(新增分支并切换到该分支)

  ![image-20240122095741162](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240122095741162.png)

  

  ![image-20240121172511929](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121172511929.png)

  

  ![image-20240121172525337](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121172525337.png)

  

![image-20240121172559287](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121172559287.png)



在hot-fix分支下，修改文件并提交

![image-20240121173218336](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121173218336.png)



- #### git merge 分支名(将其它分支内容合并到当前分支)

![image-20240121174500695](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121174500695.png)





- 生成冲突

![image-20240121180945213](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121180945213.png)



![image-20240121180959497](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121180959497.png)



- 合并冲突

![image-20240121181021994](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121181021994.png)



![image-20240121181326466](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121181326466.png)



![image-20240121181332745](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121181332745.png)



- #### git branch -d 分支名(删除本地分支)

  ![image-20240122100422904](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240122100422904.png)



- #### git push  项目别名(绑定远程链接) 本地未提交新分支(在远程仓库上创建新分支，并提交本地代码)

![](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240122101214297.png)



- #### git push  项目别名(绑定远程链接) 待删除分支名

  ![image-20240122101841193](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240122101841193.png)

- ![image-20240122101944015](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240122101944015.png)



### 5. github

#### 1. 新建项目

<img src="https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121205835395.png" alt="image-20240121205835395" style="zoom: 67%;" />



#### 2. 填写项目名称、描述信息，选择是否公开

<img src="https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121205910236.png" alt="image-20240121205910236" style="zoom: 67%;" />

#### 3. 获取项目在github上的链接

<img src="https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121205748404.png" alt="image-20240121205748404" style="zoom:67%;" />





- #### git remote -v(查看当前所有别名)

- #### git remote add 别名 项目链接(给项目起别名)

![image-20240121205701459](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121205701459.png)



- #### git push 别名 分支名(上传远程仓库)

  - 配置代理

    - git config --global http.proxy 代理地址
    - git config --global https.proxy 代理地址（查看vpn工具获得）

    ![image-20240121213852435](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121213852435.png)



**先添加到暂存区，再提交到本地库，最后才能push到远程仓库**

![image-20240121214437564](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121214437564.png)



- #### git clone 远程链接(克隆代码)

  ![image-20240121215115719](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121215115719.png)

  ![image-20240121215409717](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121215409717.png)

  ![image-20240121215635898](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121215635898.png)



**邀请成员，共同开发**

![image-20240121220701153](https://cdn.jsdelivr.net/gh/chenshuosheng/picture/git/image-20240121220701153.png)