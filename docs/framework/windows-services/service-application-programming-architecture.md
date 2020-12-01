---
title: サービス アプリケーションのプログラミング アーキテクチャ
description: サービス アプリケーションのプログラミング アーキテクチャについて理解します。 Windows サービス アプリケーションは、System.ServiceProcess.ServiceBase から継承するクラスが基になっています。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceController components, programming architecture
- ServiceBase class, service states
- Windows Service applications, code model
- services, programming architecture
- ServiceController class
- services, states
- ServiceProcessInstaller class, service application code model
- Windows Service applications, states
ms.assetid: 83230026-d068-4174-97ff-e264c896eb2f
ms.openlocfilehash: c2344dd0a7d35781aea52b24694f2cfee70a6d41
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270459"
---
# <a name="service-application-programming-architecture"></a><span data-ttu-id="ba031-104">サービス アプリケーションのプログラミング アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="ba031-104">Service Application Programming Architecture</span></span>

<span data-ttu-id="ba031-105">Windows サービス アプリケーションは、<xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> クラスから継承するクラスが基になっています。</span><span class="sxs-lookup"><span data-stu-id="ba031-105">Windows Service applications are based on a class that inherits from the <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="ba031-106">このクラスのメソッドをオーバーライドして機能を定義し、サービスの動作を決定します。</span><span class="sxs-lookup"><span data-stu-id="ba031-106">You override methods from this class and define functionality for them to determine how your service behaves.</span></span>  
  
 <span data-ttu-id="ba031-107">サービスの作成に関連する主要なクラスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ba031-107">The main classes involved in service creation are:</span></span>  
  
- <span data-ttu-id="ba031-108"><xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> — サービスを作成するときに <xref:System.ServiceProcess.ServiceBase> クラスのメソッドをオーバーライドし、この継承したクラスでサービスがどのように機能するかを決定するコードを定義します。</span><span class="sxs-lookup"><span data-stu-id="ba031-108"><xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> — You override methods from the <xref:System.ServiceProcess.ServiceBase> class when creating a service and define the code to determine how your service functions in this inherited class.</span></span>  
  
- <span data-ttu-id="ba031-109"><xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType>、<xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> — これらのクラスは、サービスのインストールとアンインストールに使います。</span><span class="sxs-lookup"><span data-stu-id="ba031-109"><xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType> and <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> —You use these classes to install and uninstall your service.</span></span>  
  
 <span data-ttu-id="ba031-110">さらに、<xref:System.ServiceProcess.ServiceController> という名前のクラスを使って、サービス自体を操作できます。</span><span class="sxs-lookup"><span data-stu-id="ba031-110">In addition, a class named <xref:System.ServiceProcess.ServiceController> can be used to manipulate the service itself.</span></span> <span data-ttu-id="ba031-111">このクラスは、サービスの作成には含まれませんが、サービスを開始および停止し、サービスにコマンドを渡し、サービスから一連の列挙値を戻すために使用できます。</span><span class="sxs-lookup"><span data-stu-id="ba031-111">This class is not involved in the creation of a service, but can be used to start and stop the service, pass commands to it, and return a series of enumerations.</span></span>  
  
## <a name="defining-your-services-behavior"></a><span data-ttu-id="ba031-112">サービスの動作の定義</span><span class="sxs-lookup"><span data-stu-id="ba031-112">Defining Your Service's Behavior</span></span>  

 <span data-ttu-id="ba031-113">サービス クラスにおいて、サービス コントロール マネージャー内でサービスの状態が変更されたときの動作を決定する基底クラスの関数をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="ba031-113">In your service class, you override base class functions that determine what happens when the state of your service is changed in the Services Control Manager.</span></span> <span data-ttu-id="ba031-114"><xref:System.ServiceProcess.ServiceBase> クラスで公開されている以下のメソッドをオーバーライドして、カスタム動作を追加できます。</span><span class="sxs-lookup"><span data-stu-id="ba031-114">The <xref:System.ServiceProcess.ServiceBase> class exposes the following methods, which you can override to add custom behavior.</span></span>  
  
|<span data-ttu-id="ba031-115">メソッド</span><span class="sxs-lookup"><span data-stu-id="ba031-115">Method</span></span>|<span data-ttu-id="ba031-116">オーバーライドの目的</span><span class="sxs-lookup"><span data-stu-id="ba031-116">Override to</span></span>|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|<span data-ttu-id="ba031-117">サービスが実行を開始するときに行う必要のあるアクションを示します。</span><span class="sxs-lookup"><span data-stu-id="ba031-117">Indicate what actions should be taken when your service starts running.</span></span> <span data-ttu-id="ba031-118">サービスが意味のある処理を実行するには、このプロシージャにコードを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba031-118">You must write code in this procedure for your service to perform useful work.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|<span data-ttu-id="ba031-119">サービスが一時停止されるときに行う必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="ba031-119">Indicate what should happen when your service is paused.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|<span data-ttu-id="ba031-120">サービスが実行を停止するときに行う必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="ba031-120">Indicate what should happen when your service stops running.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|<span data-ttu-id="ba031-121">サービスが一時停止後に正常な機能を再開するときに行う必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="ba031-121">Indicate what should happen when your service resumes normal functioning after being paused.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|<span data-ttu-id="ba031-122">システムがシャットダウンする時点でサービスが実行している場合に、シャットダウンの直前に行う必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="ba031-122">Indicate what should happen just prior to your system shutting down, if your service is running at that time.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|<span data-ttu-id="ba031-123">サービスがカスタム コマンドを受け取ったときに行う必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="ba031-123">Indicate what should happen when your service receives a custom command.</span></span> <span data-ttu-id="ba031-124">カスタム コマンドについて詳しくは、MSDN オンラインをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ba031-124">For more information on custom commands, see MSDN online.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|<span data-ttu-id="ba031-125">バッテリ低下や中断操作など、電源管理イベントを受信したときのサービスの応答方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ba031-125">Indicate how the service should respond when a power management event is received, such as a low battery or suspended operation.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="ba031-126">これらのメソッドは、サービスがその有効期間内に通過する状態を表しています。サービスは、ある状態から次の状態に遷移します。</span><span class="sxs-lookup"><span data-stu-id="ba031-126">These methods represent states that the service moves through in its lifetime; the service transitions from one state to the next.</span></span> <span data-ttu-id="ba031-127">たとえば、<xref:System.ServiceProcess.ServiceBase.OnStart%2A> が呼び出される前の <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> コマンドにサービスが応答することはありません。</span><span class="sxs-lookup"><span data-stu-id="ba031-127">For example, you will never get the service to respond to an <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> command before <xref:System.ServiceProcess.ServiceBase.OnStart%2A> has been called.</span></span>  
  
 <span data-ttu-id="ba031-128">他にも、注目する必要のあるプロパティとメソッドがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="ba031-128">There are several other properties and methods that are of interest.</span></span> <span data-ttu-id="ba031-129">次の設定があります。</span><span class="sxs-lookup"><span data-stu-id="ba031-129">These include:</span></span>  
  
- <span data-ttu-id="ba031-130"><xref:System.ServiceProcess.ServiceBase> クラスの <xref:System.ServiceProcess.ServiceBase.Run%2A> メソッド。</span><span class="sxs-lookup"><span data-stu-id="ba031-130">The <xref:System.ServiceProcess.ServiceBase.Run%2A> method on the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="ba031-131">このメソッドは、サービスのメイン エントリ ポイントです。</span><span class="sxs-lookup"><span data-stu-id="ba031-131">This is the main entry point for the service.</span></span> <span data-ttu-id="ba031-132">Windows サービス テンプレートを使ってサービスを作成するときは、アプリケーションの `Main` メソッドに、サービスを実行するコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="ba031-132">When you create a service using the Windows Service template, code is inserted in your application's `Main` method to run the service.</span></span> <span data-ttu-id="ba031-133">このコードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ba031-133">This code looks like this:</span></span>  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    > <span data-ttu-id="ba031-134">これらの例では、アプリケーションに含まれる各サービスを追加できる <xref:System.ServiceProcess.ServiceBase> 型の配列を使用しており、すべてのサービスを一緒に実行できます。</span><span class="sxs-lookup"><span data-stu-id="ba031-134">These examples use an array of type <xref:System.ServiceProcess.ServiceBase>, into which each service your application contains can be added, and then all of the services can be run together.</span></span> <span data-ttu-id="ba031-135">一方、作成するサービスが 1 つのみの場合は、配列は使わず、<xref:System.ServiceProcess.ServiceBase> から継承する新しいオブジェクトを単純に宣言して、それを実行します。</span><span class="sxs-lookup"><span data-stu-id="ba031-135">If you are only creating a single service, however, you might choose not to use the array and simply declare a new object inheriting from <xref:System.ServiceProcess.ServiceBase> and then run it.</span></span> <span data-ttu-id="ba031-136">例については、「[方法: プログラムでサービスを作成する](how-to-write-services-programmatically.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba031-136">For an example, see [How to: Write Services Programmatically](how-to-write-services-programmatically.md).</span></span>  
  
- <span data-ttu-id="ba031-137"><xref:System.ServiceProcess.ServiceBase> クラスの一連のプロパティ。</span><span class="sxs-lookup"><span data-stu-id="ba031-137">A series of properties on the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="ba031-138">これらは、サービスで呼び出すことができるメソッドを決定します。</span><span class="sxs-lookup"><span data-stu-id="ba031-138">These determine what methods can be called on your service.</span></span> <span data-ttu-id="ba031-139">たとえば、<xref:System.ServiceProcess.ServiceBase.CanStop%2A> プロパティを `true` に設定すると、サービスで <xref:System.ServiceProcess.ServiceBase.OnStop%2A> メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="ba031-139">For example, when the <xref:System.ServiceProcess.ServiceBase.CanStop%2A> property is set to `true`, the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method on your service can be called.</span></span> <span data-ttu-id="ba031-140"><xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> プロパティが `true` に設定されていると、<xref:System.ServiceProcess.ServiceBase.OnPause%2A> および <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="ba031-140">When the <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> property is set to `true`, the <xref:System.ServiceProcess.ServiceBase.OnPause%2A> and <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> methods can be called.</span></span> <span data-ttu-id="ba031-141">これらのプロパティのいずれかを `true` に設定するときは、関連するメソッドをオーバーライドして処理を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba031-141">When you set one of these properties to `true`, you should then override and define processing for the associated methods.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ba031-142">サービスが役に立つためには、少なくとも <xref:System.ServiceProcess.ServiceBase.OnStart%2A> と <xref:System.ServiceProcess.ServiceBase.OnStop%2A> をオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba031-142">Your service must override at least <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> to be useful.</span></span>  
  
 <span data-ttu-id="ba031-143">また、<xref:System.ServiceProcess.ServiceController> コンポーネントを使うと、既存のサービスと通信して、その動作を制御できます。</span><span class="sxs-lookup"><span data-stu-id="ba031-143">You can also use a component called the <xref:System.ServiceProcess.ServiceController> to communicate with and control the behavior of an existing service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba031-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba031-144">See also</span></span>

- [<span data-ttu-id="ba031-145">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="ba031-145">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="ba031-146">方法: Windows サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="ba031-146">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
