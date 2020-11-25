---
title: COR_TYPEID 構造体
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
ms.openlocfilehash: 5eeb5aef7edaa23385190a309144e1477da741e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697442"
---
# <a name="cor_typeid-structure"></a><span data-ttu-id="2cde9-102">COR_TYPEID 構造体</span><span class="sxs-lookup"><span data-stu-id="2cde9-102">COR_TYPEID Structure</span></span>

<span data-ttu-id="2cde9-103">型識別子が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2cde9-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cde9-104">構文</span><span class="sxs-lookup"><span data-stu-id="2cde9-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="2cde9-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="2cde9-105">Members</span></span>  
  
|<span data-ttu-id="2cde9-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="2cde9-106">Member</span></span>|<span data-ttu-id="2cde9-107">説明</span><span class="sxs-lookup"><span data-stu-id="2cde9-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="2cde9-108">最初のトークン。</span><span class="sxs-lookup"><span data-stu-id="2cde9-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="2cde9-109">2番目のトークン。</span><span class="sxs-lookup"><span data-stu-id="2cde9-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cde9-110">注釈</span><span class="sxs-lookup"><span data-stu-id="2cde9-110">Remarks</span></span>  

 <span data-ttu-id="2cde9-111">`COR_TYPEID`構造体は、ガベージコレクションされるオブジェクトに関する情報を提供する多数のデバッグメソッドによって返されます。</span><span class="sxs-lookup"><span data-stu-id="2cde9-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="2cde9-112">その後、その項目に関する追加情報を提供する他のデバッグメソッドに引数として渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="2cde9-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="2cde9-113">たとえば、 [コードオブジェクトを列挙する](icordebugheapenum-interface.md) ことによって、マネージヒープ上の個々のオブジェクトを表す個々の [COR_HEAPOBJECT](cor-heapobject-structure.md) オブジェクトを取得できます。</span><span class="sxs-lookup"><span data-stu-id="2cde9-113">For example, by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="2cde9-114">次に、フィールドの `COR_TYPEID` 値を `COR_HEAPOBJECT.type` [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) メソッドに渡して、オブジェクトに関する型情報を提供する、テキストオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="2cde9-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="2cde9-115">`COR_TYPEID`オブジェクトは不透明であることが想定されています。</span><span class="sxs-lookup"><span data-stu-id="2cde9-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="2cde9-116">個々のフィールドにアクセスしたり操作したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="2cde9-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="2cde9-117">唯一の用途は、メソッドの呼び出しでパラメーターとして指定された識別子として使用され、 `out` さらに情報を提供するために他のメソッドに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="2cde9-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cde9-118">要件</span><span class="sxs-lookup"><span data-stu-id="2cde9-118">Requirements</span></span>  

 <span data-ttu-id="2cde9-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cde9-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cde9-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2cde9-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2cde9-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2cde9-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cde9-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cde9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cde9-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="2cde9-123">See also</span></span>

- [<span data-ttu-id="2cde9-124">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="2cde9-124">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="2cde9-125">デバッグ</span><span class="sxs-lookup"><span data-stu-id="2cde9-125">Debugging</span></span>](index.md)
