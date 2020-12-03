---
title: イントラネット アプリケーションの完全信頼での実行
description: .NET Framework 3.5 SP1 を使用して、イントラネット アプリケーションを完全信頼で実行します。 アプリケーションとそのライブラリ アセンブリを、ネットワーク共有から完全信頼アセンブリとして実行できます。
ms.date: 03/30/2017
helpviewer_keywords:
- full trust, running intranet applications in
- intranet applications, running in full trust
- running intranet applications in full trust
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
ms.openlocfilehash: 01d98a1ca7ce67088b4f04bedf7e3ef02e0ca7a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723715"
---
# <a name="running-intranet-applications-in-full-trust"></a><span data-ttu-id="62ac9-104">イントラネット アプリケーションの完全信頼での実行</span><span class="sxs-lookup"><span data-stu-id="62ac9-104">Running Intranet Applications in Full Trust</span></span>

<span data-ttu-id="62ac9-105">.NET Framework 3.5 Service Pack 1 (SP1) 以降、アプリケーションとそのライブラリ アセンブリをネットワーク共有から完全信頼アセンブリとして実行できます。</span><span class="sxs-lookup"><span data-stu-id="62ac9-105">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), applications and their library assemblies can be run as full-trust assemblies from a network share.</span></span> <span data-ttu-id="62ac9-106">イントラネット上の共有から読み込まれたアセンブリに、<xref:System.Security.SecurityZone.MyComputer> ゾーンの証拠が自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="62ac9-106"><xref:System.Security.SecurityZone.MyComputer> zone evidence is automatically added to assemblies that are loaded from a share on the intranet.</span></span> <span data-ttu-id="62ac9-107">この証拠は、コンピューター上に存在するアセンブリと同じ許可セット (通常は完全な信頼) をこれらのアセンブリに付与します。</span><span class="sxs-lookup"><span data-stu-id="62ac9-107">This evidence gives those assemblies the same grant set (which is typically full trust) as the assemblies that reside on the computer.</span></span> <span data-ttu-id="62ac9-108">この機能は、ClickOnce アプリケーションまたはホスト上で実行するように設計されたアプリケーションには適用されません。</span><span class="sxs-lookup"><span data-stu-id="62ac9-108">This functionality does not apply to ClickOnce applications or to applications that are designed to run on a host.</span></span>

## <a name="rules-for-library-assemblies"></a><span data-ttu-id="62ac9-109">ライブラリ アセンブリのルール</span><span class="sxs-lookup"><span data-stu-id="62ac9-109">Rules for Library Assemblies</span></span>

<span data-ttu-id="62ac9-110">ネットワーク共有上の実行可能ファイルによって読み込まれるアセンブリには、次のルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="62ac9-110">The following rules apply to assemblies that are loaded by an executable on a network share:</span></span>

- <span data-ttu-id="62ac9-111">ライブラリ アセンブリは、実行可能アセンブリと同じフォルダーに存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62ac9-111">Library assemblies must reside in the same folder as the executable assembly.</span></span> <span data-ttu-id="62ac9-112">サブフォルダーに存在するアセンブリまたは異なるパスで参照されているアセンブリには、完全な信頼の許可セットは付与されません。</span><span class="sxs-lookup"><span data-stu-id="62ac9-112">Assemblies that reside in a subfolder or are referenced on a different path are not given the full-trust grant set.</span></span>

- <span data-ttu-id="62ac9-113">実行可能ファイルがアセンブリの遅延読み込みを行う場合は、実行可能ファイルの開始に使ったものと同じパスを使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="62ac9-113">If the executable delay-loads an assembly, it must use the same path that was used to start the executable.</span></span> <span data-ttu-id="62ac9-114">たとえば、共有 \\\\*network-computer*\\*share* がドライブ文字にマップされていて、そのパスから実行可能ファイルが実行される場合、ネットワーク パスを使って実行可能ファイルにより読み込まれるアセンブリには、完全な信頼は付与されません。</span><span class="sxs-lookup"><span data-stu-id="62ac9-114">For example, if the share \\\\*network-computer*\\*share* is mapped to a drive letter and the executable is run from that path, assemblies that are loaded by the executable by using the network path will not be granted full trust.</span></span> <span data-ttu-id="62ac9-115"><xref:System.Security.SecurityZone.MyComputer> ゾーン内のアセンブリを遅延読み込みするには、実行可能ファイルはドライブ文字のパスを使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="62ac9-115">To delay-load an assembly in the <xref:System.Security.SecurityZone.MyComputer> zone, the executable must use the drive letter path.</span></span>

## <a name="restoring-the-former-intranet-policy"></a><span data-ttu-id="62ac9-116">以前のイントラネット ポリシーの復元</span><span class="sxs-lookup"><span data-stu-id="62ac9-116">Restoring the Former Intranet Policy</span></span>

<span data-ttu-id="62ac9-117">以前のバージョンの .NET Framework では、共有アセンブリに <xref:System.Security.SecurityZone.Intranet> ゾーンの証拠が付与されていました。</span><span class="sxs-lookup"><span data-stu-id="62ac9-117">In earlier versions of the .NET Framework, shared assemblies were granted <xref:System.Security.SecurityZone.Intranet> zone evidence.</span></span> <span data-ttu-id="62ac9-118">共有上のアセンブリに完全な信頼を付与するには、コード アクセス セキュリティ ポリシーを指定する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="62ac9-118">You had to specify code access security policy to grant full trust to an assembly on a share.</span></span>

<span data-ttu-id="62ac9-119">この新しい動作は、イントラネットのアセンブリの既定値です。</span><span class="sxs-lookup"><span data-stu-id="62ac9-119">This new behavior is the default for intranet assemblies.</span></span> <span data-ttu-id="62ac9-120">コンピューター上のすべてのアプリケーションに適用されるレジストリ キーを設定することで、<xref:System.Security.SecurityZone.Intranet> の証拠を提供する以前の動作に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="62ac9-120">You can return to the earlier behavior of providing <xref:System.Security.SecurityZone.Intranet> evidence by setting a registry key that applies to all applications on the computer.</span></span> <span data-ttu-id="62ac9-121">この手順は、32 ビット コンピューターと 64 ビット コンピューターでは異なります。</span><span class="sxs-lookup"><span data-stu-id="62ac9-121">This process is different for 32-bit and 64-bit computers:</span></span>

- <span data-ttu-id="62ac9-122">32 ビット コンピューターでは、システム レジストリの HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework キーの下にサブキーを作成します。</span><span class="sxs-lookup"><span data-stu-id="62ac9-122">On 32-bit computers, create a subkey under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key in the system registry.</span></span> <span data-ttu-id="62ac9-123">キーの名前は LegacyMyComputerZone、DWORD 値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="62ac9-123">Use the key name LegacyMyComputerZone with a DWORD value of 1.</span></span>

- <span data-ttu-id="62ac9-124">64 ビット コンピューターでは、システム レジストリの HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework キーの下にサブキーを作成します。</span><span class="sxs-lookup"><span data-stu-id="62ac9-124">On 64-bit computers, create a subkey under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key in the system registry.</span></span> <span data-ttu-id="62ac9-125">キーの名前は LegacyMyComputerZone、DWORD 値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="62ac9-125">Use the key name LegacyMyComputerZone with a DWORD value of 1.</span></span> <span data-ttu-id="62ac9-126">HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework キーの下に、同じサブキーを作成します。</span><span class="sxs-lookup"><span data-stu-id="62ac9-126">Create the same subkey under the HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework key.</span></span>

## <a name="see-also"></a><span data-ttu-id="62ac9-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="62ac9-127">See also</span></span>

- [<span data-ttu-id="62ac9-128">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="62ac9-128">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
