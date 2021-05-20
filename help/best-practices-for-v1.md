---
title: 案頭應用程式v1.10最佳實務
description: 主要功能，並建議使用 [!DNL Adobe Experience Manager] 案頭應用程式1.10版。
exl-id: 5de06b33-c05c-47eb-b884-408b6f9afc94
source-git-commit: 78f18e68178f711d925d7e308822c657087d009a
workflow-type: tm+mt
source-wordcount: '1674'
ht-degree: 0%

---

# AEM案頭應用程式v1.10最佳作法{#aem-desktop-app-best-practices}

## 概覽 {#overview}

[!DNL Adobe Experience Manager] 案頭應用程式會將您的數位資產管理(DAM)解決方案與案頭連結，讓您可以直接在案頭開啟AEM網頁UI中可用的檔案。如果您從案頭儲存資產，資產會上傳至適當位置的AEM。

AEM案頭應用程式可讓您不必在AEM中更新錯誤的本機副本或更新錯誤的資產。 案頭應用程式的簡單易用工作流程，採用案頭作業系統提供的網路共用技術。

案頭應用程式會將AEM Assets存放庫以案頭上的網路共用形式載入。 因此，資料夾和檔案會以本地方式顯示。 不過，不建議直接從Finder或Explorer中已裝入網路共用的案頭執行數位資產管理操作。 相反地，Adobe建議您使用AEM Assets Web UI來執行作業，例如複製或移動大量資產。

>[!NOTE]
>
>閱讀本檔案前，您可以先檢閱整體[AEM和Creative Cloud整合最佳實務](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/aem-cc-integration-best-practices.html)，以了解主題的更高層級概覽。

## AEM案頭應用程式架構{#aem-desktop-app-architecture}

AEM案頭應用程式使用WebDAV(Windows)或SMB(Mac)網路共用來裝載網路共用。 掛載的網路共用僅為本地。 AEM案頭應用程式會截取呼叫（開啟、讀取、寫入），並提供額外的本機快取。 它會將遠端呼叫轉譯為AEM Assets伺服器，以最佳化AEM HTTP請求。 下圖描述了AEM案頭應用程式架構。

![AEM案頭應用程式架構](assets/arch_v1.png)

*圖：案頭應用程式架構*

儲存檔案時的額外寫入快取會先將檔案儲存在本機（使使用者不等待網路傳輸）。 接著，在預先定義的延遲（30秒）後，檔案會在背景上傳至AEM，然後資產上傳至AEM。 AEM案頭應用程式提供UI，可監控背景檔案上傳的狀態。

## 建議使用AEM案頭應用程式{#recommended-use-of-aem-desktop-app}

AEM案頭應用程式的主要功能包括：

* **從案頭上的AEM Assets Web UI開啟檔案**。從Web UI中，您可以在案頭上顯示資產（在Finder、Explorer中），或使用案頭應用程式開啟資產。

* **結帳和結帳**。資產可簽出以進行編輯，但在AEM Assets中會標示為使用者鎖定。 編輯後，可以簽入資產以解除鎖定。

* **儲存檔案的變更**。您儲存至網路共用中檔案的任何變更都會自動上傳至AEM，並建立新版本。

* **將連結的資產放入其他檔案**。在Creative Cloud（[!DNL Adobe Photoshop]、[!DNL Adobe InDesign]和[!DNL Adobe Illustrator]）等應用程式中，您可以將外部檔案作為連結進行放置。 例如，您可以將影像放入InDesign檔案中。 在此情況下，網路共用裝載可讓您瀏覽並從AEM中選取資產以放置。 放置連結的檔案也適用於某些非Adobe應用程式，如MS Office。

* **AEM中的參考解析度**。如果置入的檔案和具有連結的主檔案都儲存在AEM中，則會自動提供資產參考的伺服器端資訊。

* **從案頭存取資產**。在掛載的網路共用中，內容功能表提供[!UICONTROL More Info]對話方塊（更大的預覽、索引鍵中繼資料），以及在AEM UI中開啟資產的功能。

* **大量上傳大型的階層式資料夾**。如果您使用AEM UI中的「建立>資料夾上傳」選項來上傳資產，AEM案頭應用程式會將選取的資料夾階層上傳至背景的AEM。 您可在案頭應用程式中使用專用的UI來監控上傳進度。

## 不當使用AEM案頭應用程式{#inappropriate-use-of-aem-desktop-app}

* 請勿使用AEM案頭應用程式從案頭管理資產。 AEM案頭應用程式未建置為取代網路磁碟。 請改用下列功能：

   * AEM Assets網頁UI，適用於數位資產管理（尋找或共用資產、中繼資料，以及複製或移動）。

   * AEM案頭應用程式[!UICONTROL Folder Upload]上傳大型的階層式資料夾。

* 請勿將AEM案頭應用程式視為AEM Assets的「案頭同步」用戶端。 這裡AEM案頭應用程式的主要優點是，它提供對整個存放庫的「虛擬」存取，而案頭同步應用程式通常只同步屬於一個使用者的資產。 AEM案頭應用程式提供一定程度的快取和背景上傳；不過，它的運作方式與一般的「同步」應用程式(如Adobe Creative Cloud案頭應用程式或Microsoft OneDrive)非常不同。

* 請勿頻繁使用AEM案頭應用程式網路磁碟來儲存資產。 所有儲存操作都會傳送至AEM Assets。 因此，直接在已裝入的AEM Assets存放庫中執行密集編輯作業是不切實際的。 直接在裝載的存放庫中編輯資產會以無關版本建立資產的時間軸，並在伺服器上施加額外的額外開銷。

* 請勿使用AEM案頭應用程式，將大量資料從一個AEM例項移轉至另一個例項。 請參閱[移轉指南](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/assets-migration-guide.html)以規劃及執行資產移轉。 相反地，案頭應用程式[支援在[!DNL Adobe Experience Manager]中首次大量上傳](use-app-v1.md#bulkupload)大量資產。

## Recommendations供選定使用案例{#recommendations-for-selected-use-cases}

### 創意使用者的資產存取權{#access-to-assets-for-creative-users}

AEM案頭應用程式提供對整個DAM存放庫的虛擬存取，而案頭上的創意使用者在案頭上尋找及存取適當資產，可能會很複雜。 請使用這些最佳實務來簡化操作。

* 使用AEM Assets Web UI中的共同作業功能，讓創意使用者能更直接存取正確的資產。 共用資料夾或集合、提供智慧型集合（已儲存的搜尋），或傳送含有指標至正確資產的通知等。 創意內容使用者可在網頁UI中使用案頭動作，快速存取案頭上的這些資產。

* 請考量資產的適當權限（存取控制），為創意使用者簡化DAM存放庫的檢視，基本上只限他們存取所需或感興趣的資產：

   * 某些與創意內容使用者無關的區域可能會被拒絕供其使用者群組使用，以便從其檢視中（也可在案頭上）移除。

   * DAM中的大部分資產都是最終資產，不是用於變更 — 創意使用者應為唯讀資產。

   * 只有需要變更或潤飾的資產，才應為創意使用者啟用。 有些組織會使用AEM專案及其建立的資料夾，來托管仍受變更影響的資產。

### 搜尋資產{#searching-assets}

要搜索要在案頭上開啟的檔案：

* 使用AEM Assets網頁UI來尋找資產。 AEM Assets中的搜尋不僅功能強大（搜尋Facet、已儲存的搜尋），也提供其他功能來尋找合適的資產。 這些功能包括其他篩選器，例如根據狀態（核准、到期）、集合、工作、通知，以及與其他使用者/群組共用資料夾/集合來搜尋資產的功能。

* 找到資產後，請使用AEM UI中的「案頭動作」來存取案頭上的資產。

### 更新使用AEM案頭應用程式{#updating-assets-opened-using-aem-desktop-app}開啟的資產

如果您直接在從AEM Assets對應至本機網路共用的位置編輯資產，則每次您將資產儲存在案頭時，資產都會上傳至AEM。 此外，AEM會建立版本並產生轉譯。

如果儲存在AEM中的資產需要更新：

* 對於&#x200B;**微幅更新**，例如批准流程中的微幅修訂請求：

   * 簽出該檔案並在案頭上將其開啟。

   * 更新檔案。

   * 儲存更新的版本。 資產會更新，時間軸會顯示原始版本以供比較。

* 對於&#x200B;**重大更新**，例如需要小型創作WIP週期的變更請求：

   * 使用「顯現」(Reveal)選項開啟案頭上的適當資料夾。

   * 將檔案複製到對應AEM Assets共用以外的WIP資料夾(例如，將檔案複製到與Adobe Creative Cloud案頭應用程式同步的資料夾)。

   * 處理檔案並間歇性儲存。 變更不會儲存至AEM Assets。

   * 完成編輯後，請移動、複製或儲存從AEM對應的檔案，以將其上傳為新版本。

## 網路效能{#network-performance}

使用AEM案頭應用程式的使用者的良好體驗，主要取決於其案頭與AEM伺服器之間良好、穩定的網路連線，以及針對良好效能（尤其是上傳和更新資產）而調整的伺服器。 這些建議適用於組織中的網路/IT團隊。

### 網路考量事項{#network-considerations}

若要了解AEM Assets網路設定的最佳實務，請參閱[AEM Assets網路考量事項](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/assets-migration-guide.html)檔案。 有助於為使用者最佳化AEM案頭應用程式體驗的重要方面包括：

* **使用已正確設定的Dispatcher**。使用AEM Dispatcher提供額外的安全性，並確保已將其設定為[AEM案頭應用程式連線至Dispatcher](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher)後面的AEM

* **節省頻寬**。在Mac上，使用Finder瀏覽已裝載的存放庫時，請考慮關閉Finder中的圖示預覽。 Finder要求每個檔案產生預覽，並導致案頭應用程式在本機下載和快取資產。 請注意，在節省頻寬的同時，也會降低案頭使用者的使用體驗，因此在使用具有大資產和/或有限頻寬的存放庫時，應該這樣做。

>[!NOTE]
>
>若要關閉圖示預覽，請在搜尋器中前往[!UICONTROL View]，選取[!UICONTROL View Options]，然後取消勾選[!UICONTROL Show icon preview]選項。 這僅適用於當前資料夾 — 若要將其設為預設資料夾，請按一下相同對話方塊中的[!UICONTROL Use as default]選項。

### 優化伺服器效能{#optimizing-server-performance}

要了解如何針對效能最佳化AEM Assets伺服器，請參閱[AEM Assets效能調整指南](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/performance-tuning-guidelines.html)。 AEM案頭應用程式伺服器效能的某些重要方面，是最佳化工作流程設定，以便對資產上傳執行效能良好：

* **更高效能的資產上傳**。將[AEM資產更新工作流程模型設定為暫時](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/performance-tuning-guidelines.html)。

* **限制上載的伺服器CPU**。請確保正確設定最大並行工作流作業參數，這樣上傳不會耗盡所有CPU。
