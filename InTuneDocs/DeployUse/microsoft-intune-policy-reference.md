---
# required metadata

title: Microsoft Intune 原則參考 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: d27f2739-9791-4aae-a9db-01a4e59ccfe5

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 原則參考

您可以使用本主題中的資訊，協助您決定您要用來管理裝置的 Microsoft Intune 原則。

> 如需如何使用原則的詳細資訊，請參閱[透過 Microsoft Intune 原則管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。


## Android 設定原則

|原則名稱|當您想要執行此作業時使用|
|---------------|------------------------|
|**自訂組態 (Android 4 和更新版本、Samsung KNOX Standard 4.0 和更新版本)**|部署 OMA URI 設定，例如可用來控制裝置功能的 Wi-Fi 設定。 當設定原則中您所需要的設定無法使用時，即可使用此方法。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune 的 Android 原則設定](android-policy-settings-in-microsoft-intune.md)|
|**電子郵件設定檔 (Samsung KNOX Standard 4.0 和更新版本)**|建立、部署及監視受管理裝置上的 Exchange ActiveSync 電子郵件設定。 如此一來，使用者無須進行任何設定，就能從其個人裝置上存取公司的電子郵件。<br /><br />如需詳細資訊，請參閱[使用電子郵件設定檔與 Microsoft Intune 來設定公司電子郵件存取權](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)|
|**一般組態 (Android 4 和更新版本、Samsung KNOX Standard 4.0 和更新版本)**|設定行動裝置的安全性及功能設定。<br />指定應用程式是否相容，並報告應用程式的使用時間。<br />設定 Kiosk 模式鎖定裝置，只讓某些特定功能運作。例如，允許裝置只執行一個應用程式或停用音量按鈕。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune 的 Android 原則設定](android-policy-settings-in-microsoft-intune.md)|
|**PKCS #12 (.PFX) 憑證設定檔 (Android 4 和更新版本)**|使用這個設定檔來為裝置憑證要求建立及部署 PFX 設定。<br /><br />如需詳細資訊，請參閱[使用 Microsoft Intune 中的憑證設定檔來保護資源存取](secure-resource-access-with-certificate-profiles.md)|
|**SCEP 憑證設定檔 (Android 4 和更新版本)**|設定可與受信任行動裝置憑證一起使用的簡單憑證註冊通訊協定憑證來驗證行動裝置，以便這些裝置能夠存取 Wi-Fi 及 VPN 設定檔所設定的網路資源。<br /><br />如需詳細資訊，請參閱[使用 Microsoft Intune 中的憑證設定檔來保護資源存取](secure-resource-access-with-certificate-profiles.md)|
|**受信任憑證設定檔 (Android 4 和更新版本)**|設定可用於驗證行動裝置的受信任行動裝置憑證，以允許這些裝置存取 Wi-Fi 及 VPN 設定檔所設定的網路資源。<br /><br />如需詳細資訊，請參閱[使用 Microsoft Intune 中的憑證設定檔來保護資源存取](secure-resource-access-with-certificate-profiles.md)|
|**VPN 設定檔 (Android 4 和更新版本)**|設定及部署設定，讓使用者可以從他們的行動裝置安全地存取公司網路。 透過部署這些設定，即可最小化連線到其工作所需的使用者工作。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune.md 中的 VPN 連線](vpn-connections-in-microsoft-intune.md)|
|**Wi-Fi 設定檔 (Android 4 和更新版本)**|為組織中的使用者設定及部署無線網路設定。 透過部署這些設定，即可最小化連線到無線網路所需的使用者工作。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune 中的 Wi-Fi 連線](wi-fi-connections-in-microsoft-intune.md)|

## iOS 設定原則

|原則名稱|當您想要執行此作業時使用|
|---------------|------------------------|
|**自訂組態 (iOS 7.1 和更新版本)**|將您使用 Apple Configuration 工具建立的組態設定檔，部署到 iOS 裝置。 當設定原則中您所需要的設定無法使用時，即可使用此方法。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune 的 iOS 原則設定](ios-policy-settings-in-microsoft-intune.md)|
|**電子郵件設定檔 (iOS 7.1 和更新版本)**|建立、部署及監視受管理裝置上的 Exchange ActiveSync 電子郵件設定。 如此一來，使用者無須進行任何設定，就能從其個人裝置上存取公司的電子郵件。<br /><br />如需詳細資訊，請參閱[使用電子郵件設定檔與 Microsoft Intune 來設定公司電子郵件存取權](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)|
|**一般組態 (iOS 7.1 和更新版本)**|設定行動裝置的安全性及功能設定。<br />-   指定應用程式是否相容，並報告應用程式的使用時間。<br />設定 Kiosk 模式鎖定裝置，只讓某些特定功能運作。例如，允許裝置只執行一個應用程式或停用音量按鈕。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune 的 iOS 原則設定](ios-policy-settings-in-microsoft-intune.md)|
|**SCEP 憑證設定檔 (iOS 7.1 和更新版本)**|設定可與受信任行動裝置憑證一起使用的簡單憑證註冊通訊協定憑證來驗證行動裝置，以便這些裝置能夠存取 Wi-Fi 及 VPN 設定檔所設定的網路資源。<br /><br />如需詳細資訊，請參閱[使用 Microsoft Intune 中的憑證設定檔來保護資源存取](secure-resource-access-with-certificate-profiles.md)|
|**受信任憑證設定檔 (iOS 7.1 和更新版本)**|設定可用於驗證行動裝置的受信任行動裝置憑證，以允許這些裝置存取 Wi-Fi 及 VPN 設定檔所設定的網路資源。<br /><br />如需詳細資訊，請參閱[使用 Microsoft Intune 中的憑證設定檔來保護資源存取](secure-resource-access-with-certificate-profiles.md)|
|**VPN 設定檔 (iOS 7.1 和更新版本)**|設定及部署設定，讓使用者可以從他們的行動裝置安全地存取公司網路。 透過部署這些設定，即可最小化連線到其工作所需的使用者工作。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune.md 中的 VPN 連線](vpn-connections-in-microsoft-intune.md)|
|**Wi-Fi 設定檔 (iOS 7.1 和更新版本)**|為組織中的使用者設定及部署無線網路設定。 透過部署這些設定，即可最小化連線到無線網路所需的使用者工作。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune 中的 Wi-Fi 連線](wi-fi-connections-in-microsoft-intune.md)|
|**行動應用程式組態原則 (iOS 7.1 及更新版本)**|使用行動裝置應用程式組態原則來自動提供使用者執行 iOS 應用程式時可能需要的設定。<br /><br />如需詳細資訊，請參閱[在 Microsoft Intune 中使用行動應用程式組態原則設定 iOS 應用程式](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md)|

## Mac OS X 設定原則

|原則名稱|當您想要執行此作業時使用|
|---------------|------------------------|
|**自訂設定 (Mac OS X 10.9 及更新版本)**|將您使用 Apple Configuration 工具建立的組態設定檔，部署到 Mac 電腦。 當設定原則中您所需要的設定無法使用時，即可使用此方法。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune 的 Mac OS X 原則設定](mac-os-x-policy-settings-in-microsoft-intune.md)|
|**一般設定 (Mac OS X 10.9 及更新版本)**|設定行動裝置的安全性及功能設定。<br />指定應用程式是否相容，並報告應用程式的使用時間。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune 的 Mac OS X 原則設定](mac-os-x-policy-settings-in-microsoft-intune.md)|
|**SCEP 憑證設定檔 (Mac OS X 10.9 及更新版本)**|設定可與受信任行動裝置憑證一起使用的簡單憑證註冊通訊協定憑證來驗證行動裝置，以便這些裝置能夠存取 Wi-Fi 及 VPN 設定檔所設定的網路資源。<br /><br />如需詳細資訊，請參閱[使用 Microsoft Intune 中的憑證設定檔來保護資源存取](secure-resource-access-with-certificate-profiles.md)|
|**信任的憑證設定檔 (Mac OS X 10.9 及更新版本)**|設定可用於驗證行動裝置的受信任行動裝置憑證，以允許這些裝置存取 Wi-Fi 及 VPN 設定檔所設定的網路資源。<br /><br />如需詳細資訊，請參閱[使用 Microsoft Intune 中的憑證設定檔來保護資源存取](secure-resource-access-with-certificate-profiles.md)|
|**VPN 設定檔 (Mac OS X 10.9 及更新版本)**|設定及部署設定，讓使用者可以從他們的行動裝置安全地存取公司網路。 透過部署這些設定，即可最小化連線到其工作所需的使用者工作。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune.md 中的 VPN 連線](vpn-connections-in-microsoft-intune.md)|
|**Wi-Fi 設定檔 (Mac OS X 10.9 及更新版本)**|為組織中的使用者設定及部署無線網路設定。 透過部署這些設定，即可最小化連線到無線網路所需的使用者工作。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune 中的 Wi-Fi 連線](wi-fi-connections-in-microsoft-intune.md)|

## Windows 設定原則
僅適用於 Windows Phone 及已經註冊的 Windows 裝置。

|原則名稱|當您想要執行此作業時使用|
|---------------|------------------------|
|**自訂組態 (Windows 10 Desktop/行動裝置版和更新版本)**|部署可以用來控制裝置功能的 OMA URI 設定。 當設定原則中您所需要的設定無法使用時，即可使用此方法。<br />    如需詳細資訊，請參閱 [Microsoft Intune 的 Windows 10 原則設定](windows-10-policy-settings-in-microsoft-intune.md)|
|**自訂組態 (Windows Phone 8.1 和更新版本)**|部署可以用來控制裝置功能的 OMA URI 設定。 當設定原則中您所需要的設定無法使用時，即可使用此方法。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune 的 Windows Phone 8.1 原則設定](windows-phone-8-1-policy-settings-in-microsoft-intune.md)|
|**版本升級原則 (Windows 10 Desktop 和更新版本)**<br><br>**版本升級原則 (Windows 10 Holographic 和更新版本)**|設定及部署內含可用來將 Windows 10 裝置更新為較新版本之授權或產品金鑰資訊的原則<br><br>如需詳細資訊，請參閱 [Microsoft Intune 的版本升級原則設定](edition-upgrade-policy-settings-in-microsoft-intune.md)|  
|**電子郵件設定檔 (Windows Phone 8 和更新版本)**<br /><br />**電子郵件設定檔 (Windows 10 Desktop/行動裝置版及更新版本)**|建立、部署及監視受管理裝置上的 Exchange ActiveSync 電子郵件設定。 如此一來，使用者無須進行任何設定，就能從其個人裝置上存取公司的電子郵件。<br /><br />如需詳細資訊，請參閱[使用電子郵件設定檔與 Microsoft Intune 來設定公司電子郵件存取權](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)|
|**一般組態 (Windows 10 Desktop/行動裝置版和更新版本)**|為已經註冊的 Windows 10 Desktop 和行動裝置版裝置設定行動裝置的安全性及功能設定。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune 的 Windows 10 原則設定](windows-10-policy-settings-in-microsoft-intune.md)|
|**一般設定 (Windows 10 團隊版及更新版本)**|為已註冊的 Windows 10 團隊版裝置 (例如 Surface Hub 裝置) 設定裝置安全性及功能設定。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune 的 Windows 團隊版組態原則設定](windows-team-configuration-policy-settings-in-microsoft-intune.md)|
|**一般組態 (Windows 8.1 和更新版本)**|為已經註冊的 Windows 裝置設定行動裝置的安全性及功能設定。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune 的 Windows 原則設定](windows-configuration-policy-settings-in-microsoft-intune.md)|
|**一般組態 (Windows Phone 8.1 和更新版本)**|設定行動裝置的安全性及功能設定。<br />指定使用者可以或不得使用的應用程式，也可封鎖安裝或使用不相容的應用程式。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune 的 Windows Phone 8.1 原則設定](windows-phone-8-1-policy-settings-in-microsoft-intune.md)|
|**PKCS #12 (.PFX) 憑證設定檔 (Windows 10 Desktop/行動裝置版和更新版本)**|使用這個設定檔來為裝置憑證要求建立及部署 PFX 設定。<br /><br />如需詳細資訊，請參閱[使用 Microsoft Intune 中的憑證設定檔來保護資源存取](secure-resource-access-with-certificate-profiles.md)|
|**SCEP 憑證設定檔 (Windows 8.1 和更新版本)**<br /><br />**SCEP 憑證設定檔 (Windows Phone 8.1 和更新版本)**|設定可與受信任行動裝置憑證一起使用的簡單憑證註冊通訊協定憑證來驗證行動裝置，以便這些裝置能夠存取 Wi-Fi 及 VPN 設定檔所設定的網路資源。<br /><br />如需詳細資訊，請參閱[使用 Microsoft Intune 中的憑證設定檔來保護資源存取](secure-resource-access-with-certificate-profiles.md)|
|**受信任憑證設定檔 (Windows 8.1 和更新版本)**<br /><br />**受信任憑證設定檔 (Windows Phone 8.1 和更新版本)**|設定可用於驗證行動裝置的受信任行動裝置憑證，以允許這些裝置存取 Wi-Fi 及 VPN 設定檔所設定的網路資源。<br /><br />如需詳細資訊，請參閱[使用 Microsoft Intune 中的憑證設定檔來保護資源存取](secure-resource-access-with-certificate-profiles.md)|
|**VPN 設定檔 (Windows 10 Desktop/行動裝置版和更新版本)**<br /><br />**VPN 設定檔 (Windows 8.1 和更新版本)**<br /><br />**VPN 設定檔 (Windows Phone 8.1 和更新版本)**|設定及部署設定，讓使用者可以從他們的行動裝置安全地存取公司網路。 透過部署這些設定，即可最小化連線到其工作所需的使用者工作。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune.md 中的 VPN 連線](vpn-connections-in-microsoft-intune.md)|
|**Wi-Fi 匯入**|匯入和部署您之前匯出至檔案的 Windows Wi-Fi 組態。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune 中的 Wi-Fi 連線](wi-fi-connections-in-microsoft-intune.md)|

## 軟體原則

|原則名稱|當您想要執行此作業時使用|
|---------------|------------------------|
|**受管理瀏覽器原則 (Android 4 及更新版本)**<br /><br />**受管理的瀏覽器原則 (iOS 7.1 及更新版本)**|指定使用者在使用受管理瀏覽器應用程式時，可以及不得存取的網站。<br /><br />如需詳細資訊，請參閱[透過 Microsoft Intune 使用受管理的瀏覽器原則管理網際網路存取](manage-internet-access-using-managed-browser-policies.md)|
|**行動應用程式管理原則 (Android 4 及更新版本)**<br /><br />**行動應用程式管理原則 (iOS 7.1 及更新版本)**|修改您部署之應用程式的功能，讓這些應用程式能夠符合公司的規範及安全性原則。 例如，您可以限制受限應用程式中的剪下、複製及貼上作業，或將應用程式設定成只能在受管理瀏覽器中開啟所有的網頁連結。<br /><br />如需詳細資訊，請參閱[在 Microsoft Intune 主控台中設定及部署行動應用程式管理原則](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)|

## 一般行動裝置設定

|原則名稱|當您想要執行此作業時使用|
|---------------|------------------------|
|**Exchange ActiveSync 原則**|為 Exchange ActiveSync 所管理的裝置，設定行動裝置的安全性及功能設定。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune 的 Exchange ActiveSync 原則設定](exchange-activesync-policy-settings-in-microsoft-intune.md)|
|**行動裝置安全性原則**|<ul><li>設定行動裝置 (所有平台) 的設定，包括：<br /><br /><ul><li>安全性</li><li>加密</li><li>系統</li><li>電子郵件</li><li>應用程式</li></ul></li></ul> 重要事項：Microsoft Intune 現已針對不同的裝置平台，設置個別的組態原則，而這些原則全都包含最新的設定可供您使用。 您可以繼續使用行動裝置安全性原則，現有的部署也還能運作，但您應及早規劃改用新的設定原則。<br />如需詳細資訊，請參閱 [Microsoft Intune 的行動裝置安全性原則設定](mobile-device-security-policy-settings-in-microsoft-intune.md)|

## 條件式存取與相容性原則

### 條件式存取

|原則名稱|當您想要執行此作業時使用|
|---------------|------------------------|
|**Exchange Online 原則**<br /><br />**Exchange 內部部署原則**|管理自未由 Intune 管理或與您建立之相容性原則不相容的裝置對 Microsoft Exchange 電子郵件的存取。<br /><br />如需詳細資訊，請參閱[使用 Intune 限制 Exchange Online 和新版 Exchange Online Dedicated 環境的電子郵件存取](restrict-access-to-exchange-online-with-microsoft-intune.md)|
|**SharePoint Online 原則**|管理自未由 Intune 管理或與您建立之相容性原則不相容的裝置對 SharePoint Online 的存取。<br /><br />如需詳細資訊，請參閱[使用 Microsoft Intune 限制存取 SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)|
|**商務用 Skype**|管理自未由 Intune 管理或與您建立之相容性原則不相容的裝置對商務用 Skype 的存取。<br /><br />如需詳細資訊，請參閱[使用 Microsoft Intune 限制存取商務用 Skype](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)|
> [!NOTE]
> 您不應部署條件式存取原則給使用者與裝置， 而應設定必要的原則，並將其套用到原則鎖定的所有群組。

### 相容性原則

|原則名稱|當您想要執行此作業時使用|
|---------------|------------------------|
|**相容性原則**|定義裝置的相容性層級，然後報告不相容的裝置。 這些原則會與條件式存取搭配使用，以協助您評估應封鎖哪些裝置存取服務。<br /><br />如需詳細資訊，請參閱 [Microsoft Intune 的裝置相容性原則](introduction-to-device-compliance-policies-in-microsoft-intune.md)|

## Windows 電腦管理

|原則名稱|當您想要執行此作業時使用|
|---------------|------------------------|
|**Microsoft Intune 代理程式設定**|設定電腦上的 Intune PC 用戶端，包括下列項目的設定：<br /><br />-   Endpoint Protection<br />-   軟體更新<br />-   原則檢查排程<br /><br />這類型的原則只能部署到裝置群組。<br /><br />Intune 用戶端可根據 [更新和應用程式偵測頻率] 設定下載新的和更新的原則，預設為 8 小時。 不過，您可以隨時在電腦上強制重新整理原則。<br /><br />如需詳細資訊，請參閱[在 Microsoft Intune 中使用軟體更新讓 Windows 電腦維持最新狀態](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)|
|**Microsoft Intune Center 設定**|設定要出現在受管理電腦上之 Microsoft Intune 中心中的詳細資料。<br /><br />這類型的原則只能部署到裝置群組。<br /><br />如需詳細資訊，請參閱[使用 Microsoft Intune 電腦用戶端的一般 Windows 電腦管理工作](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)|
|**Windows 防火牆設定**|設定電腦上一般網路通訊的 Windows 防火牆設定和例外，包括：<br /><br />-   BranchCache<br />-   遠端協助<br />-   媒體共用<br /><br />這類型的原則只能部署到裝置群組。<br /><br />如需詳細資訊，請參閱[使用 Microsoft Intune 的 Endpoint Protection 協助保護 Windows 電腦](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)|

### 另請參閱

[透過 Microsoft Intune 原則管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO2-->

