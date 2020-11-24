---
title: IMetaDataTables::GetNextUserString メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextUserString
helpviewer_keywords:
- GetNextUserString method [.NET Framework metadata]
- IMetaDataTables::GetNextUserString method [.NET Framework metadata]
ms.assetid: b7cb40ee-67b7-4f4e-8dcc-ee7ac8bc986b
topic_type:
- apiref
ms.openlocfilehash: bb53d980a7b2121854748d5117bc539fed125163
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680366"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="6d75c-102">IMetaDataTables::GetNextUserString メソッド</span><span class="sxs-lookup"><span data-stu-id="6d75c-102">IMetaDataTables::GetNextUserString Method</span></span>

<span data-ttu-id="6d75c-103">現在のテーブル列の次のハードコーディングされた文字列を含む行のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="6d75c-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d75c-104">構文</span><span class="sxs-lookup"><span data-stu-id="6d75c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d75c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6d75c-105">Parameters</span></span>  

 `ixUserString`  
 <span data-ttu-id="6d75c-106">から現在の文字列列からのインデックス値。</span><span class="sxs-lookup"><span data-stu-id="6d75c-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="6d75c-107">入出力列内の次の文字列の行インデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6d75c-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d75c-108">注釈</span><span class="sxs-lookup"><span data-stu-id="6d75c-108">Remarks</span></span>  

 <span data-ttu-id="6d75c-109">このメソッドは、一貫性のある結果を返さないため、使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6d75c-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="6d75c-110">GUID テーブルの詳細については、共通言語基盤 (CLI) のドキュメント (特に「パーティション II: メタデータの定義とセマンティクス」) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d75c-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="6d75c-111">ドキュメントはオンラインで入手できます。「 [Ecma C# および共通言語基盤の標準](../../../standard/components.md#applicable-standards) と [標準 ecma-335-共通言語基盤 (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d75c-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d75c-112">要件</span><span class="sxs-lookup"><span data-stu-id="6d75c-112">Requirements</span></span>  

 <span data-ttu-id="6d75c-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d75c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d75c-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="6d75c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d75c-115">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="6d75c-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d75c-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d75c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d75c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d75c-117">See also</span></span>

- [<span data-ttu-id="6d75c-118">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6d75c-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="6d75c-119">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6d75c-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
