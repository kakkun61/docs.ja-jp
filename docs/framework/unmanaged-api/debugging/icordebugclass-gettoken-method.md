---
title: ICorDebugClass::GetToken メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetToken
helpviewer_keywords:
- GetToken method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetToken method [.NET Framework debugging]
ms.assetid: ee5c848a-eac4-4462-b07a-07ccd76a75df
topic_type:
- apiref
ms.openlocfilehash: 59f450117d1a52ce7b900d9d67330fc98281afa0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728421"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="153be-102">ICorDebugClass::GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="153be-102">ICorDebugClass::GetToken Method</span></span>

<span data-ttu-id="153be-103">`TypeDef`このクラスの定義を参照するメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="153be-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="153be-104">構文</span><span class="sxs-lookup"><span data-stu-id="153be-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="153be-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="153be-105">Parameters</span></span>  

 `pTypeDef`  
 <span data-ttu-id="153be-106">入出力 `mdTypeDef` このクラスの定義を参照するトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="153be-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="153be-107">要件</span><span class="sxs-lookup"><span data-stu-id="153be-107">Requirements</span></span>  

 <span data-ttu-id="153be-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="153be-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="153be-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="153be-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="153be-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="153be-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="153be-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="153be-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="153be-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="153be-112">See also</span></span>

- [<span data-ttu-id="153be-113">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="153be-113">Metadata Interfaces</span></span>](../metadata/metadata-interfaces.md)
