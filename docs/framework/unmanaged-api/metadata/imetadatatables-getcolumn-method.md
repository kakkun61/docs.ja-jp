---
title: IMetaDataTables::GetColumn メソッド
ms.date: 02/25/2019
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
ms.openlocfilehash: 270546f0270521e38cfdcae5e4d2137202c13cb1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711075"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="b2f9d-102">IMetaDataTables::GetColumn メソッド</span><span class="sxs-lookup"><span data-stu-id="b2f9d-102">IMetaDataTables::GetColumn Method</span></span>

<span data-ttu-id="b2f9d-103">指定したテーブル内の指定した列および行のセルに格納されている値へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2f9d-104">構文</span><span class="sxs-lookup"><span data-stu-id="b2f9d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2f9d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b2f9d-105">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="b2f9d-106">からテーブルのインデックス。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="b2f9d-107">からテーブル内の列のインデックス。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="b2f9d-108">からテーブル内の行のインデックス。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="b2f9d-109">入出力セル内の値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-109">[out] A pointer to the value in the cell.</span></span>  

## <a name="remarks"></a><span data-ttu-id="b2f9d-110">注釈</span><span class="sxs-lookup"><span data-stu-id="b2f9d-110">Remarks</span></span>

<span data-ttu-id="b2f9d-111">によって返される値の interpretion は、 `pVal` 列の型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-111">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="b2f9d-112">列の型は、 [GetColumnInfo](imetadatatables-getcolumninfo-method.md)を呼び出すことによって決定できます。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-112">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="b2f9d-113">**Getcolumn** メソッドは、 **Rid** または **codedtoken** 型の列を、完全な32ビット値に自動的に変換し `mdToken` ます。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-113">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="b2f9d-114">また、8ビットまたは16ビットの値を完全な32ビット値に自動的に変換します。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-114">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span>
- <span data-ttu-id="b2f9d-115">*ヒープ* 型の列の場合、返される *pVal* は、対応するヒープのインデックスになります。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-115">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="b2f9d-116">列の型</span><span class="sxs-lookup"><span data-stu-id="b2f9d-116">Column type</span></span>              | <span data-ttu-id="b2f9d-117">pVal を含む</span><span class="sxs-lookup"><span data-stu-id="b2f9d-117">pVal contains</span></span> | <span data-ttu-id="b2f9d-118">コメント</span><span class="sxs-lookup"><span data-stu-id="b2f9d-118">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="b2f9d-119">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="b2f9d-119">`0`..`iRidMax`</span></span><br><span data-ttu-id="b2f9d-120">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="b2f9d-120">(0..63)</span></span>  | <span data-ttu-id="b2f9d-121">mdToken</span><span class="sxs-lookup"><span data-stu-id="b2f9d-121">mdToken</span></span>     | <span data-ttu-id="b2f9d-122">*pVal* には完全なトークンが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-122">*pVal* will contain a full Token.</span></span> <span data-ttu-id="b2f9d-123">関数は、自動的に Rid を完全なトークンに変換します。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-123">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="b2f9d-124">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="b2f9d-124">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="b2f9d-125">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="b2f9d-125">(64..95)</span></span> | <span data-ttu-id="b2f9d-126">mdToken</span><span class="sxs-lookup"><span data-stu-id="b2f9d-126">mdToken</span></span> | <span data-ttu-id="b2f9d-127">返されると、 *pVal* には完全なトークンが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-127">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="b2f9d-128">関数は、CodedToken を完全なトークンに自動的に圧縮解除します。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-128">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="b2f9d-129">`iSHORT` (96)</span><span class="sxs-lookup"><span data-stu-id="b2f9d-129">`iSHORT` (96)</span></span>            | <span data-ttu-id="b2f9d-130">Int16</span><span class="sxs-lookup"><span data-stu-id="b2f9d-130">Int16</span></span>         | <span data-ttu-id="b2f9d-131">32ビットに自動的に拡張されます。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-131">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="b2f9d-132">`iUSHORT` (97)</span><span class="sxs-lookup"><span data-stu-id="b2f9d-132">`iUSHORT` (97)</span></span>           | <span data-ttu-id="b2f9d-133">UInt16</span><span class="sxs-lookup"><span data-stu-id="b2f9d-133">UInt16</span></span>        | <span data-ttu-id="b2f9d-134">32ビットに自動的に拡張されます。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-134">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="b2f9d-135">`iLONG` (98)</span><span class="sxs-lookup"><span data-stu-id="b2f9d-135">`iLONG` (98)</span></span>             | <span data-ttu-id="b2f9d-136">Int32</span><span class="sxs-lookup"><span data-stu-id="b2f9d-136">Int32</span></span>         |                                        |
| <span data-ttu-id="b2f9d-137">`iULONG` (99)</span><span class="sxs-lookup"><span data-stu-id="b2f9d-137">`iULONG` (99)</span></span>            | <span data-ttu-id="b2f9d-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="b2f9d-138">UInt32</span></span>        |                                        |
| <span data-ttu-id="b2f9d-139">`iBYTE` (100)</span><span class="sxs-lookup"><span data-stu-id="b2f9d-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="b2f9d-140">Byte</span><span class="sxs-lookup"><span data-stu-id="b2f9d-140">Byte</span></span>          | <span data-ttu-id="b2f9d-141">32ビットに自動的に拡張されます。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-141">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="b2f9d-142">`iSTRING` (101)</span><span class="sxs-lookup"><span data-stu-id="b2f9d-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="b2f9d-143">文字列ヒープインデックス</span><span class="sxs-lookup"><span data-stu-id="b2f9d-143">String heap index</span></span> | <span data-ttu-id="b2f9d-144">*pVal* は、文字列ヒープのインデックスです。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-144">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="b2f9d-145">実際の列文字列値を取得するには、 [Imetadatatables::](imetadatatables-getstring-method.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-145">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="b2f9d-146">`iGUID` (102)</span><span class="sxs-lookup"><span data-stu-id="b2f9d-146">`iGUID` (102)</span></span>            | <span data-ttu-id="b2f9d-147">Guid ヒープインデックス</span><span class="sxs-lookup"><span data-stu-id="b2f9d-147">Guid heap index</span></span> | <span data-ttu-id="b2f9d-148">*pVal* は、Guid ヒープのインデックスです。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-148">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="b2f9d-149">実際の列の Guid 値を取得するには、 [Imetadatatables 指定できる:: GetGuid](imetadatatables-getguid-method.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-149">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="b2f9d-150">`iBLOB` (103)</span><span class="sxs-lookup"><span data-stu-id="b2f9d-150">`iBLOB` (103)</span></span>            | <span data-ttu-id="b2f9d-151">Blob ヒープインデックス</span><span class="sxs-lookup"><span data-stu-id="b2f9d-151">Blob heap index</span></span> | <span data-ttu-id="b2f9d-152">*pVal* は、Blob ヒープのインデックスです。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-152">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="b2f9d-153">実際の列の Blob 値を取得するには、 [Imetadatatables 指定できる:: GetBlob](imetadatatables-getblob-method.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-153">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="b2f9d-154">要件</span><span class="sxs-lookup"><span data-stu-id="b2f9d-154">Requirements</span></span>  

 <span data-ttu-id="b2f9d-155">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-155">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2f9d-156">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="b2f9d-156">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2f9d-157">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="b2f9d-157">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2f9d-158">**.NET Framework のバージョン**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2f9d-158">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2f9d-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2f9d-159">See also</span></span>

- [<span data-ttu-id="b2f9d-160">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b2f9d-160">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="b2f9d-161">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b2f9d-161">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
