---
title: 清除 macOS 裝置
titleSuffix: Microsoft Intune
description: 了解如何從 macOS 裝置清除包括作業系統在內的所有資料。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/31/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3b0aceac9cef968222ee4f183eed87e2ac0b5849
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57392026"
---
# <a name="erase-all-data-from-a-macos-device"></a>清除 macOS 裝置的所有資料

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

您可以從 macOS 裝置清除包括作業系統在內的所有資料。 也會從 Intune 管理移除裝置。 使用者不會收到任何警告。

1. 在 [Azure 入口網站的 Intune](https://aka.ms/intuneportal) 中，選擇 [裝置] > [所有裝置] > 選擇您想清除的裝置。
![螢幕擷取畫面](./media/device-erase/choosedevice.png)
2. 按一下 [更多] > [清除]> 提供 6 位數的 [復原 PIN] 數值。 這是您必須提供給使用者的 pin，以便他們可以在自己的裝置上重新安裝作業系統。 請務必記下此 pin，因為清除動作完成後就看不到它。
![螢幕擷取畫面](./media/device-erase/providepin.png)
3. 按一下 [確定] 清除裝置。
