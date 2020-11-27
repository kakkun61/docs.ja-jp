---
title: セットアップに関する問題のトラブルシューティング
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 596aae345061796535895a091c59d50a5bffe0d8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255118"
---
# <a name="troubleshoot-setup-issues"></a><span data-ttu-id="e2a1f-102">セットアップに関する問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e2a1f-102">Troubleshoot setup issues</span></span>

<span data-ttu-id="e2a1f-103">この記事では、Windows Communication Foundation (WCF) セットアップの問題をトラブルシューティングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-103">This article describes how to troubleshoot Windows Communication Foundation (WCF) setup issues.</span></span>  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a><span data-ttu-id="e2a1f-104">.NET Framework 3.0 の MSI 修復操作の実行では修復されない一部の Windows Communication Foundation レジストリ キー</span><span class="sxs-lookup"><span data-stu-id="e2a1f-104">Some Windows Communication Foundation Registry Keys are not Repaired by Performing an MSI Repair Operation on the .NET Framework 3.0</span></span>  

 <span data-ttu-id="e2a1f-105">次のいずれかのレジストリ キーを削除した場合</span><span class="sxs-lookup"><span data-stu-id="e2a1f-105">If you delete any of the following registry keys:</span></span>  
  
- <span data-ttu-id="e2a1f-106">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="e2a1f-106">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0</span></span>  
  
- <span data-ttu-id="e2a1f-107">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="e2a1f-107">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0</span></span>  
  
- <span data-ttu-id="e2a1f-108">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="e2a1f-108">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0</span></span>  
  
- <span data-ttu-id="e2a1f-109">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="e2a1f-109">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0</span></span>  
  
- <span data-ttu-id="e2a1f-110">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="e2a1f-110">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0</span></span>  
  
 <span data-ttu-id="e2a1f-111">**コントロールパネル** の [**プログラムの追加と削除**] アプレットから起動した .NET Framework 3.0 インストーラーを使用して修復を実行した場合、キーは再作成されません。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-111">The keys are not re-created if you run repair by using the .NET Framework 3.0 installer launched from the **Add/Remove Programs** applet in **Control Panel**.</span></span> <span data-ttu-id="e2a1f-112">これらのキーを正しく再作成するには、.NET Framework 3.0 をアンインストール後、再インストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-112">To recreate these keys correctly, the user must uninstall and reinstall the .NET Framework 3.0.</span></span>  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-wmi-provider"></a><span data-ttu-id="e2a1f-113">Wmi サービスの破損によって WMI プロバイダーのインストールがブロックされる</span><span class="sxs-lookup"><span data-stu-id="e2a1f-113">WMI Service Corruption Blocks Installation of the WMI provider</span></span>

 <span data-ttu-id="e2a1f-114">.NET Framework 3.0 パッケージをインストールすると、WMI サービスの破損によって Windows Communication Foundation WMI プロバイダーのインストールがブロックされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-114">WMI Service Corruption may block the installation of the Windows Communication Foundation WMI provider when installing the .NET Framework 3.0 package.</span></span> <span data-ttu-id="e2a1f-115">インストール中に、Windows Communication Foundation インストーラーは、 *mofcomp.exe* コンポーネントを使用して、WCF *.mof* ファイルを登録できません。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-115">During installation, the Windows Communication Foundation installer is unable to register the WCF *.mof* file using the *mofcomp.exe* component.</span></span> <span data-ttu-id="e2a1f-116">発生する現象を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-116">The following is a list of symptoms:</span></span>  
  
1. <span data-ttu-id="e2a1f-117">.NET Framework 3.0 のインストールは正常に完了するのに、WCF WMI プロバイダーが登録されない。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-117">.NET Framework 3.0 installation completes successfully, but the WCF WMI provider is not registered.</span></span>  
  
2. <span data-ttu-id="e2a1f-118">アプリケーション イベント ログに、WCF の WMI プロバイダーの登録、または mofcomp.exe の実行に関する問題を示すエラー イベントが表示される。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-118">An error event appears in the application event log that references problems registering the WMI provider for WCF, or running mofcomp.exe.</span></span>  
  
3. <span data-ttu-id="e2a1f-119">ユーザーの %temp% ディレクトリの dd_wcf_retCA\* という名前のセットアップ ログ ファイルに、WCF WMI プロバイダーの登録に失敗したことが示される。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-119">The setup log file named dd_wcf_retCA\* in the user's %temp% directory contains references to failure to register the WCF WMI provider.</span></span>  
  
4. <span data-ttu-id="e2a1f-120">イベント ログまたはセットアップ トレース ログ ファイルに、次の例外のいずれかが記録される。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-120">An exception such as one the following may be listed in the event log or setup trace log file:</span></span>  
  
     <span data-ttu-id="e2a1f-121">ServiceModelReg [11:09:59:046]: System.ApplicationException : "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof" で E:\WINDOWS\system32\wbem\mofcomp.exe を実行している間に予期しない結果 3 が発生しました</span><span class="sxs-lookup"><span data-stu-id="e2a1f-121">ServiceModelReg [11:09:59:046]: System.ApplicationException: Unexpected result 3 executing E:\WINDOWS\system32\wbem\mofcomp.exe with "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof"</span></span>  
  
     <span data-ttu-id="e2a1f-122">または</span><span class="sxs-lookup"><span data-stu-id="e2a1f-122">or:</span></span>  
  
     <span data-ttu-id="e2a1f-123">ServiceModelReg [07:19:33:843]: System.TypeInitializationException : 'System.Management.ManagementPath' の型初期化子が例外をスローしました。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-123">ServiceModelReg [07:19:33:843]: System.TypeInitializationException: The type initializer for 'System.Management.ManagementPath' threw an exception.</span></span> <span data-ttu-id="e2a1f-124">---> InteropServices (0x80040154 が): 次のエラーにより、CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} のコンポーネントの COM クラスファクトリを取得できませんでした: 80040154。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-124">---> System.Runtime.InteropServices.COMException (0x80040154): Retrieving the COM class factory for component with CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} failed due to the following error: 80040154.</span></span>  
  
     <span data-ttu-id="e2a1f-125">または</span><span class="sxs-lookup"><span data-stu-id="e2a1f-125">or:</span></span>  
  
     <span data-ttu-id="e2a1f-126">ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException : ファイルまたはアセンブリ 'C:\WINDOWS\system32\wbem\mofcomp.exe'、またはその依存関係の 1 つが読み込めませんでした。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-126">ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: Could not load file or assembly 'C:\WINDOWS\system32\wbem\mofcomp.exe' or one of its dependencies.</span></span> <span data-ttu-id="e2a1f-127">指定されたファイルが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-127">The system cannot find the file specified.</span></span>  
  
     <span data-ttu-id="e2a1f-128">ファイル名 : C:\WINDOWS\system32\wbem\mofcomp.exe</span><span class="sxs-lookup"><span data-stu-id="e2a1f-128">File name: 'C:\WINDOWS\system32\wbem\mofcomp.exe</span></span>  
  
 <span data-ttu-id="e2a1f-129">上で説明した問題を解決するためには、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-129">The following steps must be followed to resolve the problem described previously.</span></span>  
  
1. <span data-ttu-id="e2a1f-130">WMI Diagnosis Utility を実行して、WMI サービスを修復します。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-130">Run the WMI Diagnosis Utility to repair the WMI service.</span></span> <span data-ttu-id="e2a1f-131">このツールの使用方法の詳細については、「 [WMI Diagnosis Utility](/previous-versions/tn-archive/ff404265(v%3dmsdn.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-131">For more information about using this tool, see [WMI Diagnosis Utility](/previous-versions/tn-archive/ff404265(v%3dmsdn.10)).</span></span>  
  
 <span data-ttu-id="e2a1f-132">**コントロールパネル** にある [**プログラムの追加と削除**] アプレットを使用して .NET Framework 3.0 インストールを修復するか、.NET Framework 3.0 をアンインストールまたは再インストールします。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-132">Repair the .NET Framework 3.0 installation by using the **Add/Remove Programs** applet located in **Control Panel**, or uninstall/reinstall the .NET Framework 3.0.</span></span>  
  
## <a name="repair-net-framework-30-after-net-framework-35-installation"></a><span data-ttu-id="e2a1f-133">3.5 のインストール .NET Framework 後に .NET Framework 3.0 を修復する</span><span class="sxs-lookup"><span data-stu-id="e2a1f-133">Repair .NET Framework 3.0 after .NET Framework 3.5 Installation</span></span>

 <span data-ttu-id="e2a1f-134">.NET Framework 3.5 をインストールした後に .NET Framework 3.0 の修復を実行すると、 *machine.config* で .NET Framework 3.5 によって導入された構成要素が削除されます。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-134">If you do a repair of .NET Framework 3.0 after you installed .NET Framework 3.5, configuration elements introduced by .NET Framework 3.5 in *machine.config* are removed.</span></span> <span data-ttu-id="e2a1f-135">ただし、 *web.config* ファイルはそのまま残ります。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-135">However, the *web.config* file remains intact.</span></span> <span data-ttu-id="e2a1f-136">この回避策としては、ARP を使用して .NET Framework 3.5 を修復するか、またはスイッチで [ワークフローサービス登録ツール (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) を使用し `/c` ます。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-136">The workaround is to repair .NET Framework 3.5 after this via ARP, or use the [WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) with the `/c` switch.</span></span>  
  
 <span data-ttu-id="e2a1f-137">[ワークフローサービス登録ツール (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) については、microsoft.net \framework\v3.5\ または%windir%\Microsoft.NET\framework64\v3.5\ を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-137">[WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) can be found at %windir%\Microsoft.NET\framework\v3.5\ or %windir%\Microsoft.NET\framework64\v3.5\</span></span>  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a><span data-ttu-id="e2a1f-138">.NET Framework 3.5 のインストール後に WCF/WF Webhost に対して IIS を適切に構成する</span><span class="sxs-lookup"><span data-stu-id="e2a1f-138">Configure IIS Properly for WCF/WF Webhost after Installing .NET Framework 3.5</span></span>  

 <span data-ttu-id="e2a1f-139">.NET Framework 3.5 インストールで WCF 関連の追加の IIS 構成設定の構成に失敗した場合、インストールログにエラーが記録されて続行されます。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-139">When .NET Framework 3.5 installation fails to configure additional WCF-related IIS configuration settings, it logs an error in the installation log and continues.</span></span> <span data-ttu-id="e2a1f-140">WorkflowServices アプリケーションを実行しようとしても、必要な構成設定がないため、実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-140">Any attempt to run WorkflowServices applications will fail, since the required configuration settings are missing.</span></span> <span data-ttu-id="e2a1f-141">たとえば、xoml やルール サービスの読み込みに失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-141">For example, loading xoml or rules service can fail.</span></span>  
  
 <span data-ttu-id="e2a1f-142">この問題を回避するには、 [ワークフローサービス登録ツール (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) とスイッチを使用して、 `/c` コンピューター上で IIS スクリプトマップを適切に構成します。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-142">To workaround this problem, use the [WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) with the `/c` switch to properly configure IIS script maps on the machine.</span></span> <span data-ttu-id="e2a1f-143">[ワークフローサービス登録ツール (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) については、microsoft.net \framework\v3.5\ または%windir%\Microsoft.NET\framework64\v3.5\ を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-143">[WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) can be found at %windir%\Microsoft.NET\framework\v3.5\ or %windir%\Microsoft.NET\framework64\v3.5\</span></span>  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule"></a><span data-ttu-id="e2a1f-144">型 ' HttpModule ' を読み込めませんでした</span><span class="sxs-lookup"><span data-stu-id="e2a1f-144">Could not load type 'System.ServiceModel.Activation.HttpModule'</span></span>

<span data-ttu-id="e2a1f-145">**アセンブリ ' System.servicemodel, Version 3.0.0.0, Culture = ニュートラル, PublicKeyToken = b77a5c561934e089 ' から型 ' HttpModule ' を読み込めませんでした**</span><span class="sxs-lookup"><span data-stu-id="e2a1f-145">**Could not load type 'System.ServiceModel.Activation.HttpModule' from assembly 'System.ServiceModel, Version 3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'**</span></span>

 <span data-ttu-id="e2a1f-146">このエラーは .NET Framework 4 がインストールされ、WCF HTTP アクティブ化が有効になっている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-146">This error occurs if .NET Framework 4 is installed and then WCF HTTP Activation is enabled.</span></span> <span data-ttu-id="e2a1f-147">この問題を解決するには、Visual Studio の開発者コマンドプロンプト内から次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="e2a1f-147">To resolve the issue, run the following command from inside the Developer Command Prompt for Visual Studio:</span></span>  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2a1f-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2a1f-148">See also</span></span>

- [<span data-ttu-id="e2a1f-149">セットアップ手順</span><span class="sxs-lookup"><span data-stu-id="e2a1f-149">Set-Up Instructions</span></span>](./samples/set-up-instructions.md)
