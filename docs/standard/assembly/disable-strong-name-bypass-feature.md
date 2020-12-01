---
title: '方法: 厳密な名前のバイパス機能を無効にする'
description: 厳密な名前のバイパスは、.NET の完全に信頼されたドメインでの署名の検証をスキップします。 1 つのアプリケーションまたはすべてのアプリケーションに対してこの機能をオーバーライドできます。
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
ms.openlocfilehash: 2846efbbd76cf677a42a7031e53661d302c6c964
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687464"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="96516-104">方法: 厳密な名前のバイパス機能を無効にする</span><span class="sxs-lookup"><span data-stu-id="96516-104">How to: Disable the strong-name bypass feature</span></span>

<span data-ttu-id="96516-105">.NET Framework Version 3.5 Service Pack 1 (SP1) 以降、アセンブリが完全信頼の <xref:System.AppDomain> オブジェクト (`MyComputer` ゾーンに既定の <xref:System.AppDomain> など) に読み込まれている場合は、厳密な名前の署名の検証が行われなくなりました。</span><span class="sxs-lookup"><span data-stu-id="96516-105">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="96516-106">これは厳密な名前のバイパス機能と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="96516-106">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="96516-107">完全に信頼された環境では、<xref:System.Security.Permissions.StrongNameIdentityPermission> に対する完全に信頼された署名済みアセンブリの要求は、その署名に関係なく、常に成功します。</span><span class="sxs-lookup"><span data-stu-id="96516-107">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="96516-108">ゾーンは完全に信頼されているため、唯一の制限として、アセンブリは完全に信頼されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="96516-108">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="96516-109">このような状況では厳密な名前は決定要因ではないため、これを検証する理由はありません。</span><span class="sxs-lookup"><span data-stu-id="96516-109">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="96516-110">厳密な名前の署名の検証をバイパスすることで、パフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="96516-110">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="96516-111">バイパス機能は、<xref:System.AppDomainSetup.ApplicationBase%2A> プロパティで指定されたディレクトリから完全信頼の <xref:System.AppDomain> に読み込まれ、遅延署名されていないすべての完全信頼アセンブリに適用されます。</span><span class="sxs-lookup"><span data-stu-id="96516-111">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="96516-112">レジストリ キー値を設定することで、コンピューターのすべてのアプリケーションに対するバイパス機能をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="96516-112">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="96516-113">アプリケーションの構成ファイルを使用すると、単一アプリケーションの設定をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="96516-113">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="96516-114">レジストリ キーを使用して無効にされているアプリケーションでは、個別にバイパス機能を元に戻すことはできません。</span><span class="sxs-lookup"><span data-stu-id="96516-114">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="96516-115">バイパス機能をオーバーライドすると、厳密な名前が正しいかどうかだけが検証されます。<xref:System.Security.Permissions.StrongNameIdentityPermission> に対するチェックは行われません。</span><span class="sxs-lookup"><span data-stu-id="96516-115">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="96516-116">特定の厳密な名前を確認するには、個別にチェックを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="96516-116">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="96516-117">厳密な名前の検証を強制する機能は、次の手順で説明するように、レジストリ キーに依存します。</span><span class="sxs-lookup"><span data-stu-id="96516-117">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="96516-118">アプリケーションが、該当のレジストリ キーへのアクセスについてアクセス制御リスト (ACL) アクセス許可を持っていないアカウントで実行されている場合、その設定は無効となります。</span><span class="sxs-lookup"><span data-stu-id="96516-118">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="96516-119">ACL アクセス許可を構成し、すべてのアセンブリ用に読み取ることができるようにキーを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="96516-119">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="96516-120">すべてのアプリケーションに対して厳密な名前のバイパス機能を無効にする</span><span class="sxs-lookup"><span data-stu-id="96516-120">Disable the strong-name bypass feature for all applications</span></span>  
  
- <span data-ttu-id="96516-121">32 ビット コンピューターでは、システム レジストリの HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework キーの下に、値が 0 の `AllowStrongNameBypass` という名前のダブルワード エントリを作成します。</span><span class="sxs-lookup"><span data-stu-id="96516-121">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
- <span data-ttu-id="96516-122">64 ビット コンピューターでは、システム レジストリの HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework キーと HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework キーの下に、値が 0 の `AllowStrongNameBypass` という名前のダブルワード エントリを作成します。</span><span class="sxs-lookup"><span data-stu-id="96516-122">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="96516-123">単一のアプリケーションに対して厳密な名前のバイパス機能を無効にする</span><span class="sxs-lookup"><span data-stu-id="96516-123">Disable the strong-name bypass feature for a single application</span></span>  
  
1. <span data-ttu-id="96516-124">アプリケーションの構成ファイルを開くか、または作成します。</span><span class="sxs-lookup"><span data-stu-id="96516-124">Open or create the application configuration file.</span></span>  
  
    <span data-ttu-id="96516-125">このファイルの詳細については、[アプリの構成](../../framework/configure-apps/index.md)に関する記事の「アプリケーション構成ファイル」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="96516-125">For more information about this file, see the Application Configuration Files section in [Configure apps](../../framework/configure-apps/index.md).</span></span>  
  
2. <span data-ttu-id="96516-126">次のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="96516-126">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="96516-127">アプリケーションのバイパス機能を元に戻すには、構成ファイル設定を削除するか、属性を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="96516-127">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96516-128">アプリケーションに対して厳密な名前のバイパス機能の有効/無効を切り替えることができるのは、コンピューターでバイパス機能が有効になっている場合だけです。</span><span class="sxs-lookup"><span data-stu-id="96516-128">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="96516-129">コンピューターでバイパス機能が無効になっている場合は、すべてのアプリケーションに対して厳密な名前が検証され、単一のアプリケーションに対する検証をバイパスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="96516-129">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96516-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="96516-130">See also</span></span>

- [<span data-ttu-id="96516-131">Sn.exe (厳密名ツール)</span><span class="sxs-lookup"><span data-stu-id="96516-131">Sn.exe (Strong Name Tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="96516-132">\<bypassTrustedAppStrongNames> 要素</span><span class="sxs-lookup"><span data-stu-id="96516-132">\<bypassTrustedAppStrongNames> element</span></span>](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [<span data-ttu-id="96516-133">厳密な名前付きアセンブリの作成と使用</span><span class="sxs-lookup"><span data-stu-id="96516-133">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
