---
title: CorErrorIfEmitOutOfOrder 列挙型
ms.date: 03/30/2017
api_name:
- CorErrorIfEmitOutOfOrder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorErrorIfEmitOutOfOrder
helpviewer_keywords:
- CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type:
- apiref
ms.openlocfilehash: 1d1b0cbb8be33f285b63e7353da973455e0fd752
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718853"
---
# <a name="corerrorifemitoutoforder-enumeration"></a><span data-ttu-id="53d11-102">CorErrorIfEmitOutOfOrder 列挙型</span><span class="sxs-lookup"><span data-stu-id="53d11-102">CorErrorIfEmitOutOfOrder Enumeration</span></span>

<span data-ttu-id="53d11-103">メタデータの生成順序が不適切である場合にエラー メッセージが生成される条件を示すフラグ値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="53d11-103">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53d11-104">構文</span><span class="sxs-lookup"><span data-stu-id="53d11-104">Syntax</span></span>  
  
```cpp  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a><span data-ttu-id="53d11-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="53d11-105">Members</span></span>  
  
|<span data-ttu-id="53d11-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="53d11-106">Member</span></span>|<span data-ttu-id="53d11-107">説明</span><span class="sxs-lookup"><span data-stu-id="53d11-107">Description</span></span>|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|<span data-ttu-id="53d11-108">エラーメッセージを生成しない既定の動作を示します。</span><span class="sxs-lookup"><span data-stu-id="53d11-108">Indicates the default behavior, which does not generate error messages.</span></span>|  
|`MDErrorOutOfOrderNone`|<span data-ttu-id="53d11-109">コンパイラがエラーメッセージを生成しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="53d11-109">Indicates that the compiler should not generate error messages.</span></span>|  
|`MDErrorOutOfOrderAll`|<span data-ttu-id="53d11-110">フィールド、プロパティ、イベント、メソッド、またはパラメーターが順序どおりに生成されない場合に、コンパイラがエラーメッセージを生成することを示します。</span><span class="sxs-lookup"><span data-stu-id="53d11-110">Indicates that the compiler should generate an error message when a field, property, event, method, or parameter is emitted out of order.</span></span>|  
|`MDMethodOutOfOrder`|<span data-ttu-id="53d11-111">メソッドが順序どおりに出力されない場合に、コンパイラがエラーメッセージを生成する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="53d11-111">Indicates that the compiler should generate an error message when a method is emitted out of order.</span></span>|  
|`MDFieldOutOfOrder`|<span data-ttu-id="53d11-112">フィールドが順序どおりに出力されない場合に、コンパイラがエラーメッセージを生成する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="53d11-112">Indicates that the compiler should generate an error message when a field is emitted out of order.</span></span>|  
|`MDParamOutOfOrder`|<span data-ttu-id="53d11-113">パラメーターが順序どおりに出力されない場合に、コンパイラがエラーメッセージを生成する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="53d11-113">Indicates that the compiler should generate an error message when a parameter is emitted out of order.</span></span>|  
|`MDPropertyOutOfOrder`|<span data-ttu-id="53d11-114">プロパティが順序どおりに出力されない場合に、コンパイラがエラーメッセージを生成する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="53d11-114">Indicates that the compiler should generate an error message when a property is emitted out of order.</span></span>|  
|`MDEventOutOfOrder`|<span data-ttu-id="53d11-115">イベントが順序どおりに生成されない場合に、コンパイラがエラーメッセージを生成する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="53d11-115">Indicates that the compiler should generate an error message when an event is emitted out of order.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="53d11-116">要件</span><span class="sxs-lookup"><span data-stu-id="53d11-116">Requirements</span></span>  

 <span data-ttu-id="53d11-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53d11-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53d11-118">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="53d11-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="53d11-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53d11-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53d11-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="53d11-120">See also</span></span>

- [<span data-ttu-id="53d11-121">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="53d11-121">Metadata Enumerations</span></span>](metadata-enumerations.md)
