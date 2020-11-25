---
title: ICorDebugType インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType
helpviewer_keywords:
- ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type:
- apiref
ms.openlocfilehash: 9407dda7aab337f667cd5043b562d0eac94f0f04
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711924"
---
# <a name="icordebugtype-interface"></a><span data-ttu-id="997ca-102">ICorDebugType インターフェイス</span><span class="sxs-lookup"><span data-stu-id="997ca-102">ICorDebugType Interface</span></span>

<span data-ttu-id="997ca-103">基本または複合 (つまり、ユーザー定義) のいずれかの型を表します。</span><span class="sxs-lookup"><span data-stu-id="997ca-103">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="997ca-104">型がジェネリックの場合、`ICorDebugType` はインスタンス化されたジェネリック型を表します。</span><span class="sxs-lookup"><span data-stu-id="997ca-104">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="997ca-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="997ca-105">Methods</span></span>  
  
|<span data-ttu-id="997ca-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="997ca-106">Method</span></span>|<span data-ttu-id="997ca-107">説明</span><span class="sxs-lookup"><span data-stu-id="997ca-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="997ca-108">EnumerateTypeParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="997ca-108">EnumerateTypeParameters Method</span></span>](icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="997ca-109">このによって参照されるクラスのジェネリックパラメーターを参照する、ツールのインターフェイスポインターを取得し <xref:System.Type> `ICorDebugType` ます。</span><span class="sxs-lookup"><span data-stu-id="997ca-109">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="997ca-110">GetBase メソッド</span><span class="sxs-lookup"><span data-stu-id="997ca-110">GetBase Method</span></span>](icordebugtype-getbase-method.md)|<span data-ttu-id="997ca-111">`ICorDebugType`このによって参照されるクラス `ICorDebugType` (存在する場合) の基本クラスを参照するへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="997ca-111">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="997ca-112">GetClass メソッド</span><span class="sxs-lookup"><span data-stu-id="997ca-112">GetClass Method</span></span>](icordebugtype-getclass-method.md)|<span data-ttu-id="997ca-113">このの型指定されたコンストラクターを参照する、によるクラスへのインターフェイスポインターを取得し `ICorDebugType` ます。</span><span class="sxs-lookup"><span data-stu-id="997ca-113">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="997ca-114">GetFirstTypeParameter メソッド</span><span class="sxs-lookup"><span data-stu-id="997ca-114">GetFirstTypeParameter Method</span></span>](icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="997ca-115">`ICorDebugType` <xref:System.Type> このによって参照されるクラスのコンストラクターの最初のジェネリックパラメーターを参照するへのインターフェイスポインターを取得し `ICorDebugType` ます。</span><span class="sxs-lookup"><span data-stu-id="997ca-115">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="997ca-116">GetRank メソッド</span><span class="sxs-lookup"><span data-stu-id="997ca-116">GetRank Method</span></span>](icordebugtype-getrank-method.md)|<span data-ttu-id="997ca-117">配列型の次元数を取得します。</span><span class="sxs-lookup"><span data-stu-id="997ca-117">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="997ca-118">GetStaticFieldValue メソッド</span><span class="sxs-lookup"><span data-stu-id="997ca-118">GetStaticFieldValue Method</span></span>](icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="997ca-119">指定したスタックフレーム内の指定したフィールドトークンによって参照される静的フィールドの値を格納する、ICorDebugValue へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="997ca-119">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="997ca-120">GetType メソッド</span><span class="sxs-lookup"><span data-stu-id="997ca-120">GetType Method</span></span>](icordebugtype-gettype-method.md)|<span data-ttu-id="997ca-121">このによって参照される共通言語ランタイムのネイティブ型を記述する CorElementType 値を取得し <xref:System.Type> `ICorDebugType` ます。</span><span class="sxs-lookup"><span data-stu-id="997ca-121">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="997ca-122">注釈</span><span class="sxs-lookup"><span data-stu-id="997ca-122">Remarks</span></span>  

 <span data-ttu-id="997ca-123">型がジェネリックの場合、は `ICorDebugClass` インスタンス型を表します。</span><span class="sxs-lookup"><span data-stu-id="997ca-123">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="997ca-124">インターフェイスは、 `ICorDebugType` インスタンス化されたジェネリック型を表します。</span><span class="sxs-lookup"><span data-stu-id="997ca-124">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="997ca-125">たとえば、Hashtable はに \<K, V> よって表さ `ICorDebugClass` れますが、hashtable は \<Int32, String> によって表さ `ICorDebugType` れます。</span><span class="sxs-lookup"><span data-stu-id="997ca-125">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="997ca-126">非ジェネリック型は、との両方で表され `ICorDebugClass` `ICorDebugType` ます。</span><span class="sxs-lookup"><span data-stu-id="997ca-126">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="997ca-127">後者のインターフェイスは、型のインスタンス化を処理するために .NET Framework バージョン2.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="997ca-127">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="997ca-128">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="997ca-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="997ca-129">要件</span><span class="sxs-lookup"><span data-stu-id="997ca-129">Requirements</span></span>  

 <span data-ttu-id="997ca-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="997ca-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="997ca-131">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="997ca-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="997ca-132">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="997ca-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="997ca-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="997ca-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="997ca-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="997ca-134">See also</span></span>

- [<span data-ttu-id="997ca-135">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="997ca-135">Debugging Interfaces</span></span>](debugging-interfaces.md)
