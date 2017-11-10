---
title: "不符合 Intune 合規性時所採取的動作"
titleSuffix: Intune on Azure
description: "了解如何為不符合 Intune 合規性建立動作"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d0e0c4b-a562-44f3-82a4-80eb688d4733
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3adc3c01d4657accfdb5cd70970ff191d06a9aef
ms.sourcegitcommit: a1c751959c9b3d5678bd9d67007e762df30eab59
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2017
---
# <a name="automate-actions-for-noncompliance"></a>自動化針對不符合合規性的動作

[不符合合規性時所採取的動作] 可讓您設定依時間順序的動作序列，以套用到不符合規性原則的裝置。 根據預設，偵測到裝置不符合合規性原則準則時，Intune 會立即會將其標示為不符合規範，然後 Azure AD 條件式存取會封鎖裝置。 [不符合合規性時所採取的動作] 讓您可以更靈活地決定該怎麼處置不符合規範的裝置。 例如，您可以決定不立即封鎖裝置，然後給使用者一個寬限期，讓其符合標準。

動作有兩種：

-   **透過電子郵件通知終端使用者**：您可以先自訂電子郵件通知，再將它傳送給終端使用者。 Intune 提供主旨、郵件內文的自訂功能，包含公司標誌、連絡資訊和其他收件者。

-   **標記裝置不符合規**：您可以用天數決定排程，在該天數之後裝置應標記為不符合規範。 這可以是立即執行，但您也可以給使用者一個寬限期，讓其符合裝置合規性原則。

## <a name="before-you-begin"></a>開始之前

您需要至少建立一個裝置合規性政策，才可以設定不合標準時的動作。

-   了解如何在這些環境中建立裝置合規性政策：

    -   [Android](compliance-policy-create-android.md)

    -   [Android for Work](compliance-policy-create-android-for-work.md)

    -   [iOS](compliance-policy-create-ios.md)
    
    -   [macOS](compliance-policy-create-mac-os.md)

    -   [Windows](compliance-policy-create-windows.md)

當您計劃使用裝置合規性原則來封鎖使用公司資源的裝置，您需要已設定好的 Azure AD 條件式存取。

- 了解[如何設定 EMS 條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)。

此外，您需要已建立好的通知郵件範本。 通知郵件範本稍後會在建立不符合標準動作程序中使用，做為傳送給使用者的電子郵件之用。

### <a name="to-create-a-notification-message-template"></a>建立通知郵件範本

1. 移至 [Intune on Azure 入口網站](https://portal.azure.com)，並使用您的 Intune 認證登入。

2. 選擇左功能表中的 [更多服務]，然後在文字方塊篩選中輸入 **Intune**。

3. 選擇 [Intune]

4. 選擇 [裝置合規性]，然後選擇 [管理] 區段下的 [通知]。

5. 選擇 [建立通知]，然後輸入下列各項：

    a.  Name

    b。  主體

    c.  訊息

    d.  電子郵件標頭 – 包含公司標誌

    e.  電子郵件頁尾 – 包含公司名稱

    f.  電子郵件頁尾 – 包含連絡資訊

![通知郵件範本範例](./media/actionsfornoncompliance-1.PNG)

一旦您完成新增資訊，請選擇 [建立]。 [通知] 郵件範本便可供使用。

> [!NOTE] 
> 您也可以編輯先前建立的 [通知] 範本。

## <a name="to-create-actions-for-non-compliance"></a>為不符合標準的情況建立動作

> [!TIP]
> 根據預設，Intune 會在不符合合規性定時所採取的動作區段提供一個預先定義的動作。 這動作是要在偵測到不符合您的裝置合規性原則準則之後，將裝置標示為不符合規範。 您可以自訂在偵測到之後多久將裝置標示為不符合規範。 這個動作無法移除。

您可以在建立新的裝置合規性政策時新增動作，或編輯現有裝置合規性政策的動作。

1.  在 Intune 工作負載中，從 [裝置合規性原則] 刀鋒視窗，選擇 [管理] 區段下的 [原則]。

2.  按一下裝置合規性原則來選擇它，然後選擇 [管理] 區段下的 [屬性]。

3.  [裝置合規性政策內容] 刀鋒視窗隨即開啟，選擇 [不符合標準時所採取的動作]。

4.  [不符合標準時所採取的動作] 刀鋒視窗隨即開啟，選擇 [新增] 並指定動作的參數。 您可以選擇先前建立的訊息範本、其他的收件者和寬限期排程。 您可以指定排程上的天數 (0 到 365)，然後強制執行條件式存取原則。 如果您指定 **0** 天，表示一旦裝置不符合裝置合規性原則，條件式存取必須**立即**封鎖存取公司資源。

5.  一旦您完成新增資訊，請依序選擇 [新增]及[確定]。

## <a name="next-steps"></a>後續步驟

您可以執行 [裝置合規性] 刀鋒視窗中可用的報表來監視裝置合規性活動。 深入了解[如何使用 Intune 監視裝置合規性](device-compliance-monitor.md)
