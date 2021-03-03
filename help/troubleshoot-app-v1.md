---
title: 疑難排解案頭應用程式1.10版。
description: 疑難排解 [!DNL Adobe Experience Manager] 案頭應用程式1.10版，以解決與安裝、升級和設定相關的偶發性問題。
translation-type: tm+mt
source-git-commit: 4870615ed40226964d077d6666b83b85b73da180
workflow-type: tm+mt
source-wordcount: '3363'
ht-degree: 1%

---


# 疑難排解[!DNL Adobe Experience Manager]案頭應用程式v1.x {#troubleshoot-aem-desktop-app}

疑難排AEM解案頭應用程式，以解決與安裝、升級、設定等相關的偶發性問題。

[!DNL Adobe Experience Manager] 案頭應用程式包含公用程式，可協助您將AEM Assets儲存庫對應為案頭上的網路共用（Mac OS上的SMB共用）。網路共用是一種作業系統技術，它使遠程源被視為電腦本地檔案系統的一部分。 在案頭應用程式中，遠端例AEM項的數位資產管理(DAM)儲存庫結構會定位為遠端檔案來源。 下圖說明案頭應用程式拓撲：

![案頭應用程式圖示](assets/aem-desktopapp-architecture.png)

使用此架構，案頭應用程式會截取檔案系統呼叫（開啟、關閉、讀取、寫入等）至已載入的網路共用，並將它們轉譯為伺服器的AEM原生HTTPAEM呼叫。 檔案會快取至本機。 如需詳細資訊，請參閱「使用案頭AEM應用程式v1.x](use-app-v1.md)」。[

## AEM案頭應用程式元件概觀{#desktop-app-component-overview}

案頭應用程式包含下列元件：

* **案頭應用程式**:應用程式將DAM裝載或卸載為遠程檔案系統，並在本地裝載的網路共用和它所連接的遠程實例之間AEM轉換檔案系統調用。
* **作業系統WebDAV/SMB客戶端**:處理Windows檔案總管/Finder和案頭應用程式之間的通訊。如果擷取、建立、修改、刪除、移動或複製檔案，作業系統(OS)WebDAV/SMB用戶端會將此作業傳送至案頭應用程式。 在收到通訊後，案頭應用程式會將它轉譯為原生AEM遠端API呼叫。 例如，如果用戶在掛載的目錄中建立檔案，WebDAV/SMB客戶端將啟動請求，案頭應用程式將其轉換為在DAM中建立檔案的HTTP請求。 WebDAV/SMB客戶端是作業系統的內置元件。 它不與案頭應用程式、AEM或Adobe相關。
* **Adobe Experience Manager實例**:提供對儲存在AEM AssetsDAM儲存庫中的資產的訪問。此外，它會代表與掛載的網路共用互動的本機案頭應用程式，執行案頭應用程式要求的動作。 目標實AEM例應運行AEM版本6.1或更高版本。 執行舊AEM版的例AEM項可能需要安裝額外的功能套件和Hotfix，才能完全發揮功能。

## 案頭應用程AEM式{#intended-use-cases-for-aem-desktop-app}的預期使用案例

案頭應AEM用程式使用網路共用技術，將遠AEM端儲存庫對應至本機案頭。 但是，它不是用來取代網路共用持有資產，即用戶直接從本機案頭執行數位資產管理操作。 這些功能包括移動或複製多個檔案，或直接在Finder/Explorer中將大型資料夾結構拖曳至AEM Assets網路共用。

案頭應AEM用程式提供在AEM AssetsTouch UI和本機案頭之間存取（開啟）和編輯（儲存）DAM資產的便利方式。 它會將AEM Assets伺服器中的資產與您案頭工作流程連結。

以下範例使用案例說明應AEM如何使用Desktop:

* 使用者登入並使AEM用網頁UI來尋找資產。
* 使用網頁UI的案頭AEM動作功能，使用者可視需要在案頭上開啟、顯示或編輯資產。
* 桌AEM面會在資產檔案類型的預設編輯器中開啟資產。
* 使用者對資產進行所需的變更。
* 修改檔案後，用戶可以使用案頭的後台同步狀態窗口查看AEM檔案的同步狀態。
* 使用「案頭」的上AEM下文選單，使用者會簽入／簽出資產，或返回DAM使用者介面。
* 完成對檔案的變更後，使用者會返回網AEM頁UI

這並非唯一的使用案例。 不過，它說明Desktop是AEM本機存取／編輯資產的便利機制。 我們建議您盡可能使用DAM網頁UI，因為它可提供更佳的體驗。 它為Adobe提供了更大的靈活性，以滿足客戶需求。

## 限制 {#limitations}

WebDAV/SMB1網路共用為在Explorer/Finder窗口中處理檔案提供了方便。 但是， Explorer/Finder透過具AEM有特定限制的網路連線進行通訊。 例如，將1-GB檔案複製至已載入的WebDAV/SMB目錄所耗用的時間，與使用Web瀏覽器將1-GB檔案上傳至網站所需的時間大致相同。 事實上，在前一種情況下，由於WebDAV/SMB協定和作業系統的WebDAV/SMB客戶端（尤其是Mac OS X）效率低下，持續時間可能會更長。

從掛載的目錄可以執行的任務類型有一些限制。 一般而言，處理大型檔案（尤其是在低／高延遲／低頻寬網路連線上）可能很有挑戰性，尤其是在編輯大型檔案時。

Adobe建議您在向客戶端提交某些類型的檔案之前，先執行一些使用案例測試，以便從掛載的目錄高效地就地編輯這些檔案。

桌AEM面不適合執行密集的檔案系統操作，包括但不限於：

* 移動或複製檔案和目錄
* 新增許多資產AEM至
* 通過檔案系統搜索和開啟檔案（瀏覽資料夾除外）
* 壓縮或解壓縮檔案存檔

由於作業系統的限制，Windows的檔案大小限制為4,294,967,295位元組（約4.29 GB）。 這是由於註冊表設定，它定義了網路共用上的檔案的大小。 註冊表設定的值是DWORD，其最大大小等於引用的數字。

[!DNL Experience Manager] 案頭應用程式沒有可設定的逾時值，此值會在固定時間間隔後 [!DNL Experience Manager] 中斷伺服器與案頭應用程式之間的連線。上傳大型資產時，如果連線在一段時間後逾時，應用程式會增加上傳逾時，重新嘗試上傳資產幾次。 不建議使用任何方法來變更預設逾時設定。

## 快取與AEM{#caching-and-communication-with-aem}通訊

案頭應AEM用程式提供內部快取和背景上傳功能，以改善使用者體驗。 當您儲存大型檔案時，它會先儲存在本機，讓您繼續工作。 在某個時候（目前為30秒）後，就會將檔案傳送至背AEM景伺服器。

與Creative Cloud案頭或其他檔案同步解決方案（如Microsoft One Drive）不同，案頭應用程AEM式不是完整的案頭同步用戶端。 其原因是它提供了對整個AEM Assets儲存庫的訪問，該儲存庫可能非常大（數百GB或TB），以實現完全同步。

快取功能可將網路／儲存空間開銷限制在與使用者相關的資產子集。

>[!CAUTION]
>
>Adobe建議關閉縮圖產生功能，以加快瀏覽速度。 如果您啟用圖示預覽，應用程式會在您瀏覽已載入的檔案夾時快取數位資產。 應用程式也會下載使用者可能不在乎的資產，這會增加伺服器的負載、耗用使用者的頻寬，並且會佔用使用者的更多磁碟空間。

以下是案頭應AEM用程式執行快取的方式：

* 當您在Finder中開啟檔案夾並顯示檔案的縮圖／預覽，或當您在應用程式中開啟檔案時，案頭應用程式會快取檔案二進位檔。
* 當您透過Finder或其他案頭應用程式儲存檔案時，會先在本機（快取）儲存檔案，並通知作業系統。 然後，檔案會排入佇列，等候上傳至背景的伺服器，最終透過網路上傳。 萬一發生網路錯誤，案頭應用程式會嘗試上傳整個檔案，最多三次。 如果在三次重試後無法上傳，檔案會標示為衝突的檔案，並透過「背景上傳佇列狀態」視窗顯示狀態。 案頭應用程式不會再嘗試更新檔案。 使用者應更新檔案，並在連線恢復後重新上傳檔案

每個操作都不會在本地快取。 以下內容會立即傳送到伺服AEM器，而不需進行本機快取：

* 對資料夾執行的任何操作，例如建立、刪除等
* 1.4 版中加入的「檔案夾上傳」功能可上傳本機檔案夾階層，而不需在本機快取檔案

## 單個操作{#individual-operations}

對個別使用者的未最佳化效能進行疑難排解時，請先檢閱[應用程式限制](#limitations)。 後續各節包含改善個別使用者效能的建議。

## 頻寬建議{#bandwidth-recommendations}

單個用戶可用的頻寬對WebDAV/SMB客戶端的效能起著關鍵作用。

Adobe建議個別使用者的上傳速度接近10 Mbps。 對於無線連接，頻寬通常在多個用戶之間共用。 如果多個用戶同時執行消耗網路頻寬的任務，效能可能會進一步降低。 為避免此類問題，請使用有線連接。

## Windows特定配置{#windows-specific-configurations}

如果您在Windows上使用Experience Manager，可以配置Windows以增強WebDAV客戶端的效能。 如需詳細資訊，請前往[https://support.microsoft.com/en-us/kb/2445570](https://support.microsoft.com/en-us/kb/2445570)。

在Windows 7中，修改IE設定可改善WebDAV的效能。 如需詳細資訊，請參閱如何在Windows 7](https://oddballupdate.com/2009/12/fix-slow-webdav-performance-in-windows-7/)中修正緩慢的WebDAV效能。[

<!-- TBD: The above performance tip is for Windows 7 which is not supported by the app anymore. Remove it later.
-->

## 併發操作{#concurrent-operations}

當您在本機與檔案互動時，AEMDesktop會檢查中是否有較新版本的檔案AEM。 如果有新版本，應用程式會將檔案的新副本下載至本機快取。 但是，如AEM果已修改本機快取檔案，Desktop不會覆寫它。 此功能可防止您的作品不慎覆寫。

當同一個檔案同時在本地和在中修改時，本AEM地修改的版本將覆蓋中的版AEM本。 在此情況下，舊版可在資產時間軸中使用。 您可以驗證兩個版本並解決任何衝突。

如果本機檔案與伺服器中可用的版本不一致，背景上傳狀態對話方塊會通知您有關衝突。 若要解決問題，請開啟衝突的檔案並加以儲存。 儲存檔案會強AEM制Desktop將您最新的本機變更同步至AEM。 您可以在時間軸中檢視資產的先前版本，並解決任何衝突。

當多位使用者嘗試在針對相同例項的個別已載入目錄中工作時，您應考量其他AEM因素。 特別是，以下因素很重要：

* 用戶的源網路上可用的頻寬量
* 原始網路的網路配置，如防火牆或代理
* 目標實例網路中可AEM用的頻寬量
* 目標實例之前是否存在調AEM度器
* 目標實例的當前負AEM載

## 其AEM他配置{#additional-aem-configurations}

如果WebDAV/SMB效能在多個用戶同時工作時嚴重降低，則可以在中配置一些內容AEM，這有助於提高效能。

## 更新資產暫時性工作流程{#update-asset-transient-workflows}

您可以啟用DAM更新資產AEM工作流程的暫時性工作流程，以改善效能。 啟用暫時性工作流程，可降低在中建立或修改資產時更新資產所需的處理能力AEM。

1. 導覽至要設定的例AEM項中的`/miscadmin`（例如`http://[Server]:[Port]/miscadmin`）。
1. 從導覽樹狀結構中，展 **開「工具** >工 **作流程** >模 **型>** dam ****」。
1. 連按兩下&#x200B;**DAM更新資產**。
1. 從浮動工具面板切換至&#x200B;**Page**&#x200B;標籤，然後按一下&#x200B;**Page Properties**。
1. 選中&#x200B;**瞬態工作流**&#x200B;複選框，然後按一下&#x200B;**確定**。

### 調整 Granite 暫時工作流程佇列 {#adjust-granite-transient-workflow-queue}

另一種提高AEM效能的方法是為Granite Transient Workflow Queue作業配置最大並行作業的值。 建議的值大約是伺服器可用CPU數的一半。 要調整值，請執行以下步驟：

1. 導覽至要設定之例項中的&#x200B;*/system/console/configMgr*(AEM例如`http://[aem_server]:[port]/system/console/configMgr`)。
1. 搜索&#x200B;**QueueConfiguration**，然後按一下以開啟每個作業，直到找到&#x200B;**Granite Transient Workflow Queue**&#x200B;作業。 按一下旁邊的編輯。
1. 更改&#x200B;**最大並行作業數**&#x200B;值，然後按一下&#x200B;**保存**。

## AWS配置{#aws-configuration}

由於網路頻寬限制，當多個用戶同時工作時，WebDAV/SMB的效能可能會降低。 Adobe建議增加在AWS上運行的目標實例AEM的AWS實例大小，以增強WebDAV/SMB的效能。

此措施特別提高了伺服器可用的網路頻寬量。 以下是一些細節：

* 專用於AWS實例的網路頻寬量隨著實例大小的增加而增加。 有關每個實例大小的可用頻寬資訊，請參閱[AWS文檔](https://aws.amazon.com/ec2/instance-types/)。
* 對大型客戶機進行故障排除時，Adobe將其實例的大小配置為AEMc4.8xlarge，主要用於4000 Mbps的專用頻寬。
* 如果實例前面有調度器，AEM請確保其大小適當。 如果實AEM例提供4000 Mbps，但調度程式僅提供500 Mbps，則有效頻寬僅為500 Mbps。 這是因為調度程式造成了網路瓶頸。

## 簽出檔案限制{#checked-out-file-limitations}

您可透過Explorer/Finder與已簽出檔案互動的方式有一些已知限制。 如果檔案已簽出，則除已簽出該檔案的用戶外，其他任何人都應該只讀。 WebDAV/SMB1協定的實施將實施AEM此規則。 但是，OS WebDAV/SMB客戶端通常無法與已簽出的檔案正常交互。 以下說明一些怪異之處。

### 一般 {#general}

寫入已簽出檔案時，僅在WebDAV實施中強制AEM執行鎖定。 因此，鎖定僅由使用WebDAV（如案頭應用程式）的用戶端執行。 此鎖定不會透過網頁介AEM面執行。 介AEM面只會在已簽出的資產的卡片檢視中顯示鎖定圖示。 圖示是修飾的，對其行為沒有影AEM響。

一般而言，WebDAV用戶端的行為並不總是如預期般。 可能還有其他問題。 不過，重新整理或檢查AEM資產是確認資產未修改的良好方式。 這是OS WebDAV客戶端的典型行為，不受Adobe的控制。

### Windows {#windows}

刪除檔案似乎成功，因為該檔案從Windows的檔案資源管理器中消失。 不過，重新整理目錄並簽AEM入資產會顯示檔案仍然存在。 此外，編輯檔案似乎成功（未顯示警告對話框或錯誤訊息）。 不過，重新開啟檔案或簽入AEM資產會顯示檔案未變更。

#### Mac OS X {#mac-os-x}

取代檔案不會顯示警告或錯誤，但是將資產勾選AEM會顯示其維持不變。 重新整理或簽入資AEM產，以確認資產未修改。

## 案頭應用程式圖示問題疑難排解(Mac OS X){#troubleshooting-desktop-app-icon-issues-mac-os-x}

安裝案頭應用程式後，案頭應用程式選單圖示會出現在選單列中。 如果未顯示該表徵圖，請執行以下步驟以解決問題：

1. 開啟作業系統終端窗口。
1. 在命令提示符下鍵入以下命令，然後按Enter鍵：

   ```shell
    cd ../Library/Caches.
   ```

1. 鍵入以下命令，然後按Enter:

   ```shell
   rm -r com.adobe.aem.assetscompanion
   ```

1. 鍵入以下命令，然後按Enter:

   ```shell
   cd ~/Library/Preferences
   ```

1. 鍵入以下命令，然後按Enter:

   ```shell
   rm com.adobe.aem.assetscompanion.plist
   ```

1. 鍵入以下命令，然後按Enter:

   ```shell
   rm ~/Library/Group\ Containers/group.com.adobe.aem.desktop/*
   ```

1. 重新啟動系統。

桌AEM面嘗試同步任何給定檔案三次。 如果檔案在第三次嘗試後無法同步，AEMDesktop會認為檔案有衝突，並透過背景上傳狀態視窗通知您。 衝突狀態表示您的最新變更仍可在本機使用，但不會同步回AEM。 案頭應AEM用程式不再嘗試同步。

要修正此情況，最簡單的方法是開啟衝突的檔案，然後再次儲存。 它強AEM制Desktop嘗試在另外三個情況下進行同步。 如果檔案仍無法同步，請參閱下列章節以取得更多說明。

## 清除AEM案頭快取{#clearing-aem-desktop-cache}

清除桌AEM面的快取是一項初步的故障排除任務，可解決幾AEM個案頭問題。

通過刪除應用程式在以下位置的快取目錄，可以清除快取。
在Windows中，`%LocalAppData%\Adobe\AssetsCompanion\Cache\`

在Mac中，`~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/`

但是，位置會根據案頭的AEM配置端點而變AEM化。 值是目標URL的編碼版本。 例如，如果應用程式鎖定`http://localhost:4502`，則目錄名稱為`http%3A%2F%2Flocalhost%3A4502%2F`。

要清除快取，請刪除&lt;編碼端AEM點>目錄。

>[!NOTE]
>
>如果清除案頭AEM快取，則未同步至的本機檔案變AEM更會遺失。

>[!NOTE]
>
>從案頭應AEM用程式1.5版開始，案頭應用程式UI中有一個選項可清除快取。

## 查找AEM案頭版本{#finding-the-aem-desktop-version}

Windows和Mac OS的AEM案頭版本確定程式相同。

按一下「AEMDesktop（案頭）」表徵圖，然後選擇&#x200B;**About**。 版本號碼顯示在螢幕上。

## 在macOSAEM上升級案頭應用程式{#upgrading-aem-desktop-app-on-macos}

在macOS上升級案頭應用程AEM式時，偶爾會發生問題。 這是由於案頭應用程式的舊AEM系統資料夾造成案頭應用程式無法正AEM確載入新版本。 要解決此問題，可以手動刪除以下資料夾和檔案。

在執行下列步驟之前，請將「Adobe Experience Manager案頭」應用程式從macOS Applications檔案夾拖曳至「垃圾筒」。 然後開啟終端機，並執行下列命令，在出現提示時提供您的密碼。

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## 保存其他人{#saving-a-file-checked-out-by-others}簽出的檔案

作業系統的技術限制，讓使用者在嘗試覆寫其他人已簽出的檔案時，無法獲得一致的使用體驗。 體驗會依用來編輯已簽出檔案的應用程式而有所不同。 有時，應用程式會顯示一條錯誤消息，指示磁碟寫入失敗，或顯示一個看似不相關或一般的錯誤。 在其他情況下，不會顯示錯誤訊息，且操作似乎成功。

在這種情況下，關閉和重新開啟檔案可能會顯示內容未變更。 不過，有些應用程式可能會儲存檔案的備份，以便套用您的變更。

不論您的行為如何，檔案都會在您登入時維持不變。 即使顯示不同版本的檔案，更改也不會同步到AEM。

## 疑難排解移動檔案{#troubleshooting-problems-around-moving-files}時的問題

伺服器API需要傳遞額外的標題、X-Destination、X-Depth和X-Overwrite，才能讓移動和復製作業運作。 預設情況下，調度程式不會傳遞這些標頭，這會導致這些操作失敗。 有關詳細資訊，請參見[ Connecting to AEM Bethind a Dispatcher](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher)。

## 案頭AEM連接問題疑難排解{#troubleshooting-aem-desktop-connection-issues}

### SAML重新導向問題{#saml-redirect-issue}

Desktop連線至您的AEMSSO啟用(SAML)例項時，最常見的原因AEM是SAML程式不會重新導向回原本要求的路徑。 或者，該連接可被重定向到未在案頭中配置的AEM主機。 執行下列步驟以驗證登入程式：

1. 開啟網頁瀏覽器。
1. 在位址列中，指定URL `/content/dam.json`。
1. 將URL取代為目AEM標例項，例如`http://localhost:4502/content/dam.json`。
1. 登入AEM。
1. 登入後，在位址列中檢查瀏覽器的目前位址。 它應符合您最初輸入的URL。
1. 驗證`/content/dam.json`之前的所有項目是否與Desktop中AEM配置的目AEM標值相符。

### SSL配置問題{#ssl-configuration-issue}

案頭應用程AEM式用於HTTP通訊的程式庫採用嚴格的SSL強制。 連線有時可能會成功使用瀏覽器，但無法使用案頭應AEM用程式。 若要正確設定SSL，請在Apache中安裝遺失的中間憑證。 請參閱[如何在Apache](https://access.redhat.com/solutions/43575)中安裝Intemider CA憑證。

## 使用AEMDesktop與dispatcher {#using-aem-desktop-with-dispatcher}

桌AEM面可與AEMDispatcher後面的部署搭配使用，這是伺服器的預設和建議AEM組態。 在制AEM作環境之前的AEM調度程式通常配置為跳過快取DAM資產。 因此，調度程式不會從案頭角度提供額外的AEM快取。 確保調整調度器配置以適用於AEMDesktop。 有關其他詳細資訊，請參見[ Connecting AEM to bethand a dispatcher](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher)。

## 正在檢查日誌檔案{#checking-for-log-files}

根據您的作業系統，您可以在以下位置找到AEMDesktop的日誌檔案：

* Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`
* Mac:`~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`
