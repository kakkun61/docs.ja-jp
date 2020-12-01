---
title: MsgBox のサンプル
description: MsgBox を使用して文字列型を In パラメーターとして値渡しするサンプルを参照します。 .NET で EntryPoint、CharSet、ExactSpelling の各フィールドをいつ使用するかを示します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
ms.openlocfilehash: 024ed612115ce73646596651fe454238418446db
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242020"
---
# <a name="msgbox-sample"></a><span data-ttu-id="4d8a6-104">MsgBox のサンプル</span><span class="sxs-lookup"><span data-stu-id="4d8a6-104">MsgBox Sample</span></span>

<span data-ttu-id="4d8a6-105">このサンプルでは、文字列型を In パラメーターとして値渡しする方法と、<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>、<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>、および <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> の各フィールドを使用する場合について説明します。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-105">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="4d8a6-106">MsgBox のサンプルで使用するアンマネージ関数とその関数宣言を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-106">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="4d8a6-107">User32.dll からエクスポートされる **MessageBox**。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-107">**MessageBox** exported from User32.dll.</span></span>  
  
    ```cpp
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,
       UINT uType);  
    ```  
  
 <span data-ttu-id="4d8a6-108">このサンプルでは、`NativeMethods` クラスの中には、`MsgBoxSample` クラスによって呼び出される各アンマネージド 関数に関するマネージド プロトタイプが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-108">In this sample, the `NativeMethods` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="4d8a6-109">マネージド プロトタイプ メソッドの `MsgBox`、`MsgBox2`、および `MsgBox3` は、同じアンマネージド 関数に対して異なる宣言を持ちます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-109">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="4d8a6-110">`MsgBox2` に対する宣言により、メッセージ ボックス内に不正な出力が生成されます。その原因は、ANSI として指定した文字型が、Unicode 関数の名前であるエントリ ポイント `MessageBoxW` と一致しないからです。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-110">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="4d8a6-111">`MsgBox3` に対する宣言により、**EntryPoint**、**CharSet**、および **ExactSpelling** の各フィールド間に不一致が発生します。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-111">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="4d8a6-112">`MsgBox3` を呼び出すと例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-112">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="4d8a6-113">文字列の名前付けと名前のマーシャリングの詳細については、「[文字セットの指定](specifying-a-character-set.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-113">For detailed information on string naming and name marshaling, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="4d8a6-114">プロトタイプの宣言</span><span class="sxs-lookup"><span data-stu-id="4d8a6-114">Declaring Prototypes</span></span>  

 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="4d8a6-115">関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="4d8a6-115">Calling Functions</span></span>  

 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="4d8a6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d8a6-116">See also</span></span>

- [<span data-ttu-id="4d8a6-117">マーシャリング (文字列の)</span><span class="sxs-lookup"><span data-stu-id="4d8a6-117">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="4d8a6-118">文字列に対する既定のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="4d8a6-118">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
- [<span data-ttu-id="4d8a6-119">マネージド コードでのプロトタイプの作成</span><span class="sxs-lookup"><span data-stu-id="4d8a6-119">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="4d8a6-120">文字セットの指定</span><span class="sxs-lookup"><span data-stu-id="4d8a6-120">Specifying a Character Set</span></span>](specifying-a-character-set.md)
