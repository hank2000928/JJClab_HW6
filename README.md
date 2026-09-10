# JJClab_HW6
參考筆記: https://github.com/wsunccake/sle15_notes/blob/master/practice/ch2.md

--------------------------------------
# 練習 6. 使用者、群組與密碼政策
## 6-1. 使用者與群組操作
確認不存在alice、bob帳號後，創建帳號並加入jjc_lab group
<img width="657" height="485" alt="image" src="https://github.com/user-attachments/assets/062eb51c-cee2-4dd0-b4d3-04aadf48d784" />

其中:
-g = Primary Group
-G = Supplementary Groups
-aG = 將使用者附加到 Supplementary Group

設定兩個users的密碼(123456789)後，確認密碼狀態。
<img width="649" height="787" alt="image" src="https://github.com/user-attachments/assets/47965cb3-b29a-435b-8866-aaa2fbfdda70" />

須讓Bob第一次登入強制改密碼，把密碼視為已過期，因此Bob下一次登入時必須更換密碼。
<img width="723" height="288" alt="image" src="https://github.com/user-attachments/assets/c5a3bcfe-e1ca-48aa-8e24-9f237747709e" />

將 bob 加入 jjc_lab（保留既有補充群組），並從 jjc_lab 移除其他user。
<img width="722" height="366" alt="image" src="https://github.com/user-attachments/assets/4ad1eeb2-c771-4248-bc71-2d56dafe52b9" />

## 6-2. 密碼過期情境（chage／政策）
將作業要求情境套用至alice: 
<img width="710" height="400" alt="image" src="https://github.com/user-attachments/assets/b94f1205-cb49-43f6-8095-117bf5fc7f1b" />

後續情境，更改新建帳號預設: 

<img width="718" height="287" alt="image" src="https://github.com/user-attachments/assets/4a846de4-572e-4409-928a-c3d5d1e0bce7" />
<img width="721" height="576" alt="image" src="https://github.com/user-attachments/assets/0b8b820c-f48c-4cbd-a764-1e31c2fa73af" />

最後建立一個新的測試帳號: 
<img width="729" height="328" alt="image" src="https://github.com/user-attachments/assets/b276b65a-b70a-4f44-be4d-61e90f2ce74f" />



------------------------------------------
# 練習 7. su / sudo 與 sudoers.d
## 7-1. 限制 su，僅特定帳號可用 sudo su -




