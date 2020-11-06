---
title: 厳密な名前付けと .NET ライブラリ
description: .NET ライブラリに対する厳密な名前付けに関するベスト プラクティスの推奨事項。
ms.date: 10/16/2018
ms.openlocfilehash: 6f9533d768331964a8e640243536b12ddde158e5
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189213"
---
# <a name="strong-naming"></a><span data-ttu-id="b4f83-103">厳密な名前付け</span><span class="sxs-lookup"><span data-stu-id="b4f83-103">Strong naming</span></span>

<span data-ttu-id="b4f83-104">厳密な名前付けとは、キーを使用してアセンブリに署名し、[厳格な名前付きのアセンブリ](../assembly/strong-named.md)を生成することです。</span><span class="sxs-lookup"><span data-stu-id="b4f83-104">Strong naming refers to signing an assembly with a key, producing a [strong-named assembly](../assembly/strong-named.md).</span></span> <span data-ttu-id="b4f83-105">アセンブリに厳密な名前が付けられている場合、名前とアセンブリのバージョン番号に基づいて一意の ID が作成され、アセンブリの競合を防ぐのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b4f83-105">When an assembly is strong-named, it creates a unique identity based on the name and assembly version number, and it can help prevent assembly conflicts.</span></span>

<span data-ttu-id="b4f83-106">厳密な名前付けの欠点は、Windows 上の .NET Framework で、アセンブリに厳密な名前が付けられると、アセンブリの厳密な読み込みが有効になることです。</span><span class="sxs-lookup"><span data-stu-id="b4f83-106">The downside to strong naming is that .NET Framework on Windows enables strict loading of assemblies once an assembly is strong named.</span></span> <span data-ttu-id="b4f83-107">厳密な名前付きのアセンブリの参照は、読み込まれたアセンブリのバージョンと完全に一致する必要があります。その場合、開発者には、アセンブリを使用する際に[バインド リダイレクトの構成](../../framework/configure-apps/redirect-assembly-versions.md)が強制されます。</span><span class="sxs-lookup"><span data-stu-id="b4f83-107">A strong-named assembly reference must exactly match the version of the loaded assembly, forcing developers to [configure binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) when using the assembly:</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly" publicKeyToken="32ab4ba45e0a69a1" culture="neutral" />
            <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

<span data-ttu-id="b4f83-108">.NET 開発者が厳密な名前付けについて不満を持つ場合、通常、その内容は厳密なアセンブリの読み込みに関するものです。</span><span class="sxs-lookup"><span data-stu-id="b4f83-108">When .NET developers complain about strong naming, what they're usually complaining about is strict assembly loading.</span></span> <span data-ttu-id="b4f83-109">さいわい、この問題は .NET Framework に特定されます。</span><span class="sxs-lookup"><span data-stu-id="b4f83-109">Fortunately, this issue is isolated to .NET Framework.</span></span> <span data-ttu-id="b4f83-110">.NET 5+、.NET Core、Xamarin、UWP、その他のほとんどの .NET 実装には、厳密な名前付けの主な欠点である厳密なアセンブリ読み込みがありません。</span><span class="sxs-lookup"><span data-stu-id="b4f83-110">.NET 5+, .NET Core, Xamarin, UWP, and most other .NET implementations don't have strict assembly loading, which is the main downside of strong naming.</span></span>

<span data-ttu-id="b4f83-111">厳密な名前付けの重要な側面の 1 つはウイルスです。厳密な名前付きのアセンブリで参照できるのは、他の厳密な名前付きのアセンブリのみです。</span><span class="sxs-lookup"><span data-stu-id="b4f83-111">One important aspect of strong naming is that it's viral: a strong named assembly can only reference other strong named assemblies.</span></span> <span data-ttu-id="b4f83-112">ご利用のライブラリに厳密な名前が付けられていない場合、厳密な名前付けが必要なアプリケーションやライブラリを構築している開発者はその使用から除外されています。</span><span class="sxs-lookup"><span data-stu-id="b4f83-112">If your library isn't strong named, then you have excluded developers who are building an application or library that needs strong naming from using it.</span></span>

<span data-ttu-id="b4f83-113">厳密な名前付けの利点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b4f83-113">The benefits of strong naming are:</span></span>

1. <span data-ttu-id="b4f83-114">アセンブリを他の厳密な名前付きのアセンブリで参照して使用することができます。</span><span class="sxs-lookup"><span data-stu-id="b4f83-114">The assembly can be referenced and used by other strong-named assemblies.</span></span>
2. <span data-ttu-id="b4f83-115">アセンブリをグローバル アセンブリ キャッシュ (GAC) に格納することができます。</span><span class="sxs-lookup"><span data-stu-id="b4f83-115">The assembly can be stored in the Global Assembly Cache (GAC).</span></span>
3. <span data-ttu-id="b4f83-116">アセンブリを、他のバージョンのアセンブリと並行して読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="b4f83-116">The assembly can be loaded side by side with other versions of the assembly.</span></span> <span data-ttu-id="b4f83-117">通常、アセンブリの並行読み込みは、プラグイン アーキテクチャを持つアプリケーションで必要となります。</span><span class="sxs-lookup"><span data-stu-id="b4f83-117">Side-by-side assembly loading is commonly required by applications with plug-in architectures.</span></span>

## <a name="create-strong-named-net-libraries"></a><span data-ttu-id="b4f83-118">厳密な名前付き .NET ライブラリを作成する</span><span class="sxs-lookup"><span data-stu-id="b4f83-118">Create strong named .NET libraries</span></span>

<span data-ttu-id="b4f83-119">オープンソースの .NET ライブラリには厳密な名前を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4f83-119">You should strong name your open-source .NET libraries.</span></span> <span data-ttu-id="b4f83-120">アセンブリに厳密な名前を付けることで、ほとんどの人が確実にそれを使用できるようになり、厳密なアセンブリの読み込みは .NET Framework にのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="b4f83-120">Strong naming an assembly ensures the most people can use it, and strict assembly loading only affects .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="b4f83-121">このガイダンスは、NuGet.org で公開されている .NET ライブラリなど、公的に配布されている .NET ライブラリに固有のものです。厳密な名前付けはほとんどの .NET アプリケーションで必要はなく、既定では行われません。</span><span class="sxs-lookup"><span data-stu-id="b4f83-121">This guidance is specific to publicly distributed .NET libraries, such as .NET libraries published on NuGet.org. Strong naming is not required by most .NET applications and should not be done by default.</span></span>

<span data-ttu-id="b4f83-122">✔️ 検討すること: ご利用のライブラリのアセンブリに厳密な名前を付ける。</span><span class="sxs-lookup"><span data-stu-id="b4f83-122">✔️ CONSIDER strong naming your library's assemblies.</span></span>

<span data-ttu-id="b4f83-123">✔️ 検討すること: ご利用のソース管理システムに厳密な名前付けキーを追加する。</span><span class="sxs-lookup"><span data-stu-id="b4f83-123">✔️ CONSIDER adding the strong naming key to your source control system.</span></span>

> <span data-ttu-id="b4f83-124">一般公開されているキーを使用することで、開発者はライブラリ ソース コードを同じキーで変更および再コンパイルすることができます。</span><span class="sxs-lookup"><span data-stu-id="b4f83-124">A publicly available key lets developers modify and recompile your library source code with the same key.</span></span>
>
> <span data-ttu-id="b4f83-125">[部分信頼シナリオ](../../framework/misc/using-libraries-from-partially-trusted-code.md)において特別なアクセス許可を付与するために、厳密な名前付けキーが過去に使用されていた場合は、そのキーを一般公開しないでください。</span><span class="sxs-lookup"><span data-stu-id="b4f83-125">You shouldn't make the strong naming key public if it has been used in the past to give special permissions in [partial-trust scenarios](../../framework/misc/using-libraries-from-partially-trusted-code.md).</span></span> <span data-ttu-id="b4f83-126">そうしないと、既存の環境が損なわれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b4f83-126">Otherwise, you might compromise existing environments.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4f83-127">コードの発行元の ID が必要な場合は、[Authenticode](/windows-hardware/drivers/install/authenticode) と [NuGet パッケージ署名](/nuget/create-packages/sign-a-package)をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b4f83-127">When the identity of the publisher of the code is desired, [Authenticode](/windows-hardware/drivers/install/authenticode) and [NuGet Package Signing](/nuget/create-packages/sign-a-package) are recommended.</span></span> <span data-ttu-id="b4f83-128">セキュリティ対策としてコード アクセス セキュリティ (CAS) を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b4f83-128">Code Access Security (CAS) should not be used as a security mitigation.</span></span>

<span data-ttu-id="b4f83-129">✔️ 検討すること: ユーザーによるバインド リダイレクトとその更新頻度を減らせるように、アセンブリのバージョンをメジャー バージョン変更時にのみインクリメントする。</span><span class="sxs-lookup"><span data-stu-id="b4f83-129">✔️ CONSIDER incrementing the assembly version on only major version changes to help users reduce binding redirects, and how often they're updated.</span></span>

> <span data-ttu-id="b4f83-130">詳細については、[バージョン管理とアセンブリのバージョン](./versioning.md#assembly-version)に関する記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4f83-130">Read more about [versioning and the assembly version](./versioning.md#assembly-version).</span></span>

<span data-ttu-id="b4f83-131">❌ 厳密な名前付けキーを追加、削除、または変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="b4f83-131">❌ DO NOT add, remove, or change the strong naming key.</span></span>

> <span data-ttu-id="b4f83-132">アセンブリの厳密な名前付けキーを変更すると、アセンブリの ID が変更され、それを使用するコンパイル済みコードが中断されます。</span><span class="sxs-lookup"><span data-stu-id="b4f83-132">Modifying an assembly's strong naming key changes the assembly's identity and breaks compiled code that uses it.</span></span> <span data-ttu-id="b4f83-133">詳細については、[バイナリの破壊的変更](./breaking-changes.md#binary-breaking-change)に関する記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4f83-133">For more information, see [binary breaking changes](./breaking-changes.md#binary-breaking-change).</span></span>

<span data-ttu-id="b4f83-134">ご利用のライブラリで、厳密な名前が指定されたバージョンおよび厳密でない名前が指定されたバージョンを ❌ 発行しないでください。</span><span class="sxs-lookup"><span data-stu-id="b4f83-134">❌ DO NOT publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="b4f83-135">たとえば、`Contoso.Api` と`Contoso.Api.StrongNamed` です。</span><span class="sxs-lookup"><span data-stu-id="b4f83-135">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

> <span data-ttu-id="b4f83-136">2 つのパッケージを発行すると、開発者のエコシステムが分岐されます。</span><span class="sxs-lookup"><span data-stu-id="b4f83-136">Publishing two packages forks your developer eco-system.</span></span> <span data-ttu-id="b4f83-137">また、両方のパッケージに従ってアプリケーションが停止した場合、型名の競合が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b4f83-137">Also, if an application ends up depending on both packages the developer can encounter type name conflicts.</span></span> <span data-ttu-id="b4f83-138">.NET の場合、さまざまなアセンブリにはさまざまな型があります。</span><span class="sxs-lookup"><span data-stu-id="b4f83-138">As far as .NET is concerned they are different types in different assemblies.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b4f83-139">[前へ](cross-platform-targeting.md)
>[次へ](nuget.md)</span><span class="sxs-lookup"><span data-stu-id="b4f83-139">[Previous](cross-platform-targeting.md)
[Next](nuget.md)</span></span>
