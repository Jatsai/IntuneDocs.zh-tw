---
title: "建立 Intune 裝置組態設定檔 | Intune Azure 預覽版"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解如何建立 Intune 裝置組態設定檔。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: a719b3f53076a55f1e888a9ddf8e98c7074dd25f
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-create-device-configuration-profiles-in-microsoft-intune"></a>如何在 Microsoft Intune 中建立裝置組態設定檔

[!INCLUDE[azure_preview](./includes/azure_preview.md)]


1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中選擇 [設定裝置]。
2. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
2. 在顯示設定檔清單的刀鋒視窗上，選擇 [建立設定檔]。
3. 在 [建立設定檔] 刀鋒視窗中，指定下列各項︰
    - **名稱** - 為新的設定檔輸入敘述性的名稱。
    - **描述** - 為設定檔輸入選擇性的描述。
    - **平台** - 選擇您想要建立的設定檔之平台類型。
    - **設定檔類型** - 選取您想要建立的設定檔類型。 可用類型清單會因所選平台而有所不同。
    - **設定** - 請參閱下列主題，以了解每個設定檔類型有關設定的相關資訊︰
        -  [裝置功能設定](device-features-configure.md)
        -  [裝置限制設定](device-restrictions-configure.md)
        -  [電子郵件設定](email-settings-configure.md)
        -  [VPN 設定](vpn-settings-configure.md)
        -  [Wi-Fi 設定](wi-fi-settings-configure.md)
        -  [Windows 10 版本升級設定](edition-upgrade-configure-windows-10.md)
        -  [憑證設定](certificates-configure.md)
        -  [Windows 資訊保護設定](windows-information-protection-configure.md)
        -  [教育設定](education-settings-configure.md)
        -  [自訂設定](custom-settings-configure.md)

    ![建立裝置設定檔](./media/create-device-profile.png)
4. 進行完設定之後，請在 [建立設定檔] 刀鋒視窗中，選擇 [建立]。

隨即會建立設定檔，並會出現在 [設定檔清單] 刀鋒視窗上。
若想繼續，並將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。


### <a name="next-steps"></a>後續步驟
如需如何指派裝置設定檔的相關資訊，請參閱[How to assign device profiles with Microsoft Intune](device-profile-assign.md) (如何以 Microsoft Intune 指派裝置設定檔)。
