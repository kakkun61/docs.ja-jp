---
title: ICorDebugRemoteTarget インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget
helpviewer_keywords:
- ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type:
- apiref
ms.openlocfilehash: 4212597b5ba43f0e4767aa585ca28a011e73e07a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711989"
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="c11df-102">ICorDebugRemoteTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c11df-102">ICorDebugRemoteTarget Interface</span></span>

<span data-ttu-id="c11df-103">開発者が共通言語ランタイム (CLR: Common Language Runtime) 環境で Silverlight ベース アプリケーションをデバッグできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="c11df-103">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c11df-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c11df-104">Syntax</span></span>  
  
```cpp  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c11df-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c11df-105">Methods</span></span>  
  
|<span data-ttu-id="c11df-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="c11df-106">Method</span></span>|<span data-ttu-id="c11df-107">説明</span><span class="sxs-lookup"><span data-stu-id="c11df-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c11df-108">ICorDebugRemoteTarget::GetHostName メソッド</span><span class="sxs-lookup"><span data-stu-id="c11df-108">ICorDebugRemoteTarget::GetHostName Method</span></span>](icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="c11df-109">リモート マシンのホスト名または IP アドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="c11df-109">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c11df-110">注釈</span><span class="sxs-lookup"><span data-stu-id="c11df-110">Remarks</span></span>  

 <span data-ttu-id="c11df-111">Windows 95、Windows 98、Windows ME、または x86 以外のプラットフォーム (IA-64、AMD64 など) では、混合モード (つまり、マネージド コードとネイティブ コード) デバッグはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c11df-111">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c11df-112">要件</span><span class="sxs-lookup"><span data-stu-id="c11df-112">Requirements</span></span>  

 <span data-ttu-id="c11df-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c11df-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c11df-114">**ヘッダー:** CorDebug .idl</span><span class="sxs-lookup"><span data-stu-id="c11df-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="c11df-115">**Library:** : corguids .lib</span><span class="sxs-lookup"><span data-stu-id="c11df-115">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="c11df-116">**.NET Framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="c11df-116">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c11df-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="c11df-117">See also</span></span>

- [<span data-ttu-id="c11df-118">ICorDebugRemote インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c11df-118">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="c11df-119">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c11df-119">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="c11df-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c11df-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
