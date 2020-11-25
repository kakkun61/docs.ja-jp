---
title: ICeeGen::EmitString メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.EmitString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type:
- apiref
ms.openlocfilehash: b9c907868df31da8d995c6a6b86db258d395335d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715447"
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="af1d0-102">ICeeGen::EmitString メソッド</span><span class="sxs-lookup"><span data-stu-id="af1d0-102">ICeeGen::EmitString Method</span></span>

<span data-ttu-id="af1d0-103">指定した文字列をコードベースに出力します。</span><span class="sxs-lookup"><span data-stu-id="af1d0-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="af1d0-104">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="af1d0-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af1d0-105">構文</span><span class="sxs-lookup"><span data-stu-id="af1d0-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af1d0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="af1d0-106">Parameters</span></span>  

 `lpString`  
 <span data-ttu-id="af1d0-107">から出力する文字列。</span><span class="sxs-lookup"><span data-stu-id="af1d0-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="af1d0-108">入出力出力された文字列の相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="af1d0-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af1d0-109">要件</span><span class="sxs-lookup"><span data-stu-id="af1d0-109">Requirements</span></span>  

 <span data-ttu-id="af1d0-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af1d0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af1d0-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="af1d0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="af1d0-112">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="af1d0-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="af1d0-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af1d0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af1d0-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="af1d0-114">See also</span></span>

- [<span data-ttu-id="af1d0-115">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="af1d0-115">ICeeGen Interface</span></span>](iceegen-interface.md)
