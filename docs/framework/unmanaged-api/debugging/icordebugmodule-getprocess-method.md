---
title: ICorDebugModule::GetProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetProcess method [.NET Framework debugging]
ms.assetid: 5e13446c-0271-446c-924a-9072c0e6eeae
topic_type:
- apiref
ms.openlocfilehash: 8f4b9e73e0d716561dd64bc0df702d835e0eee06
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709961"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="68eca-102">ICorDebugModule::GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="68eca-102">ICorDebugModule::GetProcess Method</span></span>

<span data-ttu-id="68eca-103">このモジュールの格納プロセスを取得します。</span><span class="sxs-lookup"><span data-stu-id="68eca-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68eca-104">構文</span><span class="sxs-lookup"><span data-stu-id="68eca-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68eca-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="68eca-105">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="68eca-106">入出力このモジュールを含んでいるプロセスを表す、オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="68eca-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68eca-107">要件</span><span class="sxs-lookup"><span data-stu-id="68eca-107">Requirements</span></span>  

 <span data-ttu-id="68eca-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68eca-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68eca-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68eca-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68eca-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68eca-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68eca-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68eca-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
