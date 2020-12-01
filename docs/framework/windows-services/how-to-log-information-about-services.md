---
title: '方法: サービスに関する情報のログを記録する'
description: サービスに関する情報のログを記録する方法を理解します。 Windows サービス プロジェクトがアプリケーション イベント ログとやりとりする場合は、AutoLog プロパティを設定します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoLog property
- services, logging information
- Windows Service applications, logging information about
- event logs, service applications
- application event logs, service applications
- logs, service applications
ms.assetid: c0d8140f-c055-4d8e-a2e0-37358a550116
ms.openlocfilehash: 2e5f1fd8ebbbb218e8d6eba9b2d30d05e7c0e62c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270577"
---
# <a name="how-to-log-information-about-services"></a><span data-ttu-id="bf1ee-104">方法: サービスに関する情報のログを記録する</span><span class="sxs-lookup"><span data-stu-id="bf1ee-104">How to: Log Information About Services</span></span>

<span data-ttu-id="bf1ee-105">既定では、すべての Windows サービス プロジェクトはアプリケーション イベント ログとやり取りして、そこに情報および例外を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-105">By default, all Windows Service projects have the ability to interact with the Application event log and write information and exceptions to it.</span></span> <span data-ttu-id="bf1ee-106">アプリケーションにこの機能が必要かどうかを指定するには、 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-106">You use the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to indicate whether you want this functionality in your application.</span></span> <span data-ttu-id="bf1ee-107">既定では、Windows サービス プロジェクト テンプレートで作成したサービスには、ログが有効にされます。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-107">By default, logging is turned on for any service you create with the Windows Service project template.</span></span> <span data-ttu-id="bf1ee-108"><xref:System.Diagnostics.EventLog> クラスの静的フォームを使用すると、 <xref:System.Diagnostics.EventLog> コンポーネントのインスタンスを作成したり、手動でソースを登録したりすることなく、ログにサービス情報を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-108">You can use a static form of the <xref:System.Diagnostics.EventLog> class to write service information to a log without having to create an instance of an <xref:System.Diagnostics.EventLog> component or manually register a source.</span></span>  
  
 <span data-ttu-id="bf1ee-109">ログが有効にされていると、サービスのインストーラーは自動的に、プロジェクトの各サービスを有効なイベント ソースとして、サービスのインストール先コンピューター上のアプリケーション ログに登録します。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-109">The installer for your service automatically registers each service in your project as a valid source of events with the Application log on the computer where the service is installed, when logging is turned on.</span></span> <span data-ttu-id="bf1ee-110">サービスの起動時、停止時、一時停止時、再開時、インストール時、アンインストール時には常に、サービスが情報をログに記録します。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-110">The service logs information each time the service is started, stopped, paused, resumed, installed, or uninstalled.</span></span> <span data-ttu-id="bf1ee-111">また、発生したすべてのエラーもログに記録します。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-111">It also logs any failures that occur.</span></span> <span data-ttu-id="bf1ee-112">既定の動作を使用している場合、ログにエントリを書き込むためのコードを作成する必要はありません。これは、サービスが自動的に処理します。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-112">You do not need to write any code to write entries to the log when using the default behavior; the service handles this for you automatically.</span></span>  
  
 <span data-ttu-id="bf1ee-113">アプリケーション ログ以外のイベント ログに書き込む必要がある場合は、 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> プロパティを `false`に設定し、サービス コード内に独自のカスタム イベント ログを作成して、そのログに有効なエントリのソースとしてサービスを登録します。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-113">If you want to write to an event log other than the Application log, you must set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`, create your own custom event log within your services code, and register your service as a valid source of entries for that log.</span></span> <span data-ttu-id="bf1ee-114">その後、対象の操作が行われるたびにログにエントリを記録するコードを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-114">You must then write code to record entries to the log whenever an action you're interested in occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf1ee-115">カスタム イベント ログを使用して、そのログに書き込むようにサービス アプリケーションを構成する場合、コードでサービスの <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> プロパティを設定する前に、そのイベント ログにアクセスしようとしないでください。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-115">If you use a custom event log and configure your service application to write to it, you must not attempt to access the event log before setting the service's <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property in your code.</span></span> <span data-ttu-id="bf1ee-116">サービスを有効なイベントのソースとして登録するには、イベント ログにこのプロパティの値が必要です。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-116">The event log needs this property's value to register your service as a valid source of events.</span></span>  
  
### <a name="to-enable-default-event-logging-for-your-service"></a><span data-ttu-id="bf1ee-117">サービスの既定のイベント ログを有効にするには</span><span class="sxs-lookup"><span data-stu-id="bf1ee-117">To enable default event logging for your service</span></span>  
  
- <span data-ttu-id="bf1ee-118">コンポーネントの <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> プロパティを `true`に設定します。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-118">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `true`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bf1ee-119">既定では、このプロパティは `true`に設定されています。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-119">By default, this property is set to `true`.</span></span> <span data-ttu-id="bf1ee-120">条件を評価してから、その条件の結果に基づいて <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> プロパティを設定するなどの複雑な処理を作成するのでない限り、このプロパティを明示的に設定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-120">You do not need to set this explicitly unless you are building more complex processing, such as evaluating a condition and then setting the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property based on the result of that condition.</span></span>  
  
### <a name="to-disable-event-logging-for-your-service"></a><span data-ttu-id="bf1ee-121">サービスの既定のイベント ログを無効にするには</span><span class="sxs-lookup"><span data-stu-id="bf1ee-121">To disable event logging for your service</span></span>  
  
- <span data-ttu-id="bf1ee-122">コンポーネントの <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> プロパティを `false`に設定します。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-122">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `false`.</span></span>  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a><span data-ttu-id="bf1ee-123">カスタム ログへのログ記録を設定するには</span><span class="sxs-lookup"><span data-stu-id="bf1ee-123">To set up logging to a custom log</span></span>  
  
1. <span data-ttu-id="bf1ee-124"><xref:System.ServiceProcess.ServiceBase.AutoLog%2A> プロパティを `false`に設定します。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-124">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bf1ee-125">カスタム ログを使用するには、 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> を false に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-125">You must set <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> to false in order to use a custom log.</span></span>  
  
2. <span data-ttu-id="bf1ee-126">Windows サービス アプリケーションに <xref:System.Diagnostics.EventLog> コンポーネントのインスタンスを設定します。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-126">Set up an instance of an <xref:System.Diagnostics.EventLog> component in your Windows Service application.</span></span>  
  
3. <span data-ttu-id="bf1ee-127"><xref:System.Diagnostics.EventLog.CreateEventSource%2A> メソッドを呼び出し、作成するログ ファイルのソース文字列と名前を指定して、カスタム ログを作成します。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-127">Create a custom log by calling the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method and specifying the source string and the name of the log file you want to create.</span></span>  
  
4. <span data-ttu-id="bf1ee-128"><xref:System.Diagnostics.EventLog.Source%2A> コンポーネント インスタンスの <xref:System.Diagnostics.EventLog> プロパティを、手順 3 で作成したソース文字列に設定します。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-128">Set the <xref:System.Diagnostics.EventLog.Source%2A> property on the <xref:System.Diagnostics.EventLog> component instance to the source string you created in step 3.</span></span>  
  
5. <span data-ttu-id="bf1ee-129"><xref:System.Diagnostics.EventLog.WriteEntry%2A> コンポーネント インスタンスで <xref:System.Diagnostics.EventLog> メソッドにアクセスして、エントリを作成します。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-129">Write your entries by accessing the <xref:System.Diagnostics.EventLog.WriteEntry%2A> method on the <xref:System.Diagnostics.EventLog> component instance.</span></span>  
  
     <span data-ttu-id="bf1ee-130">次のコードに、カスタム ログへのログ記録を設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-130">The following code shows how to set up logging to a custom log.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bf1ee-131">このコード例では、 <xref:System.Diagnostics.EventLog> コンポーネントのインスタンスに `eventLog1` という名前を付けています (Visual Basic では`EventLog1` )。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-131">In this code example, an instance of an <xref:System.Diagnostics.EventLog> component is named `eventLog1` (`EventLog1` in Visual Basic).</span></span> <span data-ttu-id="bf1ee-132">手順 2 で別の名前を持つインスタンスを作成した場合は、それに応じてコードを変更してください。</span><span class="sxs-lookup"><span data-stu-id="bf1ee-132">If you created an instance with another name in step 2, change the code accordingly.</span></span>  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="bf1ee-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf1ee-133">See also</span></span>

- [<span data-ttu-id="bf1ee-134">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="bf1ee-134">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
