---
title: CorSerializationType 列挙型
ms.date: 03/30/2017
api_name:
- CorSerializationType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSerializationType
helpviewer_keywords:
- CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type:
- apiref
ms.openlocfilehash: e9c9674bfe0e5a8006a4881e103b633ee8f2af1d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706054"
---
# <a name="corserializationtype-enumeration"></a><span data-ttu-id="94429-102">CorSerializationType 列挙型</span><span class="sxs-lookup"><span data-stu-id="94429-102">CorSerializationType Enumeration</span></span>

<span data-ttu-id="94429-103">共通言語ランタイムによってオブジェクトをシリアル化する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="94429-103">Specifies how an object is serialized by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94429-104">構文</span><span class="sxs-lookup"><span data-stu-id="94429-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a><span data-ttu-id="94429-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="94429-105">Members</span></span>  
  
|<span data-ttu-id="94429-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="94429-106">Member</span></span>|<span data-ttu-id="94429-107">説明</span><span class="sxs-lookup"><span data-stu-id="94429-107">Description</span></span>|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|<span data-ttu-id="94429-108">オブジェクトのシリアル化が定義されていません。</span><span class="sxs-lookup"><span data-stu-id="94429-108">Serialization of the object is undefined.</span></span>|  
|`SERIALIZATION_TYPE_BOOLEAN`|<span data-ttu-id="94429-109">オブジェクトはブール型としてシリアル化されます</span><span class="sxs-lookup"><span data-stu-id="94429-109">Object is serialized as a Boolean type</span></span>|  
|`SERIALIZATION_TYPE_CHAR`|<span data-ttu-id="94429-110">オブジェクトは文字型としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="94429-110">Object is serialized as a character type.</span></span>|  
|`SERIALIZATION_TYPE_I1`|<span data-ttu-id="94429-111">オブジェクトは符号付き1バイト整数としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="94429-111">Object is serialized as a signed 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U1`|<span data-ttu-id="94429-112">オブジェクトは、符号なし1バイト整数としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="94429-112">Object is serialized as an unsigned 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I2`|<span data-ttu-id="94429-113">オブジェクトは、符号付き2バイト整数としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="94429-113">Object is serialized as a signed 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U2`|<span data-ttu-id="94429-114">オブジェクトは、符号なし2バイト整数としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="94429-114">Object is serialized as an unsigned 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I4`|<span data-ttu-id="94429-115">オブジェクトは、符号付き4バイト整数としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="94429-115">Object is serialized as a signed 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U4`|<span data-ttu-id="94429-116">オブジェクトは、4バイトの符号なし整数としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="94429-116">Object is serialized as an unsigned 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I8`|<span data-ttu-id="94429-117">オブジェクトは、符号付き8バイト整数としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="94429-117">Object is serialized as a signed 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U8`|<span data-ttu-id="94429-118">オブジェクトは、8バイトの符号なし整数としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="94429-118">Object is serialized as an unsigned 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_R4`|<span data-ttu-id="94429-119">オブジェクトは、4バイトの浮動小数点としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="94429-119">Object is serialized as a 4-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_R8`|<span data-ttu-id="94429-120">オブジェクトは8バイト浮動小数点としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="94429-120">Object is serialized as an 8-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_STRING`|<span data-ttu-id="94429-121">オブジェクトは System.string 型としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="94429-121">Object is serialized as a System.String type.</span></span>|  
|`SERIALIZATION_TYPE_SZARRAY`|<span data-ttu-id="94429-122">オブジェクトは、1次元の下限の配列としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="94429-122">Object is serialized as a single-dimensional, zero lower-bound array.</span></span>|  
|`SERIALIZATION_TYPE_TYPE`|<span data-ttu-id="94429-123">オブジェクトは、ジェネリック型としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="94429-123">Object is serialized as a generic type.</span></span>|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|<span data-ttu-id="94429-124">オブジェクトはタグ付きオブジェクトとしてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="94429-124">Object is serialized as a tagged object.</span></span>|  
|`SERIALIZATION_TYPE_FIELD`|<span data-ttu-id="94429-125">オブジェクトはフィールドとしてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="94429-125">Object is serialized as a field.</span></span>|  
|`SERIALIZATION_TYPE_PROPERTY`|<span data-ttu-id="94429-126">オブジェクトはプロパティとしてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="94429-126">Object is serialized as a property.</span></span>|  
|`SERIALIZATION_TYPE_ENUM`|<span data-ttu-id="94429-127">オブジェクトは列挙体としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="94429-127">Object is serialized as an enumeration.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="94429-128">要件</span><span class="sxs-lookup"><span data-stu-id="94429-128">Requirements</span></span>  

 <span data-ttu-id="94429-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94429-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94429-130">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="94429-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="94429-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94429-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94429-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="94429-132">See also</span></span>

- [<span data-ttu-id="94429-133">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="94429-133">Metadata Enumerations</span></span>](metadata-enumerations.md)
