---
title: '方法: アセンブリを使用して XSLT 変換を実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76ee440b-d134-4f8f-8262-b917ad6dcbf6
ms.openlocfilehash: 62f3ec511edb7f695580dbfc386773b1dd7b7121
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829480"
---
# <a name="how-to-perform-an-xslt-transformation-by-using-an-assembly"></a><span data-ttu-id="d0661-102">方法: アセンブリを使用して XSLT 変換を実行する</span><span class="sxs-lookup"><span data-stu-id="d0661-102">How to: Perform an XSLT Transformation by Using an Assembly</span></span>
<span data-ttu-id="d0661-103">XSLT コンパイラ (xsltc.exe) は、XSLT スタイル シートをコンパイルしてアセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="d0661-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="d0661-104">このアセンブリを <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> メソッドに直接渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="d0661-104">The assembly can be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-copy-the-xml-and-xslt-files-to-your-local-computer"></a><span data-ttu-id="d0661-105">XML ファイルと XSLT ファイルをローカル コンピューターにコピーするには</span><span class="sxs-lookup"><span data-stu-id="d0661-105">To copy the XML and XSLT files to your local computer</span></span>  
  
- <span data-ttu-id="d0661-106">XSLT ファイルをローカル コンピューターにコピーし、Transform.xsl という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="d0661-106">Copy the XSLT file to your local computer and name it Transform.xsl.</span></span>  
  
    ```xml  
    <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
      xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
      xmlns:user="urn:my-scripts">  
      <msxsl:script language="C#" implements-prefix="user">  
        <![CDATA[  
      public string discount(string price){  
        char[] trimChars = { '$' };  
        //trim leading $, convert price to type double  
        double discount_value = Convert.ToDouble(price.TrimStart(trimChars));  
        //apply 10% discount and round appropriately  
        discount_value = .9*discount_value;  
        //convert value to decimal and format as currency  
        string discount_price = discount_value.ToString("C");  
        return discount_price;  
      }  
      ]]>  
      </msxsl:script>  
      <xsl:template match="catalog">  
        <html>  
          <head></head>  
          <body>  
            <table border="1">  
              <tr>  
                <th align="left">Title</th>  
                <th align="left">Author</th>  
                <th align="left">Genre</th>  
                <th align="left">Publish Date</th>  
                <th align="left">Price</th>  
              </tr>  
              <xsl:for-each select="book">  
                <tr>  
                  <td>  
                    <xsl:value-of select="title"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="author"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="genre"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="publish_date"/>  
                  </td>  
                  <xsl:choose>  
                    <xsl:when test="genre = 'Fantasy'">  
                      <td>  
                        <xsl:value-of select="user:discount(price)"/>  
                      </td>  
                    </xsl:when>  
                    <xsl:otherwise>  
                      <td>  
                        <xsl:value-of select="price"/>  
                      </td>  
                    </xsl:otherwise>  
                  </xsl:choose>  
                </tr>  
              </xsl:for-each>  
            </table>  
          </body>  
        </html>  
      </xsl:template>  
    </xsl:stylesheet>  
    ```  
  
- <span data-ttu-id="d0661-107">XML ファイルをローカル コンピューターにコピーし、`books.xml` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="d0661-107">Copy the XML file to your local computer and name it `books.xml`.</span></span>  
  
    ```xml  
    <?xml version="1.0"?>  
    <catalog>  
       <book id="bk101">  
          <author>Gambardella, Matthew</author>  
          <title>XML Developer's Guide</title>  
          <genre>Computer</genre>  
          <price>$44.95</price>  
          <publish_date>2000-10-01</publish_date>  
       </book>  
       <book id="bk102">  
          <author>Ralls, Kim</author>  
          <title>Midnight Rain</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-12-16</publish_date>  
       </book>  
       <book id="bk103">  
          <author>Corets, Eva</author>  
          <title>Maeve Ascendant</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-11-17</publish_date>  
       </book>  
       <book id="bk106">  
          <author>Randall, Cynthia</author>  
          <title>Lover Birds</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-09-02</publish_date>  
       </book>  
       <book id="bk107">  
          <author>Thurman, Paula</author>  
          <title>Splish Splash</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-11-02</publish_date>  
       </book>  
    </catalog>  
    ```  
  
### <a name="to-compile-the-style-sheet-with-the-script-enabled"></a><span data-ttu-id="d0661-108">スクリプトを有効にしてスタイル シートをコンパイルするには</span><span class="sxs-lookup"><span data-stu-id="d0661-108">To compile the style sheet with the script enabled.</span></span>  
  
1. <span data-ttu-id="d0661-109">コマンド ラインで次のコマンドを実行すると、`Transform.dll` および `Transform_Script1.dll` という名前で 2 つのアセンブリが作成されます (これが既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="d0661-109">Executing the following command from the command line creates two assemblies named `Transform.dll` and `Transform_Script1.dll` (This is the default behavior.</span></span> <span data-ttu-id="d0661-110">他に指定しなければ、既定のクラス名とアセンブリ名はメインのスタイル シートの名前になります)。</span><span class="sxs-lookup"><span data-stu-id="d0661-110">Unless otherwise specified, the name of the class and the assembly defaults to the name of the main style sheet):</span></span>  
  
    ```console  
    xsltc /settings:script+ Transform.xsl  
    ```
  
    <span data-ttu-id="d0661-111">次のコマンドを実行すると、クラス名が明示的に Transform に設定されます。</span><span class="sxs-lookup"><span data-stu-id="d0661-111">The following command explicitly sets the class name to Transform:</span></span>  
  
    ```console  
    xsltc /settings:script+ /class:Transform Transform.xsl  
    ```  
  
### <a name="to-include-the-compiled-assembly-as-a-reference-when-you-compile-your-code"></a><span data-ttu-id="d0661-112">コードをコンパイルするときにコンパイル済みアセンブリを参照として含めるには</span><span class="sxs-lookup"><span data-stu-id="d0661-112">To include the compiled assembly as a reference when you compile your code.</span></span>  
  
1. <span data-ttu-id="d0661-113">ソリューション エクスプローラーまたはコマンド ラインで参照を追加することで、Visual Studio にアセンブリを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="d0661-113">You can include an assembly in Visual Studio by adding a reference in the Solution Explorer, or from the command line.</span></span>  
  
2. <span data-ttu-id="d0661-114">コマンド ラインで C# を使用する場合、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="d0661-114">For the command line with C#, use the following:</span></span>  
  
    ```console  
    csc myCode.cs /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
3. <span data-ttu-id="d0661-115">コマンド ラインで Visual Basic を使用する場合、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="d0661-115">For the command line with Visual Basic, use the following</span></span>  
  
    ```console  
    vbc myCode.vb /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
### <a name="to-use-the-compiled-assembly-in-your-code"></a><span data-ttu-id="d0661-116">コンパイル済みアセンブリをコードで使用するには</span><span class="sxs-lookup"><span data-stu-id="d0661-116">To use the compiled assembly in your code.</span></span>  
  
<span data-ttu-id="d0661-117">コンパイルしたスタイル シートを使用して XSLT 変換を実行する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="d0661-117">The following example shows how to execute the XSLT transformation by using the compiled style sheet.</span></span>  
  
[!code-csharp[XslTransform_XSLTC#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslTransform_XSLTC/CS/XslTransform_XSLTC.cs#1)]
[!code-vb[XslTransform_XSLTC#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslTransform_XSLTC/VB/XslTransform_XSLTC.vb#1)]  
  
<span data-ttu-id="d0661-118">上記の例で、コンパイル済みアセンブリへのダイナミック リンクを作成するには、</span><span class="sxs-lookup"><span data-stu-id="d0661-118">To dynamically link to the compiled assembly, replace</span></span>
  
```csharp  
xslt.Load(typeof(Transform));  
```  
  
<span data-ttu-id="d0661-119">代入</span><span class="sxs-lookup"><span data-stu-id="d0661-119">with</span></span>  
  
```csharp
xslt.Load(System.Reflection.Assembly.Load("Transform").GetType("Transform"));  
```
  
<span data-ttu-id="d0661-120">に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d0661-120">in the example above.</span></span> <span data-ttu-id="d0661-121">Assembly.Load メソッドの詳細については、「<xref:System.Reflection.Assembly.Load%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0661-121">For more information on the Assembly.Load method, see <xref:System.Reflection.Assembly.Load%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0661-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0661-122">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="d0661-123">XSLT コンパイラ (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="d0661-123">XSLT Compiler (xsltc.exe)</span></span>](xslt-compiler-xsltc-exe.md)
- [<span data-ttu-id="d0661-124">XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="d0661-124">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="d0661-125">csc.exe を使用したコマンド ラインからのビルド</span><span class="sxs-lookup"><span data-stu-id="d0661-125">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
