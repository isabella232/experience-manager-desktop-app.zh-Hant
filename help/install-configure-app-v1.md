---
title: 安裝和配置案頭應用v1.10
description: 安裝並配置 [!DNL Experience Manager] desktop app version 1.10 to work with [!DNL Assets] 伺服器，並將要裝載為案頭上驅動器的資產映射。
exl-id: 7f3bdfb1-d345-4e48-b020-6e06531f46f2
source-git-commit: 78f18e68178f711d925d7e308822c657087d009a
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 0%

---

# 安裝並配置[!DNL Experience Manager]案頭應用v1.10 {#install-and-configure-aem-desktop-app}

使用[!DNL Experience Manager]案頭應用程式時，您可輕鬆在本機案頭上存取[!DNL Experience Manager]中的資產，並可用於任何案頭應用程式。 資產可在Mac Finder或Windows Explorer中輕鬆顯示、在案頭應用程式中開啟，並在本機變更 — 當您上傳並在存放庫中建立新版本時，變更會儲存回[!DNL Experience Manager]。

這種整合使組織中的各種角色能夠集中管理資產中的資產，並在Creative Cloud和其他應用程式中訪問這些資產，同時使之易於遵守包括品牌在內的各種標準。

若要使用[!DNL Experience Manager]案頭應用程式，

* 確保[!DNL Experience Manager]案頭應用程式支援您的[!DNL Experience Manager]伺服器版本。 請參閱[相容性矩陣](release-notes-of-v1.md#compatibilitymatrix)。

* 下載並安裝應用程式。

* 使用一些資產來測試連線。 請參閱[在案頭上存取和開啟資產](use-app-v1.md#openondesktop)。

## 系統要求、先決條件和下載連結{#system-requirements-prerequisites-and-download-links}

如需詳細資訊，請參閱[[!DNL Experience Manager] 案頭應用程式發行說明](release-notes-of-v1.md)。

## 安裝應用程式並將其連接到[!DNL Experience Manager]伺服器{#install-and-connect-aem-desktop-app-to-aem-server}

有關詳細資訊，請參閱[安裝並連接 [!DNL Experience Manager] desktop app to [!DNL Experience Manager] server](use-app-v1.md#installandconnect)。

>[!NOTE]
>
>一次只能安裝[!DNL Experience Manager]案頭應用程式的一個實例並處於活動狀態。

## 檔案處理{#file-handling}

從案頭應用程式裝載的網路共用位置變更檔案時，檔案會分兩個階段儲存至該位置。 在第一階段中，檔案會儲存在本機。 使用者可以儲存檔案並繼續處理檔案，而不需等待傳輸完成。

在第二階段中，案頭應用程式會在預先定義的延遲（例如30秒）後，將更新的檔案上傳至[!DNL Experience Manager]伺服器。 此操作在後台進行。 使用「查看資產狀態」選項可查看上載操作的狀態。

1. 上傳資產至資產。

1. 按一下工具列中的[!DNL Experience Manager]案頭應用程式圖示。

1. 從功能表中，選取「檢視資產狀態」選項。

1. 從對話方塊中，檢閱上傳操作的狀態。

>[!NOTE]
>
>[!DNL Experience Manager] 案頭應用程式可處理大小高達40 GB的資產。

## 連線至Dispatcher {#connect-to-an-aem-instance-behind-a-dispatcher}後面的[!DNL Experience Manager]例項

資產API中的複製和移動方法需要將下列其他標題傳遞至[!DNL Experience Manager]:

* X目的地
* X深
* X覆寫

[!DNL Experience Manager] 案頭使用 [!DNL Experience Manager] 包含預設埠的URL連接到。因此，Dispatcher設定中的`virtualhosts`設定應包含預設的埠號。 有關`virtualhosts`配置的詳細資訊，請參閱[標識虛擬主機](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#identifying-virtual-hosts-virtualhosts)。

如需將Dispatcher設定為傳遞這些額外標題的詳細資訊，請參閱[指定HTTP標題](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#specifying-the-http-headers-to-pass-through-clientheaders)。

### 代理支援{#proxy-support}

[!DNL Experience Manager] 案頭應用程式使用系統的預先定義代理，透過HTTPS連線至網際網路。應用程式只能使用不需要額外驗證的網路代理進行連接。

如果配置或修改Windows的代理伺服器設定（Internet選項>區域網路設定），請重新啟動[!DNL Experience Manager]案頭應用程式，使更改生效。

>[!NOTE]
>
>只有在啟動案頭應用程式時，才會套用代理設定。 關閉並重新啟動應用程式，以讓任何變更生效。

如果您的Proxy需要驗證，IT團隊可允許Proxy伺服器設定中的Experience Manager資產URL，以允許應用程式流量傳遞。

## 自訂資產資訊對話方塊{#customize-the-asset-info-dialog}

您可以覆蓋下列其中一個或兩個元件，以自訂「資產資訊」對話方塊：

* 位於`/libs/dam/gui/content/assets/moreinfo`的Granite使用者介面頁面。

* 位於`/libs/dam/gui/components/admin/moreinfo`的HTL `/css/javascript`元件。

哪個元件重疊，取決於自訂的性質。 若要變更顯示為「資產資訊」對話方塊一部分的元件，請覆蓋Granite使用者介面頁面。 若要變更對話方塊的HTML、CSS或JavaScript內容，請覆蓋HTL元件。

## 管理快取{#manage-cache}

在Windows上，快取位於`%LOCALAPPDATA%\Adobe\AssetsCompanion\Cache\`，其中是案頭應用程式中設定的[!DNL Experience Manager]主機的編碼版本。 例如， `http://localhost:4502`顯示為`http%3A%2F%2Flocalhost%3A4502%2F`。

在Mac OS X上，類似的目錄位於`~/Library/Group Containers/group.com.adobe.aem.desktop/cache`。

### 管理快取{#in-app-option-to-manage-cache}的應用程式內選項

您可以控制可用於本地快取的磁碟空間量。 系統會在本機快取資產伺服器中的成品，以提供更流暢的體驗。 您可以變更預設值以符合您的需求。 此外，您也可以清除快取，以重新擷取所有資產。 若要設定所需選項，請按一下應用程式的圖示，然後按一下&#x200B;**[!UICONTROL Advanced]** > **[!UICONTROL Manage Cache]**。****

>[!NOTE]
>
>清除快取時，會保留未儲存的變更。 未簽入[!DNL Experience Manager]伺服器的任何資產都將保留，且不會刪除。

### 更改Windows {#change-location-of-cache-on-windows}上的快取位置

[!DNL Experience Manager]案頭應用程式的快取預設位置如下：

* 在Windows中， `%LocalAppData%\Adobe\AssetsCompanion\Cache\EncodedAEMEndpoint`。

* 在Mac中，`~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/EncodedAEMEndpoint`。

`EncodedAEMEndpoint` 是應用程式設定的端 [!DNL Experience Manager] 點URL。值是[!DNL Experience Manager]伺服器的目標URL的編碼版本。 例如，如果應用程式正在定位`http://localhost:4502`，則目錄名為`http%3A%2F%2Flocalhost%3A4502`。 此示例中快取目錄的Windows路徑為`%LocalAppData%\Adobe\AssetsCompanion\Cache\http%3A%2F%2Flocalhost%3A4502`。

要將應用程式指向不同的資料夾或不同的驅動器，請編輯應用程式的配置檔案。

1. 導覽至應用程式的安裝目錄。 Windows上的預設位置為`C:\Program Files (x86)\Adobe\Adobe Experience Manager Desktop`。

1. 使用文字編輯器編輯Adobe Experience Manager Desktop.exe.config檔案。

   保存對此檔案的更改需要管理員權限。

1. 搜尋字串&quot;ProxyCacheRoot&quot;。 您會看到其值已設為快取位置`%LocalAppData%\Adobe\AssetsCompanion\Cache`。 只需將此值更改為任何有效路徑即可。

   >[!NOTE]
   >
   >應用程式會自動建立&#x200B;*&lt;編碼AEM端點>*&#x200B;子目錄。 此行為無法設定。

>[!MORELIKETHIS]
* [案頭應 [!DNL Experience Manager] 用程式簡介](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/aem-desktop-app.html)。
* [ [!DNL Experience Manager] 使用案頭應用程式](use-app-v1.md)。
* [ [!DNL Experience Manager] 疑難排解案頭應用程式](troubleshoot-app-v1.md)。

