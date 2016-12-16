---
title: "Microsoft Intune App SDK Cordova 外掛程式 | Microsoft Docs"
description: 
keywords: sdk, Cordova, intune
author: oydang
manager: angrobe
ms.author: oydang
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb940cb9-d43f-45ca-b065-ac0adc61dc6f
ms.reviewer: oydang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 613e293d9bd853d6de7cdc0d753cc8473afc180b
ms.openlocfilehash: 9ef09f43e6c878af689a500457bab578149de499


---
# <a name="microsoft-intune-app-sdk-cordova-plugin"></a>Microsoft Intune App SDK Cordova 外掛程式

> [!NOTE]
> 您可能想要先閱讀 [Intune App SDK 快速入門](intune-app-sdk-get-started.md)文章，其中說明如何在每個支援的平台上進行整合準備。


## <a name="overview"></a>概觀

[Intune App SDK Cordova 外掛程式](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)能在使用 Cordova 建置的 iOS 和 Android 應用程式中啟用 [Intune 行動應用程式管理功能](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)。 外掛程式可讓開發人員將 Intune 應用程式和資料保護功能整合至其 Cordova 應用程式。

您會發現，您可以啟用 SDK 功能，而不需要變更您的應用程式行為。 一旦將外掛程式建置到您的 iOS 或 Android 行動應用程式，IT 系統管理員便可以透過支援各種資料保護功能的 Microsoft Intune 行動應用程式管理 (MAM) 來部署原則。 我們已建置外掛程式，使得大部分的步驟會在 Cordova 建置程序中自動執行。 如此一來，您應該能夠快速地啟用應用程式的管理。 若要開始，請根據目標平台遵循下列步驟。




## <a name="whats-supported"></a>支援的項目

### <a name="developer-machines"></a>開發人員電腦
* Windows
* Mac OS


### <a name="mobile-app-platforms"></a>行動應用程式平台
* Android 4.0+
* iOS

### <a name="intune-mobile-application-management-scenarios"></a>Intune 行動應用程式管理案例

* Intune MDM 已註冊的裝置
* 協力廠商 EMM 已註冊的裝置
* 未受管理的裝置 (未使用任何 MDM 註冊)

使用 Intune App SDK Cordova 外掛程式建置的 Cordova 應用程式，現在可以在 Intune 行動裝置管理 (MDM) 註冊裝置和未註冊裝置上，接收 Intune 行動應用程式管理 (MAM) 原則。



## <a name="prerequisites"></a>必要條件

### <a name="technical-prerequisites"></a>技術性必要條件

* **[僅限 android]** 最新的 Microsoft Intune 公司入口網站應用程式永遠必須安裝在裝置上。


* 需要 0.8.0 版以上的 [Cordova 的 Azure Active Directory 驗證程式庫 (ADAL) 外掛程式](https://github.com/AzureAD/azure-activedirectory-library-for-cordova)。
  * **重要︰**由於[這裡](https://issues.apache.org/jira/browse/CB-6227?jql=text%20~%20%22plugin%20dependency%22)記載的 Apache Cordova 錯誤，已經有外掛程式相依性的應用程式將不會把外掛程式自動升級為要求的版本。


### <a name="before-you-install-and-use-microsoft-intune-app-sdk-cordova-plugin-you-must"></a>安裝和使用 Microsoft Intune App SDK Cordova 外掛程式之前，您**必須**：

* 檢閱 [Intune App SDK Cordova 外掛程式授權條款](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam/blob/master/Intune_App_SDK_Cordova_plugin_RTM_license.pdf)。

* 列印並保留一份授權條款供您備查。 下載並使用 Intune Intune App SDK Cordova 外掛程式即表示您同意這些授權條款。  若貴用戶不同意這些授權條款，請不要使用「軟體」。


## <a name="quick-start"></a>快速入門

1. 更新您的 ADAL 版本︰

    ```
    cordova plugin remove cordova-plugin-ms-adal
    cordova plugin add cordova-plugin-ms-adal@0.8.x
    ```

2. 新增 Intune App SDK for Cordova 外掛程式：

    ```
    cordova plugin add cordova-plugin-ms-intune-mam
    ```

## <a name="how-to-build-the-plugin-into-your-ios-app"></a>如何將外掛程式建置到 iOS 應用程式中

您必須完成一些步驟，應用程式才具有 Intune MAM 功能。 為了方便起見，這些步驟會在 Cordova 建置流程中自動執行，以作為建置前攔截程序。 如此一來，自動化的步驟會修改您的 `*.pbxproj`、`*-Info.plist` 和 `*.entitlements` 等專案組態相關聯檔案。 如果您的專案未包含的 entitlements 檔案，則外掛程式會自動建立一個。

這項設定只支援單一目標，而且將會在有多個目標時於第一個發現的目標上執行設定。 如果此程序失敗，請確認︰

1. 您的應用程式的 Xcode 專案是 `[name].xcodeproj`，其中 `[name]` 是 `config.xml` 中已定義的值
2. 您的專案使用[標準 Cordova 應用程式目錄結構](https://cordova.apache.org/docs/en/latest/reference/cordova-cli/index.html#directory-structure)。

## <a name="how-to-build-the-plugin-into-your-android-app"></a>如何將外掛程式建置到 Android 應用程式中

1. 使用最新的 Cordova 工具匯入此外掛程式。 外掛程式會自動叫用作為 `after_compile` 步驟。

2. 外掛程式會在建置程序的結尾建立啟用 MAM 版本的建置 APK (Android API 14+)。 建置輸出將會包含 `[Project]-intunewrapped-[Build_Configuration].apk` (例如 `helloWorld-intunewrapped-debug.apk`)。

外掛程式只支援 gradle 組建。

由於[這裡](https://issues.apache.org/jira/browse/CB-9434)記載的 Cordova bug，它導致會在 `cordova run` 忽略特定 Cordova 攔截程序。若要從命令列執行包裝的應用程式，您必須執行下列各項︰

```
$ cordova build
$ cordova run --nobuild
```


### <a name="signing-your-android-app"></a>簽署 Android 應用程式
若要將簽署資訊新增到包裝好的 APK，請像平常新增簽署資訊一樣修改 `build.json`。 例如：
```json
{
  "android": {
    "release": {
      "keystore": "your.keystore",
      "storePassword": "yourpassword",
      "alias": "youralias",
      "password" : "yourpassword",
      "keystoreType": ""
    }
  }
}
```

### <a name="build-for-android-test-only"></a>僅為 Android 測試而建置

1. 新增 `android:testOnly="true"` 至 `AndroidManifest.xml` 檔案的應用程式節點。


2. **Cordova 6.x.x：**在 `[PROJECT_ROOT]/platforms/android/cordova/lib/Adb.js` 中，變更行 60

    ```javascript
    var args = ['-s', target, 'install'];
    ```
    至
    ```javascript
    var args = ['-s', target, 'install', '-t'];
    ```

這個效果是執行 `adb install` 並使用 "-t" 旗標，因為 `testOnly` 應用程式沒有它無法安裝。

### <a name="debugging-from-visual-studio"></a>從 Visual Studio 偵錯
在第一次啟動應用程式之後，您應該會看到一個對話方塊，通知您應用程式由 Intune 管理。 按一下 [不要再顯示]，然後再從 VS 按一下 [偵錯/執行] 按鈕，以命中中斷點。

## <a name="known-limitations"></a>已知限制
### <a name="android"></a>Android
* MultiDex 支援不完整。
* 應用程式必須以 Android 4.0 (Android API 14) 或更高版本為目標。

### <a name="ios"></a>iOS
* 每當您在 **Info.plist** 檔案的 **CFBundleDocumentTypes** 節點下修改 UTI 清單，都必須在相同 plist 檔案的 [已匯入 UTI] 區段 (**UTImportedTypeDeclarations** 節點) 清除 Intune UTI，然後才再次建置。 所有的 Intune UTI 會以 `com.microsoft.intune.mam` 前置詞開頭。

* 如果您想要從 Cordova 專案移除 Intune 外掛程式，則也必須移除 iOS 平台，並且重新新增它，以復原 .xcodeproj 和.plist 檔案中的一些 Intune 設定。



<!--HONumber=Dec16_HO2-->

