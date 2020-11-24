---
title: Silverlight デバッグ
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: 49f026b8e1a3dd78a62091e77a5aba0c9a2e09d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671838"
---
# <a name="silverlight-debugging"></a><span data-ttu-id="055e3-102">Silverlight デバッグ</span><span class="sxs-lookup"><span data-stu-id="055e3-102">Silverlight Debugging</span></span>

<span data-ttu-id="055e3-103">このセクションのトピックでは、Windows オペレーティング システム上または Macintosh プラットフォーム上で動作している Silverlight ベースのアプリケーションのデバッグをサポートするために共通言語ランタイム (CLR: Common Language Runtime) で提供される環境とインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="055e3-103">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="055e3-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="055e3-104">In This Section</span></span>  

 [<span data-ttu-id="055e3-105">EnumerateCLRs 関数</span><span class="sxs-lookup"><span data-stu-id="055e3-105">EnumerateCLRs Function</span></span>](enumerateclrs-function.md)  
 <span data-ttu-id="055e3-106">プロセスで CLR を列挙するメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="055e3-106">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="055e3-107">CloseCLREnumeration 関数</span><span class="sxs-lookup"><span data-stu-id="055e3-107">CloseCLREnumeration Function</span></span>](closeclrenumeration-function.md)  
 <span data-ttu-id="055e3-108">[列挙型 Ateclrs 関数](enumerateclrs-function.md)によって返されたハンドルの配列にある有効な CLR 継続スタートアップイベントを閉じ、ハンドルおよび文字列パス配列のメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="055e3-108">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="055e3-109">CreateCoreClrDebugTarget 関数</span><span class="sxs-lookup"><span data-stu-id="055e3-109">CreateCoreClrDebugTarget Function</span></span>](createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="055e3-110">プロセスおよびランタイムの列挙のためのリモート ターゲットへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="055e3-110">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="055e3-111">CreateCordbObject 関数</span><span class="sxs-lookup"><span data-stu-id="055e3-111">CreateCordbObject Function</span></span>](createcordbobject-function.md)  
 <span data-ttu-id="055e3-112">リモート プロセスでマネージド デバッグ セッションをインスタンス化するための機能を提供するデバッガー インターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="055e3-112">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="055e3-113">CreateVersionStringFromModule 関数</span><span class="sxs-lookup"><span data-stu-id="055e3-113">CreateVersionStringFromModule Function</span></span>](createversionstringfrommodule-function.md)  
 <span data-ttu-id="055e3-114">対象プロセス内の CLR パスからバージョン文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="055e3-114">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="055e3-115">CreateDebuggingInterfaceFromVersion 関数</span><span class="sxs-lookup"><span data-stu-id="055e3-115">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="055e3-116">[Createversionstringfrommodule 関数](createversionstringfrommodule-function.md)関数から返された CLR バージョン文字列を受け取り、対応するデバッガーインターフェイスを返します。</span><span class="sxs-lookup"><span data-stu-id="055e3-116">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="055e3-117">CoreClrDebugProcInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="055e3-117">CoreClrDebugProcInfo Structure</span></span>](coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="055e3-118">リモート コンピューターで実行されているプロセスを表します。</span><span class="sxs-lookup"><span data-stu-id="055e3-118">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="055e3-119">CoreClrDebugRuntimeInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="055e3-119">CoreClrDebugRuntimeInfo Structure</span></span>](coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="055e3-120">リモート コンピューター上のプロセスに読み込まれる CLR インスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="055e3-120">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="055e3-121">GetStartupNotificationEvent 関数</span><span class="sxs-lookup"><span data-stu-id="055e3-121">GetStartupNotificationEvent Function</span></span>](getstartupnotificationevent-function.md)  
 <span data-ttu-id="055e3-122">指定された対象プロセスに読み込まれている任意の共通言語ランタイム (CLR: Common Language Runtime) によって通知されるイベント ハンドルを作成または開きます。</span><span class="sxs-lookup"><span data-stu-id="055e3-122">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="055e3-123">ICoreClrDebugTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="055e3-123">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="055e3-124">プロセスおよびランタイムの列挙のためのリモート ターゲットへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="055e3-124">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="055e3-125">InitDbgTransportManager 関数</span><span class="sxs-lookup"><span data-stu-id="055e3-125">InitDbgTransportManager Function</span></span>](initdbgtransportmanager-function.md)  
 <span data-ttu-id="055e3-126">プロセスおよびランタイムの列挙のためにリモート ターゲットに接続するよう、トランスポート マネージャーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="055e3-126">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="055e3-127">ShutdownDbgTransportManager 関数</span><span class="sxs-lookup"><span data-stu-id="055e3-127">ShutdownDbgTransportManager Function</span></span>](shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="055e3-128">リモート ターゲット コンピューターへの接続のためにトランスポート マネージャーをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="055e3-128">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="055e3-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="055e3-129">See also</span></span>

- [<span data-ttu-id="055e3-130">デバッグ コクラス</span><span class="sxs-lookup"><span data-stu-id="055e3-130">Debugging Coclasses</span></span>](debugging-coclasses.md)
- [<span data-ttu-id="055e3-131">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="055e3-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="055e3-132">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="055e3-132">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
- [<span data-ttu-id="055e3-133">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="055e3-133">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="055e3-134">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="055e3-134">Debugging Structures</span></span>](debugging-structures.md)
