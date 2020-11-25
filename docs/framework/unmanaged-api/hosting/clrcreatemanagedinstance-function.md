---
title: ClrCreateManagedInstance 関数
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
ms.openlocfilehash: 9aed79138499f1aa7b6fa3a28ad4505edd51b041
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731772"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="4cc6c-102">ClrCreateManagedInstance 関数</span><span class="sxs-lookup"><span data-stu-id="4cc6c-102">ClrCreateManagedInstance Function</span></span>

<span data-ttu-id="4cc6c-103">指定したマネージド型のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4cc6c-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="4cc6c-104">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="4cc6c-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="4cc6c-105">COM アクティブ化を使用してマネージ型のインスタンスを作成するか、ホストを使用します (「 [.NET Framework 4 および4.5 で追加された CLR ホストインターフェイス](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="4cc6c-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cc6c-106">構文</span><span class="sxs-lookup"><span data-stu-id="4cc6c-106">Syntax</span></span>  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,
    [in]  REFIID   riid,
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cc6c-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4cc6c-107">Parameters</span></span>  

 `pTypeName`  
 <span data-ttu-id="4cc6c-108">から要求されているインスタンス型の名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="4cc6c-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="4cc6c-109">から `IID` 要求されているインスタンス型の。</span><span class="sxs-lookup"><span data-stu-id="4cc6c-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="4cc6c-110">入出力呼び出し元によって要求されたマネージ型のインスタンスへのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4cc6c-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cc6c-111">注釈</span><span class="sxs-lookup"><span data-stu-id="4cc6c-111">Remarks</span></span>  

 <span data-ttu-id="4cc6c-112">共通言語ランタイムは、既にプロセスに読み込まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4cc6c-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="4cc6c-113">たとえば、関数が呼び出される前に [Corbindtoruntimeex](corbindtoruntimeex-function.md) 関数の呼び出しを使用して読み込むことができ `ClrCreateManagedInstance` ます。</span><span class="sxs-lookup"><span data-stu-id="4cc6c-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="4cc6c-114">ランタイムが読み込まれていない場合、は `ClrCreateManagedInstance` まず、ランタイムの v v1.0.3705 の読み込みを試みます。</span><span class="sxs-lookup"><span data-stu-id="4cc6c-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="4cc6c-115">失敗した場合は、ランタイムの最新バージョンの読み込みが試行されます。</span><span class="sxs-lookup"><span data-stu-id="4cc6c-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cc6c-116">要件</span><span class="sxs-lookup"><span data-stu-id="4cc6c-116">Requirements</span></span>  

 <span data-ttu-id="4cc6c-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4cc6c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cc6c-118">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4cc6c-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4cc6c-119">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4cc6c-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4cc6c-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cc6c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cc6c-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="4cc6c-121">See also</span></span>

- [<span data-ttu-id="4cc6c-122">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="4cc6c-122">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="4cc6c-123">ホスティング</span><span class="sxs-lookup"><span data-stu-id="4cc6c-123">Hosting</span></span>](index.md)
