---
title: 使用 [!DNL Experience Manager] 案頭應用程式1.x版。
description: 瞭解如何使用Adobe Experience Manager案頭應用程式1.x版，並最佳化您在案頭上使用資產的工作。
translation-type: tm+mt
source-git-commit: a25c1fa13895ae9eb7268e3e01c83a5f0b9d7d1d
workflow-type: tm+mt
source-wordcount: '2379'
ht-degree: 0%

---


# 使用[!DNL Experience Manager]案頭應用程式v1.x {#use-aem-desktop-app-v1x}

使用應用程式，您可輕鬆在本機案頭上存取[!DNL Experience Manager]中的資產，並可用於任何案頭應用程式。 資產可在Mac Finder或Windows檔案總管中輕鬆顯示、在案頭應用程式中開啟並在本機變更——這些變更會儲存回[!DNL Experience Manager]，並在儲存庫中建立新版本。

此類整合可讓組織中的不同角色集中管理資產，並在Creative Cloud和其他應用程式中存取資產，同時輕鬆符合包括品牌在內的各種標準。

您使用[!DNL Experience Manager]案頭應用程式v1執行的主要工作包括：

1. [連線至伺 [!DNL Experience Manager] 服器](#installandconnect)
1. [直接在案頭上開啟資產](#openondesktop)
1. [從案頭編輯及取出資產](#workonassets)
1. [大量上傳資產和檔案夾](#bulkupload)

如需各種建議的dos和don&#39;ts，請參閱使用app](best-practices-for-v1.md)的[最佳實務。 如果您使用應用程式時遇到問題，請參閱如何[疑難排解 [!DNL Experience Manager] desktop](troubleshoot-app-v1.md)。

>[!NOTE]
>
>[!DNL Experience Manager] 案頭應用程式已在 [!DNL Experience Manager] 6.1版本中推出，稱為 [!DNL Experience Manager Assets Companion App]。

## [!DNL Experience Manager] 創意工作流程中的案頭應用程式觸點  {#aem-desktop-app-touch-points-in-the-creative-workflow}

[!DNL Experience Manager] 案頭應用程式與 [!DNL Assets]您的創意工作流程整合，並提供下列觸控點。

![[!DNL Experience Manager] 案頭應用程式觸點創意工作流程](assets/aem_desktopapp_workflow.png)

[!DNL Experience Manager] 案頭應用程式觸點創意工作流程

## 安裝應用程式並將它連接至[!DNL Experience Manager]伺服器{#installandconnect}

開始建立或編輯創意資產之前，請先將案頭應用程式與[!DNL Assets]伺服器連接，以下載並上傳儲存庫中的資產。 執行下列工作：

1. [安裝應用程式](#installapp)。
1. [設定您的偏好](#inapppref) 設定和連線詳細資訊。
1. [連接到 [!DNL Experience Manager] ](#connect) anserver，並將資產儲存庫作為本地驅動器。
1. [在伺服器](#desktopactions) 上啟 [!DNL Experience Manager] 用案頭動作。

[!DNL Experience Manager] 案頭應用程式使用HTTPS連線來連線至伺 [!DNL Experience Manager] 服器，以穩健且安全地傳輸您的資產。

>[!NOTE]
>
>對於部分或所有安裝和配置步驟，您可能需要[!DNL Experience Manager]管理員或系統管理員的幫助。

### 安裝應用程式{#installapp}

若要使用[!DNL Experience Manager]案頭應用程式，請確定應用程式支援您的[!DNL Experience Manager]伺服器版本。 下載適合您作業系統（Mac或Windows）的安裝檔（二進位），並安裝應用程式。

根據您的網路和系統首選項，可能需要進行詳細配置。 如需詳細資訊，請參閱[安裝及設定 [!DNL Experience Manager] 案頭應用程式](install-configure-app-v1.md)。

1. 前往[[!DNL Experience Manager] 案頭應用程式下載頁面](https://helpx.adobe.com/experience-manager/kb/download-companion-app.html)並下載適合您作業系統的二進位檔。
1. 啟動下載的安裝檔案，並依照螢幕上的指示安裝應用程式。

   >[!NOTE]
   >
   >一次只能安裝一個[!DNL Experience Manager]案頭應用程式的執行個體並處於活動狀態。

### 瞭解應用程式內選項和偏好設定{#inapppref}

應用程式允許設定與[!DNL Experience Manager]伺服器連接和斷開連接、查看上載狀態、管理本地快取等。 預設設定適用於應用程式的一般使用者。 您可以調整設定，讓應用程式和與[!DNL Experience Manager]伺服器的整合發揮更大效益。 下面將詳細說明各種設定。

**探索** 資產開啟掛載儲存庫的 [!DNL Assets] 本地驅動器。換言之，請探索您本機電腦上現在可用的資產。

**檢視資** 產狀態當變更的資產上傳或新資產新增至儲存 [!DNL Assets] 庫時，應用程式會在背景上傳資產。背景上傳可讓作業更順暢，您不必等到上傳完成，尤其是大型資產。 您可以將變更儲存在本機，而不必擔心。 應用程式會花一些時間將這些資產傳送至伺服器，視可用頻寬而定。 您可以檢查上傳的狀態，以及一些更基本的資訊。

**選** 項從案頭應用程式托盤按一下選項，以存取設定，在您的系統啟動時啟動應用程式；在應用程式 [!DNL Experience Manager] 啟動時連線至伺服器；並更改安裝後可用的本 [!DNL Assets] 地驅動器號。

**「進階>管** 理快取」您可以控制可用於本機快取的磁碟空間量。來自[!DNL Assets]伺服器的物件會快取至本機，以提供更順暢的體驗。 您可以變更預設值以符合您的需求。 此外，您也可以清除快取，重新擷取所有資產。 清除快取時，它會保留未儲存的變更。 未簽入[!DNL Experience Manager]伺服器的任何資產都將保留並不刪除。

### 連接到[!DNL Experience Manager]伺服器{#connect}

應用程式支援Mac和Windows上的Proxy設定。 應用程式啟動時會讀取設定。 如果您修改Proxy設定，請重新啟動應用程式，讓變更生效。

>[!NOTE]
>
>如果您修改Proxy設定，請重新啟動應用程式，讓變更生效。 否則，應用程式會繼續使用先前設定的代理伺服器。

1. 啟動[!DNL Experience Manager]案頭應用程式。 若要將您的[!DNL Experience Manager]例項與應用程式對應，請以`https://[aem-server-url]:[port]`格式指定您的[!DNL Experience Manager]伺服器。

   ![在Mac上驗證並提供伺 [!DNL Experience Manager] 服器URL](assets/aem_desktop_app_server_url.png)

1. 在登入畫面中，指定您例項的使用者名稱和密碼。 要指定備用[!DNL Experience Manager]實例，請選擇&#x200B;**[!UICONTROL Alternate Login URL]**&#x200B;選項。

   ![在桌 [!DNL Experience Manager] 面應用程式的登入畫面上提供伺服 [!DNL Experience Manager] 器認證](assets/login_screen_v1.png)

### 在[!DNL Experience Manager]網頁介面{#desktopactions}中啟用案頭動作

從「資產」使用者介面中，您可以探索資產位置或結帳並開啟資產，以便在案頭應用程式中編輯。 這些選項稱為案頭操作，預設情況下不啟用。 請依照下列步驟進行啟用。

1. 在「資產」介面中，按一下／點選工具列右上角的「使用者」圖示。
1. 按一下&#x200B;**[!UICONTROL My Preferences]**&#x200B;以顯示&#x200B;**[!UICONTROL Preferences]**&#x200B;對話框。

   ![[!DNL Experience Manager] 介面，使用者偏好設定](assets/aem_ui_user_preferences.png)

1. 在「用戶首選項」對話框中，選擇&#x200B;**[!UICONTROL Show Desktop Actions For Assets]**。 按一下 **[!UICONTROL Accept]**.

   ![選中 [!UICONTROL Show Desktop Actions For Assets] 以啟用案頭操作](assets/enable_desktop_actions.png)

   *圖：勾選「顯示資產的案頭動作」以啟用案頭動作。*

## 存取和開啟案頭上的資產{#openondesktop}

當您按一下「**開啟**」以在本機電腦上開啟資產時，應用程式會將資產下載至其內部快取。 應用程式會啟動與已下載資產的檔案類型相關聯的原生案頭應用程式。

在Mac上，從內容選單選擇「**開啟**」，以透過[!DNL Experience Manager]案頭應用程式開啟資產。 在Windows上，從上下文選單選擇「在Web上開啟」以開啟資產。 在「資產狀態」視窗中，按一下／點選「在案頭上開啟」圖示![以開啟資產。](assets/do-not-localize/aemassets_icon_openondesktop.png)

對於Adobe InDesign(INDD)檔案，請從內容選單中選取&#x200B;**[!UICONTROL Open]**。 當您按一下此選項時，應用程式會將連結的資產下載到您的本機檔案系統，然後在Adobe InDesign中開啟INDD檔案。 此方法可確保在編輯INDD檔案時，必要的資產可在本機使用。

![使用案頭應用程式存取和開啟資產的內容選 [!DNL Experience Manager] 單選項](assets/aem_desktopapp_mac_context_menu.png)

*圖：使用案頭應用程式存取及開啟資產的內容選 [!DNL Experience Manager] 單選項。*

>[!NOTE]
>
>在Windows上，[預設的Windows 7設定](https://support.microsoft.com/en-us/kb/2668751)會防止[!DNL Experience Manager]案頭應用程式處理大於50 MB的資產。

>[!NOTE]
>
>Adobe建議您前往Mac上的Finder檢視選項，並停用已載入[!DNL Assets]資料夾的選項&#x200B;**「顯示項目資訊**」、「顯示項目預覽&#x200B;**」和「顯示預覽欄**」。 ****&#x200B;它改善了效能。

### [!DNL Experience Manager]介面{#additional-options-in-aem-assets}中的其他選項

將[!DNL Assets]儲存庫映射到本地驅動器後，您可以為映射的資產和資料夾啟用附加表徵圖和資料夾上載功能。

1. 開啟[!DNL Assets]介面，將指標暫留在資料夾或資產上，以在「卡片」檢視中將案頭動作顯示為快速動作。

   ![在「資產」UI中，開啟快速動作功能表以檢視案頭動作](assets/desktop_actions_in_card_view.png)

   *圖：在「資產」UI中，開啟快速動作功能表以檢視案頭動作。*

   當您在選取資產後，或從資產頁面的工具列按一下工具列中的&#x200B;**案頭動作**&#x200B;選項時，這些案頭動作也可供使用。

1. 若要在案頭應用程式中開啟與特定副檔名相關聯的資產，請按一下「在案頭上開啟」快速動作「在案頭上開啟」圖示&#x200B;**。](assets/do-not-localize/aemassets_icon_openondesktop.png)**![

   或者，從工具欄的&#x200B;**案頭操作**&#x200B;菜單中選擇&#x200B;**開啟**。

若要在本機檔案系統上找到特定資產，請按一下「顯現&#x200B;**快速動作![顯現圖示](assets/do-not-localize/aemassets_reveal_icon.png)」。**&#x200B;或者，從工具欄的「案頭操作」菜單中選擇「**顯現**」。****

## 瞭解資產狀態{#understand-the-asset-statuses}

| ![Windows預設應用程式圖示](assets/do-not-localize/win_default.png) | 應用程式已連線至伺服器，且所有資產都會同步化。 |
--- |--- |
| ![Windows停用圖示](assets/do-not-localize/win_disabled.png) | 應用程式已啟動，但未與伺服器連線。 某些資產可能是擱置中的同步。 |
| ![Windows檔案同步表徵圖](assets/do-not-localize/win_sync.png) | 資產正在同步化。 正在上傳或下載檔案。 您可以在「資產狀態」窗口中查看確切狀態並暫停轉移。 |
| ![Windows重新連接表徵圖](assets/do-not-localize/win_refresh.png) | 應用程式正在嘗試重新連線。 可能是網路問題導致其斷開連接。 |

## 處理您的資產{#workonassets}

### 從[!DNL Experience Manager]網頁介面{#check-out-assets-from-the-aem-web-interface}檢視資產

[!DNL Assets] 可讓您取出要編輯的資產，並在完成變更後將其存回。結帳資產後，只有您可以編輯、註解、發佈、移動或刪除資產。 取出資產會鎖定資產，並防止其他使用者執行其中任何操作。 若要能夠登出／登入資產，您需要有其「寫入」存取權。

從[!DNL Experience Manager] Web介面簽出資產有兩種方式。 如需有關第一種方法的詳細資訊，請參閱「資產UI」中的[登入和結帳檔案。 ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/check-out-and-submit-assets.html)請依照下列步驟進行，以取得當安裝[!DNL Experience Manager]案頭應用程式時，第二種登出並開啟資產的方法。

1. 開啟[!DNL Assets]介面，將指標暫留在資料夾或資產上，以在「卡片」檢視中將案頭動作顯示為快速動作。

   ![卡片檢視中的屬性選項](assets/desktop_actions_in_card_view.png)

   當您在選取資產後，或從資產頁面的工具列按一下／點選工具列中的「案頭動作」圖示時，也可使用這些案頭動作。

1. 若要開啟資產，請按一下／點選「在案頭上開啟」快速動作![「在案頭上開啟」圖示](assets/do-not-localize/aemassets_icon_openondesktop.png)。

   或者，從工具欄的「案頭操作」菜單中選擇「開啟」。

   >[!NOTE]
   >
   >當您編輯剛開啟且未勾選的檔案時，其他使用者無法得知您正在更新資產。

1. 若要在Adobe Creative Cloud應用程式中開啟資產以進行編輯，請按一下／點選「編輯案頭快速動作![編輯案頭」圖示](assets/do-not-localize/aemassets_icon_editdesktop.png)。 此外，也會檢查資產以進行編輯。 編輯完成後，請簽入資產以更新[!DNL Assets]中的更改。

   或者，從工具列的「案頭動作」選單中選擇「編輯」。

1. 選擇「開啟」菜單選項。 選取的資產會以預覽模式開啟。
1. 若要編輯資產，請選取「編輯」選項。 資產會在編輯模式中開啟。

### 查看Mac OS上Finder的資產{#check-out-assets-on-mac}

應用程式可讓您取出資產檔案，以防止其他使用者修改您正在處理的檔案。

1. 從Mac內容選單中，選取「開啟AEM資產檔案夾」選項以開啟Finder。

   ![使用案頭應用程式存取和開啟資產的內容選 [!DNL Experience Manager] 單選項](assets/aem_desktopapp_mac_context_menu.png)

   *圖：使用案頭應用程式存取及開啟資產的內容選 [!DNL Experience Manager] 單選項。*

1. 定位至要結帳的資產。
1. 在資產上按一下滑鼠右鍵，然後從內容選單中選取「更多資產資訊」。
1. 在「資產資訊」對話方塊中，按一下／點選「結帳」圖示以結帳資產。 按一下／點選「結帳」圖示後，「結帳」圖示會切換為「結帳」圖示。

   ![瀏覽至要結帳的資產](assets/browse_assets_to_checkout.png)

1. 若要簽入資產以便讓其他用戶可以使用，請按一下／點選「資產資訊」對話框中的簽入表徵圖。

### 查看Windows {#check-out-assets-on-windows}上的資產

應用程式可讓您取出資產檔案，以防止其他使用者修改您正在處理的檔案。

1. 從「上下文」菜單中，選擇「瀏覽資產」以開啟「瀏覽器」。
1. 在瀏覽器中，瀏覽至您要結帳的資產所在的位置。
1. 在資產上按一下滑鼠右鍵，然後從內容選單中選取「在網路上開啟」。
1. 在「資產資訊」對話方塊中，按一下／點選「結帳」圖示。 「結帳」圖示會切換為「登入」圖示。

   ![結帳圖示切換](assets/checkout_icon_toggles.png)

1. 在Explorer中檢閱資產。 資產![資產鎖定圖示](assets/do-not-localize/aemassets_icon_lockcheckout.png)上的鎖定圖示表示您已簽出資產。

   >[!NOTE]
   >
   >鎖定表徵圖可能會在延遲後顯示。 [!DNL Experience Manager] 案頭應用程式會快取資產以供快速存取，因此可能需要片刻時間來更新鎖定的狀態。

1. 若要簽入資產以便其他用戶可以使用，請按一下／點選&#x200B;**資產資訊**&#x200B;對話框中的簽入表徵圖。

### 使用Finder或Explorer並使用Web介面{#check-in-an-asset-using-finder-or-explorer-and-using-web-interface}簽入資產

編輯完資產後，請將資產儲存在案頭應用程式中。 從上下文菜單中，選擇&#x200B;**更多資產資訊**&#x200B;並按一下簽入。

資產會上傳至[!DNL Experience Manager]伺服器。 或者，您可以從系統托盤表徵圖中選擇&#x200B;**查看資產狀態**&#x200B;來檢查上載狀態。 或者，您也可以從[!DNL Experience Manager]網頁介面簽入資產。 按一下已勾選的資產或加以選取。 在工具欄中，按一下檢入表徵圖![檢入表徵圖](assets/do-not-localize/aemassets_icon_checkin.png)。

在本機儲存任何變更後，資產會自動上傳至[!DNL Experience Manager]。 此登入功能可讓其他[!DNL Experience Manager]使用者使用資產進行編輯。

### 大量上傳資產和資料夾至[!DNL Experience Manager]伺服器{#bulkupload}

使用[!DNL Experience Manager]案頭應用程式，您可以將包含資產的整個資料夾從本機檔案目錄上傳至[!DNL Assets]。 如此，資料夾內的所有資產都會大量上傳，而不必一次上傳一個資產。

1. 在「資產」UI中，按一下／點選工具列中的「建立&#x200B;****」，然後從選單選擇「上傳資料夾&#x200B;**」。**
1. 瀏覽至您要上傳的檔案夾，然後加以選取。
1. 按一下／點選「確定」。 「資產狀態」對話方塊會顯示上傳的狀態。

   ![在「資產狀態」窗口中查看上載狀態](assets/aem_desktopapp_bulkupload_status.png)

   在「資產狀態」窗口中查看上載狀態

   >[!NOTE]
   >
   >您可以按一下／點選適當的圖示，手動暫停或取消上傳。

1. 上傳資料夾後，請關閉對話方塊並導覽至「資產」UI。 上傳的資料夾會顯示在網頁介面中。

Adobe不建議從本機檔案系統複製貼上或將大量檔案或巢狀檔案夾拖曳至網路共用區。 由於技術限制，應用程式無法控制上傳程式，而且效能不佳。

或者，在Finder或檔案總管中選取您要上傳至[!DNL Experience Manager]的檔案／檔案夾、將檔案複製至系統剪貼簿、導覽至網路共用區中的目標檔案夾，並從[!DNL Experience Manager]案頭應用程式內容選單中選取「貼上資產」**。**&#x200B;這樣，[!DNL Experience Manager]案頭應用程式就會開始上傳貼上的資產，類似[!DNL Experience Manager]網頁介面中的「上傳資料夾」選項。****

>[!MORELIKETHIS]
>
>* [疑難排 [!DNL Experience Manager] 解案頭應用程式應用程式](troubleshoot-app-v1.md)

