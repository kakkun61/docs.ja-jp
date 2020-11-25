---
title: コード アクセス セキュリティ ポリシーの互換性と移行
description: 概要を確認し、.NET Framework 4 でのコードアクセスセキュリティポリシーの互換性と移行に関するリンクを参照してください。
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
ms.openlocfilehash: 389976556175c0b6b300e75d01327d91f94f0db9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733387"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a><span data-ttu-id="853cd-103">コード アクセス セキュリティ ポリシーの互換性と移行</span><span class="sxs-lookup"><span data-stu-id="853cd-103">Code Access Security Policy Compatibility and Migration</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="853cd-104">コードアクセスセキュリティ (CAS) のポリシー部分は、.NET Framework 4 では廃止されました。</span><span class="sxs-lookup"><span data-stu-id="853cd-104">The policy portion of code access security (CAS) has been made obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="853cd-105">その結果、互換性のために残されているポリシーの型とメンバーを明示的または[暗黙的](#implicit_use)に (他の型とメンバーを介して)[明示的](#explicit_use)に呼び出す場合は、コンパイルの警告とランタイム例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="853cd-105">As a result, you may encounter compilation warnings and runtime exceptions if you call the obsolete policy types and members [explicitly](#explicit_use) or [implicitly](#implicit_use) (through other types and members).</span></span>

<span data-ttu-id="853cd-106">以下のいずれかの方法で警告やエラーを回避できます。</span><span class="sxs-lookup"><span data-stu-id="853cd-106">You can avoid the warnings and errors by either:</span></span>

- <span data-ttu-id="853cd-107">互換性のために残されている呼び出しの .NET Framework 4 の置換に[移行](#migration)しています。</span><span class="sxs-lookup"><span data-stu-id="853cd-107">[Migrating](#migration) to the .NET Framework 4 replacements for the obsolete calls.</span></span>

   <span data-ttu-id="853cd-108">\- または</span><span class="sxs-lookup"><span data-stu-id="853cd-108">\- or -</span></span>

- <span data-ttu-id="853cd-109">[ \<NetFx40_LegacySecurityPolicy> Configuration 要素](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)を使用して、従来の CAS ポリシーの動作を選択します。</span><span class="sxs-lookup"><span data-stu-id="853cd-109">Using the [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) to opt into the legacy CAS policy behavior.</span></span>

<span data-ttu-id="853cd-110">このトピックには、次のセクションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="853cd-110">This topic contains the following sections:</span></span>

- [<span data-ttu-id="853cd-111">明示的な使用</span><span class="sxs-lookup"><span data-stu-id="853cd-111">Explicit Use</span></span>](#explicit_use)

- [<span data-ttu-id="853cd-112">暗黙的な使用</span><span class="sxs-lookup"><span data-stu-id="853cd-112">Implicit Use</span></span>](#implicit_use)

- [<span data-ttu-id="853cd-113">エラーと警告</span><span class="sxs-lookup"><span data-stu-id="853cd-113">Errors and Warnings</span></span>](#errors_and_warnings)

- [<span data-ttu-id="853cd-114">移行: 廃止された呼び出しの代替方法</span><span class="sxs-lookup"><span data-stu-id="853cd-114">Migration: Replacement for Obsolete Calls</span></span>](#migration)

- [<span data-ttu-id="853cd-115">互換性: CAS ポリシーのレガシー オプションを使用する</span><span class="sxs-lookup"><span data-stu-id="853cd-115">Compatibility: Using the CAS Policy Legacy Option</span></span>](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a><span data-ttu-id="853cd-116">明示的な使用</span><span class="sxs-lookup"><span data-stu-id="853cd-116">Explicit Use</span></span>

<span data-ttu-id="853cd-117">直接セキュリティ ポリシーを操作するメンバー、または CAS ポリシーをサンドボックス化することが必要なメンバーは廃止され、既定ではエラーを発生するようになりました。</span><span class="sxs-lookup"><span data-stu-id="853cd-117">Members that directly manipulate security policy or require CAS policy to sandbox are obsolete and will produce errors by default.</span></span>

<span data-ttu-id="853cd-118">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="853cd-118">Examples of these are:</span></span>

- <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=nameWithType>

<a name="implicit_use"></a>

## <a name="implicit-use"></a><span data-ttu-id="853cd-119">暗黙的な使用</span><span class="sxs-lookup"><span data-stu-id="853cd-119">Implicit Use</span></span>

<span data-ttu-id="853cd-120">アセンブリの読み込みオーバーロードの中にはエラーを生成するものがあります。CAS ポリシーを暗黙的に使用することが原因です。</span><span class="sxs-lookup"><span data-stu-id="853cd-120">Several assembly loading overloads produce errors because of their implicit use of CAS policy.</span></span> <span data-ttu-id="853cd-121">これらのオーバーロードはCAS ポリシーを解決するために <xref:System.Security.Policy.Evidence> パラメーターを取り、アセンブリにアクセス許可セットを提供します。</span><span class="sxs-lookup"><span data-stu-id="853cd-121">These overloads take an <xref:System.Security.Policy.Evidence> parameter that is used to resolve CAS policy and provide a permission grant set for an assembly.</span></span>

<span data-ttu-id="853cd-122">例をいくつか紹介します。</span><span class="sxs-lookup"><span data-stu-id="853cd-122">Here are some examples.</span></span> <span data-ttu-id="853cd-123">パラメーターとして <xref:System.Security.Policy.Evidence> を取るオーバーロードが廃止されました。</span><span class="sxs-lookup"><span data-stu-id="853cd-123">The obsolete overloads are those that take <xref:System.Security.Policy.Evidence> as a parameter:</span></span>

- <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

<a name="errors_and_warnings"></a>

## <a name="errors-and-warnings"></a><span data-ttu-id="853cd-124">エラーおよび警告</span><span class="sxs-lookup"><span data-stu-id="853cd-124">Errors and Warnings</span></span>

<span data-ttu-id="853cd-125">廃止された種類とメンバーが使用されると、以下のエラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="853cd-125">The obsolete types and members produce the following error messages when they are used.</span></span> <span data-ttu-id="853cd-126"><xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 型自体は廃止されていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="853cd-126">Note that the <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> type itself is not obsolete.</span></span>

<span data-ttu-id="853cd-127">コンパイル時の警告:</span><span class="sxs-lookup"><span data-stu-id="853cd-127">Compile-time warning:</span></span>

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

<span data-ttu-id="853cd-128">実行時の例外:</span><span class="sxs-lookup"><span data-stu-id="853cd-128">Run-time exception:</span></span>

<span data-ttu-id="853cd-129"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span><span class="sxs-lookup"><span data-stu-id="853cd-129"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span></span>

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a><span data-ttu-id="853cd-130">移行: 廃止された呼び出しの代替方法</span><span class="sxs-lookup"><span data-stu-id="853cd-130">Migration: Replacement for Obsolete Calls</span></span>

### <a name="determining-an-assemblys-trust-level"></a><span data-ttu-id="853cd-131">アセンブリの信頼レベルの判別</span><span class="sxs-lookup"><span data-stu-id="853cd-131">Determining an Assembly’s Trust Level</span></span>

<span data-ttu-id="853cd-132">CAS ポリシーは多くの場合、アセンブリ、アプリケーション ドメインのアクセス許可セット、または信頼レベルを判断するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="853cd-132">CAS policy is often used to determine an assembly’s or application domain’s permission grant set or trust level.</span></span> <span data-ttu-id="853cd-133">.NET Framework 4 では、セキュリティポリシーを解決する必要がない次の便利なプロパティが公開されています。</span><span class="sxs-lookup"><span data-stu-id="853cd-133">The .NET Framework 4 exposes the following useful properties that do not need to resolve security policy:</span></span>

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a><span data-ttu-id="853cd-134">アプリケーション ドメインのサンドボックス化</span><span class="sxs-lookup"><span data-stu-id="853cd-134">Application Domain Sandboxing</span></span>

<span data-ttu-id="853cd-135">通常 <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> メソッドは、アプリケーション ドメイン内のアセンブリをサンド ボックス化するために使用します。</span><span class="sxs-lookup"><span data-stu-id="853cd-135">The <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> method is typically used for sandboxing the assemblies in an application domain.</span></span> <span data-ttu-id="853cd-136">.NET Framework 4 は、この目的で使用する必要のないメンバーを公開 <xref:System.Security.Policy.PolicyLevel> します。</span><span class="sxs-lookup"><span data-stu-id="853cd-136">The .NET Framework 4 exposes members that do not have to use <xref:System.Security.Policy.PolicyLevel> for this purpose.</span></span> <span data-ttu-id="853cd-137">詳細については、「 [方法: サンドボックスで部分信頼コードを実行する](how-to-run-partially-trusted-code-in-a-sandbox.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="853cd-137">For more information, see [How to: Run Partially Trusted Code in a Sandbox](how-to-run-partially-trusted-code-in-a-sandbox.md).</span></span>

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a><span data-ttu-id="853cd-138">部分的に信頼できるコードに対する安全なまたは適切なアクセス許可セットの決定</span><span class="sxs-lookup"><span data-stu-id="853cd-138">Determining a Safe or Reasonable Permission Set for Partially Trusted Code</span></span>

<span data-ttu-id="853cd-139">多くの場合ホストでは、ホストされているコードをサンドボックス化するための適切なアクセス許可を判別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="853cd-139">Hosts often need to determine the permissions that are appropriate for sandboxing hosted code.</span></span> <span data-ttu-id="853cd-140">.NET Framework 4 より前の CAS ポリシーでは、メソッドを使用してこれを行う方法が提供されていま <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> した。</span><span class="sxs-lookup"><span data-stu-id="853cd-140">Before the .NET Framework 4, CAS policy provided a way to do this with the <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="853cd-141">代替として、.NET Framework 4 は <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> メソッドを提供します。このメソッドは、指定された証拠の安全な標準のアクセス許可セットを返します。</span><span class="sxs-lookup"><span data-stu-id="853cd-141">As a replacement, .NET Framework 4 provides the <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> method, which returns a safe, standard permission set for the provided evidence.</span></span>

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a><span data-ttu-id="853cd-142">サンドボックス化以外のシナリオ: アセンブリ読み込みのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="853cd-142">Non-Sandboxing Scenarios: Overloads for Assembly Loads</span></span>

<span data-ttu-id="853cd-143">アセンブリ読み込みオーバーロードを使用する目的は、アセンブリのサンドボックス化の代わりに、アセンブリ読み込みオーバーロードでないと使用できないパラメーターを指定することです。</span><span class="sxs-lookup"><span data-stu-id="853cd-143">The reason for using an assembly load overload might be to use parameters that are not otherwise available, instead of sandboxing the assembly.</span></span> <span data-ttu-id="853cd-144">.NET Framework 4 以降では、パラメーターとしてオブジェクトを必要としないアセンブリ読み込みオーバーロード (たとえば、) を使用して、 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType> このシナリオを有効にします。</span><span class="sxs-lookup"><span data-stu-id="853cd-144">Starting with the .NET Framework 4, assembly load overloads that do not require a <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> object as a parameter, for example, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, enable this scenario.</span></span>

<span data-ttu-id="853cd-145">アセンブリをサンドボックス化する場合には、<xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> オーバー ロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="853cd-145">If you want to sandbox an assembly, use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a><span data-ttu-id="853cd-146">互換性: CAS ポリシーのレガシー オプションを使用する</span><span class="sxs-lookup"><span data-stu-id="853cd-146">Compatibility: Using the CAS Policy Legacy Option</span></span>

<span data-ttu-id="853cd-147">[ \<NetFx40_LegacySecurityPolicy> 構成要素](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)では、プロセスまたはライブラリが従来の CAS ポリシーを使用するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="853cd-147">The [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) lets you specify that a process or library uses legacy CAS policy.</span></span> <span data-ttu-id="853cd-148">この要素を有効にすると、ポリシーと証拠のオーバーロードは、framework の以前のバージョンの場合と同様に動作します。</span><span class="sxs-lookup"><span data-stu-id="853cd-148">When you enable this element, the policy and evidence overloads will work as they did in previous versions of the framework.</span></span>

> [!NOTE]
> <span data-ttu-id="853cd-149">CAS ポリシーの動作は特定のランタイム バージョンに固有なので、そのランタイム バージョンの CAS ポリシーを変更しても、別のバージョンの CAS ポリシーには影響しません。</span><span class="sxs-lookup"><span data-stu-id="853cd-149">CAS policy behavior is specified on a runtime version basis, so modifying CAS policy for one runtime version does not affect the CAS policy of another version.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="853cd-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="853cd-150">See also</span></span>

- [<span data-ttu-id="853cd-151">方法: サンドボックスで部分信頼コードを実行する</span><span class="sxs-lookup"><span data-stu-id="853cd-151">How to: Run Partially Trusted Code in a Sandbox</span></span>](how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="853cd-152">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="853cd-152">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
