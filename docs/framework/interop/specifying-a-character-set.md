---
title: 文字セットの指定
description: ナロー (ANSI) またはワイド (Unicode) エンコードを使用する文字セットを指定する方法について説明します。 あるいは、自動ランタイム選択を指定できます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- platform invoke, attribute fields
- attribute fields in platform invoke, CharSet
- CharSet field
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
ms.openlocfilehash: 8cc4198d6c13d4705ffc5ce5229cce7a205aec8a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278181"
---
# <a name="specify-a-character-set"></a><span data-ttu-id="5f9e9-104">文字セットを指定する</span><span class="sxs-lookup"><span data-stu-id="5f9e9-104">Specify a character set</span></span>

<span data-ttu-id="5f9e9-105"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> フィールドは文字列のマーシャリングを制御し、DLL の関数名をプラットフォーム呼び出しが見つけるしくみを決定します。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-105">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="5f9e9-106">このトピックでは、両方の動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-106">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="5f9e9-107">一部の API は、文字列引数、ナロー (ANSI) とワイド (Unicode) を受け取る 2 種類の関数をエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-107">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="5f9e9-108">たとえば、Windows API には、**MessageBox** 関数の次のエントリ ポイント名が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-108">The Windows API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
- <span data-ttu-id="5f9e9-109">**MessageBoxA**</span><span class="sxs-lookup"><span data-stu-id="5f9e9-109">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="5f9e9-110">1 バイト文字の ANSI 書式設定を提供します。エントリ ポイント名に "A" が追加されます。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-110">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="5f9e9-111">**MessageBoxA** を呼び出すと、常に ANSI 形式で文字列がマーシャリングされます。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-111">Calls to **MessageBoxA** always marshal strings in ANSI format.</span></span>  
  
- <span data-ttu-id="5f9e9-112">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="5f9e9-112">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="5f9e9-113">2 バイト文字の Unicode 書式設定を提供します。エントリ ポイント名に "W" が追加されます。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-113">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="5f9e9-114">**MessageBoxW** を呼び出すと、常に Unicode 形式で文字列がマーシャリングされます。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-114">Calls to **MessageBoxW** always marshal strings in Unicode format.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="5f9e9-115">文字列のマーシャリングと名前の一致</span><span class="sxs-lookup"><span data-stu-id="5f9e9-115">String Marshaling and Name Matching</span></span>  

 <span data-ttu-id="5f9e9-116">`CharSet` フィールドは次の値を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-116">The `CharSet` field accepts the following values:</span></span>  
  
 <span data-ttu-id="5f9e9-117"><xref:System.Runtime.InteropServices.CharSet.Ansi> (既定値)</span><span class="sxs-lookup"><span data-stu-id="5f9e9-117"><xref:System.Runtime.InteropServices.CharSet.Ansi> (default value)</span></span>  
  
- <span data-ttu-id="5f9e9-118">文字列のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="5f9e9-118">String marshaling</span></span>  
  
     <span data-ttu-id="5f9e9-119">プラットフォーム呼び出しは、その管理対象形式 (Unicode) から ANSI 形式に文字列をマーシャリングします。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-119">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
- <span data-ttu-id="5f9e9-120">名前の一致</span><span class="sxs-lookup"><span data-stu-id="5f9e9-120">Name matching</span></span>  
  
     <span data-ttu-id="5f9e9-121"><xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> フィールドが `true` の場合 (Visual Basic ではこれが既定値)、プラットフォーム呼び出しによって指定した名前のみが検索されます。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-121">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="5f9e9-122">たとえば、**MessageBox** を指定した場合、プラットフォーム呼び出しは **MessageBox** を検索し、厳密に一致する綴りが見つからない場合、検索失敗となります。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-122">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="5f9e9-123">`ExactSpelling` フィールドが `false` のとき (C++ と C# で既定)、プラットフォーム呼び出しは最初に修飾なしのエイリアスを探し (**MessageBox**)、見つからなければ、修飾ありの名前を探します (**MessageBoxA**)。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-123">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="5f9e9-124">ANSI の名前一致動作と Unicode の名前一致動作は異なることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-124">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
- <span data-ttu-id="5f9e9-125">文字列のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="5f9e9-125">String marshaling</span></span>  
  
     <span data-ttu-id="5f9e9-126">プラットフォーム呼び出しは、その管理対象形式 (Unicode) から Unicode 形式に文字列をコピーします。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-126">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
- <span data-ttu-id="5f9e9-127">名前の一致</span><span class="sxs-lookup"><span data-stu-id="5f9e9-127">Name matching</span></span>  
  
     <span data-ttu-id="5f9e9-128">`ExactSpelling` フィールドが `true` の場合 (Visual Basic ではこれが既定値)、プラットフォーム呼び出しによって指定した名前のみが検索されます。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-128">When the `ExactSpelling` field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="5f9e9-129">たとえば、**MessageBox** を指定した場合、プラットフォーム呼び出しは **MessageBox** を検索し、厳密に一致する綴りが見つからない場合、検索失敗となります。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-129">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="5f9e9-130">`ExactSpelling` フィールドが `false` のとき (C++ と C# で既定)、プラットフォーム呼び出しは最初に修飾ありの名前を探し (**MessageBoxW**)、見つからなければ、修飾なしのエイリアスを探します (**MessageBox**)。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-130">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="5f9e9-131">Unicode の名前一致動作と ANSI の名前一致動作は異なることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-131">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
- <span data-ttu-id="5f9e9-132">プラットフォーム呼び出しは、対象プラットフォームに基づき、ANSI 形式または Unicode 形式を選択します。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-132">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specify-a-character-set-in-visual-basic"></a><span data-ttu-id="5f9e9-133">Visual Basic で文字セットを指定する</span><span class="sxs-lookup"><span data-stu-id="5f9e9-133">Specify a character set in Visual Basic</span></span>

<span data-ttu-id="5f9e9-134">Visual Basic では、文字セット動作を指定できます。宣言ステートメントにキーワードとして `Ansi`、`Unicode`、`Auto` を追加します。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-134">You can specify character-set behavior in Visual Basic by adding the `Ansi`, `Unicode`, or `Auto` keyword to the declaration statement.</span></span> <span data-ttu-id="5f9e9-135">文字セット キーワードを省略した場合、<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> フィールドは既定で ANSI 文字セットに設定されます。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-135">If you omit the character-set keyword, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span>

<span data-ttu-id="5f9e9-136">次の例では **MessageBox** 関数を 3 回宣言しています。宣言のたびに文字セット動作が変わっています。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-136">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="5f9e9-137">最初のステートメントでは文字セット キーワードが省略され、文字セットは既定で ANSI に設定されます。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-137">The first statement omits the character-set keyword, so the character set defaults to ANSI.</span></span> <span data-ttu-id="5f9e9-138">2 番目と 3 番目のステートメントは、キーワードで文字セットを明示的に指定しています。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-138">The second and third statements explicitly specify a character set with a keyword.</span></span>

```vb
Friend Class NativeMethods
    Friend Declare Function MessageBoxA Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Declare Unicode Function MessageBoxW Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="specify-a-character-set-in-c-and-c"></a><span data-ttu-id="5f9e9-139">C# と C++ で文字セットを指定する</span><span class="sxs-lookup"><span data-stu-id="5f9e9-139">Specify a character set in C# and C++</span></span>

<span data-ttu-id="5f9e9-140"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> フィールドは、基礎となる文字セットとして ANSI または Unicode を識別します。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-140">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="5f9e9-141">この文字セットは、メソッドの文字列引数をマーシャリングする方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-141">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="5f9e9-142">次の形式の 1 つを使用し、文字セットを指示します。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-142">Use one of the following forms to indicate the character set:</span></span>  
  
```csharp
[DllImport("DllName", CharSet = CharSet.Ansi)]
[DllImport("DllName", CharSet = CharSet.Unicode)]
[DllImport("DllName", CharSet = CharSet.Auto)]
```
  
```cpp
[DllImport("DllName", CharSet = CharSet::Ansi)]
[DllImport("DllName", CharSet = CharSet::Unicode)]
[DllImport("DllName", CharSet = CharSet::Auto)]
```
  
 <span data-ttu-id="5f9e9-143">次の例では、**MessageBox** 関数の 3 つの管理対象定義を確認できます。これにより文字セットが指定されます。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-143">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="5f9e9-144">最初の定義で、その省略により、`CharSet` フィールドは ANSI 文字セットに初期設定されます。</span><span class="sxs-lookup"><span data-stu-id="5f9e9-144">In the first definition, by its omission, the `CharSet` field defaults to the ANSI character set.</span></span>  
  
```csharp  
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll")]
    internal static extern int MessageBoxA(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Unicode)]
    internal static extern int MessageBoxW(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Auto)]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```  
  
```cpp
typedef void* HWND;

// Can use MessageBox or MessageBoxA.
[DllImport("user32")]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Can use MessageBox or MessageBoxW.
[DllImport("user32", CharSet = CharSet::Unicode)]
extern "C" int MessageBoxW(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Must use MessageBox.
[DllImport("user32", CharSet = CharSet::Auto)]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a><span data-ttu-id="5f9e9-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f9e9-145">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="5f9e9-146">マネージド コードでのプロトタイプの作成</span><span class="sxs-lookup"><span data-stu-id="5f9e9-146">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="5f9e9-147">プラットフォーム呼び出しの例</span><span class="sxs-lookup"><span data-stu-id="5f9e9-147">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="5f9e9-148">プラットフォーム呼び出しによるデータのマーシャリング</span><span class="sxs-lookup"><span data-stu-id="5f9e9-148">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
