---
title: ICLRDataTarget::ReadVirtual メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.ReadVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::ReadVirtual
helpviewer_keywords:
- ReadVirtual method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::ReadVirtual method [.NET Framework debugging]
ms.assetid: da3769eb-1828-4aa1-b9ed-db4842136a43
topic_type:
- apiref
ms.openlocfilehash: 3455397345451cc0c39cc98a0ea4374eab8350a8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703383"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="636a7-102">ICLRDataTarget::ReadVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="636a7-102">ICLRDataTarget::ReadVirtual Method</span></span>

<span data-ttu-id="636a7-103">指定された仮想メモリアドレスから指定されたバッファーにデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="636a7-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="636a7-104">構文</span><span class="sxs-lookup"><span data-stu-id="636a7-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="636a7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="636a7-105">Parameters</span></span>  

 `address`  
 <span data-ttu-id="636a7-106">から仮想メモリアドレスを格納する CLRDATA_ADDRESS。</span><span class="sxs-lookup"><span data-stu-id="636a7-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="636a7-107">入出力データを受け取るバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="636a7-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="636a7-108">からバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="636a7-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="636a7-109">入出力返されたバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="636a7-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="636a7-110">要件</span><span class="sxs-lookup"><span data-stu-id="636a7-110">Requirements</span></span>  

 <span data-ttu-id="636a7-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="636a7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="636a7-112">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="636a7-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="636a7-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="636a7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="636a7-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="636a7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="636a7-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="636a7-115">See also</span></span>

- [<span data-ttu-id="636a7-116">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="636a7-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
