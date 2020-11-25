---
title: ITypeNameFactory::ParseTypeName メソッド
ms.date: 03/30/2017
api_name:
- ITypeNameFactory.ParseTypeName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ParseTypeName
helpviewer_keywords:
- ITypeNameFactory::ParseTypeName method [.NET Framework hosting]
- ParseTypeName method [.NET Framework hosting]
ms.assetid: 13c9f063-371c-4911-a5e7-e1e0b88ae382
topic_type:
- apiref
ms.openlocfilehash: 2b4d22fac7125ad113aaef5b093396a065f682c1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728720"
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="ea846-102">ITypeNameFactory::ParseTypeName メソッド</span><span class="sxs-lookup"><span data-stu-id="ea846-102">ITypeNameFactory::ParseTypeName Method</span></span>

<span data-ttu-id="ea846-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="ea846-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea846-104">構文</span><span class="sxs-lookup"><span data-stu-id="ea846-104">Syntax</span></span>  
  
```cpp  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="ea846-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="ea846-105">Requirements</span></span>  

 <span data-ttu-id="ea846-106">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea846-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea846-107">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ea846-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ea846-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ea846-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea846-109">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea846-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea846-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea846-110">See also</span></span>

- [<span data-ttu-id="ea846-111">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea846-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
