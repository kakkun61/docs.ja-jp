---
title: ICorDebugNativeFrame::GetLocalMemoryRegisterValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue method [.NET Framework debugging]
- GetLocalMemoryRegisterValue method
ms.assetid: 33a19f6e-1029-4d53-af64-19591c6e58ee
topic_type:
- apiref
ms.openlocfilehash: 15485ac94ed9074baacc4fd2662a04bdcefcf1e7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709324"
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a><span data-ttu-id="6ed04-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue メソッド</span><span class="sxs-lookup"><span data-stu-id="6ed04-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Method</span></span>

<span data-ttu-id="6ed04-103">引数またはローカル変数の値を取得します。この値は、このネイティブフレームについて、指定したレジスタとメモリ位置にそれぞれ、下位ワードと上位ワードが格納されます。</span><span class="sxs-lookup"><span data-stu-id="6ed04-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the specified register and memory location, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ed04-104">構文</span><span class="sxs-lookup"><span data-stu-id="6ed04-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ed04-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6ed04-105">Parameters</span></span>  

 `highWordAddress`  
 <span data-ttu-id="6ed04-106">から `CORDB_ADDRESS` 値の上位ワードを格納しているメモリ位置を指定する値。</span><span class="sxs-lookup"><span data-stu-id="6ed04-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the high word of the value.</span></span>  
  
 `lowWordRegister`  
 <span data-ttu-id="6ed04-107">から値の下位ワードを含むレジスタを指定する "CorDebugRegister" 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="6ed04-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="6ed04-108">からパラメーターによって参照されるバイナリメタデータシグネチャのサイズを指定する整数 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="6ed04-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="6ed04-109">から `PCCOR_SIGNATURE` 値の型のバイナリメタデータシグネチャを指す値。</span><span class="sxs-lookup"><span data-stu-id="6ed04-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="6ed04-110">入出力指定されたレジスタおよびメモリ位置に格納されている取得値を表す "ICorDebugValue" オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6ed04-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ed04-111">要件</span><span class="sxs-lookup"><span data-stu-id="6ed04-111">Requirements</span></span>  

 <span data-ttu-id="6ed04-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ed04-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ed04-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6ed04-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ed04-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ed04-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ed04-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ed04-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ed04-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ed04-116">See also</span></span>
