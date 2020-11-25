---
title: ICeeGen::GetStringSection メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetStringSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetStringSection
helpviewer_keywords:
- ICeeGen::GetStringSection method [.NET Framework metadata]
- GetStringSection method [.NET Framework metadata]
ms.assetid: a2267d39-69d1-4de1-bf37-f752cafacc71
topic_type:
- apiref
ms.openlocfilehash: bd284bced625de39791377a9248796ca3dd76f5c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722922"
---
# <a name="iceegengetstringsection-method"></a><span data-ttu-id="8c738-102">ICeeGen::GetStringSection メソッド</span><span class="sxs-lookup"><span data-stu-id="8c738-102">ICeeGen::GetStringSection Method</span></span>

<span data-ttu-id="8c738-103">指定したハンドルによって参照されるコードセクションの文字列表現を取得します。</span><span class="sxs-lookup"><span data-stu-id="8c738-103">Gets a string representation of the code section referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="8c738-104">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="8c738-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c738-105">構文</span><span class="sxs-lookup"><span data-stu-id="8c738-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringSection (  
    [in, out] HCEESECTION     *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c738-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c738-106">Parameters</span></span>  

 `section`  
 <span data-ttu-id="8c738-107">[入力、出力]コードセクションへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="8c738-107">[in, out] The handle to the code section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c738-108">要件</span><span class="sxs-lookup"><span data-stu-id="8c738-108">Requirements</span></span>  

 <span data-ttu-id="8c738-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c738-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c738-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="8c738-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8c738-111">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="8c738-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8c738-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c738-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c738-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c738-113">See also</span></span>

- [<span data-ttu-id="8c738-114">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c738-114">ICeeGen Interface</span></span>](iceegen-interface.md)
