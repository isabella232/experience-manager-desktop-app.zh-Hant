---
title: ' [!DNL Adobe Experience Manager] 案頭應用程式的最佳作法和疑難排解'
description: 請依照最佳實務和疑難排解，解決與安裝、升級、設定等相關的偶發問題。
exl-id: f388e4ac-907d-4093-ba6f-86ecdafeb015
source-git-commit: 2c846fb9cd82691f6439e93429dffcca8127ba68
workflow-type: tm+mt
source-wordcount: '2260'
ht-degree: 0%

---

# 疑難排解[!DNL Adobe Experience Manager]案頭應用程式 {#troubleshoot-v2}

[!DNL Adobe Experience Manager] 案頭應用程式會連 [!DNL Experience Manager] 線至部署的數位資產管理(DAM)存放庫。應用程式會擷取電腦上的存放庫資訊和搜尋結果、下載及上傳檔案和資料夾，並包含管理與Assets使用者介面衝突的功能。

閱讀以疑難排解應用程式、了解最佳實務，並了解限制。

## 最佳實務 {#best-practices-to-prevent-troubles}

請遵循下列最佳實務，以防止發生一些常見問題和疑難排解。

* **了解案頭應用程式的運作方式**:開始使用應用程式之前，請先花些時間了解應用程式的運作方式。了解[!DNL Experience Manager] Web介面與案頭、存放庫對應、資產快取、本機儲存及背景上傳之間的連結。 請參閱[其運作方式](release-notes.md#how-app-works)。

* **避免資料夾名稱中不支援的字元**:建立或上傳資料夾時，請勿使用空格和無效字元。請參閱[在 [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#creating-folders)中建立資料夾中的字元清單。 資料夾名稱中不支援的字元可能會影響某些[!DNL Experience Manager]使用案例。

* **避免衝突的最佳實務**:若要避免協作多個資產時產生潛在衝突，請參閱 [避免編輯衝突](using.md#adv-workflow-collaborate-avoid-conflicts)。

* **將資料夾上傳用於大型的階層式資料夾**:使用案頭應用程式來上傳大型資料夾，而不 [!DNL Experience Manager] 使用Assets網頁介面或其他方法。應用程式會透過記錄和監控在背景上傳資產。 請參閱[大量上傳資產](using.md#bulk-upload-assets)。

* **使用最新版本**:使用最新應用程式版本，在安裝新應用程式版本或升級至更新版本之前，請務必檢查相容性 [!DNL Experience Manager] 問題。請參閱[發行說明](release-notes.md)。

* **使用相同的驅動器號**:在組織內使用相同的驅動器號來對應至 [!DNL Experience Manager] DAM。若要查看其他使用者放置的資產，路徑必須相同。 使用相同的驅動器號可確保DAM資產的路徑一致。 即使不同的使用者使用不同的驅動器號，資產仍會保持放置狀態且不會被移除。

* **留意網路**:網路效能對案頭應 [!DNL Experience Manager] 用的效能至關重要。如果您面臨檔案傳輸或批量操作響應速度慢的問題，請關閉可能導致大量網路流量的功能或應用。

* **案頭應用程式不支援的使用案例**:請勿將應用程式用於資產移轉（需要規劃和其他工具）;（例如移動大型資料夾、大型上傳、使用進階中繼資料搜尋尋找檔案）;作為同步客戶端(設計原則和使用模式與同步客戶端(如Microsoft OneDrive或Adobe Creative Cloud案頭同步)不同。

* **逾時**:目前，案頭應用程式沒有可設定的逾時值，該逾時值會在固定時間間隔後 [!DNL Experience Manager] 中斷伺服器與案頭應用程式之間的連線。上傳大型資產時，如果連線在一段時間後逾時，應用程式會增加上傳逾時，以重試幾次來上傳資產。 建議不要變更預設逾時設定。

## 疑難排解 {#troubleshooting-prep}

若要疑難排解案頭應用程式問題，請注意下列資訊。 此外，如果您選擇尋求支援，還可讓您更妥善地向Adobe客戶支援傳達問題。

### 日誌檔案的位置 {#check-log-files-v2}

[!DNL Experience Manager] 案頭應用程式會根據作業系統將其記錄檔儲存在下列位置：

在Windows上：`%LocalAppData%\Adobe\AssetsCompanion\Logs`

在Mac:`~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`

上傳許多資產時，如果某些檔案無法上傳，請參閱`backend.log`檔案以識別上傳失敗。

>[!NOTE]
>
>在處理支援請求或票證上的Adobe客戶支援時，可要求您共用記錄檔，以協助客戶支援團隊了解問題。 封存整個`Logs`資料夾，並與您的客戶支援連絡人共用。

### 更改日誌檔案中的詳細資訊級別 {#level-of-details-in-log}

要更改日誌檔案中的詳細資訊級別：

1. 確保應用程式未運行。

1. 在Windows系統上：

   1. 開啟命令窗口。

   1. 運行命令啟動[!DNL Adobe Experience Manager]案頭應用：

   ```shell
   set AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe
   ```

   在Mac系統上：

   1. 開啟終端窗口。

   1. 運行命令啟動[!DNL Adobe Experience Manager]案頭應用：

   ```shell
   AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app
   ```

有效的日誌級別為「調試」、「資訊」、「警告」或「錯誤」。 在DEBUG中記錄的詳細程度最高，在ERROR中最低。

### 啟用偵錯模式 {#enable-debug-mode}

若要進行疑難排解，您可以啟用除錯模式，並在記錄檔中取得詳細資訊。

>[!NOTE]
>
>有效的日誌級別為「調試」、「資訊」、「警告」或「錯誤」。 在DEBUG中記錄的詳細程度最高，在ERROR中最低。

若要在Mac上以除錯模式使用應用程式：

1. 開啟終端窗口或命令提示符。

1. 運行以下命令啟動[!DNL Experience Manager]案頭應用：

   `AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app`。

要在Windows上啟用調試模式，請執行以下操作：

1. 開啟命令窗口。

1. 運行以下命令啟動[!DNL Experience Manager]案頭應用：

`AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe`。

### 了解[!DNL Adobe Experience Manager]案頭應用程式版本 {#know-app-version-v2}

若要查看版本號碼：

1. 啟動應用程式。

1. 按一下右上角的點，將游標暫留在[!UICONTROL Help]上，然後按一下[!UICONTROL About]。

   此螢幕上列出了版本號。

### 清除快取 {#clear-cache-v2}

執行下列步驟：

1. 啟動應用程式並連接[!DNL Experience Manager]實例。

1. 按一下右上角的點並選取[!UICONTROL Preferences]，開啟應用程式的偏好設定。

1. 找到顯示[!UICONTROL Current Cache Size]的條目。 按一下此元素旁的垃圾桶圖示。

若要手動清除快取，請繼續下列步驟。

>[!CAUTION]
>
>這是一種潛在的破壞性操作。 如果有未上傳到[!DNL Adobe Experience Manager]的本地檔案更改，則繼續操作將丟失這些更改。

通過刪除應用程式的快取目錄來清除快取，該目錄在應用程式的首選項中找到。

1. 啟動應用程式。

1. 選擇右上角的點並選擇[!UICONTROL Preferences]以開啟應用程式的首選項。

1. 記下[!UICONTROL Cache Directory]值。

   在此目錄中，有以「編碼[!DNL Adobe Experience Manager]端點」命名的子目錄。 名稱是目標[!DNL Adobe Experience Manager] URL的編碼版本。 例如，如果應用程式正在定位`localhost:4502` ，則目錄名稱將為`localhost_4502`。

若要清除快取，請刪除所需的Encoded [!DNL Adobe Experience Manager] Endpoint目錄。 或者，刪除首選項中指定的整個目錄將清除應用程式已使用的所有實例的快取。

清除[!DNL Adobe Experience Manager]案頭應用程式的快取是一項初步的疑難排解任務，可解決數個問題。 從應用程式偏好設定中清除快取。 請參閱[設定偏好設定](install-upgrade.md#set-preferences)。 快取資料夾的預設位置為：

## 看不到已放置的資產 {#placed-assets-missing}

如果您看不到支援檔案（如INDD檔案）中放置的資產，請檢查以下內容：

* 連接到伺服器。 不穩定的網路連接可能會阻礙資產下載。

* 檔案大小。 大型資產的下載和顯示時間會更長。

* 驅動器號一致性。 如果您或其他合作者在將[!DNL Experience Manager] DAM對應至不同的驅動器號時放置了資產，則放置的資產不會顯示。

* 權限. 若要檢查您是否擁有擷取已放置資產的權限，請聯絡您的[!DNL Experience Manager]管理員。

### 對案頭應用程式用戶介面上檔案的編輯不會立即反映在[!DNL Adobe Experience Manager]中 {#changes-on-da-not-visible-on-aem}

[!DNL Adobe Experience Manager] 案頭應用程式讓使用者自行決定檔案的所有編輯作業何時完成。根據檔案的大小和複雜性，將新版本的檔案傳回[!DNL Adobe Experience Manager]需要相當長的時間。 應用程式的設計要求將檔案往返傳輸的次數減到最少，而不是猜測檔案編輯完成並自動上傳的時間。 建議用戶通過選擇上傳檔案的更改來開始將檔案傳回[!DNL Adobe Experience Manager]。

### 在macOS上升級時發生的問題 {#issues-when-upgrading-on-macos}

在macOS上升級[!DNL Experience Manager]案頭應用程式時，偶爾會發生問題。 這是由於[!DNL Experience Manager]案頭應用程式的舊系統資料夾導致新版本的[!DNL Experience Manager]案頭應用程式無法正確載入所致。 若要解決此問題，可以手動移除下列資料夾和檔案。

執行下列步驟之前，請將`Adobe Experience Manager Desktop`應用程式從macOS應用程式資料夾拖曳至垃圾桶。 然後開啟終端機，執行下列命令，並在出現提示時提供您的密碼。

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## 無法上載檔案 {#upload-fails}

如果您使用的案頭應用程式搭配[!DNL Experience Manager] 6.5.1或更新版本，請將S3或Azure連接器升級至1.10.4或更新版本。 它可解決與[OAK-8599](https://issues.apache.org/jira/browse/OAK-8599)相關的檔案上傳失敗問題。 請參閱[安裝指示](install-upgrade.md#install-v2)。

## [!DNL Experience Manager] 案頭應用程式連線問題 {#connection-issues}

如果您遇到一般連接問題，以下提供一些方法，以取得有關[!DNL Experience Manager]案頭應用程式正在執行的操作的詳細資訊。

**檢查請求記錄**

[!DNL Experience Manager] 案頭應用程式會將其傳送的所有請求，連同每個請求的回應代碼，記錄在專用的記錄檔中。

1. 在應用程式的日誌目錄中開啟`request.log`以查看這些請求。

1. 記錄中的每一行代表要求或回應。 要求後面會有`>`字元，後面接著要求的URL。 回應將會有`<`字元，後面接著回應代碼和要求的URL。 可使用每行的GUID來比對要求和回應。

**檢查應用程式的內嵌瀏覽器載入的請求**

大部分應用程式的要求都可在要求記錄中找到。 不過，如果其中沒有實用的資訊，則查看應用程式的內嵌瀏覽器所傳送的請求會很有幫助。
如需如何檢視這些要求的指示，請參閱[SAML區段](#da-connection-issue-with-saml-aem)。

### SAML登入驗證無法運作 {#da-connection-issue-with-saml-aem}

[!DNL Experience Manager] 案頭應用程式可能無法連線至您啟用SSO(SAML)的部 [!DNL Adobe Experience Manager] 署。應用程式的設計嘗試適應SSO連接和過程的變化和複雜性。 不過，設定可能需要進行其他疑難排解。

有時SAML程式不會重新導向回原本請求的路徑，或最終的重新導向是與[!DNL Adobe Experience Manager]案頭應用程式中所設定的不同的主機。 若要確認情況並非如此：

1. 開啟網頁瀏覽器。 訪問`https://[aem_server]:[port]/content/dam.json` URL。

1. 登錄[!DNL Adobe Experience Manager]部署。

1. 登入完成後，請在位址列中查看瀏覽器的目前位址。 它應完全符合最初輸入的URL。

1. 同時確認`/content/dam.json`之前的所有項目都符合[!DNL Adobe Experience Manager]案頭應用程式設定中設定的目標[!DNL Adobe Experience Manager]值。

**依照上述步驟，登入SAML程式可正常運作，但使用者仍無法登入**

[!DNL Adobe Experience Manager]案頭應用程式中顯示登錄進程的窗口只是顯示目標[!DNL Adobe Experience Manager]實例的Web用戶介面的Web瀏覽器：

* Mac版本使用[WebView](https://developer.apple.com/documentation/webkit/webview)。

* Windows版本使用基於Chromium的[CefSharp](https://cefsharp.github.io/)。

確保SAML程式支援這些瀏覽器。

若要進一步疑難排解，您可以檢視瀏覽器嘗試載入的確切URL。 若要查看此資訊：

1. 按照[調試模式](#enable-debug-mode)中啟動應用程式的指示操作。

1. 重制登錄嘗試。

1. 導覽至應用程式的[記錄目錄](#check-log-files-v2)

1. 對於Windows:

   1. 開啟「aemcompanionlog.txt」。

   1. 搜尋以「登入瀏覽器位址已變更為」開頭的訊息。 這些項目也包含應用程式載入的URL。

   若為Mac:

   1. `com.adobe.aem.desktop-nnnnnnnn-nnnnnn.log`，其中n **** 會取代為最新檔案名稱中的任何數字。

   1. 搜尋以「已載入幀」開頭的訊息。 這些項目也包含應用程式載入的URL。


查看正在載入的URL序列，有助於在SAML結尾進行疑難排解，以判斷錯誤。

### SSL設定問題 {#ssl-config-v2}

[!DNL Experience Manager]案頭應用程式用於HTTP通訊的程式庫採用嚴格的SSL強制。 有時，連線可能使用瀏覽器成功，但使用[!DNL Experience Manager]案頭應用程式失敗。 若要適當設定SSL，請在Apache中安裝遺漏的中繼憑證。 請參閱[如何在Apache](https://access.redhat.com/solutions/43575)中安裝中繼CA憑證。

[!DNL Experience Manager]案頭應用程式用於HTTP通訊的程式庫採用嚴格的SSL強制。 因此，在某些情況下，當[!DNL Adobe Experience Manager]案頭應用程式透過瀏覽器成功執行的SSL連線可能會失敗。 這很好，因為它有助於正確配置SSL並提高安全性，但當應用程式無法連線時，可能會令人沮喪。

在此情況下，建議的方法是使用工具來分析伺服器的SSL憑證並識別問題，以便加以修正。 有些網站會檢查伺服器的憑證以提供其URL。

作為暫時措施，您可以在[!DNL Adobe Experience Manager]案頭應用程式中停用嚴格的SSL強制執行。 這不是建議的長期解決方案，因為它隱藏了錯誤設定SSL的根本原因，因而降低了安全性。 要禁用嚴格強制：

1. 使用您選擇的編輯器編輯應用程式的JavaScript配置檔案，該檔案（預設情況下）位於以下位置（取決於作業系統）:

   在Mac:`/Applications/Adobe Experience Manager Desktop.app/Contents/Resources/javascript/lib-smb/config.json`

   在Windows上：`C:\Program Files (x86)\Adobe\Adobe Experience Manager Desktop\javascript\config.json`

1. 在檔案中找到下列區段：

   ```shell
   ...
   "assetRepository": {
       "options": {
   ...
   ```

1. 按如下所示添加`"strictSSL": false`以修改節：

   ```shell
   ...
   "assetRepository": {
       "options": {
           "strictSSL": false,
   ...
   ```

1. 保存檔案並重新啟動[!DNL Adobe Experience Manager]案頭應用。

### 切換至其他伺服器時發生登入問題 {#cannot-login-cookies-issue}

使用[!DNL Experience Manager]伺服器後，當您嘗試變更與其他伺服器的連線時，可能會遇到登入問題。 這是因為舊Cookie干擾新驗證。 主功能表中的[!UICONTROL Clear Cookies]選項有幫助。 登出應用程式中的當前會話，然後選擇[!UICONTROL Clear Cookies]，再繼續連接。

![切換伺服器時清除Cookie](assets/main_menu_logout_da2.png)

## 應用程式無反應 {#unresponsive}

應用程式很少會停止響應、只顯示白屏，或在介面底部顯示錯誤，而介面上沒有任何選項。 請依順序嘗試下列項目：

* 按一下右鍵應用程式介面，然後按一下&#x200B;**[!UICONTROL Refresh]**。
* 退出應用程式並再次開啟。

在這兩種方法中，應用程式都會從根DAM資料夾啟動。

## 隱藏過期的資產 {#hide-expired-assets}

從[!DNL Experience Manager]使用者介面內瀏覽資產時，不會顯示過期的資產。 若要防止從案頭應用程式和「資產連結」瀏覽資產時檢視、搜尋及擷取過期的資產，管理員可以執行下列設定。 此配置適用於所有用戶，而不考慮管理員權限。

* [Experience Manager6.5中的設定，以隱藏過期的資產](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#hide-expired-assets-via-acp-api)。
* [以Experience Manageras a Cloud Service進行設定，以隱藏過期的資產](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/manage-digital-assets.html#hide-expired-assets-via-acp-api)。

<!--
### Need additional help with [!DNL Experience Manager] desktop app {#additional-help}

Create Jira ticket with the following information:

* Use `DAM - Companion App` as the [!UICONTROL Component].

* Detailed steps to reproduce the issue in [!UICONTROL Description].

* DEBUG level logs that were captured while reproducing the issue.

* Target Experience Manager version.

* Operating system version.

* [!DNL Adobe Experience Manager] desktop app version. To know your app version, see [finding the desktop app version](#know-app-version-v2).
-->

>[!MORELIKETHIS]
>
>* [已知問題](release-notes.md#known-issues-v2)
>* [避免編輯衝突](using.md#adv-workflow-collaborate-avoid-conflicts)

