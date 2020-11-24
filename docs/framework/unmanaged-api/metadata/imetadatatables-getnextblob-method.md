---
title: IMetaDataTables::GetNextBlob メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextBlob
helpviewer_keywords:
- IMetaDataTables::GetNextBlob method [.NET Framework metadata]
- GetNextBlob method [.NET Framework metadata]
ms.assetid: 017c8ab4-4c09-4754-9935-5b0b49cabecb
topic_type:
- apiref
ms.openlocfilehash: ba694f485d5a51870a1283b6ccbcb7b042a14501
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685644"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="23630-102">IMetaDataTables::GetNextBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="23630-102">IMetaDataTables::GetNextBlob Method</span></span>

<span data-ttu-id="23630-103">テーブル内の次のバイナリラージオブジェクト (BLOB) のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="23630-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23630-104">構文</span><span class="sxs-lookup"><span data-stu-id="23630-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23630-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="23630-105">Parameters</span></span>  

 `ixBlob`  
 <span data-ttu-id="23630-106">からBlob の列から返されるインデックス。</span><span class="sxs-lookup"><span data-stu-id="23630-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="23630-107">入出力次の BLOB のインデックスを指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="23630-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23630-108">要件</span><span class="sxs-lookup"><span data-stu-id="23630-108">Requirements</span></span>  

 <span data-ttu-id="23630-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23630-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23630-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="23630-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="23630-111">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="23630-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="23630-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23630-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23630-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="23630-113">See also</span></span>

- [<span data-ttu-id="23630-114">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23630-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="23630-115">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23630-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
