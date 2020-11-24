---
title: ICorPublishProcess インターフェイス
ms.date: 03/30/2017
api_name:
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
ms.openlocfilehash: 8ee59e9d416d1c53312e4fccb6953f20b03b29b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693087"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="cd7fc-102">ICorPublishProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd7fc-102">ICorPublishProcess Interface</span></span>

<span data-ttu-id="cd7fc-103">プロセスについて表示される情報にアクセスするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="cd7fc-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd7fc-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="cd7fc-104">Methods</span></span>  
  
|<span data-ttu-id="cd7fc-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="cd7fc-105">Method</span></span>|<span data-ttu-id="cd7fc-106">説明</span><span class="sxs-lookup"><span data-stu-id="cd7fc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd7fc-107">EnumAppDomains メソッド</span><span class="sxs-lookup"><span data-stu-id="cd7fc-107">EnumAppDomains Method</span></span>](icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="cd7fc-108">このによって参照されるプロセス内のアプリケーションドメインを格納している [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) インスタンスを取得し `ICorPublishProcess` ます。</span><span class="sxs-lookup"><span data-stu-id="cd7fc-108">Gets an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="cd7fc-109">GetDisplayName メソッド</span><span class="sxs-lookup"><span data-stu-id="cd7fc-109">GetDisplayName Method</span></span>](icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="cd7fc-110">このによって参照されるプロセスの実行可能ファイルの完全パスを取得し `ICorPublishProcess` ます。</span><span class="sxs-lookup"><span data-stu-id="cd7fc-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="cd7fc-111">GetProcessID メソッド</span><span class="sxs-lookup"><span data-stu-id="cd7fc-111">GetProcessID Method</span></span>](icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="cd7fc-112">このによって参照されるプロセスのオペレーティングシステム識別子を取得し `ICorPublishProcess` ます。</span><span class="sxs-lookup"><span data-stu-id="cd7fc-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="cd7fc-113">IsManaged メソッド</span><span class="sxs-lookup"><span data-stu-id="cd7fc-113">IsManaged Method</span></span>](icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="cd7fc-114">このによって参照されるプロセス `ICorPublishProcess` がマネージコードを実行していることがわかっているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="cd7fc-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd7fc-115">要件</span><span class="sxs-lookup"><span data-stu-id="cd7fc-115">Requirements</span></span>  

 <span data-ttu-id="cd7fc-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd7fc-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd7fc-117">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="cd7fc-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="cd7fc-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd7fc-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd7fc-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd7fc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd7fc-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd7fc-120">See also</span></span>

- [<span data-ttu-id="cd7fc-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd7fc-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="cd7fc-122">CorpubPublish コクラス</span><span class="sxs-lookup"><span data-stu-id="cd7fc-122">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
