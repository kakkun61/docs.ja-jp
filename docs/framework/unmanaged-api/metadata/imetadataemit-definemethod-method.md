---
title: IMetaDataEmit::DefineMethod メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
ms.openlocfilehash: a32a1eb850943b84a0d368f883e44fd4ccf32ee9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719581"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="cd2ac-102">IMetaDataEmit::DefineMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="cd2ac-102">IMetaDataEmit::DefineMethod Method</span></span>

<span data-ttu-id="cd2ac-103">指定したシグネチャを使用してメソッドまたはグローバル関数の定義を作成し、そのメソッド定義に対するトークンを返します。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd2ac-104">構文</span><span class="sxs-lookup"><span data-stu-id="cd2ac-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethod (
    [in]  mdTypeDef         td,
    [in]  LPCWSTR           szName,
    [in]  DWORD             dwMethodFlags,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [in]  ULONG             ulCodeRVA,
    [in]  DWORD             dwImplFlags,
    [out] mdMethodDef      *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd2ac-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cd2ac-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="cd2ac-106">から `mdTypedef` メソッドの親クラスまたは親インターフェイスのトークン。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="cd2ac-107">`td` `mdTokenNil` グローバル関数を定義する場合は、に設定します。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="cd2ac-108">からUnicode のメンバー名。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="cd2ac-109">からメソッドまたはグローバル関数の属性を指定する [CorMethodAttr](cormethodattr-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-109">[in] A value of the [CorMethodAttr](cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="cd2ac-110">からメソッドシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-110">[in] The method signature.</span></span> <span data-ttu-id="cd2ac-111">署名は、指定されたとおりに永続化されます。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="cd2ac-112">任意のパラメーターの追加情報を指定する必要がある場合は、 [IMetaDataEmit:: SetParamProps](imetadataemit-setparamprops-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="cd2ac-113">からのバイト数 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="cd2ac-114">からコードのアドレス。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="cd2ac-115">からメソッドの実装機能を指定する [Cormethodimpl](cormethodimpl-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-115">[in] A value of the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="cd2ac-116">入出力メンバートークン。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd2ac-117">注釈</span><span class="sxs-lookup"><span data-stu-id="cd2ac-117">Remarks</span></span>  

 <span data-ttu-id="cd2ac-118">メタデータ API は、呼び出し元が指定された外側のクラスまたはインターフェイスに対してメソッドを出力するのと同じ順序でメソッドを永続化することを保証します。これは、パラメーターで指定し `td` ます。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="cd2ac-119">および特定のパラメーター設定の使用に関する追加情報 `DefineMethod` を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="cd2ac-120">V テーブルのスロット</span><span class="sxs-lookup"><span data-stu-id="cd2ac-120">Slots in the V-table</span></span>  

 <span data-ttu-id="cd2ac-121">ランタイムは、メソッド定義を使用して、v テーブルスロットを設定します。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="cd2ac-122">COM インターフェイスのレイアウトでパリティを保持するなど、1つ以上のスロットをスキップする必要がある場合は、v テーブルのスロットまたはスロットを取得するためにダミーメソッドが定義されています。を `dwMethodFlags` `mdRTSpecialName` [CorMethodAttr](cormethodattr-enumeration.md) 列挙の値に設定し、名前をとして指定します。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="cd2ac-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="cd2ac-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="cd2ac-124">ここで、 *SequenceNumber* はメソッドのシーケンス番号、 *CountOfSlots* は v テーブルでスキップするスロットの数です。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="cd2ac-125">*CountOfSlots* を省略すると、1が想定されます。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="cd2ac-126">これらのダミーメソッドは、マネージコードまたはアンマネージコードから呼び出すことはできません。また、マネージコードまたはアンマネージコードから呼び出しを試みると、例外が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="cd2ac-127">その唯一の目的は、ランタイムが COM 統合用に生成する v テーブルの領域を占有することです。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="cd2ac-128">重複するメソッド</span><span class="sxs-lookup"><span data-stu-id="cd2ac-128">Duplicate Methods</span></span>  

 <span data-ttu-id="cd2ac-129">重複するメソッドは定義しないでください。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-129">You should not define duplicate methods.</span></span> <span data-ttu-id="cd2ac-130">つまり、、、およびの各 `DefineMethod` パラメーターで、重複する値のセットを指定してを呼び出すことはできません `td` `wzName` `pvSig` 。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="cd2ac-131">(これら3つのパラメーターを組み合わせて、メソッドを一意に定義します)。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="cd2ac-132">ただし、メソッドの定義の1つに対して、パラメーターにビットを設定するという3つの方法を使用できます `mdPrivateScope` `dwMethodFlags` 。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="cd2ac-133">(ビットは、 `mdPrivateScope` コンパイラがこのメソッド定義への参照を生成しないことを意味します)。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="cd2ac-134">メソッドの実装情報</span><span class="sxs-lookup"><span data-stu-id="cd2ac-134">Method Implementation Information</span></span>  

 <span data-ttu-id="cd2ac-135">メソッドの実装に関する情報は、多くの場合、メソッドが宣言されているときには認識されません。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="cd2ac-136">したがって、 `ulCodeRVA` を呼び出すときに、パラメーターとパラメーターに値を渡す必要はありません `dwImplFlags` `DefineMethod` 。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="cd2ac-137">値は、必要に応じて、後で [IMetaDataEmit:: SetMethodImplFlags](imetadataemit-setmethodimplflags-method.md) または [IMetaDataEmit:: SetRVA](imetadataemit-setrva-method.md)を使用して指定できます。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="cd2ac-138">プラットフォーム呼び出し (PInvoke) や COM 相互運用のシナリオなど、状況によっては、メソッド本体が提供されず、 `ulCodeRVA` 0 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="cd2ac-139">このような状況では、ランタイムによって実装が特定されるため、メソッドを abstract としてタグ付けすることはできません。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="cd2ac-140">PInvoke のメソッドの定義</span><span class="sxs-lookup"><span data-stu-id="cd2ac-140">Defining a Method for PInvoke</span></span>  

 <span data-ttu-id="cd2ac-141">PInvoke を通じて呼び出される各アンマネージ関数に対して、対象のアンマネージ関数を表すマネージメソッドを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="cd2ac-142">マネージメソッドを定義するには、 `DefineMethod` PInvoke の使用方法に応じて、特定の値に設定されているいくつかのパラメーターと共にを使用します。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="cd2ac-143">True PInvoke-アンマネージ DLL に存在する外部アンマネージメソッドの呼び出しが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="cd2ac-144">ローカル PInvoke-現在のマネージモジュールに埋め込まれているネイティブアンマネージメソッドの呼び出しが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="cd2ac-145">パラメーターの設定を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="cd2ac-146">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cd2ac-146">Parameter</span></span>|<span data-ttu-id="cd2ac-147">True PInvoke の値</span><span class="sxs-lookup"><span data-stu-id="cd2ac-147">Values for true PInvoke</span></span>|<span data-ttu-id="cd2ac-148">ローカル PInvoke の値</span><span class="sxs-lookup"><span data-stu-id="cd2ac-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="cd2ac-149">`mdStatic` `mdSynchronized` を設定します。とをクリアし `mdAbstract` ます。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="cd2ac-150">有効なマネージ型であるパラメーターを持つ有効な共通言語ランタイム (CLR) メソッドシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="cd2ac-151">有効なマネージ型であるパラメーターを含む有効な CLR メソッドシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="cd2ac-152">0</span><span class="sxs-lookup"><span data-stu-id="cd2ac-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="cd2ac-153">`miCil` と `miManaged` を設定します。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="cd2ac-154">`miNative` と `miUnmanaged` を設定します。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd2ac-155">要件</span><span class="sxs-lookup"><span data-stu-id="cd2ac-155">Requirements</span></span>  

 <span data-ttu-id="cd2ac-156">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-156">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd2ac-157">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="cd2ac-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd2ac-158">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd2ac-159">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd2ac-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd2ac-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd2ac-160">See also</span></span>

- [<span data-ttu-id="cd2ac-161">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd2ac-161">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="cd2ac-162">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd2ac-162">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
