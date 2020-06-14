# sender_count

## 起源

在處理完一個寄送大量垃圾信件的帳號後，發現所有寄給 gmail 的信都被送到垃圾桶，於是根據 https://support.google.com/mail/answer/81126?hl=en&ref_topic=7279058](https://support.google.com/mail/answer/81126?hl=en&ref_topic=7279058) ，設立 postmaster 之外，決定將每天使用者計信數量紀錄並發給管理員，加速封鎖發送大量垃圾信帳號的程序

## 方法

1. 複製 maillog 到指定資料夾，解壓縮且合併

2. 計算每個 user 出現在當天 qmgr 的 from <user@hs.ntnu.edu.tw> 次數

      # pick up 不會計算副本數量，故不採用

      # 假設收信人有兩個，maillog 裡會出現3次 ...qmgr...from <user@hs.ntnu.edu.tw>

3. 過濾結果，留下 @*.hs.ntnu.edu.tw 的紀錄

4. 放入 crontab 設定23:00執行 script ，寄結果給管理員
