---
title: IInstallReferenceEnum::GetNextInstallReferenceItem メソッド
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum.GetNextInstallReferenceItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type:
- apiref
ms.openlocfilehash: e093de7d2c2388274cbe9ebbe46084ee6ae3ff8c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721102"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="a5a33-102">IInstallReferenceEnum::GetNextInstallReferenceItem メソッド</span><span class="sxs-lookup"><span data-stu-id="a5a33-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>

<span data-ttu-id="a5a33-103">この[Iinstallreferenceitem](iinstallreferenceenum-interface.md)オブジェクトに格納されている次の[Iinstallreferenceitem](iinstallreferenceitem-interface.md)オブジェクトへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="a5a33-103">Gets a pointer to the next [IInstallReferenceItem](iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5a33-104">構文</span><span class="sxs-lookup"><span data-stu-id="a5a33-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5a33-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a5a33-105">Parameters</span></span>  

 `ppRefItem`  
 <span data-ttu-id="a5a33-106">入出力返された `IInstallReferenceItem` ポインター。</span><span class="sxs-lookup"><span data-stu-id="a5a33-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a5a33-107">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="a5a33-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="a5a33-108">`dwFlags` 0 (ゼロ) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5a33-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="a5a33-109">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="a5a33-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="a5a33-110">`pvReserved` null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5a33-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5a33-111">要件</span><span class="sxs-lookup"><span data-stu-id="a5a33-111">Requirements</span></span>  

 <span data-ttu-id="a5a33-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5a33-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5a33-113">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="a5a33-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a5a33-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5a33-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5a33-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5a33-115">See also</span></span>

- [<span data-ttu-id="a5a33-116">IInstallReferenceItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5a33-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="a5a33-117">IInstallReferenceEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5a33-117">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
