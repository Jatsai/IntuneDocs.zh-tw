---
title: 使用 Microsoft Intune 淘汰或抹除裝置 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 淘汰或抹除 Android、Android 工作設定檔、iOS、macOS 或 Windows 裝置。 也從 Azure Active Directory 中刪除裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 896008594e17c3773831edede263c8c47cde3c48
ms.sourcegitcommit: 601327125ac8ae912d8159422de8aac7dbdc25f6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570542"
---
# <a name="remove-devices-by-using-wipe-retire-or-manually-unenrolling-the-device"></a>使用抹除、淘汰或手動取消註冊裝置來移除裝置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

透過使用 [淘汰] 或 [抹除] 動作，您可以從 Intune 移除不再需要、重新設定用途或遺失的裝置。 使用者也可以從 Intune 公司入口網站，對使用 Intune 註冊的裝置發出遠端命令。

> [!NOTE]
> 在您從 Azure Active Directory (Azure AD) 移除使用者之前，請對與該使用者建立關聯的所有裝置使用 [抹除] 或 [淘汰] 動作。 如果您從 Azure AD 移除有受控裝置的使用者，Intune 不會再抹除或淘汰這些裝置。

## <a name="wipe"></a>抹除

[抹除] 動作會將裝置還原成其出廠的預設設定。 如果您選擇 [保留註冊狀態和使用者帳戶] 核取方塊，則會保留使用者資料。 否則，會安全地清除磁碟機。

|抹除動作|**保留註冊狀態和使用者帳戶**|從 Intune 管理移除|說明|
|:-------------:|:------------:|:------------:|------------|
|**抹除**| 未勾選 | 是 | 清除所有的使用者帳戶、資料、MDM 原則及設定。 將作業系統重設為其預設狀態和設定。|
|**抹除**| 已核取 | 否 | 清除所有的 MDM 原則。 保留使用者帳戶和資料。 將使用者設定重設為預設值。 將作業系統重設為其預設狀態和設定。|

[保留註冊狀態和使用者帳戶] 選項僅適用於 Windows 10 版本 1709 或更新版本。

下次連線到 Intune 時，MDM 原則將會重新套用。

在您將裝置給予新使用者之前重設裝置，或在置遺失或遭竊的情況下，抹除會十分有用。 請謹慎選取 [抹除]。 裝置上的資料無法復原。

### <a name="wiping-a-device"></a>抹除裝置

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置] > [所有裝置]。
4. 選取您要抹除的裝置名稱。
5. 在顯示裝置名稱的窗格中，選取 [抹除]。
6. 在 Windows 10 的 1709 版或更新版本中，您也可以有 [Retain enrollment state and user account] (保留註冊狀態和使用者帳戶) 選項。 
    
    |抹除期間保留 |不保留|
    | -------------|------------|
    |與裝置建立關聯的使用者帳戶|使用者檔案|
    |機器狀態 \(網域加入、已加入 Azure AD)| 使用者安裝的應用程式 \(市集和 Win32 應用程式)|
    |行動裝置管理 (MDM) 註冊|非預設的裝置設定|
    |OEM 安裝的應用程式 \(市集和 Win32 應用程式)||
    |使用者設定檔||
    |使用者設定檔外的使用者資料||
    |使用者自動登入|| 
    
         
7. 若要確認抹除，請選取 [是]。

如果裝置已開啟且連線，則 [抹除] 動作會在 15 分鐘內傳播到所有的裝置類型。

## <a name="retire"></a>淘汰

[淘汰] 動作會移除使用 Intune 所指派的受控應用程式資料 (適用時)、設定和電子郵件設定檔。 並從 Intune 管理項目移除裝置。 當裝置下一次簽入並收到遠端 [淘汰] 動作時，便會發生。

[淘汰] 會將使用者的個人資料保留在裝置上。  

下表描述將移除哪些資料，以及移除公司資料後，[淘汰] 動作對保留在裝置上的資料有何影響。

### <a name="ios"></a>iOS

|資料類型|iOS|
|-------------|-------|
|Intune 安裝的公司應用程式和相關資料|**使用公司入口網站安裝的應用程式：** 針對已釘選到管理設定檔的應用程式，會移除所有應用程式資料與應用程式。 這些應用程式包括原本從 App Store 安裝，以及之後以公司應用程式受控的應用程式。 <br /><br /> **使用行動裝置應用程式管理及從 App Store 安裝的 Microsoft 應用程式：** 針對不受「公司入口網站」管理的應用程式，會移除由應用程式本機儲存體內之行動應用程式管理 (MAM) 加密保護的公司應用程式資料。 應用程式外受 MAM 加密保護的資料，仍維持加密狀態且無法使用，但不會被移除。 不會移除個人應用程式資料和應用程式。|
|設定|由 Intune 原則所設定的設定不再是強制性。 使用者可以變更這些設定。|
|Wi-Fi 及 VPN 設定檔設定|已移除。|
|憑證設定檔設定|憑證會予以移除及撤銷。|
|管理代理程式|已移除管理設定檔。|
|電子郵件|已移除經由 Intune 佈建的電子郵件設定檔。 已刪除裝置上的快取電子郵件。|
|Azure AD 退出|已移除 Azure AD 記錄。|

### <a name="android"></a>Android

|資料類型|Android|Android Samsung Knox Standard|
|-------------|-----------|------------------------|
|網頁連結|已移除。|已移除。|
|未受管理的 Google Play 應用程式|應用程式和資料仍會保持安裝。 <br /> <br />會移除由應用程式本機儲存體內之行動應用程式管理 (MAM) 加密保護的公司應用程式資料。 應用程式外受 MAM 加密保護的資料，仍維持加密狀態且無法使用，但不會被移除。 |應用程式和資料仍會保持安裝。 <br /> <br />會移除由應用程式本機儲存體內之行動應用程式管理 (MAM) 加密保護的公司應用程式資料。 應用程式外受 MAM 加密保護的資料，仍維持加密狀態且無法使用，但不會被移除。|
|非受控企業營運應用程式|應用程式和資料仍會保持安裝。|已解除安裝應用程式並移除應用程式的本機資料。 不會移除應用程式外的任何資料 (例如 SD 記憶卡)。|
|受管理的 Google Play 應用程式|將會移除應用程式資料。 不會移除應用程式。 應用程式外受行動應用程式管理 (MAM) 加密保護的資料 (例如 SD 記憶卡)，仍維持加密狀態且無法使用，但不會移除。|將會移除應用程式資料。 不會移除應用程式。 應用程式外受 MAM 加密保護的資料 (例如 SD 記憶卡)，仍維持加密狀態，但不會移除。|
|非受控企業營運應用程式|將會移除應用程式資料。 不會移除應用程式。 應用程式外受 MAM 加密保護的資料 (例如 SD 記憶卡)，仍維持加密狀態且無法使用，但不會移除。|將會移除應用程式資料。 不會移除應用程式。 應用程式外受 MAM 加密保護的資料 (例如 SD 記憶卡)，仍維持加密狀態且無法使用，但不會移除。|
|設定|由 Intune 原則所設定的設定不再是強制性。 使用者可以變更這些設定。|由 Intune 原則所設定的設定不再是強制性。 使用者可以變更這些設定。|
|Wi-Fi 及 VPN 設定檔設定|已移除。|已移除。|
|憑證設定檔設定|憑證會予以撤銷，但不會移除。|憑證會予以移除及撤銷。|
|管理代理程式|撤銷裝置系統管理員權限。|撤銷裝置系統管理員權限。|
|電子郵件|N/A (Android 裝置不支援電子郵件設定檔)|經由 Intune 佈建的電子郵件設定檔已移除。 已刪除裝置上的快取電子郵件。|
|Azure AD 退出|已移除 Azure AD 記錄。|已移除 Azure AD 記錄。|

### <a name="android-work-profile"></a>Android 工作設定檔

從 Android 工作設定檔裝置移除公司資料會移除該裝置上工作設定檔中的所有資料、應用程式和設定。 Intune 管理已淘汰該裝置。 Android 工作設定檔不支援抹除。

### <a name="android-enterprise-kiosk-devices"></a>Android 企業 kiosk 裝置

您只能抹除 kiosk 裝置。 您無法淘汰 Android kiosk 裝置。


### <a name="macos"></a>macOS

|資料類型|macOS|
|-------------|-------|
|設定|由 Intune 原則所設定的設定不再是強制性。 使用者可以變更這些設定。|
|Wi-Fi 及 VPN 設定檔設定|已移除。|
|憑證設定檔設定|透過 MDM 部署的憑證將會移除並撤銷。|
|管理代理程式|已移除管理設定檔。|
|Outlook|若已啟用條件式存取，裝置就不會收到新的郵件。|
|Azure AD 退出|已移除 Azure AD 記錄。|

### <a name="windows"></a>Windows

|資料類型|Windows 8.1 (MDM) 和 Windows RT 8.1|Windows RT|Windows Phone 8.1 及 Windows Phone 8|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Intune 安裝的公司應用程式和相關資料|會撤銷受 EFS 保護之檔案的索引鍵。 使用者無法開啟檔案。|不會移除公司應用程式。|原本透過公司入口網站安裝的應用程式將會解除安裝。 將會移除公司應用程式資料。|已將應用程式解除安裝。 已移除側載金鑰。<br>針對 Windows 10 版本 1703 (Creators Update) 和更新版本，不會移除 Office 365 ProPlus 應用程式。 Intune 管理延伸模組所安裝的 Win32 應用程式不會在未註冊裝置上解除安裝。 系統管理員可以利用指派排除，來確保不會對 BYOD 裝置提供 Win32 應用程式。|
|設定|由 Intune 原則所設定的設定不再是強制性。 使用者可以變更這些設定。|由 Intune 原則所設定的設定不再是強制性。 使用者可以變更這些設定。|由 Intune 原則所設定的設定不再是強制性。 使用者可以變更這些設定。|由 Intune 原則所設定的設定不再是強制性。 使用者可以變更這些設定。|
|Wi-Fi 及 VPN 設定檔設定|已移除。|已移除。|不支援。|已移除。|
|憑證設定檔設定|憑證會予以移除及撤銷。|憑證會予以移除及撤銷。|不支援。|憑證會予以移除及撤銷。|
|電子郵件|移除已啟用 EFS 的電子郵件。 這包括 Windows 郵件應用程式中的電子郵件和附件。|不支援。|已移除經由 Intune 佈建的電子郵件設定檔。 已刪除裝置上的快取電子郵件。|移除已啟用 EFS 的電子郵件。 這包括 Windows 郵件應用程式中的電子郵件和附件。 移除 Intune 佈建的郵件帳戶。|
|Azure AD 退出|否。|否。|已移除 Azure AD 記錄。|不適用。 在 Windows 10 中，您無法淘汰已加入 Azure AD 的裝置。|

### <a name="retire"></a>淘汰

1. 登入 [Azure 入口網站中的 Intune](https://aka.ms/intuneportal)。
2. 在 [裝置] 窗格中，選取 [所有裝置]。
3. 選取您要淘汰的裝置名稱。
4. 在顯示裝置名稱的窗格中，選取 [淘汰]。 選取 [是] 確認。

如果裝置已開啟且連線，則 [淘汰] 動作會在 15 分鐘內傳播到所有的裝置類型。

## <a name="delete-devices-from-the-intune-portal"></a>從 Intune 入口網站中刪除裝置

如果您想要從 Intune 入口網站移除裝置，則可以從特定的裝置窗格來刪除裝置。 下一次裝置簽入時，會移除裝置上所有的公司資料。

1. 登入 [Azure 入口網站中的 Intune](https://aka.ms/intuneportal)。
2. 選擇 [裝置] > [所有裝置] > 選擇您要刪除的裝置 > [刪除]。

### <a name="automatically-delete-devices-with-cleanup-rules"></a>使用清除規則自動刪除裝置
您可以將 Intune 設定為自動刪除看似非作用中、過時、或是沒有回應的裝置。 這些清除規則會持續監視您的裝置清查，以便您的裝置記錄保持最新狀態。 以這種方法刪除的裝置會從 Intune 管理移除。
1. 登入 [Azure 入口網站中的 Intune](https://aka.ms/intuneportal)。
2. 選擇 [裝置] > [裝置清除規則] > [確定]。
3. 在 [刪除已多日未簽入的裝置] 方塊中，輸入 90 到 270 之間的數字。
4. 選擇 [儲存]。



## <a name="delete-devices-from-the-azure-active-directory-portal"></a>從 Azure Active Directory 入口網站刪除裝置

由於通訊問題或遺失裝置，您可能需要從 Azure AD 刪除裝置。 您可以使用 [刪除] 動作來移除 Azure 入口網站中已知無法連線且不太可能與 Azure 再次通訊的裝置記錄。 [刪除] 動作不會從管理移除裝置。

1.  使用您的管理員認證登入 [Azure 入口網站中的 Azure Active Directory](http://aka.ms/accessaad)。 您也可以登入至 [Microsoft 365 系統管理中心](https://admin.microsoft.com)。 從功能表中，選取 [系統管理中心] > [Azure AD]。
2.  如果您沒有 Azure 訂用帳戶，請建立帳戶。 如果您有付費帳戶，應該不需要信用卡或付款 (請選取 [註冊免費的 Azure Active Directory]  訂閱連結)。
3.  選取 [Azure Active Directory]，然後選取您的組織。
4.  選取 [使用者]  索引標籤。
5. 選取您想要刪除之與裝置建立關聯的使用者。
6.  選取 [裝置]。
7.  視狀況移除裝置。 例如，您可能需要移除不再使用的裝置，或定義不正確的裝置。

## <a name="retire-an-apple-dep-device-from-intune"></a>從 Intune 淘汰 Apple DEP 裝置

如果您想要完全移除由 Intune 管理的 Apple DEP 裝置，請遵循下列步驟：

1. 登入 [Azure 入口網站中的 Intune](https://aka.ms/intuneportal)。
2. 選擇 [裝置] > [所有裝置] > 選擇裝置 > [淘汰]。
![淘汰的螢幕擷取畫面](./media/devices-wipe/retire.png)
3. 選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖] > 選擇權杖 > [裝置] > 選擇該裝置的核取方塊 > [刪除] > [是]。
![刪除裝置的螢幕擷取畫面](./media/devices-wipe/delete-device.png)
4. 請瀏覽 [deploy.apple.com](http://deploy.apple.com) 並依序號搜尋裝置。
5. 在 [指派至] 功能表上，選擇 [未指派]。

6. 選擇 [重新指派]。

    ![Apple 重新指派的螢幕擷取畫面](./media/devices-wipe/apple-reassign.png)

## <a name="fresh-start"></a>重新開始

適用於 Windows 10 裝置。 請深入了解[重新開始](https://docs.microsoft.com/intune/device-fresh-start)。

## <a name="next-steps"></a>後續步驟

如果您想要重新註冊已刪除的裝置，請參閱[註冊選項](enrollment-options.md)。

