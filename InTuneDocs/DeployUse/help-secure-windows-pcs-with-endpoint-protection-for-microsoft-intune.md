---
# required metadata

title: Windows 電腦的 Endpoint Protection| Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 002241bf-6cd0-4c75-a4f0-891ac7e6721a

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Microsoft Intune 的 Endpoint Protection 協助保護 Windows 電腦
Microsoft Intune 可協助您透過數種方式保護受管理電腦的安全，包括 Endpoint Protection，它可提供防禦惡意程式碼威脅的即時保護、讓惡意程式碼定義保持在最新狀態，並能自動掃描電腦。 Endpoint Protection 也提供工具，協助您管理和監視惡意程式碼攻擊。

如果您尚未在電腦上安裝 Intune 用戶端，請參閱[使用 Microsoft Intune 安裝 Windows 電腦用戶端](install-the-windows-pc-client-with-microsoft-intune.md)

使用以下各節中的資訊可協助您設定、部署及監視 Endpoint Protection。

## 選擇何時使用 Endpoint Protection
身為 IT 系統管理員，您的優先要務之一是保護您管理的電腦不受惡意程式碼和病毒威脅。 將 Intune 部署到組織中的 Windows 電腦之前，您應選取下列其中一個選項並設定其相關原則設定，決定如何保護您的電腦：

|我想要：|Endpoint Protection 原則設定|詳細資訊|
|--------------|---------------------------------------|--------------------|
|只有在未安裝任何協力廠商 Endpoint Protection 應用程式時，才能使用 Microsoft Intune Endpoint Protection。<br /><br />您可以在未安裝協力廠商 Endpoint Protection 應用程式的所有電腦上使用 Microsoft Intune Endpoint Protection。|安裝 Endpoint Protection = 是<br /><br />啟用 Endpoint Protection = 是<br /><br />即使已安裝協力廠商 Endpoint Protection 應用程式，仍安裝 Endpoint Protection = 否。|如果偵測到協力廠商 Endpoint Protection 應用程式，將不會安裝 Microsoft Intune Endpoint Protection，或將在已安裝的情況下解除安裝。|
|即使已安裝協力廠商 Endpoint Protection 應用程式，仍使用 Microsoft Intune Endpoint Protection<br /><br />透過這種方式，您會同時執行 Microsoft Intune Endpoint Protection 和協力廠商 Endpoint Protection 應用程式。 由於可能發生效能問題，所以這不是建議的設定。|安裝 Endpoint Protection = 是<br /><br />啟用 Endpoint Protection = 是<br /><br />即使已安裝協力廠商 Endpoint Protection 應用程式，仍安裝 Endpoint Protection = 是|使用時機：<br /><br />-   您想要切換成使用 Microsoft Intune Endpoint Protection。<br />-   您部署將使用 Microsoft Intune Endpoint Protection 的新用戶端。<br />-   您升級將使用 Microsoft Intune Endpoint Protection 的任何用戶端。|
|使用沒有 Microsoft Intune Endpoint Protection 的 Intune。 相反地，您將依賴協力廠商 Endpoint Protection 應用程式。|安裝 Endpoint Protection = 否|如果您不使用協力廠商 Endpoint Protection 應用程式，則不建議此設定，因為這可能會讓您的組織暴露於惡意程式碼或其他攻擊之下。<br /><br />Microsoft Intune Endpoint Protection 未安裝，而且在先前已安裝的情況下會解除安裝。|
若要從目前 Endpoint Protection 應用程式切換到 Microsoft Intune Endpoint Protection，請執行下列動作：

1.  請在將 Intune 用戶端軟體部署到這些電腦的同時，讓目前的 Endpoint Protection 應用程式繼續執行。

2.  確認 Microsoft Intune Endpoint Protection 已安裝並正協助保護用戶端電腦。

3.  利用以下方式移除協力廠商 Endpoint Protection 軟體：

    -   使用 Intune 軟體發佈，部署協力廠商 Endpoint Protection 應用程式製造商所提供的軟體移除工具。 如需詳細資訊，請參閱[使用 Microsoft Intune 部署應用程式](deploy-apps.md)

    -   手動移除協力廠商 Endpoint Protection 應用程式。

> Intune 將不會自動解除安裝協力廠商 Endpoint Protection 應用程式。

## 如何設定 Microsoft Intune Endpoint Protection
請使用下列步驟幫助您設定 Endpoint Protection for Microsoft Intune。

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)中，按一下 [原則] > [新增原則]

2.  展開 [電腦管理]，然後選取 [Microsoft Intune 代理程式設定]。 選取 [建立及部署自訂原則] 來指定 Endpoint Protection 設定的原則，然後按一下 [建立原則] 按鈕。 您可以使用建議的設定或自訂設定。 如需如何建立和部署原則的詳細資訊，請參閱[使用 Microsoft Intune 電腦用戶端的一般 Windows 電腦管理工作](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)主題。

  ![Endpoint Protection 設定](./media/pol-sa-pc-endpoint-policy.png)

您可以在 [原則] 工作區的 [所有原則] 頁面上檢視已部署的 Endpoint Protection 原則。

## Endpoint Protection 服務設定

|原則設定|詳細資料|
|------------------|--------------------|
|**安裝 Endpoint Protection**|設定為 [是]，將 Endpoint Protection 安裝在受管理的電腦上。 如果安裝期間偵測到協力廠商 Endpoint Protection 應用程式，除非 [即使已安裝協力廠商 Endpoint Protection 應用程式，仍安裝 Endpoint Protection] 設定為 [是]，否則將不會安裝 Endpoint Protection. 注意：Intune Endpoint Protection 預設會安裝在受管理電腦上。 如果您不想 Endpoint Protection 安裝在受管理的電腦上，則必須將此原則明確設定為 [否]。 如果先前已安裝 Endpoint Protection，且此原則已更新為 [否]，則將會解除安裝 Endpoint Protection 用戶端。 建議值： 是<br />即使已安裝協力廠商 Endpoint Protection 應用程式，仍安裝 Endpoint Protection|
|**設定為 [是]，則即使偵測到協力廠商 Endpoint Protection 應用程式，仍會安裝 Microsoft Intune Endpoint Protection。**|建議值： 是<br /><br />啟用 Endpoint Protection|
|**設定為 [是]，在具有 Endpoint Protection 用戶端的電腦上啟用 Microsoft Intune Endpoint Protection。**|如果設定為 [否] 並已安裝 Microsoft Intune Endpoint Protection，Endpoint Protection 用戶端使用者介面不會對使用者顯示，而且所有保護功能都會處於非作用中狀態。<br /><br />建議值： 是<br /><br />停用用戶端 UI|
|**設定為 [是]，可隱藏 Microsoft Intune Endpoint Protection 用戶端使用者介面，不讓使用者看到 (需要重新啟動用戶端電腦才會生效)。**|建議值： 否<br /><br />即使已安裝協力廠商 Endpoint Protection 應用程式，仍安裝 Endpoint Protection|
|**設定為 [是]，則即使偵測到協力廠商 Endpoint Protection 應用程式，仍會強制安裝 Microsoft Intune Endpoint Protection。**|建議值： 否<br /><br />在對惡意程式碼進行補救之前先建立系統還原點|
|**設定為 [是]  可在開始進行任何惡意程式碼補救程序之前，先建立 Windows 系統還原點。**|建議值： 是<br /><br />追蹤已解決的惡意程式碼 (天數)|
|**讓 Endpoint Protection 追蹤已解決的惡意程式碼一段指定的時間，以手動檢查先前感染過病毒的電腦。**|您可以指定 0 到 30 天的值。<br /><br />建議值： 7 天<br /><br />如果您已將 [安裝 Endpoint Protection] 和 [啟用 Endpoint Protection] 的原則值設定為 [是]，並將 [即使已安裝協力廠商 Endpoint Protection 應用程式，仍安裝 Endpoint Protection] 的原則值設定為 [否]，Microsoft Intune Endpoint Protection 將會偵測到已安裝其他 Endpoint Protection 應用程式且將不會安裝，或是在已存在的情況下解除安裝，不過，Microsoft Intune Endpoint Protection 會回報另一個 Endpoint Protection 應用程式的健全狀況到 Intune 中。|
即時保護是 Microsoft Security Essentials 在潛在威脅 (例如病毒和間諜軟體) 嘗試在電腦上自行安裝或執行時如何發出警示。

  目前發生這種情況，您會在工作列最右邊看到通知區域中的訊息 即時保護設定

### 原則設定

|詳細資料|啟用即時保護|
|------------------|--------------------|
|**啟用監視和掃描存取的所有檔案和應用程式。**|它也會在任何惡意檔案和應用程式可以在電腦上執行之前加以阻擋。 建議值： 是<br /><br />掃描所有下載|
|**啟用掃描從網際網路下載到電腦的所有檔案和附件。**|建議值： 是<br /><br />監視電腦上的檔案和程式活動|
|**啟用監視傳入檔案和傳出檔案，以及電腦上的程式活動。**|使用此設定，Endpoint Protection 可監視檔案和程式何時開始執行，並將其執行的任何動作或將對其採取的動作發出警示給您。 建議值： 是<br /><br />監視的檔案|
|**如果已啟用 [監視電腦上的檔案和程式活動]  ，此設定可讓您選擇只監視傳入、只監視傳出或監視所有檔案。**|建議值： 監視所有檔案<br /><br />啟用行為監視|
|**可讓 Microsoft Intune Endpoint Protection 在用戶端電腦上檢查可疑活動的某些模式。**|建議值： 是<br /><br />啟用網路檢查系統|
|**在用戶端電腦上啟用網路檢查系統 (NIS)。**|NIS 會使用 [Microsoft Malware Protection Center (Microsoft 惡意程式碼防護中心)](http://go.microsoft.com/fwlink/?LinkId=234249) 提供之已知弱點的簽章，協助偵測及阻擋惡意網路流量。 建議值： 是<br /><br />Endpoint Protection 的即時設定|

  ![掃描排程設定](./media/pol-sa-pc-policy-realtime.png)

### 原則設定

|詳細資訊|排程每日快速掃描|
|------------------|--------------------|
|**排程電腦上常用檔案和重要系統檔案的每日快速掃描。**|這種快速掃描對效能的影響最小。 建議值： 是<br /><br />如果您錯過連續兩次的掃描便執行快速掃描|
|**將 Endpoint Protection 設定成如果電腦錯過連續兩次的排程快速掃描，它就會自動執行快速掃描。**|建議值： 是<br /><br />排程完整掃描|
|**設定完整掃描電腦本機硬碟上的所有檔案和資源。**|此掃描可能需要一些時間，而且可能影響電腦效能 (依據掃描的檔案和資源數目而定)。 建議值： 否<br /><br />如果您錯過連續兩次的完整掃描便執行完整掃描|
|**將 Endpoint Protection 設定成如果電腦錯過連續兩次的排程完整掃描，它就會自動執行完整掃描。**|建議值：尚未設定<br /><br />掃描選項設定|

### 原則設定

|詳細資料|在安裝 Endpoint Protection 後執行完整掃描|
|------------------|--------------------|
|**將 Endpoint Protection 設定成在電腦上安裝後自動執行完整系統掃描。**|這項掃描只會在電腦閒置時執行，以減少對使用者產能的影響。 建議值： 是<br /><br />在需要時自動執行完整掃描以追蹤惡意程式碼移除|
|**設定為 [是] 可讓 Endpoint Protection 在移除惡意程式碼後在電腦上自動執行完整系統掃描，以協助確認其他檔案未受影響。**|建議值： 是<br /><br />只在電腦閒置時啟動排定的掃描|
|**設定為 [是]  可避免在電腦處於使用中狀態時啟動排程掃描，以免降低任何使用者產能。**|建議值： 是<br /><br />啟動掃描之前先檢查最新的惡意程式碼定義|
|**設定為 [是] 可讓 Endpoint Protection 在電腦上啟動掃描之前，先自動檢查最新的惡意程式碼定義。**|建議值： 是<br /><br />掃描封存檔|
|**設定為 [是] 可將 Endpoint Protection 設定成掃描電腦上封存檔 (例如 .zip 或 .cab 檔) 中的惡意程式碼。**|建議值： 否<br /><br />掃描電子郵件訊息|
|**設定為 [是] 可將 Endpoint Protection 設定成在傳入電子郵件訊息到達電腦時掃描這些電子郵件訊息。**|建議值： 是<br /><br />掃描從網路共用資料夾開啟的檔案|
|**設定為 [是] 可將 Endpoint Protection 設定成掃描從網路上的共用資料夾開啟的檔案。**|這些檔案通常是使用 UNC 路徑來存取。 啟用此功能可能會對擁有唯讀存取權的使用者造成問題，因為這些使用者無法移除惡意程式碼。 建議值： 否<br /><br />掃描對應的網路磁碟機|
|**設定為 [是] 可將 Endpoint Protection 設定成要在對應的網路磁碟機上掃描檔案。**|啟用此功能可能會對擁有唯讀存取權的使用者造成問題，因為這些使用者無法移除惡意程式碼。 建議值： 否<br /><br />掃描卸除式磁碟機|
|**設定為 [是] 可將 Endpoint Protection 設定成在您於電腦上執行完整掃描時，掃描卸除式磁碟機 (例如 USB 快閃磁碟機) 是否有惡意程式碼和垃圾軟體。**|建議值： 是<br /><br />限制掃描期間的 CPU 使用量|
|**設定在電腦上進行排程掃描期間可以使用的 CPU 使用量百分比上限。**|您可以將此值設定為 1 到 100%。 建議值： 50%<br /><br />預設動作設定|

### [選擇 Endpoint Protection 如何處理下列警示層級的惡意程式碼] 設定會指定在偵測到各種警示層級的惡意程式碼時，Endpoint Protection 所採取的預設動作。

針對每個警示層級，您可以移除惡意程式碼、進行隔離或採取 Microsoft 的建議動作。 建議值︰建議的動作 (允許 Endpoint Protection 指定動作)。 排除的檔案與資料夾設定   

### [執行掃描或使用即時保護時所要排除的檔案和資料夾] 設定會在對電腦執行掃描或使用即時保護時，排除特定的檔案或資料夾。

排除的處理程序設定

### [執行掃描或使用即時保護時所要排除的處理程序] 設定可讓您在執行掃描或使用即時保護時，排除特定的處理程序。

您只能排除具有下列副檔名的檔案：.exe、.com 或 .scr 排除的檔案類型設定

### [執行掃描或使用即時保護時所要排除的副檔名] 可讓您在對電腦執行掃描或使用即時保護時，排除特定的副檔名。

Microsoft Active Protection Service 設定

### Microsoft Active Protection Service 是一個線上社群，能協助您決定回應潛在威脅的方式。
這個社群也有助於阻止新惡意程式碼感染的擴散。 您可以選取 [是]，然後指定 [成員資格層級]，以 [加入 Microsoft Active Protection Service]： 基本 - 將有關偵測到的惡意程式碼的基本資訊傳送到 Microsoft。
  - 這包括軟體來源、您所套用或 Endpoint Protection 自動套用的動作，以及這些動作是否成功。 進階 - 將有關惡意程式碼、間諜軟體和潛在的垃圾軟體的詳細資訊傳送到 Microsoft。
  - 這包括軟體的位置、檔案名稱、軟體運作方式，以及軟體對電腦的影響。 您也可以 [根據 Microsoft Active Protection Service 報表接收動態定義]

Endpoint Protection 的管理工作

## 下列工作可協助您在執行 Endpoint Protection 的受管理電腦上執行各項管理工作：
更新惡意程式碼定義
 - Intune 主控台 - 從 [群組] 工作區，選取您要更新的電腦。
  - 按一下 [遠端工作] &gt; [更新惡意程式碼定義] 受管理電腦 - 從 Windows 通知區域啟動 Endpoint Protection 用戶端軟體。
  - 按一下 [更新] 索引標籤，然後按一下 [更新] 執行惡意程式碼掃描：
 - Intune 主控台 - 從 [群組] 工作區，選取您要掃描的電腦。
  - 按一下 [執行完整惡意程式碼掃描] 或 [執行快速惡意程式碼掃描] 受管理電腦 - 從 Windows 通知區域啟動 Endpoint Protection 用戶端軟體。
  - 選取 [快速]、[完整] 或 [自訂]，然後按一下 [立即掃描] 您可以按一下 Intune 主控台右下角的 [遠端工作] 連結，檢視遠端工作的狀態。

[遠端工作狀態]  對話方塊會列出目前的遠端工作、工作狀態、裝置名稱和任何回報的錯誤，並提供疑難排解資訊的連結 (如果適用的話)。 監視 Endpoint Protection

## 您可以使用 Microsoft Intune 管理主控台 的 [保護] [](https://manage.microsoft.com/)工作區，監視電腦上惡意程式碼的狀態。
此工作區包含兩個頁面： 保護概觀 - 以連結方式顯示重要問題，您可以按一下連結來取得詳細資訊。
 - 可能顯示的問題包括： 需要後續追蹤的惡意程式碼執行個體 – 按一下連結可檢視惡意程式碼問題的清單，包括需要採取來解決問題的後續追蹤動作。
  - 您可以進一步向下切入此清單，查看哪些電腦受到影響。 含需要後續追蹤之惡意程式碼的電腦 – 按一下連結可檢視包含未解決之惡意程式碼問題的所有電腦，包括需要採取來解決問題的後續追蹤動作。
  - N 部裝置未受到保護 – 按一下連結，查看因為沒有安裝軟體，或是因為發生錯誤，而未受到任何 Endpoint Protection 軟體保護的電腦。
  - 請選取電腦以檢視更多詳細資料。 N 部裝置正在執行其他 Endpoint Protection 應用程式 – 按一下此連結，查看正在執行協力廠商 Endpoint Protection 應用程式的電腦。
  - 所有惡意程式碼 -  顯示在您的電腦上找到的所有作用中惡意程式碼的清單。
 - 您可以切入此清單，查看受特定惡意程式碼影響的所有電腦，或者您也可以選取下列其中一項工作： 檢視內容 – 開啟頁面，顯示所選惡意程式碼的詳細資訊。
  - 了解此惡意程式碼 – 從 Microsoft 惡意程式碼防護中心開啟主題，取得關於惡意程式碼的詳細資訊。
  - 除非已安裝用戶端，並且管理至少一個電腦用戶端，否則 [保護]  工作區不會顯示在管理主控台中。

> 監視 Endpoint Protection

  ![如何檢視電腦上最近偵測到惡意程式碼的路徑](./media/pol-sa-ep-monitor.png)

### Intune 可以在裝置上最多顯示 10 個最近偵測到惡意程式碼的執行個體路徑。
[最近的偵測路徑]  預設會停用。 若要啟用此檢視： 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)中，移至 [群組] > [所有裝置] . [惡意程式碼]

1.  以滑鼠右鍵按一下欄標題。 可用的欄標題隨即出現。

2.  勾選清單中的 [最近的偵測路徑]  核取方塊。 [最近的偵測路徑]  欄隨即出現，且最多會顯示 10 個在裝置上進行監視的最新惡意程式碼執行個體。

3.  需要其他協助？ 如需進一步協助和支援，請參閱[疑難排解 Microsoft Intune 中的 Endpoint Protection](/intune/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune)

## 另請參閱
保護 Windows 電腦的原則

### See Also
[Policies to protect Windows PCs](policies-to-protect-windows-pcs-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->

