---
title: EInitializeNewDomainFlags 列挙体
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
ms.openlocfilehash: 8350b507609e63c060cda08514200d386c37a6b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724326"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="5730b-102">EInitializeNewDomainFlags 列挙体</span><span class="sxs-lookup"><span data-stu-id="5730b-102">EInitializeNewDomainFlags Enumeration</span></span>

<span data-ttu-id="5730b-103">ホストがアプリケーションドメインの初期化に関する情報をランタイムに提供できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5730b-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5730b-104">構文</span><span class="sxs-lookup"><span data-stu-id="5730b-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="5730b-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="5730b-105">Members</span></span>  
  
|<span data-ttu-id="5730b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="5730b-106">Member</span></span>|<span data-ttu-id="5730b-107">説明</span><span class="sxs-lookup"><span data-stu-id="5730b-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="5730b-108">フラグなし。</span><span class="sxs-lookup"><span data-stu-id="5730b-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="5730b-109">ホストがメソッド内のアプリケーションドメインのセキュリティ状態に変更を加えないことを、共通言語ランタイム (CLR) に通知し <xref:System.AppDomainManager.InitializeNewDomain%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="5730b-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5730b-110">注釈</span><span class="sxs-lookup"><span data-stu-id="5730b-110">Remarks</span></span>  

 <span data-ttu-id="5730b-111">[ICLRDomainManager:: SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md)メソッドは、型のパラメーターを受け取り `EInitializeNewDomainFlags` ます。</span><span class="sxs-lookup"><span data-stu-id="5730b-111">The [ICLRDomainManager::SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5730b-112">要件</span><span class="sxs-lookup"><span data-stu-id="5730b-112">Requirements</span></span>  

 <span data-ttu-id="5730b-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5730b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5730b-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5730b-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5730b-115">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5730b-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5730b-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5730b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5730b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="5730b-117">See also</span></span>

- [<span data-ttu-id="5730b-118">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="5730b-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="5730b-119">SetAppDomainManagerType メソッド</span><span class="sxs-lookup"><span data-stu-id="5730b-119">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)
