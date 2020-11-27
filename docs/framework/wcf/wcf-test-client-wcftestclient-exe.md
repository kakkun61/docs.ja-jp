---
title: WCF のテスト用クライアント (WcfTestClient.exe)
description: Wcf テストクライアントについて説明します。 wcf サービスホストと組み合わせると、シームレスなサービステストが提供されます。 クライアントテストの値を送信し、サービスの応答を表示します。
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: f583d20edf7eeea87ae1dbf63a3cadef05912833
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264128"
---
# <a name="wcf-test-client-wcftestclientexe"></a><span data-ttu-id="b1dc4-104">WCF のテスト用クライアント (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="b1dc4-104">WCF Test Client (WcfTestClient.exe)</span></span>

<span data-ttu-id="b1dc4-105">Windows Communication Foundation (WCF) テスト用クライアント (WcfTestClient.exe) は、ユーザーがテストパラメーターを入力し、その入力をサービスに送信し、サービスから返される応答を表示できるようにする GUI ツールです。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-105">Windows Communication Foundation (WCF) Test Client (WcfTestClient.exe) is a GUI tool that enables users to input test parameters, submit that input to the service, and view the response that the service sends back.</span></span> <span data-ttu-id="b1dc4-106">WCF サービスホストと組み合わせると、シームレスなサービステストエクスペリエンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-106">It provides a seamless service testing experience when combined with WCF Service Host.</span></span>

<span data-ttu-id="b1dc4-107">通常、WCF テストクライアント (WcfTestClient.exe) は次の場所にあります。-Community は、インストールされている `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` Visual Studio のレベルに応じて、"Enterprise"、"Professional"、または "community" のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-107">You can typically find the WCF Test Client (WcfTestClient.exe) in the following location: `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` - Community may be one of "Enterprise", "Professional" or "Community" depending on which level of Visual Studio is installed.</span></span>

## <a name="scenarios-for-using-test-client"></a><span data-ttu-id="b1dc4-108">テスト用クライアントを使用するシナリオ</span><span class="sxs-lookup"><span data-stu-id="b1dc4-108">Scenarios for Using Test Client</span></span>

<span data-ttu-id="b1dc4-109">以下のセクションでは、WCF テストクライアントを使用して開発プロセスを効率化できる最も一般的なシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-109">The following sections discuss the most common scenarios in which you can use WCF Test Client to streamline your development process.</span></span>

### <a name="inside-visual-studio"></a><span data-ttu-id="b1dc4-110">Visual Studio 内</span><span class="sxs-lookup"><span data-stu-id="b1dc4-110">Inside Visual Studio</span></span>

#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a><span data-ttu-id="b1dc4-111">WCF サービス ホストが、1 つのサービスを使用する WCF のテスト用クライアントを開始する</span><span class="sxs-lookup"><span data-stu-id="b1dc4-111">WCF Service Host Starts WCF Test Client with a Single Service</span></span>

<span data-ttu-id="b1dc4-112">新しい WCF サービスプロジェクトを作成し、F5 キーを押してデバッガーを起動した後、WCF サービスホストがプロジェクト内のサービスのホストを開始します。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-112">After you create a new WCF service project and press F5 to start the debugger, the WCF Service Host begins to host the service in your project.</span></span> <span data-ttu-id="b1dc4-113">次に、WCF テストクライアントが開き、構成ファイルで定義されているサービスエンドポイントの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-113">Then, WCF Test Client opens and displays a list of service endpoints defined in the configuration file.</span></span> <span data-ttu-id="b1dc4-114">ユーザーは、パラメーターをテストしてサービスを呼び出すことができ、このプロセスを繰り返して、サービスのテストおよび検証を継続的に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-114">You can test the parameters and invoke the service, and repeat this process to continuously test and validate your service.</span></span>

#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a><span data-ttu-id="b1dc4-115">WCF サービス ホストが、複数のサービスを使用する WCF のテスト用クライアントを開始する</span><span class="sxs-lookup"><span data-stu-id="b1dc4-115">WCF Service Host Starts WCF Test Client with Multiple Services</span></span>

<span data-ttu-id="b1dc4-116">また、WCF テストクライアントを使用して、複数のサービスを含むサービスプロジェクトをデバッグすることもできます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-116">You can also use WCF Test Client to help debug a service project that contains multiple services.</span></span> <span data-ttu-id="b1dc4-117">WCF テストクライアントを開くと、プロジェクト内のサービスの一覧が自動的に反復処理され、テストのために開かれます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-117">When WCF Test Client opens, it automatically iterates the list of services in your project and opens them for testing.</span></span>

### <a name="outside-visual-studio"></a><span data-ttu-id="b1dc4-118">Visual Studio の外部</span><span class="sxs-lookup"><span data-stu-id="b1dc4-118">Outside Visual Studio</span></span>

<span data-ttu-id="b1dc4-119">また、Visual Studio の外部で WCF テストクライアント (WcfTestClient.exe) を呼び出して、インターネット上の任意のサービスをテストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-119">You can also invoke the WCF Test Client (WcfTestClient.exe) outside Visual Studio to test an arbitrary service on the Internet.</span></span> <span data-ttu-id="b1dc4-120">このツールを見つけるには、次の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-120">To locate the tool, go to the following location:</span></span>

<span data-ttu-id="b1dc4-121">`C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` (コンピューターにインストールされている Visual Studio のレベルによっては、"Enterprise"、"Professional"、"Community" のいずれかになります)。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-121">`C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` (where community can be one of "Enterprise", "Professional" or "Community" depending on which level of Visual Studio is installed on the machine)</span></span>

<span data-ttu-id="b1dc4-122">ツールを使用するには、ファイル名をダブルクリックしてこの場所からツールを開くか、コマンド ラインからツールを起動します。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-122">To use the tool, double-click the file name to open it from this location, or launch it from a command line.</span></span>

<span data-ttu-id="b1dc4-123">WCF テストクライアントは、コマンドライン引数として任意の数の Uri を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-123">WCF Test Client takes an arbitrary number of URIs as command line arguments.</span></span>  <span data-ttu-id="b1dc4-124">これらの引数には、テストできるサービスの URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-124">These are the URIs of services that can be tested.</span></span>

`wcfTestClient.exe URI1 URI2 …`

<span data-ttu-id="b1dc4-125">WCF テストクライアントウィンドウが開いたら、[**ファイル**] [サービスの追加] の順にクリックし、 -> **Add Service** 開くサービスのエンドポイントアドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-125">After the WCF Test Client window is opened, click **File**->**Add Service**, and enter the endpoint address of the service you want to open.</span></span>

## <a name="wcf-test-client-user-interface"></a><span data-ttu-id="b1dc4-126">WCF のテスト用クライアントのユーザー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b1dc4-126">WCF Test Client User Interface</span></span>

<span data-ttu-id="b1dc4-127">WCF テストクライアントは、1つのサービスまたは複数のサービスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-127">You can use WCF Test Client with a single service or multiple services.</span></span>

### <a name="service-operations"></a><span data-ttu-id="b1dc4-128">サービス操作</span><span class="sxs-lookup"><span data-stu-id="b1dc4-128">Service Operations</span></span>

<span data-ttu-id="b1dc4-129">WCF テストクライアントのメインウィンドウの左ペインには、使用可能なすべてのサービスと、それぞれのエンドポイントと操作が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-129">The left pane of the WCF Test Client main window lists all the available services, along with their respective endpoints and operations.</span></span>

<span data-ttu-id="b1dc4-130">操作をダブルクリックすると、その操作の名前が付いた新しいタブ内の右ペインで、操作の内容を表示できます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-130">When you double-click an operation, you can view its content in the right pane inside a new tab with the operation's name.</span></span>

<span data-ttu-id="b1dc4-131">左ペインには、クライアントの構成ファイルも表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-131">The left pane also lists client configuration files.</span></span> <span data-ttu-id="b1dc4-132">いずれかの項目をダブルクリックすると、右ペインの新しいタブ付きウィンドウにファイルの内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-132">Double-click any of the items to display the content of the file in a new tabbed window in the right pane.</span></span>

### <a name="entering-test-parameters"></a><span data-ttu-id="b1dc4-133">テスト パラメーターの入力</span><span class="sxs-lookup"><span data-stu-id="b1dc4-133">Entering Test Parameters</span></span>

<span data-ttu-id="b1dc4-134">テスト パラメーターを表示するには、右ペインで操作をダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-134">To view the test parameters, double-click an operation to open it in the right pane.</span></span> <span data-ttu-id="b1dc4-135">既定では、パラメーターは **書式付き** ビューで表示されます。また、パラメーターに任意の値を入力して、サービスをテストできます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-135">The parameters are showed in **Formatted** view by default, and you can enter arbitrary values for the parameters to test the service.</span></span>

<span data-ttu-id="b1dc4-136">メッセージの XML を表示するには、[ **xml**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-136">To view the message's XML, click **XML**.</span></span> <span data-ttu-id="b1dc4-137">サービスに送信するには、[ **呼び出し**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-137">To send them to the service, click **Invoke**.</span></span>

<span data-ttu-id="b1dc4-138">データセットパラメーターの場合は、[.. **.** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-138">For a DataSet parameter, click the **…**</span></span> <span data-ttu-id="b1dc4-139">[編集] の横にあるボタン.. **.**</span><span class="sxs-lookup"><span data-stu-id="b1dc4-139">button next to **Edit…**</span></span> <span data-ttu-id="b1dc4-140">データグリッドを表示する新しいウィンドウで編集します。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-140">to edit it in a new window showing the DataGrid.</span></span> <span data-ttu-id="b1dc4-141">[ **データセットのコピー** ] ボタンと [ **データセットの貼り付け** ] ボタンの外観がわかります。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-141">Notice the appearance of the **Copy DataSet** and **Paste DataSet** buttons.</span></span> <span data-ttu-id="b1dc4-142">最初の編集時に DataSet オブジェクトのスキーマが不明の場合、DataGrid は空になります。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-142">If the schema of the DataSet object is unknown upon the first edit, the DataGrid is empty.</span></span> <span data-ttu-id="b1dc4-143">スキーマが同じ DataSet オブジェクトを DataGrid の現在のオブジェクトに貼り付ける必要があります </span><span class="sxs-lookup"><span data-stu-id="b1dc4-143">You have to paste a DataSet object with the same schema into the current object in the DataGrid.</span></span> <span data-ttu-id="b1dc4-144">(貼り付け操作の前に、他の場所からスキーマをコピーする必要があることに注意してください)。[ **データセットのコピー** ] ボタンをクリックして、将来使用するためにデータセットオブジェクトをコピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-144">(Notice that you need to copy the schema from somewhere else before the paste operation.) You can also copy a Dataset object for future usage by clicking the **Copy DataSet** button.</span></span>

<span data-ttu-id="b1dc4-145">サービスの応答がテスト パラメーターの下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-145">The service's response appears below the test parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="b1dc4-146">想定される戻り値が文字列の場合、入力が引用符で囲まれていなくても、結果は引用符で囲まれた文字列として表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-146">If the expected return value is a string, the result will be displayed as a quoted string even though the input provided was not in quotes.</span></span>

<span data-ttu-id="b1dc4-147">サービスのコントラクトの作成時に特定の操作を一方向として指定した場合は、サービスの応答は表示されません。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-147">If you specified a particular operation as one-way when you created the contract for the service, no service response is displayed.</span></span> <span data-ttu-id="b1dc4-148">メッセージが配信のキューに置かれると、メッセージが正常に送信されたことを通知するダイアログ ボックスがすぐに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-148">As soon as the message is queued for delivery, a dialog box pops up to notify you that the message was successfully sent.</span></span>

### <a name="session-support"></a><span data-ttu-id="b1dc4-149">セッション サポート</span><span class="sxs-lookup"><span data-stu-id="b1dc4-149">Session Support</span></span>

<span data-ttu-id="b1dc4-150">サービス操作のタブで [ **新しいプロキシを開始** する] チェックボックスをオンにすると、セッションのサポートを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-150">The **Start a new proxy** check box in a service operation's tab enables you to toggle session support.</span></span> <span data-ttu-id="b1dc4-151">既定では、このチェック ボックスはオフになります。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-151">This box is cleared by default.</span></span>

<span data-ttu-id="b1dc4-152">特定の操作 (または同じサービスエンドポイントの別の操作) に対してテストパラメーターを入力し、チェックボックスをオフにして [ **呼び出し** ] を複数回クリックすると、これらの操作は1つのプロキシを共有し、サービスの状態は複数の操作にわたって保持されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-152">When you enter test parameters for a specific operation (or another operation in the same service endpoint) and click **Invoke** multiple times with the check box cleared, these operations share one proxy and the service status is persisted across multiple operations.</span></span>

<span data-ttu-id="b1dc4-153">[ **新しいプロキシを開始** する] チェックボックスがオンになっている場合は、 **呼び出し** ごとに新しいプロキシが開始され、前のセッションシナリオが終了して、サービスの状態がリセットされます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-153">If the **Start a new proxy** check box is checked, a new proxy is started for each **Invoke**, the previous session scenario is ended, and the service status is reset.</span></span>

### <a name="editing-client-configuration"></a><span data-ttu-id="b1dc4-154">クライアント構成の編集</span><span class="sxs-lookup"><span data-stu-id="b1dc4-154">Editing Client Configuration</span></span>

<span data-ttu-id="b1dc4-155">WCF テストクライアントのメインウィンドウの左ペインには、クライアント構成ファイルが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-155">The left pane of the WCF Test Client main window lists client configuration files.</span></span> <span data-ttu-id="b1dc4-156">いずれかの項目をダブルクリックすると、右ペインにファイルの内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-156">Double-click any of the items to display the contents of the file in the right pane.</span></span>

#### <a name="edit-with-service-configuration-editor"></a><span data-ttu-id="b1dc4-157">サービス構成エディターを使用した編集</span><span class="sxs-lookup"><span data-stu-id="b1dc4-157">Edit with Service Configuration Editor</span></span>

<span data-ttu-id="b1dc4-158">左側のウィンドウで [ **Config File** ] を右クリックし、コンテキストメニューの [ **Edit with svcconfigeditor.exe**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-158">Right-click **Config File** in the left pane and select the context menu **Edit with SvcConfigEditor**.</span></span> <span data-ttu-id="b1dc4-159">サービス構成エディターが起動し、クライアント構成の内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-159">Service Configuration Editor is launched with the client configuration content.</span></span> <span data-ttu-id="b1dc4-160">このツール内で構成を編集して保存できます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-160">You can edit the configuration and save it within the tool.</span></span>

<span data-ttu-id="b1dc4-161">サービス構成エディターでファイルを保存した後、ファイルが外部で変更されたことを知らせる警告メッセージが WCF テストクライアントに表示され、再度読み込むかどうかを確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-161">After saving the file in Service Configuration Editor, WCF Test Client displays a warning message to inform you that the file has been modified outside and asks whether you would like to reload it.</span></span>

<span data-ttu-id="b1dc4-162">[ **はい**] を選択した場合、[Client.dll.config] タブの構成コンテンツには、エディターで行った変更が反映されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-162">If you select **Yes**, the configuration content in the "Client.dll.config" tab reflects the changes you made in the editor.</span></span>

<span data-ttu-id="b1dc4-163">[ **いいえ**] を選択した場合、[Client.dll.config] タブの構成内容は変更されず、変更されたコンテンツはソースファイルに自動的に保存されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-163">If you select **No**, the configuration content in the "Client.dll.config" tab remains unchanged and the modified content is automatically saved to the source file.</span></span>

#### <a name="restore-to-default-configuration"></a><span data-ttu-id="b1dc4-164">既定の構成への復元</span><span class="sxs-lookup"><span data-stu-id="b1dc4-164">Restore to Default Configuration</span></span>

<span data-ttu-id="b1dc4-165">すべての変更を取り消して、既定のクライアント構成に復元する場合は、左側のウィンドウで [ **Config File** ] を右クリックし、コンテキストメニューの [ **既定の構成に復元**] を選択します。既定の構成値が読み込まれ、[Client.dll.config] タブの内容が復元されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-165">If you want to cancel all the changes and restore to the default client configuration, right-click **Config File** in the left pane and select the context menu **Restore to Default Config**. The default configuration value is loaded and content in "Client.dll.config" tab is restored.</span></span>

#### <a name="validate-changes"></a><span data-ttu-id="b1dc4-166">変更の検証</span><span class="sxs-lookup"><span data-stu-id="b1dc4-166">Validate Changes</span></span>

<span data-ttu-id="b1dc4-167">保存された変更が WCF テストクライアントに読み込まれるときに、WCF スキーマに対して構成が有効かどうかがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-167">When saved changes are being loaded in WCF Test Client, the configuration is checked for validity against WCF schema.</span></span> <span data-ttu-id="b1dc4-168">エラーが見つかった場合は、エラーの詳細を示すダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-168">If errors are found, a dialog box is displayed to show error details.</span></span>

<span data-ttu-id="b1dc4-169">プロキシの生成中、バイナリのコンパイル中、またはサービスの呼び出し時に、編集をサポートするメニュー項目 ("Edit..."、"Restore..." など) は無効になります。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-169">During proxy generation, binary compiling, or service invoking, menu items that support editing (that is, "Edit …", "Restore …", and so on) are disabled.</span></span> <span data-ttu-id="b1dc4-170">サービスの呼び出しは、更新された構成を WCF テストクライアントに読み込むときにも無効になります。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-170">Service invocation is also disabled when loading updated configuration to WCF Test Client.</span></span>

#### <a name="persist-client-configuration"></a><span data-ttu-id="b1dc4-171">クライアント構成の保持</span><span class="sxs-lookup"><span data-stu-id="b1dc4-171">Persist Client Configuration</span></span>

<span data-ttu-id="b1dc4-172">[**ツール** -> **オプション**] [ -> **クライアントの構成**] タブには、[**サービスの起動時に常に構成を再生成** する] オプションがあります。これは既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-172">The **Tools**->**Options**->**Client Configuration** tab contains an **Always Regenerate Config When Launching Services** option, which is enabled by default.</span></span> <span data-ttu-id="b1dc4-173">このオプションは、WCF テストクライアントがサービスを読み込むたびに、最新のサービスコントラクトとサービス App.config ファイルに基づいて構成ファイルを再生成することを指定します。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-173">This option specifies that every time WCF Test Client loads a service, it regenerates a configuration file based on the latest service contract and service App.config files.</span></span>

<span data-ttu-id="b1dc4-174">WCF サービスのクライアント構成を編集していて、この更新されたファイルを常に使用してサービスをデバッグする場合は、[ **再生成** ] オプションをオフにすることができます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-174">If you have edited the client configuration for your WCF service and want to always use this updated file to debug your service, you can uncheck the **Regenerate** option.</span></span> <span data-ttu-id="b1dc4-175">これにより、サービスを更新して WCF テストクライアントを再度開く場合でも、更新されたサービスに基づいて再生成されたファイルではなく、以前に更新した Client.dll.config ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-175">By doing so, even when you update the service and reopen WCF Test Client, the Client.dll.config file is the one you updated previously instead of a regenerated one based on the updated service.</span></span>

<span data-ttu-id="b1dc4-176">ただし、再生成されたプロキシとの一貫性を保つために、構成ファイルの編集が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-176">However, you might need to edit the configuration file to make it consistent with the regenerated proxy.</span></span> <span data-ttu-id="b1dc4-177">サービスを更新したことが原因で、再生成されたプロキシと構成ファイルが一致しなくなると、サービスを呼び出したときにエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-177">If the regenerated proxy and configuration file are mismatched due to an updated service, errors will occur when the service is invoked.</span></span>

> [!CAUTION]
> <span data-ttu-id="b1dc4-178">変更したクライアント構成ファイルを後で再利用することにした場合、該当するファイルは次の場所で見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-178">If you have modified the client configuration file and select to reuse it in the future, you can find the file in the following location:</span></span>
>
> <span data-ttu-id="b1dc4-179">\Documents と Settings \\ [User Account] \My Documents\Test Client Projects.</span><span class="sxs-lookup"><span data-stu-id="b1dc4-179">\Documents and Settings\\[User Account]\My Documents\Test Client Projects.</span></span>
>
> <span data-ttu-id="b1dc4-180">クライアント構成ファイルに格納されている更新された資格情報は、このフォルダーのアクセス制御リスト (ACL) によって保護されています。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-180">Any updated credential information stored to the client configuration file is protected by the Access Control List (ACL) of this folder.</span></span>

### <a name="adding-removing-and-refreshing-services"></a><span data-ttu-id="b1dc4-181">サービスの追加、削除、および更新</span><span class="sxs-lookup"><span data-stu-id="b1dc4-181">Adding, Removing and Refreshing Services</span></span>

#### <a name="add-service"></a><span data-ttu-id="b1dc4-182">Add Service (サービスの追加)</span><span class="sxs-lookup"><span data-stu-id="b1dc4-182">Add Service</span></span>

<span data-ttu-id="b1dc4-183">[**ファイル**] [サービスの追加] をクリックして -> **Add Service** 、WCF テストクライアントにサービスを追加します。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-183">Click **File**->**Add Service** to add a service to WCF Test Client.</span></span> <span data-ttu-id="b1dc4-184">次に、追加するサービスの URI (エンドポイント アドレス) を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-184">You are then required to type the URI (endpoint address) of the service to be added.</span></span> <span data-ttu-id="b1dc4-185">サービスのアドレスには、MEX アドレスまたは WSDL アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-185">The service’s address can be a mex address or WSDL address.</span></span>

<span data-ttu-id="b1dc4-186">[ **最近使用** したサービス] サブメニューには、最近追加された10個のサービスのエンドポイントの一覧も表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-186">You can also find a list of 10 recently added services' endpoints in the **Recent Services** submenu.</span></span> <span data-ttu-id="b1dc4-187">これらのいずれかを選択すると、指定したサービスが WCF テストクライアントに追加されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-187">If you select one of them, the specified service is added to WCF Test Client.</span></span>

<span data-ttu-id="b1dc4-188">また、サービスツリーの **[マイサービスプロジェクト**] のルートを右クリックし、[ **サービスの追加** ] を選択すると、同じ結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-188">You can also right-click the root of service tree **My Service Projects**, and select **Add Service** to achieve the same result.</span></span>

<span data-ttu-id="b1dc4-189">プロキシの生成中、バイナリのコンパイル中、またはサービスの呼び出し中は、サービスの追加をサポートするメニュー項目が無効になります。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-189">During proxy generation, binary compiling, or service invocation, menu items that support adding a service are disabled.</span></span> <span data-ttu-id="b1dc4-190">また、サービスの呼び出しも無効になります。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-190">Service invocation is also disabled.</span></span>

#### <a name="remove-service"></a><span data-ttu-id="b1dc4-191">サービスの削除</span><span class="sxs-lookup"><span data-stu-id="b1dc4-191">Remove Service</span></span>

<span data-ttu-id="b1dc4-192">削除するサービスのサービスルートを右クリックし、[ **サービスの削除** ] を選択して、WCF テストクライアントからサービスを削除します。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-192">Right-click the service root of the service to be removed, and select **Remove Service** to remove a service from WCF Test Client.</span></span>

<span data-ttu-id="b1dc4-193">プロキシの生成中、バイナリのコンパイル中、またはサービスの呼び出し中は、サービスの削除をサポートするメニュー項目が無効になります。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-193">During proxy generation, binary compiling, or service invocation, menu items that support removing a service are disabled.</span></span> <span data-ttu-id="b1dc4-194">また、サービスの呼び出しも無効になります。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-194">Service invocation is also disabled.</span></span>

#### <a name="refresh-service"></a><span data-ttu-id="b1dc4-195">サービスの更新</span><span class="sxs-lookup"><span data-stu-id="b1dc4-195">Refresh Service</span></span>

<span data-ttu-id="b1dc4-196">WCF テストクライアントの実行中にサービスに変更が加えられた場合に、そのサービスの WCF テストクライアントの実装が最新であることを確認するには、サービスのサービスルートを右クリックし、[ **サービスの更新**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-196">If a change is made to the service while WCF Test Client is running and you want to ensure that the WCF Test Client implementation for that service is up-to-date, right-click the service root of the service, and select **Refresh Service**.</span></span> <span data-ttu-id="b1dc4-197">更新後、サービスの状態はリセットされます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-197">Note that after refreshing, the service status is reset.</span></span>

<span data-ttu-id="b1dc4-198">プロキシの生成中、バイナリのコンパイル中、またはサービスの呼び出し中は、サービスの更新をサポートするメニュー項目が無効になります。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-198">During proxy generation, binary compiling, or service invocation, menu items that support refreshing a service are disabled.</span></span> <span data-ttu-id="b1dc4-199">また、サービスの呼び出しも無効になります。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-199">Service invocation is also disabled.</span></span>

## <a name="location-of-files-generated-by-the-test-client"></a><span data-ttu-id="b1dc4-200">テスト クライアントが生成するファイルの場所</span><span class="sxs-lookup"><span data-stu-id="b1dc4-200">Location of Files Generated by the Test Client</span></span>

<span data-ttu-id="b1dc4-201">既定では、WCF テストクライアントは、生成されたクライアントコードと構成ファイルを "%Appdata%\local\temp\test client projects Client Projects" フォルダーに格納します。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-201">By default, WCF Test Client stores generated client code and configuration files in the "%appdata%\Local\temp\Test Client Projects" folder.</span></span> <span data-ttu-id="b1dc4-202">このフォルダーは、WCF テストクライアントが終了した後に削除されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-202">This folder is deleted after WCF Test Client exits.</span></span> <span data-ttu-id="b1dc4-203">WCF テストクライアントで構成ファイルが変更され、[サービスの開始] オプションが無効になっているときに [ **常に構成を再生成** する] が有効になっている場合、変更されたファイルは、"My Documents\Test Client Projects" の下の "CachedConfig" フォルダーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-203">If a configuration file is modified in WCF Test Client and the **Always Regenerate Config When Launching Services** option is disabled, the modified file is copied to the "CachedConfig" folder under "My Documents\Test Client Projects" with a mapping (metadata-address-to-file-name) XML file as an index.</span></span>

<span data-ttu-id="b1dc4-204">また、コマンドラインで WCF テストクライアントを起動し、スイッチを使用して、 `/ProjectPath` 生成されたファイルを格納するための新しい目的のパスを指定するか、スイッチを使用して `/RestoreProjectPath` 既定の場所を復元することもできます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-204">You can also start WCF Test Client in a command line, use the `/ProjectPath` switch to specify a new desired path for storing generated files, or use the `/RestoreProjectPath` switch to restore the default location.</span></span> <span data-ttu-id="b1dc4-205">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-205">The syntax is as follows:</span></span>

`wcfTestClient.exe /ProjectPath [desired location]`

<span data-ttu-id="b1dc4-206">このコマンドを実行しても、WCF テストクライアントは開かれません。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-206">Running this command does not open WCF Test Client.</span></span> <span data-ttu-id="b1dc4-207">フォルダーの場所が変更されるだけです。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-207">Only the folder location is changed.</span></span> <span data-ttu-id="b1dc4-208">このコマンドは、WCF テストクライアントが実行されているかどうかにかかわらず実行できます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-208">You can run this command whether WCF Test Client is running or not.</span></span> <span data-ttu-id="b1dc4-209">新しい場所は、WCF テストクライアントの再起動時に適用されます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-209">The new location is applied when WCF Test Client is restarted.</span></span> <span data-ttu-id="b1dc4-210">場所情報は、レジストリ、または "%Appdata%\local\temp\test client projects Client Projects" フォルダー内の WcfTestClient.exe ファイルに保存できます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-210">The location information can be saved in registry, or in the WcfTestClient.exe.option file in the "%appdata%\Local\temp\Test Client Projects" folder.</span></span>

## <a name="features-supported-by-wcf-test-client"></a><span data-ttu-id="b1dc4-211">WCF のテスト用クライアントでサポートされる機能</span><span class="sxs-lookup"><span data-stu-id="b1dc4-211">Features supported by WCF Test Client</span></span>

<span data-ttu-id="b1dc4-212">WCF テストクライアントでサポートされている機能の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-212">The following is a list of features supported by WCF Test Client:</span></span>

- <span data-ttu-id="b1dc4-213">サービスの呼び出し : 要求/応答メッセージおよび一方向メッセージ</span><span class="sxs-lookup"><span data-stu-id="b1dc4-213">Service Invocation: Request/Response and One-way message.</span></span>

- <span data-ttu-id="b1dc4-214">バインディング : Svcutil.exe でサポートされるすべてのバインディング</span><span class="sxs-lookup"><span data-stu-id="b1dc4-214">Bindings: all bindings supported by Svcutil.exe.</span></span>

- <span data-ttu-id="b1dc4-215">セッションの制御</span><span class="sxs-lookup"><span data-stu-id="b1dc4-215">Controlling Session.</span></span>

- <span data-ttu-id="b1dc4-216">メッセージ コントラクト</span><span class="sxs-lookup"><span data-stu-id="b1dc4-216">Message Contract.</span></span>

- <span data-ttu-id="b1dc4-217">XML シリアル化</span><span class="sxs-lookup"><span data-stu-id="b1dc4-217">XML serialization.</span></span>

<span data-ttu-id="b1dc4-218">WCF テストクライアントでサポートされていない機能の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-218">The following is a list of features not supported by WCF Test Client:</span></span>

- <span data-ttu-id="b1dc4-219">型: <xref:System.IO.Stream>、<xref:System.ServiceModel.Channels.Message>、<xref:System.Xml.XmlElement>、<xref:System.Xml.XmlAttribute>、<xref:System.Xml.XmlNode>、<xref:System.Xml.Serialization.IXmlSerializable> インターフェイスを実装する型 (関連する <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 属性を含む)、<xref:System.Xml.Linq.XDocument> 型と <xref:System.Xml.Linq.XElement> 型、および ADO.NET <xref:System.Data.DataTable> 型。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-219">Types: <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlNode>, types that implement the <xref:System.Xml.Serialization.IXmlSerializable> interface, including the related <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> attribute, and the <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> types and the ADO.NET <xref:System.Data.DataTable> type.</span></span>

- <span data-ttu-id="b1dc4-220">双方向コントラクト</span><span class="sxs-lookup"><span data-stu-id="b1dc4-220">Duplex contract.</span></span>

- <span data-ttu-id="b1dc4-221">トランザクション</span><span class="sxs-lookup"><span data-stu-id="b1dc4-221">Transaction.</span></span>

- <span data-ttu-id="b1dc4-222">セキュリティ: CardSpace、証明書、およびユーザー名/パスワード。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-222">Security: CardSpace , Certificate, and Username/Password.</span></span>

- <span data-ttu-id="b1dc4-223">バインディング : WSFederationBinding、任意のコンテキスト バインディングおよび HTTPS バインディング、WebHttpBinding (JSON 応答メッセージ サポート)</span><span class="sxs-lookup"><span data-stu-id="b1dc4-223">Bindings: WSFederationbinding, any Context bindings and Https binding, WebHttpbinding (Json response message support).</span></span>

## <a name="closing-wcf-test-client"></a><span data-ttu-id="b1dc4-224">WCF のテスト用クライアントの終了</span><span class="sxs-lookup"><span data-stu-id="b1dc4-224">Closing WCF Test Client</span></span>

<span data-ttu-id="b1dc4-225">WCF テストクライアントは、次の方法で閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-225">You can close WCF Test Client in the following ways:</span></span>

- <span data-ttu-id="b1dc4-226">**[ファイル]** メニューの **[終了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-226">On the **File** menu, click **Exit**.</span></span> <span data-ttu-id="b1dc4-227">または、WCF テストクライアントのメインウィンドウで、[ **閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-227">Alternatively, in the WCF Test Client main window, click **Close**.</span></span> <span data-ttu-id="b1dc4-228">どちらのアクションも、wcf サービスの自動ホストをシャットダウンし、visual Studio によって WCF テストクライアントが起動された場合に Visual Studio のデバッグプロセスを停止します。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-228">Both of these actions also shut down WCF Service Auto Host and stop the Visual Studio debugging process if WCF Test Client was launched by Visual Studio.</span></span>

- <span data-ttu-id="b1dc4-229">通知領域の [ **WCF サービスホスト** ] アイコンを右クリックし、[終了] をクリックし **ます。**</span><span class="sxs-lookup"><span data-stu-id="b1dc4-229">Right-click the **WCF Service Host** icon in the notification area, and then click **Exit.**</span></span> <span data-ttu-id="b1dc4-230">これにより、WCF サービスの自動ホストと WCF テストクライアントの両方がシャットダウンされ、Visual Studio のデバッグプロセスが停止します。</span><span class="sxs-lookup"><span data-stu-id="b1dc4-230">This shuts down both WCF Service Auto Host and WCF Test Client and stops the Visual Studio debugging process.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1dc4-231">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1dc4-231">See also</span></span>

- [<span data-ttu-id="b1dc4-232">WCF サービス ホスト (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="b1dc4-232">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
