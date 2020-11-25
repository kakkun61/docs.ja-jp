---
title: IMetaDataDispenserEx インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
ms.openlocfilehash: 60d321c1a87a5da433437c9d4587fa9f8947acf4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713380"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="d5e06-102">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5e06-102">IMetaDataDispenserEx Interface</span></span>

<span data-ttu-id="d5e06-103">[IMetaDataDispenser インターフェイス](imetadatadispenser-interface.md)インターフェイスを拡張して、メタデータ api が現在のメタデータスコープに対してどのように動作するかを制御する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="d5e06-103">Extends the [IMetaDataDispenser Interface](imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d5e06-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="d5e06-104">Methods</span></span>  
  
|<span data-ttu-id="d5e06-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d5e06-105">Method</span></span>|<span data-ttu-id="d5e06-106">説明</span><span class="sxs-lookup"><span data-stu-id="d5e06-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d5e06-107">FindAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="d5e06-107">FindAssembly Method</span></span>](imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="d5e06-108">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="d5e06-108">This method is not implemented.</span></span> <span data-ttu-id="d5e06-109">呼び出された場合は E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="d5e06-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="d5e06-110">FindAssemblyModule メソッド</span><span class="sxs-lookup"><span data-stu-id="d5e06-110">FindAssemblyModule Method</span></span>](imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="d5e06-111">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="d5e06-111">This method is not implemented.</span></span> <span data-ttu-id="d5e06-112">呼び出された場合は E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="d5e06-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="d5e06-113">GetCORSystemDirectory メソッド</span><span class="sxs-lookup"><span data-stu-id="d5e06-113">GetCORSystemDirectory Method</span></span>](imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="d5e06-114">現在の共通言語ランタイム (CLR) が格納されているディレクトリを取得します。</span><span class="sxs-lookup"><span data-stu-id="d5e06-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="d5e06-115">このメソッドは、アウトプロセスデバッガーでの使用に対してのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d5e06-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="d5e06-116">別のコンポーネントから呼び出された場合は、E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="d5e06-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="d5e06-117">GetOption メソッド</span><span class="sxs-lookup"><span data-stu-id="d5e06-117">GetOption Method</span></span>](imetadatadispenserex-getoption-method.md)|<span data-ttu-id="d5e06-118">現在のメタデータスコープの指定したオプションの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="d5e06-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="d5e06-119">オプションは、現在のメタデータスコープへの呼び出しの処理方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="d5e06-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="d5e06-120">OpenScopeOnITypeInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="d5e06-120">OpenScopeOnITypeInfo Method</span></span>](imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="d5e06-121">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="d5e06-121">This method is not implemented.</span></span> <span data-ttu-id="d5e06-122">呼び出された場合は E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="d5e06-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="d5e06-123">SetOption メソッド</span><span class="sxs-lookup"><span data-stu-id="d5e06-123">SetOption Method</span></span>](imetadatadispenserex-setoption-method.md)|<span data-ttu-id="d5e06-124">指定されたオプションを、現在のメタデータスコープの指定された値に設定します。</span><span class="sxs-lookup"><span data-stu-id="d5e06-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="d5e06-125">オプションは、現在のメタデータスコープへの呼び出しの処理方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="d5e06-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d5e06-126">要件</span><span class="sxs-lookup"><span data-stu-id="d5e06-126">Requirements</span></span>  

 <span data-ttu-id="d5e06-127">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5e06-127">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5e06-128">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="d5e06-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d5e06-129">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="d5e06-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d5e06-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5e06-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5e06-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5e06-131">See also</span></span>

- [<span data-ttu-id="d5e06-132">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5e06-132">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="d5e06-133">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5e06-133">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="d5e06-134">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5e06-134">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d5e06-135">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5e06-135">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
