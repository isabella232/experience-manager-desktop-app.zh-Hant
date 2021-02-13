---
title: '[!DNL Adobe Experience Manager] 案頭應用程式版本注意事項'
description: ' [!DNL Adobe Experience Manager] 案頭應用程式的發行詳細資訊、增強功能、新功能、相容性和下載連結。'
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: b5292d9386432bd7c6ba5d7117dbc9fd9f014941
workflow-type: tm+mt
source-wordcount: '1418'
ht-degree: 35%

---


# [!DNL Adobe Experience Manager] 案頭應用程式版本注意事項  {#release-notes-v2}

| 產品 | [!DNL Adobe Experience Manager] 桌面應用程式 |
|--- |--- |
| 應用程式版本（修訂版） | 2.1(2.1.0.0) |
| 支援的[!DNL Adobe Experience Manager]版本 | [!DNL Experience Manager] 作為 [!DNL Cloud Service]; [!DNL Experience Manager] 6.5; [!DNL Experience Manager] 6.4; [!DNL Experience Manager] 6.3（含相容套件） |
| 類型 | 次要版本 |
| 發行日期 | 2020年12月17日（Mac和Win） |
| 下載AEM 6.x的URL | [macOS 64位元](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-osx-2.1.0.0.dmg); [Windows 64位元](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win64-2.1.0.0.exe); [Windows 32位元](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win32-2.1.0.0.exe) |
| 將AEM的URL下載為[!DNL Cloud Service] | [macOS 64位元](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-osx-2.1.0.0.dmg); [Windows 64位元](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-win64-2.1.0.0.exe); [Windows 32位元](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-win32-2.1.0.0.exe) |

## 系統需求和先決條件 {#system-requirements-and-prerequisites-v2}

[!DNL Adobe Experience Manager] 桌面應用程式與下列作業系統相容：

* Mac OS X 10.14或更新版本，以及最新的錯誤修正。

* Windows 10含有最新的Service Pack和錯誤修正。

>[!NOTE]
>
>供應商(https://support.microsoft.com/en-us/help/4057281/windows-7-support-ended-on-january-14-2020)不再支援Windows 7。

應用程式適用於下列[!DNL Experience Manager]版本，不論部署為[!DNL Cloud Service]、部署在Adobe Managed Services(AMS)或內部部署：

* [[!DNL Experience Manager] as a [!DNL Cloud Service]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/home.html).

* [[!DNL Experience Manager] 6.5.0或更](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html) 新版本。

* [[!DNL Experience Manager] 6.4.4或更](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/sp-release-notes.html) 新版本。

* [!DNL Experience Manager] 6.4.0 - 6.4.3和相容 [軟體包](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)。

>[!NOTE]
>
>[!DNL Experience Manager] 6.3的案頭應用程式支援已過時。 Adobe建議升級至較新且支援的[!DNL Adobe Experience Manager]版本。
>[!DNL Experience Manager] 6.3.3.1或更新版本可在安裝[相容性套件](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)後與案頭應用程式搭配使用。 [!DNL Experience Manager] 6.3中沒有此類軟體包，因為[未計畫](https://helpx.adobe.com/tw/experience-manager/maintenance-releases-roadmap.html)服務包。

您打算在本機電腦上安裝的應用程式版本需要特定的[!DNL Adobe Experience Manager]伺服器版本／其他伺服器端元件（服務套件、Hotfix或功能套件）。 請洽詢您的[!DNL Experience Manager]管理員以取得協助。

### 支援不同的資產和檔案類型{#support-for-file-types}

應用程式支援儲存在[!DNL Experience Manager]中的資產，這些資產代表二進位檔案的基本作業。 在原生桌面應用程式中開啟檔案時，需透過作業系統內的特定應用程式（例如 Mac Preview 或 Adobe Photoshop），以特定檔案類型（例如 PNG 或 JPG）開啟。

部分檔案類型支援將連結的資產放入二進位檔。當使用案頭應用程式開啟這類二進位檔案時，如果資產存在於[!DNL Experience Manager]儲存庫中，應用程式會預先下載連結的資產。 目前支援的檔案類型包括：

* [!DNL Adobe InDesign] 檔案（INDD格式）
* [!DNL Adobe Illustrator] 檔案（AI格式）
* [!DNL Adobe Photoshop] 檔案（PS格式）

上述應用程式的[!DNL Adobe Creative Cloud] 2018和[!DNL Adobe Creative Cloud] 2019版本都支援此功能。 應用程式會使用啟發式、最佳比對方法，將連結資產的本機案頭路徑對應至[!DNL Experience Manager]伺服器上的URL。 依賴的假設如下：

* 原生應用程式中置入檔案的路徑使用全域案頭路徑（從本機網路共用置入，顯示[!UICONTROL Reveal]選項）。

* 透過原生應用程式，將路徑儲存在檔案的 XMP 記錄中.

* [!DNL Experience Manager] 已擷取含有資產中繼資料記錄的 XMP 記錄.

* 路徑可以與[!DNL Experience Manager]中的資產匹配，即，置入的檔案也位於[!DNL Experience Manager]中匹配路徑下。

## 新增功能和功能改善 {#whats-new-added}

如需詳細資訊，請參閱[v2.0](introduction.md#whats-new-v2)的新增功能。

**應用程式2.1.0.0版中的更新**

* 若要上傳資產，使用者現在可以直接從Windows檔案總管或Mac Finder，拖曳應用程式介面上的檔案或檔案夾。 除了應用程式中先前提供的上傳選項外，這個功能還可運作。

**應用程式2.0.3版中的更新**

目前版本中修正的錯誤為：

* 修正Windows使用者嘗試使用應用程式存取[!DNL Adobe Experience Manager] 6.5.5.0例項上的DAM儲存庫時所面臨的登入問題。

**應用程式2.0.2版中的更新**

錯誤修正和更新包括：

* 若要改善上傳效能，請在[!UICONTROL Preferences]中增加上傳加速。 當此設定開啟時，應用程式會使用更多本機CPU執行緒，而且會耗用更多資源。

* 修正檔案名稱或路徑包含特定GB18030字元時，資產上傳的問題。<!-- CQ-4283494 -->

* 切換至搜尋結果中的其他排序類型後，即可使用依關聯性排序選項。<!-- CQ-4286874 -->

* 案頭應用程式現在會列出子資料夾，而不需要明確重新整理。<!-- CQ-4285711 -->

* (Windows)已修正某些Windows電腦上罕見的無法使用應用程式介面問題。 使用者無法按一下應用程式介面，因為當介面元素的點按區域出現扭曲時，會側移。<!-- CQ-4280785 -->

**應用程式2.0.1版中的更新**

錯誤修正和更新包括：

* 允許選項配置`%Temp%`目錄以匹配`%APPDATA%`路徑。<!-- CQ-4282665 -->

* 允許使用者透過Okta SAML驗證登入[!DNL Experience Manager]作者。<!-- CQ-4278134 -->

## 安裝指示 {#installation-instructions-v2}

若要瞭解如何安裝和設定應用程式，請參閱[Install [!DNL Experience Manager] 案頭應用程式](install-upgrade.md)。

如果您要從舊版[!DNL Experience Manager]案頭應用程式升級，則必須遵循這些從舊版[升級中列出的轉換最佳實務。](install-upgrade.md#upgrade-from-previous-version)

## 應用程式運作方式的重要附註 {#how-app-works}

請務必瞭解以下關於應用程式及其運作方式的資訊。

* 應用程式可完整控制需要將資產二進位檔從和完全傳輸至[!DNL Experience Manager]（開啟、編輯、上傳變更和上傳資產）的作業。

   * 如果想要在桌面使用資產，您需要明確地「開啟」、「編輯」或「下載」資產至桌面，並可使用個別檔案、資料夾或多個檔案選取的方式進行上述操作。

   * 如果您想要對上傳至[!DNL Experience Manager]的資產進行本機變更，您必須個別選取或透過多選取來選取[!UICONTROL Upload Changes]。

   * 應用程式不是同步案頭資產和[!DNL Experience Manager]的「同步用戶端」。

   * 應用程式不提供將[!DNL Experience Manager]儲存庫映射為虛擬資料夾結構的網路共用。

* 應用程式顯示的資產清單內容是根據 的資產資料庫。應用程式不會顯示或管理從本機下載、並在本機檔案或快取資料夾中重新命名的任何檔案。

* 如果應用程式未顯示預期的結果，請按一下頂端列中的重新整理圖示。

* 區域網路共享（在您進行 [!UICONTROL Reveal File] 動作時顯示）只會顯示本機可用的檔案（和資料夾）。[!UICONTROL Reveal File] 和 [!UICONTROL Reveal Folder] 會預先下載資產，協助您取得顯示在區域網路共享中的正確資產。

* 當 Adobe Creative cloud 應用程式讀取連結／置於 Creative Cloud 應用程式原生檔案中的資產檔案時，會使用 SMB (Mac)／WebDAV(Win) 區域網路共享。

下圖說明當使用者執行動作時，資產和檔案如何從雲端移動至本機檔案系統（反向移動亦適用）。

![[!DNL Experience Manager]透過桌面應用程式，資產從 伺服器移動至原生桌面應用程式](assets/da20_flow_diagram.png)

## 已知問題 {#known-issues-v2}

**使用者介面問題：**

* 有時，案頭應用程式的介面可能會變成空白。 按一下右鍵，然後按一下[!UICONTROL Refresh]重新載入應用程式。 進行此類刷新後，您將從DAM儲存庫的根目錄開始。 資產的更新或狀態會保留。<!-- CQ-4270267 -->

* 在沒有追蹤板或滑鼠指標的情況下，很難導覽資料夾／搜尋結果。 沒有滑鼠滾輪的滑鼠裝置可能無法顯示捲軸。<!-- CQ-4269947 -->

* 少數情況下，當上傳的資產變更時，進度列可能無法顯示正確的進度。

* 在您套用、移除篩選器以尋找所有在本機編輯的資產後，應用程式不會將使用者引導至剛開始的搜尋結果或資料夾檢視。應用程式會顯示 DAM 資料庫的根資料夾。

* 當您連線至未執行[!DNL Experience Manager]伺服器的URL時，連線畫面會停止回應。 請退出應用程式並重新啟動。

**CRUD（建立、讀取、更新和刪除）相關問題：**

* 若應用程式嘗試上傳包含無效字元的檔案，可能會導致伺服器端上傳失敗。<!-- CQ-4273652 -->

* 當上傳含有注釋的資產變更時，注釋會與資產一起儲存在[!DNL Experience Manager]中，但不會顯示為版本修訂注釋。 此問題已在[!DNL Experience Manager] 6.4.5和[!DNL Experience Manager] 6.5.1中解決。Adobe建議安裝最新的Service Pack。<!-- CQ-4268990 -->

* 使用者無法取消資產傳輸。如果您不小心觸發了非預期的大量傳輸，請退出應用程式並重新啟動。<!-- CQ-4278940 -->

**平台問題：**

* 某些時候，即使您可能尚未編輯資產，Windows 上的資產狀態可能會在開啟後立即變更為 [!UICONTROL Edited Locally]。按一下 [!UICONTROL Refresh] 以更新。

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] 文件](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/landing/home.html)
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] [!DNL Assets] 文件](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/home.html)
>* [如何使用桌 [!DNL Experience Manager] 面應用程式](using.md)
>* [安裝和升級桌面應用程式](install-upgrade.md)
>* [最佳作法與疑難排解提示](troubleshoot.md)

