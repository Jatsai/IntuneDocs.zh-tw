---
title: "設定 Windows 10 行動裝置版和 Windows Phone 管理 | Microsoft Intune"
description: "啟用適用於使用 Microsoft Itune 之 Windows 10 行動裝置版或 Windows Phone 裝置的行動裝置管理 (MDM)。"
keywords: 
author: staciebarker
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c59707ba2967b069dc30aee71d2642e91d71b23b
ms.openlocfilehash: 3141d4b2ad1a21e2ac5ba7b6cafb74f567d07f7a


---


# <a name="set-up-windows-phone-and-windows-10-mobile-management-with-microsoft-intune"></a>使用 Microsoft Intune 設定 Windows Phone 和 Windows 10 行動裝置版管理

Intune 系統管理員有兩種方式可為 Windows 10 行動裝置版與 Windows Phone 裝置啟用註冊與管理：

- **[使用 Azure Active Directory 自動註冊](#azure-active-directory-enrollment)** - Windows 10 與 Windows 10 行動裝置版使用者將工作或學校帳戶新增至裝置，即可註冊裝置
- **[公司入口網站註冊](#company-portal-app-enrollment)** - Windows Phone 8.1 和更新版本使用者註冊其裝置的方法為下載並安裝公司入口網站應用程式，然後在應用程式中輸入其工作或學校帳戶認證。


[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="company-portal-app-enrollment"></a>公司入口網站應用程式註冊
您可以讓使用者使用 Intune 公司入口網站應用程式安裝並註冊其裝置。 如果您建立 DNS CNAME 資源記錄，使用者會連線並註冊 Intune，而不需要輸入伺服器名稱。

1.  **設定 Intune**<br>如果尚未這麼做，請將[行動裝置管理 (MDM) 授權單位](prerequisites-for-enrollment.md#step-2-set-mdm-authority)設定為 **Microsoft Intune**，然後設定 MDM，為行動裝置管理做好準備。

2.  **建立 CNAME** (選用)<br>建立公司網域的 **CNAME** DNS 資源記錄。 例如，假設公司網站為 contoso.com，您就必須在 DNS 中建立 CNAME，將 EnterpriseEnrollment.contoso.com 重新導向 enterpriseenrollment-s.manage.microsoft.com。

    雖然建立 CNAME DNS 項目為選擇性作業，但是 CNAME 記錄可讓使用者更輕鬆地註冊。 如果找不到任何註冊 CNAME 記錄，系統會提示使用者手動輸入 MDM 伺服器名稱 https://manage.microsoft.com。

    如果您目前在 DNS 中有 CNAME，它會將EnterpriseEnrollment.contoso.com 重新導向到 manage.microsoft.com，我們建議您在 DNS 中將它取代為把 EnterpriseEnrollment.contoso.com 重新導向到 enterpriseenrollment-s.manage.microsoft.com 的 CNAME。 建議進行這項變更，因為 manage.microsoft.com 端點即將取代為未來版本中的註冊。

    如果已驗證的網域不止一個，請為每個網域建立一筆 CNAME 記錄。 CNAME 資源記錄必須包含下列資訊：

  |類型|主機名稱|指向|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 小時|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小時|

  `EnterpriseEnrollment-s.manage.microsoft.com` – 支援從電子郵件的網域名稱辨識網域，重新導向至 Intune 服務

  `EnterpriseRegistration.windows.net` - 支援將使用工作或學校帳戶向 Azure Active Directory 註冊的 Windows 8.1 和 Windows 10 行動裝置版裝置

  如果您的公司對使用者認證使用多個網域，請為每個網域建立 CNAME 記錄。

  例如，假設公司網站為 contoso.com，您就必須在 DNS 中建立 CNAME，將 EnterpriseEnrollment.contoso.com 重新導向 EnterpriseEnrollment-s.manage.microsoft.com。 DNS 記錄變更可能需要 72 小時才會傳播完成。 在 DNS 記錄傳播完成之前，您無法在 Intune 中驗證 DNS 變更。

3.  **驗證 CNAME**<br>在 [Intune 管理主控台](http://manage.microsoft.com)中，選擇 [管理] &gt; [行動裝置管理] &gt; [Windows Phone]。 在 [指定已驗證的網域名稱] 方塊中輸入公司網站中已驗證網域的 URL，然後選擇 [測試自動偵測]。

    ![設定 Windows 的行動裝置管理對話方塊](../media/windows-phone-enrollment.png)

4.  **選擇性步驟**<br>Windows 10 不需要**新增側載金鑰**步驟。 只有在您將無法在 Windows 市集使用的企業營運 (LOB) 應用程式散發到裝置時，才需要**上傳程式碼簽署憑證**步驟。

5.  **告訴使用者如何註冊其裝置來存取公司資源。**

    如需使用者註冊指示，請參閱[在 Intune 註冊 Windows 裝置](../enduser/enroll-your-device-in-intune-windows.md)。 您也可以讓使用者前往[當您在 Intune 註冊您的裝置時，您的 IT 系統管理員會看到什麼內容？](../enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md)

    如需其他使用者工作的資訊，請參閱下列文章：
    - [要告訴使用者之關於使用 Microsoft Intune 的事項](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [適用於 Windows 裝置的使用者指南](../enduser/using-your-windows-device-with-intune.md)

除非您要將公司入口網站部署至裝置，否則不需要進行任何額外的工作。  在管理主控台中可以放心略過步驟 2 和 3。



<!--HONumber=Dec16_HO2-->

