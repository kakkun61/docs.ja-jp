---
title: IMetaDataTables インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables
helpviewer_keywords:
- IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type:
- apiref
ms.openlocfilehash: 073e73f082416308b893974471e39cbf5243d01c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708856"
---
# <a name="imetadatatables-interface"></a><span data-ttu-id="21bc3-102">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="21bc3-102">IMetaDataTables Interface</span></span>

<span data-ttu-id="21bc3-103">テーブル内のメタデータ情報の格納と取得のためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="21bc3-103">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="21bc3-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-104">Methods</span></span>  
  
|<span data-ttu-id="21bc3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-105">Method</span></span>|<span data-ttu-id="21bc3-106">説明</span><span class="sxs-lookup"><span data-stu-id="21bc3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="21bc3-107">GetBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-107">GetBlob Method</span></span>](imetadatatables-getblob-method.md)|<span data-ttu-id="21bc3-108">指定した列インデックスにあるバイナリラージオブジェクト (BLOB) へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="21bc3-108">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>|  
|[<span data-ttu-id="21bc3-109">GetBlobHeapSize メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-109">GetBlobHeapSize Method</span></span>](imetadatatables-getblobheapsize-method.md)|<span data-ttu-id="21bc3-110">BLOB ヒープのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="21bc3-110">Gets the size, in bytes, of the BLOB heap.</span></span>|  
|[<span data-ttu-id="21bc3-111">GetCodedTokenInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-111">GetCodedTokenInfo Method</span></span>](imetadatatables-getcodedtokeninfo-method.md)|<span data-ttu-id="21bc3-112">指定した行インデックスに関連付けられているトークンの配列へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="21bc3-112">Gets a pointer to an array of tokens associated with the specified row index.</span></span>|  
|[<span data-ttu-id="21bc3-113">GetColumn メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-113">GetColumn Method</span></span>](imetadatatables-getcolumn-method.md)|<span data-ttu-id="21bc3-114">指定したテーブルインデックスにあるテーブル内の、指定した列インデックスにある列に格納されている値へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="21bc3-114">Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="21bc3-115">GetColumnInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-115">GetColumnInfo Method</span></span>](imetadatatables-getcolumninfo-method.md)|<span data-ttu-id="21bc3-116">指定されたテーブル内の指定された列に関するデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="21bc3-116">Gets data about the specified column in the specified table.</span></span>|  
|[<span data-ttu-id="21bc3-117">GetGuid メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-117">GetGuid Method</span></span>](imetadatatables-getguid-method.md)|<span data-ttu-id="21bc3-118">指定したインデックス位置にある行から GUID を取得します。</span><span class="sxs-lookup"><span data-stu-id="21bc3-118">Gets a GUID from the row at the specified index.</span></span>|  
|[<span data-ttu-id="21bc3-119">GetGuidHeapSize メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-119">GetGuidHeapSize Method</span></span>](imetadatatables-getguidheapsize-method.md)|<span data-ttu-id="21bc3-120">GUID ヒープのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="21bc3-120">Gets the size, in bytes, of the GUID heap.</span></span>|  
|[<span data-ttu-id="21bc3-121">GetNextBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-121">GetNextBlob Method</span></span>](imetadatatables-getnextblob-method.md)|<span data-ttu-id="21bc3-122">テーブル内の次の BLOB のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="21bc3-122">Gets the index of the next BLOB in the table.</span></span>|  
|[<span data-ttu-id="21bc3-123">GetNextGuid メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-123">GetNextGuid Method</span></span>](imetadatatables-getnextguid-method.md)|<span data-ttu-id="21bc3-124">現在のテーブル列の次の GUID 値のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="21bc3-124">Gets the index of the next GUID value in the current table column.</span></span>|  
|[<span data-ttu-id="21bc3-125">GetNextString メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-125">GetNextString Method</span></span>](imetadatatables-getnextstring-method.md)|<span data-ttu-id="21bc3-126">現在のテーブル列の次の文字列のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="21bc3-126">Gets the index of the next string in the current table column.</span></span>|  
|[<span data-ttu-id="21bc3-127">GetNextUserString メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-127">GetNextUserString Method</span></span>](imetadatatables-getnextuserstring-method.md)|<span data-ttu-id="21bc3-128">現在のテーブル列の次のハードコーディングされた文字列を含む行のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="21bc3-128">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>|  
|[<span data-ttu-id="21bc3-129">GetNumTables メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-129">GetNumTables Method</span></span>](imetadatatables-getnumtables-method.md)|<span data-ttu-id="21bc3-130">現在のインスタンスのスコープ内にあるテーブルの数を取得し `IMetaDataTables` ます。</span><span class="sxs-lookup"><span data-stu-id="21bc3-130">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>|  
|[<span data-ttu-id="21bc3-131">GetRow メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-131">GetRow Method</span></span>](imetadatatables-getrow-method.md)|<span data-ttu-id="21bc3-132">指定したテーブルインデックスにあるテーブル内の指定した行インデックスにある行を取得します。</span><span class="sxs-lookup"><span data-stu-id="21bc3-132">Gets the row at the specified row index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="21bc3-133">GetString メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-133">GetString Method</span></span>](imetadatatables-getstring-method.md)|<span data-ttu-id="21bc3-134">現在の参照スコープのテーブル列から、指定したインデックス位置にある文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="21bc3-134">Gets the string at the specified index from the table column in the current reference scope.</span></span>|  
|[<span data-ttu-id="21bc3-135">GetStringHeapSize メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-135">GetStringHeapSize Method</span></span>](imetadatatables-getstringheapsize-method.md)|<span data-ttu-id="21bc3-136">文字列ヒープのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="21bc3-136">Gets the size, in bytes, of the string heap.</span></span>|  
|[<span data-ttu-id="21bc3-137">GetTableIndex メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-137">GetTableIndex Method</span></span>](imetadatatables-gettableindex-method.md)|<span data-ttu-id="21bc3-138">指定したトークンによって参照されるテーブルのインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="21bc3-138">Gets the index for the table referenced by the specified token.</span></span>|  
|[<span data-ttu-id="21bc3-139">GetTableInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-139">GetTableInfo Method</span></span>](imetadatatables-gettableinfo-method.md)|<span data-ttu-id="21bc3-140">指定されたテーブルインデックスにあるテーブルの名前、行のサイズ、行数、列の数、およびキー列のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="21bc3-140">Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.</span></span>|  
|[<span data-ttu-id="21bc3-141">GetUserString メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-141">GetUserString Method</span></span>](imetadatatables-getuserstring-method.md)|<span data-ttu-id="21bc3-142">現在のスコープ内の文字列列にある、指定したインデックス位置にあるハードコーディングされた文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="21bc3-142">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>|  
|[<span data-ttu-id="21bc3-143">GetUserStringHeapSize メソッド</span><span class="sxs-lookup"><span data-stu-id="21bc3-143">GetUserStringHeapSize Method</span></span>](imetadatatables-getuserstringheapsize-method.md)|<span data-ttu-id="21bc3-144">ユーザー文字列ヒープのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="21bc3-144">Gets the size, in bytes, of the user string heap.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="21bc3-145">要件</span><span class="sxs-lookup"><span data-stu-id="21bc3-145">Requirements</span></span>  

 <span data-ttu-id="21bc3-146">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21bc3-146">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21bc3-147">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="21bc3-147">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="21bc3-148">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="21bc3-148">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="21bc3-149">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21bc3-149">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21bc3-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="21bc3-150">See also</span></span>

- [<span data-ttu-id="21bc3-151">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="21bc3-151">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="21bc3-152">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="21bc3-152">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
