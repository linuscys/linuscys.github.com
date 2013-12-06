---
layout: post
title: ssh 登入免密碼
---

一般登入ssh時都要輸入密碼，但因為密碼被要求定期更換，而且每次都要輸入實在很麻煩，所以ssh免密碼就顯得很重要啦！

免密碼的原理其實很簡單，先在client端產生一組金鑰組，包含公鑰和私鑰，再把公鑰放到要連的server中就完成啦。

### 詳細步驟

#### Step 1. 在client端產生金鑰組

    ssh-keygen -t rsa
    (記得Enter passphrase的地方要直接按enter)    

這樣就會產生id_rsa(私鑰)及id_rsa.pub(公鑰)兩個檔案

#### Step 2. 將公鑰放到要連線的server端

信任名單的檔案名稱為authorized_keys，所以只要將剛剛產生的id_rsa.pub放到~/.ssh/authorized_keys就完成啦～