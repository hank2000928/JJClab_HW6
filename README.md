# JJClab_HW6
參考筆記: https://github.com/wsunccake/sle15_notes/blob/master/practice/ch2.md

--------------------------------------
# 練習 6. 使用者、群組與密碼政策
## 6-1~6-3
確認不存在alice、bob帳號後，創建帳號並加入jjc_lab group
<img width="657" height="485" alt="image" src="https://github.com/user-attachments/assets/062eb51c-cee2-4dd0-b4d3-04aadf48d784" />

其中:
-g = Primary Group
-G = Supplementary Groups
-aG = 將使用者附加到 Supplementary Group

## 6-4~6-
設定兩個users的密碼(123456789)後，確認密碼狀態。
<img width="649" height="787" alt="image" src="https://github.com/user-attachments/assets/47965cb3-b29a-435b-8866-aaa2fbfdda70" />

須讓Bob第一次登入強制改密碼，把密碼視為已過期，因此Bob下一次登入時必須更換密碼。
<img width="723" height="288" alt="image" src="https://github.com/user-attachments/assets/c5a3bcfe-e1ca-48aa-8e24-9f237747709e" />
