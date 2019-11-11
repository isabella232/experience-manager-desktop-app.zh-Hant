---
title: AEM案頭應用程式版本注意事項
seo-title: AEM案頭應用程式版本注意事項
description: AEM案頭應用程式v1.x的發行詳細資訊、增強功能、新功能、相容性和下載連結。
seo-description: AEM案頭應用程式v1.x的發行詳細資訊、增強功能、新功能、相容性和下載連結。
uuid: b783c3f8-aa1e-4c05-b687-5894909769f5
contentOwner: asgupta
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: 3052549b-fe75-44fb-a55e-5cc612868f54
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b74a3ff5c9a25ee1433dd661a1bce677271a5ebe

---


# AEM案頭應用程式版本注意事項 {#release-notes-v2}

| 產品 | Adobe Experience Manager(AEM)案頭應用程式 |
|---------------|--------------------------------------------------------------------|
| 應用程式版本（修訂版） | 2.0 (2.0.0.4) |
| 支援的AEM版本 | AEM 6.5、AEM 6.4、AEM 6.3（含相容性套件） |
| 類型 | 主要版本 |
| 發行日期 | 2019年8月30日(Mac)、2019年9月9日(Win) |
| 下載URL | [MacOS 64位元](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-osx-2.0.0.4.dmg); [Windows 64位元](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win64-2.0.0.4.exe); [Windows 32位元](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win32-2.0.0.4.exe) |

## 系統需求和先決條件 {#system-requirements-and-prerequisites-v2}

AEM案頭應用程式與下列作業系統相容：

* Mac OS X 10.10或更新版本，以及最新的錯誤修正。
* Windows 7和Windows 10含有最新的Service pack和錯誤修正。

此應用程式可與下列AEM版本搭配使用，不論部署在內部部署或部署在Adobe Managed Services(AMS)上：

* [AEM 6.5.0或更新版本](https://helpx.adobe.com/experience-manager/6-5/release-notes.html)
* [AEM 6.4.4或更新版本](https://helpx.adobe.com/experience-manager/6-4/release-notes/sp-release-notes.html)
* AEM 6.4.0 - 6.4.3與相容套 [件](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)
* AEM 6.3.3.1及更新版本及相容 [套件](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)
* 對於AEM 6.3，不計 [划任何Service Pack](https://helpx.adobe.com/experience-manager/maintenance-releases-roadmap.html)。 Adobe建議升級至更新的AEM版本。

您打算在本機電腦上安裝的應用程式版本需要特定的Adobe Experience Manager伺服器版本／其他伺服器端元件（服務套件、修補程式或功能套件）。 請連絡您的AEM管理員以取得協助。

### 支援不同的資產和檔案類型 {#support-for-file-types}

應用程式支援儲存在AEM中的資產，這些資產代表其基本作業的二進位檔案。 在原生案頭應用程式中開啟檔案時，作業系統會依賴特定檔案類型（例如PNG或JPG）與特定應用程式（例如Mac Preview或Adobe Photoshop）的關聯。

有幾種檔案類型支援將連結資產放入二進位檔。 當使用案頭應用程式開啟這類二進位檔案時，如果資產存在於AEM儲存庫中，應用程式會預先下載連結的資產。 目前支援的檔案類型包括：

* Adobe inDesign檔案（INDD格式）
* Adobe Illustrator檔案（AI格式）
* Adobe Photoshop檔案（PS格式）

上述應用程式的Adobe Creative Cloud 2018和Creative Cloud 2019版本都支援此功能。 應用程式會使用啟發式、最佳比對方法，將連結資產的本機案頭路徑對應至AEM伺服器上的URL。 它依賴一些假設：

* 原生應用程式中置入檔案的路徑使用全域案頭路徑（從本機網路共用置入檔案，顯示「顯示」選項）
* 路徑會由原生應用程式儲存在檔案的XMP記錄中
* AEM已擷取XMP記錄，其路徑是資產的中繼資料記錄
* 路徑可以與AEM中的資產相符（也就是說，置入的檔案也位於AEM中的符合路徑下）

## 新功能和增強功能 {#whats-new-added}

如需詳細資訊，請參 [閱「應用程式的新增功能」](introduction.md#whats-new-v2)。

## 安裝指示 {#installation-instructions-v2}

若要瞭解如何安裝和設定應用程式，請參閱「安 [裝AEM案頭應用程式」](install-upgrade.md)。

如果您要從舊版AEM案頭應用程式升級，您必須依照下列最佳實務進行轉換，這些最佳實務是從舊版 [升級時列出的](install-upgrade.md#upgrade-from-previous-version)。

## 應用程式運作方式的重要附註 {#how-app-works}

請務必瞭解以下應用程式及其運作方式。

* 應用程式可完整控制從AEM到AEM（開啟、編輯、上傳變更和上傳資產）的資產二進位檔完整傳輸作業。
   * 如果您想要在案頭上使用資產，則需要明確地「開啟」、「編輯」或「下載」至案頭，不論是個別、在檔案夾中，或是透過多選項。
   * 如果您想要將資產的本機變更上傳至AEM，您必須個別選 [!UICONTROL Upload Changes]取或透過多選取。
   * 應用程式不是同步案頭和AEM上資產的「同步用戶端」。
   * 應用程式不提供將AEM存放庫對應為虛擬資料夾結構的網路共用。
* 應用程式顯示的資產清單是以AEM Assets存放庫的狀態為基礎。 應用程式不會顯示或管理本機下載並重新命名於本機檔案或快取檔案夾中的任何檔案。
* 如果應用程式未顯示預期的結果，請按一下頂端列中的重新整理圖示。
* 本地網路共用（在您使用操作時顯示） [!UICONTROL Reveal File] 僅顯示本地可用的檔案（和資料夾）。 [!UICONTROL Reveal File] 並預 [!UICONTROL Reveal Folder] 先下載資產，協助取得顯示在本機網路共用中的適當資產。
* 當Adobe Creative cloud應用程式讀取連結／置入Creative cloud應用程式原生檔案中的資產檔案時，會使用SMB(Mac)/WebDAV(Win)本機網路共用。

下圖說明資產和檔案從雲端流向本機檔案系統的流程，反之亦然，如使用者動作所啟動。

![透過案頭應用程式將資產從AEM伺服器流向原生案頭應用程式](assets/do-not-localize/da20_flow_diagram.png)

## Known issues {#known-issues-v2}

**使用者介面問題：**
* 有時，案頭應用程式的介面可能會變成空白。 按一下滑鼠右鍵，然 [!UICONTROL Refresh] 後按一下以再次載入應用程式。 此重新整理會重設應用程式的狀態，而您會從DAM儲存庫根目錄的歡迎畫面開始。 <!-- CQ-4270267 -->
* 在沒有軌跡板或滑鼠滾輪的情況下，很難導覽資料夾／搜尋結果。 沒有滑鼠滾輪的滑鼠裝置可能無法顯示捲軸。 <!-- CQ-4269947 -->
* 上傳資產變更時，進度列不常正確顯示。
* 套用和移除篩選器以尋找所有本機編輯的資產後，應用程式不會將使用者帶至使用者開始使用的搜尋結果或資料夾檢視。 應用程式會顯示DAM儲存庫的根資料夾。
* 當您連線至未執行AEM伺服器的URL時，連線畫面會停止回應。 退出應用程式並重新啟動。

**CRUD（建立、讀取、更新和刪除）問題：**
* 應用程式會嘗試上傳包含無效字元的檔案，這可能會導致伺服器端上傳失敗。 <!-- CQ-4273652 -->
* 當上傳含有註解的變更至資產時，註解會與AEM中的資產一起儲存，但是無法顯示為版本修訂註解（在AEM 6.4.5、6.5.1中解決）。 <!-- CQ-4268990 -->
* 使用者無法取消資產轉讓。 如果您觸發了非預期的大型轉移，請退出應用程式並重新啟動。 <!-- CQ-4278940 -->

**平台問題：**
* 有時，在Windows上，資產的狀態可能會在開啟後立即變 [!UICONTROL Edited Locally] 更為，即使您可能尚未編輯資產。 按一 [!UICONTROL Refresh] 下以更新。

>[!MORELIKETHIS]
>
>* [AEM 6.5檔案](https://helpx.adobe.com/support/experience-manager/6-5.html)
>* [AEM Assets 6.5檔案](https://docs.adobe.com/content/help/en/experience-manager-64/assets/home.html)
>* [使用AEM案頭應用程式](using.md)
>* [安裝和升級案頭應用程式](install-upgrade.md)
>* [最佳實務與疑難排解提示](troubleshoot.md)

