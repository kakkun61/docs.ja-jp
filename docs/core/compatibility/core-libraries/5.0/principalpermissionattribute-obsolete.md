---
title: 破壊的変更:PrincipalPermissionAttribute は現在使用されていないエラーです
description: Core .NET ライブラリにおける .NET 5.0 の破壊的変更について学習します。PrincipalPermissionAttribute コンストラクターは非推奨であり、コンパイル時のエラーを発生させます。
ms.date: 11/01/2020
ms.openlocfilehash: 138bbf25fd493c1bb9c2b3f10b62681c735ea7b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759452"
---
# <a name="principalpermissionattribute-is-obsolete-as-error"></a><span data-ttu-id="e71e9-103">PrincipalPermissionAttribute は現在使用されていないエラーです</span><span class="sxs-lookup"><span data-stu-id="e71e9-103">PrincipalPermissionAttribute is obsolete as error</span></span>

<span data-ttu-id="e71e9-104"><xref:System.Security.Permissions.PrincipalPermissionAttribute> コンストラクターは非推奨であり、コンパイル時のエラーを発生させます。</span><span class="sxs-lookup"><span data-stu-id="e71e9-104">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructor is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="e71e9-105">この属性をインスタンス化したり、メソッドに適用したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e71e9-105">You cannot instantiate this attribute or apply it to a method.</span></span>

## <a name="change-description"></a><span data-ttu-id="e71e9-106">変更の説明</span><span class="sxs-lookup"><span data-stu-id="e71e9-106">Change description</span></span>

<span data-ttu-id="e71e9-107">.NET Framework と .NET Core では、<xref:System.Security.Permissions.PrincipalPermissionAttribute> 属性を使用してメソッドに注釈を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="e71e9-107">On .NET Framework and .NET Core, you can annotate methods with the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute.</span></span> <span data-ttu-id="e71e9-108">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e71e9-108">For example:</span></span>

```csharp
[PrincipalPermission(SecurityAction.Demand, Role = "Administrators")]
public void MyMethod()
{
    // Code that should only run when the current user is an administrator.
}
```

<span data-ttu-id="e71e9-109">.NET 5.0 以降では、<xref:System.Security.Permissions.PrincipalPermissionAttribute> 属性をメソッドに適用できません。</span><span class="sxs-lookup"><span data-stu-id="e71e9-109">Starting in .NET 5.0, you cannot apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a method.</span></span> <span data-ttu-id="e71e9-110">この属性のコンストラクターは非推奨であり、コンパイル時のエラーを発生させます。</span><span class="sxs-lookup"><span data-stu-id="e71e9-110">The constructor for the attribute is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="e71e9-111">他の非推奨警告とは異なり、エラーを非表示にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e71e9-111">Unlike other obsoletion warnings, you can't suppress the error.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="e71e9-112">変更理由</span><span class="sxs-lookup"><span data-stu-id="e71e9-112">Reason for change</span></span>

<span data-ttu-id="e71e9-113"><xref:System.Security.Permissions.SecurityAttribute> をサブクラス化する他の型と同様に、<xref:System.Security.Permissions.PrincipalPermissionAttribute> 型は .NET のコード アクセス セキュリティ (CAS) インフラストラクチャに含まれます。</span><span class="sxs-lookup"><span data-stu-id="e71e9-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> type, like other types that subclass <xref:System.Security.Permissions.SecurityAttribute>, is part of .NET's Code Access Security (CAS) infrastructure.</span></span> <span data-ttu-id="e71e9-114">.NET Framework 2.x から 4.x では、完全信頼のシナリオの下でアプリケーションが実行されている場合でも、ランタイムによってメソッド エントリで <xref:System.Security.Permissions.PrincipalPermissionAttribute> 注釈が強制されます。</span><span class="sxs-lookup"><span data-stu-id="e71e9-114">In .NET Framework 2.x - 4.x, the runtime enforces <xref:System.Security.Permissions.PrincipalPermissionAttribute> annotations on method entry, even if the application is running under a full-trust scenario.</span></span> <span data-ttu-id="e71e9-115">.NET Core と .NET 5.0 以降では CAS 属性がサポートされず、ランタイムで無視されます。</span><span class="sxs-lookup"><span data-stu-id="e71e9-115">.NET Core and .NET 5.0 and later don't support CAS attributes, and the runtime ignores them.</span></span>

<span data-ttu-id="e71e9-116">.NET Framework の動作と .NET Core と .NET 5.0 の動作がこのように違うことで、アクセスをブロックすべきなのに許可される "フェール オープン" シナリオが発生します。</span><span class="sxs-lookup"><span data-stu-id="e71e9-116">This difference in behavior from .NET Framework to .NET Core and .NET 5.0 can result in a "fail open" scenario, where access should have been blocked but instead has been allowed.</span></span> <span data-ttu-id="e71e9-117">"フェール オープン" シナリオを回避するため、.NET 5.0 以降を対象とするコードではこの属性を適用できません。</span><span class="sxs-lookup"><span data-stu-id="e71e9-117">To prevent the "fail open" scenario, you can no longer apply the attribute in code that targets .NET 5.0 or later.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e71e9-118">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="e71e9-118">Version introduced</span></span>

<span data-ttu-id="e71e9-119">5.0</span><span class="sxs-lookup"><span data-stu-id="e71e9-119">5.0</span></span>

## <a name=""></a><span data-ttu-id="e71e9-120"><a id="permission-action">推奨される操作</a></span><span class="sxs-lookup"><span data-stu-id="e71e9-120"><a id="permission-action">Recommended action</a></span></span>

<span data-ttu-id="e71e9-121">非推奨エラーが発生する場合、措置をとる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e71e9-121">If you encounter the obsoletion error, you must take action.</span></span>

- <span data-ttu-id="e71e9-122">**ASP.NET MVC アクション メソッドにこの属性を適用する場合:**</span><span class="sxs-lookup"><span data-stu-id="e71e9-122">**If you're applying the attribute to an ASP.NET MVC action method:**</span></span>

  <span data-ttu-id="e71e9-123">ASP.NET に組み込まれている承認インフラストラクチャを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="e71e9-123">Consider using ASP.NET's built-in authorization infrastructure.</span></span> <span data-ttu-id="e71e9-124">次のコードからは、<xref:System.Web.Mvc.AuthorizeAttribute> 属性を使用してコントローラーに注釈を付ける方法がわかります。</span><span class="sxs-lookup"><span data-stu-id="e71e9-124">The following code demonstrates how to annotate a controller with an <xref:System.Web.Mvc.AuthorizeAttribute> attribute.</span></span> <span data-ttu-id="e71e9-125">ASP.NET ランタイムによって、アクションの実行前に、ユーザーが承認されます。</span><span class="sxs-lookup"><span data-stu-id="e71e9-125">The ASP.NET runtime will authorize the user before performing the action.</span></span>

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

  <span data-ttu-id="e71e9-126">詳細については、「[ASP.NET Core でのロールベースの承認](/aspnet/core/security/authorization/roles)」と「[ASP.NET Core での承認の概要](/aspnet/core/security/authorization/introduction)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e71e9-126">For more information, see [Role-based authorization in ASP.NET Core](/aspnet/core/security/authorization/roles) and [Introduction to authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span>

- <span data-ttu-id="e71e9-127">**Web アプリのコンテキスト外でライブラリ コードにこの属性を適用する場合:**</span><span class="sxs-lookup"><span data-stu-id="e71e9-127">**If you're applying the attribute to library code outside the context of a web app:**</span></span>

  <span data-ttu-id="e71e9-128">メソッドの先頭で手動確認します。</span><span class="sxs-lookup"><span data-stu-id="e71e9-128">Perform the checks manually at the beginning of your method.</span></span> <span data-ttu-id="e71e9-129">これは <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> メソッドを使用すると実行できます。</span><span class="sxs-lookup"><span data-stu-id="e71e9-129">This can be done by using the <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> method.</span></span>

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

## <a name="affected-apis"></a><span data-ttu-id="e71e9-130">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="e71e9-130">Affected APIs</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- Security

### Affected APIs

- `T:System.Security.Permissions.PrincipalPermissionAttribute`

-->
