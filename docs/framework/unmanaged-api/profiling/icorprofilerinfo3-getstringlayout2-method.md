---
title: ICorProfilerInfo3::GetStringLayout2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
ms.openlocfilehash: dc4df7e7cb93f137013d0a0e4d805c7563d4fe1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697897"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="2bc46-102">ICorProfilerInfo3::GetStringLayout2 メソッド</span><span class="sxs-lookup"><span data-stu-id="2bc46-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>

<span data-ttu-id="2bc46-103">文字列オブジェクトのレイアウトに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="2bc46-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="2bc46-104">このメソッドは、 [ICorProfilerInfo2:: GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) メソッドよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="2bc46-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bc46-105">構文</span><span class="sxs-lookup"><span data-stu-id="2bc46-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bc46-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2bc46-106">Parameters</span></span>  

 `pStringLengthOffset`  
 <span data-ttu-id="2bc46-107">入出力 `ObjectID` 文字列自体の長さを格納する、ポインターを基準とした位置のオフセットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2bc46-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="2bc46-108">長さはとして格納され `DWORD` ます。</span><span class="sxs-lookup"><span data-stu-id="2bc46-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="2bc46-109">入出力ワイド文字の文字列を格納するポインターを基準とした、バッファーのオフセットへのポインター `ObjectID` 。</span><span class="sxs-lookup"><span data-stu-id="2bc46-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bc46-110">注釈</span><span class="sxs-lookup"><span data-stu-id="2bc46-110">Remarks</span></span>  

 <span data-ttu-id="2bc46-111">文字列は、null で終わることができます。</span><span class="sxs-lookup"><span data-stu-id="2bc46-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bc46-112">要件</span><span class="sxs-lookup"><span data-stu-id="2bc46-112">Requirements</span></span>  

 <span data-ttu-id="2bc46-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bc46-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bc46-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2bc46-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2bc46-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bc46-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bc46-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bc46-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bc46-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bc46-117">See also</span></span>

- [<span data-ttu-id="2bc46-118">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2bc46-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="2bc46-119">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2bc46-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
