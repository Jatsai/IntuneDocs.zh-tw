---
# required metadata

title: 使用 Intune 的常見方式 | Microsoft Intune
description:
keywords:
author: jeffgilb
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 1f37d4ff-b5a7-4a89-8884-a6184908b09c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Intune 的常見方式

深入實作工作時，契合貴公司的企業行動力專案關係人與業務目標很重要。  不論您是企業行動力新手，還是從另一個產品移轉而來，這一點都很要。  企業行動力需求已大幅創新，Microsoft 用來解決這些需求的方法有時可能與市場的其他解決方案不同。  契合業務目標的最佳方式是針對您想要為員工、協力廠商和 IT 塑造的環境，以表達您要完成的工作。  以下簡介 6 個依賴 Intune 的常見案例，以及如何規劃及部署每個案例的詳細資訊連結。

>[!NOTE] 您是否想要了解 Microsoft IT 如何使用 Intune，讓 Microsoft 員工在其行動裝置上存取公司資源，同時保護公司資料？ [閱讀此技術性案例研究](https://www.microsoft.com/itshowcase/Article/Content/588)，詳細查看 Microsoft IT 如何使用 Intune 與其他服務來管理身分識別、裝置、應用程式和資料。  

## 保護內部部署電子郵件和資料，以透過行動裝置安全存取
大部分企業行動力策略計劃一開始都是讓員工，在行動裝置上使用網際網路安全地存取電子郵件。 許多組織仍然有內部部署資料和應用程式伺服器，例如裝載在其公司網路上的 Microsoft Exchange。 Intune 和 Enterprise Mobility Suite (EMS) 為 Exchange Server 提供唯一的整合式條件存取解決方案，確保在使用 Intune 註冊裝置前沒有行動應用程式能夠存取電子郵件，且不需要將其他閘道電腦部署到公司網路的邊緣即可執行所有工作！

除了電子郵件，Intune 支援也能存取需要安全存取內部部署資料的行動應用程式，像是商務營運應用程式伺服器。  這通常是使用 Intune 受管理憑證完成，適用於在周邊網路結合標準 VPN 閘道或 Proxy 的存取控制，例如 Microsoft Azure AD 應用程式 Proxy。  在這些情況下，存取公司資料的唯一方法就是註冊裝置進行管理。  註冊後，管理系統可確保存取公司資料的裝置符合您的政策。  此外，Intune 的 App Wrapping Tool 可用來包含商務營運應用程式中的存取資料，讓它無法將公司資料傳遞至取用者應用程式或服務。

<!-- Learn more about how to plan and deploy Intune to help secure on-premises email and data. -->

## 保護 Office 365 電子郵件和資料，以透過行動裝置安全存取
您可以更容易，您的使用者也以更順暢地在 Office 365 中保護公司資料 (電子郵件、文件、立即訊息、連絡人)。 Intune 和 Enterprise Mobility Suite 提供唯一的整合式條件式存取解決方案，以確保沒有任何使用者、應用程式或裝置可以存取 Office 365 資料，除非它們符合您公司的法規遵循需求 (執行多因素驗證、註冊至 Intune、使用受管理應用程式、支援的 OS 版本、裝置 pin、低使用者風險設定檔等)。 在其各自的應用程式存放區中的 Office 行動應用程式會準備好開始使用資料內含項目原則 (可透過 Intune 設定)，可讓您避免與未受 IT 管理的應用程式 (例如原生電子郵件應用程式) 和儲存位置 (例如 Dropbox) 共用資料。  這項功能內建於 Office 365 和 EMS。  您不需要部署額外的基礎結構即可取得此值。

常見的 Office 365 部署作法是要求註冊裝置加以管理，但前題是它們需要使用公司應用程式/憑證/Wi-Fi/VPN 組態以完整佈建，這通常是公司擁有的裝置情況。  不過，如果使用者只需要存取公司電子郵件與文件 (通常是個人擁有的裝置情況)，則使用者也需要使用 Office 行動應用程式 (已套用資料內含項目原則)，並完全略過註冊裝置！  無論如何，將由已定義的原則保護 Office 365 資料。

<!-- Learn more about how to plan and deploy Intune to help secure Office 365 email and data. -->

## 將「攜帶您自己的裝置」(BYOD) 計劃提供給所有員工
BYOD 會繼續在組織間受歡迎，為員工減少硬體支出或提高行動產能選擇。 目前幾乎每個人都有手機，因此為什麼不在口袋內再放一支？ 主要的挑戰一直都是說服員工註冊其個人裝置加以管理，因為它們害怕 IT 部門會看到並使用他們的裝置做其他事。  

當裝置註冊不可行時，Intune 提供一個 BYOD 替代方法來簡單管理包含公司資料的應用程式。  Intune 可保護公司資料，即使有問題的應用程式存取公司和個人資料也可以，此情況適用於 Office 行動應用程式。  身為系統管理員，您可以要求使用者從 Office 行動應用程式存取 Office 365，並使用保護資料的原則來設定應用程式 (加密、釘選受保護等等)。  這些原則會防止未受管理應用程式和儲存位置遺失資料 – 應用程式內部或外部。  例如，這些原則會防止使用者將公司電子郵件設定檔的文字複製到取用者的電子郵件設定檔，即使兩個設定檔都是在 Outlook Mobile 中設定也是如此。  可針對您的 BYOD 使用者需要的其他服務及應用程式部署類似設定。

<!-- Learn more about how to plan and deploy Intune to support BYOD.-->

## 向資訊工作者核發公司電話
目前的大部分資訊工作者都是機動工作，在行動裝置上創造產能是提升競爭力的必要方式。  這些員工隨時隨地都需要順暢地存取所有公司應用程式和資料。  您需要確保公司資料安全且具有低管理成本。  

Intune 提供了大量的佈建和管理解決方案，其整合目前市場上的主要企業裝置管理平台，包括 Apple 裝置註冊方案和 Samsung KNOX 行動安全性平台。  使用 Intune 集中撰寫裝置設定，可高度自動化佈建某些公司裝置。  

試想一下︰將未拆封的 iPhone 手機交給員工。 員工開啟手機電源，然後瀏覽他們必須自行驗證之帶有公司品牌的安裝流程。 IPhone 順暢地設定安全性原則 (加密硬碟、裝置 pin 等)、電子郵件/Wi-Fi/VPN/憑證設定檔，及一組基本應用程式。 接著，員工啟動 Intune 公司入口網站應用程式以存取提供給他們的選擇性公司應用程式。

<!-- Learn more about how to plan and deploy Intune to support corporate owned devices. -->

## 將限制使用的共用平板電腦發給您的工作人員
越來越多工作人員使用行動技術。  例如，共用的平板電腦現在是零售商店員工的交流園地。  不論是用來處理銷售或立即檢查庫存，平板電腦皆有助於大幅提升與客戶的互動。  在此情況下，簡單的使用者體驗很重要。  基於這個理由，通常會將有限用途模式下的平板電腦散發給員工，例如，單一特定業務應用程式是員工可進行互動的唯一工具。  Intune 可讓您大量佈建、保護和集中管理這些共用的平板電腦 (可設定在此有限用途模式下執行)。

<!-- Learn more about how to plan and deploy Intune to support shared tablets. -->

## 讓您的員工從未受管理的公用 kiosk 中安全存取 Office 365
有時候您的員工需要使用您無法管理的裝置、應用程式或瀏覽器，例如商展和旅館的公用電腦。  您應該允許員工從中存取公司電子郵件？  利用 Intune 和企業行動套件，您就可以選擇。  答案可以是「不行」，方法是限制您的組織所管理的裝置存取電子郵件。  或者，您可以選擇允許有限存取這些未受信任電腦，方法是要求多因素驗證，並只允許瀏覽器在無法下載檔案的模式下 (例如電子郵件附件) 存取 (Outlook Web Access)。  這可確保經過嚴格驗證的員工不會不小心將公司資料放在不受信任的電腦上。

<!-- Learn more about how to plan and deploy Intune to support kiosks. -->


<!--HONumber=May16_HO1-->

