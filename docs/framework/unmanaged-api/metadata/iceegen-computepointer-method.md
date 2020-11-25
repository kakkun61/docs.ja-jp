---
title: ICeeGen::ComputePointer メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.ComputePointer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type:
- apiref
ms.openlocfilehash: 41a3b9c77fc766b2fa39b406dedbb3203cc97ad9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715473"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="3e5a3-102">ICeeGen::ComputePointer メソッド</span><span class="sxs-lookup"><span data-stu-id="3e5a3-102">ICeeGen::ComputePointer Method</span></span>

<span data-ttu-id="3e5a3-103">指定されたコードセクションのバッファーを決定します。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="3e5a3-104">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e5a3-105">構文</span><span class="sxs-lookup"><span data-stu-id="3e5a3-105">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e5a3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3e5a3-106">Parameters</span></span>  

 `section`  
 <span data-ttu-id="3e5a3-107">からバッファーを返す対象のコードセクション。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="3e5a3-108">からポインターを取得するメソッドの相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="3e5a3-109">入出力返されたバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e5a3-110">要件</span><span class="sxs-lookup"><span data-stu-id="3e5a3-110">Requirements</span></span>  

 <span data-ttu-id="3e5a3-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e5a3-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="3e5a3-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e5a3-113">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3e5a3-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e5a3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e5a3-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e5a3-115">See also</span></span>

- [<span data-ttu-id="3e5a3-116">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3e5a3-116">ICeeGen Interface</span></span>](iceegen-interface.md)
