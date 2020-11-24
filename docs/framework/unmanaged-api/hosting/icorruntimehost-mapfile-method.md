---
title: ICorRuntimeHost::MapFile メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.MapFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::MapFile
helpviewer_keywords:
- ICorRuntimeHost::MapFile method [.NET Framework hosting]
- MapFile method [.NET Framework hosting]
ms.assetid: 45ae0502-0a31-4342-b7e3-f36e1cf738f3
topic_type:
- apiref
ms.openlocfilehash: 60e1d5d49f6f8c6fec060d8751e94410986aa3fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671383"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="201b8-102">ICorRuntimeHost::MapFile メソッド</span><span class="sxs-lookup"><span data-stu-id="201b8-102">ICorRuntimeHost::MapFile Method</span></span>

<span data-ttu-id="201b8-103">指定されたファイルをメモリにマップします。</span><span class="sxs-lookup"><span data-stu-id="201b8-103">Maps the specified file into memory.</span></span> <span data-ttu-id="201b8-104">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="201b8-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="201b8-105">構文</span><span class="sxs-lookup"><span data-stu-id="201b8-105">Syntax</span></span>  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="201b8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="201b8-106">Parameters</span></span>  

 `hFile`  
 <span data-ttu-id="201b8-107">からマップするファイルのハンドル。</span><span class="sxs-lookup"><span data-stu-id="201b8-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="201b8-108">入出力ファイルのマッピングを開始する開始メモリアドレス。</span><span class="sxs-lookup"><span data-stu-id="201b8-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="201b8-109">要件</span><span class="sxs-lookup"><span data-stu-id="201b8-109">Requirements</span></span>  

 <span data-ttu-id="201b8-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="201b8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="201b8-111">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="201b8-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="201b8-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="201b8-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="201b8-113">**.NET Framework バージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="201b8-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="201b8-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="201b8-114">See also</span></span>

- [<span data-ttu-id="201b8-115">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="201b8-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
