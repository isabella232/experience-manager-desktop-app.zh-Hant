---
title: 使用 [!DNL Experience Manager] 案頭應用程式1.10版。
description: 了解如何使用Adobe Experience Manager案頭應用程式1.10版，並透過案頭上的資產最佳化您的工作。
feature: 案頭應用程式，資產管理
exl-id: 2fdc1c8d-b822-4cca-ad06-bd875a00aa6d
source-git-commit: dcd29d0bbb32004d970d334c256e659f4a4c39e1
workflow-type: tm+mt
source-wordcount: '2371'
ht-degree: 0%

---

# 使用[!DNL Experience Manager]案頭應用程式v1.10 {#use-aem-desktop-app-v1x}

使用應用程式時，您可輕鬆在本機案頭上存取[!DNL Experience Manager]中的資產，並可用於任何案頭應用程式。 資產可在Mac Finder或Windows Explorer中輕鬆顯示、在案頭應用程式中開啟，並在本機變更 — 變更會透過在存放庫中建立的新版本，儲存回[!DNL Experience Manager]。

這種整合使組織中的各種角色能夠集中管理資產中的資產，並在Creative Cloud和其他應用程式中訪問這些資產，同時使之易於遵守包括品牌在內的各種標準。

使用[!DNL Experience Manager]案頭應用程式v1時的主要工作包括：

1. [連接 [!DNL Experience Manager] 伺服器](#installandconnect)
1. [直接在案頭上開啟資產](#openondesktop)
1. [從案頭編輯和簽出資產](#workonassets)
1. [大量上傳資產和資料夾](#bulkupload)

如需各種建議的dos和don&#39;t，請參閱使用app](best-practices-for-v1.md)的[最佳實務。 如果您在使用應用程式時遇到問題，請參閱如何[疑難排解 [!DNL Experience Manager] desktop](troubleshoot-app-v1.md)。

>[!NOTE]
>
>案頭應用程式於[!DNL Experience Manager] 6.1版本中推出，稱為[!DNL Experience Manager Assets Companion App]。

## [!DNL Experience Manager] 創意工作流程中的案頭應用程式接觸點 {#aem-desktop-app-touch-points-in-the-creative-workflow}

[!DNL Experience Manager] 案頭應用程式與 [!DNL Assets]整合至您的創意工作流程，並提供下列接觸點。

![[!DNL Experience Manager] 案頭應用程式接觸點：創意工作流程](assets/aem_desktopapp_workflow.png)

[!DNL Experience Manager] 案頭應用程式接觸點：創意工作流程

## 安裝應用程式並將其連接到[!DNL Experience Manager]伺服器 {#installandconnect}

開始建立或編輯創意資產之前，請先將案頭應用程式與[!DNL Assets]伺服器連線，以下載和上傳存放庫中的資產。 執行下列工作：

1. [安裝應用程式](#installapp)。
1. [設定您的偏好](#inapppref) 設定和連線詳細資訊。
1. [連線至anserver [!DNL Experience Manager] ](#connect) 並將資產存放庫以本機磁碟形式安裝。
1. [啟用案頭](#desktopactions) 操作 [!DNL Experience Manager] 伺服器。

[!DNL Experience Manager] 案頭應用程式使用HTTPS連線連線來連線至 [!DNL Experience Manager] 伺服器，以穩健安全地傳輸您的資產。

>[!NOTE]
>
>對於部分或所有安裝和配置步驟，您可能需要[!DNL Experience Manager]管理員或系統管理員的幫助。

### 安裝應用程式 {#installapp}

若要使用[!DNL Experience Manager]案頭應用程式，請確定應用程式支援您的[!DNL Experience Manager]伺服器版本。 下載適合您作業系統（Mac或Windows）的安裝檔案（二進位），然後安裝應用程式。

根據您的網路和系統首選項，可能需要詳細配置。 如需詳細資訊，請參閱[安裝並設定 [!DNL Experience Manager] 案頭應用程式](install-configure-app-v1.md) 。

1. 前往[[!DNL Experience Manager] 案頭應用程式v1.10下載頁面](/help/release-notes-of-v1.md)並下載適合您作業系統的二進位檔。
1. 啟動下載的安裝檔案，並依照螢幕上的指示安裝應用程式。

   >[!NOTE]
   >
   >一次只能安裝[!DNL Experience Manager]案頭應用程式的一個實例並處於活動狀態。

### 了解應用程式內選項和偏好設定 {#inapppref}

應用程式允許設定與[!DNL Experience Manager]伺服器連接和斷開連接、查看上載狀態、管理本地快取等。 預設設定適用於應用程式的一般使用者。 您可以調整設定，以從應用程式和退出與[!DNL Experience Manager]伺服器的整合中獲得更多資訊。 下方會詳細說明各種設定。

**探索** 資產開啟載入存放庫的本 [!DNL Assets] 機磁碟。換句話說，探索現在可在本機電腦上使用的資產。

**檢視資** 產狀態上傳已變更的資產或將新資產新增至 [!DNL Assets] 存放庫時，應用程式會在背景上傳資產。背景上傳可讓您順利執行操作，而無須等待上傳完成，尤其是大型資產。 您可以將變更儲存在本機，並加以忽略。 應用程式需要一些時間將這些資產傳送至伺服器，具體取決於可用頻寬。 您可以檢查上傳的狀態，以及一些更基本的資訊。

**** 選項按一下案頭應用程式托盤中的選項，以在系統啟動時訪問啟動應用程式的設定；在應用程式 [!DNL Experience Manager] 啟動時連線至伺服器；並更改安裝後可用的本 [!DNL Assets] 地驅動器號。

**高級>管** 理快取您可以控制可用於本地快取的磁碟空間量。在本地快取[!DNL Assets]伺服器中的工件，以獲得更流暢的體驗。 您可以變更預設值以符合您的需求。 此外，您也可以清除快取，以重新擷取所有資產。 清除快取時，會保留未儲存的變更。 未簽入[!DNL Experience Manager]伺服器的任何資產都將保留，且不會刪除。

### 連接到[!DNL Experience Manager]伺服器 {#connect}

應用程式支援Mac和Windows上的代理設定。 應用程式啟動時會讀取設定。 如果您修改代理設定，請重新啟動應用程式，讓變更生效。

>[!NOTE]
>
>如果您修改代理設定，請重新啟動應用程式，讓變更生效。 否則，應用程式會繼續使用先前設定的代理伺服器。

1. 啟動[!DNL Experience Manager]案頭應用程式。 若要將您的[!DNL Experience Manager]例項對應至應用程式，請以`https://[aem-server-url]:[port]`格式指定您的[!DNL Experience Manager]伺服器。

   ![在Mac上驗證並提供伺 [!DNL Experience Manager] 服器URL](assets/aem_desktop_app_server_url.png)

1. 在登入畫面中，指定執行個體的使用者名稱和密碼。 要指定替代的[!DNL Experience Manager]實例，請選擇&#x200B;**[!UICONTROL Alternate Login URL]**&#x200B;選項。

   ![在案 [!DNL Experience Manager] 頭應用程式的登入畫面上提供伺 [!DNL Experience Manager] 服器憑證](assets/login_screen_v1.png)

### 在[!DNL Experience Manager] Web介面中啟用案頭操作 {#desktopactions}

從「資產」使用者介面，您可以探索資產位置或結帳並開啟資產，以便在案頭應用程式中進行編輯。 這些選項稱為案頭操作，預設情況下不啟用。 請依照下列步驟來啟用。

1. 在「資產」介面，按一下/點選工具列右上角的「使用者」圖示。
1. 按一下&#x200B;**[!UICONTROL My Preferences]**&#x200B;以顯示&#x200B;**[!UICONTROL Preferences]**&#x200B;對話方塊。

   ![[!DNL Experience Manager] 用戶首選項介面](assets/aem_ui_user_preferences.png)

1. 在[!UICONTROL User Preferences]對話方塊中，選取&#x200B;**[!UICONTROL Show Desktop Actions For Assets]**，然後按一下&#x200B;**[!UICONTROL Accept]**。

   ![檢查 [!UICONTROL Show Desktop Actions For Assets] 以啟用案頭操作](assets/enable_desktop_actions.png)

   *圖：核取 [!UICONTROL Show Desktop Actions For Assets] 以啟用案頭動作。*

## 在案頭上存取和開啟資產 {#openondesktop}

當您按一下&#x200B;**開啟**&#x200B;以在本機電腦上開啟資產時，應用程式會將資產下載至其內部快取。 應用程式會啟動與下載資產的檔案類型相關聯的原生案頭應用程式。

在Mac上，從內容功能表選取&#x200B;**開啟**，以透過[!DNL Experience Manager]案頭應用程式開啟資產。 在Windows上，從內容功能表選取「在網頁上開啟」以開啟資產。 在「資產狀態」視窗中，按一下/點選「在案頭上開啟」圖示](assets/do-not-localize/aemassets_icon_openondesktop.png)以開啟資產。![

若為Adobe InDesign(INDD)檔案，請從上下文菜單中選擇&#x200B;**[!UICONTROL Open]**。 按一下此選項時，應用程式會將連結的資產下載至您的本機檔案系統，然後在Adobe InDesign中開啟INDD檔案。 此方法可確保在編輯INDD檔案時，必要的資產可在本機使用。

![使用案頭應用程式存取和開啟資產的內容功能 [!DNL Experience Manager] 表選項](assets/aem_desktopapp_mac_context_menu.png)

*圖：使用案頭應用程式存取及開啟資產的內容功能 [!DNL Experience Manager] 表選項。*

>[!NOTE]
>
>在Windows上， [預設的Windows 7設定](https://support.microsoft.com/en-us/kb/2668751)會防止[!DNL Experience Manager]案頭應用程式處理大於50 MB的資產。

<!-- TBD: The above note is for Windows 7 which is not supported by the app anymore. Remove it later.
-->

>[!NOTE]
>
>Adobe建議您前往Mac上的「尋找器檢視選項」，並停用已裝入[!DNL Assets]資料夾的選項&#x200B;**顯示項目資訊**、**顯示項目預覽**&#x200B;和&#x200B;**顯示預覽欄**。 它提高了效能。

### [!DNL Experience Manager]介面中的其他選項 {#additional-options-in-aem-assets}

將[!DNL Assets]存放庫對應至本機磁碟後，您可以啟用其他圖示，並啟用「資料夾上傳」功能，以針對對應的資產和資料夾顯示。

1. 開啟[!DNL Assets]介面，將指標移至資料夾或資產上，以在「卡片」檢視中將案頭動作顯示為快速動作。

   ![在Assets UI中，開啟快速動作功能表以查看案頭動作](assets/desktop_actions_in_card_view.png)

   *圖：在「資產」UI中，開啟快速動作功能表以查看案頭動作。*

   在選取資產後或從資產頁面的工具列按一下工具列中的&#x200B;**案頭動作**&#x200B;選項時，也可使用這些案頭動作。

1. 若要在與特定檔案副檔名相關聯的案頭應用程式中開啟資產，請按一下&#x200B;**在案頭上開啟**&#x200B;快速操作![在案頭上開啟表徵圖](assets/do-not-localize/aemassets_icon_openondesktop.png)。

   或者，從工具欄的&#x200B;**案頭操作**&#x200B;菜單中選擇&#x200B;**開啟**。

若要在您的本機檔案系統上找出特定資產，請按一下「**Reveal**&#x200B;快速動作![Reveal圖示](assets/do-not-localize/aemassets_reveal_icon.png)」。 或者，從工具欄的&#x200B;**案頭操作**&#x200B;菜單中選擇&#x200B;**顯示**。

## 了解資產狀態 {#understand-the-asset-statuses}

| ![Windows預設應用表徵圖](assets/do-not-localize/win_default.png) | 應用程式已連線至伺服器，且所有資產皆已同步。 |
--- |--- |
| ![Windows禁用表徵圖](assets/do-not-localize/win_disabled.png) | 應用程式已啟動，但未與伺服器連線。 某些資產可能正在等待同步。 |
| ![Windows檔案同步表徵圖](assets/do-not-localize/win_sync.png) | 資產正在同步。 正在上載或下載檔案。 您可以在「資產狀態」窗口中查看確切狀態並暫停轉移。 |
| ![Windows重新連接表徵圖](assets/do-not-localize/win_refresh.png) | 應用正在嘗試重新連接。 網路問題可能導致其斷開連接。 |

## 使用您的資產 {#workonassets}

### 從[!DNL Experience Manager]網頁介面查看資產 {#check-out-assets-from-the-aem-web-interface}

[!DNL Assets] 可讓您簽出要編輯的資產，並在完成變更後重新簽入。結帳資產後，只有您可以編輯、注釋、發佈、移動或刪除資產。 簽出資產會鎖定資產，並防止其他使用者執行任何這些操作。 若要簽出/登入資產，您需要這些資產的寫入存取權。

從[!DNL Experience Manager] Web介面簽出資產有兩種方式。 如需第一個方法的詳細資訊，請參閱從Assets UI](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/check-out-and-submit-assets.html)簽入和簽出檔案。 [請依照下列步驟操作，了解安裝[!DNL Experience Manager]案頭應用程式時，要簽出並開啟資產的第二個方法。

1. 開啟[!DNL Assets]介面，將指標移至資料夾或資產上，以在「卡片」檢視中將案頭動作顯示為快速動作。

   ![卡片檢視中的「屬性」選項](assets/desktop_actions_in_card_view.png)

   在選取資產後，或從資產頁面的工具列按一下/點選工具列中的「案頭動作」圖示，也可使用這些案頭動作。

1. 若要開啟資產，請按一下/點選「在案頭上開啟」快速動作![「在案頭上開啟」圖示](assets/do-not-localize/aemassets_icon_openondesktop.png)。

   或者，從工具欄的「案頭操作」菜單中選擇「開啟」。

   >[!NOTE]
   >
   >當您編輯剛開啟且未簽出的檔案時，其他使用者無法得知您正在更新資產。

1. 若要開啟資產以在Adobe Creative Cloud應用程式中進行編輯，請按一下/點選「編輯案頭快速動作![編輯案頭圖示](assets/do-not-localize/aemassets_icon_editdesktop.png)」。 這也會簽出資產以進行編輯。 完成編輯後，簽入資產以更新[!DNL Assets]中的更改。

   或者，從工具欄的「案頭操作」菜單中選擇「編輯」。

1. 選取「開啟」功能表選項。 選取的資產會以預覽模式開啟。
1. 若要編輯資產，請選取「編輯」選項。 資產會以編輯模式開啟。

### 從Mac OS上的Finder簽出資產 {#check-out-assets-on-mac}

應用程式可讓您簽出資產檔案，以防止其他使用者修改您正在使用的檔案。

1. 從Mac內容菜單中，選擇開啟AEM Assets資料夾選項以開啟Finder。

   ![使用案頭應用程式存取和開啟資產的內容功能 [!DNL Experience Manager] 表選項](assets/aem_desktopapp_mac_context_menu.png)

   *圖：使用案頭應用程式存取及開啟資產的內容功能 [!DNL Experience Manager] 表選項。*

1. 導覽至您要結帳的資產。
1. 以滑鼠右鍵按一下資產，然後從內容功能表選取「更多資產資訊」 。
1. 在「資產資訊」對話方塊中，按一下/點選「結帳」圖示以結帳資產。 按一下/點選後，「結帳」圖示會切換至「簽入」圖示。

   ![瀏覽至要結帳的資產](assets/browse_assets_to_checkout.png)

1. 若要簽入資產以供其他使用者使用，請按一下/點選「資產資訊」對話方塊中的簽入圖示。

### 在Windows上查看資產 {#check-out-assets-on-windows}

應用程式可讓您簽出資產檔案，以防止其他使用者修改您正在使用的檔案。

1. 從「內容」功能表中，選取「探索資產」以開啟「瀏覽器」。
1. 在瀏覽器中，導覽至您要結帳的資產位置。
1. 以滑鼠右鍵按一下資產，然後從內容功能表選取「在網頁上開啟」 。
1. 在「資產資訊」對話方塊中，按一下/點選「結帳」圖示。 「結帳」圖示切換為「簽入」圖示。

   ![結帳圖示切換](assets/checkout_icon_toggles.png)

1. 在Explorer中檢閱資產。 資產![資產鎖定圖示](assets/do-not-localize/aemassets_icon_lockcheckout.png)上的鎖定圖示表示您已簽出資產。

   >[!NOTE]
   >
   >延遲後可能會出現鎖定圖示。 [!DNL Experience Manager] 案頭應用程式會快取資產以快速存取，因此可能需要一些時間才能更新鎖定狀態。

1. 若要簽入資產以供其他使用者使用，請按一下/點選&#x200B;**資產資訊**&#x200B;對話方塊中的簽入圖示。

### 使用Finder或Explorer並使用Web介面簽入資產 {#check-in-an-asset-using-finder-or-explorer-and-using-web-interface}

完成資產編輯後，將資產儲存在案頭應用程式中。 從上下文菜單中，選擇&#x200B;**更多資產資訊**&#x200B;並按一下簽入。

資產會上傳至[!DNL Experience Manager]伺服器。 您可以選擇從系統托盤表徵圖中選擇&#x200B;**查看資產狀態** ，以檢查上載的狀態。 或者，您也可以從[!DNL Experience Manager]網頁介面簽入資產。 按一下已簽出的資產或選擇它。 在工具欄中，按一下簽入表徵圖![簽入表徵圖](assets/do-not-localize/aemassets_icon_checkin.png)。

在本機儲存任何變更後，資產就會自動上傳至[!DNL Experience Manager]。 簽入使資產可供其他[!DNL Experience Manager]使用者編輯。

### 將大量上傳資產和資料夾至[!DNL Experience Manager]伺服器 {#bulkupload}

使用[!DNL Experience Manager]案頭應用程式，您可以從本機檔案目錄將包含資產的整個資料夾上傳至[!DNL Assets]。 如此一來，資料夾內的所有資產都會大量上傳，不必一次上傳一個資產。

1. 在「資產」UI中，從工具列按一下/點選「 **建立** 」，然後從功能表選擇「 **上傳資料夾** 」。
1. 瀏覽至您要上傳的資料夾並加以選取。
1. 按一下/點選「確定」。 「資產狀態」對話方塊會顯示上傳的狀態。

   ![在「資產狀態」窗口中查看上載的狀態](assets/aem_desktopapp_bulkupload_status.png)

   在「資產狀態」窗口中查看上載的狀態

   >[!NOTE]
   >
   >您可以按一下/點選適當的圖示，手動暫停或取消上傳。

1. 上傳資料夾後，關閉對話方塊並導覽至「資產」UI。 上傳的資料夾會顯示在網頁介面中。

Adobe不建議從本地檔案系統複製貼上或將大量檔案或巢狀資料夾拖曳至網路共用區域。 由於技術限制，應用程式無法控制上傳程式，且效能不佳。

或者，在Finder或Explorer中選取您要上傳至[!DNL Experience Manager]的檔案/資料夾，將它們複製到系統剪貼簿，導覽至網路共用區域的目標資料夾，然後從[!DNL Experience Manager]案頭應用程式內容選單中選取&#x200B;**貼上資產**。 如此一來，[!DNL Experience Manager]案頭應用程式就會開始上傳貼上的資產，類似於[!DNL Experience Manager]網頁介面中可用的&#x200B;**上傳資料夾**&#x200B;選項。

>[!MORELIKETHIS]
>
>* [疑難排解 [!DNL Experience Manager] 案頭應用程式](troubleshoot-app-v1.md)

