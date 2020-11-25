---
title: IAssemblyEnum::GetNextAssembly メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.GetNextAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type:
- apiref
ms.openlocfilehash: af43d9cf4d5aa790036a13d060fc6ccf113f335d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719893"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="1616b-102">IAssemblyEnum::GetNextAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="1616b-102">IAssemblyEnum::GetNextAssembly Method</span></span>

<span data-ttu-id="1616b-103">この[Iassemblyenum](iassemblyenum-interface.md)オブジェクトに格納されている次の[IAssemblyName](iassemblyname-interface.md)へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="1616b-103">Gets a pointer to the next [IAssemblyName](iassemblyname-interface.md) contained in this [IAssemblyEnum](iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1616b-104">構文</span><span class="sxs-lookup"><span data-stu-id="1616b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1616b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1616b-105">Parameters</span></span>  

 `pvReserved`  
 <span data-ttu-id="1616b-106">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="1616b-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="1616b-107">`pvReserved` null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1616b-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="1616b-108">入出力返された `IAssemblyName` ポインター。</span><span class="sxs-lookup"><span data-stu-id="1616b-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="1616b-109">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="1616b-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="1616b-110">`dwFlags` 0 (ゼロ) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1616b-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1616b-111">要件</span><span class="sxs-lookup"><span data-stu-id="1616b-111">Requirements</span></span>  

 <span data-ttu-id="1616b-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1616b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1616b-113">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="1616b-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1616b-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1616b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1616b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="1616b-115">See also</span></span>

- [<span data-ttu-id="1616b-116">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1616b-116">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="1616b-117">IAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1616b-117">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
