# **Git版本切換**

[TOC]

## **版本切換 (讀檔)**

版本跳躍在hg是**update**

但在git被稱為**checkout**或是**switch**

### **Sourcetree**

對要前往的版本點選擇checkout

![1571276062508](pic/Git/1571276062508.png)

---

當前版本Graph欄位的圈圈會是中空的

![1571276767098](pic/Git/1571276767098.png)

---

### **TortoiseGit**

資料夾按右鍵選擇show log，選擇Switch/Checkout也行但操作版本跳躍在commit選項時，不知道為甚麼特別卡

![1571276817647](pic/Git/1571276817647.png)

對要切換的版本點右鍵選擇Switch/Checkout to this

![1571277178322](pic/Git/1571277178322.png)

記得將Create New Branch勾掉不然會長一個分支出來

![1571277408733](pic/Git/1571277408733.png)

---

當前版本

Message欄位的字體會是粗體

![1571277561595](pic/Git/1571277561595.png)

---

### **SmartGit**

先開啟Log v

![1571278177166](pic/Git/1571278177166.png)

對要切換的版本點右鍵選擇Check Out...

![1571278360220](pic/Git/1571278360220.png)

![1571278442985](pic/Git/1571278442985.png)

---

#### 有些版本不見了怎麼辦

到左下角把Local Branches勾起來就會顯示出來了

![1571278600995](pic/Git/1571278600995.png)

---

當前版本會有一個三角形箭頭顯示

![1571278722941](pic/Git/1571278722941.png)

---

### **GitKraken**

對要切換的版本點右鍵選擇Checkout this commit

![1571279020610](pic/Git/1571279020610.png)

---

當前版本前面會有一條連線與勾勾

![1571279101025](pic/Git/1571279101025.png)

---
## **版本比較**
### **Sourcetree**

[ref](https://community.atlassian.com/t5/Bitbucket-questions/SourceTree-diff-between-two-commits/qaq-p/70248)

使用Ctrl+Click選擇兩個commit，就可以看到差異。

![1571298325979](pic/Git/1571298325979.png)

要看細節或使用外部的比較軟體可以這樣子做

![1571298444568](pic/Git/1571298444568.png)

---

### **TortoiseGit**

右鍵顯示show log

![1571276817647](pic/Git/1571276817647.png)

在要比較的提交上點右鍵選擇 Compare with working tree，就會與當前版本(粗體)比較差異。

![1571298975902](pic/Git/1571298975902.png)

雙擊可以用比較軟體看細節

![1571299050568](pic/Git/1571299050568.png)

---

### **SmartGit**

先開啟Log v

![1571278177166](pic/Git/1571278177166.png)

使用Ctrl+Click選擇兩個commit，就可以看到差異。

![1571299268983](pic/Git/1571299268983.png)

---

### **GitKraken**

使用Ctrl+Click選擇兩個commit，就可以看到差異。

![1571299526062](pic/Git/1571299526062.png)

要看細節可以點右邊的檔案或按右鍵開啟外掛的比較軟體

![1571299575219](pic/Git/1571299575219.png)

---

# [Next - Git多工](./Git_03_merge.md)

# [Home](./Home.md)

