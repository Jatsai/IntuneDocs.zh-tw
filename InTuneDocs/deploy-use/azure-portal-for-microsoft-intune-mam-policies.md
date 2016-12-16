---
title: "MAM 原則的 Azure 入口網站 | Microsoft Intune"
description: "使用 Azure 入口網站建立行動裝置應用程式管理原則。 無論裝置是否有在 Intune 中註冊，您都可以套用在這裡建立的原則。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 10/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7d6dae94-a833-40b7-9016-14ea234bb33c
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: b377d527621693f4c231f6f8b16cab277853cdf7


---

# <a name="azure-portal-for-microsoft-intune-mam-policies"></a>Microsoft Intune MAM 原則的 Azure 入口網站

## <a name="use-the-azure-portal"></a>使用 Azure 入口網站
Azure 入口網站可讓您建立和管理行動應用程式管理 (MAM) 原則。

建立 MAM 原則的 Azure 入口網站支援︰
- **在 Intune 中註冊和管理**之裝置上執行的應用程式。

- **非**由任何 MDM 解決方案註冊之裝置上執行的應用程式。
- **在協力廠商 MDM 解決方案中註冊**之裝置上執行的應用程式。

>[!IMPORTANT]


> 若您是使用 [Intune 管理主控台](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)管理裝置，即可使用 Intune 管理主控台，為已在 Intune 中註冊的裝置建立支援應用程式的 MAM 原則。

> Intune 管理主控台可能不會顯示所有 MAM 原則設定。 Azure 入口網站是建立 MAM 原則的新管理主控台。 如果您同時在 Intune 管理主控台和 Azure 入口網站中建立 MAM 原則，系統會將 Azure 入口網站中的原則套用至應用程式並部署給使用者。


## <a name="sign-in-to-the-azure-portal-and-customize-your-start-page"></a>登入 Azure 入口網站並自訂起始畫面

1.  移至 [Azure 入口網站](https://portal.azure.com)，並使用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 認證登入。

    ![Azure 入口網站登入頁面的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  成功登入之後，您會看到 [儀表板]。 您可以自訂 [儀表板] 頁面。

    ![Azure 入口網站儀表板的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  在 [瀏覽] 功能表上，尋找 **Intune**。![反白顯示 Intune [瀏覽] 功能表的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_Browse_Intune.png)

4.  選擇 [Intune] > [Intune 行動應用程式管理] > [設定]。

    ![Intune 行動應用程式管理刀鋒視窗的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]

    > 若要將刀鋒視窗釘選到 [開始]  頁面，您可以使用刀鋒視窗的 [釘選]  選項。 按一下 [Intune 行動應用程式管理] 刀鋒視窗的釘選圖示，將刀鋒視窗釘選到 [開始] 頁面。

    ![反白顯示釘選圖示的 Intune 行動應用程式管理刀鋒視窗的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![包含釘選的 Intune 磚之儀表板的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)
## <a name="next-steps"></a>後續步驟
[準備設定行動應用程式管理原則](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->

