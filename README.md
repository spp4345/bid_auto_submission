# bid_auto_submission
決包說明輔助程式V_0808&V_0809

## 更新紀錄
### 2020/12/16
  - 因寧波地皮案件檔案各信息位置變更，重新調整arguments.csv
  - 將tree_refresh與tree_refresh-w合併，呼叫時僅更新-w區域，設定參數為zone = '-w'
  - 擷取案件名稱func append_pdftext(li, **kwargs)，在gui.py呼叫時傳入案件名稱及次別之位置信息
  - 於擷取pdf信息用的pdf_extract.ipynb中，增加可拖曳的上下左右座標的slider
### 2020/12/9
  - 增加可否抵扣資訊抓取，並顯示於案件資訊視窗
  - 修正判斷最低價計算稅前價錯誤的問題(包含新台幣未正確抓取)
  - 將bid物件模型傳入參數修正為傳入dict
  - 修正較預算0.0%的錯誤
  - 較預算略低的範圍改為-0.1%~0%之間。
  - 修正有議價但是沒有回覆，程式用議後金額判斷的錯誤
  - 修正簡轉繁"面"->'麵"的錯誤。
### 2020/9/3
  - 修復了呈核表2頁只列印1頁的問題
  - 修復了部分案件預算金額抓取錯誤的問題
  - 修復了讀取-w檔抓取既有決包說明內容不全的問題
  - 修復了部分簡體字轉為繁體字錯誤的問題，例如志->誌(x)志(o)、系->係(x)系(o)
  - 針對較預算差異增加了較預算高+X%、較預算低-X%，差異率<-0.05%~ 0%之間時，呈現較預算略低
  - 將PDF檔各信息位置參數外部化，寫在argument_position.csv
### 2020/8/9
  - 大陸案件呈核表已秀出預算需求稅率，增加bid物件require_rate屬性作為預算需求稅率
  - 自動說明會抓取預算需求稅率並做出對應的說明
### 2020/8/8
  - 套版檔Template.yaml
    - 增加可自定義廠商名稱的標記如「」或""
    - 增加可自定義去除廠商名稱的關鍵詞如"工程行"、"機械"...等，可以自行增加關鍵詞
  - 使用介面
    - 增加「寫入PDF後自動更新-w區」的開關
    - 增加PDF檔案列表增加搜尋功能，可鍵入工程名稱關鍵字Highlight項目
    - 高度增加，為了可以瀏覽更多檔案
    - 寬度增加，邊界剛好是呈核表的邊界，方便斷行參考
  - 選單列
    - 自動換行可記錄斷行字數，右鍵斷行依前次字元數斷行
    - 編輯詞庫中增加可打開套版檔案(template.yaml)
    - 設定載入黨路徑增加ERP路徑設定
  - 錯誤修訂
    - 修訂了預約工程存檔檔名有星號的問題
    - 修訂了部分PDF參數未正確擷取的問題
### 2020/6/8
  - 將說明"專類"更改為"專業類別"
  - 加入自動貼上決包說明的功能，可指定熱鍵，預設為ctrl+3，預設間隔時間為0.5秒，要更改請開啟config.ini，將hotkey = ctrl+3改成你要的
  - 將寫入WORD針對發生錯誤時的啟動的程序取消，以觀察發生錯誤時的錯誤信息
  - 將comp_code.yaml寫入config.ini檔，並以絕對路徑方式儲存，可把此檔放在網路空間供大家一起編輯補充及使用
### 2020/6
  - 加入選擇套版檔案template_cn.yaml or template_tw.yaml，config.ini初始設定時提示請使用者選擇檔案
  - 加入公司代碼別對照檔comp_code.yaml，程式執行時若是沒有對應的代碼會提示請使用者輸入並記錄於comp_code.yaml
  - 加入專業類別標籤，自動判斷案件專類及等級需求，及最低價廠商等級所對應的決包說明
  - 加入編輯字詞庫於選單列，編輯後可案右鍵重新載入字詞庫
  - 加入將決包說明寫入指定WORD檔功能
## 使用方法
 1. 將execution內的檔案下載後，將所有的檔案放在同一資料夾內
 2. 如果之前已經安裝過本程式，把之前的comp_code.yaml、rformat.yaml、hot_phrases.yaml放在同一資料夾並覆蓋，第一次執行前確認資料夾內沒有config.ini，如果有的話直接刪除
 3. 將auto_sb-3.4-0808.abc副檔名abc改為exe，會變成猩猩圖案然後滑鼠左鍵雙擊執行(如果會被判定成病毒再試試看auto_sb-3.6-0808.abc)
 4. 程式自動檢查有無設定檔config.ini，如果沒有會產生新的config.ini，並提示選擇套版檔
 4. 台灣請選擇template_tw.yaml，大陸請選擇template_cn.yaml
 5. 程式會自動偵測ERP開啟的暫存檔於user id\AppData\Local\Microsoft\Windows\INetCache\內之pdf檔，如果是win7系統另外設定路徑
 6. 如果是呈核表的pdf檔，會於程式檔案列表中出現該案工程名稱及次別
 7. 點選要產生決包說明的檔案，於右側說明元件中會出現對應的決包說明
 8. 部分需要使用者再輸入的資訊，會以{}標籤的形式出現，於說明元件按下滑鼠右鍵可叫出popup選單，可再**按下{}字詞取代會提示請使用者輸入資料**
 9. 編修決包說明資料，確認無誤後可以按下寫入PDF，再按下列印PDF即可列印
 10. 寫入WORD檔可將決包說明寫入使用者紀錄決包說明的WORD檔(決包說明增加於WORD檔最下方)，**只能用WORD版本2010年後的docx檔**
 11. 自動決包說明使用方法，完成決包說明的文字編輯後，於選單列按下**「導入自動貼上」**，下方狀態列會提示可至ERP按下熱鍵(預設為ctrl+3)自動貼上，預設間隔時間為0.5秒

