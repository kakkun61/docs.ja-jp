---
title: ICeeGen::GetIMapTokenIface メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetIMapTokenIface
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetIMapTokenIface
helpviewer_keywords:
- GetIMapTokenIface method [.NET Framework metadata]
- ICeeGen::GetIMapTokenIface method [.NET Framework metadata]
ms.assetid: 847a5531-c37d-49cd-8844-9e54b5d86cf7
topic_type:
- apiref
ms.openlocfilehash: 079a599ff87146c4eed4b15d57696338fb25f530
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674310"
---
# <a name="iceegengetimaptokeniface-method"></a><span data-ttu-id="eed1e-102">ICeeGen::GetIMapTokenIface メソッド</span><span class="sxs-lookup"><span data-stu-id="eed1e-102">ICeeGen::GetIMapTokenIface Method</span></span>

<span data-ttu-id="eed1e-103">指定したトークンによって参照されるインターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="eed1e-103">Gets the interface referenced by the specified token.</span></span>  
  
 <span data-ttu-id="eed1e-104">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="eed1e-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eed1e-105">構文</span><span class="sxs-lookup"><span data-stu-id="eed1e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIMapTokenIface (  
    [in, out] IUnknown   **pIMapToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eed1e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eed1e-106">Parameters</span></span>  

 `pIMapToken`  
 <span data-ttu-id="eed1e-107">[入力、出力]返されるインターフェイスのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="eed1e-107">[in, out] The metadata token for the interface to be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eed1e-108">要件</span><span class="sxs-lookup"><span data-stu-id="eed1e-108">Requirements</span></span>  

 <span data-ttu-id="eed1e-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eed1e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eed1e-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="eed1e-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eed1e-111">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="eed1e-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eed1e-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eed1e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eed1e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="eed1e-113">See also</span></span>

- [<span data-ttu-id="eed1e-114">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eed1e-114">ICeeGen Interface</span></span>](iceegen-interface.md)
