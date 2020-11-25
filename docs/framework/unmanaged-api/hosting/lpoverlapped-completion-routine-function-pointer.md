---
title: LPOVERLAPPED_COMPLETION_ROUTINE 関数ポインター
ms.date: 03/30/2017
api_name:
- LPOVERLAPPED_COMPLETION_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type:
- apiref
ms.openlocfilehash: a3a45a13073cf422064d28554a274e068db6f517
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727511"
---
# <a name="lpoverlapped_completion_routine-function-pointer"></a><span data-ttu-id="e30ec-102">LPOVERLAPPED_COMPLETION_ROUTINE 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="e30ec-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>

<span data-ttu-id="e30ec-103">デバイスに対する重複 I/O (非同期 I/O) が完了したときに、ホストに通知する関数を指します。</span><span class="sxs-lookup"><span data-stu-id="e30ec-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="e30ec-104">この関数ポインターは .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="e30ec-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e30ec-105">構文</span><span class="sxs-lookup"><span data-stu-id="e30ec-105">Syntax</span></span>  
  
```cpp  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e30ec-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e30ec-106">Parameters</span></span>  

 `dwErrorCode`  
 <span data-ttu-id="e30ec-107">からデバイスが閉じられている場合は、エラーコードである値。それ以外の場合、この値は0です。</span><span class="sxs-lookup"><span data-stu-id="e30ec-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="e30ec-108">デバイスを閉じると、デバイスに対するすべての保留中の i/o が直ちに完了します。</span><span class="sxs-lookup"><span data-stu-id="e30ec-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="e30ec-109">からI/o 操作によって転送されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="e30ec-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="e30ec-110">からI/o 要求を完了するために使用される情報を格納する構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e30ec-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e30ec-111">注釈</span><span class="sxs-lookup"><span data-stu-id="e30ec-111">Remarks</span></span>  

 <span data-ttu-id="e30ec-112">`LPOVERLAPPED_COMPLETION_ROUTINE`ポイントがコールバック関数であり、ホストアプリケーションのライターによって実装されている必要がある関数。</span><span class="sxs-lookup"><span data-stu-id="e30ec-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="e30ec-113">コールバック関数を使用すると、ホストは、完了した i/o 要求を処理できます。</span><span class="sxs-lookup"><span data-stu-id="e30ec-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e30ec-114">要件</span><span class="sxs-lookup"><span data-stu-id="e30ec-114">Requirements</span></span>  

 <span data-ttu-id="e30ec-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e30ec-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e30ec-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e30ec-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e30ec-117">**ライブラリ:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="e30ec-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="e30ec-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e30ec-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e30ec-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="e30ec-119">See also</span></span>

- [<span data-ttu-id="e30ec-120">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="e30ec-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
