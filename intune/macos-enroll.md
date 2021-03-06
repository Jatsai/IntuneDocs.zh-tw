---
title: 設定 macOS 裝置的註冊
titleSuffix: Microsoft Intune
description: 了解如何在 Intune 中設定 macOS 裝置的註冊。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2a968334ecf3ddb90a3f97841cc191c553b39ca
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "59568319"
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>在 Intune 中設定 macOS 裝置的註冊

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 可讓您管理 macOS 裝置，以為使用者提供公司電子郵件與應用程式的存取權。

身為 Intune 系統管理員，您可以設定公司擁有 macOS 裝置與個人擁有 macOS 裝置 (「攜帶您自己的裝置」或 BYOD) 的註冊。 

## <a name="prerequisites"></a>必要條件

請於設定 macOS 裝置註冊之前，先完成下列必要條件︰

- [設定網域](custom-domain-name-configure.md)
- [設定 MDM 授權單位](mdm-authority-set.md)
- [建立群組](groups-add.md)
- [設定公司入口網站](company-portal-app.md)
- 在 [Microsoft 365 系統管理中心](http://go.microsoft.com/fwlink/p/?LinkId=698854)指派使用者授權
- [取得 Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)

## <a name="user-owned-macos-devices-byod"></a>使用者擁有的 macOS 裝置 (BYOD)

您可以讓使用者註冊其個人裝置以便使用 Intune 來管理，這稱為「攜帶您自己的裝置」或 BYOD。 完成必要條件並指派使用者授權之後，您的使用者就可以透過執行下列動作來註冊其裝置：
- 移至[公司入口網站](https://portal.manage.microsoft.com)或
- 下載「公司入口網站」應用程式。
您也可以將線上註冊步驟的連結傳送給他們：[在 Intune 註冊 macOS 裝置](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos)。

如需其他使用者工作的資訊，請參閱下列文章：

- [使用 Microsoft Intune 之使用者體驗的相關資源](end-user-educate.md)
- [使用具有 Intune 的 macOS 裝置](/intune-user-help/using-your-macos-device-with-intune)

## <a name="company-owned-macos-devices"></a>公司擁有的 macOS 裝置
針對為使用者購買裝置的組織來說，Intune 可支援下列 macOS 公司擁有裝置的註冊方法：
- [Apple 的裝置註冊計劃 (DEP)](device-enrollment-program-enroll-macos.md)：組織可以透過 Apple 的裝置註冊計劃 (DEP) 購買 macOS 裝置。 DEP 可以讓您在「線上」部署註冊設定檔，將裝置納入管理。
- [裝置註冊管理員 (DEM)](device-enrollment-manager-enroll.md)：您可以使用 DEM 帳戶來註冊最多 1,000 部裝置。

## <a name="block-macos-enrollment"></a>封鎖 macOS 註冊
根據預設，Intune 會讓 macOS 裝置註冊。 若要封鎖註冊 macOS 裝置，請參閱 [Set device type restrictions](enrollment-restrictions-set.md) (設定裝置類型限制)。

## <a name="enroll-virtual-macos-machines-for-testing"></a>註冊虛擬 macOS 機器進行測試

> [!NOTE]
> 只支援 macOS 虛擬機器進行測試。 您不應該使用 macOS 虛擬機器作為終端使用者的實際執行裝置。 

您可以使用 Parallels Desktop 或 VMware Fusion 註冊 macOS 虛擬機器進行測試。 

針對 Parallels Desktop，您需要設定虛擬機器的硬體型號和序號，讓 Intune 可以進行辨識。 遵循 Parallels 的設定硬體類型和[序號](http://kb.parallels.com/123455)指示，設定必要的設定來進行測試。 建議您比對執行虛擬機器之裝置的硬體型號與您所建立之虛擬機器的硬體型號。 您可以在 **Apple 功能表** > [關於此 Mac][系統報表] >  > [模型識別碼] 中找到這個硬體型號。 

針對 VMware Fusion，您需要[編輯 .vmx 檔案](https://kb.vmware.com/s/article/1014782)，設定虛擬機器的硬體型號和序號。 建議您比對執行虛擬機器之裝置的硬體型號與您所建立之虛擬機器的硬體型號。 您可以在 **Apple 功能表** > [關於此 Mac][系統報表] >  > [模型識別碼] 中找到這個硬體型號。 

## <a name="user-approved-enrollment"></a>通過使用者核准的註冊

「通過使用者核准」的註冊是一種 macOS 註冊，可讓您管理某些敏感的安全性設定。 如需詳細資訊，請參閱 [Apple 支援文件](https://support.apple.com/HT208019)。

若要成為使用者核准，使用者必須在使用 [macOS 公司入口網站] 註冊之後，使用 [系統偏好設定] 手動提供核准。 針對 macOS 10.13.2 和更新版本的使用者，[macOS 公司入口網站] 提供進行此操作的指示。

若要了解裝置是否為「使用者核准」，請移至 Intune 入口網站並選取 [裝置] > [所有裝置] > 選擇裝置 > [硬體]。 檢查 [使用者核准] 欄位。

## <a name="next-steps"></a>後續步驟

註冊 macOS 裝置之後，您可以[建立 macOS 裝置的自訂設定](custom-settings-macos.md)。
