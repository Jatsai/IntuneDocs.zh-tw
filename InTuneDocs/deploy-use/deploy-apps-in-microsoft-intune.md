---
title: "如何部署應用程式 | Microsoft Intune"
description: "使用本主題中的資訊以協助您透過 Microsoft Intune 部署應用程式。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b42019e-73da-4538-a496-212f11d5bf9b
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d73df65a36b348f0941b1e7889d083406bc082f9
ms.openlocfilehash: b13d1a6a1a0f995b1169fabd09a2f0a4cf9b630d

---
# <a name="deploy-apps-in-microsoft-intune"></a>在 Microsoft Intune 中部署應用程式

使用本主題中的資訊以協助您透過 Microsoft Intune 部署應用程式。


## <a name="deploy-an-app"></a>部署應用程式
在這個程序中，您會將應用程式部署到選取的裝置或使用者群組。

### <a name="to-deploy-an-app"></a>部署應用程式

1. 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，按一下 **[應用程式]** &gt; **[應用程式]**，以檢視您管理的應用程式清單。

2.  選取您要部署的應用程式，然後按一下 **[管理部署]**。

3.  在 *&lt;[應用程式名稱]&gt;* 對話方塊中，從 **[選取群組]** 頁面選擇您要部署應用程式的使用者或裝置群組。

4.  在 [部署動作] 頁面上，設定下列項目：

    - **核淮** - 選擇部署為：
        - **必要** (強制安裝)
        - **可用** (使用者視需要從公司入口網站進行安裝)
        - **不適用** (應用程式不會安裝，也不會顯示在公司入口網站中)
        - **解除安裝** (應用程式會從目標裝置解除安裝)
    - **期限** - 若為必要安裝，請選擇部署應用程式的期限。 您可以從預先定義的值當中進行選取，或者選取 **[自訂]** 來設定您自己的期限。

5. 如果您要部署的應用程式可以透過行動應用程式管理原則進行設定，則會顯示 [行動應用程式管理] 頁面。 在這個頁面上，選取您要與這個應用程式建立關聯的行動應用程式管理原則。

    [查看哪些 Microsoft 應用程式與行動應用程式管理原則相容。](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)

6. 如果您要部署的應用程式與 Intune VPN 設定檔相容，則會顯示 [VPN 設定檔] 頁面。 在這個頁面上，您可以選擇將 iOS 應用程式與已部署的 VPN 設定檔建立關聯。 啟動應用程式時，將會自動開啟 VPN 連線。 要讓 VPN 設定檔能夠使用，必須先啟用 [個別 App VPN] 設定檔設定。
 如需如何設定 VPN 設定檔 (包括如何將設定檔與應用程式建立關聯) 的詳細資訊，請參閱 [Microsoft Intune 中的 VPN 連線](vpn-connections-in-microsoft-intune.md)。

<!---
>[!TIP]
>If an end user previously installed an iOS app and you now deploy it with a deployment action of **Available**, Intune will automatically begin to manage that app with no further action required by you, or the end-user.
--->

## <a name="example"></a>範例

在此範例中，會將應用程式當作**可用**部署至 iOS 裝置。
應用程式會在公司入口網站中使用者的裝置上顯示，而使用者可以從該處安裝應用程式。

例如，在此螢幕擷取畫面中，適用於 iOS 的 Bing 應用程式是透過使用具備自訂圖示的**外部連結**安裝類型進行部署， 且已選取**在公司入口網站中將此項目顯示為熱門應用程式並將它反白**選項。  
![iOS 可用應用程式](./media/available-install-on-iOS.png)

如果您將**必要**應用程式部署至 iOS 裝置，使用者會收到應用程式準備安裝的通知。 例如，在這個螢幕擷取畫面中，適用於 iOS 的工作資料夾應用程式是透過 **[App Store 中所管理的 iOS 應用程式]** 安裝類型進行部署。  
![iOS 必要應用程式](./media/iOS-Required-install.PNG)

## <a name="next-steps"></a>後續步驟

部署應用程式之後，您會想要監視其進度。 如需詳細資訊，請參閱[在 Microsoft Intune 中監視應用程式](monitor-apps-in-microsoft-intune.md)。



<!--HONumber=Nov16_HO2-->

