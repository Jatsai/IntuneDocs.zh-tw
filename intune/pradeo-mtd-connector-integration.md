---
title: 設定 Pradeo 與 Intune 的整合
titleSuffix: Intune on Azure
description: Pradeo 連接器與 Intune 的整合
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 06/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 82872ba6-80f8-4cc9-adf4-0ccd8ff26dd2
ms.openlocfilehash: 223161bd12f40b3539ce2502599eb3324c7458ca
ms.sourcegitcommit: f70d6aaea59b52cd0d7bd3008afd243868967fd6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2018
ms.locfileid: "37067430"
---
# <a name="integrate-pradeo-with-intune"></a>整合 Pradeo 與 Intune

完成下列步驟以將 Pradeo Mobile Threat Defense 解決方案與 Intune 整合。

## <a name="before-you-begin"></a>開始之前

> [!NOTE]
> 下列步驟必須在 [Pradeo Security 主控台](https://www.apps-security.com)中完成。

開始將 Pradeo 與 Intune 整合之前，請確定您有下列項目：

-   Microsoft Intune 訂閱

-   可授與下列權限的 Azure Active Directory 管理員認證：

    -   登入及讀取使用者設定檔

    -   以登入的使用者身分存取目錄

    -   讀取目錄資料

    -   將裝置資訊傳送至 Intune

-   用來存取 Pradeo Security 主控台的系統管理員認證。

### <a name="pradeo-app-authorization"></a>Pradeo 應用程式授權

Pradeo 應用程式授權程序如下：

-   允許 Pradeo 服務將裝置健全狀況狀態的相關資訊傳送回 Intune。

-   將 Pradeo 與 Azure AD 註冊群組成員資格同步，以填入其裝置的資料庫。

-   允許 Pradeo 管理主控台使用 Azure AD 單一登入 (SSO)。

-   允許 Pradeo 應用程式使用 Azure AD SSO 登入。

## <a name="to-set-up-pradeo-integration"></a>設定 Pradeo 整合

1.  請前往 [Pradeo Security 主控台](https://www.apps-security.com)，並使用您的認證登入。

2.  從功能表選擇 [Administration - Enterprise Mobility Management] \(管理 - Enterprise Mobility 管理\)。

3.  選擇 **Intune 標誌**。

4.  在 [EMM (Enterprise mobility management) - Intune] \(EMM (Enterprise Mobility 管理) - Intune\) 視窗中的 [Step 1] \(步驟 1\) 下，選擇 [Pradeo Connector] \(Pradeo 連接器\) 按鈕。 

    ![Pradeo EMM Intune 視窗](./media/pradeo_setup.png)

5. 在 Microsoft Intune 連線視窗中，輸入您的 Intune 認證。

5.  Pradeo 網頁會重新開啟。 在 [Step 2] \(步驟 2\) 下，選擇 [Pradeo Device Health] \(Pradeo 裝置健康情況\) 按鈕。

7. 在 Pradeo-Intune 連接器視窗中，選取 [Accept] \(接受\)。 

8. 在 Pradeo 裝置 API 連接器視窗中，選取 [Accept] \(接受\)。

9. Pradeo 網頁會重新開啟。 在 [Step 3] \(步驟 3\) 下，選擇 [Connect to Microsoft] \(連線到 Microsoft\) 按鈕。 

10. 在 Microsoft Intune 驗證視窗中，輸入您的 Intune 認證。

11. 出現 [Successful Integration] \(成功整合\) 訊息時，整合即完成。

## <a name="next-steps"></a>接下來的步驟

-   [設定 Pradeo 應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)