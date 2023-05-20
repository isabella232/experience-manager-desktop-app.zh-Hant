---
title: 針對和排除故障的最佳做法 [!DNL Adobe Experience Manager] 案頭應用
description: 按照最佳做法並排除故障以解決與安裝、升級、配置等相關的偶發問題。
exl-id: f388e4ac-907d-4093-ba6f-86ecdafeb015
source-git-commit: 2c846fb9cd82691f6439e93429dffcca8127ba68
workflow-type: tm+mt
source-wordcount: '2260'
ht-degree: 0%

---

# 故障排除 [!DNL Adobe Experience Manager] 案頭應用 {#troubleshoot-v2}

[!DNL Adobe Experience Manager] 案頭應用連接到 [!DNL Experience Manager] 部署的數字資產管理(DAM)儲存庫。 應用程式將獲取電腦上的儲存庫資訊和搜索結果，下載並上載檔案和資料夾，並包括管理與Assets用戶介面衝突的功能。

閱讀以排除應用程式故障，瞭解最佳實踐並找出其局限性。

## 最佳做法 {#best-practices-to-prevent-troubles}

遵循以下最佳實踐，以防止一些常見問題和故障排除。

* **瞭解案頭應用的工作原理**:在開始使用該應用程式之前，請花些時間瞭解該應用的工作原理。 瞭解在 [!DNL Experience Manager] web介面和案頭、儲存庫映射、資產快取、本地保存和後台上傳。 請參閱 [如何工作](release-notes.md#how-app-works)。

* **避免資料夾名稱中不支援的字元**:在建立或上載資料夾時，不要使用空格和無效字元。 請參閱以下位置的字元清單 [在中建立資料夾 [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#creating-folders)。 部分 [!DNL Experience Manager] 資料夾名稱中不支援的字元可能會影響使用案例。

* **避免衝突的最佳做法**:要避免在協作多個資產時出現潛在衝突，請參閱 [避免編輯衝突](using.md#adv-workflow-collaborate-avoid-conflicts)。

* **對大型分層資料夾使用資料夾上載**:不使用Assets Web介面或其他方法，請使用 [!DNL Experience Manager] 案頭應用以上載大型資料夾。 應用通過日誌記錄和監視在後台上傳資產。 請參閱 [批量上載資產](using.md#bulk-upload-assets)。

* **使用最新版本**:使用最新應用版本，在安裝新應用版本或升級到較新應用之前，始終檢查相容性 [!DNL Experience Manager] 。 請參閱 [發行說明](release-notes.md)。

* **使用相同的驅動器號**:使用組織中的相同驅動器號映射到 [!DNL Experience Manager] 水壩。 要查看其他用戶放置的資產，路徑必須相同。 使用相同的驅動器號可確保DAM資產的一條恆定路徑。 即使不同用戶使用不同的驅動器盤符，這些資產仍會被放置，並且不會被移除。

* **注意網路**:網路效能對於 [!DNL Experience Manager] 案頭應用的效能。 如果您對檔案傳輸或批量操作的響應速度減慢，請關閉可能導致大量網路流量的功能或應用。

* **不支援的案頭應用使用案例**:不要使用Assets遷移應用程式（它需要規劃和其他工具）;執行繁重的DAM操作（如移動大資料夾、大上載、使用高級元資料搜索查找檔案）;作為同步客戶端(設計原則和使用模式與MicrosoftOneDrive或Adobe Creative Cloud案頭同步等同步客戶端不同)。

* **超時**:當前，案頭應用沒有可配置的超時值，無法斷開與 [!DNL Experience Manager] 伺服器和案頭應用。 上載大型資產時，如果連接在一段時間後超時，則應用會通過增加上載超時來重試多次上載資產。 沒有建議的更改預設超時設定的方法。

## 如何排除故障 {#troubleshooting-prep}

要解決案頭應用程式問題，請注意以下資訊。 此外，如果您選擇尋求支援，它還會讓您更好地將問題傳達給Adobe客戶支援。

### 日誌檔案的位置 {#check-log-files-v2}

[!DNL Experience Manager] desktop app會根據作業系統將其日誌檔案儲存在以下位置：

在Windows上： `%LocalAppData%\Adobe\AssetsCompanion\Logs`

Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`

上載多個資產時，如果某些檔案無法上載，請參閱 `backend.log` 檔案以標識失敗的上載。

>[!NOTE]
>
>在支援請求或票證上與Adobe客戶支援合作時，可能會要求您共用日誌檔案以幫助客戶支援團隊瞭解此問題。 存檔整個 `Logs` 資料夾，並與您的客戶支援聯繫人共用。

### 更改日誌檔案中的詳細資訊級別 {#level-of-details-in-log}

要更改日誌檔案中的詳細資訊級別，請執行以下操作：

1. 確保應用程式未運行。

1. 在Windows系統上：

   1. 開啟命令窗口。

   1. 啟動 [!DNL Adobe Experience Manager] 運行以下命令：

   ```shell
   set AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe
   ```

   在Mac系統：

   1. 開啟終端窗口。

   1. 啟動 [!DNL Adobe Experience Manager] 運行以下命令：

   ```shell
   AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app
   ```

有效的日誌級別為DEBUG、INFO、WARN或ERROR。 日誌的詳細程度在DEBUG中最高，在ERROR中最低。

### 啟用調試模式 {#enable-debug-mode}

要進行故障排除，您可以啟用調試模式並在日誌中獲取詳細資訊。

>[!NOTE]
>
>有效的日誌級別為DEBUG、INFO、WARN或ERROR。 日誌的詳細程度在DEBUG中最高，在ERROR中最低。

要在Mac的調試模式下使用該應用：

1. 開啟終端窗口或命令提示符。

1. 啟動 [!DNL Experience Manager] 運行以下命令：

   `AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app`。

要在Windows上啟用調試模式：

1. 開啟命令窗口。

1. 啟動 [!DNL Experience Manager] 運行以下命令：

`AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe`。

### 瞭解 [!DNL Adobe Experience Manager] 案頭應用程式版本 {#know-app-version-v2}

要查看版本號，請執行以下操作：

1. 啟動應用程式。

1. 按一下右上角的橢圓，懸停在 [!UICONTROL Help]，然後按一下 [!UICONTROL About]。

   版本號列在此螢幕上。

### 清除快取 {#clear-cache-v2}

執行以下步驟：

1. 啟動應用程式並連接 [!DNL Experience Manager] 實例。

1. 通過按一下右上角的橢圓並選取 [!UICONTROL Preferences]。

1. 查找顯示 [!UICONTROL Current Cache Size]。 按一下此元素旁邊的資源回收筒表徵圖。

要手動清除快取，請繼續執行以下步驟。

>[!CAUTION]
>
>這可能是破壞性操作。 如果有未上載到的本地檔案更改 [!DNL Adobe Experience Manager]，則這些更改將通過繼續操作丟失。

通過刪除應用程式的快取目錄清除快取，該目錄位於應用程式的首選項中。

1. 啟動應用程式。

1. 通過選擇右上角的橢圓並選擇 [!UICONTROL Preferences]。

1. 注意 [!UICONTROL Cache Directory] 值。

   在此目錄中，有以Encoded命名的子目錄 [!DNL Adobe Experience Manager] 端點。 名稱是目標的編碼版本 [!DNL Adobe Experience Manager] URL。 例如，如果應用程式瞄準 `localhost:4502` 則目錄名稱 `localhost_4502`。

要清除快取，請刪除所需的已編碼 [!DNL Adobe Experience Manager] 終結點目錄。 或者，刪除首選項中指定的整個目錄將清除應用程式已使用的所有實例的快取。

清除 [!DNL Adobe Experience Manager] 案頭應用的快取是解決幾個問題的初步故障排除任務。 從應用首選項中清除快取。 請參閱 [設定首選項](install-upgrade.md#set-preferences)。 快取資料夾的預設位置是：

## 無法查看已放置的資產 {#placed-assets-missing}

如果您看不到支援檔案（如INDD檔案）中放置的您或其他創意專業人員的資產，請檢查以下內容：

* 連接到伺服器。 不穩定的網路連接可能會阻止資產下載。

* 檔案大小。 下載和顯示大型資產需要更長時間。

* 驅動器盤符一致性。 如果您或其他協作者在映射時放置了資產 [!DNL Experience Manager] DAM到其他驅動器號時，放置的資產不顯示。

* 權限。要檢查您是否有權獲取已放置的資產，請與 [!DNL Experience Manager] 管理員。

### 對案頭應用用戶介面上檔案的編輯不反映在 [!DNL Adobe Experience Manager] 立即 {#changes-on-da-not-visible-on-aem}

[!DNL Adobe Experience Manager] 案頭應用讓用戶決定何時完成對檔案的所有編輯。 根據檔案的大小和複雜性，將新版本的檔案傳輸到 [!DNL Adobe Experience Manager]。 應用程式的設計要求最小化檔案往返傳輸的次數，而不是猜測檔案編輯完成並自動上載的時間。 建議用戶啟動將檔案傳回 [!DNL Adobe Experience Manager] 選擇上載檔案的更改。

### 升級macOS時的問題 {#issues-when-upgrading-on-macos}

升級時偶爾會出現問題 [!DNL Experience Manager] 案頭應用macOS。 這是由於的舊系統資料夾 [!DNL Experience Manager] 案頭應用阻止新版本 [!DNL Experience Manager] 要正確載入的案頭應用。 要解決此問題，可以手動刪除以下資料夾和檔案。

在執行以下步驟之前，拖動 `Adobe Experience Manager Desktop` 從「macOS應用程式」資料夾到「垃圾」。 然後開啟終端，執行以下命令，並在出現提示時提供密碼。

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## 無法上載檔案 {#upload-fails}

如果您正在將案頭應用與 [!DNL Experience Manager] 6.5.1或更高版本，將S3或Azure連接器升級到1.10.4版或更高版本。 它解決了與 [OAK-8599](https://issues.apache.org/jira/browse/OAK-8599)。 請參閱 [安裝說明](install-upgrade.md#install-v2)。

## [!DNL Experience Manager] 案頭應用程式連接問題 {#connection-issues}

如果您遇到一般連接問題，請通過以下方式獲取有關以下內容的詳細資訊 [!DNL Experience Manager] 案頭應用正在執行。

**檢查請求日誌**

[!DNL Experience Manager] 案頭應用將它發送的所有請求以及每個請求的響應代碼記錄在專用日誌檔案中。

1. 開啟 `request.log` 以查看這些請求。

1. 日誌中的每一行都表示請求或響應。 請求將具有 `>` 字元後跟請求的URL。 響應將具有 `<` 字元後跟響應代碼和請求的URL。 可以使用每行的GUID匹配請求和響應。

**檢查應用程式的嵌入式瀏覽器載入的請求**

大多數應用程式的請求都在請求日誌中找到。 但是，如果那裡沒有有用的資訊，則查看應用程式的嵌入式瀏覽器發送的請求會非常有用。
查看 [SAML節](#da-connection-issue-with-saml-aem) 有關如何查看這些請求的說明。

### SAML登錄驗證無效 {#da-connection-issue-with-saml-aem}

[!DNL Experience Manager] 案頭應用可能無法連接到您啟用SSO(SAML) [!DNL Adobe Experience Manager] 部署。 應用程式的設計嘗試適應SSO連接和進程的變化和複雜性。 但是，安裝程式可能需要進行其他故障診斷。

有時SAML進程不會重定向回最初請求的路徑，或者最終重定向到的主機與中配置的主機不同 [!DNL Adobe Experience Manager] 案頭應用。 要驗證情況不是這樣：

1. 開啟Web瀏覽器。 訪問 `https://[aem_server]:[port]/content/dam.json` URL。

1. 登錄到 [!DNL Adobe Experience Manager] 部署。

1. 登錄完成後，在地址欄中查看瀏覽器的當前地址。 它應與最初輸入的URL完全匹配。

1. 同時驗證以前的所有內容 `/content/dam.json` 與目標匹配 [!DNL Adobe Experience Manager] 配置的值 [!DNL Adobe Experience Manager] 案頭應用的設定。

**按照上述步驟，登錄SAML進程工作正常，但用戶仍無法登錄**

窗口 [!DNL Adobe Experience Manager] 顯示登錄進程的案頭應用程式只是一個顯示目標的Web瀏覽器 [!DNL Adobe Experience Manager] 實例的web用戶介面：

* Mac版本使用 [Web視圖](https://developer.apple.com/documentation/webkit/webview)。

* Windows版本使用基於鉻的 [切夫夏普](https://cefsharp.github.io/)。

確保SAML進程支援這些瀏覽器。

若要進一步排除故障，可以查看瀏覽器正嘗試載入的確切URL。 要查看此資訊：

1. 按照中啟動應用程式的說明 [調試模式](#enable-debug-mode)。

1. 重現登錄嘗試。

1. 導航到 [日誌目錄](#check-log-files-v2) 的

1. 對於Windows:

   1. 開啟&quot;aemopionlog.txt&quot;。

   1. 搜索以「登錄瀏覽器地址更改為」開頭的消息。 這些條目還包含應用程式載入的URL。

   Mac:

   1. `com.adobe.aem.desktop-nnnnnnnn-nnnnnn.log`的子菜單。 **n** 替換為最新檔案名中的任何數字。

   1. 搜索以「已載入幀」開頭的消息。 這些條目還包含應用程式載入的URL。


查看正在載入的URL序列有助於在SAML的末尾進行故障排除，以確定錯誤所在。

### SSL配置問題 {#ssl-config-v2}

那些 [!DNL Experience Manager] 用於HTTP通信的案頭應用採用嚴格的SSL強制。 有時，連接可能使用瀏覽器成功，但使用失敗 [!DNL Experience Manager] 案頭應用。 要正確配置SSL，請在Apache中安裝缺少的中間證書。 請參閱 [如何在Apache中安裝中間CA證書](https://access.redhat.com/solutions/43575)。

那些 [!DNL Experience Manager] 用於HTTP通信的案頭應用採用嚴格的SSL強制。 因此，在某些情況下，通過瀏覽器成功的SSL連接會失敗， [!DNL Adobe Experience Manager] 案頭應用。 這很好，因為它鼓勵正確配置SSL並提高安全性，但當應用程式無法連接時，這會令人沮喪。

在此情況下，建議使用一種工具來分析伺服器的SSL證書並識別問題，以便更正這些問題。 有些網站會檢查伺服器的證書提供其URL。

作為臨時措施，可以在 [!DNL Adobe Experience Manager] 案頭應用。 這不是建議的長期解決方案，因為它通過隱藏錯誤配置SSL的根本原因來降低安全性。 要禁用嚴格強制，請執行以下操作：

1. 使用所選的編輯器編輯應用程式的JavaScript配置檔案，該檔案在以下位置（取決於作業系統）找到（預設）:

   Mac: `/Applications/Adobe Experience Manager Desktop.app/Contents/Resources/javascript/lib-smb/config.json`

   在Windows上： `C:\Program Files (x86)\Adobe\Adobe Experience Manager Desktop\javascript\config.json`

1. 在檔案中找到以下部分：

   ```shell
   ...
   "assetRepository": {
       "options": {
   ...
   ```

1. 通過添加修改節 `"strictSSL": false` 如下：

   ```shell
   ...
   "assetRepository": {
       "options": {
           "strictSSL": false,
   ...
   ```

1. 保存檔案並重新啟動 [!DNL Adobe Experience Manager] 案頭應用。

### 切換到其他伺服器時的登錄問題 {#cannot-login-cookies-issue}

使用 [!DNL Experience Manager] 伺服器，當您嘗試更改與其他伺服器的連接時，可能會遇到登錄問題。 這是由於舊Cookie干擾了新身份驗證。 主菜單中的選項 [!UICONTROL Clear Cookies] 幫助。 註銷應用程式中的當前會話並選擇 [!UICONTROL Clear Cookies] 繼續連接之前。

![切換伺服器時清除Cookie](assets/main_menu_logout_da2.png)

## 應用未響應 {#unresponsive}

應用程式很少會無響應、只顯示白屏或在介面底部顯示錯誤，而介面上沒有任何選項。 按順序嘗試以下操作：

* 按一下右鍵應用程式介面，然後按一下 **[!UICONTROL Refresh]**。
* 退出應用程式並再次開啟。

在這兩種方法中，應用程式都從根DAM資料夾啟動。

## 隱藏過期資產 {#hide-expired-assets}

從內部瀏覽資產時 [!DNL Experience Manager] 用戶介面，不顯示過期資產。 為防止在從案頭應用程式和資產連結瀏覽資產時查看、搜索和獲取過期資產，管理員可以執行以下配置。 該配置適用於所有用戶，而與管理員權限無關。

* [Experience Manager6.5中的配置以隱藏過期資產](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#hide-expired-assets-via-acp-api)。
* [在Experience Manageras a Cloud Service中配置以隱藏過期資產](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/manage-digital-assets.html#hide-expired-assets-via-acp-api)。

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

