---
title: '方法: GenericPrincipal オブジェクトと GenericIdentity オブジェクトを作成する'
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Creating Generic Identity Objects
- GenericPrincipal Objects
- Creating GenericPrincipal Objects
- GenericIdentity Objects
ms.assetid: 465694cf-258b-4747-9dae-35b01a5bcdbb
ms.openlocfilehash: cde4669a1bac49d1d9fde39c99707561379aec19
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818994"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a><span data-ttu-id="3f19a-102">方法: GenericPrincipal オブジェクトと GenericIdentity オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="3f19a-102">How to: Create GenericPrincipal and GenericIdentity Objects</span></span>

> [!NOTE]
> <span data-ttu-id="3f19a-103">この記事は、Windows に適用されます。</span><span class="sxs-lookup"><span data-stu-id="3f19a-103">This article applies to Windows.</span></span>
>
> <span data-ttu-id="3f19a-104">ASP.NET Core の詳細については、「 [ASP.NET Core セキュリティの概要](/aspnet/core/security/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f19a-104">For information about ASP.NET Core, see [Overview of ASP.NET Core Security](/aspnet/core/security/).</span></span>

<span data-ttu-id="3f19a-105">クラスをクラスと共に使用して、 <xref:System.Security.Principal.GenericIdentity> <xref:System.Security.Principal.GenericPrincipal> Windows ドメインに依存しない認証スキームを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="3f19a-105">You can use the <xref:System.Security.Principal.GenericIdentity> class in conjunction with the <xref:System.Security.Principal.GenericPrincipal> class to create an authorization scheme that exists independent of a Windows domain.</span></span>

### <a name="to-create-a-genericprincipal-object"></a><span data-ttu-id="3f19a-106">GenericPrincipal オブジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="3f19a-106">To create a GenericPrincipal object</span></span>

1. <span data-ttu-id="3f19a-107">ID クラスの新しいインスタンスを作成し、インスタンスに付ける名前で初期化します。</span><span class="sxs-lookup"><span data-stu-id="3f19a-107">Create a new instance of the identity class and initialize it with the name you want it to hold.</span></span> <span data-ttu-id="3f19a-108">新しい **GenericIdentity** オブジェクトを作成し、名前 `MyUser` で初期化するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3f19a-108">The following code creates a new **GenericIdentity** object and initializes it with the name `MyUser`.</span></span>

    ```vb
    Dim myIdentity As New GenericIdentity("MyUser")
    ```

    ```csharp
    GenericIdentity myIdentity = new GenericIdentity("MyUser");
    ```

2. <span data-ttu-id="3f19a-109">**GenericPrincipal** クラスの新しいインスタンスを作成し、前に作成した **GenericIdentity** オブジェクトと、プリンシパルに関連付けるロールを表す文字列の配列で、このインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="3f19a-109">Create a new instance of the **GenericPrincipal** class and initialize it with the previously created **GenericIdentity** object and an array of strings that represent the roles that you want associated with this principal.</span></span> <span data-ttu-id="3f19a-110">管理者のロールとユーザーのロールを表す文字列の配列を指定するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3f19a-110">The following code example specifies an array of strings that represent an administrator role and a user role.</span></span> <span data-ttu-id="3f19a-111">**GenericPrincipal** は、前の **GenericIdentity** と文字列配列で初期化されます。</span><span class="sxs-lookup"><span data-stu-id="3f19a-111">The **GenericPrincipal** is then initialized with the previous **GenericIdentity** and the string array.</span></span>

    ```vb
    Dim myStringArray As String() = {"Manager", "Teller"}
    DIm myPrincipal As New GenericPrincipal(myIdentity, myStringArray)
    ```

    ```csharp
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal = new GenericPrincipal(myIdentity, myStringArray);
    ```

3. <span data-ttu-id="3f19a-112">次のコードを使用して、プリンシパルを現在のスレッドに結合します。</span><span class="sxs-lookup"><span data-stu-id="3f19a-112">Use the following code to attach the principal to the current thread.</span></span> <span data-ttu-id="3f19a-113">これは、プリンシパルを複数回検証する必要がある場合、アプリケーションで実行されている他のコードによって検証する必要がある場合、またはオブジェクトによって検証する必要がある場合に役立ち <xref:System.Security.Permissions.PrincipalPermission> ます。</span><span class="sxs-lookup"><span data-stu-id="3f19a-113">This is valuable in situations where the principal must be validated several times, it must be validated by other code running in your application, or it must be validated by a <xref:System.Security.Permissions.PrincipalPermission> object.</span></span> <span data-ttu-id="3f19a-114">このような場合でも、プリンシパル オブジェクトをスレッドに結合せずにロール ベースの検証を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3f19a-114">You can still perform role-based validation on the principal object without attaching it to the thread.</span></span> <span data-ttu-id="3f19a-115">詳細については、「[プリンシパル オブジェクトの置き換え](replacing-a-principal-object.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f19a-115">For more information, see [Replacing a Principal Object](replacing-a-principal-object.md).</span></span>

    ```vb
    Thread.CurrentPrincipal = myPrincipal
    ```

    ```csharp
    Thread.CurrentPrincipal = myPrincipal;
    ```

## <a name="example"></a><span data-ttu-id="3f19a-116">例</span><span class="sxs-lookup"><span data-stu-id="3f19a-116">Example</span></span>

<span data-ttu-id="3f19a-117">次のコード例では、**GenericPrincipal** と **GenericIdentity** のインスタンスを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3f19a-117">The following code example demonstrates how to create an instance of a **GenericPrincipal** and a **GenericIdentity**.</span></span> <span data-ttu-id="3f19a-118">このコードは、各オブジェクトの値をコンソールに表示します。</span><span class="sxs-lookup"><span data-stu-id="3f19a-118">This code displays the values of these objects to the console.</span></span>

```vb
Imports System.Security.Principal
Imports System.Threading

Public Class Class1

    Public Shared Sub Main()
        ' Create generic identity.
        Dim myIdentity As New GenericIdentity("MyIdentity")

        ' Create generic principal.
        Dim myStringArray As String() =  {"Manager", "Teller"}
        Dim myPrincipal As New GenericPrincipal(myIdentity, myStringArray)

        ' Attach the principal to the current thread.
        ' This is not required unless repeated validation must occur,
        ' other code in your application must validate, or the
        ' PrincipalPermission object is used.
        Thread.CurrentPrincipal = myPrincipal

        ' Print values to the console.
        Dim name As String = myPrincipal.Identity.Name
        Dim auth As Boolean = myPrincipal.Identity.IsAuthenticated
        Dim isInRole As Boolean = myPrincipal.IsInRole("Manager")

        Console.WriteLine("The name is: {0}", name)
        Console.WriteLine("The isAuthenticated is: {0}", auth)
        Console.WriteLine("Is this a Manager? {0}", isInRole)

    End Sub

End Class
```

```csharp
using System;
using System.Security.Principal;
using System.Threading;

public class Class1
{
    public static int Main(string[] args)
    {
    // Create generic identity.
    GenericIdentity myIdentity = new GenericIdentity("MyIdentity");

    // Create generic principal.
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal =
        new GenericPrincipal(myIdentity, myStringArray);

    // Attach the principal to the current thread.
    // This is not required unless repeated validation must occur,
    // other code in your application must validate, or the
    // PrincipalPermission object is used.
    Thread.CurrentPrincipal = myPrincipal;

    // Print values to the console.
    String name =  myPrincipal.Identity.Name;
    bool auth =  myPrincipal.Identity.IsAuthenticated;
    bool isInRole =  myPrincipal.IsInRole("Manager");

    Console.WriteLine("The name is: {0}", name);
    Console.WriteLine("The isAuthenticated is: {0}", auth);
    Console.WriteLine("Is this a Manager? {0}", isInRole);

    return 0;
    }
}
```

<span data-ttu-id="3f19a-119">実行されると、アプリケーションの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3f19a-119">When executed, the application displays output similar to the following.</span></span>

```console
The Name is: MyIdentity
The IsAuthenticated is: True
Is this a Manager? True
```

## <a name="see-also"></a><span data-ttu-id="3f19a-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f19a-120">See also</span></span>

- <xref:System.Security.Principal.GenericIdentity>
- <xref:System.Security.Principal.GenericPrincipal>
- <xref:System.Security.Permissions.PrincipalPermission>
- [<span data-ttu-id="3f19a-121">プリンシパル オブジェクトの置き換え</span><span class="sxs-lookup"><span data-stu-id="3f19a-121">Replacing a Principal Object</span></span>](replacing-a-principal-object.md)
- [<span data-ttu-id="3f19a-122">プリンシパル オブジェクトと ID オブジェクト</span><span class="sxs-lookup"><span data-stu-id="3f19a-122">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
