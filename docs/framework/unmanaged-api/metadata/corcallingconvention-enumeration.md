---
title: CorCallingConvention 列挙型
ms.date: 03/30/2017
api_name:
- CorCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallingConvention
helpviewer_keywords:
- CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type:
- apiref
ms.openlocfilehash: c9b20500a4a9e4649a938e00e3b059d1395da1d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718931"
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="5da3b-102">CorCallingConvention 列挙型</span><span class="sxs-lookup"><span data-stu-id="5da3b-102">CorCallingConvention Enumeration</span></span>

<span data-ttu-id="5da3b-103">マネージド コードで作成される呼び出し規則のタイプを記述する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="5da3b-103">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5da3b-104">構文</span><span class="sxs-lookup"><span data-stu-id="5da3b-104">Syntax</span></span>  
  
```cpp  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="5da3b-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="5da3b-105">Members</span></span>  
  
|<span data-ttu-id="5da3b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="5da3b-106">Member</span></span>|<span data-ttu-id="5da3b-107">説明</span><span class="sxs-lookup"><span data-stu-id="5da3b-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="5da3b-108">既定の呼び出し規約を示します。</span><span class="sxs-lookup"><span data-stu-id="5da3b-108">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="5da3b-109">メソッドが可変個のパラメーターを受け取ることを示します。</span><span class="sxs-lookup"><span data-stu-id="5da3b-109">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="5da3b-110">は、フィールドへの呼び出しであることを示します。</span><span class="sxs-lookup"><span data-stu-id="5da3b-110">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="5da3b-111">呼び出しがローカルメソッドに対して行うことを示します。</span><span class="sxs-lookup"><span data-stu-id="5da3b-111">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="5da3b-112">は、プロパティへの呼び出しであることを示します。</span><span class="sxs-lookup"><span data-stu-id="5da3b-112">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="5da3b-113">呼び出しがアンマネージであることを示します。</span><span class="sxs-lookup"><span data-stu-id="5da3b-113">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="5da3b-114">ジェネリックメソッドのインスタンス化を示します。</span><span class="sxs-lookup"><span data-stu-id="5da3b-114">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="5da3b-115">可変個のパラメーターを受け取るメソッドへの64ビット PInvoke 呼び出しを示します。</span><span class="sxs-lookup"><span data-stu-id="5da3b-115">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="5da3b-116">4ビットの値が無効であることを示します。</span><span class="sxs-lookup"><span data-stu-id="5da3b-116">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="5da3b-117">呼び出し規則が下位4ビットによって記述されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="5da3b-117">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="5da3b-118">最上位ビットがパラメーターを記述することを示し `this` ます。</span><span class="sxs-lookup"><span data-stu-id="5da3b-118">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="5da3b-119">`this`パラメーターがシグネチャに明示的に記述されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="5da3b-119">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="5da3b-120">型引数の数が明示的に指定されたジェネリックメソッドシグネチャを示します。</span><span class="sxs-lookup"><span data-stu-id="5da3b-120">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="5da3b-121">これは、通常のパラメーターカウントの前になります。</span><span class="sxs-lookup"><span data-stu-id="5da3b-121">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5da3b-122">要件</span><span class="sxs-lookup"><span data-stu-id="5da3b-122">Requirements</span></span>  

 <span data-ttu-id="5da3b-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5da3b-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5da3b-124">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="5da3b-124">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="5da3b-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5da3b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5da3b-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="5da3b-126">See also</span></span>

- [<span data-ttu-id="5da3b-127">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="5da3b-127">Metadata Enumerations</span></span>](metadata-enumerations.md)
