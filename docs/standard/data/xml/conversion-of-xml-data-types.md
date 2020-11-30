---
title: XML データ型の変換
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
ms.openlocfilehash: 108cfbf1ee8ff3d6fbe088d6dd14d0354750cb0c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701498"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="27281-102">XML データ型の変換</span><span class="sxs-lookup"><span data-stu-id="27281-102">Conversion of XML Data Types</span></span>

<span data-ttu-id="27281-103">**XmlConvert** クラスのメソッドのほとんどは、文字列と厳密に型指定された形式との間のデータ変換に使われます。</span><span class="sxs-lookup"><span data-stu-id="27281-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly typed formats.</span></span> <span data-ttu-id="27281-104">これらのメソッドはロケールに依存しません。</span><span class="sxs-lookup"><span data-stu-id="27281-104">Methods are locale independent.</span></span> <span data-ttu-id="27281-105">つまり、変換の実行時にはロケールの設定は考慮されません。</span><span class="sxs-lookup"><span data-stu-id="27281-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="27281-106">文字列を型として読み込む</span><span class="sxs-lookup"><span data-stu-id="27281-106">Reading String as types</span></span>  

 <span data-ttu-id="27281-107">文字列を読み込んで **DateTime** 型に変換するサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="27281-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="27281-108">入力として次の XML を使用します。</span><span class="sxs-lookup"><span data-stu-id="27281-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="27281-109">**入力**</span><span class="sxs-lookup"><span data-stu-id="27281-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="27281-110">次のコードは、文字列を **DateTime** 形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="27281-110">This code converts the string to the **DateTime** format:</span></span>  
  
```vb  
reader.ReadStartElement()  
Dim vDateTime As DateTime = XmlConvert.ToDateTime(reader.ReadString())  
Console.WriteLine(vDateTime)  
```  
  
```csharp  
reader.ReadStartElement();  
DateTime vDateTime = XmlConvert.ToDateTime(reader.ReadString());  
Console.WriteLine(vDateTime);  
```  
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="27281-111">文字列を型として書き込む</span><span class="sxs-lookup"><span data-stu-id="27281-111">Writing Strings as types</span></span>  

 <span data-ttu-id="27281-112">**Int32** を読み込んで文字列に変換するサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="27281-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="27281-113">入力として次の XML を使用します。</span><span class="sxs-lookup"><span data-stu-id="27281-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="27281-114">**入力**</span><span class="sxs-lookup"><span data-stu-id="27281-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="27281-115">次のコードは、**Int32** を **String** に変換します。</span><span class="sxs-lookup"><span data-stu-id="27281-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="27281-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="27281-116">See also</span></span>

- [<span data-ttu-id="27281-117">文字列の .NET Framework データ型への変換</span><span class="sxs-lookup"><span data-stu-id="27281-117">Converting Strings to .NET Framework Data Types</span></span>](converting-strings-to-dotnet-data-types.md)
- [<span data-ttu-id="27281-118">.NET Framework 型の文字列への変換</span><span class="sxs-lookup"><span data-stu-id="27281-118">Converting .NET Framework Types to Strings</span></span>](converting-dotnet-types-to-strings.md)
