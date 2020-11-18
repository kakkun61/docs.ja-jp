---
title: 偽装と復帰
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
ms.openlocfilehash: 90f43510eb0e71fb324012fa00ac08f9ee3292ac
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820060"
---
# <a name="impersonating-and-reverting"></a><span data-ttu-id="e9335-102">偽装と復帰</span><span class="sxs-lookup"><span data-stu-id="e9335-102">Impersonating and Reverting</span></span>

> [!NOTE]
> <span data-ttu-id="e9335-103">この記事は、Windows に適用されます。</span><span class="sxs-lookup"><span data-stu-id="e9335-103">This article applies to Windows.</span></span>
>
> <span data-ttu-id="e9335-104">ASP.NET Core の詳細については、「 [ASP.NET Core Security](/aspnet/core/security/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9335-104">For information about ASP.NET Core, see [ASP.NET Core Security](/aspnet/core/security/).</span></span>

<span data-ttu-id="e9335-105">場合によっては、Windows アカウント トークンを取得して、Windows アカウントを偽装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9335-105">Sometimes you might need to obtain a Windows account token to impersonate a Windows account.</span></span> <span data-ttu-id="e9335-106">たとえば、ASP.NET ベースのアプリケーションが、時間によって複数のユーザーの代わりに操作しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="e9335-106">For example, your ASP.NET-based application might have to act on behalf of several users at different times.</span></span> <span data-ttu-id="e9335-107">その場合、アプリケーションはインターネット インフォメーション サービス (IIS) から管理者を表すトークンを受け入れて、そのユーザーを偽装し、操作を実行してから前の ID に戻ります。</span><span class="sxs-lookup"><span data-stu-id="e9335-107">Your application might accept a token that represents an administrator from Internet Information Services (IIS), impersonate that user, perform an operation, and revert to the previous identity.</span></span> <span data-ttu-id="e9335-108">続いて、IIS から管理者より権限が少ないユーザーを表すトークンを受け入れ、操作を実行してから、また元に戻ります。</span><span class="sxs-lookup"><span data-stu-id="e9335-108">Next, it might accept a token from IIS that represents a user with fewer rights, perform some operation, and revert again.</span></span>  
  
 <span data-ttu-id="e9335-109">アプリケーションが、IIS によって現在のスレッドにアタッチされていない Windows アカウントを偽装しなければならない場合は、そのアカウントのトークンを取得し、そのトークンを使用してアカウントをアクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9335-109">In situations where your application must impersonate a Windows account that has not been attached to the current thread by IIS, you must retrieve that account's token and use it to activate the account.</span></span> <span data-ttu-id="e9335-110">それには、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="e9335-110">You can do this by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="e9335-111">アンマネージ **LogonUser** メソッドを呼び出すことによって、特定のユーザーのアカウント トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="e9335-111">Retrieve an account token for a particular user by making a call to the unmanaged **LogonUser** method.</span></span> <span data-ttu-id="e9335-112">このメソッドは .NET 基底クラスライブラリには含まれていませんが、アンマネージ **advapi32.dll** にあります。</span><span class="sxs-lookup"><span data-stu-id="e9335-112">This method is not in the .NET base class library, but is located in the unmanaged **advapi32.dll**.</span></span> <span data-ttu-id="e9335-113">アンマネージ コード内のメソッドへのアクセスは高度な操作であり、ここでは説明しません。</span><span class="sxs-lookup"><span data-stu-id="e9335-113">Accessing methods in unmanaged code is an advanced operation and is beyond the scope of this discussion.</span></span> <span data-ttu-id="e9335-114">詳細については、「[アンマネージ コードとの相互運用](../../framework/interop/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9335-114">For more information, see [Interoperating with Unmanaged Code](../../framework/interop/index.md).</span></span> <span data-ttu-id="e9335-115">**LogonUser** メソッドと **advapi32.dll** の詳細については、プラットフォーム SDK ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9335-115">For more information about the **LogonUser** method and **advapi32.dll**, see the Platform SDK documentation.</span></span>  
  
2. <span data-ttu-id="e9335-116">**WindowsIdentity** クラスの新しいインスタンスを作成し、トークンを渡します。</span><span class="sxs-lookup"><span data-stu-id="e9335-116">Create a new instance of the **WindowsIdentity** class, passing the token.</span></span> <span data-ttu-id="e9335-117">次のコードに、この呼び出しを示します。ここで、`hToken` は Windows トークンを表します。</span><span class="sxs-lookup"><span data-stu-id="e9335-117">The following code demonstrates this call, where `hToken` represents a Windows token.</span></span>  
  
    ```csharp  
    WindowsIdentity impersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim impersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3. <span data-ttu-id="e9335-118">このコードに示されているように、<xref:System.Security.Principal.WindowsImpersonationContext> クラスの新しいインスタンスを作成し、そのインスタンスを、初期化されたクラスの <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> メソッドで初期化することで、偽装を開始します。</span><span class="sxs-lookup"><span data-stu-id="e9335-118">Begin impersonation by creating a new instance of the <xref:System.Security.Principal.WindowsImpersonationContext> class and initializing it with the <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> method of the initialized class, as shown in the following code.</span></span>  
  
    ```csharp  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate()  
    ```  
  
4. <span data-ttu-id="e9335-119">偽装する必要がなくなったら、以下のコードに示されているように <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> メソッドを呼び出して、偽装を元に戻します。</span><span class="sxs-lookup"><span data-stu-id="e9335-119">When you no longer need to impersonate, call the <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> method to revert the impersonation, as shown in the following code.</span></span>  
  
    ```csharp  
    myImpersonation.Undo();  
    ```  
  
    ```vb  
    myImpersonation.Undo()  
    ```  
  
 <span data-ttu-id="e9335-120">信頼されたコードが既にオブジェクトをスレッドにアタッチしている場合は、 <xref:System.Security.Principal.WindowsPrincipal> アカウントトークンを受け取らないインスタンスメソッド **Impersonate** を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="e9335-120">If trusted code has already attached a <xref:System.Security.Principal.WindowsPrincipal> object to the thread, you can call the instance method **Impersonate**, which does not take an account token.</span></span> <span data-ttu-id="e9335-121">この方法が役立つのは、スレッドで **WindowsPrincipal** オブジェクトが表しているユーザーが、現在プロセスが実行されているユーザーではない場合のみです。</span><span class="sxs-lookup"><span data-stu-id="e9335-121">Note that this is only useful when the **WindowsPrincipal** object on the thread represents a user other than the one under which the process is currently executing.</span></span> <span data-ttu-id="e9335-122">このような状態は、たとえば、Windows 認証を有効にして、偽装を無効にした ASP.NET を使用している場合に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="e9335-122">For example, you might encounter this situation using ASP.NET with Windows authentication turned on and impersonation turned off.</span></span> <span data-ttu-id="e9335-123">その場合、プロセスはインターネット インフォメーション サービス (IIS) で構成されたアカウントで実行されますが、現在のプリンシパルは、ページにアクセスしている Windows ユーザーを表しています。</span><span class="sxs-lookup"><span data-stu-id="e9335-123">In this case, the process is running under an account configured in Internet Information Services (IIS) while the current principal represents the Windows user that is accessing the page.</span></span>  
  
 <span data-ttu-id="e9335-124">**Impersonate** も **Undo** も、現在の **Principal** <xref:System.Security.Principal.IPrincipal> 呼び出しコンテキストに関連付けられているプリンシパルオブジェクト () を変更しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e9335-124">Note that neither **Impersonate** nor **Undo** changes the **Principal** object (<xref:System.Security.Principal.IPrincipal>)  associated with the current call context.</span></span> <span data-ttu-id="e9335-125">代わりに、偽装と復帰によって、現在のオペレーティングシステムプロセスに関連付けられているトークンが変更されます。</span><span class="sxs-lookup"><span data-stu-id="e9335-125">Rather, impersonation and reverting change the token associated with the current operating system process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9335-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9335-126">See also</span></span>

- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.Security.Principal.WindowsImpersonationContext>
- [<span data-ttu-id="e9335-127">プリンシパル オブジェクトと ID オブジェクト</span><span class="sxs-lookup"><span data-stu-id="e9335-127">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="e9335-128">アンマネージ コードとの相互運用</span><span class="sxs-lookup"><span data-stu-id="e9335-128">Interoperating with Unmanaged Code</span></span>](../../framework/interop/index.md)
- [<span data-ttu-id="e9335-129">ASP.NET Core のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="e9335-129">ASP.NET Core Security</span></span>](/aspnet/core/security/)
