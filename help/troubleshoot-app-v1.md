---
title: 對案頭應用1.10版進行故障排除。
description: 故障排除 [!DNL Adobe Experience Manager] 案頭應用1.10版，以解決與安裝、升級和配置相關的偶發問題。
exl-id: 1e1409c2-bf5e-4e2d-a5aa-3dd74166862c
source-git-commit: 2ae49374b362921a5a82fc2e040064b4e573b8c1
workflow-type: tm+mt
source-wordcount: '3291'
ht-degree: 1%

---

# 故障排除 [!DNL Adobe Experience Manager] 案頭應用v1.x {#troubleshoot-aem-desktop-app}

排除AEM案頭應用的故障，以解決與安裝、升級、配置等相關的偶發問題。

[!DNL Adobe Experience Manager] 案頭應用包括實用程式，可幫助您將AEM Assets儲存庫映射為案頭上的網路共用(MacOS上的SMB共用)。 網路共用是一種作業系統技術，它使遠程源能夠被視為電腦本地檔案系統的一部分。 在案頭應用中，遠程實AEM例的數字資產管理(DAM)儲存庫結構將作為遠程檔案源。 下圖描述了案頭應用拓撲：

![案頭應用程式圖](assets/aem-desktopapp-architecture.png)

使用此體系結構，案頭應用會截取檔案系統調用（開啟、關閉、讀取、寫入等）到已掛載的網路共用，並將它們轉換為對伺服器的AEM本機HTTP調AEM用。 檔案在本地快取。 有關詳細資訊，請參閱 [使用AEM案頭應用v1.x](use-app-v1.md)。

## AEM案頭應用元件概述 {#desktop-app-component-overview}

案頭應用包括以下元件：

* **案頭應用程式**:應用程式將裝載或卸載DAM作為遠程檔案系統，並在本地裝載的網路共用和它所連接的遠程實例之間AEM轉換檔案系統調用。
* **作業系統WebDAV/SMB客戶端**:處理Windows Explorer/Finder和案頭應用之間的通信。 如果檢索、建立、修改、刪除、移動或複製檔案，則作業系統(OS)WebDAV/SMB客戶端會將此操作傳送到案頭應用。 在接收通信後，案頭應用將其轉換為本機AEM遠程API調用。 例如，如果用戶在已裝載的目錄中建立檔案，WebDAV/SMB客戶端將啟動請求，案頭應用將該請求轉換為在DAM中建立檔案的HTTP請求。 WebDAV/SMB客戶端是作業系統的內置元件。 它不以任何方式與案頭應AEM用或Adobe相關。
* **Adobe Experience Manager實例**:提供對儲存在AEM AssetsDAM儲存庫中的資產的訪問。 此外，它代表與掛載的網路共用交互的本地案頭應用程式執行案頭應用程式請求的操作。 目標實AEM例應運行AEM6.1版或更高版本。 運行AEM以前版AEM本的實例可能需要安裝額外的功能包和熱修復程式才能完全正常工作。

## 案頭應用的預AEM期使用案例 {#intended-use-cases-for-aem-desktop-app}

桌AEM面應用使用網路共用技術將遠程儲存庫AEM映射到本地案頭。 但是，它不是作為網路共用持有資產的替代品，在該資產中，用戶直接從其本地案頭執行數字資產管理操作。 這包括移動或複製多個檔案，或將大型資料夾結構直接拖到Finder/Explorer中的AEM Assets網路共用中。

案頭應AEM用提供了在AEM AssetsTouch UI和本地案頭之間訪問（開啟）和編輯（保存）DAM資產的便捷方式。 它將AEM Assets伺服器中的資產與您基於案頭的工作流連結起來。

以下示例用例說明應AEM如何使用Desktop:

* 用戶登錄並AEM使用Web UI查找資產。
* 使用Web UI的案頭操AEM作功能，用戶可根據需要開啟、顯示或編輯案頭上的資產。
* 桌AEM面在預設編輯器中為資產的檔案類型開啟資產。
* 用戶對資產進行所需的更改。
* 修改檔案後，用戶可以使用案頭的後台同步狀態窗AEM口查看檔案的同步狀態。
* 使用「案頭」(AEMDesktop)的上下文菜單，用戶將簽入/取出資產，或返回DAM用戶介面。
* 完成對檔案的更改後，用戶返回到WebAEM UI

這不是唯一的用例。 但是，它說明了AEMDesktop是在本地訪問/編輯資產的方便機制。 我們鼓勵您盡可能多地使用DAM Web UI，因為它提供了更好的體驗。 它為Adobe提供了更大的靈活性以滿足客戶需求。

## 限制 {#limitations}

WebDAV/SMB1網路共用為在Explorer/Finder窗口中處理檔案提供了方便。 但是， Explorer/Finder通過具AEM有某些限制的網路連接進行通信。 例如，將1 GB檔案複製到已裝載的WebDAV/SMB目錄所花費的時間與使用Web瀏覽器將1 GB檔案上載到網站所需的時間大致相同。 事實上，在前一種情況下，由於WebDAV/SMB協定和作業系統的WebDAV/SMB客戶端(特別是MacOS X)的效率低下，持續時間可能會更長。

可以從已裝載目錄執行的任務類型存在限制。 通常，處理大檔案（尤其是在低/高延遲/低頻寬網路連接上）可能是一個難題，尤其是在編輯大檔案時。

Adobe建議在向客戶端提交某些類型的檔案可以從已裝載的目錄就地高效編輯之前，執行一些用例測試。

桌AEM面不適合執行密集的檔案系統操作，包括但不限於：

* 移動或複製檔案和目錄
* 將許多資產添加到AEM
* 通過檔案系統搜索和開啟檔案（瀏覽資料夾除外）
* 壓縮或解壓縮檔案存檔

由於作業系統的限制， Windows的檔案大小限制為4,294,967,295位元組（約4.29 GB）。 這是因為註冊表設定定義了網路共用上的檔案的大小。 註冊表設定的值是DWORD，其最大大小等於引用的編號。

[!DNL Experience Manager] 案頭應用沒有可配置的超時值，該超時值會斷開與 [!DNL Experience Manager] 伺服器和案頭應用。 上載大型資產時，如果連接在一段時間後超時，則應用會通過增加上載超時來重試多次上載資產。 沒有建議的更改預設超時設定的方法。

## 快取和通AEM信 {#caching-and-communication-with-aem}

案頭應AEM用提供內部快取和後台上載功能，以改進最終用戶體驗。 保存大檔案時，首先將其保存到本地，以便繼續工作。 在某個時間（當前為30秒）後，檔案將發送到後台AEM的伺服器。

與Creative Cloud案頭或其他檔案同步解決方案(如Microsoft一驅動器)不AEM同，案頭應用不是完整的案頭同步客戶端。 其原因是它提供了對整個AEM Assets儲存庫的訪問權限，該儲存庫可能非常大（數百GB或TB），以實現完全同步。

快取提供了將網路/儲存開銷限制為僅與用戶相關的資產子集的能力。

>[!CAUTION]
>
>Adobe建議關閉縮略圖生成，以加快瀏覽速度。 如果啟用表徵圖預覽，則在您瀏覽已裝入的資料夾時，應用會快取數字資產。 該應用還下載用戶可能不關心的資產，這會增加伺服器負載，佔用用戶頻寬，並佔用用戶的更多磁碟空間。

以下是案頭應AEM用如何執行快取：

* 當您在Finder中開啟資料夾並顯示檔案的縮略圖/預覽時，或者當您在應用程式中開啟檔案時，案頭應用會快取檔案二進位檔案。
* 當您通過Finder或其他案頭應用程式儲存檔案時，首先在本地（快取）儲存該檔案，並通知作業系統。 然後，檔案將排隊上傳到後台伺服器，並最終通過網路上傳。 如果出現網路錯誤，案頭應用將重試上載整個檔案最多三次。 如果在三次重試後無法上載，則檔案被標籤為衝突檔案，並且狀態通過「後台上載隊列狀態」窗口顯示。 案頭應用不再嘗試更新該檔案。 用戶應在恢復連接後更新檔案並重新上載

每個操作都不在本地快取。 以下內容會立即在不AEM使用本地快取的情況下傳輸到伺服器：

* 對資料夾執行的任何操作，如建立、刪除等
* 1.4 版中加入的「檔案夾上傳」功能可上傳本機檔案夾階層，而不需在本機快取檔案

## 單個操作 {#individual-operations}

對單個用戶的未優化效能進行故障排除時，請首先查看 [應用程式限制](#limitations)。 隨後的部分包括改進個別用戶效能的建議。

## 頻寬建議 {#bandwidth-recommendations}

單個用戶可用的頻寬在WebDAV/SMB客戶端的效能中起著關鍵作用。

Adobe建議單個用戶的上載速度接近10 Mbps。 對於無線連接，頻寬通常在多個用戶之間共用。 如果多個用戶同時執行消耗網路頻寬的任務，效能可能會進一步降低。 要避免此類問題，請使用有線連接。

<!-- AG, 8/18: The Windows KB article is removed by MS now. Giving 404. Also, Win 7 support is gone and the desktop app is also not supported on Win 7. Hiding this content for now.

## Windows-specific configurations {#windows-specific-configurations}

If you use Experience Manager on Windows, you can configure Windows to enhance the performance of the WebDAV client. For more information, go to [https://support.microsoft.com/en-us/kb/2445570](https://support.microsoft.com/en-us/kb/2445570).

On Windows 7, modifying IE settings can improve the performance of WebDAV. For details, see how to [fix slow WebDAV performance in Windows 7](https://oddballupdate.com/2009/12/fix-slow-webdav-performance-in-windows-7/).
-->

## 併發操作 {#concurrent-operations}

在本地與檔案交互時，AEMDesktop會檢查中是否有較新版本的文AEM件。 如果有新版本可用，應用程式會將檔案的新副本下載到本地快取。 但是，AEM如果已修改Desktop，則不覆蓋本地快取的檔案。 此功能可防止您的工作被無意覆蓋。

當本地和在中修改同一檔案AEM時，本地修改的版本將覆蓋中的版AEM本。 在此情況下，以前的版本可在資產的時間軸中使用。 您可以驗證兩個版本並解決任何衝突。

如果本地檔案與伺服器中可用的版本不一致，則後台上載狀態對話框會通知您衝突。 要解決此問題，請開啟衝突檔案並保存它。 保存檔案會強AEM制案頭將最新的本地更改同步AEM到。 您可以在時間軸中查看資產的早期版本並解決任何衝突。

當多個用戶嘗試在針對同一實例的單獨裝入目錄中工作時，應考慮其AEM他因素。 特別是，以下因素很重要：

* 用戶原始網路上可用的頻寬量
* 原始網路的網路配置，如防火牆或代理
* 目標實例網路中可AEM用的頻寬量
* 是否在目標實例之前存在調AEM度程式
* 目標實例上的當前負AEM載

## 其他配AEM置 {#additional-aem-configurations}

如果當多個用戶同時工作時， WebDAV/SMB效能會急劇降低，您可以在中配置一些內容AEM，這有助於提高效能。

## 更新資產臨時工作流 {#update-asset-transient-workflows}

通過啟用DAM更新資產工AEM作流的臨時工作流，可以提高側面的效能。 啟用臨時工作流會降低在中建立或修改資產時更新資產所需的處理AEM能力。

1. 導航到 `/miscadmin` 在Experience Manager實例(`https://[aem_server]:[port]/miscadmin`)。
1. 從導覽樹狀結構中，展 **開「工具** >工 **作流程** >模 **型>** dam ****」。
1. 按兩下 **DAM更新資產**。
1. 從浮動工具面板切換到 **頁面** 按鈕 **頁面屬性**。
1. 選擇 **臨時工作流** 複選框，然後按一下 **確定**。

### 調整 Granite 暫時工作流程佇列 {#adjust-granite-transient-workflow-queue}

另一種提高性AEM能的方法是為Granite Transient Workflow Queue作業配置最大並行作業的值。 建議的值大約是伺服器可用CPU數的一半。 要調整值，請執行以下步驟：

1. 導航到 `/system/console/configMgr` 例AEM如， `https://[aem_server]:[port]/system/console/configMgr`)。
1. 搜索 `QueueConfiguration`，然後按一下以開啟每個作業，直到找到 **花崗岩瞬態工作流隊列** 作業，然後按一下 **編輯**。
1. 更改 `Maximum Parallel Jobs` 值，然後按一下 **保存**。

## AWS配置 {#aws-configuration}

由於網路頻寬的限制，當多個用戶同時工作時，WebDAV/SMB的效能可能會降低。 Adobe建議增加在AWS運行的目標實AEM例的AWS實例大小，以增強WebDAV/SMB的效能。

此度量專門提高伺服器可用的網路頻寬量。 下面是一些詳細資訊：

* 專用於AWS實例的網路頻寬量隨實例大小的增加而增加。 有關每個實例大小可用頻寬的資訊，請參見 [AWS文檔](https://aws.amazon.com/ec2/instance-types/)。
* 在對大型客戶端進行故障排除時，Adobe將其實例的大AEM小配置為c4.8xlarge，主要針對它提供的4000 Mbps專用頻寬。
* 如果實例前面有調度程式AEM，請確保其大小適當。 如果實AEM例提供4000 Mbps，但調度程式僅提供500 Mbps，則有效頻寬僅為500 Mbps。 這是因為調度程式會造成網路瓶頸。

## 簽出檔案限制 {#checked-out-file-limitations}

在通過Explorer/Finder與簽出檔案交互的方式上存在一些已知的限制。 如果檔案已簽出，則該檔案應只讀給除已簽出該檔案的用戶之外的任何用戶。 WebDAV/SMB1協定的實現強制AEM執行此規則。 但是，OS WebDAV/SMB客戶端通常不會與簽出的檔案進行正常交互。 下面介紹一些古怪的事。

### 一般 {#general}

寫入簽出檔案時，僅在AEMWebDAV實現中強制執行鎖。 因此，只有使用WebDAV的客戶端（如案頭應用）才會強制執行鎖定。 未通過Web介面強AEM制鎖定。 該接AEM口僅在卡視圖中顯示已簽出資產的鎖定表徵圖。 該表徵圖是修飾的，對行為無影AEM響。

通常， WebDAV客戶端的行為不總是像預期的那樣。 可能還有其他問題。 但是，刷新或簽入資AEM產是驗證資產是否未修改的可靠方法。 此行為是OS WebDAV客戶端的典型行為，該客戶端不受Adobe控制。

### Windows {#windows}

刪除檔案似乎成功，因為該檔案會從Windows中的檔案資源管理器中消失。 但是，刷新目錄並簽AEM入資產表明檔案仍然存在。 此外，編輯檔案似乎成功（未顯示警告對話框或錯誤消息）。 但是，重新開啟檔案或簽入AEM資產會顯示檔案未更改。

#### MacOS X {#mac-os-x}

替換檔案不會顯示警告或錯誤，但檢入該資AEM產會顯示它保持不變。 刷新或簽入資AEM產以驗證資產是否未被修改。

## 案頭應用表徵圖問題疑難解答(MacOS X) {#troubleshooting-desktop-app-icon-issues-mac-os-x}

安裝案頭應用後，菜單欄中將顯示案頭應用菜單表徵圖。 如果未顯示該表徵圖，請執行以下步驟來解決問題：

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

桌AEM面嘗試同步任何給定檔案三次。 如果檔案在第三次嘗試後無法同步，AEM則Desktop會認為該檔案衝突，並通過後台上載狀態窗口通知您。 衝突狀態表示您的最新更改仍可在本地使用，但未同步回AEM。 案頭應AEM用不再嘗試同步。

修復此情況的最簡單方法是開啟衝突檔案並重新保存。 它強AEM制案頭嘗試另外三次同步。 如果檔案仍無法同步，請參閱下面的各節以獲得更多幫助。

## 清除桌AEM面快取 {#clearing-aem-desktop-cache}

清除AEM案頭的快取是一項初步的故障排除任務，可解決幾AEM個案頭問題。

您可以通過刪除以下位置的應用程式快取目錄來清除快取。
在Windows中， `%LocalAppData%\Adobe\AssetsCompanion\Cache\`

在Mac, `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/`

但是，位置可能會根據桌AEM面的已配置端AEM點而改變。 該值是目標URL的編碼版本。 例如，如果應用程式瞄準 `http://localhost:4502`，目錄名為 `http%3A%2F%2Flocalhost%3A4502%2F`。

要清除快取，請刪除 &lt;encoded aem=&quot;&quot; endpoint=&quot;&quot;> 的子菜單。

>[!NOTE]
>
>如果清除AEM案頭快取，則未同步到的本地檔案更AEM改將丟失。

>[!NOTE]
>
>從案頭應AEM用1.5版開始，案頭應用UI中有一個選項可清除快取。

## 查找桌AEM面版本 {#finding-the-aem-desktop-version}

確定Windows和AEMMacOS的案頭版本的步驟相同。

按一下「Desktop(桌AEM面)」表徵圖，然後選擇 **關於**。 版本號顯示在螢幕上。

## 升級AEMmacOS案頭應用 {#upgrading-aem-desktop-app-on-macos}

在macOS升級案頭應AEM用時，偶爾會出現問題。 這是由於案頭應用的舊系統AEM資料夾阻止正確載入新AEM版本的案頭。 要解決此問題，可以手動刪除以下資料夾和檔案。

在執行以下步驟之前，將「Adobe Experience Manager案頭」應用程式從「macOS應用程式」資料夾拖到「垃圾箱」。 然後開啟終端，然後執行以下命令，在出現提示時提供密碼。

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## 保存其他人簽出的檔案 {#saving-a-file-checked-out-by-others}

作業系統的技術限制使用戶在試圖覆蓋由他人簽出的檔案時無法獲得一致的體驗。 根據用於編輯簽出檔案的應用程式的不同，體驗會有所不同。 有時，應用程式會顯示一條錯誤消息，指示磁碟寫入失敗，或顯示看似不相關或一般的錯誤。 在其他情況下，不顯示錯誤資訊，操作似乎成功。

在這種情況下，關閉並重新開啟檔案可能會顯示內容未更改。 但是，某些應用程式可能會儲存檔案的備份，以便可以應用更改。

無論該行為如何，在簽入時檔案都保持不變。 即使顯示檔案的不同版本，更改也不會同步到AEM。

## 對移動檔案的問題進行故障排除 {#troubleshooting-problems-around-moving-files}

伺服器API需要傳遞其他標頭、X-Destination、X-Depth和X-Overwrite，以便移動和複製操作正常工作。 預設情況下，調度程式不會傳遞這些標頭，這會導致這些操作失敗。 有關詳細資訊，請參見 [連接到AEM調度程式後](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher)。

## 案頭連AEM接問題疑難解答 {#troubleshooting-aem-desktop-connection-issues}

### SAML重定向問題 {#saml-redirect-issue}

Desktop連接到啟AEM用SSO(SAML)實例時出現問題的最常見AEM原因是SAML進程沒有重定向回最初請求的路徑。 或者，可以將連接重定向到未在案頭中配置的AEM主機。 執行以下步驟驗證登錄過程：

1. 開啟Web瀏覽器。
1. 在地址欄中，指定URL `/content/dam.json`。
1. 將URL替換為目標實AEM例，例如 `https://localhost:4502/content/dam.json`。
1. 登錄AEM。
1. 登錄後，在地址欄中檢查瀏覽器的當前地址。 它應與最初輸入的URL匹配。
1. 驗證之前的所有內容 `/content/dam.json` 與案頭中AEM配置的目AEM標值匹配。

### SSL配置問題 {#ssl-configuration-issue}

案頭應用AEM用於HTTP通信的庫使用嚴格的SSL強制。 有時，連接可能使用瀏覽器成功，但使用案頭應AEM用失敗。 要正確配置SSL，請在Apache中安裝缺少的中間證書。 請參閱 [如何在Apache中安裝中間CA證書](https://access.redhat.com/solutions/43575)。

## 將桌AEM面與調度程式一起使用 {#using-aem-desktop-with-dispatcher}

桌AEM面可與AEM調度程式後的部署配合使用，這是伺服器的預設和推薦AEM的配置。 創AEM作環境前AEM的調度程式通常配置為跳過快取DAM資產。 因此，從案頭的角度來看，調度程式不提AEM供附加快取。 確保調度程式配置已調整為適用於AEMDesktop。 有關其他詳細資訊，請參閱 [連接到AEM調度程式後](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher)。

## 正在檢查日誌檔案 {#checking-for-log-files}

根據您的作業系統，您可以在以下位置AEM找到Desktop的日誌檔案：

* Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`
* Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`
