---
title: 使用 [!DNL Experience Manager] 案頭應用程式
description: 直接從Win或Mac案頭使用 [!DNL Adobe Experience Manager] desktop app, to work with [!DNL Adobe Experience Manager] DAM資產，並用於其他應用程式。
mini-toc-levels: 1
feature: Desktop App,Asset Management
exl-id: fa19d819-231a-4a01-bfd2-6bba6fec2f18
translation-type: tm+mt
source-git-commit: 4616934e8923693106401da008e2510310d0742a
workflow-type: tm+mt
source-wordcount: '3905'
ht-degree: 0%

---

# 使用[!DNL Adobe Experience Manager]案頭應用程式{#use-aem-desktop-app-v2}

使用[!DNL Adobe Experience Manager]案頭應用程式，輕鬆存取儲存在您本機案頭上[!DNL Adobe Experience Manager] DAM存放庫中的數位資產，並在任何案頭應用程式中使用這些資產。 您可以在案頭應用程式中開啟資產並在本機編輯資產——使用版本控制將變更上傳回[!DNL Experience Manager]，以便與其他使用者共用更新。 您也可以將新的檔案和檔案夾階層上傳至[!DNL Experience Manager]、建立檔案夾，以及從[!DNL Experience Manager] DAM刪除資產或檔案夾。

整合可讓組織中的不同角色在[!DNL Experience Manager Assets]集中管理資產，並在Windows或Mac OS的原生應用程式中存取本機案頭上的資產。

當您登出後或第一次開啟應用程式時，請以`https://[aem-server-url]:[port]/`格式提供[!DNL Experience Manager]伺服器的URL。 然後選擇[!UICONTROL Connect]選項。 提供憑證以連接應用程式和伺服器。

您使用[!DNL Experience Manager]案頭應用程式執行的主要工作有：

![使用案頭應用程式可完成的工作流程 [!DNL Experience Manager] 和工](assets/aem_desktop_app_usecases_v2.png "作流程使用案頭應用程式可完成的工 [!DNL Adobe Experience Manager] 作流程")
下載這 [](assets/aem_desktop_app_usecases_print.pdf) 個可列印的PDF檔案。

## 案頭應用程式的運作方式{#how-app-works2}

開始使用應用程式之前，請先瞭解[應用程式的運作方式](release-notes.md#how-app-works)。 此外，請熟悉下列詞語：

* **[!UICONTROL Desktop Actions]**:從「資產」網頁介面，在瀏覽器中，您可以探索資產位置或結帳並開啟資產，以便在原生案頭應用程式中進行編輯。這些動作可從網頁介面使用，並使用案頭應用程式功能。 請參閱[如何啟用案頭動作](using.md#desktopactions-v2)。

* 檔案狀態為&#x200B;**[!UICONTROL Cloud Only]**:此類資產不會下載在本機機器上，且僅能在[!DNL Experience Manager]伺服器上使用。

* 檔案狀態為&#x200B;**[!UICONTROL Available locally]**:資產會依原樣下載並在本機電腦上使用。 資產不會變更。

* 檔案狀態為&#x200B;**[!UICONTROL Edited locally]**:這些資產會在本機修改，而變更會保留至已上傳至[!DNL Experience Manager]伺服器。 上傳後，狀態會變更為[!UICONTROL Available locally]。 請參閱[編輯資產](using.md#edit-assets-upload-updated-assets)。

* 檔案狀態為&#x200B;**[!UICONTROL Editing conflict]**:如果您和其他使用者同時修改資產，應用程式會指出發生編輯衝突。 應用程式也提供保留或放棄變更的選項。 請參閱[如何避免編輯衝突](using.md#adv-workflow-collaborate-avoid-conflicts)。

* 檔案狀態為&#x200B;**[!UICONTROL Modified remotely]**:應用程式會指出您下載的資產是否在[!DNL Experience Manager]伺服器上變更。 應用程式也提供下載最新版本和更新本機副本的選項。 請參閱[如何避免編輯衝突](using.md#adv-workflow-collaborate-avoid-conflicts)。

* **[!UICONTROL Check-out]**:如果您正在編輯檔案或打算編輯檔案，則可切換狀態以簽出。它會在應用程式和[!DNL Experience Manager]網頁介面中的資產上新增鎖定圖示。 鎖定圖示會指示其他使用者避免同時編輯相同的資產，因為這會導致編輯衝突。

* **[!UICONTROL Check-in]**:將資產標示為安全，讓其他使用者可進行編輯，而不會造成編輯衝突。當您上傳變更時，鎖定圖示會自動移除。 切換登入狀態也會移除鎖定圖示，不過建議不要手動登入而不上傳變更。 如果您捨棄變更，請手動切換登入。

* **[!UICONTROL Open]** 動作：只要開啟資產，即可在原生應用程式中預覽。不建議您使用此動作來編輯資產，因為它不會簽出資產，而其他使用者可以進行編輯，進而導致編輯衝突。

* **[!UICONTROL Edit]** 動作：使用動作修改影像。按一下[!UICONTROL Edit]動作會自動取出資產並在資產上新增鎖定圖示。 按一下「編輯」後，如果您不想編輯資產，請按一下[!UICONTROL Toggle check-in]。 若要刪除、重新命名或移動[!DNL Experience Manager] DAM資料夾階層中的資產，請使用[!DNL Experience Manager]網頁介面動作，而非編輯動作。

* **[!UICONTROL Download]** 動作：將資產下載至您的本機電腦。您現在可以下載資產，稍後再進行編輯；離線工作，稍後再上傳變更。 資產會下載在檔案系統的快取資料夾中。

* **[!UICONTROL Reveal File]** 或動 **[!UICONTROL Reveal Folder]** 作：當資產下載至本機快取檔案夾時，應用程式會模擬本機網路磁碟機，並為每個資產提供本機路徑。若要瞭解此路徑，請在應用程式中使用適當的顯現選項。 在Creative Cloud應用程式中放置資產時，必須顯示動作。 請參閱[置入資產](using.md#place-assets-in-native-documents)。

* **[!UICONTROL Open In Web]** 動作：若要在Web介面中檢 [!DNL Experience Manager] 視資產，請在Web中開啟它。您可以從[!DNL Experience Manager]介面啟動更多工作流程，例如更新中繼資料或資產搜尋。

* **[!UICONTROL Delete]** 動作：從 [!DNL Experience Manager] DAM儲存庫刪除資產。動作會刪除Experience Manager伺服器上資產的原始副本。 如果只想放棄對本地資產的修改，請參閱[放棄更改](using.md#edit-assets-upload-updated-assets)。

* **[!UICONTROL Upload Changes]**:案頭應用程式只會在您明確上傳至伺服器時，才會上傳更新 [!DNL Experience Manager] 的資產。當您儲存編輯時，變更只會儲存在本機電腦上。 上傳時，資產會自動登入，並移除鎖定圖示。 請參閱[編輯資產](using.md#edit-assets-upload-updated-assets)。

## 在[!DNL Experience Manager]網頁介面{#desktopactions-v2}中啟用案頭動作

從瀏覽器的[!DNL Assets]使用者介面，您可以探索資產位置或結帳並開啟資產，以便在案頭應用程式中進行編輯。 這些選項稱為[!UICONTROL Desktop Actions]，預設為未啟用。 若要啟用它，請依照下列步驟進行。

1. 在[!DNL Assets]控制台中，按一下工具欄中的&#x200B;**[!UICONTROL User]**&#x200B;表徵圖。
1. 按一下&#x200B;**[!UICONTROL My Preferences]**&#x200B;以顯示&#x200B;**[!UICONTROL Preferences]**&#x200B;對話框。

1. 在「用戶首選項」對話框中，選擇&#x200B;**[!UICONTROL Show Desktop Actions For Assets]**。 按一下 **[!UICONTROL Accept]**.


   ![選擇「顯示資產的案頭動作」以啟用案頭動作](assets/enable_desktop_actions.png)

   *圖：選擇 [!UICONTROL Show Desktop Actions For Assets] 以啟用案頭操作。*

## 瀏覽、搜尋及預覽資產{#browse-search-preview-assets}

您可以瀏覽、搜尋和預覽[!DNL Experience Manager]儲存庫中的可用資產，全部都可從案頭應用程式中進行。 在應用程式中試用下列項目：

1. 瀏覽至資料夾，並查看資料夾中可用資產的一些基本資訊，以及所有資產的小縮圖。

   ![瀏覽DAM檔案和檔](assets/browse_folder_da2.png "案夾瀏覽DAM檔案和檔案夾")

1. 若要檢視詳細資訊以及個別資產的較大縮圖，請按一下檔案名稱。

   ![檢視資產和動作的較大預覽](assets/large_preview_actions_da2.png "檢視資產和動作的較大預覽")

1. 按一下&#x200B;**[!UICONTROL Open]**&#x200B;或&#x200B;**[!UICONTROL Edit]**，在本機下載檔案，然後只需在原生應用程式中檢視或編輯檔案。
1. 使用關鍵字搜尋以在[!DNL Experience Manager]儲存庫中尋找相關資產。 使用`?`和`*`做為萬用字元。 這些萬用字元會分別取代單一字元或多個字元。 視需要篩選並排序結果。

   ![使用星號通配符的示例搜](assets/search_wildcard_da2.png "索使用星號通配符的示例搜索")

   ![使用星號通配符的另一](assets/search_wildcard2_da2.png "個示例搜索使用星號通配符不同位置的另一個示例搜索")

>[!NOTE]
>
>應用程式會在多個中繼資料欄位中比對搜尋准則，而不只是資產的標題或檔案名稱，以顯示資產。

## 下載資產 {#download-assets}

您可以下載本機檔案系統上的資產。 應用程式會從[!DNL Experience Manager]伺服器擷取資產，並將相同的副本儲存在您的本機檔案系統上。

按一下![更多選項表徵圖](assets/do-not-localize/more2_da2.png)以獲得選項，然後按一下![下載表徵圖](assets/do-not-localize/download_cloud_da2.png)以下載。

![資產的下載選項資](assets/download_option_da2.png "產的下載選項")

>[!NOTE]
>
>當下載或上傳大型檔案或多個檔案時，應用程式會關閉資產和檔案夾上的動作。 當下載或上傳完成時，這些動作即可使用。

如果佇列大或您遇到網路問題，下載多個資產可能會導致效能不佳。 此外，當您下載資料夾時，可能會無意中佇列許多資產以供下載。 為避免等待時間過長，應用程式會限制單次下載的資產數目。 要瞭解如何配置它，請參閱[設定首選項](install-upgrade.md#set-preferences)。 即使低於此限制，應用程式有時也可能會在下載明顯較大的檔案夾之前先尋求確認。

![App確認下載相對大量的資](assets/download_confirmation_da2.png "產App確認下載相對大量的資產")

如果選取並下載檔案夾，應用程式只會下載直接儲存在[!DNL Experience Manager]檔案夾中的資產。 它不會自動從子資料夾下載資產。

## 在案頭上開啟資產{#openondesktop-v2}

您可以開啟遠端資產，以便在原生應用程式中檢視。 資產會下載至本機資料夾，並在與檔案格式關聯的原生應用程式中啟動。 您可以變更原生應用程式，在Mac或Windows中開啟特定的檔案類型（副檔名）。

從資產功能表按一下&#x200B;**[!UICONTROL Open]**。 資產會在本機下載並在原生應用程式中開啟。 在狀態列中檢查大型資產的下載進度和傳輸速度。

<!-- ![Download progress bar for large-sized assets](assets/download_status_bar_da2.png "Download progress bar for large-sized assets")
-->

>[!NOTE]
>
>如果預期的變更未反映在應用程式中，請按一下重新整理圖示![重新整理圖示](assets/do-not-localize/refresh.png)，或在應用程式介面中按一下滑鼠右鍵，然後按一下&#x200B;**[!UICONTROL Refresh]**。 當較大的下載或上傳正在進行時，無法使用這些動作。

若要開啟資產的本機下載檔案夾，請按一下「更多動作」圖示](assets/do-not-localize/more2_da2.png)，然後按一下「顯示」圖示](assets/do-not-localize/reveal_action2_da2.png) **[!UICONTROL Reveal File]**&#x200B;動作。![![

## 使用資產或將資產放入原生檔案{#place-assets-in-native-documents}

在某些情況下，例如將資產放入原生檔案時，您可以在Windows檔案總管或Mac Finder中存取檔案。 若要進入本機下載檔案的檔案系統位置，請使用![顯現圖示](assets/do-not-localize/reveal_action2_da2.png) **[!UICONTROL Reveal File]**&#x200B;選項。

![資產的「顯現檔案」動](assets/revealfile_action_da2.png "作資產的「顯現檔案」動作")

按一下資料夾上的&#x200B;**[!UICONTROL Reveal File]**&#x200B;或&#x200B;**[!UICONTROL Reveal Folder]**，開啟Windows資源管理器或Mac Finder，並在本地電腦上預選檔案或資料夾。 此選項對於將[!DNL Experience Manager]檔案放置在支援放置或連結本機檔案的原生應用程式中非常有用。 要瞭解如何在Adobe InDesign放置檔案，請參閱[放置圖形](https://helpx.adobe.com/indesign/using/placing-graphics.html)。

**[!UICONTROL Reveal File]**&#x200B;動作會開啟本機網路共用，僅顯示本機可用的資產，亦即顯示使用應用程式揭露、下載或開啟／編輯的資產。 本地網路共用不會將任何更改上載到[!DNL Experience Manager]。 若要上傳變更，請在應用程式中明確使用&#x200B;**[!UICONTROL Upload Changes]**&#x200B;或&#x200B;**[!UICONTROL Upload]**&#x200B;動作。

>[!NOTE]
>
>為向後相容於[!DNL Experience Manager]案頭應用程式v1.x，透過本機網路共用來提供顯示的檔案，僅公開本機可用的檔案。 顯示檔案的案頭路徑與應用程式v1.x建立的路徑相同。

>[!CAUTION]
>
>請勿使用&#x200B;**[!UICONTROL Reveal File]**&#x200B;選項來編輯原生應用程式中的資產。 請改用&#x200B;**[!UICONTROL Edit]**&#x200B;動作。 如需詳細資訊，請參閱[進階工作流程：在相同檔案上共同作業，避免編輯衝突](#adv-workflow-collaborate-avoid-conflicts)。

## 編輯資產並上傳更新的資產至[!DNL Experience Manager] {#edit-assets-upload-updated-assets}

當您要進行變更並將更新的資產上傳至AExperience ManagerEM伺服器時，請開啟資產以供編輯。 若要避免與其他使用者的編輯衝突，請使用應用程式來啟動編輯工作階段。 開始編輯之前，請確定資產上沒有鎖定圖示，亦即，其他使用者未編輯資產。

若要編輯資產，請搜尋資產或瀏覽至資產的位置。 按一下![更多表徵圖](assets/do-not-localize/more2_da2.png) ，然後按一下&#x200B;**[!UICONTROL Edit]**。

使用&#x200B;**[!UICONTROL Toggle Check-out]**&#x200B;鎖定資產，以防止在以下兩種情況下與其他使用者的編輯衝突：

* 您已開始編輯資產，但未先勾選（例如只開啟資產）。
* 您打算很快開始編輯資產，而不希望其他人編輯。

完成編輯後，應用程式會顯示已變更資產的&#x200B;**[!UICONTROL Edited Locally]**&#x200B;狀態。 儲存至資產的所有變更都僅限本機，直到您將變更上傳至[!DNL Experience Manager]為止。 若要逐一上傳個別或數個資產，請從資產選項按一下&#x200B;**[!UICONTROL Upload Changes]**。 它會在[!DNL Experience Manager]中建立資產版本。 使用[!DNL Assets]的Web介面，您可在[時間軸檢視](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/activity-stream.html)中查看資產歷史記錄。

![應用程式中的上傳變更選](assets/upload_changes_single1_da2.png "項應用程式中的上傳變更選項")

![檢視資產大型預覽時上傳變更選](assets/upload_changes_single2_da2.png "項檢視資產大型預覽時上傳變更選項")

如需協作編輯的最佳實務，請參閱[進階工作流程：在相同檔案上共同作業，避免編輯衝突](#adv-workflow-collaborate-avoid-conflicts)。

在下列情況下，您可能會想要放棄對本機資產所做的變更和編輯。 按一下 **[!UICONTROL Discard Changes]**.

* 如果您不想在[!DNL Experience Manager]中保存本地更改。
* 儲存部分變更後，開始對原始資產進行變更。
* 不再需要編輯資產時，請停止編輯。

如有必要，請切換結帳。 更新的資產會從本機快取資料夾中移除，當您編輯或開啟時，會再次下載。

## 上傳新資產並新增至[!DNL Experience Manager] {#upload-and-add-new-assets-to-aem}

使用者可以新增資產至DAM儲存庫。 例如，您可能是廣告公司攝影師或承包商，想要將大量像片從像片拍攝新增至[!DNL Experience Manager]儲存庫。 若要新增內容至[!DNL Experience Manager]，請在應用程式頂端列中選取![上傳至雲端選項](assets/do-not-localize/upload_to_cloud_da2.png)。 瀏覽至本機檔案系統中的資產檔案，然後按一下&#x200B;**[!UICONTROL Select]**。 或者，在應用程式介面上拖動檔案或資料夾。 應用程式會開始上傳資產。 如果上傳時間較長，應用程式會在底部顯示進度列。 建立或上傳檔案夾時，請勿使用空格和無效字元。 請參閱[ [!DNL Assets]](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#creating-folders)中建立資料夾的允許字元清單。

<!-- ![Download progress bar for large-sized assets](assets/upload_status_da2.png "Download progress bar for large-sized assets")
-->

您可以從本機檔案系統上傳檔案夾或個別檔案。 資料夾的階層會在上傳時保留。 在大量上傳資產之前，請參閱[大量上傳](#bulk-upload-assets)。

要查看指定會話中傳輸的資產清單，請按一下&#x200B;**[!UICONTROL View]** > **[!UICONTROL Assets transfers]**。 該清單允許您查看並快速驗證當前會話的檔案傳輸。

![特定會話中的已轉讓資產清](assets/assets_transfered_da2.png "單特定會話中已轉讓資產清單")

您可以在&#x200B;**[!UICONTROL Preferences]** > **[!UICONTROL Upload acceleration]**&#x200B;設定中控制上傳並行（加速）。 並行性更強通常可加快上傳速度，但會耗費大量資源，耗用本機電腦的處理能力。 如果您遇到系統速度緩慢，請使用較低的並行值重新嘗試上載。

>[!NOTE]
>
>如果您退出應用程式並重新開啟，傳輸清單不會持續存在，也無法使用。

>[!NOTE]
>
>如果檔案無法上傳，且您要連接到[!DNL Experience Manager] 6.5.1或更新版本的部署，請參閱此[疑難排解資訊](troubleshoot.md#upload-fails)。

## 使用多個資產{#work-with-multiple-assets}

使用者可使用動作（例如一次上傳所有編輯或按幾下滑鼠上傳巢狀資料夾），輕鬆處理並管理多個資產。

### 瀏覽大型資料夾{#browse-large-folders}

使用包含許多資產的檔案夾時，請捲動以檢視更多資產。 若要使用鍵盤捲動，請按幾下Tab鍵，以在頂端選取資產。 請注意反白顯示的資產，以得知何時選取。 現在使用向下鍵來移動資產清單。

### 選取資產的快速動作{#quick-actions-for-selected-assets}

按一下幾個資產的縮圖，以選取資產。 若要選取所有資產，請按一下應用程式頂端列中的核取方塊。 應用程式底部的工具列會顯示一組共同適用於所有選取資產的動作。

![底部的工具列顯示與選取資產相關的動](assets/actions_bottom_toolbar1_da2.png "作底部的工具列顯示選取資產的一般動作")

![沒有選取範圍的常用動作時工具列中沒有](assets/actions_bottom_toolbar2_da2.png "動作沒有選取範圍的常用動作時工具列中沒有動作")

底部工具列中可用的動作取決於選取檔案的狀態。 例如，如果只選擇&#x200B;**[!UICONTROL Edited Locally]**&#x200B;檔案，則會看到&#x200B;**[!UICONTROL Upload Changes]**&#x200B;表徵圖。 如果您選擇&#x200B;**[!UICONTROL Edited locally]**&#x200B;和&#x200B;**[!UICONTROL Cloud only]**&#x200B;的混合，則&#x200B;**[!UICONTROL Upload Changes]**&#x200B;動作不可用。

### 尋找所有編輯的影像{#find-all-edited-images}

應用程式提供一個稱為&#x200B;**[!UICONTROL Edited locally]**&#x200B;的檢視，讓您快速存取您在本機下載（透過[!UICONTROL Open]或[!UICONTROL Edit]動作）後進行修改的所有檔案。 應用程式可讓您選取所有本機編輯的資產，並按幾下滑鼠即可上傳變更。 此檢視也會顯示有編輯衝突的本機編輯資產。

![篩選以查看所有本機編輯的資](assets/edited_locally_filter_da2.png "產篩選以查看所有本機編輯的資產，例如大量上傳編輯")

### 大量上傳資產{#bulk-upload-assets}

使用者或組織（例如攝影師或創意廣告公司）可在場景中建立許多本機資產，例如像片拍攝、潤飾或從[!DNL Experience Manager]以外的較大集合中選取。 他們可以直接從案頭應用程式將這些大型的本機資料夾上傳至[!DNL Assets]。 資料夾階層會保留，而且會上傳所有巢狀子資料夾和包含的資產。 上傳的資產也可立即供相同伺服器的其他使用者使用。 資產會在背景上傳，因此作業不會系結至網頁瀏覽器作業。

![從案頭大量上傳多個本機資料夾至 [!DNL Experience Manager]](assets/upload_local_folders_da2.png "從案頭大量上傳多個本機資料夾至Experience Manager")

上傳後，如果預期的變更未反映在應用程式中，請按一下重新整理圖示![重新整理圖示](assets/do-not-localize/refresh.png)。

>[!NOTE]
>
>請勿使用上傳功能來移轉兩個[!DNL Experience Manager]部署的資產。 請參閱[遷移指南](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/assets-migration-guide.html)。

### 轉讓資產清單{#list-of-transferred-assets}

要查看指定會話中傳輸的資產清單，請參閱[將資產上傳到 [!DNL Experience Manager]](#upload-and-add-new-assets-to-aem)。

## 進階工作流程：從[!DNL Assets] Web介面{#adv-workflow-start-from-aem-ui}開始

如有必要，請從「資產」網頁介面啟動您的工作流程。 案頭應用程式已與[!DNL Experience Manager]整合，以在使用Desktop Actions提出要求時接管。

從Web介面啟動工作流程的特殊案例是資產發現。 資產使用者介面中的Omnisearch列提供豐富而進階的搜尋體驗。 您可能想先在Web上找到所需的資產，然後使用[!UICONTROL Desktop Actions]啟動應用程式中的工作流程。 有些範例包括使用Facet篩選搜尋結果、尋找從Adobe Stock取得授權的特定資產，或由您的組織實作的自訂，讓您從Web介面進行更好的搜尋。

當您嘗試在「資產」網頁介面上執行下列動作時，會使用案頭應用程式功能：

* 允許[!UICONTROL Open]、[!UICONTROL Edit]和[!UICONTROL Reveal]的[!UICONTROL Desktop Actions]
* [!UICONTROL Upload folder]
* [!UICONTROL Check-out] 或 [!UICONTROL check-in]

例如，適用於已在應用程式中籤出的資產的網頁介面動作有[!UICONTROL Open]、[!UICONTROL Reveal]和[!UICONTROL Check-in]。

![網頁介面中的案頭 [!DNL Experience Manager] 動作](assets/assets_web_actions_da2.png "Experience Manager網頁介面中的案頭動作")

>[!NOTE]
>
>瀏覽器可能會提示您允許啟動[!DNL Adobe Experience Manager]案頭。 若要享受從瀏覽器傳輸至應用程式的不間斷功能，請選取適當的核取方塊，讓應用程式隨時都能接手。

您無法使用Web介面找到下列資訊或工作流程。 使用案頭應用程式，因為網頁介面不會追蹤本機變更，而且不會察覺下列事項：

* 在本機編輯的檔案。
* 發生編輯衝突的檔案，以及解決衝突的方法。
* 將本機變更上傳至[!DNL Experience Manager]。
* 本機可用檔案的各種狀態。

相反地，您可以從案頭應用程式開始，使用&#x200B;**[!UICONTROL Open In Web]**&#x200B;動作，在網頁介面中開啟資產。

## 進階工作流程：在相同檔案上協作，避免編輯衝突{#adv-workflow-collaborate-avoid-conflicts}

在協作環境中，多位使用者可能會使用同一組資產，而這些資產可能會導致版本修訂衝突。 為防止衝突，請遵循以下最佳做法：

* 請勿按一下[!UICONTROL Open]來編輯任何資產。 請勿從檔案系統資料夾開啟，編輯本機下載的資產。 其他使用者不知道資產正在編輯中。
* 若要編輯資產，請一律按一下[!UICONTROL Edit]。 它會在原生應用程式中開啟資產，並在資產上新增鎖定圖示，讓其他使用者知道資產正在編輯中。
* 如果您不小心開始編輯而未按一下[!UICONTROL Edit]，請按一下[!UICONTROL Toggle Check-in]。 這會新增資產的鎖定圖示。 即使您打算稍後編輯資產，但不想讓其他人編輯資產，請按一下[!UICONTROL Toggle Check-in]以鎖定資產。
* 在編輯資產之前，請確定其他使用者未編輯資產。 尋找資產上的鎖定圖示。
* 完成編輯後，請上傳所有變更，然後登入資產。

![編輯衝突狀](assets/edits_conflicts_status_da2.png "態編輯衝突狀態")

如果本機下載的資產在[!DNL Experience Manager]伺服器上更新，應用程式會顯示&#x200B;**[!UICONTROL Modified remotely]**&#x200B;狀態。 您可以分別按一下[!UICONTROL Remove]或[!UICONTROL Update]，移除本機副本或重新整理本機副本。 對話框上的連結允許您查看資產的兩個版本。

![遠程修改資產時解決衝突的選](assets/modified_remotely_dialog_da2.png "項遠程修改資產時解決衝突的選項")

如果您正在本機編輯的資產也會在伺服器上更新，但您不知情，應用程式會顯示&#x200B;**[!UICONTROL Editing Conflict]**&#x200B;狀態。 您可以保留一組變更——保留您的更新（按一下&#x200B;**[!UICONTROL Keep Mine]**）並刪除其他使用者的編輯，或尊重其他使用者的更新並刪除您的更新(**[!UICONTROL Overwrite Mine]**)。

![解決編輯衝突的選](assets/editing_conflict_dialog_da2.png "項解決編輯衝突的選項")

## 進階工作流程：放置和連結資產至InDesign檔案{#adv-workflow-place-assets-indesign}

當您使用[!DNL Experience Manager]案頭應用程式開啟包含連結資產的檔案時，資產會預先下載並顯示在原生應用程式中。 要使此工作流程正常運作，您的原生應用程式必須支援放置本機資產的連結，而[!DNL Experience Manager]必須支援將二進位檔案中的這些連結解析為伺服器端參照。

[!DNL Experience Manager] 案頭應用程式支援此工作流程，其中包含幾種精選的Adobe Creative Cloud案頭應用程式和檔案格式-Adobe InDesign、Adobe Illustrator和Adobe Photoshop。工作流程可讓您有效率地處理支援的Creative Cloud檔案。 因此，如果使用者A將一些資產放入InDesign檔案並將其簽入[!DNL Experience Manager]，使用者B會在InDesign檔案中看到資產，即使這些資產不在檔案中。 這些資產會在使用者B的機器上本機下載。

>[!NOTE]
>
>案頭應用程式可以對應至Windows上的任何磁碟機。 但是，對於平滑操作，請勿更改預設驅動器盤符。 如果同一組織的使用者使用不同的磁碟盤符，則無法看到其他人放置的資產。 路徑變更時，不會擷取置入的資產。 置入的資產會繼續置入二進位檔案（例如INDD）中，且不會移除。

要瞭解此工作流程的限制，請參閱[系統需求和支援的版本](release-notes.md)。

若要使用此工作流程搭配影像資產和InDesign，請依照下列步驟進行：

1. 使用[!DNL Experience Manager]中已置入資產的INDD檔案，讓您隨時都能使用。 要瞭解如何建立此類INDD檔案，請參閱[放置圖形](https://helpx.adobe.com/indesign/using/placing-graphics.html)。
1. 在案頭應用程式中，**[!UICONTROL Edit]**&#x200B;包含已置入資產的INDD檔案位於[!DNL Experience Manager]。
1. 應用程式會同時下載InDesign檔案和連結的資產。 InDesign開啟檔案時，會解析連結、下載資產，並在InDesign檔案中顯示資產。
1. 要在InDesign檔案中放置新圖形，請對資產使用&#x200B;**[!UICONTROL Reveal File]**&#x200B;操作。 此動作會在本機下載資產，並在Windows檔案總管或Mac Finder中開啟本機網路共用位置。
1. 將顯示的資產放入InDesign文檔中。 這會在文檔中建立連結。
1. 在您完成InDesign檔案中的編輯後，請加以儲存，然後使用案頭應用程式將其上傳至[!DNL Experience Manager]。

## 進階工作流程：本機下載資產{#adv-workflow-download-assets-locally}

應用程式會在許多情況下從您檔案系統的本機[!DNL Experience Manager]伺服器下載資產。 下載會佔用頻寬和磁碟空間。 瞭解這些案例有助於您最佳化等待下載完成的時間。

您可以隨選從應用程式內下載資產。 請參閱[下載資產](#download-assets)。

當您使用[!UICONTROL Open]動作在原生案頭應用程式中開啟資產時，如果本機尚未提供資產，則會在本機下載資產。 請參閱[Open assets](#openondesktop-v2)。

當您從應用程式中揭示資產或資料夾的位置時，資產或資料夾會先在本機下載，然後在本機網路共用的電腦上開啟。 請參閱[Open assets](#openondesktop-v2)。

當您使用[!UICONTROL Edit]動作編輯原生案頭應用程式中的資產時，如果本機尚未提供資產，則會在本機下載資產。 請參閱[編輯資產並將更新的資產上傳至 [!DNL Experience Manager]](#edit-assets-upload-updated-assets)。

如果應用程式已安裝並獲准使用，它會在您從[!DNL Experience Manager]網頁介面使用[!UICONTROL Desktop Actions]時完成動作。 應用程式會先下載資產，然後完成動作。
