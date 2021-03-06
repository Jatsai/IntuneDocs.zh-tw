---
title: 適用於 Microsoft Intune 的商務用 Windows Update 設定 - Azure | Microsoft Docs
description: 您可以使用 Intune 部署適用於 Windows 10 裝置的 WUfB 設定。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: c5a0ee88a24804294346888facef523f89fee816
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66046641"
---
# <a name="windows-update-settings-for-intune"></a>適用於 Intune 的 Windows Update 設定  

檢視您可以透過 Microsoft Intune [設定及管理](windows-update-for-business-configure.md)的 Windows 10 Update 設定。  

當您在 Intune 中設定適用於 Windows 10 Update 更新通道的設定時，您設定的是 Windows Update 設定。 如果 Windows Update 設定具有 Windows 10 版本相依性，則版本相依性會在設定詳細資料中註明。  

## <a name="update-settings"></a>Update 設定  

Update 設定可控制裝置將下載的位元和時機。 如需每個設定之行為的詳細資訊，請參閱 Windows 參考文件。  

### <a name="servicing-channel"></a>維護通道  

- **預設**：半年通道 (已設定目標)  
- **Windows 參考文件**：[Update/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  
設定裝置接收 Windows 更新的通道 (分支)。 在更新傳遞之前，不同的通道可以使用不同的延遲期。  

例如，「半年通道」  有六個月的延遲。 如果您使用此通道，而沒有此設定主體的額外延遲，則裝置會在發行更新的六個月後安裝更新。  

支援的更新通道：  

- 半年通道  
- 半年通道 (已設定目標)  
- Windows 測試人員 - 快  
- Windows 測試人員 - 慢  
- 發行 Windows 測試人員  

如果您選取測試人員通道，Intune 會自動設定 Windows 更新設定 [Update/ManagePreviewBuilds](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds)，以使測試人員組建生效。  


> [!IMPORTANT]  
> 從 Windows 1903 版開始，「半年通道 (已設定目標)」  (SAC-T) 已淘汰而不再使用。 隨著此變更的推出，SAC-T 與「半年通道」  合併。 若要深入了解此變更以及它如何影響商務用 Windows Update，請參閱 Windows IT 專業人員部落格文章[商務用 Windows Update 與 SAC-T 的停用](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523) \(英文\)。
 


### <a name="microsoft-product-updates"></a>Microsoft 產品更新  

- **預設**：允許
- **Windows 參考文件**：[Update/AllowMUUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

選擇 [允許]  從 Microsoft Update 掃描應用程式更新。    

### <a name="windows-drivers"></a>Windows 驅動程式  

- **預設**：允許
- **Windows 參考文件**：[Update/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)

選擇 [允許]  在更新期間包含 Windows Update 驅動程式

### <a name="quality-update-deferral-period-days"></a>品質更新延遲期間 (天)  

- **預設**：0  
- **Windows 參考文件**：[Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

指定品質更新的延遲天數 (從 0 到 30)。 這段期間會加上您選取之維護通道的任何延遲期間。 延遲期間的開始時間是裝置接收原則的時候。  

品質更新通常會修正和改進現有的 Windows 功能。  

### <a name="feature-update-deferral-period-days"></a>功能更新延遲期間 (天)  

- **預設**：0  
- **Windows 參考文件**：[Update/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

指定功能更新的延遲天數。 這段期間會加上您選取之維護通道的任何延遲期間。 延遲期間的開始時間是裝置接收原則的時候。  
支援的延遲期間：  

- *Windows 1709 版或更新版本*：0 到 365 天  
- *Windows 1703 版*：0 到 180 天  

「功能更新」通常是 Windows 的新功能。  

### <a name="set-feature-update-uninstall-period-2--60-days"></a>設定功能更新解除安裝期間 (2 到 60 天)  

- **預設**：10  
- **Windows 參考文件**：[Update/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

設定在經過多少時間之後無法解除安裝功能更新。  

在此期間到期後，先前的更新位元會從裝置上移除，且無法再解除安裝為之前的更新版本。  

例如，假設更新通道具有 20 天的功能更新解除安裝期間。 在 25 天之後，您決定要復原上次的功能更新，並使用 [解除安裝] 選項。  已安裝功能更新超過 20 天的裝置無法解除安裝，因為它們已在維護當中移除了必要的位元。 不過，僅安裝功能更新 19 天的裝置，只要在尚未超過 20 天的解除安裝期間成功簽入以接收解除安裝命令，就可以解除安裝更新。  


## <a name="user-experience-settings"></a>使用者體驗設定  

使用者體驗設定控制裝置重新啟動和提醒的使用者體驗。 如需每個設定之行為的詳細資訊，請參閱 Windows 參考文件。  

### <a name="automatic-update-behavior"></a>自動更新行為  

- **預設**：在排程時間自動安裝並重新啟動  
- **Windows 參考文件**：[Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

選擇要如何安裝自動更新和何時重新啟動裝置 (如有需要)。  

請參閱 Windows 參考文件，以取得下列支援選項的完整資訊：  

- **通知下載**：在下載更新前先通知使用者。 使用者選擇下載和安裝更新。  

- **在維護期間自動安裝**：當裝置未在使用中或以電池電源執行時自動下載更新，然後在自動維護期間安裝。 當需要重新啟動時，系統會在七天內持續提示使用者重新啟動，之後便會強制重新啟動。  

  此選項可在更新安裝之後自動重新啟動裝置。 使用 [使用時間]  設定來定義封鎖自動重新啟動的期間：  

  - **使用時間開始**：指定針對因安裝更新而抑制重新啟動的開始時間。  
    **Windows 參考文件**：[Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **預設**：上午 8 點  
  
  - **使用時間結束**：指定針對因安裝更新而抑制重新開機的結束時間。  
    **Windows 參考文件**：[Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **預設**：下午 5 點  

- **在維護期間自動安裝並重新啟動**：當裝置未在使用中或以電池電源執行時自動下載更新，然後在自動維護期間安裝。 當需要重新啟動時，裝置會在未使用時重新啟動。 (這是非受控裝置的預設設定)。  

  此選項可在更新安裝之後自動重新啟動裝置。 [使用時間]  設定的用法並未在 Windows Update 設定中描述，但 Intune 會用來定義封鎖自動重新啟動的期間：  

  - **使用時間開始**：指定針對因安裝更新而抑制重新啟動的開始時間。  
    **Windows 參考文件**：[Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **預設**：上午 8 點  

  - **使用時間結束**：指定針對因安裝更新而抑制重新開機的結束時間。  
    **Windows 參考文件**：[Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **預設**：下午 5 點  

- **在排定的時間自動安裝並重新啟動**：指定安裝的日期和時間。 如果未指定，則會在每日早上 3 點執行安裝，接著在 15 分鐘的倒數後重新啟動。 登入的使用者可以延遲倒數計時和重新啟動。  
  
  此選項支援其他設定。  
  **Windows 參考文件**：[Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  - **自動行為頻率**：使用此設定來排定何時安裝更新，包括週、日及時間。  
    **預設**：每週

  - **已排程的安裝日**：指定要在一週的哪一天安裝更新。  
    **預設**：任一天  

  - **已排程的安裝時間**：指定要在一天中的何時安裝更新。  
    **預設**：上午 3 點  

- **在沒有使用者控制的情況下自動安裝並重新開機**：當裝置未在使用中或以電池電源執行時自動下載更新，然後在自動維護期間安裝。 當需要重新啟動時，裝置會在未使用時重新啟動。 這個選項會將使用者控制窗格設為唯讀。  

- **重設為預設**：在執行 2018 年 10 月更新或更新版本的 Windows 10 電腦上還原原始的自動更新設定。  


### <a name="restart-checks"></a>重新啟動檢查  

- **預設**：允許  
- **Windows 參考文件**：[Update/SetEDURestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

此設定根據裝置的 Windows 版本會有不同的結果：  

- Windows 1703 及較舊版本：當您重新啟動裝置時，會進行一些檢查，包括檢查作用中的使用者、電池電量、執行中的遊戲等。 若要在重新啟動裝置時略過這些檢查，請選取 [略過]  。  
- 從 Windows 1709 版開始：在「使用時間」期間，不會針對更新執行下列程序：掃描、下載、安裝和重新啟動。 在「使用時間」之後，只要裝置通過電池檢查和電源檢查，便會執行更新程序，且可將裝置從睡眠喚醒、掃描、下載、安裝和重新開機。 如需詳細資訊，請參閱 [Update/SetEDURestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart)。  

### <a name="block-user-from-pausing-windows-updates"></a>防止使用者暫停 Windows 更新  

- **預設**：允許  
- **Windows 參考文件**：[Update/SetDisablePauseUXAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

允許或封鎖裝置使用者暫停更新的安裝。 

### <a name="block-user-from-scanning-for-windows-updates"></a>防止使用者掃描 Windows 更新  
 - **預設**：允許
 - **Windows 參考文件**：[Update/SetDisableUXWUAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisableuxwuaccess) 

指定要允許或封鎖使用者掃描 Windows Update 的權限。 例如，如果您設定「封鎖」  ，則使用者無法存取 Windows Update 掃描、下載及安裝功能。  

### <a name="require-users-approval-to-restart-outside-of-work-hours"></a>要求使用者核准以在上班時間外重新啟動  

- **預設**：未設定  
- **Windows 參考文件**：[Update/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
選取 [必要]  以要求使用者核准裝置在上班時間外重新啟動。  
   
### <a name="remind-user-prior-to-required-auto-restart-with-dismissible-reminder-hours"></a>使用可關閉的提醒，在必要的自動重新開機之前提醒使用者 (小時)  

- **預設**：預設不會設定此選項，且不會向使用者顯示提醒  。  
- **Windows 參考文件**：[Update/ScheduleRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

指定要在自動重新啟動前，提前多少時間向使用者顯示有關該重新啟動的可關閉通知。 支援 **2**、**4**、**8**、**12** 或 **24** 小時的值。  

### <a name="remind-user-prior-to-required-auto-restart-with-permanent-reminder-minutes"></a>使用永久提醒，在必要的自動重新開機之前提醒使用者 (分鐘)  

- **預設**：預設不會設定此選項，且不會向使用者顯示提醒  。  
- **Windows 參考文件**：[Update/ScheduleImminentRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning) 

指定要在自動重新啟動前，提前多少時間向使用者顯示有關該重新啟動的不可關閉警告。 支援 **15**、**30** 或 **60** 分鐘的值。  

### <a name="windows-update-notification-level"></a>Windows Update 通知層級  
- **預設**：使用預設 Windows Update 通知 
- **Windows 參考文件**：[Update/UpdateNotificationLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updatenotificationlevel)

指定使用者看到的 Windows Update 通知層級。 此設定不會控制如何及何時下載並安裝更新。

### <a name="allow-user-to-restart-engaged-restart"></a>可讓使用者重新啟動 (預約重新啟動)  

- **預設**：未設定  
- **Windows 參考文件**：不適用   
- **Windows 版本**：支援 Windows 10 1803 版和更新版本  

  > [!NOTE]  
  > Windows 10 1809 版導入額外的重新啟動設定，可讓不同的設定套用至功能和品質更新。 不過，由 Intune 管理的設定無法分別套用至不同的更新類型。 相反地，Intune 會為功能和品質更新套用相同的值。  

當設定為 [必要]  時，您可以使用 Windows 10 更新的預約重新啟動選項。 這些選項可協助裝置使用者在安裝需要重新啟動的更新之後，管理重新啟動裝置的時機。  

如需此選項的詳細資訊，請參閱 Windows 10 文件中的[預約重新啟動](https://docs.microsoft.com/windows/deployment/update/waas-restart#engaged-restart) \(機器翻譯\) 以部署更新。  

下列設定用來控制預約重新啟動動作的發生時機。  

- **在自動重新啟動後將使用者轉換至預約重新啟動 (天數)**  
  - **預設**：預設並未設定此選項，但支援 **2** 到 **30** 的值。  
  - **Windows 參考文件**：[Update/EngagedRestartTransitionSchedule](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestarttransitionschedule)  
  指定在安裝更新之後，直到裝置進入預約重新啟動行為要多少時間。 在設定的天數之後，使用者會收到重新啟動裝置的提示。  

- **延遲預約重新啟動提醒 (天數)**  
  - **預設**：預設並未設定此選項，但支援 **1** 到 **3** 的值。  
  - **Windows 參考文件**：[Update/EngagedRestartSnoozeSchedule](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestartsnoozeschedule)  
  指定重新啟動提示可延遲多少時間。  在延遲期間之後，會再次顯示重新啟動提示。 使用者可以繼續延遲提醒，直到達到安裝期限為止。  

- **設定暫止重新啟動的期限 (天數)**  
  - **預設**：預設並未設定此選項，但支援 **2** 到 **30** 的值。  
  - **Windows 參考文件**：[Update/EngagedRestartDeadline](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestartdeadline)  
  指定預約重新啟動行為開始後，在裝置強制執行必要重新啟動之前的等候天數上限。 此重新啟動會提示使用者儲存工作。

### <a name="delivery-optimization-download-mode"></a>傳遞最佳化下載模式  

[傳遞最佳化] 不再是 [軟體更新] 下 [Windows 10 更新通道] 的其中一項設定。 現在會透過裝置設定來設定傳遞最佳化。 不過，您仍然可以在主控台中使用先前的設定。 您可以將先前的設定編輯為「未設定」  來移除這些設定，但無法修改這些設定。 

若要避免新原則與舊原則之間的衝突，請參閱[從現有更新通道移動到傳遞最佳化](delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization)，然後將您的設定移至傳遞最佳化設定檔。
