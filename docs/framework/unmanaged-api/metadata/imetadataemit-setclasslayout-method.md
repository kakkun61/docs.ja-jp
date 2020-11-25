---
title: IMetaDataEmit::SetClassLayout メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type:
- apiref
ms.openlocfilehash: ee10907fb7f5d90db1bdce845272cd3de38e35a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718697"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="5cd4a-102">IMetaDataEmit::SetClassLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="5cd4a-102">IMetaDataEmit::SetClassLayout Method</span></span>

<span data-ttu-id="5cd4a-103">以前に呼び出した [Typedef メソッド](imetadataemit-definetypedef-method.md)の呼び出しで定義されたクラスのフィールドのレイアウトを完了します。</span><span class="sxs-lookup"><span data-stu-id="5cd4a-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cd4a-104">構文</span><span class="sxs-lookup"><span data-stu-id="5cd4a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,
    [in]  DWORD               dwPackSize,
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],
    [in]  ULONG               ulClassSize
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cd4a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5cd4a-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="5cd4a-106">から `mdTypeDef` レイアウトするクラスを指定するトークン。</span><span class="sxs-lookup"><span data-stu-id="5cd4a-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="5cd4a-107">からパッキングサイズは1、2、4、8、または16バイトです。</span><span class="sxs-lookup"><span data-stu-id="5cd4a-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="5cd4a-108">パッキングサイズは、隣接するフィールド間のバイト数です。</span><span class="sxs-lookup"><span data-stu-id="5cd4a-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="5cd4a-109">から [COR_FIELD_OFFSET](cor-field-offset-structure.md) 構造体の配列。各構造体は、クラスのフィールドと、クラス内のフィールドのオフセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="5cd4a-109">[in] An array of [COR_FIELD_OFFSET](cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="5cd4a-110">で配列を終了 `mdTokenNil` します。</span><span class="sxs-lookup"><span data-stu-id="5cd4a-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="5cd4a-111">からクラスのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5cd4a-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cd4a-112">注釈</span><span class="sxs-lookup"><span data-stu-id="5cd4a-112">Remarks</span></span>  

 <span data-ttu-id="5cd4a-113">クラスを最初に定義するには、 [IMetaDataEmit::D efineTypeDef](imetadataemit-definetypedef-method.md) メソッドを呼び出し、クラスのフィールドに対して3つのレイアウト (automatic、シーケンシャル、explicit) のいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5cd4a-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="5cd4a-114">通常は、自動レイアウトを使用し、フィールドをレイアウトする最適な方法をランタイムが選択できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5cd4a-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="5cd4a-115">ただし、アンマネージコードが使用する配置に従って、フィールドをレイアウトすることが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5cd4a-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="5cd4a-116">この場合は、シーケンシャルまたは明示的なレイアウトを選択し、を呼び出して、 `SetClassLayout` フィールドのレイアウトを完成させます。</span><span class="sxs-lookup"><span data-stu-id="5cd4a-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
- <span data-ttu-id="5cd4a-117">シーケンシャルレイアウト: パッキングサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="5cd4a-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="5cd4a-118">フィールドは、自然サイズまたはパッキングサイズのいずれかに従って整列されます。どちらの場合も、フィールドのオフセットは小さくなります。</span><span class="sxs-lookup"><span data-stu-id="5cd4a-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="5cd4a-119">`rFieldOffsets`を `ulClassSize` 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="5cd4a-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
- <span data-ttu-id="5cd4a-120">明示的なレイアウト: 各フィールドのオフセットを指定するか、クラスのサイズとパッキングサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="5cd4a-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cd4a-121">要件</span><span class="sxs-lookup"><span data-stu-id="5cd4a-121">Requirements</span></span>  

 <span data-ttu-id="5cd4a-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5cd4a-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cd4a-123">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="5cd4a-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5cd4a-124">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="5cd4a-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5cd4a-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cd4a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cd4a-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="5cd4a-126">See also</span></span>

- [<span data-ttu-id="5cd4a-127">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5cd4a-127">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="5cd4a-128">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5cd4a-128">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
