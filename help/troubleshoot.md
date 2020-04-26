---
title: Adobe Experience Manager案頭應用程式的最佳實務和疑難排解
description: 遵循最佳實務並進行疑難排解，以解決與安裝、升級、設定等相關的偶發問題。
uuid: ce98a3e7-5454-41be-aaaa-4252b3e0f8dd
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: f5eb222a-6cdf-4ae3-9cf2-755c873f397c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b92e47456f9e16c24eac43d1c5fef9a582f143b5

---


# Troubleshoot Adobe Experience Manager desktop app {#troubleshoot-v2}

Adobe Experience Manager(AEM)案頭應用程式會連接至遠端Experience Manager部署的數位資產管理(DAM)儲存庫。 應用程式會擷取儲存庫資訊並在您的電腦上搜尋結果、下載和上傳檔案和檔案夾，並包含與AEM Assets使用者介面衝突的管理功能。

閱讀以疑難排解應用程式、瞭解最佳實務，並瞭解限制。

## Best practices {#best-practices-to-prevent-troubles}

遵守下列最佳實務，以防止出現一些常見問題和疑難排解。

* **瞭解案頭應用程式的運作方式**:開始使用應用程式之前，請花幾分鐘的時間瞭解應用程式的運作方式。 瞭解Web UI與案頭之間的連結、儲存庫對應、資產快取、本機儲存以及在背景上傳。 了 [解運作方式](release-notes.md#how-app-works)。

* **避免資料夾名稱中不支援的字元**:建立或上傳檔案夾時，請勿使用空白字元和無效字元。 請參閱Experience Manager Assets中建立 [資料夾的字元清單](https://docs.adobe.com/content/help/en/experience-manager-65/assets/managing/managing-assets-touch-ui.html#Creatingfolders)。 有些Adobe Experience Manager使用案例可能會受到檔案夾名稱中不支援的字元影響。

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

若要疑難排解，您可以啟用除錯模式，並在記錄檔中取得更多資訊。 若要在Mac的除錯模式中使用應用程式，請在終端機或命令提示符下使用下列命令列選項： `AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app`。

要在Windows上啟用調試模式，請執行以下步驟：

1. 在案頭 `Adobe Experience Manager Desktop.exe.config` 應用程式安裝資料夾中尋找檔案。 依預設，資料夾為 `C:\Program Files\Adobe\Adobe Experience Manager Desktop`。 儲存並關閉檔案。

1. 找 `<level value="INFO"/>` 到檔案結尾處。 將值更 `DEBUG`改為，即 `<level value="DEBUG"/>`。

1. 在案頭 `logging.json` 應用程式安裝資料夾中尋找檔案。 依預設，資料夾為 `C:\Program Files\Adobe\Adobe Experience Manager Desktop\javascript\`。

1. 在文 `logging.json` 件中，找到參數的所有實 `level` 例。 將值從更改 `info` 為 `debug`。 儲存並關閉檔案。

1. 清除在應用程式偏好設定中設定位置的快取目錄。

1. 重新啟動案頭應用程式。

<!-- The Windows command doesn't work for now.
* On Windows: `SET AEM_DESKTOP_LOG_LEVEL=DEBUG & "C:\Program Files\Adobe\Adobe Experience Manager Desktop\Adobe Experience Manager Desktop.exe"`
-->

### 日誌檔案的位置 {#check-log-files-v2}

您可以在下列位置找到AEM案頭應用程式的記錄檔。 上傳許多資產時，如果有些檔案無法上傳，請參 `backend.log` 閱檔案以識別失敗的上傳。

* Windows上的路徑： `%LocalAppData%\Adobe\AssetsCompanion\Logs`

* Mac上的路徑： `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`

>[!NOTE]
>
>在支援要求／票證上與Adobe客戶服務合作時，可能會要求您共用記錄檔，以協助客戶服務團隊瞭解問題。 封存整個資 `Logs` 料夾，並與您的客戶服務聯絡人共用。

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

## 看不到置入的資產 {#placed-assets-missing}

如果您或其他創意專業人員無法在支援檔案（例如INDD檔案）中看到所放置的資產，請勾選下列項目：

* 連線至伺服器。 不穩定的網路連線可能會拖慢資產下載。
* 檔案大小。 大型資產下載和展示的時間較長。
* 驅動器號的一致性。 如果您或其他共同作業者在將AEM DAM對應至不同的磁碟盤符時置入資產，則不會顯示置入的資產。
* 權限. 若要檢查您是否擁有擷取置入資產的權限，請連絡您的AEM管理員。

## 在macOS上升級時的問題 {#issues-when-upgrading-on-macos}

在macOS上升級AEM案頭應用程式時，偶爾會發生問題。 這是由於AEM案頭應用程式的舊系統資料夾導致無法正確載入新版AEM案頭應用程式。 要解決此問題，可以手動刪除以下資料夾和檔案。

在執行下列步驟之前，請將應用程 `Adobe Experience Manager Desktop` 式從macOS Applications檔案夾拖曳至「垃圾筒」。 然後開啟終端機，執行下列命令，並在出現提示時提供您的密碼。

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## 無法上傳檔案 {#upload-fails}

如果您正在搭配AEM 6.5.1或更新版本使用案頭應用程式，請將S3或Azure連接器升級至1.10.4或更新版本。 它可解決與 [OAK-8599相關的檔案上傳失敗問題](https://issues.apache.org/jira/browse/OAK-8599)。 請參閱 [安裝指示](install-upgrade.md#install-v2)。

## SSL設定問題 {#ssl-config-v2}

AEM案頭應用程式用於HTTP通訊的程式庫採用嚴格的SSL強制。 有時，連線可能會使用瀏覽器成功，但無法使用AEM案頭應用程式。 若要正確設定SSL，請在Apache中安裝遺失的中間憑證。 請參 [閱如何在Apache中安裝Intemider CA憑證](https://access.redhat.com/solutions/43575)。

## 應用程式沒有回應 {#unresponsive}

應用程式很少會停止回應、只顯示白色畫面，或在介面底部顯示錯誤，而介面上沒有任何選項。 請依順序嘗試下列項目：

1. 在應用程式介面上按一下滑鼠右鍵，然後按一下 **[!UICONTROL Refresh]**。
1. 退出應用程式並重新啟動它。

在這兩種方法中，應用程式都會從根DAM檔案夾開始。

>[!MORELIKETHIS]
>
>* [已知問題](release-notes.md#known-issues-v2)
>* [避免編輯衝突](using.md#adv-workflow-collaborate-avoid-conflicts)