---
title: 使用 [!DNL Experience Manager] 案頭應用1.10版。
description: 瞭解如何使用Adobe Experience Manager案頭應用1.10版並優化案頭上資產的工作。
feature: Desktop App,Asset Management
exl-id: 2fdc1c8d-b822-4cca-ad06-bd875a00aa6d
source-git-commit: dcd29d0bbb32004d970d334c256e659f4a4c39e1
workflow-type: tm+mt
source-wordcount: '2367'
ht-degree: 0%

---

# 使用 [!DNL Experience Manager] 案頭應用1.10版 {#use-aem-desktop-app-v1x}

使用應用程式， [!DNL Experience Manager] 可在您的本地案頭上輕鬆訪問，並可用於任何案頭應用程式。 在Mac查找器或Windows資源管理器中，可以輕鬆顯示資產，在案頭應用程式中開啟並在本地更改 — 更改將保存回 [!DNL Experience Manager] 在儲存庫中建立了新版本。

這種整合使組織中的各種角色能夠集中管理資產中的資產，並在Creative Cloud和其他應用程式中訪問這些資產，同時使您能夠輕鬆遵守包括品牌推廣在內的各種標準。

您使用 [!DNL Experience Manager] 案頭應用v1包括：

1. [與 [!DNL Experience Manager] 伺服器](#installandconnect)
1. [直接在案頭上開啟資產](#openondesktop)
1. [編輯和簽出案頭上的資產](#workonassets)
1. [批量上載資產和資料夾](#bulkupload)

有關各種建議的do和don&#39;ts，請參見 [使用應用程式的最佳做法](best-practices-for-v1.md)。 如果您在使用應用程式時遇到問題，請參閱 [故障排除 [!DNL Experience Manager] 案頭](troubleshoot-app-v1.md)。

>[!NOTE]
>
>案頭應用已在 [!DNL Experience Manager] 6.1版，並且 [!DNL Experience Manager Assets Companion App]。

## [!DNL Experience Manager] 創意工作流中的案頭應用觸摸點 {#aem-desktop-app-touch-points-in-the-creative-workflow}

[!DNL Experience Manager] 案頭應用，以及 [!DNL Assets]，整合到您的創意工作流中，並提供以下觸點。

![[!DNL Experience Manager] 案頭應用觸摸指向創意工作流程](assets/aem_desktopapp_workflow.png)

[!DNL Experience Manager] 案頭應用觸摸指向創意工作流程

## 安裝並將應用連接到 [!DNL Experience Manager] 伺服器 {#installandconnect}

在開始建立或編輯創意資產之前，請將案頭應用程式與 [!DNL Assets] 下載和上載儲存庫中的資產的伺服器。 執行以下任務：

1. [安裝應用](#installapp)。
1. [設定首選項](#inapppref) 和連接詳細資訊。
1. [連接到 [!DNL Experience Manager] 伺服器](#connect) 並將資產儲存庫作為本地驅動器裝載。
1. [啟用案頭操作](#desktopactions) 上 [!DNL Experience Manager] 伺服器。

[!DNL Experience Manager] 案頭應用使用HTTPS連接連接到 [!DNL Experience Manager] 伺服器，以強健和安全地傳輸您的資產。

>[!NOTE]
>
>對於部分或全部安裝和配置步驟，您可能需要您的 [!DNL Experience Manager] 管理員或系統管理員。

### 安裝應用程式 {#installapp}

要使用 [!DNL Experience Manager] 案頭應用，確保 [!DNL Experience Manager] 應用支援伺服器版本。 下載適合您的作業系統(Mac或Windows)的安裝檔案（二進位檔案）並安裝該應用。

根據網路和系統首選項的不同，可能需要進行詳細配置。 請參閱 [安裝和配置 [!DNL Experience Manager] 案頭應用](install-configure-app-v1.md) 的子菜單。

1. 轉到 [[!DNL Experience Manager] 案頭應用v1.10下載頁](/help/release-notes-of-v1.md) 並下載適合您的作業系統的二進位檔案。
1. 啟動下載的安裝檔案並按照螢幕說明安裝應用。

   >[!NOTE]
   >
   >只有一個實例 [!DNL Experience Manager] 案頭應用程式可以安裝並一次處於活動狀態。

### 瞭解應用程式內選項和首選項 {#inapppref}

應用程式允許設定與連接並斷開 [!DNL Experience Manager] 伺服器、查看上載狀態、管理本地快取等。 預設設定適用於應用程式的典型用戶。 您可以調整設定以從應用程式和整合中獲取更多資訊 [!DNL Experience Manager] 伺服器。 下面詳細介紹了各種設定。

**瀏覽資產** 開啟本地驅動器， [!DNL Assets] 儲存庫已掛載。 換句話說，瀏覽現在在本地電腦上可用的資產。

**查看資產狀態** 上載更改的資產或將新資產添加到 [!DNL Assets] 儲存庫，應用程式將在後台上載資產。 後台上載允許平滑操作，而無需等待上載完成，特別是對於大型資產。 您可以在本地保存更改並將其忘記。 應用程式需要一些時間將這些資產發送到伺服器，具體取決於可用頻寬。 您可以檢查上載的狀態以及一些更基本的資訊。

**選項** 按一下案頭應用程式托盤中的選項以訪問設定，在系統啟動時啟動應用程式；連接到 [!DNL Experience Manager] 應用啟動時的伺服器；更改本地驅動器號 [!DNL Assets] 在裝載後可用。

**高級>管理快取** 您可以控制可用於本地快取的磁碟空間量。 來自 [!DNL Assets] 伺服器在本地快取，以獲得更流暢的體驗。 您可以更改預設值以滿足您的要求。 此外，還可以清除快取以重新提取所有資產。 清除快取時，它會保留未保存的更改。 未簽入的任何資產 [!DNL Experience Manager] 伺服器將保留且未刪除。

### 連接到 [!DNL Experience Manager] 伺服器 {#connect}

該應用支援Mac和Windows上的代理配置。 應用程式啟動時讀取配置。 如果修改代理設定，請重新啟動應用以使更改生效。

>[!NOTE]
>
>如果修改代理設定，請重新啟動應用以使更改生效。 否則，應用繼續使用以前配置的代理伺服器。

1. 啟動 [!DNL Experience Manager] 案頭應用。 映射 [!DNL Experience Manager] 應用程式實例，指定 [!DNL Experience Manager] 格式 `https://[aem-server-url]:[port]`。

   ![在Mac驗證並提供 [!DNL Experience Manager] 伺服器URL](assets/aem_desktop_app_server_url.png)

1. 在登錄螢幕中，指定實例的用戶名和密碼。 指定備用 [!DNL Experience Manager] 實例，選擇 **[!UICONTROL Alternate Login URL]** 的雙曲餘切值。

   ![提供 [!DNL Experience Manager] 登錄螢幕上的伺服器憑據 [!DNL Experience Manager] 案頭應用](assets/login_screen_v1.png)

### 在中啟用案頭操作 [!DNL Experience Manager] Web介面 {#desktopactions}

在「資產」用戶介面中，您可以瀏覽資產位置或簽出並開啟資產以在案頭應用程式中進行編輯。 這些選項稱為案頭操作，預設情況下不啟用。 按照這些步驟啟用它。

1. 在「資產」介面中，按一下/點擊工具欄右上角的「用戶」表徵圖。
1. 按一下 **[!UICONTROL My Preferences]** 顯示 **[!UICONTROL Preferences]** 對話框。

   ![[!DNL Experience Manager] 用戶介面與用戶首選項](assets/aem_ui_user_preferences.png)

1. 在 [!UICONTROL User Preferences] 對話框，選擇 **[!UICONTROL Show Desktop Actions For Assets]**，然後按一下 **[!UICONTROL Accept]**。

   ![檢查 [!UICONTROL Show Desktop Actions For Assets] 啟用案頭操作](assets/enable_desktop_actions.png)

   *圖：檢查 [!UICONTROL Show Desktop Actions For Assets] 啟用案頭操作。*

## 訪問和開啟案頭上的資產 {#openondesktop}

按一下 **開啟** 要在本地電腦上開啟資產，應用會將該資產下載到其內部快取。 應用啟動與下載資產的檔案類型關聯的本機案頭應用程式。

在Mac，選擇 **開啟** 從上下文菜單開啟資產 [!DNL Experience Manager] 案頭應用。 在Windows上，從上下文菜單中選擇「在Web上開啟」以開啟資產。 在「資產狀態」窗口中，按一下/點擊 ![「在案頭上開啟」表徵圖](assets/do-not-localize/aemassets_icon_openondesktop.png) 來修改標籤元素的屬性。

對於Adobe InDesign(INDD)檔案，選擇 **[!UICONTROL Open]** 的子菜單。 按一下此選項後，應用程式會將連結的資產下載到本地檔案系統，然後在Adobe InDesign開啟INDD檔案。 此方法確保在編輯INDD檔案時，必要的資產在本地可用。

![用於訪問和開啟資產的上下文菜單選項 [!DNL Experience Manager] 案頭應用](assets/aem_desktopapp_mac_context_menu.png)

*圖：用於訪問和開啟資產的上下文菜單選項 [!DNL Experience Manager] 案頭應用。*

>[!NOTE]
>
>在Windows上， [預設Windows 7設定](https://support.microsoft.com/en-us/kb/2668751) 防 [!DNL Experience Manager] 處理大於50 MB的資產的案頭應用。

<!-- TBD: The above note is for Windows 7 which is not supported by the app anymore. Remove it later.
-->

>[!NOTE]
>
>Adobe建議您轉到Mac上的Finder View選項並停用這些選項 **顯示項資訊**。 **顯示項目預覽**, **顯示預覽列** 已安裝 [!DNL Assets] 的子菜單。 它提高了效能。

### 中的其他選項 [!DNL Experience Manager] 介面 {#additional-options-in-aem-assets}

在您映射 [!DNL Assets] 儲存庫到本地驅動器，您可以啟用其他表徵圖和資料夾上載功能，以顯示映射的資產和資料夾。

1. 開啟 [!DNL Assets] 將指針懸停在資料夾或資產上，以在「卡」視圖中將案頭操作顯示為快速操作。

   ![在資產UI中，開啟快速操作菜單以查看案頭操作](assets/desktop_actions_in_card_view.png)

   *圖：在資產UI中，開啟快速操作菜單以查看案頭操作。*

   當您按一下 **案頭操作** 的子菜單。

1. 要在與特定檔案副檔名關聯的案頭應用程式中開啟資產，請按一下 **在案頭上開啟** 快速操作 ![「在案頭上開啟」表徵圖](assets/do-not-localize/aemassets_icon_openondesktop.png)。

   或者，選擇 **開啟** 從 **案頭操作** 的子菜單。

要在本地檔案系統上查找特定資產，請按一下 **顯示** 快速操作 ![顯示表徵圖](assets/do-not-localize/aemassets_reveal_icon.png)。 或者，選擇 **顯示** 從 **案頭操作** 的子菜單。

## 瞭解資產狀態 {#understand-the-asset-statuses}

| ![Windows預設應用表徵圖](assets/do-not-localize/win_default.png) | 應用程式已連接到伺服器，並且所有資產都已同步。 |
--- |--- |
| ![Windows禁用表徵圖](assets/do-not-localize/win_disabled.png) | 應用已啟動，但未與伺服器連接。 某些資產可能正在掛起同步。 |
| ![Windows檔案同步表徵圖](assets/do-not-localize/win_sync.png) | 資產正在同步。 正在上載或下載檔案。 您可以從「資產狀態」窗口查看確切狀態並暫停轉移。 |
| ![Windows重新連接表徵圖](assets/do-not-localize/win_refresh.png) | 應用正在嘗試重新連接。 可能是網路問題導致它斷開連接。 |

## 處理您的資產 {#workonassets}

### 從 [!DNL Experience Manager] Web介面 {#check-out-assets-from-the-aem-web-interface}

[!DNL Assets] 允許您簽出要編輯的資產，並在完成更改後將其簽回。 簽出資產後，只有您才能編輯、注釋、發佈、移動或刪除資產。 簽出資產會鎖定資產並阻止其他用戶執行其中的任何操作。 要能夠簽出/簽入資產，您需要對其進行寫入訪問。

有兩種方法可從 [!DNL Experience Manager] Web介面。 有關第一種方法的詳細資訊，請參見 [從資產UI簽入和簽出檔案](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/check-out-and-submit-assets.html)。 執行以下步驟，以便第二種方法在 [!DNL Experience Manager] 已安裝案頭應用。

1. 開啟 [!DNL Assets] 將指針懸停在資料夾或資產上，以在「卡」視圖中將案頭操作顯示為快速操作。

   ![「卡視圖」中的「屬性」選項](assets/desktop_actions_in_card_view.png)

   在選擇資產後或從資產頁面的工具欄中按一下/點擊工具欄中的「案頭操作」表徵圖時，這些案頭操作也可用。

1. 要開啟資產，請按一下/點擊「在案頭上開啟」快速操作 ![「在案頭上開啟」表徵圖](assets/do-not-localize/aemassets_icon_openondesktop.png)。

   或者，從工具欄的「案頭操作」菜單中選擇「開啟」。

   >[!NOTE]
   >
   >當您編輯剛開啟且未簽出的檔案時，其他用戶不會知道您正在更新資產。

1. 要開啟資產以在Adobe Creative Cloud應用程式中進行編輯，請按一下/點擊「編輯案頭快速操作」 ![編輯案頭表徵圖](assets/do-not-localize/aemassets_icon_editdesktop.png)。 這還會檢查資產以進行編輯。 編輯完畢後，簽入資產，以更新 [!DNL Assets]。

   或者，從工具欄的「案頭操作」菜單中選擇「編輯」。

1. 選擇「開啟」菜單選項。 所選資產在預覽模式下開啟。
1. 要編輯資產，請選擇「編輯」選項。 資產在編輯模式下開啟。

### 從MacOS上的Finder中籤出資產 {#check-out-assets-on-mac}

應用允許您簽出資產檔案，以防止其他用戶修改您正在處理的檔案。

1. 從「Mac」上下文菜單中，選擇「開啟AEM Assets資料夾」選項以開啟「查找器」。

   ![用於訪問和開啟資產的上下文菜單選項 [!DNL Experience Manager] 案頭應用](assets/aem_desktopapp_mac_context_menu.png)

   *圖：用於訪問和開啟資產的上下文菜單選項 [!DNL Experience Manager] 案頭應用。*

1. 定位至要簽出的資產。
1. 按一下右鍵資產，然後從上下文菜單中選擇「更多資產資訊」。
1. 在「資產資訊」對話框中，按一下/點擊「檢出」表徵圖以檢出資產。 按一下/點擊「簽入」表徵圖後，「簽出」表徵圖將切換到簽入表徵圖。

   ![瀏覽到要結帳的資產](assets/browse_assets_to_checkout.png)

1. 要簽入資產，以便其他用戶可以使用，請按一下/點擊「資產資訊」對話框中的簽入表徵圖。

### 在Windows上簽出資產 {#check-out-assets-on-windows}

應用允許您簽出資產檔案，以防止其他用戶修改您正在處理的檔案。

1. 從「上下文」菜單中，選擇「瀏覽資產」以開啟瀏覽器。
1. 在瀏覽器中，導航到要簽出的資產的位置。
1. 按一下右鍵資產，然後從上下文菜單中選擇「在Web上開啟」。
1. 在「資產資訊」對話框中，按一下/點擊「檢出」表徵圖。 「檢出」(Checkout)表徵圖切換為檢入表徵圖。

   ![「簽出」表徵圖切換](assets/checkout_icon_toggles.png)

1. 在瀏覽器中複查資產。 資產上的鎖定表徵圖 ![資產鎖定表徵圖](assets/do-not-localize/aemassets_icon_lockcheckout.png) 表示您已簽出資產。

   >[!NOTE]
   >
   >鎖定表徵圖可能在延遲後出現。 [!DNL Experience Manager] 案頭應用快取資產以便快速訪問，因此可能需要幾分鐘時間更新鎖定的狀態。

1. 要簽入資產，以便其他用戶可以使用，請按一下/點擊 **資產資訊** 對話框。

### 使用Finder或Explorer並使用Web介面簽入資產 {#check-in-an-asset-using-finder-or-explorer-and-using-web-interface}

編輯完資產後，將資產保存在案頭應用程式中。 從上下文菜單中，選擇 **更多資產資訊** 並按一下「簽入」。

資產將上載到 [!DNL Experience Manager] 伺服器。 （可選）通過選擇 **查看資產狀態** 表徵圖。 或者，您可以從 [!DNL Experience Manager] Web介面。 按一下已檢出的資產或將其選中。 在工具欄中，按一下簽入表徵圖 ![簽入表徵圖](assets/do-not-localize/aemassets_icon_checkin.png)。

資產已上載到 [!DNL Experience Manager] 在本地保存任何更改後自動執行。 簽入使資產可供其他用戶使用 [!DNL Experience Manager] 編輯。

### 將資產和資料夾批量上載到 [!DNL Experience Manager] 伺服器 {#bulkupload}

使用 [!DNL Experience Manager] 案頭應用程式，您可以將包含資產的整個資料夾從本地檔案目錄上載到 [!DNL Assets]。 這樣，資料夾內的所有資產都將批量上載，而不必一次上載一個。

1. 在「資產」UI中，按一下/點擊 **建立** ，然後 **上載資料夾** 的子菜單。
1. 瀏覽到要上載的資料夾並選擇它。
1. 按一下/點擊「OK（確定）」。 「資產狀態」對話框顯示上載的狀態。

   ![在「資產狀態」窗口中查看載入狀態](assets/aem_desktopapp_bulkupload_status.png)

   在「資產狀態」窗口中查看載入狀態

   >[!NOTE]
   >
   >通過按一下/輕擊相應表徵圖，可手動暫停或取消上載。

1. 資料夾上載後，關閉對話框並導航到「資產」UI。 上載的資料夾顯示在Web介面中。

Adobe不建議將更多檔案或嵌套資料夾從本地檔案系統複製貼上或拖到網路共用區。 由於技術限制，應用無法控制上載過程，且效能較差。

或者，選擇要上載到的檔案/資料夾 [!DNL Experience Manager] 在Finder或Explorer中，將它們複製到系統剪貼簿，導航到網路共用區中的目標資料夾，然後從 [!DNL Experience Manager] 案頭應用上下文菜單 **貼上資產**。 這邊， [!DNL Experience Manager] 案頭應用開始上載貼上的資產，類似於 **上載資料夾** 的 [!DNL Experience Manager] Web介面。

>[!MORELIKETHIS]
>
>* [故障排除 [!DNL Experience Manager] 案頭應用程式應用程式](troubleshoot-app-v1.md)

