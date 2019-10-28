# 雜記

> [LINE BOT](#1)
   
   * [VM設定](#1-1)

   * [對接LINE API](#1-2)
   
   * [經典款實作構想](#1-3)
   
> [目錄2](#2)

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

### <h3 id="1">對接LINE API</h3> 

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
