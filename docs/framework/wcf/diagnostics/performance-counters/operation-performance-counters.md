---
title: 操作パフォーマンス カウンター
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 01f3ed7b2722f7ff4bdbb50e352920bdc277330f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295231"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="420b0-102">操作パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="420b0-102">Operation Performance Counters</span></span>

<span data-ttu-id="420b0-103">操作パフォーマンス カウンターは、パフォーマンス モニター (Perfmon.exe) を使用して表示した場合、`ServiceModelOperation 4.0.0.0` パフォーマンス オブジェクトの下にあります。</span><span class="sxs-lookup"><span data-stu-id="420b0-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="420b0-104">それぞれの操作に個別のインスタンスがあります。</span><span class="sxs-lookup"><span data-stu-id="420b0-104">Each operation has an individual instance.</span></span> <span data-ttu-id="420b0-105">つまり、指定したコントラクトに 10 の操作がある場合、10 の操作カウンター インスタンスがそのコントラクトに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="420b0-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="420b0-106">オブジェクトのインスタンスには次のパターンの名前が付いています。</span><span class="sxs-lookup"><span data-stu-id="420b0-106">The object instances are named using the following pattern:</span></span>  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 <span data-ttu-id="420b0-107">このカウンターにより呼び出しがどのように使用されている、操作がどれほど効率的に実行されているかを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="420b0-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="420b0-108">パフォーマンス カウンターのインスタンス名の長さには制限があります。</span><span class="sxs-lookup"><span data-stu-id="420b0-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="420b0-109">Windows Communication Foundation (WCF) カウンターインスタンス名が最大長を超えると、WCF はインスタンス名の一部をハッシュ値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="420b0-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="420b0-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="420b0-110">See also</span></span>

- [<span data-ttu-id="420b0-111">パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="420b0-111">Performance Counters</span></span>](index.md)
