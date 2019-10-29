# **Git多工**

[TOC]

## **分支**

如果你只想用一條分支當作時間線記錄程式的話，那以上所說的功能已經可以滿足你啦。但身為專業的程序猿(媛)，一定不會止步於此...接下來要說說分支的操作

### **Sourcetree**

點開Branch後創建

![1571300407554](pic/Git/1571300407554.png)

---

### **TortoiseGit**

右鍵TortoiseGit > Show log

對要開動分支的提交按右鍵 > Create Branch at this version...

![1571301266955](pic/Git/1571301266955.png)

![1571301470701](pic/Git/1571301470701.png)

---

### **SmartGit**

![1571302164402](pic/Git/1571302164402.png)

![1571302294755](pic/Git/1571302294755.png)

### **GitKraken**

真簡單

![1571302940859](pic/Git/1571302940859.png)

---

## **合併**

考慮以下狀況

```
基礎為c語言輸出hello world (上中)

一分支修改成 c++輸出hello world (上左)

一分支修改成用迴圈輸出10次 (上右)

>> 期望合併成用c++輸出hello world 10次 (下)
```

![1571279770592](pic/Git/1571279770592.png)
### **Sourcetree**

[ref](https://www.itread01.com/content/1541573643.html)

上述狀況希望將分支feature/loop合併到master，要先切換(checkout)到要合併分支

![1571363143975](pic/Git_03_merge/1571363143975.png)

選擇要合併的分支選ok

![1571363200612](pic/Git_03_merge/1571363200612.png)

這樣操作使用外部工具解決衝突

![1571363314087](pic/Git_03_merge/1571363314087.png)

合併完成後保存就可以關閉外部工具了

![1571363480224](pic/Git_03_merge/1571363480224.png)

記得要提交合併完成的結果

![1571363574441](pic/Git_03_merge/1571363574441.png)

完成圖

![1571363801005](pic/Git_03_merge/1571363801005.png)

*.orig的檔案是合併過程的產物，可以刪除不用追蹤。

### **TortoiseGit**

第一次使用要設定合併的工具

滑鼠右鍵 > TortoiseGit > Setting

![1571364293736](pic/Git_03_merge/1571364293736.png)

選擇完工具後記得還要加上對應的參數[ref](https://www.scootersoftware.com/support.php?zz=kb_vcs)

```powershell
"C:\Program Files\Beyond Compare 4\BCompare.exe" %mine %theirs %base %merged /title1=%yname /title2=%tname /title3=%bname /title4=%mname
```

![1571364866995](pic/Git_03_merge/1571364866995.png)

---

開啟畫面: 滑鼠右鍵 > TortoiseGit > Show Log

對要合併的分支按右鍵選擇Merge to

![1571365081686](pic/Git_03_merge/1571365081686.png)

![1571365619738](pic/Git_03_merge/1571365619738.png)

![1571365626447](pic/Git_03_merge/1571365626447.png)

![1571365633822](pic/Git_03_merge/1571365633822.png)

![1571365642989](pic/Git_03_merge/1571365642989.png)

合併完成後可以選擇繼續提交合併結果或之後再提交

![1571365649584](pic/Git_03_merge/1571365649584.png)

![1571365736160](pic/Git_03_merge/1571365736160.png)

完成圖

![1571365664580](pic/Git_03_merge/1571365664580.png)

---

### **SmartGit**



![1571366541038](pic/Git_03_merge/1571366541038.png)

![1571367081687](pic/Git_03_merge/1571367081687.png)

雙擊檔案開啟解決衝突的畫面

![1571367091034](pic/Git_03_merge/1571367091034.png)

![1571367118528](pic/Git_03_merge/1571367118528.png)

![1571367123889](pic/Git_03_merge/1571367123889.png)

---

完成圖

![1571367128092](pic/Git_03_merge/1571367128092.png)

可以不用依靠beyond compare，本身的就堪用了。當然你想使用也可以[參考](https://www.scootersoftware.com/support.php?zz=kb_vcs#smartgithg)試試看

---

### **GitKraken**

對要合併過去的分支按右鍵選擇Merge `xxx` into `ooo`

![1571368122155](pic/Git_03_merge/1571368122155.png)

如果有衝突就會警告並提示要解決衝突

點選有衝突的檔案

![1571368191990](pic/Git_03_merge/1571368191990.png)

將衝突解決完後保存

![1571368230441](pic/Git_03_merge/1571368230441.png)

輸入訊息就可以提交了

![1571368288200](pic/Git_03_merge/1571368288200.png)

---

完成圖

![1571368346917](pic/Git_03_merge/1571368346917.png)

---

# [Next - 版本同步](./Git_04_sync.md)

# [Home](./Home.md)

