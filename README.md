# bid_auto_submission
決包說明輔助程式V1.0

## 更新紀錄
2020/6
  - 加入選擇套版檔案template_cn.yaml or template_tw.yaml，config.ini初始設定時提示請使用者選擇檔案
  - 加入公司代碼別對照檔comp_code.yaml，程式執行時若是沒有對應的代碼會提示請使用者輸入並記錄於comp_code.yaml
  - 加入專業類別標籤，自動判斷案件專類及等級需求，及最低價廠商等級所對應的決包說明
  - 加入編輯字詞庫於選單列，編輯後可案右鍵重新載入字詞庫
  - 加入將決包說明寫入指定WORD檔功能
## 使用方法
 1. 將execution內的檔案下載後，將所有的檔案放在同一資料夾內
 2. 將main.abc改為main.exe，並執行main.exe
 3.第一次執行會產生設定檔config.ini，並提示選擇套版檔
 4.台灣請選擇template_tw.yaml，大陸請選擇template_cn.yaml
 5.程式會自動偵測ERP開啟的暫存檔於user id\AppData\Local\Microsoft\Windows\INetCache\內之pdf檔
 6.如果是呈核表的pdf檔，會於程式檔案列表中出現該案工程名稱及次別
 7.點選要產生決包說明的檔案，於右側說明元件中會出現對應的決包說明
 8.部分需要使用者再輸入的資訊，會以{}標籤的形式出現，於說明文件按下滑鼠右鍵可叫出popup選單，可再按下{}字詞取代會提示請使用者輸入資料
 9.編修決包說明資料，確認無誤後可以按下寫入PDF，再按下列印PDF即可列印
10.寫入WORD檔可將決包說明寫入使用者紀錄決包說明的WORD檔(決包說明增加於WORD檔最下方)
