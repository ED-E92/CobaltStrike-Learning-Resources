
# 介紹
官網：https://www.cobaltstrike.com

指南：Cobalt Strike 使用者指南

Cobalt Strike 官方的工具倉庫：https://cobalt-strike.github.io/community_kit/

Cobalt Strike 是一個用於對手模擬和紅隊行動的平台。它提供了後滲透代理和隱藏通道功能，用來模擬在客戶網路中長期潛伏的安全威脅。Cobalt Strike 的 Malleable C2 Profile 功能可以讓每次變更 C2 的網路信標，讓它看起來像是不同的惡意軟體。這些工具補充了 Cobalt Strike 強大的社交工程流程、協作能力和獨特的報告功能，旨在協助藍隊進行訓練。

總體而言，Cobalt Strike 是安全專業人員常用的全面且強大的工具，用來評估網路和系統的安全性，並識別和利用潛在的漏洞和弱點。

# 學習如何使用 Cobalt Strike

要了解如何使用 Cobalt Strike，您可以按照以下步驟進行：

  1、閱讀 Cobalt Strike（https://www.cobaltstrike.com/）創作者提供的文件和教程，這些資源可以在官方網站上找到。這會給您介紹該工具的特性和功能，以及如何使用它的詳細說明。

  2、加入 Reddit 或 LinkedIn 等線上社群和論壇，Cobalt Strike 用戶可以在這些平台上分享使用該工具的提示、技巧和建議。這能讓您獲得其他用戶的寶貴見解和觀點，幫助您從他們的經驗中學習。

  3、參加專注於 Cobalt Strike 或相關主題（例如滲透測試或網路安全）的研討會、會議或培訓課程。這些活動能提供您實務經驗和知識，還可以幫助您與該領域的其他專業人士建立聯繫。

  4、在安全且受控的環境（例如虛擬機器或實驗室網路）中練習使用 Cobalt Strike。這樣可以讓您試驗該工具並了解它的運作方式，而不會對網路或系統的安全造成威脅。


# 安裝與配置
## 環境準備
下載連結（破解版本）：https://github.com/Ixve/Red-Team-Tools?tab=readme-ov-file （請勿用於任何非法用途，僅供學習研究使用。為了您的安全，請在虛擬機中進行測試）

伺服器端：Ubuntu / CentOS

客戶端：Windows / macOS / Kali Linux

伺服器端/客戶端環境：Oracle Java 1.8

## JAVA 安裝
Ubuntu：執行 sudo apt install -y openjdk-8-jdk

CentOS：執行 sudo yum install java-8-openjdk-devel

macOS：執行 brew install java11

Windows：下載網址：https://www.oracle.com/java/technologies/downloads/#java8-windows

檢查是否安裝成功：執行 java -version

## 客戶端與伺服器端連線
Cobalt Strike 使用 C/S 架構，客戶端會連接到團隊伺服器，而團隊伺服器再連接到目標。換句話說，Cobalt Strike 的客戶端不會直接與目標伺服器互動，而是通過團隊伺服器來進行。因此，本文將介紹如何讓 Cobalt Strike 的客戶端連接到團隊伺服器。

## 伺服器端啟動
建議使用 screen 開啟一個新視窗（可選）：執行 screen -S cs

賦予執行權限：執行 chmod +x teamserver

在新視窗中執行指令啟動 Teamserver：./teamserver <host> <password> [/path/to/c2.profile]
![image](https://github.com/user-attachments/assets/4a2ed2da-ff55-4450-a90f-3d753da17305)

服務端啟動後，就可以開啟客戶端進行連線了。

## 客戶端連線伺服器端
在 Linux 上，直接執行 start.sh 腳本檔案，輸入團隊伺服器的 IP、密碼以及自己的使用者名稱進行連接。

點選 "Connect" 連線後，會彈出提示訊息。如果提示訊息中的雜湊值是正確的，就點擊 "Yes" 來連接團隊伺服器，隨後即可進入 Cobalt Strike 客戶端介面。

在 Windows 上的連線方式類似，直接雙擊 start.bat 檔案來啟動客戶端，然後輸入 IP、密碼和使用者名稱，點選 "Connect" 即可。

執行客戶端腳本後會顯示連線訊息，輸入服務端 IP 位址、連接埠（預設為 50050）以及帳號密碼來進行連線。

連線成功後，即可進入客戶端介面。

![image](https://github.com/user-attachments/assets/1a653d3e-7fd2-40ce-9619-1dbe76109f5d)


# 基礎操作
## 功能介紹
### 可視化介面
Cobalt Strike 的使用者介面分為兩部分：介面上方顯示會話或目標的視覺化，介面下方顯示與每個 Cobalt Strike 功能或會話相關的標籤。您可以點擊這兩部分之間的區域，根據需要調整它們的大小。

![image](https://github.com/user-attachments/assets/ab46b967-d551-4b01-9a70-edac5424d1f0)

#### 工具列
Cobalt Strike 頂部的工具列可以快速存取 Cobalt Strike 的常用功能。了解工具列上的按鈕，能大幅提升你使用 Cobalt Strike 的效率。

|     圖示      | 作用 |
| ------------- | ------------- |
| ![image](https://github.com/user-attachments/assets/46e0e254-dcfe-4f78-bad0-95dc35eceeec)  | 連接到另一個團隊伺服器  |
| ![image](https://github.com/user-attachments/assets/b0417e12-7061-46a7-a3ae-1e0378dc1e93)  | 斷開與當前團隊伺服器的連線  |
| ![image](https://github.com/user-attachments/assets/17cf9f2c-3db6-4c98-9ca2-aa82c6c163bd)  | 創建和編輯 Cobalt Strike 的監聽器  |
| ![image](https://github.com/user-attachments/assets/f78c3ed0-1e1b-4351-9b4d-26f5cb095db5)  | 在圖表視圖中顯示會話  |
| ![image](https://github.com/user-attachments/assets/1dad743b-d314-4296-a539-5a5afeda96da)  | 在表格視圖中顯示會話  |
| ![image](https://github.com/user-attachments/assets/8d2fa5de-ce97-41ec-ba59-d2fccd7a24d8)  | 在表格視圖中顯示目標 |
| ![image](https://github.com/user-attachments/assets/ae76a8d0-1ca8-47bb-8e7b-4870b4cfcfa5)  | 管理網路伺服器  |
| ![image](https://github.com/user-attachments/assets/90cea4d5-7934-4b22-9c46-b48a9e25da9a)  | 查看憑證  |
| ![image](https://github.com/user-attachments/assets/ae48c87c-2a0c-40ef-8407-99531ade9453)  | 查看下載的檔案  |
| ![image](https://github.com/user-attachments/assets/299f9e3c-4ae3-45f3-89dd-bda5d33ab0ba)  | 查看鍵盤紀錄  |
| ![image](https://github.com/user-attachments/assets/b49fcd85-b1c5-4103-8c7b-7193ba94a1de)  | 查看截圖  |

### 監聽器與 Payload

#### 監聽器管理

監聽器不僅是 Payload 的設定資訊，還是 Cobalt Strike 啟動伺服器來接收 Payload 連線的指令。監聽器包含了用戶定義的名稱、Payload 類型以及幾個特定於 Payload 的選項。
在 Cobalt Strike 中選擇「監聽器」，將會打開一個選項卡，列出所有已配置的 Payload 和監聽器。

![image](https://github.com/user-attachments/assets/94c4c442-701e-467f-b0c0-e93093a8f6d6)

按下「添加」來創建新的監聽器，將會顯示「新監聽器」面板。

![image](https://github.com/user-attachments/assets/c1977540-c348-4d80-8500-c6aff8a85317)

使用下拉選單選擇您想要配置的有效負載/監聽器類型之一。每種類型有不同的參數，包含以下幾種：

DNS Beacon

HTTP Beacon and HTTPS Beacon

SMB Beacon

TCP Beacon

External C2

Foreign Listeners

### Beacon Payload
Beacon Payload 非常靈活，支持異步和互動式通信：異步通信的速度較慢，Beacon 會回傳心跳包、下載任務並進入睡眠狀態；互動式通信則是即時進行的。

#### Payload 分類
Cobalt Strike 的 Payloads 通常分為兩種：

Stage (Stageless) Payload（無階段）

Stager Payload（分階段）

它們之間的區別和關係如下：

Stager Payload（分階段） 是一個小型程式，通常經過手動優化的彙編程式，負責下載 Stage (Stageless) Payload（無階段），將其注入記憶體，並將執行權交給它，這個過程稱為分階段式。

主要包含兩大類：一類是生成 shellcode，另一類是直接生成可執行檔案。

![image](https://github.com/user-attachments/assets/66f60815-fbb5-4e78-9b83-61ac57082e6b)

針對 Windows 可執行檔案主要有兩種：

Windows Executeable 對應於 Stager Payload

Windows Executeable(s) 對應於 Stageless Payload

![image](https://github.com/user-attachments/assets/fd5ea52e-efda-4832-a3ef-f26297143746)

#### 生成 Beacon

首先，請建立監聽器。

![image](https://github.com/user-attachments/assets/96524996-7bcf-417a-9199-50c393870556)

選擇生成 Stageless 的 exe 可執行檔案：

![image](https://github.com/user-attachments/assets/3c5de4b6-cbfa-46e1-8ac3-e6aa2135d661)

在受害者機器上執行後，即可收到 Beacon 會話。

#### 執行命令：

![image](https://github.com/user-attachments/assets/3b816cc7-187d-467f-96a1-177a3b27e873)

# 請勿用於任何非法用途，僅供學習和研究使用。

