---
title: 構造体の受け渡し
description: 構造体とクラスをアンマネージド関数に渡す方法について説明します。 書式設定された型を定義するために使用する StructLayoutAttribute 属性について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
ms.openlocfilehash: ece5db8fdf803ce2f450ebeaaad66a379cfbf992
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268912"
---
# <a name="passing-structures"></a><span data-ttu-id="331a9-104">構造体の受け渡し</span><span class="sxs-lookup"><span data-stu-id="331a9-104">Passing Structures</span></span>

<span data-ttu-id="331a9-105">多くのアンマネージド 関数では、構造体のメンバー (Visual Basic ではユーザー定義型) またはマネージド コードで定義されたクラスのメンバーがパラメーターとして渡されることを期待しています。</span><span class="sxs-lookup"><span data-stu-id="331a9-105">Many unmanaged functions expect you to pass, as a parameter to the function, members of structures (user-defined types in Visual Basic) or members of classes that are defined in managed code.</span></span> <span data-ttu-id="331a9-106">プラットフォーム呼び出しを使って構造体またはクラスをアンマネージ コードに渡す場合は、元のレイアウトやアラインメントを保持するための追加情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="331a9-106">When passing structures or classes to unmanaged code using platform invoke, you must provide additional information to preserve the original layout and alignment.</span></span> <span data-ttu-id="331a9-107">このトピックでは、フォーマットされた型を定義するために使用する <xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="331a9-107">This topic introduces the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute, which you use to define formatted types.</span></span> <span data-ttu-id="331a9-108">マネージ構造体やマネージド クラスの場合は、**LayoutKind** 列挙型によって提供される想定されたレイアウト動作から選択できます。</span><span class="sxs-lookup"><span data-stu-id="331a9-108">For managed structures and classes, you can select from several predictable layout behaviors supplied by the **LayoutKind** enumeration.</span></span>  
  
 <span data-ttu-id="331a9-109">ここで説明する概念の中心は、構造体の型とクラスの型の相違点です。</span><span class="sxs-lookup"><span data-stu-id="331a9-109">Central to the concepts presented in this topic is an important difference between structure and class types.</span></span> <span data-ttu-id="331a9-110">構造体は値型であり、クラスは参照型です。クラスは常に最低 1 つのレベルのメモリの間接参照 (値へのポインター) を提供します。</span><span class="sxs-lookup"><span data-stu-id="331a9-110">Structures are value types and classes are reference types — classes always provide at least one level of memory indirection (a pointer to a value).</span></span> <span data-ttu-id="331a9-111">アンマネージ関数は、次の表の第 1 列のシグネチャに示されているように、間接参照を必要とすることが多いため、この違いは重要です。</span><span class="sxs-lookup"><span data-stu-id="331a9-111">This difference is important because unmanaged functions often demand indirection, as shown by the signatures in the first column of the following table.</span></span> <span data-ttu-id="331a9-112">他の列のマネージ構造体およびマネージド クラスの宣言は、宣言でどの程度間接参照のレベルを調整できるかを示しています。宣言は、Visual Basic と Visual C# の両方で指定されています。</span><span class="sxs-lookup"><span data-stu-id="331a9-112">The managed structure and class declarations in the remaining columns show the degree to which you can adjust the level of indirection in your declaration.Declarations are provided for both Visual Basic and Visual C#.</span></span>  
  
|<span data-ttu-id="331a9-113">アンマネージ シグネチャ</span><span class="sxs-lookup"><span data-stu-id="331a9-113">Unmanaged signature</span></span>|<span data-ttu-id="331a9-114">マネージド宣言</span><span class="sxs-lookup"><span data-stu-id="331a9-114">Managed declaration:</span></span> <br /><span data-ttu-id="331a9-115">間接参照なし</span><span class="sxs-lookup"><span data-stu-id="331a9-115">no indirection</span></span><br />`Structure MyType`<br />`struct MyType;`|<span data-ttu-id="331a9-116">マネージド宣言</span><span class="sxs-lookup"><span data-stu-id="331a9-116">Managed declaration:</span></span> <br /><span data-ttu-id="331a9-117">1 レベルの間接参照</span><span class="sxs-lookup"><span data-stu-id="331a9-117">one level of indirection</span></span><br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> <span data-ttu-id="331a9-118">0 レベルの間接参照を必要とします。</span><span class="sxs-lookup"><span data-stu-id="331a9-118">Demands zero levels of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="331a9-119">0 レベルの間接参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="331a9-119">Adds zero levels of indirection.</span></span>|<span data-ttu-id="331a9-120">既に 1 レベルの間接参照が存在するため調整できません。</span><span class="sxs-lookup"><span data-stu-id="331a9-120">Not possible because there is already one level of indirection.</span></span>|  
|`DoWork(MyType* x);`<br /><br /> <span data-ttu-id="331a9-121">1 レベルの間接参照を必要とします。</span><span class="sxs-lookup"><span data-stu-id="331a9-121">Demands one level of indirection.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="331a9-122">1 レベルの間接参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="331a9-122">Adds one level of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="331a9-123">0 レベルの間接参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="331a9-123">Adds zero levels of indirection.</span></span>|  
|`DoWork(MyType** x);`<br /><br /> <span data-ttu-id="331a9-124">2 レベルの間接参照を必要とします。</span><span class="sxs-lookup"><span data-stu-id="331a9-124">Demands two levels of indirection.</span></span>|<span data-ttu-id="331a9-125">**ByRef** **ByRef** または `ref` `ref` を使用できないため調整できません。</span><span class="sxs-lookup"><span data-stu-id="331a9-125">Not possible because **ByRef** **ByRef** or `ref` `ref` cannot be used.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="331a9-126">1 レベルの間接参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="331a9-126">Adds one level of indirection.</span></span>|  
  
 <span data-ttu-id="331a9-127">この表は、プラットフォーム呼び出しの宣言について次のようなガイドラインを示しています。</span><span class="sxs-lookup"><span data-stu-id="331a9-127">The table describes the following guidelines for platform invoke declarations:</span></span>  
  
- <span data-ttu-id="331a9-128">アンマネージ関数が間接参照を必要としない場合は、値渡しによる構造体を使用します。</span><span class="sxs-lookup"><span data-stu-id="331a9-128">Use a structure passed by value when the unmanaged function demands no indirection.</span></span>  
  
- <span data-ttu-id="331a9-129">アンマネージ関数が 1 レベルの間接参照を必要とする場合は、参照渡しによる構造体または値渡しによるクラスのいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="331a9-129">Use either a structure passed by reference or a class passed by value when the unmanaged function demands one level of indirection.</span></span>  
  
- <span data-ttu-id="331a9-130">アンマネージ関数が 2 レベルの間接参照を必要とする場合は、参照渡しによるクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="331a9-130">Use a class passed by reference when the unmanaged function demands two levels of indirection.</span></span>  
  
## <a name="declaring-and-passing-structures"></a><span data-ttu-id="331a9-131">構造体の宣言と受け渡し</span><span class="sxs-lookup"><span data-stu-id="331a9-131">Declaring and Passing Structures</span></span>  

 <span data-ttu-id="331a9-132">マネージド コードで `Point` 型および `Rect` 型を定義し、これらの型を User32.dll ファイル内の **PtInRect** 関数にパラメーターとして渡す方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="331a9-132">The following example shows how to define the `Point` and `Rect` structures in managed code, and pass the types as parameter to the **PtInRect** function in the User32.dll file.</span></span> <span data-ttu-id="331a9-133">**PtInRect** は、次に示すアンマネージ シグネチャを持っています。</span><span class="sxs-lookup"><span data-stu-id="331a9-133">**PtInRect** has the following unmanaged signature:</span></span>  
  
```cpp
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="331a9-134">この関数は RECT 型へのポインターを期待しているため、Rect 構造体は参照渡しする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="331a9-134">Notice that you must pass the Rect structure by reference, since the function expects a pointer to a RECT type.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
    Public x As Integer  
    Public y As Integer  
End Structure  
  
Public Structure <StructLayout(LayoutKind.Explicit)> Rect  
    <FieldOffset(0)> Public left As Integer  
    <FieldOffset(4)> Public top As Integer  
    <FieldOffset(8)> Public right As Integer  
    <FieldOffset(12)> Public bottom As Integer  
End Structure  
  
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "user32.dll" (
        ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
    public int x;  
    public int y;  
}
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
    [FieldOffset(0)] public int left;  
    [FieldOffset(4)] public int top;  
    [FieldOffset(8)] public int right;  
    [FieldOffset(12)] public int bottom;  
}
  
internal static class NativeMethods
{  
    [DllImport("User32.dll")]  
    internal static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## <a name="declaring-and-passing-classes"></a><span data-ttu-id="331a9-135">クラスの宣言と受け渡し</span><span class="sxs-lookup"><span data-stu-id="331a9-135">Declaring and Passing Classes</span></span>  

 <span data-ttu-id="331a9-136">クラスが固定したメンバー レイアウトを持っている場合に限り、クラスのメンバーをアンマネージ DLL 関数に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="331a9-136">You can pass members of a class to an unmanaged DLL function, as long as the class has a fixed member layout.</span></span> <span data-ttu-id="331a9-137">定義の順序で固定されている `MySystemTime` クラスのメンバーを User32.dll ファイル内の **GetSystemTime** に渡す方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="331a9-137">The following example demonstrates how to pass members of the `MySystemTime` class, which are defined in sequential order, to the **GetSystemTime** in the User32.dll file.</span></span> <span data-ttu-id="331a9-138">**GetSystemTime** は、次に示すアンマネージ シグネチャを持っています。</span><span class="sxs-lookup"><span data-stu-id="331a9-138">**GetSystemTime** has the following unmanaged signature:</span></span>  
  
```cpp
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="331a9-139">値型とは異なり、クラスは常に 1 レベルの間接参照を使用します。</span><span class="sxs-lookup"><span data-stu-id="331a9-139">Unlike value types, classes always have at least one level of indirection.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Class MySystemTime  
    Public wYear As Short  
    Public wMonth As Short  
    Public wDayOfWeek As Short
    Public wDay As Short  
    Public wHour As Short  
    Public wMinute As Short  
    Public wSecond As Short  
    Public wMiliseconds As Short  
End Class  
  
Friend Class NativeMethods  
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        sysTime As MySystemTime)  
    Friend Declare Auto Function MessageBox Lib "User32.dll" (
        hWnd As IntPtr, lpText As String, lpCaption As String, uType As UInteger) As Integer  
End Class  
  
Public Class TestPlatformInvoke
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        NativeMethods.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        NativeMethods.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)
    End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class MySystemTime {  
    public ushort wYear;
    public ushort wMonth;  
    public ushort wDayOfWeek;
    public ushort wDay;
    public ushort wHour;
    public ushort wMinute;
    public ushort wSecond;
    public ushort wMilliseconds;
}  
internal static class NativeMethods
{  
    [DllImport("Kernel32.dll")]  
    internal static extern void GetSystemTime(MySystemTime st);  
  
    [DllImport("user32.dll", CharSet = CharSet.Auto)]  
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);  
}  
  
public class TestPlatformInvoke  
{  
    public static void Main()  
    {  
        MySystemTime sysTime = new MySystemTime();  
        NativeMethods.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        NativeMethods.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="331a9-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="331a9-140">See also</span></span>

- [<span data-ttu-id="331a9-141">DLL 関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="331a9-141">Calling a DLL Function</span></span>](calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
