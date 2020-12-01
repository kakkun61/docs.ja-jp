---
title: 登録を必要としない COM 相互運用機能
description: 登録を必要としない COM 相互運用機能を使用してコンポーネントをアクティブにします。アセンブリ情報を格納するために Windows レジストリは使用しません。
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], interop
- COM interop, registration-free COM interop
- registration-free COM interop
- manifests [.NET Framework]
- registration-free activation
- object activation
- registration-free COM interop, about registration-free COM interop
ms.assetid: 90f308b9-82dc-414a-bce1-77e0155e56bd
ms.openlocfilehash: f61ad954215aecfc9380a47de788d36f327ab0b3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239537"
---
# <a name="registration-free-com-interop"></a><span data-ttu-id="3a23a-103">登録を必要としない COM 相互運用機能</span><span class="sxs-lookup"><span data-stu-id="3a23a-103">Registration-Free COM Interop</span></span>

<span data-ttu-id="3a23a-104">登録を必要としない COM 相互運用機能は、アセンブリ情報を格納するために Windows レジストリを使用しないで、コンポーネントをアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="3a23a-104">Registration-free COM interop activates a component without using the Windows registry to store assembly information.</span></span> <span data-ttu-id="3a23a-105">展開中にコンピューター上のコンポーネントを登録するのではなく、バインディングとアクティベーションに関する情報を含む Win32 スタイルのマニフェスト ファイルをデザイン時に作成します。</span><span class="sxs-lookup"><span data-stu-id="3a23a-105">Instead of registering a component on a computer during deployment, you create Win32-style manifest files at design time that contain information about binding and activation.</span></span> <span data-ttu-id="3a23a-106">レジストリ キーではなく、これらのマニフェスト ファイルが、オブジェクトのアクティベーションを指示します。</span><span class="sxs-lookup"><span data-stu-id="3a23a-106">These manifest files, rather than registry keys, direct the activation of an object.</span></span>  
  
 <span data-ttu-id="3a23a-107">展開中に登録するのではなく、登録を必要としないアクティベーションをアセンブリに使用することには、次の 2 つの利点があります。</span><span class="sxs-lookup"><span data-stu-id="3a23a-107">Using registration-free activation for your assemblies instead of registering them during deployment offers two advantages:</span></span>  
  
- <span data-ttu-id="3a23a-108">複数のバージョンの DLL がコンピューターにインストールされているとき、どのバージョンをアクティブ化するかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="3a23a-108">You can control which DLL version is activated when more than one version is installed on a computer.</span></span>  
  
- <span data-ttu-id="3a23a-109">エンドユーザーは XCOPY または FTP を使用して、アプリケーションをコンピューターの適切なディレクトリにコピーできます。</span><span class="sxs-lookup"><span data-stu-id="3a23a-109">End users can use XCOPY or FTP to copy your application to an appropriate directory on their computer.</span></span> <span data-ttu-id="3a23a-110">その後、そのディレクトリでアプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="3a23a-110">The application can then be run from that directory.</span></span>  
  
 <span data-ttu-id="3a23a-111">このセクションでは、登録を必要としない COM 相互運用機能に必要な 2 つの種類のマニフェストについて説明します。それらはアプリケーション マニフェストとコンポーネント マニフェストです。</span><span class="sxs-lookup"><span data-stu-id="3a23a-111">This section describes the two types of manifests needed for registration-free COM interop: application and component manifests.</span></span> <span data-ttu-id="3a23a-112">これらのマニフェストは、XML ファイルです。</span><span class="sxs-lookup"><span data-stu-id="3a23a-112">These manifests are XML files.</span></span> <span data-ttu-id="3a23a-113">アプリケーション マニフェストは、アプリケーション開発者によって作成され、アセンブリやアセンブリの依存関係を記述するメタデータを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="3a23a-113">An application manifest, which is created by an application developer, contains metadata that describes assemblies and assembly dependencies.</span></span> <span data-ttu-id="3a23a-114">コンポーネント マニフェストは、コンポーネント開発者によって作成されるものであり、そこには、本来 Windows レジストリに存在する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3a23a-114">A component manifest, created by a component developer, contains information otherwise located in the Windows registry.</span></span>  
  
### <a name="requirements-for-registration-free-com-interop"></a><span data-ttu-id="3a23a-115">登録を必要としない COM 相互運用機能の要件</span><span class="sxs-lookup"><span data-stu-id="3a23a-115">Requirements for registration-free COM interop</span></span>  
  
1. <span data-ttu-id="3a23a-116">登録を必要としない COM 相互運用機能のサポートは、ライブラリ アセンブリの種類に応じて、具体的にはアセンブリがアンマネージド (COM side-by-side) であるかマネージド (.NET ベース) であるかによって、多少異なります。</span><span class="sxs-lookup"><span data-stu-id="3a23a-116">Support for registration-free COM interop varies slightly depending on the type of library assembly; specifically, whether the assembly is unmanaged (COM side-by-side) or managed (.NET-based).</span></span> <span data-ttu-id="3a23a-117">次の表は、それぞれのアセンブリの種類について、オペレーティング システムと .NET Framework のバージョン要件を示しています。</span><span class="sxs-lookup"><span data-stu-id="3a23a-117">The following table shows the operating system and .NET Framework version requirements for each assembly type.</span></span>  
  
    |<span data-ttu-id="3a23a-118">アセンブリの種類</span><span class="sxs-lookup"><span data-stu-id="3a23a-118">Assembly type</span></span>|<span data-ttu-id="3a23a-119">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="3a23a-119">Operating system</span></span>|<span data-ttu-id="3a23a-120">.NET Framework のバージョン</span><span class="sxs-lookup"><span data-stu-id="3a23a-120">.NET Framework version</span></span>|  
    |-------------------|----------------------|----------------------------|  
    |<span data-ttu-id="3a23a-121">COM side-by-side</span><span class="sxs-lookup"><span data-stu-id="3a23a-121">COM side-by-side</span></span>|<span data-ttu-id="3a23a-122">Microsoft Windows XP</span><span class="sxs-lookup"><span data-stu-id="3a23a-122">Microsoft Windows XP</span></span>|<span data-ttu-id="3a23a-123">不要。</span><span class="sxs-lookup"><span data-stu-id="3a23a-123">Not required.</span></span>|  
    |<span data-ttu-id="3a23a-124">.NET ベース</span><span class="sxs-lookup"><span data-stu-id="3a23a-124">.NET-based</span></span>|<span data-ttu-id="3a23a-125">Windows XP SP2</span><span class="sxs-lookup"><span data-stu-id="3a23a-125">Windows XP with SP2</span></span>|<span data-ttu-id="3a23a-126">.NET Framework バージョン 1.1</span><span class="sxs-lookup"><span data-stu-id="3a23a-126">NET Framework version 1.1 or later.</span></span>|  
  
     <span data-ttu-id="3a23a-127">Windows Server 2003 ファミリも、.NET ベースのアセンブリで、登録を必要としない COM 相互運用機能をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3a23a-127">The Windows Server 2003 family also supports registration-free COM interop for .NET-based assemblies.</span></span>  
  
     <span data-ttu-id="3a23a-128">NET ベースのクラスが COM からの登録を必要としないアクティブ化と互換性を持つためには、そのクラスがパラメーターなしのコンストラクターを持ち、パブリックであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="3a23a-128">For a .NET-based class to be compatible with registry-free activation from COM, the class must have a parameterless constructor and must be public.</span></span>  
  
### <a name="configuring-com-components-for-registration-free-activation"></a><span data-ttu-id="3a23a-129">登録を必要としないアクティベーション用の COM コンポーネントの構成</span><span class="sxs-lookup"><span data-stu-id="3a23a-129">Configuring COM components for registration-free activation</span></span>  
  
1. <span data-ttu-id="3a23a-130">COM コンポーネントが登録を必要としないアクティベーションに含まれるようにするには、それを side-by-side アセンブリとして展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a23a-130">For a COM component to participate in registration-free activation, it must be deployed as a side-by-side assembly.</span></span> <span data-ttu-id="3a23a-131">Side-by-side アセンブリはアンマネージ アセンブリです。</span><span class="sxs-lookup"><span data-stu-id="3a23a-131">Side-by-side assemblies are unmanaged assemblies.</span></span>  <span data-ttu-id="3a23a-132">詳しくは、「[Using Side-by-side Assemblies](/windows/desktop/SbsCs/using-side-by-side-assemblies)」(side-by-side アセンブリの使用) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3a23a-132">For more information, see [Using Side-by-side Assemblies](/windows/desktop/SbsCs/using-side-by-side-assemblies).</span></span>  
  
     <span data-ttu-id="3a23a-133">COM の side-by-side アセンブリを使用するには、.NET ベースのアプリケーション開発者が、バインディングとアクティベーションの情報を含むアプリケーション マニフェストを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a23a-133">To use COM side-by-side assemblies, a .NET-based application developer must provide an application manifest, which contains the binding and activation information.</span></span> <span data-ttu-id="3a23a-134">Windows XP オペレーティング システムには、アンマネージの side-by-side アセンブリのサポートが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="3a23a-134">Support for unmanaged side-by-side assemblies is built into the Windows XP operating system.</span></span> <span data-ttu-id="3a23a-135">オペレーティング システムでサポートされている COM ランタイムは、アクティブ化されるコンポーネントがレジストリに存在しない場合、アプリケーション マニフェストをスキャンしてアクティベーション情報を見つけます。</span><span class="sxs-lookup"><span data-stu-id="3a23a-135">The COM runtime, supported by the operating system, scans an application manifest for activation information when the component being activated is not in the registry.</span></span>  
  
     <span data-ttu-id="3a23a-136">登録を必要としないアクティベーションは、Windows XP にインストールされている COM コンポーネントでは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="3a23a-136">Registration-free activation is optional for COM components installed on Windows XP.</span></span> <span data-ttu-id="3a23a-137">アプリケーションに side-by-side アセンブリを追加する方法の詳細な手順については、「[Using Side-by-side Assemblies](/windows/desktop/SbsCs/using-side-by-side-assemblies)」(side-by-side アセンブリの使用) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3a23a-137">For detailed instructions on adding a side-by-side assembly to an application, see [Using Side-by-side Assemblies](/windows/desktop/SbsCs/using-side-by-side-assemblies).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3a23a-138">Side-by-side 実行は、ランタイムの複数のバージョンと、特定のバージョンのランタイムを使用するアプリケーションおよびコンポーネントの複数のバージョンを、同一のコンピューター上で同時に実行できるようにするための、.NET Framework の機能です。</span><span class="sxs-lookup"><span data-stu-id="3a23a-138">Side-by-side execution is a .NET Framework feature that enables multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, to run on the same computer at the same time.</span></span> <span data-ttu-id="3a23a-139">Side-by-side 実行と side-by-side アセンブリは、side-by-side 機能を提供するための別個のメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="3a23a-139">Side-by-side execution and side-by-side assemblies are different mechanisms for providing side-by-side functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a23a-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a23a-140">See also</span></span>

- [<span data-ttu-id="3a23a-141">方法: 登録を必要としないアクティベーション用の .NET Framework ベースの COM コンポーネントを構成する</span><span class="sxs-lookup"><span data-stu-id="3a23a-141">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)
