---
title: HOST_TYPE 列挙型
ms.date: 03/30/2017
api_name:
- HOST_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- HOST_TYPE
helpviewer_keywords:
- HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type:
- apiref
ms.openlocfilehash: 31640ada28af8e35554b91d5931d427fbaa8dcbe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721856"
---
# <a name="host_type-enumeration"></a><span data-ttu-id="ceb9c-102">HOST_TYPE 列挙型</span><span class="sxs-lookup"><span data-stu-id="ceb9c-102">HOST_TYPE Enumeration</span></span>

<span data-ttu-id="ceb9c-103">アプリケーションを起動しているホストの種類を指定する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="ceb9c-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceb9c-104">構文</span><span class="sxs-lookup"><span data-stu-id="ceb9c-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="ceb9c-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="ceb9c-105">Members</span></span>  
  
|<span data-ttu-id="ceb9c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="ceb9c-106">Member</span></span>|<span data-ttu-id="ceb9c-107">説明</span><span class="sxs-lookup"><span data-stu-id="ceb9c-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="ceb9c-108">AppLaunch.exe からアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="ceb9c-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="ceb9c-109">部分的に信頼されたアプリケーションには、この値を使用します。</span><span class="sxs-lookup"><span data-stu-id="ceb9c-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="ceb9c-110">アプリケーションを直接起動します。</span><span class="sxs-lookup"><span data-stu-id="ceb9c-110">Launch the application directly.</span></span> <span data-ttu-id="ceb9c-111">つまり、アプリケーションを独自の .exe ファイルから起動します。</span><span class="sxs-lookup"><span data-stu-id="ceb9c-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="ceb9c-112">この値は、完全に信頼されたアプリケーションに使用します。</span><span class="sxs-lookup"><span data-stu-id="ceb9c-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="ceb9c-113">HOST_TYPE_APPLAUNCH と同じです。</span><span class="sxs-lookup"><span data-stu-id="ceb9c-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ceb9c-114">要件</span><span class="sxs-lookup"><span data-stu-id="ceb9c-114">Requirements</span></span>  

 <span data-ttu-id="ceb9c-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ceb9c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ceb9c-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ceb9c-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ceb9c-117">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ceb9c-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ceb9c-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ceb9c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceb9c-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="ceb9c-119">See also</span></span>

- [<span data-ttu-id="ceb9c-120">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="ceb9c-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
