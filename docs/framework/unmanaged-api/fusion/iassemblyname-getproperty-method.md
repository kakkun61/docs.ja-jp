---
title: IAssemblyName::GetProperty メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetProperty
helpviewer_keywords:
- IAssemblyName::GetProperty method [.NET Framework fusion]
- GetProperty method [.NET Framework fusion]
ms.assetid: e59fda62-77d5-4e37-89cb-ce7ae4627975
topic_type:
- apiref
ms.openlocfilehash: 3a6f19d9fc90972e767625fadf30cc4af50d9017
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727888"
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="1afbe-102">IAssemblyName::GetProperty メソッド</span><span class="sxs-lookup"><span data-stu-id="1afbe-102">IAssemblyName::GetProperty Method</span></span>

<span data-ttu-id="1afbe-103">指定したプロパティ識別子によって参照されるプロパティへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="1afbe-103">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1afbe-104">構文</span><span class="sxs-lookup"><span data-stu-id="1afbe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1afbe-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1afbe-105">Parameters</span></span>  

 `PropertyId`  
 <span data-ttu-id="1afbe-106">から要求されたプロパティの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="1afbe-106">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="1afbe-107">入出力返されたプロパティデータ。</span><span class="sxs-lookup"><span data-stu-id="1afbe-107">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="1afbe-108">[入力、出力]のサイズ (バイト単位) `pvProperty` 。</span><span class="sxs-lookup"><span data-stu-id="1afbe-108">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1afbe-109">要件</span><span class="sxs-lookup"><span data-stu-id="1afbe-109">Requirements</span></span>  

 <span data-ttu-id="1afbe-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1afbe-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1afbe-111">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="1afbe-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1afbe-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1afbe-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1afbe-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="1afbe-113">See also</span></span>

- [<span data-ttu-id="1afbe-114">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1afbe-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
