---
title: Microsoft Intune 中的 macOS 裝置設定 - Azure | Microsoft Docs
titleSuffix: ''
description: 在 Microsoft Intune 中於 macOS 裝置上新增、設定或建立設定來限制功能 (包括設定密碼需求)、控制鎖定畫面、使用內建應用程式、新增受限制或核准的應用程式、處理藍牙裝置、連線到雲端以進行備份和儲存、啟用 Kiosk 模式、新增網域，以及控制使用者與 Safari 網頁瀏覽器的互動方式。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/13/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5feec66e791da4038bd069cdad69a7ba573f27f3
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798372"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>使用 Intune 來允許或限制功能的 macOS 裝置設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文列出並描述您可以在 macOS 裝置上控制的各種不同設定。 作為行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來允許或停用功能、設定密碼規則、允許或限制特定應用程式，以及執行其他作業。

這些設定會新增至 Intune 裝置組態設定檔，然後指派或部署到您的 macOS 裝置。

## <a name="before-you-begin"></a>開始之前

[建立裝置限制組態設定檔](device-restrictions-configure.md#create-the-profile)。

## <a name="general"></a>一般

- **封鎖定義查閱**：[封鎖] 會防止使用者將某個文字醒目提示，然後在裝置上查閱其定義。 [未設定] (預設) 會允許存取定義查閱功能。
- **封鎖聽寫**：[封鎖] 會防止使用者使用語音輸入來輸入文字。 [未設定] (預設) 會允許使用者使用聽寫輸入。
- **封鎖內容快取**：選擇 [未設定] (預設) 來啟用內容快取。 快取存放會將應用程式資料、網頁瀏覽器資料、下載及更多資料儲存在本機裝置上。 選取 [封鎖] 來防止這項資料儲存在快取中。

  如需 macOS 上的內容快取詳細資訊，請參閱 [Manage content caching on Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (在 Mac 上管理內容快取) (開啟另一個網站)。

  本功能適用於：  
  - macOS 10.13 及更新版本

- **延遲軟體更新**：當設定為 [未設定] (預設) 時，當 Apple 發行軟體更新時便會顯示在裝置上。 例如，如果 macOS 更新由 Apple 在特定日期發行，則該更新會在發行日期左右自然地出現在裝置上。 種子組建更新會立即被允許，不會有延遲。

  [啟用] 可讓您延遲在裝置上顯示軟體更新的時間，從 0-90 天。 此設定無法控制更新何時安裝或未安裝。 

  - **延遲軟體更新的可見度**：輸入從 0-90 天的值。 當延遲到期時，使用者會收到通知，以更新為觸發延遲時可用的最舊版 OS。

    例如，如果 macOS 更新在 **1 月 1 日**推出，且 [延遲可見度] 設為 [5 天]，則更新不會在裝置上顯示為可用的更新。 在發行之後的**第六天**，可以使用該更新，終端使用者也可以安裝它。

    本功能適用於：  
    - macOS 10.13.4 及更新版本

## <a name="password"></a>密碼

- **密碼**：**要求**使用者輸入密碼才可存取該裝置。 [未設定](預設) 不需要密碼，且不會強制任何限制，例如封鎖簡單密碼或設定最小長度。
  - **必要的密碼類型**：指定密碼是否只能是數字，或是否必須為英數字元 (包含字母和數字)。 只有 Mac OS X 10.10.3 版與更新版本才支援這項設定。
  - **密碼中的非英數字元數目**：指定密碼中所需的複雜字元數 (**0** 到 **4**)。<br>複雜字元是一種符號，例如 "**?**"。
  - **密碼長度下限**：輸入使用者必須設定的密碼長度下限 (介於 **4** 到 **16** 個字元之間)。
  - **簡單密碼**：允許使用簡單密碼，例如 **0000** 或 **1234**。
  - **在螢幕鎖定最少幾分鐘後必須輸入密碼**：指定電腦多長時間沒有活動後，即需要密碼才可解除鎖定。
  - **沒有活動最久幾分鐘後鎖定螢幕**：指定電腦必須閒置多長時間，螢幕才會鎖住。
  - **密碼到期 (天)**：指定使用者經過多少天後必須變更密碼 (**1** 到 **255** 天)。
  - **避免重複使用以前用過的密碼**：輸入不可重複使用先前用過之密碼的次數 (從 **1** 到 **24**)。

- **封鎖使用者修改密碼**：選擇 [封鎖] 來防止變更、新增或移除密碼。 [未設定] (預設) 允許新增、變更或移除密碼。
- **封鎖指紋解除鎖定**：選擇 [封鎖] 以防止使用指紋來解除鎖定裝置。 [未設定] (預設) 會允許使用者使用指紋將裝置解除鎖定。

- **防止自動填滿密碼** ：選擇 [封鎖] 來防止使用 macOS 上的自動填滿密碼功能。 選擇 [封鎖] 也有下列影響：

  - 系統不會提示使用者使用 Safari 或任何應用程式中的已儲存密碼。
  - 系統會停用 [自動高強度密碼]，且不會向使用者建議高強度密碼。

  [未設定] (預設) 可允許這些功能。

- **防止近接要求密碼**：選擇 [封鎖] 來讓使用者的裝置不會向鄰近的裝置要求密碼。 [未設定] (預設) 允許這些密碼要求。

- **防止共用密碼**：[封鎖] 會防止裝置使用 AirDrop 與彼此共用密碼。 [未設定] (預設) 允許共用密碼。

## <a name="built-in-apps"></a>內建應用程式

- **封鎖 Safari 自動填滿**：[封鎖] 會停用裝置上 Safari 中的自動填滿功能。 [未設定] (預設) 會允許使用者變更網頁瀏覽器中的自動完成設定。
- **封鎖相機**：選擇 [封鎖] 來防止在裝置上存取相機。 [未設定] (預設) 會允許存取裝置的相機。
- **封鎖 Apple Music**：[封鎖] 會將 Music 應用程式還原至傳統模式並停用 Music 服務。 [未設定] (預設) 會允許使用 Apple Music 應用程式。
- **封鎖 Spotlight 網際網路搜尋結果**：[封鎖] 會防止 Spotlight 傳回來自網際網路搜尋的任何結果。 [未設定] (預設) 會允許 Spotlight 搜尋連線到網際網路以提供搜尋結果。
- **封鎖使用 iTunes 傳輸檔案**：[封鎖] 會停用應用程式檔案共用服務。 適用於 macOS 10.13 和更新版本。 [未設定] (預設) 可允許應用程式檔案共用服務。

## <a name="restricted-apps"></a>受限應用程式

您可以在受限制應用程式清單中，設定下列清單之一︰

- [禁止的應用程式] 清單：列出不允許使用者安裝與執行的應用程式 (並非由 Intune 管理)。 使用者要安裝禁止的應用程式並不會受到阻止，但如果真的安裝，系統會向系統管理員回報。
- [核准的應用程式] 清單：列出允許使用者安裝的應用程式。 使用者絕不能安裝未列出的應用程式。 自動允許 Intune 所管理的應用程式。 使用者要安裝不在核准清單上的應用程式並不會受到阻止。 但是，如果真的安裝，系統會向系統管理員回報。

若要設定清單，請按一下 [新增]，然後指定您所選的名稱，也可指定應用程式發行者以及應用程式的套件組合識別碼 (例如 *com.apple.calculator*)。

## <a name="connected-devices"></a>已連線的裝置

- **封鎖 AirDrop**：[封鎖] 會防止在裝置上使用 AirDrop。 [未設定] (預設) 允許使用 AirDrop 功能與鄰近裝置交換內容。
- **封鎖 Apple Watch 自動解除鎖定**：[封鎖] 會防止使用者以他們的 Apple Watch 解除鎖定其 macOS 裝置。 [未設定](預設) 會允許使用者以 Apple Watch 解除鎖定其 macOS 裝置。

## <a name="cloud-and-storage"></a>雲端與儲存體

- **封鎖 iCloud 鑰匙圈同步**：選擇 [封鎖] 來停止將儲存在 [鑰匙圈] 中的認證同步到 iCloud。 [未設定] (預設) 會讓使用者同步這些認證。
- **封鎖 iCloud 文件同步**：[封鎖] 會防止 iCloud 同步文件和資料。 [未設定] (預設) 會允許將文件和索引鍵/值同步到 iCloud 儲存空間。
- **封鎖 iCloud 郵件備份**：[封鎖] 會防止 iCloud 同步到 macOS 郵件應用程式。 [未設定] (預設) 會允許郵件同步到 iCloud。
- **封鎖 iCloud 連絡人備份**：[封鎖] 會防止 iCloud 同步裝置連絡人。 [未設定] (預設) 會允許使用 iCloud 同步連絡人。
- **封鎖 iCloud 行事曆備份**：[封鎖] 會防止 iCloud 同步到 macOS 行事曆應用程式。 [未設定] (預設) 會允許行事曆同步到 iCloud。
- **封鎖 iCloud 提醒備份**：[封鎖] 會防止 iCloud 同步到 macOS 提醒應用程式。 [未設定] (預設) 會允許提醒同步到 iCloud。
- **封鎖 iCloud 書籤備份**：[封鎖] 會防止 iCloud 同步裝置書籤。 [未設定] (預設) 會允許書籤同步到 iCloud。
- **封鎖 iCloud 備忘稿備份**：[封鎖] 會防止 iCloud 同步裝置備忘稿。 [未設定] (預設) 會允許備忘稿同步到 iCloud。

## <a name="domains"></a>Domains

- **電子郵件網域 URL**：將一或多個 URL 新增到清單中。 當使用者接收到來自不是您所設定之網域的電子郵件時，該電子郵件會在 MacOS 郵件應用程式中標記為不受信任。

## <a name="next-steps"></a>後續步驟

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

您也可以在 [iOS](device-restrictions-ios.md) 裝置上限制裝置功能和設定。
