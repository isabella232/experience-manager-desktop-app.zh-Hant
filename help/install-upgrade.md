---
title: 安裝和設定案頭應用程式
description: 安裝並設定 [!DNL Adobe Experience Manager] desktop app to work with [!DNL Adobe Experience Manager Assets] 伺服器，並下載您本機檔案系統上的資產。
translation-type: tm+mt
source-git-commit: caf6faf17157a0e9e3bffd40b4bdd0802a71dad7
workflow-type: tm+mt
source-wordcount: '1300'
ht-degree: 1%

---


# 安裝[!DNL Adobe Experience Manager]案頭應用程式{#install-app-v2}

使用[!DNL Adobe Experience Manager]案頭應用程式，[!DNL Experience Manager]中的資產可輕鬆在您的本機案頭上使用，並可用於任何原生案頭應用程式。 資產可以預覽、在原生案頭應用程式中開啟、在Mac Finder或Windows檔案總管中透露，以放入其他檔案，並在本機變更——當您上傳時，變更會儲存回[!DNL Experience Manager]，並在儲存庫中建立新版本。

這樣的整合允許組織中的各種角色，

* 在[!DNL Experience Manager Assets]集中管理資產。

* 在任何原生案頭應用程式中存取資產，包括協力廠商應用程式和Adobe Creative Cloud。 同時，使用者可輕鬆符合各種標準，包括品牌。

若要使用[!DNL Experience Manager]案頭應用程式，

* 請確定您的[!DNL Experience Manager]版本受[!DNL Experience Manager]案頭應用程式支援。 請參閱[系統需求](release-notes.md)。

* 下載並安裝應用程式。 請參閱下面的[安裝案頭應用程式](#install-v2)。

* 使用幾個資產測試連線。 請參閱[如何瀏覽及搜尋資產](using.md#browse-search-preview-assets)。

## 系統需求、先決條件和下載連結{#tech-specs-v2}

如需詳細資訊，請參閱[[!DNL Experience Manager] 案頭應用程式版本注意事項](release-notes.md)。

## 從舊版{#upgrade-from-previous-version}升級

如果您是v1.x案頭應用程式的使用者，請瞭解該應用程式先前和最新版本之間的差異和相似性。 請參閱[案頭應用程式的新增功能](introduction.md#whats-new-v2)和[應用程式的運作方式](release-notes.md#how-app-works)

>[!NOTE]
>
>電腦上無法共存兩個版本的案頭應用程式。 在安裝版本之前，請先解除安裝其他版本。

若要從舊版應用程式升級，請依照下列指示進行：

1. 在升級之前，請同步您的所有資產，並將變更上傳至[!DNL Experience Manager]。 這是為了避免在解除安裝應用程式時遺失任何編輯。

1. 解除安裝舊版應用程式。 卸載時，選擇清除快取的選項。

1. 重新啟動您的電腦。

1. [下載](release-notes.md) 並安 [](#install-v2) 裝最新的應用程式。請依照下列指示進行。

## 安裝 {#install-v2}

若要安裝案頭應用程式，請依照下列步驟進行。 在安裝最新應用程式之前，請先解除安裝任何現有的Adobe[!DNL Experience Manager]案頭應用程式v1.x。 如需詳細資訊，請參閱上文。

1. 從[版本注意事項](release-notes.md)頁面下載最新的安裝程式。

1. 讓[!DNL Experience Manager]部署的URL和認證隨手可得。

1. 如果您要從其他應用程式版本升級，請參閱[升級案頭應用程式](#upgrade-from-previous-version)。

1. 如果您使用[!DNL Experience Manager]做為[!DNL Cloud Service]、[!DNL Experience Manager] 6.4.4或更新版本，或[!DNL Experience Manager] 6.5.0或更新版本，請略過此步驟。 確保您的[!DNL Experience Manager]設定符合[發行說明](release-notes.md)中提及的相容性要求。 如有必要，請下載適用的[相容性軟體包](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)，並使用[!DNL Experience Manager]軟體包管理器作為[!DNL Experience Manager]管理員進行安裝。 要安裝軟體包，請參見[如何使用軟體包](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html)。

1. 執行安裝程式二進位檔，並依照螢幕上的指示進行安裝。

1. 在Windows上，安裝程式可能會提示安裝`Visual Studio C++ Redistributable 2015`。 依照螢幕上的指示進行安裝。 如果安裝失敗，則手動安裝。 從[這裡](https://www.microsoft.com/en-us/download/details.aspx?id=52685)下載安裝程式，並同時安裝`vc_redist.x64.exe`和`vc_redist.x86.exe`檔案。 重新執行[!DNL Experience Manager]案頭應用程式安裝程式。

1. 根據提示重新啟動電腦。 啟動並設定案頭應用程式。

1. 若要將應用程式與[!DNL Experience Manager]儲存庫連線，請按一下托盤中的應用程式圖示並啟動應用程式。 以`https://[aem_server]:[port]/`格式提供[!DNL Experience Manager]伺服器的地址。

   按一下&#x200B;**[!UICONTROL Connect]**&#x200B;並提供憑據。

   ![案頭應用程式與輸入伺服器位址的連線畫面](assets/connect_da2.png)

   *圖：連線畫面輸入伺服器位址。*

   >[!CAUTION]
   >
   >確保[!DNL Experience Manager]伺服器地址前後沒有前導或尾隨空格。 否則，應用程式無法連線至[!DNL Experience Manager]伺服器。

1. 成功連接後，您可以查看[!DNL Experience Manager] DAM的根資料夾中可用的資料夾和資產清單。 您可以從應用程式內瀏覽資料夾。

   ![在登入時，應用程式會顯示DAM內容](assets/firstview_da2.png)

   *圖：應用程式在登入後會顯示DAM內容*

1. （[!DNL Experience Manager] 6.5.1或更新版本）如果您使用含[!DNL Experience Manager] 6.5.1或更新版本的案頭應用程式，請將S3或Azure連接器升級至1.10.4或更新版本。 請參閱[Azure連接器](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html#azure-data-store)或[S3連接器](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html#amazon-s-data-store)。

   如果您是Adobe Managed Services(AMS)客戶，請聯絡Adobe客戶服務。

## 設定首選項{#set-preferences}

要更改首選項，請按一下![更多選項表徵圖](assets/do-not-localize/more_options_da2.png)和&#x200B;**[!UICONTROL Preference]** ![首選項表徵圖](assets/do-not-localize/preferences_icon_da2.png)。 在&#x200B;**[!UICONTROL Preferences]**&#x200B;視窗中，調整下列值：

* [!UICONTROL Launch application on login]。

* [!UICONTROL Show window when application starts]。

* **[!UICONTROL Cache Directory]**:應用程式的本機快取位置（包含本機下載的資產）。

* **[!UICONTROL Network Drive Letter]**:用於映射到 [!DNL Experience Manager] DAM的驅動器號。如果您不確定，請勿變更此項。 應用程式可以對應至Windows上的任何驅動器號。 如果兩個使用者放置不同磁碟機號碼的資產，他們就看不到彼此放置的資產。 資產的路徑會變更。 資產會保留在二進位檔案中（例如INDD），不會移除。 應用程式會列出所有可用的磁碟機盤符，預設會使用最後可用的盤符，通常為`Z`。

* **[!UICONTROL Maximum Cache Size]**:允許在硬碟上以GB為單位快取，以儲存本機下載的資產。

* **[!UICONTROL Current cache size]**:本機下載資產的儲存大小。只有在使用應用程式下載資產後，才會顯示資訊。

* **[!UICONTROL Automatically download linked assets]**:如果您下載原始檔案，則會自動擷取置於支援原生Creative Cloud應用程式中的資產。

* **[!UICONTROL Maximum number of downloads]**: ![警告](assets/do-not-localize/caution-icon.png) 圖示請謹慎變更。首次下載資產時（透過「顯現」、「開啟」、「編輯」、「下載」或類似選項），只有在批次包含的資產少於此數目時，才會下載資產。 預設值為 50。如果您不確定，請勿變更。 增加值可能會延長等候時間，而降低值可能不允許您一次下載必要的資產或檔案夾。

* **[!UICONTROL Use legacy conventions when creating nodes for assets and folders]**: ![警告](assets/do-not-localize/caution-icon.png) 圖示請謹慎變更。此設定可讓應用程式在上傳檔案夾時模擬v1.10應用程式行為。 在v1.10中，在儲存庫中建立的節點名稱會使用用戶提供的資料夾名稱的空格和外框。 不過，在應用程式的v2.1中，檔案夾名稱中的額外空格會轉換為破折號。 例如，如果未選擇該選項並保留了v2.1中的預設行為，則上載`New Folder`或`new   folder`將在儲存庫中建立相同的節點。 如果選取此選項，則會在儲存庫中為上述兩個檔案夾建立不同的節點，並符合v1.10應用程式的行為。

   v2.1的預設行為仍然保持不變，即，將資料夾名稱中的多個空格替換為儲存庫節點名稱中的破折號，並轉換為小寫節點名稱。

* **[!UICONTROL Upload Acceleration]**: ![警告](assets/do-not-localize/caution-icon.png) 圖示請謹慎變更。上傳資產時，應用程式可使用並行上傳來改善上傳速度。 您可以將滑桿向右移動，以增加上傳的並行性。 遠端左側的滑桿表示沒有並行（單執行緒上傳），中間位置對應10個並行執行緒，而遠端右側的上限則對應20個並行執行緒。 更高的併發限制會佔用更多資源。

若要更新不可用的偏好設定，請登出[!DNL Experience Manager]伺服器，然後進行更新。 更新首選項後，按一下「保存首選項」![](assets/do-not-localize/save_preferences_da2.png)。

![案頭應用程式偏好設定和設定](assets/preferences_da2.png)

*圖：案頭應用程式偏好設定。*

## 解除安裝應用程式{#uninstall-the-app}

要在Windows上卸載應用程式，請執行以下步驟：

1. 將您的所有變更上傳至[!DNL Experience Manager]，以避免遺失任何編輯。 請參閱[編輯資產並將更新的資產上傳至 [!DNL Experience Manager]](using.md#edit-assets-upload-updated-assets)。 登出並[!UICONTROL Exit]應用程式。

1. 移除應用程式時，請移除任何其他作業系統應用程式。 從Windows的「Add and remove programs（添加和刪除程式）」中卸載它。

1. 要刪除快取和日誌，請選中必要的複選框。

   ![卸載對話框以刪除日誌和快取](assets/uninstall_da2.png)

1. 依照螢幕上的指示進行。 完成後，重新啟動電腦。

若要解除安裝Mac上的應用程式，請依照下列步驟進行：

1. 將您的所有變更上傳至[!DNL Experience Manager]，以避免遺失任何編輯。 請參閱[編輯資產並將更新的資產上傳至 [!DNL Experience Manager]](using.md#edit-assets-upload-updated-assets)。 登出並[!UICONTROL Exit]應用程式。

1. 從`/Applications`移除`Adobe Experience Manager Desktop.app`。

或者，若要清除Mac上的內部應用程式快取並解除安裝應用程式，您可以在終端機中執行下列命令：

```shell
/Applications/Adobe Experience Manager Desktop/Contents/Resources/uninstall-osx/uninstall.sh
```
