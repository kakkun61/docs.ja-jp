---
title: IDebugAutoAttach::AutoAttach メソッド
ms.date: 03/30/2017
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
ms.openlocfilehash: 64dd653bb0d4e383075a999e0803e4acfd0fae3d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720101"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="ab13d-102">IDebugAutoAttach::AutoAttach メソッド</span><span class="sxs-lookup"><span data-stu-id="ab13d-102">IDebugAutoAttach::AutoAttach Method</span></span>

<span data-ttu-id="ab13d-103">サーバーによって呼び出されたデバッガーの自動アタッチを実行します。</span><span class="sxs-lookup"><span data-stu-id="ab13d-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab13d-104">構文</span><span class="sxs-lookup"><span data-stu-id="ab13d-104">Syntax</span></span>  
  
```cpp  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab13d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ab13d-105">Parameters</span></span>  

 `guidPort`  
 <span data-ttu-id="ab13d-106">から常にに設定 `GUID_NULL` します。</span><span class="sxs-lookup"><span data-stu-id="ab13d-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="ab13d-107">からプロセス ID。通常は関数を使用して取得さ `GetCurrentProcessId` れます。</span><span class="sxs-lookup"><span data-stu-id="ab13d-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="ab13d-108">からプログラムの種類: `AUTOATTACH_PROGRAM_WIN32` 、 `AUTOATTACH_PROGRAM_COMPLUS` 、または `AUTOATTACH_PROGRAM_UNKNOWN` 。</span><span class="sxs-lookup"><span data-stu-id="ab13d-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="ab13d-109">からプログラム ID。</span><span class="sxs-lookup"><span data-stu-id="ab13d-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="ab13d-110">からデバッグ動詞によって渡された文字列。</span><span class="sxs-lookup"><span data-stu-id="ab13d-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab13d-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="ab13d-111">Return Value</span></span>  

 <span data-ttu-id="ab13d-112">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="ab13d-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab13d-113">要件</span><span class="sxs-lookup"><span data-stu-id="ab13d-113">Requirements</span></span>  

 <span data-ttu-id="ab13d-114">**ヘッダー:** DbgAutoAttach .h</span><span class="sxs-lookup"><span data-stu-id="ab13d-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab13d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab13d-115">See also</span></span>

- [<span data-ttu-id="ab13d-116">IDebugAutoAttach インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ab13d-116">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)
