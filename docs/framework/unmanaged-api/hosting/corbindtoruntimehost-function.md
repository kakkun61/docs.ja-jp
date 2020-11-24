---
title: CorBindToRuntimeHost 関数
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeHost
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeHost
helpviewer_keywords:
- CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type:
- apiref
ms.openlocfilehash: 7ba35823ccb670ad0201d1950687dc83cc9ba64a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673745"
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="5f58b-102">CorBindToRuntimeHost 関数</span><span class="sxs-lookup"><span data-stu-id="5f58b-102">CorBindToRuntimeHost Function</span></span>

<span data-ttu-id="5f58b-103">ホストが、指定したバージョンの共通言語ランタイム (CLR: Common Language Runtime) をプロセスに読み込むことができるようにします。</span><span class="sxs-lookup"><span data-stu-id="5f58b-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="5f58b-104">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="5f58b-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f58b-105">構文</span><span class="sxs-lookup"><span data-stu-id="5f58b-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,
    [in] LPCWSTR       pwszBuildFlavor,
    [in] LPCWSTR       pwszHostConfigFile,
    [in] VOID*         pReserved,
    [in] DWORD         startupFlags,
    [in] REFCLSID      rclsid,
    [in] REFIID        riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f58b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5f58b-106">Parameters</span></span>  

 `pwszVersion`  
 <span data-ttu-id="5f58b-107">[入力] 読み込む CLR のバージョンを示す文字列。</span><span class="sxs-lookup"><span data-stu-id="5f58b-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="5f58b-108">.NET Framework のバージョン番号は、ピリオドで *区切られた* 4 つの部分で構成されます。</span><span class="sxs-lookup"><span data-stu-id="5f58b-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="5f58b-109">`pwszVersion` として渡される文字列は、文字 "v" で始まり、バージョン番号の最初の 3 つの部分がその後に続く必要があります (たとえば "v1.0.1529")。</span><span class="sxs-lookup"><span data-stu-id="5f58b-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="5f58b-110">いくつかのバージョンの CLR は、以前のバージョンの CLR との互換性を指定するポリシー ステートメントと共にインストールされています。</span><span class="sxs-lookup"><span data-stu-id="5f58b-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="5f58b-111">既定では、スタートアップ shim により、ポリシー ステートメントに対して `pwszVersion` が評価され、要求されたバージョンと互換性がある最新バージョンのランタイムが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="5f58b-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="5f58b-112">ホストは shim に対し、`pwszVersion` パラメーターで値 STARTUP_LOADER_SAFEMODE を渡すことにより、ポリシー評価を省略し、`startupFlags` で指定されたバージョンとまったく同じバージョンを読み込ませることができます。</span><span class="sxs-lookup"><span data-stu-id="5f58b-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="5f58b-113">`pwszVersion` が `null,` の場合、メソッドはどのバージョンの CLR も読み込みません。</span><span class="sxs-lookup"><span data-stu-id="5f58b-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="5f58b-114">代わりに、ランタイムの読み込みに失敗したことを示す CLR_E_SHIM_RUNTIMELOAD が返されます。</span><span class="sxs-lookup"><span data-stu-id="5f58b-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="5f58b-115">[入力] CLR のサーバー ビルドまたはワークステーション ビルドのどちらを読み込むかを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="5f58b-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="5f58b-116">有効な値は `svr` と `wks` です。</span><span class="sxs-lookup"><span data-stu-id="5f58b-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="5f58b-117">ワークステーション ビルドはシングルプロセッサ コンピューターでクライアント アプリケーションを実行するために最適化され、サーバー ビルドはガベージ コレクションでマルチ プロセッサを利用するために最適化されています。</span><span class="sxs-lookup"><span data-stu-id="5f58b-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="5f58b-118">`pwszBuildFlavor`が null に設定されている場合、ワークステーションのビルドが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="5f58b-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="5f58b-119">をシングルプロセッサコンピューターで実行する場合、がに設定されていても、ワークステーションのビルドは常に読み込まれ `pwszBuildFlavor` `svr` ます。</span><span class="sxs-lookup"><span data-stu-id="5f58b-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="5f58b-120">ただし、 `pwszBuildFlavor` がに設定され、 `svr` 同時実行ガベージコレクションが指定されている場合 (パラメーターの説明を参照 `startupFlags` )、サーバービルドが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="5f58b-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f58b-121">同時実行ガベージ コレクションは、Intel Itanium アーキテクチャ (以前の IA-64) を実装する 64 ビット システム上で WOW64 x86 エミュレーターを実行しているアプリケーションではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="5f58b-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="5f58b-122">64ビット Windows システムでの WOW64 の使用の詳細については、「 [32 ビットアプリケーションの実行](/windows/desktop/WinProg64/running-32-bit-applications)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f58b-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="5f58b-123">[入力] 読み込む CLR のバージョンを指定するホスト構成ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="5f58b-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="5f58b-124">ファイル名に絶対パスが含まれていない場合、ファイルは呼び出しを行った実行可能ファイルと同じディレクトリにあるものと見なされます。</span><span class="sxs-lookup"><span data-stu-id="5f58b-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="5f58b-125">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="5f58b-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="5f58b-126">[入力] 同時実行ガベージ コレクション、ドメインに中立なコード、および `pwszVersion` パラメーターの動作を制御するフラグのセット。</span><span class="sxs-lookup"><span data-stu-id="5f58b-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="5f58b-127">どのフラグも設定されていない場合は、既定はシングル ドメインになります。</span><span class="sxs-lookup"><span data-stu-id="5f58b-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="5f58b-128">サポートされている値の一覧については、 [STARTUP_FLAGS 列挙体](startup-flags-enumeration.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f58b-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="5f58b-129">から `CLSID` [ICorRuntimeHost](icorruntimehost-interface.md) または [ICLRRuntimeHost](iclrruntimehost-interface.md) のいずれかのインターフェイスを実装するコクラスの。</span><span class="sxs-lookup"><span data-stu-id="5f58b-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="5f58b-130">サポートされている値は CLSID_CorRuntimeHost と CLSID_CLRRuntimeHost です。</span><span class="sxs-lookup"><span data-stu-id="5f58b-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="5f58b-131">[入力] 要求するインターフェイスの `IID`。</span><span class="sxs-lookup"><span data-stu-id="5f58b-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="5f58b-132">サポートされている値は IID_ICorRuntimeHost と IID_ICLRRuntimeHost です。</span><span class="sxs-lookup"><span data-stu-id="5f58b-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="5f58b-133">[出力] 読み込まれたランタイムのバージョンへのインターフェイス ポインター。</span><span class="sxs-lookup"><span data-stu-id="5f58b-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f58b-134">要件</span><span class="sxs-lookup"><span data-stu-id="5f58b-134">Requirements</span></span>  

 <span data-ttu-id="5f58b-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f58b-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f58b-136">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5f58b-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="5f58b-137">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5f58b-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f58b-138">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f58b-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f58b-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f58b-139">See also</span></span>

- [<span data-ttu-id="5f58b-140">CorBindToCurrentRuntime 関数</span><span class="sxs-lookup"><span data-stu-id="5f58b-140">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="5f58b-141">CorBindToRuntime 関数</span><span class="sxs-lookup"><span data-stu-id="5f58b-141">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="5f58b-142">CorBindToRuntimeByCfg 関数</span><span class="sxs-lookup"><span data-stu-id="5f58b-142">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="5f58b-143">CorBindToRuntimeEx 関数</span><span class="sxs-lookup"><span data-stu-id="5f58b-143">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="5f58b-144">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f58b-144">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="5f58b-145">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="5f58b-145">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
