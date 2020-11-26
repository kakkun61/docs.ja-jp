---
title: Trust プロトコルが混在するフェデレーション シナリオ
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
ms.openlocfilehash: 5ce178c0b2c83469a26993ce6db2d6c87815543b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248176"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="2d44b-102">Trust プロトコルが混在するフェデレーション シナリオ</span><span class="sxs-lookup"><span data-stu-id="2d44b-102">Mixing Trust Protocols in Federated Scenarios</span></span>

<span data-ttu-id="2d44b-103">シナリオによっては、フェデレーション クライアントが、Trust バージョンの一致しないサービスやセキュリティ トークン サービス (STS: Security Token Service) と通信する場合があります。</span><span class="sxs-lookup"><span data-stu-id="2d44b-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="2d44b-104">たとえば、サービス WSDL に、STS とは異なるバージョンの WS-Trust 要素を持つ `RequestSecurityTokenTemplate` アサーションが含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="2d44b-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="2d44b-105">このような場合、Windows Communication Foundation (WCF) クライアントは、から受信した WS-Trust 要素 `RequestSecurityTokenTemplate` を、STS 信頼バージョンと一致するように変換します。</span><span class="sxs-lookup"><span data-stu-id="2d44b-105">In such cases, a Windows Communication Foundation (WCF) client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> <span data-ttu-id="2d44b-106">WCF は、標準バインディングに対してのみ、不一致の信頼バージョンを処理します。</span><span class="sxs-lookup"><span data-stu-id="2d44b-106">WCF handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="2d44b-107">WCF によって認識されるすべての標準アルゴリズムパラメーターは、標準バインディングの一部です。</span><span class="sxs-lookup"><span data-stu-id="2d44b-107">All standard algorithm parameters that are recognized by WCF are part of the standard binding.</span></span> <span data-ttu-id="2d44b-108">このトピックでは、サービスと STS の間のさまざまな信頼設定を使用した WCF の動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="2d44b-108">This topic describes the WCF behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="2d44b-109">RP 2005/02 および STS 2005/02</span><span class="sxs-lookup"><span data-stu-id="2d44b-109">RP Feb 2005 and STS Feb 2005</span></span>  

 <span data-ttu-id="2d44b-110">証明書利用者 (RP: Relying Party) の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2d44b-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 <span data-ttu-id="2d44b-111">クライアント構成ファイルには、パラメーターのリストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2d44b-111">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="2d44b-112">WCF では、クライアントとサービスの両方のパラメーターを区別できません。すべてのパラメーターが追加され、(RST) に送信され `RequestSecurityTokenTemplate` ます。</span><span class="sxs-lookup"><span data-stu-id="2d44b-112">WCF cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="2d44b-113">RP Trust 1.3 および STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="2d44b-113">RP Trust 1.3 and STS Trust 1.3</span></span>  

 <span data-ttu-id="2d44b-114">RP の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2d44b-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 <span data-ttu-id="2d44b-115">クライアント構成ファイルには、RP によって指定されたパラメーターをラップする `secondaryParameters` 要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2d44b-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="2d44b-116">`EncryptionAlgorithm` `CanonicalizationAlgorithm` `KeyWrapAlgorithm` これらが要素内に存在する場合、WCF は、RST の最上位の要素から、、およびの各要素を削除し `SecondaryParameters` ます。</span><span class="sxs-lookup"><span data-stu-id="2d44b-116">WCF removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> <span data-ttu-id="2d44b-117">WCF は、 `SecondaryParameters` 変更されていない送信 RST に要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="2d44b-117">WCF appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="2d44b-118">RP Trust 2005/02 および STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="2d44b-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  

 <span data-ttu-id="2d44b-119">RP の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2d44b-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 <span data-ttu-id="2d44b-120">クライアント構成ファイルには、パラメーターのリストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2d44b-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="2d44b-121">WCF では、クライアント構成ファイルからサービスパラメーターとクライアントパラメーターを区別できません。</span><span class="sxs-lookup"><span data-stu-id="2d44b-121">From the client configuration file, WCF cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="2d44b-122">したがって、WCF は、すべてのパラメーターを信頼バージョン1.3 名前空間に変換します。</span><span class="sxs-lookup"><span data-stu-id="2d44b-122">Therefore WCF converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 <span data-ttu-id="2d44b-123">WCF は `KeyType` 、、、およびの各要素を次のように処理し `KeySize` `TokenType` ます。</span><span class="sxs-lookup"><span data-stu-id="2d44b-123">WCF handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
- <span data-ttu-id="2d44b-124">WSDL をダウンロードし、バインディングを作成して、`KeyType`、`KeySize`、および `TokenType` を RP パラメーターから割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2d44b-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="2d44b-125">その後、クライアント構成ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="2d44b-125">The client configuration file is then generated.</span></span>  
  
- <span data-ttu-id="2d44b-126">この時点で、クライアントは構成ファイル内のパラメーターを変更できます。</span><span class="sxs-lookup"><span data-stu-id="2d44b-126">The client can now change any parameter in the configuration file.</span></span>  
  
- <span data-ttu-id="2d44b-127">実行時に、WCF は、、、およびを除く、クライアント構成ファイルのセクションに指定されたすべてのパラメーターをコピーし `AdditionalTokenParameters` `KeyType` `KeySize` `TokenType` ます。これは、これらのパラメーターは構成ファイルの生成時に考慮されるためです。</span><span class="sxs-lookup"><span data-stu-id="2d44b-127">During runtime, WCF copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="2d44b-128">RP Trust 1.3 および STS Trust 2005/02</span><span class="sxs-lookup"><span data-stu-id="2d44b-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  

 <span data-ttu-id="2d44b-129">RP の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2d44b-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 <span data-ttu-id="2d44b-130">クライアント構成ファイルには、RP によって指定されたパラメーターをラップする `secondaryParamters` 要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2d44b-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="2d44b-131">WCF は、セクション内で指定されたすべてのパラメーター `SecondaryParameters` を最上位の RST 要素にコピーしますが、2005 WS-Trust 名前空間には変換しません。</span><span class="sxs-lookup"><span data-stu-id="2d44b-131">WCF copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
