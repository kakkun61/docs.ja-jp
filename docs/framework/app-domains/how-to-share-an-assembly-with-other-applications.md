---
title: '方法: アセンブリを他のアプリケーションと共有する'
description: .NET でアセンブリを他のアプリケーションと共有する方法を参照します。 アセンブリはプライベート (既定) または共有にすることができます。 アセンブリを共有するには、アセンブリを GAC に配置します。
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 1056f8b555713d5d67488537e6c06cc457c4d312
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242540"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a><span data-ttu-id="2ef3f-105">方法: アセンブリを他のアプリケーションと共有する</span><span class="sxs-lookup"><span data-stu-id="2ef3f-105">How to: Share an assembly with other applications</span></span>

<span data-ttu-id="2ef3f-106">アセンブリはプライベートまたは共有にすることができます。既定では、ほとんどの単純なプログラムは、他のアプリケーションによって使われることを意図されていないので、プライベート アセンブリで構成されます。</span><span class="sxs-lookup"><span data-stu-id="2ef3f-106">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  

<span data-ttu-id="2ef3f-107">他のアプリケーションとアセンブリを共有するには、[グローバル アセンブリ キャッシュ (GAC)](gac.md) にアセンブリを置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ef3f-107">In order to share an assembly with other applications, it must be placed in the [global assembly cache (GAC)](gac.md).</span></span>  
  
<span data-ttu-id="2ef3f-108">アセンブリを共有するには:</span><span class="sxs-lookup"><span data-stu-id="2ef3f-108">To share an assembly:</span></span>
  
1. <span data-ttu-id="2ef3f-109">アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="2ef3f-109">Create your assembly.</span></span> <span data-ttu-id="2ef3f-110">詳しくは、「[アセンブリを作成する](../../standard/assembly/create.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2ef3f-110">For more information, see [Create assemblies](../../standard/assembly/create.md).</span></span>  
  
2. <span data-ttu-id="2ef3f-111">アセンブリに厳密な名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2ef3f-111">Assign a strong name to your assembly.</span></span> <span data-ttu-id="2ef3f-112">詳細については、「[方法:厳密な名前でアセンブリに署名する](../../standard/assembly/sign-strong-name.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ef3f-112">For more information, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>  
  
3. <span data-ttu-id="2ef3f-113">アセンブリにバージョン情報を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2ef3f-113">Assign version information to your assembly.</span></span> <span data-ttu-id="2ef3f-114">詳細については、「[アセンブリのバージョン管理](../../standard/assembly/versioning.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ef3f-114">For more information, see [Assembly versioning](../../standard/assembly/versioning.md).</span></span>  
  
4. <span data-ttu-id="2ef3f-115">グローバル アセンブリ キャッシュにアセンブリを追加します。</span><span class="sxs-lookup"><span data-stu-id="2ef3f-115">Add your assembly to the global assembly cache.</span></span> <span data-ttu-id="2ef3f-116">詳細については、「[方法:アセンブリをグローバル アセンブリ キャッシュにインストールする](install-assembly-into-gac.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ef3f-116">For more information, see [How to: Install an assembly into the global assembly cache](install-assembly-into-gac.md).</span></span>  
  
5. <span data-ttu-id="2ef3f-117">他のアプリケーションからアセンブリに含まれる型にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2ef3f-117">Access the types contained in the assembly from other applications.</span></span> <span data-ttu-id="2ef3f-118">詳細については、「[方法:厳密な名前のアセンブリを参照する](../../standard/assembly/reference-strong-named.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ef3f-118">For more information, see [How to: Reference a strong-named assembly](../../standard/assembly/reference-strong-named.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ef3f-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ef3f-119">See also</span></span>

- [<span data-ttu-id="2ef3f-120">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="2ef3f-120">C# programming guide</span></span>](../../../api/index.md)
- [<span data-ttu-id="2ef3f-121">プログラミングの概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ef3f-121">Programming concepts (Visual Basic)</span></span>](../../../api/index.md)
- [<span data-ttu-id="2ef3f-122">アセンブリを使用したプログラム</span><span class="sxs-lookup"><span data-stu-id="2ef3f-122">Program with assemblies</span></span>](../../standard/assembly/index.md)
