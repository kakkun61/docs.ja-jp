---
title: IInstallReferenceEnum インターフェイス
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum
helpviewer_keywords:
- IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type:
- apiref
ms.openlocfilehash: f56a9049cd4b503124abe9dd4866dc91779e268e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721063"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="91007-102">IInstallReferenceEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="91007-102">IInstallReferenceEnum Interface</span></span>

<span data-ttu-id="91007-103">グローバルアセンブリキャッシュにインストールされている参照アセンブリの列挙子を表します。</span><span class="sxs-lookup"><span data-stu-id="91007-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91007-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="91007-104">Syntax</span></span>  
  
```cpp  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="91007-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="91007-105">Methods</span></span>  
  
|<span data-ttu-id="91007-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="91007-106">Method</span></span>|<span data-ttu-id="91007-107">説明</span><span class="sxs-lookup"><span data-stu-id="91007-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="91007-108">GetNextInstallReferenceItem メソッド</span><span class="sxs-lookup"><span data-stu-id="91007-108">GetNextInstallReferenceItem Method</span></span>](iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="91007-109">このに格納されている次のへのポインターを取得し `IInstallReferenceItem` `IInstallReferenceEnum` ます。</span><span class="sxs-lookup"><span data-stu-id="91007-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="91007-110">要件</span><span class="sxs-lookup"><span data-stu-id="91007-110">Requirements</span></span>  

 <span data-ttu-id="91007-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91007-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91007-112">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="91007-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="91007-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91007-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91007-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="91007-114">See also</span></span>

- [<span data-ttu-id="91007-115">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="91007-115">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="91007-116">IInstallReferenceItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="91007-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
