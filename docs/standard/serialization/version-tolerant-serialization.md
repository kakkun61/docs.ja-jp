---
title: バージョン トレラントなシリアル化
description: シリアル化可能な型を簡単に変更できるようにする機能のセットであるバージョン トレラントなシリアル化について説明します。
ms.date: 08/08/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- version tolerant serialization
- serialization, custom serialization
- serialization, version tolerant
- serialization, controlling
- versions and serialization
- BinaryFormatter class, samples
- serialization, attributes
ms.assetid: bea0ffe3-2708-4a16-ac7d-e586ed6b8e8d
ms.openlocfilehash: 26612c5b0591efa61fcd476733aee2b219d67c62
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96438161"
---
# <a name="version-tolerant-serialization"></a><span data-ttu-id="53720-103">バージョン トレラントなシリアル化</span><span class="sxs-lookup"><span data-stu-id="53720-103">Version tolerant serialization</span></span>

<span data-ttu-id="53720-104">.NET Framework の最新バージョンでは、アプリケーションのあるバージョンから次のバージョンに移行しても再利用できる、シリアル化可能な型の作成に問題がありました。</span><span class="sxs-lookup"><span data-stu-id="53720-104">In the earliest versions of .NET Framework, creating serializable types that would be reusable from one version of an application to the next was problematic.</span></span> <span data-ttu-id="53720-105">フィールドを追加して型を変更すると、次のような問題が発生していました。</span><span class="sxs-lookup"><span data-stu-id="53720-105">If a type was modified by adding extra fields, the following problems would occur:</span></span>

- <span data-ttu-id="53720-106">以前のバージョンのアプリケーションは、古い型の新しいバージョンを逆シリアル化するように要求すると例外をスローする。</span><span class="sxs-lookup"><span data-stu-id="53720-106">Older versions of an application would throw exceptions when asked to deserialize new versions of the old type.</span></span>
- <span data-ttu-id="53720-107">新しいバージョンのアプリケーションは、データが欠落している以前のバージョンの型を逆シリアル化すると例外をスローする。</span><span class="sxs-lookup"><span data-stu-id="53720-107">Newer versions of an application would throw exceptions when deserializing older versions of a type with missing data.</span></span>

<span data-ttu-id="53720-108">バージョン トレラントなシリアル化 (VTS: Version Tolerant Serialization) は、シリアル化可能な型を、長期にわたって簡単に変更できるようにする機能のセットです。</span><span class="sxs-lookup"><span data-stu-id="53720-108">Version Tolerant Serialization (VTS) is a set of features that makes it easier, over time, to modify serializable types.</span></span> <span data-ttu-id="53720-109">具体的には、VTS 機能が、ジェネリック型を含め、<xref:System.SerializableAttribute> 属性が適用されているクラスに対して有効です。</span><span class="sxs-lookup"><span data-stu-id="53720-109">Specifically, the VTS features are enabled for classes to which the <xref:System.SerializableAttribute> attribute has been applied, including generic types.</span></span> <span data-ttu-id="53720-110">VTS を使用すると、他のバージョンの型との互換性を失うことなく、これらのクラスに新しいフィールドを追加できます。</span><span class="sxs-lookup"><span data-stu-id="53720-110">VTS makes it possible to add new fields to those classes without breaking compatibility with other versions of the type.</span></span>

<span data-ttu-id="53720-111">VTS 機能は、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> を使用する場合に有効になります。</span><span class="sxs-lookup"><span data-stu-id="53720-111">The VTS features are enabled when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="53720-112">また、<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> を使用する場合は、外部データの複数バージョン対応機能を除くすべての機能が有効になります。</span><span class="sxs-lookup"><span data-stu-id="53720-112">Additionally, all features except extraneous data tolerance are also enabled when using the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="53720-113">シリアル化でこれらのクラスを使用する方法の詳細については、「[バイナリ シリアル化](binary-serialization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53720-113">For more information about using these classes for serialization, see [Binary Serialization](binary-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a><span data-ttu-id="53720-114">機能の一覧</span><span class="sxs-lookup"><span data-stu-id="53720-114">Feature list</span></span>

<span data-ttu-id="53720-115">この機能セットの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="53720-115">The set of features includes the following:</span></span>

- <span data-ttu-id="53720-116">外部データまたは予期しないデータの複数バージョン対応。</span><span class="sxs-lookup"><span data-stu-id="53720-116">Tolerance of extraneous or unexpected data.</span></span> <span data-ttu-id="53720-117">これにより、型の新しいバージョンから以前のバージョンにデータを送信できます。</span><span class="sxs-lookup"><span data-stu-id="53720-117">This enables newer versions of the type to send data to older versions.</span></span>
- <span data-ttu-id="53720-118">欠落しているオプション データの複数バージョン対応。</span><span class="sxs-lookup"><span data-stu-id="53720-118">Tolerance of missing optional data.</span></span> <span data-ttu-id="53720-119">これにより、以前のバージョンから新しいバージョンにデータを送信できます。</span><span class="sxs-lookup"><span data-stu-id="53720-119">This enables older versions to send data to newer versions.</span></span>
- <span data-ttu-id="53720-120">シリアル化のコールバック。</span><span class="sxs-lookup"><span data-stu-id="53720-120">Serialization callbacks.</span></span> <span data-ttu-id="53720-121">これにより、データが欠落している場合に、既定値の高度な設定ができます。</span><span class="sxs-lookup"><span data-stu-id="53720-121">This enables intelligent default value setting in cases where data is missing.</span></span>

<span data-ttu-id="53720-122">さらに、オプション フィールドが新たに追加されたときに宣言を生成する機能があります。</span><span class="sxs-lookup"><span data-stu-id="53720-122">In addition, there is a feature for declaring when a new optional field has been added.</span></span> <span data-ttu-id="53720-123">これは、<xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> 属性の <xref:System.Runtime.Serialization.OptionalFieldAttribute> プロパティです。</span><span class="sxs-lookup"><span data-stu-id="53720-123">This is the <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> property of the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute.</span></span>

<span data-ttu-id="53720-124">これらの機能については、以下のセクションでさらに詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="53720-124">These features are discussed in greater detail in the following sections.</span></span>

### <a name="tolerance-of-extraneous-or-unexpected-data"></a><span data-ttu-id="53720-125">外部データまたは予期しないデータの複数バージョン対応</span><span class="sxs-lookup"><span data-stu-id="53720-125">Tolerance of extraneous or unexpected data</span></span>

<span data-ttu-id="53720-126">これまで、逆シリアル化中に外部データまたは予期しないデータが検出されると、例外がスローされていました。</span><span class="sxs-lookup"><span data-stu-id="53720-126">In the past, during deserialization, any extraneous or unexpected data caused exceptions to be thrown.</span></span> <span data-ttu-id="53720-127">VTS ではこのような場合、例外がスローされるのではなく、外部データまたは予期しないデータがすべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="53720-127">With VTS, in the same situation, any extraneous or unexpected data is ignored instead of causing exceptions to be thrown.</span></span> <span data-ttu-id="53720-128">これにより、新しいバージョンの型 (フィールドが追加されたバージョン) を使用するアプリケーションが、同じ型の以前のバージョンを必要とするアプリケーションに情報を送ることができます。</span><span class="sxs-lookup"><span data-stu-id="53720-128">This enables applications that use newer versions of a type (that is, a version that includes more fields) to send information to applications that expect older versions of the same type.</span></span>

<span data-ttu-id="53720-129">次の例では、バージョン 2.0 の `CountryField` クラスの `Address` に含まれる追加データは、以前のアプリケーションで新しいバージョンを逆シリアル化する場合、無視されます。</span><span class="sxs-lookup"><span data-stu-id="53720-129">In the following example, the extra data contained in the `CountryField` of version 2.0 of the `Address` class is ignored when an older application deserializes the newer version.</span></span>

```csharp  
// Version 1 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
}  
// Version 2.0 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
    // The older application ignores this data.  
    public string CountryField;  
}  
```  
  
```vb  
' Version 1 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
End Class  
  
' Version 2.0 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
    ' The older application ignores this data.  
    Public CountryField As String  
End Class  
```  

### <a name="tolerance-of-missing-data"></a><span data-ttu-id="53720-130">欠落しているデータの複数バージョン対応</span><span class="sxs-lookup"><span data-stu-id="53720-130">Tolerance of missing data</span></span>

<span data-ttu-id="53720-131"><xref:System.Runtime.Serialization.OptionalFieldAttribute> 属性をフィールドに適用すると、そのフィールドをオプションとしてマークできます。</span><span class="sxs-lookup"><span data-stu-id="53720-131">Fields can be marked as optional by applying the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to them.</span></span> <span data-ttu-id="53720-132">逆シリアル化中に、オプション データの欠落が検出されても、シリアル化エンジンはデータが存在しないことを無視し、例外をスローしません。</span><span class="sxs-lookup"><span data-stu-id="53720-132">During deserialization, if the optional data is missing, the serialization engine ignores the absence and does not throw an exception.</span></span> <span data-ttu-id="53720-133">そのため、以前のバージョンの型を必要とするアプリケーションから、同じ型の新しいバージョンを必要とするアプリケーションにデータを送信できます。</span><span class="sxs-lookup"><span data-stu-id="53720-133">Thus, applications that expect older versions of a type can send data to applications that expect newer versions of the same type.</span></span>

<span data-ttu-id="53720-134">バージョン 2.0 の `Address` クラスで、`CountryField` フィールドをオプションとしてマークする方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="53720-134">The following example shows version 2.0 of the `Address` class with the `CountryField` field marked as optional.</span></span> <span data-ttu-id="53720-135">バージョン 2.0 を必要とする新しいアプリケーションに対して、以前のアプリケーションがバージョン 1 を送信した場合、データが存在しないことは無視されます。</span><span class="sxs-lookup"><span data-stu-id="53720-135">If an older application sends version 1 to a newer application that expects version 2.0, the absence of the data is ignored.</span></span>

```csharp
[Serializable]
public class Address
{
    public string Street;
    public string City;

    [OptionalField]
    public string CountryField;
}
```

```vb
<Serializable> _
Public Class Address
    Public Street As String
    Public City As String

    <OptionalField> _
    Public CountryField As String
End Class
```
  
### <a name="serialization-callbacks"></a><span data-ttu-id="53720-136">シリアル化のコールバック</span><span class="sxs-lookup"><span data-stu-id="53720-136">Serialization callbacks</span></span>

<span data-ttu-id="53720-137">シリアル化のコールバックは、次の 4 つの時点でシリアル化プロセスおよび逆シリアル化プロセスにフックする機構です。</span><span class="sxs-lookup"><span data-stu-id="53720-137">Serialization callbacks are a mechanism that provides hooks into the serialization/deserialization process at four points.</span></span>

|<span data-ttu-id="53720-138">属性</span><span class="sxs-lookup"><span data-stu-id="53720-138">Attribute</span></span>|<span data-ttu-id="53720-139">関連するメソッドが呼び出されるタイミング</span><span class="sxs-lookup"><span data-stu-id="53720-139">When the Associated Method is Called</span></span>|<span data-ttu-id="53720-140">一般的な用途</span><span class="sxs-lookup"><span data-stu-id="53720-140">Typical Use</span></span>|
|---------------|------------------------------------------|-----------------|
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="53720-141">逆シリアル化の前。\*</span><span class="sxs-lookup"><span data-stu-id="53720-141">Before deserialization.\*</span></span>|<span data-ttu-id="53720-142">オプション フィールドの既定値を初期化します。</span><span class="sxs-lookup"><span data-stu-id="53720-142">Initialize default values for optional fields.</span></span>|
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="53720-143">逆シリアル化の後</span><span class="sxs-lookup"><span data-stu-id="53720-143">After deserialization.</span></span>|<span data-ttu-id="53720-144">他のフィールドの内容に基づいて、オプション フィールドの値を修正します。</span><span class="sxs-lookup"><span data-stu-id="53720-144">Fix optional field values based on contents of other fields.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="53720-145">シリアル化の前</span><span class="sxs-lookup"><span data-stu-id="53720-145">Before serialization.</span></span>|<span data-ttu-id="53720-146">シリアル化の準備をします。</span><span class="sxs-lookup"><span data-stu-id="53720-146">Prepare for serialization.</span></span> <span data-ttu-id="53720-147">たとえば、オプションのデータ構造を作成します。</span><span class="sxs-lookup"><span data-stu-id="53720-147">For example, create optional data structures.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="53720-148">シリアル化の後</span><span class="sxs-lookup"><span data-stu-id="53720-148">After serialization.</span></span>|<span data-ttu-id="53720-149">シリアル化イベントのログを記録します。</span><span class="sxs-lookup"><span data-stu-id="53720-149">Log serialization events.</span></span>|

 <span data-ttu-id="53720-150">\* このコールバックは、逆シリアル化コンストラクターの前に呼び出されます (存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="53720-150">\* This callback is invoked before the deserialization constructor, if one is present.</span></span>

#### <a name="using-callbacks"></a><span data-ttu-id="53720-151">コールバックの使用</span><span class="sxs-lookup"><span data-stu-id="53720-151">Using callbacks</span></span>

<span data-ttu-id="53720-152">コールバックを使用するには、<xref:System.Runtime.Serialization.StreamingContext> パラメーターを受け取るメソッドに、適切な属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="53720-152">To use callbacks, apply the appropriate attribute to a method that accepts a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span> <span data-ttu-id="53720-153">各属性でマークできるのは、クラスごとに 1 つのメソッドだけです。</span><span class="sxs-lookup"><span data-stu-id="53720-153">Only one method per class can be marked with each of these attributes.</span></span> <span data-ttu-id="53720-154">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="53720-154">For example:</span></span>

```csharp
[OnDeserializing]
private void SetCountryRegionDefault(StreamingContext sc)
{
    CountryField = "Japan";
}
```

```vb
<OnDeserializing>
Private Sub SetCountryRegionDefault(sc As StreamingContext)
    CountryField = "Japan"
End Sub
```

<span data-ttu-id="53720-155">これらのメソッドの使用目的は、バージョン管理です。</span><span class="sxs-lookup"><span data-stu-id="53720-155">The intended use of these methods is for versioning.</span></span> <span data-ttu-id="53720-156">オプション フィールドにデータがない場合、逆シリアル化の実行中に、このフィールドが正しく初期化されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="53720-156">During deserialization, an optional field may not be correctly initialized if the data for the field is missing.</span></span> <span data-ttu-id="53720-157">この問題を解決するには、正しい値を割り当てるメソッドを作成してから、このメソッドに **OnDeserializingAttribute** 属性または **OnDeserializedAttribute** 属性のいずれかを適用します。</span><span class="sxs-lookup"><span data-stu-id="53720-157">This can be corrected by creating the method that assigns the correct value, then applying either the **OnDeserializingAttribute** or **OnDeserializedAttribute** attribute to the method.</span></span>

<span data-ttu-id="53720-158">型のコンテキストで使用されるメソッドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="53720-158">The following example shows the method in the context of a type.</span></span> <span data-ttu-id="53720-159">以前のバージョンのアプリケーションが新しいバージョンのアプリケーションに `Address` クラスのインスタンスを送信すると、`CountryField` フィールドのデータが欠落します。</span><span class="sxs-lookup"><span data-stu-id="53720-159">If an earlier version of an application sends an instance of the `Address` class to a later version of the application, the `CountryField` field data will be missing.</span></span> <span data-ttu-id="53720-160">しかし、逆シリアル化を行うと、このフィールドは既定値である "Japan" に設定されます。</span><span class="sxs-lookup"><span data-stu-id="53720-160">But after deserialization, the field will be set to a default value "Japan".</span></span>

```csharp
[Serializable]
public class Address
{
    public string Street;
    public string City;
    [OptionalField]
    public string CountryField;

    [OnDeserializing]
    private void SetCountryRegionDefault(StreamingContext sc)
    {
        CountryField = "Japan";
    }
}
```

```vb
<Serializable> _
Public Class Address
    Public Street As String
    Public City As String
    <OptionalField> _
    Public CountryField As String

    <OnDeserializing> _
    Private Sub SetCountryRegionDefault(sc As StreamingContext)
        CountryField = "Japan"
    End Sub
End Class
```

## <a name="the-versionadded-property"></a><span data-ttu-id="53720-161">VersionAdded プロパティ</span><span class="sxs-lookup"><span data-stu-id="53720-161">The VersionAdded property</span></span>

<span data-ttu-id="53720-162">**OptionalFieldAttribute** には **VersionAdded** プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="53720-162">The **OptionalFieldAttribute** has the **VersionAdded** property.</span></span> <span data-ttu-id="53720-163">このプロパティは、指定されたフィールドに追加された型のバージョンを示します。</span><span class="sxs-lookup"><span data-stu-id="53720-163">The property indicates which version of a type a given field has been added.</span></span> <span data-ttu-id="53720-164">次の例に示すように、このプロパティの値は 2 を開始値として、型が変更されるたびに常に 1 ずつインクリメントする必要があります。</span><span class="sxs-lookup"><span data-stu-id="53720-164">It should be incremented by exactly one (starting at 2) every time the type is modified, as shown in the following example:</span></span>

```csharp
// Version 1.0
[Serializable]
public class Person
{
    public string FullName;
}

// Version 2.0
[Serializable]
public class Person
{
    public string FullName;

    [OptionalField(VersionAdded = 2)]
    public string NickName;
    [OptionalField(VersionAdded = 2)]
    public DateTime BirthDate;
}

// Version 3.0
[Serializable]
public class Person
{
    public string FullName;

    [OptionalField(VersionAdded=2)]
    public string NickName;
    [OptionalField(VersionAdded=2)]
    public DateTime BirthDate;

    [OptionalField(VersionAdded=3)]
    public int Weight;
}
```

```vb
' Version 1.0
<Serializable> _
Public Class Person
    Public FullName
End Class

' Version 2.0
<Serializable> _
Public Class Person
    Public FullName As String

    <OptionalField(VersionAdded := 2)> _
    Public NickName As String
    <OptionalField(VersionAdded := 2)> _
    Public BirthDate As DateTime
End Class

' Version 3.0
<Serializable> _
Public Class Person
    Public FullName As String

    <OptionalField(VersionAdded := 2)> _
    Public NickName As String
    <OptionalField(VersionAdded := 2)> _
    Public BirthDate As DateTime

    <OptionalField(VersionAdded := 3)> _
    Public Weight As Integer
End Class
```

## <a name="serializationbinder"></a><span data-ttu-id="53720-165">SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="53720-165">SerializationBinder</span></span>

<span data-ttu-id="53720-166">サーバー上とクライアント上では異なるバージョンのクラスが必要なため、ユーザーによっては、シリアル化するクラスと逆シリアル化するクラスを制御することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="53720-166">Some users may need to control which class to serialize and deserialize because a different version of the class is required on the server and client.</span></span> <span data-ttu-id="53720-167"><xref:System.Runtime.Serialization.SerializationBinder> は、シリアル化中および逆シリアル化中に使用される実際の型を制御するために使用される抽象クラスです。</span><span class="sxs-lookup"><span data-stu-id="53720-167"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span> <span data-ttu-id="53720-168">このクラスを使用するには、クラスを <xref:System.Runtime.Serialization.SerializationBinder> から派生させ、<xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> メソッドと <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="53720-168">To use this class, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> methods.</span></span> <span data-ttu-id="53720-169">詳細については、「[SerializationBinder を使用したシリアル化および逆シリアル化の制御](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53720-169">For more information, see [Controlling Serialization and Deserialization with SerializationBinder](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span></span>

## <a name="best-practices"></a><span data-ttu-id="53720-170">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="53720-170">Best practices</span></span>

<span data-ttu-id="53720-171">バージョン管理が正しく行われるように、バージョン間で型を変更するときは次の規則に従ってください。</span><span class="sxs-lookup"><span data-stu-id="53720-171">To ensure proper versioning behavior, follow these rules when modifying a type from version to version:</span></span>

- <span data-ttu-id="53720-172">シリアル化したフィールドを削除しない。</span><span class="sxs-lookup"><span data-stu-id="53720-172">Never remove a serialized field.</span></span>
- <span data-ttu-id="53720-173">以前のバージョンでフィールドに <xref:System.NonSerializedAttribute> 属性が適用されていない場合、新しいバージョンでもこの属性を適用しない。</span><span class="sxs-lookup"><span data-stu-id="53720-173">Never apply the <xref:System.NonSerializedAttribute> attribute to a field if the attribute was not applied to the field in the previous version.</span></span>
- <span data-ttu-id="53720-174">シリアル化したフィールドの名前または型を変更しない。</span><span class="sxs-lookup"><span data-stu-id="53720-174">Never change the name or the type of a serialized field.</span></span>
- <span data-ttu-id="53720-175">新しいシリアル化フィールドを追加する場合は、**OptionalFieldAttribute** 属性を適用する。</span><span class="sxs-lookup"><span data-stu-id="53720-175">When adding a new serialized field, apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="53720-176">以前のバージョンでシリアル化できなかったフィールドから **NonSerializedAttribute** 属性を削除する場合は、**OptionalFieldAttribute** 属性を適用する。</span><span class="sxs-lookup"><span data-stu-id="53720-176">When removing a **NonSerializedAttribute** attribute from a field (that was not serializable in a previous version), apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="53720-177">すべてのオプション フィールドに対して、既定値として 0 または **null** が許容される場合以外は、シリアル化コールバックを使用して意味のある既定値を設定する。</span><span class="sxs-lookup"><span data-stu-id="53720-177">For all optional fields, set meaningful defaults using the serialization callbacks unless 0 or **null** as defaults are acceptable.</span></span>

<span data-ttu-id="53720-178">型が今後のシリアル化エンジンと互換性を保つようにするには、次のガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="53720-178">To ensure that a type will be compatible with future serialization engines, follow these guidelines:</span></span>

- <span data-ttu-id="53720-179">**OptionalFieldAttribute** 属性には常に **VersionAdded** を設定する。</span><span class="sxs-lookup"><span data-stu-id="53720-179">Always set the **VersionAdded** property on the **OptionalFieldAttribute** attribute correctly.</span></span>
- <span data-ttu-id="53720-180">バージョンの分岐は避ける。</span><span class="sxs-lookup"><span data-stu-id="53720-180">Avoid branched versioning.</span></span>

## <a name="see-also"></a><span data-ttu-id="53720-181">関連項目</span><span class="sxs-lookup"><span data-stu-id="53720-181">See also</span></span>

- <xref:System.SerializableAttribute>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- <xref:System.NonSerializedAttribute>
- [<span data-ttu-id="53720-182">バイナリ シリアル化</span><span class="sxs-lookup"><span data-stu-id="53720-182">Binary Serialization</span></span>](binary-serialization.md)
