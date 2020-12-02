---
title: 'セキュリティ: ASP.NET Web フォームおよびでの認証と承認 Blazor'
description: ASP.NET Web フォームおよびで認証と承認を処理する方法について説明し Blazor ます。
author: ardalis
ms.author: daroth
no-loc:
- Blazor
ms.date: 11/20/2020
ms.openlocfilehash: 0344960237a5d9da61eb0d85987c44e136f1be48
ms.sourcegitcommit: 2f485e721f7f34b87856a51181b5b56624b31fd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2020
ms.locfileid: "96509846"
---
# <a name="security-authentication-and-authorization-in-aspnet-web-forms-and-no-locblazor"></a><span data-ttu-id="90942-103">セキュリティ:ASP.NET Web Forms および Blazor  での認証と承認</span><span class="sxs-lookup"><span data-stu-id="90942-103">Security: Authentication and Authorization in ASP.NET Web Forms and Blazor</span></span>

<span data-ttu-id="90942-104">ASP.NET の Web フォームアプリケーションからに移行する Blazor 場合、アプリケーションで認証が構成されていることを前提として、ほとんどの場合、認証と承認の実行方法を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90942-104">Migrating from an ASP.NET Web Forms application to Blazor will almost certainly require updating how authentication and authorization are performed, assuming the application had authentication configured.</span></span> <span data-ttu-id="90942-105">この章では、ASP.NET Web フォームユニバーサルプロバイダーモデル (メンバーシップ、ロール、およびユーザープロファイルの場合) から移行する方法と、アプリから ASP.NET Core Id を使用する方法について説明し Blazor ます。</span><span class="sxs-lookup"><span data-stu-id="90942-105">This chapter will cover how to migrate from the ASP.NET Web Forms universal provider model (for membership, roles, and user profiles) and how to work with ASP.NET Core Identity from Blazor apps.</span></span> <span data-ttu-id="90942-106">この章では、大まかな手順と考慮事項について説明しますが、詳細な手順とスクリプトについては、参照されているドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="90942-106">While this chapter will cover the high-level steps and considerations, the detailed steps and scripts may be found in the referenced documentation.</span></span>

## <a name="aspnet-universal-providers"></a><span data-ttu-id="90942-107">ASP.NET ユニバーサルプロバイダー</span><span class="sxs-lookup"><span data-stu-id="90942-107">ASP.NET universal providers</span></span>

<span data-ttu-id="90942-108">ASP.NET 2.0 以降、ASP.NET Web Forms platform は、メンバーシップなどのさまざまな機能のプロバイダーモデルをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="90942-108">Since ASP.NET 2.0, the ASP.NET Web Forms platform has supported a provider model for a variety of features, including membership.</span></span> <span data-ttu-id="90942-109">ユニバーサルメンバーシッププロバイダーは、オプションのロールプロバイダーと共に、一般的に ASP.NET Web フォームアプリケーションと共に展開されます。</span><span class="sxs-lookup"><span data-stu-id="90942-109">The universal membership provider, along with the optional role provider, is commonly deployed with ASP.NET Web Forms applications.</span></span> <span data-ttu-id="90942-110">現在も引き続き正常に機能する認証と承認を管理するための、堅牢で安全な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="90942-110">It offers a robust and secure way to manage authentication and authorization that continues to work well today.</span></span> <span data-ttu-id="90942-111">これらのユニバーサルプロバイダーの最新のオファリングは、NuGet パッケージである、 [Microsoft](https://www.nuget.org/packages/Microsoft.AspNet.Providers)で提供されています。</span><span class="sxs-lookup"><span data-stu-id="90942-111">The most recent offering of these universal providers is available as a NuGet package, [Microsoft.AspNet.Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers).</span></span>

<span data-ttu-id="90942-112">ユニバーサルプロバイダーは、、、、などのテーブルを含む SQL データベーススキーマを操作し `aspnet_Applications` `aspnet_Membership` `aspnet_Roles` `aspnet_Users` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-112">The Universal Providers work with a SQL database schema that includes tables like `aspnet_Applications`, `aspnet_Membership`, `aspnet_Roles`, and `aspnet_Users`.</span></span> <span data-ttu-id="90942-113">[aspnet_regsql.exe コマンド](/previous-versions/ms229862(v=vs.140))を実行して構成すると、基になるデータを操作するために必要なすべてのクエリとコマンドを提供するテーブルとストアドプロシージャがプロバイダーによってインストールされます。</span><span class="sxs-lookup"><span data-stu-id="90942-113">When configured by running the [aspnet_regsql.exe command](/previous-versions/ms229862(v=vs.140)), the providers install tables and stored procedures that provide all of the necessary queries and commands to work with the underlying data.</span></span> <span data-ttu-id="90942-114">データベーススキーマとこれらのストアドプロシージャは、新しい ASP.NET Identity および ASP.NET Core Id システムと互換性がないため、既存のデータを新しいシステムに移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90942-114">The database schema and these stored procedures are not compatible with newer ASP.NET Identity and ASP.NET Core Identity systems, so existing data must be migrated into the new system.</span></span> <span data-ttu-id="90942-115">図1は、ユニバーサルプロバイダー用に構成されたテーブルスキーマの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="90942-115">Figure 1 shows an example table schema configured for universal providers.</span></span>

![ユニバーサルプロバイダースキーマ](./media/security/membership-tables.png)

<span data-ttu-id="90942-117">ユニバーサルプロバイダーは、ユーザー、メンバーシップ、ロール、およびプロファイルを処理します。</span><span class="sxs-lookup"><span data-stu-id="90942-117">The universal provider handles users, membership, roles, and profiles.</span></span> <span data-ttu-id="90942-118">ユーザーにはグローバル一意識別子が割り当てられ、ユーザー Id やユーザー名などの基本情報がテーブルに格納されます。 `aspnet_Users`</span><span class="sxs-lookup"><span data-stu-id="90942-118">Users are assigned globally unique identifiers and basic information like userId, userName etc. are stored in the `aspnet_Users` table.</span></span> <span data-ttu-id="90942-119">パスワード、パスワード形式、パスワード salt、ロックアウトカウンター、詳細などの認証情報は、テーブルに格納されます。 `aspnet_Membership`</span><span class="sxs-lookup"><span data-stu-id="90942-119">Authentication information, such as password, password format, password salt, lockout counters and details, etc. are stored in the `aspnet_Membership` table.</span></span> <span data-ttu-id="90942-120">ロールは、名前と一意の識別子の単純なもので構成され、アソシエーションテーブルを介してユーザーに割り当てられ `aspnet_UsersInRoles` 、多対多のリレーションシップを提供します。</span><span class="sxs-lookup"><span data-stu-id="90942-120">Roles consist simply of names and unique identifiers, which are assigned to users via the `aspnet_UsersInRoles` association table, providing a many-to-many relationship.</span></span>

<span data-ttu-id="90942-121">既存のシステムがメンバーシップに加えてロールを使用している場合は、ユーザーアカウント、関連付けられているパスワード、ロール、およびロールメンバーシップを ASP.NET Core Id に移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90942-121">If your existing system is using roles in addition to membership, you will need to migrate the user accounts, the associated passwords, the roles, and the role membership into ASP.NET Core Identity.</span></span> <span data-ttu-id="90942-122">また、通常は、if ステートメントを使用して、宣言型のフィルター、属性、またはタグヘルパーを利用することで、現在ロールチェックを実行しているコードを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90942-122">You will also most likely need to update your code where you're currently performing role checks using if statements to instead leverage declarative filters, attributes, and/or tag helpers.</span></span> <span data-ttu-id="90942-123">移行に関する考慮事項の詳細については、この章の最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90942-123">We will review migration considerations in greater detail at the end of this chapter.</span></span>

### <a name="authorization-configuration-in-web-forms"></a><span data-ttu-id="90942-124">Web フォームでの承認構成</span><span class="sxs-lookup"><span data-stu-id="90942-124">Authorization configuration in Web Forms</span></span>

<span data-ttu-id="90942-125">ASP.NET Web フォームアプリケーションで特定のページへの承認されたアクセスを構成するには、通常、匿名ユーザーが特定のページまたはフォルダーにアクセスできないように指定します。</span><span class="sxs-lookup"><span data-stu-id="90942-125">To configure authorized access to certain pages in an ASP.NET Web Forms application, typically you specify that certain pages or folders are inaccessible to anonymous users.</span></span> <span data-ttu-id="90942-126">この構成は、web.config ファイルで行います。</span><span class="sxs-lookup"><span data-stu-id="90942-126">This configuration is done in the web.config file:</span></span>

```xml
<?xml version="1.0"?>
<configuration>
    <system.web>
      <authentication mode="Forms">
        <forms defaultUrl="~/home.aspx" loginUrl="~/login.aspx"
          slidingExpiration="true" timeout="2880"></forms>
      </authentication>

      <authorization>
        <deny users="?" />
      </authorization>
    </system.web>
</configuration>
```

<span data-ttu-id="90942-127">構成セクションでは、 `authentication` アプリケーションのフォーム認証を設定します。</span><span class="sxs-lookup"><span data-stu-id="90942-127">The `authentication` configuration section sets up the forms authentication for the application.</span></span> <span data-ttu-id="90942-128">セクションは、 `authorization` アプリケーション全体の匿名ユーザーを許可しないために使用されます。</span><span class="sxs-lookup"><span data-stu-id="90942-128">The `authorization` section is used to disallow anonymous users for the entire application.</span></span> <span data-ttu-id="90942-129">ただし、場所ごとにより詳細な承認規則を提供したり、ロールベースの承認チェックを適用したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="90942-129">However, you can provide more granular authorization rules on a per-location basis as well as apply role-based authorization checks.</span></span>

```xml
<location path="login.aspx">
  <system.web>
    <authorization>
      <allow users="*" />
    </authorization>
  </system.web>
</location>
```

<span data-ttu-id="90942-130">上記の構成を最初の構成と組み合わせると、匿名ユーザーがログインページにアクセスできるようになり、認証されていないユーザーに対するサイト全体の制限が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="90942-130">The above configuration, when combined with the first one, would allow anonymous users to access the login page, overriding the site-wide restriction on non-authenticated users.</span></span>

```xml
<location path="/admin">
  <system.web>
    <authorization>
      <allow roles="Administrators" />
      <deny users="*" />
    </authorization>
  </system.web>
</location>
```

<span data-ttu-id="90942-131">上記の構成を他の構成と組み合わせて使用すると、 `/admin` フォルダーとその中のすべてのリソースへのアクセスが "Administrators" ロールのメンバーに制限されます。</span><span class="sxs-lookup"><span data-stu-id="90942-131">The above configuration, when combined with the others, restricts access to the `/admin` folder and all resources within it to members of the "Administrators" role.</span></span> <span data-ttu-id="90942-132">この制限は、フォルダールート内に別のファイルを配置することでも適用でき `web.config` `/admin` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-132">This restriction could also be applied by placing a separate `web.config` file within the `/admin` folder root.</span></span>

### <a name="authorization-code-in-web-forms"></a><span data-ttu-id="90942-133">Web フォームでの認証コード</span><span class="sxs-lookup"><span data-stu-id="90942-133">Authorization code in Web Forms</span></span>

<span data-ttu-id="90942-134">を使用してアクセスを構成するだけでなく `web.config` 、Web フォームアプリケーションのアクセスと動作をプログラムで構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="90942-134">In addition to configuring access using `web.config`, you can also programmatically configure access and behavior in your Web Forms application.</span></span> <span data-ttu-id="90942-135">たとえば、特定の操作を実行する機能を制限したり、ユーザーのロールに基づいて特定のデータを表示したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="90942-135">For instance, you can restrict the ability to perform certain operations or view certain data based on the user's role.</span></span>

<span data-ttu-id="90942-136">このコードは、コードビハインドロジックとページ自体の両方で使用できます。</span><span class="sxs-lookup"><span data-stu-id="90942-136">This code can be used both in code-behind logic as well as in the page itself:</span></span>

```html
<% if (HttpContext.Current.User.IsInRole("Administrators")) { %>
  <a href="/admin">Go To Admin</a>
<% } %>
```

<span data-ttu-id="90942-137">ユーザーロールのメンバーシップを確認するだけでなく、認証されているかどうかを判断することもできます (ただし、上記の場所ベースの構成を使用することをお勧めします)。</span><span class="sxs-lookup"><span data-stu-id="90942-137">In addition to checking user role membership, you can also determine if they are authenticated (though often this is better done using the location-based configuration covered above).</span></span> <span data-ttu-id="90942-138">このアプローチの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="90942-138">Below is an example of this approach.</span></span>

```csharp
protected void Page_Load(object sender, EventArgs e)
{
    if (!User.Identity.IsAuthenticated)
    {
        FormsAuthentication.RedirectToLoginPage();
    }
    if (!Roles.IsUserInRole(User.Identity.Name, "Administrators"))
    {
        MessageLabel.Text = "Only administrators can view this.";
        SecretPanel.Visible = false;
    }
}
```

<span data-ttu-id="90942-139">上のコードでは、ロールベースのアクセス制御 (RBAC) を使用して、ページの特定の要素 (など) が `SecretPanel` 現在のユーザーのロールに基づいて表示されるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="90942-139">In the code above, role-based access control (RBAC) is used to determine whether certain elements of the page, such as a `SecretPanel`, are visible based on the current user's role.</span></span>

<span data-ttu-id="90942-140">通常、ASP.NET Web フォームアプリケーションは、ファイル内のセキュリティ `web.config` を構成し、 `.aspx` ページとその関連分離コードファイルに必要なチェックを追加し `.aspx.cs` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-140">Typically, ASP.NET Web Forms applications configure security within the `web.config` file and then add additional checks where needed in `.aspx` pages and their related `.aspx.cs` code-behind files.</span></span> <span data-ttu-id="90942-141">ほとんどのアプリケーションは、多くの場合、追加の役割プロバイダーを使用して、ユニバーサルメンバーシッププロバイダーを利用します。</span><span class="sxs-lookup"><span data-stu-id="90942-141">Most applications leverage the universal membership provider, frequently with the additional role provider.</span></span>

## <a name="aspnet-core-identity"></a><span data-ttu-id="90942-142">ASP.NET Core ID</span><span class="sxs-lookup"><span data-stu-id="90942-142">ASP.NET Core Identity</span></span>

<span data-ttu-id="90942-143">認証と承認を行っていても、ASP.NET Core Id では、ユニバーサルプロバイダーと比較して、異なる抽象化と仮定を使用します。</span><span class="sxs-lookup"><span data-stu-id="90942-143">Although still tasked with authentication and authorization, ASP.NET Core Identity uses a different set of abstractions and assumptions when compared to the universal providers.</span></span> <span data-ttu-id="90942-144">たとえば、新しい Id モデルはサードパーティの認証をサポートしているため、ユーザーはソーシャルメディアアカウントまたは他の信頼された認証プロバイダーを使用して認証を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="90942-144">For example, the new Identity model supports third party authentication, allowing users to authenticate using a social media account or other trusted authentication provider.</span></span> <span data-ttu-id="90942-145">ASP.NET Core Id は、ログイン、ログアウト、登録など、一般的に必要なページの UI をサポートします。</span><span class="sxs-lookup"><span data-stu-id="90942-145">ASP.NET Core Identity supports UI for commonly needed pages like login, logout, and register.</span></span> <span data-ttu-id="90942-146">データアクセスには EF Core を利用し、EF Core の移行を使用して、データモデルをサポートするために必要なスキーマを生成します。</span><span class="sxs-lookup"><span data-stu-id="90942-146">It leverages EF Core for its data access, and uses EF Core migrations to generate the necessary schema required to support its data model.</span></span> <span data-ttu-id="90942-147">[ASP.NET Core での id](/aspnet/core/security/authentication/identity)の概要では、ASP.NET Core id に含まれるものの概要と、その使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="90942-147">This [introduction to Identity on ASP.NET Core](/aspnet/core/security/authentication/identity) provides a good overview of what is included with ASP.NET Core Identity and how to get started working with it.</span></span> <span data-ttu-id="90942-148">アプリケーションとそのデータベースに ASP.NET Core Id をまだ設定していない場合は、開始するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="90942-148">If you haven't already set up ASP.NET Core Identity in your application and its database, it will help you get started.</span></span>

### <a name="roles-claims-and-policies"></a><span data-ttu-id="90942-149">役割、要求、およびポリシー</span><span class="sxs-lookup"><span data-stu-id="90942-149">Roles, claims, and policies</span></span>

<span data-ttu-id="90942-150">ユニバーサルプロバイダーと ASP.NET Core Id の両方で、ロールの概念がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="90942-150">Both the universal providers and ASP.NET Core Identity support the concept of roles.</span></span> <span data-ttu-id="90942-151">ユーザーのロールを作成し、ユーザーをロールに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="90942-151">You can create roles for users and assign users to roles.</span></span> <span data-ttu-id="90942-152">ユーザーは任意の数のロールに属することができ、承認実装の一部としてロールのメンバーシップを確認できます。</span><span class="sxs-lookup"><span data-stu-id="90942-152">Users can belong to any number of roles, and you can verify role membership as part of your authorization implementation.</span></span>

<span data-ttu-id="90942-153">ロールに加えて、ASP.NET Core id では、信頼性情報とポリシーの概念がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="90942-153">In addition to roles, ASP.NET Core identity supports the concepts of claims and policies.</span></span> <span data-ttu-id="90942-154">ロールは、そのロールのユーザーがアクセスできる必要がある一連のリソースに特に対応する必要がありますが、要求は単にユーザーの id の一部になります。</span><span class="sxs-lookup"><span data-stu-id="90942-154">While a role should specifically correspond to a set of resources a user in that role should be able to access, a claim is simply part of a user's identity.</span></span> <span data-ttu-id="90942-155">クレームは、サブジェクトの内容を表す名前と値のペアであり、サブジェクトが実行できる内容ではありません。</span><span class="sxs-lookup"><span data-stu-id="90942-155">A claim is a name value pair that represents what the subject is, not what the subject can do.</span></span>

<span data-ttu-id="90942-156">ユーザーの要求を直接検査し、ユーザーにリソースへのアクセス権を付与する必要があるかどうかを、これらの値に基づいて判断することができます。</span><span class="sxs-lookup"><span data-stu-id="90942-156">It is possible to directly inspect a user's claims and determine based on these values whether a user should be given access to a resource.</span></span> <span data-ttu-id="90942-157">ただし、多くの場合、このようなチェックは繰り返し、システム全体にわたって分散されます。</span><span class="sxs-lookup"><span data-stu-id="90942-157">However, such checks are often repetitive and scattered throughout the system.</span></span> <span data-ttu-id="90942-158">より優れたアプローチは、 *ポリシー* を定義することです。</span><span class="sxs-lookup"><span data-stu-id="90942-158">A better approach is to define a *policy*.</span></span>

<span data-ttu-id="90942-159">承認ポリシーは、1つまたは複数の要件で構成されます。</span><span class="sxs-lookup"><span data-stu-id="90942-159">An authorization policy consists of one or more requirements.</span></span> <span data-ttu-id="90942-160">ポリシーは、のメソッドで承認サービス構成の一部として登録され `ConfigureServices` `Startup.cs` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-160">Policies are registered as part of the authorization service configuration in the `ConfigureServices` method of `Startup.cs`.</span></span> <span data-ttu-id="90942-161">たとえば、次のコードスニペットでは、"Can" という名前のポリシーを構成しています。このポリシーでは、ユーザーが "カナダ" の値を持つ国の要求を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="90942-161">For example, the following code snippet configures a policy called "CanadiansOnly", which has the requirement that the user has the Country claim with the value of "Canada".</span></span>

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("CanadiansOnly", policy => policy.RequireClaim(ClaimTypes.Country, "Canada"));
});
```

<span data-ttu-id="90942-162">[カスタムポリシーの作成方法の詳細については、ドキュメントを参照して](/aspnet/core/security/authorization/policies)ください。</span><span class="sxs-lookup"><span data-stu-id="90942-162">You can [learn more about how to create custom policies in the documentation](/aspnet/core/security/authorization/policies).</span></span>

<span data-ttu-id="90942-163">ポリシーまたはロールを使用しているかどうかにかかわらず、アプリケーションの特定のページで、 Blazor 属性を持つロールまたはポリシーが `[Authorize]` ディレクティブで適用される必要があることを指定でき `@attribute` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-163">Whether you're using policies or roles, you can specify that a particular page in your Blazor application requires that role or policy with the `[Authorize]` attribute, applied with the `@attribute` directive.</span></span>

<span data-ttu-id="90942-164">ロールが必要:</span><span class="sxs-lookup"><span data-stu-id="90942-164">Requiring a role:</span></span>

```csharp
@attribute [Authorize(Roles ="administrators")]
```

<span data-ttu-id="90942-165">ポリシーが満たされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="90942-165">Requiring a policy be satisfied:</span></span>

```csharp
@attribute [Authorize(Policy ="CanadiansOnly")]
```

<span data-ttu-id="90942-166">コード内のユーザーの認証状態、ロール、または要求へのアクセスが必要な場合、この機能を実現するには主に2つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="90942-166">If you need access to a user's authentication state, roles, or claims in your code, there are two primary ways to achieve this functionality.</span></span> <span data-ttu-id="90942-167">1つ目は、認証状態をカスケード型パラメーターとして受け取ることです。</span><span class="sxs-lookup"><span data-stu-id="90942-167">The first is to receive the authentication state as a cascading parameter.</span></span> <span data-ttu-id="90942-168">2つ目は、挿入されたを使用して状態にアクセスすることです `AuthenticationStateProvider` 。</span><span class="sxs-lookup"><span data-stu-id="90942-168">The second is to access the state using an injected `AuthenticationStateProvider`.</span></span> <span data-ttu-id="90942-169">これらの各方法の詳細については、 [ Blazor セキュリティのドキュメント](/aspnet/core/blazor/security/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90942-169">The details of each of these approaches are described in the [Blazor Security documentation](/aspnet/core/blazor/security/).</span></span>

<span data-ttu-id="90942-170">次のコードは、をカスケード型 `AuthenticationState` パラメーターとして受け取る方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="90942-170">The following code shows how to receive the `AuthenticationState` as a cascading parameter:</span></span>

```csharp
[CascadingParameter]
private Task<AuthenticationState> authenticationStateTask { get; set; }
```

<span data-ttu-id="90942-171">このパラメーターを使用すると、次のコードを使用してユーザーを取得できます。</span><span class="sxs-lookup"><span data-stu-id="90942-171">With this parameter in place, you can get the user using this code:</span></span>

```csharp
var authState = await authenticationStateTask;
var user = authState.User;
```

<span data-ttu-id="90942-172">次のコードは、を挿入する方法を示してい `AuthenticationStateProvider` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-172">The following code shows how to inject the `AuthenticationStateProvider`:</span></span>

```csharp
@using Microsoft.AspNetCore.Components.Authorization
@inject AuthenticationStateProvider AuthenticationStateProvider
```

<span data-ttu-id="90942-173">プロバイダーを配置すると、次のコードを使用してユーザーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="90942-173">With the provider in place, you can gain access to the user with the following code:</span></span>

```csharp
AuthenticationState authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
ClaimsPrincipal user = authState.User;

if (user.Identity.IsAuthenticated)
{
  // work with user.Claims and/or user.Roles
}
```

<span data-ttu-id="90942-174">**注:**`AuthorizeView`この章の後半で説明するコンポーネントは、ユーザーがページまたはコンポーネントに表示する内容を宣言的に制御する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="90942-174">**Note:** The `AuthorizeView` component, covered later in this chapter, provides a declarative way to control what a user sees on a page or component.</span></span>

<span data-ttu-id="90942-175">(サーバーアプリケーションで) ユーザーと要求を操作するに Blazor は、 `UserManager<T>` `IdentityUser` ユーザーの要求を列挙および変更するために使用できる (既定で使用する) を挿入することも必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="90942-175">To work with users and claims (in Blazor Server applications) you may also need to inject a `UserManager<T>` (use `IdentityUser` for default) which you can use to enumerate and modify claims for a user.</span></span> <span data-ttu-id="90942-176">最初に型を挿入し、それをプロパティに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="90942-176">First inject the type and assign it to a property:</span></span>

```csharp
@inject UserManager<IdentityUser> MyUserManager
```

<span data-ttu-id="90942-177">次に、それを使用してユーザーの要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="90942-177">Then use it to work with the user's claims.</span></span> <span data-ttu-id="90942-178">次のサンプルは、ユーザーにクレームを追加して永続化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="90942-178">The following sample shows how to add and persist a claim on a user:</span></span>

```csharp
private async Task AddCountryClaim()
{
    var authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
    var user = authState.User;
    var identityUser = await MyUserManager.FindByNameAsync(user.Identity.Name);

    if (!user.HasClaim(c => c.Type == ClaimTypes.Country))
    {
        // stores the claim in the cookie
        ClaimsIdentity id = new ClaimsIdentity();
        id.AddClaim(new Claim(ClaimTypes.Country, "Canada"));
        user.AddIdentity(id);

        // save the claim in the database
        await MyUserManager.AddClaimAsync(identityUser, new Claim(ClaimTypes.Country, "Canada"));
    }
}
```

<span data-ttu-id="90942-179">ロールを使用する必要がある場合は、同じアプローチに従います。</span><span class="sxs-lookup"><span data-stu-id="90942-179">If you need to work with roles, follow the same approach.</span></span> <span data-ttu-id="90942-180">`RoleManager<T>` `IdentityRole` ロール自体の一覧表示と管理には、(既定の型に使用) を挿入する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="90942-180">You may need to inject a `RoleManager<T>` (use `IdentityRole` for default type) to list and manage the roles themselves.</span></span>

<span data-ttu-id="90942-181">**注:**BlazorWebassembly では、これらの操作を実行するためにサーバー api を提供する必要があります (またはを直接使用するので `UserManager<T>` はなく `RoleManager<T>` )。</span><span class="sxs-lookup"><span data-stu-id="90942-181">**Note:** In Blazor WebAssembly projects, you will need to provide server APIs to perform these operations (instead of using `UserManager<T>` or `RoleManager<T>` directly).</span></span> <span data-ttu-id="90942-182">BlazorWebassembly アプリケーションは、この目的のために公開されている API エンドポイントを安全に呼び出すことによって、信頼性情報や役割を管理します。</span><span class="sxs-lookup"><span data-stu-id="90942-182">A Blazor WebAssembly client application would manage claims and/or roles by securely calling API endpoints exposed for this purpose.</span></span>

### <a name="migration-guide"></a><span data-ttu-id="90942-183">移行ガイド</span><span class="sxs-lookup"><span data-stu-id="90942-183">Migration guide</span></span>

<span data-ttu-id="90942-184">ASP.NET Web フォームとユニバーサルプロバイダーから ASP.NET Core Id に移行するには、いくつかの手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90942-184">Migrating from ASP.NET Web Forms and universal providers to ASP.NET Core Identity requires several steps:</span></span>

1. <span data-ttu-id="90942-185">ASP.NET Core Id データベーススキーマを転送先データベースに作成する</span><span class="sxs-lookup"><span data-stu-id="90942-185">Create ASP.NET Core Identity database schema in the destination database</span></span>
2. <span data-ttu-id="90942-186">ユニバーサルプロバイダースキーマから ASP.NET Core Id スキーマにデータを移行する</span><span class="sxs-lookup"><span data-stu-id="90942-186">Migrate data from universal provider schema to ASP.NET Core Identity schema</span></span>
3. <span data-ttu-id="90942-187">からミドルウェアおよびサービスに構成を移行します。通常は、 `web.config``Startup.cs`</span><span class="sxs-lookup"><span data-stu-id="90942-187">Migrate configuration from the `web.config` to middleware and services, typically in `Startup.cs`</span></span>
4. <span data-ttu-id="90942-188">コントロールと条件を使用して個々のページを更新し、タグヘルパーと新しい id Api を使用します。</span><span class="sxs-lookup"><span data-stu-id="90942-188">Update individual pages using controls and conditionals to use tag helpers and new identity APIs.</span></span>

<span data-ttu-id="90942-189">以下のセクションでは、これらの各手順について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="90942-189">Each of these steps is described in detail in the following sections.</span></span>

### <a name="creating-the-aspnet-core-identity-schema"></a><span data-ttu-id="90942-190">ASP.NET Core Id スキーマの作成</span><span class="sxs-lookup"><span data-stu-id="90942-190">Creating the ASP.NET Core Identity schema</span></span>

<span data-ttu-id="90942-191">ASP.NET Core Id に使用される必要なテーブル構造を作成するには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="90942-191">There are several ways to create the necessary table structure used for ASP.NET Core Identity.</span></span> <span data-ttu-id="90942-192">最も簡単なのは、新しい ASP.NET Core Web アプリケーションを作成することです。</span><span class="sxs-lookup"><span data-stu-id="90942-192">The simplest is to create a new ASP.NET Core Web application.</span></span> <span data-ttu-id="90942-193">[Web アプリケーション] を選択し、個々のユーザーアカウントを使用するように認証を変更します。</span><span class="sxs-lookup"><span data-stu-id="90942-193">Choose Web Application and then change Authentication to use Individual User Accounts.</span></span>

![個々のユーザーアカウントを持つ新しいプロジェクト](./media/security/individual-user-accounts.png)

<span data-ttu-id="90942-195">コマンドラインからを実行すると、同じことを行うことができ `dotnet new webapp -au Individual` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-195">From the command line, you can do the same thing by running `dotnet new webapp -au Individual`.</span></span> <span data-ttu-id="90942-196">アプリが作成されたら、それを実行し、サイトに登録します。</span><span class="sxs-lookup"><span data-stu-id="90942-196">Once the app has been created, run it and register on the site.</span></span> <span data-ttu-id="90942-197">次のようなページをトリガーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="90942-197">You should trigger a page like the one shown below:</span></span>

![[移行の適用] ページ](./media/security/apply-migrations-page.png)

<span data-ttu-id="90942-199">[移行の適用] ボタンをクリックすると、必要なデータベーステーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="90942-199">Click on the "Apply Migrations" button and the necessary database tables should be created for you.</span></span> <span data-ttu-id="90942-200">また、次のように、移行ファイルがプロジェクトに表示されます。</span><span class="sxs-lookup"><span data-stu-id="90942-200">In addition, the migration files should appear in your project, as shown:</span></span>

![移行ファイル](./media/security/migration-files.png)

<span data-ttu-id="90942-202">次のコマンドラインツールを使用すると、web アプリケーションを実行しなくても、自分で移行を実行できます。</span><span class="sxs-lookup"><span data-stu-id="90942-202">You can run the migration yourself, without running the web application, using this command-line tool:</span></span>

```powershell
dotnet ef database update
```

<span data-ttu-id="90942-203">新しいスキーマを既存のデータベースに適用するスクリプトを実行する場合は、コマンドラインからこれらの移行をスクリプト化することができます。</span><span class="sxs-lookup"><span data-stu-id="90942-203">If you would rather run a script to apply the new schema to an existing database, you can script these migrations from the command-line.</span></span> <span data-ttu-id="90942-204">次のコマンドを実行して、スクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="90942-204">Run this command to generate the script:</span></span>

```powershell
dotnet ef migrations script -o auth.sql
```

<span data-ttu-id="90942-205">上記のコマンドを実行すると、出力ファイルに SQL スクリプトが生成され `auth.sql` 、任意のデータベースに対して実行できます。</span><span class="sxs-lookup"><span data-stu-id="90942-205">The above command will produce a SQL script in the output file `auth.sql`, which can then be run against whatever database you like.</span></span> <span data-ttu-id="90942-206">コマンドの実行で問題が発生した場合は、 `dotnet ef` [EF Core ツールがシステムにインストールされ](/ef/core/miscellaneous/cli/dotnet)ていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="90942-206">If you have any trouble running `dotnet ef` commands, [make sure you have the EF Core tools installed on your system](/ef/core/miscellaneous/cli/dotnet).</span></span>

<span data-ttu-id="90942-207">ソーステーブルに列が追加されている場合は、新しいスキーマでこれらの列の最適な場所を特定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90942-207">In the event you have additional columns on your source tables, you will need to identify the best location for these columns in the new schema.</span></span> <span data-ttu-id="90942-208">一般に、テーブルで見つかった列は `aspnet_Membership` テーブルにマップする必要があり `AspNetUsers` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-208">Generally, columns found on the `aspnet_Membership` table should be mapped to the `AspNetUsers` table.</span></span> <span data-ttu-id="90942-209">の列 `aspnet_Roles` をにマップする必要があり `AspNetRoles` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-209">Columns on `aspnet_Roles` should be mapped to `AspNetRoles`.</span></span> <span data-ttu-id="90942-210">テーブルのその他の列 `aspnet_UsersInRoles` がテーブルに追加され `AspNetUserRoles` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-210">Any additional columns on the `aspnet_UsersInRoles` table would be added to the `AspNetUserRoles` table.</span></span>

<span data-ttu-id="90942-211">また、別のテーブルに列を追加することも検討してください。</span><span class="sxs-lookup"><span data-stu-id="90942-211">It's also worth considering putting any additional columns on separate tables.</span></span> <span data-ttu-id="90942-212">そのため、今後の移行では、既定の id スキーマのカスタマイズを考慮する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="90942-212">So that future migrations won't need to take into account such customizations of the default identity schema.</span></span>

### <a name="migrating-data-from-universal-providers-to-aspnet-core-identity"></a><span data-ttu-id="90942-213">ユニバーサルプロバイダーから ASP.NET Core Id へのデータの移行</span><span class="sxs-lookup"><span data-stu-id="90942-213">Migrating data from universal providers to ASP.NET Core Identity</span></span>

<span data-ttu-id="90942-214">変換先テーブルスキーマを配置したら、次の手順では、ユーザーとロールのレコードを新しいスキーマに移行します。</span><span class="sxs-lookup"><span data-stu-id="90942-214">Once you have the destination table schema in place, the next step is to migrate your user and role records to the new schema.</span></span> <span data-ttu-id="90942-215">スキーマの相違点 (どの列がどの新しい列にマップされているかなど) の完全な一覧については、 [こちら](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90942-215">A complete list of the schema differences, including which columns map to which new columns, can be found [here](/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span>

<span data-ttu-id="90942-216">メンバーシップから新しい id テーブルにユーザーを移行するには、 [ドキュメントに記載](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)されている手順に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="90942-216">To migrate your users from membership to the new identity tables, you should [follow the steps described in the documentation](/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span> <span data-ttu-id="90942-217">次の手順とスクリプトを実行した後、ユーザーは次回ログインするときにパスワードを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90942-217">After following these steps and the script provided, your users will need to change their password the next time they log in.</span></span>

<span data-ttu-id="90942-218">ユーザーのパスワードを移行することはできますが、プロセスはさらに複雑になります。</span><span class="sxs-lookup"><span data-stu-id="90942-218">It is possible to migrate user passwords but the process is much more involved.</span></span> <span data-ttu-id="90942-219">移行プロセスの一環としてユーザーがパスワードを更新する必要があり、新しい一意のパスワードを使用するように勧めることは、アプリケーションの全体的なセキュリティを強化することです。</span><span class="sxs-lookup"><span data-stu-id="90942-219">Requiring users to update their passwords as part of the migration process, and encouraging them to use new, unique passwords, is likely to enhance the overall security of the application.</span></span>

### <a name="migrating-security-settings-from-webconfig-to-startupcs"></a><span data-ttu-id="90942-220">web.config から Startup.cs へのセキュリティ設定の移行</span><span class="sxs-lookup"><span data-stu-id="90942-220">Migrating security settings from web.config to Startup.cs</span></span>

<span data-ttu-id="90942-221">前述のように、ASP.NET のメンバーシップとロールプロバイダーは、アプリケーションのファイルで構成され `web.config` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-221">As noted above, ASP.NET membership and role providers are configured in the application's `web.config` file.</span></span> <span data-ttu-id="90942-222">ASP.NET Core アプリは IIS に関連付けられていないため、構成に別のシステムを使用するため、これらの設定は別の場所で構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90942-222">Since ASP.NET Core apps are not tied to IIS and use a separate system for configuration, these settings must be configured elsewhere.</span></span> <span data-ttu-id="90942-223">ほとんどの場合、ASP.NET Core Id はファイルで構成され `Startup.cs` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-223">For the most part, ASP.NET Core Identity is configured in the `Startup.cs` file.</span></span> <span data-ttu-id="90942-224">(Id テーブルスキーマを生成するために) 前に作成した web プロジェクトを開き、そのファイルを確認し `Startup.cs` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-224">Open the web project that was created earlier (to generate the identity table schema) and review its `Startup.cs` file.</span></span>

<span data-ttu-id="90942-225">既定の ConfigureServices メソッドは、EF Core と Id のサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="90942-225">The default ConfigureServices method adds support for EF Core and Identity:</span></span>

```csharp
// This method gets called by the runtime. Use this method to add services to the container.
public void ConfigureServices(IServiceCollection services)
{
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
}
```

<span data-ttu-id="90942-226">`AddDefaultIdentity`拡張メソッドは、既定のとフレームワークの型を使用するように id を構成するために使用され `ApplicationDbContext` `IdentityUser` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-226">The `AddDefaultIdentity` extension method is used to configure Identity to use the default `ApplicationDbContext` and the framework's `IdentityUser` type.</span></span> <span data-ttu-id="90942-227">カスタムを使用している場合は `IdentityUser` 、ここでその型を指定してください。</span><span class="sxs-lookup"><span data-stu-id="90942-227">If you're using a custom `IdentityUser`, be sure to specify its type here.</span></span> <span data-ttu-id="90942-228">これらの拡張メソッドがアプリケーションで動作していない場合は、適切な using ステートメントがあることと、必要な NuGet パッケージ参照があることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="90942-228">If these extension methods aren't working in your application, check that you have the appropriate using statements and that you have the necessary NuGet package references.</span></span> <span data-ttu-id="90942-229">たとえば、プロジェクトにはいくつかのバージョンのおよびパッケージが参照されている必要があり `Microsoft.AspNetCore.Identity.EntityFrameworkCore` `Microsoft.AspNetCore.Identity.UI` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-229">For example, your project should have some version of the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` and `Microsoft.AspNetCore.Identity.UI` packages referenced.</span></span>

<span data-ttu-id="90942-230">また、 `Startup.cs` サイトに必要なミドルウェアが構成されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="90942-230">Also in `Startup.cs` you should see the necessary middleware configured for the site.</span></span> <span data-ttu-id="90942-231">具体的には、 `UseAuthentication` とは `UseAuthorization` 適切な場所に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="90942-231">Specifically, `UseAuthentication` and `UseAuthorization` should be set up, and in the proper location.</span></span>

```csharp

// This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
        app.UseDatabaseErrorPage();
    }
    else
    {
        app.UseExceptionHandler("/Error");
        // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
        app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
}
```

<span data-ttu-id="90942-232">ASP.NET Identity は、からの場所への匿名またはロールベースのアクセスを構成しません `Startup.cs` 。</span><span class="sxs-lookup"><span data-stu-id="90942-232">ASP.NET Identity does not configure anonymous or role-based access to locations from `Startup.cs`.</span></span> <span data-ttu-id="90942-233">ASP.NET Core のフィルターには、場所固有の承認構成データを移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90942-233">You will need to migrate any location-specific authorization configuration data to filters in ASP.NET Core.</span></span> <span data-ttu-id="90942-234">このような更新が必要なフォルダーとページをメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="90942-234">Make note of which folders and pages will require such updates.</span></span> <span data-ttu-id="90942-235">これらの変更は、次のセクションで行います。</span><span class="sxs-lookup"><span data-stu-id="90942-235">You will make these changes in the next section.</span></span>

### <a name="updating-individual-pages-to-use-aspnet-core-identity-abstractions"></a><span data-ttu-id="90942-236">ASP.NET Core Id の抽象化を使用するように個々のページを更新する</span><span class="sxs-lookup"><span data-stu-id="90942-236">Updating individual pages to use ASP.NET Core Identity abstractions</span></span>

<span data-ttu-id="90942-237">ASP.NET Web フォームアプリケーションで、 `web.config` 匿名ユーザーに特定のページまたはフォルダーへのアクセスを拒否する設定があった場合、その `[Authorize]` ようなページに属性を追加することによって、これらの変更を移行します。</span><span class="sxs-lookup"><span data-stu-id="90942-237">In your ASP.NET Web Forms application, if you had `web.config` settings to deny access to certain pages or folders to anonymous users, you would migrate these changes by adding the `[Authorize]` attribute to such pages:</span></span>

```razor
@attribute [Authorize]
```

<span data-ttu-id="90942-238">特定のロールに属しているユーザー以外のアクセスを拒否した場合は、ロールを指定する属性を追加して、この動作を移行することもできます。</span><span class="sxs-lookup"><span data-stu-id="90942-238">If you further had denied access except to those users belonging to a certain role, you would likewise migrate this behavior by adding an attribute specifying a role:</span></span>

```razor
@attribute [Authorize(Roles ="administrators")]
```

<span data-ttu-id="90942-239">属性は、 `[Authorize]` `@page` ルーター経由で到達したコンポーネントに対してのみ機能し Blazor ます。</span><span class="sxs-lookup"><span data-stu-id="90942-239">The `[Authorize]` attribute only works on `@page` components that are reached via the Blazor Router.</span></span> <span data-ttu-id="90942-240">属性は子コンポーネントでは使用できませんが、代わりにを使用する必要があり `AuthorizeView` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-240">The attribute does not work with child components, which should instead use `AuthorizeView`.</span></span>

<span data-ttu-id="90942-241">特定のユーザーにコードを表示するかどうかを判断するためのロジックがページマークアップ内にある場合は、これをコンポーネントで置き換えることができ `AuthorizeView` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-241">If you have logic within page markup for determining whether to display some code to a certain user, you can replace this with the `AuthorizeView` component.</span></span> <span data-ttu-id="90942-242">[Authorizeview コンポーネント](/aspnet/core/blazor/security#authorizeview-component)は、ユーザーが表示を許可されているかどうかに応じて、UI を選択的に表示します。</span><span class="sxs-lookup"><span data-stu-id="90942-242">The [AuthorizeView component](/aspnet/core/blazor/security#authorizeview-component) selectively displays UI depending on whether the user is authorized to see it.</span></span> <span data-ttu-id="90942-243">また、 `context` ユーザー情報へのアクセスに使用できる変数も公開されています。</span><span class="sxs-lookup"><span data-stu-id="90942-243">It also exposes a `context` variable that can be used to access user information.</span></span>

```razor
<AuthorizeView>
    <Authorized>
        <h1>Hello, @context.User.Identity.Name!</h1>
        <p>You can only see this content if you are authenticated.</p>
    </Authorized>
    <NotAuthorized>
        <h1>Authentication Failure!</h1>
        <p>You are not signed in.</p>
    </NotAuthorized>
</AuthorizeView>
```

<span data-ttu-id="90942-244">`Task<AuthenticationState`属性を使用して構成されたからユーザーにアクセスすることで、手続き型ロジック内の認証状態にアクセスでき `[CascadingParameter]` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-244">You can access the authentication state within procedural logic by accessing the user from a `Task<AuthenticationState` configured with the `[CascadingParameter]` attribute.</span></span> <span data-ttu-id="90942-245">この構成を使用すると、ユーザーにアクセスできるようになります。認証されているかどうか、および特定のロールに属しているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="90942-245">This configuration will get you access to the user, which can let you determine if they are authenticated and if they belong to a particular role.</span></span> <span data-ttu-id="90942-246">ポリシー procedurally を評価する必要がある場合は、のインスタンスを挿入 `IAuthorizationService` し、そのインスタンスでメソッドを呼び出すことができ `AuthorizeAsync` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-246">If you need to evaluate a policy procedurally, you can inject an instance of the `IAuthorizationService` and calls the `AuthorizeAsync` method on it.</span></span> <span data-ttu-id="90942-247">次のサンプルコードは、ユーザー情報を取得し、承認されたユーザーがポリシーによって制限されたタスクを実行することを許可する方法を示して `content-editor` います。</span><span class="sxs-lookup"><span data-stu-id="90942-247">The following sample code demonstrates how to get user information and allow an authorized user to perform a task restricted by the `content-editor` policy.</span></span>

```razor
@using Microsoft.AspNetCore.Authorization
@inject IAuthorizationService AuthorizationService

<button @onclick="@DoSomething">Do something important</button>

@code {
    [CascadingParameter]
    private Task<AuthenticationState> authenticationStateTask { get; set; }

    private async Task DoSomething()
    {
        var user = (await authenticationStateTask).User;

        if (user.Identity.IsAuthenticated)
        {
            // Perform an action only available to authenticated (signed-in) users.
        }

        if (user.IsInRole("admin"))
        {
            // Perform an action only available to users in the 'admin' role.
        }

        if ((await AuthorizationService.AuthorizeAsync(user, "content-editor"))
            .Succeeded)
        {
            // Perform an action only available to users satisfying the
            // 'content-editor' policy.
        }
    }
}
```

<span data-ttu-id="90942-248">最初のは、 `AuthenticationState` このようなカスケード型のパラメーターにバインドする前に、カスケード値として設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90942-248">The `AuthenticationState` first need to be set up as a cascading value before it can be bound to a cascading parameter like this.</span></span> <span data-ttu-id="90942-249">通常、これはコンポーネントを使用し `CascadingAuthenticationState` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-249">That's typically done using the `CascadingAuthenticationState` component.</span></span> <span data-ttu-id="90942-250">通常、この構成は次のように行われ `App.razor` ます。</span><span class="sxs-lookup"><span data-stu-id="90942-250">This configuration is typically done in `App.razor`:</span></span>

```razor
<CascadingAuthenticationState>
    <Router AppAssembly="@typeof(Program).Assembly">
        <Found Context="routeData">
            <AuthorizeRouteView RouteData="@routeData"
                DefaultLayout="@typeof(MainLayout)" />
        </Found>
        <NotFound>
            <LayoutView Layout="@typeof(MainLayout)">
                <p>Sorry, there's nothing at this address.</p>
            </LayoutView>
        </NotFound>
    </Router>
</CascadingAuthenticationState>
```

## <a name="summary"></a><span data-ttu-id="90942-251">まとめ</span><span class="sxs-lookup"><span data-stu-id="90942-251">Summary</span></span>

<span data-ttu-id="90942-252">Blazor では、ASP.NET Core Id である ASP.NET Core と同じセキュリティモデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="90942-252">Blazor uses the same security model as ASP.NET Core, which is ASP.NET Core Identity.</span></span> <span data-ttu-id="90942-253">カスタマイズが元のデータスキーマに適用されていないと仮定すると、ユニバーサルプロバイダーから ASP.NET Core Id への移行は比較的簡単です。</span><span class="sxs-lookup"><span data-stu-id="90942-253">Migrating from universal providers to ASP.NET Core Identity is relatively straightforward, assuming not too much customization was applied to the original data schema.</span></span> <span data-ttu-id="90942-254">データが移行されたら、アプリでの認証と承認の使用に Blazor ついて詳しく説明されています。また、ほとんどのセキュリティ要件をプログラムによってサポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="90942-254">Once the data has been migrated, working with authentication and authorization in Blazor apps is well documented, with configurable as well as programmatic support for most security requirements.</span></span>

## <a name="references"></a><span data-ttu-id="90942-255">References</span><span class="sxs-lookup"><span data-stu-id="90942-255">References</span></span>

- [<span data-ttu-id="90942-256">ASP.NET Core での Id の概要</span><span class="sxs-lookup"><span data-stu-id="90942-256">Introduction to Identity on ASP.NET Core</span></span>](/aspnet/core/security/authentication/identity)
- [<span data-ttu-id="90942-257">ASP.NET メンバーシップ認証から ASP.NET Core 2.0 Id に移行する</span><span class="sxs-lookup"><span data-stu-id="90942-257">Migrate from ASP.NET Membership authentication to ASP.NET Core 2.0 Identity</span></span>](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)
- [<span data-ttu-id="90942-258">認証と Id を ASP.NET Core に移行する</span><span class="sxs-lookup"><span data-stu-id="90942-258">Migrate Authentication and Identity to ASP.NET Core</span></span>](/aspnet/core/migration/identity)
- [<span data-ttu-id="90942-259">Blazor認証と承認の ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="90942-259">ASP.NET Core Blazor authentication and authorization</span></span>](/aspnet/core/blazor/security/)

>[!div class="step-by-step"]
><span data-ttu-id="90942-260">[前へ](config.md)
>[次へ](migration.md)</span><span class="sxs-lookup"><span data-stu-id="90942-260">[Previous](config.md)
[Next](migration.md)</span></span>
