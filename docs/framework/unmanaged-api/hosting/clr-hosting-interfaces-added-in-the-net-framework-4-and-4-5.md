---
title: .NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: 6ee3b8cdf348a5eade3903e2d26b4f9b93886305
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706815"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="a5d85-102">.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5d85-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>

<span data-ttu-id="a5d85-103">ここでは、アンマネージホストが .NET Framework 4、.NET Framework 4.5、およびそれ以降のバージョンの共通言語ランタイム (CLR) をアプリケーションに統合するために使用できるインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a5d85-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework 4, .NET Framework 4.5, and later versions into their applications.</span></span> <span data-ttu-id="a5d85-104">これらのインターフェイスは、ホストがランタイムを構成してプロセスに読み込むためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a5d85-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="a5d85-105">.NET Framework 4 以降では、すべてのホストインターフェイスに次の特性があります。</span><span class="sxs-lookup"><span data-stu-id="a5d85-105">Starting with the .NET Framework 4, all hosting interfaces have the following characteristics:</span></span>  
  
- <span data-ttu-id="a5d85-106">これらは、有効期間管理 ( `AddRef` および `Release` )、カプセル化 (暗黙的なコンテキスト)、および `QueryInterface` COM からの使用を行います。</span><span class="sxs-lookup"><span data-stu-id="a5d85-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
- <span data-ttu-id="a5d85-107">これらの型は `BSTR` 、、、などの COM 型を使用しません `SAFEARRAY` `VARIANT` 。</span><span class="sxs-lookup"><span data-stu-id="a5d85-107">They do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
- <span data-ttu-id="a5d85-108">[CoCreateInstance 関数](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)を使用するアパートメントモデル、集計、またはレジストリのアクティブ化はありません。</span><span class="sxs-lookup"><span data-stu-id="a5d85-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a5d85-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a5d85-109">In This Section</span></span>  

 [<span data-ttu-id="a5d85-110">ICLRAppDomainResourceMonitor インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5d85-110">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="a5d85-111">アプリケーションドメインのメモリおよび CPU 使用率を検査するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a5d85-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="a5d85-112">ICLRDomainManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5d85-112">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)  
 <span data-ttu-id="a5d85-113">既定のアプリケーションドメインを初期化し、初期化プロパティを指定するために使用されるアプリケーションドメインマネージャーをホストが指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a5d85-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="a5d85-114">ICLRGCManager2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5d85-114">ICLRGCManager2 Interface</span></span>](iclrgcmanager2-interface.md)  
 <span data-ttu-id="a5d85-115">[SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md)メソッドを提供します。これにより、ホストはガベージコレクションセグメントのサイズとガベージコレクションシステムのジェネレーション0の最大サイズをより大きい値に設定でき `DWORD` ます。</span><span class="sxs-lookup"><span data-stu-id="a5d85-115">Provides the [SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="a5d85-116">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5d85-116">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)  
 <span data-ttu-id="a5d85-117">特定のバージョンの CLR を返し、インストールされているすべての CLRs の一覧を取得し、すべてのインプロセスランタイムを一覧表示し、アクティベーションインターフェイスを返し、アセンブリをコンパイルするために使用される CLR バージョンを検出するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a5d85-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="a5d85-118">ICLRMetaHostPolicy インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5d85-118">ICLRMetaHostPolicy Interface</span></span>](iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="a5d85-119">ポリシー条件、マネージアセンブリ、バージョン、および構成ファイルに基づいて CLR インターフェイスを提供する [Getrequestedruntime](iclrmetahostpolicy-getrequestedruntime-method.md) メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a5d85-119">Provides the [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="a5d85-120">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5d85-120">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)  
 <span data-ttu-id="a5d85-121">バージョン、ディレクトリ、読み込みステータスなど、特定のランタイムに関する情報を返すメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a5d85-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="a5d85-122">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5d85-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)  
 <span data-ttu-id="a5d85-123">厳密な名前でアセンブリに署名するための基本的なグローバル静的関数を提供します。</span><span class="sxs-lookup"><span data-stu-id="a5d85-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="a5d85-124">すべての [ICLRStrongName](iclrstrongname-interface.md) メソッドは、標準 COM hresult を返します。</span><span class="sxs-lookup"><span data-stu-id="a5d85-124">All the [ICLRStrongName](iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="a5d85-125">ICLRStrongName2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5d85-125">ICLRStrongName2 Interface</span></span>](iclrstrongname2-interface.md)  
 <span data-ttu-id="a5d85-126">セキュリティで保護されたハッシュアルゴリズム (SHA-256、SHA-384、および SHA-512) の SHA-1 グループを使用して、厳密な名前を作成する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="a5d85-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="a5d85-127">ICLRTask2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5d85-127">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)  
 <span data-ttu-id="a5d85-128">には、 [ICLRTask インターフェイス](iclrtask-interface.md)のすべての機能が用意されています。また、には、現在のスレッドでスレッドの中止を遅延させることができるメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="a5d85-128">Provides all the functionality of the [ICLRTask Interface](iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a5d85-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5d85-129">Related Sections</span></span>  

 [<span data-ttu-id="a5d85-130">非推奨の CLR のホスト インターフェイスおよびコクラス</span><span class="sxs-lookup"><span data-stu-id="a5d85-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="a5d85-131">.NET Framework バージョン1.0 および1.1 で提供されるホストインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a5d85-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="a5d85-132">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5d85-132">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="a5d85-133">.NET Framework バージョン2.0、3.0、および3.5 で提供されるホストインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a5d85-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="a5d85-134">ホスティング</span><span class="sxs-lookup"><span data-stu-id="a5d85-134">Hosting</span></span>](index.md)  
 <span data-ttu-id="a5d85-135">.NET Framework でのホスティングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a5d85-135">Introduces hosting in the .NET Framework.</span></span>
