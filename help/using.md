---
title: 使用 [!DNL Experience Manager] 案頭應用程式
description: 直接從Win或Mac案頭使用 [!DNL Adobe Experience Manager] desktop app, to work with [!DNL Adobe Experience Manager] DAM資產，並用於其他應用程式。
mini-toc-levels: 1
feature: 案頭應用程式，資產管理
exl-id: fa19d819-231a-4a01-bfd2-6bba6fec2f18
source-git-commit: dcd29d0bbb32004d970d334c256e659f4a4c39e1
workflow-type: tm+mt
source-wordcount: '4053'
ht-degree: 0%

---

# 使用[!DNL Adobe Experience Manager]案頭應用程式 {#use-aem-desktop-app-v2}

使用[!DNL Adobe Experience Manager]案頭應用程式，輕鬆存取儲存在本機案頭上[!DNL Adobe Experience Manager] DAM存放庫中的數位資產，並在任何案頭應用程式中使用這些資產。 您可以在案頭應用程式中開啟資產，並在本機編輯資產 — 透過版本控制將變更上傳回[!DNL Experience Manager]，以與其他使用者共用更新。 您也可以將新檔案和資料夾階層上傳至[!DNL Experience Manager]、建立資料夾，以及從[!DNL Experience Manager] DAM刪除資產或資料夾。

整合可讓組織中的各種角色在[!DNL Experience Manager Assets]中集中管理資產，以及在Windows或Mac OS的原生應用程式中存取本機案頭上的資產。

在登出後或首次開啟應用程式時，請以`https://[aem-server-url]:[port]/`格式提供[!DNL Experience Manager]伺服器的URL。 然後選取[!UICONTROL Connect]選項。 提供憑證以將應用程式與伺服器連線。

使用[!DNL Experience Manager]案頭應用程式所執行的主要任務為：

![使用案頭應用程式可完成的工作 [!DNL Experience Manager] 流程和](assets/aem_desktop_app_usecases_v2.png "任務使用案頭應用程式可完成的工作 [!DNL Adobe Experience Manager] 流程")
下載此可 [](assets/aem_desktop_app_usecases_print.pdf) 打印的PDF檔案。

## 案頭應用程式如何運作 {#how-app-works2}

開始使用應用程式之前，請先了解[應用程式的運作方式](release-notes.md#how-app-works)。 此外，請熟悉下列詞語：

* **[!UICONTROL Desktop Actions]**:從「資產」網頁介面，從瀏覽器內探索資產位置或簽出並開啟資產，以便在原生案頭應用程式中進行編輯。這些動作可從網頁介面使用案頭應用程式功能。 請參閱[如何啟用案頭操作](using.md#desktopactions-v2)。

* 檔案狀態為&#x200B;**[!UICONTROL Cloud Only]**:此類資產不會下載到本機電腦上，且僅可在[!DNL Experience Manager]伺服器上使用。

* 檔案狀態為&#x200B;**[!UICONTROL Available locally]**:資產會下載，並依原樣在本機電腦上提供。 資產不會變更。

* 檔案狀態為&#x200B;**[!UICONTROL Edited locally]**:這些資產會在本機修改，且變更會保留至上傳至[!DNL Experience Manager]伺服器。 上傳後，狀態會變更為[!UICONTROL Available locally]。 請參閱[編輯資產](using.md#edit-assets-upload-updated-assets)。

* 檔案狀態為&#x200B;**[!UICONTROL Editing conflict]**:如果您和其他使用者同時修改資產，應用程式會指出發生編輯衝突。 應用程式也提供保留或捨棄變更的選項。 請參閱[如何避免編輯衝突](using.md#adv-workflow-collaborate-avoid-conflicts)。

* 檔案狀態為&#x200B;**[!UICONTROL Modified remotely]**:應用程式會指出您下載的資產是否在[!DNL Experience Manager]伺服器上變更。 應用程式也提供下載最新版本和更新本機副本的選項。 請參閱[如何避免編輯衝突](using.md#adv-workflow-collaborate-avoid-conflicts)。

* **[!UICONTROL Check-out]**:如果要編輯檔案或要編輯檔案，則可切換要簽出的狀態。它會在應用程式和[!DNL Experience Manager]網頁介面中的資產上新增鎖定圖示。 鎖定圖示會向其他使用者指出，避免同時編輯相同的資產，因為這會導致編輯衝突。

* **[!UICONTROL Check-in]**:將資產標示為安全，讓其他使用者可以編輯，而不會造成編輯衝突。上傳變更時，鎖定圖示會自動移除。 切換簽入狀態也會刪除鎖定表徵圖，不過建議不要在不上載更改的情況下手動簽入。 如果您放棄更改，則手動切換簽入。

* **[!UICONTROL Open]** 動作：只需開啟資產，在原生應用程式中預覽。不建議使用此動作來編輯資產，因為它不會簽出資產，而其他使用者可以進行編輯而導致編輯衝突。

* **[!UICONTROL Edit]** 動作：使用動作來修改影像。按一下[!UICONTROL Edit]動作會自動勾出資產並在資產上新增鎖定圖示。 按一下「編輯」後，如果您不想編輯資產，請按一下「[!UICONTROL Toggle check-in]」。 若要刪除、重新命名或移動[!DNL Experience Manager] DAM資料夾階層中的資產，請使用[!DNL Experience Manager]網頁介面動作，而非編輯動作。

* **[!UICONTROL Download]** 動作：將資產下載至本機電腦。您可以立即下載資產，稍後再編輯；離線工作，稍後上傳變更。 資產會下載至檔案系統上的快取資料夾中。

* **[!UICONTROL Reveal File]** 或動 **[!UICONTROL Reveal Folder]** 作：當資產下載至本機快取資料夾時，應用程式會模擬本機網路磁碟，並為每個資產提供本機路徑。若要知道此路徑，請在應用程式中使用適當的顯現選項。 在Creative Cloud應用程式中放置資產時，需要顯示操作。 請參閱[放置資產](using.md#place-assets-in-native-documents)。

* **[!UICONTROL Open In Web]** 動作：若要在Web介面中 [!DNL Experience Manager] 檢視資產，請在Web中開啟資產。您可以從[!DNL Experience Manager]介面起始更多工作流程，例如更新中繼資料或資產探索。

* **[!UICONTROL Delete]** 動作：從DAM存放庫刪 [!DNL Experience Manager] 除資產。動作會刪除Experience Manager伺服器上資產的原始復本。 如果您只想捨棄對本機資產的修改，請參閱[捨棄變更](using.md#edit-assets-upload-updated-assets)。

* **[!UICONTROL Upload Changes]**:只有當您明確上傳至伺服器時，案頭應用程式才會上傳更新的 [!DNL Experience Manager] 資產。儲存編輯時，變更只會儲存在本機電腦上。 上傳時，資產會自動簽入並移除鎖定圖示。 請參閱[編輯資產](using.md#edit-assets-upload-updated-assets)。

## 在[!DNL Experience Manager] Web介面中啟用案頭操作 {#desktopactions-v2}

從瀏覽器的[!DNL Assets]使用者介面中，您可以探索資產位置或結帳並開啟資產，以便在案頭應用程式中進行編輯。 這些選項稱為[!UICONTROL Desktop Actions]，預設情況下未啟用。 若要啟用此功能，請依照下列步驟操作。

1. 在[!DNL Assets]主控台中，按一下工具列中的&#x200B;**[!UICONTROL User]**&#x200B;圖示。
1. 按一下&#x200B;**[!UICONTROL My Preferences]**&#x200B;以顯示&#x200B;**[!UICONTROL Preferences]**&#x200B;對話方塊。

1. 在[!UICONTROL User Preferences]對話方塊中，選取&#x200B;**[!UICONTROL Show Desktop Actions For Assets]**，然後按一下&#x200B;**[!UICONTROL Accept]**。


   ![選取「顯示資產的案頭動作」以啟用案頭動作](assets/enable_desktop_actions.png)

   *圖：選擇 [!UICONTROL Show Desktop Actions For Assets] 以啟用案頭操作。*

## 瀏覽、搜尋和預覽資產 {#browse-search-preview-assets}

您可以瀏覽、搜尋和預覽[!DNL Experience Manager]存放庫中可用的資產，所有這些資產都可從案頭應用程式內進行。 在應用程式中嘗試下列項目：

1. 瀏覽至資料夾，查看資料夾中可用資產的一些基本資訊，以及所有資產的小縮圖。

   ![瀏覽DAM檔案和資料](assets/browse_folder_da2.png "夾瀏覽DAM檔案和資料夾")

1. 若要檢視詳細資訊和個別資產的較大縮圖，請按一下檔案名稱。

   ![查看資產和動作的較大預覽](assets/large_preview_actions_da2.png "查看資產和動作的較大預覽")

1. 按一下&#x200B;**[!UICONTROL Open]**&#x200B;或&#x200B;**[!UICONTROL Edit]**&#x200B;將檔案下載到本地，只需在本地應用程式中查看或編輯該檔案即可。
1. 使用關鍵字搜尋，以在[!DNL Experience Manager]存放庫中尋找相關資產。 使用`?`和`*`作為通配符。 這些萬用字元會分別取代單一字元或多個字元。 視需要篩選結果並排序。

   ![使用星號通配符的搜](assets/search_wildcard_da2.png "索示例使用星號通配符的搜索")

   ![使用星號通配符的另一](assets/search_wildcard2_da2.png "個示例搜索使用星號通配符的不同位置")

>[!NOTE]
>
>應用程式會在多個中繼資料欄位中比對搜尋條件，而不只是資產的標題或檔案名稱，以顯示資產。

## 下載資產 {#download-assets}

您可以在本機檔案系統上下載資產。 應用程式會從[!DNL Experience Manager]伺服器擷取資產，並將相同的副本儲存在本機檔案系統上。

按一下![更多選項表徵圖](assets/do-not-localize/more2_da2.png)獲取選項，然後按一下![下載表徵圖](assets/do-not-localize/download_cloud_da2.png)下載。

![資產的下載選](assets/download_option_da2.png "項資產的下載選項")

>[!NOTE]
>
>下載或上傳大型檔案或許多檔案時，應用程式會關閉資產和資料夾上的動作。 下載或上傳完成時，即可使用這些動作。

如果佇列大小很大或您遇到網路問題，下載多個資產可能會導致效能不佳。 此外，下載資料夾時，您可能會在不知情的情況下將許多資產排入下載佇列。 為避免等候時間過長，應用程式會限制一次下載的資產數量。 要了解如何配置，請參閱[設定首選項](install-upgrade.md#set-preferences)。 即使低於此限制，應用程式也可能會在下載明顯較大的資料夾之前，尋求確認。

![應用程式確認下載相對大量的](assets/download_confirmation_da2.png "資產應用程式確認下載相對大量的資產")

如果選取並下載資料夾，應用程式只會下載直接儲存在[!DNL Experience Manager]資料夾中的資產。 它不會自動從子資料夾下載資產。

## 在案頭上開啟資產 {#openondesktop-v2}

您可以開啟遠端資產，以在原生應用程式中檢視。 資產會下載至本機資料夾，並在與檔案格式相關聯的原生應用程式中啟動。 您可以變更原生應用程式，以在Mac或Windows中開啟特定的檔案類型（副檔名）。

從資產功能表按一下&#x200B;**[!UICONTROL Open]**。 資產會在本機下載，並在原生應用程式中開啟。 在狀態列中檢查大型資產的下載進度和傳輸速度。

<!-- ![Download progress bar for large-sized assets](assets/download_status_bar_da2.png "Download progress bar for large-sized assets")
-->

>[!NOTE]
>
>如果應用程式未反映預期的變更，請按一下重新整理圖示![重新整理圖示](assets/do-not-localize/refresh.png)，或在應用程式介面中按一下滑鼠右鍵，然後按一下&#x200B;**[!UICONTROL Refresh]**。 當正在進行較大的下載或上載時，這些操作不可用。

若要開啟資產的本機下載資料夾，請按一下「![更多動作」圖示](assets/do-not-localize/more2_da2.png)，然後按一下「![顯示」圖示](assets/do-not-localize/reveal_action2_da2.png) **[!UICONTROL Reveal File]**&#x200B;動作。

## 使用資產或將資產放入原生檔案 {#place-assets-in-native-documents}

在某些情況下，例如將資產放入原生檔案時，您會在Windows檔案總管或Mac Finder中存取檔案。 要獲取本地下載檔案的檔案系統位置，請使用![顯示表徵圖](assets/do-not-localize/reveal_action2_da2.png) **[!UICONTROL Reveal File]**&#x200B;選項。

![資產的「顯示檔案」(Reveal File)操](assets/revealfile_action_da2.png "作資產的「顯示檔案」(Reveal File)操作")

在資料夾上按一下&#x200B;**[!UICONTROL Reveal File]**&#x200B;或&#x200B;**[!UICONTROL Reveal Folder]**，開啟Windows資源管理器或Mac Finder，並在本地電腦上預先選擇該檔案或資料夾。 此選項非常有用，例如將[!DNL Experience Manager]檔案放置在支援放置或連結本地檔案的本機應用程式中。 要查看如何在Adobe InDesign中放置檔案，請參閱[放置圖形](https://helpx.adobe.com/indesign/using/placing-graphics.html)。

**[!UICONTROL Reveal File]**&#x200B;動作會開啟本機網路共用，僅顯示本機可用的資產，亦即顯示使用應用程式顯示、下載或開啟/編輯的資產。 本地網路共用不將任何更改上載到[!DNL Experience Manager]。 若要上傳變更，請在應用程式中明確使用&#x200B;**[!UICONTROL Upload Changes]**&#x200B;或&#x200B;**[!UICONTROL Upload]**&#x200B;動作。

>[!NOTE]
>
>為了向後相容[!DNL Experience Manager]案頭應用程式v1.x，顯示的檔案是從本地網路共用提供的，僅顯示本地可用的檔案。 顯示檔案的案頭路徑與應用程式v1.x所建立的路徑相同。

>[!CAUTION]
>
>請勿使用&#x200B;**[!UICONTROL Reveal File]**&#x200B;選項來編輯原生應用程式中的資產。 請改用&#x200B;**[!UICONTROL Edit]**&#x200B;動作。 如需詳細資訊，請參閱[進階工作流程：對相同的檔案進行協作並避免編輯衝突](#adv-workflow-collaborate-avoid-conflicts)。

## 編輯資產並將更新的資產上傳至[!DNL Experience Manager] {#edit-assets-upload-updated-assets}

當您想要變更時，請開啟資產以進行編輯，並將更新的資產上傳至AExperience ManagerEM伺服器。 若要避免與其他使用者的編輯作業產生衝突，請使用應用程式起始編輯工作階段。 開始編輯之前，請確定資產上沒有鎖定圖示，也就是說，其他使用者並未編輯資產。

若要編輯資產，請搜尋資產或瀏覽至資產的位置。 按一下「![更多」表徵圖](assets/do-not-localize/more2_da2.png)，然後按一下「**[!UICONTROL Edit]**」。

使用&#x200B;**[!UICONTROL Toggle Check-out]**&#x200B;來鎖定資產，以防止在下列兩種情況下與其他使用者的編輯作業產生衝突：

* 您已開始編輯資產，但未先簽出（例如只開啟資產）。
* 您打算盡快開始編輯資產，但不希望其他人編輯。

完成編輯後，應用程式會顯示已變更資產的&#x200B;**[!UICONTROL Edited Locally]**&#x200B;狀態。 儲存至資產的所有變更都僅限本機，直到您將變更上傳至[!DNL Experience Manager]為止。 若要逐一上傳個別或數個資產，請從資產選項按一下&#x200B;**[!UICONTROL Upload Changes]**。 它會在[!DNL Experience Manager]中建立資產版本。 使用[!DNL Assets]的Web介面，您可以在[時間軸檢視](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/activity-stream.html)中查看資產歷史記錄。

![應用程式的appUpload變更選](assets/upload_changes_single1_da2.png "項中的上傳變更選項")

![檢視資產的大型預覽時上傳變更選](assets/upload_changes_single2_da2.png "項檢視資產的大型預覽時上傳變更選項")

如需協作編輯的最佳實務，請參閱[進階工作流程：對相同的檔案進行協作並避免編輯衝突](#adv-workflow-collaborate-avoid-conflicts)。

在下列情況下，您可能會想要捨棄變更，並編輯本機資產。 按一下 **[!UICONTROL Discard Changes]**.

* 如果您不想在[!DNL Experience Manager]中保存本地更改。
* 儲存部分變更後，開始對原始資產進行變更。
* 停止編輯資產，因為不再需要它。

如有必要，請切換簽出。 更新的資產會從本機快取資料夾中移除，並在您編輯或開啟資產時重新下載。

## 上傳新資產並將其新增至[!DNL Experience Manager] {#upload-and-add-new-assets-to-aem}

使用者可以新增資產至DAM存放庫。 例如，您可能是機構攝影師或承包商，希望將大量照片從照片添加到[!DNL Experience Manager]儲存庫。 若要新增內容至[!DNL Experience Manager]，請在應用程式頂端列選取![上傳至雲端選項](assets/do-not-localize/upload_to_cloud_da2.png)。 瀏覽到本地檔案系統中的資產檔案，然後按一下&#x200B;**[!UICONTROL Select]**。 或者，若要上傳資產，請拖曳應用程式介面上的檔案或資料夾。 在Windows上，如果您將資產拖曳至應用程式內的資料夾，資產就會上傳至資料夾。 如果上傳所需時間較長，應用程式會顯示進度列。

<!-- ![Download progress bar for large-sized assets](assets/upload_status_da2.png "Download progress bar for large-sized assets")
-->

您可以從本機檔案系統上傳資料夾或個別檔案。 資料夾的階層會在上傳時保留。 在大量上傳資產之前，請參閱[大量上傳](#bulk-upload-assets)。

若要檢視指定工作階段中轉移的資產清單，請按一下「**[!UICONTROL View]** > **[!UICONTROL Assets transfers]**」。 清單可讓您檢視並快速驗證目前工作階段的檔案傳輸。

![特定會話中已轉移資產清](assets/assets_transfered_da2.png "單特定會話中已轉移資產清單")

您可以在&#x200B;**[!UICONTROL Preferences]** > **[!UICONTROL Upload acceleration]**&#x200B;設定中控制上傳併發（加速）。 更多併發通常提供更快的上載速度，但可能需要大量資源，佔用本地電腦的更大處理能力。 如果系統速度慢，請使用較低的併發值重新嘗試上載。

>[!NOTE]
>
>傳輸清單不具永久性，且如果您退出應用程式並重新開啟該應用程式，將無法使用。

### 管理資產名稱中的特殊字元 {#special-characters-in-filename}

在舊版應用程式中，儲存庫中建立的節點名稱會保留使用者提供之資料夾名稱的空格和大小寫。 要使當前應用程式模擬v1.10應用程式的節點命名規則，請在[!UICONTROL Preferences]中啟用[!UICONTROL Use legacy conventions when creating nodes for assets and folders]。 請參閱[應用程式偏好設定](/help/install-upgrade.md#set-preferences)。 此舊式偏好設定預設為停用。

>[!NOTE]
>
>應用程式只會使用下列命名慣例來變更存放庫中的節點名稱。 應用程式會依原樣保留資產的`Title`。

<!-- TBD: Do NOT use this table.

| Where do characters occur | Characters | Legacy preference | Renaming convention | Example |
|---|---|---|---|---|
| In file name extension | `.` | Enabled or disabled | Retained as is | NA |
| File or folder name | `. / : [ ] | *` | Enabled or disabled | Replaced with a `-` (hyphen) | `myimage.jpg` remains as is and `my.image.jpg` changes to `my-image.jpg`. |
| Folder name | `% ; # , + ? ^ { } "` | Disabled | Replaced with a `-` (hyphen) | tbd |
| File name | `% # ? { } &` | Disabled | Replaced with a `-` (hyphen) | tbd |
| File name | Whitespaces | Enabled or disabled | Retained as is | NA |
| Folder name | Whitespaces | Disabled | Replaced with a `-` (hyphen) | tbd |
| File name | Uppercase characters | Disabled | Retained as is | tbd |
| Folder name | Uppercase characters | Disabled | Replaced with a `-` (hyphen) | tbd |
-->

| 字元數 ‡ | 應用程式中的舊式偏好設定 | 檔案名稱中發生時 | 資料夾名稱中發生時 | 範例 |
|---|---|---|---|---|
| `. / : [ ] | *` | 啟用或停用 | 替換為`-`（連字型大小）。 副檔名中的`.`（圓點）會依原樣保留。 | 替換為`-`（連字型大小）。 | `myimage.jpg` 保持不變，且 `my.image.jpg` 會變 `my-image.jpg`更。 |
| `% ; # , + ? ^ { } "` 和空格 | ![取消選擇](assets/do-not-localize/deselect-icon.png) 表徵圖禁用 | 會保留空格 | 替換為`-`（連字型大小）。 | `My Folder.` 變更為 `my-folder-`。 |
| `# % { } ? & .` | ![取消選擇](assets/do-not-localize/deselect-icon.png) 表徵圖禁用 | 替換為`-`（連字型大小）。 | 不適用. | `#My New File.` 變更為 `-My New File-`。 |
| 大寫字元 | ![取消選擇](assets/do-not-localize/deselect-icon.png) 表徵圖禁用 | 外殼保持原樣。 | 已變更為小寫字元。 | `My New Folder` 變更為 `my-new-folder`。 |
| 大寫字元 | ![選取的已核取](assets/do-not-localize/selection-checked-icon.png) 圖示已啟用 | 外殼保持原樣。 | 外殼保持原樣。 | 不適用. |

*字元清單以空白字元分隔。

<!-- TBD: Check if the following is to be included in the footnote.

Do not use &#92;&#92; in the names of files and &#92;&#116; &#38; in the names of folders. 
-->


<!-- TBD: Securing the below presentation of the same content in a comment.

**File names**

| Characters | Replaced by |
|---|---|
| &#35; &#37; &#123; &#63; &#125; &#38; &#46; &#47; &#58; &#91; &#124; &#93; &#42; | hyphen (-) |
| whitespaces | whitespaces are retained |
| capital case | casing is retained |

>[!CAUTION]
>
>Avoid using &#92;&#92; in file names.

**Folder names**

| Characters | Replaced by |
|---|---|
| Characters | Replaced by |
| &#37; &#59; &#35; &#44; &#43; &#63; &#94; &#123; &#123; &#34; &#46; &#47; &#59; &#91; &#93; &#124; &#42; | hyphen (-) |
| whitespaces | hyphen (-) |
| capital case | lower case |

>[!CAUTION]
>
>Avoid using &#92;&#92; &#92;&#116; &#38; in folder names.

>[!NOTE]
>
>If you enable [!UICONTROL Use legacy conventions when creating nodes for assets and folders] in app [!UICONTROL Preferences], then the app emulates v1.10 app behavior when uploading folders. In v1.10, the node names created in the repository respect spaces and casing of the folder names provided by the user. For more information, see [app Preferences](/help/install-upgrade.md#set-preferences).

-->

## 使用多個資產 {#work-with-multiple-assets}

使用者可以透過一次上傳所有編輯內容，或只要按幾下即可上傳巢狀資料夾等動作，輕鬆處理及管理多個資產。

### 瀏覽大型資料夾 {#browse-large-folders}

使用包含許多資產的資料夾時，請捲動以檢視更多資產。 若要使用鍵盤捲動，請按下Tab鍵幾次，以在頂端選取資產。 請注意醒目提示的資產，以知道其選取時間。 現在請使用向下鍵來瀏覽資產清單。

### 所選資產的快速動作 {#quick-actions-for-selected-assets}

按一下數個資產的縮圖，以選取資產。 若要選取所有資產，請按一下應用程式頂端列的核取方塊。 應用程式底部的工具列中，會顯示一組共同適用於所有選取資產的動作。

![底部的工具列顯示與所選資產相關的動](assets/actions_bottom_toolbar1_da2.png "作底部的工具列顯示所選資產的一般動作")

![沒有選取範圍的常見動作時工具列中沒有動作選取範圍](assets/actions_bottom_toolbar2_da2.png "沒有選取範圍的常見動作時工具列中沒有動作")

底部工具列中可用的動作取決於選取檔案的狀態。 例如，如果僅選擇&#x200B;**[!UICONTROL Edited Locally]**&#x200B;檔案，則會看到&#x200B;**[!UICONTROL Upload Changes]**&#x200B;表徵圖。 如果選擇&#x200B;**[!UICONTROL Edited locally]**&#x200B;和&#x200B;**[!UICONTROL Cloud only]**&#x200B;的組合，則&#x200B;**[!UICONTROL Upload Changes]**&#x200B;操作不可用。

### 查找所有已編輯的影像 {#find-all-edited-images}

應用程式提供一個稱為&#x200B;**[!UICONTROL Edited locally]**&#x200B;的視圖，讓您快速訪問本地下載的所有檔案（通過[!UICONTROL Open]或[!UICONTROL Edit]操作），然後進行修改。 應用程式可讓您選取所有在本機編輯的資產，並按幾下即可上傳變更。 此檢視也會顯示有編輯衝突之本機編輯的資產。

![篩選以查看所有在本機編輯的](assets/edited_locally_filter_da2.png "資產篩選可查看所有在本機編輯的資產，例如大量上傳編輯")

### 大量上傳資產 {#bulk-upload-assets}

使用者或組織（例如攝影師或創意經紀）可在案例中建立許多本機資產，例如拍攝、潤飾或從在[!DNL Experience Manager]外完成的較大集合中選取。 他們可以直接從案頭應用程式將這些大型本機資料夾上傳至[!DNL Assets]。 會保留資料夾階層，並上傳所有巢狀子資料夾和包含的資產。 上傳的資產也可立即供相同伺服器的其他使用者使用。 資產會在背景上傳，因此作業不會系結至網頁瀏覽器工作階段。

![從案頭大量上傳多個本機資料夾至從案 [!DNL Experience Manager]](assets/upload_local_folders_da2.png "頭大量上傳多個本機資料夾至Experience Manager")

上傳後，如果應用程式未反映預期的變更，請按一下重新整理圖示![重新整理圖示](assets/do-not-localize/refresh.png)。

>[!NOTE]
>
>請勿使用上傳功能來跨兩個[!DNL Experience Manager]部署移轉資產。 請改為參閱[遷移指南](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/assets-migration-guide.html)。

### 已轉移資產清單 {#list-of-transferred-assets}

若要檢視指定工作階段中轉移的資產清單，請參閱[將資產上傳至 [!DNL Experience Manager]](#upload-and-add-new-assets-to-aem)。

## 進階工作流程：從[!DNL Assets] web介面開始 {#adv-workflow-start-from-aem-ui}

如有需要，從Assets網頁介面起始您的工作流程。 案頭應用程式與[!DNL Experience Manager]整合，以便在使用案頭動作提出請求時接管。

從Web介面啟動工作流程的特殊案例是資產探索。 Assets使用者介面中的Omnisearch列提供豐富的進階搜尋體驗。 您可能想要先在網頁上找到所需的資產，然後使用[!UICONTROL Desktop Actions]在應用程式中起始工作流程。 部分範例案例包括使用Facet篩選搜尋結果、找到從Adobe Stock授權的特定資產，或由貴組織實作的自訂，讓您能從Web介面進行更好的探索。

當您嘗試在Assets網頁介面上執行下列動作時，會使用案頭應用程式功能：

* 允許[!UICONTROL Open]、[!UICONTROL Edit]和[!UICONTROL Reveal]的[!UICONTROL Desktop Actions]
* [!UICONTROL Upload folder]
* [!UICONTROL Check-out] 或 [!UICONTROL check-in]

例如，可用於已在應用程式中籤出之資產的網頁介面動作為[!UICONTROL Open]、[!UICONTROL Reveal]及[!UICONTROL Check-in]。

![Web介面中的案頭 [!DNL Experience Manager] 操作](assets/assets_web_actions_da2.png "Experience ManagerWeb介面中的案頭操作")

>[!NOTE]
>
>瀏覽器可能會提示您允許啟動[!DNL Adobe Experience Manager]案頭。 若要享受從瀏覽器傳輸至應用程式的不間斷傳輸，請選取適當的核取方塊，一律允許應用程式接管。

您無法使用Web介面找到以下資訊或工作流。 使用案頭應用程式，因為網頁介面不會追蹤本機變更且不知道下列項目：

* 在本機編輯的檔案。
* 編輯衝突的檔案及解決方法。
* 將本機變更上傳至[!DNL Experience Manager]。
* 本機可用檔案的各種狀態。

相反地，您可以從案頭應用程式開始，使用&#x200B;**[!UICONTROL Open In Web]**&#x200B;動作，在網頁介面中開啟資產。

## 進階工作流程：在同一檔案上協作，避免編輯衝突 {#adv-workflow-collaborate-avoid-conflicts}

在協作環境中，多個使用者可能會處理同一組資產，而這可能導致版本設定衝突。 要防止衝突，請遵循以下最佳做法：

* 請勿按一下[!UICONTROL Open]來編輯任何資產。 請勿從檔案系統資料夾開啟，以編輯本機下載的資產。 其他使用者不知道正在編輯資產。
* 若要編輯資產，請一律按一下[!UICONTROL Edit]。 它會在原生應用程式中開啟資產，並在資產上新增鎖定圖示，讓其他使用者知道資產正在編輯中。
* 如果您不小心開始編輯而未點按[!UICONTROL Edit]，請按一下「[!UICONTROL Toggle Check-in]」。 這會將鎖定圖示新增至資產。 即使您打算稍後編輯資產，但不想讓其他人編輯資產，請按一下「[!UICONTROL Toggle Check-in]」以鎖定資產。
* 編輯資產之前，請確定其他使用者未編輯資產。 尋找資產上的鎖定圖示。
* 完成編輯後，上傳所有變更，然後簽入資產。

![編輯衝突的](assets/edits_conflicts_status_da2.png "狀態編輯衝突的狀態")

如果本機下載的資產在[!DNL Experience Manager]伺服器上更新，應用程式會顯示&#x200B;**[!UICONTROL Modified remotely]**&#x200B;狀態。 您可以分別按一下[!UICONTROL Remove]或[!UICONTROL Update]來移除本機副本或重新整理本機副本。 對話方塊上的連結可讓您檢視資產的兩個版本。

![遠程修改資產時解決衝突的選](assets/modified_remotely_dialog_da2.png "項遠程修改資產時解決衝突的選項")

如果您在本機編輯的資產也在伺服器上更新，而您並不知情，應用程式會顯示&#x200B;**[!UICONTROL Editing Conflict]**&#x200B;狀態。 您可以保留一組更改 — 保留您的更新（按一下&#x200B;**[!UICONTROL Keep Mine]**）並刪除其他用戶的編輯，或保留其他用戶的更新並刪除您的更新(**[!UICONTROL Overwrite Mine]**)。

![解決編輯衝突的選](assets/editing_conflict_dialog_da2.png "項解決編輯衝突的選項")

## 進階工作流程：在InDesign檔案中放置及連結資產 {#adv-workflow-place-assets-indesign}

當您使用[!DNL Experience Manager]案頭應用程式來開啟含有連結資產的檔案時，資產會預先下載並顯示在原生應用程式中。 若要讓此工作流程正常運作，您的原生應用程式必須支援放置本機資產的連結，且[!DNL Experience Manager]必須支援將二進位檔案中的這些連結解析為伺服器端參考。

[!DNL Experience Manager] 案頭應用程式透過一些精選的Adobe Creative Cloud案頭應用程式和檔案格式(Adobe InDesign、Adobe Illustrator和Adobe Photoshop)支援此工作流程。工作流程可讓您有效使用支援的Creative Cloud檔案。 因此，如果使用者A將一些資產放入InDesign檔案中並將其簽入[!DNL Experience Manager]，即使資產不屬於檔案，使用者B仍會在InDesign檔案中看見資產。 資產會在使用者B的電腦上本機下載。

>[!NOTE]
>
>案頭應用程式可以映射到Windows上的任何驅動器。 但是，為了順利操作，請勿更改預設驅動器號。 如果同一組織的使用者使用不同的驅動器號，則無法看見其他人放置的資產。 路徑變更時，不會擷取已放置的資產。 置入的資產會繼續放置在二進位檔案（例如INDD）中，且不會遭到移除。

要了解此工作流的限制，請參閱[系統要求和支援的版本](release-notes.md)。

若要使用影像資產和InDesign來嘗試此工作流程，請執行下列步驟：

1. 保存[!DNL Experience Manager]中放置資產的INDD檔案。 要了解如何建立這樣的INDD檔案，請參閱[放置圖形](https://helpx.adobe.com/indesign/using/placing-graphics.html)。
1. 從案頭應用程式內，**[!UICONTROL Edit]**&#x200B;內有放置資產的INDD檔案[!DNL Experience Manager]。
1. 應用程式會同時下載InDesign檔案和連結的資產。 InDesign開啟檔案時，會解析連結、下載資產，以及將資產顯示在InDesign檔案中。
1. 若要在InDesign檔案中放置新圖形，請對資產使用&#x200B;**[!UICONTROL Reveal File]**&#x200B;操作。 動作會在本機下載資產，並在Windows檔案總管或Mac Finder中開啟本機網路共用位置。
1. 將顯示的資產放入InDesign文檔中。 這會在文檔中建立連結。
1. 在InDesign文檔中完成編輯後，請保存該文檔，然後使用案頭應用程式將其上傳到[!DNL Experience Manager]。

## 進階工作流程：在本機下載資產 {#adv-workflow-download-assets-locally}

在許多情況下，應用程式會從檔案系統上的本機[!DNL Experience Manager]伺服器下載資產。 下載佔用頻寬和磁碟空間。 了解這些案例可協助您最佳化等待下載完成的時間。

您可隨選從應用程式內下載資產。 請參閱[下載資產](#download-assets)。

當您使用[!UICONTROL Open]動作在原生案頭應用程式中開啟資產時，如果資產尚未在本機可用，則會將資產下載到本機。 請參閱[開啟資產](#openondesktop-v2)。

當您從應用程式內顯示資產或資料夾的位置時，資產或資料夾會先在本機下載，然後在電腦上以本機網路共用開啟。 請參閱[開啟資產](#openondesktop-v2)。

當您使用[!UICONTROL Edit]動作來編輯原生案頭應用程式中的資產時，如果本機尚未提供資產，則會將資產下載至本機。 請參閱[編輯資產並將更新的資產上傳至 [!DNL Experience Manager]](#edit-assets-upload-updated-assets)。

如果已安裝應用程式且允許使用，則會在您從[!DNL Experience Manager]網頁介面使用[!UICONTROL Desktop Actions]時完成動作。 應用程式會先下載資產，然後完成動作。
