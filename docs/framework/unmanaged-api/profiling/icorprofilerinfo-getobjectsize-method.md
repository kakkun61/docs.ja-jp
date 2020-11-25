---
title: ICorProfilerInfo::GetObjectSize メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
ms.openlocfilehash: 4abcf9f4575b32dd125fd8a00783043900993c3e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724105"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="0996e-102">ICorProfilerInfo::GetObjectSize メソッド</span><span class="sxs-lookup"><span data-stu-id="0996e-102">ICorProfilerInfo::GetObjectSize Method</span></span>

<span data-ttu-id="0996e-103">指定したオブジェクトのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="0996e-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0996e-104">構文</span><span class="sxs-lookup"><span data-stu-id="0996e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0996e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0996e-105">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="0996e-106">からオブジェクトの ID です。</span><span class="sxs-lookup"><span data-stu-id="0996e-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="0996e-107">入出力オブジェクトのサイズへのポインター (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="0996e-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0996e-108">注釈</span><span class="sxs-lookup"><span data-stu-id="0996e-108">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0996e-109">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="0996e-109">This method is obsolete.</span></span> <span data-ttu-id="0996e-110">64ビットプラットフォームで 4 GB を超えるオブジェクトの COR_E_OVERFLOW を返します。</span><span class="sxs-lookup"><span data-stu-id="0996e-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="0996e-111">代わりに  [ICorProfilerInfo4:: GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="0996e-111">Use the  [ICorProfilerInfo4::GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="0996e-112">多くの場合、同じ種類の異なるオブジェクトのサイズは同じです。</span><span class="sxs-lookup"><span data-stu-id="0996e-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="0996e-113">ただし、配列や文字列など、一部の型では、オブジェクトごとにサイズが異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0996e-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="0996e-114">メソッドによって返されるサイズには、 `GetObjectSize` オブジェクトがガベージコレクションヒープに配置された後に表示されるアラインメントの埋め込みは含まれません。</span><span class="sxs-lookup"><span data-stu-id="0996e-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="0996e-115">メソッドを使用して `GetObjectSize` オブジェクトからガベージコレクションヒープ上のオブジェクトに進む場合は、必要に応じて、手動でアラインメントのパディングを追加します。</span><span class="sxs-lookup"><span data-stu-id="0996e-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
- <span data-ttu-id="0996e-116">32ビットの Windows では、COR_PRF_GC_GEN_0、COR_PRF_GC_GEN_1、および COR_PRF_GC_GEN_2 は4バイトの配置を使用し、COR_PRF_GC_LARGE_OBJECT_HEAP は8バイトの配置を使用します。</span><span class="sxs-lookup"><span data-stu-id="0996e-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
- <span data-ttu-id="0996e-117">64ビットの Windows では、アラインメントは常に8バイトです。</span><span class="sxs-lookup"><span data-stu-id="0996e-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0996e-118">要件</span><span class="sxs-lookup"><span data-stu-id="0996e-118">Requirements</span></span>  

 <span data-ttu-id="0996e-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0996e-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0996e-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0996e-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0996e-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0996e-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0996e-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0996e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0996e-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="0996e-123">See also</span></span>

- [<span data-ttu-id="0996e-124">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0996e-124">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
