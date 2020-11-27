---
title: '方法: カスタム クレームを作成する'
description: WCF でカスタム要求を作成する方法について説明します。 WCF では、さまざまな組み込みの要求がサポートされており、一部のアプリケーションではカスタム要求が必要になる場合があります。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: ea3bc7384ca10538ca5ab1d3bb05da6a2757fb67
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256015"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="09231-104">方法: カスタム クレームを作成する</span><span class="sxs-lookup"><span data-stu-id="09231-104">How to: Create a Custom Claim</span></span>

<span data-ttu-id="09231-105">Windows Communication Foundation (WCF) の Id モデルインフラストラクチャには、組み込みのクレームの種類と権限のセットが用意されて <xref:System.IdentityModel.Claims.Claim> います。これらの型と権限を使用してインスタンスを作成するためのヘルパー関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="09231-105">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="09231-106">これらの組み込みの要求は、WCF が既定でサポートするクライアント資格情報の種類で検出された情報をモデル化するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="09231-106">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="09231-107">多くの場合はこの組み込みクレームで十分ですが、一部のアプリケーションでカスタム クレームが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="09231-107">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="09231-108">クレームは、クレームが適用されるリソースを示すクレームの種類と、リソースにアサートされる権限で構成されます。</span><span class="sxs-lookup"><span data-stu-id="09231-108">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="09231-109">このトピックでは、カスタム クレームを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="09231-109">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="09231-110">プリミティブ データ型に基づくカスタム クレームを作成するには</span><span class="sxs-lookup"><span data-stu-id="09231-110">To create a custom claim that is based on a primitive data type</span></span>  
  
1. <span data-ttu-id="09231-111">クレームの種類、リソースの値、<xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> コンストラクターへの権限を渡すことで、カスタム クレームを作成します。</span><span class="sxs-lookup"><span data-stu-id="09231-111">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="09231-112">クレームの種類の一意の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="09231-112">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="09231-113">クレームの種類は一意の文字列識別子です。</span><span class="sxs-lookup"><span data-stu-id="09231-113">The claim type is a unique string identifier.</span></span> <span data-ttu-id="09231-114">カスタム クレームを作成する場合、クレームの種類に使用されている文字列識別子が一意になるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="09231-114">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="09231-115">WCF によって定義されるクレームの種類の一覧については、クラスを参照してください <xref:System.IdentityModel.Claims.ClaimTypes> 。</span><span class="sxs-lookup"><span data-stu-id="09231-115">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="09231-116">プリミティブ データ型とリソースの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="09231-116">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="09231-117">リソースはオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="09231-117">A resource is an object.</span></span> <span data-ttu-id="09231-118">CLR 型のリソースにはプリミティブを指定できます。たとえば、<xref:System.String> や <xref:System.Int32>、または任意のシリアル化可能な型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="09231-118">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="09231-119">要求は WCF によってさまざまなポイントでシリアル化されるため、リソースの CLR 型はシリアル化可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="09231-119">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="09231-120">プリミティブ型はシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="09231-120">Primitive types are serializable.</span></span>  
  
    3. <span data-ttu-id="09231-121">WCF で定義されている権限、またはカスタム権限の一意の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="09231-121">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="09231-122">権限は一意の文字列識別子です。</span><span class="sxs-lookup"><span data-stu-id="09231-122">A right is a unique string identifier.</span></span> <span data-ttu-id="09231-123">WCF によって定義される権限は、クラスで定義され <xref:System.IdentityModel.Claims.Rights> ます。</span><span class="sxs-lookup"><span data-stu-id="09231-123">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="09231-124">カスタム クレームを作成する場合、権限に使用されている文字列識別子が一意になるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="09231-124">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="09231-125">次のコード例では、`http://example.org/claims/simplecustomclaim` という名前のリソース用の `Driver's License` というクレームの種類と <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> 権限を持つカスタム クレームを作成します。</span><span class="sxs-lookup"><span data-stu-id="09231-125">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="09231-126">プリミティブ以外のデータ型に基づくカスタム クレームを作成するには</span><span class="sxs-lookup"><span data-stu-id="09231-126">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1. <span data-ttu-id="09231-127">クレームの種類、リソースの値、<xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> コンストラクターへの権限を渡すことで、カスタム クレームを作成します。</span><span class="sxs-lookup"><span data-stu-id="09231-127">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="09231-128">クレームの種類の一意の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="09231-128">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="09231-129">クレームの種類は一意の文字列識別子です。</span><span class="sxs-lookup"><span data-stu-id="09231-129">The claim type is a unique string identifier.</span></span> <span data-ttu-id="09231-130">カスタム クレームを作成する場合、クレームの種類に使用されている文字列識別子が一意になるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="09231-130">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="09231-131">WCF によって定義されるクレームの種類の一覧については、クラスを参照してください <xref:System.IdentityModel.Claims.ClaimTypes> 。</span><span class="sxs-lookup"><span data-stu-id="09231-131">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="09231-132">リソース用のシリアル化可能な、プリミティブ型以外の型を選択または定義します。</span><span class="sxs-lookup"><span data-stu-id="09231-132">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="09231-133">リソースはオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="09231-133">A resource is an object.</span></span> <span data-ttu-id="09231-134">要求は WCF によってさまざまなポイントでシリアル化されるため、リソースの CLR 型はシリアル化可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="09231-134">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="09231-135">プリミティブ型は既にシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="09231-135">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="09231-136">新しい型を作成する場合は、<xref:System.Runtime.Serialization.DataContractAttribute> をクラスに適用します。</span><span class="sxs-lookup"><span data-stu-id="09231-136">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="09231-137">また、クレームの一部としてシリアル化する必要のある新しい型のすべてのメンバーにも <xref:System.Runtime.Serialization.DataMemberAttribute> 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="09231-137">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="09231-138">`MyResourceType` というカスタム リソース型を定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="09231-138">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]
  
    3. <span data-ttu-id="09231-139">WCF で定義されている権限、またはカスタム権限の一意の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="09231-139">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="09231-140">権限は一意の文字列識別子です。</span><span class="sxs-lookup"><span data-stu-id="09231-140">A right is a unique string identifier.</span></span> <span data-ttu-id="09231-141">WCF によって定義される権限は、クラスで定義され <xref:System.IdentityModel.Claims.Rights> ます。</span><span class="sxs-lookup"><span data-stu-id="09231-141">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="09231-142">カスタム クレームを作成する場合、権限に使用されている文字列識別子が一意になるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="09231-142">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="09231-143">次のコード例では、`http://example.org/claims/complexcustomclaim` というクレームの種類 (`MyResourceType` カスタム リソース型) および <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> 権限を持つカスタム クレームを作成します。</span><span class="sxs-lookup"><span data-stu-id="09231-143">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]
  
## <a name="example"></a><span data-ttu-id="09231-144">例</span><span class="sxs-lookup"><span data-stu-id="09231-144">Example</span></span>  

 <span data-ttu-id="09231-145">次のコード例で、プリミティブ リソース型を持つカスタム クレームと、プリミティブ以外のリソース型を持つカスタム クレームの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="09231-145">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="09231-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="09231-146">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="09231-147">ID モデルを使用したクレームと承認の管理</span><span class="sxs-lookup"><span data-stu-id="09231-147">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
