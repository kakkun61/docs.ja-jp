---
title: IMetaDataTables::GetString メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type:
- apiref
ms.openlocfilehash: 8ecaa003084064be1071a85aa726c38d773ec0b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672579"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="4a814-102">IMetaDataTables::GetString メソッド</span><span class="sxs-lookup"><span data-stu-id="4a814-102">IMetaDataTables::GetString Method</span></span>

<span data-ttu-id="4a814-103">現在の参照スコープのテーブル列から、指定したインデックス位置にある文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="4a814-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a814-104">構文</span><span class="sxs-lookup"><span data-stu-id="4a814-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a814-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4a814-105">Parameters</span></span>  

 `ixString`  
 <span data-ttu-id="4a814-106">から次の値の検索を開始する位置のインデックス。</span><span class="sxs-lookup"><span data-stu-id="4a814-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="4a814-107">入出力返された文字列値へのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4a814-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a814-108">要件</span><span class="sxs-lookup"><span data-stu-id="4a814-108">Requirements</span></span>  

 <span data-ttu-id="4a814-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a814-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a814-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="4a814-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4a814-111">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="4a814-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4a814-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a814-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a814-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a814-113">See also</span></span>

- [<span data-ttu-id="4a814-114">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4a814-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="4a814-115">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4a814-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
