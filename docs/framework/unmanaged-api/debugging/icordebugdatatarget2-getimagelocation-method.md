---
title: ICorDebugDataTarget2::GetImageLocation メソッド
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
ms.openlocfilehash: c909b46a9bb70d23d1cd3a769ac24fcf58479308
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713796"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="df293-102">ICorDebugDataTarget2::GetImageLocation メソッド</span><span class="sxs-lookup"><span data-stu-id="df293-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>

<span data-ttu-id="df293-103">モジュールのベース アドレスからモジュールのパスを返します。</span><span class="sxs-lookup"><span data-stu-id="df293-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df293-104">構文</span><span class="sxs-lookup"><span data-stu-id="df293-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df293-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="df293-105">Parameters</span></span>  

 `baseAddress`  
 <span data-ttu-id="df293-106">からモジュールのベースアドレスを表す [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) 値。</span><span class="sxs-lookup"><span data-stu-id="df293-106">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="df293-107">[入力] モジュールのパスを受け取るバッファー内の文字数。</span><span class="sxs-lookup"><span data-stu-id="df293-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="df293-108">[出力] `szName` バッファーに書き込まれる文字数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="df293-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="df293-109">[出力] モジュールのパス。</span><span class="sxs-lookup"><span data-stu-id="df293-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df293-110">注釈</span><span class="sxs-lookup"><span data-stu-id="df293-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df293-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="df293-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df293-112">要件</span><span class="sxs-lookup"><span data-stu-id="df293-112">Requirements</span></span>  

 <span data-ttu-id="df293-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df293-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df293-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df293-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df293-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df293-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df293-116">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df293-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df293-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="df293-117">See also</span></span>

- [<span data-ttu-id="df293-118">ICorDebugDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="df293-118">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="df293-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="df293-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
