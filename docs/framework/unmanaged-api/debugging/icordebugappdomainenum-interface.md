---
title: ICorDebugAppDomainEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum
helpviewer_keywords:
- ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: e9226e6e-ca2c-428e-bb38-0c099210f507
topic_type:
- apiref
ms.openlocfilehash: 37b6bcb48681704e3db47f81a51a9d21f00dfb37
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723195"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="79ff9-102">ICorDebugAppDomainEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79ff9-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="79ff9-103">`Next`列挙体の次の位置から始まる指定された数の値を返すメソッドを提供し `ICorDebugAppDomainEnum` ます。</span><span class="sxs-lookup"><span data-stu-id="79ff9-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="79ff9-104">このインターフェイスは、"ICorDebugEnum" のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="79ff9-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79ff9-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="79ff9-105">Methods</span></span>  
  
|<span data-ttu-id="79ff9-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="79ff9-106">Method</span></span>|<span data-ttu-id="79ff9-107">説明</span><span class="sxs-lookup"><span data-stu-id="79ff9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="79ff9-108">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="79ff9-108">Next Method</span></span>](icordebugappdomainenum-next-method.md)|<span data-ttu-id="79ff9-109">現在のカーソル位置から開始して、指定した数のアプリケーションドメインをコレクションから取得します。</span><span class="sxs-lookup"><span data-stu-id="79ff9-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79ff9-110">注釈</span><span class="sxs-lookup"><span data-stu-id="79ff9-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79ff9-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="79ff9-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79ff9-112">要件</span><span class="sxs-lookup"><span data-stu-id="79ff9-112">Requirements</span></span>  

 <span data-ttu-id="79ff9-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79ff9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79ff9-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79ff9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79ff9-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79ff9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79ff9-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79ff9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79ff9-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="79ff9-117">See also</span></span>

- [<span data-ttu-id="79ff9-118">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79ff9-118">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="79ff9-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="79ff9-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
