---
title: "以 Intune 設定 Windows 10 版本升級 | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰了解如何使用 Intune 升級您管理的 Windows 10 裝置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 49da713cfe61ce21501e0a8e0f6e0c225b2bc291
ms.lasthandoff: 02/16/2017


---

# <a name="how-to-configure-windows-10-edition-upgrades-in-microsoft-intune"></a>如何在 Microsoft Intune 中設定 Windows 10 版本升級

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

使用本主題中的資訊，了解如何設定 Windows 10 版本升級設定檔。 此設定檔可讓您自動將執行下列任一 Windows 10 版本的裝置，升級為較新的版本：

- Windows 10 Desktop
- Windows 10 Holographic
- Windows 10 Mobile

支援下列升級路徑：

- 從 Windows 10 Pro 到 Windows 10 Enterprise
- 從 Windows 10 Home 到 Windows 10 Education
- 從 Windows 10 Mobile 到 Windows 10 Mobile Enterprise
- 從 Windows 10 Holographic Pro 到 Windows 10 Holographic Enterprise

## <a name="before-you-start"></a>開始之前
在開始將裝置升級至最新版本之前，您需要下列其中一項：

- 可以在您以原則設為目標的所有裝置上 (適用於 Windows 10 Desktop 版本)，安裝新版本 Windows 的有效產品金鑰。 您可以使用多次啟用金鑰 (MAK) 或金鑰管理伺服器 (KMS) 金鑰。 或來自 Microsoft 的授權檔案，其中包含在您以原則設為目標的所有裝置上 (適用於 Windows 10 行動裝置版與 Windows 10 全像攝影版)，安裝新版 Windows 的授權資訊。
- 必須在 Microsoft Intune 中註冊您的目標 Windows 10 裝置。 您無法將版本升級原則和執行 Intune 電腦用戶端軟體的電腦搭配使用。

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>建立內含裝置限制設定的裝置設定檔

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中選擇 [設定裝置]。
2. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
3. 在設定檔刀鋒視窗中，選擇 [建立設定檔]。
4. 在 [建立設定檔] 刀鋒視窗中，為教育升級設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選擇 [Windows 10 及更新版本]。
6. 從 [設定檔類型] 下拉式清單中，選擇 [版本升級]。
7. 在 [版本升級] 刀鋒視窗中，設定下列項目︰
    - **升級來源版本** - 從下拉式清單中，選取希望裝置升級的 Windows 10 版本。
    - **要升級的目標版本** - 從下拉式清單中，選取希望目標裝置升級的 Windows 10 桌面版、Windows 10 全像攝影版或 Windows 10 行動裝置版之版本。
    - **產品金鑰** - 指定您從 Microsoft 取得的產品金鑰，可用來升級所有 Windows 10 Desktop 目標裝置。<br>建立包含產品金鑰的原則之後，稍後便無法再編輯該產品金鑰。 這是因為金鑰基於安全性考量而隱藏。 若要變更產品金鑰，您必須再次輸入完整金鑰。
    - **授權檔案** - 選擇 [瀏覽] 可選取您從 Microsoft 取得的授權檔，包含要將目標裝置升級的 Windows 全像攝影版或 Windows 10 行動裝置版的授權資訊。
8. 當您完成時，請返回 [建立設定檔] 刀鋒視窗，然後點擊 [建立]。

隨即會建立設定檔，並會出現在 [設定檔清單] 刀鋒視窗上。
若想繼續，並將此設定檔指派給群組，請參閱[如何指派裝置設定檔](how-to-assign-device-profiles.md)。

