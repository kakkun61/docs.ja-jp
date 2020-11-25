---
title: ICeeGen::GetMethodBuffer メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
ms.openlocfilehash: e9c2dab9f30be6e5eea8f6570b297f8df11b6fe6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715330"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="0e470-102">ICeeGen::GetMethodBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="0e470-102">ICeeGen::GetMethodBuffer Method</span></span>

<span data-ttu-id="0e470-103">指定した相対仮想アドレスで、メソッドの適切なサイズのバッファーを取得します。</span><span class="sxs-lookup"><span data-stu-id="0e470-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="0e470-104">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="0e470-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e470-105">構文</span><span class="sxs-lookup"><span data-stu-id="0e470-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e470-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0e470-106">Parameters</span></span>  

 `RVA`  
 <span data-ttu-id="0e470-107">からバッファーを返すメソッドの相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="0e470-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="0e470-108">入出力返されたバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0e470-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e470-109">要件</span><span class="sxs-lookup"><span data-stu-id="0e470-109">Requirements</span></span>  

 <span data-ttu-id="0e470-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e470-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e470-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="0e470-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e470-112">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="0e470-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0e470-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e470-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e470-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e470-114">See also</span></span>

- [<span data-ttu-id="0e470-115">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e470-115">ICeeGen Interface</span></span>](iceegen-interface.md)
