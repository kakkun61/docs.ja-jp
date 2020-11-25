---
title: ICLRMetaHost インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
ms.openlocfilehash: 75c8d550e572795a291f4639f9f28bd5214ff188
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714017"
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="7f0fc-102">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7f0fc-102">ICLRMetaHost Interface</span></span>

<span data-ttu-id="7f0fc-103">バージョン番号に基づいて特定のバージョンの共通言語ランタイム (CLR) を返すメソッド、インストールされているすべての CLRs の一覧表示、指定されたプロセスに読み込まれたすべてのランタイムの一覧表示、アセンブリをコンパイルするために使用される CLR バージョンの検出、クリーンランタイムシャットダウンを使用したプロセスの終了、従来の API バインディングのクエリを</span><span class="sxs-lookup"><span data-stu-id="7f0fc-103">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7f0fc-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="7f0fc-104">Methods</span></span>  
  
|<span data-ttu-id="7f0fc-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7f0fc-105">Method</span></span>|<span data-ttu-id="7f0fc-106">説明</span><span class="sxs-lookup"><span data-stu-id="7f0fc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7f0fc-107">EnumerateInstalledRuntimes メソッド</span><span class="sxs-lookup"><span data-stu-id="7f0fc-107">EnumerateInstalledRuntimes Method</span></span>](iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="7f0fc-108">コンピューターにインストールされている各 CLR バージョンの有効な [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスポインターを含む列挙を返します。</span><span class="sxs-lookup"><span data-stu-id="7f0fc-108">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="7f0fc-109">EnumerateLoadedRuntimes メソッド</span><span class="sxs-lookup"><span data-stu-id="7f0fc-109">EnumerateLoadedRuntimes Method</span></span>](iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="7f0fc-110">指定されたプロセスに読み込まれる各 CLR の有効な [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスポインターを含む列挙体を返します。</span><span class="sxs-lookup"><span data-stu-id="7f0fc-110">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="7f0fc-111">このメソッドは、 [Getversionfromprocess](getversionfromprocess-function.md)よりも優先します。</span><span class="sxs-lookup"><span data-stu-id="7f0fc-111">This method supersedes [GetVersionFromProcess](getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="7f0fc-112">ExitProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="7f0fc-112">ExitProcess Method</span></span>](iclrmetahost-exitprocess-method.md)|<span data-ttu-id="7f0fc-113">読み込まれたすべてのランタイムを正常にシャットダウンしてから、プロセスを終了しようとします。</span><span class="sxs-lookup"><span data-stu-id="7f0fc-113">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="7f0fc-114">[CorExitProcess](corexitprocess-function.md)関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="7f0fc-114">Supersedes the [CorExitProcess](corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="7f0fc-115">GetRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="7f0fc-115">GetRuntime Method</span></span>](iclrmetahost-getruntime-method.md)|<span data-ttu-id="7f0fc-116">特定の CLR バージョンに対応する [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="7f0fc-116">Gets the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="7f0fc-117">このメソッドは、 [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md)フラグと共に使用される[Corbindtoruntimeex](corbindtoruntimeex-function.md)関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="7f0fc-117">This method supersedes the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="7f0fc-118">GetVersionFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="7f0fc-118">GetVersionFromFile Method</span></span>](iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="7f0fc-119">ファイルパスを指定して、アセンブリの元の .NET Framework コンパイルバージョン (メタデータに格納されている) を取得します。</span><span class="sxs-lookup"><span data-stu-id="7f0fc-119">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="7f0fc-120">このメソッドは、 [GetFileVersion](getfileversion-function.md)よりも優先します。</span><span class="sxs-lookup"><span data-stu-id="7f0fc-120">This method supersedes [GetFileVersion](getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="7f0fc-121">QueryLegacyV2RuntimeBinding メソッド</span><span class="sxs-lookup"><span data-stu-id="7f0fc-121">QueryLegacyV2RuntimeBinding Method</span></span>](iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="7f0fc-122">レガシアクティブ化ポリシーがバインドされているランタイムを表すインターフェイスを返します。たとえば、 `useLegacyV2RuntimeActivationPolicy` [ \<startup> 要素](../../configure-apps/file-schema/startup/startup-element.md)構成ファイルのエントリで属性を使用したり、レガシアクティベーション api を直接使用したり、 [ICLRRuntimeInfo:: BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md)メソッドを呼び出したりします。</span><span class="sxs-lookup"><span data-stu-id="7f0fc-122">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="7f0fc-123">RequestRuntimeLoadedNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="7f0fc-123">RequestRuntimeLoadedNotification Method</span></span>](iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="7f0fc-124">CLR バージョンが最初に読み込まれたが、まだ開始されていない場合は、指定された関数ポインターへのコールバックを保証します。</span><span class="sxs-lookup"><span data-stu-id="7f0fc-124">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="7f0fc-125">このメソッドは、 [Lockclrversion](lockclrversion-function.md)を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7f0fc-125">This method supersedes [LockClrVersion](lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f0fc-126">注釈</span><span class="sxs-lookup"><span data-stu-id="7f0fc-126">Remarks</span></span>  

 <span data-ttu-id="7f0fc-127">このインターフェイスのインスタンスを取得する唯一の方法は、 [Clrcreateinstance](clrcreateinstance-function.md) 関数を次のように呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7f0fc-127">The only way to get an instance of this interface is by calling the [CLRCreateInstance](clrcreateinstance-function.md) function as follows:</span></span>  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="7f0fc-128">要件</span><span class="sxs-lookup"><span data-stu-id="7f0fc-128">Requirements</span></span>  

 <span data-ttu-id="7f0fc-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f0fc-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f0fc-130">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="7f0fc-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7f0fc-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="7f0fc-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f0fc-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f0fc-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f0fc-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f0fc-133">See also</span></span>

- [<span data-ttu-id="7f0fc-134">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7f0fc-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="7f0fc-135">ホスティング</span><span class="sxs-lookup"><span data-stu-id="7f0fc-135">Hosting</span></span>](index.md)
