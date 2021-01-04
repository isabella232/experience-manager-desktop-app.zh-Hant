---
title: 安裝並設定 [!DNL Experience Manager] 案頭應用程式1.x版
description: 安裝並配置 [!DNL Experience Manager] desktop app version 1.x to work with [!DNL Assets] 伺服器，並將資產映射為在案頭上作為驅動器裝載。
translation-type: tm+mt
source-git-commit: a25c1fa13895ae9eb7268e3e01c83a5f0b9d7d1d
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 0%

---


# 安裝並配置[!DNL Experience Manager]案頭應用程式v1.x {#install-and-configure-aem-desktop-app}

使用[!DNL Experience Manager]案頭應用程式，您就可輕鬆存取[!DNL Experience Manager]中的資產，並可用於任何案頭應用程式。 資產可在Mac Finder或Windows檔案總管中輕鬆顯示、在案頭應用程式中開啟，並在本機變更——當您上傳時，變更會儲存回[!DNL Experience Manager]，並在儲存庫中建立新版本。

此類整合可讓組織中的不同角色集中管理資產，並在Creative Cloud和其他應用程式中存取資產，同時輕鬆符合包括品牌在內的各種標準。

若要使用[!DNL Experience Manager]案頭應用程式，

* 確保[!DNL Experience Manager]案頭應用程式支援您的[!DNL Experience Manager]伺服器版本。 請參閱[相容性矩陣](release-notes-of-v1.md#compatibilitymatrix)。

* 下載並安裝應用程式。

* 使用幾個資產測試連線。 請參閱[存取和開啟案頭上的資產](use-app-v1.md#openondesktop)。

## 系統需求、先決條件和下載連結{#system-requirements-prerequisites-and-download-links}

如需詳細資訊，請參閱[[!DNL Experience Manager] 案頭應用程式版本注意事項](release-notes-of-v1.md)。

## 安裝應用程式並將它連接至[!DNL Experience Manager]伺服器{#install-and-connect-aem-desktop-app-to-aem-server}

有關詳細資訊，請參閱[安裝並連接 [!DNL Experience Manager] desktop app to [!DNL Experience Manager] 伺服器](use-app-v1.md#installandconnect)。

>[!NOTE]
>
>一次只能安裝一個[!DNL Experience Manager]案頭應用程式的執行個體並處於活動狀態。

## 檔案處理{#file-handling}

當從案頭應用程式載入的網路共用位置變更檔案時，檔案會分兩個階段儲存至該位置。 在第一階段，檔案會儲存在本機。 使用者可儲存檔案並繼續處理檔案，而不需等待傳輸完成。

在第二階段，案頭應用程式會在預先定義的延遲（例如30秒）後，將更新的檔案上傳至[!DNL Experience Manager]伺服器。 此操作在後台進行。 使用「查看資產狀態」選項可查看上載操作的狀態。

1. 上傳資產至資產。

1. 按一下工具列上的[!DNL Experience Manager]案頭應用程式圖示。

1. 從菜單中，選擇「查看資產狀態」選項。

1. 從對話方塊中，檢視上傳作業的狀態。

>[!NOTE]
>
>[!DNL Experience Manager] 案頭應用程式可處理大小高達40 GB的資產。

## 連接到調度程式{#connect-to-an-aem-instance-behind-a-dispatcher}後面的[!DNL Experience Manager]實例

資產API中的複製和移動方法需要將下列額外標題傳遞至[!DNL Experience Manager]:

* X目標
* X-深度
* X覆寫

[!DNL Experience Manager] 案頭會使 [!DNL Experience Manager] 用包含預設連接埠的URL連線至。因此，調度器配置中的`virtualhosts`設定應包含預設埠號。 有關`virtualhosts`配置的詳細資訊，請參見[ identify virtual hosts](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#identifying-virtual-hosts-virtualhosts)。

有關配置調度程式以通過這些附加標頭的其他資訊，請參見[指定HTTP標頭](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#specifying-the-http-headers-to-pass-through-clientheaders)。

### 代理支援{#proxy-support}

[!DNL Experience Manager] 案頭應用程式使用系統預先定義的代理，透過HTTPS連線至網際網路。應用程式只能使用不需要額外驗證的網路代理進行連線。

如果您為Windows配置或修改代理伺服器設定（「Internet選項」>「LAN設定」），請重新啟動[!DNL Experience Manager]案頭應用程式以使更改生效。

>[!NOTE]
>
>只有在啟動案頭應用程式時，才會套用Proxy設定。 關閉並重新啟動應用程式，讓任何變更生效。

如果您的代理需要驗證，IT團隊可以允許代理伺服器設定中的Experience Manager Assets URL，以允許應用程式流量傳遞。

## 自訂「資產資訊」對話方塊{#customize-the-asset-info-dialog}

您可以通過覆蓋下列其中一個或兩個元件來自定義「資產資訊」對話框：

* 位於`/libs/dam/gui/content/assets/moreinfo`的Granite用戶介面頁。

* `/libs/dam/gui/components/admin/moreinfo`處的HTL `/css/javascript`元件。

哪個元件是重疊的，取決於自訂的性質。 若要變更在「資產資訊」對話方塊中顯示的元件，請覆蓋「花崗岩」使用者介面頁面。 若要變更對話方塊的HTML、CSS或JavaScript內容，請覆蓋HTL元件。

## 管理快取{#manage-cache}

在Windows上，快取位於`%LOCALAPPDATA%\Adobe\AssetsCompanion\Cache\`，其中是案頭應用程式中設定之[!DNL Experience Manager]主機的編碼版本。 例如，`http://localhost:4502`顯示為`http%3A%2F%2Flocalhost%3A4502%2F`。

在Mac OS X上，類似的目錄位於`~/Library/Group Containers/group.com.adobe.aem.desktop/cache`。

### 管理快取的應用程式內選項{#in-app-option-to-manage-cache}

您可以控制可用於本地快取的磁碟空間量。 來自Assets伺服器的物件會在本機快取，以提供更順暢的體驗。 您可以變更預設值以符合您的需求。 此外，您也可以清除快取，重新擷取所有資產。 若要設定所需的選項，請按一下應用程式的圖示，然後按一下&#x200B;**[!UICONTROL Advanced]** > **[!UICONTROL Manage Cache]**。****

>[!NOTE]
>
>清除快取時，它會保留未儲存的變更。 未簽入[!DNL Experience Manager]伺服器的任何資產都將保留並不刪除。

### 更改Windows {#change-location-of-cache-on-windows}上快取的位置

[!DNL Experience Manager]案頭應用程式的快取預設位置如下：

* 在Windows中，`%LocalAppData%\Adobe\AssetsCompanion\Cache\EncodedAEMEndpoint`。

* 在Mac中，`~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/EncodedAEMEndpoint`。

`EncodedAEMEndpoint` 是應用程式的設定 [!DNL Experience Manager] 端點URL。值是[!DNL Experience Manager]伺服器的目標URL編碼版本。 例如，如果應用程式鎖定`http://localhost:4502`，則目錄名稱為`http%3A%2F%2Flocalhost%3A4502`。 此示例中到快取目錄的Windows路徑為`%LocalAppData%\Adobe\AssetsCompanion\Cache\http%3A%2F%2Flocalhost%3A4502`。

要將應用程式指向不同的資料夾或驅動器，請編輯應用程式的配置檔案。

1. 導覽至應用程式的安裝目錄。 Windows上的預設位置為`C:\Program Files (x86)\Adobe\Adobe Experience Manager Desktop`。

1. 使用文字編輯器編輯Adobe Experience Manager Desktop.exe.config檔案。

   要保存對此檔案所做的更改，需要管理員權限。

1. 搜尋字串&quot;ProxyCacheRoot&quot;。 您會看到其值已設為快取位置`%LocalAppData%\Adobe\AssetsCompanion\Cache`。 只要將此值變更為任何有效路徑即可。

   >[!NOTE]
   >
   >應用程式會自動建立&#x200B;*&lt;Encoded AEM Endpoint>*&#x200B;子目錄。 此行為不可配置。

>[!MORELIKETHIS]
* [案頭應 [!DNL Experience Manager] 用程式簡介](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/aem-desktop-app.html)。
* [使用 [!DNL Experience Manager] 案頭應用程式](use-app-v1.md)。
* [疑難 [!DNL Experience Manager] 排解案頭應用程式](troubleshoot-app-v1.md)。

