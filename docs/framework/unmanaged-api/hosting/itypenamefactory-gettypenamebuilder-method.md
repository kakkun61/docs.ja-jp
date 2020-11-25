---
title: ITypeNameFactory::GetTypeNameBuilder メソッド
ms.date: 03/30/2017
api_name:
- ITypeNameFactory.GetTypeNameBuilder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetTypeNameBuilder
helpviewer_keywords:
- ITypeNameFactory::GetTypeNameBuilder method [.NET Framework hosting]
- GetTypeNameBuilder method [.NET Framework hosting]
ms.assetid: c682f744-996e-43c7-a9ea-c57cbc755398
topic_type:
- apiref
ms.openlocfilehash: 67e5e66ae88cfcc777d631268ed555bcb4eb31b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728746"
---
# <a name="itypenamefactorygettypenamebuilder-method"></a><span data-ttu-id="be593-102">ITypeNameFactory::GetTypeNameBuilder メソッド</span><span class="sxs-lookup"><span data-stu-id="be593-102">ITypeNameFactory::GetTypeNameBuilder Method</span></span>

<span data-ttu-id="be593-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="be593-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be593-104">構文</span><span class="sxs-lookup"><span data-stu-id="be593-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeNameBuilder (  
    [out, retval] ITypeNameBuilder** ppTypeBuilder  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="be593-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="be593-105">Requirements</span></span>  

 <span data-ttu-id="be593-106">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be593-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be593-107">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="be593-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="be593-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="be593-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be593-109">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be593-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be593-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="be593-110">See also</span></span>

- [<span data-ttu-id="be593-111">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="be593-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
