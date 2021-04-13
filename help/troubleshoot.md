---
title: '案頭應用程式的最佳實務與疑難排解 [!DNL Adobe Experience Manager] '
description: 遵循最佳實務並進行疑難排解，以解決與安裝、升級、設定等相關的偶發問題。
exl-id: f388e4ac-907d-4093-ba6f-86ecdafeb015
translation-type: tm+mt
source-git-commit: b893ad24d360ed382cab50771413219ea7bda09e
workflow-type: tm+mt
source-wordcount: '2261'
ht-degree: 0%

---

# 疑難排解[!DNL Adobe Experience Manager]案頭應用程式{#troubleshoot-v2}

[!DNL Adobe Experience Manager] 案頭應用程式會連 [!DNL Experience Manager] 線至部署的數位資產管理(DAM)儲存庫。應用程式會擷取儲存庫資訊並在您的電腦上搜尋結果、下載和上傳檔案和檔案夾，並包含管理與「資產」使用者介面衝突的功能。

閱讀以疑難排解應用程式、瞭解最佳實務，並瞭解限制。

## 最佳做法{#best-practices-to-prevent-troubles}

遵守下列最佳實務，以防止出現一些常見問題和疑難排解。

* **瞭解案頭應用程式的運作方式**:在開始使用應用程式之前，請花些時間瞭解應用程式的運作方式。瞭解[!DNL Experience Manager]網頁介面與案頭、資料庫對應、資產快取、本機儲存與背景上傳之間的連結。 請參閱[其運作方式](release-notes.md#how-app-works)。

* **避免資料夾名稱中不支援的字元**:建立或上傳檔案夾時，請勿使用空格和無效字元。請參閱[ [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#creating-folders)中的「建立資料夾」中的字元清單。 某些[!DNL Experience Manager]使用案例可能會受到資料夾名稱中不支援的字元影響。

* **避免衝突的最佳實務**:若要避免在協作多個資產時產生潛在衝突，請參 [閱避免編輯衝突](using.md#adv-workflow-collaborate-avoid-conflicts)。

* **對大型、階層式資料夾使用資料夾上傳**:使用案頭應用程式來上傳大型資料夾，而不是使用「資產」 [!DNL Experience Manager] 網頁介面或其他方法。應用程式會透過記錄和監控在背景上傳資產。 請參閱[大量上傳資產](using.md#bulk-upload-assets)。

* **使用最新版本**:使用最新的應用程式版本，在安裝新應用程式版本或升級至較新版本之前，請務必先檢查相容 [!DNL Experience Manager] 性。請參閱[發行說明](release-notes.md)。

* **使用相同的驅動器號**:在組織內使用相同的驅動器盤符來映射 [!DNL Experience Manager] DAM。若要查看其他使用者置入的資產，路徑必須相同。 使用相同的驅動器盤符可確保DAM資產的常態路徑。 即使不同的用戶使用不同的驅動器號，這些資產仍會保持放置狀態且不會被移除。

* **注意網路**:網路效能是案頭應 [!DNL Experience Manager] 用程式效能的關鍵。如果您遇到檔案傳輸或大量作業的回應速度變慢，請關閉可能導致大量網路流量的功能或應用程式。

* **案頭應用程式不支援的使用案例**:請勿將應用程式用於資產移轉（它需要規劃和其他工具）;執行繁重的DAM作業（例如移動大型資料夾、大型上傳、使用進階中繼資料搜尋尋找檔案）;同步客戶端(設計原則和使用模式與同步客戶端(如Microsoft OneDrive或Adobe Creative Cloud案頭同步)不同。

* **逾時**:目前，案頭應用程式沒有可設定的逾時值，在固定時間間隔後，會 [!DNL Experience Manager] 中斷伺服器與案頭應用程式之間的連線。上傳大型資產時，如果連線在一段時間後逾時，應用程式會增加上傳逾時，重新嘗試上傳資產幾次。 不建議使用任何方法來變更預設逾時設定。

## 如何疑難排解{#troubleshooting-prep}

若要疑難排解案頭應用程式問題，請注意下列資訊。 此外，如果您選擇尋求支援，它可讓您更妥善地將問題傳達給Adobe客戶服務。

### 日誌檔案{#check-log-files-v2}的位置

[!DNL Experience Manager] 案頭應用程式會根據作業系統，將其記錄檔儲存在下列位置：

在Windows上：`%LocalAppData%\Adobe\AssetsCompanion\Logs`

在Mac上：`~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`

上傳許多資產時，如果有些檔案無法上傳，請參閱`backend.log`檔案以識別失敗的上傳。

>[!NOTE]
>
>與Adobe客戶服務合作時，若需支援請求或票證，您會被要求共用記錄檔，以協助客戶服務團隊瞭解問題。 封存整個`Logs`資料夾，並與您的客戶服務聯絡人共用。

### 更改日誌檔案{#level-of-details-in-log}中的詳細資訊級別

要更改日誌檔案中的詳細資訊級別：

1. 確保應用程式未運行。

1. 在Windows系統上：

   1. 開啟命令窗口。

   1. 運行命令啟動[!DNL Adobe Experience Manager]案頭應用程式：

   ```shell
   set AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe
   ```

   在Mac系統上：

   1. 開啟終端窗口。

   1. 運行命令啟動[!DNL Adobe Experience Manager]案頭應用程式：

   ```shell
   AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app
   ```

有效的日誌級別為DEBUG、INFO、WARN或ERROR。 在DEBUG中，日誌的詳細程度最高，在ERROR中則最低。

### 啟用調試模式{#enable-debug-mode}

若要疑難排解，您可以啟用除錯模式，並在記錄檔中取得更多資訊。

>[!NOTE]
>
>有效的日誌級別為DEBUG、INFO、WARN或ERROR。 在DEBUG中，日誌的詳細程度最高，在ERROR中則最低。

若要在Mac的除錯模式中使用應用程式：

1. 開啟終端窗口或命令提示符。

1. 執行下列命令以啟動[!DNL Experience Manager]案頭應用程式：

   `AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app`。

要在Windows上啟用調試模式，請執行以下操作：

1. 開啟命令窗口。

1. 執行下列命令以啟動[!DNL Experience Manager]案頭應用程式：

`AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe`。

### 瞭解[!DNL Adobe Experience Manager]案頭應用程式版本{#know-app-version-v2}

要查看版本號：

1. 啟動應用程式。

1. 按一下右上角的橢圓，將滑鼠指標暫留在[!UICONTROL Help]上，然後按一下[!UICONTROL About]。

   此畫面上會列出版本號碼。

### 清除快取 {#clear-cache-v2}

執行以下步驟：

1. 啟動應用程式並連接[!DNL Experience Manager]實例。

1. 按一下右上角的橢圓並選擇[!UICONTROL Preferences]以開啟應用程式的首選項。

1. 找到顯示[!UICONTROL Current Cache Size]的條目。 按一下此元素旁的垃圾桶圖示。

要手動清除快取，請繼續以下步驟。

>[!CAUTION]
>
>這是一項具有潛在破壞性的操作。 如果有未上傳至[!DNL Adobe Experience Manager]的本機檔案變更，則這些變更將因繼續而遺失。

通過刪除應用程式的快取目錄（在應用程式的首選項中）來清除快取。

1. 啟動應用程式。

1. 通過選擇右上角的橢圓並選擇[!UICONTROL Preferences]來開啟應用程式的首選項。

1. 請注意[!UICONTROL Cache Directory]值。

   在此目錄中，有以「編碼[!DNL Adobe Experience Manager]端點」命名的子目錄。 名稱是目標[!DNL Adobe Experience Manager] URL的編碼版本。 例如，如果應用程式鎖定`localhost:4502`，則目錄名稱將為`localhost_4502`。

要清除快取，請刪除所需的編碼[!DNL Adobe Experience Manager]端點目錄。 或者，刪除首選項中指定的整個目錄將清除應用程式已使用的所有實例的快取。

清除[!DNL Adobe Experience Manager]案頭應用程式的快取是一項初步的疑難排解工作，可解決數個問題。 從應用程式偏好設定中清除快取。 請參閱[設定首選項](install-upgrade.md#set-preferences)。 快取資料夾的預設位置為：

## 無法看到置入的資產{#placed-assets-missing}

如果您或其他創意專業人員無法在支援檔案（例如INDD檔案）中看到所放置的資產，請勾選下列項目：

* 連線至伺服器。 不穩定的網路連線可能會拖慢資產下載。

* 檔案大小。 大型資產下載和展示的時間較長。

* 驅動器號的一致性。 如果您或其他合作夥伴在將[!DNL Experience Manager] DAM對應至不同的驅動器盤符時置入資產，則不會顯示置入的資產。

* 權限. 若要檢查您是否擁有擷取置入資產的權限，請連絡您的[!DNL Experience Manager]管理員。

### 案頭應用程式使用者介面上檔案的編輯無法立即反映在[!DNL Adobe Experience Manager]中{#changes-on-da-not-visible-on-aem}

[!DNL Adobe Experience Manager] 案頭應用程式讓使用者自行決定檔案的所有編輯何時完成。根據檔案的大小和複雜性，將新版本的檔案傳輸回[!DNL Adobe Experience Manager]需要大量時間。 應用程式的設計要求將檔案來回傳輸的次數減到最少，而不是猜測檔案編輯完成並自動上傳的時間。 建議用戶通過選擇上傳檔案的更改來啟動檔案傳回[!DNL Adobe Experience Manager]。

### 在macOS上升級時的問題{#issues-when-upgrading-on-macos}

在macOS上升級[!DNL Experience Manager]案頭應用程式時，偶爾會發生問題。 這是由於[!DNL Experience Manager]案頭應用程式的舊系統資料夾導致無法正確載入新版[!DNL Experience Manager]案頭應用程式。 要解決此問題，可以手動刪除以下資料夾和檔案。

在執行下列步驟之前，請將`Adobe Experience Manager Desktop`應用程式從macOS Applications檔案夾拖曳至「垃圾筒」。 然後開啟終端機，執行下列命令，並在出現提示時提供您的密碼。

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## 無法上傳檔案{#upload-fails}

如果您使用的案頭應用程式與[!DNL Experience Manager] 6.5.1或更新版本相同，請將S3或Azure連接器升級至1.10.4或更新版本。 它可解決與[OAK-8599](https://issues.apache.org/jira/browse/OAK-8599)相關的檔案上傳失敗問題。 請參閱[安裝說明](install-upgrade.md#install-v2)。

## [!DNL Experience Manager] 案頭應用程式連線問題  {#connection-issues}

如果您遇到一般連接問題，請以下提供一些方法，以取得有關[!DNL Experience Manager]案頭應用程式所執行動作的詳細資訊。

**檢查請求記錄**

[!DNL Experience Manager] 案頭應用程式會將其傳送的所有請求，以及每個請求的回應代碼記錄在專用的記錄檔中。

1. 在應用程式的日誌目錄中開啟`request.log`以查看這些請求。

1. 記錄中的每一行代表請求或回應。 請求後面會有`>`字元，後面會有請求的URL。 回應後面會有`<`字元，後面接著回應程式碼和請求的URL。 請求和回應可使用每行的GUID進行比對。

**檢查應用程式的內嵌瀏覽器載入的請求**

大部分應用程式的請求都位於請求記錄中。 不過，如果沒有有用的資訊，則查看應用程式的內嵌瀏覽器所傳送的要求會很有用。
如需如何檢視這些請求的指示，請參閱[SAML章節](#da-connection-issue-with-saml-aem)。

### SAML登入驗證無法運作{#da-connection-issue-with-saml-aem}

[!DNL Experience Manager] 案頭應用程式可能無法連線至您啟用SSO(SAML)的部 [!DNL Adobe Experience Manager] 署。應用程式的設計嘗試因應SSO連線和程式的不同和複雜性。 不過，設定可能需要進行其他疑難排解。

有時SAML程式不會重新導向回原本要求的路徑，或最終的重新導向是與[!DNL Adobe Experience Manager]案頭應用程式中設定的主機不同。 要確認情況並非如此：

1. 開啟網頁瀏覽器。 存取`https://[aem_server]:[port]/content/dam.json` URL。

1. 登入[!DNL Adobe Experience Manager]部署。

1. 登入完成後，請在位址列中查看瀏覽器的目前位址。 它應完全符合最初輸入的URL。

1. 此外，請確認`/content/dam.json`之前的所有項目都符合[!DNL Adobe Experience Manager]案頭應用程式設定中設定的目標[!DNL Adobe Experience Manager]值。

**登入SAML程式可依照上述步驟正常運作，但使用者仍無法登入**

[!DNL Adobe Experience Manager]案頭應用程式中顯示登入程式的視窗，只是顯示目標[!DNL Adobe Experience Manager]例項Web使用者介面的Web瀏覽器：

* Mac版本使用[WebView](https://developer.apple.com/documentation/webkit/webview)。

* Windows版本使用基於Chromium的[CefSharp](https://cefsharp.github.io/)。

請確定SAML程式支援這些瀏覽器。

若要進一步疑難排解，可檢視瀏覽器正嘗試載入的確切URL。 要查看此資訊，請執行以下操作：

1. 按照[debug mode](#enable-debug-mode)中啟動應用程式的指示操作。

1. 重制登錄嘗試。

1. 導覽至應用程式的[log directory](#check-log-files-v2)

1. 針對Windows:

   1. 開啟「aemcompanionlog.txt」。

   1. 搜尋以「登入瀏覽器位址變更為」開頭的訊息。 這些項目也包含應用程式載入的URL。

   針對Mac:

   1. `com.adobe.aem.desktop-nnnnnnnn-nnnnnn.log`，其中 **** n將由最新檔案名稱中的任何數字取代。

   1. 搜尋以「載入影格」開頭的訊息。 這些項目也包含應用程式載入的URL。


查看正在載入的URL順序有助於在SAML結尾疑難排解，以判斷出錯之處。

### SSL配置問題{#ssl-config-v2}

[!DNL Experience Manager]案頭應用程式用於HTTP通訊的程式庫採用嚴格的SSL強制。 有時，連線可能會使用瀏覽器成功，但使用[!DNL Experience Manager]案頭應用程式失敗。 若要正確設定SSL，請在Apache中安裝遺失的中間憑證。 請參閱[如何在Apache](https://access.redhat.com/solutions/43575)中安裝Intemider CA憑證。

[!DNL Experience Manager]案頭應用程式用於HTTP通訊的程式庫採用嚴格的SSL強制。 因此，在[!DNL Adobe Experience Manager]案頭應用程式中，有些例項會讓透過瀏覽器成功的SSL連線失敗。 這很好，因為它可促進正確配置SSL並提高安全性，但當應用程式無法連線時，可能會令人沮喪。

在這種情況下，建議的方法是使用工具來分析伺服器的SSL憑證並識別問題，以便加以修正。 有些網站會在提供伺服器URL時檢查伺服器的憑證。

作為一項臨時措施，您可以在[!DNL Adobe Experience Manager]案頭應用程式中停用嚴格的SSL強制。 這不是建議的長期解決方案，因為它會隱藏錯誤設定SSL的根本原因，以降低安全性。 要禁用嚴格強制，請執行以下操作：

1. 使用您選擇的編輯器編輯應用程式的JavaScript設定檔案，依預設會在下列位置（視作業系統而定）找到這些檔案：

   在Mac上：`/Applications/Adobe Experience Manager Desktop.app/Contents/Resources/javascript/lib-smb/config.json`

   在Windows上：`C:\Program Files (x86)\Adobe\Adobe Experience Manager Desktop\javascript\config.json`

1. 在檔案中找到下列章節：

   ```shell
   ...
   "assetRepository": {
       "options": {
   ...
   ```

1. 按如下方式添加`"strictSSL": false`以修改該部分：

   ```shell
   ...
   "assetRepository": {
       "options": {
           "strictSSL": false,
   ...
   ```

1. 儲存檔案並重新啟動[!DNL Adobe Experience Manager]案頭應用程式。

### 切換到其他伺服器{#cannot-login-cookies-issue}時的登錄問題

使用[!DNL Experience Manager]伺服器後，當您嘗試變更與不同伺服器的連線時，可能會遇到登入問題。 這是因為舊Cookie干擾新驗證。 主菜單中的[!UICONTROL Clear Cookies]選項有幫助。 註銷應用程式中的目前工作階段，然後在繼續連線之前選取[!UICONTROL Clear Cookies]。

![切換伺服器時清除Cookie](assets/main_menu_logout_da2.png)

## 應用程式沒有回應{#unresponsive}

應用程式很少會停止回應、只顯示白色畫面，或在介面底部顯示錯誤，而介面上沒有任何選項。 請依順序嘗試下列項目：

* 按一下右鍵應用程式介面，然後按一下&#x200B;**[!UICONTROL Refresh]**。
* 退出應用程式並再次開啟。

在這兩種方法中，應用程式都會從根DAM檔案夾開始。

## 隱藏過期的資產{#hide-expired-assets}

從[!DNL Experience Manager]使用者介面瀏覽資產時，不會顯示過期的資產。 若要防止在從案頭應用程式和資產連結瀏覽資產時檢視、搜尋及擷取過期資產，管理員可執行下列設定。 此設定適用於所有使用者，不論管理員權限為何。

* [在Experience Manager6.5中設定以隱藏過期資產](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#hide-expired-assets-via-acp-api)。
* [以Experience Manager設定為Cloud Service，以隱藏過期資產](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/manage-digital-assets.html#hide-expired-assets-via-acp-api)。

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

