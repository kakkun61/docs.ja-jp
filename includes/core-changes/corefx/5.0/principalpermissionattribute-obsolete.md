---
ms.openlocfilehash: d9526055041f036958699aa935aa6cfef494b520
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434965"
---
### <a name="principalpermissionattribute-is-obsolete-as-error"></a><span data-ttu-id="e624b-101">PrincipalPermissionAttribute は現在使用されていないエラーです</span><span class="sxs-lookup"><span data-stu-id="e624b-101">PrincipalPermissionAttribute is obsolete as error</span></span>

<span data-ttu-id="e624b-102"><xref:System.Security.Permissions.PrincipalPermissionAttribute> コンストラクターは非推奨であり、コンパイル時のエラーを発生させます。</span><span class="sxs-lookup"><span data-stu-id="e624b-102">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructor is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="e624b-103">この属性をインスタンス化したり、メソッドに適用したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e624b-103">You cannot instantiate this attribute or apply it to a method.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e624b-104">変更の説明</span><span class="sxs-lookup"><span data-stu-id="e624b-104">Change description</span></span>

<span data-ttu-id="e624b-105">.NET Framework と .NET Core では、<xref:System.Security.Permissions.PrincipalPermissionAttribute> 属性を使用してメソッドに注釈を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="e624b-105">On .NET Framework and .NET Core, you can annotate methods with the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute.</span></span> <span data-ttu-id="e624b-106">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e624b-106">For example:</span></span>

```csharp
[PrincipalPermission(SecurityAction.Demand, Role = "Administrators")]
public void MyMethod()
{
    // Code that should only run when the current user is an administrator.
}
```

<span data-ttu-id="e624b-107">.NET 5.0 以降では、<xref:System.Security.Permissions.PrincipalPermissionAttribute> 属性をメソッドに適用できません。</span><span class="sxs-lookup"><span data-stu-id="e624b-107">Starting in .NET 5.0, you cannot apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a method.</span></span> <span data-ttu-id="e624b-108">この属性のコンストラクターは非推奨であり、コンパイル時のエラーを発生させます。</span><span class="sxs-lookup"><span data-stu-id="e624b-108">The constructor for the attribute is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="e624b-109">他の非推奨警告とは異なり、エラーを非表示にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e624b-109">Unlike other obsoletion warnings, you can't suppress the error.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e624b-110">変更理由</span><span class="sxs-lookup"><span data-stu-id="e624b-110">Reason for change</span></span>

<span data-ttu-id="e624b-111"><xref:System.Security.Permissions.SecurityAttribute> をサブクラス化する他の型と同様に、<xref:System.Security.Permissions.PrincipalPermissionAttribute> 型は .NET のコード アクセス セキュリティ (CAS) インフラストラクチャに含まれます。</span><span class="sxs-lookup"><span data-stu-id="e624b-111">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> type, like other types that subclass <xref:System.Security.Permissions.SecurityAttribute>, is part of .NET's Code Access Security (CAS) infrastructure.</span></span> <span data-ttu-id="e624b-112">.NET Framework 2.x から 4.x では、完全信頼のシナリオの下でアプリケーションが実行されている場合でも、ランタイムによってメソッド エントリで <xref:System.Security.Permissions.PrincipalPermissionAttribute> 注釈が強制されます。</span><span class="sxs-lookup"><span data-stu-id="e624b-112">In .NET Framework 2.x - 4.x, the runtime enforces <xref:System.Security.Permissions.PrincipalPermissionAttribute> annotations on method entry, even if the application is running under a full-trust scenario.</span></span> <span data-ttu-id="e624b-113">.NET Core と .NET 5.0 以降では CAS 属性がサポートされず、ランタイムで無視されます。</span><span class="sxs-lookup"><span data-stu-id="e624b-113">.NET Core and .NET 5.0 and later don't support CAS attributes, and the runtime ignores them.</span></span>

<span data-ttu-id="e624b-114">.NET Framework の動作と .NET Core と .NET 5.0 の動作がこのように違うことで、アクセスをブロックすべきなのに許可される "フェール オープン" シナリオが発生します。</span><span class="sxs-lookup"><span data-stu-id="e624b-114">This difference in behavior from .NET Framework to .NET Core and .NET 5.0 can result in a "fail open" scenario, where access should have been blocked but instead has been allowed.</span></span> <span data-ttu-id="e624b-115">"フェール オープン" シナリオを回避するため、.NET 5.0 以降を対象とするコードではこの属性を適用できません。</span><span class="sxs-lookup"><span data-stu-id="e624b-115">To prevent the "fail open" scenario, you can no longer apply the attribute in code that targets .NET 5.0 or later.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e624b-116">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="e624b-116">Version introduced</span></span>

<span data-ttu-id="e624b-117">5.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="e624b-117">5.0 Preview 7</span></span>

#### <a name=""></a><span data-ttu-id="e624b-118"><a id="permission-action">推奨される操作</a></span><span class="sxs-lookup"><span data-stu-id="e624b-118"><a id="permission-action">Recommended action</a></span></span>

<span data-ttu-id="e624b-119">非推奨エラーが発生する場合、措置をとる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e624b-119">If you encounter the obsoletion error, you must take action.</span></span>

- <span data-ttu-id="e624b-120">**ASP.NET MVC アクション メソッドにこの属性を適用する場合:**</span><span class="sxs-lookup"><span data-stu-id="e624b-120">**If you're applying the attribute to an ASP.NET MVC action method:**</span></span>

  <span data-ttu-id="e624b-121">ASP.NET に組み込まれている承認インフラストラクチャを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="e624b-121">Consider using ASP.NET's built-in authorization infrastructure.</span></span> <span data-ttu-id="e624b-122">次のコードからは、<xref:System.Web.Mvc.AuthorizeAttribute> 属性を使用してコントローラーに注釈を付ける方法がわかります。</span><span class="sxs-lookup"><span data-stu-id="e624b-122">The following code demonstrates how to annotate a controller with an <xref:System.Web.Mvc.AuthorizeAttribute> attribute.</span></span> <span data-ttu-id="e624b-123">ASP.NET ランタイムによって、アクションの実行前に、ユーザーが承認されます。</span><span class="sxs-lookup"><span data-stu-id="e624b-123">The ASP.NET runtime will authorize the user before performing the action.</span></span>

  ```csharp
  using Microsoft.AspNetCore.Authorization;

  namespace MySampleApp
  {
      [Authorize(Roles = "Administrator")]
      public class AdministrationController : Controller
      {
          public ActionResult MyAction()
          {
              // This code won't run unless the current user
              // is in the 'Administrator' role.
          }
      }
  }
  ```

  <span data-ttu-id="e624b-124">詳細については、「[ASP.NET Core でのロールベースの承認](/aspnet/core/security/authorization/roles)」と「[ASP.NET Core での承認の概要](/aspnet/core/security/authorization/introduction)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e624b-124">For more information, see [Role-based authorization in ASP.NET Core](/aspnet/core/security/authorization/roles) and [Introduction to authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span>

- <span data-ttu-id="e624b-125">**Web アプリのコンテキスト外でライブラリ コードにこの属性を適用する場合:**</span><span class="sxs-lookup"><span data-stu-id="e624b-125">**If you're applying the attribute to library code outside the context of a web app:**</span></span>

  <span data-ttu-id="e624b-126">メソッドの先頭で手動確認します。</span><span class="sxs-lookup"><span data-stu-id="e624b-126">Perform the checks manually at the beginning of your method.</span></span> <span data-ttu-id="e624b-127">これは <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> メソッドを使用すると実行できます。</span><span class="sxs-lookup"><span data-stu-id="e624b-127">This can be done by using the <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> method.</span></span>

  ```csharp
  using System.Threading;

  void DoSomething()
  {
      if (Thread.CurrentPrincipal == null
          || !Thread.CurrentPrincipal.IsInRole("Administrators"))
      {
          throw new Exception("User is anonymous or isn't an admin.");
      }

      // Code that should run only when user is an administrator.
  }
  ```

#### <a name="category"></a><span data-ttu-id="e624b-128">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="e624b-128">Category</span></span>

- <span data-ttu-id="e624b-129">Core .NET ライブラリ</span><span class="sxs-lookup"><span data-stu-id="e624b-129">Core .NET libraries</span></span>
- <span data-ttu-id="e624b-130">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e624b-130">Security</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e624b-131">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="e624b-131">Affected APIs</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Permissions.PrincipalPermissionAttribute`

-->
