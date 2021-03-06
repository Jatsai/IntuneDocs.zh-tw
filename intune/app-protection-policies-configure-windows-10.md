---
title: 設定適用於 Windows 10 的應用程式保護原則
titleSuffix: Microsoft Intune
description: 本主題描述如何設定適用於 Windows 10 裝置的應用程式保護原則 (簡稱 APP)。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9f7bff9fa319f8df1abc4622237d1f9b98b9a685
ms.sourcegitcommit: 617bd653c34c1e6a4e2ad61811c5912f8dab775c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2019
ms.locfileid: "59570711"
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>準備好設定適用於 Windows 10 的應用程式保護原則 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

透過在 Azure AD 中設定 MAM 提供者，針對 Windows 10 啟用行動應用程式管理 (MAM)。 在 Azure AD 中設定 MAM 提供者可讓您在使用 Intune 建立新的 Windows 資訊保護 (WIP) 原則時定義註冊狀態。 註冊狀態可以是 MAM 或行動裝置管理 (MDM)。

## <a name="to-configure-the-mam-provider"></a>設定 MAM 提供者

1. 登入 Azure 入口網站，然後選擇 [Azure Active Directory]。

2. 選擇 [管理] 群組中的 [行動性 (MDM 與 MAM)]。

3. 按一下 [Microsoft Intune]。

4. 在 [設定] 刀鋒視窗上的 [還原預設的 MAM URL] 群組中進行設定。

   **MAM 使用者範圍**  
   使用 MAM 自動註冊來管理您員工之 Windows 裝置上的企業資料。 將會針對攜帶您自己的裝置案例設定 MAM 自動註冊。<ul><li>**無**<br>若所有使用者都不能在 MAM 中註冊，請選取此選項。</li><li>**部分**<br>選取包含將要在 MAM 中註冊之使用者的 Azure AD 群組。</li><li>**全部**<br>若所有使用者都可以在 MAM 中註冊，請選取此選項。</li></ul>

   **MDM 使用規定 URL**  
   Microsoft Intune 不支援 MAM 使用條款 URL。 此輸入方塊必須保留空白才能套用保護原則。

   **MAM 探索 URL**  
   MAM 服務註冊端點的 URL。 註冊端點用來註冊裝置，以使用 MAM 服務進行管理。

   **MAM 合規性 URL**  
   Microsoft Intune 不支援 MAM 合規性 URL。 此輸入方塊必須保留空白才能套用保護原則。 

5.  按一下 **[儲存]**。

## <a name="next-steps"></a>後續步驟

[建立 WIP 應用程式保護原則 (英文)](windows-information-protection-policy-create.md)
