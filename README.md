# 雜記

> [LINE BOT](#1)

   * [VM設定](#1-1)

   * [對接LINE API](#1-2)

   * [經典款實作構想](#1-3)
   
> [GIT](#2)

   * [HEROKU](#2-1)

   * [GITHUB COMMAND](#2-2)
   
> [Jupyter on AWS EC2 for remote](#3)

> [Docker](#4)

   * [Graph](#4-1)

   * [CE版 & EE版](#4-2)

   * [Nouns](#4-3)

   * [Docekr Install for Windows home](#4-4)

   * [Docker Install for Ubuntu](#4-5)

   * [Docker command line](#4-6)

   * [Dockerfile](#4-7)

   * [創建自己的images](#4-8)

   * [Push Dockerhub](#4-9)

   * [jupyter/base-notebook image QA](#4-10)
   
> [TENSORFLOW](#5)

   * [Linux install command](#5-1)
   
   * [Linux uninstall command](#5-2)
   
> [VS Code](#6)

   * [Hot Key](#6-1)

   * [setting.json](#6-2)
   
> [Linux 基本概念及指令整理](#7)

   * [Linux 系統](#7-1)
   
   * [Linux 基本檔案權限概念](#7-2)
   
   * [Linux 資源架構](#7-3)
   
   * [Linux 常用指令](#7-4)
   
## <h3 id="1">LINE BOT</h3>

### <h3 id="1-1">VM設定</h3>

> virtualbox

0. 匯入ova

1. 設定ipv4

    ex.192.168.xxx.x

> MobaXterm

0. [git clone repo](https://github.com/BingHongLi/line_chat_bot_tutorial)

1. ls 遊覽檔案清單

2. cd 前往您要的路徑

3. sh build.sh 建置環境

4. docker images 檢視映像檔

4. sh start.sh 啟動環境

> Docker start

### <h3 id="1-2">對接LINE API</h3> 

> Line message api

1. create a provider

2. create messaging api

3. search your bot api info and insert info to code 

python
```python
# line_secret_key code
{
  "channel_access_token":"your token",
  "secret_key":"your key",
  "self_user_id":"your id",
  "rich_menu_id":"放入生成自定義菜單的id",
  "server_url":"ngrok url or bababa..."
}
```

### <h3 id="1-3">經典款實作構想</h3>

#### 核心功能選單

1. 製作圖文
 
    * 設定檔

    * 把設定檔上傳至line取得id

    * 把圖片上傳至指定的id

    * 綁定用戶跟圖文選單

2. 取資料

3. 綁定用戶及發送歡迎詞

# <h3 id="2">GIT COMMAND</h3>

### <h3 id="2-1">HEROKU</h3>

python
```python
# Install the Heroku CLI 
```

cmd
```cmd
# 檔案上傳指令

heroku login
git add .
git commit -m "message"
git push heroku master
```

### <h3 id="2-2">GITHUB COMMAND</h3>

假設我現在在桌面創新資料夾，並開啟cmd

* git blame >>> 查看這個爛code誰寫。

* git log >>> 查看異動紀錄。

* git clone url >>> download repo

git
```git
# 初始化
1. git init 初始化資料夾
2. git remote add origin https://github.com/gn0262487838/... ;建立remote。
3. git push -u origin master ;設定為預設路徑。
4. git status 檢查資料狀態
```

git
```git
# 開始使用
1. git add "檔名" or git add . ;表所有檔案
2. git commit -m "message..."
3. git push -u origin master ; -u表示預設origin master，之後再push時就只要打git push。
```

git
```
# 回到某一版
1. git log ; 查看log並找尋版號(ex. commit asggr43vsa...)
2. git reset --hard 版號 ; --hard 表示當前的檔案，如不加只會改變版號而不會改變內容物。
3. git log ; 會發現少掉最新的版號，因為檔案已還原成過去的某一版
# 回到未來某一版
1. git reflog ; 即可看到過去及未來的log
2. git reset --hard 版號

* 如果下reset發現沒有變回來，就表示忘了加--hard，直接在下一次重新輸入指令時記得加上--hard就可以了!!!
```

git
```
# 查看分支
1. git branch
# 建立新分支
1. git branch 分支名稱
# 前往分支
1. git checkout
# 刪除分支
1. git branch -D 分支名稱

* 注意，無法刪除目前所在的分支，需要切換到別的分支才能刪除本來所在位置的分支!!!
```

git
```
# 現在有兩個RD，RD1異動test1.txt中func1並新增test2.txt，RD2修改test1.txt中func2並新增test3.txt
# 此時RD1先做完並commit and push並告知RD2他做完了，RD2想說先pull下來他的檔案再繼續修改，
# 但他遇到無法先pull下來，他該怎麼做才能把RD1檔案pull下來並不會覆蓋自己已經寫好的func2?
# 此時有兩種做法，一種先commit，另一種是stash(建議使用，這樣之後維護比較好追蹤!!!)
1. git add .
2. git stash save "封存名稱"  
3. git stash list 查看目前有那些stash
4. git pull 把RD1檔案download and merge
5. git stash pop stash@{0} 把剛剛第二步驟封存的資料加回來到目前分支並刪除此stash

* 如果stash裡面有多餘的不想用，可用git stash drop stash@{1} 就可以直接從stash裡面刪除!!!
```


## <h3 id="3">Jupyter on AWS EC2 for remote</h3>

1. log in AWS EC2 instance

2. check installs

ubuntu
```linux
$ sudo apt-get update

$ sudo apt-get python3-pip python3-dev python-venv

$ sudo apt-get install git

$ sudo apt-get install ufw

$ sudo ufw allow ssh

$ sudo python3 -m pip install jupyter
```

3. generate jupyter config

ubuntu
```linux
$ jupyter notebook --generate-config

$ cd 'The config file should be located under path'

$ ipython
```

python
```python
from notebook.auth import passwd
passwd()

# remember your password
```

ubuntu
```linux
$ vim ~/.jupyter/jupyter_notebook_config.py 
```

python
```python
# Notebook config

c = get_config()

c.NotebookApp.allow_origin = 'put your public IP Address here'
c.NotebookApp.ip = '*'
c.NotebookApp.allow_remote_access = True
c.NotebookApp.open_browser = False
c.NotebookApp.password = u'your password'
c.NotebookApp.port = 8888

# now open your local browser,then enjoy yuor jupyter
```

## <h3 id="4">Docker</h3> 

### <h3 id="4-1">Graph</h3>

比較一下傳統與Docker的差別。

![](https://camo.githubusercontent.com/7a4ea08672138edaffe9bc70dd9a92400593a178/68747470733a2f2f692e696d6775722e636f6d2f49716947796f4a2e706e67)

### <h3 id="4-2">CE版 & EE版</h3>

coming soon

### <h3 id="4-3">Nouns</h3>

> Images

* 安裝在虛擬機上的作業系統。

* Image is R\O

> Container

* 利用映像檔所創造出來的，一個Image可以創造出多個不同的Container，Container也可以被啟動、開始、停止、刪除，並且互相分離。

* Container is R\W

> Registry

* [Docker hub](https://hub.docker.com/)

### <h3 id="4-4">Docekr Install for Windows home</h3>

0. BIOS 開啟虛擬化功能。

1. check your windows version

    * pro 直接去官網安裝

    * home by docker-toolbox(背後藉由VM實現虛擬化) 
    
    [Docker Github Releases](https://github.com/docker/toolbox/releases)

2. install and run

    * 假如先前已安裝git，需要手動設定path

    解決方法:

        1. 右鍵點擊Docker Quickstart Terminal 
        
        2. 內容

        3. 目標改為:
        
        "你的git安裝位置\Git\bin\bash.exe" --login -i "C:\Program Files\Docker Toolbox\start.sh"

### <h3 id="4-5">Docker Install for Ubuntu</h3>

coming soon

### <h3 id="4-6">Docker command line</h3>

ubuntu
```linux
# 查看目前映像

$ docker images

# 從倉庫下載映像

$ docker pull ubuntu:18.04
or
$ docker pull registry.hub.docker.com/ubuntu:18.04

# 刪除映像

$ docker rmi -f ImageID 

# run for new building container

$ docker run -itd -p 80:80 -p 443:8000 ubuntu:18.04 /bin/bash
'''
-t >>> 讓Docker分配一個虛擬終端（pseudo-tty）並綁定到容器的標準輸入上。

-i >>> 讓容器的標準輸入保持打開。

-d >>> 代表在Detached（背景）執行，如不加-d，預設會foreground(前景)執行

-p >>> 代表將本機的80port的所有流量轉發到container中的80port，可重覆使用並指定另一個port

--net >>> 設定要開啟的網路模式 ex.bridge、none、host

-rm >>> 建立container，當使用後關閉時會自動刪除此container。

'''

# run for stopping container

$ docker start containerID

# stop container

$ docker stop containerID

# restart container

$ docker restart containerID

# delete container

$ docker rm containerID

# 進入在運作的container(使用此指令，可在cmd上打exit直接離開且並不會關閉container!!!如果使用attach則不行這樣~)

$ docker exec -it containerID bash

# 查看目前的container

$ docker ps -all

# 查看目前docker 容量使用狀態

$ docker system df 
```

### <h3 id="4-7">Dockerfile</h3>

ubuntu
```linux
$ mkdir "foder"    
$ cd "foder"
$ touch Dockerfile
$ vim Dockerfile
```

dockfile
```dockerfile
# 使用官方ubuntu images
FROM python:3

# 註記誰的
MAINTAINER yourname <youremail@gmail.com>

# 設定工作目錄
WORKDIR /line_bot_docker

# 複製目前目錄下的內容，放進Docker容器中的/line_bot_docker
ADD . /line_bot_docker

RUN apt-get update -y && apt-get install python3-dev -y && apt-get install python3-pip -y

# requirements.txt 裡面放kit 
RUN pip install --upgrade pip

RUN pip install --no-cache-dir -r requirements.txt

# 開80 port，讓Docker容器可以外部存取
EXPOSE 80

# 當Docker容器啟動時，自動執行app.py
CMD ["python3","app.py"]
```

### <h3 id="4-8">創建自己的images</h3>

ubuntu
```linux
$ sudo docker build -t yourDockerHubName/ImageName:tag .

* -t標記添加tag，指定新的映像檔的使用者info

* . 是Dockerfile所在的path，也可以換成具體的Dockerfile的path
```

### <h3 id="4-9">Push Dockerhub</h3>

ubnutu
```linux
$ sudo docker tag ImageName yourDockerHubName/ImageName:tag

$ sudo docker push yourDockerHubName/ImageName:tag
```

### <h3 id="4-10">jupyter/base-notebook image QA</h3>

Q.在開啟容器bash時，會遇到使用者已經被定義好而無法使用sudo的情況。

A.$ docker run -it --net=host --user root -e GRANT_SUDO=yes jupyter/base-notebook /bin/bash

* --net=host 表示指定容器本身的網域不做隔閡，直接跟本機網域共用。

* --user root 指定使用者為root

* -e 設定環境變數?


## <h3 id="5">TensorFlow</h5>

### <h3 id="5-1">Linux install command</h3>

ubuntu
```ubuntu
# check version

$ python3 --version
$ pip3 --version
$ virtualenv --version

# if not,please install 

$ sudo apt update
$ sudo apt install python3-dev python3-pip python3-virtualenv

# create a new virtual environment
# reate a new virtual environment by choosing a Python interpreter and making a ./venv directory to hold it

$ virtualenv --system-site-packages -p python3 ./venv

# Activate the virtual environment using a shell-specific command

$ source ./venv/bin/activate


# install tensorflow & keras

(venv) $ pip install tensorflow
(venv) $ pip install keras

# exit virtualenv

$ deactivate
```

### <h3 id="5-2">Linux uninstall command</h3>

ubuntu
```ubuntu
# uninstall
# -r "targetdirectory"

$ rm -r ./venv
```

## <h3 id="6">VS Code</h3>

### <h3 id="6-1">Hot Key</h3>

1. ctrl + shift + p 指令搜尋
2. ctrl + shift + f global reference search or global file search
3. ctrl + p 在跳出的小視窗中打 
   " > " 即是第一項的功能
   " : " 即可以row number搜尋code
4. ctrl + 上或下鍵 捲動視窗
5. ctrl + ` 顯示或隱藏terminal
6. ctrl + 數字鍵 切換分割視窗
7. ctrl + w 關閉所選的視窗(或分割視窗)
8. ctrl + tab 選擇視窗(或檔案)
9. ctrl + F2 此功能不分大小寫，搜尋相同的變數或函式名稱，可同時修改或更正!!!
9. alt + 左或右鍵 可選擇視窗，跟第八項功能類似
10. alt + 上或下鍵 可整批移動code的位置
11. alt + 滑鼠左鍵 可選取多個位置

[詳情請查閱官方github](https://github.com/Microsoft/vscode-tips-and-tricks)

### <h3 id="6-2">setting.json</h3>

```settings.json
{
  "files.trimTrailingWhitespace": true, // 儲存的時候，自動過濾多餘空格
  "files.autoSave": "onWindowChange", // 是否自動儲存檔案
  "files.autoGuessEncoding": true,
  "files.defaultLanguage": "markdown",

  "editor.fontSize": 20,
  "editor.wordWrap": "on", // code的顯示範圍，超過就換行。
  "editor.renderIndentGuides": true, // 顯示縮排線

  "terminal.integrated.fontSize": 20,
  "terminal.integrated.copyOnSelection": true,
  "terminal.integrated.rightClickBehavior": "copyPaste",

  "python.pythonPath": "你python編譯器的路徑\\python.exe",
  "python.linting.enabled": true,
  "python.linting.pylintEnabled": true,
  "[python]": {
    "editor.tabSize": 4,
    "editor.formatOnSave": true,
    "editor.showFoldingControls": "always",
    "editor.formatOnType": true,
    "editor.insertSpaces": true,
    "editor.detectIndentation": true,
  },

  "[html]": {
    "editor.tabSize": 2,
    "editor.autoIndent": "none",
  },

  "git.autofetch": false,
  // 讓 VSCode 在背景自動執行 git fetch
  "git.enableSmartCommit": false,
  // 如果所有變更都還沒有 git add ( Stage ) 的話，預設會自動全部 Commit，不會再先問過。
  "git.confirmSync": true,
  // 當要同步 Git 遠端儲存庫時，false表示不需要再提問。
  
  "auto-rename-tag.activationOnLanguage": [
    "html",
    "xml",
    "php"
  ],
  // 因為 Auto Rename Tag 擴充套件非常好用，但預設會自動套用在所有檔案格式，這會帶來一些麻煩。
  // 例如在 JS/TS 檔案中剛好改到有 < 的內容時，會導致程式被改壞，所以建議限制特定檔案才需要這個功能。
}


```

## <h3 id="7">Linux 基本概念及指令整理</h3>

### <h3 id="7-1">Linux 系統</h3>

來自Debian 

![](https://assets.ubuntu.com/v1/8dd99b80-ubuntu-logo14.png)

* 軟體套件管理主要是apt-get，使用 apt-get install/remove 套件名稱 來安裝/移除套件

* 不支援cPanel

來自Red hat

![](https://upload.wikimedia.org/wikipedia/commons/thumb/b/bf/Centos-logo-light.svg/658px-Centos-logo-light.svg.png)

* 軟體套件管理主要是yum，使用 yum install/remove 套件名稱 來安裝/移除套件

* 支援cPanel

### <h3 id="7-2">Linux 基本檔案權限概念</h3>

> 身分別
  
  1. u : user   使用者
  2. g : group  群組
  3. o : other  其他人
  4. a : all(以上三種都包含)
  
> 檔案權限
  
  分為 r、w、x
  1. r : 只可讀取    也可表示成數字 : 1
  2. w : 可以被寫入  也可表示成數字 : 2
  3. x : 能被執行    也可表示成數字 : 4
  
> 檔案資訊

```
drwxrwxr-x. 2 root mail 1024  1月 07 10:10 /var/jack
    A       B   C    D    E         F          G

1. A : 第一字元為檔案類型:
          * - : 表 一般檔案
          * d : 表 目錄檔(資料夾的意思)
       第二到第四為一組 表 使用者權限或者root權限
       第五到第七為一組 表 群組權限
       第七到第九為一組 表 other權限
2. B : 檔案連結數
3. C : 檔案擁有者
4. D : 所屬群組
5. E : 檔案大小(kb)
6. F : 最後修改日期與時間
7. G : 檔案所在位置及名稱
```

### <h3 id="7-3">Linux 資源架構</h3>

* 以下路徑為大致擺放的物件，視個別配置會有所不同。

> /usr 全名unix software resource

> /usr/bin 放置一般使用者可以操作的指令(類似設定windows環境參數一樣)

> /usr/sbin 放置root可以操作的指令(類似設定windows環境參數一樣)

> /usr/lib 放置系統函式庫或核心函式庫(64位元放在/usr/lib64)

> /boot 放置開機相關檔案

> /dev 放置device檔案 ex.鍵盤滑鼠...等

> /etc 放置系統檔案

> /home 一般使用者的家目錄(常用的表示方式 : ~/ )

> /root 系統管理員的家目錄

> /var 放置變數或紀錄檔

> /tmp 全名temporary

> /opt 全名optional

### <h3 id="7-4">Linux 常用指令</h3>

* 可使用 man 指令 來查看說明手冊!!!

linux
```linux
0. clear 清除terminal std output
1. echo
2. ls 查看檔案資訊 
3. ll 查看檔案資訊
4. pwd 列印出目前工作目錄
5. cd 移動到XX目錄　(~ : 家目錄　.. : 上一層目錄　/ : 根目錄)
6. cp 複製一份
7. mv 移動某個檔案(資料夾)到另外一個地方 或 更改檔案(資料夾)名稱
8. rm [-r][-f][-rf] 刪除檔案(使用此指令記住，別亂使用!!!!! 　[] 表 參數 )
7. mkdir 創建資料夾
8. file 檢查檔案類型
9. find 搜尋檔案
10.id 查詢當前使用者的uid及gid
11.grep 文字搜索
12.touch 更改timestamp或者新增空白檔案
13.chmod 更改檔案權限
14.cat 將文件內容輸出至terminal
15.vim 進入vim編輯器
16.useradd
17.passwd
18.usermo
19.userdel -r(加上-r表示連同家目錄及郵件夾都刪除，如忘了加，都要手動刪除喔!!!)
20.kill 使用PID來終止程式
21.killall 使用檔案名稱來終止程式
22.crontab 例行性工作排程
```
