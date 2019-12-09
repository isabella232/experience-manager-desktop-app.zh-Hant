---
title: AEM案頭應用程式1.x版最佳實務
description: Adobe Experience manager案頭應用程式1.x版的主要功能和建議使用。
uuid: ba8fbc74-e1ad-4085-a031-ffd317628ba6
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: 57d5cd78-abce-4ede-a50e-7c161ddb43ae
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ad5337c8e1697d0a37d3020d25802dc1d732f320

---


# AEM案頭應用程式v1.x最佳實務 {#aem-desktop-app-best-practices}

## 概覽 {#overview}

Adobe Experience Manager(AEM)案頭應用程式會將您的數位資產管理(DAM)解決方案連結至您的案頭，讓您可以直接在案頭上開啟AEM網頁UI中可用的檔案。 如果您從案頭儲存資產，資產會上傳至AEM的適當位置。

AEM案頭應用程式讓您不必在AEM中更新不正確的本機副本或更新錯誤資產。 案頭應用程式的簡單好用工作流程，是使用案頭作業系統提供的網路共用技術來啟用的。

案頭應用程式會將AEM Assets儲存庫以網路共用的形式載入案頭。 因此，資料夾和檔案會像本地檔案一樣顯示。 不過，建議您不要直接在Finder或Explorer中已載入網路共用的案頭上執行數位資產管理作業。 Adobe建議您改用AEM Assets Web UI來執行操作，例如複製或移動大量資產。

>[!NOTE]
>
>在閱讀本檔案之前，您可以先閱讀整體 [AEM和Creative cloud整合的最佳實務](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-integration-best-practices.html) ，以取得主題的更高階概觀。

## AEM desktop app architecture {#aem-desktop-app-architecture}

AEM案頭應用程式使用WebDAV(Windows)或SMB(Mac)網路共用來載入網路共用。 掛載的網路共用僅為本地共用。 AEM案頭應用程式會截取呼叫（開啟、讀取、寫入），並提供其他本機快取。 它可將遠端呼叫轉譯至AEM Assets伺服器，以最佳化AEM HTTP請求。 下圖說明AEM案頭應用程式架構。

![AEM案頭應用程式架構](assets/chlimage_1.png)

儲存檔案時的額外寫入快取會先將檔案儲存在本機（以免使用者等待網路傳輸）。 然後，在預先定義的延遲（30秒）後，檔案會在背景上傳至AEM，然後資產會上傳至AEM。 AEM案頭應用程式提供UI，用於監控背景檔案上傳的狀態。

## 建議使用AEM案頭應用程式 {#recommended-use-of-aem-desktop-app}

AEM案頭應用程式的主要功能包括：

* 從案頭上的AEM Assets網頁UI開啟檔案：從網頁UI，您可以在案頭上顯示資產（在Finder、Explorer中），或使用案頭應用程式開啟資產。
* 登出和登入：資產可以勾出以進行編輯，在AEM Assets中會標籤為使用者鎖定。 編輯後，可以簽入資產以解除鎖定。
* 儲存檔案的變更：您儲存至網路共用中檔案的任何變更都會自動上傳至AEM，並建立新版本。
* 將連結資產置於其他檔案：在Creative Cloud（PS、ID、AI等）等應用程式中，您可以將外部檔案置入為連結（例如，您可以將影像置入InDesign檔案）。 在這種情況下，網路共用載入可讓您瀏覽並從AEM選取資產以放置位置。 放置連結的檔案也適用於某些非Adobe應用程式，例如MS Office。
* AEM中的參考解析度：如果置入的檔案和具有連結的主檔案都儲存在AEM中，它可以自動提供有關資產參考的伺服器端資訊。
* 從案頭存取資產：在已載入的網路共用中，內容相關選單提供「更多資訊」對話方塊（較大的預覽、關鍵中繼資料），以及在AEM UI中開啟資產的功能。
* 大量上傳大型、階層式資料夾：如果您使用AEM UI中的「建立&gt;檔案夾上傳」選項來上傳資產，AEM案頭應用程式會將選取的檔案夾階層上傳到背景的AEM。 您可在案頭應用程式中使用專用的UI來監控上傳進度。

## 不當使用AEM案頭應用程式 {#inappropriate-use-of-aem-desktop-app}

* 請勿使用AEM案頭應用程式來管理案頭上的資產。 AEM案頭應用程式未建立為網路磁碟機的取代。 請改用下列功能：
   * AEM Assets網頁UI，用於數位資產管理（尋找／共用資產、中繼資料、複製／移動等）
   * AEM案頭應用程式資料夾上傳以上傳大型的階層式資料夾

* 請勿將AEM案頭應用程式視為AEM Assets的「案頭同步」用戶端。 AEM案頭應用程式的主要優點在於，它提供對整個儲存庫的「虛擬」存取權，而案頭同步應用程式通常只同步屬於一位使用者的資產。 AEM案頭應用程式提供一定程度的快取和背景上傳；不過，它的運作方式與一般的「同步」應用程式（例如Adobe Creative cloud案頭應用程式或Microsoft oneDrive）非常不同。
* 請勿經常使用AEM案頭應用程式網路磁碟機來儲存資產。 所有儲存作業都會傳輸至AEM Assets。 因此，直接在已載入的AEM Assets儲存庫中執行密集編輯作業是不現實的。 直接在掛載的儲存庫中編輯資產時，會使用不相關的版本建立資產的時間軸，並在伺服器上施加額外的開銷。
* 請勿使用AEM案頭應用程式，將大量資料從一個AEM例項移轉至另一個AEM例項。 請參閱遷移指 [南](https://helpx.adobe.com/experience-manager/6-4/assets/using/assets-migration-guide.html) ，以規劃和執行資產遷移。 相反地，案頭應 [用程式支援在](use-app-v1.md#bulkupload) AEM中首次大量上傳大量資產。

## 針對選定使用案例的建議 {#recommendations-for-selected-use-cases}

### 為創意使用者取用資產 {#access-to-assets-for-creative-users}

AEM案頭應用程式提供對整個DAM存放庫的虛擬存取權——而且案頭上的創意使用者在案頭上尋找並存取適當資產可能會很複雜。 使用這些最佳實務來簡化這些作業。

* 使用AEM Assets Web UI中的協作功能，讓創意使用者更直接地存取適當的資產。 其中包括共用資料夾或系列、提供智慧型系列（儲存的搜尋），或傳送通知及指向適當資產。 然後，創意使用者就可以在網頁UI中使用案頭動作，快速存取案頭上的這些資產。
* 考慮資產的適當權限（存取控制），以簡化創意使用者在DAM儲存庫中檢視的作業，基本上限制他們僅能存取所需／感興趣的資產：

   * 某些與創意使用者無關的區域，可能會因為使用者群組而遭拒，以便從其檢視中移除，桌上型電腦也會拒絕
   * DAM中的大部分資產都是最終資產，不是為了變更——這些資產應為創意使用者唯讀
   * 只有需要變更／潤飾的資產才應為創意使用者啟用寫入功能。 有些組織會使用AEM projects及其建立的檔案夾來代管仍受變更影響的資產。

### 搜尋資產 {#searching-assets}

要搜索要在案頭上開啟的檔案：

* 使用AEM Assets網頁UI來尋找資產。 AEM Assets中的搜尋功能不僅強大（搜尋Facet、儲存的搜尋），還提供其他功能以尋找正確的資產。 這些功能包括其他篩選器，例如根據狀態（核准、到期）、系列、工作、通知，以及與其他使用者／群組共用資料夾／系列的能力來搜尋資產。
* 找到資產後，請使用AEM UI中的「案頭動作」來存取案頭上的資產。

### 更新使用AEM案頭應用程式開啟的資產 {#updating-assets-opened-using-aem-desktop-app}

如果您直接在從AEM Assets對應至本機網路共用的位置編輯資產，則每次在案頭上儲存資產時，資產都會上傳至AEM。 此外，AEM會建立版本並產生轉譯。

如果儲存在AEM中的資產需要更新：

* 對於 **次要更新**，例如核准程式中的次要潤飾要求：

   * 將檔案取出並在案頭上開啟
   * 更新檔案
   * 儲存更新的版本。 資產會更新，時間軸會顯示原始版本以供比較

* 對於 **重大更新**，例如需要小型創意WIP週期的變更請求：

   * 使用「顯現」選項在案頭上開啟適當的檔案夾
   * 將檔案複製至WIP檔案夾，而不在對應的AEM Assets共用範圍內（例如，將檔案複製到與Adobe Creative cloud案頭應用程式同步的檔案夾）
   * 處理檔案並間歇性儲存檔案。 變更不會儲存至AEM Assets
   * 編輯完成後，請移動、複製或儲存從AEM映射的檔案，以將其上傳為新版本

## 網路效能 {#network-performance}

使用AEM案頭應用程式的使用者可享有的良好體驗，很大程度上取決於其桌上型電腦和AEM伺服器之間良好、穩定的網路連線，以及針對良好效能而調整的伺服器，尤其是有關上傳和更新資產的伺服器。 這些建議適用於組織中的網路/IT團隊。

### 網路考量 {#network-considerations}

若要瞭解有關AEM Assets網路設定的最佳實務，請參閱 [AEM Assets網路考量事項檔案](https://helpx.adobe.com/experience-manager/6-4/assets/using/assets-network-considerations.html) 。 協助使用者最佳化AEM案頭應用程式體驗的一些重要方面包括：

* **** 使用正確配置的Dispatcher :使用AEM Dispatcher以取得其他安全性，並確保已針對 [AEM案頭應用程式連線設定此AEM案頭應用程式，以便在Dispatcher後方進行AEM](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html#ConnectingtoAEMBehindaDispatcher)

* **** 節省頻寬：在Mac上的Finder中關閉圖示預覽——使用Finder瀏覽已掛載的儲存庫時，請考慮。 Finder會要求每個檔案產生預覽，並導致案頭應用程式在本機下載及快取資產。 請注意，在節省頻寬的同時，它也會降低案頭用戶的使用體驗，因此在使用具有大資產和／或有限頻寬的儲存庫時，應該這樣做。

>[!NOTE]
>
>若要關閉圖示預覽，請在Finder中移至「檢視」，選取「檢視選項」，然後取消勾選「顯示圖示預覽」選項。 這隻適用於目前的資料夾——若要將它設為預設值，請按一下同一視窗中的「使用為預設值」按鈕。

### 最佳化伺服器效能 {#optimizing-server-performance}

若要瞭解AEM Assets伺服器如何最佳化以獲得效能，請參閱 [AEM Assets Performance Tuning Guide](https://helpx.adobe.com/in/experience-manager/6-4/assets/using/performance-tuning-guidelines.html)。 AEM案頭應用程式伺服器效能的一些重要方面是最佳化工作流程設定，以便在資產上傳時發揮良好效能：

* **** 更具效能的資產上傳：將「 [AEM資產更新」工作流程模型設定為「暫時」](https://helpx.adobe.com/experience-manager/6-4/assets/using/performance-tuning-guidelines.html#Workflows)。

* **** 限制上傳的伺服器CPU:請確定已正確設定最大並行工作流程工作參數，如此上傳不會耗盡所有CPU。