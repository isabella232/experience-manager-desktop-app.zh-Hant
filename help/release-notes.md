---
title: Adobe Experience Manager案頭應用程式版本注意事項
description: Adobe Experience Manager案頭應用程式的發行詳細資訊、增強功能、新功能、相容性和下載連結。
uuid: b783c3f8-aa1e-4c05-b687-5894909769f5
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: 3052549b-fe75-44fb-a55e-5cc612868f54
index: y
internal: n
snippet: y
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 3eb9ab89ff6338fb29cfad1a031944119908d0a2
workflow-type: tm+mt
source-wordcount: '1320'
ht-degree: 48%

---


# Adobe Experience Manager案頭應用程式版本注意事項 {#release-notes-v2}

| 產品 | Adobe Experience manager 桌面應用程式 |
|--- |--- |
| 應用程式版本（修訂版） | 2.0 (2.0.2.0) |
| 支援的 AEM 版本 | AEM即雲端服務； AEM 6.5; AEM 6.4; AEM 6.3（含相容性套件） |
| 類型 | 次要版本 |
| 發行日期 | 2020年4月15日（Mac和Win） |
| 下載 URL | [macOS 64位元](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-osx-2.0.2.0.dmg); [Windows 64位元](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win64-2.0.2.0.exe); [Windows 32位元](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win32-2.0.2.0.exe) |

## 系統需求和先決條件 {#system-requirements-and-prerequisites-v2}

Adobe Experience Manager案頭應用程式與下列作業系統相容：

* Mac OS X 10.14或更新版本，以及最新的錯誤修正。

* Windows 7 和 Windows 10，提供最新的服務套件和錯誤修正。

此應用程式可與下列Experience Manager版本搭配使用，不論部署為雲端服務、部署在Adobe Managed Services(AMS)或內部部署：

* [Experience Manager 雲端服務](https://docs.adobe.com/content/help/zh-Hant/experience-manager-cloud-service/release-notes/home.html).

* [Experience Manager 6.5.0或更新版本](https://docs.adobe.com/content/help/en/experience-manager-65/release-notes/release-notes.html) 。

* [Experience Manager 6.4.4或更新版本](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/release-notes.html) 。

* Experience Manager 6.4.0 - 6.4.3及相容 [套件](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)。

>[!NOTE]
>
>Experience Manager 6.3案頭應用程式支援已過時。 Adobe建議升級至較新且支援的Adobe Experience Manager版本。
>安裝相容性套件後，Experience Manager 6.3.3.1或更新版本可與案頭應用程 [式搭配使用](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)。 Experience Manager 6.3沒有此類套件，因為計畫中 [沒有Service Pack](https://helpx.adobe.com/tw/experience-manager/maintenance-releases-roadmap.html)。

您打算在本機電腦上安裝的應用程式版本，需要搭配特定的 Adobe Experience Manager 伺服器版本／其他伺服器端元件（服務套件、修補程式或功能套件）。請連絡您的Adobe Experience Manager管理員以取得協助。

### Support for different assets and file types {#support-for-file-types}

應用程式支援儲存在Adobe Experience Manager中的資產，這些資產代表二進位檔案的基本作業。 在原生桌面應用程式中開啟檔案時，需透過作業系統內的特定應用程式（例如 Mac Preview 或 Adobe Photoshop），以特定檔案類型（例如 PNG 或 JPG）開啟。

部分檔案類型支援將連結的資產放入二進位檔。當使用案頭應用程式開啟這類二進位檔案時，如果資產存在於Experience Manager儲存庫中，應用程式會預先下載連結的資產。 目前支援的檔案類型包括：

* [!DNL Adobe InDesign] 檔案（INDD格式）
* [!DNL Adobe Illustrator] 檔案（AI格式）
* [!DNL Adobe Photoshop] 檔案（PS格式）

上述應用程式的Adobe Creative Cloud 2018和Adobe Creative Cloud 2019版本都支援此功能。 應用程式會使用啟發式、最佳比對方法，將連結資產的本機案頭路徑對應至Experience Manager伺服器上的URL。 依賴的假設如下：

* Paths to placed files in the native application use a global desktop path (placed from the local network share shown with [!UICONTROL Reveal] option).

* 透過原生應用程式，將路徑儲存在檔案的 XMP 記錄中.

* Experience Manager已擷取XMP記錄，並包含資產中繼資料記錄的路徑。

* 路徑可以與Experience Manager中的資產相符，即置入的檔案也位於Experience Manager中，路徑相符。

## 新增功能和功能改善 {#whats-new-added}

To know the details, see [What&#39;s new in v2.0](introduction.md#whats-new-v2).

**應用程式2.0.2版中的更新**

錯誤修正和更新包括：

* 若要改善上傳效能，請在中增加上傳加速 [!UICONTROL Preferences]。 當此設定開啟時，應用程式會使用更多本機CPU執行緒，並且耗用更多資源。

* 修正檔案名稱或路徑包含特定GB18030字元時，資產上傳的問題。 <!-- CQ-4283494 -->

* 切換至搜尋結果中的其他排序類型後，即可使用依關聯性排序選項。 <!-- CQ-4286874 -->

* 案頭應用程式現在會列出子資料夾，而不需要明確重新整理。 <!-- CQ-4285711 -->

* (Windows)已修正某些Windows電腦上罕見的無法使用應用程式介面問題。 使用者無法按一下應用程式介面，因為當介面元素的點按區域出現扭曲時，會側移。 <!-- CQ-4280785 -->

**應用程式2.0.1版中的更新**

錯誤修正和更新包括：

* 允許選項配置目 `%Temp%` 錄以匹配路 `%APPDATA%` 徑。 <!-- CQ-4282665 -->

* 允許使用者透過Okta SAML驗證登入AEM作者。 <!-- CQ-4278134 -->

## 安裝指示 {#installation-instructions-v2}

To know how to install and configure the app, see [Install Experience Manager desktop app](install-upgrade.md).

If you are upgrading from a previous Experience Manager desktop app, you must follow these best practices for transitioning that are listed at [upgrade from previous version](install-upgrade.md#upgrade-from-previous-version).

## 應用程式運作方式的重要附註 {#how-app-works}

請務必瞭解以下關於應用程式及其運作方式的資訊。

* 透過應用程式，您可以完整控制在 AEM 間進行之資產二進位檔的傳輸作業（開啟、編輯、上傳變更和上傳資產）。

   * 如果想要在桌面使用資產，您需要明確地「開啟」、「編輯」或「下載」資產至桌面，並可使用個別檔案、資料夾或多個檔案選取的方式進行上述操作。

   * 如果您想要將資產的本機變更內容上傳至 AEM，您需要以個別或多個檔案的方式選取 [!UICONTROL Upload Changes]。

   * 此應用程式不是將資產從桌面同步到 AEM 上的「同步用戶端」。

   * 應用程式不提供將 AEM 資料庫作為虛擬資料夾結構的網路共享。

* 應用程式顯示的資產清單內容是根據 AEM 的資產資料庫。應用程式不會顯示或管理從本機下載、並在本機檔案或快取資料夾中重新命名的任何檔案。

* 如果應用程式未顯示預期的結果，請按一下頂端列中的重新整理圖示。

* 區域網路共享（在您進行 [!UICONTROL Reveal File] 動作時顯示）只會顯示本機可用的檔案（和資料夾）。[!UICONTROL Reveal File] 和 [!UICONTROL Reveal Folder] 會預先下載資產，協助您取得顯示在區域網路共享中的正確資產。

* 當 Adobe Creative cloud 應用程式讀取連結／置於 Creative Cloud 應用程式原生檔案中的資產檔案時，會使用 SMB (Mac)／WebDAV(Win) 區域網路共享。

下圖說明當使用者執行動作時，資產和檔案如何從雲端移動至本機檔案系統（反向移動亦適用）。

![透過桌面應用程式，資產從 AEM 伺服器移動至原生桌面應用程式](assets/da20_flow_diagram.png)

## 已知問題 {#known-issues-v2}

**使用者介面問題：**

* 有時，案頭應用程式的介面會變成空白。 Right-click and click [!UICONTROL Refresh] to re-load the application. 進行此類刷新後，您將從DAM儲存庫的根目錄開始。 資產的更新或狀態會保留。 <!-- CQ-4270267 -->

* 在沒有追蹤板或滑鼠指標的情況下，很難導覽資料夾／搜尋結果。 The scroll-bar might not appear with mouse devices without mouse wheel. <!-- CQ-4269947 -->

* 少數情況下，當上傳的資產變更時，進度列可能無法顯示正確的進度。

* 在您套用、移除篩選器以尋找所有在本機編輯的資產後，應用程式不會將使用者引導至剛開始的搜尋結果或資料夾檢視。應用程式會顯示 DAM 資料庫的根資料夾。

* 某些時候，當您連線至未執行 AEM 伺服器的 URL 時，連線畫面會停止回應。請退出應用程式並重新啟動。

**CRUD（建立、讀取、更新和刪除）相關問題：**

* 若應用程式嘗試上傳包含無效字元的檔案，可能會導致伺服器端上傳失敗。<!-- CQ-4273652 -->

* 當上傳含有注釋的變更至資產時，這些注釋會與資產一起儲存在AEM中，但不會顯示為版本修訂注釋。 此問題已在AEM 6.4.5和AEM 6.5.1中解決。 Adobe強烈建議安裝最新的Service Pack。 <!-- CQ-4268990 -->

* 使用者無法取消資產傳輸。如果您不小心觸發了非預期的大量傳輸，請退出應用程式並重新啟動。<!-- CQ-4278940 -->

**平台問題：**

* 某些時候，即使您可能尚未編輯資產，Windows 上的資產狀態可能會在開啟後立即變更為 [!UICONTROL Edited Locally]。按一下 [!UICONTROL Refresh] 以更新。

>[!MORELIKETHIS]
>
>* [AEM as a Cloud Service檔案](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/landing/home.html)
>* [AEM as a Cloud Service Assets檔案](https://docs.adobe.com/content/help/zh-Hant/experience-manager-cloud-service/assets/home.html)
>* [如何使用Experience Manager案頭應用程式](using.md)
>* [安裝和升級桌面應用程式](install-upgrade.md)
>* [最佳作法與疑難排解提示](troubleshoot.md)

