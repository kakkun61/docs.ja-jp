---
title: インターネット インフォメーション サービスのホスティング手順
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 151c5ba8dd79e8554e7d79fb5b8182740b0be18e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237691"
---
# <a name="internet-information-service-hosting-instructions"></a><span data-ttu-id="2d855-102">インターネット インフォメーション サービスのホスティング手順</span><span class="sxs-lookup"><span data-stu-id="2d855-102">Internet Information Service Hosting Instructions</span></span>

<span data-ttu-id="2d855-103">インターネット インフォメーション サービス (IIS) によってホストされているこのサンプルを実行するには、IIS が適切にインストールされて実行されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d855-103">To run the samples that are hosted by Internet Information Services (IIS), you must make sure that IIS is properly installed and is running.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a><span data-ttu-id="2d855-104">Windows Server 2008 R2 に IIS バージョン 7.5 をインストールするには</span><span class="sxs-lookup"><span data-stu-id="2d855-104">To install IIS version 7.5 on Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="2d855-105">**サーバーマネージャー** から、[ロール] を選択し **ます。**</span><span class="sxs-lookup"><span data-stu-id="2d855-105">From **Server Manager**, select **Roles.**</span></span> <span data-ttu-id="2d855-106">[ **役割の概要**] で、[ **役割の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-106">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="2d855-107">[ **次へ** ] をクリックして、[ **サーバーの役割の選択** ] ダイアログを表示します。</span><span class="sxs-lookup"><span data-stu-id="2d855-107">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="2d855-108">[**役割**] ボックスの一覧から [**アプリケーションサーバー** ] を選択し、[**次へ**] を2回クリックして、アプリケーションサーバーの役割の **[役割サービスの選択**] ダイアログを表示します。</span><span class="sxs-lookup"><span data-stu-id="2d855-108">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="2d855-109">[ **Web サーバー (IIS)** ] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="2d855-109">Select the **Web Server (IIS)** check box.</span></span> <span data-ttu-id="2d855-110">追加の役割サービスと機能をインストールするように求めるメッセージが表示されたら、[ **必要な機能の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-110">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="2d855-111">[ **次へ** ] を2回クリックして、Web サーバー (IIS) の役割の **[役割サービスの選択** ] ダイアログを表示します。</span><span class="sxs-lookup"><span data-stu-id="2d855-111">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="2d855-112">[ **管理ツール**]、[ **IIS 6 管理互換**] の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="2d855-112">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="2d855-113">[ **IIS 6 スクリプトツール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2d855-113">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="2d855-114">追加の役割サービスと機能をインストールするように求めるメッセージが表示されたら、[ **必要な役割サービスの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-114">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="2d855-115">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-115">Click **Next**.</span></span>  
  
6. <span data-ttu-id="2d855-116">選択の概要が正しい場合は、[ **インストール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-116">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="2d855-117">インストールが完了したら、[ **閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-117">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-7"></a><span data-ttu-id="2d855-118">Windows 7 に IIS バージョン 7.5 をインストールするには</span><span class="sxs-lookup"><span data-stu-id="2d855-118">To install IIS version 7.5 on Windows 7</span></span>  
  
1. <span data-ttu-id="2d855-119">**[スタート]** ボタン、**[コントロール パネル]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-119">Click **Start**, and then click **Control Panel**.</span></span>  
  
2. <span data-ttu-id="2d855-120">**プログラム** グループを開きます。</span><span class="sxs-lookup"><span data-stu-id="2d855-120">Open the **Programs** group.</span></span>  
  
3. <span data-ttu-id="2d855-121">[ **プログラムと機能**] の [ **Windows の機能の有効化または無効化**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-121">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="2d855-122">[ **ユーザーアカウント制御** ] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2d855-122">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="2d855-123">**[続行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-123">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="2d855-124">[ **Windows の機能** ] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2d855-124">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="2d855-125">**インターネットインフォメーションサービス** というラベルの付いた項目を展開します。</span><span class="sxs-lookup"><span data-stu-id="2d855-125">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="2d855-126">[ **World Wide Web Services**] というラベルの付いた項目を展開します。</span><span class="sxs-lookup"><span data-stu-id="2d855-126">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="2d855-127">[ **アプリケーション開発機能**] というラベルの付いた項目を展開します。</span><span class="sxs-lookup"><span data-stu-id="2d855-127">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="2d855-128">次の項目が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2d855-128">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="2d855-129">**.NET 拡張機能**</span><span class="sxs-lookup"><span data-stu-id="2d855-129">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="2d855-130">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="2d855-130">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="2d855-131">**ISAPI 拡張機能**</span><span class="sxs-lookup"><span data-stu-id="2d855-131">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="2d855-132">**ISAPI フィルター**</span><span class="sxs-lookup"><span data-stu-id="2d855-132">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="2d855-133">[ **World Wide Web Services**] というラベルの付いた項目の下で、[ **共通の Http 機能**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="2d855-133">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
10. <span data-ttu-id="2d855-134">**静的なコンテンツ** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2d855-134">Make sure **Static Content** is selected.</span></span>  
  
11. <span data-ttu-id="2d855-135">[ **World Wide Web Services**] というラベルの付いた項目の下にある [ **セキュリティ**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="2d855-135">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
12. <span data-ttu-id="2d855-136">**Windows 認証** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2d855-136">Make sure that **Windows Authentication** is selected.</span></span>  
  
13. <span data-ttu-id="2d855-137">**インターネットインフォメーションサービス** ディレクトリで、[ **Web 管理ツール**] というラベルの付いた項目を展開し、[ **IIS 管理コンソール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2d855-137">Under the **Internet Information Services** directory, expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
14. <span data-ttu-id="2d855-138">[ **Iis 6 管理互換**] というラベルの付いた項目を展開し、[ **Iis 6 スクリプトツール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2d855-138">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="2d855-139">**インターネットインフォメーションサービス** ディレクトリで、 **Microsoft .NET Framework 3.5.1**] というラベルの付いた項目を展開し、[ **Http アクティブ化の Windows Communication Foundation**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2d855-139">Under the **Internet Information Services** directory, expand the item labeled **Microsoft .NET Framework 3.5.1**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="2d855-140">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-140">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a><span data-ttu-id="2d855-141">Windows Server 2008 に IIS バージョン 7.0 をインストールするには</span><span class="sxs-lookup"><span data-stu-id="2d855-141">To install IIS version 7.0 on Windows Server 2008</span></span>  
  
1. <span data-ttu-id="2d855-142">**サーバーマネージャー** から、[**ロール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2d855-142">From **Server Manager**, select **Roles**.</span></span> <span data-ttu-id="2d855-143">[ **役割の概要**] で、[ **役割の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-143">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="2d855-144">[ **次へ** ] をクリックして、[ **サーバーの役割の選択** ] ダイアログを表示します。</span><span class="sxs-lookup"><span data-stu-id="2d855-144">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="2d855-145">[**役割**] ボックスの一覧から [**アプリケーションサーバー** ] を選択し、[**次へ**] を2回クリックして、アプリケーションサーバーの役割の **[役割サービスの選択**] ダイアログを表示します。</span><span class="sxs-lookup"><span data-stu-id="2d855-145">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="2d855-146">[ **Web サーバー (IIS)** ] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="2d855-146">Select **Web Server (IIS)** check box.</span></span> <span data-ttu-id="2d855-147">追加の役割サービスと機能をインストールするように求めるメッセージが表示されたら、[ **必要な機能の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-147">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="2d855-148">[ **次へ** ] を2回クリックして、Web サーバー (IIS) の役割の **[役割サービスの選択** ] ダイアログを表示します。</span><span class="sxs-lookup"><span data-stu-id="2d855-148">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="2d855-149">[ **管理ツール**]、[ **IIS 6 管理互換**] の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="2d855-149">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="2d855-150">[ **IIS 6 スクリプトツール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2d855-150">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="2d855-151">追加の役割サービスと機能をインストールするように求めるメッセージが表示されたら、[ **必要な役割サービスの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-151">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="2d855-152">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-152">Click **Next**.</span></span>  
  
6. <span data-ttu-id="2d855-153">選択の概要が正しい場合は、[ **インストール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-153">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="2d855-154">インストールが完了したら、[ **閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-154">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a><span data-ttu-id="2d855-155">Windows Vista に IIS バージョン 7.0 をインストールするには</span><span class="sxs-lookup"><span data-stu-id="2d855-155">To install IIS version 7.0 on Windows Vista</span></span>  
  
1. <span data-ttu-id="2d855-156">[スタート] ボタンをクリックし、[コントロール パネル] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-156">Click Start, and then click Control Panel.</span></span>  
  
2. <span data-ttu-id="2d855-157">[ **プログラム** ] グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="2d855-157">Select the **Programs** group.</span></span>  
  
3. <span data-ttu-id="2d855-158">[ **プログラムと機能**] の [ **Windows の機能の有効化または無効化**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-158">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="2d855-159">[ **ユーザーアカウント制御** ] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2d855-159">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="2d855-160">**[続行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-160">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="2d855-161">[ **Windows の機能** ] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2d855-161">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="2d855-162">**インターネットインフォメーションサービス** というラベルの付いた項目を展開します。</span><span class="sxs-lookup"><span data-stu-id="2d855-162">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="2d855-163">[ **World Wide Web Services**] というラベルの付いた項目を展開します。</span><span class="sxs-lookup"><span data-stu-id="2d855-163">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="2d855-164">[ **アプリケーション開発機能**] というラベルの付いた項目を展開します。</span><span class="sxs-lookup"><span data-stu-id="2d855-164">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="2d855-165">次の項目が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2d855-165">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="2d855-166">**.NET 拡張機能**</span><span class="sxs-lookup"><span data-stu-id="2d855-166">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="2d855-167">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="2d855-167">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="2d855-168">**ISAPI 拡張機能**</span><span class="sxs-lookup"><span data-stu-id="2d855-168">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="2d855-169">**ISAPI フィルター**</span><span class="sxs-lookup"><span data-stu-id="2d855-169">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="2d855-170">[ **Web 管理ツール**] というラベルの付いた項目を展開し、[ **IIS 管理コンソール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2d855-170">Expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
10. <span data-ttu-id="2d855-171">[ **World Wide Web Services**] というラベルの付いた項目の下で、[ **共通の Http 機能**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="2d855-171">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
11. <span data-ttu-id="2d855-172">**静的なコンテンツ** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2d855-172">Make sure **Static Content** is selected.</span></span>  
  
12. <span data-ttu-id="2d855-173">[ **World Wide Web Services**] というラベルの付いた項目の下にある [ **セキュリティ**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="2d855-173">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
13. <span data-ttu-id="2d855-174">**Windows 認証** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2d855-174">Make sure **Windows Authentication** is selected.</span></span>  
  
14. <span data-ttu-id="2d855-175">[ **Iis 6 管理互換**] というラベルの付いた項目を展開し、[ **Iis 6 スクリプトツール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2d855-175">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="2d855-176">**Microsoft .NET Framework 3.0**] というラベルの付いた項目を展開し、[ **Windows Communication Foundation Http Activation**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2d855-176">Expand the item labeled **Microsoft .NET Framework 3.0**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="2d855-177">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-177">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a><span data-ttu-id="2d855-178">Windows Server 2003 に IIS バージョン 6.0 をインストールするには</span><span class="sxs-lookup"><span data-stu-id="2d855-178">To install IIS version 6.0 on Windows Server 2003</span></span>  
  
1. <span data-ttu-id="2d855-179">[ **サーバーの管理**] で、[ **ロールの追加または削除**] をクリックし、[ **次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-179">From **Manage Your Server**, click **Add or remove a role**, and then click **Next**.</span></span>  
  
2. <span data-ttu-id="2d855-180">[**サーバーの役割**] ボックスの一覧から [**アプリケーションサーバー (IIS、ASP.NET)** ] を選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-180">Select **Application server (IIS, ASP.NET)** from the **Server Role** list, and then click **Next**.</span></span>  
  
3. <span data-ttu-id="2d855-181">[ **ASP.NET を有効にする** ] チェックボックスをオンにし、[ **次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-181">Select **Enable ASP.NET** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="2d855-182">選択内容が正しい場合は、[次へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-182">If the summary of selections is correct, click Next.</span></span>  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a><span data-ttu-id="2d855-183">Service Pack 2 および Service Pack 3 がインストールされている Windows XP に IIS バージョン 5.1 をインストールするには</span><span class="sxs-lookup"><span data-stu-id="2d855-183">To install IIS version 5.1 on Windows XP with Service Pack 2 and Service Pack 3 installed</span></span>  
  
1. <span data-ttu-id="2d855-184">コントロール パネルで、**[プログラムの追加と削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-184">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2. <span data-ttu-id="2d855-185">**[プログラムの追加と削除]** ダイアログ ボックスで、**[Windows コンポーネントの追加と削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-185">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3. <span data-ttu-id="2d855-186">**Windows コンポーネントウィザード** で、[**インターネットインフォメーションサービス (IIS)** ] チェックボックスをオンにして、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-186">In the **Windows Components Wizard**, select the **Internet Information Services (IIS)** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="2d855-187">[ **ファイルが必要** ] ダイアログボックスが表示されたら、オペレーティングシステムのインストールディスクを挿入し、i386 フォルダーを参照して、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-187">If the **Files Needed** dialog box is displayed, insert your operating system installation disc, browse to the i386 folder, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="2d855-188">インストールが完了したら、[ **完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d855-188">When installation completes, click **Finish**.</span></span>  
  
6. <span data-ttu-id="2d855-189">[ **プログラムの追加と削除** ] ダイアログボックスを閉じて、[ **コントロールパネル**] を閉じます。</span><span class="sxs-lookup"><span data-stu-id="2d855-189">Close the **Add or Remove Programs** dialog box, and then close **Control Panel**.</span></span>  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a><span data-ttu-id="2d855-190">IIS と ASP.NET がインストールされていることを確認するには</span><span class="sxs-lookup"><span data-stu-id="2d855-190">To verify the installation of IIS and ASP.NET</span></span>  
  
1. <span data-ttu-id="2d855-191">このトピックの最後に示す HTML ファイルを \InetPub\wwwroot のルート ディレクトリに保存し、Default.aspx という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="2d855-191">Save the HTML file found at the end of this topic in the root \InetPub\wwwroot directory and name it Default.aspx.</span></span>  
  
2. <span data-ttu-id="2d855-192">ブラウザー ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="2d855-192">Open a browser window.</span></span>  
  
3. <span data-ttu-id="2d855-193">[ `http://localhost/Default.aspx` アドレス] ボックスに「」と入力し、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2d855-193">Type `http://localhost/Default.aspx` in the address box, and then press ENTER.</span></span>  
  
4. <span data-ttu-id="2d855-194">Web ページに、テキスト "Hello World" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2d855-194">A Web page with the text "Hello World" should appear.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d855-195">新しいバージョンの .NET Framework をインストールするたびに、aspnet_isapi を IIS の Web サービス拡張機能として再登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d855-195">Each time you install a new version of the .NET Framework, you must re-register aspnet_isapi as a Web service extension for IIS.</span></span> <span data-ttu-id="2d855-196">これを行うには、`aspnet_regiis –I –enable` コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="2d855-196">To do so, issue the `aspnet_regiis –I –enable` command.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="2d855-197">サンプル コード</span><span class="sxs-lookup"><span data-stu-id="2d855-197">Sample Code</span></span>  
  
```xml  
<html>  
   <body>  
       <form >  
           <h3> Hello World  
           </h3>  
       </form>  
   </body>  
</html>  
```
