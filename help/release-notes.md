---
title: '[!DNL Adobe Experience Manager] 案頭應用程式發行說明'
description: ' [!DNL Adobe Experience Manager] 案頭應用程式的發行詳細資訊、增強功能、新功能、相容性和下載連結。'
mini-toc-levels: 1
feature: 案頭應用程式，發行資訊
exl-id: e058e7a2-fcc8-4ad1-899e-20695db6bc72
source-git-commit: 56596ade6e7aca5020af6df485289c5902417594
workflow-type: tm+mt
source-wordcount: '1670'
ht-degree: 24%

---

# [!DNL Adobe Experience Manager] 案頭應用程式發行說明 {#release-notes-v2}

最新案頭應用程式2.1版(2.1.3.2)的發行資訊如下。 發行日期為2021年7月19日。

**支援的[!DNL Experience Manager]版本**&#x200B;為：

* [!DNL Experience Manager] as a [!DNL Cloud Service]. 請參閱[發行說明](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/home.html?lang=zh-Hant)。
* [!DNL Experience Manager] 6.5.0或更新版本，位於Adobe Managed Services(AMS)或內部部署。請參閱[Service Pack發行說明](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=zh-Hant)。
* [!DNL Experience Manager] 6.4.4或更新版本，位於Adobe Managed Services(AMS)或內部部署。請參閱[Service Pack發行說明](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/sp-release-notes.html)。
* [!DNL Experience Manager] 6.4.0 - 6.4.3，並安裝在Adobe Managed Services( [](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) AMS)或內部部署上的相容性套件。
* [!DNL Experience Manager] 6.3（包含相容性套件）
* [!DNL Experience Manager] 6.3.3.1或更新版本，並安裝相容 [性套](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) 件。[!DNL Experience Manager] 6.3.3.0或舊版不支援案頭應用程式。

[!DNL Adobe Experience Manager] 案頭應用程式適用於下列 **作業系統**:

* macOS X 10.14或更新版本，並提供最新的錯誤修正。 [尚不支援使](https://support.apple.com/en-us/HT211814) 用Apple硅的Mac電腦。
* Windows 10提供最新的Service Pack和錯誤修正。

支援作業系統的&#x200B;**下載URL**&#x200B;為：

| 作業系統 | [!DNL Experience Manager] as a [!DNL Cloud Service] | [!DNL Experience Manager] 6.x |
|---|---|---|
| macOS(v2.1.3.2) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-osx-2.1.3.2.dmg) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-osx-2.1.3.2.dmg) |
| Windows 64位元(v2.1.3.2) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-win64-2.1.3.2.exe) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win64-2.1.3.2.exe) |
| Windows 32位元(v2.1.3.1) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-win32-2.1.3.1.exe) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win32-2.1.3.1.exe) |

>[!NOTE]
>
>不再支援Windows 7。 請參閱[有關Windows 7的EOL的文章](https://support.microsoft.com/en-us/help/4057281/windows-7-support-ended-on-january-14-2020)。

<!-- The version of the app you plan to install on your local machine requires a specific [!DNL Adobe Experience Manager] server version/additional server-side components (service packs, hot fixes, or feature packs). Contact your [!DNL Experience Manager] administrator for help.
-->

## 支援不同的資產和檔案類型 {#support-for-file-types}

應用程式支援儲存在[!DNL Experience Manager]中的資產，這些資產表示二進位檔案的基本操作。 在原生桌面應用程式中開啟檔案時，需透過作業系統內的特定應用程式（例如 Mac Preview 或 Adobe Photoshop），以特定檔案類型（例如 PNG 或 JPG）開啟。

部分檔案類型支援將連結的資產放入二進位檔。使用案頭應用程式開啟這類二進位檔案時，如果資產存在於[!DNL Experience Manager]存放庫中，應用程式會預先下載連結的資產。 目前支援的檔案類型包括：

* [!DNL Adobe InDesign] 檔案（INDD格式）
* [!DNL Adobe Illustrator] 檔案（AI格式）
* [!DNL Adobe Photoshop] 檔案（PS格式）

上述應用程式的[!DNL Adobe Creative Cloud] 2018和[!DNL Adobe Creative Cloud] 2019版本均支援此功能。 應用程式會使用啟發式、最佳比對方法，將連結資產的本機案頭路徑對應至[!DNL Experience Manager]伺服器上的URL。 依賴的假設如下：

* 本地應用程式中置入檔案的路徑使用全局案頭路徑（從顯示[!UICONTROL Reveal]選項的本地網路共用放置）。

* 透過原生應用程式，將路徑儲存在檔案的 XMP 記錄中.

* [!DNL Experience Manager] 已擷取含有資產中繼資料記錄的 XMP 記錄.

* 路徑可以與[!DNL Experience Manager]中的資產匹配，即放置的檔案也位於[!DNL Experience Manager]中的匹配路徑下。

## 新功能、增強功能和錯誤修正 {#what-is-new}

要了解詳細資訊，請參閱[v2.0](introduction.md#whats-new-v2)中的新功能。

**應用程式v2.1.3.2中的更新**

新版應用程式隨附一些重大修正。

**應用程式v2.1.3.1中的更新**

目前版本修正的錯誤為：

* 即使使用大型資產，資產上傳和下載速度也有所改善。 此版本修正了上傳超大型檔案時，透過[!DNL desktop app]上傳的資產有時會失敗的問題。

**應用程式2.1.2.0版中的更新**

* 應用程式的主功能表中新增了[!UICONTROL Clear Cookies]的新選項。 例如從伺服器變更連線至其他伺服器時，這有助於解決潛在的登入問題。 請參閱[在連接](/help/troubleshoot.md#cannot-login-cookies-issue)之前清除Cookie。

* 新增選項，讓應用程式（若已選取）可上傳資料夾和檔案，使其在[!DNL Adobe Experience Manager]中建立的節點名稱與本機檔案和資料夾名稱相同。

   此行為類似於第1版案頭應用程式中的預設行為。 而在目前版本中，如果未啟用選項，資料夾名稱中的空格和字元`% ; # , + ? ^ { } "`會以資料夾路徑中的破折號取代。 此外，資料夾路徑中的大小寫字元也會轉換為小寫。 但在檔案名中，字元`# % { } ? &`被破折號取代；但空間和外殼都留著。 如需詳細資訊，請參閱[應用程式偏好設定](/help/install-upgrade.md#set-preferences)和[上傳並新增資產](/help/using.md#upload-and-add-new-assets-to-aem)。

**應用程式2.1.1.0版中的更新**

* 進階設定可讓應用程式在上傳資料夾時模擬v1.10應用程式的行為。 在v1.10中，在儲存庫中建立的節點名稱會保留使用者提供的資料夾名稱的空格和大小寫。 v2.1的預設行為仍然相同，亦即在存放庫節點名稱中使用連字型大小取代資料夾名稱中的多個空格，然後轉換為小寫節點名稱。 請參閱[應用程式偏好設定](/help/install-upgrade.md#set-preferences)。

**應用程式2.1.0.0版中的更新**

* 若要上傳資產，使用者現在可以直接從Windows檔案總管或Mac Finder，拖曳應用程式介面上的檔案或資料夾。 除了應用程式中可用的上傳選項外，這個選項也有效。 請參閱[上傳資產](/help/using.md#upload-and-add-new-assets-to-aem) <!-- CQ-4309527 -->

**應用程式v2.0.3中的更新**

此版本修正的錯誤為：

* 修正Windows上應用程式使用者嘗試存取[!DNL Adobe Experience Manager] 6.5.5.0上DAM存放庫時的登入問題。

**應用程式2.0.2版中的更新**

錯誤修正和更新包括：

* 上傳加速設定現已可用來提升上傳效能。 開啟此設定時，使用更多本機CPU執行緒可讓應用程式上傳更快，且耗用的資源也更多。

* 檔案名稱或包含特定GB18030個字元的路徑固定時，即會上傳資產。<!-- CQ-4283494 -->

* 在搜尋結果中切換至其他排序類型後，可使用依關聯性排序選項。<!-- CQ-4286874 -->

* 案頭應用程式現在無需明確重新整理即可列出子資料夾。<!-- CQ-4285711 -->

* (Windows)修正某些Windows電腦上應用程式介面無法使用的罕見問題。 使用者無法點按應用程式介面，因為介面元素的點按區域會以側向方式扭曲。<!-- CQ-4280785 -->

**應用程式v2.0.1中的更新**

錯誤修正和更新包括：

* 允許將`%Temp%`目錄配置為與`%APPDATA%`路徑匹配的選項。<!-- CQ-4282665 -->

* 允許使用者透過Okta SAML驗證登入[!DNL Experience Manager]作者。<!-- CQ-4278134 -->

## 安裝指示 {#installation-instructions-v2}

若要了解如何安裝及設定應用程式，請參閱[安裝 [!DNL Experience Manager] 案頭應用程式](install-upgrade.md)。

如果您要從先前的[!DNL Experience Manager]案頭應用程式進行升級，則必須遵循列於[從舊版](install-upgrade.md#upgrade-from-previous-version)進行升級的這些最佳實務進行轉換。

## 應用程式運作方式的重要附註 {#how-app-works}

請務必瞭解以下關於應用程式及其運作方式的資訊。

* 應用程式可完全控制需要從[!DNL Experience Manager]到完整傳輸資產二進位檔的作業（開啟、編輯、上傳變更和上傳資產）。

   * 如果想在案頭上使用資產，您必須明確地「開啟」、「編輯」或「下載」至案頭，可分別、在資料夾中或透過多選取項目進行。

   * 如果您想要將資產的本機變更上傳至[!DNL Experience Manager]，您需要個別或透過多個選取項目來選取[!UICONTROL Upload Changes]。

   * 應用程式不是跨案頭和[!DNL Experience Manager]同步資產的「同步客戶端」。

   * 應用程式不提供將[!DNL Experience Manager]儲存庫映射為虛擬資料夾結構的網路共用。

* 應用程式顯示的資產清單內容是根據 的資產資料庫。應用程式不會顯示或管理從本機下載、並在本機檔案或快取資料夾中重新命名的任何檔案。

* 如果應用程式未顯示預期的結果，請按一下頂端列中的重新整理圖示。

* 區域網路共享（在您進行 [!UICONTROL Reveal File] 動作時顯示）只會顯示本機可用的檔案（和資料夾）。[!UICONTROL Reveal File] 和 [!UICONTROL Reveal Folder] 會預先下載資產，協助您取得顯示在區域網路共享中的正確資產。

* 當 Adobe Creative cloud 應用程式讀取連結／置於 Creative Cloud 應用程式原生檔案中的資產檔案時，會使用 SMB (Mac)／WebDAV(Win) 區域網路共享。

下圖說明資產和檔案從雲端流向本機檔案系統的流程，以及由使用者動作起始的相反方式。

![[!DNL Experience Manager]透過桌面應用程式，資產從 伺服器移動至原生桌面應用程式](assets/da20_flow_diagram.png)

## 已知問題 {#known-issues-v2}

**使用者介面問題：**

* 有時，案頭應用程式的介面可能會變成空白。 按一下右鍵，然後按一下[!UICONTROL Refresh]以重新載入應用程式。 重新整理後，您就會從DAM存放庫的根目錄開始。 系統會保留資產的更新或狀態。<!-- CQ-4270267 -->

* 在沒有追蹤板或滑鼠指標的情況下，很難導覽資料夾/搜尋結果。 沒有滑鼠滾輪的滑鼠裝置可能無法顯示捲軸。<!-- CQ-4269947 -->

* 少數情況下，當上傳的資產變更時，進度列可能無法顯示正確的進度。

* 在您套用、移除篩選器以尋找所有在本機編輯的資產後，應用程式不會將使用者引導至剛開始的搜尋結果或資料夾檢視。應用程式會顯示 DAM 資料庫的根資料夾。

* 有時，當您連線到未執行[!DNL Experience Manager]伺服器的URL時，連線畫面會停止回應。 請退出應用程式並重新啟動。

**CRUD（建立、讀取、更新和刪除）相關問題：**

* 當上傳含有註解的變更至資產時，註解會與資產一併儲存於[!DNL Experience Manager]中，但無法顯示為版本設定註解。 此問題已在[!DNL Experience Manager] 6.4.5和[!DNL Experience Manager] 6.5.1中解決。Adobe建議安裝最新的Service Pack。<!-- CQ-4268990 -->

* 使用者無法取消資產傳輸。如果您不小心觸發了非預期的大量傳輸，請退出應用程式並重新啟動。<!-- CQ-4278940 -->

**平台問題：**

* 某些時候，即使您可能尚未編輯資產，Windows 上的資產狀態可能會在開啟後立即變更為 [!UICONTROL Edited Locally]。按一下 [!UICONTROL Refresh] 以更新。

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] 文件](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/landing/home.html)
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] [!DNL Assets] 文件](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/home.html)
>* [如何使用 [!DNL Experience Manager] 案頭應用程式](using.md)
* [安裝和升級桌面應用程式](install-upgrade.md)
* [最佳作法與疑難排解提示](troubleshoot.md)

