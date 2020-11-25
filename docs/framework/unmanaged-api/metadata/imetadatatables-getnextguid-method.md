---
title: IMetaDataTables::GetNextGuid メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type:
- apiref
ms.openlocfilehash: 71dce539941f78feff3d5f89028d654cade25feb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727264"
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="8c959-102">IMetaDataTables::GetNextGuid メソッド</span><span class="sxs-lookup"><span data-stu-id="8c959-102">IMetaDataTables::GetNextGuid Method</span></span>

<span data-ttu-id="8c959-103">現在のテーブル列の次の GUID 値のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="8c959-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c959-104">構文</span><span class="sxs-lookup"><span data-stu-id="8c959-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c959-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c959-105">Parameters</span></span>  

 `ixGuid`  
 <span data-ttu-id="8c959-106">からGUID テーブルの列からのインデックス値。</span><span class="sxs-lookup"><span data-stu-id="8c959-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="8c959-107">入出力次の GUID 値のインデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c959-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c959-108">注釈</span><span class="sxs-lookup"><span data-stu-id="8c959-108">Remarks</span></span>  

  <span data-ttu-id="8c959-109">このメソッドは、一貫性のある結果を返さないため、使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8c959-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="8c959-110">GUID テーブルの詳細については、共通言語基盤 (CLI) のドキュメント (特に「パーティション II: メタデータの定義とセマンティクス」) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c959-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="8c959-111">ドキュメントはオンラインで入手できます。「 [Ecma C# および共通言語基盤の標準](../../../standard/components.md#applicable-standards) と [標準 ecma-335-共通言語基盤 (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c959-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c959-112">要件</span><span class="sxs-lookup"><span data-stu-id="8c959-112">Requirements</span></span>  

 <span data-ttu-id="8c959-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c959-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c959-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="8c959-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8c959-115">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="8c959-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8c959-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c959-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c959-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c959-117">See also</span></span>

- [<span data-ttu-id="8c959-118">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c959-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="8c959-119">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c959-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
