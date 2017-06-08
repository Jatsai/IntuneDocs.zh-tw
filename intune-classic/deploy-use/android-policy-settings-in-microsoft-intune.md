---

title: "Android 和 Samsung KNOX 原則設定 | Microsoft Docs"
description: "建立可以在您使用 Intune 管理的 Android 裝置上控制設定及功能的原則。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71cc39cf-e726-40fd-8d08-78776e099a4b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c2652e405879d4506c40b500c489a5e92ad15282
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="android-and-samsung-knox-standard-policy-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Android 和 Samsung KNOX Standard 原則設定

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 提供一系列您可以在 Android 裝置上設定的內建一般設定。 此外，您可以指定開放行動聯盟的統一資源識別項 (OMA-URI) 值，來建立 Intune 未提供使用的自訂設定。

## <a name="general-configuration-policy"></a>一般組態原則

使用 Intune 的「Android 一般組態原則」設定下列設定：

-   **行動裝置安全性設定** - 可從預先定義的設定清單中選擇，讓您可以控制裝置上某個功能範圍。

-   **Kiosk 模式** (僅適用於 Samsung KNOX Standard 裝置) - 鎖定裝置，只允許特定功能運作。 例如，您可以允許裝置只執行您指定的一個受管理應用程式，也可以停用裝置上的音量按鈕。 這些設定可能用於裝置的展示模型，或是專用來只執行一個功能的裝置 (例如銷售點裝置)。

-   **相容與不相容的應用程式** - 指定公司中相容或不相容應用程式的清單。 在 Android 和 iOS 裝置上，「不相容應用程式報表」可用來針對使用者已安裝的應用程式，檢視您在清單中所指定應用程式的相容性。 此報表無法實際封鎖應用程式的安裝作業。

> [!TIP]
> 您可以設定使用者的條款及條件，確定他們知道將會評估其裝置上的所有應用程式 (包括個人應用程式)，並會封鎖不相容的應用程式，或將它報告為不相容。 使用者必須先接受這些條款及條件，才能註冊他們的裝置，並使用公司入口網站來取得應用程式。 如需使用條款與條件的詳細資訊，請參閱 [Microsoft Intune 的條款和條件原則設定](terms-and-condition-policy-settings-in-microsoft-intune.md)。

若此主題未包含您所需的設定，您可以使用 Android 自訂原則加以建立，讓您能夠使用 OMA-URI 設定來控制裝置。 如需詳細資訊，請移至本主題稍後的[自訂原則設定](#custom-policy-settings)。

### <a name="password-settings"></a>密碼設定

|設定名稱|詳細資料|Android 4.0+|Samsung KNOX Standard|
|----------------|-|----------------|----------------|
|**需要密碼來解除行動裝置鎖定**|指定支援的裝置上是否需要密碼。|是|是|
|**最小密碼長度**|指定密碼長度下限。|是|是|
|**抹除裝置前允許的重複登入失敗次數**|指定抹除裝置前允許的登入失敗次數。|是|是|
|**關閉螢幕前的非使用狀態分鐘數**|指定裝置自動鎖定之前，需停止活動達幾分鐘。|是|是|
|**密碼到期 (天數)**|指定必須變更密碼的間隔天數。|是|是|
|**記住密碼歷程記錄**|指定要記憶先前使用過的密碼數目。|是|是|
|**記住密碼歷程記錄** - **不得重複使用以前用過的密碼**|防止重複使用舊密碼。|是|是|
|**密碼品質**|指定所需的密碼複雜性等級，以及是否可以使用生物識別裝置。|是|是|
|**允許指紋解除鎖定**|允許使用指紋以解除鎖定裝置。|否|是|
|**允許 Smart Lock 和其他信任代理程式**<br>(Android 5 及更新版本)|讓您在相容的 Android 裝置上控制 Smart Lock 功能。 此電話功能 (有時也稱為信任代理程式) 可讓您在裝置位於受信任的位置 (例如連線到特定的藍牙裝置或靠近 NFC 標記) 時，停用或略過裝置鎖定畫面密碼。您可以使用此設定來防止使用者設定 Smart Lock。|是|否|

### <a name="encryption-settings"></a>加密設定

|設定名稱|詳細資料|Android 4.0+|Samsung KNOX Standard|
|----------------|---|-------------|----------------|
|**在行動裝置上要求加密**|行動裝置上的檔案需要加密。|是|是|
|**儲存卡需要加密**|指定裝置儲存卡是否必須加密。|否|是|

### <a name="system-settings"></a>系統設定

|設定名稱|詳細資料|Android 4.0+|Samsung KNOX Standard|
|----------------|---|-------------|----------------|
|**允許螢幕擷取**|讓使用者擷取螢幕內容做為映像。|否|是|
|**允許提交診斷資料**|允許裝置將診斷資訊提交到 Google。|否|是|
|**允許恢復出廠預設值**|允許使用者在裝置上重設為原廠設定。|否|是|

### <a name="cloud-settings---documents-and-data"></a>雲端設定 - 文件和資料

|設定名稱|詳細資料|Android 4.0+|Samsung KNOX Standard|
|----------------|----|------------------------|----------------|
|**允許 Google 備份**|允許使用 Google 備份。|否|是|

### <a name="cloud-settings---accounts-and-synchronization"></a>雲端設定 - 帳戶和同步處理

|設定名稱|詳細資料|Android 4.0+|Samsung KNOX Standard|
|----------------|-----|-----------|----------------|
|**允許 Google 帳戶自動同步處理**|允許自動同步處理 Google 帳戶設定。|否|是|

### <a name="application-settings---browser"></a>應用程式設定 - 瀏覽器

|設定名稱|詳細資料|Android 4.0+|Samsung KNOX Standard|
|----------------|-----|-----------|----------------|
|**允許網頁瀏覽器**|指定是否可使用裝置的預設網頁瀏覽器。|否|是|
|**允許自動填滿**|允許使用網頁瀏覽器的自動填入功能。|否|是|
|**允許快顯封鎖程式**|允許在網頁瀏覽器中使用快顯封鎖程式。|否|是|
|**允許 Cookie**|允許裝置的網頁瀏覽器使用 Cookie。|否|是|
|**允許動態指令碼處理**|允許裝置的網頁瀏覽器使用動態指令碼處理。|否|是|

### <a name="application-settings---apps"></a>應用程式設定 - 應用程式

|設定名稱|詳細資料|Android 4.0+|Samsung KNOX Standard|
|----------------|----|------------|----------------|
|**允許 Google Play 商店**|允許使用者在裝置上存取 Google Play 商店。|否|是|

### <a name="device-capabilities-settings---hardware"></a>裝置功能設定 - 硬體

|設定名稱|詳細資料|Android 4.0+|Samsung KNOX Standard|
|----------------|-----|-----------|----------------|
|**允許相機**|允許使用裝置相機。|是|是|
|**允許抽取式存放裝置**|允許裝置使用卸除式存放裝置，例如 SD 記憶卡。|否|是|
|**允許 Wi-Fi**|允許使用裝置的 Wi-Fi 功能。|否|是|
|**允許 Wi-Fi 網際網路共用功能**|允許使用裝置的 Wi-Fi 網際網路共用功能。|否|是|
|**允許地理位置**|允許裝置利用位置資訊。|否|是|
|**允許 NFC**|允許使用近距離無線通訊的操作 (如果裝置支援)。|否|是|
|**允許藍牙**|允許在裝置上使用藍牙。|否|是|
|**允許關閉電源**|可讓使用者關閉裝置電源。<br /><br />如果停用此設定，Samsung KNOX Standard 裝置的 [抹除裝置前允許的重複登入失敗次數] 設定無法運作。|否|是|

### <a name="device-capabilities-settings---cellular"></a>裝置功能設定 - 行動電話通訊

|設定名稱|詳細資料|Android 4.0+|Samsung KNOX Standard|
|----------------|---|-------------|----------------|
|**允許語音漫遊**|允許裝置在行動電話通訊網路時進行語音漫遊。|否|是|
|**允許數據漫遊**|允許裝置在行動電話通訊網路時進行數據漫遊。|否|是|
|**允許 SMS/MMS 傳訊**|允許在裝置上使用 SMS 和多媒體簡訊。|否|是|

### <a name="device-capabilities-settings---features"></a>裝置功能設定 - 功能

|設定名稱|詳細資料|Android 4.0+|Samsung KNOX Standard|
|----------------|----|------------|----------------|
|**允許語音助理**|允許在裝置上使用語音助理軟體。|否|是|
|**允許語音撥號**|在裝置上啟用或停用語音撥號功能。|否|是|
|**允許複製並貼上**|允許裝置上的複製及貼上功能。|否|是|
|**允許應用程式之間共用剪貼簿**|允許使用剪貼簿在應用程式之間複製並貼上。|否|是|
|**允許 YouTube**|允許在裝置上使用 YouTube。|否|是|

### <a name="settings-for-compliant-and-noncompliant-apps"></a>相容與不相容之應用程式的設定
在 [相容與不相容應用程式] 清單中，使用下列資訊，以指定相容或不相容應用程式的清單：

> [!NOTE]
> 單一原則只能包含一份相容應用程式的清單或不相容應用程式的清單。 您不能在相同的原則中同時指定兩者。

|設定名稱|詳細資料|
|----------------|--------------------|
|**當使用者安裝列出的應用程式時回報不符合規範**|列出不由 Intune 管理且您不想讓使用者安裝及執行的應用程式。 如果使用者安裝上述任何一項應用程式，其會列入不相容應用程式報表中。|
|**當使用者安裝列出的應用程式時不回報不符合規範**|列出您要允許的應用程式。 為了保持相容，使用者絕不能安裝未列出的應用程式。 自動允許 Intune 所管理的應用程式。|
|**[新增]**|將應用程式新增至選取的清單。 在 App Store 中指定應用程式名稱、應用程式發行者 (選用) 以及應用程式的 URL。<br /><br />如需詳細資訊，請參閱本主題稍後的[指定 URL 給 App Store](#specify-urls-to-app-stores)。|
|**匯入應用程式**|匯入逗點分隔值檔案中所指定的應用程式清單。 請在檔案中使用「應用程式名稱, 發行者, 應用程式 URL」的格式。|
|**編輯**|可讓您編輯所選取應用程式的名稱、發行者和 URL。|
|**刪除**|從清單中刪除選取的應用程式。|

包含相容和不相容應用程式設定的原則必須部署到使用者群組。

### <a name="kiosk-mode-settings"></a>Kiosk 模式設定
為 **Samsung KNOX Standard 裝置**指定下列設定：

|設定名稱|詳細資料|
|----------------|--------------------|
|**選取當裝置為 Kiosk 模式時可執行的受管理應用程式**|選擇 [瀏覽]，然後選取當裝置為 Kiosk 模式時可執行的受管理應用程式 (目前不支援指定為市集連結的應用程式)。 不允許在裝置上執行其他應用程式。|
|**允許音量按鈕**|啟用或停用裝置上的音量按鈕。|
|**允許喚醒螢幕睡眠按鈕**|啟用或停用裝置上的喚醒螢幕睡眠按鈕。|

### <a name="reference-information-for-compliant-and-noncompliant-apps"></a>相容與不相容之應用程式的參考資訊

#### <a name="monitor-compliant-and-noncompliant-apps"></a>監視相容與不相容的應用程式
使用 [不相容應用程式報表]  檢視允許和封鎖應用程式的相容性。

###### <a name="to-run-the-noncompliant-apps-report"></a>執行不相容應用程式報表

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [報表] &gt; [不相容應用程式報表]。

2.  選取要檢查的裝置群組。 然後選擇您是否要檢查相容應用程式、不相容應用程式，或同時檢查兩者。 最後，選擇 [檢視報表]。

#### <a name="specify-urls-to-app-stores"></a>指定 URL 給 App Store
若要在相容或不相容應用程式清單中指定應用程式 URL，請採取下列步驟︰

在 [Google Play 商店的 [應用程式] 區段](https://play.google.com/store/apps)中，搜尋您要使用的應用程式。

開啟應用程式的安裝頁面，然後將 URL 複製到剪貼簿。 您現在可以使用在相容或不相容的應用程式清單中使用此 URL。

範例：在 Google Play 中搜尋 Microsoft Office Mobile。 您要使用的 URL 是 **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**。

## <a name="custom-policy-settings"></a>自訂原則設定
使用 Microsoft Intune **Android 自訂組態原則**來部署 OMA-URI 設定，此設定可用來控制 Android 裝置上的功能。 這些是許多行動裝置製造商用來控制裝置功能的標準設定。

此功能的目的是讓您部署無法使用 Intune 原則設定的 Android 設定。
Intune 目前支援有限數目的 Android 自訂原則。 請參閱本主題中的範例，以找出您可以設定的原則。

### <a name="general-settings"></a>一般設定

|設定名稱|詳細資料|
    |----------------|--------------------|
    |**Name**|輸入 Android 自訂原則的唯一名稱，有助於您在 Intune 主控台中識別該原則。|
    |**說明**|提供可給予 Android 自訂原則概觀的說明，以及可協助您找到該說明的其他相關資訊。|

### <a name="oma-uri-settings"></a>OMA-URI 設定

   |設定名稱|詳細資料|
    |--------|--------------------|
    |**設定名稱**|輸入 OMA-URI 設定的唯一名稱，協助您在設定清單中識別該設定。|
    |**設定描述**|提供可給予設定概觀的說明，以及可協助您找到該說明的其他相關資訊。|
    |**資料類型**|選取您要在其中指定這個 OMA-URI 設定的日期類型。 選擇 [字串]、[字串 (XML)]、[日期和時間]、[整數]、[浮點數] 或 [布林值]。|
    |**OMA-URI (區分大小寫)**|指定您想要提供設定的 OMA-URI。|
    |**值**|指定要與您先前指定的 OMA-URI 產生關聯的值。|

### <a name="examples"></a>範例

- [使用預先共用的金鑰建立 Wi-Fi 設定檔](pre-shared-key-wi-fi-profile.md)
- [使用自訂原則來建立 Android 裝置的個別應用程式 VPN 設定檔](per-app-vpn-for-android-pulse-secure.md)
- [使用自訂原則來允許及封鎖 Samsung KNOX 裝置的應用程式](custom-policy-to-allow-and-block-samsung-knox-apps.md)

### <a name="see-also"></a>請參閱
[使用 Microsoft Intune 原則管理裝置的設定及功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
