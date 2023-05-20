---
title: 安裝和配置案頭應用
description: 安裝和配置 [!DNL Adobe Experience Manager] 案頭應用與 [!DNL Adobe Experience Manager Assets] 並下載本地檔案系統上的資產。
feature: Desktop App,Release Information
exl-id: 422e51c1-c456-4151-bb43-4b3d29a58187
source-git-commit: 5b5970cec02d4a605bd7d826d1daa71fe228b0d9
workflow-type: tm+mt
source-wordcount: '1426'
ht-degree: 0%

---

# 安裝 [!DNL Adobe Experience Manager] 案頭應用 {#install-app-v2}

使用 [!DNL Adobe Experience Manager] 案頭應用程式， [!DNL Experience Manager] 可在您的本地案頭上輕鬆使用，並可用於任何本機案頭應用程式。 資產可以預覽、在本機案頭應用程式中開啟、在Mac查找器或Windows資源管理器中顯示以放置在其他文檔中，並可以在本地更改 — 更改將保存回 [!DNL Experience Manager] 上載並在儲存庫中建立新版本時。

這種整合允許組織中的各種角色：

* 集中管理資產 [!DNL Experience Manager Assets]。

* 訪問任何本機案頭應用程式（包括第三方應用程式）和Adobe Creative Cloud的資產。 同時，用戶可以輕鬆地遵循品牌等各種標準。

要使用 [!DNL Experience Manager] 案頭應用：

* 確保 [!DNL Experience Manager] 版本受支援 [!DNL Experience Manager] 案頭應用。 查看 [系統要求](release-notes.md)。

* 下載並安裝應用程式。 請參閱 [安裝案頭應用](#install-v2) 下。

* Test連接，使用少量資產。 請參閱 [如何瀏覽和搜索資產](using.md#browse-search-preview-assets)。

## 系統要求、先決條件和下載連結 {#tech-specs-v2}

有關詳細資訊，請參見 [[!DNL Experience Manager] 案頭應用發行說明](release-notes.md)。

## 從早期版本升級 {#upgrade-from-previous-version}

如果您是案頭應用v1.x的用戶，則瞭解該應用的上一版本與最新版本之間的差異和相似性。 請參閱 [案頭應用中的新增功能](introduction.md#whats-new-v2) 和 [應用的工作原理](release-notes.md#how-app-works)。

>[!NOTE]
>
>電腦上不能共存兩個版本的案頭應用。 在安裝版本之前，請卸載其他版本。

要從應用的早期版本升級，請按照以下說明操作：

1. 升級前，同步所有資產並將更改上載到 [!DNL Experience Manager]。 這樣做是為了避免在卸載應用程式時丟失任何編輯內容。

1. 卸載此應用的早期版本。 卸載時，選擇清除快取的選項。

1. 重新啟動電腦。

1. [下載](release-notes.md) 和 [安裝](#install-v2) 最新應用。 按照下面的說明操作。

## 安裝 {#install-v2}

要安裝案頭應用，請執行以下步驟。 卸載任何現有Adobe [!DNL Experience Manager] 安裝最新應用之前，案頭應用v1.x。 有關詳細資訊，請參閱上文。

1. 從 [發行說明](release-notes.md) 的子菜單。

1. 保留您的URL和憑據 [!DNL Experience Manager] 部署非常方便。

1. 如果要從其他版本的應用升級，請參閱 [升級案頭應用](#upgrade-from-previous-version)。

1. 如果您正在使用 [!DNL Experience Manager] 作為 [!DNL Cloud Service]。 [!DNL Experience Manager] 6.4.4或更高版本，或 [!DNL Experience Manager] 6.5.0或更高版本。 確保 [!DNL Experience Manager] 安裝程式符合中提到的相容性要求 [發行說明](release-notes.md)。 如有必要，請下載適用的 [相容性包](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) 並使用 [!DNL Experience Manager] 包管理器 [!DNL Experience Manager] 管理員。 要安裝軟體包，請參見 [如何使用包](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html)。

1. 執行安裝程式二進位檔案，並按照螢幕說明進行安裝。

1. 在Windows上，安裝程式可能會提示安裝 `Visual Studio C++ Redistributable 2015`。 按照螢幕說明安裝。 如果安裝失敗，請手動安裝。 從下載安裝程式 [這裡](https://www.microsoft.com/en-us/download/details.aspx?id=52685) 同時安裝 `vc_redist.x64.exe` 和 `vc_redist.x86.exe` 的子菜單。 重新運行 [!DNL Experience Manager] 案頭應用安裝程式。

1. 根據提示重新啟動電腦。 啟動並配置案頭應用。

1. 將應用與 [!DNL Experience Manager] 儲存庫，按一下托盤中的應用表徵圖並啟動應用。 提供地址 [!DNL Experience Manager] 格式 `https://[aem_server]:[port]/`。

   按一下 **[!UICONTROL Connect]** 並提供證書。

   ![案頭應用與輸入伺服器地址的連接螢幕](assets/connect_da2.png)

   *圖：連接到輸入伺服器地址的螢幕。*

   選擇 **[!UICONTROL Remember Connection]** 以避免每次登錄案頭應用時輸入連接詳細資訊。

   >[!CAUTION]
   >
   >確保地址之前或之後沒有前導空格或尾隨空格 [!DNL Experience Manager] 伺服器。 否則，應用無法連接到 [!DNL Experience Manager] 伺服器。

1. 成功連接後，您可以查看的根資料夾中可用的資料夾和資產清單 [!DNL Experience Manager] 水壩。 可以從應用中瀏覽資料夾。

   ![登錄後，應用將顯示DAM內容](assets/firstview_da2.png)

   *圖：應用程式在登錄後顯示DAM內容*

1. ([!DNL Experience Manager] 6.5.1或更高版本)如果您正在使用案頭應用 [!DNL Experience Manager] 6.5.1或更高版本，將S3或Azure連接器升級到1.10.4版或更高版本。 請參閱 [Azure連接器](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html#azure-data-store) 或 [S3連接器](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html#amazon-s-data-store)。

   如果您是Adobe托管服務(AMS)客戶，請與Adobe客戶支援聯繫。

## 設定首選項 {#set-preferences}

要更改首選項，請按一下 ![「更多選項」表徵圖](assets/do-not-localize/more_options_da2.png) 和 **[!UICONTROL Preference]** ![「首選項」表徵圖](assets/do-not-localize/preferences_icon_da2.png)。 在 **[!UICONTROL Preferences]** 窗口，調整以下值：

* [!UICONTROL Launch application on login]。

* [!UICONTROL Show window when application starts]。

* **[!UICONTROL Cache Directory]**:應用的本地快取位置（包含本地下載的資產）。

* **[!UICONTROL Network Drive Letter]**:用於映射到 [!DNL Experience Manager] 水壩。 如果您不確定，請不要更改此項。 該應用可以映射到Windows上的任何驅動器號。 如果兩個用戶放置不同驅動器盤符的資產，則他們無法看到彼此放置的資產。 資產的路徑會改變。 這些資產將保留在二進位檔案（如INDD）中，並且不會刪除。 應用會列出所有可用的驅動器盤符，預設情況下使用通常為 `Z`。

* **[!UICONTROL Maximum Cache Size]**:硬碟上允許的快取(GB)，用於儲存本地下載的資產。

* **[!UICONTROL Current cache size]**:本地下載的資產的儲存大小。 僅當使用應用下載資產後，才會顯示該資訊。

* **[!UICONTROL Automatically download linked assets]**:如果下載原始檔案，則自動獲取放置在受支援的本機Creative Cloud應用中的資產。

* **[!UICONTROL Maximum number of downloads]**: ![警告表徵圖](assets/do-not-localize/caution-icon.png) 謹慎更改。 首次下載資產時（通過「顯示」、「開啟」、「編輯」、「下載」或類似選項），僅當批包含的資產少於此數字時，才下載資產。 預設值為 50。如果不確定，不要更改。 增加值可能導致等待時間延長，而減少值可能不允許您一次性下載必要的資產或資料夾。

* **[!UICONTROL Use legacy conventions when creating nodes for assets and folders]**: ![警告表徵圖](assets/do-not-localize/caution-icon.png) 謹慎更改。 此設定允許應用在上載資料夾時模擬v1.10應用行為。 在v1.10中，在儲存庫中建立的節點名稱涉及用戶提供的資料夾名稱的空格和大小寫。 但是，在應用的v2.1中，資料夾名稱中的額外空格將轉換為短划線。 例如，上載 `New Folder` 或 `new   folder` 如果未選中該選項並保留v2.1中的預設行為，則在儲存庫中建立相同的節點。 如果選擇此選項，則會在儲存庫中為上述兩個資料夾建立不同的節點，並且它與v1.10應用的行為相匹配。

   v2.1的預設行為仍保持不變，即，將資料夾名稱中的多個空格替換為儲存庫節點名稱中的短划線，並轉換為小寫節點名稱。

* **[!UICONTROL Upload Acceleration]**: ![警告表徵圖](assets/do-not-localize/caution-icon.png) 謹慎更改。 在上載資產時，應用程式可以使用併發上載來提高上載速度。 通過向右移動滑塊，可以增加上載的併發性。 左側的滑塊表示沒有併發（單線程上載），中間位置對應10個併發線程，右側的最大限制對應20個併發線程。 較高的併發限制會佔用更多資源。

要更新不可用的首選項，請註銷 [!DNL Experience Manager] 伺服器，然後更新。 更新首選項後，按一下 ![保存首選項](assets/do-not-localize/save_preferences_da2.png)。

![案頭應用首選項和設定](assets/preferences_da2.png)

*圖：案頭應用首選項。*

### 代理支援 {#proxy-support}

[!DNL Experience Manager] 案頭應用使用系統的預定義代理通過HTTPS連接到Internet。 應用只能使用不需要額外身份驗證的網路代理進行連接。

如果為Windows配置或修改代理伺服器設定（Internet選項> LAN設定），請重新啟動 [!DNL Experience Manager] 案頭應用，更改生效。 啟動案頭應用時應用代理配置。 關閉並重新啟動應用，使任何更改生效。

如果代理需要身份驗證，IT團隊可以 [!DNL Experience Manager Assets] 代理伺服器設定中的URL，以允許應用程式通信通過。

## 卸載應用 {#uninstall-the-app}

要在Windows上卸載應用程式，請執行以下步驟：

1. 將所有更改上載到 [!DNL Experience Manager] 以免丟失任何編輯。 請參閱 [編輯資產並將更新的資產上載到 [!DNL Experience Manager]](using.md#edit-assets-upload-updated-assets)。 註銷並 [!UICONTROL Exit] 應用程式。

1. 刪除其他作業系統應用程式時刪除該應用。 從Windows上的「Add and remove programs（添加和刪除程式）」中卸載它。

1. 要刪除快取和日誌，請選中必要的複選框。

   ![卸載對話框以刪除日誌和快取](assets/uninstall_da2.png)

1. 按照螢幕說明操作。 完成後，重新啟動電腦。

要卸載Mac上的應用程式，請執行以下步驟：

1. 將所有更改上載到 [!DNL Experience Manager] 以免丟失任何編輯。 請參閱 [編輯資產並將更新的資產上載到 [!DNL Experience Manager]](using.md#edit-assets-upload-updated-assets)。 註銷並 [!UICONTROL Exit] 應用程式。

1. 刪除 `Adobe Experience Manager Desktop.app` 從 `/Applications`。

或者，要清理Mac上的內部應用程式快取並卸載該應用程式，可以在終端中執行以下命令：

```shell
/Applications/Adobe Experience Manager Desktop/Contents/Resources/uninstall-osx/uninstall.sh
```
