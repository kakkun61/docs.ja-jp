---
title: セキュリティ イベントの監査
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
ms.openlocfilehash: 985004313c7d9843f2e9960805a6c0623d43a41f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96234818"
---
# <a name="auditing-security-events"></a><span data-ttu-id="c493a-102">セキュリティ イベントの監査</span><span class="sxs-lookup"><span data-stu-id="c493a-102">Auditing Security Events</span></span>

<span data-ttu-id="c493a-103">Windows Communication Foundation (WCF) を使用して作成されたアプリケーションは、監査機能を使用してセキュリティイベント (成功、失敗、またはその両方) をログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="c493a-103">Applications created with Windows Communication Foundation (WCF) can log security events (either success, failure, or both) with the auditing feature.</span></span> <span data-ttu-id="c493a-104">これらのイベントは Windows システム イベント ログに書き込まれ、イベント ビューアーを使用して確認できます。</span><span class="sxs-lookup"><span data-stu-id="c493a-104">The events are written to the Windows system event log and can be examined using the Event Viewer.</span></span>  
  
 <span data-ttu-id="c493a-105">監査を使用すると、管理者は既に発生した攻撃や現在進行中の攻撃を検出できます。</span><span class="sxs-lookup"><span data-stu-id="c493a-105">Auditing provides a way for an administrator to detect an attack that has already occurred or is in progress.</span></span> <span data-ttu-id="c493a-106">また、開発者がセキュリティ関連の問題をデバッグする際にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c493a-106">In addition, auditing can help a developer to debug security-related problems.</span></span> <span data-ttu-id="c493a-107">たとえば、認証またはポリシー チェックの構成エラーによって承認済みユーザーへのアクセスが拒否された場合、開発者は、イベント ログを検査することによって、このエラーの原因をすばやく発見し、取り出すことができます。</span><span class="sxs-lookup"><span data-stu-id="c493a-107">For example, if an error in the configuration of the authorization or checking policy accidentally denies access to an authorized user, a developer can quickly discover and isolate the cause of this error by examining the event log.</span></span>  
  
 <span data-ttu-id="c493a-108">WCF セキュリティの詳細については、「 [セキュリティの概要](security-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c493a-108">For more information about WCF security, see [Security Overview](security-overview.md).</span></span> <span data-ttu-id="c493a-109">WCF のプログラミングの詳細については、「 [基本的な Wcf プログラミング](../basic-wcf-programming.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c493a-109">For more information about programming WCF, see [Basic WCF Programming](../basic-wcf-programming.md).</span></span>  
  
## <a name="audit-level-and-behavior"></a><span data-ttu-id="c493a-110">監査レベルと動作</span><span class="sxs-lookup"><span data-stu-id="c493a-110">Audit Level and Behavior</span></span>  

 <span data-ttu-id="c493a-111">セキュリティ監査には次の 2 つのレベルがあります。</span><span class="sxs-lookup"><span data-stu-id="c493a-111">Two levels of security audits exist:</span></span>  
  
- <span data-ttu-id="c493a-112">呼び出し元を承認するサービス承認レベル。</span><span class="sxs-lookup"><span data-stu-id="c493a-112">Service authorization level, in which a caller is authorized.</span></span>  
  
- <span data-ttu-id="c493a-113">メッセージレベル。 WCF がメッセージの有効性をチェックし、呼び出し元を認証します。</span><span class="sxs-lookup"><span data-stu-id="c493a-113">Message level, in which WCF checks for message validity and authenticates the caller.</span></span>  
  
 <span data-ttu-id="c493a-114">成功または失敗の両方の監査レベルを確認できます。これは、 *監査の動作* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c493a-114">You can check both audit levels for success or failure, which is known as the *audit behavior*.</span></span>  
  
## <a name="audit-log-location"></a><span data-ttu-id="c493a-115">監査ログの場所</span><span class="sxs-lookup"><span data-stu-id="c493a-115">Audit Log Location</span></span>  

 <span data-ttu-id="c493a-116">監査のレベルと動作を決定したら、ユーザー (または管理者) は監査ログの場所を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c493a-116">Once you determine an audit level and behavior, you (or an administrator) can specify a location for the audit log.</span></span> <span data-ttu-id="c493a-117">監査ログの場所は、Default、Application、および Security の 3 つから選択できます。</span><span class="sxs-lookup"><span data-stu-id="c493a-117">The three choices include: Default, Application, and Security.</span></span> <span data-ttu-id="c493a-118">Default を指定した場合、ログの実際の場所は、ユーザーが使用しているシステムと、セキュリティ ログへの書き込みがサポートされているかどうかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="c493a-118">When you specify Default, the actual log depends on which system you are using and whether the system supports writing to the security log.</span></span> <span data-ttu-id="c493a-119">詳細については、このトピックで後述する「オペレーティングシステム」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c493a-119">For more information, see the "Operating System" section later in this topic.</span></span>  
  
 <span data-ttu-id="c493a-120">セキュリティ ログへの書き込みを行うには、`SeAuditPrivilege` が必要です。</span><span class="sxs-lookup"><span data-stu-id="c493a-120">To write to the Security log requires the `SeAuditPrivilege`.</span></span> <span data-ttu-id="c493a-121">既定では、この権限は Local System アカウントと Network Service アカウントだけに与えられています。</span><span class="sxs-lookup"><span data-stu-id="c493a-121">By default, only Local System and Network Service accounts have this privilege.</span></span> <span data-ttu-id="c493a-122">セキュリティ ログの `read` および `delete` 機能を管理するには、`SeSecurityPrivilege` が必要です。</span><span class="sxs-lookup"><span data-stu-id="c493a-122">To manage the Security log functions `read` and `delete` requires the `SeSecurityPrivilege`.</span></span> <span data-ttu-id="c493a-123">既定では、この権限は管理者だけに与えられています。</span><span class="sxs-lookup"><span data-stu-id="c493a-123">By default, only administrators have this privilege.</span></span>  
  
 <span data-ttu-id="c493a-124">これに対し、アプリケーション ログは認証済みユーザーが読み書きできます。</span><span class="sxs-lookup"><span data-stu-id="c493a-124">In contrast, authenticated users can read and write to the Application log.</span></span> <span data-ttu-id="c493a-125">既定では、Windows XP は監査イベントをアプリケーションログに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="c493a-125">Windows XP writes audit events to the Application log by default.</span></span> <span data-ttu-id="c493a-126">すべての認証済みユーザーに表示される個人情報をログに格納することもできます。</span><span class="sxs-lookup"><span data-stu-id="c493a-126">The log can also contain personal information that is visible to all authenticated users.</span></span>  
  
## <a name="suppressing-audit-failures"></a><span data-ttu-id="c493a-127">監査エラーの抑制</span><span class="sxs-lookup"><span data-stu-id="c493a-127">Suppressing Audit Failures</span></span>  

 <span data-ttu-id="c493a-128">監査中に監査エラーを表示しないように指定するオプションも用意されています。</span><span class="sxs-lookup"><span data-stu-id="c493a-128">Another option during auditing is whether to suppress any audit failure.</span></span> <span data-ttu-id="c493a-129">既定では、監査エラーはアプリケーションに影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="c493a-129">By default, an audit failure does not affect an application.</span></span> <span data-ttu-id="c493a-130">ただし、必要に応じて、このオプションを `false` に設定し、例外をスローすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c493a-130">If required, however, you can set the option to `false`, which causes an exception to be thrown.</span></span>  
  
## <a name="programming-auditing"></a><span data-ttu-id="c493a-131">プログラミング監査</span><span class="sxs-lookup"><span data-stu-id="c493a-131">Programming Auditing</span></span>  

 <span data-ttu-id="c493a-132">監査動作は、プログラムまたは構成を使用して指定できます。</span><span class="sxs-lookup"><span data-stu-id="c493a-132">You can specify auditing behavior either programmatically or through configuration.</span></span>  
  
### <a name="auditing-classes"></a><span data-ttu-id="c493a-133">監査クラス</span><span class="sxs-lookup"><span data-stu-id="c493a-133">Auditing Classes</span></span>  

 <span data-ttu-id="c493a-134">監査動作をプログラムで指定するときに使用するクラスとプロパティを次の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="c493a-134">The following table describes the classes and properties used to program auditing behavior.</span></span>  
  
|<span data-ttu-id="c493a-135">インスタンス</span><span class="sxs-lookup"><span data-stu-id="c493a-135">Class</span></span>|<span data-ttu-id="c493a-136">説明</span><span class="sxs-lookup"><span data-stu-id="c493a-136">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|<span data-ttu-id="c493a-137">サービス動作として監査を行うための設定オプションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c493a-137">Enables setting options for auditing as a service behavior.</span></span>|  
|<xref:System.ServiceModel.AuditLogLocation>|<span data-ttu-id="c493a-138">書き込み先のログを指定するための列挙体。</span><span class="sxs-lookup"><span data-stu-id="c493a-138">Enumeration to specify which log to write to.</span></span> <span data-ttu-id="c493a-139">指定できる値は、Default、Application、および Security です。</span><span class="sxs-lookup"><span data-stu-id="c493a-139">The possible values are Default, Application, and Security.</span></span> <span data-ttu-id="c493a-140">Default を選択した場合、実際のログの場所はオペレーティング システムによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="c493a-140">When you select Default, the operating system determines the actual log location.</span></span> <span data-ttu-id="c493a-141">このトピックの「アプリケーションまたはセキュリティ イベント ログの選択」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c493a-141">See the "Application or Security Event Log Choice" section later in this topic.</span></span>|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|<span data-ttu-id="c493a-142">メッセージ レベルで監査されるメッセージ認証イベントの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="c493a-142">Specifies which types of message authentication events are audited at the message level.</span></span> <span data-ttu-id="c493a-143">`None`、`Failure`、`Success` および `SuccessOrFailure` から選択できます。</span><span class="sxs-lookup"><span data-stu-id="c493a-143">The choices are `None`, `Failure`, `Success`, and `SuccessOrFailure`.</span></span>|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|<span data-ttu-id="c493a-144">サービス レベルで監査されるサービス承認イベントの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="c493a-144">Specifies which types of service authorization events are audited at the service level.</span></span> <span data-ttu-id="c493a-145">`None`、`Failure`、`Success` および `SuccessOrFailure` から選択できます。</span><span class="sxs-lookup"><span data-stu-id="c493a-145">The choices are `None`, `Failure`, `Success`, and `SuccessOrFailure`.</span></span>|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|<span data-ttu-id="c493a-146">監査が失敗した場合に、クライアント要求をどのように処理するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c493a-146">Specifies what happens to the client request when auditing fails.</span></span> <span data-ttu-id="c493a-147">たとえば、`SeAuditPrivilege` を持たないサービスがセキュリティ ログへの書き込みを試行したとします。</span><span class="sxs-lookup"><span data-stu-id="c493a-147">For example, when the service attempts to write to the security log, but does not have `SeAuditPrivilege`.</span></span> <span data-ttu-id="c493a-148">この場合、既定値の `true` が設定されていると、エラーは無視され、クライアント要求は正常に処理されます。</span><span class="sxs-lookup"><span data-stu-id="c493a-148">The default value of `true` indicates that failures are ignored, and the client request is processed normally.</span></span>|  
  
 <span data-ttu-id="c493a-149">監査イベントをログに記録するようにアプリケーションを設定する例については、「 [方法: セキュリティイベントを監査](how-to-audit-wcf-security-events.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c493a-149">For an example of setting up an application to log audit events, see [How to: Audit Security Events](how-to-audit-wcf-security-events.md).</span></span>  
  
### <a name="configuration"></a><span data-ttu-id="c493a-150">構成</span><span class="sxs-lookup"><span data-stu-id="c493a-150">Configuration</span></span>  

 <span data-ttu-id="c493a-151">構成を使用して、の下にを追加することによって監査の動作を指定することもでき [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) ます。</span><span class="sxs-lookup"><span data-stu-id="c493a-151">You can also use configuration to specify auditing behavior by adding a [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) under the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md).</span></span> <span data-ttu-id="c493a-152">次のコードに示すように、の下に要素を追加する必要があり [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ます。</span><span class="sxs-lookup"><span data-stu-id="c493a-152">You must add the element under a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) as shown in the following code.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <behavior>  
        <!-- auditLogLocation="Application" or "Security" -->  
        <serviceSecurityAudit  
                  auditLogLocation="Application"  
                  suppressAuditFailure="true"  
                  serviceAuthorizationAuditLevel="Failure"  
                  messageAuthenticationAuditLevel="SuccessOrFailure" />
      </behavior>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="c493a-153">監査が有効になっているが、`auditLogLocation` が指定されていない場合、セキュリティ ログへの書き込みをサポートしているプラットフォームでの既定のログ名は "セキュリティ" ログになります。それ以外の場合は、"アプリケーション" ログになります。</span><span class="sxs-lookup"><span data-stu-id="c493a-153">If auditing is enabled and an `auditLogLocation` is not specified, the default log name is "Security" log for the platform supporting writing to the Security log; otherwise, it is "Application" log.</span></span> <span data-ttu-id="c493a-154">セキュリティログへの書き込みをサポートしているのは、Windows Server 2003 および Windows Vista オペレーティングシステムだけです。</span><span class="sxs-lookup"><span data-stu-id="c493a-154">Only the Windows Server 2003 and Windows Vista operating systems support writing to the Security log.</span></span> <span data-ttu-id="c493a-155">詳細については、このトピックで後述する「オペレーティングシステム」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c493a-155">For more information, see the "Operating System" section later in this topic.</span></span>  
  
## <a name="security-considerations"></a><span data-ttu-id="c493a-156">セキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="c493a-156">Security Considerations</span></span>  

 <span data-ttu-id="c493a-157">監査が有効になっていることが悪意のあるユーザーに知られた場合、そのユーザーは監査エントリの書き込みにつながる無効なメッセージを送信する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c493a-157">If a malicious user knows that auditing is enabled, that attacker can send invalid messages that cause audit entries to be written.</span></span> <span data-ttu-id="c493a-158">このような方法で監査ログに書き込みが行われると、監査システムに障害が発生します。</span><span class="sxs-lookup"><span data-stu-id="c493a-158">If the audit log is filled in this manner, the auditing system fails.</span></span> <span data-ttu-id="c493a-159">これを防ぐには、<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> プロパティを `true` に設定し、イベント ビューアーのプロパティを使用して監査動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="c493a-159">To mitigate this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to `true` and use the properties of the Event Viewer to control the auditing behavior.</span></span>  
  
 <span data-ttu-id="c493a-160">Windows XP 上のアプリケーションログに書き込まれる監査イベントは、認証されたユーザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c493a-160">Audit events that are written to the Application Log on Windows XP are visible to any authenticated user.</span></span>  
  
## <a name="choosing-between-application-and-security-event-logs"></a><span data-ttu-id="c493a-161">アプリケーションまたはセキュリティ イベント ログの選択</span><span class="sxs-lookup"><span data-stu-id="c493a-161">Choosing Between Application and Security Event Logs</span></span>  

 <span data-ttu-id="c493a-162">アプリケーション イベント ログとセキュリティ イベント ログのどちらにログを記録するかを選択するには、次の表の情報を参考にしてください。</span><span class="sxs-lookup"><span data-stu-id="c493a-162">The following tables provide information to help you choose whether to log into the Application or the Security event log.</span></span>  
  
#### <a name="operating-system"></a><span data-ttu-id="c493a-163">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="c493a-163">Operating System</span></span>  
  
|<span data-ttu-id="c493a-164">システム</span><span class="sxs-lookup"><span data-stu-id="c493a-164">System</span></span>|<span data-ttu-id="c493a-165">アプリケーション ログ</span><span class="sxs-lookup"><span data-stu-id="c493a-165">Application log</span></span>|<span data-ttu-id="c493a-166">Security log</span><span class="sxs-lookup"><span data-stu-id="c493a-166">Security log</span></span>|  
|------------|---------------------|------------------|  
|<span data-ttu-id="c493a-167">Windows XP SP2 以降</span><span class="sxs-lookup"><span data-stu-id="c493a-167">Windows XP SP2 or later</span></span>|<span data-ttu-id="c493a-168">サポートされています</span><span class="sxs-lookup"><span data-stu-id="c493a-168">Supported</span></span>|<span data-ttu-id="c493a-169">サポートされていません</span><span class="sxs-lookup"><span data-stu-id="c493a-169">Not supported</span></span>|  
|<span data-ttu-id="c493a-170">Windows Server 2003 SP1 および Windows Vista</span><span class="sxs-lookup"><span data-stu-id="c493a-170">Windows Server 2003 SP1 and Windows Vista</span></span>|<span data-ttu-id="c493a-171">サポートされています</span><span class="sxs-lookup"><span data-stu-id="c493a-171">Supported</span></span>|<span data-ttu-id="c493a-172">スレッド コンテキストが `SeAuditPrivilege` を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="c493a-172">Thread context must possess `SeAuditPrivilege`</span></span>|  
  
#### <a name="other-factors"></a><span data-ttu-id="c493a-173">その他の要素</span><span class="sxs-lookup"><span data-stu-id="c493a-173">Other Factors</span></span>  

 <span data-ttu-id="c493a-174">オペレーティング システム以外に、ログ記録の使用可能性を制御する設定を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="c493a-174">In addition to the operating system, the following table describes other settings that control the enablement of logging.</span></span>  
  
|<span data-ttu-id="c493a-175">要素</span><span class="sxs-lookup"><span data-stu-id="c493a-175">Factor</span></span>|<span data-ttu-id="c493a-176">アプリケーション ログ</span><span class="sxs-lookup"><span data-stu-id="c493a-176">Application log</span></span>|<span data-ttu-id="c493a-177">Security log</span><span class="sxs-lookup"><span data-stu-id="c493a-177">Security log</span></span>|  
|------------|---------------------|------------------|  
|<span data-ttu-id="c493a-178">監査ポリシーの監査</span><span class="sxs-lookup"><span data-stu-id="c493a-178">Audit policy management</span></span>|<span data-ttu-id="c493a-179">適用不可。</span><span class="sxs-lookup"><span data-stu-id="c493a-179">Not applicable.</span></span>|<span data-ttu-id="c493a-180">セキュリティ ログは、構成だけでなく、ローカル セキュリティ機関 (LSA: Local Security Authority) ポリシーによっても制御されます。</span><span class="sxs-lookup"><span data-stu-id="c493a-180">Along with configuration, the Security log is also controlled by the local security authority (LSA) policy.</span></span> <span data-ttu-id="c493a-181">[オブジェクト アクセスの監査] カテゴリも有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c493a-181">The "Audit object access" category must also be enabled.</span></span>|  
|<span data-ttu-id="c493a-182">既定のユーザー エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="c493a-182">Default user experience</span></span>|<span data-ttu-id="c493a-183">すべての認証済みユーザーがアプリケーション ログに書き込むことができるため、アプリケーション プロセスでは追加のアクセス許可手順は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="c493a-183">All authenticated users can write to the Application log, so no additional permission step is needed for application processes.</span></span>|<span data-ttu-id="c493a-184">アプリケーション プロセス (コンテキスト) が `SeAuditPrivilege` を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="c493a-184">The application process (context) must have `SeAuditPrivilege`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c493a-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="c493a-185">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [<span data-ttu-id="c493a-186">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="c493a-186">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="c493a-187">基本的な WCF プログラミング</span><span class="sxs-lookup"><span data-stu-id="c493a-187">Basic WCF Programming</span></span>](../basic-wcf-programming.md)
- [<span data-ttu-id="c493a-188">方法: セキュリティ イベントを監査する</span><span class="sxs-lookup"><span data-stu-id="c493a-188">How to: Audit Security Events</span></span>](how-to-audit-wcf-security-events.md)
- [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md)
- [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md)
- <span data-ttu-id="c493a-189">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c493a-189">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
