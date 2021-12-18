# Git与Github

## 版本控制

- 版本工程：是一种在开发过程中用于管理我们对文件、目录或工程等内容的修改历史，方便查看更改历史纪录，备份一边恢复以前版本的软件工程技术
  
  - 常见版本控制器
    
    - Git
    
    - SVN
    
    - CVS
    
    - VSS
    
    - TFS

### 版本控制的分类

- 本地版本控制
  
  - 记录文件每次更新，可以对每一个版本做一个快照，或是记录补丁文件，适合个人用

- 集中版本控制
  
  - 所有版本数据都保存在服务器上，协同开发者从服务器上同步更新或上传自己的修改
  
  - 不联网就看不到历史版本；服务器损坏会丢失所有数据
  
  - SVN

- 分布式版本控制
  
  - 所有版本信息仓库全部同步到本地的每个用户，可离线提交，只需在联网时push到相应的服务器或其他的用户那
  
  - 增加了本地储存空间的占用
  
  - Git

## Git

- Git Bash
  
  - Unix与Linux风格的命令行

- Git CMD
  
  - Windows风格的命令行

- Git GUI
  
  - 图形界面的Git

## 基本的Linux命令

## Git基本理论

### 工作区域

- Git本地有三个工作区域
  
  - 工作目录(Working Directory)：平时放代码的地方
  
  - 暂存区(Stage/Index)：暂存区，用于临时存放改动，事实上是一个文件，保存即将提交到文件列表的信息
  
  - 资源库(Repository或Git Directory)：仓库区(或本地仓库)，就是安全存放数据的位置，这里面有提交到所有版本的数据。其中HEAD指向最新放入仓库的版本
  
  - 远程的git仓库(Remote Directory)：远程仓库，托管代码的服务器
    
    - **git add files**** Working Directory Stage(Index);
    
    - **git commit**** Stage(Index) History
    
    - **git push** History Remote Directory
    
    - **git pull** Remote Directory History
    
    - **git reset**  History Stage(Index)

## Git项目搭建

- 本地仓库搭建
  
  - git init

- 克隆远程仓库
  
  - git clone [url]

## Git文件操作

- 文件的四种状态
  
  - untracked:未跟踪，但并没有加入到git库，不参与版本控制，用过git add状态变为staged;
  
  - modify:文件已入库，未修改，即版本库中的文件快照内容与文件夹完全一致；这种类型的文件有两种去处，如果被修改，变为modified，如果使用gir rm移出版本库，则称为untracked文件
  
  - modified:文件已修改，仅仅是修改，并没有进行其他操作。通过git add可暂存staged状态，使用git checked则丢弃修改，返回到unmodify状态，这个git checked即从库中取出文件，覆盖当前修改
  
  - staged:暂存状态，执行git commit则将修改同步到库中，这是库中的文件和本地文件又变为一致，文件unmodify状态，执行git reset HEAD filename取消暂存，文件改为modified

- 查看文件状态
  
  - 查看指定文件状态
    
    - git status [filename]
  
  - 查看所有文件状态
    
    - git status
  
  - 操作文件
    
    - git add .   添加所有文件到暂存区
    
    - git commit -m   提交暂存区的内容到本地仓库   -m提交信息

- 忽略文件
  
  - 在目录下建立".gitignore"文件，特定文件将不纳入版本控制，文件规则如下：
    
    - 忽略文件中的空行或以井号(#)开头的行
    
    - 可以使用Linux通配符。例如星号(\*)代表任意多个字符，问号(?)代表一个字符，方括号([abc])代表可选字符范围，大括号({string1,string2,...})代表可选的字符串等。
    
    - 如果名称前面有一个感叹号(!)表示例外规则
    
    - 如果名称前是一个路径分隔符(/)，表示要忽略的文件在此目录下，而子目录中的文件不忽略
    
    - 如果名称后是一个路径分隔符(/)，表示要忽略的是此目录下该名称的子目录，而非文件(默认文件或目录都忽略)
    
    - ```git
      #为注释
      *.txt        #忽略所有
      !lib.txt     #但lib.txt除外
      /temp        #仅忽略项目根目录下的TODO文件，不包括其他目录temp
      build/       #忽略build/根目录下的所有文件
      doc/*.txt    #会忽略doc/note.txt但不包括doc/server/arch.txt
      ```

- 设置本机绑定SSH公钥，实现免密登陆
  
  - ```git
    # 进入 C:/Users/Adiministrator/.ssh 目录
    # 生成公钥
    ssh keygen
    ```

- 用码云创建自己的仓库
