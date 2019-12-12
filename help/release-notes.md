---
title: AEM案頭應用程式版本注意事項
description: AEM案頭應用程式的發行詳細資訊、增強功能、新功能、相容性和下載連結。
uuid: b783c3f8-aa1e-4c05-b687-5894909769f5
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: 3052549b-fe75-44fb-a55e-5cc612868f54
index: y
internal: n
snippet: y
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: b2015bd65db70a25e4c52e62a4de45a01a6748d5

---


# AEM desktop app release notes {#release-notes-v2}

| 產品 | Adobe Experience Manager (AEM) 桌面應用程式 |
|---------------|--------------------------------------------------------------------|
| 應用程式版本（修訂版） | 2.0 (2.0.1.1) |
| 支援的 AEM 版本 | AEM 6.5、AEM 6.4、AEM 6.3（含相容性套件） |
| 類型 | 次要版本 |
| 發行日期 | 2019年12月12日（Mac和Win） |
| 下載 URL | [MacOS 64 位元](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-osx-2.0.1.1.dmg)；[Windows 64 位元](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win64-2.0.1.1.exe)；[Windows 32 位元](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win32-2.0.1.1.exe) |

## 系統需求和先決條件 {#system-requirements-and-prerequisites-v2}

AEM 桌面應用程式與下列作業系統相容：

* Mac OS X 10.10 或更新版本，提供最新的錯誤修正。
* Windows 7 和 Windows 10，提供最新的服務套件和錯誤修正。

此應用程式可與下列的 AEM 版本搭配使用，不論是於內部部署或部署在 Adobe Managed Services (AMS) 上：

* [AEM 6.5.0 或更新版本](https://helpx.adobe.com/experience-manager/6-5/release-notes.html)
* [AEM 6.4.4 或更新版本](https://helpx.adobe.com/experience-manager/6-4/release-notes/sp-release-notes.html)
* AEM 6.4.0 版本至 AEM 6.4.3 版本，搭配[相容性套件](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)

>[!NOTE]
>
>不再支援AEM 6.3的案頭應用程式。 Adobe建議升級至較新且支援的AEM版本。
>AEM 6.3.3.1或更新版本可在安裝相容性套件後與案頭應用 [程式搭配使用](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)。 AEM 6.3沒有此類套件可供使用，因為計畫 [中沒有Service Pack](https://helpx.adobe.com/experience-manager/maintenance-releases-roadmap.html)。

您打算在本機電腦上安裝的應用程式版本，需要搭配特定的 Adobe Experience Manager 伺服器版本／其他伺服器端元件（服務套件、修補程式或功能套件）。請連絡您的 AEM 管理員以取得協助。

### Support for different assets and file types {#support-for-file-types}

應用程式支援儲存在 AEM 中、透過二進位檔進行基本運算的資產。在原生桌面應用程式中開啟檔案時，需透過作業系統內的特定應用程式（例如 Mac Preview 或 Adobe Photoshop），以特定檔案類型（例如 PNG 或 JPG）開啟。

部分檔案類型支援將連結的資產放入二進位檔。使用桌面應用程式開啟此類型的二進位檔案時，若資產存在於 AEM 的資料庫中，應用程式會預先下載連結的資產。目前支援的檔案類型包括：

* Adobe inDesign 檔案（INDD格式）
* Adobe Illustrator 檔案（AI格式）
* Adobe Photoshop 檔案（PS格式）

上述應用程式的Adobe Creative Cloud 2018和Adobe Creative Cloud 2019版本都支援此功能。 應用程式會透過啟發式、最佳比對方法，將連結資產的本機桌面路徑對應至 AEM 伺服器上的 URL。依賴的假設如下：

* Paths to placed files in the native application use a global desktop path (placed from the local network share shown with [!UICONTROL Reveal] option).
* 透過原生應用程式，將路徑儲存在檔案的 XMP 記錄中.
* AEM 已擷取含有資產中繼資料記錄的 XMP 記錄.
* 路徑可以與AEM中的資產相符，亦即，置入的檔案也位於AEM中的符合路徑下)。

## 新增功能和功能改善 {#whats-new-added}

To know the details, see [What's new in v2.0](introduction.md#whats-new-v2).

2.0.1版中的錯誤修正和更新包括：

* 允許選項配置目 `%Temp%` 錄以匹配路 `%APPDATA%` 徑。 <!-- CQ-4282665 -->
* 允許使用者透過Okta SAML驗證登入AEM作者。 <!-- CQ-4278134 -->


## 安裝指示 {#installation-instructions-v2}

若要瞭解如何安裝和設定應用程式，請參閱[「安裝 AEM 桌面應用程式」](install-upgrade.md)。

如果您要從舊版 AEM 桌面應用程式進行升級，您必須遵循列於[從舊版進行升級](install-upgrade.md#upgrade-from-previous-version)的最佳作法進行轉換。

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
* 當上傳含有注釋的變更至資產時，這些注釋會與資產一起儲存在AEM中，但不會顯示為版本修訂注釋。 此問題已在AEM 6.4.5和AEM 6.5.1中解決。Adobe強烈建議安裝最新的Service Pack。 <!-- CQ-4268990 -->
* 使用者無法取消資產傳輸。如果您不小心觸發了非預期的大量傳輸，請退出應用程式並重新啟動。<!-- CQ-4278940 -->

**平台問題：**

* 某些時候，即使您可能尚未編輯資產，Windows 上的資產狀態可能會在開啟後立即變更為 [!UICONTROL Edited Locally]。按一下 [!UICONTROL Refresh] 以更新。

>[!MORELIKETHIS]
>
>* [AEM 6.5 檔案](https://helpx.adobe.com/support/experience-manager/6-5.html)
>* [AEM Assets 6.5 檔案](https://docs.adobe.com/content/help/en/experience-manager-65/assets/home.html)
>* [如何使用AEM案頭應用程式](using.md)
>* [安裝和升級桌面應用程式](install-upgrade.md)
>* [最佳作法與疑難排解提示](troubleshoot.md)

