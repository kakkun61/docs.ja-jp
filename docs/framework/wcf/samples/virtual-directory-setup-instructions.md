---
title: 仮想ディレクトリのセットアップ手順
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: dba6547888935ccf36ec0924fd3c95e8fbda5688
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243652"
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="0ac2e-102">仮想ディレクトリのセットアップ手順</span><span class="sxs-lookup"><span data-stu-id="0ac2e-102">Virtual Directory Setup Instructions</span></span>

<span data-ttu-id="0ac2e-103">Windows Communication Foundation (WCF) サンプルは、%SystemDrive%\inetpub\wwwroot\servicemodelsamples フォルダーにマップされている servicemodelsamples という名前の共通の仮想ディレクトリを共有することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-103">The Windows Communication Foundation (WCF) samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ac2e-104">%SystemDrive% は、インターネット インフォメーション サービス (IIS) がインストールされているドライブの場所に応じて、通常は C: または D: になります。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-104">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="0ac2e-105">Setupvroot.bat を実行し、 [Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md) でファイルを Cleanupvroot.bat して、仮想ディレクトリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-105">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="0ac2e-106">この仮想ディレクトリを手動で作成する場合は、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-106">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="0ac2e-107">手順</span><span class="sxs-lookup"><span data-stu-id="0ac2e-107">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="0ac2e-108">IIS 7.0 または7.5 で仮想ディレクトリを作成するには</span><span class="sxs-lookup"><span data-stu-id="0ac2e-108">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="0ac2e-109">[ **スタート** ] メニューの [ファイルの **実行**] をクリックし、「 **inetmgr.exe** 」と入力して、インターネットインフォメーションサービス (IIS) MMC スナップインを開きます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-109">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="0ac2e-110">左側のウィンドウで、コンピューターの名前のノードを展開し、[ **サイト** ] ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-110">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3. <span data-ttu-id="0ac2e-111">[既定の **Web サイト**] を右クリックし、[ **アプリケーションの追加** ] を選択して [ **アプリケーションの追加] ウィンドウ** を開きます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-111">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4. <span data-ttu-id="0ac2e-112">ウィンドウで、作成する `servicemodelsamples` 仮想ディレクトリの別名として「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-112">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="0ac2e-113">次のディレクトリを作成します。%SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="0ac2e-113">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6. <span data-ttu-id="0ac2e-114">物理パスを %SystemDrive%\inetpub\wwwroot\servicemodelsamples に設定します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-114">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="0ac2e-115">WCF サンプルの多くは、ビルド時にサービス実行可能ファイルをこの場所にコピーします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-115">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7. <span data-ttu-id="0ac2e-116">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-116">Click **OK**.</span></span> <span data-ttu-id="0ac2e-117">Web アプリケーションが、WCF サンプル用に作成されました。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-117">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0ac2e-118">すべての WCF サンプルで同じ servicemodelsamples Web アプリケーションが使用されるため、このタスクは1回だけ実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-118">This task must be performed only once, because all of the WCF samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0ac2e-119">このドキュメントでは、`virtual directory`という用語は `Web application`と同じ意味で使用しています。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-119">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="0ac2e-120">仮想ディレクトリを作成するだけでなく、そのプロパティを設定して、WCF サービスを実行できるようにする必要もあります。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-120">In addition to creating the virtual directory, you must also set its properties to enable WCF services to run.</span></span> <span data-ttu-id="0ac2e-121">詳細については、以下をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-121">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="0ac2e-122">仮想ディレクトリを IIS 5.1 または 6.0 で作成するには</span><span class="sxs-lookup"><span data-stu-id="0ac2e-122">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="0ac2e-123">コマンドプロンプトウィンドウを開き、「」と入力して `start inetmgr` 、インターネットインフォメーションサービス (IIS) MMC スナップインを開きます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-123">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="0ac2e-124">左側のウィンドウで、コンピューターの名前のノードを展開し、[ **Web サイト** ] ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-124">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3. <span data-ttu-id="0ac2e-125">[既定の **Web サイト** ] を右クリックし、[ **新規]、[仮想ディレクトリ** ] の順に選択して、仮想ディレクトリの作成ウィザードを開きます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-125">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4. <span data-ttu-id="0ac2e-126">ウィザードで、作成する `servicemodelsamples` 仮想ディレクトリのエイリアスとして「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-126">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="0ac2e-127">パスを %SystemDrive%\inetpub\wwwroot\servicemodelsamples に設定します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-127">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="0ac2e-128">WCF サンプルの多くは、ビルド時にサービス実行可能ファイルをこの場所にコピーします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-128">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
6. <span data-ttu-id="0ac2e-129">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-129">Click **Next**.</span></span>  
  
7. <span data-ttu-id="0ac2e-130">既定では、次のチェック ボックスがオンになっています。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-130">By default, the following check boxes are selected:</span></span>  
  
    - <span data-ttu-id="0ac2e-131">**読み取り**</span><span class="sxs-lookup"><span data-stu-id="0ac2e-131">**Read**</span></span>  
  
    - <span data-ttu-id="0ac2e-132">**[ASP などのスクリプトを実行する]**</span><span class="sxs-lookup"><span data-stu-id="0ac2e-132">**Run scripts (such as ASP)**</span></span>  
  
8. <span data-ttu-id="0ac2e-133">[ **次へ**] をクリックし、[ **完了** ] をクリックしてウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-133">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0ac2e-134">すべての WCF サンプルで同じ servicemodelsamples 仮想ディレクトリが使用されるため、このタスクは1回だけ実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-134">This task must be performed only once because all of the WCF samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="0ac2e-135">IIS 7.0 または7.5 で追加の仮想ディレクトリプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="0ac2e-135">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="0ac2e-136">servicemodelsamples ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-136">Click the servicemodelsamples node.</span></span> <span data-ttu-id="0ac2e-137">ウィンドウの下端に沿って 2 つのビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-137">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="0ac2e-138">[ **機能ビュー** ] を選択します (まだ選択されていない場合)。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-138">Select **Features View** if it isn’t already selected.</span></span>  
  
2. <span data-ttu-id="0ac2e-139">**ディレクトリ参照** のエントリをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-139">Double-click the entry for **Directory Browsing**.</span></span>  
  
3. <span data-ttu-id="0ac2e-140">[操作] ウィンドウで、[ **有効にする** ] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-140">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="0ac2e-141">これにより、Internet Explorer でディレクトリにアクセスできるようになり、サービスのデバッグに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-141">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="0ac2e-142">最後に、servicemodelsamples フォルダーのセキュリティ プロパティを、他のユーザーがアクセスできるように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-142">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="0ac2e-143">詳細については、以下をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-143">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="0ac2e-144">仮想ディレクトリの追加プロパティを IIS 5.1 または 6.0 で設定するには</span><span class="sxs-lookup"><span data-stu-id="0ac2e-144">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="0ac2e-145">[Servicemodelsamples] ノードを右クリックし、[ **プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-145">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="0ac2e-146">既定では、次のチェック ボックスがオンになっています。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-146">By default, the following check boxes are selected:</span></span>  
  
    - <span data-ttu-id="0ac2e-147">**読み取り**</span><span class="sxs-lookup"><span data-stu-id="0ac2e-147">**Read**</span></span>  
  
    - <span data-ttu-id="0ac2e-148">**ログアクセス**</span><span class="sxs-lookup"><span data-stu-id="0ac2e-148">**Log visits**</span></span>  
  
    - <span data-ttu-id="0ac2e-149">**このリソースにインデックスを付けます**</span><span class="sxs-lookup"><span data-stu-id="0ac2e-149">**Index this resource**</span></span>  
  
3. <span data-ttu-id="0ac2e-150">[ **ディレクトリの参照** ] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-150">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="0ac2e-151">これにより、Internet Explorer でディレクトリにアクセスできるようになり、サービスのデバッグに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-151">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="0ac2e-152">IIS 7.0 または7.5 でフォルダーのセキュリティプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="0ac2e-152">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="0ac2e-153">%SystemDrive%\inetpub\wwwroot\servicemodelsamples に移動します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-153">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="0ac2e-154">Servicemodelsamples フォルダーを右クリックし、[ **共有** ] または [ **共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-154">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3. <span data-ttu-id="0ac2e-155">[ **追加** ] ボタンの左側にある下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-155">Click the down arrow to the left of the **Add** button.</span></span>  
  
4. <span data-ttu-id="0ac2e-156">[ **検索** ] エントリを選択します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-156">Select the **Find** entry.</span></span> <span data-ttu-id="0ac2e-157">**[ユーザーまたはグループの選択**] ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-157">The **Select Users or Groups** window opens.</span></span>  
  
5. <span data-ttu-id="0ac2e-158">**[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-158">Click **Advanced**.</span></span>  
  
6. <span data-ttu-id="0ac2e-159">**[場所]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-159">Click **Locations**.</span></span> <span data-ttu-id="0ac2e-160">[ **場所** ] ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-160">The **Locations** window is now open.</span></span>  
  
7. <span data-ttu-id="0ac2e-161">使用するコンピューターのエントリを選択します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-161">Select the entry for the computer being used.</span></span> <span data-ttu-id="0ac2e-162">一覧表示されているドメインやネットワークのエントリではなく、ローカル コンピューターを選択してください。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-162">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="0ac2e-163">コンピューターを選択したら、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-163">After you have selected the computer, click **OK**.</span></span>  
  
8. <span data-ttu-id="0ac2e-164">**[Find Now]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-164">Click **Find Now**.</span></span> <span data-ttu-id="0ac2e-165">これで、ローカル コンピューターに関連付けられたオブジェクトが検索結果に表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-165">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="0ac2e-166">[**名前 (相対識別名)** ] 列で **IIS_IUSRS** エントリを探します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-166">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="0ac2e-167">そのエントリを選択し、[ **OK** ] をクリックして [検索結果] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-167">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="0ac2e-168">[ **OK]** をクリックして、[ **ユーザーまたはグループの選択** ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-168">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="0ac2e-169">変更を保持するには、[ **共有** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-169">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="0ac2e-170">共有を有効にするための変更が完了したら、[ **完了** ] をクリックして [ **ファイルの共有** ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-170">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="0ac2e-171">フォルダーのセキュリティ プロパティを IIS 5.1 または 6.0 で設定するには</span><span class="sxs-lookup"><span data-stu-id="0ac2e-171">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="0ac2e-172">%SystemDrive%\inetpub\wwwroot\servicemodelsamples に移動します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-172">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="0ac2e-173">**Servicemodelsamples** フォルダーを右クリックし、[**共有とセキュリティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-173">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3. <span data-ttu-id="0ac2e-174">**[セキュリティ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-174">Click the **Security** tab.</span></span>  
  
4. <span data-ttu-id="0ac2e-175">IIS 6.0 を使用している場合は、[ **グループ名またはユーザー名** ] ボックスで、[ **インターネットゲストアカウント** ] が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-175">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="0ac2e-176">表示されていない場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-176">If it is not listed:</span></span>  
  
    1. <span data-ttu-id="0ac2e-177">**[スタート]** ボタンをクリックし、**コントロール パネル** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-177">Click **Start** and then click **Control Panel**.</span></span>  
  
    2. <span data-ttu-id="0ac2e-178">[ **ユーザーアカウント** ] アイコンが表示されない場合は、[ **カテゴリビューに切り替え] を** クリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-178">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3. <span data-ttu-id="0ac2e-179">[ **ユーザーアカウント** ] アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-179">Click the **User Accounts** icon.</span></span>  
  
    4. <span data-ttu-id="0ac2e-180">[コントロールパネルを選択してください] アイコンをクリックし、[ **ユーザーアカウント**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-180">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5. <span data-ttu-id="0ac2e-181">[ **ユーザーアカウント** ] ダイアログボックスで、[ **詳細設定** ] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-181">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6. <span data-ttu-id="0ac2e-182">**[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-182">Click **Advanced**.</span></span>  
  
    7. <span data-ttu-id="0ac2e-183">[ **ローカルユーザーとグループ** ] ダイアログボックスで、[ **ユーザー** ] フォルダーをクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-183">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8. <span data-ttu-id="0ac2e-184">右側のウィンドウで、[ **インターネットゲストアカウント**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-184">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="0ac2e-185">[ **プロパティ** ] ダイアログボックスで、インターネットゲストアカウントとして使用されている名前をコピーします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-185">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="0ac2e-186">既定では、その名前は "USR_" で始まり、その次にコンピューターの名前が続きます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-186">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="0ac2e-187">**[プロパティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-187">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="0ac2e-188">[ **ローカルユーザーとグループ** ] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-188">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="0ac2e-189">[ **ユーザーアカウント** ] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-189">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="0ac2e-190">[その他の **ユーザーアカウント** ] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-190">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="0ac2e-191">[ **Servicemodelsamples のプロパティ** ] ダイアログボックスの [ **セキュリティ** ] タブで、[ **追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-191">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="0ac2e-192">コンピューターの名前とバックスラッシュを入力し、インターネットユーザーアカウントの名前を貼り付けます (例、myMachineName \\ % internetguestaccountname%)。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-192">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="0ac2e-193">[ **名前の確認** ] をクリックして、追加を確認します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-193">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="0ac2e-194">名前が有効な場合は、すべての文字が下線付きの大文字になります。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-194">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5. <span data-ttu-id="0ac2e-195">IIS 6.0 の場合は、[ **グループ名またはユーザー名** ] ボックスに [ネットワークサービス] が表示されていることも確認します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-195">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="0ac2e-196">NETWORK SERVICE が表示されていない場合:</span><span class="sxs-lookup"><span data-stu-id="0ac2e-196">If NETWORK SERVICE is not listed:</span></span>  
  
    1. <span data-ttu-id="0ac2e-197">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-197">Click **Add**.</span></span>  
  
    2. <span data-ttu-id="0ac2e-198">**[ユーザーまたはグループの選択**] ダイアログボックスで、コンピューター名の後にバックスラッシュを入力します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-198">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3. <span data-ttu-id="0ac2e-199">バックスラッシュの後に「 **service** 」と入力します (スペースは不要です)。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-199">Type **service** after the backslash (no space).</span></span>  
  
    4. <span data-ttu-id="0ac2e-200">[ **名前の確認**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-200">Click **Check names**.</span></span>  
  
    5. <span data-ttu-id="0ac2e-201">複数の名前が見つかった場合は、[ **ネットワークサービス** ] を選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-201">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6. <span data-ttu-id="0ac2e-202">[ **OK** ] をクリックして、[ **ユーザーまたはグループの選択** ] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-202">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6. <span data-ttu-id="0ac2e-203">IIS 5.1 で Windows XP SP2 を使用している場合は、[ **グループ名またはユーザー名** ] ボックスに、インターネットゲストアカウントと ASPNET の両方が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-203">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="0ac2e-204">ASPNET ユーザーは、組み込みの **Users** セキュリティグループのメンバーである可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-204">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="0ac2e-205">その場合、 **ユーザー** グループがダイアログボックスに表示されている場合は、許可されたユーザーの一覧に個別のアイテムとして追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-205">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="0ac2e-206">ASPNET が **Users** セキュリティグループに属しているかどうかを確認するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-206">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1. <span data-ttu-id="0ac2e-207">**[スタート]** ボタンをクリックし、 **[コントロール パネル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-207">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2. <span data-ttu-id="0ac2e-208">[ **ユーザーアカウント** ] アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-208">Click the **User Accounts** icon.</span></span>  
  
    3. <span data-ttu-id="0ac2e-209">[ **グループ** ] 列で、[ **ASPNET** ] の値が "Users" であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0ac2e-209">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ac2e-210">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ac2e-210">See also</span></span>

- [<span data-ttu-id="0ac2e-211">インターネット インフォメーション サービスのホスティング手順</span><span class="sxs-lookup"><span data-stu-id="0ac2e-211">Internet Information Service Hosting Instructions</span></span>](internet-information-service-hosting-instructions.md)
