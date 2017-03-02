---
title: "取得 Apple MDM Push Certificate | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰了解取得 Apple MDM Push Certificate 以利用 Intune 管理 iOS 裝置的步驟。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: a6ac1074055892f5ec42fb4057e47e9349fb5a33
ms.lasthandoff: 02/15/2017


---

# <a name="get-an-apple-mdm-push-certificate"></a>取得 Apple MDM Push Certificate 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune 可啟用 iPad、iPhone 和 Mac OS X 裝置的行動裝置管理 (MDM)，且可提供使用者對公司電子郵件和應用程式的存取。 Intune 需要 Apple Push Notification Service (APNs) 憑證，才能管理 iOS 和 Mac 裝置。 將憑證新增至 Intune 之後，使用者即可安裝公司入口網站應用程式，來註冊其裝置，或是您可以設定公司擁有的 iOS 裝置管理。

**取得 Apple MDM Push Certificate：**<br>
在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。 在 Intune 刀鋒視窗上，選擇 [註冊裝置]  >  [Apple MDM Push Certificate]，並依照 Azure 入口網站中的步驟編號進行，如下所示。

**步驟 1.需要下載 Intune 憑證簽署要求，才可建立 Apple MDM Push Certificate。**<br>
選取 [下載您的 CSR]，在本機下載並儲存 .csr 檔案。 .csr 檔案用來向 Apple Push Certificates Portal 要求信任關係憑證。

**步驟 2.建立 Apple MDM Push Certificate。**<br>
選取 [建立您的 MDM Push Certificate]，以前往 Apple Push Certificates 入口網站。 以公司 Apple ID 登入，使用 .csr 檔案建立推播憑證的憑證。 於 Apple 的 Push Certificates 入口網站上選擇 [上傳] 之後，您會收到一個 .json 檔案。 請務必為推播憑證使用此檔案。 完成下載，並回到 Apple Push Certificates 入口網站的 「Certificates for Third-Party Servers」 (協力廠商伺服器的憑證)，然後選擇 **[下載]**。 下載推播憑證 (.pem 檔案)，並於本機儲存該檔案。
注意

**步驟 3.輸入用以建立 Apple MDM Push Certificate 的 Apple ID。**

**步驟 4.瀏覽至 Apple MDM Push Certificate 以進行上傳。**<br>
前往憑證 (.pem) 檔案，選擇 [開啟]，然後選擇 [上傳]。 使用推播憑證，透過將原則推送到已註冊的行動裝置，Intune 即可註冊和管理 iOS 裝置。
