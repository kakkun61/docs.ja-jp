---
title: CorBindToCurrentRuntime 関数
ms.date: 03/30/2017
api_name:
- CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- HeaderDef
f1_keywords:
- CorBindToCurrentRuntime
helpviewer_keywords:
- CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type:
- apiref
ms.openlocfilehash: 4a8ab6e1aeedef5b821fc977387b8039f54edd64
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682498"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="9854f-102">CorBindToCurrentRuntime 関数</span><span class="sxs-lookup"><span data-stu-id="9854f-102">CorBindToCurrentRuntime Function</span></span>

<span data-ttu-id="9854f-103">XML ファイルに格納されているバージョン情報を使用して、共通言語ランタイム (CLR: Common Language Runtime) をプロセスに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="9854f-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="9854f-104">XML ファイルの形式は、標準のアプリケーション構成ファイルの後にモデル化されています。</span><span class="sxs-lookup"><span data-stu-id="9854f-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="9854f-105">構成ファイルの詳細については、「[構成ファイル スキーマ](../../configure-apps/file-schema/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9854f-105">For more information about configuration files, see [Configuration File Schema](../../configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="9854f-106">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="9854f-106">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="9854f-107">「 [プロセスへの共通言語ランタイムの読み込み](/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9854f-107">See [Loading the Common Language Runtime into a Process](/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9854f-108">構文</span><span class="sxs-lookup"><span data-stu-id="9854f-108">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9854f-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9854f-109">Parameters</span></span>  

 `pwszFileName`  
 <span data-ttu-id="9854f-110">から読み込む CLR のバージョンを指定するアプリケーション構成ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="9854f-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="9854f-111">ファイル名が完全修飾されていない場合は、呼び出しを行った実行可能ファイルと同じディレクトリに存在すると見なされます。</span><span class="sxs-lookup"><span data-stu-id="9854f-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="9854f-112">読み込むランタイムのバージョンは、構成ファイルの要素の version 属性によって記述され [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="9854f-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="9854f-113">バージョンが指定されていない場合、または要素が見つからない場合は、 `<requiredRuntime>` コンピューターにインストールされている最新バージョンの CLR が読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="9854f-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="9854f-114">から `CLSID` [ICorRuntimeHost](icorruntimehost-interface.md) または [ICLRRuntimeHost](iclrruntimehost-interface.md) のいずれかのインターフェイスを実装するコクラスの。</span><span class="sxs-lookup"><span data-stu-id="9854f-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="9854f-115">サポートされている値は CLSID_CorRuntimeHost と CLSID_CLRRuntimeHost です。</span><span class="sxs-lookup"><span data-stu-id="9854f-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="9854f-116">[入力] 要求するインターフェイスの `IID`。</span><span class="sxs-lookup"><span data-stu-id="9854f-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="9854f-117">サポートされている値は IID_ICorRuntimeHost と IID_ICLRRuntimeHost です。</span><span class="sxs-lookup"><span data-stu-id="9854f-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="9854f-118">入出力返されたインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="9854f-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9854f-119">要件</span><span class="sxs-lookup"><span data-stu-id="9854f-119">Requirements</span></span>  

 <span data-ttu-id="9854f-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9854f-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9854f-121">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9854f-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9854f-122">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9854f-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9854f-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9854f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9854f-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="9854f-124">See also</span></span>

- [<span data-ttu-id="9854f-125">CorBindToRuntime 関数</span><span class="sxs-lookup"><span data-stu-id="9854f-125">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="9854f-126">CorBindToRuntimeByCfg 関数</span><span class="sxs-lookup"><span data-stu-id="9854f-126">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="9854f-127">CorBindToRuntimeEx 関数</span><span class="sxs-lookup"><span data-stu-id="9854f-127">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="9854f-128">CorBindToRuntimeHost 関数</span><span class="sxs-lookup"><span data-stu-id="9854f-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="9854f-129">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9854f-129">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="9854f-130">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="9854f-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
