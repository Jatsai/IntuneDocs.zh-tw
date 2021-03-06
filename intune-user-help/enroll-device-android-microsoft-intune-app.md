---
title: 使用 Microsoft Intune 應用程式註冊公司裝置 | Microsoft Docs
description: 描述如何在 Intune 中註冊公司 Android 裝置
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: b23323766e91e31c48aec6a51dfae971c3a333e8
ms.sourcegitcommit: 1dc9d4e1d906fab3fc46b291c67545cfa2231660
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735752"
---
# <a name="enroll-your-corporate-device-with-the-microsoft-intune-app"></a>使用 Microsoft Intune 應用程式註冊您的公司裝置

註冊您公司所擁有的 Android 裝置，以安全地存取公司電子郵件、應用程式及其他您組織開放使用的資料。 Microsoft Intune 應用程式支援執行 Android 6.0 及更新版本的公司擁有裝置。 它會在註冊期間，於新及恢復出廠預設值的裝置上自動安裝。 

目前有四種註冊方式。 您的組織應讓您了解要使用何種選項。
 
* 近距離無線通訊 (NFC)  
* 權杖  
* QR 代碼   
* Google Zero Touch  

## <a name="enroll-device"></a>註冊裝置 
完成這些步驟來設定及註冊您的裝置。  

> [!NOTE]
> Android 版本或裝置製造商可能會要求您完成此程序並未涵蓋的額外步驟。 您在螢幕擷取畫面中看到的色彩和文字，在您裝置上的顯示方式也可能會不同。  

1. 開啟新裝置或恢復出廠預設值之裝置的電源。  
2. 在 [歡迎使用]  畫面上選取您的語言。   若您收到指示，要求您使用 QR 代碼或 NFC 註冊，請遵循以下符合該方法的步驟。  
     * NFC：輕觸針對程式設計師裝置提供支援的 NFC 裝置，來連線到您組織的網路。 遵循畫面上的提示。 當您到達 Chrome 的服務條款畫面時，請繼續前往步驟 5。  

     * QR 代碼：完成 [QR 代碼註冊](#qr-code-enrollment)中的步驟。  

     若您收到指示，要求您使用另一種方法，請繼續前往步驟 3。    

1. 連線到 Wi-Fi 並點選 [下一步]  。 遵循符合您註冊方法的步驟。 

    * 權杖：當您到達 Google 登入畫面時，請完成[權杖註冊](#token-enrollment)中的步驟。    
    * Google Zero Touch：在您連線到 Wi-Fi 後，組織將會重新辨識您的裝置。 繼續前往步驟 4 並遵循畫面上的提示，直到安裝完成。    
 
       ![Google 條款畫面的範例影像 (若您使用 Google Zero Touch 的話)，其中已醒目提示 [接受並繼續] 按鈕。](./media/google-zero-touch-intune-app-01.png)   
   
4. 檢閱 Google 的條款。 然後點選 [接受並繼續]  。  

      ![Google 條款畫面的範例影像，其中已醒目提示 [接受並繼續] 按鈕。](./media/fully-managed-intune-app-04.png)   

6. 檢閱 Chrome 的服務條款。 然後點選 [接受並繼續]  。  

   ![Google 服務條款畫面的範例影像，其中已醒目提示 [接受並繼續] 按鈕。](./media/fully-managed-intune-app-06.png)   

7. 在登入畫面上，使用您的公司或學校帳戶登入。   

    a. 輸入您的電子郵件，然後點選 [下一步]  。      
    b. 輸入您的密碼，然後點選 [登入]  。  

8. 取決於您組織的需求，您可能會收到提示，要求您更新設定 (例如畫面鎖定或加密)。 若您看到這些提示，請點選 [設定]  並遵循畫面上的說明。  

   ![設定您公司電話畫面的範例影像，其中已醒目提示 [設定] 按鈕。](./media/fully-managed-intune-app-10.png)   

9. 若要在您的裝置上安裝公司應用程式，請點選 [安裝]  。 安裝完成後，請點選 [下一步]  。  

   ![設定您公司電話畫面的範例影像，其中已醒目提示 [安裝] 按鈕。](./media/fully-managed-intune-app-11.png)   

10. 當您收到訊息，顯示裝置已準備就緒時，請點選 [完成]  。 

11. 前往您的應用程式，並開啟 Microsoft Intune 應用程式。 選取 [登入]  。 

12. 在 [設定存取]  畫面上，您將會看到暫止的工作清單。 點選 [繼續]  。  

       ![Microsoft Intune 應用程式 [設定存取] 畫面的範例影像，顯示暫止的工作。](./media/fully-managed-intune-app-14.png)   

13. 當裝置註冊完成時，請點選 [繼續]  。 Microsoft Intune 可能會提示您更新其他裝置設定。   

       ![Microsoft Intune 應用程式 [更新裝置設定] 畫面的範例影像。](./media/fully-managed-intune-app-15-2.png)   

14. 當清單中的所有項目都顯示綠色圓形時，表示安裝已完成。 您現在可以存取公司的資源。  

       ![Microsoft Intune 應用程式 [設定存取] 畫面的範例影像，顯示完成的工作。](./media/fully-managed-intune-app-16.png)   


## <a name="qr-code-enrollment"></a>QR 代碼註冊  
在本節中，您將會掃描您公司提供的 QR 代碼。  當您完成時，我們會將您重新導向回裝置註冊步驟。     
  
1. 在 [歡迎]  畫面上，點選畫面五次來啟動 QR 代碼安裝。  

   ![裝置安裝 [歡迎] 畫面的範例影像，其中已醒目提示點選畫面的說明。](./media/qr-code-intune-app-01.png)  

2. 請遵循任何畫面上的說明，來連線到 Wi-Fi。  
3. 若您的裝置沒有 QR 代碼掃描器，則安裝畫面會顯示安裝掃描器的進度。 等待安裝完成。  
4. 出現提示時，請掃描組織給您的註冊設定檔 QR 代碼。  
5. 返回[註冊裝置](#enroll-device)的步驟 4 來繼續安裝。  

## <a name="token-enrollment"></a>權杖註冊  
在本節中，您將會輸入您公司提供的權杖。 當您完成時，我們會將您重新導向回裝置註冊步驟。  

1. 在 Google 登入畫面的 [電子郵件或電話]  方塊中，鍵入 **afw#setup**。 點選 [下一步]  。 

   ![Google 登入畫面的範例影像，其中顯示已在欄位中鍵入 "afw#setup"。](./media/token-intune-app-01.png)   

2. 針對 [Android 裝置原則]  應用程式選擇 [安裝]  。 繼續安裝。 取決於您的裝置，您可能需要檢閱及接受其他條款。    

3. 在 [註冊此裝置]  畫面上，選取 [下一步]  。  

   ![[註冊此裝置] 畫面的範例影像。 其中顯示 QR 代碼的插畫並醒目提示 [下一步] 按鈕。](./media/token-intune-app-02.png)  

4. 選取 [輸入代碼]  。

   ![使用中 QR 代碼掃描器的範例螢幕擷取畫面。 其中已醒目提示 [輸入代碼] 按鈕。](./media/token-intune-app-03.png)  

5. 在 [掃描或輸入代碼]  畫面上，鍵入組織給您的代碼。  然後按一下 [下一步]  。  

   ![[掃描或輸入代碼] 畫面的範例影像，其中已醒目提示 [下一步] 按鈕。](./media/token-intune-app-04.png)  

6. 返回[註冊裝置](#enroll-device)的步驟 4 來繼續安裝。  



## <a name="next-steps"></a>後續步驟   
是否仍需要協助？ 請連絡公司支援人員 (可查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)以取得連絡資訊)，或是撰寫電子郵件給 <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 小組</a>。  
