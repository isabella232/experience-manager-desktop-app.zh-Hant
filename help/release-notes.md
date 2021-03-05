---
title: '[!DNL Adobe Experience Manager] 案頭應用程式版本注意事項'
description: ' [!DNL Adobe Experience Manager] 案頭應用程式的發行詳細資訊、增強功能、新功能、相容性和下載連結。'
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 784ffb2468d856589fbf29b10b965b3c3d919a2f
workflow-type: tm+mt
source-wordcount: '1468'
ht-degree: 28%

---


# [!DNL Adobe Experience Manager] 案頭應用程式版本注意事項  {#release-notes-v2}

最新案頭應用程式2.1版(2.1.1.0)的發行資訊如下。 發行日期為2021年3月5日。 它是具有增強功能的次要版本。

支援的[!DNL Experience Manager]版本包括：

* [!DNL Experience Manager] as a [!DNL Cloud Service]. 請參閱[發行說明](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/home.html)。
* [!DNL Experience Manager] 6.5.0或更新版本，位於Adobe Managed Services(AMS)或內部部署。請參閱[Service Pack發行說明](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html)。
* [!DNL Experience Manager] 6.4.4或更新版本，位於Adobe Managed Services(AMS)或內部部署。請參閱[Service Pack發行說明](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/sp-release-notes.html)。
* [!DNL Experience Manager] 6.4.0 - 6.4.3，並安裝相容 [性](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) 套件至Adobe Managed Services(AMS)或內部部署。
* [!DNL Experience Manager] 6.3（含相容套件）
* [!DNL Experience Manager] 6.3.3.1或更新版本，並安裝相容 [性套](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) 件。[!DNL Experience Manager] 6.3.3.0或舊版不支援案頭應用程式。

[!DNL Adobe Experience Manager] 案頭應用程式適用於下列作業系統：

* macOS X 10.14或更新版本，以及最新的錯誤修正。
* Windows 10含有最新的Service Pack和錯誤修正。

支援作業系統的下載URL包括：

| 作業系統 | [!DNL Experience Manager] as a [!DNL Cloud Service] | [!DNL Experience Manager] 6.x |
|---|---|---|
| macOS 64位元 | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-osx-2.1.1.0.dmg) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-osx-2.1.1.0.dmg) |
| Windows 64位元 | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-win64-2.1.1.0.exe) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win64-2.1.1.0.exe) |
| Windows 32位元 | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-win32-2.1.1.0.exe) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win32-2.1.1.0.exe) |

>[!NOTE]
>
>不再支援Windows 7。 請參閱[有關Windows 7的EOL的文章。](https://support.microsoft.com/en-us/help/4057281/windows-7-support-ended-on-january-14-2020)

<!-- The version of the app you plan to install on your local machine requires a specific [!DNL Adobe Experience Manager] server version/additional server-side components (service packs, hot fixes, or feature packs). Contact your [!DNL Experience Manager] administrator for help.
-->

## 支援不同的資產和檔案類型{#support-for-file-types}

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

## 新功能、增強功能和錯誤修正{#what-is-new}

如需詳細資訊，請參閱[v2.0](introduction.md#whats-new-v2)的新增功能。

**在應用程式v2.1.1.0中更新**

* 進階設定可讓應用程式在上傳檔案夾時模擬v1.10應用程式行為。 在v1.10中，在儲存庫中建立的節點名稱會使用用戶提供的資料夾名稱的空格和外框。 v2.1的預設行為仍然維持不變，即，在資料庫節點名稱中以連字型大小取代資料夾名稱中的多個空格，並轉換為小寫節點名稱。 請參閱[應用程式偏好設定](/help/install-upgrade.md#set-preferences)。

**在應用程式v2.1.0.0中更新**

* 若要上傳資產，使用者現在可以直接從Windows檔案總管或Mac Finder，拖曳應用程式介面上的檔案或檔案夾。 除了應用程式中先前提供的上傳選項外，這個功能還可運作。<!-- CQ-4309527 -->

**在應用程式v2.0.3中更新**

目前版本中修正的錯誤為：

* 修正Windows上嘗試存取[!DNL Adobe Experience Manager] 6.5.5.0上DAM儲存庫的應用程式使用者登入問題。

**應用程式2.0.2版中的更新**

錯誤修正和更新包括：

* 上傳加速設定現在已可供使用，可大幅提升上傳效能。 當此設定開啟時，應用程式會使用更多本機CPU執行緒來加快上傳速度，並且耗用更多資源。

* 當包含特定GB18030字元的檔案名稱或路徑已修正時，資產上傳。<!-- CQ-4283494 -->

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

   * 如果您想要在案頭上使用資產，您必須明確地將資產「開啟」、「編輯」或「下載」至您的案頭，不論是個別開啟、在檔案夾中，或是透過多選項。

   * 如果您想要對上傳至[!DNL Experience Manager]的資產進行本機變更，您必須個別選取或透過多選取來選取[!UICONTROL Upload Changes]。

   * 應用程式不是同步案頭資產和[!DNL Experience Manager]的「同步用戶端」。

   * 應用程式不提供將[!DNL Experience Manager]儲存庫映射為虛擬資料夾結構的網路共用。

* 應用程式顯示的資產清單內容是根據 的資產資料庫。應用程式不會顯示或管理從本機下載、並在本機檔案或快取資料夾中重新命名的任何檔案。

* 如果應用程式未顯示預期的結果，請按一下頂端列中的重新整理圖示。

* 區域網路共享（在您進行 [!UICONTROL Reveal File] 動作時顯示）只會顯示本機可用的檔案（和資料夾）。[!UICONTROL Reveal File] 和 [!UICONTROL Reveal Folder] 會預先下載資產，協助您取得顯示在區域網路共享中的正確資產。

* 當 Adobe Creative cloud 應用程式讀取連結／置於 Creative Cloud 應用程式原生檔案中的資產檔案時，會使用 SMB (Mac)／WebDAV(Win) 區域網路共享。

下圖說明資產和檔案從雲端流向本機檔案系統的流程，並以相反的方式，由使用者動作啟動。

![[!DNL Experience Manager]透過桌面應用程式，資產從 伺服器移動至原生桌面應用程式](assets/da20_flow_diagram.png)

## 已知問題 {#known-issues-v2}

**使用者介面問題：**

* 有時，案頭應用程式的介面可能會變成空白。 按一下右鍵並按一下[!UICONTROL Refresh]以重新載入應用程式。 進行此類刷新後，您將從DAM儲存庫的根目錄開始。 資產的更新或狀態會保留。<!-- CQ-4270267 -->

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

