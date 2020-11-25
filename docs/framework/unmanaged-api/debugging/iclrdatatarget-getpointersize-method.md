---
title: ICLRDataTarget::GetPointerSize メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetPointerSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetPointerSize
helpviewer_keywords:
- GetPointerSize method [.NET Framework debugging]
- ICLRDataTarget::GetPointerSize method [.NET Framework debugging]
ms.assetid: 51d9f4a4-81a7-4527-8537-5212bdb05c70
topic_type:
- apiref
ms.openlocfilehash: 077aa50465d99c9098f26e67b3852feb0d399142
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703526"
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="fff7d-102">ICLRDataTarget::GetPointerSize メソッド</span><span class="sxs-lookup"><span data-stu-id="fff7d-102">ICLRDataTarget::GetPointerSize Method</span></span>

<span data-ttu-id="fff7d-103">ターゲットプロセスが使用するポインター型のサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="fff7d-103">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="fff7d-104">このメソッドは、共通言語ランタイムのデータアクセスサービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="fff7d-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fff7d-105">構文</span><span class="sxs-lookup"><span data-stu-id="fff7d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fff7d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fff7d-106">Parameters</span></span>  

 `pointerSize`  
 <span data-ttu-id="fff7d-107">入出力ターゲットプロセスのポインターのサイズ (バイト単位) を指定する整数値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="fff7d-107">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fff7d-108">注釈</span><span class="sxs-lookup"><span data-stu-id="fff7d-108">Remarks</span></span>  

 <span data-ttu-id="fff7d-109">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="fff7d-109">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fff7d-110">要件</span><span class="sxs-lookup"><span data-stu-id="fff7d-110">Requirements</span></span>  

 <span data-ttu-id="fff7d-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fff7d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fff7d-112">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="fff7d-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="fff7d-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fff7d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fff7d-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fff7d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fff7d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="fff7d-115">See also</span></span>

- [<span data-ttu-id="fff7d-116">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fff7d-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
