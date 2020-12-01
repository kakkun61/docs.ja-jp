---
title: '方法: サービスのセキュリティ コンテキストを指定する'
description: サービスのセキュリティ コンテキストを指定します。 既定のシステム アカウントのコンテキストで実行されるサービスには、ログインしているユーザーとは別のシステム リソースのアクセス権があります。
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
ms.openlocfilehash: dcf0680f1bcb0f0e927bdb37ea56f7b3025be09b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270538"
---
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="2a2c0-104">方法: サービスのセキュリティ コンテキストを指定する</span><span class="sxs-lookup"><span data-stu-id="2a2c0-104">How to: Specify the Security Context for Services</span></span>

<span data-ttu-id="2a2c0-105">既定では、サービスはログインしているユーザーのセキュリティ コンテキストとは異なるセキュリティ コンテキストで実行します。</span><span class="sxs-lookup"><span data-stu-id="2a2c0-105">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="2a2c0-106">サービスは `LocalSystem` という名前の既定のシステム アカウントのコンテキストで実行し、このコンテキストはサービスに対してユーザーとは異なるシステム リソースへのアクセス特権を付与します。</span><span class="sxs-lookup"><span data-stu-id="2a2c0-106">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="2a2c0-107">この動作を変更し、サービスの実行が異なるユーザー アカウントで行われるように指定することができます。</span><span class="sxs-lookup"><span data-stu-id="2a2c0-107">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="2a2c0-108">サービスが実行しているプロセスの <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> プロパティを操作することで、セキュリティ コンテキストを設定します。</span><span class="sxs-lookup"><span data-stu-id="2a2c0-108">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="2a2c0-109">このプロパティでは、次の 4 種類のアカウントのいずれかに、サービスを設定できます。</span><span class="sxs-lookup"><span data-stu-id="2a2c0-109">This property allows you to set the service to one of four account types:</span></span>  
  
- <span data-ttu-id="2a2c0-110">`User`: システムは、サービスのインストール時に有効なユーザー名とパスワードの指定を要求し、ネットワーク上の 1 人のユーザーによって指定されたアカウントのコンテキストで実行します。</span><span class="sxs-lookup"><span data-stu-id="2a2c0-110">`User`, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
- <span data-ttu-id="2a2c0-111">`LocalService`: ローカル コンピューター上で非特権ユーザーとして機能し、リモート サーバーに匿名の資格情報を提示するアカウントのコンテキストで実行します。</span><span class="sxs-lookup"><span data-stu-id="2a2c0-111">`LocalService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
- <span data-ttu-id="2a2c0-112">`LocalSystem`: 広範なローカル特権を提供し、リモート サーバーにコンピューターの資格情報を提示するアカウントのコンテキストで実行します。</span><span class="sxs-lookup"><span data-stu-id="2a2c0-112">`LocalSystem`, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
- <span data-ttu-id="2a2c0-113">`NetworkService`: ローカル コンピューター上で非特権ユーザーとして機能し、リモート サーバーにコンピューターの資格情報を提示するアカウントのコンテキストで実行します。</span><span class="sxs-lookup"><span data-stu-id="2a2c0-113">`NetworkService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="2a2c0-114">詳細については、<xref:System.ServiceProcess.ServiceAccount> 列挙型のページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2a2c0-114">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="2a2c0-115">サービスのセキュリティ コンテキストを指定するには</span><span class="sxs-lookup"><span data-stu-id="2a2c0-115">To specify the security context for a service</span></span>  
  
1. <span data-ttu-id="2a2c0-116">サービスの作成後、必要なインストーラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="2a2c0-116">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="2a2c0-117">詳細については、[サービス アプリケーションにインストーラーを追加する](how-to-add-installers-to-your-service-application.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a2c0-117">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
2. <span data-ttu-id="2a2c0-118">デザイナーで、`ProjectInstaller` クラスにアクセスし、対象となるサービスのサービス プロセス インストーラーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a2c0-118">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2a2c0-119">すべてのサービス アプリケーションについて、`ProjectInstaller` クラスには少なくとも 2 つのインストール コンポーネントがあります。プロジェクト内のすべてのサービスに対するプロセスをインストールするものと、アプリケーションに含まれるサービスごとに 1 つのインストーラーです。</span><span class="sxs-lookup"><span data-stu-id="2a2c0-119">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="2a2c0-120">このインスタンスでは、<xref:System.ServiceProcess.ServiceProcessInstaller> を選びます。</span><span class="sxs-lookup"><span data-stu-id="2a2c0-120">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3. <span data-ttu-id="2a2c0-121">**[プロパティ]** ウィンドウで、<xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="2a2c0-121">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a2c0-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a2c0-122">See also</span></span>

- [<span data-ttu-id="2a2c0-123">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="2a2c0-123">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="2a2c0-124">方法: サービス アプリケーションにインストーラーを追加する</span><span class="sxs-lookup"><span data-stu-id="2a2c0-124">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="2a2c0-125">方法: Windows サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="2a2c0-125">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
