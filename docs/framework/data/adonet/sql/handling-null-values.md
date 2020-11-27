---
title: null 値の処理
description: .NET Framework Data Provider for SQL Server による null 値の処理方法について説明します。また、null 値と SqlBoolean、3 つの値を持つロジック、null 値の割り当てについても説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 2dda65f605ea9de616f01d6e52eb4e0e5def4db7
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2020
ms.locfileid: "94982519"
---
# <a name="handling-null-values"></a><span data-ttu-id="54914-103">null 値の処理</span><span class="sxs-lookup"><span data-stu-id="54914-103">Handling Null Values</span></span>

<span data-ttu-id="54914-104">列の値が不明または欠落している場合は、リレーショナル データベースの NULL 値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="54914-104">A null value in a relational database is used when the value in a column is unknown or missing.</span></span> <span data-ttu-id="54914-105">null は、空の文字列 (文字型または 日時データ型の場合) でも、0 値 (数値データ型の場合) でもありません。</span><span class="sxs-lookup"><span data-stu-id="54914-105">A null is neither an empty string (for character or datetime data types) nor a zero value (for numeric data types).</span></span> <span data-ttu-id="54914-106">ANSI SQL-92 の規格では、すべての null が一貫して処理されるように、すべてのデータ型で同じである必要があると規定されています。</span><span class="sxs-lookup"><span data-stu-id="54914-106">The ANSI SQL-92 specification states that a null must be the same for all data types, so that all nulls are handled consistently.</span></span> <span data-ttu-id="54914-107"><xref:System.Data.SqlTypes> 名前空間では、<xref:System.Data.SqlTypes.INullable> インターフェイスを実装することによって null セマンティクスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="54914-107">The <xref:System.Data.SqlTypes> namespace provides null semantics by implementing the <xref:System.Data.SqlTypes.INullable> interface.</span></span> <span data-ttu-id="54914-108"><xref:System.Data.SqlTypes> 内の各データ型には、それぞれ独自に `IsNull` プロパティと `Null` 値があり、データ型のインスタンスに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="54914-108">Each of the data types in <xref:System.Data.SqlTypes> has its own `IsNull` property and a `Null` value that can be assigned to an instance of that data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54914-109">.NET Framework version 2.0 では、null 許容値型がサポートされました。この型を使用することで、値型を拡張して基になる型のすべての値を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="54914-109">The .NET Framework version 2.0 introduced support for nullable value types, which allow programmers to extend a value type to represent all values of the underlying type.</span></span> <span data-ttu-id="54914-110">これらの CLR null 許容値型は、<xref:System.Nullable> 構造体のインスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="54914-110">These CLR nullable value types represent an instance of the <xref:System.Nullable> structure.</span></span> <span data-ttu-id="54914-111">この機能は、値の型がボックスまたはアンボックスされるときに特に有効であり、オブジェクト型との互換性が強化されます。</span><span class="sxs-lookup"><span data-stu-id="54914-111">This capability is especially useful when value types are boxed and unboxed, providing enhanced compatibility with object types.</span></span> <span data-ttu-id="54914-112">ANSI SQL の null は `null` 参照 (Visual Basic では `Nothing`) と動作が異なるため、CLR null 許容値型は null のデータベースへの格納を意図したものではありません。</span><span class="sxs-lookup"><span data-stu-id="54914-112">CLR nullable value types are not intended for storage of database nulls because an ANSI SQL null does not behave the same way as a `null` reference (or `Nothing` in Visual Basic).</span></span> <span data-ttu-id="54914-113">データベースの ANSI SQL NULL 値を操作するには、<xref:System.Data.SqlTypes> ではなく <xref:System.Nullable> NULL を使用します。</span><span class="sxs-lookup"><span data-stu-id="54914-113">For working with database ANSI SQL null values, use <xref:System.Data.SqlTypes> nulls rather than <xref:System.Nullable>.</span></span> <span data-ttu-id="54914-114">Visual Basic での CLR null 許容値型の操作の詳細については「[null 許容値型](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)」を、C# については「[null 許容値型](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54914-114">For more information on working with CLR value nullable types in Visual Basic see [Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md), and for C# see [Nullable value types](../../../../csharp/language-reference/builtin-types/nullable-value-types.md).</span></span>  
  
## <a name="nulls-and-three-valued-logic"></a><span data-ttu-id="54914-115">NULL および 3 つの値を持つロジック</span><span class="sxs-lookup"><span data-stu-id="54914-115">Nulls and Three-Valued Logic</span></span>  

 <span data-ttu-id="54914-116">列定義に NULL 値を許可することで、3 つの値を持つロジックをアプリケーションに定義できます。</span><span class="sxs-lookup"><span data-stu-id="54914-116">Allowing null values in column definitions introduces three-valued logic into your application.</span></span> <span data-ttu-id="54914-117">比較では、次の 3 つの状態のいずれかに評価されます。</span><span class="sxs-lookup"><span data-stu-id="54914-117">A comparison can evaluate to one of three conditions:</span></span>  
  
- <span data-ttu-id="54914-118">True</span><span class="sxs-lookup"><span data-stu-id="54914-118">True</span></span>  
  
- <span data-ttu-id="54914-119">False</span><span class="sxs-lookup"><span data-stu-id="54914-119">False</span></span>  
  
- <span data-ttu-id="54914-120">不明</span><span class="sxs-lookup"><span data-stu-id="54914-120">Unknown</span></span>  
  
 <span data-ttu-id="54914-121">null は不明と見なされるため、2 つの null 値を互いに比較しても、値が等しいとは見なされません。</span><span class="sxs-lookup"><span data-stu-id="54914-121">Because null is considered to be unknown, two null values compared to each other are not considered to be equal.</span></span> <span data-ttu-id="54914-122">算術演算子を使用した式では、オペランドのいずれかが null である場合は結果も null になります。</span><span class="sxs-lookup"><span data-stu-id="54914-122">In expressions using arithmetic operators, if any of the operands is null, the result is null as well.</span></span>  
  
## <a name="nulls-and-sqlboolean"></a><span data-ttu-id="54914-123">null と SqlBoolean</span><span class="sxs-lookup"><span data-stu-id="54914-123">Nulls and SqlBoolean</span></span>  

 <span data-ttu-id="54914-124">任意の <xref:System.Data.SqlTypes> 間の比較により、<xref:System.Data.SqlTypes.SqlBoolean> が返されます。</span><span class="sxs-lookup"><span data-stu-id="54914-124">Comparison between any <xref:System.Data.SqlTypes> will return a <xref:System.Data.SqlTypes.SqlBoolean>.</span></span> <span data-ttu-id="54914-125">各 `SqlType` に対する `IsNull` 関数では <xref:System.Data.SqlTypes.SqlBoolean> が返され、null 値の確認に使用できます。</span><span class="sxs-lookup"><span data-stu-id="54914-125">The `IsNull` function for each `SqlType` returns a <xref:System.Data.SqlTypes.SqlBoolean> and can be used to check for null values.</span></span> <span data-ttu-id="54914-126">次の真理値表は、null 値がある場合に AND、OR、NOT 演算子がどのように機能するかを示しています。</span><span class="sxs-lookup"><span data-stu-id="54914-126">The following truth tables show how the AND, OR, and NOT operators function in the presence of a null value.</span></span> <span data-ttu-id="54914-127">(T=true、F=false、U=不明または null。)</span><span class="sxs-lookup"><span data-stu-id="54914-127">(T=true, F=false, and U=unknown, or null.)</span></span>  
  
 <span data-ttu-id="54914-128">![真理値表](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span><span class="sxs-lookup"><span data-stu-id="54914-128">![Truth Table](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span></span>  
  
### <a name="understanding-the-ansi_nulls-option"></a><span data-ttu-id="54914-129">ANSI_NULLS オプションについて</span><span class="sxs-lookup"><span data-stu-id="54914-129">Understanding the ANSI_NULLS Option</span></span>  

 <span data-ttu-id="54914-130"><xref:System.Data.SqlTypes> では、ANSI_NULLS オプションが SQL Server で設定された場合と同じセマンティクスになります。</span><span class="sxs-lookup"><span data-stu-id="54914-130"><xref:System.Data.SqlTypes> provides the same semantics as when the ANSI_NULLS option is set on in SQL Server.</span></span> <span data-ttu-id="54914-131">すべての算術演算子 (+、-、\*、/、%)、ビット演算子 (~、&、\|)、およびほとんどの関数では、プロパティ `IsNull` を除き、オペランドまたは引数が null であった場合に null を返します。</span><span class="sxs-lookup"><span data-stu-id="54914-131">All arithmetic operators (+, -, \*, /, %), bitwise operators (~, &, \|), and most functions return null if any of the operands or arguments is null, except for the property `IsNull`.</span></span>  
  
 <span data-ttu-id="54914-132">ANSI SQL-92 標準では、WHERE 句で *columnName* = NULL とすることは認められていません。</span><span class="sxs-lookup"><span data-stu-id="54914-132">The ANSI SQL-92 standard does not support *columnName* = NULL in a WHERE clause.</span></span> <span data-ttu-id="54914-133">SQL Server では、ANSI_NULLS オプションによって、データベース内の既定の null 値の許容と null 値に対する比較の評価の両方が制御されます。</span><span class="sxs-lookup"><span data-stu-id="54914-133">In SQL Server, the ANSI_NULLS option controls both default nullability in the database and evaluation of comparisons against null values.</span></span> <span data-ttu-id="54914-134">ANSI_NULLS が有効になっている (既定) 場合、null 値をテストする式で IS NULL 演算子を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54914-134">If ANSI_NULLS is turned on (the default), the IS NULL operator must be used in expressions when testing for null values.</span></span> <span data-ttu-id="54914-135">たとえば次の比較では、ANSI_NULLS がオンである場合、常に不明となります。</span><span class="sxs-lookup"><span data-stu-id="54914-135">For example, the following comparison always yields unknown when ANSI_NULLS is on:</span></span>  
  
```sql
colname > NULL  
```  
  
 <span data-ttu-id="54914-136">また、null 値を含む変数との比較でも不明となります。</span><span class="sxs-lookup"><span data-stu-id="54914-136">Comparison to a variable containing a null value also yields unknown:</span></span>  
  
```sql
colname > @MyVariable  
```  
  
 <span data-ttu-id="54914-137">NULL 値をテストするには、IS NULL または IS NOT NULL 述語を使用します。</span><span class="sxs-lookup"><span data-stu-id="54914-137">Use the IS NULL or IS NOT NULL predicate to test for a null value.</span></span> <span data-ttu-id="54914-138">これにより WHERE 句が複雑になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="54914-138">This can add complexity to the WHERE clause.</span></span> <span data-ttu-id="54914-139">たとえば、AdventureWorks Customer テーブル内の TerritoryID 列では null 値が許可されています。</span><span class="sxs-lookup"><span data-stu-id="54914-139">For example, the TerritoryID column in the AdventureWorks Customer table allows null values.</span></span> <span data-ttu-id="54914-140">SELECT ステートメントによってその他の値と合わせて NULL 値もテストされる場合は、IS NULL 述語を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="54914-140">If a SELECT statement is to test for null values in addition to others, it must include an IS NULL predicate:</span></span>  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 <span data-ttu-id="54914-141">SQL Server で ANSI_NULLS を無効にすると、等値演算子を使用して null と比較する式を作成できます。</span><span class="sxs-lookup"><span data-stu-id="54914-141">If you set ANSI_NULLS off in SQL Server, you can create expressions that use the equality operator to compare to null.</span></span> <span data-ttu-id="54914-142">ただし、別の接続ではこの接続の null オプションの設定を回避することはできません。</span><span class="sxs-lookup"><span data-stu-id="54914-142">However, you can't prevent different connections from setting null options for that connection.</span></span> <span data-ttu-id="54914-143">IS NULL を使用した null 値のテストは、接続の ANSI_NULLS の設定に関係なく常に機能します。</span><span class="sxs-lookup"><span data-stu-id="54914-143">Using IS NULL to test for null values always works, regardless of the ANSI_NULLS settings for a connection.</span></span>  
  
 <span data-ttu-id="54914-144">`DataSet` では、ANSI_NULLS をオフに設定することはできません。<xref:System.Data.SqlTypes> における NULL 値の処理については、常に ANSI SQL-92 標準に準拠します。</span><span class="sxs-lookup"><span data-stu-id="54914-144">Setting ANSI_NULLS off is not supported in a `DataSet`, which always follows the ANSI SQL-92 standard for handling null values in <xref:System.Data.SqlTypes>.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="54914-145">NULL 値の割り当て</span><span class="sxs-lookup"><span data-stu-id="54914-145">Assigning Null Values</span></span>  

 <span data-ttu-id="54914-146">NULL 値は特殊であり、ストレージおよび割り当てのセマンティクスは、システムおよびストレージ システムの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="54914-146">Null values are special, and their storage and assignment semantics differ across different type systems and storage systems.</span></span> <span data-ttu-id="54914-147">`Dataset` は、異なる種類のストレージ システムで使用されるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="54914-147">A `Dataset` is designed to be used with different type and storage systems.</span></span>  
  
 <span data-ttu-id="54914-148">このセクションでは、異なる種類のシステムにある <xref:System.Data.DataRow> の <xref:System.Data.DataColumn> に null 値を割り当てるための null セマンティクスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="54914-148">This section describes the null semantics for assigning null values to a <xref:System.Data.DataColumn> in a <xref:System.Data.DataRow> across the different type systems.</span></span>  
  
 `DBNull.Value`  
 <span data-ttu-id="54914-149">この割り当ては、任意の型の `DataColumn` で有効です。</span><span class="sxs-lookup"><span data-stu-id="54914-149">This assignment is valid for a `DataColumn` of any type.</span></span> <span data-ttu-id="54914-150">その型が `INullable` を実装している場合、`DBNull.Value` は、厳密に型指定された適切な null 値に強制的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="54914-150">If the type implements `INullable`, `DBNull.Value` is coerced into the appropriate strongly typed Null value.</span></span>  
  
 `SqlType.Null`  
 <span data-ttu-id="54914-151">すべての <xref:System.Data.SqlTypes> データ型で `INullable` を実装します。</span><span class="sxs-lookup"><span data-stu-id="54914-151">All <xref:System.Data.SqlTypes> data types implement `INullable`.</span></span> <span data-ttu-id="54914-152">暗黙的なキャスト演算子を使用して、厳密に型指定された null 値を列のデータ型に変換できる場合は、割り当てが行われます。</span><span class="sxs-lookup"><span data-stu-id="54914-152">If the strongly typed null value can be converted into the column's data type using implicit cast operators, the assignment should go through.</span></span> <span data-ttu-id="54914-153">そうでない場合は、無効なキャスト例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="54914-153">Otherwise an invalid cast exception is thrown.</span></span>  
  
 `null`  
 <span data-ttu-id="54914-154">'null' が特定の `DataColumn` データ型で有効な値である場合は、`INullable` 型 (`SqlType.Null`) に関連付けられた適切な `DbNull.Value` または `Null` に強制的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="54914-154">If 'null' is a legal value for the given `DataColumn` data type, it is coerced into the appropriate `DbNull.Value` or `Null` associated with the `INullable` type (`SqlType.Null`)</span></span>  
  
 `derivedUdt.Null`  
 <span data-ttu-id="54914-155">UDT 列の場合、null 値は常に `DataColumn` に関連付けられた型に基づいて格納されます。</span><span class="sxs-lookup"><span data-stu-id="54914-155">For UDT columns, nulls are always stored based on the type associated with the `DataColumn`.</span></span> <span data-ttu-id="54914-156">`DataColumn` に関連付けられた UDT が `INullable` を実装しておらず、そのサブクラスで実装している場合を考えてみます。</span><span class="sxs-lookup"><span data-stu-id="54914-156">Consider the case of a UDT associated with a `DataColumn` that does not implement `INullable` while its sub-class does.</span></span> <span data-ttu-id="54914-157">この場合、派生クラスに関連付けられた厳密に型指定された null 値が割り当てられていれば、null ストレージが常に DataColumn のデータ型と一致するため、型指定されていない `DbNull.Value` として格納されます。</span><span class="sxs-lookup"><span data-stu-id="54914-157">In this case, if a strongly typed null value associated with the derived class is assigned, it is stored as an untyped `DbNull.Value`, because null storage is always consistent with the DataColumn's data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54914-158">`Nullable<T>` または <xref:System.Nullable> 構造体は、現在 `DataSet` ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="54914-158">The `Nullable<T>` or <xref:System.Nullable> structure is not currently supported in the `DataSet`.</span></span>  
  
### <a name="multiple-column-row-assignment"></a><span data-ttu-id="54914-159">複数列 (行) の割り当て</span><span class="sxs-lookup"><span data-stu-id="54914-159">Multiple Column (Row) Assignment</span></span>  

 <span data-ttu-id="54914-160">`DataTable.Add` を行にマップできる、`DataTable.LoadDataRow` や <xref:System.Data.DataRow.ItemArray%2A> などの API については、DataColumn の既定値に 'null' をマップします。</span><span class="sxs-lookup"><span data-stu-id="54914-160">`DataTable.Add`, `DataTable.LoadDataRow`, or other APIs that accept an <xref:System.Data.DataRow.ItemArray%2A> that gets mapped to a row, map 'null' to the DataColumn's default value.</span></span> <span data-ttu-id="54914-161">配列内のオブジェクトに `DbNull.Value` またはその厳密に型指定された同等の値が含まれている場合は、上記と同じ規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="54914-161">If an object in the array contains `DbNull.Value` or its strongly typed counterpart, the same rules as described above are applied.</span></span>  
  
 <span data-ttu-id="54914-162">さらに、`DataRow.["columnName"]` null 値割り当てのインスタンスには次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="54914-162">In addition, the following rules apply for an instance of `DataRow.["columnName"]` null assignments:</span></span>  
  
1. <span data-ttu-id="54914-163">"*既定*" の値は `DbNull.Value` です。ただし、それが厳密に型指定された適切な null 値となる、厳密に型指定された null 列は例外です。</span><span class="sxs-lookup"><span data-stu-id="54914-163">The *default* value is `DbNull.Value` for all except the strongly typed null columns where it is the appropriate strongly typed null value.</span></span>  
  
2. <span data-ttu-id="54914-164">XML ファイルへのシリアル化中に null 値が ("xsi:nil" として) 書き出されることはありません。</span><span class="sxs-lookup"><span data-stu-id="54914-164">Null values are never written out during serialization to XML files (as in "xsi:nil").</span></span>  
  
3. <span data-ttu-id="54914-165">既定値を含む null 以外の値はすべて、XML へのシリアル化中に常に書き出されます。</span><span class="sxs-lookup"><span data-stu-id="54914-165">All non-null values, including defaults, are always written out while serializing to XML.</span></span> <span data-ttu-id="54914-166">これは、null 値 (xsi:nil) が明示的であり、既定値が暗黙的である XSD/XML セマンティクスとは異なります (XML にない場合、検証パーサーが関連付けられた XSD スキーマから取得します)。</span><span class="sxs-lookup"><span data-stu-id="54914-166">This is unlike XSD/XML semantics where a null value (xsi:nil) is explicit and the default value is implicit (if not present in XML, a validating parser can get it from an associated XSD schema).</span></span> <span data-ttu-id="54914-167">`DataTable` ではこの逆になり、null 値が暗黙的であり、既定値が明示的です。</span><span class="sxs-lookup"><span data-stu-id="54914-167">The opposite is true for a `DataTable`: a null value is implicit and the default value is explicit.</span></span>  
  
4. <span data-ttu-id="54914-168">XML 入力から読み取られた各行で欠落している列値にはすべて、NULL が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="54914-168">All missing column values for rows read from XML input are assigned NULL.</span></span> <span data-ttu-id="54914-169"><xref:System.Data.DataTable.NewRow%2A> または同様のメソッドを使用して作成された行には、DataColumn の既定値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="54914-169">Rows created using <xref:System.Data.DataTable.NewRow%2A> or similar methods are assigned the DataColumn's default value.</span></span>  
  
5. <span data-ttu-id="54914-170"><xref:System.Data.DataRow.IsNull%2A> メソッドは、`true` と `DbNull.Value` のどちらに対しても `INullable.Null` を返します。</span><span class="sxs-lookup"><span data-stu-id="54914-170">The <xref:System.Data.DataRow.IsNull%2A> method returns `true` for both `DbNull.Value` and `INullable.Null`.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="54914-171">NULL 値の割り当て</span><span class="sxs-lookup"><span data-stu-id="54914-171">Assigning Null Values</span></span>  

 <span data-ttu-id="54914-172">任意の <xref:System.Data.SqlTypes> インスタンスの既定値は NULL です。</span><span class="sxs-lookup"><span data-stu-id="54914-172">The default value for any <xref:System.Data.SqlTypes> instance is null.</span></span>  
  
 <span data-ttu-id="54914-173"><xref:System.Data.SqlTypes> の null 値は型固有であり、`DbNull` などの 1 つの値で表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="54914-173">Nulls in <xref:System.Data.SqlTypes> are type-specific and cannot be represented by a single value, such as `DbNull`.</span></span> <span data-ttu-id="54914-174">null 値を確認するには、`IsNull` プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="54914-174">Use the `IsNull` property to check for nulls.</span></span>  
  
 <span data-ttu-id="54914-175">null 値は次のコード例に示すように、<xref:System.Data.DataColumn> に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="54914-175">Null values can be assigned to a <xref:System.Data.DataColumn> as shown in the following code example.</span></span> <span data-ttu-id="54914-176">null 値は例外をトリガーすることなく、`SqlTypes` 変数に直接割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="54914-176">You can directly assign null values to `SqlTypes` variables without triggering an exception.</span></span>  
  
### <a name="example"></a><span data-ttu-id="54914-177">例</span><span class="sxs-lookup"><span data-stu-id="54914-177">Example</span></span>  

 <span data-ttu-id="54914-178">次のコード例では、<xref:System.Data.SqlTypes.SqlInt32> と <xref:System.Data.SqlTypes.SqlString> として定義された 2 つの列を含む <xref:System.Data.DataTable> を作成します。</span><span class="sxs-lookup"><span data-stu-id="54914-178">The following code example creates a <xref:System.Data.DataTable> with two columns defined as <xref:System.Data.SqlTypes.SqlInt32> and <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="54914-179">このコードでは、既知の値の 1 行と null 値の 1 行を追加し、<xref:System.Data.DataTable> を反復処理します。これによって変数に値を割り当て、コンソール ウィンドウに出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="54914-179">The code adds one row of known values, one row of null values and then iterates through the <xref:System.Data.DataTable>, assigning the values to variables and displaying the output in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 <span data-ttu-id="54914-180">この例を実行すると、次の結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="54914-180">This example displays the following results:</span></span>  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a><span data-ttu-id="54914-181">NULL 値と SqlTypes および CLR 型との比較</span><span class="sxs-lookup"><span data-stu-id="54914-181">Comparing Null Values with SqlTypes and CLR Types</span></span>  

 <span data-ttu-id="54914-182">NULL 値を比較する場合は、`Equals` メソッドによって <xref:System.Data.SqlTypes> で NULL 値を評価する方法と、CLR 型を使用する方法との違いを理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="54914-182">When comparing null values, it is important to understand the difference between the way the `Equals` method evaluates null values in <xref:System.Data.SqlTypes> as compared with the way it works with CLR types.</span></span> <span data-ttu-id="54914-183"><xref:System.Data.SqlTypes>`Equals` メソッドはすべて、null 値の評価にデータベース セマンティクスを使用します。値の一方または両方が null である場合は、その比較によって null が得られます。</span><span class="sxs-lookup"><span data-stu-id="54914-183">All of the <xref:System.Data.SqlTypes>`Equals` methods use database semantics for evaluating null values: if either or both of the values is null, the comparison yields null.</span></span> <span data-ttu-id="54914-184">これに対して、2 つの <xref:System.Data.SqlTypes> に対して CLR `Equals` メソッドを使用すると、両方が null である場合に true が得られます。</span><span class="sxs-lookup"><span data-stu-id="54914-184">On the other hand, using the CLR `Equals` method on two <xref:System.Data.SqlTypes> will yield true if both are null.</span></span> <span data-ttu-id="54914-185">これは、CLR `String.Equals` メソッドなどのインスタンス メソッドの使用と、静的/共有メソッド `SqlString.Equals` の使用の違いを反映しています。</span><span class="sxs-lookup"><span data-stu-id="54914-185">This reflects the difference between using an instance method such as the CLR `String.Equals` method, and using the static/shared method, `SqlString.Equals`.</span></span>  
  
 <span data-ttu-id="54914-186">次の例は、`SqlString.Equals` メソッドと `String.Equals` メソッドにそれぞれ null 値のペアを渡し、次に空の文字列のペアを渡した場合の各メソッドの結果の違いを示しています。</span><span class="sxs-lookup"><span data-stu-id="54914-186">The following example demonstrates the difference in results between the `SqlString.Equals` method and the `String.Equals` method when each is passed a pair of null values and then a pair of empty strings.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 <span data-ttu-id="54914-187">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="54914-187">The code produces the following output:</span></span>  
  
```output
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True
```  
  
## <a name="see-also"></a><span data-ttu-id="54914-188">関連項目</span><span class="sxs-lookup"><span data-stu-id="54914-188">See also</span></span>

- [<span data-ttu-id="54914-189">SQL Server データ型と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="54914-189">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="54914-190">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="54914-190">ADO.NET Overview</span></span>](../ado-net-overview.md)
