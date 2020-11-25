---
title: ICorDebugModule2::ApplyChanges メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ApplyChanges
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type:
- apiref
ms.openlocfilehash: a6b1a7c9be821890a3f15d8c3297273607f5bedd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709701"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="5be3f-102">ICorDebugModule2::ApplyChanges メソッド</span><span class="sxs-lookup"><span data-stu-id="5be3f-102">ICorDebugModule2::ApplyChanges Method</span></span>

<span data-ttu-id="5be3f-103">メタデータの変更と、Microsoft 中間言語 (MSIL) コードの変更を実行中のプロセスに適用します。</span><span class="sxs-lookup"><span data-stu-id="5be3f-103">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5be3f-104">構文</span><span class="sxs-lookup"><span data-stu-id="5be3f-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5be3f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5be3f-105">Parameters</span></span>  

 `cbMetadata`  
 <span data-ttu-id="5be3f-106">からデルタメタデータのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5be3f-106">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="5be3f-107">からデルタメタデータを格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="5be3f-107">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="5be3f-108">バッファーのアドレスは、 [IMetaDataEmit2:: SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md) メソッドから返されます。</span><span class="sxs-lookup"><span data-stu-id="5be3f-108">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="5be3f-109">メタデータ内の相対仮想アドレス (RVAs) は、MSIL コードの先頭に対して相対的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5be3f-109">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="5be3f-110">からデルタ MSIL コードのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5be3f-110">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="5be3f-111">から更新された MSIL コードを格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="5be3f-111">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5be3f-112">注釈</span><span class="sxs-lookup"><span data-stu-id="5be3f-112">Remarks</span></span>  

 <span data-ttu-id="5be3f-113">パラメーターは、 `pbMetadata` ( [IMetaDataEmit2:: SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md)によって出力される) 特別なデルタメタデータ形式です。</span><span class="sxs-lookup"><span data-stu-id="5be3f-113">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="5be3f-114">`pbMetadata` 以前のメタデータをベースとして受け取り、そのベースに適用する個々の変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="5be3f-114">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="5be3f-115">これに対し、のパラメーターには、 `pbIL[` 更新されたメソッドの新しい msil が含まれています。これは、そのメソッドの前の msil を完全に置き換えることを目的としています。</span><span class="sxs-lookup"><span data-stu-id="5be3f-115">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="5be3f-116">デルタ MSIL とメタデータがデバッガーのメモリ内に作成されると、デバッガーはを呼び出して、 `ApplyChanges` 変更を共通言語ランタイム (CLR) に送信します。</span><span class="sxs-lookup"><span data-stu-id="5be3f-116">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="5be3f-117">ランタイムはそのメタデータテーブルを更新し、新しい MSIL をプロセスに配置して、新しい MSIL の just-in-time (JIT) コンパイルを設定します。</span><span class="sxs-lookup"><span data-stu-id="5be3f-117">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="5be3f-118">変更が適用されると、デバッガーは [IMetaDataEmit2:: ResetENCLog](../metadata/imetadataemit2-resetenclog-method.md) を呼び出して、次の編集セッションの準備を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="5be3f-118">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="5be3f-119">デバッガーはプロセスを続行できます。</span><span class="sxs-lookup"><span data-stu-id="5be3f-119">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="5be3f-120">デバッガーは、 `ApplyChanges` デルタメタデータを持つモジュールでを呼び出すたびに、変更を出力するために使用されるコピーを除き、そのモジュールのメタデータのすべてのコピーで同じデルタメタデータを使用して [IMetaDataEmit:: ApplyEditAndContinue](../metadata/imetadataemit-applyeditandcontinue-method.md) を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5be3f-120">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="5be3f-121">メタデータのコピーが実際のメタデータと同期しなくなる場合、デバッガーは常にそのコピーを破棄して新しいコピーを取得できます。</span><span class="sxs-lookup"><span data-stu-id="5be3f-121">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="5be3f-122">メソッドが失敗した場合 `ApplyChanges` 、デバッグセッションは無効な状態にあり、再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5be3f-122">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5be3f-123">要件</span><span class="sxs-lookup"><span data-stu-id="5be3f-123">Requirements</span></span>  

 <span data-ttu-id="5be3f-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5be3f-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5be3f-125">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5be3f-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5be3f-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5be3f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5be3f-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5be3f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
