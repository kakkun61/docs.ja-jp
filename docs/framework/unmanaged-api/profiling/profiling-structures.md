---
title: 構造体のプロファイリング
ms.date: 03/30/2017
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
ms.openlocfilehash: 3f832850fac918a568d02e9ef2f1e5b140ffc04f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722753"
---
# <a name="profiling-structures"></a><span data-ttu-id="f626d-102">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="f626d-102">Profiling Structures</span></span>

<span data-ttu-id="f626d-103">このセクションではプロファイル API で使用されるアンマネージ構造体について説明します。</span><span class="sxs-lookup"><span data-stu-id="f626d-103">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f626d-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f626d-104">In This Section</span></span>  

 [<span data-ttu-id="f626d-105">COR_PRF_ASSEMBLY_REFERENCE_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="f626d-105">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="f626d-106">共通言語ランタイムに、アセンブリ参照クロージャー ウォークを実行するときに考慮するべき参照アセンブリに関する詳細を提供します。</span><span class="sxs-lookup"><span data-stu-id="f626d-106">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="f626d-107">COR_PRF_CODE_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="f626d-107">COR_PRF_CODE_INFO Structure</span></span>](cor-prf-code-info-structure.md)  
 <span data-ttu-id="f626d-108">メモリに格納されている 1 個の連続ブロックからなるネイティブ コードを表します。</span><span class="sxs-lookup"><span data-stu-id="f626d-108">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="f626d-109">COR_PRF_EX_CLAUSE_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="f626d-109">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="f626d-110">特定の例外句インスタンスおよび関連するフレームに関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="f626d-110">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="f626d-111">COR_PRF_FUNCTION 構造体</span><span class="sxs-lookup"><span data-stu-id="f626d-111">COR_PRF_FUNCTION Structure</span></span>](cor-prf-function-structure.md)  
 <span data-ttu-id="f626d-112">関数の一意の表記を、その関数の ID を再コンパイルされたバージョンの ID と組み合わせることによって、提供します。</span><span class="sxs-lookup"><span data-stu-id="f626d-112">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="f626d-113">COR_PRF_FUNCTION_ARGUMENT_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="f626d-113">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="f626d-114">関数の引数を左から右方向で表します。</span><span class="sxs-lookup"><span data-stu-id="f626d-114">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="f626d-115">COR_PRF_FUNCTION_ARGUMENT_RANGE 構造体</span><span class="sxs-lookup"><span data-stu-id="f626d-115">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="f626d-116">メモリに左から右方向へ連続で格納される関数の引数のブロックを表します。</span><span class="sxs-lookup"><span data-stu-id="f626d-116">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="f626d-117">COR_PRF_GC_GENERATION_RANGE 構造体</span><span class="sxs-lookup"><span data-stu-id="f626d-117">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="f626d-118">ガーベッジ コレクションを実行中のメモリ範囲 (ブロック) を説明します。</span><span class="sxs-lookup"><span data-stu-id="f626d-118">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f626d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="f626d-119">Related Sections</span></span>  

 <span data-ttu-id="f626d-120">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="f626d-120">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="f626d-121">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="f626d-121">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="f626d-122">プロファイリングの概要</span><span class="sxs-lookup"><span data-stu-id="f626d-122">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="f626d-123">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f626d-123">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="f626d-124">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="f626d-124">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="f626d-125">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="f626d-125">Profiling Enumerations</span></span>](profiling-enumerations.md)
