---
title: IMetaDataTables::GetNextString メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextString
helpviewer_keywords:
- IMetaDataTables::GetNextString method [.NET Framework metadata]
- GetNextString method [.NET Framework metadata]
ms.assetid: d9720428-c353-4f07-a7e8-899e106a1b37
topic_type:
- apiref
ms.openlocfilehash: b79dbdd64ac171d1bc4cd30b96ee76b4a853afb6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727251"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="76837-102">IMetaDataTables::GetNextString メソッド</span><span class="sxs-lookup"><span data-stu-id="76837-102">IMetaDataTables::GetNextString Method</span></span>

<span data-ttu-id="76837-103">現在のテーブル列の次の文字列のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="76837-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76837-104">構文</span><span class="sxs-lookup"><span data-stu-id="76837-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextString (
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76837-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="76837-105">Parameters</span></span>  

 `ixString`  
 <span data-ttu-id="76837-106">から文字列テーブル列からのインデックス値。</span><span class="sxs-lookup"><span data-stu-id="76837-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="76837-107">入出力列内の次の文字列のインデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="76837-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76837-108">要件</span><span class="sxs-lookup"><span data-stu-id="76837-108">Requirements</span></span>  

 <span data-ttu-id="76837-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76837-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76837-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="76837-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="76837-111">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="76837-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="76837-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76837-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76837-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="76837-113">See also</span></span>

- [<span data-ttu-id="76837-114">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="76837-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="76837-115">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="76837-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
