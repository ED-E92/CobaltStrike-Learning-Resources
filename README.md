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
![image](https://github.com/user-attachments/assets/f3c6999d-4afd-4b2a-b471-82a36efe2301)

服務端啟動後，就可以開啟客戶端進行連線了。

## 客戶端連線伺服器端
在 Linux 上，直接執行 start.sh 腳本檔案，輸入團隊伺服器的 IP、密碼以及自己的使用者名稱進行連接。

點選 "Connect" 連線後，會彈出提示訊息。如果提示訊息中的雜湊值是正確的，就點擊 "Yes" 來連接團隊伺服器，隨後即可進入 Cobalt Strike 客戶端介面。

在 Windows 上的連線方式類似，直接雙擊 start.bat 檔案來啟動客戶端，然後輸入 IP、密碼和使用者名稱，點選 "Connect" 即可。

執行客戶端腳本後會顯示連線訊息，輸入服務端 IP 位址、連接埠（預設為 50050）以及帳號密碼來進行連線。

連線成功後，即可進入客戶端介面。

# 基礎操作
## 功能介紹
### 可視化介面
Cobalt Strike 的使用者介面分為兩部分：介面上方顯示會話或目標的視覺化，介面下方顯示與每個 Cobalt Strike 功能或會話相關的標籤。您可以點擊這兩部分之間的區域，根據需要調整它們的大小。

![image](https://github.com/user-attachments/assets/df5fcec1-c466-4f84-bfef-e6a71fba0a3a)
