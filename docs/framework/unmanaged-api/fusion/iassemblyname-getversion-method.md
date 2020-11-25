---
title: IAssemblyName::GetVersion メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetVersion
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetVersion
helpviewer_keywords:
- IAssemblyName::GetVersion method [.NET Framework fusion]
- GetVersion method, IAssemblyName interface [.NET Framework fusion]
ms.assetid: 42230928-2c33-41fd-9519-d96efef6c7af
topic_type:
- apiref
ms.openlocfilehash: 6f37979c7a4873a7751db0296dc7d485c3444561
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715902"
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="1df17-102">IAssemblyName::GetVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="1df17-102">IAssemblyName::GetVersion Method</span></span>

<span data-ttu-id="1df17-103">この [IAssemblyName](iassemblyname-interface.md) オブジェクトによって参照されるアセンブリのバージョン情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="1df17-103">Gets the version information for the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1df17-104">構文</span><span class="sxs-lookup"><span data-stu-id="1df17-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1df17-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1df17-105">Parameters</span></span>  

 `pdwVersionHi`  
 <span data-ttu-id="1df17-106">入出力バージョンの上位32ビット。</span><span class="sxs-lookup"><span data-stu-id="1df17-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="1df17-107">入出力バージョンの下位32ビット。</span><span class="sxs-lookup"><span data-stu-id="1df17-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1df17-108">要件</span><span class="sxs-lookup"><span data-stu-id="1df17-108">Requirements</span></span>  

 <span data-ttu-id="1df17-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1df17-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1df17-110">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="1df17-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1df17-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1df17-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1df17-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="1df17-112">See also</span></span>

- [<span data-ttu-id="1df17-113">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1df17-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
