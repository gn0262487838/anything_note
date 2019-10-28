# 雜記

> [LINE BOT](#1)
   
   * [VM設定](#1-1)

   * [對接LINE API](#1-2)
   
   * [經典款實作構想](#1-3)
   
> [GIT](#2)

   * [HEROKU](#2-1)
   
   * [GITHUB](#2-2)

## <h3 id="1">LINE BOT</h3>

### <h3 id="1-1">VM設定</h3>

> virtualbox

0. 匯入ova

1. 設定ipv4

    ex.192.168.114.1

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

 > 製作圖文
 
 * 設定檔
 
 * 把設定檔上傳至line取得id
 
 * 把圖片上傳至指定的id
 
 * 綁定用戶跟圖文選單

> 取個資

> 綁定用戶及發送歡迎詞

# <h3 id="2">GIT COMMAND</h3>

### <h3 id="2-1">HEROKU</h3>

```python
# Install the Heroku CLI 

# 檔案上傳指令
heroku login
git add .
git commit -m "message"
git push heroku master
```

### <h3 id="2-2">GITHUB</h3>

假設我現在在桌面創新資料夾，並開啟cmd
* git blame >>> 查看這個爛code誰寫。
* git log >>> 查看異動紀錄。
* git clone url >>> download repo

```python
# 初始化
1. git init 初始化資料夾
2. git remote add origin https://github.com/gn0262487838/... ;建立remote。
3. git push -u origin master ;設定為預設路徑。
4. git status 檢查資料狀態
```

```python
# 開始使用
3. git add "檔名" or git add . ;表所有檔案
4. git commit -m "message..."
5. git push -u origin master ; -u表示預設origin master，之後再push時就只要打git push。
```
