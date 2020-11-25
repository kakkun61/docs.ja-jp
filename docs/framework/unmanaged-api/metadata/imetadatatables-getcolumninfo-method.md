---
title: IMetaDataTables::GetColumnInfo メソッド
ms.date: 10/10/2019
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
ms.openlocfilehash: 227d9ab67ab3091508232be3018ca520a6b5dcc6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711053"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="09ed7-102">IMetaDataTables::GetColumnInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="09ed7-102">IMetaDataTables::GetColumnInfo Method</span></span>

<span data-ttu-id="09ed7-103">指定されたテーブル内の指定された列に関するデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="09ed7-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09ed7-104">構文</span><span class="sxs-lookup"><span data-stu-id="09ed7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumnInfo (
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09ed7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="09ed7-105">Parameters</span></span>

=======

 `ixTbl`  
 <span data-ttu-id="09ed7-106">から目的のテーブルのインデックス。</span><span class="sxs-lookup"><span data-stu-id="09ed7-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="09ed7-107">から目的の列のインデックス。</span><span class="sxs-lookup"><span data-stu-id="09ed7-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="09ed7-108">入出力行内の列のオフセットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="09ed7-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="09ed7-109">入出力列のサイズ (バイト単位) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="09ed7-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="09ed7-110">入出力列内の値の型へのポインター。</span><span class="sxs-lookup"><span data-stu-id="09ed7-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="09ed7-111">入出力列名へのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="09ed7-111">[out] A pointer to a pointer to the column name.</span></span>  

## <a name="remarks"></a><span data-ttu-id="09ed7-112">注釈</span><span class="sxs-lookup"><span data-stu-id="09ed7-112">Remarks</span></span>

<span data-ttu-id="09ed7-113">返される列の型は、値の範囲内にあります。</span><span class="sxs-lookup"><span data-stu-id="09ed7-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="09ed7-114">pType</span><span class="sxs-lookup"><span data-stu-id="09ed7-114">pType</span></span>                    | <span data-ttu-id="09ed7-115">説明</span><span class="sxs-lookup"><span data-stu-id="09ed7-115">Description</span></span>   | <span data-ttu-id="09ed7-116">ヘルパー関数</span><span class="sxs-lookup"><span data-stu-id="09ed7-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="09ed7-117">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="09ed7-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="09ed7-118">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="09ed7-118">(0..63)</span></span>   | <span data-ttu-id="09ed7-119">Rid</span><span class="sxs-lookup"><span data-stu-id="09ed7-119">Rid</span></span>           | <span data-ttu-id="09ed7-120">**IsRidType**</span><span class="sxs-lookup"><span data-stu-id="09ed7-120">**IsRidType**</span></span><br><span data-ttu-id="09ed7-121">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="09ed7-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="09ed7-122">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="09ed7-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="09ed7-123">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="09ed7-123">(64..95)</span></span> | <span data-ttu-id="09ed7-124">コード化されたトークン</span><span class="sxs-lookup"><span data-stu-id="09ed7-124">Coded token</span></span> | <span data-ttu-id="09ed7-125">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="09ed7-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="09ed7-126">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="09ed7-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="09ed7-127">`iSHORT` (96)</span><span class="sxs-lookup"><span data-stu-id="09ed7-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="09ed7-128">Int16</span><span class="sxs-lookup"><span data-stu-id="09ed7-128">Int16</span></span>         | <span data-ttu-id="09ed7-129">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="09ed7-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="09ed7-130">`iUSHORT` (97)</span><span class="sxs-lookup"><span data-stu-id="09ed7-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="09ed7-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="09ed7-131">UInt16</span></span>        | <span data-ttu-id="09ed7-132">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="09ed7-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="09ed7-133">`iLONG` (98)</span><span class="sxs-lookup"><span data-stu-id="09ed7-133">`iLONG` (98)</span></span>             | <span data-ttu-id="09ed7-134">Int32</span><span class="sxs-lookup"><span data-stu-id="09ed7-134">Int32</span></span>         | <span data-ttu-id="09ed7-135">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="09ed7-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="09ed7-136">`iULONG` (99)</span><span class="sxs-lookup"><span data-stu-id="09ed7-136">`iULONG` (99)</span></span>            | <span data-ttu-id="09ed7-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="09ed7-137">UInt32</span></span>        | <span data-ttu-id="09ed7-138">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="09ed7-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="09ed7-139">`iBYTE` (100)</span><span class="sxs-lookup"><span data-stu-id="09ed7-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="09ed7-140">Byte</span><span class="sxs-lookup"><span data-stu-id="09ed7-140">Byte</span></span>          | <span data-ttu-id="09ed7-141">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="09ed7-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="09ed7-142">`iSTRING` (101)</span><span class="sxs-lookup"><span data-stu-id="09ed7-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="09ed7-143">String</span><span class="sxs-lookup"><span data-stu-id="09ed7-143">String</span></span>        | <span data-ttu-id="09ed7-144">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="09ed7-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="09ed7-145">`iGUID` (102)</span><span class="sxs-lookup"><span data-stu-id="09ed7-145">`iGUID` (102)</span></span>            | <span data-ttu-id="09ed7-146">Guid</span><span class="sxs-lookup"><span data-stu-id="09ed7-146">Guid</span></span>          | <span data-ttu-id="09ed7-147">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="09ed7-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="09ed7-148">`iBLOB` (103)</span><span class="sxs-lookup"><span data-stu-id="09ed7-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="09ed7-149">BLOB</span><span class="sxs-lookup"><span data-stu-id="09ed7-149">Blob</span></span>          | <span data-ttu-id="09ed7-150">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="09ed7-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="09ed7-151">*ヒープ* に格納されている値 (つまり、 `IsHeapType == true` ) は次を使用して読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="09ed7-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="09ed7-152">`iSTRING`: **Imetadatatables**</span><span class="sxs-lookup"><span data-stu-id="09ed7-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="09ed7-153">`iGUID`: **Imetadatatables 実行できます。 GetGUID**</span><span class="sxs-lookup"><span data-stu-id="09ed7-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="09ed7-154">`iBLOB`: **Imetadatatables 実行できます。 GetBlob**</span><span class="sxs-lookup"><span data-stu-id="09ed7-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="09ed7-155">上の表で定義されている定数を使用するには、 `#define _DEFINE_META_DATA_META_CONSTANTS` *cor* ヘッダーファイルによって提供されるディレクティブをインクルードします。</span><span class="sxs-lookup"><span data-stu-id="09ed7-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="09ed7-156">要件</span><span class="sxs-lookup"><span data-stu-id="09ed7-156">Requirements</span></span>  

 <span data-ttu-id="09ed7-157">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09ed7-157">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09ed7-158">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="09ed7-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="09ed7-159">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="09ed7-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="09ed7-160">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09ed7-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ed7-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="09ed7-161">See also</span></span>

- [<span data-ttu-id="09ed7-162">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="09ed7-162">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="09ed7-163">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="09ed7-163">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
