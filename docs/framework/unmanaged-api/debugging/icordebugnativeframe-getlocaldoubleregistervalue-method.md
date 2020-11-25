---
title: ICorDebugNativeFrame::GetLocalDoubleRegisterValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalDoubleRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue method [.NET Framework debugging]
- GetLocalDoubleRegisterValue method [.NET Framework debugging]
ms.assetid: 1f838215-ac8a-434f-8ce6-03021d3098d9
topic_type:
- apiref
ms.openlocfilehash: 10f06fb04099ef947711bc7c5641e5a7f1fa36b7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695700"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a><span data-ttu-id="8bcae-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue メソッド</span><span class="sxs-lookup"><span data-stu-id="8bcae-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Method</span></span>

<span data-ttu-id="8bcae-103">このネイティブフレームの指定した2つのレジスタに格納されている引数またはローカル変数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="8bcae-103">Gets the value of an argument or local variable that is stored in the two specified registers for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bcae-104">構文</span><span class="sxs-lookup"><span data-stu-id="8bcae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bcae-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8bcae-105">Parameters</span></span>  

 `highWordReg`  
 <span data-ttu-id="8bcae-106">から値の上位ワードを含むレジスタを指定する "CorDebugRegister" 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="8bcae-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordReg`  
 <span data-ttu-id="8bcae-107">から `CorDebugRegister` 値の下位ワードを含むレジスタを指定する列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="8bcae-107">[in] A value of the `CorDebugRegister` enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="8bcae-108">からパラメーターによって参照されるバイナリメタデータシグネチャのサイズを指定する整数 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="8bcae-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="8bcae-109">から `PCCOR_SIGNATURE` 値の型のバイナリメタデータシグネチャを指す値。</span><span class="sxs-lookup"><span data-stu-id="8bcae-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="8bcae-110">入出力指定したレジスタに格納されている取得値を表す "ICorDebugValue" オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8bcae-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified registers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bcae-111">注釈</span><span class="sxs-lookup"><span data-stu-id="8bcae-111">Remarks</span></span>  

 <span data-ttu-id="8bcae-112">メソッドは、 `GetLocalDoubleRegisterValue` ネイティブフレームまたは just-in-time (JIT) でコンパイルされたフレームのどちらでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="8bcae-112">The `GetLocalDoubleRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bcae-113">要件</span><span class="sxs-lookup"><span data-stu-id="8bcae-113">Requirements</span></span>  

 <span data-ttu-id="8bcae-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8bcae-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bcae-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8bcae-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8bcae-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bcae-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bcae-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bcae-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bcae-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="8bcae-118">See also</span></span>
