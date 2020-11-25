---
title: RUNTIME_INFO_FLAGS 列挙型
ms.date: 03/30/2017
api_name:
- RUNTIME_INFO_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RUNTIME_INFO_FLAGS
helpviewer_keywords:
- RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type:
- apiref
ms.openlocfilehash: 6f4fbb40053628d60ba7f094fcb5d50a94d63e1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729942"
---
# <a name="runtime_info_flags-enumeration"></a><span data-ttu-id="beac7-102">RUNTIME_INFO_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="beac7-102">RUNTIME_INFO_FLAGS Enumeration</span></span>

<span data-ttu-id="beac7-103">共通言語ランタイム (CLR) に関する情報を返す必要があるかどうかを示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="beac7-103">Contains values that indicate what information about the common language runtime (CLR) should be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beac7-104">構文</span><span class="sxs-lookup"><span data-stu-id="beac7-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="beac7-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="beac7-105">Members</span></span>  
  
|<span data-ttu-id="beac7-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="beac7-106">Member</span></span>|<span data-ttu-id="beac7-107">説明</span><span class="sxs-lookup"><span data-stu-id="beac7-107">Description</span></span>|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|<span data-ttu-id="beac7-108">ディレクトリ情報を含めないことを示します。</span><span class="sxs-lookup"><span data-stu-id="beac7-108">Indicates that directory information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|<span data-ttu-id="beac7-109">バージョン情報を含めないことを示します。</span><span class="sxs-lookup"><span data-stu-id="beac7-109">Indicates that version information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|<span data-ttu-id="beac7-110">エラーが発生したときにエラーダイアログボックスを表示しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="beac7-110">Indicates that an error dialog box should not be shown upon failure.</span></span>|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|<span data-ttu-id="beac7-111">SEM_FAILCRITICALERRORS フラグを使用して [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) 関数を呼び出した場合の効果をオーバーライドする必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="beac7-111">Indicates that the effects of calling the [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) function with the SEM_FAILCRITICALERRORS flag should be overridden.</span></span> <span data-ttu-id="beac7-112">つまり、エラーが発生すると、抑制されるのではなく、インストールのダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="beac7-112">That is, an installation dialog box should be shown upon failure, instead of being suppressed.</span></span>|  
|`RUNTIME_INFO_REQUEST_AMD64`|<span data-ttu-id="beac7-113">AMD-64 互換バージョンのランタイムに関する情報の要求を示します。</span><span class="sxs-lookup"><span data-stu-id="beac7-113">Indicates a request for information about an AMD-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_IA64`|<span data-ttu-id="beac7-114">IA-64 互換バージョンのランタイムに関する情報の要求を示します。</span><span class="sxs-lookup"><span data-stu-id="beac7-114">Indicates a request for information about an IA-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_X86`|<span data-ttu-id="beac7-115">ランタイムの x86 互換バージョンに関する情報の要求を示します。</span><span class="sxs-lookup"><span data-stu-id="beac7-115">Indicates a request for information about an x86-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_UPGRADE_VERSION`|<span data-ttu-id="beac7-116">バージョンのアップグレード情報を含める必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="beac7-116">Indicates that version upgrade information should be included.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="beac7-117">注釈</span><span class="sxs-lookup"><span data-stu-id="beac7-117">Remarks</span></span>  

 <span data-ttu-id="beac7-118">次のプラットフォームアーキテクチャフラグは一度に1つだけ指定でき、組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="beac7-118">The following platform architecture flags can be specified only one at a time and cannot be combined:</span></span>  
  
- <span data-ttu-id="beac7-119">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="beac7-119">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="beac7-120">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="beac7-120">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="beac7-121">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="beac7-121">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="beac7-122">要件</span><span class="sxs-lookup"><span data-stu-id="beac7-122">Requirements</span></span>  

 <span data-ttu-id="beac7-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="beac7-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="beac7-124">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="beac7-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="beac7-125">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="beac7-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="beac7-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="beac7-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beac7-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="beac7-127">See also</span></span>

- [<span data-ttu-id="beac7-128">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="beac7-128">Hosting Enumerations</span></span>](hosting-enumerations.md)
