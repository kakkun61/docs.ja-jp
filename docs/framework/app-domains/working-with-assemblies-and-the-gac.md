---
title: アセンブリとグローバル アセンブリ キャッシュの使用
description: .NET のアセンブリとグローバル アセンブリ キャッシュ (GAC) を使用します。 アセンブリを GAC にインストールする理由について確認します。
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
ms.openlocfilehash: e27fdd7def2d234e1e8eb7557e869bf478d68210
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279312"
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a><span data-ttu-id="7d182-104">アセンブリとグローバル アセンブリ キャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="7d182-104">Working with Assemblies and the Global Assembly Cache</span></span>

<span data-ttu-id="7d182-105">あるアセンブリを複数のアプリケーションで共有する場合は、そのアセンブリをグローバル アセンブリ キャッシュ内にインストールできます。</span><span class="sxs-lookup"><span data-stu-id="7d182-105">If you intend to share an assembly among several applications, you can install it into the global assembly cache.</span></span> <span data-ttu-id="7d182-106">共通言語ランタイムをインストールしている各コンピューターは、このコードをコンピューター全体で使用できます。</span><span class="sxs-lookup"><span data-stu-id="7d182-106">Each computer where the common language runtime is installed has this machine-wide code cache.</span></span> <span data-ttu-id="7d182-107">グローバル アセンブリ キャッシュは、そのコンピューター上の複数のアプリケーションで共有するように指定されたアセンブリを格納します。</span><span class="sxs-lookup"><span data-stu-id="7d182-107">The global assembly cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span> <span data-ttu-id="7d182-108">グローバル アセンブリ キャッシュ内にインストールされるアセンブリは、厳密な名前を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d182-108">An assembly must have a strong name to be installed in the global assembly cache.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d182-109">グローバル アセンブリ キャッシュ内に配置されるアセンブリは、アセンブリ名とファイル名の拡張子を除く部分が一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d182-109">Assemblies placed in the global assembly cache must have the same assembly name and file name (not including the file name extension).</span></span> <span data-ttu-id="7d182-110">たとえば、アセンブリ名が myAssembly のアセンブリの場合、ファイル名は myAssembly.exe または myAssembly.dll である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d182-110">For example, an assembly with the assembly name of myAssembly must have a file name of either myAssembly.exe or myAssembly.dll.</span></span>  
  
<span data-ttu-id="7d182-111">アセンブリの共有が必要な場合にだけ、アセンブリをグローバル アセンブリ キャッシュにインストールします。</span><span class="sxs-lookup"><span data-stu-id="7d182-111">You should share assemblies by installing them into the global assembly cache only when necessary.</span></span> <span data-ttu-id="7d182-112">一般的には、明らかにアセンブリを共有する必要がある場合を除いて、アセンブリの依存関係はプライベートにし、アセンブリはアプリケーション ディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="7d182-112">As a general guideline, keep assembly dependencies private and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="7d182-113">また、COM 相互運用 (機能) またはアンマネージ コードからアセンブリにアクセスできるようにするために、アセンブリをグローバル アセンブリ キャッシュにインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7d182-113">In addition, you do not have to install assemblies into the global assembly cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
<span data-ttu-id="7d182-114">アセンブリをグローバル アセンブリ キャッシュにインストールする理由は、いくつか考えられます。</span><span class="sxs-lookup"><span data-stu-id="7d182-114">There are several reasons why you might want to install an assembly into the global assembly cache:</span></span>  
  
- <span data-ttu-id="7d182-115">共有の場所。</span><span class="sxs-lookup"><span data-stu-id="7d182-115">Shared location.</span></span>  
  
     <span data-ttu-id="7d182-116">複数のアプリケーションで使用するアセンブリは、グローバル アセンブリ キャッシュに配置できます。</span><span class="sxs-lookup"><span data-stu-id="7d182-116">Assemblies that should be used by applications can be put in the global assembly cache.</span></span> <span data-ttu-id="7d182-117">たとえば、すべてのアプリケーションがグローバル アセンブリ キャッシュ内の 1 つのアセンブリを使用する場合は、アセンブリへの参照をリダイレクトするバージョン ポリシー ステートメントを Machine.config ファイルに追加できます。</span><span class="sxs-lookup"><span data-stu-id="7d182-117">For example, if all applications should use an assembly located in the global assembly cache, a version policy statement can be added to the Machine.config file that redirects references to the assembly.</span></span>  
  
- <span data-ttu-id="7d182-118">ファイル セキュリティ。</span><span class="sxs-lookup"><span data-stu-id="7d182-118">File security.</span></span>  
  
     <span data-ttu-id="7d182-119">通常、管理者は、書き込みおよび実行アクセスを制御するアクセス制御リスト (ACL: Access Control List) を使用して systemroot ディレクトリを保護します。</span><span class="sxs-lookup"><span data-stu-id="7d182-119">Administrators often protect the systemroot directory using an Access Control List (ACL) to control write and execute access.</span></span> <span data-ttu-id="7d182-120">グローバル アセンブリ キャッシュは、systemroot ディレクトリにインストールされるため、このディレクトリの ACL を継承します。</span><span class="sxs-lookup"><span data-stu-id="7d182-120">Because the global assembly cache is installed in the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="7d182-121">グローバル アセンブリ キャッシュからファイルを削除する場合は、管理者権限を持つユーザーに対してだけ許可することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7d182-121">It is recommended that only users with Administrator privileges be allowed to delete files from the global assembly cache.</span></span>  
  
- <span data-ttu-id="7d182-122">side-by-side でのバージョン管理。</span><span class="sxs-lookup"><span data-stu-id="7d182-122">Side-by-side versioning.</span></span>  
  
     <span data-ttu-id="7d182-123">名前は同じでもバージョン情報が異なるアセンブリの複数のコピーを、グローバル アセンブリ キャッシュ内で管理できます。</span><span class="sxs-lookup"><span data-stu-id="7d182-123">Multiple copies of assemblies with the same name but different version information can be maintained in the global assembly cache.</span></span>  
  
- <span data-ttu-id="7d182-124">追加の検索場所。</span><span class="sxs-lookup"><span data-stu-id="7d182-124">Additional search location.</span></span>  
  
     <span data-ttu-id="7d182-125">共通言語ランタイムは、構成ファイル内のコードベース情報をプローブまたは使用する前に、グローバル アセンブリ キャッシュ内にアセンブリ要求と一致するアセンブリがあるかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="7d182-125">The common language runtime checks the global assembly cache for an assembly that matches the assembly request before probing or using the codebase information in a configuration file.</span></span>  
  
 <span data-ttu-id="7d182-126">アセンブリのグローバル アセンブリ キャッシュへのインストールを明示的に避けたい場合もあります。</span><span class="sxs-lookup"><span data-stu-id="7d182-126">Note that there are scenarios where you explicitly do not want to install an assembly into the global assembly cache.</span></span> <span data-ttu-id="7d182-127">アプリケーションを構成するアセンブリの 1 つをグローバル アセンブリ キャッシュに配置した場合は、アプリケーション ディレクトリをコピーする XCOPY を使用してアプリケーションをレプリケートしたりインストールしたりすることはできなくなります。</span><span class="sxs-lookup"><span data-stu-id="7d182-127">If you place one of the assemblies that make up an application into the global assembly cache, you can no longer replicate or install the application by using XCOPY to copy the application directory.</span></span> <span data-ttu-id="7d182-128">この場合は、グローバル アセンブリ キャッシュ内のアセンブリも移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d182-128">In this case, you must also move the assembly into the global assembly cache.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7d182-129">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7d182-129">In This Section</span></span>  

[<span data-ttu-id="7d182-130">方法: アセンブリをグローバル アセンブリ キャッシュにインストールする</span><span class="sxs-lookup"><span data-stu-id="7d182-130">How to: Install an Assembly into the Global Assembly Cache</span></span>](install-assembly-into-gac.md)  
<span data-ttu-id="7d182-131">アセンブリをグローバル アセンブリ キャッシュにインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7d182-131">Describes the ways to install an assembly into the global assembly cache.</span></span>  
  
[<span data-ttu-id="7d182-132">方法: グローバル アセンブリ キャッシュの内容を表示する</span><span class="sxs-lookup"><span data-stu-id="7d182-132">How to: View the Contents of the Global Assembly Cache</span></span>](how-to-view-the-contents-of-the-gac.md)  
<span data-ttu-id="7d182-133">[グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) を使用して、グローバル アセンブリ キャッシュの内容を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7d182-133">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
[<span data-ttu-id="7d182-134">方法: グローバル アセンブリ キャッシュからアセンブリを削除する</span><span class="sxs-lookup"><span data-stu-id="7d182-134">How to: Remove an Assembly from the Global Assembly Cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)  
<span data-ttu-id="7d182-135">[グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) を使用して、グローバル アセンブリ キャッシュからアセンブリを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7d182-135">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to remove an assembly from the global assembly cache.</span></span>  
  
[<span data-ttu-id="7d182-136">サービス コンポーネントとグローバル アセンブリ キャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="7d182-136">Using Serviced Components with the Global Assembly Cache</span></span>](use-serviced-components-with-the-gac.md)  
<span data-ttu-id="7d182-137">サービス コンポーネント (マネージド COM+ コンポーネント) をグローバル アセンブリ キャッシュに配置する必要がある理由について説明します。</span><span class="sxs-lookup"><span data-stu-id="7d182-137">Explains why serviced components (managed COM+ components) should be placed in the global assembly cache.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7d182-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d182-138">Related Sections</span></span>  

[<span data-ttu-id="7d182-139">アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="7d182-139">Creating Assemblies</span></span>](../../standard/assembly/create.md)  
<span data-ttu-id="7d182-140">アセンブリの作成の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="7d182-140">Provides an overview of creating assemblies.</span></span>  
  
[<span data-ttu-id="7d182-141">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="7d182-141">Global Assembly Cache</span></span>](gac.md)  
<span data-ttu-id="7d182-142">グローバル アセンブリ キャッシュについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7d182-142">Describes the global assembly cache.</span></span>  
  
[<span data-ttu-id="7d182-143">方法: アセンブリの内容を表示する</span><span class="sxs-lookup"><span data-stu-id="7d182-143">How to: View Assembly Contents</span></span>](../../standard/assembly/view-contents.md)  
<span data-ttu-id="7d182-144">[Ildasm.exe (IL 逆アセンブラー)](../tools/ildasm-exe-il-disassembler.md) を使用して、アセンブリ内の MSIL (Microsoft Intermediate Language) 情報を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7d182-144">Explains how to use the [Ildasm.exe (IL Disassembler)](../tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in an assembly.</span></span>  
  
[<span data-ttu-id="7d182-145">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="7d182-145">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)  
<span data-ttu-id="7d182-146">共通言語ランタイムが、アプリケーションを構成するアセンブリを検出して読み込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7d182-146">Describes how the common language runtime locates and loads the assemblies that make up your application.</span></span>  
  
[<span data-ttu-id="7d182-147">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="7d182-147">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="7d182-148">マネージド アプリケーションを構成するブロックであるアセンブリについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7d182-148">Describes assemblies, the building blocks of managed applications.</span></span>
