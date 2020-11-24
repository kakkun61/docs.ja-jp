---
title: ICorDebugAppDomain::GetName メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
ms.openlocfilehash: 501a4543940437bfe2a6cb0952aed8184107150c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672163"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="a4fe1-102">ICorDebugAppDomain::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="a4fe1-102">ICorDebugAppDomain::GetName Method</span></span>

<span data-ttu-id="a4fe1-103">アプリケーションドメインの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="a4fe1-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4fe1-104">構文</span><span class="sxs-lookup"><span data-stu-id="a4fe1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4fe1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a4fe1-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="a4fe1-106">[in] `szName` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="a4fe1-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="a4fe1-107">このメソッドをクエリモードにするには、この値を0に設定します。</span><span class="sxs-lookup"><span data-stu-id="a4fe1-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="a4fe1-108">入出力名前のサイズ、またはで実際に返された文字数へのポインター `szName` 。</span><span class="sxs-lookup"><span data-stu-id="a4fe1-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="a4fe1-109">クエリモードでは、この値によって、呼び出し元は、名前に割り当てるバッファーの大きさを知ることができます。</span><span class="sxs-lookup"><span data-stu-id="a4fe1-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="a4fe1-110">入出力アプリケーションドメインの名前を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="a4fe1-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4fe1-111">注釈</span><span class="sxs-lookup"><span data-stu-id="a4fe1-111">Remarks</span></span>  

 <span data-ttu-id="a4fe1-112">デバッガーは、 `GetName` メソッドを1回呼び出して、名前に必要なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="a4fe1-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="a4fe1-113">デバッガーによってバッファーが割り当てられ、メソッドが2回目に呼び出されてバッファーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a4fe1-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="a4fe1-114">名前のサイズを取得するための最初の呼び出しは、 *クエリモード* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="a4fe1-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4fe1-115">要件</span><span class="sxs-lookup"><span data-stu-id="a4fe1-115">Requirements</span></span>  

 <span data-ttu-id="a4fe1-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4fe1-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4fe1-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a4fe1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4fe1-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4fe1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4fe1-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4fe1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
