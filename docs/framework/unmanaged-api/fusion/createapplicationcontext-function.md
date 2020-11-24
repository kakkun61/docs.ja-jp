---
title: CreateApplicationContext 関数
ms.date: 03/30/2017
api_name:
- CreateApplicationContext
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateApplicationContext
helpviewer_keywords:
- CreateApplicationContext function [.NET Framework fusion]
ms.assetid: 7bf8a141-b2c0-4058-9885-1cef7dcaa811
topic_type:
- apiref
ms.openlocfilehash: 9418be85f5b72bac8eed7f5ea4af4fc42439b01f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683233"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="11faa-102">CreateApplicationContext 関数</span><span class="sxs-lookup"><span data-stu-id="11faa-102">CreateApplicationContext Function</span></span>

<span data-ttu-id="11faa-103">この関数は、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="11faa-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11faa-104">構文</span><span class="sxs-lookup"><span data-stu-id="11faa-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="11faa-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="11faa-105">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="11faa-106">からフレンドリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="11faa-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="11faa-107">入出力アプリケーションコンテキストへのポインター。</span><span class="sxs-lookup"><span data-stu-id="11faa-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11faa-108">要件</span><span class="sxs-lookup"><span data-stu-id="11faa-108">Requirements</span></span>  

 <span data-ttu-id="11faa-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11faa-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11faa-110">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="11faa-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="11faa-111">**ライブラリ:** Fusion.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="11faa-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="11faa-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11faa-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11faa-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="11faa-113">See also</span></span>

- [<span data-ttu-id="11faa-114">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11faa-114">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="11faa-115">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="11faa-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="11faa-116">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="11faa-116">Global Assembly Cache</span></span>](../../app-domains/gac.md)
