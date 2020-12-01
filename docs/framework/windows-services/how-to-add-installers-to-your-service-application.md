---
title: '方法: サービス アプリケーションにインストーラーを追加する'
description: サービス アプリケーションにインストーラを追加する方法について確認します。 Visual Studio には、サービス アプリに関連付けられているリソースをインストールできるインストール コンポーネントが付属しています。
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, deploying
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
ms.openlocfilehash: 451f0db21e80dfc3dc40052179ac4ec60c2aabdc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270668"
---
# <a name="how-to-add-installers-to-your-service-application"></a><span data-ttu-id="14016-104">方法: サービス アプリケーションにインストーラーを追加する</span><span class="sxs-lookup"><span data-stu-id="14016-104">How to: Add Installers to Your Service Application</span></span>

<span data-ttu-id="14016-105">Visual Studio には、サービス アプリケーションに関連付けられているリソースをインストールできるインストール コンポーネントが付属しています。</span><span class="sxs-lookup"><span data-stu-id="14016-105">Visual Studio ships installation components that can install resources associated with your service applications.</span></span> <span data-ttu-id="14016-106">インストール コンポーネントは、個々のサービスをインストール先のシステムに登録し、サービス コントロール マネージャーにサービスが存在することを認識させます。</span><span class="sxs-lookup"><span data-stu-id="14016-106">Installation components register an individual service on the system to which it is being installed and let the Services Control Manager know that the service exists.</span></span> <span data-ttu-id="14016-107">サービス アプリケーションを操作するときは、[プロパティ] ウィンドウでリンクを選択して、適切なインストーラーをプロジェクトに自動的に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="14016-107">When you work with a service application, you can select a link in the Properties window to automatically add the appropriate installers to your project.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14016-108">サービスに対するプロパティの値は、サービス クラスからインストーラー クラスにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="14016-108">Property values for your service are copied from the service class to the installer class.</span></span> <span data-ttu-id="14016-109">サービス クラスでプロパティの値を更新した場合、インストーラーでは自動的には更新されません。</span><span class="sxs-lookup"><span data-stu-id="14016-109">If you update the property values on the service class, they are not automatically updated in the installer.</span></span>  
  
 <span data-ttu-id="14016-110">インストーラーをプロジェクトに追加すると、新しいクラス (既定の名前は `ProjectInstaller`) がプロジェクトに作成され、その中に適切なインストール コンポーネントのインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="14016-110">When you add an installer to your project, a new class (which, by default, is named `ProjectInstaller`) is created in the project, and instances of the appropriate installation components are created within it.</span></span> <span data-ttu-id="14016-111">このクラスは、プロジェクトで必要なすべてのインストール コンポーネントの中心的な場所として機能します。</span><span class="sxs-lookup"><span data-stu-id="14016-111">This class acts as a central point for all of the installation components your project needs.</span></span> <span data-ttu-id="14016-112">たとえば、2 番目のサービスをアプリケーションに追加し、[インストーラーの追加] リンクをクリックしても、2 番目のインストーラー クラスは作成されません。代わりに、2 番目のサービスに必要な追加のインストール コンポーネントは、既存のクラスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="14016-112">For example, if you add a second service to your application and click the Add Installer link, a second installer class is not created; instead, the necessary additional installation component for the second service is added to the existing class.</span></span>  
  
 <span data-ttu-id="14016-113">サービスが正しくインストールされるようにするために、インストーラー内で特殊なコーディングを行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="14016-113">You do not need to do any special coding within the installers to make your services install correctly.</span></span> <span data-ttu-id="14016-114">ただし、インストール プロセスに特別な機能を追加する必要がある場合は、インストーラーの内容の変更が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="14016-114">However, you may occasionally need to modify the contents of the installers if you need to add special functionality to the installation process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14016-115">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="14016-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="14016-116">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="14016-116">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="14016-117">詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14016-117">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-installers-to-your-service-application"></a><span data-ttu-id="14016-118">サービス アプリケーションにインストーラーを追加するには</span><span class="sxs-lookup"><span data-stu-id="14016-118">To add installers to your service application</span></span>  
  
1. <span data-ttu-id="14016-119">**ソリューション エクスプローラー** で、インストール コンポーネントを追加するサービスの **[デザイン]** ビューにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="14016-119">In **Solution Explorer**, access **Design** view for the service for which you want to add an installation component.</span></span>  
  
2. <span data-ttu-id="14016-120">デザイナーの背景をクリックして、サービスの内容ではなくサービス自体を選択します。</span><span class="sxs-lookup"><span data-stu-id="14016-120">Click the background of the designer to select the service itself, rather than any of its contents.</span></span>  
  
3. <span data-ttu-id="14016-121">デザイナーにフォーカスを置いた状態で右クリックし、 **[インストーラーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="14016-121">With the designer in focus, right-click, and then click **Add Installer**.</span></span>  
  
     <span data-ttu-id="14016-122">新しいクラス `ProjectInstaller`、および 2 つのインストール コンポーネント <xref:System.ServiceProcess.ServiceProcessInstaller> と <xref:System.ServiceProcess.ServiceInstaller> がプロジェクトに追加され、サービスのプロパティ値がコンポーネントにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="14016-122">A new class, `ProjectInstaller`, and two installation components, <xref:System.ServiceProcess.ServiceProcessInstaller> and <xref:System.ServiceProcess.ServiceInstaller>, are added to your project, and property values for the service are copied to the components.</span></span>  
  
4. <span data-ttu-id="14016-123"><xref:System.ServiceProcess.ServiceInstaller> コンポーネントをクリックし、<xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> プロパティが、サービス自体の <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> プロパティと同じ値に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="14016-123">Click the <xref:System.ServiceProcess.ServiceInstaller> component and verify that the value of the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to the same value as the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property on the service itself.</span></span>  
  
5. <span data-ttu-id="14016-124">サービスの開始方法を決定するには、<xref:System.ServiceProcess.ServiceInstaller> コンポーネントをクリックし、<xref:System.ServiceProcess.ServiceInstaller.StartType%2A> プロパティを適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="14016-124">To determine how your service will be started, click the <xref:System.ServiceProcess.ServiceInstaller> component and set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to the appropriate value.</span></span>  
  
    |<span data-ttu-id="14016-125">[値]</span><span class="sxs-lookup"><span data-stu-id="14016-125">Value</span></span>|<span data-ttu-id="14016-126">結果</span><span class="sxs-lookup"><span data-stu-id="14016-126">Result</span></span>|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|<span data-ttu-id="14016-127">インストールの後、サービスを手動で開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14016-127">The service must be manually started after installation.</span></span> <span data-ttu-id="14016-128">詳細については、[サービスを開始する](how-to-start-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14016-128">For more information, see [How to: Start Services](how-to-start-services.md).</span></span>|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|<span data-ttu-id="14016-129">サービスは、コンピューターが再起動されるたびに、自動的に開始します。</span><span class="sxs-lookup"><span data-stu-id="14016-129">The service will start by itself whenever the computer reboots.</span></span>|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|<span data-ttu-id="14016-130">サービスは開始できません。</span><span class="sxs-lookup"><span data-stu-id="14016-130">The service cannot be started.</span></span>|  
  
6. <span data-ttu-id="14016-131">サービスが実行するセキュリティ コンテキストを決定するには、<xref:System.ServiceProcess.ServiceProcessInstaller> コンポーネントをクリックし、適切なプロパティ値を設定します。</span><span class="sxs-lookup"><span data-stu-id="14016-131">To determine the security context in which your service will run, click the <xref:System.ServiceProcess.ServiceProcessInstaller> component and set the appropriate property values.</span></span> <span data-ttu-id="14016-132">詳細については、[サービスのセキュリティ コンテキストを指定する](how-to-specify-the-security-context-for-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14016-132">For more information, see [How to: Specify the Security Context for Services](how-to-specify-the-security-context-for-services.md).</span></span>  
  
7. <span data-ttu-id="14016-133">カスタム処理を実行する必要があるメソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="14016-133">Override any methods for which you need to perform custom processing.</span></span>  
  
8. <span data-ttu-id="14016-134">プロジェクトの追加サービスごとに、手順 1 から 7 を実行します。</span><span class="sxs-lookup"><span data-stu-id="14016-134">Perform steps 1 through 7 for each additional service in your project.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="14016-135">プロジェクトの追加サービスごとに、新しい <xref:System.ServiceProcess.ServiceInstaller> コンポーネントをプロジェクトの `ProjectInstaller` クラスに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14016-135">For each additional service in your project, you must add an additional <xref:System.ServiceProcess.ServiceInstaller> component to the project's `ProjectInstaller` class.</span></span> <span data-ttu-id="14016-136">手順 3 で追加した <xref:System.ServiceProcess.ServiceProcessInstaller> コンポーネントは、プロジェクト内のすべての個別サービス インストーラーで動作します。</span><span class="sxs-lookup"><span data-stu-id="14016-136">The <xref:System.ServiceProcess.ServiceProcessInstaller> component added in step three works with all of the individual service installers in the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14016-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="14016-137">See also</span></span>

- [<span data-ttu-id="14016-138">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="14016-138">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="14016-139">方法: サービスをインストールおよびアンインストールする</span><span class="sxs-lookup"><span data-stu-id="14016-139">How to: Install and Uninstall Services</span></span>](how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="14016-140">方法: サービスを開始する</span><span class="sxs-lookup"><span data-stu-id="14016-140">How to: Start Services</span></span>](how-to-start-services.md)
- [<span data-ttu-id="14016-141">方法: サービスのセキュリティ コンテキストを指定する</span><span class="sxs-lookup"><span data-stu-id="14016-141">How to: Specify the Security Context for Services</span></span>](how-to-specify-the-security-context-for-services.md)
