---
title: Regsvcs.exe (.NET サービス インストール ツール)
description: Regsvcs.exe (.NET サービス インストール ツール) を使用します。 アセンブリの読み込みと登録、プログラムによってクラスに追加したサービスの構成などを行います。
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
ms.openlocfilehash: 58a20084457cb217f3af73f4b4ff9ea251647782
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238550"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="5020f-104">Regsvcs.exe (.NET サービス インストール ツール)</span><span class="sxs-lookup"><span data-stu-id="5020f-104">Regsvcs.exe (.NET Services Installation Tool)</span></span>

<span data-ttu-id="5020f-105">.NET サービス インストール ツールは、次のアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="5020f-105">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="5020f-106">アセンブリの読み込みと登録。</span><span class="sxs-lookup"><span data-stu-id="5020f-106">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="5020f-107">タイプ ライブラリの生成、登録、および指定された COM+ アプリケーションへのインストール。</span><span class="sxs-lookup"><span data-stu-id="5020f-107">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="5020f-108">プログラムでクラスに追加したサービスの設定。</span><span class="sxs-lookup"><span data-stu-id="5020f-108">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="5020f-109">このツールを実行するには、Visual Studio 用開発者コマンド プロンプト (または Windows 7 の Visual Studio コマンド プロンプト) を使用します。</span><span class="sxs-lookup"><span data-stu-id="5020f-109">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="5020f-110">詳細については、「[Visual Studio 用開発者コマンド プロンプト](developer-command-prompt-for-vs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5020f-110">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="5020f-111">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="5020f-111">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5020f-112">構文</span><span class="sxs-lookup"><span data-stu-id="5020f-112">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll
```  
  
## <a name="parameters"></a><span data-ttu-id="5020f-113">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5020f-113">Parameters</span></span>  
  
|<span data-ttu-id="5020f-114">引数</span><span class="sxs-lookup"><span data-stu-id="5020f-114">Argument</span></span>|<span data-ttu-id="5020f-115">説明</span><span class="sxs-lookup"><span data-stu-id="5020f-115">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="5020f-116">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="5020f-116">*assemblyFile.dll*</span></span>|<span data-ttu-id="5020f-117">ソース アセンブリ ファイル。</span><span class="sxs-lookup"><span data-stu-id="5020f-117">The source assembly file.</span></span> <span data-ttu-id="5020f-118">アセンブリは、厳密な名前で署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5020f-118">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="5020f-119">詳しくは、「[厳密な名前でのアセンブリへの署名](../../standard/assembly/sign-strong-name.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5020f-119">For more information, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span>|  
  
|<span data-ttu-id="5020f-120">オプション</span><span class="sxs-lookup"><span data-stu-id="5020f-120">Option</span></span>|<span data-ttu-id="5020f-121">説明</span><span class="sxs-lookup"><span data-stu-id="5020f-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5020f-122">**/appdir:** *path*</span><span class="sxs-lookup"><span data-stu-id="5020f-122">**/appdir:** *path*</span></span>|<span data-ttu-id="5020f-123">アプリケーションのルート ディレクトリを示します。</span><span class="sxs-lookup"><span data-stu-id="5020f-123">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="5020f-124">**/appname:** *applicationName*</span><span class="sxs-lookup"><span data-stu-id="5020f-124">**/appname:** *applicationName*</span></span>|<span data-ttu-id="5020f-125">検索または作成する COM+ アプリケーションの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="5020f-125">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="5020f-126">**/c**</span><span class="sxs-lookup"><span data-stu-id="5020f-126">**/c**</span></span>|<span data-ttu-id="5020f-127">ターゲット アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="5020f-127">Creates the target application.</span></span>|  
|<span data-ttu-id="5020f-128">**/componly**</span><span class="sxs-lookup"><span data-stu-id="5020f-128">**/componly**</span></span>|<span data-ttu-id="5020f-129">コンポーネントだけを設定します。メソッドとインターフェイスは無視されます。</span><span class="sxs-lookup"><span data-stu-id="5020f-129">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="5020f-130">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="5020f-130">**/exapp**</span></span>|<span data-ttu-id="5020f-131">このツールが既存のアプリケーションを要求するように指定します。</span><span class="sxs-lookup"><span data-stu-id="5020f-131">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="5020f-132">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="5020f-132">**/extlb**</span></span>|<span data-ttu-id="5020f-133">既存のタイプ ライブラリを使用します。</span><span class="sxs-lookup"><span data-stu-id="5020f-133">Uses an existing type library.</span></span>|  
|<span data-ttu-id="5020f-134">**/fc**</span><span class="sxs-lookup"><span data-stu-id="5020f-134">**/fc**</span></span>|<span data-ttu-id="5020f-135">対象アプリケーションを検索または作成します。</span><span class="sxs-lookup"><span data-stu-id="5020f-135">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="5020f-136">**/help**</span><span class="sxs-lookup"><span data-stu-id="5020f-136">**/help**</span></span>|<span data-ttu-id="5020f-137">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="5020f-137">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="5020f-138">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="5020f-138">**/noreconfig**</span></span>|<span data-ttu-id="5020f-139">既存の対象アプリケーションを再設定しません。</span><span class="sxs-lookup"><span data-stu-id="5020f-139">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="5020f-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="5020f-140">**/nologo**</span></span>|<span data-ttu-id="5020f-141">Microsoft 著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="5020f-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="5020f-142">**/parname:** *name*</span><span class="sxs-lookup"><span data-stu-id="5020f-142">**/parname:** *name*</span></span>|<span data-ttu-id="5020f-143">検索または作成する COM+ アプリケーションの名前または ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="5020f-143">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="5020f-144">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="5020f-144">**/reconfig**</span></span>|<span data-ttu-id="5020f-145">既存の対象アプリケーションを再設定します。</span><span class="sxs-lookup"><span data-stu-id="5020f-145">Reconfigures an existing target application.</span></span> <span data-ttu-id="5020f-146">既定値です。</span><span class="sxs-lookup"><span data-stu-id="5020f-146">This is the default.</span></span>|  
|<span data-ttu-id="5020f-147">**/tlb:** *typelibraryfile*</span><span class="sxs-lookup"><span data-stu-id="5020f-147">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="5020f-148">インストールするタイプ ライブラリ ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="5020f-148">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="5020f-149">**/u**</span><span class="sxs-lookup"><span data-stu-id="5020f-149">**/u**</span></span>|<span data-ttu-id="5020f-150">対象アプリケーションをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="5020f-150">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="5020f-151">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="5020f-151">**/quiet**</span></span>|<span data-ttu-id="5020f-152">クワイエット モードを指定します。ロゴと成功メッセージは表示されません。</span><span class="sxs-lookup"><span data-stu-id="5020f-152">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="5020f-153">**/?**</span><span class="sxs-lookup"><span data-stu-id="5020f-153">**/?**</span></span>|<span data-ttu-id="5020f-154">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="5020f-154">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5020f-155">Remarks</span><span class="sxs-lookup"><span data-stu-id="5020f-155">Remarks</span></span>  

 <span data-ttu-id="5020f-156">Regsvcs.exe には、*assemblyFile.dll* で指定されているソース アセンブリ ファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="5020f-156">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="5020f-157">このアセンブリは、厳密な名前で署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5020f-157">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="5020f-158">厳密な名前での署名について詳しくは、「[厳密な名前でのアセンブリへの署名](../../standard/assembly/sign-strong-name.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5020f-158">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span> <span data-ttu-id="5020f-159">対象アプリケーションおよびタイプ ライブラリの名前は、オプションです。</span><span class="sxs-lookup"><span data-stu-id="5020f-159">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="5020f-160">引数 *applicationName* はソース アセンブリ ファイルから生成できます。存在しない場合は、Regsvcs.exe によって作成されます。</span><span class="sxs-lookup"><span data-stu-id="5020f-160">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="5020f-161">引数 *typelibraryfile* にはタイプ ライブラリ名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5020f-161">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="5020f-162">タイプ ライブラリ名を指定しない場合、Regsvcs.exe は既定値としてアセンブリ名を使用します。</span><span class="sxs-lookup"><span data-stu-id="5020f-162">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="5020f-163">Regsvcs.exe がコンポーネントのメソッドを登録する場合は、それらのメソッドに対する[確認要求](/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100))と[リンク確認要求](../misc/link-demands.md)の影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="5020f-163">When Regsvcs.exe registers a component's methods, it is subject to the [demands](/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="5020f-164">このツールは完全に信頼された環境で実行されるため、アクセス許可に対するほとんどの確認要求は成功します。</span><span class="sxs-lookup"><span data-stu-id="5020f-164">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="5020f-165">ただし、Regsvcs.exe では、<xref:System.Security.Permissions.StrongNameIdentityPermission> または <xref:System.Security.Permissions.PublisherIdentityPermission> に対する確認要求やリンク確認要求によって保護されたメソッドを含むコンポーネントを登録することはできません。</span><span class="sxs-lookup"><span data-stu-id="5020f-165">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="5020f-166">Regsvcs.exe を使用するには、ローカル コンピューターの管理特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="5020f-166">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="5020f-167">上記のアクションの実行中に Regsvcs.exe が異常終了した場合は、対応するエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5020f-167">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5020f-168">使用例</span><span class="sxs-lookup"><span data-stu-id="5020f-168">Examples</span></span>  

 <span data-ttu-id="5020f-169">`myTest.dll` に含まれるすべてのパブリック クラスを `myTargetApp` (既存の COM+ アプリケーション) に追加し、タイプ ライブラリ `myTest.tlb` を生成するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="5020f-169">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="5020f-170">`myTest.dll` に含まれるすべてのパブリック クラスを `myTargetApp` (既存の COM+ アプリケーション) に追加し、タイプ ライブラリ `newTest.tlb` を生成するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="5020f-170">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="5020f-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="5020f-171">See also</span></span>

- [<span data-ttu-id="5020f-172">ツール</span><span class="sxs-lookup"><span data-stu-id="5020f-172">Tools</span></span>](index.md)
- [<span data-ttu-id="5020f-173">方法: 厳密な名前でアセンブリに署名する</span><span class="sxs-lookup"><span data-stu-id="5020f-173">How to: Sign an Assembly with a Strong Name</span></span>](../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="5020f-174">Visual Studio 用開発者コマンド プロンプト</span><span class="sxs-lookup"><span data-stu-id="5020f-174">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
