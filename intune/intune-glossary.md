---
title: "Intune 字彙"
titleSuffix: Intune on Azure
description: "了解在 Microsoft Intune 中使用的一些術語"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bd7b5613-ee9f-4dc3-990c-ab4c1d40720d
ms.custom: intune-azure
ms.openlocfilehash: a9b43fc1a1877a3fc8bf4c5ee00e02dfee3cdea8
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="microsoft-intune-glossary"></a>Microsoft Intune 字彙

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="a"></a>A

|||
|-|-|
|應用程式指派|可讓使用者[尋找、下載及安裝](/intune/app-management)他們需要的應用程式。 這先前稱為*應用程式部署*。|
|應用程式組態設定檔|在執行之前使用特定設定，設定 [iOS](/intune/app-configuration-policies-use-ios) 或 [Android](/intune/app-configuration-policies-use-android) 應用程式。|
|應用程式監視|可讓您[檢閱與應用程式指派相關的最近狀態和活動](/intune/apps-monitor)。|
|應用程式保護資料移除工作|從使用者的裝置中[移除應用程式資料](/intune/app-protection-policies)。|
|應用程式保護原則|可確保使用者的應用程式符合您的[公司資料保護原則](/intune/app-protection-policies)。|
|App SDK|[Microsoft Intune App SDK](/intune/app-sdk) 可讓您將功能新增至內部撰寫的應用程式，讓 Intune 應用程式保護原則可以管理它們。|
|應用程式解除安裝動作|可讓您從使用者的裝置[解除安裝應用程式](/intune/apps-deploy)。|
|App Wrapping Tool|建立企業營運應用程式包裝函式的[命令列應用程式](/intune/apps-prepare-mobile-application-management)，可讓 Intune 應用程式保護原則對其進行管理。|
|指派動作|[指派應用程式](/intune/apps-deploy)時所進行的選擇。 您可以選擇將應用程式安裝設為必要 (必須)、選擇性 (可用)，也可以解除安裝應用程式。|
|可用安裝|使用這個動作指派應用程式時，應用程式會顯示在公司入口網站中，而且使用者可以[隨需安裝](/intune/apps-deploy)。|
|Azure 入口網站|[閱讀更多](/intune/what-is-intune) Intune 全新主控台。|

## <a name="b"></a>B
|||
|-|-|
|BYOD|[攜帶您自己的裝置](/intune/device-enrollment)。 使用者可以在裝置上安裝 Intune 公司入口網站應用程式，然後進行註冊，以存取公司資源 (例如電子郵件、公司應用程式、公司資料和支援)。|

## <a name="c"></a>C
|||
|-|-|
|憑證設定檔|當您使用 Wi-Fi、電子郵件或 VPN 設定檔時，可以使用這個原則類型，透過憑證[安全存取公司資源](/intune/certificates-configure)。|
|COD|根據組織需求和所管理裝置的類型，可以透過數種方式註冊[公司擁有的裝置](/intune/device-enrollment)。|
|公司入口網站|可供使用者[存取公司資料和應用程式](/intune/company-portal-customize)的應用程式或網站。|
|相容性原則|確定裝置[符合特定規則](/intune/device-compliance) (例如使用 PIN 存取裝置)，以及裝置上所儲存資料的加密。|
|符合規定及不符合規定的應用程式|這些設定是[裝置限制設定檔](/intune/device-restrictions-configure)的一部分，可讓您定義使用者可以執行或無法執行的應用程式清單。 然後，Intune 會通知您，透過 已安裝不相容應用程式的報表，或執行報表。 對於某些平台，Intune 也可以封鎖安裝不相容的應用程式。|
|條件式存取|[允許存取公司電子郵件、Office 365 和其他服務](/intune/conditional-access)，而這些項目僅來自與您所設定之規則相容的裝置。|
|自訂原則|一般組態原則未包含符合您需求的內建設定時，請[使用這些原則](/intune/custom-settings-configure)。 您可以使用自訂原則，透過其他方式 (例如 Apple Configurator 或 OMA-URI) 建立設定。|

## <a name="d"></a>D
|||
|-|-|
|部署|將應用程式或原則傳送至所管理裝置或使用者的動作。 這個動作現在又稱為*指派*。|
|裝置註冊管理員|組織可以搭配使用 Intune 與單一使用者帳戶來管理大量的行動裝置。 [裝置註冊管理員 (DEM) 帳戶](/intune/device-enrollment-program-enroll-ios)是特殊 Intune 帳戶，最多可以註冊 1,000 部裝置。|
|裝置設定檔|[這些設定檔](/intune/device-profile-create)可讓您在所管理的裝置上設定各種不同的安全性、功能和存取設定。|

## <a name="e"></a>E
|||
|-|-|
|電子郵件設定檔|這個原則可以用來設定行動裝置上的[電子郵件存取設定](/intune/email-settings-configure)，以將使用者必須執行的設定量減到最少。|
|EMS|Microsoft Enterprise Mobility + Security (之前為 Enterprise Mobility Suite) 會保護公司資料，同時讓使用者[存取應用程式和其所需的內容](https://www.microsoft.com/cloud-platform/enterprise-mobility)。|
|使用者|使用 Intune 管理之[手機和電腦這類裝置的使用者](/intune/end-user-educate)。|
|註冊|Microsoft Intune 使用[註冊](/intune/device-enrollment)來管理裝置，並允許其存取資源。|

## <a name="f"></a>F
|||
|-|-|
|FastTrack|適用於合格方案中具有 150 個授權之 Intune 使用者的 [Microsoft 服務](https://technet.microsoft.com/library/mt228265.aspx)。 Microsoft 專家可使用這項服務與您合作，來啟動並執行 Intune。|

## <a name="g"></a>G
|||
|-|-|
|中|群組可讓您[邏輯收集使用者或裝置](/intune/groups-get-started)。 例如，您可以建立所有 Windows 電腦的群組。 然後，您可以將應用程式和設定檔指派給這些群組。|

## <a name="h"></a>H
|||
|-|-|
|混合式|可以透過 System Center Configuration Manager 主控台管理使用 Intune 所註冊之裝置的設定。|

## <a name="i"></a>I
|||
|-|-|
|Intune 入口網站|用於大部分 Intune 管理作業的 Azure 入口網站。|
|Intune 軟體用戶端|另一種[管理一些 Windows 電腦](/intune-classic/get-started/choose-how-to-manage-devices)的方式。如需決定要使用之方法的協助，請參閱選擇如何管理裝置。|
|Intune 軟體發行者|一種工具，用來[定義您要部署的應用程式並將它們上傳至雲端儲存空間](/intune-classic/deploy-use/add-apps)。|
|清查|用來檢視所管理裝置上[安裝的硬體和軟體](/intune/device-inventory)。|

## <a name="k"></a>K
|||
|-|-|
|資訊站模式|設定為[裝置限制設定檔](/intune/device-restrictions-configure)的一 部分，這個模式可讓您鎖定裝置。 例如，您可以設定零售裝置只允許執行一些應用程式。|

## <a name="m"></a>M
|||
|-|-|
|受管理的瀏覽器|一個[網頁瀏覽應用程式](/intune/app-configuration-managed-browser)，您可以在組織中使用 Intune 來指派此應用程式。 受管理的瀏覽器原則會設定允許清單或封鎖清單，以限制受管理瀏覽器的使用者可瀏覽的網站。|
|MDM 授權單位|[MDM 授權單位](/intune/mdm-authority-set)會定義有權管理一組裝置的管理服務。 MDM 授權單位選項包括單獨使用 Intune，以及具備 Intune 的 Configuration Manager。|
|行動應用程式組態原則|一個 [iOS](/intune/app-configuration-policies-use-ios) 或 [Android](/intune/app-configuration-policies-use-android) 原則，用來在執行時提供相容應用程式的設定 (例如，公司名稱或伺服器位址)。|
|行動應用程式佈建原則|一個 iOS 原則，可協助您確定所指派 iOS 應用程式的[佈建設定檔](/intune/app-provisioning-profile-ios)未過期。|
|行動應用程式管理|[行動應用程式管理 (MAM)](/intune/app-lifecycle) 可讓您針對使用者發行、推送、設定、保護、監視和更新行動應用程式。
|行動裝置管理|[行動裝置管理 (MDM)](/intune/device-lifecycle) 可讓您在 Intune 中註冊裝置，以佈建、設定、監視和管理這些裝置。



## <a name="o"></a>O
|||
|-|-|
|OMA-DM|開放行動裝置聯盟裝置管理。 一種業界標準裝置管理通訊協定，許多硬體製造商可用來控制行動裝置和電腦的功能。|
|OMA-URI|開放行動裝置聯盟統一資源識別碼。 這些項目可識別符合 OMA-DM 標準的個別裝置設定。 沒有內建設定符合需求時，這些設定可以用於 [Intune 自訂設定檔](/intune/custom-settings-configure)。|

## <a name="p"></a>P
|||
|-|-|
|密碼重設|一種 Intune 功能，可讓您強制使用者在支援的裝置上[重設密碼](/intune/device-passcode-reset)。|

## <a name="r"></a>R
|||
|-|-|
|遠端鎖定|這是一種 Intune 功能，讓您即使未擁有裝置，也能[鎖定支援的裝置](/intune/device-remote-lock)。|
|必要安裝|當您使用這個動作指派應用程式時，不需要[使用者介入](/intune/apps-deploy)即可完成安裝。 在某些平台上，使用者可能必須接受安裝)。|


## <a name="s"></a>S
|||
|-|-|
|選擇性抹除|[選擇性抹除](/intune/device-company-data-remove)只會移除公司資料，包括適用的行動應用程式管理 (MAM) 資料、設定和裝置的電子郵件設定檔。 選擇性抹除會將使用者的個人資料保留在裝置上。|
|側載|安裝企業營運應用程式，而不需要從應用程式市集中存取的動作。|
|訂用帳戶|您為了存取 Intune 租用戶所簽訂的合約。|

## <a name="t"></a>T
|||
|-|-|
|TeamViewer|一個協力廠商應用程式，可搭配 Intune 來為您使用 Intune 管理的 Android 裝置提供[遠端協助功能](/intune/device-profile-android-teamviewer)。|
|租用戶|您可以使用訂用帳戶存取之 Intune 服務的單一執行個體。|
|條款及條件|一種指派給使用者的原則類型，包含使用者必須[閱讀並接受](/intune/terms-and-conditions-create)的資訊，才能使用公司入口網站來註冊和存取其工作。|

## <a name="v"></a>V
|||
|-|-|
|大量採購應用程式與書籍|針對您想要在公司內使用的應用程式或書籍，某些應用程式市集可讓您購買多個授權。 Intune 可協助您管理[透過此類方案所購買](/intune/vpp-apps)的應用程式與書籍。 您可以從應用程式市集匯入授權資訊、追蹤已經使用的授權數，並避免您所安裝的應用程式超過您所擁有的授權數。|
|VPN 設定檔|一種原則，可將 [VPN 設定](/intune/vpn-settings-configure)指派給所管理的裝置，以將使用者所需的任何設定減到最少。|

## <a name="w"></a>W
|||
|-|-|
|Wi-Fi 設定檔|一種原則，可將[無線網路設定](/intune/wi-fi-settings-configure)指派給裝置，讓使用者連接至公司網路，而不需要知道或進行任何設定。