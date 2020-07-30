---
title: 使用AEM案頭應用程式1.x版。
description: 瞭解如何使用Adobe Experience Manager案頭應用程式1.x版，並最佳化您在案頭上使用資產的工作。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 67e117648de8298f78992afea5ae0962fd2c698b
workflow-type: tm+mt
source-wordcount: '2516'
ht-degree: 0%

---


# 使用AEM案頭應用程式v1.x {#use-aem-desktop-app-v1x}

使用「應用程式」,AEM中的資產可輕鬆在您的本機案頭上存取，並可用於任何案頭應用程式。 您可以在Mac Finder或Windows檔案總管中輕鬆顯示資產、在案頭應用程式中開啟並在本機變更——這些變更會儲存回AEM，並在儲存庫中建立新版本。

此類整合可讓組織中的不同角色集中管理AEM Assets中的資產，並在Creative Cloud和其他應用程式中存取資產，同時讓您輕鬆符合各種標準，包括品牌。

您使用AEM案頭應用程式v1的主要工作包括：

1. [連線AEM伺服器](#installandconnect)
1. [直接在案頭上開啟資產](#openondesktop)
1. [從案頭編輯及取出資產](#workonassets)
1. [大量上傳資產和檔案夾](#bulkupload)

如需各種建議的dos和don&#39;ts，請參閱使 [用應用程式的最佳實務](best-practices-for-v1.md)。 如果您使用應用程式時遇到問題，請參閱如何疑難排 [解AEM案頭](troubleshoot-app-v1.md)。

>[!NOTE]
>
>AEM案頭應用程式已在AEM 6.1版本中推出，稱為「AEM Assets Companion App」。

## 創意工作流程中的AEM案頭應用程式觸點 {#aem-desktop-app-touch-points-in-the-creative-workflow}

AEM Desktop應用程式與AEM Assets整合在您的創意工作流程中，並提供下列觸控點。

![AEM案頭應用程式觸點創意工作流程](assets/aem_desktopapp_workflow.png)

AEM案頭應用程式觸點創意工作流程

## 安裝AEM案頭應用程式並將其連接至AEM伺服器 {#installandconnect}

在您開始建立或編輯創意資產之前，請先將案頭應用程式與AEM Assets伺服器連接，以下載並上傳儲存庫中的資產。 執行下列工作：

1. [安裝應用程式](#installapp)。
1. [設定您的偏好設定](#inapppref) 和連線詳細資訊。
1. [連線至AEM伺服器](#connect) ，並將資產存放庫裝載為本機磁碟。
1. [在AEM伺服器上啟用案頭動作](#desktopactions) 。

AEM案頭應用程式使用HTTPS連線來連線至AEM伺服器，以強穩且安全地傳輸您的資產。

>[!NOTE]
>
>對於部分或全部的安裝與設定步驟，您可能需要AEM管理員或系統管理員的協助。

### 安裝應用程式 {#installapp}

若要使用AEM案頭應用程式，請確定您的AEM伺服器版本受AEM案頭應用程式支援。 下載適合您作業系統（Mac或Windows）的安裝檔（二進位），並安裝應用程式。

根據您的網路和系統首選項，可能需要進行詳細配置。 如需詳 [細資訊，請參閱「安裝及設定AEM案頭應用程式](install-configure-app-v1.md) 」。

1. 前往 [AEM Desktop應用程式下載頁面](https://helpx.adobe.com/experience-manager/kb/download-companion-app.html) ，並下載適合您作業系統的二進位檔。
1. 啟動下載的安裝檔案，並依照螢幕上的指示安裝應用程式。

   >[!NOTE]
   >
   >一次只能安裝一個AEM案頭應用程式執行個體並啟用。

### 瞭解應用程式內選項和偏好設定 {#inapppref}

應用程式可讓您設定連線與AEM伺服器中斷連線、檢視上傳狀態、管理本機快取等。 預設設定適用於應用程式的一般使用者。 您可以調整設定，讓應用程式和AEM伺服器的整合發揮更大效益。 下面將詳細說明各種設定。

**探索Assets** 開啟載入AEM Assets存放庫的本機磁碟機。 換言之，請探索您本機電腦上現在可用的資產。

**檢視資產狀態** ：當變更的資產上傳或新資產新增至AEM Assets存放庫時，應用程式會在背景上傳資產。 背景上傳可讓作業更順暢，您不必等到上傳完成，尤其是大型資產。 您可以將變更儲存在本機，而不必擔心。 應用程式會花一些時間將這些資產傳送至伺服器，視可用頻寬而定。 您可以檢查上傳的狀態，以及一些更基本的資訊。

**選項** ：從AEM Desktop應用程式托盤按一下／點選「選項」，以存取設定，在您的系統啟動時啟動應用程式； 在應用程式啟動時連線至AEM伺服器； 以及，更改安裝後AEM Assets可用的本地驅動器盤符。

**「進階>管理快取** 」您可以控制可用於本機快取的磁碟空間量。 來自AEM Assets伺服器的物件會在本機快取，以提供更順暢的體驗。 您可以變更預設值以符合您的需求。 此外，您也可以清除快取，重新擷取所有資產。 清除快取時，它會保留未儲存的變更。 未簽入AEM伺服器的任何資產都會保留且不會刪除。

### 連線至AEM伺服器 {#connect}

應用程式支援Mac和Windows上的Proxy設定。 應用程式啟動時會讀取設定。 如果您修改Proxy設定，請重新啟動應用程式，讓變更生效。

>[!NOTE]
>
>如果您修改Proxy設定，請重新啟動應用程式，讓變更生效。 否則，應用程式會繼續使用先前設定的代理伺服器。

1. 啟動AEM Desktop應用程式。 若要將您的AEM例項與應用程式對應，請以格式指定您的AEM伺服器 `https://[aem-server-url]:[port]`。

   ![在Mac上驗證並提供AEM伺服器URL](assets/aem_desktop_app_server_url.png)

1. 在登入畫面中，指定您例項的使用者名稱和密碼。 若要指定替代AEM例項，請選取 **[!UICONTROL Alternate Login URL]** 選項。

   ![在AEM Desktop的登入畫面上提供AEM伺服器認證](assets/chlimage_1-2.png)

### 在AEM網頁介面中啟用案頭動作 {#desktopactions}

從「資產」使用者介面中，您可以探索資產位置或結帳並開啟資產，以便在案頭應用程式中編輯。 這些選項稱為案頭操作，預設情況下不啟用。 請依照下列步驟進行啟用。

1. 在「資產」介面中，按一下／點選工具列右上角的「使用者」圖示。
1. 按一 **[!UICONTROL My Preferences]** 下以顯示對 **[!UICONTROL Preferences]** 話方塊。

   ![AEM介面與使用者偏好設定](assets/aem_ui_user_preferences.png)

1. 在「用戶首選項」對話框中，選擇 **[!UICONTROL Show Desktop Actions For Assets]**。 按一下 **[!UICONTROL Accept]**.

   ![勾選「顯示資產的案頭動作」以啟用案頭動作](assets/chlimage_1-3.png)

   *圖： 勾選「顯示資產的案頭動作」以啟用案頭動作。*

## 在案頭上存取和開啟資產 {#openondesktop}

當您按一下「 **開啟** 」以在本機電腦上開啟資產時，應用程式會將資產下載至其內部快取。 應用程式會啟動與已下載資產的檔案類型相關聯的原生案頭應用程式。

在Mac上，從內容選 **單選取** 「開啟」，以透過AEM案頭應用程式開啟資產。 在Windows上，從上下文選單選擇「在Web上開啟」以開啟資產。 在「資產狀態」視窗中，按一下／點選「在桌 ![面上開啟」圖示](assets/do-not-localize/aemassets_icon_openondesktop.png) ，以開啟資產。

若是Adobe InDesign(INDD)檔案，請從內容選 **[!UICONTROL Open]** 單中選取。 當您按一下此選項時，應用程式會將連結的資產下載到您的本機檔案系統，然後在Adobe InDesign中開啟INDD檔案。 此方法可確保在編輯INDD檔案時，必要的資產可在本機使用。

![使用AEM Desktop應用程式存取和開啟資產的內容選單選項](assets/aem_desktopapp_mac_context_menu.png)

*圖： 使用AEM案頭應用程式存取和開啟資產的內容選單選項。*

>[!NOTE]
>
>在Windows上，預 [設的Windows 7設定](https://support.microsoft.com/en-us/kb/2668751) ，會防止AEM案頭應用程式處理大於50 MB的資產。

>[!NOTE]
>
>Adobe建議您前往Mac上的Finder檢視選項，並停用已載入AEM Assets檔案夾的 **「顯示項目資訊**」、「顯示項目預覽 **」和「****** 顯示預覽」欄。 它改善了效能。

### AEM介面中的其他選項 {#additional-options-in-aem-assets}

將AEM Assets儲存庫對應至本機磁碟機後，您可以啟用其他圖示和「檔案夾上傳」功能，以針對已映射的資產和檔案夾顯示。

1. 開啟AEM Assets介面，並將指標暫留在資料夾或資產上，以在「卡片」檢視中將案頭動作顯示為快速動作。

   ![在「資產」UI中，開啟快速動作功能表以檢視案頭動作](assets/chlimage_1-4.png)

   *圖： 在「資產」UI中，開啟快速動作功能表以檢視案頭動作。*

   當您在選取資產後，或從資產頁面的工具列按一下工具列中的「案頭動作 **** 」圖示時，這些案頭動作也可供使用。

1. 若要在案頭應用程式中開啟與特定副檔名相關聯的資產，請按一下／點選「在案頭上開啟」快速動作「在案頭上 **開啟」圖示**![](assets/do-not-localize/aemassets_icon_openondesktop.png)。

   或者，從工具 **欄的** 「案頭動 **作** 」選單選擇「開啟」。

若要在本機檔案系統上找到特定資產，請按一下「顯 **示** 」快速動 ![作「顯示」圖示](assets/do-not-localize/aemassets_reveal_icon.png)。 或者，從工具 **欄的** 「案頭 **操作** 」菜單中選擇「顯示」。

## 瞭解資產狀態 {#understand-the-asset-statuses}

| ![Windows預設應用程式圖示](assets/do-not-localize/win_default.png) | 應用程式已連線至伺服器，且所有資產都會同步化。 |
--- |--- |
| ![Windows停用圖示](assets/do-not-localize/win_disabled.png) | 應用程式已啟動，但未與伺服器連線。 某些資產可能是擱置中的同步。 |
| ![Windows檔案同步表徵圖](assets/do-not-localize/win_sync.png) | 資產正在同步化。 正在上傳或下載檔案。 您可以在「資產狀態」窗口中查看確切狀態並暫停轉移。 |
| ![Windows重新連接表徵圖](assets/do-not-localize/win_refresh.png) | 應用程式正在嘗試重新連線。 可能是網路問題導致其斷開連接。 |

## 處理您的資產 {#workonassets}

### 從AEM網頁介面檢視資產 {#check-out-assets-from-the-aem-web-interface}

AEM Assets可讓您取出要編輯的資產，並在完成變更後將其存回。 結帳資產後，只有您可以編輯、註解、發佈、移動或刪除資產。 取出資產會鎖定資產，並防止其他使用者執行其中任何操作。 若要能夠登出／登入資產，您需要有其「寫入」存取權。

從AEM網頁介面簽出資產有兩種方式。 如需有關第一種方法的詳細資訊，請參 [閱「資產UI」的登入和結帳檔案](https://docs.adobe.com/content/help/en/experience-manager-65/assets/managing/check-out-and-submit-assets.html)。 請依照這些步驟進行，以取得在安裝AEM Desktop應用程式時，要簽出並開啟資產的第二種方法。

1. 開啟AEM Assets介面，並將指標暫留在資料夾或資產上，以在「卡片」檢視中將案頭動作顯示為快速動作。

   ![卡片檢視中的屬性選項](assets/chlimage_1-4.png)

   當您在選取資產後，或從資產頁面的工具列按一下／點選工具列中的「案頭動作」圖示時，也可使用這些案頭動作。

1. 若要開啟資產，請按一下／點選「在案頭上開啟」快速動作「在案頭上 ![開啟」圖示](assets/do-not-localize/aemassets_icon_openondesktop.png)。

   或者，從工具欄的「案頭操作」菜單中選擇「開啟」。

   >[!NOTE]
   >
   >當您編輯剛開啟且未勾選的檔案時，其他使用者無法得知您正在更新資產。

1. 若要在Adobe Creative Cloud應用程式中開啟資產以進行編輯，請按一下／點選「編輯案頭快速動作編輯案頭」 ![圖示](assets/do-not-localize/aemassets_icon_editdesktop.png)。 此外，也會檢查資產以進行編輯。 編輯完成後，請簽入資產，以更新AEM Assets中的變更。

   或者，從工具列的「案頭動作」選單中選擇「編輯」。

1. 選擇「開啟」菜單選項。 選取的資產會以預覽模式開啟。
1. 若要編輯資產，請選取「編輯」選項。 資產會在編輯模式中開啟。

### 在Mac OS上查看Finder中的資產 {#check-out-assets-on-mac}

應用程式可讓您取出資產檔案，以防止其他使用者修改您正在處理的檔案。

1. 從Mac內容選單中，選取「開啟AEM資產檔案夾」以開啟Finder。

   ![使用AEM Desktop應用程式存取和開啟資產的內容選單選項](assets/aem_desktopapp_mac_context_menu.png)

   使用AEM Desktop應用程式存取和開啟資產的內容選單選項

1. 定位至要結帳的資產。

   ![在Mac的AEM Assets內容選單中開啟](assets/chlimage_1-5.png)

1. 在資產上按一下滑鼠右鍵，然後從內容選單中選取「更多資產資訊」。
1. 在「資產資訊」對話方塊中，按一下／點選「結帳」圖示以結帳資產。 按一下／點選「結帳」圖示後，「結帳」圖示會切換為「結帳」圖示。

   ![瀏覽至要結帳的資產](assets/chlimage_1-6.png)

1. 若要簽入資產以便讓其他用戶可以使用，請按一下／點選「資產資訊」對話框中的簽入表徵圖。

### 在Windows上查看資產 {#check-out-assets-on-windows}

應用程式可讓您取出資產檔案，以防止其他使用者修改您正在處理的檔案。

1. 從「上下文」菜單中，選擇「瀏覽資產」以開啟「瀏覽器」。
1. 在瀏覽器中，瀏覽至您要結帳的資產所在的位置。

   ![結帳圖示切換](assets/chlimage_1-7.png)

1. 在資產上按一下滑鼠右鍵，然後從內容選單中選取「在網路上開啟」。
1. 在「資產資訊」對話方塊中，按一下／點選「結帳」圖示。 「結帳」圖示會切換為「登入」圖示。

   ![結帳圖示切換](assets/chlimage_1-8.png)

1. 在Explorer中檢閱資產。 資產「資產」鎖定圖示上的 ![鎖定圖示](assets/do-not-localize/aemassets_icon_lockcheckout.png) ，表示您已簽出資產。

   >[!NOTE]
   >
   >鎖定表徵圖可能會在延遲後顯示。 AEM案頭應用程式會快取資產以供快速存取，因此可能需要片刻時間更新鎖定的狀態。

1. 若要簽入資產以便讓其他用戶可以使用，請按一下／點選「資產資訊」對話框中的 **簽入表徵圖** 。

### 使用Finder或Explorer並使用Web介面簽入資產 {#check-in-an-asset-using-finder-or-explorer-and-using-web-interface}

編輯完資產後，請將資產儲存在案頭應用程式中。 從上下文選單中，選取「 **更多資產資訊** 」，然後按一下登入。

資產會上傳至AEM伺服器。 （可選）您可以從系統托盤表徵圖中選擇「查看 **資產狀態** 」來檢查上載狀態。 或者，您也可以從AEM網頁介面簽入資產。 按一下已勾選的資產或加以選取。 在工具列中，按一下登入圖示 ![登入圖示](assets/do-not-localize/aemassets_icon_checkin.png)。

在本機儲存任何變更後，資產就會自動上傳至AEM。 此登入功能可讓其他AEM使用者使用資產進行編輯。

### 大量上傳資產和資料夾至AEM伺服器 {#bulkupload}

使用AEM Desktop，您可以將包含資產的整個檔案夾從本機檔案目錄上傳至AEM Assets。 如此，資料夾內的所有資產都會大量上傳，而不必一次上傳一個。

1. 從「資產」使用者介面，按一下／點選工 **具列中的** 「建立」，然後從功能表 **選擇「上傳資料夾** 」。
1. 瀏覽至您要上傳的檔案夾，然後加以選取。
1. 按一下／點選「確定」。 「資產狀態」對話方塊會顯示上傳的狀態。

   ![在「資產狀態」窗口中查看上載狀態](assets/aem_desktopapp_bulkupload_status.png)

   在「資產狀態」窗口中查看上載狀態

   >[!NOTE]
   >
   >您可以按一下／點選適當的圖示，手動暫停或取消上傳。

1. 上傳資料夾後，請關閉對話方塊並導覽至「資產」UI。 上傳的資料夾會顯示在網頁介面中。

Adobe不建議從本機檔案系統複製貼上或將大量檔案或巢狀檔案夾拖曳至網路共用區。 由於技術限制，應用程式無法控制上傳程式，而且效能不佳。

或者，在Finder或檔案總管中選取您要上傳至AEM的檔案／檔案夾、將檔案複製至系統剪貼簿、導覽至網路共用區中的目標檔案夾，並從AEM案頭應用程式內容選單中選取「貼上資產」 ****。 如此，AEM案頭應用程式就會開始上傳貼上的資產，類似於AEM網頁介面中 **的「上傳檔案夾** 」選項。

>[!MORELIKETHIS]
>
>* [AEM 桌面應用程式簡介](https://helpx.adobe.com/customer-care-office-hours/aem/desktop-app.html)
>* [瞭解AEM案頭應用程式的登入／登出](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/collaboration/checkin-checkout-technical-video-understand.html)
>* [疑難排解AEM案頭應用程式應用程式](troubleshoot-app-v1.md)

