---
title: '方法: Windows サービスを作成する'
description: Windows サービス プロジェクト テンプレートを使用してサービスを作成します。 ServiceName プロパティを設定し、インストーラを作成して、OnStart と OnStop メソッドをオーバーライドします。
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
ms.openlocfilehash: 9b171fa54cf65a482625c276c26185b12075c753
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270707"
---
# <a name="how-to-create-windows-services"></a><span data-ttu-id="efe64-104">方法: Windows サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="efe64-104">How to: Create Windows Services</span></span>

<span data-ttu-id="efe64-105">サービスを作成するときには、**Windows サービス** と呼ばれる、Visual Studio プロジェクトのテンプレートを使用できます。</span><span class="sxs-lookup"><span data-stu-id="efe64-105">When you create a service, you can use a Visual Studio project template called **Windows Service**.</span></span> <span data-ttu-id="efe64-106">このテンプレートを使用すると、作業の多くを自動化できます。この自動化は、適切なクラスと名前空間を参照し、サービスの基底クラスからの継承を設定し、メソッドのいくつかをオーバーライドすることで実現されます。</span><span class="sxs-lookup"><span data-stu-id="efe64-106">This template automatically does much of the work for you by referencing the appropriate classes and namespaces, setting up the inheritance from the base class for services, and overriding several of the methods you're likely to want to override.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="efe64-107">Windows サービスのプロジェクト テンプレートは、Visual Studio の Express Edition では使用できません。</span><span class="sxs-lookup"><span data-stu-id="efe64-107">The Windows Services project template is not available in the Express edition of Visual Studio.</span></span>  
  
 <span data-ttu-id="efe64-108">実用的なサービスを作成するには、少なくとも以下の作業を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="efe64-108">At a minimum, to create a functional service you must:</span></span>  
  
- <span data-ttu-id="efe64-109"><xref:System.ServiceProcess.ServiceBase.ServiceName%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="efe64-109">Set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property.</span></span>  
  
- <span data-ttu-id="efe64-110">サービス アプリケーションに必要なインストーラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="efe64-110">Create the necessary installers for your service application.</span></span>  
  
- <span data-ttu-id="efe64-111"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドと <xref:System.ServiceProcess.ServiceBase.OnStop%2A> メソッドのオーバーライドとコーディングを行い、サービスの動作をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="efe64-111">Override and specify code for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods to customize the ways in which your service behaves.</span></span>  
  
### <a name="to-create-a-windows-service-application"></a><span data-ttu-id="efe64-112">Windows サービス アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="efe64-112">To create a Windows Service application</span></span>  
  
1. <span data-ttu-id="efe64-113">**Windows サービス** プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="efe64-113">Create a **Windows Service** project.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="efe64-114">テンプレートを使用せずにサービスを記述する方法については、「[方法: プログラムでサービスを作成する](how-to-write-services-programmatically.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efe64-114">For instructions on writing a service without using the template, see [How to: Write Services Programmatically](how-to-write-services-programmatically.md).</span></span>  
  
2. <span data-ttu-id="efe64-115">**[プロパティ]** ウィンドウで、サービスの <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="efe64-115">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for your service.</span></span>  
  
     <span data-ttu-id="efe64-116">![ServiceName プロパティを設定します。](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span><span class="sxs-lookup"><span data-stu-id="efe64-116">![Set the ServiceName property.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="efe64-117"><xref:System.ServiceProcess.ServiceBase.ServiceName%2A> プロパティの値は、各インストーラー クラスに記録されている名前と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="efe64-117">The value of the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property must always match the name recorded in the installer classes.</span></span> <span data-ttu-id="efe64-118">このプロパティを変更した場合は、インストーラー クラスの <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> プロパティも変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="efe64-118">If you change this property, you must update the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property of installer classes as well.</span></span>  
  
3. <span data-ttu-id="efe64-119">次のいずれかのプロパティを設定して、サービスの動作を決定します。</span><span class="sxs-lookup"><span data-stu-id="efe64-119">Set any of the following properties to determine how your service will function.</span></span>  
  
    |<span data-ttu-id="efe64-120">プロパティ</span><span class="sxs-lookup"><span data-stu-id="efe64-120">Property</span></span>|<span data-ttu-id="efe64-121">設定</span><span class="sxs-lookup"><span data-stu-id="efe64-121">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|<span data-ttu-id="efe64-122">サービスが実行停止要求を受け付ける場合は `True` を設定します。サービスの実行を停止しない場合は `false` を設定します。</span><span class="sxs-lookup"><span data-stu-id="efe64-122">`True` to indicate that the service will accept requests to stop running; `false` to prevent the service from being stopped.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|<span data-ttu-id="efe64-123">サービスがコンピューターのシャットダウン時に通知を受けて `True` プロシージャを呼び出す場合は、<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> を設定します。</span><span class="sxs-lookup"><span data-stu-id="efe64-123">`True` to indicate that the service wants to receive notification when the computer on which it lives shuts down, enabling it to call the <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedure.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|<span data-ttu-id="efe64-124">サービスが一時停止要求または再開要求を受け付ける場合は `True` を設定します。サービスを一時停止または再開しない場合は `false` を設定します。</span><span class="sxs-lookup"><span data-stu-id="efe64-124">`True` to indicate that the service will accept requests to pause or to resume running; `false` to prevent the service from being paused and resumed.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|<span data-ttu-id="efe64-125">コンピューターの電源状態の変化をサービスに通知する場合は `True` を設定します。サービスに電源状態の変化を通知しない場合は、`false` を設定します。</span><span class="sxs-lookup"><span data-stu-id="efe64-125">`True` to indicate that the service can handle notification of changes to the computer's power status; `false` to prevent the service from being notified of these changes.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|<span data-ttu-id="efe64-126">サービスがアクションを実行したときにアプリケーション イベント ログに情報を入力する場合は `True` を設定します。この機能を無効にする場合は `false` を設定します。</span><span class="sxs-lookup"><span data-stu-id="efe64-126">`True` to write informational entries to the Application event log when your service performs an action; `false` to disable this functionality.</span></span> <span data-ttu-id="efe64-127">詳細については、[サービスに関する情報のログを記録する](how-to-log-information-about-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efe64-127">For more information, see [How to: Log Information About Services](how-to-log-information-about-services.md).</span></span> <span data-ttu-id="efe64-128">**注:** 既定では、<xref:System.ServiceProcess.ServiceBase.AutoLog%2A> は `true` に設定されています。</span><span class="sxs-lookup"><span data-stu-id="efe64-128">**Note:**  By default, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> is set to `true`.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="efe64-129"><xref:System.ServiceProcess.ServiceBase.CanStop%2A> または <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> を `false` に設定すると、**サービス コントロール マネージャー** は、対応するメニュー オプション (サービスの停止、一時停止、または継続) を無効にします。</span><span class="sxs-lookup"><span data-stu-id="efe64-129">When <xref:System.ServiceProcess.ServiceBase.CanStop%2A> or <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> are set to `false`, the **Service Control Manager** will disable the corresponding menu options to stop, pause, or continue the service.</span></span>  
  
4. <span data-ttu-id="efe64-130">コード エディターを起動し、<xref:System.ServiceProcess.ServiceBase.OnStart%2A> プロシージャと <xref:System.ServiceProcess.ServiceBase.OnStop%2A> プロシージャの処理を記述します。</span><span class="sxs-lookup"><span data-stu-id="efe64-130">Access the Code Editor and fill in the processing you want for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures.</span></span>  
  
5. <span data-ttu-id="efe64-131">ほかに動作を定義するメソッドがある場合は、それをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="efe64-131">Override any other methods for which you want to define functionality.</span></span>  
  
6. <span data-ttu-id="efe64-132">サービス アプリケーションの必要なインストーラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="efe64-132">Add the necessary installers for your service application.</span></span> <span data-ttu-id="efe64-133">詳細については、[サービス アプリケーションにインストーラーを追加する](how-to-add-installers-to-your-service-application.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efe64-133">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
7. <span data-ttu-id="efe64-134">**[ビルド]** メニューの **[ソリューションのビルド]** をクリックして、プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="efe64-134">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="efe64-135">F5 キーを押してプロジェクトを実行しないでください。この方法ではサービス プロジェクトを実行できません。</span><span class="sxs-lookup"><span data-stu-id="efe64-135">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
8. <span data-ttu-id="efe64-136">サービスをインストールします。</span><span class="sxs-lookup"><span data-stu-id="efe64-136">Install the service.</span></span> <span data-ttu-id="efe64-137">詳細については、[サービスをインストールおよびアンインストールする](how-to-install-and-uninstall-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efe64-137">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efe64-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="efe64-138">See also</span></span>

- [<span data-ttu-id="efe64-139">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="efe64-139">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="efe64-140">方法: プログラムでサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="efe64-140">How to: Write Services Programmatically</span></span>](how-to-write-services-programmatically.md)
- [<span data-ttu-id="efe64-141">方法: サービス アプリケーションにインストーラーを追加する</span><span class="sxs-lookup"><span data-stu-id="efe64-141">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="efe64-142">方法: サービスに関する情報のログを記録する</span><span class="sxs-lookup"><span data-stu-id="efe64-142">How to: Log Information About Services</span></span>](how-to-log-information-about-services.md)
- [<span data-ttu-id="efe64-143">方法: サービスを開始する</span><span class="sxs-lookup"><span data-stu-id="efe64-143">How to: Start Services</span></span>](how-to-start-services.md)
- [<span data-ttu-id="efe64-144">方法: サービスのセキュリティ コンテキストを指定する</span><span class="sxs-lookup"><span data-stu-id="efe64-144">How to: Specify the Security Context for Services</span></span>](how-to-specify-the-security-context-for-services.md)
- [<span data-ttu-id="efe64-145">方法: サービスをインストールおよびアンインストールする</span><span class="sxs-lookup"><span data-stu-id="efe64-145">How to: Install and Uninstall Services</span></span>](how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="efe64-146">チュートリアル: コンポーネント デザイナーによる Windows サービス アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="efe64-146">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
