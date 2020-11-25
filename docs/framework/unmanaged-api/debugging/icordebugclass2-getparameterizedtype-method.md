---
title: ICorDebugClass2::GetParameterizedType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.GetParameterizedType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::GetParameterizedType
helpviewer_keywords:
- GetParameterizedType method [.NET Framework debugging]
- ICorDebugClass2::GetParameterizedType method [.NET Framework debugging]
ms.assetid: 94b591c4-9302-4af2-a510-089496afb036
topic_type:
- apiref
ms.openlocfilehash: 139181975d16c2cdacec10ed646cfc2b8fb31a20
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717995"
---
# <a name="icordebugclass2getparameterizedtype-method"></a><span data-ttu-id="edfff-102">ICorDebugClass2::GetParameterizedType メソッド</span><span class="sxs-lookup"><span data-stu-id="edfff-102">ICorDebugClass2::GetParameterizedType Method</span></span>

<span data-ttu-id="edfff-103">このクラスの型宣言を取得します。</span><span class="sxs-lookup"><span data-stu-id="edfff-103">Gets the type declaration for this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edfff-104">構文</span><span class="sxs-lookup"><span data-stu-id="edfff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edfff-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="edfff-105">Parameters</span></span>  

 `elementType`  
 <span data-ttu-id="edfff-106">からこのクラスの要素の型を指定する CorElementType 列挙体の値。この ICorDebugClass2 が値の型を表す場合は、この値を ELEMENT_TYPE_VALUETYPE に設定します。</span><span class="sxs-lookup"><span data-stu-id="edfff-106">[in] A value of the CorElementType enumeration that specifies the element type for this class: Set this value to ELEMENT_TYPE_VALUETYPE if this ICorDebugClass2 represents a value type.</span></span> <span data-ttu-id="edfff-107">このが複合型を表す場合は、この値を ELEMENT_TYPE_CLASS に設定し `ICorDebugClass2` ます。</span><span class="sxs-lookup"><span data-stu-id="edfff-107">Set this value to ELEMENT_TYPE_CLASS if this `ICorDebugClass2` represents a complex type.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="edfff-108">から型がジェネリックの場合は、型パラメーターの数。</span><span class="sxs-lookup"><span data-stu-id="edfff-108">[in] The number of type parameters, if the type is generic.</span></span> <span data-ttu-id="edfff-109">型パラメーターの数 (存在する場合) は、クラスで必要な数と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="edfff-109">The number of type parameters (if any) must match the number required by the class.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="edfff-110">からポインターの配列。各ポインターは、型パラメーターを表す、テキスト型のオブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="edfff-110">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type parameter.</span></span> <span data-ttu-id="edfff-111">クラスが非ジェネリックの場合、この値は null になります。</span><span class="sxs-lookup"><span data-stu-id="edfff-111">If the class is non-generic, this value is null.</span></span>  
  
 `ppType`  
 <span data-ttu-id="edfff-112">入出力型宣言を表すオブジェクトのアドレスへのポインター `ICorDebugType` 。</span><span class="sxs-lookup"><span data-stu-id="edfff-112">[out] A pointer to the address of an `ICorDebugType` object that represents the type declaration.</span></span> <span data-ttu-id="edfff-113">このオブジェクトは、 <xref:System.Type> マネージコード内のオブジェクトに相当します。</span><span class="sxs-lookup"><span data-stu-id="edfff-113">This object is equivalent to a <xref:System.Type> object in managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edfff-114">注釈</span><span class="sxs-lookup"><span data-stu-id="edfff-114">Remarks</span></span>  

 <span data-ttu-id="edfff-115">クラスが非ジェネリックの場合、つまり、型パラメーターがない場合は、 `GetParameterizedType` クラスに対応するランタイム型オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="edfff-115">If the class is non-generic, that is, if it has no type parameters, `GetParameterizedType` simply gets the runtime type object corresponding to the class.</span></span> <span data-ttu-id="edfff-116">クラス `elementType` が値型の場合は、パラメーターをクラスの正しい要素型に設定する必要があります。それ以外の場合は、ELEMENT_TYPE_CLASS を ELEMENT_TYPE_VALUETYPE ます。</span><span class="sxs-lookup"><span data-stu-id="edfff-116">The `elementType` parameter should be set to the correct element type for the class: ELEMENT_TYPE_VALUETYPE if the class is a value type; otherwise, ELEMENT_TYPE_CLASS.</span></span>  
  
 <span data-ttu-id="edfff-117">クラスが型パラメーター (など) を受け入れる場合は `ArrayList<T>` 、を使用して、インスタンス化された型 (など) `GetParameterizedType` の型オブジェクトを構築でき `ArrayList<int>` ます。</span><span class="sxs-lookup"><span data-stu-id="edfff-117">If the class accepts type parameters (for example, `ArrayList<T>`), you can use `GetParameterizedType` to construct a type object for an instantiated type such as `ArrayList<int>`.</span></span>  
  
## <a name="background-information"></a><span data-ttu-id="edfff-118">背景情報</span><span class="sxs-lookup"><span data-stu-id="edfff-118">Background Information</span></span>  

 <span data-ttu-id="edfff-119">.NET Framework バージョン1.0 および1.1 では、メタデータ内のすべての型を、実行中のプロセスの型に直接マップすることができます。</span><span class="sxs-lookup"><span data-stu-id="edfff-119">In the .NET Framework versions 1.0 and 1.1, every type in the metadata could be directly mapped to a type in the running process.</span></span> <span data-ttu-id="edfff-120">したがって、メタデータ型とランタイム型には、実行中のプロセスで1つの表現が含まれていました。</span><span class="sxs-lookup"><span data-stu-id="edfff-120">Thus, a metadata type and a runtime type had a single representation in the running process.</span></span> <span data-ttu-id="edfff-121">ただし、メタデータ内の1つのジェネリック型は、実行中のプロセスの型のさまざまなインスタンス化にマップできます。</span><span class="sxs-lookup"><span data-stu-id="edfff-121">However, one generic type in metadata can be mapped to many different instantiations of the type in the running process.</span></span> <span data-ttu-id="edfff-122">たとえば、メタデータ型は `SortedList<K,V>` 、、、などにマップでき `SortedList<String, EmployeeRecord>` `SortedList<Int32, String>` `SortedList<String,Array<Int32>>` ます。</span><span class="sxs-lookup"><span data-stu-id="edfff-122">For example, the metadata type `SortedList<K,V>` can map to `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, and so on.</span></span> <span data-ttu-id="edfff-123">そのため、型のインスタンス化を処理する方法が必要です。</span><span class="sxs-lookup"><span data-stu-id="edfff-123">Thus, you need a way to handle type instantiation.</span></span>  
  
 <span data-ttu-id="edfff-124">.NET Framework バージョン2.0 では、インターフェイスが導入されて `ICorDebugType` います。</span><span class="sxs-lookup"><span data-stu-id="edfff-124">The .NET Framework version 2.0 introduces the `ICorDebugType` interface.</span></span> <span data-ttu-id="edfff-125">ジェネリック型の場合、 `ICorDebugClass` オブジェクトまたは `ICorDebugClass2` オブジェクトはインスタンス type ( `SortedList<K,V>` ) を表し、オブジェクトはインスタンス化された `ICorDebugType` さまざまな型を表します。</span><span class="sxs-lookup"><span data-stu-id="edfff-125">For a generic type, an `ICorDebugClass` or `ICorDebugClass2` object represents the uninstantiated type (`SortedList<K,V>`), and an `ICorDebugType` object represents the various instantiated types.</span></span> <span data-ttu-id="edfff-126">オブジェクトまたはオブジェクトを指定した場合は、 `ICorDebugClass` `ICorDebugClass2` メソッドを `ICorDebugType` 呼び出すことによって、インスタンス化の対象となるオブジェクトを作成でき `ICorDebugClass2::GetParameterizedType` ます。</span><span class="sxs-lookup"><span data-stu-id="edfff-126">Given an `ICorDebugClass` or `ICorDebugClass2` object, you can create an `ICorDebugType` object for any instantiation by calling the `ICorDebugClass2::GetParameterizedType` method.</span></span> <span data-ttu-id="edfff-127">また、Int32 などの `ICorDebugType` 単純型のオブジェクト、または非ジェネリック型のオブジェクトを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="edfff-127">You can also create an `ICorDebugType` object for a simple type, such as Int32, or for a non-generic type.</span></span>  
  
 <span data-ttu-id="edfff-128">`ICorDebugType`型の実行時の概念を表すオブジェクトの導入は、API 全体で波及効果を持ちます。</span><span class="sxs-lookup"><span data-stu-id="edfff-128">The introduction of the `ICorDebugType` object to represent the run-time notion of a type has a ripple effect throughout the API.</span></span> <span data-ttu-id="edfff-129">以前にまたはオブジェクトを取得した関数、または値を使用した関数は、 `ICorDebugClass` `ICorDebugClass2` `CorElementType` オブジェクトを取得するために一般化されてい `ICorDebugType` ます。</span><span class="sxs-lookup"><span data-stu-id="edfff-129">Functions that previously took an `ICorDebugClass` or `ICorDebugClass2` object or even a `CorElementType` value are generalized to take an `ICorDebugType` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edfff-130">要件</span><span class="sxs-lookup"><span data-stu-id="edfff-130">Requirements</span></span>  

 <span data-ttu-id="edfff-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="edfff-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edfff-132">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="edfff-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="edfff-133">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edfff-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edfff-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edfff-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
