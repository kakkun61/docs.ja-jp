---
author: dotpaul
ms.author: paulming
ms.date: 05/01/2019
ms.topic: include
ms.openlocfilehash: cf944ae9ca200d34a1f0f32e68bf3aee73a9500a
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2020
ms.locfileid: "96591105"
---
- <span data-ttu-id="ecdfe-101">可能であれば、代わりにセキュリティで保護されたシリアライザーを使用して、 **攻撃者が任意の型を逆シリアル化することを許可しない** でください。</span><span class="sxs-lookup"><span data-stu-id="ecdfe-101">If possible, use a secure serializer instead, and **don't allow an attacker to specify an arbitrary type to deserialize**.</span></span> <span data-ttu-id="ecdfe-102">安全性の高いシリアライザーには次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="ecdfe-102">Some safer serializers include:</span></span>

  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <span data-ttu-id="ecdfe-103"><xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -使用しないで <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType> ください。</span><span class="sxs-lookup"><span data-stu-id="ecdfe-103"><xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> - Never use <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ecdfe-104">型リゾルバーを使用する必要がある場合は、逆シリアル化された型を予期されるリストに制限します。</span><span class="sxs-lookup"><span data-stu-id="ecdfe-104">If you must use a type resolver, restrict deserialized types to an expected list.</span></span>
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - <span data-ttu-id="ecdfe-105">Newtonsoft Json.NET-TypeNameHandling を使用します。</span><span class="sxs-lookup"><span data-stu-id="ecdfe-105">Newtonsoft Json.NET - Use TypeNameHandling.None.</span></span> <span data-ttu-id="ecdfe-106">TypeNameHandling に別の値を使用する必要がある場合は、カスタム ISerializationBinder を使用して、逆シリアル化された型を予期されるリストに制限します。</span><span class="sxs-lookup"><span data-stu-id="ecdfe-106">If you must use another value for TypeNameHandling, restrict deserialized types to an expected list with a custom ISerializationBinder.</span></span>
  - <span data-ttu-id="ecdfe-107">プロトコル バッファー</span><span class="sxs-lookup"><span data-stu-id="ecdfe-107">Protocol Buffers</span></span>

- <span data-ttu-id="ecdfe-108">シリアル化されたデータの改ざん防止を行います。</span><span class="sxs-lookup"><span data-stu-id="ecdfe-108">Make the serialized data tamper-proof.</span></span> <span data-ttu-id="ecdfe-109">シリアル化後に、シリアル化されたデータに暗号署名します。</span><span class="sxs-lookup"><span data-stu-id="ecdfe-109">After serialization, cryptographically sign the serialized data.</span></span> <span data-ttu-id="ecdfe-110">逆シリアル化する前に、暗号化署名を検証します。</span><span class="sxs-lookup"><span data-stu-id="ecdfe-110">Before deserialization, validate the cryptographic signature.</span></span> <span data-ttu-id="ecdfe-111">暗号化キーが公開され、キーのローテーションのための設計になっていないことを防止します。</span><span class="sxs-lookup"><span data-stu-id="ecdfe-111">Protect the cryptographic key from being disclosed and design for key rotations.</span></span>
