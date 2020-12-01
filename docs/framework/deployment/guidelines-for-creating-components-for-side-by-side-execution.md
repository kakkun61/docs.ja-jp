---
title: side-by-side 実行用のコンポーネントを作成するためのガイドライン
description: side-by-side 実行用のコンポーネントを作成するためのガイドラインを確認します。 たとえば、型 ID を特定のファイル バージョンにバインドしたり、バージョンを認識するストレージを使用したりします。
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, multiple application versions
- side-by-side execution, multiple component versions
ms.assetid: 5c540161-6e40-42e9-be92-6175aee2c46a
ms.openlocfilehash: 3ac7c514a69ae05b00e7a486aadcbf41e5d1cbd6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262516"
---
# <a name="guidelines-for-creating-components-for-side-by-side-execution"></a><span data-ttu-id="09843-104">side-by-side 実行用のコンポーネントを作成するためのガイドライン</span><span class="sxs-lookup"><span data-stu-id="09843-104">Guidelines for Creating Components for Side-by-Side Execution</span></span>

<span data-ttu-id="09843-105">side-by-side 実行用にデザインしたマネージド アプリケーションまたはマネージド コンポーネントを作成するときのガイドラインを次に示します。</span><span class="sxs-lookup"><span data-stu-id="09843-105">Follow these general guidelines to create managed applications or components designed for side-by-side execution:</span></span>  
  
- <span data-ttu-id="09843-106">型 ID をファイルの特定のバージョンにバインドします。</span><span class="sxs-lookup"><span data-stu-id="09843-106">Bind type identity to a particular version of a file.</span></span>  
  
     <span data-ttu-id="09843-107">共通言語ランタイムは、厳密な名前付きのアセンブリを使用して、型 ID を特定のファイル バージョンにバインドします。</span><span class="sxs-lookup"><span data-stu-id="09843-107">The common language runtime binds type identity to a particular file version by using strong-named assemblies.</span></span> <span data-ttu-id="09843-108">side-by-side 実行用のアプリケーションまたはコンポーネントを作成するには、すべてのアセンブリに厳密な名前を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="09843-108">To create an application or component for side-by-side execution, you must give all assemblies a strong name.</span></span> <span data-ttu-id="09843-109">これによって精密な型 ID が作成され、どのような型解決でも正しいファイルに接続されます。</span><span class="sxs-lookup"><span data-stu-id="09843-109">This creates precise type identity and ensures that any type resolution is directed to the correct file.</span></span> <span data-ttu-id="09843-110">厳密な名前付きのアセンブリには、バージョン、カルチャ、および発行元情報が含まれていて、ランタイムはこれを使用して、バインド要求を実行するために正しいファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="09843-110">A strong-named assembly contains version, culture, and publisher information that the runtime uses to locate the correct file to fulfill a binding request.</span></span>  
  
- <span data-ttu-id="09843-111">バージョンを認識するストレージを使用します。</span><span class="sxs-lookup"><span data-stu-id="09843-111">Use version-aware storage.</span></span>  
  
     <span data-ttu-id="09843-112">ランタイムは、グローバル アセンブリ キャッシュを使用して、バージョンを認識するストレージを提供します。</span><span class="sxs-lookup"><span data-stu-id="09843-112">The runtime uses the global assembly cache to provide version-aware storage.</span></span> <span data-ttu-id="09843-113">グローバル アセンブリ キャッシュはバージョンを認識するディレクトリ構造で、.NET Framework を使用するどのコンピューターにもインストールされています。</span><span class="sxs-lookup"><span data-stu-id="09843-113">The global assembly cache is a version-aware directory structure installed on every computer that uses the .NET Framework.</span></span> <span data-ttu-id="09843-114">グローバル アセンブリ キャッシュにインストールされているアセンブリは、そのアセンブリの新しいバージョンがインストールされても、上書きされません。</span><span class="sxs-lookup"><span data-stu-id="09843-114">Assemblies installed in the global assembly cache are not overwritten when a new version of that assembly is installed.</span></span>  
  
- <span data-ttu-id="09843-115">分離して実行されるアプリケーションまたはコンポーネントを作成します。</span><span class="sxs-lookup"><span data-stu-id="09843-115">Create an application or component that runs in isolation.</span></span>  
  
     <span data-ttu-id="09843-116">分離して実行されるアプリケーションまたはコンポーネントは、それらのアプリケーションまたはコンポーネントの 2 つのインスタンスが同時に実行されるときの競合を避けるために、リソースを管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="09843-116">An application or component that runs in isolation must manage resources to avoid conflicts when two instances of the application or component are running simultaneously.</span></span> <span data-ttu-id="09843-117">また、アプリケーションまたはコンポーネントは、バージョン固有のファイル構造を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="09843-117">The application or component must also use a version-specific file structure.</span></span>  
  
## <a name="application-and-component-isolation"></a><span data-ttu-id="09843-118">アプリケーションとコンポーネントの分離</span><span class="sxs-lookup"><span data-stu-id="09843-118">Application and Component Isolation</span></span>  

 <span data-ttu-id="09843-119">side-by-side 実行用のアプリケーションまたはコンポーネントのデザインを成功させる鍵の 1 つとして、分離が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="09843-119">One key to successfully designing an application or component for side-by-side execution is isolation.</span></span> <span data-ttu-id="09843-120">アプリケーションまたはコンポーネントは、特にファイル I/O をはじめとするすべてのリソースを、分離された方法で管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="09843-120">The application or component must manage all resources, particularly file I/O, in an isolated manner.</span></span> <span data-ttu-id="09843-121">アプリケーションまたはコンポーネントを、確実に分離して実行するには、次のガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="09843-121">Follow these guidelines to make sure your application or component runs in isolation:</span></span>  
  
- <span data-ttu-id="09843-122">バージョン固有の方法でレジストリに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="09843-122">Write to the registry in a version-specific way.</span></span> <span data-ttu-id="09843-123">バージョンを示したハイブまたはキーに値を格納し、コンポーネントのバージョンをまたいで情報や状態を共有しないようにします。</span><span class="sxs-lookup"><span data-stu-id="09843-123">Store values in hives or keys that indicate the version, and do not share information or state across versions of a component.</span></span> <span data-ttu-id="09843-124">これにより、同時に実行されている 2 つのアプリケーションまたはコンポーネントが情報を上書きしてしまうことを防げます。</span><span class="sxs-lookup"><span data-stu-id="09843-124">This prevents two applications or components running at the same time from overwriting information.</span></span>  
  
- <span data-ttu-id="09843-125">競合状態が発生しないように、名前付きカーネル オブジェクトをバージョン固有にします。</span><span class="sxs-lookup"><span data-stu-id="09843-125">Make named kernel objects version-specific so that a race condition does not occur.</span></span> <span data-ttu-id="09843-126">たとえば、同じアプリケーションの 2 つのバージョンから生成された 2 つのセマフォが相互に待機すると、競合状態が発生します。</span><span class="sxs-lookup"><span data-stu-id="09843-126">For example, a race condition occurs when two semaphores from two versions of the same application wait on each other.</span></span>  
  
- <span data-ttu-id="09843-127">ファイル名とディレクトリ名でバージョンを認識できるようにします。</span><span class="sxs-lookup"><span data-stu-id="09843-127">Make file and directory names version-aware.</span></span> <span data-ttu-id="09843-128">これは、ファイル構造がバージョン情報に依存することを意味します。</span><span class="sxs-lookup"><span data-stu-id="09843-128">This means that file structures should rely on version information.</span></span>  
  
- <span data-ttu-id="09843-129">ユーザー アカウントとグループをバージョン固有の方法で作成します。</span><span class="sxs-lookup"><span data-stu-id="09843-129">Create user accounts and groups in a version-specific manner.</span></span> <span data-ttu-id="09843-130">アプリケーションによって作成されるユーザー アカウントとグループを、バージョンで識別できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="09843-130">User accounts and groups created by an application should be identified by version.</span></span> <span data-ttu-id="09843-131">アプリケーションのバージョン間で、ユーザー アカウントとグループを共有しないでください。</span><span class="sxs-lookup"><span data-stu-id="09843-131">Do not share user accounts and groups between versions of an application.</span></span>  
  
## <a name="installing-and-uninstalling-versions"></a><span data-ttu-id="09843-132">バージョンのインストールとアンインストール</span><span class="sxs-lookup"><span data-stu-id="09843-132">Installing and Uninstalling Versions</span></span>  

 <span data-ttu-id="09843-133">side-by-side 用のアプリケーションをデザインするときは、バージョンのインストールとアンインストールに関する次のガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="09843-133">When designing an application for side-by-side execution, follow these guidelines concerning installing and uninstalling versions:</span></span>  
  
- <span data-ttu-id="09843-134">.NET Framework の異なるバージョンで実行されている他のアプリケーションによって必要になる可能性のある情報をレジストリから削除しないでください。</span><span class="sxs-lookup"><span data-stu-id="09843-134">Do not delete information from the registry that may be needed by other applications running under a different version of the .NET Framework.</span></span>  
  
- <span data-ttu-id="09843-135">.NET Framework の異なるバージョンで実行されている他のアプリケーションによって必要になる可能性のある情報をレジストリ内で置き換えないでください。</span><span class="sxs-lookup"><span data-stu-id="09843-135">Do not replace information in the registry that may be needed by other applications running under a different version of the .NET Framework.</span></span>  
  
- <span data-ttu-id="09843-136">.NET Framework の異なるバージョンで実行されている他のアプリケーションによって必要になる可能性のある COM コンポーネントの登録を解除しないでください。</span><span class="sxs-lookup"><span data-stu-id="09843-136">Do not unregister COM components that may be needed by other applications running under a different version of the .NET Framework.</span></span>  
  
- <span data-ttu-id="09843-137">既に登録されている COM サーバー用の **InprocServer32** または他のレジストリ エントリを変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="09843-137">Do not change **InprocServer32** or other registry entries for a COM server that was already registered.</span></span>  
  
- <span data-ttu-id="09843-138">.NET Framework の異なるバージョンで実行されている他のアプリケーションによって必要になる可能性のあるユーザー アカウントまたはグループを削除しないでください。</span><span class="sxs-lookup"><span data-stu-id="09843-138">Do not delete user accounts or groups that may be needed by other applications running under a different version of the .NET Framework.</span></span>  
  
- <span data-ttu-id="09843-139">バージョン管理されていないパスを含むレジストリには何も追加しないでください。</span><span class="sxs-lookup"><span data-stu-id="09843-139">Do not add anything to the registry that contains an unversioned path.</span></span>  
  
## <a name="file-version-number-and-assembly-version-number"></a><span data-ttu-id="09843-140">ファイルのバージョン番号とアセンブリのバージョン番号</span><span class="sxs-lookup"><span data-stu-id="09843-140">File Version Number and Assembly Version Number</span></span>  

 <span data-ttu-id="09843-141">ファイルのバージョンは Win32 バージョン リソースであり、ランタイムでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="09843-141">File version is a Win32 version resource that is not used by the runtime.</span></span> <span data-ttu-id="09843-142">一般に、インプレース更新の場合であっても、ファイルのバージョンを更新してください。</span><span class="sxs-lookup"><span data-stu-id="09843-142">In general, you update the file version even for an in-place update.</span></span> <span data-ttu-id="09843-143">まったく同じ 2 つのファイルが異なるファイル バージョン情報を持つことや、2 つの異なるファイルが同じファイル バージョン情報を持つことがあります。</span><span class="sxs-lookup"><span data-stu-id="09843-143">Two identical files can have different file version information, and two different files can have the same file version information.</span></span>  
  
 <span data-ttu-id="09843-144">アセンブリのバージョンは、アセンブリ バインディングのためにランタイムによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="09843-144">The assembly version is used by the runtime for assembly binding.</span></span> <span data-ttu-id="09843-145">2 つの同一のアセンブリであっても、バージョン番号が異なると、ランタイムによって 2 つの異なるアセンブリとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="09843-145">Two identical assemblies with different version numbers are treated as two different assemblies by the runtime.</span></span>  
  
 <span data-ttu-id="09843-146">[グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) では、ファイルのバージョン番号が新しい場合にのみ、アセンブリを置換できます。</span><span class="sxs-lookup"><span data-stu-id="09843-146">The [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) allows you to replace an assembly when only the file version number is newer.</span></span> <span data-ttu-id="09843-147">一般的に、インストーラーは、アセンブリのバージョン番号が大きくない限り、アセンブリを上書きでインストールしません。</span><span class="sxs-lookup"><span data-stu-id="09843-147">The installer generally does not install over an assembly unless the assembly version number is greater.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09843-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="09843-148">See also</span></span>

- [<span data-ttu-id="09843-149">side-by-side 実行</span><span class="sxs-lookup"><span data-stu-id="09843-149">Side-by-Side Execution</span></span>](side-by-side-execution.md)
- [<span data-ttu-id="09843-150">方法: 自動バインディング リダイレクトを有効/無効にする</span><span class="sxs-lookup"><span data-stu-id="09843-150">How to: Enable and Disable Automatic Binding Redirection</span></span>](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
