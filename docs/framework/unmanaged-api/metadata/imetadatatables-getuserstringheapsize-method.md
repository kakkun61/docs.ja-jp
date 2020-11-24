---
title: IMetaDataTables::GetUserStringHeapSize メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetUserStringHeapSize method [.NET Framework metadata]
- GetUserStringHeapSize method [.NET Framework metadata]
ms.assetid: cba9e4d6-9461-4420-9614-96ff7039ec9c
topic_type:
- apiref
ms.openlocfilehash: 048010f00f6581a29c6b1a3150bf5ae8822b5664
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672462"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="9f436-102">IMetaDataTables::GetUserStringHeapSize メソッド</span><span class="sxs-lookup"><span data-stu-id="9f436-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>

<span data-ttu-id="9f436-103">ユーザー文字列ヒープのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="9f436-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f436-104">構文</span><span class="sxs-lookup"><span data-stu-id="9f436-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f436-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f436-105">Parameters</span></span>  

 `pcbBlobs`  
 <span data-ttu-id="9f436-106">入出力ユーザー文字列ヒープのサイズ (バイト単位) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9f436-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f436-107">要件</span><span class="sxs-lookup"><span data-stu-id="9f436-107">Requirements</span></span>  

 <span data-ttu-id="9f436-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f436-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f436-109">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="9f436-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9f436-110">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f436-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9f436-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f436-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f436-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f436-112">See also</span></span>

- [<span data-ttu-id="9f436-113">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f436-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="9f436-114">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f436-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
