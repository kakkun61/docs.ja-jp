---
description: '#pragma warning - C# リファレンス'
title: '#pragma warning - C# リファレンス'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 5b67d384e37a5e509ce8ebcc5ddeb16a4437ea2b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91168531"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="d3bf8-103">#pragma 警告 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d3bf8-103">#pragma warning (C# Reference)</span></span>

<span data-ttu-id="d3bf8-104">`#pragma warning` を使用すると、特定の警告を有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d3bf8-104">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3bf8-105">構文</span><span class="sxs-lookup"><span data-stu-id="d3bf8-105">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3bf8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bf8-106">Parameters</span></span>  

 `warning-list`  
 <span data-ttu-id="d3bf8-107">警告番号のコンマ区切りのリスト。</span><span class="sxs-lookup"><span data-stu-id="d3bf8-107">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="d3bf8-108">"CS" というプレフィックスは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="d3bf8-108">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="d3bf8-109">警告番号が指定されていないと、`disable` はすべての警告を無効にし、`restore` はすべての警告を有効にします。</span><span class="sxs-lookup"><span data-stu-id="d3bf8-109">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3bf8-110">Visual Studio で警告番号を調べるには、プロジェクトをビルドし、**[出力]** ウィンドウで警告番号を探してください。</span><span class="sxs-lookup"><span data-stu-id="d3bf8-110">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3bf8-111">例</span><span class="sxs-lookup"><span data-stu-id="d3bf8-111">Example</span></span>  
  
```csharp
// pragma_warning.cs  
using System;  
  
#pragma warning disable 414, CS3021  
[CLSCompliant(false)]  
public class C  
{  
    int i = 1;  
    static void Main()  
    {  
    }  
}  
#pragma warning restore CS3021  
[CLSCompliant(false)]  // CS3021  
public class D  
{  
    int i = 1;  
    public static void F()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3bf8-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3bf8-112">See also</span></span>

- [<span data-ttu-id="d3bf8-113">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="d3bf8-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d3bf8-114">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="d3bf8-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d3bf8-115">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="d3bf8-115">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="d3bf8-116">C# コンパイラ エラー</span><span class="sxs-lookup"><span data-stu-id="d3bf8-116">C# Compiler Errors</span></span>](../compiler-messages/index.md)
