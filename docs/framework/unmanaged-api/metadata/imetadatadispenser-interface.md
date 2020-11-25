---
title: IMetaDataDispenser インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser
helpviewer_keywords:
- IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type:
- apiref
ms.openlocfilehash: c798aeba46adf91a8c13f8143c00f02173a0bb52
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726107"
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="0e398-102">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e398-102">IMetaDataDispenser Interface</span></span>

<span data-ttu-id="0e398-103">新しいメタデータスコープを作成したり、既存のメタデータスコープを開いたりするためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="0e398-103">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0e398-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="0e398-104">Methods</span></span>  
  
|<span data-ttu-id="0e398-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="0e398-105">Method</span></span>|<span data-ttu-id="0e398-106">説明</span><span class="sxs-lookup"><span data-stu-id="0e398-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0e398-107">DefineScope メソッド</span><span class="sxs-lookup"><span data-stu-id="0e398-107">DefineScope Method</span></span>](imetadatadispenser-definescope-method.md)|<span data-ttu-id="0e398-108">新しいメタデータを作成できる新しい領域をメモリに作成します。</span><span class="sxs-lookup"><span data-stu-id="0e398-108">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="0e398-109">OpenScope メソッド</span><span class="sxs-lookup"><span data-stu-id="0e398-109">OpenScope Method</span></span>](imetadatadispenser-openscope-method.md)|<span data-ttu-id="0e398-110">ディスク上の既存のファイルを開き、そのメタデータをメモリにマップします。</span><span class="sxs-lookup"><span data-stu-id="0e398-110">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="0e398-111">OpenScopeOnMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="0e398-111">OpenScopeOnMemory Method</span></span>](imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="0e398-112">既存のメタデータを含むメモリ領域を開きます。</span><span class="sxs-lookup"><span data-stu-id="0e398-112">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="0e398-113">つまり、このメソッドは、既存のデータがメタデータとして扱われる、指定されたメモリ領域を開きます。</span><span class="sxs-lookup"><span data-stu-id="0e398-113">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e398-114">要件</span><span class="sxs-lookup"><span data-stu-id="0e398-114">Requirements</span></span>  

 <span data-ttu-id="0e398-115">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e398-115">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e398-116">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="0e398-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e398-117">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="0e398-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0e398-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e398-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e398-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e398-119">See also</span></span>

- [<span data-ttu-id="0e398-120">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e398-120">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="0e398-121">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e398-121">Metadata Interfaces</span></span>](metadata-interfaces.md)
