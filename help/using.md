---
title: 使用AEM案頭應用程式
seo-title: 使用Adobe Experience manager案頭應用程式
description: 瞭解如何安裝和使用Adobe Experience Manager案頭應用程式，直接從Win或Mac案頭處理AEM資產。 瞭解最佳實務和疑難排解資訊。
seo-description: 瞭解如何安裝和使用Adobe Experience Manager案頭應用程式，直接從Win或Mac案頭處理AEM資產。 瞭解最佳實務和疑難排解資訊。
uuid: 55057617-89de-43cd-8419-1252a42ab2fb
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: 39d7bcad-d7b0-4978-a790-4cb68b8a7d6a
index: y
internal: n
snippet: y
mini-toc-levels: '1'
translation-type: tm+mt
source-git-commit: b74a3ff5c9a25ee1433dd661a1bce677271a5ebe

---


# 使用AEM案頭應用程式 {#use-aem-desktop-app-v2}

使用Adobe Experience Manager(AEM)案頭應用程式，輕鬆存取您本機案頭上的AEM資產，並在任何案頭應用程式中使用這些資產。 您可以在案頭應用程式中開啟資產並在本機編輯資產——透過版本控制將變更上傳回AEM，以便與其他使用者共用更新。 您也可以將新檔案和檔案夾階層上傳至AEM、建立檔案夾，以及從AEM刪除資產或檔案夾。

整合可讓組織中的各種角色集中管理AEM Assets中的資產，並在Windows或Mac OS的原生應用程式中存取本機案頭上的資產。

當您登出後或第一次開啟應用程式時，請提供AEM伺服器的URL。 按一下「連接」。 提供您的認證以連接應用程式與伺服器。

您使用AEM案頭應用程式所做的主要工作包括：

![您可使用AEM案頭應用程式完成的工作流程和](assets/do-not-localize/whats-new-desktop-app-v2.png "工作工作流程和您可使用AEM案頭應用程式完成的工作")下 [載這個](assets/do-not-localize/aem_desktop_app_usecases_print.pdf) 可立即列印的PDF檔案。

## 案頭應用程式的運作方式 {#how-app-works2}

在您開始使用應用程式之前，請先了 [解應用程式的運作方式](release-notes.md#how-app-works)。 此外，請熟悉下列詞語：

* **[!UICONTROL Desktop Actions]**:從「資產」網頁介面，在瀏覽器中，您可以探索資產位置或結帳並開啟資產，以便在原生案頭應用程式中進行編輯。 這些動作可從網頁介面使用，並使用案頭應用程式功能。 瞭解 [如何啟用案頭動作](using.md#desktopactions-v2)。

* 檔案狀態 **[!UICONTROL Cloud Only]**&#x200B;為：此類資產不會下載至本機電腦，而且只能在AEM伺服器上使用。

* 檔案狀態 **[!UICONTROL Available locally]**&#x200B;為：資產會依原樣下載並在本機電腦上使用。 資產不會變更。

* 檔案狀態 **[!UICONTROL Edited locally]**&#x200B;為：這些資產會在本機進行修改，而變更仍會保留至已上傳至AEM伺服器。 上傳後，狀態會變更為 [!UICONTROL Available locally]。 請參閱 [編輯資產](using.md#edit-assets-upload-updated-assets)。

* 檔案狀態 **[!UICONTROL Editing conflict]**&#x200B;為：如果您和其他使用者同時修改資產，應用程式會指出發生編輯衝突。 應用程式也提供保留或放棄變更的選項。 瞭解 [如何避免編輯衝突](using.md#adv-workflow-collaborate-avoid-conflicts)。

* 檔案狀態 **[!UICONTROL Modified remotely]**&#x200B;為：應用程式會指出您已下載的資產是否在AEM伺服器上變更。 應用程式也提供下載最新版本和更新本機副本的選項。 瞭解 [如何避免編輯衝突](using.md#adv-workflow-collaborate-avoid-conflicts)。

* **結帳**:如果您正在編輯檔案或打算編輯檔案，則可切換狀態以簽出。 它會在應用程式和AEM網頁介面中的資產上新增鎖定圖示。 鎖定圖示會指示其他使用者避免同時編輯相同的資產，因為這會導致編輯衝突。

* **登入**:將資產標示為安全，讓其他使用者可進行編輯，而不會造成編輯衝突。 當您上傳變更時，鎖定圖示會自動移除。 切換登入狀態也會移除鎖定圖示，不過建議不要手動登入而不上傳變更。 如果您捨棄變更，請手動切換登入。

* **[!UICONTROL Open]** 動作：只要開啟資產，即可在原生應用程式中預覽。 不建議您使用此動作來編輯資產，因為它不會簽出資產，而其他使用者可以進行編輯，進而導致編輯衝突。

* **[!UICONTROL Edit]** 動作：使用動作修改影像。 按一 [!UICONTROL Edit] 下動作會自動取出資產，並在資產上新增鎖定圖示。 按一下「編輯」後，如果您不想編輯資產，請按一下 [!UICONTROL Toggle check-in]。 若要刪除、重新命名或移動AEM DAM檔案夾階層中的資產，請使用AEM網頁介面動作，而非編輯動作。

* **[!UICONTROL Download]** 動作：將資產下載至您的本機電腦。 您現在可以下載資產，稍後再進行編輯；離線工作，稍後再上傳變更。 資產會下載在檔案系統的快取資料夾中。

* **[!UICONTROL Reveal File]** 或 **[!UICONTROL Reveal Folder]** 動作：當資產下載至本機快取檔案夾時，應用程式會模擬本機網路磁碟機，並為每個資產提供本機路徑。 若要瞭解此路徑，請在應用程式中使用適當的顯現選項。 在Creative cloud應用程式中放置資產時，需要顯示動作。 請參 [閱置入資產](using.md#place-assets-in-native-documents)。

* **[!UICONTROL Open In Web]** 動作：若要在AEM網頁介面中檢視資產，請在網頁中開啟它。 您可以從AEM介面啟動更多工作流程，例如更新中繼資料或資產搜尋。

* **[!UICONTROL Delete]** 動作：從AEM DAM儲存庫刪除資產。 此動作會刪除AEM伺服器上資產的原始復本。 如果您只想放棄對本機資產的修改，請參閱捨 [棄變更](using.md#edit-assets-upload-updated-assets)。

* **[!UICONTROL Upload Changes]**:案頭應用程式只會在您明確上傳至AEM伺服器時，才上傳更新的資產。 當您儲存編輯時，變更只會儲存在本機電腦上。 上傳時，資產會自動登入，並移除鎖定圖示。 請參閱 [編輯資產](using.md#edit-assets-upload-updated-assets)。

## 在AEM網頁介面中啟用案頭動作 {#desktopactions-v2}

在瀏覽器的「資產」使用者介面中，您可以探索資產位置或結帳並開啟資產，以便在案頭應用程式中編輯。 這些選項會被呼 [!UICONTROL Desktop Actions] 叫，並且預設不會啟用。 若要啟用它，請依照下列步驟進行。

1. 在「資產」主控台中，按一下／點 **[!UICONTROL User]** 選工具列中的圖示。
1. 按一下／點選 **[!UICONTROL My Preferences]** 以顯示對 **[!UICONTROL Preferences]** 話方塊。
1. 在「用戶首選項」對話框中，選擇 **[!UICONTROL Show Desktop Actions For Assets]**。 按一下／點選 **[!UICONTROL Accept]**。

   ![勾選「顯示資產的案頭動作」以啟用案頭動作](assets/chlimage_1-3.png)

   選中 [!UICONTROL Show Desktop Actions For Assets] 以啟用案頭動作

## 瀏覽、搜尋和預覽資產 {#browse-search-preview-assets}

您可以從案頭應用程式中瀏覽、搜尋和預覽AEM儲存庫中的可用資產。 在應用程式中試用下列項目：

1. 瀏覽至資料夾，並查看資料夾中可用資產的一些基本資訊，以及所有資產的小縮圖。

   ![瀏覽DAM檔案和檔](assets/browse_folder_da2.png "案夾瀏覽DAM檔案和檔案夾")

1. 若要檢視詳細資訊以及個別資產的較大縮圖，請按一下檔案名稱。

   ![檢視資產和動作的較大預覽](assets/large_preview_actions_da2.png "檢視資產和動作的較大預覽")

1. 按一 **[!UICONTROL Open]** 下或 **[!UICONTROL Edit]** 以在本機下載檔案，然後只需在原生應用程式中檢視或編輯檔案即可。
1. 使用關鍵字搜尋，以在AEM儲存庫中尋找相關資產。 使用 `?` 和 `*` 作為通配符。 這些萬用字元會分別取代單一字元或多個字元。 視需要篩選並排序結果。

   ![使用星號通配符的示例搜](assets/search_wildcard_da2.png "索使用星號通配符的示例搜索")

   ![使用星號通配符的另一](assets/search_wildcard2_da2.png "個示例搜索使用星號通配符不同位置的另一個示例搜索")

>[!NOTE]
>
>應用程式會在多個中繼資料欄位中比對搜尋准則，而不只是資產的標題或檔案名稱，以顯示資產。

## 下載資產 {#download-assets}

您可以下載本機檔案系統上的資產。 應用程式會從AEM伺服器擷取資產，並將相同的副本儲存在您的本機檔案系統上。

按一 ![下更多選項圖示](assets/do-not-localize/more2_da2.png) ，以取得選項，然後按 ![一下下載圖示](assets/do-not-localize/download_cloud_da2.png) 。

![資產的下載選項資](assets/download_option_da2.png "產的下載選項")

>[!NOTE]
>
>當下載或上傳大型檔案或多個檔案時，應用程式會關閉資產和檔案夾上的動作。 當下載或上傳完成時，這些動作即可使用。

如果佇列大或您遇到網路問題，下載多個資產可能會導致效能不佳。 此外，當您下載資料夾時，可能會無意中佇列許多資產以供下載。 為避免等待時間過長，應用程式會限制單次下載的資產數目。 要瞭解如何配置它，請參閱設定 [首選項](install-upgrade.md#set-preferences)。 即使低於此限制，應用程式有時也可能會在下載明顯較大的檔案夾之前先尋求確認。

![App確認下載相對大量的資](assets/download_confirmation_da2.png "產App確認下載相對大量的資產")

如果已選取並下載檔案夾，應用程式只會下載直接儲存在AEM中檔案夾中的資產。 它不會自動從子資料夾下載資產。

## 在案頭上開啟資產 {#openondesktop-v2}

您可以開啟遠端資產，以便在原生應用程式中檢視。 資產會下載至本機資料夾，並在與檔案格式關聯的原生應用程式中啟動。 您可以變更原生應用程式，在Mac或Windows中開啟特定的檔案類型（副檔名）。

從資 **[!UICONTROL Open]** 產選單按一下。 資產會在本機下載並在原生應用程式中開啟。 在狀態列中檢查大型資產的下載進度和傳輸速度。
<!-- ![Download progress bar for large-sized assets](assets/download_status_bar_da2.png "Download progress bar for large-sized assets")

-->

>[!NOTE]
>
>如果預期的變更未反映在應用程式中，請按一下重新整理圖示 ![「重新整理」圖示](assets/do-not-localize/refresh.png) ，或在應用程式介面中按一下滑鼠右鍵，然後按一下 **[!UICONTROL Refresh]**。 當較大的下載或上傳正在進行時，無法使用這些動作。

若要開啟資產的本機下載檔案夾，請按一下「更多 ![動作」圖示](assets/do-not-localize/more2_da2.png) ，然後按一 ![下「顯現」圖示](assets/do-not-localize/reveal_action2_da2.png)**[!UICONTROL Reveal File]** 動作。

## 使用資產或將資產置入原生檔案 {#place-assets-in-native-documents}

在某些情況下，例如將資產放入原生檔案時，您可以在Windows檔案總管或Mac finder中存取檔案。 若要進入本機下載檔案的檔案系統位置，請使用「顯現」 ![圖示](assets/do-not-localize/reveal_action2_da2.png)**[!UICONTROL Reveal File]** 選項。

![資產的「顯現檔案」動](assets/revealfile_action_da2.png "作資產的「顯現檔案」動作")

按一 **[!UICONTROL Reveal File]**&#x200B;下或在 **[!UICONTROL Reveal Folder]** 資料夾上，開啟Windows檔案總管或Mac Finder，並在本機電腦上預先選取檔案或資料夾。 這個選項對於將AEM檔案置入支援置入或連結本機檔案的原生應用程式非常有用。 若要瞭解如何在Adobe inDesign中置入檔案，請參閱「置入 [圖形」](https://helpx.adobe.com/indesign/using/placing-graphics.html)。

此動 **[!UICONTROL Reveal File]** 作會開啟本機網路共用，僅顯示本機可用的資產——亦即顯示使用應用程式揭露、下載或開啟／編輯的資產。 本機網路共用不會上傳任何變更至AEM。 若要上傳變更，請明確使用 **[!UICONTROL Upload Changes]** 應用 **[!UICONTROL Upload]** 程式中的或動作。

>[!NOTE]
>
>為了向後相容於AEM案頭應用程式v1.x，透過本機網路共用來提供顯示的檔案，僅公開本機可用的檔案。 顯示檔案的案頭路徑與應用程式v1.x建立的路徑相同。

>[!CAUTION]
>
>請勿使用選 **[!UICONTROL Reveal File]** 項來編輯原生應用程式中的資產。 請改用動 **[!UICONTROL Edit]** 作。 如需詳細資訊，請參閱「進階 [工作流程」:在相同檔案上進行協作，避免編輯衝突](#adv-workflow-collaborate-avoid-conflicts)。

## 編輯資產並將更新的資產上傳至AEM {#edit-assets-upload-updated-assets}

當您想要進行變更並將更新的資產上傳至AEM伺服器時，請開啟資產以進行編輯。 若要避免與其他使用者的編輯衝突，請使用應用程式來啟動編輯工作階段。 開始編輯之前，請確定資產上沒有鎖定圖示，亦即，其他使用者未編輯資產。

若要編輯資產，請搜尋資產或瀏覽至資產的位置。 按一 ![下「更多」圖示](assets/do-not-localize/more2_da2.png) ，然後按一 **[!UICONTROL Edit]**&#x200B;下。

在下 **[!UICONTROL Toggle Check-out]** 列兩種情況下，使用鎖定資產以防止與其他使用者的編輯衝突：

* 您已開始編輯資產，但未先勾選（例如只開啟資產）。
* 您打算很快開始編輯資產，而不希望其他人編輯。

完成編輯後，應用程式會顯示已變 **[!UICONTROL Edited Locally]** 更資產的狀態。 所有儲存至資產的變更都僅限本機，直到您將變更上傳至AEM為止。 若要逐一上傳個別或少數資產，請從資產 **[!UICONTROL Upload Changes]** 的選項按一下。 它會在AEM中建立資產版本。 使用AEM Assets的Web介面，您可以在時間軸檢視中查看資 [產歷史記錄](https://helpx.adobe.com/experience-manager/6-5/assets/using/activity-stream.html)。

![應用程式中的上傳變更選](assets/upload_changes_single1_da2.png "項應用程式中的上傳變更選項")

![檢視資產大型預覽時上傳變更選](assets/upload_changes_single2_da2.png "項檢視資產大型預覽時上傳變更選項")

如需協作編輯的最佳實務，請參閱進 [階工作流程：在相同檔案上進行協作，避免編輯衝突](#adv-workflow-collaborate-avoid-conflicts)。

在下列情況下，您可能會想要放棄對本機資產所做的變更和編輯。 Click **[!UICONTROL Discard Changes]**.

* 如果您不想在AEM中儲存本機變更。
* 儲存部分變更後，開始對原始資產進行變更。
* 不再需要編輯資產時，請停止編輯。

如有必要，請切換結帳。 更新的資產會從本機快取資料夾中移除，當您編輯或開啟時，會再次下載。

## 上傳並新增資產至AEM {#upload-and-add-new-assets-to-aem}

使用者可以新增資產至DAM儲存庫。 例如，您可能是廣告公司的攝影師或承包商，想要將大量像片從像片拍攝新增至AEM存放庫。 若要新增新內容至AEM，請按一 ![下應用程式頂端列中的](assets/do-not-localize/upload_to_cloud_da2.png) 「上傳至雲端」圖示。 瀏覽至本機檔案系統中的資產檔案，然後按一下 **[!UICONTROL Select]**。 應用程式會開始上傳資產，如果資產上傳的時間較長，就會在底部顯示進度列。 建立或上傳檔案夾時，請勿使用空格和無效字元。 請參閱「在AEM Assets中建立 [檔案夾」中的字元清單](https://helpx.adobe.com/experience-manager/6-5/assets/using/managing-assets-touch-ui.html#Creatingfolders)。

<!-- ![Download progress bar for large-sized assets](assets/upload_status_da2.png "Download progress bar for large-sized assets")
-->

您可以從本機檔案系統上傳檔案夾或個別檔案。 資料夾的階層會在上傳時保留。 在大量上傳資產之前，請參閱 [大量上傳](#bulk-upload-assets)。

若要檢視指定作業中傳輸的資產清單，請按一下 **[!UICONTROL View]** &gt; **[!UICONTROL Assets transfers]**。 該清單允許您查看並快速驗證當前會話的檔案傳輸。

![特定會話中的已轉讓資產清](assets/assets_transfered_da2.png "單特定會話中已轉讓資產清單")

>[!NOTE]
>
>如果您退出應用程式並重新開啟，傳輸清單不會持續存在，也無法使用。

>[!NOTE]
>
>如果檔案無法上傳，而且您要連線至AEM 6.5.1或更新版本的部署，請參閱此疑難排 [解資訊](troubleshoot.md#upload-fails)。

## 使用多個資產 {#work-with-multiple-assets}

使用者可使用動作（例如一次上傳所有編輯或按幾下滑鼠上傳巢狀資料夾），輕鬆處理並管理多個資產。

### 瀏覽大型資料夾 {#browse-large-folders}

使用包含許多資產的檔案夾時，請捲動以檢視更多資產。 若要使用鍵盤捲動，請按幾下Tab鍵，以在頂端選取資產。 請注意反白顯示的資產，以得知何時選取。 現在使用向下鍵來移動資產清單。

### 選取資產的快速動作 {#quick-actions-for-selected-assets}

按一下幾個資產的縮圖，以選取資產。 若要選取所有資產，請按一下應用程式頂端列中的核取方塊。 應用程式底部的工具列會顯示一組共同適用於所有選取資產的動作。

![底部的工具列顯示與選取資產相關的動](assets/actions_bottom_toolbar1_da2.png "作底部的工具列顯示選取資產的一般動作")

![沒有選取範圍的常用動作時工具列中沒有](assets/actions_bottom_toolbar2_da2.png "動作沒有選取範圍的常用動作時工具列中沒有動作")

底部工具列中可用的動作取決於選取檔案的狀態。 例如，如果您只選取檔 **[!UICONTROL Edited Locally]** 案，您會看到圖 **[!UICONTROL Upload Changes]** 示。 如果您選取了和的混 **[!UICONTROL Edited locally]** 合 **[!UICONTROL Cloud only]**，則 **[!UICONTROL Upload Changes]** 此動作不可用。

### 尋找所有編輯過的影像 {#find-all-edited-images}

應用程式提供一個稱為 **[!UICONTROL Edited locally]**&#x200B;的檢視，讓您快速存取您在本機（透過或動作）下載並修改的 [!UICONTROL Open] 所有 [!UICONTROL Edit] 檔案。 應用程式可讓您選取所有本機編輯的資產，並按幾下滑鼠即可上傳變更。 此檢視也會顯示有編輯衝突的本機編輯資產。

![篩選以查看所有本機編輯的資](assets/edited_locally_filter_da2.png "產篩選以查看所有本機編輯的資產，例如大量上傳編輯")

### 大量上傳資產 {#bulk-upload-assets}

使用者或組織（例如攝影師或創意廣告公司）可以在情境中建立許多本機資產，例如像片拍攝、潤飾或從AEM以外的較大集合中選取。 他們可以直接從案頭應用程式將這些大型的本機資料夾上傳至AEM Assets。 資料夾階層會保留，而且會上傳所有巢狀子檔案夾和包含的資產。 上傳的資產也可立即供相同伺服器的其他使用者使用。 資產會在背景上傳，因此作業不會系結至網頁瀏覽器作業。

![從案頭大量上傳多個本機檔案夾至](assets/upload_local_folders_da2.png "AEMulk從案頭上傳多個本機檔案夾至AEM")

上傳後，如果預期的變更未反映在應用程式中，請按一下重新整理圖示「重新整理」 ![圖示](assets/do-not-localize/refresh.png)。

>[!NOTE]
>
>請勿使用上傳功能來跨兩個AEM部署移轉資產。 請參閱移轉 [指南](https://helpx.adobe.com/experience-manager/6-5/assets/using/assets-migration-guide.html)。

### 轉讓資產清單 {#list-of-transferred-assets}

若要檢視指定作業中傳輸的資產清單，請參閱「 [上傳資產至AEM](#upload-and-add-new-assets-to-aem)」。

## 進階工作流程：從AEM Assets網頁介面開始 {#adv-workflow-start-from-aem-ui}

如有必要，從AEM Assets網頁介面開始您的工作流程。 案頭應用程式已與AEM整合，以便在使用Desktop Actions提出要求時接管。

從Web介面啟動工作流程的特殊案例是資產發現。 資產使用者介面中的Omnisearch列提供豐富而進階的搜尋體驗。 您可能想要先在Web上找到所需的資產，然後使用啟動應用程式中的工作流程 [!UICONTROL Desktop Actions]。 有些範例包括使用Facet篩選搜尋結果、尋找從Adobe Stock授權的特定資產，或由您的組織實作的自訂，讓您從網頁介面進行更好的探索。

當您嘗試在「資產」網頁介面上執行下列動作時，會使用案頭應用程式功能：

* 允 [!UICONTROL Desktop Actions] 許 [!UICONTROL Open]、 [!UICONTROL Edit]和 [!UICONTROL Reveal]
* [!UICONTROL Upload folder]
* [!UICONTROL Check-out] 或 [!UICONTROL check-in]

例如，適用於在應用程式中籤出的資產的網頁介面動作 [!UICONTROL Open]有 [!UICONTROL Reveal]、和 [!UICONTROL Check-in]。

![AEM網頁介面中的案頭動](assets/assets_web_actions_da2.png "作AEM網頁介面中的案頭動作")

>[!NOTE]
>
>瀏覽器可能會提示您允許啟動Adobe Experience Manager Desktop。 若要享受從瀏覽器傳輸至應用程式的不間斷功能，請選取適當的核取方塊，讓應用程式隨時都能接手。

您無法使用Web介面找到下列資訊或工作流程。 使用案頭應用程式，因為網頁介面不會追蹤本機變更，而且不會察覺下列事項：

* 在本機編輯的檔案。
* 發生編輯衝突的檔案，以及解決衝突的方法。
* 將本機變更上傳至AEM。
* 本機可用檔案的各種狀態。

相反地，您可以從案頭應用程式開始，使用動作，在網頁介面中開啟資 **[!UICONTROL Open In Web]** 產。

## 進階工作流程：在相同的檔案上進行協作，避免編輯衝突 {#adv-workflow-collaborate-avoid-conflicts}

在協作環境中，多位使用者可能會使用同一組資產，而這些資產可能會導致版本修訂衝突。 為防止衝突，請遵循以下最佳做法：

* 不要按一下以編輯任何資產 [!UICONTROL Open]。 請勿從檔案系統資料夾開啟，編輯本機下載的資產。 其他使用者不知道資產正在編輯中。
* 若要編輯資產，請一律按一下 [!UICONTROL Edit]。 它會在原生應用程式中開啟資產，並在資產上新增鎖定圖示，讓其他使用者知道資產正在編輯中。
* 如果您 [!UICONTROL Toggle Check-in] 不小心開始編輯而未按一下，請按一下 [!UICONTROL Edit]。 這會新增資產的鎖定圖示。 即使您打算稍後編輯資產，但不想讓其他人編輯資產，請按一 [!UICONTROL Toggle Check-in] 下以鎖定資產。
* 在編輯資產之前，請確定其他使用者未編輯資產。 尋找資產上的鎖定圖示。
* 完成編輯後，請上傳所有變更，然後登入資產。

![編輯衝突狀](assets/edits_conflicts_status_da2.png "態編輯衝突狀態")

如果AEM伺服器上已更新本機下載的資產，應用程式會顯示 **[!UICONTROL Modified remotely]** 狀態。 您可以分別按一下或，移除本機復本或重新整理本 [!UICONTROL Remove] 機 [!UICONTROL Update] 復本。 對話框上的連結允許您查看資產的兩個版本。

![遠程修改資產時解決衝突的選](assets/modified_remotely_dialog_da2.png "項遠程修改資產時解決衝突的選項")

如果您正在本機編輯的資產也會在伺服器上更新，但您不知情，應用程式會顯示狀 **[!UICONTROL Editing Conflict]** 態。 您可以保留一組變更——保留您的更新(按一下 **[!UICONTROL Keep Mine]**)並刪除其他使用者的編輯，或尊重其他使用者的更新並刪除您的更新(**[!UICONTROL Overwrite Mine]**)。

![解決編輯衝突的選](assets/editing_conflict_dialog_da2.png "項解決編輯衝突的選項")

## 進階工作流程：置入和連結InDesign檔案中的資產 {#adv-workflow-place-assets-indesign}

當您使用AEM案頭應用程式開啟包含連結資產的檔案時，資產會預先下載並顯示在原生應用程式中。 若要讓此工作流程運作，您的原生應用程式必須支援放置本機資產的連結，而AEM必須支援解析二進位檔案中的這些連結至伺服器端參照。

AEM案頭應用程式支援此工作流程，只需使用幾種精選的Adobe Creative cloud案頭應用程式和檔案格式- Adobe inDesign、Adobe Illustrator和Adobe Photoshop。 此工作流程可讓您有效率地使用支援的Creative cloud檔案。 因此，如果使用者A將一些資產放入InDesign檔案並將其簽入AEM，使用者B會在InDesign檔案中看到資產，即使這些資產不在檔案中。 這些資產會在使用者B的機器上本機下載。

>[!NOTE]
>
>案頭應用程式可以對應至Windows上的任何磁碟機。 但是，對於平滑操作，請勿更改預設驅動器盤符。 如果同一組織的使用者使用不同的磁碟盤符，則無法看到其他人放置的資產。 路徑變更時，不會擷取置入的資產。 置入的資產會繼續置入二進位檔案（例如INDD）中，且不會移除。

若要瞭解此工作流程的限制，請參閱 [系統需求和支援版本](release-notes.md#system-requirements-and-prerequisites-v2)。

若要使用此工作流程與影像資產和InDesign搭配使用，請依照下列步驟進行：

1. 在AEM中使用已置入的資產，讓INDD檔案保持便利。 要瞭解如何建立此類INDD檔案，請參 [閱放置圖形](https://helpx.adobe.com/indesign/using/placing-graphics.html)。
1. 在案頭應用程式中， **[!UICONTROL Edit]** 在AEM中包含已置入資產的INDD檔案。
1. 應用程式會同時下載InDesign檔案和連結的資產。 當InDesign開啟檔案時，會解析連結、下載資產，並在InDesign檔案中顯示資產。
1. 若要在InDesign檔案中置入新圖形，請對 **[!UICONTROL Reveal File]** 資產使用動作。 此動作會在本機下載資產，並在Windows檔案總管或Mac Finder中開啟本機網路共用位置。
1. 將顯示的資產放入InDesign檔案中。 這會在文檔中建立連結。
1. 在您完成InDesign檔案中的編輯後，請儲存它，然後使用案頭應用程式將它上傳至AEM。

## 進階工作流程：本機下載資產 {#adv-workflow-download-assets-locally}

應用程式會在許多情況下，從您檔案系統的本機AEM伺服器下載資產。 下載會佔用頻寬和磁碟空間。 瞭解這些案例有助於您最佳化等待下載完成的時間。

您可以隨選從應用程式內下載資產。 請參閱 [下載資產](#download-assets)。

當您使用動作 [!UICONTROL Open] 在原生案頭應用程式中開啟資產時，資產會在本機下載（如果本機尚未提供）。 請參閱 [開啟資產](#openondesktop-v2)。

當您從應用程式中揭示資產或資料夾的位置時，資產或資料夾會先在本機下載，然後在本機網路共用的電腦上開啟。 請參閱 [開啟資產](#openondesktop-v2)。

當您使用動作 [!UICONTROL Edit] 在原生案頭應用程式中編輯資產時，資產會在本機下載（如果本機尚未提供）。 請參 [閱編輯資產並將更新的資產上傳至AEM](#edit-assets-upload-updated-assets)。

如果應用程式已安裝並獲准使用，它會在您從AEM網頁介面使用時完 [!UICONTROL Desktop Actions] 成動作。 應用程式會先下載資產，然後完成動作。