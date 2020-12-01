---
title: COM 相互運用機能によるデータのマーシャリング
description: COM 相互運用機能によるデータのマーシャリングに関する記事をご覧ください。 Tlbimp.exe と Tlbexp.exe ツールは、COM タイプ ライブラリと相互運用機能アセンブリ間の変換を行います。
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: bcbd2c50fcbd9af3f2eead57ac2e26f8db0c6ad6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275945"
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="3bfe7-104">COM 相互運用機能によるデータのマーシャリング</span><span class="sxs-lookup"><span data-stu-id="3bfe7-104">Marshaling Data with COM Interop</span></span>

<span data-ttu-id="3bfe7-105">COM 相互運用は、マネージド コードから COM オブジェクトを使用すること、およびマネージド オブジェクトを COM に公開することの、両方の操作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="3bfe7-105">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="3bfe7-106">COM との間でデータをマーシャリングする操作のサポートは広範で、ほとんどの場合、正しいマーシャリング動作が提供されます。</span><span class="sxs-lookup"><span data-stu-id="3bfe7-106">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="3bfe7-107">Windows SDK には、以下の COM 相互運用ツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3bfe7-107">The Windows SDK includes the following COM interop tools:</span></span>  
  
- <span data-ttu-id="3bfe7-108">[タイプ ライブラリ インポーター (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md)、これは COM タイプ ライブラリを相互運用アセンブリに変換します。</span><span class="sxs-lookup"><span data-stu-id="3bfe7-108">[Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="3bfe7-109">このアセンブリから、相互運用マーシャリング サービスは、マネージド メモリとアンマネージド メモリ間のデータ マーシャリングを実行するラッパーを生成します。</span><span class="sxs-lookup"><span data-stu-id="3bfe7-109">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
- <span data-ttu-id="3bfe7-110">[タイプ ライブラリ エクスポーター (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md)、これは COM タイプ ライブラリをアセンブリから生成して、メソッド呼び出しの際にマーシャリングを実行するラッパーを生成します。</span><span class="sxs-lookup"><span data-stu-id="3bfe7-110">[Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="3bfe7-111">以下のセクションは、マーシャラーに追加の型情報を提供できる (またはその必要がある) ときに、相互運用ラッパーをカスタマイズするためのプロセスについて説明するトピックにリンクしています。</span><span class="sxs-lookup"><span data-stu-id="3bfe7-111">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3bfe7-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3bfe7-112">In This Section</span></span>  

<span data-ttu-id="3bfe7-113">[方法: ラッパーを手動で作成する](how-to-create-wrappers-manually.md) マネージド ソース コードにおいて COM ラッパーを手動で作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3bfe7-113">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) Describes how to create a COM wrapper manually in managed source code.</span></span>

 [<span data-ttu-id="3bfe7-114">方法: マネージド コード DCOM を WCF に移行する</span><span class="sxs-lookup"><span data-stu-id="3bfe7-114">How to: Migrate Managed-Code DCOM to WCF</span></span>](how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="3bfe7-115">最も安全なソリューションのために、マネージド DCOM コードを WCF に移行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3bfe7-115">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3bfe7-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="3bfe7-116">Related Sections</span></span>  

 <span data-ttu-id="3bfe7-117">[COM のデータ型](/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3bfe7-117">[COM Data Types](/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="3bfe7-118">対応するマネージドとアンマネージドのデータ型を提供します。</span><span class="sxs-lookup"><span data-stu-id="3bfe7-118">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="3bfe7-119">[COM 呼び出し可能ラッパーのカスタマイズ](/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3bfe7-119">[Customizing COM Callable Wrappers](/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="3bfe7-120">デザイン時に <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性を使用して、データ型を明示的にマーシャリングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3bfe7-120">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="3bfe7-121">[ランタイム呼び出し可能ラッパーのカスタマイズ](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3bfe7-121">[Customizing Runtime Callable Wrappers](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="3bfe7-122">相互運用アセンブリで型のマーシャリング動作を調整する方法、および COM 型を手動で定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3bfe7-122">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="3bfe7-123">[高度な COM 相互運用性](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3bfe7-123">[Advanced COM Interoperability](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="3bfe7-124">.NET Framework アプリケーションに COM コンポーネントを組み込む方法についての詳細情報へのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="3bfe7-124">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="3bfe7-125">[アセンブリからタイプ ライブラリへの変換の要約](/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3bfe7-125">[Assembly to Type Library Conversion Summary](/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="3bfe7-126">アセンブリからタイプ ライブラリにエクスポート変換するプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3bfe7-126">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="3bfe7-127">[タイプ ライブラリからアセンブリへの変換の要約](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3bfe7-127">[Type Library to Assembly Conversion Summary](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="3bfe7-128">タイプ ライブラリからアセンブリにインポート変換するプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3bfe7-128">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="3bfe7-129">[ジェネリック型を使用する相互運用](/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3bfe7-129">[Interoperating Using Generic Types](/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="3bfe7-130">COM 相互運用性のジェネリック型を使用するとき、どのアクションがサポートされるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3bfe7-130">Describes which actions are supported when using generic types for COM interoperability.</span></span>
