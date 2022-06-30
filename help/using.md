---
title: 使用 [!DNL Experience Manager] 案頭應用
description: 使用 [!DNL Adobe Experience Manager] 案頭應用，使用 [!DNL Adobe Experience Manager] DAM資產直接來自您的Win或Mac台式機，並用於其他應用程式。
mini-toc-levels: 1
feature: Desktop App,Asset Management
exl-id: fa19d819-231a-4a01-bfd2-6bba6fec2f18
source-git-commit: ca04b64e1ebfee4b677fcc5ef84b0e8fd9950d17
workflow-type: tm+mt
source-wordcount: '4054'
ht-degree: 0%

---

# 使用 [!DNL Adobe Experience Manager] 案頭應用 {#use-aem-desktop-app-v2}

使用 [!DNL Adobe Experience Manager] 案頭應用程式，可輕鬆訪問儲存在 [!DNL Adobe Experience Manager] 本地案頭上的DAM儲存庫，並將這些資產用於任何案頭應用程式。 您可以在案頭應用程式中開啟資產並在本地編輯資產 — 將更改上載回 [!DNL Experience Manager] 與版本控制項共用更新。 您還可以將新檔案和資料夾層次結構上載到 [!DNL Experience Manager]，建立資料夾，並從中刪除資產或資料夾 [!DNL Experience Manager] 水壩。

整合允許組織中的各種角色集中管理 [!DNL Experience Manager Assets] 以及訪問Windows或MacOS上本機應用程式中本地案頭上的資產。

在註銷後或首次開啟應用程式時，請提供 [!DNL Experience Manager] 格式 `https://[aem-server-url]:[port]/`。 然後選擇 [!UICONTROL Connect] 的雙曲餘切值。 提供憑據以將應用與伺服器連接。

使用 [!DNL Adobe Experience Manager] 案頭應用為：

![可以使用 [!DNL Experience Manager] 案頭應用](assets/aem_desktop_app_usecases_v2.png "可以使用 [!DNL Adobe Experience Manager] 案頭應用")
下載 [這個](assets/aem_desktop_app_usecases_print.pdf) 打印就緒PDF檔案。

## 案頭應用的工作原理 {#how-app-works2}

開始使用應用程式之前，請瞭解 [應用的工作原理](release-notes.md#how-app-works)。 另外，熟悉以下術語：

* **[!UICONTROL Desktop Actions]**:從「資產」Web介面，在瀏覽器中，您可以瀏覽資產位置或簽出並開啟資產，以便在本機案頭應用程式中進行編輯。 這些操作可從Web介面使用案頭應用功能。 請參閱 [如何啟用案頭操作](using.md#desktopactions-v2)。

* 檔案狀態為 **[!UICONTROL Cloud Only]**:此類資產不會下載到本地電腦上，可在 [!DNL Experience Manager] 僅伺服器。

* 檔案狀態為 **[!UICONTROL Available locally]**:這些資產將按原樣下載，並可在本地電腦上使用。 資產不會更改。

* 檔案狀態為 **[!UICONTROL Edited locally]**:此類資產在本地修改，並且更改仍保留到上載到 [!DNL Experience Manager] 伺服器。 上載後，狀態將更改為 [!UICONTROL Available locally]。 請參閱 [編輯資產](using.md#edit-assets-upload-updated-assets)。

* 檔案狀態為 **[!UICONTROL Editing conflict]**:如果您和其他用戶同時修改了資產，則應用會指示已發生編輯衝突。 應用還提供了保留或放棄更改的選項。 請參閱 [如何避免編輯衝突](using.md#adv-workflow-collaborate-avoid-conflicts)。

* 檔案狀態為 **[!UICONTROL Modified remotely]**:應用指示您下載的資產是否在 [!DNL Experience Manager] 伺服器。 該應用還提供下載最新版本和更新本地副本的選項。 請參閱 [如何避免編輯衝突](using.md#adv-workflow-collaborate-avoid-conflicts)。

* **[!UICONTROL Check-out]**:如果正在編輯檔案或要編輯檔案，則切換狀態以簽出。 它會在應用中的資產上添加一個鎖定表徵圖， [!DNL Experience Manager] Web介面。 鎖定表徵圖指示其他用戶避免同時編輯同一資產，因為這會導致編輯衝突。

* **[!UICONTROL Check-in]**:將資產標籤為安全，以便其他用戶編輯而不引起編輯衝突。 上載更改時，鎖表徵圖將自動刪除。 切換簽入狀態也會刪除鎖定表徵圖，儘管建議在不上載更改的情況下不手動簽入。 如果放棄更改，則手動切換簽入。

* **[!UICONTROL Open]** 操作：只需開啟資產，在本機應用程式中預覽它即可。 建議不要使用此操作來編輯資產，因為它不簽出資產，而其他用戶可以進行編輯而導致編輯衝突。

* **[!UICONTROL Edit]** 操作：使用操作修改影像。 按一下 [!UICONTROL Edit] 操作會自動簽出資產並在資產上添加鎖定表徵圖。 按一下「編輯」(Edit)後，如果不想編輯資產，則按一下 [!UICONTROL Toggle check-in]。 刪除、更名或移動資產 [!DNL Experience Manager] DAM資料夾層次結構，使用 [!DNL Experience Manager] web介面操作，而不是編輯操作。

* **[!UICONTROL Download]** 操作：將資產下載到本地電腦。 您可以立即下載這些資產，稍後進行編輯；離線工作，稍後上載更改。 資產將下載到檔案系統的快取資料夾中。

* **[!UICONTROL Reveal File]** 或 **[!UICONTROL Reveal Folder]** 操作：當資產下載到本地快取資料夾時，應用模擬本地網路驅動器並為每個資產提供本地路徑。 要瞭解此路徑，請在應用中使用相應的顯示選項。 在Creative Cloud應用程式中放置資產時，需要顯示操作。 請參閱 [放置資產](using.md#place-assets-in-native-documents)。

* **[!UICONTROL Open In Web]** 操作：要在中查看資產，請執行以下操作： [!DNL Experience Manager] Web介面，在Web中開啟。 您可以從 [!DNL Experience Manager] 介面，如更新元資料或資產發現。

* **[!UICONTROL Delete]** 操作：從 [!DNL Experience Manager] DAM儲存庫。 該操作將刪除Experience Manager伺服器上資產的原始副本。 如果只希望放棄對本地資產的修改，請參閱 [放棄更改](using.md#edit-assets-upload-updated-assets)。

* **[!UICONTROL Upload Changes]**:案頭應用僅在您顯式上載到 [!DNL Experience Manager] 伺服器。 保存編輯內容時，更改僅保存在本地電腦上。 上載時，資產將自動簽入並刪除鎖定表徵圖。 請參閱 [編輯資產](using.md#edit-assets-upload-updated-assets)。

## 在中啟用案頭操作 [!DNL Experience Manager] Web介面 {#desktopactions-v2}

從 [!DNL Assets] 用戶介面，您可以瀏覽資產位置或簽出並開啟資產以在案頭應用程式中進行編輯。 這些選項被調用 [!UICONTROL Desktop Actions] 預設情況下未啟用。 要啟用它，請執行以下步驟。

1. 在 [!DNL Assets] 控制台，按一下 **[!UICONTROL User]** 的子菜單。
1. 按一下 **[!UICONTROL My Preferences]** 顯示 **[!UICONTROL Preferences]** 對話框。

1. 在 [!UICONTROL User Preferences] 對話框，選擇 **[!UICONTROL Show Desktop Actions For Assets]**，然後按一下 **[!UICONTROL Accept]**。


   ![選擇「顯示資產的案頭操作」以啟用案頭操作](assets/enable_desktop_actions.png)

   *圖：選擇 [!UICONTROL Show Desktop Actions For Assets] 啟用案頭操作。*

## 瀏覽、搜索和預覽資產 {#browse-search-preview-assets}

您可以瀏覽、搜索和預覽 [!DNL Experience Manager] 儲存庫，全部來自案頭應用程式。 請在應用中嘗試以下操作：

1. 瀏覽到資料夾，查看資料夾中可用資產的一些基本資訊以及所有資產的小縮略圖。

   ![瀏覽DAM檔案和資料夾](assets/browse_folder_da2.png "瀏覽DAM檔案和資料夾")

1. 要查看詳細資訊和單個資產的較大縮略圖，請按一下檔案名。

   ![查看資產和操作的更大預覽](assets/large_preview_actions_da2.png "查看資產和操作的更大預覽")

1. 按一下 **[!UICONTROL Open]** 或 **[!UICONTROL Edit]** 以本地下載檔案，並分別查看該檔案或在本機應用程式中編輯該檔案。
1. 使用關鍵字搜索以在 [!DNL Experience Manager] 儲存庫。 使用 `?` 和 `*` 作為通配符。 這些通配符分別用於單個字元或多個字元。 根據需要篩選和排序結果。

   ![使用星號通配符的示例搜索](assets/search_wildcard_da2.png "使用星號通配符的示例搜索")

   ![使用星號通配符的另一個示例搜索](assets/search_wildcard2_da2.png "使用星號通配符的不同位置的另一個示例搜索")

>[!NOTE]
>
>應用通過在多個元資料欄位中匹配搜索條件來顯示資產，而不只是資產的標題或檔案名。

## 下載資產 {#download-assets}

您可以下載本地檔案系統上的資產。 應用從中提取資產 [!DNL Experience Manager] 並將同一副本保存到本地檔案系統。

按一下 ![「更多選項」表徵圖](assets/do-not-localize/more2_da2.png) ，按一下 ![下載表徵圖](assets/do-not-localize/download_cloud_da2.png) 下載。

![資產的下載選項](assets/download_option_da2.png "資產的下載選項")

>[!NOTE]
>
>下載或上載大檔案或許多檔案時，應用程式會關閉對資產和資料夾的操作。 當下載或上載完成時，這些操作可用。

如果隊列大小較大或您遇到某些網路問題，下載多個資產可能會導致效能下降。 此外，在下載資料夾時，您可能無意中將許多資產排入下載隊列。 為避免等待時間過長，該應用會限制一次下載的資產數量。 要瞭解如何配置，請參見 [設定首選項](install-upgrade.md#set-preferences)。 即使低於此限制，該應用在下載明顯較大的資料夾之前，有時也會尋求確認。

![應用確認下載相對大量的資產](assets/download_confirmation_da2.png "應用確認下載相對大量的資產")

如果選擇並下載了資料夾，則應用程式只下載直接儲存在資料夾中的資產 [!DNL Experience Manager]。 它不會自動從子資料夾中下載資產。

## 在案頭上開啟資產 {#openondesktop-v2}

您可以開啟遠程資產以在本機應用程式中查看。 這些資產被下載到本地資料夾並在與檔案格式相關聯的本機應用程式中啟動。 您可以更改本機應用程式以在Mac或Windows中開啟特定檔案類型（副檔名）。

按一下 **[!UICONTROL Open]** 的子菜單。 資產在本地下載，並在本地應用程式中開啟。 在狀態欄中檢查大型資產的下載進度和傳輸速度。

<!-- ![Download progress bar for large-sized assets](assets/download_status_bar_da2.png "Download progress bar for large-sized assets")
-->

>[!NOTE]
>
>如果應用程式中未反映預期更改，請按一下「刷新」表徵圖 ![「刷新」表徵圖](assets/do-not-localize/refresh.png) 或在應用介面中按一下右鍵，然後按一下 **[!UICONTROL Refresh]**。 當正在進行較大的下載或上載時，這些操作不可用。

要開啟資產的本地下載資料夾，請按一下 ![「更多操作」表徵圖](assets/do-not-localize/more2_da2.png) 按一下 ![顯示表徵圖](assets/do-not-localize/reveal_action2_da2.png) **[!UICONTROL Reveal File]** 操作。

## 使用資產或將資產放入本機文檔 {#place-assets-in-native-documents}

在某些情況下，例如，在將資產放入本機文檔時，您可以訪問Windows資源管理器或Mac查找器中的檔案。 要獲取本地下載檔案的檔案系統位置，請使用 ![顯示表徵圖](assets/do-not-localize/reveal_action2_da2.png) **[!UICONTROL Reveal File]** 的雙曲餘切值。

![顯示資產的檔案操作](assets/revealfile_action_da2.png "顯示資產的檔案操作")

按一下 **[!UICONTROL Reveal File]**&#x200B;或 **[!UICONTROL Reveal Folder]** 在資料夾上開啟Windows資源管理器或Mac查找器，並在本地電腦上預先選定檔案或資料夾。 這個選項對於 [!DNL Experience Manager] 本地應用程式中支援放置或連結本地檔案的檔案。 要查看如何在Adobe InDesign放置檔案，請參閱 [放置圖形](https://helpx.adobe.com/indesign/using/placing-graphics.html)。

的 **[!UICONTROL Reveal File]** 操作會開啟本地網路共用，該共用僅顯示本地可用的資產 — 即顯示使用應用程式顯示、下載或開啟/編輯的資產。 本地網路共用未上載任何更改 [!DNL Experience Manager]。 要上載更改，請明確使用 **[!UICONTROL Upload Changes]** 或 **[!UICONTROL Upload]** 操作。

>[!NOTE]
>
>為了向後相容 [!DNL Experience Manager] 案頭應用v1.x，顯示的檔案從本地網路共用中提供，僅公開本地可用檔案。 顯示檔案的案頭路徑與app v1.x建立的路徑相同。

>[!CAUTION]
>
>不使用 **[!UICONTROL Reveal File]** 選項以編輯本機應用程式中的資產。 而是使用 **[!UICONTROL Edit]** 操作。 要瞭解更多資訊，請參閱 [高級工作流：協作同一檔案，避免編輯衝突](#adv-workflow-collaborate-avoid-conflicts)。

## 編輯資產並將更新的資產上載到 [!DNL Experience Manager] {#edit-assets-upload-updated-assets}

開啟資產，以便在您要進行更改並將更新的資產上載到AExperience ManagerEM伺服器時進行編輯。 為避免與其他用戶的編輯衝突，請使用應用啟動編輯會話。 開始編輯之前，請確保資產上沒有鎖定表徵圖，即其他用戶未編輯資產。

要編輯資產，請搜索資產或瀏覽到資產的位置。 按一下 ![「更多」表徵圖](assets/do-not-localize/more2_da2.png) 按一下 **[!UICONTROL Edit]**。

使用 **[!UICONTROL Toggle Check-out]** 在以下兩種情況下鎖定資產以防止與其他用戶的編輯衝突：

* 您已開始編輯資產，但未先將其簽出（例如，只開啟它）。
* 您打算很快開始編輯資產，但不希望其他人編輯。

完成編輯後，應用將顯示 **[!UICONTROL Edited Locally]** 更改的資產的狀態。 保存到資產的所有更改都僅在本地，直到您將更改上載到 [!DNL Experience Manager]。 要逐個上載單個或幾個資產，請按一下 **[!UICONTROL Upload Changes]** 的下界。 它將在中建立資產的版本 [!DNL Experience Manager]。 使用的Web介面 [!DNL Assets]，您可以在 [時間軸視圖](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/activity-stream.html)。

![在應用中上載更改選項](assets/upload_changes_single1_da2.png "在應用中上載更改選項")

![查看資產的大型預覽時上載更改選項](assets/upload_changes_single2_da2.png "查看資產的大型預覽時上載更改選項")

有關協作編輯的最佳做法，請參見 [高級工作流：協作同一檔案，避免編輯衝突](#adv-workflow-collaborate-avoid-conflicts)。

在以下情況下，您可能希望放棄對本地資產的更改和編輯。 按一下 **[!UICONTROL Discard Changes]**.

* 如果您不想將本地更改保存到 [!DNL Experience Manager]。
* 保存一些更改後，開始對原始資產進行更改。
* 停止編輯資產，因為不再需要它。

如有必要，請切換簽出。 更新的資產將從本地快取資料夾中刪除，並在您編輯或開啟它時再次下載。

## 將新資產上載和添加到 [!DNL Experience Manager] {#upload-and-add-new-assets-to-aem}

用戶可以向DAM儲存庫添加新資產。 例如，您可能是代理攝影師或承包商，希望將照片中的大量照片添加到 [!DNL Experience Manager] 儲存庫。 向添加新內容 [!DNL Experience Manager]選中 ![上載到雲選項](assets/do-not-localize/upload_to_cloud_da2.png) 在應用程式的頂欄。 瀏覽到本地檔案系統中的資產檔案，然後按一下 **[!UICONTROL Select]**。 或者，要上載資產，請拖動應用程式介面上的檔案或資料夾。 在Windows上，如果將資產拖動到應用程式內的資料夾上，則這些資產將上載到資料夾中。 如果上載需要較長時間，則應用將顯示進度欄。

<!-- ![Download progress bar for large-sized assets](assets/upload_status_da2.png "Download progress bar for large-sized assets")
-->

可以從本地檔案系統上載資料夾或單個檔案。 資料夾的層次結構在上載時保留。 批量上載資產之前，請參見 [批量上載](#bulk-upload-assets)。

要查看給定會話中轉移的資產清單，請按一下 **[!UICONTROL View]** > **[!UICONTROL Assets transfers]**。 該清單允許您查看並快速驗證當前會話的檔案傳輸。

![特定會話中轉移的資產清單](assets/assets_transfered_da2.png "特定會話中轉移的資產清單")

您可以在 **[!UICONTROL Preferences]** > **[!UICONTROL Upload acceleration]** 的子菜單。 更多併發通常會提供更快的上載，但可能會佔用大量資源，消耗本地電腦的更多處理能力。 如果系統運行緩慢，請使用較低的併發值重新嘗試上載。

>[!NOTE]
>
>傳輸清單不是永久的，如果退出應用並重新開啟，則該清單不可用。

### 管理資產名稱中的特殊字元 {#special-characters-in-filename}

在舊版應用中，儲存庫中建立的節點名稱保留了用戶提供的資料夾名稱的空格和大寫。 如果當前應用程式要模擬v1.10應用程式的節點命名規則，請啟用 [!UICONTROL Use legacy conventions when creating nodes for assets and folders] 的 [!UICONTROL Preferences]。 請參閱 [應用首選項](/help/install-upgrade.md#set-preferences)。 預設情況下，此舊首選項處於禁用狀態。

>[!NOTE]
>
>應用僅使用以下命名約定更改儲存庫中的節點名稱。 應用將保留 `Title` 按原樣計算。

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

| 字元數 ‡ | 應用中的舊首選項 | 在檔案名中出現時 | 在資料夾名稱中發生時 | 範例 |
|---|---|---|---|---|
| `. / : [ ] | *` | 已啟用或已禁用 | 替換為 `-` （連字元）。 A `.` 檔案名副檔名中的（點）保持原樣。 | 替換為 `-` （連字元）。 | `myimage.jpg` 保持原樣 `my.image.jpg` 更改 `my-image.jpg`。 |
| `% ; # , + ? ^ { } "` 和空格 | ![取消選擇表徵圖](assets/do-not-localize/deselect-icon.png) 已禁用 | 保留空格 | 替換為 `-` （連字元）。 | `My Folder.` 更改 `my-folder-`。 |
| `# % { } ? & .` | ![取消選擇表徵圖](assets/do-not-localize/deselect-icon.png) 已禁用 | 替換為 `-` （連字元）。 | 不適用. | `#My New File.` 更改 `-My New File-`。 |
| 大寫字元 | ![取消選擇表徵圖](assets/do-not-localize/deselect-icon.png) 已禁用 | 外殼保持原樣。 | 已更改為小寫字元。 | `My New Folder` 更改 `my-new-folder`。 |
| 大寫字元 | ![選中的選項](assets/do-not-localize/selection-checked-icon.png) 已啟用 | 外殼保持原樣。 | 外殼保持原樣。 | 不適用. |

？字元清單是以空格分隔的清單。

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

用戶可以使用操作輕鬆處理和管理多個資產，例如一次上載所有編輯內容或按一下幾下即可上載嵌套資料夾。

### 瀏覽大型資料夾 {#browse-large-folders}

使用包含許多資產的資料夾時，滾動以查看更多資產。 要使用鍵盤滾動，請按Tab鍵幾次以選擇頂部的資產。 注意突出顯示的資產，以瞭解它何時被選中。 現在，使用&lt;下箭頭>鍵在資產清單中移動。

### 選定資產的快速操作 {#quick-actions-for-selected-assets}

按一下幾個資產的縮略圖以選擇資產。 要選擇所有資產，請按一下應用頂欄中的複選框。 適用於所有選定資產的一組操作集合顯示在應用程式底部的工具欄中。

![底部的工具欄顯示與選定資產相關的操作](assets/actions_bottom_toolbar1_da2.png "底部的工具欄顯示選定資產的常用操作")

![沒有所選內容的常用操作時，工具欄中沒有操作](assets/actions_bottom_toolbar2_da2.png "沒有所選內容的常用操作時，工具欄中沒有操作")

底部工具欄中可用的操作取決於選定檔案的狀態。 例如，如果僅選擇 **[!UICONTROL Edited Locally]** 檔案，您看到 **[!UICONTROL Upload Changes]** 表徵圖 如果選擇 **[!UICONTROL Edited locally]** 和 **[!UICONTROL Cloud only]**，也請參見Wiki頁。 **[!UICONTROL Upload Changes]** 操作不可用。

### 查找所有已編輯的影像 {#find-all-edited-images}

應用程式提供一個視圖，稱為 **[!UICONTROL Edited locally]**，以便您快速訪問本地下載的所有檔案(通過 [!UICONTROL Open] 或 [!UICONTROL Edit] 操作)，然後修改。 該應用允許您選擇所有本地編輯的資產，並在幾次按一下後上載更改。 此視圖還顯示具有編輯衝突的本地編輯資產。

![篩選以查看所有本地編輯的資產](assets/edited_locally_filter_da2.png "篩選以查看所有本地編輯的資產，例如批量上載編輯內容")

### 批量上載資產 {#bulk-upload-assets}

用戶或組織，如攝影師或創意機構，可以在場景中建立大量本地資產，如照片、修飾或從外部完成的較大集合中選擇 [!DNL Experience Manager]。 他們可以將這些大型本地資料夾上載到 [!DNL Assets] 直接從案頭應用中。 資料夾層次被保留，並上載所有嵌套的子資料夾和包含的資產。 上載的資產也可立即供同一伺服器的其他用戶使用。 資產在後台上載，因此該操作不會與Web瀏覽器會話關聯。

![將多個本地資料夾從案頭批量上載到 [!DNL Experience Manager]](assets/upload_local_folders_da2.png "將多個本地資料夾從案頭批量上載到Experience Manager")

上載後，如果應用程式中未反映預期的更改，請按一下刷新表徵圖 ![「刷新」表徵圖](assets/do-not-localize/refresh.png)。

>[!NOTE]
>
>不使用上載功能跨兩個位置遷移資產 [!DNL Experience Manager] 部署。 相反，請參閱 [遷移指南](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/assets-migration-guide.html)。

### 已轉讓資產清單 {#list-of-transferred-assets}

要查看給定會話中轉移的資產清單，請參閱 [將資產上載到 [!DNL Experience Manager]](#upload-and-add-new-assets-to-aem)。

## 高級工作流：從 [!DNL Assets] Web介面 {#adv-workflow-start-from-aem-ui}

如有必要，請從「資產」Web介面啟動您的工作流。 案頭應用與 [!DNL Experience Manager] 以在請求時使用「案頭操作」進行接管。

從Web介面啟動工作流的一個特殊情況是資產發現。 Assets中的Omnisearch欄用戶介面提供豐富而高級的搜索體驗。 您可能希望首先在Web上查找所需資產，然後在應用中啟動工作流， [!UICONTROL Desktop Actions]。 一些示例案例包括使用facet篩選搜索結果、查找從Adobe Stock獲得許可的特定資產，或您的組織實施的允許您從Web介面更好地發現的自定義。

當您嘗試在Assets Web介面上執行以下操作時，將使用案頭應用功能：

* 的 [!UICONTROL Desktop Actions] 允許 [!UICONTROL Open]。 [!UICONTROL Edit], [!UICONTROL Reveal]
* [!UICONTROL Upload folder]
* [!UICONTROL Check-out] 或 [!UICONTROL check-in]

例如，在Web介面上可用於在應用中籤出的資產的操作是 [!UICONTROL Open]。 [!UICONTROL Reveal], [!UICONTROL Check-in]。

![中的案頭操作 [!DNL Experience Manager] Web介面](assets/assets_web_actions_da2.png "Experience ManagerWeb介面中的案頭操作")

>[!NOTE]
>
>瀏覽器可能會提示您允許啟動 [!DNL Adobe Experience Manager] 台式機。 要享受從瀏覽器到應用程式的不間斷傳輸，請選中相應的複選框以始終允許應用程式接管。

您無法使用Web介面找到以下資訊或工作流。 使用案頭應用，因為Web介面不跟蹤本地更改，並且不知道以下內容：

* 本地編輯的檔案。
* 存在編輯衝突的檔案及其解決方法。
* 將本地更改上載到 [!DNL Experience Manager]。
* 本地可用檔案的各種狀態。

相反，您可以從案頭應用程式開始使用 **[!UICONTROL Open In Web]** 操作。

## 高級工作流：協作同一檔案，避免編輯衝突 {#adv-workflow-collaborate-avoid-conflicts}

在協作環境中，多個用戶可能使用同一組資產，這可能導致版本控制衝突。 要防止衝突，請遵循以下最佳做法：

* 不要通過按一下 [!UICONTROL Open]。 不要通過從檔案系統資料夾開啟來編輯本地下載的資產。 其他用戶不知道正在編輯資產。
* 要編輯資產，請始終按一下 [!UICONTROL Edit]。 它將在本機應用程式中開啟該資產，並在該資產上添加一個鎖定表徵圖，以便其他用戶知道正在編輯該資產。
* 按一下 [!UICONTROL Toggle Check-in] 如果無意中開始編輯，則 [!UICONTROL Edit]。 這將向資產添加鎖定表徵圖。 即使您計畫稍後編輯資產，但希望避免其他人編輯它，請按一下 [!UICONTROL Toggle Check-in] 鎖定資產。
* 編輯資產之前，請確保其他用戶未編輯該資產。 查找資產上的鎖定表徵圖。
* 完成編輯後，上載所有更改，然後簽入資產。

![編輯衝突的狀態](assets/edits_conflicts_status_da2.png "編輯衝突的狀態")

如果本地下載的資產在 [!DNL Experience Manager] 伺服器，應用顯示 **[!UICONTROL Modified remotely]** 狀態。 通過按一下，您可以刪除本地副本或刷新本地副本 [!UICONTROL Remove] 或 [!UICONTROL Update] 分別進行。 對話框上的連結允許您查看資產的兩個版本。

![遠程修改資產時解決衝突的選項](assets/modified_remotely_dialog_da2.png "遠程修改資產時解決衝突的選項")

如果您正在本地編輯的資產也在伺服器上更新，而您不知情，則應用將顯示 **[!UICONTROL Editing Conflict]** 狀態。 您可以保留一組更改 — 或者保留更新(按一下 **[!UICONTROL Keep Mine]**)並刪除其他用戶的編輯或尊重其他用戶的更新，並刪除您的(**[!UICONTROL Overwrite Mine]**)。

![解決編輯衝突的選項](assets/editing_conflict_dialog_da2.png "解決編輯衝突的選項")

## 高級工作流：放置和連結資產到InDesign檔案中 {#adv-workflow-place-assets-indesign}

使用 [!DNL Experience Manager] 案頭應用程式開啟具有連結資產的檔案，這些資產將預下載並顯示在本機應用程式中。 要使此工作流正常工作，您的本地應用程式必須支援將連結放置到本地資產和 [!DNL Experience Manager] 必須支援將二進位檔案中的這些連結解析為伺服器端引用。

[!DNL Experience Manager] 案頭應用支援此工作流，只有幾種選擇的Adobe Creative Cloud案頭應用程式和檔案格式 — Adobe InDesign、Adobe Illustrator和Adobe Photoshop。 該工作流允許您有效地處理受支援的Creative Cloud檔案。 因此，如果用戶A將一些資產放入InDesign檔案中並將其簽入 [!DNL Experience Manager]，用戶B在InDesign檔案中看到資產，即使這些資產不是檔案的一部分。 在用戶B的機器上本地下載資產。

>[!NOTE]
>
>案頭應用可以映射到Windows上的任何驅動器。 但是，對於平滑操作，不要更改預設驅動器號。 如果同一組織的用戶使用不同的驅動器號，則他們無法看到其他用戶放置的資產。 路徑更改時不會讀取已放置的資產。 已放置的資產繼續放置在二進位檔案（如INDD）中，並且不會被刪除。

要瞭解此工作流的限制，請參閱 [系統要求和支援的版本](release-notes.md)。

要使用影像資產和InDesign嘗試此工作流，請執行以下步驟：

1. 使用已放置資產的INDD檔案 [!DNL Experience Manager]。 要瞭解如何建立此類INDD檔案，請參見 [放置圖形](https://helpx.adobe.com/indesign/using/placing-graphics.html)。
1. 在案頭應用中， **[!UICONTROL Edit]** 放置資產的INDD檔案 [!DNL Experience Manager]。
1. 該應用同時下載InDesign檔案和連結資產。 當InDesign開啟文檔時，連結將被解析，資產將被下載，資產將顯示在InDesign文檔中。
1. 要在InDesign檔案中放置新圖形，請使用 **[!UICONTROL Reveal File]** 操作。 此操作將本地下載資產並在Windows資源管理器或Mac查找器中開啟本地網路共用位置。
1. 將顯示的資產放在InDesign文檔中。 這將在文檔中建立連結。
1. 在InDesign文檔中完成編輯後，將其保存並上載到 [!DNL Experience Manager] 使用案頭應用。

## 高級工作流：本地下載資產 {#adv-workflow-download-assets-locally}

應用從 [!DNL Experience Manager] 在許多情況下，在檔案系統上本地安裝伺服器。 下載佔用頻寬和磁碟空間。 瞭解這些方案有助於優化下載完成的等待時間。

您可以按需從應用程式內下載資產。 請參閱 [下載資產](#download-assets)。

使用 [!UICONTROL Open] 操作以在本機案頭應用程式中開啟資產，如果本地尚不可用，則本地下載該資產。 請參閱 [未結資產](#openondesktop-v2)。

當您從應用程式中顯示資產或資料夾的位置時，資產或資料夾首先在本地下載，然後在本地網路共用中在您的電腦上開啟。 請參閱 [未結資產](#openondesktop-v2)。

使用 [!UICONTROL Edit] 操作以編輯本地案頭應用程式中的資產，如果本地尚不可用，則本地下載該資產。 請參閱 [編輯資產並將更新的資產上載到 [!DNL Experience Manager]](#edit-assets-upload-updated-assets)。

如果已安裝並允許使用該應用，則當您使用 [!UICONTROL Desktop Actions] 從 [!DNL Experience Manager] Web介面。 應用先下載資產，然後完成操作。
