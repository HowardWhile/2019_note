# **Git 版本同步**

[TOC]

使用的是線上的版本庫，不用特別做設定，就可以拉收、推送同步。

如果是使用電腦本地的資料夾當作版本庫(server)，需要到.git/config之中，將**bare的屬性改成true**。不然本地clone的版本庫(client)就只能拉收，無法推送到該版本庫(server)中。

```powershell
[core]
	...
	bare = true
	...
```

git clone --bare

---

### **Sourcetree**



### **TortoiseGit**
### **SmartGit**
### **GitKraken**
## **hg 轉換成 git版本庫**

 https://dotblogs.com.tw/rickyteng/2018/04/08/225902 

## **Git Flow**

 https://blog.csdn.net/stupid56862/article/details/80708811 

# [Home](./Home.md)

