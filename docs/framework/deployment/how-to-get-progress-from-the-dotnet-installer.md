---
title: '方法: .NET Framework 4.5 インストーラーの進行状況を表示する'
description: .NET Framework 4.5 インストーラーの進行状況を表示する方法について学習します。 このバージョンの .NET 用アプリを開発する場合は、アプリのセットアップに .NET Framework 4.5 セットアップを含める (チェーンする) ことができます。
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- progress information, .NET Framework installer
- .NET Framework, installing
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
ms.openlocfilehash: 7e21a376c5a7551ecadeaa70c0a70968dc5752fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729123"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a><span data-ttu-id="c5bf4-104">方法: .NET Framework 4.5 インストーラーの進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="c5bf4-104">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>

<span data-ttu-id="c5bf4-105">.NET Framework 4.5 は再頒布可能なランタイムです。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-105">The .NET Framework 4.5 is a redistributable runtime.</span></span> <span data-ttu-id="c5bf4-106">このバージョンの .NET Framework 用アプリを開発する場合は、アプリのセットアップに必要なパーツとして、.NET Framework 4.5 セットアップを含める (チェーンする) ことができます。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-106">If you develop apps for this version of the .NET Framework, you can include (chain) .NET Framework 4.5 setup as a prerequisite part of your app's setup.</span></span> <span data-ttu-id="c5bf4-107">セットアップ手順をカスタマイズまたは統一するために、アプリのセットアップの進行状況を表示しながら、.NET Framework 4.5 セットアップをサイレントで起動し、その進行状況を追跡できます。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-107">To present a customized or unified setup experience, you may want to silently launch .NET Framework 4.5 setup and track its progress while showing your app's setup progress.</span></span> <span data-ttu-id="c5bf4-108">サイレントな追跡を可能にするために、.NET Framework 4.5 セットアップ (監視対象) ではメモリ マップ I/O (MMIO) セグメントを使用することでプロトコルを定義し、セットアップ (ウォッチャーまたはチェーン元) と通信します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-108">To enable silent tracking, .NET Framework 4.5 setup (which can be watched) defines a protocol by using a memory-mapped I/O (MMIO) segment to communicate with your setup (the watcher or chainer).</span></span> <span data-ttu-id="c5bf4-109">このプロトコルは、チェーン元による進行状況情報の取得、詳細な結果の取得、メッセージへの応答、.NET Framework 4.5 セットアップの取り消しを行う方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-109">This protocol defines a way for a chainer to obtain progress information, get detailed results, respond to messages, and cancel the .NET Framework 4.5 setup.</span></span>

- <span data-ttu-id="c5bf4-110">**呼び出し**。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-110">**Invocation**.</span></span> <span data-ttu-id="c5bf4-111">.NET Framework 4.5 セットアップを呼び出して、MMIO セクションから進行状況情報を受け取るには、セットアップ プログラムで以下の処理を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-111">To call .NET Framework 4.5 setup and receive progress information from the MMIO section, your setup program must do the following:</span></span>

    1. <span data-ttu-id="c5bf4-112">.NET Framework 4.5 再頒布可能プログラムを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-112">Call the .NET Framework 4.5 redistributable program:</span></span>

        `dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name`

        <span data-ttu-id="c5bf4-113">この *section name* は、アプリの識別に使用する名前です。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-113">Where *section name* is any name you want to use to identify your app.</span></span> <span data-ttu-id="c5bf4-114">.NET Framework のセットアップでは MMIO セクションに対する読み書きを非同期に行うので、その間、イベントおよびメッセージの使用が役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-114">.NET Framework setup reads and writes to the MMIO section asynchronously, so you might find it convenient to use events and messages during that time.</span></span> <span data-ttu-id="c5bf4-115">この例では、.NETFramework セットアップ プロセスは、MMIO セクションの割り当て (`TheSectionName`) とイベントの定義 (`TheEventName`) の両方を行うコンストラクターによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-115">In the example, the .NET Framework setup process is created by a constructor that both allocates the MMIO section (`TheSectionName`) and defines an event (`TheEventName`):</span></span>

        ```cpp
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        <span data-ttu-id="c5bf4-116">これらの名前は、実際のセットアップ プログラムの固有な名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-116">Please replace those names with names that are unique to your setup program.</span></span>

    2. <span data-ttu-id="c5bf4-117">MMIO セクションから読み取ります。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-117">Read from the MMIO section.</span></span> <span data-ttu-id="c5bf4-118">.NET Framework 4.5 では、ダウンロード操作とインストール操作は同時に行われます。 .NET Framework の 1 つのパーツがインストールしている間に、別のパーツがダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-118">In the .NET Framework 4.5, the download and installation operations are simultaneous: One part of the .NET Framework might be installing while another part is downloading.</span></span> <span data-ttu-id="c5bf4-119">その結果、進行状況は、0 から 255 まで増加する 2 つの値 (`m_downloadSoFar` および `m_installSoFar`) として MMIO セクションに送り返されます (書き込まれます)。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-119">As a result, progress is sent back (that is, written) to the MMIO section as two numbers (`m_downloadSoFar` and `m_installSoFar`) that increase from 0 to 255.</span></span> <span data-ttu-id="c5bf4-120">255 が書き込まれて、.NET Framework が終了すると、インストールは完了します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-120">When 255 is written and the .NET Framework exits, the installation is complete.</span></span>

- <span data-ttu-id="c5bf4-121">**終了コード**。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-121">**Exit codes**.</span></span> <span data-ttu-id="c5bf4-122">.NET Framework 4.5 再頒布可能プログラムを呼び出すためのコマンドからの以下の終了コードは、セットアップが成功または失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-122">The following exit codes from the command to call the .NET Framework 4.5 redistributable program indicate whether setup has succeeded or failed:</span></span>

  - <span data-ttu-id="c5bf4-123">0: セットアップは、正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-123">0 - Setup completed successfully.</span></span>

  - <span data-ttu-id="c5bf4-124">3010: セットアップは正常に完了しました。システムの再起動が必要です。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-124">3010 – Setup completed successfully; a system restart is required.</span></span>

  - <span data-ttu-id="c5bf4-125">1602: セットアップは取り消されました。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-125">1602 – Setup has been canceled.</span></span>

  - <span data-ttu-id="c5bf4-126">他のすべてのコード: セットアップでエラーが発生しました。詳細については、%temp% に作成されるログ ファイルを調べてください。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-126">All other codes - Setup encountered errors; examine the log files created in %temp% for details.</span></span>

- <span data-ttu-id="c5bf4-127">**セットアップの取り消し**。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-127">**Canceling setup**.</span></span> <span data-ttu-id="c5bf4-128">`Abort` メソッドを使用して MMIO セクションの `m_downloadAbort` フラグと `m_ installAbort` フラグを設定することで、いつでもセットアップを取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-128">You can cancel setup at any time by using the `Abort` method to set the `m_downloadAbort` and `m_ installAbort` flags in the MMIO section.</span></span>

## <a name="chainer-sample"></a><span data-ttu-id="c5bf4-129">チェーン元のサンプル</span><span class="sxs-lookup"><span data-stu-id="c5bf4-129">Chainer Sample</span></span>

<span data-ttu-id="c5bf4-130">チェーン元のサンプルが、進行状況を表示しながらサイレントで起動し、.NET Framework 4.5 セットアップを追跡します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-130">The Chainer sample silently launches and tracks .NET Framework 4.5 setup while showing progress.</span></span> <span data-ttu-id="c5bf4-131">このサンプルは、.NET Framework 4 用のチェーン元サンプルに似ています。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-131">This sample is similar to the Chainer sample provided for the .NET Framework 4.</span></span> <span data-ttu-id="c5bf4-132">ただし、.NET Framework 4 アプリケーションを閉じるためのメッセージ ボックスを処理することで、システムの再起動を避けることができます。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-132">However, in addition, it can avoid system restarts by processing the message box for closing .NET Framework 4 apps.</span></span> <span data-ttu-id="c5bf4-133">このメッセージ ボックスの詳細については、「[.NET Framework 4.5 のインストール中のシステム再起動の削減](reducing-system-restarts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-133">For information about this message box, see [Reducing System Restarts During .NET Framework 4.5 Installations](reducing-system-restarts.md).</span></span> <span data-ttu-id="c5bf4-134">このサンプルは .NET Framework 4 インストーラーで使用できます。そのシナリオではメッセージは送信されません。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-134">You can use this sample with the .NET Framework 4 installer; in that scenario, the message is simply not sent.</span></span>

> [!WARNING]
> <span data-ttu-id="c5bf4-135">例の実行は、管理者として行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-135">You must run the example as an administrator.</span></span>

<span data-ttu-id="c5bf4-136">MSDN サンプル ギャラリーから [.NET Framework 4.5 チェーン元のサンプル](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba)の完全な Visual Studio ソリューションをダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-136">You can download the complete Visual Studio solution for the [.NET Framework 4.5 Chainer Sample](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) from the MSDN Samples Gallery.</span></span>

<span data-ttu-id="c5bf4-137">以下のセクションでは、この例の重要なファイルである MMIOChainer.h、ChainingdotNet4.cpp、および IProgressObserver.h について説明します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-137">The following sections describe the significant files in this sample: MMIOChainer.h, ChainingdotNet4.cpp, and IProgressObserver.h.</span></span>

#### <a name="mmiochainerh"></a><span data-ttu-id="c5bf4-138">MMIOChainer.h</span><span class="sxs-lookup"><span data-stu-id="c5bf4-138">MMIOChainer.h</span></span>

- <span data-ttu-id="c5bf4-139">MMIOChainer.h ファイル ([完全なコード](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)を参照) には、データ構造体の定義と、チェーン元クラスが派生する基底クラスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-139">The MMIOChainer.h file (see [complete code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)) contains the data structure definition and the base class from which the chainer class should be derived.</span></span> <span data-ttu-id="c5bf4-140">.NET Framework 4.5 によって、MMIO データ構造体が拡張され、.NET Framework 4.5 インストーラーが必要とするデータが処理されます。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-140">The .NET Framework 4.5 extends the MMIO data structure to handle data that the .NET Framework 4.5 installer needs.</span></span> <span data-ttu-id="c5bf4-141">MMIO 構造体への変更には下位互換性があるため、.NET Framework 4 チェーン元は、再コンパイルを必要とせずに .NET Framework 4.5 のセットアップで機能します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-141">The changes to the MMIO structure are backward-compatible, so a .NET Framework 4 chainer can work with .NET Framework 4.5 setup without requiring recompilation.</span></span> <span data-ttu-id="c5bf4-142">ただし、このシナリオはシステムの再起動を削減するための機能をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-142">However, this scenario does not support the feature for reducing system restarts.</span></span>

    <span data-ttu-id="c5bf4-143">バージョン フィールドは、構造体およびメッセージ形式へのリビジョンを識別するための手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-143">A version field provides a means of identifying revisions to the structure and message format.</span></span> <span data-ttu-id="c5bf4-144">.NET Framework セットアップでは、`VirtualQuery` 関数を呼び出してファイル マップのサイズを判断することで、チェーン元インターフェイスのバージョンを判別します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-144">The .NET Framework setup determines the version of the chainer interface by calling the `VirtualQuery` function to determine the size of the file mapping.</span></span> <span data-ttu-id="c5bf4-145">サイズがバージョン フィールドに対応できる十分な大きさである場合、.NET Framework セットアップでは指定された値を使用します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-145">If the size is large enough to accommodate the version field, .NET Framework setup uses the specified value.</span></span> <span data-ttu-id="c5bf4-146">.NET Framework 4 の場合のように、バージョン フィールドを含めるにはファイル マップが小さすぎる場合、セットアップ プロセスではバージョン 0 (4) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-146">If the file mapping is too small to contain a version field, which is the case with the .NET Framework 4, the setup process assumes version 0 (4).</span></span> <span data-ttu-id="c5bf4-147">.NET Framework セットアップが送信しようとするメッセージのバージョンをチェーン元がサポートしていない場合、.NET Framework セットアップでは応答を無視します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-147">If the chainer does not support the version of the message that .NET Framework setup wants to send, .NET Framework setup assumes an ignore response.</span></span>

    <span data-ttu-id="c5bf4-148">MMIO データ構造体は以下のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-148">The MMIO data structure is defined as follows:</span></span>

    ```cpp
    // MMIO data structure for interprocess communication
        struct MmioDataStructure
        {
            bool m_downloadFinished;               // Is download complete?
            bool m_installFinished;                // Is installation complete?
            bool m_downloadAbort;                  // Set to cause downloader to abort.
            bool m_installAbort;                   // Set to cause installer to abort.
            HRESULT m_hrDownloadFinished;          // Resulting HRESULT for download.
            HRESULT m_hrInstallFinished;           // Resulting HRESULT for installation.
            HRESULT m_hrInternalError;
            WCHAR m_szCurrentItemStep[MAX_PATH];
            unsigned char m_downloadSoFar;         // Download progress 0-255 (0-100% done).
            unsigned char m_installSoFar;          // Installation progress 0-255 (0-100% done).
            WCHAR m_szEventName[MAX_PATH];         // Event that chainer creates and chainee opens to sync communications.

            BYTE m_version;                        // Version of the data structure, set by chainer:
                                                   // 0x0: .NET Framework 4
                                                   // 0x1: .NET Framework 4.5

            DWORD m_messageCode;                   // Current message sent by the chainee; 0 if no message is active.
            DWORD m_messageResponse;               // Chainer's response to current message; 0 if not yet handled.
            DWORD m_messageDataLength;             // Length of the m_messageData field, in bytes.
            BYTE m_messageData[1];                 // Variable-length buffer; content depends on m_messageCode.
        };
    ```

- <span data-ttu-id="c5bf4-149">`MmioDataStructure` データ構造体を直接使用するのではなく、チェーン元を実装するための `MmioChainer` クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-149">The `MmioDataStructure` data structure should not be used directly; use the `MmioChainer` class instead to implement your chainer.</span></span> <span data-ttu-id="c5bf4-150">`MmioChainer` クラスから派生させて、.NET Framework 4.5 再頒布可能プログラムをチェーンします。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-150">Derive from the `MmioChainer` class to chain the .NET Framework 4.5 redistributable.</span></span>

#### <a name="iprogressobserverh"></a><span data-ttu-id="c5bf4-151">IProgressObserver.h</span><span class="sxs-lookup"><span data-stu-id="c5bf4-151">IProgressObserver.h</span></span>

- <span data-ttu-id="c5bf4-152">IProgressObserver.h ファイルは進行状況のオブザーバー ([完全なコードを参照](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)) を実装します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-152">The IProgressObserver.h file implements a progress observer ([see complete code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)).</span></span> <span data-ttu-id="c5bf4-153">このオブザーバーは、ダウンロードとインストールの進行状況 (1% ～ 100% 完了を示す、符号なしの `char` 0 ～ 255 の値で指定) の通知を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-153">This observer gets notified of download and installation progress (specified as an unsigned `char`, 0-255, indicating 1%-100% complete).</span></span> <span data-ttu-id="c5bf4-154">オブザーバーは、チェーン対象がメッセージを送信したときにも通知を受け取ります。通知を受け取ったオブザーバーは、応答を送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-154">The observer is also notified when the chainee sends a message, and the observer should send a response.</span></span>

    ```cpp
        class IProgressObserver
        {
        public:
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent
        };
    ```

#### <a name="chainingdotnet45cpp"></a><span data-ttu-id="c5bf4-155">ChainingdotNet4.5.cpp</span><span class="sxs-lookup"><span data-stu-id="c5bf4-155">ChainingdotNet4.5.cpp</span></span>

- <span data-ttu-id="c5bf4-156">[ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) ファイルは、`Server` クラスを実装します。このクラスは `MmioChainer` クラスから派生し、適切なメソッドをオーバーライドして進行状況情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-156">The [ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) file implements the `Server` class, which derives from the `MmioChainer` class and overrides the appropriate methods to display progress information.</span></span> <span data-ttu-id="c5bf4-157">MmioChainer は、指定されたセクション名でセクションを作成し、指定されたイベント名でチェーン元を初期化します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-157">The MmioChainer creates a section with the specified section name and initializes the chainer with the specified event name.</span></span> <span data-ttu-id="c5bf4-158">イベント名は、マップされたデータ構造体に保存されます。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-158">The event name is saved in the mapped data structure.</span></span> <span data-ttu-id="c5bf4-159">セクションとイベント名は一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-159">You should make the section and event names unique.</span></span> <span data-ttu-id="c5bf4-160">次のコードの `Server` クラスは、指定されたセットアップ プログラムを起動して進行状況を監視し、終了コードを返します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-160">The `Server` class in the following code launches the specified setup program, monitors its progress, and returns an exit code.</span></span>

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    <span data-ttu-id="c5bf4-161">インストールが Main メソッドで開始されます。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-161">The installation is started in the Main method.</span></span>

    ```cpp
    // Main entry point for program
    int __cdecl main(int argc, _In_count_(argc) char **_argv)
    {
        int result = 0;
        CString args;
        if (argc > 1)
        {
            args = CString(_argv[1]);
        }

        if (IsNetFx4Present(NETFX45_RC_REVISION))
        {
            printf(".NET Framework 4.5 is already installed");
        }
        else
        {
            result = Server().Launch(args);
        }

        return result;
    }
    ```

- <span data-ttu-id="c5bf4-162">インストールを始める前に、チェーン元では `IsNetFx4Present` を呼び出して、.NET Framework 4.5 が既にインストールされているかどうかの確認が行われます。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-162">Before launching the installation, the chainer checks to see if the .NET Framework 4.5 is already installed by calling `IsNetFx4Present`:</span></span>

    ```cpp
    ///  Checks for presence of the .NET Framework 4.
    ///    A value of 0 for dwMinimumRelease indicates a check for the .NET Framework 4 full
    ///    Any other value indicates a check for a specific compatible release of the .NET Framework 4.
    #define NETFX40_FULL_REVISION 0
    // TODO: Replace with released revision number
    #define NETFX45_RC_REVISION MAKELONG(50309, 5)   // .NET Framework 4.5
    bool IsNetFx4Present(DWORD dwMinimumRelease)
    {
        DWORD dwError = ERROR_SUCCESS;
        HKEY hKey = NULL;
        DWORD dwData = 0;
        DWORD dwType = 0;
        DWORD dwSize = sizeof(dwData);

        dwError = ::RegOpenKeyExW(HKEY_LOCAL_MACHINE, L"SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full", 0, KEY_READ, &hKey);
        if (ERROR_SUCCESS == dwError)
        {
            dwError = ::RegQueryValueExW(hKey, L"Release", 0, &dwType, (LPBYTE)&dwData, &dwSize);

            if ((ERROR_SUCCESS == dwError) && (REG_DWORD != dwType))
            {
                dwError = ERROR_INVALID_DATA;
            }
            else if (ERROR_FILE_NOT_FOUND == dwError)
            {
                // Release value was not found, let's check for 4.0.
                dwError = ::RegQueryValueExW(hKey, L"Install", 0, &dwType, (LPBYTE)&dwData, &dwSize);

                // Install = (REG_DWORD)1;
                if ((ERROR_SUCCESS == dwError) && (REG_DWORD == dwType) && (dwData == 1))
                {
                    // treat 4.0 as Release = 0
                    dwData = 0;
                }
                else
                {
                    dwError = ERROR_INVALID_DATA;
                }
            }
        }

        if (hKey != NULL)
        {
            ::RegCloseKey(hKey);
        }

        return ((ERROR_SUCCESS == dwError) && (dwData >= dwMinimumRelease));
    }
    ```

- <span data-ttu-id="c5bf4-163">`Launch` メソッド内の実行可能ファイル (例では Setup.exe) のパスを正しい場所に変更するか、コードをカスタマイズして場所を判断することができます。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-163">You can change the path of the executable (Setup.exe in the example) in the `Launch` method to point to its correct location, or customize the code to determine the location.</span></span> <span data-ttu-id="c5bf4-164">`MmioChainer` 基底クラスは、派生クラスが呼び出すブロッキング `Run()` メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-164">The `MmioChainer` base class provides a blocking `Run()` method that the derived class calls.</span></span>

    ```cpp
    bool Launch(const CString& args)
    {
    CString cmdline = L"dotNetFx45_Full_x86_x64.exe -pipe TheSectionName " + args; // Customize with name and location of setup .exe that you want to run
    STARTUPINFO si = {0};
    si.cb = sizeof(si);
    PROCESS_INFORMATION pi = {0};

    // Launch the Setup.exe that installs the .NET Framework 4.5
    BOOL bLaunchedSetup = ::CreateProcess(NULL,
     cmdline.GetBuffer(),
     NULL, NULL, FALSE, 0, NULL, NULL,
     &si,
     &pi);

    // If successful
    if (bLaunchedSetup != 0)
    {
    IProgressObserver& observer = dynamic_cast<IProgressObserver&>(*this);
    Run(pi.hProcess, observer);

    ……………………..
    return (bLaunchedSetup != 0);
    }
    ```

- <span data-ttu-id="c5bf4-165">`Send` メソッドはメッセージを途中受信して処理します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-165">The `Send` method intercepts and processes the messages.</span></span> <span data-ttu-id="c5bf4-166">このバージョンの .NET Framework では、サポートされているメッセージはアプリケーションの終了メッセージのみです。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-166">In this version of the .NET Framework, the only supported message is the close application message.</span></span>

    ```cpp
            // SendMessage
            //
            // Send a message and wait for the response.
            // dwMessage: Message to send
            // pData: The buffer to copy the data to
            // dwDataLength: Initially a pointer to the size of pBuffer. Upon successful call, the number of bytes copied to pBuffer.
            //--------------------------------------------------------------
        virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength)
        {
            DWORD dwResult = 0;
            printf("received message: %d\n", dwMessage);
            // Handle message
            switch (dwMessage)
            {
            case MMIO_CLOSE_APPS:
                {
                    printf("    applications are holding files in use:\n");
                    IronMan::MmioCloseApplications* applications = reinterpret_cast<IronMan::MmioCloseApplications*>(pData);
                    for(DWORD i = 0; i < applications->m_dwApplicationsSize; i++)
                    {
                        printf("      %ls (%d)\n", applications->m_applications[i].m_szName, applications->m_applications[i].m_dwPid);
                    }

                    printf("    should appliations be closed? (Y)es, (N)o, (R)efresh : ");
                    while (dwResult == 0)
                    {
                        switch (toupper(getwchar()))
                        {
                        case 'Y':
                            dwResult = IDYES;  // Close apps
                            break;
                        case 'N':
                            dwResult = IDNO;
                            break;
                        case 'R':
                            dwResult = IDRETRY;
                            break;
                        }
                    }
                    printf("\n");
                    break;
                }
            default:
                break;
            }
            printf("  response: %d\n  ", dwResult);
            return dwResult;
        }
    };
    ```

- <span data-ttu-id="c5bf4-167">進行状況のデータは、0 (0%) ～ 255 (100%) の範囲の符号なし `char` です。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-167">Progress data is an unsigned `char` between 0 (0%) and 255 (100%).</span></span>

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- <span data-ttu-id="c5bf4-168">HRESULT は、`Finished` メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-168">The HRESULT is passed to the `Finished` method.</span></span>

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="c5bf4-169">.NET Framework 4.5 の再頒布可能プログラムによって、通常、多数の進行状況メッセージと、(チェーン元側で) 完了を示す 1 つのメッセージが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-169">The .NET Framework 4.5 redistributable typically writes many progress messages and a single message that indicates completion (on the chainer side).</span></span> <span data-ttu-id="c5bf4-170">また、非同期に読み取りを行って、`Abort` レコードを探します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-170">It also reads asynchronously, looking for `Abort` records.</span></span> <span data-ttu-id="c5bf4-171">`Abort` レコードを受け取った場合は、インストールを取り消し、インストールが中止され、セットアップ操作がロールバックされた後に、データとして E_ABORT を含む終了レコードを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-171">If it receives an `Abort` record, it cancels the installation, and writes a finished record with E_ABORT as its data after the installation has been aborted and setup operations have been rolled back.</span></span>

<span data-ttu-id="c5bf4-172">標準的なサーバーは、ランダムな MMIO ファイル名を作成し、ファイル (前のコード例の `Server::CreateSection` で示されているファイル) を作成した後、`CreateProcess` メソッドを使用して `-pipe someFileSectionName` オプションでパイプ名を渡すことによって、再頒布可能プログラムを起動します。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-172">A typical server creates a random MMIO file name, creates the file (as shown in the previous code example, in `Server::CreateSection`), and launches the redistributable by using the `CreateProcess` method and passing the pipe name with the `-pipe someFileSectionName` option.</span></span> <span data-ttu-id="c5bf4-173">サーバーは、アプリケーションの UI 固有のコードを使用して `OnProgress`、`Send`、および `Finished` の各メソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5bf4-173">The server should implement `OnProgress`, `Send`, and `Finished` methods with application UI-specific code.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5bf4-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5bf4-174">See also</span></span>

- [<span data-ttu-id="c5bf4-175">配置ガイド (開発者向け)</span><span class="sxs-lookup"><span data-stu-id="c5bf4-175">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)
- [<span data-ttu-id="c5bf4-176">配置</span><span class="sxs-lookup"><span data-stu-id="c5bf4-176">Deployment</span></span>](index.md)
