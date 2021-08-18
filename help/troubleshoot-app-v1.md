---
title: 案頭應用程式1.10版疑難排解。
description: 疑難排解 [!DNL Adobe Experience Manager] 案頭應用程式1.10版，以解決與安裝、升級和配置相關的偶發性問題。
exl-id: 1e1409c2-bf5e-4e2d-a5aa-3dd74166862c
source-git-commit: 2ae49374b362921a5a82fc2e040064b4e573b8c1
workflow-type: tm+mt
source-wordcount: '3291'
ht-degree: 1%

---

# 疑難排解[!DNL Adobe Experience Manager]案頭應用程式v1.x {#troubleshoot-aem-desktop-app}

疑難排解AEM案頭應用程式，以解決與安裝、升級、設定等相關的偶發問題。

[!DNL Adobe Experience Manager] 案頭應用程式包含實用程式，可協助您將AEM Assets存放庫對應為案頭上的網路共用（Mac OS上的SMB共用）。網路共用是一種作業系統技術，它使遠程源被視為電腦本地檔案系統的一部分。 在案頭應用程式的案例中，遠端AEM例項的數位資產管理(DAM)存放庫結構會定位為遠端檔案來源。 下圖描述了案頭應用拓撲：

![案頭應用程式圖](assets/aem-desktopapp-architecture.png)

透過此架構，案頭應用程式會截取檔案系統呼叫（開啟、關閉、讀取、寫入等）至已載入的網路共用，並將這些呼叫轉譯為對AEM伺服器的原生AEM HTTP呼叫。 檔案會快取到本機。 如需詳細資訊，請參閱[使用AEM案頭應用程式v1.x](use-app-v1.md)。

## AEM案頭應用程式元件概觀 {#desktop-app-component-overview}

案頭應用程式包含下列元件：

* **案頭應用程式**:應用程式會裝載或卸載DAM作為遠程檔案系統，並在本地裝載的網路共用與它所連接的遠程AEM實例之間轉換檔案系統調用。
* **作業系統WebDAV/SMB客戶端**:處理Windows資源管理器/查找器和案頭應用程式之間的通信。如果檢索、建立、修改、刪除、移動或複製檔案，作業系統(OS)WebDAV/SMB客戶端會將此操作與案頭應用程式通信。 收到通訊後，案頭應用程式會將其轉譯為原生AEM遠端API呼叫。 例如，如果使用者在已載入的目錄中建立檔案，WebDAV/SMB用戶端會起始請求，案頭應用程式會將此請求轉譯為在DAM中建立檔案的HTTP請求。 WebDAV/SMB客戶端是作業系統的內置元件。 它與案頭應用程式、AEM或Adobe皆無關聯。
* **Adobe Experience Manager例項**:可存取儲存在AEM Assets DAM存放庫中的資產。此外，它代表與掛載的網路共用交互的本地案頭應用程式執行案頭應用請求的操作。 目標AEM例項應執行AEM 6.1版或更新版本。 執行舊版AEM的AEM執行個體可能需要安裝額外的功能套件和Hotfix，才能正常運作。

## AEM案頭應用程式的預期使用案例 {#intended-use-cases-for-aem-desktop-app}

AEM案頭應用程式使用網路共用技術將遠端AEM存放庫對應至本機案頭。 但是，這並非取代網路共用持有資產，因為使用者直接從本機案頭執行數位資產管理操作。 這包括移動或複製多個檔案，或直接在Finder/Explorer中將大型資料夾結構拖曳至AEM Assets網路共用。

AEM案頭應用程式提供在AEM Assets觸控式UI和本機案頭之間存取（開啟）和編輯（儲存）DAM資產的便利方式。 它會將AEM Assets伺服器中的資產連結至您以案頭為基礎的工作流程。

以下範例使用案例說明應如何使用AEM Desktop:

* 使用者登入AEM並使用網頁UI來尋找資產。
* 使用AEM網頁UI的案頭動作功能，使用者可視需要在案頭開啟、顯示或編輯資產。
* AEM Desktop會在資產檔案類型的預設編輯器中開啟資產。
* 使用者對資產進行所需的變更。
* 修改檔案後，用戶可以使用AEM Desktop的後台同步狀態窗口查看該檔案的同步狀態。
* 使用AEM Desktop的內容功能表，使用者會簽入/簽出資產，或返回DAM使用者介面。
* 完成檔案的變更後，使用者會返回AEM網頁UI

這並非唯一的使用案例。 不過，它說明AEM Desktop是在本機存取/編輯資產的便利機制。 建議您盡量使用DAM Web UI，因為它可提供更好的體驗。 它為Adobe提供更大的彈性，以符合客戶需求。

## 限制 {#limitations}

WebDAV/SMB1網路共用為在Explorer/Finder窗口中處理檔案提供了便利。 不過，Explorer/Finder和AEM會透過具有特定限制的網路連線進行通訊。 例如，將1-GB檔案複製到裝載的WebDAV/SMB目錄所花費的時間與使用Web瀏覽器將1-GB檔案上載到網站所需的時間大致相同。 事實上，在前一種情況下，由於WebDAV/SMB協定和作業系統的WebDAV/SMB客戶端（特別是Mac OS X）效率低下，持續時間可能會更長。

可以從裝載的目錄執行的任務類型有一些限制。 一般而言，處理大型檔案（尤其是在低/高延遲/低頻寬的網路連接上）可能是一項挑戰，特別是在編輯大型檔案時。

Adobe建議您先執行一些使用案例測試，然後再向客戶端提交某些類型的檔案，以便從裝載的目錄就地有效地編輯。

AEM Desktop不適合執行密集的檔案系統操作，包括但不限於：

* 移動或複製檔案和目錄
* 新增許多資產至AEM
* 通過檔案系統搜索和開啟檔案（瀏覽資料夾除外）
* 壓縮或解壓縮檔案存檔

由於作業系統的限制，Windows的檔案大小限制為4,294,967,295位元組（約4.29 GB）。 這是由於註冊表設定定義了網路共用上的檔案的大小。 註冊表設定的值是DWORD，其大小上限等於引用的數字。

[!DNL Experience Manager] 案頭應用程式沒有可設定的逾時值，該逾時值會在固定時間 [!DNL Experience Manager] 間隔後中斷伺服器與案頭應用程式之間的連線。上傳大型資產時，如果連線在一段時間後逾時，應用程式會增加上傳逾時，以重試幾次來上傳資產。 建議不要變更預設逾時設定。

## 快取與AEM通訊 {#caching-and-communication-with-aem}

AEM案頭應用程式提供內部快取和背景上傳功能，以改善一般使用者體驗。 儲存大型檔案時，會先將其儲存在本機，以便您繼續運作。 在某個時間（目前為30秒）之後，會將檔案傳送至背景的AEM伺服器。

與Creative Cloud案頭或其他檔案同步解決方案（如Microsoft One Drive）不同，AEM案頭應用程式不是完整的案頭同步客戶端。 其原因是，它提供了對整個AEM Assets儲存庫的訪問，該儲存庫可能非常大（數百GB或TB），以實現完全同步。

快取功能可將網路/儲存的負載限制在與使用者相關的資產子集。

>[!CAUTION]
>
>Adobe建議關閉縮圖產生，以加快瀏覽速度。 如果您啟用圖示預覽，當您瀏覽已載入的資料夾時，應用程式會快取數位資產。 應用程式也會下載使用者可能不在乎的資產，這會增加伺服器的負載、耗用使用者的頻寬，並使用更多使用者的磁碟空間。

以下是AEM案頭應用程式執行快取的方式：

* 當您在Finder中開啟資料夾且顯示檔案的縮圖/預覽，或當您在應用程式中開啟檔案時，案頭應用程式會快取檔案二進位。
* 當您通過Finder或其他案頭應用程式儲存檔案時，檔案會先在本機（快取）儲存，並通知作業系統。 然後，檔案會排入佇列，等候在背景上傳至伺服器，並最終透過網路上傳。 發生網路錯誤時，案頭應用程式會重試上傳整個檔案最多三次。 如果重試三次後無法上傳，則檔案會標示為衝突的檔案，狀態會透過「背景上傳佇列狀態」視窗顯示。 案頭應用程式不會再嘗試更新檔案。 使用者應更新檔案，並在連線恢復後重新上傳

不會在本機快取每個操作。 不會進行本機快取，下列內容會立即傳送至AEM伺服器：

* 對資料夾的任何操作，例如建立、刪除等
* 1.4 版中加入的「檔案夾上傳」功能可上傳本機檔案夾階層，而不需在本機快取檔案

## 個別操作 {#individual-operations}

針對個別使用者的次最佳化效能進行疑難排解時，請先檢閱[應用程式限制](#limitations)。 後續章節包含改善個別使用者效能的建議。

## 頻寬建議 {#bandwidth-recommendations}

單個用戶可用的頻寬在WebDAV/SMB客戶端的效能中起著關鍵作用。

Adobe建議個別使用者的上傳速度接近10 Mbps。 對於無線連接，頻寬通常在多個用戶之間共用。 如果多個用戶同時執行消耗網路頻寬的任務，則效能可能會進一步降低。 若要避免這類問題，請使用有線連線。

<!-- AG, 8/18: The Windows KB article is removed by MS now. Giving 404. Also, Win 7 support is gone and the desktop app is also not supported on Win 7. Hiding this content for now.

## Windows-specific configurations {#windows-specific-configurations}

If you use Experience Manager on Windows, you can configure Windows to enhance the performance of the WebDAV client. For more information, go to [https://support.microsoft.com/en-us/kb/2445570](https://support.microsoft.com/en-us/kb/2445570).

On Windows 7, modifying IE settings can improve the performance of WebDAV. For details, see how to [fix slow WebDAV performance in Windows 7](https://oddballupdate.com/2009/12/fix-slow-webdav-performance-in-windows-7/).
-->

## 併發操作 {#concurrent-operations}

當您在本機與檔案互動時，AEM Desktop會檢查AEM中是否有較新版本的檔案可用。 如果有新版本可用，應用程式會將檔案的最新副本下載到本機快取。 不過，如果已修改AEM Desktop，則不會覆寫本機快取的檔案。 此功能可防止無意中覆寫您的工作。

在本機和AEM中修改相同檔案時，本機修改的版本會覆寫AEM中的版本。 在此情況下，資產時間軸會提供舊版。 您可以驗證兩個版本並解決任何衝突。

如果本機檔案與伺服器中可用的版本不一致，背景上傳狀態對話方塊會通知您有關衝突的資訊。 若要解決此問題，請開啟衝突的檔案並儲存。 儲存檔案會強制AEM Desktop將您的最新本機變更同步至AEM。 您可以在時間軸中檢視資產的舊版本，並解決任何衝突。

當多個使用者嘗試在針對相同AEM例項的個別裝載目錄中工作時，您應考量其他因素。 尤其是，以下因素很重要：

* 用戶源網路上的可用頻寬量
* 原始網路的網路配置（如防火牆或代理）
* 目標AEM實例的網路中可用的頻寬量
* 目標AEM例項之前是否存在Dispatcher
* 目標AEM例項上的目前載入

## 其他AEM設定 {#additional-aem-configurations}

如果多個用戶同時工作時， WebDAV/SMB的效能會顯著降低，您可以在AEM中配置一些內容，這將有助於提高效能。

## 更新資產暫時性工作流程 {#update-asset-transient-workflows}

您可以為「DAM更新資產」工作流程啟用暫時性工作流程，以改善AEM端的效能。 啟用暫時性工作流程，可在AEM中建立或修改資產時，降低更新資產所需的處理能力。

1. 導覽至Experience Manager例項(`https://[aem_server]:[port]/miscadmin`)中的`/miscadmin`。
1. 從導覽樹狀結構中，展 **開「工具** >工 **作流程** >模 **型>** dam ****」。
1. 按兩下&#x200B;**DAM更新資產**。
1. 從浮動工具面板，切換到&#x200B;**Page**&#x200B;頁簽，然後按一下&#x200B;**Page Properties**。
1. 選擇「**暫時工作流**」複選框，然後按一下「**確定**」。

### 調整 Granite 暫時工作流程佇列 {#adjust-granite-transient-workflow-queue}

另一種改善AEM效能的方法，是為Granite暫時工作流程佇列作業設定最大平行作業的值。 建議的值大約是伺服器可用CPU數量的一半。 要調整值，請執行以下步驟：

1. 導覽至要設定的AEM例項中的`/system/console/configMgr`（例如`https://[aem_server]:[port]/system/console/configMgr`）。
1. 搜索`QueueConfiguration`，然後按一下以開啟每個作業，直到找到&#x200B;**Granite暫時工作流隊列**&#x200B;作業，然後按一下&#x200B;**Edit**。
1. 更改`Maximum Parallel Jobs`值，然後按一下&#x200B;**Save**。

## AWS配置 {#aws-configuration}

由於網路頻寬限制，當多個用戶同時工作時， WebDAV/SMB的效能可能會降低。 Adobe建議增加在AWS上運行的目標AEM實例的AWS實例的大小，以增強WebDAV/SMB的效能。

此措施特別提高了伺服器可用的網路頻寬量。 以下是部分細節：

* 專用於AWS實例的網路頻寬量隨著實例大小的增加而增加。 有關每個實例大小的可用頻寬的資訊，請參閱[AWS文檔](https://aws.amazon.com/ec2/instance-types/)。
* 對大型客戶端進行故障排除時，Adobe將其AEM實例的大小配置為c4.8xlarge，主要是針對它提供的4000 Mbps專用頻寬。
* 如果AEM例項前面有Dispatcher，請確定其大小適當。 如果AEM執行個體提供4000 Mbps，但Dispatcher僅提供500 Mbps，則有效頻寬僅為500 Mbps。 這是因為Dispatcher會造成網路瓶頸。

## 簽出檔案限制 {#checked-out-file-limitations}

通過Explorer/Finder與簽出檔案交互的方式有一些已知限制。 如果已簽出檔案，則除已簽出該檔案的用戶外，該檔案應為所有人只讀。 在AEM中實施WebDAV/SMB1協定可強制執行此規則。 但是，OS WebDAV/SMB客戶端通常不能與簽出的檔案正常交互。 以下介紹一些怪異之處。

### 一般 {#general}

寫入簽出檔案時，僅在AEM WebDAV實施內強制執行鎖定。 因此，僅使用WebDAV（如案頭應用程式）的客戶端才會強制執行鎖。 鎖定不會透過AEM網頁介面強制執行。 AEM介面只會在已簽出資產的卡片檢視中顯示鎖定圖示。 圖示為修飾，對AEM的行為沒有影響。

通常， WebDAV客戶端並不總是如預期般運行。 可能還有其他問題。 不過，在AEM中重新整理或檢查資產是驗證資產未修改的音效方式。 此行為是OS WebDAV客戶端的典型行為，不受Adobe控制。

### Windows {#windows}

刪除檔案似乎成功，因為該檔案從Windows中的檔案資源管理器中消失。 不過，重新整理目錄並簽入AEM資產時，會顯示檔案仍存在。 此外，編輯檔案似乎成功（未顯示警告對話框或錯誤消息）。 不過，重新開啟檔案或簽入AEM資產會顯示檔案未變更。

#### Mac OS X {#mac-os-x}

取代檔案不會顯示警告或錯誤，但在AEM中勾選資產會顯示資產維持不變。 在AEM中重新整理或勾選資產，以確認資產未修改。

## 案頭應用程式圖示問題疑難排解(Mac OS X) {#troubleshooting-desktop-app-icon-issues-mac-os-x}

安裝案頭應用程式後，案頭應用程式功能表圖示會出現在功能表列中。 如果未顯示圖示，請執行下列步驟以解決問題：

1. 開啟作業系統終端窗口。
1. 在命令提示符下鍵入以下命令，然後按Enter鍵：

   ```shell
    cd ../Library/Caches.
   ```

1. 鍵入以下命令，然後按Enter鍵：

   ```shell
   rm -r com.adobe.aem.assetscompanion
   ```

1. 鍵入以下命令，然後按Enter鍵：

   ```shell
   cd ~/Library/Preferences
   ```

1. 鍵入以下命令，然後按Enter鍵：

   ```shell
   rm com.adobe.aem.assetscompanion.plist
   ```

1. 鍵入以下命令，然後按Enter鍵：

   ```shell
   rm ~/Library/Group\ Containers/group.com.adobe.aem.desktop/*
   ```

1. 重新啟動系統。

AEM Desktop會嘗試同步任何指定檔案三次。 如果第三次嘗試後檔案無法同步，AEM Desktop會認為檔案發生衝突，並透過背景上傳狀態視窗通知您。 衝突狀態表示您的最新變更仍可在本機使用，但不會同步回AEM。 AEM案頭應用程式不再嘗試同步。

解決此情況的最簡單方法是開啟衝突的檔案並再次保存。 它會強制AEM Desktop嘗試另外三次同步。 如果檔案仍無法同步，請參閱下方各節以取得更多說明。

## 清除AEM案頭快取 {#clearing-aem-desktop-cache}

清除AEM Desktop的快取是可解決數個AEM Desktop問題的初步疑難排解工作。

您可以在下列位置刪除應用程式的快取目錄，以清除快取。
在Windows中， `%LocalAppData%\Adobe\AssetsCompanion\Cache\`

在Mac中， `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/`

不過，位置可能會隨著AEM Desktop所設定的AEM端點而變更。 值是目標URL的編碼版本。 例如，如果應用程式正在定位`http://localhost:4502`，則目錄名為`http%3A%2F%2Flocalhost%3A4502%2F`。

若要清除快取，請刪除&lt;Encoded AEM Endpoint>目錄。

>[!NOTE]
>
>如果清除AEM案頭快取，未同步至AEM的本機檔案變更將會遺失。

>[!NOTE]
>
>從AEM案頭應用程式1.5版開始，案頭應用程式UI中會提供清除快取的選項。

## 尋找AEM案頭版本 {#finding-the-aem-desktop-version}

Windows和Mac OS中確定AEM案頭版本的過程相同。

按一下AEM案頭表徵圖，然後選擇&#x200B;**關於**。 版本號碼會顯示在畫面上。

## 在macOS上升級AEM案頭應用程式 {#upgrading-aem-desktop-app-on-macos}

在macOS上升級AEM案頭應用程式時，偶爾會發生問題。 這是因為AEM案頭應用程式的舊版系統資料夾無法正確載入新版本的AEM Desktop所造成。 若要解決此問題，可以手動移除下列資料夾和檔案。

在執行下列步驟之前，請將「Adobe Experience Manager Desktop」應用程式從macOS Applications資料夾拖曳至Trash。 然後開啟終端機，並執行下列命令，在出現提示時提供您的密碼。

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## 保存其他人簽出的檔案 {#saving-a-file-checked-out-by-others}

作業系統的技術限制會防止使用者在嘗試覆寫其他人簽出的檔案時，有一致的體驗。 體驗會因用來編輯已簽出檔案的應用程式而異。 有時，應用程式會顯示錯誤消息，指示磁碟寫入失敗，或顯示看似不相關或一般的錯誤。 在其他情況下，不會顯示錯誤訊息，且操作似乎成功。

在此情況下，關閉和重新開啟檔案可能會顯示內容未變更。 但是，某些應用程式可能會儲存檔案的備份，以便應用您的更改。

無論採取何種行為，當您簽入時，檔案都會維持不變。 即使顯示不同版本的檔案，變更也不會同步至AEM。

## 疑難排解移動檔案的相關問題 {#troubleshooting-problems-around-moving-files}

伺服器API需要傳遞其他標頭X-Destination、X-Depth和X-Overwrite，移動和複製操作才能運作。 Dispatcher預設不會傳遞這些標題，而會導致這些操作失敗。 如需詳細資訊，請參閱[連線至Dispatcher](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher)後面的AEM 。

## 疑難排解AEM案頭連線問題 {#troubleshooting-aem-desktop-connection-issues}

### SAML重新導向問題 {#saml-redirect-issue}

AEM Desktop連線至您啟用SSO(SAML)AEM例項時，最常見的原因是SAML程式不會重新導向回原本請求的路徑。 或者，可將連接重定向到未在AEM案頭中配置的主機。 執行下列步驟以驗證登入程式：

1. 開啟網頁瀏覽器。
1. 在網址列中指定URL `/content/dam.json`。
1. 將URL取代為目標AEM例項，例如`https://localhost:4502/content/dam.json`。
1. 登入AEM。
1. 登入後，在位址列中檢查瀏覽器的目前位址。 它應符合您最初輸入的URL。
1. 確認`/content/dam.json`之前的所有項目都符合AEM Desktop中設定的目標AEM值。

### SSL設定問題 {#ssl-configuration-issue}

AEM案頭應用程式用於HTTP通訊的程式庫採用嚴格的SSL強制。 有時，連線可能使用瀏覽器成功，但使用AEM案頭應用程式失敗。 若要適當設定SSL，請在Apache中安裝遺漏的中繼憑證。 請參閱[如何在Apache](https://access.redhat.com/solutions/43575)中安裝中繼CA憑證。

## 搭配使用AEM Desktop與Dispatcher {#using-aem-desktop-with-dispatcher}

AEM Desktop可搭配AEM部署在Dispatcher後面使用，這是AEM伺服器的預設且建議的設定。 AEM製作環境前的AEM dispatcher通常會設定為略過快取DAM資產。 因此，從AEM Desktop的觀點來看，Dispatcher不提供其他快取。 請確定Dispatcher設定已調整為適用於AEM Desktop。 如需其他詳細資訊，請參閱[連線至Dispatcher](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher)背後的AEM。

## 正在檢查日誌檔案 {#checking-for-log-files}

根據您的作業系統，您可以在以下位置找到AEM Desktop的日誌檔案：

* Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`
* Mac:`~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`
