---
title: カスタムのシリアル化
description: カスタムのシリアル化とは、型のシリアル化と逆シリアル化を制御することです。 シリアル化を制御することで、シリアル化の互換性を確保できます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binary serialization, custom serialization
- custom serialization
- binary serialization, controlling
- OptionalFieldAttribute class, custom serialization
- ISerializable interface, custom serialization
- OnDeserializingAttribute class, custom serialization
- OnSerializedAttribute class, custom serialization
- serialization, custom serialization
- serialization, controlling
- OnDeserializedAttribute class, custom serialization
- OnSerializingAttribute class, custom serialization
ms.assetid: 12ed422d-5280-49b8-9b71-a2ed129c0384
ms.openlocfilehash: 4ca78c71f464a914c07583825d4a7027ebb11bf6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679040"
---
# <a name="custom-serialization"></a><span data-ttu-id="3bc89-104">カスタムのシリアル化</span><span class="sxs-lookup"><span data-stu-id="3bc89-104">Custom serialization</span></span>

<span data-ttu-id="3bc89-105">カスタムのシリアル化は、型のシリアル化と逆シリアル化を制御するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="3bc89-105">Custom serialization is the process of controlling the serialization and deserialization of a type.</span></span> <span data-ttu-id="3bc89-106">シリアル化を制御することで、シリアル化の互換性を保証できます。つまり、型のコア機能を損なうことなく、1 つの型の複数のバージョン間でシリアル化および逆シリアル化を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3bc89-106">By controlling serialization, it's possible to ensure serialization compatibility, which is the ability to serialize and deserialize between versions of a type without breaking the core functionality of the type.</span></span> <span data-ttu-id="3bc89-107">たとえば、最初のバージョンの型では、フィールドが 2 つだけあるとします。</span><span class="sxs-lookup"><span data-stu-id="3bc89-107">For example, in the first version of a type, there may be only two fields.</span></span> <span data-ttu-id="3bc89-108">新しいバージョンでは、これにいくつかのフィールドが追加されています。</span><span class="sxs-lookup"><span data-stu-id="3bc89-108">In the next version of a type, several more fields are added.</span></span> <span data-ttu-id="3bc89-109">この場合、2 番目のバージョンのアプリケーションでは、両方の型をシリアル化および逆シリアル化できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bc89-109">Yet the second version of an application must be able to serialize and deserialize both types.</span></span> <span data-ttu-id="3bc89-110">以下のセクションでは、シリアル化の制御方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3bc89-110">The following sections describe how to control serialization.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
> <span data-ttu-id="3bc89-111">.NET Framework 4.0 より前のバージョンでは、部分的に信頼されたアセンブリでのカスタム ユーザー データのシリアル化は `GetObjectData` を使用して実行されていました。</span><span class="sxs-lookup"><span data-stu-id="3bc89-111">In versions previous to .NET Framework 4.0, serialization of custom user data in a partially trusted assembly was accomplished using `GetObjectData`.</span></span> <span data-ttu-id="3bc89-112">バージョン 4.0 以降では、そのメソッドは、部分的に信頼されたアセンブリで実行できないようにする <xref:System.Security.SecurityCriticalAttribute> 属性でマークされています。</span><span class="sxs-lookup"><span data-stu-id="3bc89-112">Starting with version 4.0, that method is marked with the <xref:System.Security.SecurityCriticalAttribute> attribute, which prevents execution in partially trusted assemblies.</span></span> <span data-ttu-id="3bc89-113">この状況に対処するには、<xref:System.Runtime.Serialization.ISafeSerializationData> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="3bc89-113">To work around this condition, implement the <xref:System.Runtime.Serialization.ISafeSerializationData> interface.</span></span>  
  
## <a name="running-custom-methods-during-and-after-serialization"></a><span data-ttu-id="3bc89-114">シリアル化時およびシリアル化後のカスタム メソッドの実行</span><span class="sxs-lookup"><span data-stu-id="3bc89-114">Running custom methods during and after serialization</span></span>

<span data-ttu-id="3bc89-115">シリアル化時およびシリアル化後にカスタム メソッドを実行するための推奨される方法は、シリアル化時およびシリアル化後にデータを修正するために使用されるメソッドに、以下の属性を適用することです。</span><span class="sxs-lookup"><span data-stu-id="3bc89-115">The recommended way to run custom methods during and after serialization is to apply the following attributes to methods that are used to correct data during and after serialization:</span></span>  
  
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 <span data-ttu-id="3bc89-116">これらの属性を適用すると、シリアル化プロセスと逆シリアル化プロセスの 4 つのフェーズのうち、いずれか、またはすべてに型を参加させることができます。</span><span class="sxs-lookup"><span data-stu-id="3bc89-116">These attributes allow the type to participate in any one of, or all four of the phases, of the serialization and deserialization processes.</span></span> <span data-ttu-id="3bc89-117">これらの属性は、各フェーズで呼び出す必要がある型のメソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="3bc89-117">The attributes specify the methods of the type that should be invoked during each phase.</span></span> <span data-ttu-id="3bc89-118">これらのメソッドはシリアル化ストリームにはアクセスしませんが、これらを使用すると、シリアル化の前後、または逆シリアル化の前後にオブジェクトを変更できます。</span><span class="sxs-lookup"><span data-stu-id="3bc89-118">The methods do not access the serialization stream but instead allow you to alter the object before and after serialization, or before and after deserialization.</span></span> <span data-ttu-id="3bc89-119">これらの属性は型の継承階層の全レベルで適用でき、各メソッドは、基本クラスから最派生クラスまで、階層内で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3bc89-119">The attributes can be applied at all levels of the type inheritance hierarchy, and each method is called in the hierarchy from the base to the most derived.</span></span> <span data-ttu-id="3bc89-120">このしくみでは、最派生実装でシリアル化および逆シリアル化が行われるため、<xref:System.Runtime.Serialization.ISerializable> インターフェイスの実装の複雑性やその実装によって発生する問題が回避されます。</span><span class="sxs-lookup"><span data-stu-id="3bc89-120">This mechanism avoids the complexity and any resulting issues of implementing the <xref:System.Runtime.Serialization.ISerializable> interface by giving the responsibility for serialization and deserialization to the most derived implementation.</span></span> <span data-ttu-id="3bc89-121">また、フォーマッタは、フィールド値の設定およびシリアル化ストリームからの取得を無視できます。</span><span class="sxs-lookup"><span data-stu-id="3bc89-121">Additionally, this mechanism allows the formatters to ignore the population of fields and retrieval from the serialization stream.</span></span> <span data-ttu-id="3bc89-122">シリアル化および逆シリアル化の制御の詳細と例については、上記の各リンクをクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="3bc89-122">For details and examples of controlling serialization and deserialization, click any of the previous links.</span></span>  
  
 <span data-ttu-id="3bc89-123">また、既存のシリアル化可能な型に新しいフィールドを追加する場合は、このフィールドに <xref:System.Runtime.Serialization.OptionalFieldAttribute> 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="3bc89-123">In addition, when adding a new field to an existing serializable type, apply the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to the field.</span></span> <span data-ttu-id="3bc89-124">新しいフィールドが含まれていないストリームを処理する際に、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> および <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> はこのフィールドの不足を無視します。</span><span class="sxs-lookup"><span data-stu-id="3bc89-124">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignores the absence of the field when a stream that is missing the new field is processed.</span></span>  
  
## <a name="implementing-the-iserializable-interface"></a><span data-ttu-id="3bc89-125">ISerializable インターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="3bc89-125">Implementing the ISerializable interface</span></span>  

 <span data-ttu-id="3bc89-126">シリアル化を制御するもう 1 つの方法は、オブジェクトに <xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装することです。</span><span class="sxs-lookup"><span data-stu-id="3bc89-126">The other way to control serialization is achieved by implementing the <xref:System.Runtime.Serialization.ISerializable> interface on an object.</span></span> <span data-ttu-id="3bc89-127">ただし、シリアル化の制御では、前のセクションで説明した方法がこの方法よりも優先されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3bc89-127">Note, however, that the method in the previous section supersedes this method to control serialization.</span></span>  
  
 <span data-ttu-id="3bc89-128">また、[Serializable](xref:System.SerializableAttribute) 属性を使用してマークされ、クラス レベルまたはクラスのコンストラクターで宣言セキュリティまたは強制セキュリティが設定されたクラスでは、既定のシリアル化を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="3bc89-128">In addition, you should not use default serialization on a class that is marked with the [Serializable](xref:System.SerializableAttribute) attribute and has declarative or imperative security at the class level or on its constructors.</span></span> <span data-ttu-id="3bc89-129">代わりに、このようなクラスでは、常に <xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bc89-129">Instead, these classes should always implement the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
 <span data-ttu-id="3bc89-130"><xref:System.Runtime.Serialization.ISerializable> を実装すると、`GetObjectData` メソッドと、このオブジェクトが逆シリアル化されるときに使用される専用のコンストラクターも実装されます。</span><span class="sxs-lookup"><span data-stu-id="3bc89-130">Implementing <xref:System.Runtime.Serialization.ISerializable> involves implementing the `GetObjectData` method and a special constructor that is used when the object is deserialized.</span></span> <span data-ttu-id="3bc89-131">前のセクションで使用した <xref:System.Runtime.Serialization.ISerializable> クラスに `MyObject` を実装する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="3bc89-131">The following sample code shows how to implement <xref:System.Runtime.Serialization.ISerializable> on the `MyObject` class from a previous section.</span></span>  
  
```csharp
[Serializable]
public class MyObject : ISerializable
{
    public int n1;
    public int n2;
    public String str;

    public MyObject()
    {
    }

    protected MyObject(SerializationInfo info, StreamingContext context)
    {
      n1 = info.GetInt32("i");
      n2 = info.GetInt32("j");
      str = info.GetString("k");
    }

    [SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter = true)]
    public virtual void GetObjectData(SerializationInfo info, StreamingContext context)
    {
        info.AddValue("i", n1);
        info.AddValue("j", n2);
        info.AddValue("k", str);
    }
}
```

```vb
<Serializable()>  _
Public Class MyObject
    Implements ISerializable
    Public n1 As Integer
    Public n2 As Integer
    Public str As String

    Public Sub New()
    End Sub

    Protected Sub New(ByVal info As SerializationInfo, ByVal context As StreamingContext)
        n1 = info.GetInt32("i")
        n2 = info.GetInt32("j")
        str = info.GetString("k")
    End Sub 'New

    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)> _
    Public Overridable Sub GetObjectData(ByVal info As SerializationInfo, ByVal context As StreamingContext)
        info.AddValue("i", n1)
        info.AddValue("j", n2)
        info.AddValue("k", str)
    End Sub
End Class
```  
  
 <span data-ttu-id="3bc89-132">シリアル化時に **GetObjectData** を呼び出す場合は、メソッド呼び出しで提供される <xref:System.Runtime.Serialization.SerializationInfo> を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bc89-132">When **GetObjectData** is called during serialization, you are responsible for populating the <xref:System.Runtime.Serialization.SerializationInfo> provided with the method call.</span></span> <span data-ttu-id="3bc89-133">シリアル化の対象とする変数は、名前と値のペアとして追加します。</span><span class="sxs-lookup"><span data-stu-id="3bc89-133">Add the variables to be serialized as name and value pairs.</span></span> <span data-ttu-id="3bc89-134">名前には、任意のテキストを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3bc89-134">Any text can be used as the name.</span></span> <span data-ttu-id="3bc89-135">逆シリアル化時にオブジェクトを復元するのに十分なデータがシリアル化される場合は、<xref:System.Runtime.Serialization.SerializationInfo> に追加するメンバー変数を自由に決定できます。</span><span class="sxs-lookup"><span data-stu-id="3bc89-135">You have the freedom to decide which member variables are added to the <xref:System.Runtime.Serialization.SerializationInfo>, provided that sufficient data is serialized to restore the object during deserialization.</span></span> <span data-ttu-id="3bc89-136">基本オブジェクトが <xref:System.Runtime.Serialization.ISerializable> を実装している場合、派生クラスはその基本オブジェクトの **GetObjectData** メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bc89-136">Derived classes should call the **GetObjectData** method on the base object if the latter implements <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
 <span data-ttu-id="3bc89-137">シリアル化によって、他の方法ではアクセスできないオブジェクト インスタンス データを他のコードから参照または変更できるようになります。</span><span class="sxs-lookup"><span data-stu-id="3bc89-137">Note that serialization can allow other code to see or modify object instance data that is otherwise inaccessible.</span></span> <span data-ttu-id="3bc89-138">したがって、シリアル化を実行するコードには、<xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> フラグが指定された [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) が必要です。</span><span class="sxs-lookup"><span data-stu-id="3bc89-138">Therefore, code that performs serialization requires the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="3bc89-139">既定のポリシーでは、インターネットからダウンロードしたコードまたはイントラネット コードにはこのアクセス許可は与えられず、ローカル コンピューター上のコードにだけ付与されます。</span><span class="sxs-lookup"><span data-stu-id="3bc89-139">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span> <span data-ttu-id="3bc89-140">**GetObjectData** メソッドは、<xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> フラグが指定された [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) を要求するか、特にプライベート データの保護に役立つ他のアクセス許可を要求することによって、明示的に保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bc89-140">The **GetObjectData** method must be explicitly protected either by demanding the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified or by demanding other permissions that specifically help protect private data.</span></span>  
  
 <span data-ttu-id="3bc89-141">プライベート フィールドに機密情報が格納されている場合は、**GetObjectData** で適切なアクセス許可を要求してデータを保護してください。</span><span class="sxs-lookup"><span data-stu-id="3bc89-141">If a private field stores sensitive information, you should demand the appropriate permissions on **GetObjectData** to protect the data.</span></span> <span data-ttu-id="3bc89-142">**SerializationFormatter** フラグが指定された [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) を付与されているコードは、プライベート フィールドに格納されているデータを参照および変更できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3bc89-142">Remember that code that has been granted [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the **SerializationFormatter** flag specified can view and modify the data stored in private fields.</span></span> <span data-ttu-id="3bc89-143">この [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) が付与されている悪意のある呼び出し元によって、隠しディレクトリの位置や付与されたアクセス許可などのデータが参照され、コンピューター上のセキュリティの脆弱性が悪用される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3bc89-143">A malicious caller granted this [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) can view data such as hidden directory locations or granted permissions and use the data to exploit a security vulnerability on the computer.</span></span> <span data-ttu-id="3bc89-144">指定できるセキュリティ アクセス許可フラグの完全な一覧については、「[SecurityPermissionFlag 列挙体](xref:System.Security.Permissions.SecurityPermissionFlag)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bc89-144">For a complete list of the security permission flags you can specify, see the [SecurityPermissionFlag Enumeration](xref:System.Security.Permissions.SecurityPermissionFlag).</span></span>  
  
 <span data-ttu-id="3bc89-145"><xref:System.Runtime.Serialization.ISerializable> をクラスに追加する場合は、**GetObjectData** と専用のコンストラクターの両方を実装する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3bc89-145">It's important to stress that when <xref:System.Runtime.Serialization.ISerializable> is added to a class you must implement both **GetObjectData** and the special constructor.</span></span> <span data-ttu-id="3bc89-146">**GetObjectData** がない場合、コンパイラから警告が出力されます。</span><span class="sxs-lookup"><span data-stu-id="3bc89-146">The compiler warns you if **GetObjectData** is missing.</span></span> <span data-ttu-id="3bc89-147">ただし、コンストラクターの実装を強制することはできないため、コンストラクターが指定されていなくても警告は表示されず、コンストラクターがないクラスの逆シリアル化が試行された時点で例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="3bc89-147">However, because it is impossible to enforce the implementation of a constructor, no warning is provided if the constructor is absent, and an exception is thrown when an attempt is made to deserialize a class without the constructor.</span></span>  
  
 <span data-ttu-id="3bc89-148">セキュリティやバージョン管理に関して発生する可能性がある問題を回避するために、現在のデザインは <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> メソッドよりも優先されています。</span><span class="sxs-lookup"><span data-stu-id="3bc89-148">The current design was favored above a <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> method to get around potential security and versioning problems.</span></span> <span data-ttu-id="3bc89-149">たとえば、`SetObjectData` メソッドは、インターフェイスの一部として定義された場合にはパブリックである必要があるため、ユーザーは **SetObjectData** メソッドが複数回呼び出されることを防ぐためにコードを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bc89-149">For example, a `SetObjectData` method must be public if it is defined as part of an interface; thus users must write code to defend against having the **SetObjectData** method called multiple times.</span></span> <span data-ttu-id="3bc89-150">そうしないと、操作を実行しているオブジェクトで **SetObjectData** メソッドを呼び出す悪意のあるアプリケーションによって、さまざまな問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3bc89-150">Otherwise, a malicious application that calls the **SetObjectData** method on an object in the process of executing an operation can cause potential problems.</span></span>  
  
 <span data-ttu-id="3bc89-151">逆シリアル化時に、<xref:System.Runtime.Serialization.SerializationInfo> は、これをクラスに渡すために提供されているコンストラクターを使用してクラスに渡されます。</span><span class="sxs-lookup"><span data-stu-id="3bc89-151">During deserialization, <xref:System.Runtime.Serialization.SerializationInfo> is passed to the class using the constructor provided for this purpose.</span></span> <span data-ttu-id="3bc89-152">オブジェクトが逆シリアル化されるときには、コンストラクターに対して設定された参照可能範囲の制限は無視されるため、パブリック、プロテクト、内部、またはプライベートとしてクラスをマークできます。</span><span class="sxs-lookup"><span data-stu-id="3bc89-152">Any visibility constraints placed on the constructor are ignored when the object is deserialized; so you can mark the class as public, protected, internal, or private.</span></span> <span data-ttu-id="3bc89-153">ただし、クラスがシールされている場合を除いて、コンストラクターをプロテクトにすることがベスト プラクティスです。クラスがシールされている場合は、コンストラクターをプライベートとマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bc89-153">However, it is a best practice to make the constructor protected unless the class is sealed, in which case the constructor should be marked private.</span></span> <span data-ttu-id="3bc89-154">コンストラクターは入力の検証も実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bc89-154">The constructor should also perform thorough input validation.</span></span> <span data-ttu-id="3bc89-155">悪意のあるコードによる不適切な使用を回避するために、コンストラクターは、他のコンストラクターを使用してクラスのインスタンスを取得する場合と同様のセキュリティ チェックおよびアクセス許可を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bc89-155">To avoid misuse by malicious code, the constructor should enforce the same security checks and permissions required to obtain an instance of the class using any other constructor.</span></span> <span data-ttu-id="3bc89-156">この推奨事項に従わないと、パブリック コンストラクターを使用する標準インスタンスの構築時に適用されるはずのセキュリティが適用されず、悪意のあるコードが、オブジェクトを事前にシリアル化し、<xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> フラグが指定された [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) で制御を取得して、クライアント コンピューター上でオブジェクトを逆シリアル化することが可能になります。</span><span class="sxs-lookup"><span data-stu-id="3bc89-156">If you do not follow this recommendation, malicious code can preserialize an object, obtain control with the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified and deserialize the object on a client computer bypassing any security that would have been applied during standard instance construction using a public constructor.</span></span>  
  
 <span data-ttu-id="3bc89-157">オブジェクトの状態を復元するには、シリアル化時に使用した名前を使って、<xref:System.Runtime.Serialization.SerializationInfo> から変数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="3bc89-157">To restore the state of the object, simply retrieve the values of the variables from <xref:System.Runtime.Serialization.SerializationInfo> using the names used during serialization.</span></span> <span data-ttu-id="3bc89-158">基本クラスに <xref:System.Runtime.Serialization.ISerializable> が実装されている場合は、基本オブジェクトがその変数を復元できるようにするために、基本コンストラクターを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bc89-158">If the base class implements <xref:System.Runtime.Serialization.ISerializable>, the base constructor should be called to allow the base object to restore its variables.</span></span>  
  
 <span data-ttu-id="3bc89-159"><xref:System.Runtime.Serialization.ISerializable> を実装しているクラスから新しいクラスを派生させるときに、派生クラスにシリアル化する必要がある変数がある場合は、派生クラスでコンストラクターと **GetObjectData** メソッドの両方を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bc89-159">When you derive a new class from one that implements <xref:System.Runtime.Serialization.ISerializable>, the derived class must implement both the constructor as well as the **GetObjectData** method if it has variables that need to be serialized.</span></span> <span data-ttu-id="3bc89-160">上記の `MyObject` クラスを使用してこれを行う方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="3bc89-160">The following code example shows how this is done using the `MyObject` class shown previously.</span></span>  
  
```csharp
[Serializable]
public class ObjectTwo : MyObject
{
    public int num;

    public ObjectTwo()
      : base()
    {
    }

    protected ObjectTwo(SerializationInfo si, StreamingContext context)
      : base(si, context)
    {
        num = si.GetInt32("num");
    }

    [SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter = true)]
    public override void GetObjectData(SerializationInfo si, StreamingContext context)
    {
        base.GetObjectData(si,context);
        si.AddValue("num", num);
    }
}
```

```vb
<Serializable()>  _
Public Class ObjectTwo
    Inherits MyObject
    Public num As Integer

    Public Sub New()

    End Sub

    Protected Sub New(ByVal si As SerializationInfo, _
    ByVal context As StreamingContext)
        MyBase.New(si, context)
        num = si.GetInt32("num")
    End Sub

    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)> _
    Public Overrides Sub GetObjectData(ByVal si As SerializationInfo, ByVal context As StreamingContext)
        MyBase.GetObjectData(si, context)
        si.AddValue("num", num)
    End Sub
End Class
```  
  
 <span data-ttu-id="3bc89-161">必ず、逆シリアル化コンストラクターで基本クラスを呼び出すようにしてください。</span><span class="sxs-lookup"><span data-stu-id="3bc89-161">Don't forget to call the base class in the deserialization constructor.</span></span> <span data-ttu-id="3bc89-162">そうしないと、基本クラスのコンストラクターが呼び出されず、逆シリアル化後にオブジェクトが完全には構築されません。</span><span class="sxs-lookup"><span data-stu-id="3bc89-162">If this isn't done, the constructor on the base class is never called, and the object is not fully constructed after deserialization.</span></span>  
  
 <span data-ttu-id="3bc89-163">オブジェクトは内側から外側に向かって再構築されるため、逆シリアル化時にメソッドを呼び出すと、望ましくない副作用を引き起こす可能性があります。これは、呼び出されるメソッドが、呼び出しの時点では逆シリアル化されていないオブジェクト参照を参照することがあるためです。</span><span class="sxs-lookup"><span data-stu-id="3bc89-163">Objects are reconstructed from the inside out; and calling methods during deserialization can have undesirable side effects, because the methods called might refer to object references that have not been deserialized by the time the call is made.</span></span> <span data-ttu-id="3bc89-164">逆シリアル化対象のクラスで <xref:System.Runtime.Serialization.IDeserializationCallback> を実装する場合、オブジェクト グラフ全体が逆シリアル化された時点で <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%2A> メソッドが自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3bc89-164">If the class being deserialized implements the <xref:System.Runtime.Serialization.IDeserializationCallback>, the <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%2A> method is automatically called when the entire object graph has been deserialized.</span></span> <span data-ttu-id="3bc89-165">この時点で、参照されているすべての子オブジェクトが完全に復元されます。</span><span class="sxs-lookup"><span data-stu-id="3bc89-165">At this point, all the child objects referenced have been fully restored.</span></span> <span data-ttu-id="3bc89-166">ハッシュ テーブルは、イベント リスナーを使用せずに逆シリアル化することが困難なクラスの典型的な例です。</span><span class="sxs-lookup"><span data-stu-id="3bc89-166">A hash table is a typical example of a class that is difficult to deserialize without using the event listener.</span></span> <span data-ttu-id="3bc89-167">逆シリアル化時にキーと値のペアを取得することは簡単ですが、これらのオブジェクトをハッシュ テーブルに戻すと、このハッシュ テーブルから派生したクラスが逆シリアル化されているかどうかわからないため、問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3bc89-167">It is easy to retrieve the key and value pairs during deserialization, but adding these objects back to the hash table can cause problems, because there is no guarantee that classes that derived from the hash table have been deserialized.</span></span> <span data-ttu-id="3bc89-168">したがって、この段階でハッシュ テーブルのメソッドを呼び出すことはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="3bc89-168">Calling methods on a hash table at this stage is therefore not advisable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bc89-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="3bc89-169">See also</span></span>

- [<span data-ttu-id="3bc89-170">バイナリ シリアル化</span><span class="sxs-lookup"><span data-stu-id="3bc89-170">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="3bc89-171">XML シリアル化および SOAP シリアル化</span><span class="sxs-lookup"><span data-stu-id="3bc89-171">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="3bc89-172">セキュリティとシリアル化</span><span class="sxs-lookup"><span data-stu-id="3bc89-172">Security and Serialization</span></span>](../../framework/misc/security-and-serialization.md)
