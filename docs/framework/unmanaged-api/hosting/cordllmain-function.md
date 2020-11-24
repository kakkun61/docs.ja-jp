---
title: _CorDllMain 関数
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
ms.openlocfilehash: 1b3ebcabc66ee7ca29245bb02d958be311bc65fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673697"
---
# <a name="_cordllmain-function"></a><span data-ttu-id="9165e-102">\_CorDllMain 関数</span><span class="sxs-lookup"><span data-stu-id="9165e-102">\_CorDllMain Function</span></span>

<span data-ttu-id="9165e-103">共通言語ランタイム (CLR) を初期化し、DLL アセンブリの CLR ヘッダー内のマネージエントリポイントを検索して、実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="9165e-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9165e-104">構文</span><span class="sxs-lookup"><span data-stu-id="9165e-104">Syntax</span></span>  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9165e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9165e-105">Parameters</span></span>  

 `hInst`  
 <span data-ttu-id="9165e-106">から読み込まれたモジュールのインスタンスハンドル。</span><span class="sxs-lookup"><span data-stu-id="9165e-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="9165e-107">からDLL のエントリポイント関数が呼び出される理由を示します。</span><span class="sxs-lookup"><span data-stu-id="9165e-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="9165e-108">このパラメーターには、DLL \_ PROCESS_ATTACH、dll \_ スレッド \_ のアタッチ、dll \_ スレッドの \_ アタッチ、または dll プロセスの \_ \_ デタッチのいずれかの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9165e-108">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="9165e-109">これらの値の詳細については、Platform SDK のドキュメントを参照してください `DllMain` 。</span><span class="sxs-lookup"><span data-stu-id="9165e-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="9165e-110">から未使用.</span><span class="sxs-lookup"><span data-stu-id="9165e-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9165e-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="9165e-111">Return Value</span></span>  

 <span data-ttu-id="9165e-112">このメソッドは `true` 、成功し `false` た場合はを返し、エラーが発生した場合はを返します。</span><span class="sxs-lookup"><span data-stu-id="9165e-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9165e-113">注釈</span><span class="sxs-lookup"><span data-stu-id="9165e-113">Remarks</span></span>  

 <span data-ttu-id="9165e-114">この関数は、DLL アセンブリのオペレーティングシステムローダーによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9165e-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="9165e-115">実行可能アセンブリの場合、ローダーは代わりに[ \_ CorExeMain](corexemain-function.md)関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9165e-115">For executable assemblies, the loader calls the [\_CorExeMain](corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="9165e-116">オペレーティングシステムローダーは、DLL ファイルで指定されたエントリポイントに関係なく、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9165e-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="9165e-117">`_CorDllMain`関数は、オペレーティングシステムローダーによって直接呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9165e-117">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="9165e-118">詳細については、 [ \_ corvalidateimage](corvalidateimage-function.md)トピックの「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9165e-118">For additional information, see the Remarks section in the [\_CorValidateImage](corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9165e-119">要件</span><span class="sxs-lookup"><span data-stu-id="9165e-119">Requirements</span></span>  

 <span data-ttu-id="9165e-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9165e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9165e-121">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="9165e-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9165e-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9165e-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9165e-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9165e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9165e-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="9165e-124">See also</span></span>

- [<span data-ttu-id="9165e-125">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="9165e-125">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
