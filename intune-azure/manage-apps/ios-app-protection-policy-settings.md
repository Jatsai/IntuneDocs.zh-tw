---
title: "iOS 應用程式保護原則設定"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰本主題說明 iOS 裝置的應用程式保護原則設定。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f8b08f2-504c-4b38-bea2-b8a4ef0526b8
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: a391f9e16faf315c5fb88191f3de3f8f2f3d5178
ms.lasthandoff: 02/18/2017


---

#  <a name="ios-app-protection-policy-settings"></a>iOS 應用程式保護原則設定
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

您可為 Azure 入口網站中 [設定] 刀鋒視窗上的應用程式保護原則，[設定](app-protection-policies.md)本主題內所述的原則設定。

原則設定分為「資料重新配置」和「存取」設定兩類。 在本主題中 [受原則管理的應用程式] 一詞是指設有應用程式保護原則的應用程式。

##  <a name="data-relocation-settings"></a>資料重新配置設定

| 設定 | 如何使用 | 預設值 |
|------|------|------|
| **禁止 iTunes 和 iCloud 備份** | 選擇 [是]，防止這個應用程式將工作或學校資料備份至 iTunes 和 iCloud。 選擇 [否]，允許這個應用程式將工作或學校資料備份至 iTunes 和 iCloud。| 是 |
| **允許應用程式將資料傳送到其他應用程式** | 指定可以接收這個應用程式資料的應用程式： <ul><li> **受原則管理的應用程式**：只允許傳送至其他受原則管理的應用程式。</li> <li>**所有應用程式**：允許傳送到任何應用程式。 </li> <li>**無**：不允許將資料傳送到任何應用程式 (包括其他受原則管理的應用程式)。</li></ul> 此外，如果這個選項設定為 [受原則管理的應用程式] 或 [無]，則會封鎖允許焦點搜尋在應用程式中搜尋資料的 iOS 9 功能。 <br><br> 有一些 Intune 可以允許資料傳輸至其中的豁免應用程式和服務。 如需應用程式和服務的完整清單，請參閱[資料傳輸豁免](#Data-transfer-exemptions)。 | 所有應用程式 |
| **允許應用程式接收來自其他應用程式的資料** | 指定可將資料傳送至這個應用程式的應用程式： <ul><li>**受原則管理的應用程式**：只允許從其他受原則管理的應用程式傳送。</li><li>**所有應用程式**：允許從任何應用程式傳送資料。</li><li>**無**：不允許從任何應用程式 (包括其他受原則管理的應用程式) 傳送資料。 </li></ul> <p>  有一些 Intune 可以允許從中進行資料傳輸的豁免應用程式和服務。 如需應用程式和服務的完整清單，請參閱[資料傳輸豁免](#Data-transfer-exemptions)。 | 所有應用程式 |
| **不可進行另存新檔** | 選擇 [是]，在這個應用程式中停用 [另存新檔] 選項。 如果您想要允許使用 [另存新檔]，請選擇 [否]。 | 否 |
| **限制與其他應用程式的剪下、複製和貼上** | 指定何時剪下、複製和貼上動作可與這個應用程式搭配使用。 從下列選項進行選擇： <ul><li>**封鎖**：不允許在這個應用程式與任何其他應用程式之間進行剪下、複製和貼上動作。</li><li>**受原則管理的應用程式**：允許在這個應用程式與其他受原則管理的應用程式之間進行剪下、複製和貼上動作。</li><li>**具有貼上的受原則管理的應用程式**：允許在這個應用程式與其他受原則管理的應用程式之間進行剪下或複製。 允許將資料從任何應用程式貼入這個應用程式。</li><li>**任何應用程式**：不限制與這個應用程式之間的剪下、複製和貼上。 | 任何應用程式 |
|**限制 Web 內容以顯示於受管理的瀏覽器中** | 選擇 [是]，強制在 Managed Browser 應用程式中開啟應用程式中的網頁連結。 <br><br> 針對未在 Intune 中註冊的裝置，受原則管理應用程式中的網頁連結只能在 Managed Browser 應用程式中開啟。 <br><br> 如果您使用 Intune 管理裝置，請參閱[透過 Microsoft Intune 使用受管理的瀏覽器原則管理網際網路存取](https://docs.microsoft.com/en-us/intune/deploy-use/manage-internet-access-using-managed-browser-policies)。 | 否 |
| **加密應用程式資料** | 針對受原則管理的應用程式，使用 iOS 所提供的裝置層級加密配置來加密待用資料。 需要 PIN 時，會根據應用程式保護原則中的設定來加密資料。 <br><br> 前往[這裡](https://support.apple.com/HT202739)的正式 Apple 文件，來查看哪些 iOS 加密模組已經 FIPS 140-2 認證或擱置 FIPS 140-2 認證。 <br><br> 指定何時加密這個應用程式中的工作或學校資料。 從下列選項進行選擇： <ul><li>**鎖定裝置時**：鎖定裝置時，會加密與這個原則相關聯的所有應用程式資料。</li><li>**當裝置鎖定時且有開啟的檔案**：鎖定裝置時，除了在應用程式中目前開啟的檔案資料以外，會加密與這個原則相關聯的其他所有應用程式資料。</li><li>**裝置重新啟動後**：重新啟動裝置後，與這項原則相關聯的所有應用程式資料都會經過加密，直到第一次解除鎖定裝置為止。</li><li>**使用裝置設定**：應用程式資料會根據裝置上的預設設定加密。 當您啟用這項設定時，使用者必須設定並使用 PIN 才能存取其裝置。  如果沒有 PIN，將不會開啟應用程式，而且會出現下列訊息提示使用者設定 PIN：「您的組織要求您先啟用裝置 PIN，才能存取此應用程式」。 </li></ul> | 當裝置鎖住時 |
| **停用連絡人同步** | 選擇 [是]，防止應用程式將資料儲存至裝置上的原生「連絡人」應用程式。 如果您選擇 [否]，則應用程式可以將資料儲存至裝置上的原生「連絡人」應用程式。 <br><br>當您執行選擇性抹除以移除應用程式中的工作或學校資料時，會移除直接從應用程式同步到原生「連絡人」應用程式的連絡人。 無法清除從原生通訊錄同步處理到其他外部來源的任何連絡人。 目前這僅適用於 Microsoft Outlook 應用程式。 | 否 |
| **停用列印** | 選擇 [是]，防止應用程式列印工作或學校資料。 | 否 |


> [!NOTE]
> 沒有資料重新配置設定可以控制 iOS 裝置上的 Apple 受管理「開啟於」功能。 若要使用管理 Apple「開啟於」，請參閱[使用 Microsoft Intune 管理 iOS 應用程式之間的資料傳輸](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)。

## <a name="data-transfer-exemptions"></a>資料傳輸豁免

在特定情況下，有一些 Intune 應用程式保護原則可以允許豁免應用程式和平台服務傳送和接收資料傳輸。 這份清單可能隨時變更，並反映視為對安全產能有所幫助的服務和應用程式。

| 應用程式/服務名稱 | 說明 |
| ---- | --- |
|tel; telprompt | 原生 Phone 應用程式 |
| skype | Skype |
| app-settings | 裝置設定 |
| itms; itmss; itms-apps; itms-appss; itms-services | App Store |
| calshow | 原生行事曆 |


## <a name="access-settings"></a>存取設定

| 設定 | 如何使用 | 預設值 |
|------|------|------|
| **需要 PIN 碼才可存取** | 選擇 [是]，需要 PIN 才能使用這個應用程式。 使用者第一次在工作或學校內容中執行應用程式時，系統會提示他們設定這個 PIN。 預設值 = [是]。<br><br> 進行下列 PIN 強度設定： <ul><li>**PIN 碼重設前的嘗試次數**：指定使用者必須嘗試順利輸入幾次其 PIN 後才能重設 PIN。 預設值 = **5**。</li><li> **允許簡單的 PIN**：選擇 [是]，允許使用者使用簡單的 PIN 序列 (例如 1234 或 1111)。 選擇 [否]，防止其使用簡單的序號。 預設值 = [是]。 </li><li> **PIN 長度**：指定 PIN 序列的最小位數。 預設值 = **4**。 </li><li> **允許指紋而非 PIN (iOS 8.0+)**：選擇 [是]，讓使用者對應用程式存取使用 [Touch ID](https://support.apple.com/en-us/HT201371)，而非 PIN。 預設值 = [是]。</li></ul> 在 iOS 裝置上，您可以讓使用者使用 [Touch ID](https://support.apple.com/en-us/HT201371) 而非 PIN 來證明其身分識別。 使用者嘗試使用自己的工作或學校帳戶來使用這個應用程式時，系統會提示他們提供自己的指紋識別，而不是輸入 PIN。 </li></ul>| 需要 PIN 碼：是 <br><br> PIN 碼重設嘗試次數：5 <br><br> 允許簡單的 PIN：是 <br><br> PIN 長度：4 <br><br> 允許指紋：是 |
| **需要公司認證才能存取** | 選擇 [是]，需要使用者使用工作或學校帳戶登入來進行應用程式存取，而不是輸入 PIN。 如果您設定為 [是]，則會覆寫 PIN 或 Touch ID 的需求。  | 否 |
| **封鎖在已進行 JB 或 Root 破解的裝置上執行受管理的應用程式** |  選擇 [是]，防止在已進行 JB 或 Root 破解的裝置上執行這個應用程式。 使用者仍然可以繼續使用這個應用程式來執行個人工作，但必須使用不同的裝置來存取這個應用程式中的工作或學校資料。 | 是 |
| **重新檢查存取需求前等候時間 (分鐘)** | 進行以下設定： <ul><li>**逾時**：指定經過多少時間 (分鐘) 之後即會重新檢查應用程式存取需求。 預設值 = **30** 分鐘。</li><li>**離線寬限期**：如果裝置已離線，指定經過多少時間 (分鐘) 之後即會重新檢查應用程式存取需求。 預設值 = **720** 分鐘 (12 小時)。</li></ul>| 逾時：30 <br><br> 離線：720 |
| **離線間隔幾天後抹除 App 資料** | 如果裝置已離線超過一段期間，即可抹除這個應用程式中的工作或學校資料。 指定裝置可以離線的天數，在這之後會從裝置移除工作或學校資料。 <br><br> | 90 天 |

##  <a name="add-ins-for-outlook-app"></a>Outlook 應用程式增益集

Outlook 最近為 iOS 版 Outlook 推出了增益集，您可將熱門的應用程式與電子郵件用戶端相整合。 Web、Windows、Mac 和 iOS 版的 Outlook，皆提供 Outlook 增益集。 因為增益集透過 Microsoft Exchange 進行管理，所以除非使用者的 Exchange 對使用者關閉了增益集，否則，使用者將可在 Outlook 與未受管理的增益集應用程式之間，共用資料與郵件。

若想要停止讓使用者無法存取及安裝 Outlook 增益集 (如此會影響所有 Outlook 用戶端)，請務必在 Exchange 系統管理中心對角色進行下列變更︰

- 為避免使用者安裝 Office 市集增益集，請移除使用者的「我的市集」角色。
- 為避免使用者側載增益集，請移除使用者的「我的自訂應用程式」角色。
- 為避免使用者安裝所有增益集，請移除使用者的「我的自訂應用程式」與「我的市集」角色。

這些指示適用於 Office 365、Exchange 2016、Exchange 2013 (跨 Web、Windows、Mac 與行動裝置上的 Outlook)。

- 深入了解[適用於 Outlook 的增益集](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx)。
- 深入了解 [How to specify the administrators and users who can install and manage add-ins for Outlook app](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx) (如何指定可安裝及管理 Outlook 應用程式增益集的系統管理員與使用者)。
