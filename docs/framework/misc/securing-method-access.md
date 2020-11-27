---
title: メソッド アクセスの保護
description: パブリックに使用することを意図していないがパブリックである必要があるメソッドに対して、メソッドアクセスをセキュリティで保護する方法について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, method access
- secure coding, method access
- security [.NET Framework], method access
- method access security
ms.assetid: f7c2d6ec-3b18-4e0e-9991-acd97189d818
ms.openlocfilehash: 52ae1eb4b6210403ce9c5aa96479809f885b0eba
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251218"
---
# <a name="securing-method-access"></a><span data-ttu-id="53359-103">メソッド アクセスの保護</span><span class="sxs-lookup"><span data-stu-id="53359-103">Securing Method Access</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="53359-104">信頼関係のない任意のコードに呼び出しを許可することが不適切なメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="53359-104">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="53359-105">このようなメソッドは、制限された情報を提供する、渡された任意の情報を信頼する、パラメーターのエラー チェックを行わない、誤ったパラメーターを受け取って正しく機能しないかなんらかの被害をもたらすなどの、いくつかの危険性をもたらします。</span><span class="sxs-lookup"><span data-stu-id="53359-105">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="53359-106">これらのケースを認識し、メソッドを保護するために役立つ措置を講じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="53359-106">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="53359-107">パブリックでの使用を目的としていないメソッドをパブリックとして使用する場合は、メソッドを制限する必要があることがあります。</span><span class="sxs-lookup"><span data-stu-id="53359-107">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="53359-108">たとえば、独自の DLL 経由で呼び出すインターフェイスはパブリックにする必要があります。しかし、顧客がそのインターフェイスを使用したり、悪意のあるコードがコンポーネントへのエントリ ポイントとして攻略したりするのを防ぐために、そのインターフェイスをパブリックとして公開しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="53359-108">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="53359-109">パブリックに使用することを想定していないメソッドを制限するもう1つの一般的な理由は、内部インターフェイスとなる可能性のあるものをドキュメント化してサポートしないことです。</span><span class="sxs-lookup"><span data-stu-id="53359-109">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be an internal interface.</span></span>  
  
 <span data-ttu-id="53359-110">マネージド コードには、メソッド アクセスを制限するいくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="53359-110">Managed code offers several ways to restrict method access:</span></span>  
  
- <span data-ttu-id="53359-111">クラス、アセンブリ、派生クラスが信頼されている場合は、これらへのアクセシビリティのスコープを制限します。</span><span class="sxs-lookup"><span data-stu-id="53359-111">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="53359-112">これが、メソッド アクセスを制限する最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="53359-112">This is the simplest way to limit method access.</span></span> <span data-ttu-id="53359-113">一般に、派生クラスは、派生元のクラスよりも信頼度が低くなる場合がありますが、場合によっては親クラスの id を共有します。</span><span class="sxs-lookup"><span data-stu-id="53359-113">In general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="53359-114">特に、キーワードから信頼を推測しないでください `protected` 。これは、必ずしもセキュリティコンテキストで使用されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="53359-114">In particular, do not infer trust from the keyword `protected`, which is not necessarily used in the security context.</span></span>  
  
- <span data-ttu-id="53359-115">指定された id の呼び出し元へのメソッドアクセスを制限します。基本的には、任意の特定の [証拠](/previous-versions/dotnet/netframework-4.0/7y5x1hcd(v=vs.100)) (厳密な名前、発行元、ゾーンなど) を選択します。</span><span class="sxs-lookup"><span data-stu-id="53359-115">Limit the method access to callers of a specified identity--essentially, any particular [evidence](/previous-versions/dotnet/netframework-4.0/7y5x1hcd(v=vs.100)) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
- <span data-ttu-id="53359-116">選択したアクセス許可を持つ呼び出し元だけにメソッド アクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="53359-116">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="53359-117">同様に、宣言セキュリティを使用すると、クラスの継承を制御できます。</span><span class="sxs-lookup"><span data-stu-id="53359-117">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="53359-118">**InheritanceDemand** を使用して、次の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="53359-118">You can use **InheritanceDemand** to do the following:</span></span>  
  
- <span data-ttu-id="53359-119">派生したクラスに、特定の ID またはアクセス許可を要求します。</span><span class="sxs-lookup"><span data-stu-id="53359-119">Require derived classes to have a specified identity or permission.</span></span>  
  
- <span data-ttu-id="53359-120">特定のメソッドをオーバーライドする派生クラスに、特定の ID またはアクセス許可を要求します。</span><span class="sxs-lookup"><span data-stu-id="53359-120">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="53359-121">呼び出し元に特定の厳密な名前による署名を要求することによってアクセスを制限し、パブリック クラスの保護に役立つ方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="53359-121">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="53359-122">この例では、 <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> 厳密な名前の **要求** でを使用します。</span><span class="sxs-lookup"><span data-stu-id="53359-122">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="53359-123">厳密な名前でアセンブリに署名する方法についてのタスクベースの情報については、「 [Strong-Named アセンブリの作成と使用](../../standard/assembly/create-use-strong-named.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53359-123">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../standard/assembly/create-use-strong-named.md).</span></span>  
  
```vb  
<StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey := "…hex…", Name := "App1", Version := "0.0.0.0")>  _  
Public Class Class1  
End Class  
```  
  
```csharp  
[StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey="…hex…", Name="App1", Version="0.0.0.0")]  
public class Class1  
{  
  
}
```  
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="53359-124">クラスとメンバーを信頼関係のないコードが使用できないようにする</span><span class="sxs-lookup"><span data-stu-id="53359-124">Excluding Classes and Members from Use by Untrusted Code</span></span>  

 <span data-ttu-id="53359-125">このセクションで示す宣言を使用すると、特定のクラスとメソッド、およびプロパティとイベントが部分的な信頼のコードによって使用されるのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="53359-125">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="53359-126">これらの宣言をクラスに適用することで、すべてのメソッド、プロパティ、およびイベントに保護を適用できます。</span><span class="sxs-lookup"><span data-stu-id="53359-126">By applying these declarations to a class, you apply the protection to all its methods, properties, and events.</span></span> <span data-ttu-id="53359-127">ただし、フィールドアクセスは、宣言セキュリティの影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="53359-127">However, field access is not affected by declarative security.</span></span> <span data-ttu-id="53359-128">また、リンク確認要求は直前の呼び出し元に対して保護できるようにするだけで、攻撃を受ける可能性が残っています。</span><span class="sxs-lookup"><span data-stu-id="53359-128">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53359-129">新しい透過性モデルは .NET Framework 4 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="53359-129">A new transparency model has been introduced in the .NET Framework 4.</span></span> <span data-ttu-id="53359-130">[透過的セキュリティコード、レベル 2](security-transparent-code-level-2.md)モデルは、属性を使用してセキュリティで保護されたコードを識別し <xref:System.Security.SecurityCriticalAttribute> ます。</span><span class="sxs-lookup"><span data-stu-id="53359-130">The [Security-Transparent Code, Level 2](security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="53359-131">セキュリティ クリティカル コードでは、呼び出し元と継承先の両方が完全に信頼されていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="53359-131">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="53359-132">.NET Framework の以前のバージョンのコード アクセス セキュリティ規則で実行されているアセンブリは、レベル 2 のアセンブリを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="53359-132">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="53359-133">この場合、セキュリティ クリティカル属性は、完全な信頼のためのリンク確認要求として扱われます。</span><span class="sxs-lookup"><span data-stu-id="53359-133">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="53359-134">厳密な名前が付けられたアセンブリでは、すべてのパブリックにアクセスできるメソッド、プロパティ、およびイベントに [LinkDemand](link-demands.md) が適用され、完全に信頼された呼び出し元に対して使用が制限されます。</span><span class="sxs-lookup"><span data-stu-id="53359-134">In strong-named assemblies, a [LinkDemand](link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="53359-135">この機能を無効にするには、<xref:System.Security.AllowPartiallyTrustedCallersAttribute> 属性を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53359-135">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="53359-136">このため、信頼関係のない呼び出し元を除外するクラスを明示的に指定することは、署名のないアセンブリまたはこの属性を持つアセンブリだけに必要です。これらの宣言を使用して、信頼関係のない呼び出し元からの利用を想定していない型のサブセットをマークできます。</span><span class="sxs-lookup"><span data-stu-id="53359-136">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="53359-137">クラスおよびメンバーを信頼関係のないコードによって使用されるのを防ぐ方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="53359-137">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="53359-138">パブリックの非シール クラスの場合:</span><span class="sxs-lookup"><span data-stu-id="53359-138">For public nonsealed classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
Public Class CanDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public class CanDeriveFromMe  
{  
}  
```  
  
 <span data-ttu-id="53359-139">パブリックのシール クラスの場合:</span><span class="sxs-lookup"><span data-stu-id="53359-139">For public sealed classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
NotInheritable Public Class CannotDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public sealed class CannotDeriveFromMe  
{  
}  
```  
  
 <span data-ttu-id="53359-140">パブリックの抽象クラスの場合:</span><span class="sxs-lookup"><span data-stu-id="53359-140">For public abstract classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _  
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
MustInherit Public Class CannotCreateInstanceOfMe_CanCastToMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public abstract class CannotCreateInstanceOfMe_CanCastToMe {}  
```  
  
 <span data-ttu-id="53359-141">パブリックの仮想関数の場合:</span><span class="sxs-lookup"><span data-stu-id="53359-141">For public virtual functions:</span></span>  
  
```vb  
Class Base1
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overridable Sub CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Base1  
```  
  
```csharp  
class Base1
{  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
    public virtual void CanOverrideOrCallMe() {}  
}  
```  
  
 <span data-ttu-id="53359-142">パブリックの抽象関数の場合:</span><span class="sxs-lookup"><span data-stu-id="53359-142">For public abstract functions:</span></span>  
  
```vb  
MustInherit Class Base2  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Sub MustOverrideMe()  
    End Sub  
End Class 'Base2  
```  
  
```csharp  
abstract class Base2 {  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
public abstract void MustOverrideMe();  
}  
```  
  
 <span data-ttu-id="53359-143">基本クラスが完全な信頼を確認要求しない、パブリック オーバーライド関数の場合:</span><span class="sxs-lookup"><span data-stu-id="53359-143">For public override functions where the base class does not demand full trust:</span></span>  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name="FullTrust")]
    public override void CanOverrideOrCallMe()
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 <span data-ttu-id="53359-144">基本クラスが完全な信頼を確認要求する、パブリック オーバーライド関数の場合:</span><span class="sxs-lookup"><span data-stu-id="53359-144">For public override functions where the base class demands full trust:</span></span>  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]
    public override void CanOverrideOrCallMe()
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 <span data-ttu-id="53359-145">パブリック インターフェイスの場合:</span><span class="sxs-lookup"><span data-stu-id="53359-145">For public interfaces:</span></span>  
  
```vb  
Public Interface ICanCastToMe  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
    Sub CanImplementMe()  
End Interface 'ICanCastToMe  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
Class Implemented  
    Implements ICanCastToMe  
    Public Sub CanImplementMe()  
    End Sub 'CanImplementMe  
```  
  
```csharp  
public interface ICanCastToMe
{  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
void CanImplementMe();  
}  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
class Implemented : ICanCastToMe  
{  
    public void CanImplementMe()  
    {  
    }  
}  
```  
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="53359-146">Virtual Internal Overrides または Overloads Overridable Friend</span><span class="sxs-lookup"><span data-stu-id="53359-146">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53359-147">このセクションでは、メソッドを `virtual` および `internal` ( `Overloads` `Overridable` `Friend` Visual Basic) の両方として宣言するときのセキュリティの問題について警告します。</span><span class="sxs-lookup"><span data-stu-id="53359-147">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads` `Overridable` `Friend` in Visual Basic).</span></span> <span data-ttu-id="53359-148">この警告は .NET Framework バージョン1.0 および1.1 にのみ適用されます。これは、それ以降のバージョンには適用されません。</span><span class="sxs-lookup"><span data-stu-id="53359-148">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="53359-149">.NET Framework バージョン1.0 および1.1 では、他のアセンブリでコードを使用できないことを確認するときに、型システムのアクセシビリティの微妙な違いに注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53359-149">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="53359-150">**Virtual** および **internal** として宣言されているメソッド (Visual Basic 内のオーバーロードのオーバーライド可能な **Friend** ) は、親クラスの vtable エントリをオーバーライドできます。また、内部のため、同じアセンブリ内からのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="53359-150">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="53359-151">ただし、オーバーライドのアクセシビリティは **virtual** キーワードによって決定され、そのコードがクラス自体にアクセスできる限り、別のアセンブリからオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="53359-151">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="53359-152">オーバーライドの可能性が問題を示している場合は、宣言セキュリティを使用して修正します。または、厳密には必要でない場合は、 **仮想** キーワードを削除します。</span><span class="sxs-lookup"><span data-stu-id="53359-152">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="53359-153">言語コンパイラによってコンパイルエラーによってこれらのオーバーライドが回避される場合でも、他のコンパイラで記述されたコードがオーバーライドされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="53359-153">Even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53359-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="53359-154">See also</span></span>

- [<span data-ttu-id="53359-155">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="53359-155">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
