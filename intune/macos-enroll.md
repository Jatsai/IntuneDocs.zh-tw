---
title: "在 Intune 中註冊 macOS 裝置"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解如何在 Intune Azure 預覽版中註冊 macOS 裝置。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c10a28a51e9f6bed99a657cd940b00f3114e4588
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="enroll-macos-devices-in-intune-azure-preview"></a>在 Intune Azure 預覽版中註冊 macOS 裝置

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Intune 可讓您管理 macOS 裝置。 若要啟用裝置管理，您的使用者必須前往[公司入口網站](http://portal.manage.microsoft.com)，並遵循提示以註冊其裝置。 管理 macOS 裝置之後，您可以[建立 macOS 裝置的自訂設定](custom settings-macos.md)。 即將推出更多功能。

## <a name="prerequisites"></a>必要條件

請於設定 macOS 裝置註冊之前，先完成下列必要條件︰

- [設定網域](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [設定 MDM 授權單位](mdm-authority-set.md)
- [建立群組](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [設定公司入口網站](company-portal-app.md)
- 指派 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)中的使用者授權
- [取得 Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)

## <a name="set-up-macos-enrollment"></a>設定 macOS 註冊

根據預設，Intune 已允許註冊 macOS 裝置。

若要封鎖註冊 macOS 裝置，請參閱 [Set device type restrictions](enrollment-restrictions-set.md#set-device-type-restrictions) (設定裝置類型限制)。

若要設定使用者能夠註冊的裝置數上限，請參閱 [Set device limit restrictions](enrollment-restrictions-set.md#set-device-limit-restrictions) (設定裝置限制)。

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>告知使用者如何註冊其裝置才可存取公司資源

您需要告訴使用者前往[公司入口網站](http://portal.manage.microsoft.com)，並遵循提示以註冊其裝置。 您也可以將線上註冊步驟的連結傳送給他們︰[在 Intune 註冊 macOS 裝置](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos)。

如需其他使用者工作的資訊，請參閱下列文章：

- [使用 Microsoft Intune 之使用者體驗的相關資源](https://docs.microsoft.com/intune-classic/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)
- [搭配 Intune 使用 iOS 或 macOS 裝置](https://docs.microsoft.com/intune-user-help/using-your-ios-or-mac-os-x-device-with-intune)
