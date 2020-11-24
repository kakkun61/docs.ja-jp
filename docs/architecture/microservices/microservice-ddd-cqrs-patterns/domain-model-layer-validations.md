---
title: ドメイン モデル レイヤーでの検証の設計
description: コンテナー化された .NET アプリケーション用の .NET マイクロサービス アーキテクチャ | ドメイン モデル検証の主要な概念を理解する。
ms.date: 10/08/2018
ms.openlocfilehash: 18c8350d0bf514a8a01a210a2a2a6d8f73317580
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820632"
---
# <a name="design-validations-in-the-domain-model-layer"></a><span data-ttu-id="0d759-103">ドメイン モデル レイヤーでの検証を設計する</span><span class="sxs-lookup"><span data-stu-id="0d759-103">Design validations in the domain model layer</span></span>

<span data-ttu-id="0d759-104">DDD では、検証ルールは不変条件として考えることができます。</span><span class="sxs-lookup"><span data-stu-id="0d759-104">In DDD, validation rules can be thought as invariants.</span></span> <span data-ttu-id="0d759-105">集計の主な役割は、その集計内のすべてのエンティティの状態の変更にわたってインバリアントを強制することです。</span><span class="sxs-lookup"><span data-stu-id="0d759-105">The main responsibility of an aggregate is to enforce invariants across state changes for all the entities within that aggregate.</span></span>

<span data-ttu-id="0d759-106">ドメイン エンティティは、常に有効なエンティティである必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d759-106">Domain entities should always be valid entities.</span></span> <span data-ttu-id="0d759-107">常に true にする必要のあるオブジェクトには、特定のインバリアント数があります。</span><span class="sxs-lookup"><span data-stu-id="0d759-107">There are a certain number of invariants for an object that should always be true.</span></span> <span data-ttu-id="0d759-108">たとえば、order item オブジェクトは、正の整数である必要がある数量と、アーティクル名および価格を常に持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d759-108">For example, an order item object always has to have a quantity that must be a positive integer, plus an article name and price.</span></span> <span data-ttu-id="0d759-109">そのため、インバリアントの強制は、(特に集計ルートの) ドメイン エンティティの役目となり、エンティティ オブジェクトは有効になっていない限り存在できません。</span><span class="sxs-lookup"><span data-stu-id="0d759-109">Therefore, invariants enforcement is the responsibility of the domain entities (especially of the aggregate root) and an entity object should not be able to exist without being valid.</span></span> <span data-ttu-id="0d759-110">インバリアント ルールは、コントラクトとして単純に表され、違反があった場合には例外または通知が発生します。</span><span class="sxs-lookup"><span data-stu-id="0d759-110">Invariant rules are simply expressed as contracts, and exceptions or notifications are raised when they are violated.</span></span>

<span data-ttu-id="0d759-111">この背後にある理由は、オブジェクトがなってはならない状態にあるため、多くのバグが発生するからです。</span><span class="sxs-lookup"><span data-stu-id="0d759-111">The reasoning behind this is that many bugs occur because objects are in a state they should never have been in.</span></span>

<span data-ttu-id="0d759-112">UserProfile を受け取る SendUserCreationEmailService があるとします。Name が null でないそのサービスでどのように合理化できるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="0d759-112">Let's propose we now have a SendUserCreationEmailService that takes a UserProfile ... how can we rationalize in that service that Name is not null?</span></span> <span data-ttu-id="0d759-113">再度チェックしますか。</span><span class="sxs-lookup"><span data-stu-id="0d759-113">Do we check it again?</span></span> <span data-ttu-id="0d759-114">多くの場合、わざわざチェックなどせずに、他の誰かが検証してから自分に送信してくれる "最善の結果を期待" しているのではないでしょうか。</span><span class="sxs-lookup"><span data-stu-id="0d759-114">Or more likely ... you just don't bother to check and "hope for the best"—you hope that someone bothered to validate it before sending it to you.</span></span> <span data-ttu-id="0d759-115">もちろん、記述すべき最初のテストのうちの 1 つである TDD を使用すると、null 名を持つ顧客を送信した場合に、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="0d759-115">Of course, using TDD one of the first tests we should be writing is that if I send a customer with a null name that it should raise an error.</span></span> <span data-ttu-id="0d759-116">しかし、この種のテストを繰り返し記述しているうちに、"名前が null になることを許可しなかったら、これらのテストのすべては必要ないのではないか" ということに気が付きました。</span><span class="sxs-lookup"><span data-stu-id="0d759-116">But once we start writing these kinds of tests over and over again we realize ... "wait if we never allowed name to become null we wouldn't have all of these tests".</span></span>

## <a name="implement-validations-in-the-domain-model-layer"></a><span data-ttu-id="0d759-117">ドメイン モデル レイヤーでの検証を実装する</span><span class="sxs-lookup"><span data-stu-id="0d759-117">Implement validations in the domain model layer</span></span>

<span data-ttu-id="0d759-118">検証は通常、ドメイン エンティティ コンストラクター内、またはエンティティを更新できるメソッドに実装されます。</span><span class="sxs-lookup"><span data-stu-id="0d759-118">Validations are usually implemented in domain entity constructors or in methods that can update the entity.</span></span> <span data-ttu-id="0d759-119">検証を実装するには、データを検証し、検証が失敗した場合に例外を発生させるといった、複数の方法があります。</span><span class="sxs-lookup"><span data-stu-id="0d759-119">There are multiple ways to implement validations, such as verifying data and raising exceptions if the validation fails.</span></span> <span data-ttu-id="0d759-120">検証に使用する仕様パターンや、例外が発生すると、検証ごとに例外を返すのではなく、エラーのコレクションを返す通知パターンのような、より高度なパターンもあります。</span><span class="sxs-lookup"><span data-stu-id="0d759-120">There are also more advanced patterns such as using the Specification pattern for validations, and the Notification pattern to return a collection of errors instead of returning an exception for each validation as it occurs.</span></span>

### <a name="validate-conditions-and-throw-exceptions"></a><span data-ttu-id="0d759-121">条件を検証して例外をスローする</span><span class="sxs-lookup"><span data-stu-id="0d759-121">Validate conditions and throw exceptions</span></span>

<span data-ttu-id="0d759-122">次のコード例は、例外を発生させることによってドメイン エンティティで検証するための最も簡単な方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="0d759-122">The following code example shows the simplest approach to validation in a domain entity by raising an exception.</span></span> <span data-ttu-id="0d759-123">このセクションの最後にある参照テーブルには、前述したパターンに基づくより高度な実装へのリンクがあります。</span><span class="sxs-lookup"><span data-stu-id="0d759-123">In the references table at the end of this section you can see links to more advanced implementations based on the patterns we have discussed previously.</span></span>

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

<span data-ttu-id="0d759-124">さらによい例は、内部状態が変わっていないか、メソッドのすべての変更が発生したことを確認する必要を示すものでしょう。</span><span class="sxs-lookup"><span data-stu-id="0d759-124">A better example would demonstrate the need to ensure that either the internal state did not change, or that all the mutations for a method occurred.</span></span> <span data-ttu-id="0d759-125">たとえば、次の実装では、オブジェクトが無効な状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="0d759-125">For example, the following implementation would leave the object in an invalid state:</span></span>

```csharp
public void SetAddress(string line1, string line2,
    string city, string state, int zip)
{
    _shippingAddress.line1 = line1 ?? throw new ...
    _shippingAddress.line2 = line2;
    _shippingAddress.city = city ?? throw new ...
    _shippingAddress.state = (IsValid(state) ? state : throw new …);
}
```

<span data-ttu-id="0d759-126">状態の値が無効な場合は、address の最初の行と city が既に変更されています。</span><span class="sxs-lookup"><span data-stu-id="0d759-126">If the value of the state is invalid, the first address line and the city have already been changed.</span></span> <span data-ttu-id="0d759-127">address が無効になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0d759-127">That might make the address invalid.</span></span>

<span data-ttu-id="0d759-128">同様の方法は、エンティティのコンストラクターで、エンティティの作成後、例外を発生させてそのエンティティが有効であることを確認するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="0d759-128">A similar approach can be used in the entity's constructor, raising an exception to make sure that the entity is valid once it is created.</span></span>

### <a name="use-validation-attributes-in-the-model-based-on-data-annotations"></a><span data-ttu-id="0d759-129">データ注釈に基づいてモデルで検証属性を使用する</span><span class="sxs-lookup"><span data-stu-id="0d759-129">Use validation attributes in the model based on data annotations</span></span>

<span data-ttu-id="0d759-130">Required 属性や MaxLength 属性のようなデータ注釈を使用すると、「[テーブル マッピング](infrastructure-persistence-layer-implementation-entity-framework-core.md#table-mapping)」セクションで詳述したように、EF Core データベースのフィールド プロパティを構成することができます。しかし、.NET Framework の EF 4.x 以降に行われているので、[それらは EF Core でのエンティティ検証では機能しなくなりました](https://github.com/dotnet/efcore/issues/3680) (<xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> メソッドも機能しません)。</span><span class="sxs-lookup"><span data-stu-id="0d759-130">Data annotations, like the Required or MaxLength attributes, can be used to configure EF Core database field properties, as explained in detail in the [Table mapping](infrastructure-persistence-layer-implementation-entity-framework-core.md#table-mapping) section, but [they no longer work for entity validation in EF Core](https://github.com/dotnet/efcore/issues/3680) (neither does the <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> method), as they have done since EF 4.x in .NET Framework.</span></span>

<span data-ttu-id="0d759-131">コントローラーの通常どおりのアクション呼び出しの前に行われるモデル バインディングの際にモデル検証で、データ注釈と <xref:System.ComponentModel.DataAnnotations.IValidatableObject> インターフェイスを引き続き使用することができます。しかし、そのモデルは ViewModel または DTO であることを前提としており、それはドメイン モデルに関する問題ではなく、MVC または API に関する問題です。</span><span class="sxs-lookup"><span data-stu-id="0d759-131">Data annotations and the <xref:System.ComponentModel.DataAnnotations.IValidatableObject> interface can still be used for model validation during model binding, prior to the controller's actions invocation as usual, but that model is meant to be a ViewModel or DTO and that's an MVC or API concern not a domain model concern.</span></span>

<span data-ttu-id="0d759-132">概念の違いが明らかにされていれば、ご利用のアクションで非推奨のエンティティ クラス オブジェクトが受信される場合に、検証用のエンティティ クラス内でデータ注釈と `IValidatableObject` を引き続き使用することができます。</span><span class="sxs-lookup"><span data-stu-id="0d759-132">Having made the conceptual difference clear, you can still use data annotations and `IValidatableObject` in the entity class for validation, if your actions receive an entity class object parameter, which is not recommended.</span></span> <span data-ttu-id="0d759-133">その場合、アクションが呼び出されるすぐ前に行われるモデル バインディングの際に検証は実行されるので、コントローラーの ModelState.IsValid プロパティを調べてその結果を確認することができます。ただし、繰り返しになりますが、それはコントローラー内で実行され、実行されるのは DbContext 内にエンティティ オブジェクトが保持される前ではありません。それは EF 4.x 以降に行われているからです。</span><span class="sxs-lookup"><span data-stu-id="0d759-133">In that case, validation will occur upon model binding, just before invoking the action and you can check the controller's ModelState.IsValid property to check the result, but then again, it happens in the controller, not before persisting the entity object in the DbContext, as it had done since EF 4.x.</span></span>

<span data-ttu-id="0d759-134">DbContext の SaveChanges メソッドをオーバーライドすれば、データ注釈と `IValidatableObject.Validate` メソッドを使用してエンティティ クラスにカスタム検証を引き続き実装することができます。</span><span class="sxs-lookup"><span data-stu-id="0d759-134">You can still implement custom validation in the entity class using data annotations and the `IValidatableObject.Validate` method, by overriding the DbContext's SaveChanges method.</span></span>

<span data-ttu-id="0d759-135">`IValidatableObject` エンティティを検証するための実装のサンプルについては、[GitHub 上のこちらのコメント](https://github.com/dotnet/efcore/issues/3680#issuecomment-155502539)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d759-135">You can see a sample implementation for validating `IValidatableObject` entities in [this comment on GitHub](https://github.com/dotnet/efcore/issues/3680#issuecomment-155502539).</span></span> <span data-ttu-id="0d759-136">そのサンプルでは属性ベースの検証は行われていません。その検証については、同じオーバーライド内でリフレクションを使用することで容易に実装できるはずです。</span><span class="sxs-lookup"><span data-stu-id="0d759-136">That sample doesn't do attribute-based validations, but they should be easy to implement using reflection in the same override.</span></span>

<span data-ttu-id="0d759-137">ただし、DDD の観点から、ドメイン モデルはエンティティの動作メソッド内の例外を使用して、または検証規則を強制する仕様パターンと通知パターンを実装することで、リーンに保つことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0d759-137">However, from a DDD point of view, the domain model is best kept lean with the use of exceptions in your entity's behavior methods, or by implementing the Specification and Notification patterns to enforce validation rules.</span></span>

<span data-ttu-id="0d759-138">UI 層内でモデルの検証を許可するために、入力を受け取る ViewModel クラス内 (ドメイン エンティティではなく) のアプリケーション層でデータ注釈を使用するのは合理的です。</span><span class="sxs-lookup"><span data-stu-id="0d759-138">It can make sense to use data annotations at the application layer in ViewModel classes (instead of domain entities) that will accept input, to allow for model validation within the UI layer.</span></span> <span data-ttu-id="0d759-139">ただし、ドメイン モデル内での検証の実行時にはこれを行わないでください。</span><span class="sxs-lookup"><span data-stu-id="0d759-139">However, this should not be done at the exclusion of validation within the domain model.</span></span>

### <a name="validate-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a><span data-ttu-id="0d759-140">仕様パターンと通知パターンを実装することでエンティティを検証する</span><span class="sxs-lookup"><span data-stu-id="0d759-140">Validate entities by implementing the Specification pattern and the Notification pattern</span></span>

<span data-ttu-id="0d759-141">最後に、ドメイン モデルで検証を実装するより複雑な方法は、後述するその他の技術情報の一部で説明されているように、仕様パターンと通知パターンを組み合わせて実装することです。</span><span class="sxs-lookup"><span data-stu-id="0d759-141">Finally, a more elaborate approach to implementing validations in the domain model is by implementing the Specification pattern in conjunction with the Notification pattern, as explained in some of the additional resources listed later.</span></span>

<span data-ttu-id="0d759-142">これらのパターンの 1 つだけを使用することもできます。たとえば、コントロール ステートメントを使用して手動で検証していますが、検証エラーの一覧をスタックして返すには通知パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="0d759-142">It is worth mentioning that you can also use just one of those patterns—for example, validating manually with control statements, but using the Notification pattern to stack and return a list of validation errors.</span></span>

### <a name="use-deferred-validation-in-the-domain"></a><span data-ttu-id="0d759-143">ドメインで遅延検証を使用する</span><span class="sxs-lookup"><span data-stu-id="0d759-143">Use deferred validation in the domain</span></span>

<span data-ttu-id="0d759-144">ドメインで遅延検証に対処するには、さまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="0d759-144">There are various approaches to deal with deferred validations in the domain.</span></span> <span data-ttu-id="0d759-145">Vaughn Vernon 氏は自身の著書『[Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)』で、検証に関するセクションでこれらについて説明しています。</span><span class="sxs-lookup"><span data-stu-id="0d759-145">In his book [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discusses these in the section on validation.</span></span>

### <a name="two-step-validation"></a><span data-ttu-id="0d759-146">2 段階検証</span><span class="sxs-lookup"><span data-stu-id="0d759-146">Two-step validation</span></span>

<span data-ttu-id="0d759-147">2 段階検証も検討してください。</span><span class="sxs-lookup"><span data-stu-id="0d759-147">Also consider two-step validation.</span></span> <span data-ttu-id="0d759-148">データ転送オブジェクト (DTO) コマンドにはフィールド レベルの検証を使用し、エンティティ内にはドメイン レベルの検証を使用します。</span><span class="sxs-lookup"><span data-stu-id="0d759-148">Use field-level validation on your command Data Transfer Objects (DTOs) and domain-level validation inside your entities.</span></span> <span data-ttu-id="0d759-149">検証エラーを処理しやすくするために、例外の代わりに結果オブジェクトを返すことで、これを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="0d759-149">You can do this by returning a result object instead of exceptions in order to make it easier to deal with the validation errors.</span></span>

<span data-ttu-id="0d759-150">たとえば、データ注釈を使用したフィールドの検証を使用している場合、検証定義を複製しないでください。</span><span class="sxs-lookup"><span data-stu-id="0d759-150">Using field validation with data annotations, for example, you do not duplicate the validation definition.</span></span> <span data-ttu-id="0d759-151">ただし、DTO の場合、実行はサーバー側とクライアント側の両方で可能です (たとえば、コマンドと ViewModels)。</span><span class="sxs-lookup"><span data-stu-id="0d759-151">The execution, though, can be both server-side and client-side in the case of DTOs (commands and ViewModels, for instance).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0d759-152">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="0d759-152">Additional resources</span></span>

- <span data-ttu-id="0d759-153">**Rachel Appel。ASP.NET Core MVC でのモデル検証の概要** </span><span class="sxs-lookup"><span data-stu-id="0d759-153">**Rachel Appel. Introduction to model validation in ASP.NET Core MVC** </span></span>\
  <https://docs.microsoft.com/aspnet/core/mvc/models/validation>

- <span data-ttu-id="0d759-154">**Rick Anderson の 検証の追加** </span><span class="sxs-lookup"><span data-stu-id="0d759-154">**Rick Anderson. Adding validation** </span></span>\
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

- <span data-ttu-id="0d759-155">**Martin Fowler。検証で例外のスローを通知に置き換える** </span><span class="sxs-lookup"><span data-stu-id="0d759-155">**Martin Fowler. Replacing Throwing Exceptions with Notification in Validations** </span></span>\
  <https://martinfowler.com/articles/replaceThrowWithNotification.html>

- <span data-ttu-id="0d759-156">**仕様と通知のパターン** </span><span class="sxs-lookup"><span data-stu-id="0d759-156">**Specification and Notification Patterns** </span></span>\
  <https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns>

- <span data-ttu-id="0d759-157">**Lev Gorodinski。ドメイン駆動設計 (DDD) での検証** </span><span class="sxs-lookup"><span data-stu-id="0d759-157">**Lev Gorodinski. Validation in Domain-Driven Design (DDD)** </span></span>\
  <http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/>

- <span data-ttu-id="0d759-158">**Colin Jack。ドメイン モデルの検証** </span><span class="sxs-lookup"><span data-stu-id="0d759-158">**Colin Jack. Domain Model Validation** </span></span>\
  <https://colinjack.blogspot.com/2008/03/domain-model-validation.html>

- <span data-ttu-id="0d759-159">**Jimmy Bogard。DDD 世界での検証** </span><span class="sxs-lookup"><span data-stu-id="0d759-159">**Jimmy Bogard. Validation in a DDD world** </span></span>\
  <https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/>

> [!div class="step-by-step"]
> <span data-ttu-id="0d759-160">[前へ](enumeration-classes-over-enum-types.md)
> [次へ](client-side-validation.md)</span><span class="sxs-lookup"><span data-stu-id="0d759-160">[Previous](enumeration-classes-over-enum-types.md)
[Next](client-side-validation.md)</span></span>
