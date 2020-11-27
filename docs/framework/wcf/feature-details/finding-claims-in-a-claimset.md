---
title: ClaimSet でのクレームの検索
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], finding in a claimset
- claims [WCF]
ms.assetid: a76ce107-aeb3-47d0-bfa9-134c53664e20
ms.openlocfilehash: c43a47b32a2a3c15d1a51b8b6931ebb021722a64
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268457"
---
# <a name="finding-claims-in-a-claimset"></a><span data-ttu-id="621ca-102">ClaimSet でのクレームの検索</span><span class="sxs-lookup"><span data-stu-id="621ca-102">Finding Claims in a ClaimSet</span></span>

<span data-ttu-id="621ca-103">クレームに基づく承認を使用する場合に、特定の種類のクレームの <xref:System.IdentityModel.Claims.ClaimSet> の内容を調べることは、一般的なタスクです。</span><span class="sxs-lookup"><span data-stu-id="621ca-103">Examining the content of a <xref:System.IdentityModel.Claims.ClaimSet> for particular types of claims is a common task when using claim-based authorization.</span></span> <span data-ttu-id="621ca-104">特定のクレームが存在するかどうか、<xref:System.IdentityModel.Claims.ClaimSet> を検査するには、<xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="621ca-104">To examine a <xref:System.IdentityModel.Claims.ClaimSet> for the presence of particular claims, use the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> method.</span></span> <span data-ttu-id="621ca-105">このメソッドでは、<xref:System.IdentityModel.Claims.ClaimSet> を直接繰り返すよりも優れたパフォーマンスが得られます。</span><span class="sxs-lookup"><span data-stu-id="621ca-105">This method provides better performance than iterating directly over the <xref:System.IdentityModel.Claims.ClaimSet>.</span></span> <span data-ttu-id="621ca-106">次の例は、この使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="621ca-106">The following example demonstrates this usage.</span></span> <span data-ttu-id="621ca-107">`claimType` パラメーターと `claimRight` パラメーターには `null` を指定できます。</span><span class="sxs-lookup"><span data-stu-id="621ca-107">Note that the `claimType` and `claimRight` parameters can be `null`.</span></span> <span data-ttu-id="621ca-108">その場合、パラメーターはすべてのクレームの種類および権限と一致します。</span><span class="sxs-lookup"><span data-stu-id="621ca-108">In that case, the parameters will match all claim types and claim rights.</span></span>  
  
## <a name="example"></a><span data-ttu-id="621ca-109">例</span><span class="sxs-lookup"><span data-stu-id="621ca-109">Example</span></span>  

 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="621ca-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="621ca-110">See also</span></span>

- [<span data-ttu-id="621ca-111">ID モデルを使用したクレームと承認の管理</span><span class="sxs-lookup"><span data-stu-id="621ca-111">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
