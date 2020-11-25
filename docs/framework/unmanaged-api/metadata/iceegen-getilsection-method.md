---
title: ICeeGen::GetIlSection メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetIlSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetIlSection
helpviewer_keywords:
- GetIlSection method [.NET Framework metadata]
- ICeeGen::GetIlSection method [.NET Framework metadata]
ms.assetid: 6f2db2ca-203f-4ac3-9530-208642ca385e
topic_type:
- apiref
ms.openlocfilehash: c179d5e1ca976d8f425e7c408ceb663cba64f641
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715343"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="b443a-102">ICeeGen::GetIlSection メソッド</span><span class="sxs-lookup"><span data-stu-id="b443a-102">ICeeGen::GetIlSection Method</span></span>

<span data-ttu-id="b443a-103">指定したハンドルによって参照される中間言語コードベースのセクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="b443a-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="b443a-104">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b443a-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b443a-105">構文</span><span class="sxs-lookup"><span data-stu-id="b443a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b443a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b443a-106">Parameters</span></span>  

 `section`  
 <span data-ttu-id="b443a-107">から取得するセクションへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="b443a-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b443a-108">要件</span><span class="sxs-lookup"><span data-stu-id="b443a-108">Requirements</span></span>  

 <span data-ttu-id="b443a-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b443a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b443a-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="b443a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b443a-111">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="b443a-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b443a-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b443a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b443a-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b443a-113">See also</span></span>

- [<span data-ttu-id="b443a-114">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b443a-114">ICeeGen Interface</span></span>](iceegen-interface.md)
