---
title: データ メンバーの順序
description: WCF でのデータメンバーの順序について説明します。 アプリケーションでは、データメンバーが送信または予想される順序を把握したり、変更したりする必要がある場合があります。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: 1cb63569c1789b1577588caf63fb0a0259e530ff
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262165"
---
# <a name="data-member-order"></a><span data-ttu-id="2581c-104">データ メンバーの順序</span><span class="sxs-lookup"><span data-stu-id="2581c-104">Data Member Order</span></span>

<span data-ttu-id="2581c-105">一部のアプリケーションでは、各種のデータ メンバーから送信される、または受信されると予想できるデータの順序 (たとえばシリアル化された XML でデータが表れる順序) がわかると便利です。</span><span class="sxs-lookup"><span data-stu-id="2581c-105">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="2581c-106">この順序を変更する必要が生じることもあります。</span><span class="sxs-lookup"><span data-stu-id="2581c-106">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="2581c-107">ここでは、このような順序を決定する規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="2581c-107">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="2581c-108">基本的な規則</span><span class="sxs-lookup"><span data-stu-id="2581c-108">Basic Rules</span></span>  

 <span data-ttu-id="2581c-109">データの順序を決定する基本的な規則には、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="2581c-109">The basic rules for data ordering include:</span></span>  
  
- <span data-ttu-id="2581c-110">データ コントラクト型が継承階層の一部である場合、その基本型のデータ メンバーが常に最初の順番になります。</span><span class="sxs-lookup"><span data-stu-id="2581c-110">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
- <span data-ttu-id="2581c-111">次に来るのは <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 属性の <xref:System.Runtime.Serialization.DataMemberAttribute> プロパティが設定されていない、現在の型のデータ メンバー (アルファベット順) になります。</span><span class="sxs-lookup"><span data-stu-id="2581c-111">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
- <span data-ttu-id="2581c-112">その次に来るのは、<xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 属性の <xref:System.Runtime.Serialization.DataMemberAttribute> プロパティが設定されているすべてのデータ メンバーです。</span><span class="sxs-lookup"><span data-stu-id="2581c-112">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="2581c-113">これらのデータ メンバーはまず `Order` プロパティの値によって並べられ、次に特定の `Order` 値を持つメンバーが複数ある場合は、そのアルファベット順に並びます。</span><span class="sxs-lookup"><span data-stu-id="2581c-113">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="2581c-114">Order 値はスキップされることがあります。</span><span class="sxs-lookup"><span data-stu-id="2581c-114">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="2581c-115">アルファベット順は、<xref:System.String.CompareOrdinal%2A> メソッドを呼び出すことによって確立されます。</span><span class="sxs-lookup"><span data-stu-id="2581c-115">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2581c-116">使用例</span><span class="sxs-lookup"><span data-stu-id="2581c-116">Examples</span></span>  

 <span data-ttu-id="2581c-117">次のコードについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="2581c-117">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="2581c-118">作成される XML は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2581c-118">The XML produced is similar to the following.</span></span>  
  
```xml  
<DerivedType>  
    <!-- Zebra is a base data member, and appears first. -->  
    <zebra/>
  
    <!-- Cat has no Order, appears alphabetically first. -->  
    <cat/>  
  
   <!-- Dog has no Order, appears alphabetically last. -->  
    <dog/>
  
    <!-- Bird is the member with the smallest Order value -->  
    <bird/>  
  
    <!-- Albatross has the next Order value, alphabetically first. -->  
    <albatross/>  
  
    <!-- Parrot, with the next Order value, alphabetically last. -->  
     <parrot/>  
  
    <!-- Antelope is the member with the highest Order value. Note that   
    Order=2 is skipped -->  
     <antelope/>
</DerivedType>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2581c-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="2581c-119">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="2581c-120">データ コントラクトの等価性</span><span class="sxs-lookup"><span data-stu-id="2581c-120">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="2581c-121">データ コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="2581c-121">Using Data Contracts</span></span>](using-data-contracts.md)
