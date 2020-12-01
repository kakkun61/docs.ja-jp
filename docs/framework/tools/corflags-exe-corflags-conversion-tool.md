---
title: CorFlags.exe (CorFlags 変換ツール)
description: CorFlags.exe (CorFlags 変換ツール) を理解します。 このツールにより、ポータブル実行可能ファイル イメージのヘッダー内の CorFlags セクションを構成できます。
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: 3f9f2a71a7a33de13264ce60fa7ff6ea5832aace
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247188"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="26da9-104">CorFlags.exe (CorFlags 変換ツール)</span><span class="sxs-lookup"><span data-stu-id="26da9-104">CorFlags.exe (CorFlags Conversion Tool)</span></span>

<span data-ttu-id="26da9-105">CorFlags 変換ツールを使用して、ポータブル実行可能 (PE) ファイル イメージのヘッダー内の CorFlags セクションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="26da9-105">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="26da9-106">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="26da9-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="26da9-107">このツールを実行するには、Visual Studio 用開発者コマンド プロンプト (または Windows 7 の Visual Studio コマンド プロンプト) を使用します。</span><span class="sxs-lookup"><span data-stu-id="26da9-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="26da9-108">詳細については、「[Visual Studio 用開発者コマンド プロンプト](developer-command-prompt-for-vs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26da9-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="26da9-109">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="26da9-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26da9-110">構文</span><span class="sxs-lookup"><span data-stu-id="26da9-110">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="26da9-111">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26da9-111">Parameters</span></span>  
  
|<span data-ttu-id="26da9-112">必須パラメーター</span><span class="sxs-lookup"><span data-stu-id="26da9-112">Required parameter</span></span>|<span data-ttu-id="26da9-113">説明</span><span class="sxs-lookup"><span data-stu-id="26da9-113">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="26da9-114">CorFlags を設定するアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="26da9-114">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="26da9-115">オプション</span><span class="sxs-lookup"><span data-stu-id="26da9-115">Option</span></span>|<span data-ttu-id="26da9-116">説明</span><span class="sxs-lookup"><span data-stu-id="26da9-116">Description</span></span>|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|<span data-ttu-id="26da9-117">32BITREQUIRED フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="26da9-117">Sets the 32BITREQUIRED flag.</span></span>|  
|`-32BIT[REQ]-`|<span data-ttu-id="26da9-118">32BITREQUIRED フラグをクリアします。</span><span class="sxs-lookup"><span data-stu-id="26da9-118">Clears the 32BITREQUIRED flag.</span></span>|  
|`-32BITPREF+`|<span data-ttu-id="26da9-119">32BITPREFERRED フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="26da9-119">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="26da9-120">アプリは、64 ビット プラットフォーム上でも 32 ビット プロセスとして実行します。</span><span class="sxs-lookup"><span data-stu-id="26da9-120">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="26da9-121">このフラグは、EXE ファイルでのみ設定します。</span><span class="sxs-lookup"><span data-stu-id="26da9-121">Set this flag only on EXE files.</span></span> <span data-ttu-id="26da9-122">このフラグを DLL で設定した場合、64 ビット プロセスで DLL を読み込むことができず、<xref:System.BadImageFormatException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="26da9-122">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="26da9-123">このフラグを設定した EXE ファイルは、64 ビット プロセスで読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="26da9-123">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="26da9-124">.NET Framework 4.5 で新たに追加されました。</span><span class="sxs-lookup"><span data-stu-id="26da9-124">New in the .NET Framework 4.5.</span></span>|  
|`-32BITPREF-`|<span data-ttu-id="26da9-125">32BITPREFERRED フラグをクリアします。</span><span class="sxs-lookup"><span data-stu-id="26da9-125">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="26da9-126">.NET Framework 4.5 で新たに追加されました。</span><span class="sxs-lookup"><span data-stu-id="26da9-126">New in the .NET Framework 4.5.</span></span>|  
|`-?`|<span data-ttu-id="26da9-127">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="26da9-127">Displays command syntax and options for the tool.</span></span>|  
|`-Force`|<span data-ttu-id="26da9-128">厳密な名前が付けられているアセンブリであっても、強制的に更新します。</span><span class="sxs-lookup"><span data-stu-id="26da9-128">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="26da9-129">**重要:** 厳密な名前が付けられているアセンブリを更新する場合は、そのコードを実行する前に再署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26da9-129">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|`-help`|<span data-ttu-id="26da9-130">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="26da9-130">Displays command syntax and options for the tool.</span></span>|  
|`-ILONLY+`|<span data-ttu-id="26da9-131">ILONLY フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="26da9-131">Sets the ILONLY flag.</span></span>|  
|`-ILONLY-`|<span data-ttu-id="26da9-132">ILONLY フラグをクリアします。</span><span class="sxs-lookup"><span data-stu-id="26da9-132">Clears the ILONLY flag.</span></span>|  
|`-nologo`|<span data-ttu-id="26da9-133">Microsoft 著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="26da9-133">Suppresses the Microsoft startup banner display.</span></span>|  
|`-RevertCLRHeader`|<span data-ttu-id="26da9-134">CLR ヘッダー バージョンを 2.0 に戻します。</span><span class="sxs-lookup"><span data-stu-id="26da9-134">Reverts the CLR header version to 2.0.</span></span>|  
|`-UpgradeCLRHeader`|<span data-ttu-id="26da9-135">CLR ヘッダー バージョンを 2.5 にアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="26da9-135">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="26da9-136">**注:** アセンブリをネイティブに実行するには、CLR ヘッダー バージョン 2.5 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="26da9-136">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26da9-137">Remarks</span><span class="sxs-lookup"><span data-stu-id="26da9-137">Remarks</span></span>  

 <span data-ttu-id="26da9-138">オプションが何も指定されていない場合、CorFlags 変換ツールは指定されているアセンブリのフラグを表示します。</span><span class="sxs-lookup"><span data-stu-id="26da9-138">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26da9-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="26da9-139">See also</span></span>

- [<span data-ttu-id="26da9-140">ツール</span><span class="sxs-lookup"><span data-stu-id="26da9-140">Tools</span></span>](index.md)
- [<span data-ttu-id="26da9-141">64 ビット アプリケーション</span><span class="sxs-lookup"><span data-stu-id="26da9-141">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="26da9-142">Visual Studio 用開発者コマンド プロンプト</span><span class="sxs-lookup"><span data-stu-id="26da9-142">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
