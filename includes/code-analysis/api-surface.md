---
ms.openlocfilehash: bf7ea8a36b9c36d82b4c00ada890829bf4c2c024
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "97700862"
---
### <a name="include-specific-api-surfaces"></a><span data-ttu-id="a6b3d-101">特定の API サーフェスを含める</span><span class="sxs-lookup"><span data-stu-id="a6b3d-101">Include specific API surfaces</span></span>

<span data-ttu-id="a6b3d-102">ユーザー補助に基づいて、この規則を実行するコードベースの部分を構成できます。</span><span class="sxs-lookup"><span data-stu-id="a6b3d-102">You can configure which parts of your codebase to run this rule on, based on their accessibility.</span></span> <span data-ttu-id="a6b3d-103">たとえば、パブリックでない API サーフェイスに対してのみルールを実行するように指定するには、プロジェクトの *editorconfig* ファイルに次のキーと値のペアを追加します。</span><span class="sxs-lookup"><span data-stu-id="a6b3d-103">For example, to specify that the rule should run only against the non-public API surface, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.api_surface = private, internal
```
