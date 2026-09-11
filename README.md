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
為預防誤鎖su權限，最後再做7-1

## 7-2. 為 myadmin 建立獨立 sudoers 設定
創建myadmin帳號，密碼設置123456789
<img width="718" height="248" alt="image" src="https://github.com/user-attachments/assets/d8cc4d24-5bd3-4925-a9b5-ef19998a8e82" />


利用visudo -f /etc/sudoers.d/myadmin，新增myadmin ALL=(ALL) ALL，意思是：
myadmin 可以透過 sudo 執行所有管理指令，但仍需輸入自己的密碼。
<img width="715" height="169" alt="image" src="https://github.com/user-attachments/assets/a7657172-12dc-4ad2-8da0-b3a6ff04e9a4" />

存檔退出後，確認權限：  
<img width="723" height="285" alt="image" src="https://github.com/user-attachments/assets/e275b847-3d06-46f1-ad8a-72f6bda29b35" />

切換至myadmin測試:  
<img width="732" height="608" alt="image" src="https://github.com/user-attachments/assets/5b33a974-2f67-44eb-b7d5-1b57dc9cfb81" />

## 7-3. poweroff 群組可關機
建立poweroff群組後，將bob加入群組
<img width="704" height="136" alt="image" src="https://github.com/user-attachments/assets/40eba873-f640-4172-813e-3b4fa519e8e2" />

確認關機指令實際路徑後，用<visudo -f /etc/sudoers.d/poweroff>寫入: 
<img width="717" height="165" alt="image" src="https://github.com/user-attachments/assets/ba76eb30-0c3a-4901-98be-7fe0f8e71f2c" />

<img width="723" height="84" alt="image" src="https://github.com/user-attachments/assets/6c209120-832e-410c-82f2-1c1efb484db0" />

驗證bob具有 poweroff / shutdown 相關權限。
<img width="712" height="181" alt="image" src="https://github.com/user-attachments/assets/33afa40f-6580-46e0-8a91-6eefcd7a3e3b" />
<img width="705" height="177" alt="image" src="https://github.com/user-attachments/assets/c9b3fcd4-92db-4686-aa38-21ec3e680420" />

## 7-1. 限制 su，僅特定帳號可用 sudo su -

建立wheel group，納入須有su權限的user
<img width="719" height="218" alt="image" src="https://github.com/user-attachments/assets/af5e1408-a38d-4341-9146-f0042e24cacb" />

確認PAM檔案  
<img width="712" height="487" alt="image" src="https://github.com/user-attachments/assets/7b0c5432-8530-4f4f-bf7b-ca98f1e959e7" />

vi /etc/pam.d/su 修改如下(修改前、後對比)  
<img width="725" height="249" alt="image" src="https://github.com/user-attachments/assets/5373c4e3-ef8e-4bbe-8b48-5921b4a469a7" />
<img width="717" height="259" alt="image" src="https://github.com/user-attachments/assets/76565ac6-f73a-496e-9966-97a8a6b7fd1b" />

同樣在 pam_rootok.so 修改成：  
<img width="698" height="279" alt="image" src="https://github.com/user-attachments/assets/450de5f1-aa5a-4d37-8260-b57b20eeee50" />

實測，alice無su權限:   
<img width="716" height="257" alt="image" src="https://github.com/user-attachments/assets/b3c2e733-d90c-45dc-8c45-8ef7ef503865" />

最後實測myadmin，具有su權限:   
<img width="713" height="256" alt="image" src="https://github.com/user-attachments/assets/0c27eb13-222b-4683-9258-49d6e3140650" />
