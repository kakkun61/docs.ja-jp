---
title: '方法: ファイルがアセンブリであるかどうかを確認する'
description: この記事では、ファイルが .NET アセンブリであるかどうかを手動およびプログラムによって確認する方法について説明します。
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: b78acaad31996f8fc2b965f51f541e99aeceb111
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731502"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="aedf0-103">方法: ファイルがアセンブリであるかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="aedf0-103">How to: Determine if a file is an assembly</span></span>

<span data-ttu-id="aedf0-104">ファイルが管理されていて、ファイルのメタデータにアセンブリ エントリが含まれている場合、そのファイルはアセンブリです。</span><span class="sxs-lookup"><span data-stu-id="aedf0-104">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="aedf0-105">アセンブリとメタデータの詳細については、「[アセンブリ マニフェスト](manifest.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aedf0-105">For more information on assemblies and metadata, see [Assembly manifest](manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="aedf0-106">ファイルがアセンブリかどうかを手動で確認する方法</span><span class="sxs-lookup"><span data-stu-id="aedf0-106">How to manually determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="aedf0-107">[Ildasm.exe (IL 逆アセンブラー)](../../framework/tools/ildasm-exe-il-disassembler.md) を起動します。</span><span class="sxs-lookup"><span data-stu-id="aedf0-107">Start the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2. <span data-ttu-id="aedf0-108">テストするファイルを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="aedf0-108">Load the file you want to test.</span></span>  
  
3. <span data-ttu-id="aedf0-109">**ILDASM** で、そのファイルが移植可能な実行可能 (PE) ファイルではないと報告された場合、そのファイルはアセンブリでありません。</span><span class="sxs-lookup"><span data-stu-id="aedf0-109">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="aedf0-110">詳細については、トピック「[方法: アセンブリの内容を表示する](view-contents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aedf0-110">For more information, see the topic [How to: View assembly contents](view-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="aedf0-111">ファイルがアセンブリかどうかをプログラムによって確認する方法</span><span class="sxs-lookup"><span data-stu-id="aedf0-111">How to programmatically determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="aedf0-112">テストするファイルの完全パスと名前を渡して、<xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="aedf0-112">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method, passing the full file path and name of the file you are testing.</span></span>  
  
2. <span data-ttu-id="aedf0-113"><xref:System.BadImageFormatException> 例外がスローされた場合、ファイルはアセンブリでありません。</span><span class="sxs-lookup"><span data-stu-id="aedf0-113">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aedf0-114">例</span><span class="sxs-lookup"><span data-stu-id="aedf0-114">Example</span></span>  

<span data-ttu-id="aedf0-115">次の例では、DLL がアセンブリかどうかをテストして確認します。</span><span class="sxs-lookup"><span data-stu-id="aedf0-115">This example tests a DLL to see if it is an assembly.</span></span>  

```csharp
class TestAssembly  
{  
    static void Main()  
    {  
  
        try  
        {  
            System.Reflection.AssemblyName testAssembly =  
                System.Reflection.AssemblyName.GetAssemblyName(@"C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll");  
  
            System.Console.WriteLine("Yes, the file is an assembly.");  
        }  
  
        catch (System.IO.FileNotFoundException)  
        {  
            System.Console.WriteLine("The file cannot be found.");  
        }  
  
        catch (System.BadImageFormatException)  
        {  
            System.Console.WriteLine("The file is not an assembly.");  
        }  
  
        catch (System.IO.FileLoadException)  
        {  
            System.Console.WriteLine("The assembly has already been loaded.");  
        }  
    }  
}  
/* Output (with .NET Framework 3.5 installed):  
    Yes, the file is an assembly.  
*/  
```  

```vb  
Module Module1  
    Sub Main()  
        Try  
            Dim testAssembly As Reflection.AssemblyName =  
                                Reflection.AssemblyName.GetAssemblyName("C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll")  
            Console.WriteLine("Yes, the file is an Assembly.")  
        Catch ex As System.IO.FileNotFoundException  
            Console.WriteLine("The file cannot be found.")  
        Catch ex As System.BadImageFormatException  
            Console.WriteLine("The file is not an Assembly.")  
        Catch ex As System.IO.FileLoadException  
            Console.WriteLine("The Assembly has already been loaded.")  
        End Try  
        Console.ReadLine()  
    End Sub  
End Module  
' Output (with .NET Framework 3.5 installed):  
'        Yes, the file is an Assembly.  
```

<span data-ttu-id="aedf0-116"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> メソッドはテスト ファイルを読み込み、情報が読み取られた時点で解放します。</span><span class="sxs-lookup"><span data-stu-id="aedf0-116">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aedf0-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="aedf0-117">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="aedf0-118">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="aedf0-118">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="aedf0-119">プログラミングの概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aedf0-119">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="aedf0-120">.NET のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="aedf0-120">Assemblies in .NET</span></span>](index.md)
