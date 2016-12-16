---
title: "使用 Intune App Wrapping Tool 包裝 iOS 應用程式 | Microsoft Intune"
description: "使用本主題中的資訊，了解如何能夠直接包裝 iOS 應用程式，但不需要修改應用程式本身的程式碼。 準備應用程式，以便您可以套用行動裝置應用程式管理原則。"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ee7e0491c0635c45cbc0377a5de01d5eba851132
ms.openlocfilehash: 0eee40c3c3c6bdfc3da2e715ef7b46e8408ba319


---

# <a name="prepare-ios-apps-for-mobile-application-management-with-the-intune-app-wrapping-tool"></a>準備將 iOS 應用程式交由 Intune App Wrapping Tool 進行行動應用程式管理

使用 Microsoft Intune App Wrapping Tool for iOS，只需啟用 Intune 應用程式保護功能，而無須變更應用程式本身的程式碼，就能變更內部 iOS 應用程式的行為。

此工具為 Mac OS 命令列應用程式，可會建立應用程式的包裝函式。 應用程式經過處理之後，就能使用 IT 系統管理員所部署的 Intune [行動應用程式管理原則](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)，來變更應用程式的功能。

若要下載此工具，請參閱 GitHub 上的 [Microsoft Intune App Wrapping Tool for iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios)。



## <a name="fulfill-the-prerequisites-for-the-app-wrapping-tool"></a>滿足 App Wrapping Tool 的必要條件
若要深入了解取得必要條件的方式，請參閱[如何取得 Intune App Wrapping Tool for iOS 的必要條件](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/)部落格文章。

|需求|詳細資訊|
|---------------|--------------------------------|
|支援的作業系統和工具組 | 您必須對執行 OS X 10.8.5 或更新版本的 macOS 電腦執行 App Wrapping Tool，並在該電腦上安裝 XCode 工具組第 5 版或更新版本。|
|簽署憑證和佈建設定檔 | 您必須擁有 Apple 簽署憑證和佈建設定檔。 請參閱 [Apple 開發人員文件](https://developer.apple.com/)。|
|使用 App Wrapping Tool 處理應用程式  |應用程式必須由您的公司或獨立軟體廠商 (ISV) 開發及簽署。 您無法使用此工具來處理來自 Apple Store 的應用程式。 應用程式必須針對 iOS 8.0 或更新版本撰寫。 應用程式必須也採用位置獨立可執行檔 (PIE) 格式。 如需 PIE 格式的詳細資訊，請參閱您的 Apple 開發人員文件。 最後，應用程式的副檔名必須是 **.app** 或 **.ipa**。|
|此工具無法處理的應用程式 | 加密的應用程式、未簽署的應用程式和具有擴充檔案屬性的應用程式。|
|設定您的應用程式權利|包裝應用程式之前，必須先設定權利，將一般不會授與的其他權限及功能提供給應用程式。 如需指示，請參閱[設定應用程式權利](#setting-app-entitlements)。|

## <a name="install-the-app-wrapping-tool"></a>安裝應用程式包裝工具

1.  從 [GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) 將 App Wrapping Tool 的檔案下載到 macOS 電腦。

2.  按兩下 **Microsoft Intune App Wrapping Tool for iOS.dmg**。 終端使用者授權合約 (EULA) 視窗隨即出現。 請仔細閱讀文件。

3. 選擇 [同意] 接受 EULA，將封裝掛接到您的電腦。

4.  開啟 **IntuneMAMPackager** 資料夾，並將其內容儲存到 macOS 電腦。 您現在已可開始執行 App Wrapping Tool。

## <a name="run-the-app-wrapping-tool"></a>執行應用程式包裝工具

### <a name="use-terminal"></a>使用終端機

開啟 macOS 終端機程式，並瀏覽至您儲存 App Wrapping Tool 檔案的資料夾。 可執行檔工具的名稱為 IntuneMAMPackager，位於 IntuneMAMPackager/Contents/MacOS 中。 執行命令如下︰

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioning profile paths>]
```

> [!NOTE]
> 下表中有一些是選擇性參數。

**範例：**下列範例命令會在名為 MyApp.ipa 的應用程式上執行 App Wrapping Tool。 佈建設定檔和簽署憑證的 SHA-1 雜湊均已指定並可用來簽署已包裝的應用程式。 輸出應用程式 (MyApp_Wrapped.ipa) 會建立並儲存在您的桌面資料夾中。

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB  -v true
```

### <a name="command-line-parameters"></a>命令列參數
使用 App Wrapping Tool 時，可以搭配下列命令列參數：

|屬性|用法|
|---------------|--------------------------------|
|**-i**|`<Path of the input native iOS application file>`。 檔案結尾必須是 .app 或 .ipa。 |
|**-o**|`<Path of the wrapped output application>` |
|**-p**|`<Path of your provisioning profile for iOS apps>`|
|**-c**|`<SHA1 hash of the signing certificate>`|
|**-h**|顯示可搭配 App Wrapping Tool 一起使用之命令列屬性的詳細用法資訊。|
|**-v**|(選擇性) 將詳細訊息輸出到主控台。|
|**-e**| (選擇性) 若使用此旗標，App Wrapping Tool 會書處理應用程式時移除缺少的權利。 如需詳細資料，請參閱設定應用程式的權利。|
|**-xe**| (選擇性) 列印應用程式 iOS 延伸模組的相關資訊，以及使用這些功能所需的權利。 如需詳細資料，請參閱＜設定應用程式的權利＞。 |
|**-x**| (可省略) `<An array of paths to extension provisioning profiles>`。 如果您的應用程式需要延伸模組佈建設定檔，請使用此選項。|
|**-f**|(選擇性) `<Path to a plist file specifying arguments.>`：若選擇使用 plist 範本指定其餘的 IntuneMAMPackager 屬性 (例如 -i、-o、-p 等等)，請在 [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html) 檔案之前設定此旗標。 請參閱＜使用 plist 輸入引數＞。 |
|**-b**|(可省略) 如果希望包裝的輸出應用程式和輸入應用程式有相同的套件組合版本，請使用 -b 不加引數 (不建議使用)。 <br/><br/> 如果希望包裝的應用程式有自訂的 CFBundleVersion，請使用 `-b <custom bundle version>`。 若選擇指定自訂 CFBundleVersion，建議使用最低有效元件累加原生應用程式的 CFBundleVersion，例如 1.0.0 -> 1.0.1。 |

### <a name="use-a-plist-to-input-arguments"></a>使用 plist 輸入引數
您可將所有命令引數放入 [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html) 檔案，即可輕鬆執行應用程式包裝工具。 Plist 是一種類似於 XML 的檔案格式，可讓您透過表單介面輸入命令列引數。

在 IntuneMAMPackager/Contents/MacOS 資料夾中，使用文字編輯器或 Xcode 開啟 `Parameters.plist` {空白的 plist 範本)。 為下列金鑰輸入您的引數︰

| Plist 金鑰 |  預設值| 附註 |
|------------------|--------------|-----|
| 輸入應用程式封裝路徑  |empty| 與 -i 相同|
| 輸出應用程式封裝路徑 |empty| 與 -o 相同|
| 佈建設定檔路徑 |empty| 與 -p 相同|
| SHA-1 憑證雜湊 |empty| 與 -c 相同|
| 啟用詳細資訊 |false| 與 -v 相同|
| 移除缺少的權利 | false| 與 -c 相同|
| 避免預設的組建 |false | 相當於只使用 -b 而不使用引數|
|組建字串覆寫 | empty| 已包裝的輸出應用程式的自訂 CFBundleVersion |
|延伸模組佈建設定檔路徑 | empty| 應用程式的延伸模組佈建設定檔陣列。


執行 IntuneMAMPackager 並指設定 plist 一個引數︰

```bash
./IntuneMAMPackager –f Parameters.plist
```

### <a name="post-wrapping"></a>包裝後置動作

完成包裝程序之後，即會顯示「應用程式已成功地包裝」訊息。 如果發生錯誤，請參閱[錯誤訊息](#error-messages-and-log-files)以取得協助。

已包裝的應用程式會儲存在您先前指定的輸出資料夾。 您可以將應用程式上傳到 Intune 管理主控台，然後將其關聯到行動應用程式管理原則。

> [!IMPORTANT]
> 上傳已包裝的應用程式時，如果較舊的 (包裝或原生) 版本已部署到 Intune，您可以嘗試更新舊版應用程式。 如果發生錯誤，請將應用程式上傳為新的應用程式，並刪除舊版。

您現在可以將應用程式部署到使用者群組，並將應用程式保護原則的目標設定為該應用程式。 應用程式將會使用您指定的應用程式保護原則在裝置上執行。

## <a name="error-messages-and-log-files"></a>錯誤訊息和記錄檔
使用下列資訊對您使用 App Wrapping Tool 時所遇到的問題進行疑難排解。

### <a name="error-messages"></a>錯誤訊息
若 App Wrapping Tool 無法成功完成，將會在主控台中顯示下列其中一則錯誤訊息：

|錯誤訊息|詳細資訊|
|-----------------|--------------------|
|您必須指定有效的 iOS 佈建設定檔。|您的佈建設定檔可能無效。 請確認您具備裝置正確的權限，且您已將設定檔的目標設定在開發或散發。 您的佈建設定檔也可能過期。|
|請指定有效的輸入應用程式名稱。|請確定您指定的輸入應用程式名稱正確。|
|請指定輸出應用程式的有效路徑。|請確定您指定的輸出應用程式路徑已存在且正確。|
|請指定有效的輸入佈建設定檔。|請確定您提供有效的佈建設定檔名稱和副檔名。 您的佈建設定檔可能缺少權利，或是您可能未加入 -p 命令列選項。|
|找不到您指定的輸入應用程式。 請指定有效的輸入應用程式名稱和路徑。|請確定您的輸入應用程式路徑有效且已存在。 請確定輸入應用程式存在於該位置。|
|找不到您指定的輸入佈建設定檔。 請指定有效的輸入佈建設定檔。|請確定輸入佈建檔案的路徑有效，且您指定的檔案已存在。|
|找不到您指定的輸出應用程式資料夾。 請指定輸出應用程式的有效路徑。|請確定您指定的輸出路徑有效且已存在。|
|輸出應用程式的副檔名不是 **.ipa**。|App Wrapping Tool 只接受副檔名為 **.app** 及 **.ipa** 的應用程式。 請確定您的輸出檔案具有有效的副檔名。|
|指定了無效的簽章憑證。 請指定有效的 Apple 簽章憑證。|請確定您已經從 Apple 開發人員入口網站下載正確的簽章憑證。 您的憑證可能已過期，或可能缺少公用或私用金鑰。 您的 Apple 憑證及佈建設定檔若能正確地在 Xcode 中簽署應用程式，便能用於 App Wrapping Tool。|
|您指定的輸入應用程式無效。 請指定有效的應用程式。|請確定您具有已經編譯為 .app 或 .ipa 檔案的有效 iOS 應用程式。|
|您指定的輸入應用程式已加密。 請指定有效的未加密應用程式。|App Wrapping Tool 不支援經過加密的應用程式。 請提供未加密的應用程式。|
|您指定的輸入應用程式不是位置獨立可執行檔 (PIE) 格式。 請指定有效的 PIE 格式應用程式。|無關位置的可執行檔 (PIE) 應用程式可以在執行時從隨機記憶體位址載入。 這在安全性上有許多好處。 如需安全性優點的詳細資訊，請參閱您的 Apple 開發人員文件。|
|您指定的輸入應用程式已經包裝。 請指定有效的未包裝應用程式。|您無法處理此工具已經處理過的應用程式。 如果您想要再次處理應用程式，請使用原始版本的應用程式來執行此工具。|
|您指定的輸入應用程式未簽署。 請指定有效的已簽署應用程式。|應用程式包裝工具需要已簽署的應用程式。 請參閱您的開發人員文件，了解如何簽署已包裝的應用程式。|
|您指定的輸入應用程式必須為 .ipa 或 .app 格式。|應用程式包裝工具只接受 .app 和 .ipa 副檔名。 請確定您的輸入檔副檔名有效，且已經編譯為 .app 或 .ipa 檔案。|
|您指定的輸入應用程式已包裝，且是最新的原則範本版本。|App Wrapping Tool 不會使用最新的原則範本版本重新包裝現有已經包裝的應用程式。|
|警告：未指定 SHA1 憑證雜湊。 請確定您的已包裝應用程式已經簽署，然後再部署。|請務必在 –c 命令列旗標後指定有效的 SHA1 雜湊。 |

### <a name="log-files-for-the-app-wrapping-tool"></a>App Wrapping Tool 的記錄檔
使用 App Wrapping Tool 包裝的應用程式會產生記錄，而這些記錄會寫入 iOS 用戶端裝置主控台。 當您的應用程式出現問題，需要判斷問題是否與 App Wrapping Tool 相關時，此資訊即能派上用場。 若要得到此資訊，請使用下列步驟：

1.  藉由執行應用程式來重現問題。

2.  遵照 [偵錯已部署的 iOS 應用程式](https://developer.apple.com/library/ios/qa/qa1747/_index.html)的 Apple 指示收集主控台輸出。

3.  在主控台輸入下列指令碼，篩選應用程式限制輸出的已儲存記錄：

    ```
    grep “IntuneAppRestrictions” <text file containing console output> > <required filtered log file name>
    ```
    您可以將篩選過的記錄檔提交給 Microsoft。

    > [!NOTE]
    > 在記錄檔中，項目「組建版本」表示 Xcode 的組建版本。

    已包裝的應用程式也會提供使用者選項，在應用程式當機之後，直接從裝置透過電子郵件傳送記錄檔。 使用者可以將記錄檔傳送給您檢查，並視需要轉寄給 Microsoft。


### <a name="certificate-provisioning-profile-and-authentication-requirements"></a>憑證、佈建設定檔和驗證需求

App Wrapping Tool for iOS 必須滿足此工具的一些需求，才能發揮全部的功能。

|需求|詳細資料|
|---------------|-----------|
|iOS 佈建設定檔|加入設定檔之前，請先確定其有效性。 App Wrapping Tool 在處理 iOS 應用程式期間，不會檢查佈建設定檔過期與否。 如果指定了過期的佈建設定檔，應用程式包裝工具會包含過期的佈建設定檔，而您將不會知道有問題，直到在 iOS 裝置上安裝應用程式失敗。|
|iOS 簽署憑證|指定簽署憑證之前，請先確定其有效性。 工具在處理 iOS 應用程式時，不會檢查憑證是否已過期。 如果提供已過期憑證的雜湊，則工具會處理並簽署應用程式，但它無法在裝置上安裝。<br /><br />請確定為簽署已包裝應用程式提供的憑證，在佈建設定檔中有相符的項目。 工具不會驗證針對為簽署包裝應用程式所提供的憑證，佈建設定檔是否有相符的項目。|
|驗證|裝置必須有 PIN，加密才能運作。 在部署已包裝應用程式的裝置上，點選裝置上的狀態列，將要求使用者使用工作或學校帳戶重新登入。 包裝應用程式中的預設原則為「重新啟動時驗證」。 iOS 在處理任何外部通知 (例如來電) 時，會結束並重新啟動應用程式。


## <a name="setting-app-entitlements"></a>設定應用程式權利
包裝應用程式之前，您可以授與*權利*，將超過應用程式一般所能執行的其他權限及功能提供給應用程式。 *權利檔案*還可在程式碼簽署期間，用於指定應用程式內的特殊權限 (例如共用金鑰鏈的存取權)。 某些稱為*功能*的應用程式服務，會在應用程式開發期間於 Xcode 內啟用。 啟用後，您的權利檔案中會反映這些功能。 如需權利和功能的詳細資訊，請參閱 iOS Developer Library 中的[新增功能](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html)。 如需支援功能的完整清單，請參閱[支援的功能](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html)。

### <a name="supported-capabilities-for-the-app-wrapping-tool-for-ios"></a>App Wrapping Tool for iOS 的支援功能

|功能|說明|建議的指引|
|--------------|---------------|------------------------|
|應用程式群組|使用 [應用程式群組] 可以讓多個應用程式同時存取共用容器，並允許應用程式之間進行其他處理序之間的通訊。<br /><br />若要啟用應用程式群組，請開啟 [功能] 窗格，然後按一下 [應用程式群組] 中的 [開啟]。 您可以新增應用程式群組或選取現有的應用程式群組。|使用應用程式群組時，請使用反向 DNS 標記法：<br /><br />*group.com.companyName.AppGroup*|
|背景模式|啟用 [背景模式] 可讓您的 iOS 應用程式繼續在背景中執行。||
|資料保護|[資料保護] 為使用 iOS 應用程式儲存在磁碟上的檔案，增加一層安全性。 [資料保護] 使用特定裝置上的現有內建加密硬體，以加密格式將檔案儲存在磁碟上。 您必須佈建應用程式，才能使用 [資料保護]。||
|在應用程式內購買|[在應用程式內購買] 讓您可以連線到市集，並安全地處理使用者的付款，形同將市集直接內嵌在您的應用程式中。 您可以使用 [在應用程式內購買] 為增強功能或您應用程式可用的其他內容收款。||
|金鑰鏈共用|啟用 [金鑰鏈共用] 可讓您的應用程式與您小組所開發的其他應用程式共用金鑰鏈中的密碼。|使用 [金鑰鏈共用] 時，請使用反向 DNS 標記法：<br /><br />*com.companyName.KeychainGroup*|
|個人 VPN|啟用 [個人 VPN] 可讓您的應用程式建立及控制使用網路擴充功能架構的自訂系統 VPN 組態。||
|推送通知|Apple Push Notification Service (APNs) 可讓不在前景執行的應用程式在有使用者可用的資訊時，通知使用者。|若要讓 [推播通知] 運作，您必須使用應用程式專屬的佈建設定檔。<br /><br />遵循 [Apple 開發人員文件](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html)中的步驟。|
|無線配件組態|啟用 [無線配件組態] 可為您的專案新增外部配件架構，並允許您的應用程式設定 MFi Wi-Fi 配件。||

### <a name="steps-to-enable-entitlements"></a>啟用權利的步驟

1.  啟用您應用程式中的功能：

    a.  在 Xcode 中，移至您的應用程式的目標，然後按一下 [功能]。

    b。  開啟適當的功能。 如需每項功能及如何決定正確值的詳細資訊，請參閱 [iOS Developer Library 中的新增功能](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html)。

    c.  記下您在程序期間所建立的任何識別碼。

    d.  建置並簽署要包裝的應用程式。

2.  啟用您佈建設定檔中的權利：

    a.  登入 Apple Developer Member Center。

    b。  為您的應用程式建立佈建設定檔。 如需相關指示，請參閱[如何取得 Intune App Wrapping Tool for iOS 的必要條件](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/)。

    c.  在您的佈建設定檔中，啟用您應用程式中所擁有的相同權利。 您必須提供在開發應用程式期間所指定的相同識別碼。

    d.  完成 [佈建設定檔精靈]，並下載您的檔案。

3.  確定您已符合所有必要條件，然後再包裝應用程式。

### <a name="troubleshoot-common-errors-with-entitlements"></a>權利常見錯誤的疑難排解
若 App Wrapping Tool for iOS 顯示權利錯誤，請嘗試下列疑難排解步驟。

|問題|原因|解決方法|
|---------|---------|--------------|
|無法剖析從輸入應用程式產生的權利。|App Wrapping Tool 無法讀取從應用程式解壓縮的權利檔案。 權利檔案的格式可能不正確。|檢查您應用程式的權利檔案。 下列指示說明其作法。 檢查權利檔案時，請檢查是否有任何格式不正確的語法。 檔案格式應該是 XML。|
|佈建設定檔中遺失權利 (會列出遺失的權利)。 使用具有這些權利的佈建設定檔重新封裝應用程式。|在佈建設定檔中啟用的權利與在應用程式中啟用的功能不符。 與特定功能 (例如 [應用程式群組]、[金鑰鏈共用] 等等) 相關聯的識別碼也會不符。|一般而言，您可以建立新的佈建設定檔，並啟用與應用程式相同的功能。 當設定檔與應用程式之間的識別碼不符時，App Wrapping Tool 會更換識別碼 (如果可以)。 若在建立新的佈建設定檔之後繼續收到此錯誤，您可以嘗試使用 -e 參數移除應用程式的權利 (請參閱＜使用 -e 參數移除應用程式的權利＞一節)。|

### <a name="find-the-existing-entitlements-of-a-signed-app"></a>尋找已簽署應用程式的現有權利
若要檢閱已簽署應用程式和佈建設定檔的現有權利：

1.  找到 .ipa 檔案並將其副檔名變更為 .zip。

2.  展開 .zip 檔案。 這會產生內含 .app 套件組合的 Payload 資料夾。

3.  使用 codesign 工具檢查 .app 套件的權利，其中 `YourApp.app` 是 .app 套件的實際名稱:

    ```
    $ codesign -d --entitlements :- "Payload/YourApp.app"
    ```

4.  使用安全性工具檢查應用程式之內嵌佈建設定檔的權利，其中 `YourApp.app` 是 .app 套件的實際名稱。

    ```
    $ security -D -i "Payload/YourApp.app/embedded.mobileprovision"
    ```

### <a name="remove-entitlements-from-an-app-by-using-the-e-parameter"></a>使用 –e 參數移除應用程式的權利
這個命令會移除應用程式中任何已啟用但不在權利檔案中的功能。 如果您移除的是應用程式正在使用的功能，可能會中斷您的應用程式。 例如若廠商生產的應用程式預設應具備所有功能，您可能會移除缺少的功能。

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## <a name="security-and-privacy-for-the-app-wrapping-tool"></a>App Wrapping Tool 的安全性與隱私權
當您使用 App Wrapping Tool 時，請使用下列安全性與隱私權的最佳作法。

-   要簽署的憑證、佈建設定檔，以及您指定的企業營運系統應用程式，必須位在用以執行 App Wrapping Tool 的該部 macOS 電腦上。 若檔案使用 UNC 路徑，請確定這些路徑可從 macOS 電腦存取。 路徑必須透過 IPsec 或 SMB 簽章保護。

    匯入管理主控台的已包裝應用程式，必須位於工具執行所在的同一部電腦上。 若檔案位於 UNC 路徑上，請確定該路徑可從執行管理主控台的電腦存取。 路徑必須透過 IPsec 或 SMB 簽章保護。

-   從 GitHub 存放庫下載 App Wrapping Tool 的環境，必須透過 IPsec 或 SMB 簽署加以保護。

-   您所處理的應用程式必須來自值得信任的來源，以確保防護免於攻擊威脅。

-   確保您在 App Wrapping Tool 中指定的輸出資料夾受到保護。若此資料夾為遠端資料夾更應如此。

-   包含檔案上傳對話方塊的 iOS 應用程式，可以讓使用者規避應用程式適用的剪下、複製及貼上限制。 例如，使用者可以使用檔案上傳對話方塊，來上傳應用程式資料的螢幕擷取畫面。

-   當您從經過包裝的應用程式內監視裝置上的文件資料夾時，可能會出現一個名為 .msftintuneapplauncher 的資料夾。 若您變更或刪除此檔案，可能會影響受限應用程式正常運作。

### <a name="see-also"></a>請參閱
- [決定如何準備應用程式，以使用 Microsoft Intune 管理行動裝置應用程式](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)</br>
- [使用 Microsoft Intune 原則管理裝置的設定及功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)</br>
- [使用 SDK 讓應用程式能夠管理行動裝置應用程式](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Dec16_HO2-->

