---
title: CreateCoreClrDebugTarget 関数
ms.date: 03/30/2017
api_name:
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
ms.openlocfilehash: f0188facf0b7d33e6e1ecc12921a139165f777a1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686632"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="3a7bb-102">CreateCoreClrDebugTarget 関数</span><span class="sxs-lookup"><span data-stu-id="3a7bb-102">CreateCoreClrDebugTarget Function</span></span>

<span data-ttu-id="3a7bb-103">リモートコンピューター上で実行されているデバッガープロキシへの接続を作成し、 [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) オブジェクトを返します。このオブジェクトを使用して、リモートコンピューター上で実行中のプロセスおよび読み込まれたランタイムのクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="3a7bb-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a7bb-104">構文</span><span class="sxs-lookup"><span data-stu-id="3a7bb-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a7bb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3a7bb-105">Parameters</span></span>  

 `dwAddress`  
 <span data-ttu-id="3a7bb-106">[in] リモート対象コンピューターの IPv4 アドレス。</span><span class="sxs-lookup"><span data-stu-id="3a7bb-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="3a7bb-107">入出力作成される [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) オブジェクトへのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3a7bb-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a7bb-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="3a7bb-108">Return Value</span></span>  

 <span data-ttu-id="3a7bb-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="3a7bb-109">S_OK</span></span>  
 <span data-ttu-id="3a7bb-110">プロセス内の CLR 数が正常に判別され、対応するハンドルとパスの配列が正しく入力されました。</span><span class="sxs-lookup"><span data-stu-id="3a7bb-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="3a7bb-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3a7bb-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="3a7bb-112">`ppTarget`  用に十分なメモリを割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="3a7bb-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="3a7bb-113">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="3a7bb-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="3a7bb-114">その他のエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3a7bb-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a7bb-115">要件</span><span class="sxs-lookup"><span data-stu-id="3a7bb-115">Requirements</span></span>  

 <span data-ttu-id="3a7bb-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a7bb-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a7bb-117">**ヘッダー:** Coreclrremoteデバッグインターフェイス .h</span><span class="sxs-lookup"><span data-stu-id="3a7bb-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="3a7bb-118">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="3a7bb-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="3a7bb-119">**.NET Framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="3a7bb-119">**.NET Framework Versions:** 3.5 SP1</span></span>
