---
title: 案頭應用1.10版最佳實踐
description: 關鍵功能和建議使用 [!DNL Adobe Experience Manager] 案頭應用1.10版。
exl-id: 5de06b33-c05c-47eb-b884-408b6f9afc94
source-git-commit: 7a7236c36f615e97e9d040e6139368a931eb579e
workflow-type: tm+mt
source-wordcount: '1676'
ht-degree: 0%

---

# AEM案頭應用v1.10最佳做法 {#aem-desktop-app-best-practices}

## 概觀 {#overview}

[!DNL Adobe Experience Manager] 案頭應用將您的數字資產管理(DAM)解決方案與您的案頭連結，以便您可以直接在案頭上打AEM開web UI中可用的檔案。 如果從案頭保存資產，則會將其上載AEM到相應位置。

桌AEM面應用消除了您在中更新不正確的本地副本或更新錯誤資產的機AEM會。 案頭應用的易用工作流使用案頭作業系統提供的網路共用技術來啟用。

案頭應用將AEM Assets儲存庫作為網路共用裝載在案頭上。 因此，資料夾和檔案看起來就像是本地檔案。 但是，建議不要直接從Finder或Explorer中掛載的網路共用中的案頭執行數字資產管理操作。 相反，Adobe建議您使用AEM AssetsWeb UI執行操作，如複製或移動大量資產。

>[!NOTE]
>
>在閱讀此文檔之前，您可以查看 [AEM和Creative Cloud整合最佳做法](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/aem-cc-integration-best-practices.html) 的子菜單。

## AEM案頭應用架構 {#aem-desktop-app-architecture}

案頭AEM應用使用WebDAV(Windows)或SMB(Mac)網路共用來裝載網路共用。 掛載的網路共用僅是本地共用。 案頭AEM應用會截取調用（開啟、讀取、寫入），並提供附加的本地快取。 它將遠程呼叫轉換到AEM Assets伺服器，以AEM優化HTTP請求。 下圖描述了案頭應AEM用體系結構。

![AEM案頭應用架構](assets/arch_v1.png)

*圖：案頭應用架構*

保存檔案時寫入時的附加快取會導致檔案首先在本地保存（這樣用戶就不會等待網路傳輸）。 然後，在預定義延遲(30s)之後，檔案在後AEM台上載到，然後資產被上載到AEM。 案頭應AEM用提供用於監視後台檔案上載狀態的UI。

## 建議使用桌AEM面應用 {#recommended-use-of-aem-desktop-app}

案頭應用的AEM關鍵功能包括：

* **在案頭上開啟來自AEM AssetsWeb UI的檔案**。 從Web UI中，可以顯示案頭上的資產（在Finder、Explorer中），或使用案頭應用程式開啟資產。

* **簽出和簽入**。 可以簽出資產進行編輯，這些資產被標籤為已鎖定，供AEM Assets用戶使用。 編輯後，可以簽入資產以解鎖資產。

* **保存對檔案的更改**。 您保存到網路共用中檔案的任何更改都會自動上載AEM到，並且會建立新版本。

* **將連結的資產置於其他文檔中**。 在應用程式中，如Creative Cloud([!DNL Adobe Photoshop]。 [!DNL Adobe InDesign], [!DNL Adobe Illustrator])，可以將外部檔案作為連結放置。 例如，可以將影像放入InDesign文檔。 在這種情況下，網路共用裝載允許您瀏覽並從中選擇資AEM產以放置。 放置連結的檔案也適用於某些非Adobe應用，如MS Office。

* **中的引用解AEM析**。 如果兩者都儲存了已放置檔案和帶連結的主檔案，則AEM它可自動提供有關資產引用的伺服器端資訊。

* **從案頭訪問資產**。 在掛載的網路共用中，上下文菜單提供 [!UICONTROL More Info] 對話框（更大的預覽、鍵元資料），以及在UI中開啟資AEM產的能力。

* **批量上載大型分層資料夾**。 如果您使用UI中的「建立」>「資料夾上載」選項AEM來上載資產，AEM則案頭應用會將所選資料夾層次結構上載到AEM後台。 可以使用案頭應用中的專用UI監視上載進度。

## 案頭應用AEM的使用不當 {#inappropriate-use-of-aem-desktop-app}

* 不要使用桌AEM面應用程式管理案頭上的資產。 未AEM將案頭應用作為網路驅動器的替代。 請改用以下功能：

   * AEM AssetsWeb UI，用於數字資產管理（查找或共用資產、元資料，以及複製或移動）。

   * AEM案頭應用 [!UICONTROL Folder Upload] 上載大型分層資料夾。

* 不要將桌AEM面應用視為AEM Assets的「案頭同步」客戶端。 此處案頭應AEM用的主要優點是它提供了對整個儲存庫的「虛擬」訪問，而案頭同步應用程式通常只同步屬於一個用戶的資產。 AEM案頭應用提供一定程度的快取和後台上傳；不過，它與典型的「同步」應用程式(如Adobe Creative Cloud案頭應用或MicrosoftOneDrive)的工作方式截然不同。

* 不要經常使AEM用案頭應用網路驅動器保存資產。 所有保存操作都被傳輸到AEM Assets。 因此，直接在裝載的AEM Assets儲存庫中執行密集編輯操作是不現實的。 直接在已裝載的儲存庫中編輯資產會使用無關版本來建立資產的時間線，並會在伺服器上施加額外的開銷。

* 不要使用AEM案頭應用程式將大量資料從一個實例遷移AEM到另一個實例。 查看 [遷移指南](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/assets-migration-guide.html) 計畫並執行資產遷移。 相比之下，案頭應用 [支援批量上載](use-app-v1.md#bulkupload) 在2014年 [!DNL Adobe Experience Manager]。

## Recommendations用於選定使用案例 {#recommendations-for-selected-use-cases}

### 為創意用戶訪問資產 {#access-to-assets-for-creative-users}

案頭應AEM用提供了對整個DAM儲存庫的虛擬訪問 — 案頭上的創意用戶查找和訪問其案頭上的正確資產可能很複雜。 使用這些最佳做法來簡化這些操作。

* 使用AEM AssetsWeb UI中的協作功能，讓創意用戶更直接地訪問正確的資產。 其中包括共用資料夾或集合、提供智慧集合（保存的搜索）或發送帶有指向正確資產的指針的通知。 創意用戶隨後可以使用Web UI中的案頭操作快速訪問其案頭上的這些資產。

* 考慮對資產（訪問控制）的適當權限，以簡化創意用戶在DAM儲存庫中的視圖，基本上限制他們只訪問他們需要或感興趣的資產：

   * 某些與創意用戶無關的區域可能會被拒絕，因為用戶組將其從其視圖中刪除，案頭上也會刪除。

   * DAM中的多數資產都是最終資產，並不是為了改變 — 這些資產應該只對有創意的用戶是只讀的。

   * 只有需要更改或修飾的資產才應為創意用戶啟用寫操作。 某些組織使AEM用「項目」及其建立的資料夾來托管仍受更改影響的資產。

### 搜尋資產 {#searching-assets}

搜索要在案頭上開啟的檔案：

* 使用AEM AssetsWeb UI查找資產。 不僅在AEM Assets搜索功能強大（搜索小面、保存的搜索），還提供了查找正確資產的附加功能。 這些包括其他篩選器，如根據狀態（批准、到期）、收集、任務、通知以及與其他用戶/組共用資料夾/收集來搜索資產的功能。

* 找到資產後，使用UI中的「案頭操作」AEM訪問案頭上的資產。

### 正在更新使用案頭應AEM用開啟的資產 {#updating-assets-opened-using-aem-desktop-app}

如果直接在從AEM Assets映射到本地網路共用的位置編輯資產，則每次在案頭上AEM保存該資產時，都會將其上載到。 此外，還創AEM建版本並生成格式副本。

如果儲存在中的資AEM產需要更新：

* 對於 **次要更新**，例如審批流程中的次要修改請求：

   * 簽出檔案並在案頭上將其開啟。

   * 更新檔案。

   * 保存更新的版本。 資產將被更新，時間軸顯示原始版本以供比較。

* 對於 **主要更新**，例如需要小的建立WIP週期的變更請求：

   * 使用「顯示」選項開啟案頭上的相應資料夾。

   * 將檔案複製到映射的AEM Assets共用之外的WIP資料夾(例如，將檔案複製到與Adobe Creative Cloud案頭應用同步的資料夾)。

   * 處理檔案並間歇性地保存。 更改不會保存到AEM Assets。

   * 編輯完成後，移動、複製或保存映射自的檔案，AEM以將其作為新版本上載。

## 網路效能 {#network-performance}

對於使用案頭應用的AEM用戶來說，良好的體驗很大程度上取決於其台式機和伺服器之間良好、穩定的網路連接AEM，以及為獲得良好效能而調整的伺服器，尤其是在上載和更新資產方面。 這些建議針對組織中的網路/IT團隊。

### 網路注意事項 {#network-considerations}

要瞭解有關AEM Assets網路配置的最佳實踐，請參閱 [如何批量遷移資產](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/assets-migration-guide.html) 的子菜單。 幫助用戶優化案頭應AEM用體驗的一些重要方面包括：

* **使用正確配置的Dispatcher**。 使用AEMDispatcher進行其他安全性，並確保為 [桌AEM面應用連接AEM到調度程式後](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher)

* **節省頻寬**。 使用Finder瀏覽已掛載的儲存庫時，請考慮在Mac的Finder中關閉表徵圖預覽。 Finder請求每個檔案生成預覽，並使案頭應用程式本地下載和快取資產。 請注意，在節省頻寬的同時，它還會減少案頭上用戶的用戶體驗，因此在使用具有大資產和/或有限頻寬的儲存庫時應該這樣做。

>[!NOTE]
>
>要關閉表徵圖預覽，請在Finder中轉到 [!UICONTROL View]選中 [!UICONTROL View Options]，然後取消檢查 [!UICONTROL Show icon preview] 的雙曲餘切值。 這僅適用於當前資料夾 — 要使其成為預設值，請按一下 [!UICONTROL Use as default] 的子菜單。

### 優化伺服器效能 {#optimizing-server-performance}

要瞭解如何優化AEM Assets伺服器的效能，請參閱 [AEM Assets效能調整指南](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/performance-tuning-guidelines.html)。 案頭應用伺服器效能的一些重要方AEM面是優化工作流配置，以便它在資產上傳方面表現良好：

* **更多效能資產上載**。 配置 [資產AEM更新工作流模型為暫時](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/performance-tuning-guidelines.html)。

* **限制上載的伺服器CPU**。 確保正確設定了最大並行工作流作業參數，這樣上載不會耗盡所有CPU。
