---
title: 安裝和配置案頭應用
description: 安裝並配置 [!DNL Adobe Experience Manager] desktop app to work with [!DNL Adobe Experience Manager Assets] 伺服器，並下載本地檔案系統上的資產。
feature: 案頭應用程式，發行資訊
exl-id: 422e51c1-c456-4151-bb43-4b3d29a58187
source-git-commit: ea7227110aac38115829c93e7339dcdfbd9394a6
workflow-type: tm+mt
source-wordcount: '1410'
ht-degree: 0%

---

# 安裝[!DNL Adobe Experience Manager]案頭應用程式 {#install-app-v2}

使用[!DNL Adobe Experience Manager]案頭應用程式時，您可輕鬆在本機案頭上取得[!DNL Experience Manager]中的資產，並可用於任何原生案頭應用程式。 資產可以預覽、在原生案頭應用程式中開啟、顯示在Mac Finder或Windows Explorer中以放置在其他檔案中，並可在本機變更 — 當您上傳且在存放庫中建立新版本時，變更會儲存回[!DNL Experience Manager]。

這種整合可讓組織中的各種角色，

* 在[!DNL Experience Manager Assets]中集中管理資產。

* 存取任何原生案頭應用程式（包括協力廠商應用程式）和Adobe Creative Cloud中的資產。 同時，使用者可輕鬆遵守各種標準，包括品牌推廣。

若要使用[!DNL Experience Manager]案頭應用程式，

* 確保[!DNL Experience Manager]案頭應用程式支援您的[!DNL Experience Manager]版本。 請參閱[系統要求](release-notes.md)。

* 下載並安裝應用程式。 請參閱下方的[安裝案頭應用程式](#install-v2)。

* 使用一些資產來測試連線。 請參閱[如何瀏覽及搜尋資產](using.md#browse-search-preview-assets)。

## 系統需求、必要條件和下載連結 {#tech-specs-v2}

如需詳細資訊，請參閱[[!DNL Experience Manager] 案頭應用程式發行說明](release-notes.md)。

## 從舊版升級 {#upgrade-from-previous-version}

如果您是案頭應用程式v1.x的使用者，請了解應用程式先前版本與最新版本之間的差異與相似性。 請參閱[案頭應用程式的新增功能](introduction.md#whats-new-v2)和[應用程式的運作方式](release-notes.md#how-app-works)

>[!NOTE]
>
>兩個版本的案頭應用程式無法在電腦上共存。 安裝版本之前，請卸載其他版本。

若要從舊版應用程式升級，請依照下列指示操作：

1. 升級前，請同步所有資產，並將變更上傳至[!DNL Experience Manager]。 這是為了避免在解除安裝應用程式時遺失任何編輯。

1. 解除安裝應用程式的舊版。 解除安裝時，選取要清除快取的選項。

1. 重新啟動電腦。

1. [](release-notes.md) 下載並安 [](#install-v2) 裝最新的應用程式。請依照下列指示操作。

## 安裝 {#install-v2}

要安裝案頭應用程式，請執行以下步驟。 安裝最新應用程式之前，請卸載任何現有Adobe[!DNL Experience Manager]案頭應用程式v1.x。 如需詳細資訊，請參閱上文。

1. 從[發行說明](release-notes.md)頁面下載最新安裝程式。

1. 保持[!DNL Experience Manager]部署的URL和憑證便於使用。

1. 如果您要從其他版本的應用程式升級，請參閱[升級案頭應用程式](#upgrade-from-previous-version)。

1. 如果您使用[!DNL Experience Manager]作為[!DNL Cloud Service]、[!DNL Experience Manager] 6.4.4或更新版本，或[!DNL Experience Manager] 6.5.0或更新版本，請跳過此步驟。 確保您的[!DNL Experience Manager]設定符合[發行說明](release-notes.md)中提及的相容性要求。 如有必要，請下載適用的[相容性包](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)，並使用[!DNL Experience Manager]包管理器作為[!DNL Experience Manager]管理員進行安裝。 要安裝軟體包，請參閱[如何使用軟體包](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html)。

1. 執行安裝程式二進位檔，並依照螢幕上的指示進行安裝。

1. 在Windows上，安裝程式可能會提示安裝`Visual Studio C++ Redistributable 2015`。 按照螢幕上的說明進行安裝。 如果安裝失敗，則手動安裝。 從[此處](https://www.microsoft.com/en-us/download/details.aspx?id=52685)下載安裝程式，並安裝`vc_redist.x64.exe`和`vc_redist.x86.exe`檔案。 重新運行[!DNL Experience Manager]案頭應用程式安裝程式。

1. 按提示重新啟動電腦。 啟動並設定案頭應用程式。

1. 若要將應用程式與[!DNL Experience Manager]存放庫連線，請按一下托盤中的應用程式圖示，然後啟動應用程式。 以`https://[aem_server]:[port]/`格式提供[!DNL Experience Manager]伺服器的地址。

   按一下&#x200B;**[!UICONTROL Connect]**&#x200B;並提供憑證。

   ![案頭應用與輸入伺服器地址的連接螢幕](assets/connect_da2.png)

   *圖：連接螢幕到輸入伺服器地址。*

   >[!CAUTION]
   >
   >確保[!DNL Experience Manager]伺服器地址之前或之後沒有前導或尾隨空格。 否則，應用程式無法連接到[!DNL Experience Manager]伺服器。

1. 成功連線後，您可以檢視[!DNL Experience Manager] DAM的根資料夾中可用的資料夾和資產清單。 您可以從應用程式內瀏覽資料夾。

   ![登入時，應用程式會顯示DAM內容](assets/firstview_da2.png)

   *圖：應用程式會在登入後顯示DAM內容*

1. （[!DNL Experience Manager] 6.5.1或更新版本）如果您使用的案頭應用程式搭配[!DNL Experience Manager] 6.5.1或更新版本，請將S3或Azure連接器升級至1.10.4或更新版本。 請參閱[Azure連接器](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html#azure-data-store)或[S3連接器](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html#amazon-s-data-store)。

   如果您是Adobe Managed Services(AMS)客戶，請聯絡Adobe客戶服務。

## 設定偏好設定 {#set-preferences}

要更改首選項，請按一下![更多選項表徵圖](assets/do-not-localize/more_options_da2.png)和&#x200B;**[!UICONTROL Preference]** ![首選項表徵圖](assets/do-not-localize/preferences_icon_da2.png)。 在&#x200B;**[!UICONTROL Preferences]**&#x200B;窗口中，調整以下值：

* [!UICONTROL Launch application on login]。

* [!UICONTROL Show window when application starts]。

* **[!UICONTROL Cache Directory]**:應用程式的本機快取位置（包含本機下載的資產）。

* **[!UICONTROL Network Drive Letter]**:用於映射至DAM的驅動器 [!DNL Experience Manager] 號。如果您不確定，請勿變更此項目。 應用程式可以映射到Windows上的任何驅動器號。 如果兩個使用者放置不同驅動器盤符的資產，則看不到對方放置的資產。 資產的路徑會變更。 資產會保留在二進位檔案（例如INDD）中，且不會移除。 應用程式會列出所有可用的驅動器號，預設會使用最後可用的號碼，通常為`Z`。

* **[!UICONTROL Maximum Cache Size]**:允許的硬碟快取（以GB為單位），用於儲存本機下載的資產。

* **[!UICONTROL Current cache size]**:本機下載資產的儲存大小。只有在使用應用程式下載資產後，才會顯示資訊。

* **[!UICONTROL Automatically download linked assets]**:如果您下載原始檔案，系統會自動擷取置於支援原生Creative Cloud應用程式中的。

* **[!UICONTROL Maximum number of downloads]**: ![警告](assets/do-not-localize/caution-icon.png) 表徵圖請謹慎更改。首次下載資產時（透過「顯示」、「開啟」、「編輯」、「下載」或類似選項），只有在批次包含的數量少於此數字時，才會下載資產。 預設值為 50。如果您不確定，請勿變更。 增加值可能會導致等候時間延長，而降低值可能無法讓您一次下載必要的資產或資料夾。

* **[!UICONTROL Use legacy conventions when creating nodes for assets and folders]**: ![警告](assets/do-not-localize/caution-icon.png) 表徵圖請謹慎更改。此設定可讓應用程式在上傳資料夾時模擬v1.10應用程式的行為。 在v1.10中，在儲存庫中建立的節點名稱會保留使用者提供的資料夾名稱的空格和大小寫。 不過，在應用程式的v2.1中，資料夾名稱中的額外空格會轉換為破折號。 例如，如果未選取選項，且保留v2.1中的預設行為，則上傳`New Folder`或`new   folder`會在存放庫中建立相同的節點。 如果選取此選項，系統會在存放庫中為上述兩個資料夾建立不同的節點，並符合v1.10應用程式的行為。

   v2.1的預設行為仍然相同，也就是說，將資料夾名稱中的多個空格替換為儲存庫節點名稱中的破折號，然後轉換為小寫節點名稱。

* **[!UICONTROL Upload Acceleration]**: ![警告](assets/do-not-localize/caution-icon.png) 表徵圖請謹慎更改。上傳資產時，應用程式可使用同時上傳來改善上傳速度。 您可以將滑桿移至右側，以增加上傳的並行性。 最左側的滑桿表示沒有併發（單線程上傳），中間位置對應10個併發線程，而最右側的上限對應20個併發線程。 更高的併發限制將佔用更多資源。

要更新不可用的首選項，請從[!DNL Experience Manager]伺服器中註銷，然後更新。 更新首選項後，按一下「保存首選項」](assets/do-not-localize/save_preferences_da2.png)。![

![案頭應用程式偏好設定和設定](assets/preferences_da2.png)

*圖：案頭應用程式偏好設定。*

### 代理支援 {#proxy-support}

[!DNL Experience Manager] 案頭應用程式使用系統的預先定義代理，透過HTTPS連線至網際網路。應用程式只能使用不需要額外驗證的網路代理進行連接。

如果配置或修改Windows的代理伺服器設定（Internet選項>區域網路設定），請重新啟動[!DNL Experience Manager]案頭應用程式，使更改生效。 啟動案頭應用程式時，會套用代理設定。 關閉並重新啟動應用程式，以讓任何變更生效。

如果您的代理需要身份驗證，則IT團隊可以允許代理伺服器設定中的[!DNL Experience Manager Assets] URL，以允許應用程式流量通過。

## 解除安裝應用程式 {#uninstall-the-app}

要在Windows上卸載應用程式，請執行以下步驟：

1. 將所有變更上傳至[!DNL Experience Manager]，以免遺失任何編輯內容。 請參閱[編輯資產並將更新的資產上傳至 [!DNL Experience Manager]](using.md#edit-assets-upload-updated-assets)。 註銷並[!UICONTROL Exit]應用。

1. 移除應用程式時，請移除任何其他作業系統應用程式。 從「Add（添加）」中卸載它，並在Windows上刪除程式。

1. 若要移除快取和記錄，請選取必要的核取方塊。

   ![卸載對話框以刪除日誌和快取](assets/uninstall_da2.png)

1. 按照螢幕上的說明操作。 完成後，重新啟動電腦。

要在Mac上卸載應用程式，請執行以下步驟：

1. 將所有變更上傳至[!DNL Experience Manager]，以免遺失任何編輯內容。 請參閱[編輯資產並將更新的資產上傳至 [!DNL Experience Manager]](using.md#edit-assets-upload-updated-assets)。 註銷並[!UICONTROL Exit]應用。

1. 從`/Applications`中移除`Adobe Experience Manager Desktop.app`。

或者，若要清除Mac上的內部應用程式快取並解除安裝應用程式，您可以在終端機中執行下列命令：

```shell
/Applications/Adobe Experience Manager Desktop/Contents/Resources/uninstall-osx/uninstall.sh
```
