---
title: クラス '<classname>' の情報を読み込めません。
ms.date: 07/20/2015
f1_keywords:
- vbc30712
- bc30712
helpviewer_keywords:
- BC30712
ms.assetid: c7ffbd6d-05c6-4261-b44b-1bcd521bb350
ms.openlocfilehash: 05c3303db90a396479bc396c5c2395c3afbb59ae
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161609"
---
# <a name="bc30712-unable-to-load-information-for-class-classname"></a><span data-ttu-id="3f5a2-102">BC30712:クラス '\<classname>' の情報を読み込めません。</span><span class="sxs-lookup"><span data-stu-id="3f5a2-102">BC30712: Unable to load information for class '\<classname>'</span></span>

<span data-ttu-id="3f5a2-103">使用可能ではないクラスが参照されました。</span><span class="sxs-lookup"><span data-stu-id="3f5a2-103">A reference was made to a class that is not available.</span></span>

 <span data-ttu-id="3f5a2-104">**エラー ID:** BC30712</span><span class="sxs-lookup"><span data-stu-id="3f5a2-104">**Error ID:** BC30712</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="3f5a2-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="3f5a2-105">To correct this error</span></span>

1. <span data-ttu-id="3f5a2-106">クラスが定義されていること、およびその名前を正しく入力したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="3f5a2-106">Verify that the class is defined and that you spelled the name correctly.</span></span>

2. <span data-ttu-id="3f5a2-107">モジュールで宣言されたいずれかのメンバーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="3f5a2-107">Try accessing one of the members declared in the module.</span></span> <span data-ttu-id="3f5a2-108">宣言されているモジュールがまだ読み込まれていないために、デバッグ環境ではメンバーを特定できないという場合もあります。</span><span class="sxs-lookup"><span data-stu-id="3f5a2-108">In some cases, the debugging environment cannot locate members because the modules where they are declared have not been loaded yet.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f5a2-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f5a2-109">See also</span></span>

- [<span data-ttu-id="3f5a2-110">Visual Studio でのデバッグ</span><span class="sxs-lookup"><span data-stu-id="3f5a2-110">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
