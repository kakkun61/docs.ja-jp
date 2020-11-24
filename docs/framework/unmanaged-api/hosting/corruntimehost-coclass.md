---
title: CorRuntimeHost コクラス
ms.date: 03/30/2017
api_name:
- CorRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRuntimeHost
helpviewer_keywords:
- CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type:
- apiref
ms.openlocfilehash: cd4e675b4ba50b47146428d204c28cc943c23c69
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688004"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="6585d-102">CorRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="6585d-102">CorRuntimeHost Coclass</span></span>

<span data-ttu-id="6585d-103">共通言語ランタイムによって実行されるアプリケーションを管理するためのインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="6585d-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6585d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6585d-104">Syntax</span></span>  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="6585d-105">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6585d-105">Interfaces</span></span>  
  
|<span data-ttu-id="6585d-106">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6585d-106">Interface</span></span>|<span data-ttu-id="6585d-107">説明</span><span class="sxs-lookup"><span data-stu-id="6585d-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="6585d-108">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6585d-108">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)|<span data-ttu-id="6585d-109">共通言語ランタイム (CLR: common language runtime) を構成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="6585d-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="6585d-110">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6585d-110">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)|<span data-ttu-id="6585d-111">ホストが共通言語ランタイムを明示的に開始または停止したり、アプリケーションドメインを作成および構成したり、既定のドメインにアクセスしたり、プロセスで実行されているすべてのドメインを列挙したりできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="6585d-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="6585d-112">IDebuggerInfo Iインターフェイス</span><span class="sxs-lookup"><span data-stu-id="6585d-112">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)|<span data-ttu-id="6585d-113">デバッグサービスの状態に関する情報を取得するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="6585d-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="6585d-114">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6585d-114">IGCHost Interface</span></span>](igchost-interface.md)|<span data-ttu-id="6585d-115">ガベージコレクションシステムに関する情報を取得し、ガベージコレクションのいくつかの側面を制御するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="6585d-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="6585d-116">IValidator</span><span class="sxs-lookup"><span data-stu-id="6585d-116">"IValidator"</span></span>|<span data-ttu-id="6585d-117">ポータブル実行可能イメージを検証し、検証エラーの詳細なレポートを作成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="6585d-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6585d-118">要件</span><span class="sxs-lookup"><span data-stu-id="6585d-118">Requirements</span></span>  

 <span data-ttu-id="6585d-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6585d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6585d-120">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6585d-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="6585d-121">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6585d-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6585d-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6585d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6585d-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="6585d-123">See also</span></span>

- [<span data-ttu-id="6585d-124">ホスト コクラス</span><span class="sxs-lookup"><span data-stu-id="6585d-124">Hosting Coclasses</span></span>](hosting-coclasses.md)
