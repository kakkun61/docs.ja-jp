---
title: IMetaDataEmit2 インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
ms.openlocfilehash: b8ad159dace734c343297b256092162f17ab829b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726484"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="c7626-102">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c7626-102">IMetaDataEmit2 Interface</span></span>

<span data-ttu-id="c7626-103">[IMetaDataEmit](imetadataemit-interface.md)インターフェイスを拡張して、主にジェネリック型を操作できるようにします。</span><span class="sxs-lookup"><span data-stu-id="c7626-103">Extends the [IMetaDataEmit](imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7626-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="c7626-104">Methods</span></span>  
  
|<span data-ttu-id="c7626-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c7626-105">Method</span></span>|<span data-ttu-id="c7626-106">説明</span><span class="sxs-lookup"><span data-stu-id="c7626-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7626-107">DefineGenericParam メソッド</span><span class="sxs-lookup"><span data-stu-id="c7626-107">DefineGenericParam Method</span></span>](imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="c7626-108">ジェネリック型パラメーターの定義を作成し、そのジェネリック型パラメーターへのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="c7626-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="c7626-109">DefineMethodSpec メソッド</span><span class="sxs-lookup"><span data-stu-id="c7626-109">DefineMethodSpec Method</span></span>](imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="c7626-110">メソッドのジェネリックインスタンスを作成し、その定義へのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="c7626-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="c7626-111">GetDeltaSaveSize メソッド</span><span class="sxs-lookup"><span data-stu-id="c7626-111">GetDeltaSaveSize Method</span></span>](imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="c7626-112">現在のエディットコンティニュセッションの変更を表すために必要なデータのサイズの差を示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="c7626-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="c7626-113">ResetENCLog メソッド</span><span class="sxs-lookup"><span data-stu-id="c7626-113">ResetENCLog Method</span></span>](imetadataemit2-resetenclog-method.md)|<span data-ttu-id="c7626-114">エディットコンティニュログをリセットし、新しいセッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="c7626-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="c7626-115">SaveDelta メソッド</span><span class="sxs-lookup"><span data-stu-id="c7626-115">SaveDelta Method</span></span>](imetadataemit2-savedelta-method.md)|<span data-ttu-id="c7626-116">現在のエディットコンティニュセッションから、指定したファイルへの変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="c7626-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="c7626-117">SaveDeltaToMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="c7626-117">SaveDeltaToMemory Method</span></span>](imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="c7626-118">現在のエディットコンティニュセッションの変更をメモリに保存します。</span><span class="sxs-lookup"><span data-stu-id="c7626-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="c7626-119">SaveDeltaToStream メソッド</span><span class="sxs-lookup"><span data-stu-id="c7626-119">SaveDeltaToStream Method</span></span>](imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="c7626-120">現在のエディットコンティニュセッションから、指定されたストリームに変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="c7626-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="c7626-121">SetGenericParamProps メソッド</span><span class="sxs-lookup"><span data-stu-id="c7626-121">SetGenericParamProps Method</span></span>](imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="c7626-122">指定したトークンによって参照されるジェネリックパラメーター定義のプロパティ値を設定します。</span><span class="sxs-lookup"><span data-stu-id="c7626-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7626-123">要件</span><span class="sxs-lookup"><span data-stu-id="c7626-123">Requirements</span></span>  

 <span data-ttu-id="c7626-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7626-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7626-125">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="c7626-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7626-126">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="c7626-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c7626-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7626-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7626-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7626-128">See also</span></span>

- [<span data-ttu-id="c7626-129">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c7626-129">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="c7626-130">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c7626-130">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
