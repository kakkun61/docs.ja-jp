---
title: 選択的シリアル化
description: この記事では、NonSerialized 属性でフィールドをマークして、フィールドをシリアル化できないようにする方法について説明します。
ms.date: 08/07/2017
dev_langs:
- CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
ms.openlocfilehash: 3c99a3be92beb992ff20188b02ff33a92f196baf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722181"
---
# <a name="selective-serialization"></a><span data-ttu-id="6c13d-103">選択的シリアル化</span><span class="sxs-lookup"><span data-stu-id="6c13d-103">Selective serialization</span></span>

<span data-ttu-id="6c13d-104">クラスには、シリアル化できないフィールドが含まれていることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="6c13d-104">A class often contains fields that shouldn't be serialized.</span></span> <span data-ttu-id="6c13d-105">たとえば、クラスのメンバー変数の 1 つにスレッド ID が格納されているとします。</span><span class="sxs-lookup"><span data-stu-id="6c13d-105">For example, assume a class stores a thread ID in a member variable.</span></span> <span data-ttu-id="6c13d-106">クラスを逆シリアル化すると、クラスのシリアル化時に格納された ID を持つスレッドが実行されなくなることがあります。したがって、この値をシリアル化しても意味はありません。</span><span class="sxs-lookup"><span data-stu-id="6c13d-106">When the class is deserialized, the thread stored the ID for when the class was serialized might no longer be running; so serializing this value doesn't make sense.</span></span> <span data-ttu-id="6c13d-107">以下のように、メンバー変数に [NonSerialized](xref:System.NonSerializedAttribute) 属性を使用してマークすることで、メンバー変数がシリアル化されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="6c13d-107">You can prevent member variables from being serialized by marking them with the [NonSerialized](xref:System.NonSerializedAttribute) attribute as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

<span data-ttu-id="6c13d-108">機密データを含むオブジェクトは、可能であれば、シリアル化できないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="6c13d-108">If possible, make an object that could contain security-sensitive data nonserializable.</span></span> <span data-ttu-id="6c13d-109">オブジェクトをシリアル化する必要がある場合は、機密データを格納する特定のフィールドに `NonSerialized` 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="6c13d-109">If the object must be serialized, apply the `NonSerialized` attribute to specific fields that store sensitive data.</span></span> <span data-ttu-id="6c13d-110">これらのフィールドをシリアル化の対象から除外しない場合は、フィールドに格納されているデータがシリアル化のアクセス許可を持つ任意のコードに公開されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6c13d-110">If you don't exclude these fields from serialization, be aware that the data they store are exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="6c13d-111">安全なシリアル化コードの記述の詳細については、「[セキュリティとシリアル化](../../framework/misc/security-and-serialization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c13d-111">For more information about writing secure serialization code, see [Security and Serialization](../../framework/misc/security-and-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="6c13d-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c13d-112">See also</span></span>

- [<span data-ttu-id="6c13d-113">バイナリ シリアル化</span><span class="sxs-lookup"><span data-stu-id="6c13d-113">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="6c13d-114">XML シリアル化および SOAP シリアル化</span><span class="sxs-lookup"><span data-stu-id="6c13d-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="6c13d-115">セキュリティとシリアル化</span><span class="sxs-lookup"><span data-stu-id="6c13d-115">Security and Serialization</span></span>](../../framework/misc/security-and-serialization.md)
