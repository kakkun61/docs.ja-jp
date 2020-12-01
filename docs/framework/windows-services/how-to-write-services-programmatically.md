---
title: '方法: プログラムでサービスを作成する'
description: 継承とその他のインフラストラクチャ要素を自分で設定して、プログラムによってサービスを記述する方法を確認します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
ms.openlocfilehash: ab153b89272323a1a7a71181559f4f4eee082640
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270512"
---
# <a name="how-to-write-services-programmatically"></a><span data-ttu-id="3c792-103">方法: プログラムでサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="3c792-103">How to: Write Services Programmatically</span></span>

<span data-ttu-id="3c792-104">Windows サービス プロジェクトのテンプレートを使用しない場合は、継承などの基本要素を設定して独自のサービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3c792-104">If you choose not to use the Windows Service project template, you can write your own services by setting up the inheritance and other infrastructure elements yourself.</span></span> <span data-ttu-id="3c792-105">プログラミングによってサービスを作成する場合は、テンプレートでは自動化される手順を手動で行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c792-105">When you create a service programmatically, you must perform several steps that the template would otherwise handle for you:</span></span>  
  
- <span data-ttu-id="3c792-106">サービス クラスが <xref:System.ServiceProcess.ServiceBase> クラスから継承されるように設定します。</span><span class="sxs-lookup"><span data-stu-id="3c792-106">You must set up your service class to inherit from the <xref:System.ServiceProcess.ServiceBase> class.</span></span>  
  
- <span data-ttu-id="3c792-107">サービス プロジェクトの `Main` メソッドを作成します。このメソッドは、実行するサービスを定義し、それに対して <xref:System.ServiceProcess.ServiceBase.Run%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3c792-107">You must create a `Main` method for your service project that defines the services to run and calls the <xref:System.ServiceProcess.ServiceBase.Run%2A> method on them.</span></span>  
  
- <span data-ttu-id="3c792-108"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> プロシージャと <xref:System.ServiceProcess.ServiceBase.OnStop%2A> プロシージャをオーバーライドし、任意の処理内容を記述します。</span><span class="sxs-lookup"><span data-stu-id="3c792-108">You must override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures and fill in any code you want them to run.</span></span>  
  
### <a name="to-write-a-service-programmatically"></a><span data-ttu-id="3c792-109">プログラミングによってサービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="3c792-109">To write a service programmatically</span></span>  
  
1. <span data-ttu-id="3c792-110">空のプロジェクトを作成し、必要な名前空間への参照を作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="3c792-110">Create an empty project and create a reference to the necessary namespaces by following these steps:</span></span>  
  
    1. <span data-ttu-id="3c792-111">**ソリューション エクスプローラー** で、 **[参照]** ノードを右クリックし、 **[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c792-111">In **Solution Explorer**, right-click the **References** node and click **Add Reference**.</span></span>  
  
    2. <span data-ttu-id="3c792-112">**[.NET Framework]** タブで **System.dll** までスクロールして選択し、 **[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c792-112">On the **.NET Framework** tab, scroll to **System.dll** and click **Select**.</span></span>  
  
    3. <span data-ttu-id="3c792-113">**System.ServiceProcess.dll** までスクロールして選択し、 **[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c792-113">Scroll to **System.ServiceProcess.dll** and click **Select**.</span></span>  
  
    4. <span data-ttu-id="3c792-114">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c792-114">Click **OK**.</span></span>  
  
2. <span data-ttu-id="3c792-115">クラスを追加し、<xref:System.ServiceProcess.ServiceBase> から継承されるように設定します。</span><span class="sxs-lookup"><span data-stu-id="3c792-115">Add a class and configure it to inherit from <xref:System.ServiceProcess.ServiceBase>:</span></span>  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. <span data-ttu-id="3c792-116">次のコードを追加してサービス クラスを設定します。</span><span class="sxs-lookup"><span data-stu-id="3c792-116">Add the following code to configure your service class:</span></span>  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. <span data-ttu-id="3c792-117">クラスの `Main` メソッドを作成し、それを使用してクラスに含まれるサービスを定義します。`userService1` がクラスの名前です。</span><span class="sxs-lookup"><span data-stu-id="3c792-117">Create a `Main` method for your class, and use it to define the service your class will contain; `userService1` is the name of the class:</span></span>  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. <span data-ttu-id="3c792-118"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドをオーバーライドし、サービスの開始時に実行する処理を定義します。</span><span class="sxs-lookup"><span data-stu-id="3c792-118">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and define any processing you want to occur when your service is started.</span></span>  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. <span data-ttu-id="3c792-119">他に独自の処理を定義するメソッドがあればそれをオーバーライドし、サービスが行うアクションを記述します。</span><span class="sxs-lookup"><span data-stu-id="3c792-119">Override any other methods you want to define custom processing for, and write code to determine the actions the service should take in each case.</span></span>  
  
7. <span data-ttu-id="3c792-120">サービス アプリケーションの必要なインストーラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="3c792-120">Add the necessary installers for your service application.</span></span> <span data-ttu-id="3c792-121">詳細については、[サービス アプリケーションにインストーラーを追加する](how-to-add-installers-to-your-service-application.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c792-121">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
8. <span data-ttu-id="3c792-122">**[ビルド]** メニューの **[ソリューションのビルド]** をクリックして、プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3c792-122">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3c792-123">F5 キーを押してプロジェクトを実行しないでください。この方法ではサービス プロジェクトを実行できません。</span><span class="sxs-lookup"><span data-stu-id="3c792-123">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
9. <span data-ttu-id="3c792-124">セットアップ プロジェクトと、サービスをインストールするカスタム処理を作成します。</span><span class="sxs-lookup"><span data-stu-id="3c792-124">Create a setup project and the custom actions to install your service.</span></span> <span data-ttu-id="3c792-125">例については、「[チュートリアル: コンポーネント デザイナーによる Windows サービス アプリケーションの作成](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c792-125">For an example, see [Walkthrough: Creating a Windows Service Application in the Component Designer](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
10. <span data-ttu-id="3c792-126">サービスをインストールします。</span><span class="sxs-lookup"><span data-stu-id="3c792-126">Install the service.</span></span> <span data-ttu-id="3c792-127">詳細については、[サービスをインストールおよびアンインストールする](how-to-install-and-uninstall-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c792-127">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c792-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c792-128">See also</span></span>

- [<span data-ttu-id="3c792-129">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="3c792-129">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="3c792-130">方法: Windows サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="3c792-130">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="3c792-131">方法: サービス アプリケーションにインストーラーを追加する</span><span class="sxs-lookup"><span data-stu-id="3c792-131">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="3c792-132">方法: サービスに関する情報のログを記録する</span><span class="sxs-lookup"><span data-stu-id="3c792-132">How to: Log Information About Services</span></span>](how-to-log-information-about-services.md)
- [<span data-ttu-id="3c792-133">チュートリアル: コンポーネント デザイナーによる Windows サービス アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="3c792-133">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
