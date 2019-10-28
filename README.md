# 雜記

> [LINE BOT](#1)
   
   * [VM設定](#1-1)

   * [對接LINE API](#1-2)
   
   * [經典款實作構想](#1-3)
   
> [GIT](#2)

   * [HEROKU](#2-1)
   
   * [GITHUB COMMAND](#2-2)
   
> [Jupyter on AWS EC2 for remote](#3)

> [DockerInstall](#4)

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

> Docker 

* 自己研究

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

python
```python
# 初始化
1. git init 初始化資料夾
2. git remote add origin https://github.com/gn0262487838/... ;建立remote。
3. git push -u origin master ;設定為預設路徑。
4. git status 檢查資料狀態
```

python
```python
# 開始使用
3. git add "檔名" or git add . ;表所有檔案
4. git commit -m "message..."
5. git push -u origin master ; -u表示預設origin master，之後再push時就只要打git push。
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

> 比較一下傳統與Docker的差別。

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

# 進入在運作的container
$ docker exec -it containerID bash

# 查看目前的container
$ docker ps -all
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
