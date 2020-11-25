---
title: ICorDebugAssembly::GetAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type:
- apiref
ms.openlocfilehash: 55a798bcc575aee3f309c35eb454a0675e0cbd97
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734076"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="53a17-102">ICorDebugAssembly::GetAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="53a17-102">ICorDebugAssembly::GetAppDomain Method</span></span>

<span data-ttu-id="53a17-103">このインスタンスを含むアプリケーションドメインへのインターフェイスポインターを取得し `ICorDebugAssembly` ます。</span><span class="sxs-lookup"><span data-stu-id="53a17-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53a17-104">構文</span><span class="sxs-lookup"><span data-stu-id="53a17-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53a17-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="53a17-105">Parameters</span></span>  

 `ppAppDomain`  
 <span data-ttu-id="53a17-106">入出力アプリケーションドメインを表す、のアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="53a17-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53a17-107">注釈</span><span class="sxs-lookup"><span data-stu-id="53a17-107">Remarks</span></span>  

 <span data-ttu-id="53a17-108">このアセンブリがシステムアセンブリの場合、は `GetAppDomain` null を返します。</span><span class="sxs-lookup"><span data-stu-id="53a17-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53a17-109">要件</span><span class="sxs-lookup"><span data-stu-id="53a17-109">Requirements</span></span>  

 <span data-ttu-id="53a17-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53a17-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53a17-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53a17-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53a17-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53a17-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53a17-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53a17-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
