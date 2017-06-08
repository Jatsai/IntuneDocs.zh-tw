---
title: "如何將 iOS 市集應用程式新增至 Intune | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解如何將 iOS 市集應用程式新增至 Intune。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 16d6da2bf1ebab609b8e9be4bec998d2f081600b
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---

# <a name="how-to-add-ios-store-apps-to-microsoft-intune"></a>如何將 iOS 市集應用程式新增至 Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

## <a name="before-you-start"></a>開始之前

如果應用程式在應用程式市集中是免費的，您只能使用這個方法指派應用程式。 如果您想要使用 Intune 指派付費應用程式，請考慮使用 [iOS 大量採購方案](vpp-apps-ios.md)。


## <a name="step-1---search-for-the-app-in-the-store"></a>步驟 1 - 搜尋存放區中的應用程式

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 **Intune** 刀鋒視窗上選擇 [管理應用程式]。
4. 在 [行動裝置應用程式] 工作負載中，選擇 [管理] > [應用程式]。
5. 從應用程式清單上方選擇 [新增]。
6. 在 [新增應用程式] 刀鋒視窗中，選擇 [搜尋 App Store]。
7. 在 **Apple App Store** 刀鋒視窗中，於 [搜尋] 方塊中輸入名稱 (或一部分的名稱)。 Intune 會搜尋市集，並傳回一份相關的結果。
8. 請從清單中，選擇您想要的應用程式，然後按一下 [確定]。

## <a name="step-2---configure-app-information"></a>步驟 2 - 設定應用程式資訊

1. 在 [新增應用程式] 刀鋒視窗中選擇 [應用程式資訊]。
2. 在 [編輯應用程式] 刀鋒視窗中設定下列資訊。 完成設定後，按一下 [新增]。 刀鋒視窗中有一些值會隨所選的應用程式自動填入︰
- **名稱** - 輸入要顯示在公司入口網站中的應用程式名稱。 確定您使用的所有應用程式名稱都是唯一的。 如果有重複的應用程式名稱，使用者只會在公司入口網站中看到其中一個應用程式。
    - **描述** - 輸入應用程式的描述。 使用者會在公司入口網站中看到這個描述。
- **發行者** - 輸入應用程式的發行者名稱。
- **App Store URL** - 輸入您要建立之應用程式的 App Store URL。
- **最小作業系統** - 從清單中選擇應用程式所能安裝的最小作業系統版本。 若將應用程式指派給安裝舊版作業系統的裝置，就不會進行安裝。
- **類別** (選用)。 選取一或多個內建應用程式類別，或選取您建立的類別。 這可以讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式。
- **將此顯示為公司入口網站中的精選應用程式** - 當使用者瀏覽應用程式時，以醒目方式在公司入口網站的主頁面上顯示此應用程式。
- **資訊 URL** - 選擇是否要輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
- **隱私權 URL** - 選擇是否要輸入包含此應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
- **開發人員** - 選擇是否要輸入應用程式開發人員的姓名。
- **擁有者** - 選擇是否要輸入此應用程式的擁有者名稱，例如**人力資源部門**。
- **注意** - 輸入要與此應用程式相關聯的附註。
- **上傳圖示** - 上傳應用程式所要關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。
3. 完成之後，請在 [新增應用程式] 刀鋒視窗中選擇 [儲存]。

您建立的應用程式將會顯示在應用程式清單中，而您可從中將應用程式指派給您選擇的群組。 如需協助，請參閱[如何將應用程式指派給群組](apps-deploy.md)。
