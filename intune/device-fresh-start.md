---
title: "透過 Intune 重設 Windows 10 裝置"
titleSuffix: Intune on Azure
description: "了解如何使用「重新開始」來重設執行 Intune 的 Windows 10 電腦。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 590472c0ab9f0103d72730b8ab01dc324c852a7a
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>透過 Intune 使用「重新開始」重設 Windows 10 裝置


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**重新開始**裝置動作會在執行 Creators Update 的 Windows 10 電腦上移除所有已安裝的應用程式，然後將該電腦自動更新至最新的 Windows 版本。
這可用來協助移除通常會隨新電腦一起提供的預先安裝 OEM 應用程式。 您可以設定是否在發出此裝置動作時保留使用者資料。 在這種情況下，會移除應用程式和設定，但會保留使用者主資料夾的內容。

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 在 [裝置和群組] 刀鋒視窗中選擇 [所有裝置]。
5. 從您管理的裝置清單中，選擇 Windows 10 電腦裝置，然後選擇 [重新開始] 裝置遠端動作。

若要查看您剛採取的動作狀態，請在 [裝置和群組] 刀鋒視窗中，選擇 [裝置動作]。
