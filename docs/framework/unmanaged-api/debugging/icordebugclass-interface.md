---
title: ICorDebugClass インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass
helpviewer_keywords:
- ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type:
- apiref
ms.openlocfilehash: 4f488741f4233f06c128e0a262ce798ef27af3ff
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699639"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="108a3-102">ICorDebugClass インターフェイス</span><span class="sxs-lookup"><span data-stu-id="108a3-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="108a3-103">基本型または複合型 (つまり、ユーザー定義) のいずれかの型を表します。</span><span class="sxs-lookup"><span data-stu-id="108a3-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="108a3-104">型がジェネリックの場合、`ICorDebugClass` はインスタンス化されないジェネリック型を表します。</span><span class="sxs-lookup"><span data-stu-id="108a3-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="108a3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="108a3-105">Methods</span></span>  
  
|<span data-ttu-id="108a3-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="108a3-106">Method</span></span>|<span data-ttu-id="108a3-107">説明</span><span class="sxs-lookup"><span data-stu-id="108a3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="108a3-108">GetModule メソッド</span><span class="sxs-lookup"><span data-stu-id="108a3-108">GetModule Method</span></span>](icordebugclass-getmodule-method.md)|<span data-ttu-id="108a3-109">このクラスを定義するモジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="108a3-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="108a3-110">GetStaticFieldValue メソッド</span><span class="sxs-lookup"><span data-stu-id="108a3-110">GetStaticFieldValue Method</span></span>](icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="108a3-111">指定された静的フィールドの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="108a3-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="108a3-112">GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="108a3-112">GetToken Method</span></span>](icordebugclass-gettoken-method.md)|<span data-ttu-id="108a3-113">`TypeDef`このクラスのメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="108a3-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="108a3-114">注釈</span><span class="sxs-lookup"><span data-stu-id="108a3-114">Remarks</span></span>  

 <span data-ttu-id="108a3-115">インターフェイスは、 `ICorDebugClass` インスタンスジェネリック型を表します。</span><span class="sxs-lookup"><span data-stu-id="108a3-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="108a3-116">は、インスタンス化されたジェネリック型を表します。</span><span class="sxs-lookup"><span data-stu-id="108a3-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="108a3-117">たとえば、は `Hashtable<K, V>` で表されますが、は `ICorDebugClass` `Hashtable<Int32, String>` によって表さ `ICorDebugType` れます。</span><span class="sxs-lookup"><span data-stu-id="108a3-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="108a3-118">非ジェネリック型は、との両方で表され `ICorDebugClass` `ICorDebugType` ます。</span><span class="sxs-lookup"><span data-stu-id="108a3-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="108a3-119">後者のインターフェイスは、型のインスタンス化を処理するために .NET Framework バージョン2.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="108a3-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="108a3-120">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="108a3-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="108a3-121">要件</span><span class="sxs-lookup"><span data-stu-id="108a3-121">Requirements</span></span>  

 <span data-ttu-id="108a3-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="108a3-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="108a3-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="108a3-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="108a3-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="108a3-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="108a3-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="108a3-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="108a3-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="108a3-126">See also</span></span>

- [<span data-ttu-id="108a3-127">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="108a3-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
