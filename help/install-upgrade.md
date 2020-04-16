---
title: 安裝和設定Adobe Experience Manager案頭應用程式
description: 安裝並設定Adobe Experience Manager案頭應用程式，以便與Adobe Experience Manager Assets伺服器搭配運作，並下載您本機檔案系統上的資產。
uuid: 79bc9de9-5708-41f9-ac43-68c1fd2a2129
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: f6365302-1690-4719-9b8c-035719422740
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 49532b1c5eec497df5b29084675c08f25a15819a

---


# Install Adobe Experience Manager desktop app {#install-app-v2}

使用Adobe Experience Manager案頭應用程式，Experience Manager中的資產可輕鬆在您的本機案頭上使用，並可用於任何原生案頭應用程式。 資產可以預覽、在原生案頭應用程式中開啟、在Mac Finder或Windows檔案總管中透露，以放入其他檔案，並在本機變更——當您上傳時，變更會儲存回Experience Manager，並在儲存庫中建立新版本。

這樣的整合允許組織中的各種角色，

* 在Experience Manager Assets中集中管理資產。
* 在任何原生案頭應用程式（包括協力廠商應用程式）和Adobe Creative Cloud中存取資產。 同時，使用者可輕鬆符合各種標準，包括品牌。

若要使用Experience Manager案頭應用程式，

* 確保Experience Manager案頭應用程式支援您的Experience Manager版本。 請參閱 [以下系統需](release-notes.md#system-requirements-and-prerequisites-v2) 求。
* 下載並安裝應用程式。 請參 [閱以下安裝案頭應用程](#install-v2) 式。
* 使用幾個資產測試連線。 瞭解 [如何瀏覽及搜尋資產](using.md#browse-search-preview-assets)。

## 系統需求、必要條件和下載連結 {#tech-specs-v2}

如需詳細資訊，請參閱 [Experience Manager案頭應用程式版本注意事項](release-notes.md)。

## 從應用程式v1.x升級至應用程式v2 {#upgrade-from-previous-version}

如果您是應用程式的現有使用者，請瞭解應用程式的舊版與最新版本之間的差異與相似性。 此外，請依照這些准則，從v1.x轉換至最新版本。

>[!NOTE]
>
>案頭應用程式v1.x和v2無法在機器上共存。 在安裝版本之前，請先解除安裝其他版本。

若要從v1.x升級至最新版的應用程式，請依照下列指示進行：

1. 在升級之前，請同步您的所有資產。 使用應用程式v1.x上傳所有變更。這是為了避免在解除安裝應用程式v1.x時遺失任何變更。
1. 解除安裝應用程式v1.x。卸載v1.x時，請清除快取。
1. 重新啟動您的電腦。
1. 下載並安裝最新的應用程式。 請依照下列指示進行。

## 安裝 {#install-v2}

若要安裝案頭應用程式，請依照下列步驟進行。 在安裝最新應用程式之前，請先解除安裝任何現有的Adobe Experience Manager案頭應用程式v1.x。 如需詳細資訊，請參閱上文。

1. 讓Experience Manager部署的URL和認證隨時隨手可得。
1. 如果您使用Experience Manager做為Cloud服務、Experience Manager 6.4.4或更新版本，或Experience Manager 6.5.0或更新版本，請略過此步驟。 確保Experience Manager設定符合發行說明中提及的相容 [性要求](release-notes.md)。 如有必要，請下載適 [用的相容性套件](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) ，並使用Experience Manager Package Manager作為Experience Manager管理員進行安裝。 要安裝軟體包，請參 [閱How to with Packages](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/package-manager.html)。
1. 執行安裝程式二進位檔，並依照螢幕上的指示進行安裝。
1. 在Windows上，安裝程式可能會提示安裝 `Visual Studio C++ Redistributable 2015`。 依照螢幕上的指示進行安裝。 如果安裝失敗，則手動安裝。 從這裡下載安裝 [程式](https://www.microsoft.com/en-us/download/details.aspx?id=52685) ，並同時安裝 `vc_redist.x64.exe` 和檔 `vc_redist.x86.exe` 案。 重新執行AEM案頭應用程式安裝程式。
1. 根據提示重新啟動電腦。 啟動並設定案頭應用程式。
1. 若要將應用程式與AEM儲存庫連接，請按一下托盤中的應用程式圖示以啟動應用程式。 提供AEM例項的位址。 按一下 **[!UICONTROL Connect]** 並提供憑據。

   ![案頭應用程式的連線畫面與輸入伺服器位](assets/connect_da2.png "址連線畫面與輸入伺服器位址")

   >[!C作業]
   >
   >請確定AEM伺服器位址前後沒有前導或尾隨空格。 否則，應用程式無法連線至AEM伺服器。

1. 成功連線後，您可以檢視AEM DAM根資料夾中可用的資料夾和資產清單。 您可以從應用程式內瀏覽資料夾。

   ![登入時，應用程式會顯示DAM](assets/firstview_da2.png "內容登入時，應用程式會顯示DAM內容")

1. （Experience Manager 6.5.1或更新版本）如果您正在使用含Experience Manager 6.5.1或更新版本的案頭應用程式，請將S3或Azure連接器升級至1.10.4或更新版本。 請參 [閱Azure連接器](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/data-store-config.html#AzureDataStore) 或 [S3連接器](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/data-store-config.html#AmazonS3DataStore)。

   如果您是Adobe Managed Services(AMS)客戶，請聯絡Adobe客戶服務。

## 設定首選項 {#set-preferences}

要更改首選項，請按一下「更 ![多選項」表徵圖](assets/do-not-localize/more_options_da2.png) ，並 **[!UICONTROL Preference]** 按一下「首 ![選項」表徵圖](assets/do-not-localize/preferences_icon_da2.png)。 在窗口 **[!UICONTROL Preferences]** 中，調整以下值：

* [!UICONTROL Launch application on login].
* [!UICONTROL Show window when application starts].
* **[!UICONTROL Cache Directory]**:應用程式的本機快取位置（包含本機下載的資產）。
* **[!UICONTROL Network Drive Letter]**:用來對應至AEM DAM的磁碟機號碼。 如果您不確定，請勿變更此項。 應用程式可以對應至Windows上的任何驅動器號。 如果兩個使用者放置不同磁碟機號碼的資產，他們就看不到彼此放置的資產。 資產的路徑會變更。 資產會保留在二進位檔案中（例如INDD），不會移除。 應用程式會列出所有可用的磁碟機盤符，並依預設會使用最後可用的盤符 `Z`。
* **[!UICONTROL Maximum Cache Size]**:允許在硬碟上以GB為單位快取，以儲存本機下載的資產。
* **[!UICONTROL Current cache size]**:本機下載資產的儲存大小。 只有在使用應用程式下載資產後，才會顯示資訊。
* **[!UICONTROL Automatically download linked assets]**:如果您下載原始檔案，則會自動擷取置於支援原生Creative Cloud應用程式中的資產。
* **[!UICONTROL Maximum number of downloads]**:首次下載資產時（透過「顯現」、「開啟」、「編輯」、「下載」或類似選項），只有在批次包含的資產少於此數目時，才會下載資產。 預設值為 50。如果您不確定，請勿變更。 增加值可能會延長等候時間，而降低值可能不允許您一次下載必要的資產或檔案夾。
* **[!UICONTROL Upload Acceleration]**:上傳資產時，應用程式可使用並行上傳來改善上傳速度。 您可以將滑桿向右移動，以增加上傳的並行性。 遠端左側的滑桿表示沒有並行（單執行緒上傳），中間位置對應10個並行執行緒，遠端右側的上限則對應20個並行執行緒。 較高的併發限制要求本機處理器的資源消耗更多。

若要更新無法使用的偏好設定，請登出AEM伺服器。 更新偏好設定後，按一下「 ![儲存偏好設定](assets/do-not-localize/save_preferences_da2.png) 」以儲存變更。

![AEM案頭應用程式偏好設定和設定桌](assets/preferences_da2.png "面應用程式偏好設定")

## 解除安裝應用程式 {#uninstall-the-app}

要在Windows上卸載應用程式，請執行以下步驟：

1. 將您的所有變更上傳至AEM，以避免遺失任何編輯。 請參 [閱編輯資產並將更新的資產上傳至AEM](using.md#edit-assets-upload-updated-assets)。 登出應用 [!UICONTROL Exit] 程式。
1. 移除應用程式時，請移除任何其他作業系統應用程式。 從Windows的「Add and remove programs（添加和刪除程式）」中卸載它。
1. 要刪除快取和日誌，請選中必要的複選框。
   ![解除安裝對話方塊以移除記錄檔和快取](assets/uninstall_da2.png "解除安裝對話方塊以移除記錄檔和快取")
1. 依照螢幕上的指示進行。 完成後，重新啟動電腦。

若要解除安裝Mac上的應用程式，請依照下列步驟進行：

1. 將您的所有變更上傳至AEM，以避免遺失任何編輯。 請參 [閱編輯資產並將更新的資產上傳至AEM](using.md#edit-assets-upload-updated-assets)。 登出應用 [!UICONTROL Exit] 程式。
1. 從中 `Adobe Experience Manager Desktop.app` 刪除 `/Applications`。

或者，若要清除Mac上的內部應用程式快取並解除安裝應用程式，您可以在終端機中執行下列命令：
`/Applications/Adobe Experience Manager Desktop/Contents/Resources/uninstall-osx/uninstall.sh`
