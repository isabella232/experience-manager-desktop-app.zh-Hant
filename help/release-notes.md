---
title: '[!DNL Adobe Experience Manager] 案頭應用發行說明'
description: 發佈詳細資訊、增強功能、新功能、相容性和下載連結 [!DNL Adobe Experience Manager] 案頭應用。
mini-toc-levels: 1
feature: Desktop App,Release Information
exl-id: e058e7a2-fcc8-4ad1-899e-20695db6bc72
source-git-commit: fd89a1ffa06e82f866c614150d1e3fc9b8e07bca
workflow-type: tm+mt
source-wordcount: '1853'
ht-degree: 20%

---

# [!DNL Adobe Experience Manager] 案頭應用發行說明 {#release-notes-v2}

最新案頭應用2.1版(2.1.4.0)的發行資訊如下。 發行日期為2021年12月16日。

的 **支援 [!DNL Experience Manager] 版本** 為：

* [!DNL Experience Manager] as a [!DNL Cloud Service]. 請參閱 [發行說明](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/home.html?lang=zh-Hant)。
* [!DNL Experience Manager] 6.5.0或更新版本，在Adobe Managed Services(AMS)或本地。 請參閱 [服務包發行說明](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=zh-Hant)。
* [!DNL Experience Manager] 6.4.4或更新版本，在Adobe Managed Services(AMS)或本地。 請參閱 [服務包發行說明](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/sp-release-notes.html?lang=zh-Hant)。
* [!DNL Experience Manager] 6.4.0 - 6.4.3 [相容性包](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) 安裝在Adobe Managed Services(AMS)或本地。
* [!DNL Experience Manager] 6.3（帶相容軟體包）
* [!DNL Experience Manager] 6.3.3.1或更高版本 [相容性包](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) 已安裝。 不支援 [!DNL Experience Manager] 6.3.3.0或早期版本。

[!DNL Adobe Experience Manager] 案頭應用可用於以下 **作業系統**:

* macOSX 10.14或更高版本，帶有最新的錯誤修復。 [Mac電腦和Apple硅](https://support.apple.com/en-us/HT211814) 尚不支援。
* Windows 10帶有最新的Service Pack和錯誤修復程式。

的 **下載URL** 支援的作業系統包括：

| 作業系統 | [!DNL Experience Manager] as a [!DNL Cloud Service] | [!DNL Experience Manager] 6.x |
|---|---|---|
| macOS(v2.1.4.0) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-osx-2.1.4.0.dmg) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-osx-2.1.4.0.dmg) |
| Windows 64位(v2.1.4.0) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-win64-2.1.4.0.exe) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win64-2.1.4.0.exe) |
| Windows 32位(v2.1.4.0) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-win32-2.1.4.0.exe) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win32-2.1.4.0.exe) |
| macOS(v2.1.3.4) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-osx-2.1.3.4.dmg) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-osx-2.1.3.4.dmg) |
| Windows 64位(v2.1.3.4) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-win64-2.1.3.4.exe) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win64-2.1.3.4.exe) |
| Windows 32位(v2.1.3.1) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-win32-2.1.3.1.exe) | [下載連結](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win32-2.1.3.1.exe) |

>[!NOTE]
>
>不再支援Windows 7。 請參閱 [關於Windows 7 EOL的文章](https://support.microsoft.com/en-us/help/4057281/windows-7-support-ended-on-january-14-2020)。

## 支援不同的資產和檔案類型 {#support-for-file-types}

應用程式支援儲存在 [!DNL Experience Manager] 表示二進位檔案的基本操作。 在原生桌面應用程式中開啟檔案時，需透過作業系統內的特定應用程式（例如 Mac Preview 或 Adobe Photoshop），以特定檔案類型（例如 PNG 或 JPG）開啟。

部分檔案類型支援將連結的資產放入二進位檔。如果連結的資產存在於 [!DNL Experience Manager] 使用案頭應用開啟此類二進位檔案時的儲存庫。 目前支援的檔案類型包括：

* [!DNL Adobe InDesign] 檔案（INDD格式）
* [!DNL Adobe Illustrator] 檔案（AI格式）
* [!DNL Adobe Photoshop] 檔案（PS格式）

支援該功能 [!DNL Adobe Creative Cloud] 2018年及 [!DNL Adobe Creative Cloud] 版本。 應用使用啟發式、最佳匹配方法將連結資產的本地案頭路徑映射到 [!DNL Experience Manager] 伺服器。 依賴的假設如下：

* 到本地應用程式中放置檔案的路徑使用全局案頭路徑（從顯示為的本地網路共用中放置） [!UICONTROL Reveal] 選項。

* 透過原生應用程式，將路徑儲存在檔案的 XMP 記錄中.

* [!DNL Experience Manager] 已擷取含有資產中繼資料記錄的 XMP 記錄.

* 路徑可以與中的資產匹配 [!DNL Experience Manager]，即，放置的檔案也位於 [!DNL Experience Manager] 在匹配路徑下。

## 新功能、增強功能和錯誤修復 {#what-is-new}

要瞭解詳細資訊，請參閱 [v2.0中的新增功能](introduction.md#whats-new-v2)。

**應用v2.1.4.0中的更新**

新版本的應用程式提供了錯誤修復。

**應用v2.1.3.4中的更新**

新版本的應用程式提供了錯誤修復。

**應用v2.1.3.3中的更新**

新版本的應用程式提供了錯誤修復。

**應用v2.1.3.2中的更新**

此版本的應用程式提供了錯誤修復。

**應用v2.1.3.1中的更新**

此版本中修復的錯誤是：

* 資產上傳和下載速度已經提高，即使是大資產。 此版本解決了資產上載時的問題 [!DNL desktop app] 有時上載非常大的檔案時失敗。

**應用v2.1.2.0中的更新**

* 新選項 [!UICONTROL Clear Cookies] 的子菜單。 它有助於解決潛在的登錄問題，例如，將連接從伺服器更改為其他伺服器時。 請參閱 [在連接前清除Cookie](/help/troubleshoot.md#cannot-login-cookies-issue)。

* 添加一個選項，該選項（如果選中）允許應用上載資料夾和檔案，以便在中建立其節點名 [!DNL Adobe Experience Manager] 與本地檔案和資料夾名稱相同。

   此行為與案頭應用版本1中的預設行為類似。 而在當前版本中，如果未啟用該選項，則空格和字元 `% ; # , + ? ^ { } "` 資料夾名稱中，資料夾路徑中的短划線替換為。 此外，資料夾路徑中的大寫字元會轉換為小寫字元。 但是，在檔案名中， `# % { } ? &` 用划線代替；但白色空間和外殼被保留。 有關詳細資訊，請參閱 [應用首選項](/help/install-upgrade.md#set-preferences) 和 [上載和添加新資產](/help/using.md#upload-and-add-new-assets-to-aem)。

**應用v2.1.1.0中的更新**

* 高級設定允許應用在上載資料夾時模擬v1.10應用行為。 在v1.10中，在儲存庫中建立的節點名稱涉及用戶提供的資料夾名稱的空格和大小寫。 v2.1的預設行為仍然保持不變，即，在儲存庫節點名稱中用連字元替換資料夾名稱中的多個空格，並轉換為小寫節點名稱。 請參閱 [應用首選項](/help/install-upgrade.md#set-preferences)。

**應用v2.1.0.0中的更新**

* 要上載資產，用戶現在可以直接從Windows資源管理器或Mac查找器中拖動應用程式介面上的檔案或資料夾。 除了應用程式中提供的上載選項外，此選項還可用。 請參閱 [上載資產](/help/using.md#upload-and-add-new-assets-to-aem) <!-- CQ-4309527 -->

**應用v2.0.3中的更新**

此版本中修復的錯誤是：

* 已修復Windows上嘗試訪問DAM儲存庫的應用用戶的登錄問題 [!DNL Adobe Experience Manager] 6.5.5.0。

**應用v2.0.2中的更新**

錯誤修復和更新包括：

* 上載加速設定現在可用於提高上載效能。 開啟此設定後，應用會使用更多本地CPU線程以更快的速度上載，並且資源更密集。

* 當包含某些GB18030字元的檔案名或路徑是固定的時，資產上載。 <!-- CQ-4283494 -->

* 切換到搜索結果中的其他排序類型後，「按相關性排序」選項可用。 <!-- CQ-4286874 -->

* 案頭應用現在列出子資料夾，而無需顯式刷新。 <!-- CQ-4285711 -->

* (Windows)修復了某些Windows電腦上不可用的應用程式介面的罕見問題。 用戶無法按一下應用介面，因為介面元素的按一下區域「已轉移」邊向顯示為扭曲。 <!-- CQ-4280785 -->

**應用v2.0.1中的更新**

錯誤修復和更新包括：

* 允許選項配置 `%Temp%` 目錄匹配 `%APPDATA%` 路徑。 <!-- CQ-4282665 -->

* 允許用戶登錄 [!DNL Experience Manager] 通過Okta SAML身份驗證建立。 <!-- CQ-4278134 -->

## 安裝指示 {#installation-instructions-v2}

要瞭解如何安裝和配置應用，請參見 [安裝 [!DNL Experience Manager] 案頭應用](install-upgrade.md)。

如果要從上一個升級 [!DNL Experience Manager] 案頭應用，您必須遵循這些用於轉換的最佳實踐，這些最佳實踐列於 [升級到以前版本](install-upgrade.md#upgrade-from-previous-version)。

## 應用程式運作方式的重要附註 {#how-app-works}

請務必瞭解以下關於應用程式及其運作方式的資訊。

* 該應用程式提供對需要從資產二進位檔案向和向資產二進位檔案的完全傳輸的操作的完全控制 [!DNL Experience Manager] （開啟、編輯、上載更改和上載資產）。

   * 如果要在案頭上使用資產，必須分別、在資料夾中或通過多選擇顯式開啟、編輯或下載到案頭。

   * 如果要獲取上載到的資產的本地更改 [!DNL Experience Manager]，需要選擇 [!UICONTROL Upload Changes]，可單獨或通過多選。

   * 應用程式不是在案頭上同步資產的「同步客戶端」， [!DNL Experience Manager]。

   * 應用程式不提供映射 [!DNL Experience Manager] 儲存庫作為虛擬資料夾結構。

* 應用程式顯示的資產清單內容是根據 的資產資料庫。應用程式不會顯示或管理從本機下載、並在本機檔案或快取資料夾中重新命名的任何檔案。

* 如果應用程式未顯示預期的結果，請按一下頂端列中的重新整理圖示。

* 區域網路共享（在您進行 [!UICONTROL Reveal File] 動作時顯示）只會顯示本機可用的檔案（和資料夾）。[!UICONTROL Reveal File] 和 [!UICONTROL Reveal Folder] 會預先下載資產，協助您取得顯示在區域網路共享中的正確資產。

* 當 Adobe Creative cloud 應用程式讀取連結／置於 Creative Cloud 應用程式原生檔案中的資產檔案時，會使用 SMB (Mac)／WebDAV(Win) 區域網路共享。

下圖說明了資產和檔案從雲到本地檔案系統的流程，以及由用戶操作啟動的相反方式。

![[!DNL Experience Manager]透過桌面應用程式，資產從 伺服器移動至原生桌面應用程式](assets/da20_flow_diagram.png)

## 已知問題 {#known-issues-v2}

**使用者介面問題：**

* 有時，案頭應用的介面可能變為空白。 按一下右鍵並按一下 [!UICONTROL Refresh] 重新載入應用程式。 刷新後，從DAM儲存庫的根開始。 保留資產的更新或狀態。 <!-- CQ-4270267 -->

* 在沒有跟蹤板或滑鼠指針的情況下，很難導航資料夾/搜索結果。 沒有滑鼠滾輪的滑鼠設備可能不會出現捲動條。 <!-- CQ-4269947 -->

* 少數情況下，當上傳的資產變更時，進度列可能無法顯示正確的進度。

* 在您套用、移除篩選器以尋找所有在本機編輯的資產後，應用程式不會將使用者引導至剛開始的搜尋結果或資料夾檢視。應用程式會顯示 DAM 資料庫的根資料夾。

* 有時，當您連接到沒有 [!DNL Experience Manager] 伺服器運行時，連接螢幕無響應。 請退出應用程式並重新啟動。

**CRUD（建立、讀取、更新和刪除）相關問題：**

* 將更改上載到帶有注釋的資產時，注釋與資產一起儲存在 [!DNL Experience Manager] 但作為版本化注釋不可見。 此問題已在 [!DNL Experience Manager] 6.4.5和 [!DNL Experience Manager] 6.5.1。Adobe建議安裝最新的Service Pack。 <!-- CQ-4268990 -->

* 使用者無法取消資產傳輸。如果您不小心觸發了非預期的大量傳輸，請退出應用程式並重新啟動。<!-- CQ-4278940 -->

**平台問題：**

* 某些時候，即使您可能尚未編輯資產，Windows 上的資產狀態可能會在開啟後立即變更為 [!UICONTROL Edited Locally]。按一下 [!UICONTROL Refresh] 以更新。

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] 文件](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/landing/home.html)
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] [!DNL Assets] 文件](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/home.html)
>* [如何使用 [!DNL Experience Manager] 案頭應用](using.md)
>* [安裝和升級桌面應用程式](install-upgrade.md)
>* [最佳作法與疑難排解提示](troubleshoot.md)

