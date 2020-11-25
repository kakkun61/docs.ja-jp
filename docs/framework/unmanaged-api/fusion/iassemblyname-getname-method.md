---
title: IAssemblyName::GetName メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetName
helpviewer_keywords:
- GetName method, IAssemblyName interface [.NET Framework debugging]
- IAssemblyName::GetName method [.NET Framework fusion]
ms.assetid: 1dee9781-1cf3-48a9-a376-d18ea1f73280
topic_type:
- apiref
ms.openlocfilehash: 58b8b83ce1db9338612cbaa01a0db0862cf1054e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727901"
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="0d65c-102">IAssemblyName::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="0d65c-102">IAssemblyName::GetName Method</span></span>

<span data-ttu-id="0d65c-103">この [IAssemblyName](iassemblyname-interface.md) オブジェクトによって参照されるアセンブリの単純な、暗号化されていない名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="0d65c-103">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d65c-104">構文</span><span class="sxs-lookup"><span data-stu-id="0d65c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d65c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0d65c-105">Parameters</span></span>  

 `lpcwBuffer`  
 <span data-ttu-id="0d65c-106">[入力、出力] `pwzName` Null 終端文字を含むワイド文字ののサイズ。</span><span class="sxs-lookup"><span data-stu-id="0d65c-106">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="0d65c-107">入出力参照されたアセンブリの名前を保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="0d65c-107">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d65c-108">要件</span><span class="sxs-lookup"><span data-stu-id="0d65c-108">Requirements</span></span>  

 <span data-ttu-id="0d65c-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d65c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d65c-110">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="0d65c-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0d65c-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d65c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d65c-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d65c-112">See also</span></span>

- [<span data-ttu-id="0d65c-113">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d65c-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
