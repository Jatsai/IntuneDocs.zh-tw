---
title: "使用 Cisco ISE 限制存取網路 | Microsoft Intune"
description: "使用 Cisco ISE 與 Intune，讓裝置向 Intune 註冊並符合原則，然後才存取 Cisco ISE 控制的 WiFi 和 VPN。"
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 06/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5631bac3-921d-438e-a320-d9061d88726c
translationtype: Human Translation
ms.sourcegitcommit: f33a86c51320c75ce74d20e0cac2b9581990ecec
ms.openlocfilehash: 78945498a951e7b897164ae6f33c4e87d521ca5b


---

# 使用 Cisco ISE 與 Microsoft Intune
Intune 與 Cisco ISE 整合可讓您在 ISE 環境中使用 Intune 裝置註冊與相容性狀態來撰寫網路原則。 這些原則可確保您公司網路的存取權僅限於由 Intune 所管理且符合 Intune 原則的裝置。 

## 設定

若要啟用這項整合，您不需要在 Intune 租用戶中進行任何設定。 您必須提供權限給 Cisco ISE 伺服器，以便存取 Intune 租用戶，且在此完成之後，其餘的設定會在 Cisco ISE 伺服器中發生。 這篇文章提供您指示，為 ISE 伺服器提供存取 Intune 租用戶的權限。 

### 步驟 1︰管理憑證
1. 在 Azure Active Directory (AAD) 主控台中，匯出憑證。 

    #### Internet Explorer 11
        
    a. 以系統管理員身分執行 Internet Explorer，並登入 AAD 主控台。
  
    b。 在 [網址] 列中選擇鎖定圖示，然後選擇 [檢視憑證]
    
    c. 在憑證內容的 [詳細資料] 索引標籤，選擇 [複製到檔案]。

    d. 在 [憑證匯出精靈] 的 [歡迎使用] 頁面上，選擇 [下一步]。 

    e. 在 [匯出檔案格式] 頁面上，保留預設值 [DER 編碼二進位 x.509 (.CER)]，然後選擇 [下一步]。  

    f. 在 [要匯出的檔案] 頁面上，選擇 [瀏覽] 選取儲存檔案的位置，並提供檔案名稱。 雖然看似您選取要匯出的檔案，但您實際上是為匯出的憑證將儲存到的檔案命名。 選擇 [下一步] &gt; [完成]。

    #### Safari
    
    a. 登入 AAD 主控台。

    b。 選擇鎖定圖示 &gt; [更多資訊]。
    
    c. 選擇 [檢視憑證] &gt; [詳細資料]。

    d. 選擇憑證，然後選擇 [匯出]。  


> [!IMPORTANT]
> 檢查憑證的到期日，因為您必須在此憑證到期時匯出並匯入新的憑證。

    

2. 從 ISE 主控台內，將 Intune 憑證 (您已匯出的檔案) 匯入到 [受信任的憑證] 存放區。
3. 在 ISE 主控台中，移至 [管理]  >  [憑證]  >  [系統憑證]。
4. 選取 ISE 憑證，然後選擇 [匯出]。
5. 在文字編輯器中，編輯匯出的憑證︰
 - 刪除 ** -----BEGIN CERTIFICATE-----**
 - 刪除 ** -----END CERTIFICATE-----**
 - 請確定所有的文字在同一行

### 步驟 2︰在 AAD 租用戶中為 ISE 建立應用程式
1. 在 Azure Active Directory (AAD) 主控台中，選擇 [應用程式]  >  [新增應用程式]  >  [加入我的組織正在開發的應用程式]。
2. 提供應用程式的名稱和 URL。 URL 可能是您的公司網站。
3. 下載應用程式資訊清單 (JSON 檔案)。
4. 編輯資訊清單 JSON 檔案。 在稱為 **keyCredentials** 的設定中，提供步驟 1 中的已編輯憑證文字作為設定值。
5. 儲存檔案，而不變更其名稱。
6. 提供應用程式對於 Microsoft Graph 和 Microsoft Intune API 的權限。
    1. 針對 Microsoft Graph，選擇下列各項
        - **應用程式權限**︰讀取目錄資料
        - **已委派的權限**： 
            - 隨時存取使用者的資料
          - 登入使用者
   2. 針對 Microsoft Intune API，在 [應用程式權限] 中選擇 [Get device state and compliance from Intune] (從 Intune 取得裝置狀態和相容性)。

7. 選擇 [檢視端點]，並複製下列值以便用於進行 ISE 設定︰

|AAD 入口網站中的值|ISE 入口網站中的對應欄位|
|-------------------|---------------------------------|
|Microsoft Azure AD Graph API 端點|自動搜索 URL|
|OAuth 2.0 權杖端點|權杖簽發 URL|
|使用用戶端識別碼更新您的程式碼|用戶端識別碼|


### 步驟 3：進行 ISE 設定 
2. 在 ISE 管理員主控台中，提供這些設定值︰ 
  - **伺服器類型**：Mobile Device Manager
  - **驗證類型**：OAuth – 用戶端認證
  - **自動搜索**：是
  - **自動探索 URL**︰輸入步驟 1 的值
  - **用戶端識別碼**︰輸入步驟 1 的值
  - **權杖簽發 URL**︰輸入步驟 1 的值



## Intune 租用戶和 Cisco ISE 伺服器之間共用的資訊
下表列出您的 Intune 租用戶和 Cisco ISE 伺服器之間，針對 Intune 所管理之裝置共用的資訊。

|屬性|  說明|
|---------------|------------------------------------------------------------|
|complianceState|   True 或 false (字串)，指出裝置相容或不相容。|
|isManaged| True 或 false，指出用戶端是否由 Intune 管理。|
|macAddress|裝置的 Mac 位址。|
|serialNumber|裝置的序號。 僅適用於 iOS 裝置。|
|imei|IMEI (15 位數︰14 個數字再加上一個檢查碼) 或 IMEISV (16 位數) 包含裝置的來源、型號和序號等資訊。 IMEI/SV 的結構指定於 3GPP TS 23.003 中。 僅適用於具有 SIM 卡的裝置。|
|udid|唯一裝置識別碼，40 個字母和數字的序列，專用於 iOS 裝置。|
|meid|行動設備識別碼，用來識別實體 CDMA 行動站設備的全球唯一編號。 數字的格式由 3GPP2 報表 S. R0048 所定義，但實際上，可以將它視為 IMEI 但具有十六進位的數字。 MEID 有 56 個位元長 (14 個十六進位的數字)。 它包含三個欄位，包括 8 位元地區碼 (RR)、24 位元製造商碼，和製造商指派的 24 位元序號。| 
|osVersion| 裝置的作業系統版本。
|模型|裝置型號。
|manufacturer|裝置製造商。
|azureDeviceId| 裝置加入 Azure Active Directory 工作地點之後的識別碼。 若裝置未加入則為空的 guid。|
|lastContactTimeUtc|裝置上一次簽入 Intune 管理服務時的日期和時間。 


## 使用者經驗

當使用者嘗試使用任何未經註冊的裝置存取資源時，他們將看見註冊的提示，如以下所示︰

![註冊提示的範例](../media/cisco-ise-user-iphone.png)

當使用者選擇註冊，就會重新導向至 Intune 註冊程序。 這些主題中說明 Intune 的使用者註冊體驗︰

- [在 Intune 註冊 Android 裝置](/intune/end-user/enroll-your-device-in-Intune-android)</br>
- [在 Intune 註冊 iOS 裝置](/intune/end-user/enroll-your-device-in-intune-ios)</br>
- [在 Intune 註冊 Mac OS X 裝置](/intune/end-user/enroll-your-device-in-intune-mac-os-x)</br>
- [在 Intune 註冊 Windows 裝置](/intune/end-user/enroll-your-device-in-intune-windows)</br> 

另外還有[可下載的註冊指示集合](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a)，可用來建立自訂的使用者體驗指導方針。


### 請參閱

[Cisco 身分識別服務引擎系統管理員指南 2.1 版](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html#task_820C9C2A1A6647E995CA5AAB01E1CDEF)




<!--HONumber=Jun16_HO4-->

