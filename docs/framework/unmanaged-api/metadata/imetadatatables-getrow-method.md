---
title: IMetaDataTables::GetRow メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
ms.openlocfilehash: 01c4c1734aa0701f787a2b73787e9e4781901d42
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672657"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="f8a84-102">IMetaDataTables::GetRow メソッド</span><span class="sxs-lookup"><span data-stu-id="f8a84-102">IMetaDataTables::GetRow Method</span></span>

<span data-ttu-id="f8a84-103">指定したテーブルインデックスにあるテーブル内の指定した行インデックスにある行を取得します。</span><span class="sxs-lookup"><span data-stu-id="f8a84-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8a84-104">構文</span><span class="sxs-lookup"><span data-stu-id="f8a84-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8a84-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f8a84-105">Parameters</span></span>  

 `ixTbl`  
 <span data-ttu-id="f8a84-106">から行の取得元となるテーブルのインデックス。</span><span class="sxs-lookup"><span data-stu-id="f8a84-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="f8a84-107">から取得する行のインデックス。</span><span class="sxs-lookup"><span data-stu-id="f8a84-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="f8a84-108">入出力行へのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f8a84-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8a84-109">注釈</span><span class="sxs-lookup"><span data-stu-id="f8a84-109">Remarks</span></span>  

  <span data-ttu-id="f8a84-110">このメソッドは、一貫性のある結果を返さないため、使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f8a84-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="f8a84-111">GUID テーブルの詳細については、共通言語基盤 (CLI) のドキュメント (特に「パーティション II: メタデータの定義とセマンティクス」) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8a84-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="f8a84-112">ドキュメントはオンラインで入手できます。「 [Ecma C# および共通言語基盤の標準](../../../standard/components.md#applicable-standards) と [標準 ecma-335-共通言語基盤 (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8a84-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8a84-113">要件</span><span class="sxs-lookup"><span data-stu-id="f8a84-113">Requirements</span></span>  

 <span data-ttu-id="f8a84-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8a84-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8a84-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="f8a84-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f8a84-116">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="f8a84-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f8a84-117">**.NET Framework のバージョン**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8a84-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8a84-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8a84-118">See also</span></span>

- [<span data-ttu-id="f8a84-119">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8a84-119">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="f8a84-120">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8a84-120">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
