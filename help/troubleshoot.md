---
title: Adobe Experience Manager案頭應用程式的最佳實務和疑難排解
description: 遵循最佳實務並進行疑難排解，以解決與安裝、升級、設定等相關的偶發問題。
uuid: ce98a3e7-5454-41be-aaaa-4252b3e0f8dd
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.5/ASSETS, SG_EXPERIENCEMANAGER/6.4/ASSETS, SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: f5eb222a-6cdf-4ae3-9cf2-755c873f397c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b4add64df21991495d5cc01e6250bbc9fc444ff0
workflow-type: tm+mt
source-wordcount: '1880'
ht-degree: 0%

---


# Troubleshoot Adobe Experience Manager desktop app {#troubleshoot-v2}

Adobe Experience Manager(AEM)案頭應用程式會連接至遠端Experience Manager部署的數位資產管理(DAM)儲存庫。 應用程式會擷取儲存庫資訊並在您的電腦上搜尋結果、下載和上傳檔案和檔案夾，並包含與AEM Assets使用者介面衝突的管理功能。

閱讀以疑難排解應用程式、瞭解最佳實務，並瞭解限制。

## Best practices {#best-practices-to-prevent-troubles}

遵守下列最佳實務，以防止出現一些常見問題和疑難排解。

* **瞭解案頭應用程式的運作方式**:在開始使用應用程式之前，請花些時間瞭解應用程式的運作方式。 瞭解Experience Manager網頁介面與案頭之間的連結、儲存庫對應、資產快取、本機儲存及在背景上傳。 了 [解運作方式](release-notes.md#how-app-works)。

* **避免資料夾名稱中不支援的字元**:建立或上傳檔案夾時，請勿使用空格和無效字元。 請參閱Experience Manager Assets中建立 [資料夾的字元清單](https://docs.adobe.com/content/help/en/experience-manager-65/assets/managing/managing-assets-touch-ui.html#Creatingfolders)。 有些Adobe Experience Manager使用案例可能會受到檔案夾名稱中不支援的字元影響。

* **避免衝突的最佳實務**:若要避免在協作多個資產時產生潛在衝突，請參 [閱避免編輯衝突](using.md#adv-workflow-collaborate-avoid-conflicts)。

* **對大型、階層式資料夾使用資料夾上傳**:使用Experience Manager案頭應用程式來上傳大型資料夾，而不是使用「資產」網頁介面或其他方法。 應用程式會透過記錄和監控在背景上傳資產。 請參閱 [大量上傳資產](using.md#bulk-upload-assets)。

* **使用最新版本**:使用最新的應用程式版本，在安裝新應用程式版本或升級至較新的Adobe Experience Manager版本之前，請務必先檢查相容性。 請參閱 [發行說明](release-notes.md)。

* **使用相同的驅動器號**:在組織內使用相同的驅動器號來對應至Adobe Experience Manager DAM。 若要查看其他使用者置入的資產，路徑必須相同。 使用相同的驅動器盤符可確保DAM資產的常態路徑。 即使不同的用戶使用不同的驅動器號，這些資產仍會保持放置狀態且不會被移除。

* **注意網路**:網路效能是Experience Manager案頭應用程式效能的關鍵。 如果您遇到檔案傳輸或大量作業的回應速度變慢，請關閉可能導致大量網路流量的功能或應用程式。

* **案頭應用程式不支援的使用案例**:請勿將應用程式用於資產移轉（它需要規劃和其他工具）;執行繁重的DAM作業（例如移動大型資料夾、大型上傳、使用進階中繼資料搜尋尋找檔案）;同步用戶端(設計原則和使用模式與同步用戶端（例如Microsoft OneDrive或Adobe Creative Cloud案頭同步）不同。

* **逾時**:目前，案頭應用程式沒有可設定的逾時值，此值會在固定時間間隔後中斷Experience Manager伺服器與案頭應用程式之間的連線。 上傳大型資產時，如果連線在一段時間後逾時，應用程式會增加上傳逾時，重新嘗試上傳資產幾次。 不建議使用任何方法來變更預設逾時設定。

## 如何疑難排解 {#troubleshooting-prep}

若要疑難排解案頭應用程式問題，請注意下列資訊。 此外，如果您選擇尋求支援，它可讓您更妥善地將問題傳達給Adobe客戶服務。

### 啟用除錯模式 {#enable-debug-mode}

若要疑難排解，您可以啟用除錯模式，並在記錄檔中取得更多資訊。

>[!NOTE]
>
>有效的日誌級別為DEBUG、INFO、WARN或ERROR。 在DEBUG中，日誌的詳細程度最高，在ERROR中則最低。

若要在Mac的除錯模式中使用應用程式：

1. 開啟終端窗口或命令提示符。

1. 執行下列 [!DNL Experience Manager] 命令以啟動案頭應用程式：

   `AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app`。

要在Windows上啟用調試模式，請執行以下操作：

1. 開啟命令窗口。

1. 執行 [!DNL Experience Manager] 下列命令以啟動案頭應用程式：

`AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe`。

### 日誌檔案的位置 {#check-log-files-v2}

[!DNL Experience Manager] 案頭應用程式會根據作業系統，將其記錄檔儲存在下列位置：

在Windows上： `%LocalAppData%\Adobe\AssetsCompanion\Logs`

在Mac上： `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`

上傳許多資產時，如果有些檔案無法上傳，請參 `backend.log` 閱檔案以識別失敗的上傳。

>[!NOTE]
>
>在支援要求或票證上與Adobe客戶服務合作時，可能會要求您共用記錄檔，以協助客戶服務團隊瞭解問題。 封存整個資 `Logs` 料夾，並與您的客戶服務聯絡人共用。

### 清除快取 {#clear-cache-v2}

清除AEM案頭應用程式的快取是一項初步的疑難排解工作，可解決數個問題。 從應用程式偏好設定中清除快取。 請參 [閱設定首選項](install-upgrade.md#set-preferences)。 快取資料夾的預設位置為：

* 在Windows上： `%LocalAppData%\Adobe\AssetsCompanion\Cache\`

* 在Mac上： `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/`

不過，位置會依AEM案頭的設定AEM端點而變更。 值是目標URL的編碼版本。 例如，如果應用程式正在定位， `http://localhost:4502`則目錄名稱為 `http%3A%2F%2Flocalhost%3A4502%2F`。 要清除快取，請刪除相應的資料夾。 清除快取的另一個原因是當磁碟空間不足時釋放磁碟空間。

>[!CAUTION]
>
>如果您清除AEM案頭快取，未同步至AEM伺服器的本機資產修改將無法撤銷。

### 瞭解AEM案頭應用程式版本 {#know-app-version-v2}

按一 ![下「應用程式選單](assets/do-not-localize/more_options_da2.png) 」以開啟應用程式的選單，然後按一下 **[!UICONTROL Help]** > **[!UICONTROL About]**。

### 看不到置入的資產 {#placed-assets-missing}

如果您或其他創意專業人員無法在支援檔案（例如INDD檔案）中看到所放置的資產，請勾選下列項目：

* 連線至伺服器。 不穩定的網路連線可能會拖慢資產下載。
* 檔案大小。 大型資產下載和展示的時間較長。
* 驅動器號的一致性。 如果您或其他共同作業者在將AEM DAM對應至不同的磁碟盤符時置入資產，則不會顯示置入的資產。
* 權限. 若要檢查您是否擁有擷取置入資產的權限，請連絡您的AEM管理員。

### 在macOS上升級時的問題 {#issues-when-upgrading-on-macos}

在macOS上升級AEM案頭應用程式時，偶爾會發生問題。 這是由於AEM案頭應用程式的舊系統資料夾導致無法正確載入新版AEM案頭應用程式。 要解決此問題，可以手動刪除以下資料夾和檔案。

在執行下列步驟之前，請將應用程 `Adobe Experience Manager Desktop` 式從macOS Applications檔案夾拖曳至「垃圾筒」。 然後開啟終端機，執行下列命令，並在出現提示時提供您的密碼。

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

### 無法上傳檔案 {#upload-fails}

如果您正在搭配AEM 6.5.1或更新版本使用案頭應用程式，請將S3或Azure連接器升級至1.10.4或更新版本。 它可解決與 [OAK-8599相關的檔案上傳失敗問題](https://issues.apache.org/jira/browse/OAK-8599)。 請參閱 [安裝指示](install-upgrade.md#install-v2)。

### [!DNL Experience Manager] 案頭應用程式連線問題 {#connection-issues}

如果您遇到一般的連線問題，請以下提供一些方式，以取得有關案頭應用程式 [!DNL Experience Manager] 所執行動作的詳細資訊。

**檢查請求記錄**

[!DNL Experience Manager] 案頭應用程式會將其傳送的所有請求，以及每個請求的回應代碼記錄在專用的記錄檔中。

1. 在應 `request.log` 用程式的記錄目錄中開啟，以檢視這些請求。

1. 記錄中的每一行代表請求或回應。 請求後面會 `>` 有一個字元，後面接有請求的URL。 回應後面會 `<` 有一個字元，後面接著回應程式碼和請求的URL。 請求和回應可使用每行的GUID進行比對。

**檢查應用程式的內嵌瀏覽器載入的請求**

大部分應用程式的請求都位於請求記錄中。 不過，如果沒有有用的資訊，則查看應用程式的內嵌瀏覽器所傳送的要求會很有用。
如需如 [何檢視這些請求的指示](#da-connection-issue-with-saml-aem) ，請參閱SAML區段。

#### SAML登入驗證無法運作 {#da-connection-issue-with-saml-aem}

如果 [!DNL Experience Manager] 案頭應用程式未連線至您啟用SSO(SAML)的例項 [!DNL Adobe Experience Manager] ，請閱讀本節以疑難排解。 SSO程式各異，有時複雜，而應用程式的設計則盡量配合這些連線類型。 不過，有些設定需要額外的疑難排解。

有時SAML程式不會重新導向回原本要求的路徑，或最終的重新導向是與案頭應用程式中設定的主機不 [!DNL Adobe Experience Manager] 同。 要確認情況並非如此：

1. 開啟網頁瀏覽器。

1. 在位址列 `<AEM host>/content/dam.json` 中輸入URL。

   例如， `<AEM host>` 以目標 [!DNL Adobe Experience Manager] 實例替換 `http://localhost:4502/content/dam.json`。

1. 登入實 [!DNL Adobe Experience Manager] 例。

1. 登入完成後，請在位址列中查看瀏覽器的目前位址。 它應完全符合最初輸入的URL。

1. 此外，也請確認所有項目 `/content/dam.json` 在符合案頭應 [!DNL Adobe Experience Manager] 用程式設定 [!DNL Adobe Experience Manager] 中設定的目標值之前。

**登入SAML程式可依照上述步驟正常運作，但使用者仍無法登入**

案頭應用 [!DNL Adobe Experience Manager] 程式中顯示登入程式的視窗只是顯示目標執行個體Web使 [!DNL Adobe Experience Manager] 用者介面的網頁瀏覽器：

* Mac版本使用 [WebView](https://developer.apple.com/documentation/webkit/webview)。

* Windows版本使用Chromium架構的 [CefSharp](https://cefsharp.github.io/)。

請確定SAML程式支援這些瀏覽器。

若要進一步疑難排解，可檢視瀏覽器正嘗試載入的確切URL。 要查看此資訊，請執行以下操作：

1. 請遵循在除錯模式中啟動應用程式 [的指示](#enable-debug-mode)。

1. 重制登錄嘗試。

1. 導覽至應 [用程式的記](#check-log-files-v2) 錄目錄

1. 針對Windows:

   1. 開啟「aemcompanionlog.txt」。

   1. 搜尋以「登入瀏覽器位址變更為」開頭的訊息。 這些項目也包含應用程式載入的URL。

   針對Mac:

   1. `com.adobe.aem.desktop-nnnnnnnn-nnnnnn.log`，其中 **n** 由最新檔案名中的數字替換。

   1. 搜尋以「載入影格」開頭的訊息。 這些項目也包含應用程式載入的URL。


查看正在載入的URL順序有助於在SAML結尾疑難排解，以判斷出錯之處。

#### SSL設定問題 {#ssl-config-v2}

AEM案頭應用程式用於HTTP通訊的程式庫採用嚴格的SSL強制。 有時，連線可能會使用瀏覽器成功，但無法使用AEM案頭應用程式。 若要正確設定SSL，請在Apache中安裝遺失的中間憑證。 請參 [閱如何在Apache中安裝Intemider CA憑證](https://access.redhat.com/solutions/43575)。


AEM Desktop用於HTTP通訊的程式庫都採用嚴格的SSL強制。 因此，有時SSL連線會透過瀏覽器失敗，而案頭應用程式會 [!DNL Adobe Experience Manager] 失敗。 這很好，因為它可促進正確配置SSL並提高安全性，但當應用程式無法連線時，可能會令人沮喪。

在這種情況下，建議的方法是使用工具來分析伺服器的SSL憑證並識別問題，以便加以修正。 有些網站會在提供伺服器URL時檢查伺服器的憑證。

作為一項臨時措施，您可以停用案頭應用程式中嚴格的SSL [!DNL Adobe Experience Manager] 強制執行。 這不是建議的長期解決方案，因為它會隱藏錯誤設定SSL的根本原因，以降低安全性。 要禁用嚴格強制，請執行以下操作：

1. 使用您選擇的編輯器編輯應用程式的JavaScript設定檔案，依預設會在下列位置（視作業系統而定）找到這些檔案：

   在Mac上： `/Applications/Adobe Experience Manager Desktop.app/Contents/Resources/javascript/lib-smb/config.json`

   在Windows上： `C:\Program Files (x86)\Adobe\Adobe Experience Manager Desktop\javascript\config.json`

1. 在檔案中找到下列章節：

   ```shell
   ...
   "assetRepository": {
       "options": {
   ...
   ```

1. 通過添加以下內容來修改 `"strictSSL": false` 該部分：

   ```shell
   ...
   "assetRepository": {
       "options": {
           "strictSSL": false,
   ...
   ```

1. 儲存檔案並重新啟動案頭應 [!DNL Adobe Experience Manager] 用程式。

### 應用程式沒有回應 {#unresponsive}

應用程式很少會停止回應、只顯示白色畫面，或在介面底部顯示錯誤，而介面上沒有任何選項。 請依順序嘗試下列項目：

* 在應用程式介面上按一下滑鼠右鍵，然後按一下 **[!UICONTROL Refresh]**。
* 退出應用程式並再次開啟。

在這兩種方法中，應用程式都會從根DAM檔案夾開始。

>[!MORELIKETHIS]
>
>* [已知問題](release-notes.md#known-issues-v2)
>* [避免編輯衝突](using.md#adv-workflow-collaborate-avoid-conflicts)

