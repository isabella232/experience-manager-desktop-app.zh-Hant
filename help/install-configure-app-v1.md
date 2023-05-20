---
title: 安裝和配置案頭應用1.10版
description: 安裝和配置 [!DNL Experience Manager] 案頭應用1.10版，用於 [!DNL Assets] 並將要裝載的資產映射為案頭上的驅動器。
exl-id: 7f3bdfb1-d345-4e48-b020-6e06531f46f2
source-git-commit: 78f18e68178f711d925d7e308822c657087d009a
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 0%

---

# 安裝和配置 [!DNL Experience Manager] 案頭應用1.10版 {#install-and-configure-aem-desktop-app}

使用 [!DNL Experience Manager] 案頭應用程式， [!DNL Experience Manager] 可在您的本地案頭上輕鬆訪問，並可用於任何案頭應用程式。 在Mac查找器或Windows資源管理器中，可以輕鬆顯示資產，在案頭應用程式中開啟並在本地更改 — 更改將保存回 [!DNL Experience Manager] 上載並在儲存庫中建立新版本時。

這種整合使組織中的各種角色能夠集中管理資產中的資產，並在Creative Cloud和其他應用程式中訪問這些資產，同時使您能夠輕鬆遵守包括品牌推廣在內的各種標準。

要使用 [!DNL Experience Manager] 案頭應用，

* 確保 [!DNL Experience Manager] 伺服器版本受支援 [!DNL Experience Manager] 案頭應用。 查看 [相容性矩陣](release-notes-of-v1.md#compatibilitymatrix)。

* 下載並安裝應用程式。

* Test連接，使用少量資產。 請參閱 [訪問和開啟案頭上的資產](use-app-v1.md#openondesktop)。

## 系統要求、先決條件和下載連結 {#system-requirements-prerequisites-and-download-links}

有關詳細資訊，請參見 [[!DNL Experience Manager] 案頭應用發行說明](release-notes-of-v1.md)。

## 安裝並將應用連接到 [!DNL Experience Manager] 伺服器 {#install-and-connect-aem-desktop-app-to-aem-server}

有關詳細資訊，請參閱 [安裝並連接 [!DNL Experience Manager] 案頭應用 [!DNL Experience Manager] 伺服器](use-app-v1.md#installandconnect)。

>[!NOTE]
>
>只有一個實例 [!DNL Experience Manager] 案頭應用程式可以安裝並一次處於活動狀態。

## 檔案處理 {#file-handling}

當從案頭應用程式裝載的網路共用位置更改檔案時，檔案將分兩個階段保存到該位置。 在第一階段中，檔案被本地保存。 用戶可以保存檔案並繼續處理該檔案，而無需等待傳輸完成。

在第二階段，案頭應用將更新的檔案上載到 [!DNL Experience Manager] 伺服器在預定義的延遲後（例如30s）。 此操作在後台進行。 使用「查看資產狀態」選項可查看上載操作的狀態。

1. 將資產上載到資產。

1. 按一下 [!DNL Experience Manager] 表徵圖。

1. 從菜單中選擇「查看資產狀態」選項。

1. 從對話框中，查看上載操作的狀態。

>[!NOTE]
>
>[!DNL Experience Manager] 案頭應用可處理大小高達40 GB的資產。

## 連接到 [!DNL Experience Manager] 調度程式後面的實例 {#connect-to-an-aem-instance-behind-a-dispatcher}

Assets API中的複製和移動方法需要將以下附加標頭傳遞給 [!DNL Experience Manager]:

* X目標
* X深
* X覆蓋

[!DNL Experience Manager] 案頭連接 [!DNL Experience Manager] 使用包含預設埠的URL。 因此， `virtualhosts` 調度程式配置中的設定應包括預設埠號。 有關詳細資訊 `virtualhosts` 配置，請參見 [標識虛擬主機](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#identifying-virtual-hosts-virtualhosts)。

有關配置調度程式以傳遞這些附加標頭的其他資訊，請參見 [指定HTTP標頭](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#specifying-the-http-headers-to-pass-through-clientheaders)。

### 代理支援 {#proxy-support}

[!DNL Experience Manager] 案頭應用使用系統的預定義代理通過HTTPS連接到Internet。 應用只能使用不需要額外身份驗證的網路代理進行連接。

如果為Windows配置或修改代理伺服器設定（Internet選項> LAN設定），請重新啟動 [!DNL Experience Manager] 案頭應用，更改生效。

>[!NOTE]
>
>僅當啟動案頭應用時才應用代理配置。 關閉並重新啟動應用，使任何更改生效。

如果您的代理需要身份驗證，則IT團隊可以允許代理伺服器設定中的Experience Manager AssetsURL允許應用程式通信通過。

## 自定義資產資訊對話框 {#customize-the-asset-info-dialog}

可以通過覆蓋以下一個或兩個元件來定制「資產資訊」(Asset Info)對話框：

* 位於的「花崗岩」用戶介面頁 `/libs/dam/gui/content/assets/moreinfo`。

* HTL `/css/javascript` 元件 `/libs/dam/gui/components/admin/moreinfo`。

哪個元件重疊，取決於定製的性質。 要更改作為「資產資訊」對話框一部分顯示的元件，請覆蓋「花崗岩」用戶介面頁。 要更改對話框的HTML、CSS或JavaScript內容，請覆蓋HTL元件。

## 管理快取 {#manage-cache}

在Windows上，快取位於 `%LOCALAPPDATA%\Adobe\AssetsCompanion\Cache\`，其中是 [!DNL Experience Manager] 在案頭應用中配置的主機。 比如說， `http://localhost:4502` 顯示 `http%3A%2F%2Flocalhost%3A4502%2F`。

在MacOS X上，類似的目錄位於 `~/Library/Group Containers/group.com.adobe.aem.desktop/cache`。

### 管理快取的應用內選項 {#in-app-option-to-manage-cache}

您可以控制可用於本地快取的磁碟空間量。 Assets伺服器中的對象在本地快取，以獲得更流暢的體驗。 您可以更改預設值以滿足您的要求。 此外，還可以清除快取以重新提取所有資產。 要設定所需選項，請按一下應用程式的表徵圖，然後按一下 **[!UICONTROL Advanced]** > **[!UICONTROL Manage Cache]**。***

>[!NOTE]
>
>清除快取時，它會保留未保存的更改。 未簽入的任何資產 [!DNL Experience Manager] 伺服器將保留且未刪除。

### 更改Windows上快取的位置 {#change-location-of-cache-on-windows}

快取的預設位置 [!DNL Experience Manager] 案頭應用如下所示：

* 在Windows中， `%LocalAppData%\Adobe\AssetsCompanion\Cache\EncodedAEMEndpoint`。

* 在Mac, `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/EncodedAEMEndpoint`。

`EncodedAEMEndpoint` 已配置應用 [!DNL Experience Manager] 終結點URL。 值是目標URL的編碼版本 [!DNL Experience Manager] 伺服器。 例如，如果應用程式瞄準 `http://localhost:4502`，目錄名為 `http%3A%2F%2Flocalhost%3A4502`。 本示例中快取目錄的Windows路徑是 `%LocalAppData%\Adobe\AssetsCompanion\Cache\http%3A%2F%2Flocalhost%3A4502`。

要將應用程式指向其他資料夾或其他驅動器，請編輯應用程式的配置檔案。

1. 導航到應用的安裝目錄。 Windows上的預設位置是 `C:\Program Files (x86)\Adobe\Adobe Experience Manager Desktop`。

1. 使用文本編輯器編輯Adobe Experience ManagerDesktop.exe.config檔案。

   保存對此檔案的更改需要管理員權限。

1. 搜索字串「ProxyCacheRoot」。 您會看到其值已設定為快取位置 `%LocalAppData%\Adobe\AssetsCompanion\Cache`。 只需將此值更改為任何有效路徑即可。

   >[!NOTE]
   >
   >應用自動建立 *&lt;encoded aem=&quot;&quot; endpoint=&quot;&quot;>* 子目錄。 此行為不可配置。

>[!MORELIKETHIS]
* [簡介 [!DNL Experience Manager] 案頭應用](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/aem-desktop-app.html)。
* [使用 [!DNL Experience Manager] 案頭應用](use-app-v1.md)。
* [故障排除 [!DNL Experience Manager] 案頭應用](troubleshoot-app-v1.md)。

