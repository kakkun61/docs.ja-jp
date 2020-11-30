---
description: -highentropyva (C# コンパイラ オプション)
title: -highentropyva (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: f3cdeb5e63d632fecbbd94501558cc53c28a918a
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91173205"
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="6db91-103">-highentropyva (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="6db91-103">-highentropyva (C# Compiler Options)</span></span>

<span data-ttu-id="6db91-104">**-highentropyva** コンパイラ オプションは、特定の実行可能ファイルで高エントロピ ASLR (Address Space Layout Randomization) をサポートするかどうかを Windows カーネルに示します。</span><span class="sxs-lookup"><span data-stu-id="6db91-104">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6db91-105">構文</span><span class="sxs-lookup"><span data-stu-id="6db91-105">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6db91-106">引数</span><span class="sxs-lookup"><span data-stu-id="6db91-106">Arguments</span></span>  

 <span data-ttu-id="6db91-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="6db91-107">`+` &#124; `-`</span></span>  
 <span data-ttu-id="6db91-108">このオプションは、64 ビットの実行可能ファイルまたは [-platform:anycpu](./platform-compiler-option.md) コンパイラ オプションによって示される実行可能ファイルで、高エントロピ仮想アドレス空間をサポートすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="6db91-108">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](./platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="6db91-109">既定では、このオプションが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="6db91-109">The option is disabled by default.</span></span> <span data-ttu-id="6db91-110">有効にするには、**-highentropyva+** または **-highentropyva** を使用してください。</span><span class="sxs-lookup"><span data-stu-id="6db91-110">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6db91-111">注釈</span><span class="sxs-lookup"><span data-stu-id="6db91-111">Remarks</span></span>  

 <span data-ttu-id="6db91-112">**-highentropyva** オプションを指定すると、適合するバージョンの Windows カーネルで、ASLR の一環としてプロセスのアドレス空間レイアウトをランダム化する際、より高いエントロピを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="6db91-112">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="6db91-113">より高いエントロピを使うということは、スタックやヒープといったメモリ領域に割り当てることのできるアドレス数が増えることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6db91-113">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="6db91-114">これによって特定のメモリ領域の位置を推測しづらくなる効果が得られます。</span><span class="sxs-lookup"><span data-stu-id="6db91-114">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="6db91-115">**-highentropyva** コンパイラ オプションが指定された場合、対象となる実行可能ファイルとその依存モジュールは、64 ビット プロセスとして動作する際に 4 ギガバイト (GB) を超えるポインター値を処理できることが必要です。</span><span class="sxs-lookup"><span data-stu-id="6db91-115">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
