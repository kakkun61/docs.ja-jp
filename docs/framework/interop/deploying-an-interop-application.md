---
title: 相互運用アプリケーションの配置
description: 相互運用アプリケーションを配置します。これには、通常、.NET クライアント アセンブリ、個別の COM タイプ ライブラリの相互運用機能アセンブリ、および登録済み COM コンポーネントが含まれています。
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], interop
- strong-named assemblies, interop applications
- unsigned assemblies
- private assemblies
- exposing COM components to .NET Framework
- interoperation with unmanaged code, deploying applications
- shared assemblies
- COM interop, deploying applications
- interoperation with unmanaged code, exposing COM components
- signed assemblies
- COM interop, exposing COM components
ms.assetid: ea8a403e-ae03-4faa-9d9b-02179ec72992
ms.openlocfilehash: 2a8c94ac482bc16cb373fc694c4610ad42e8f631
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267092"
---
# <a name="deploying-an-interop-application"></a><span data-ttu-id="faa5d-103">相互運用アプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="faa5d-103">Deploying an Interop Application</span></span>

<span data-ttu-id="faa5d-104">通常、相互運用アプリケーションには、.NET クライアント アセンブリ、個別の COM タイプ ライブラリを表す 1 つ以上の相互運用機能アセンブリ、および 1 つ以上の登録済み COM コンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="faa5d-104">An interop application typically includes a .NET client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span> <span data-ttu-id="faa5d-105">Visual Studio および Windows SDK には、タイプ ライブラリをインポートして相互運用アセンブリに変換するためのツールが用意されています。詳しくは「[タイプ ライブラリのアセンブリとしてのインポート](importing-a-type-library-as-an-assembly.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="faa5d-105">Visual Studio and the Windows SDK provide tools to import and convert a type library to an interop assembly, as discussed in [Importing a Type Library as an Assembly](importing-a-type-library-as-an-assembly.md).</span></span> <span data-ttu-id="faa5d-106">相互運用アプリケーションを配置する方法には、次の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="faa5d-106">There are two ways to deploy an interop application:</span></span>  
  
- <span data-ttu-id="faa5d-107">埋め込まれた相互運用機能型を使用する:.NET Framework 4 以降では、相互運用機能アセンブリから実行可能ファイルに型情報を埋め込むようにコンパイラに指示できます。</span><span class="sxs-lookup"><span data-stu-id="faa5d-107">By using embedded interop types: Beginning with the .NET Framework 4, you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="faa5d-108">コンパイラは、アプリケーションで使用する型情報のみを埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="faa5d-108">The compiler embeds only the type information that your application uses.</span></span> <span data-ttu-id="faa5d-109">アプリケーションで相互運用機能アセンブリを配置する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="faa5d-109">You do not have to deploy the interop assembly with your application.</span></span> <span data-ttu-id="faa5d-110">この手法を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="faa5d-110">This is the recommended technique.</span></span>  
  
- <span data-ttu-id="faa5d-111">相互運用機能アセンブリの配置:相互運用機能アセンブリへの標準の参照を作成できます。</span><span class="sxs-lookup"><span data-stu-id="faa5d-111">By deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="faa5d-112">この場合、アプリケーションで相互運用機能アセンブリを展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="faa5d-112">In this case, the interop assembly must be deployed with your application.</span></span> <span data-ttu-id="faa5d-113">この手法を採用し、プライベートの COM コンポーネントを使用しない場合は、常に、マネージド コードに組み込む予定の COM コンポーネントの作成者によって発行されたプライマリ相互運用機能アセンブリ (PIA) を参照します。</span><span class="sxs-lookup"><span data-stu-id="faa5d-113">If you employ this technique, and you are not using a private COM component, always reference the primary interop assembly (PIA) published by the author of the COM component you intend to incorporate in your managed code.</span></span> <span data-ttu-id="faa5d-114">プライマリ相互運用機能アセンブリの生成と使用の詳細については、「[プライマリ相互運用機能](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="faa5d-114">For more information about producing and using primary interop assemblies, see [Primary Interop Assemblies](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).</span></span>  
  
 <span data-ttu-id="faa5d-115">埋め込まれた相互運用機能型を使用すると、配置を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="faa5d-115">If you use embedded interop types, deployment is simple and straightforward.</span></span> <span data-ttu-id="faa5d-116">特別な操作を行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="faa5d-116">There is nothing special you need to do.</span></span> <span data-ttu-id="faa5d-117">ここからは、アプリケーションで相互運用機能アセンブリを配置するシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="faa5d-117">The rest of this article describes the scenarios for deploying interop assemblies with your application.</span></span>  
  
## <a name="deploying-interop-assemblies"></a><span data-ttu-id="faa5d-118">相互運用機能アセンブリの配置</span><span class="sxs-lookup"><span data-stu-id="faa5d-118">Deploying Interop Assemblies</span></span>  

 <span data-ttu-id="faa5d-119">アセンブリには厳密な名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="faa5d-119">Assemblies can have strong names.</span></span> <span data-ttu-id="faa5d-120">厳密な名前のアセンブリには、一意の識別子を提供する、発行者の公開キーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="faa5d-120">A strong-named assembly includes the publisher's public key, which provides a unique identity.</span></span> <span data-ttu-id="faa5d-121">発行者は、 **/keyfile** オプションを使用して、[タイプ ライブラリ インポーター (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) で生成されたアセンブリに署名できます。</span><span class="sxs-lookup"><span data-stu-id="faa5d-121">Assemblies that are produced by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) can be signed by the publisher by using the **/keyfile** option.</span></span> <span data-ttu-id="faa5d-122">署名付きアセンブリは、グローバル アセンブリ キャッシュにインストールできます。</span><span class="sxs-lookup"><span data-stu-id="faa5d-122">You can install signed assemblies into the global assembly cache.</span></span> <span data-ttu-id="faa5d-123">署名のないアセンブリは、プライベート アセンブリとしてユーザーのコンピューターにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="faa5d-123">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>  
  
### <a name="private-assemblies"></a><span data-ttu-id="faa5d-124">プライベート アセンブリ</span><span class="sxs-lookup"><span data-stu-id="faa5d-124">Private Assemblies</span></span>  

 <span data-ttu-id="faa5d-125">プライベートに使用するアセンブリをインストールするには、アプリケーションの実行可能ファイルと、インポートされた COM 型を含む相互運用機能アセンブリの両方を同じディレクトリ構造にインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="faa5d-125">To install an assembly to be used privately, both the application executable and the interop assembly that contains imported COM types must be installed in the same directory structure.</span></span> <span data-ttu-id="faa5d-126">別個のアプリケーション ディレクトリに配置された Client1.exe と Client2.exe によってプライベートに使用される、署名のない相互運用機能アセンブリを次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="faa5d-126">The following illustration shows an unsigned interop assembly to be used privately by Client1.exe and Client2.exe, which reside in separate application directories.</span></span> <span data-ttu-id="faa5d-127">この例の LOANLib.dll という相互運用機能アセンブリは、2 回インストールされています。</span><span class="sxs-lookup"><span data-stu-id="faa5d-127">The interop assembly, which is called LOANLib.dll in this example, is installed twice.</span></span>  
  
 <span data-ttu-id="faa5d-128">![ディレクトリ構造と Windows レジストリ](./media/deploying-an-interop-application/com-private-deployment.gif "プライベートに配置する場合のディレクトリ構造とレジストリ エントリ")</span><span class="sxs-lookup"><span data-stu-id="faa5d-128">![Directory structure and Windows registry](./media/deploying-an-interop-application/com-private-deployment.gif "Directory structure and registry entries for a private deployment")</span></span>  
  
 <span data-ttu-id="faa5d-129">アプリケーションに関連付けられているすべての COM コンポーネントを、Windows レジストリにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="faa5d-129">All COM components associated with the application must be installed in the Windows registry.</span></span> <span data-ttu-id="faa5d-130">この図の Client1.exe と Client2.exe が別のコンピューターにインストールされている場合は、両方のコンピューターで COM コンポーネントを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="faa5d-130">If Client1.exe and Client2.exe in the illustration are installed on different computers, you must register the COM components on both computers.</span></span>  
  
### <a name="shared-assemblies"></a><span data-ttu-id="faa5d-131">共有アセンブリ</span><span class="sxs-lookup"><span data-stu-id="faa5d-131">Shared Assemblies</span></span>  

 <span data-ttu-id="faa5d-132">複数のアプリケーションによって共有されるアセンブリは、グローバル アセンブリ キャッシュと呼ばれる集中化されたリポジトリにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="faa5d-132">Assemblies that are shared by multiple applications should be installed in a centralized repository called the global assembly cache.</span></span> <span data-ttu-id="faa5d-133">.NET クライアントは、署名され、グローバル アセンブリ キャッシュにインストールされた、相互運用機能アセンブリの同じコピーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="faa5d-133">.NET clients can access the same copy of the interop assembly, which is signed and installed in the global assembly cache.</span></span> <span data-ttu-id="faa5d-134">プライマリ相互運用機能アセンブリの生成と使用の詳細については、「[プライマリ相互運用機能](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="faa5d-134">For more information about producing and using primary interop assemblies, see [Primary Interop Assemblies](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faa5d-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="faa5d-135">See also</span></span>

- [<span data-ttu-id="faa5d-136">.NET Framework への COM コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="faa5d-136">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="faa5d-137">タイプ ライブラリのアセンブリとしてのインポート</span><span class="sxs-lookup"><span data-stu-id="faa5d-137">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- <span data-ttu-id="faa5d-138">[マネージド コードでの COM 型の使用](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="faa5d-138">[Using COM Types in Managed Code](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="faa5d-139">相互運用プロジェクトのコンパイル</span><span class="sxs-lookup"><span data-stu-id="faa5d-139">Compiling an Interop Project</span></span>](compiling-an-interop-project.md)
