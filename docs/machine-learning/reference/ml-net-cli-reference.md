---
title: ML.NET CLI コマンド リファレンス
description: ML.NET CLI ツールの auto-train コマンドの概要、サンプル、およびリファレンス。
ms.date: 06/03/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 6f07cd8b4237f8931bbc0ec97bc0bbe18c488f16
ms.sourcegitcommit: e395fabeeea5c705d243d246fa64446839ac85b6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/03/2021
ms.locfileid: "97856069"
---
# <a name="the-mlnet-cli-command-reference"></a><span data-ttu-id="d188f-103">ML.NET CLI コマンド リファレンス</span><span class="sxs-lookup"><span data-stu-id="d188f-103">The ML.NET CLI command reference</span></span>

<span data-ttu-id="d188f-104">`classification`、`regression`、`recommendation` コマンドは、ML.NET CLI ツールによって提供されるメイン コマンドです。</span><span class="sxs-lookup"><span data-stu-id="d188f-104">The `classification`, `regression`, and `recommendation` commands are the main commands provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="d188f-105">このコマンドを使用すると、自動機械学習 (AutoML) を使用する分類、回帰、推奨モデル用の高品質の ML.NET モデルと、そのモデルを実行またはスコア付けする C# のコード例を生成できます。</span><span class="sxs-lookup"><span data-stu-id="d188f-105">These commands allow you to generate good quality ML.NET models for classification, regression, and recommendation models using automated machine learning (AutoML) as well as the example C# code to run/score that model.</span></span> <span data-ttu-id="d188f-106">さらに、そのモデルをトレーニングするための C# コードも生成され、そのモデルのアルゴリズムと設定を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="d188f-106">In addition, the C# code to train the model is generated for you to research the algorithm and settings of the model.</span></span>

> [!NOTE]
> <span data-ttu-id="d188f-107">このトピックは、現在プレビュー段階の ML.NET CLI と ML.NET AutoML について述べており、内容が変更される場合があります。</span><span class="sxs-lookup"><span data-stu-id="d188f-107">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="overview"></a><span data-ttu-id="d188f-108">概要</span><span class="sxs-lookup"><span data-stu-id="d188f-108">Overview</span></span>

<span data-ttu-id="d188f-109">使用例:</span><span class="sxs-lookup"><span data-stu-id="d188f-109">Example usage:</span></span>

```console
mlnet regression --dataset "cars.csv" --label-col price
```

<span data-ttu-id="d188f-110">`mlnet` ML タスク コマンド (`classification`、`regression`、`recommendation`) では、次の資産が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d188f-110">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) generate the following assets:</span></span>

- <span data-ttu-id="d188f-111">すぐに使用できるシリアル化されたモデル .zip ("最適なモデル")。</span><span class="sxs-lookup"><span data-stu-id="d188f-111">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="d188f-112">その生成されたモデルを実行/スコア付けする C# コード。</span><span class="sxs-lookup"><span data-stu-id="d188f-112">C# code to run/score that generated model.</span></span>
- <span data-ttu-id="d188f-113">そのモデルの生成に使用されるトレーニング コードを含む C# コード。</span><span class="sxs-lookup"><span data-stu-id="d188f-113">C# code with the training code used to generate that model.</span></span>

<span data-ttu-id="d188f-114">最初の 2 つの資産は、モデルを使用して予測を行うために、エンド ユーザー アプリ (ASP.NET Core Web アプリ、サービス、デスクトップ アプリなど) で直接使用できます。</span><span class="sxs-lookup"><span data-stu-id="d188f-114">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app and more) to make predictions with the model.</span></span>

<span data-ttu-id="d188f-115">3 つ目の資産のトレーニング コードは、生成されたモデルをトレーニングするために CLI によって使用された ML.NET API コードを示しています。このため、そのモデルの特定のアルゴリズムと設定を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="d188f-115">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate the specific algorithm and settings of the model.</span></span>

## <a name="examples"></a><span data-ttu-id="d188f-116">使用例</span><span class="sxs-lookup"><span data-stu-id="d188f-116">Examples</span></span>

<span data-ttu-id="d188f-117">分類問題に適した最も簡単な CLI コマンド (AutoML では、指定されたデータからほとんどの構成が推測されます):</span><span class="sxs-lookup"><span data-stu-id="d188f-117">The simplest CLI command for a classification problem (AutoML infers most of the configuration from the provided data):</span></span>

```console
mlnet classification --dataset "customer-feedback.tsv" --label-col Sentiment
```

<span data-ttu-id="d188f-118">回帰問題に適したもう 1 つの簡単な CLI コマンド:</span><span class="sxs-lookup"><span data-stu-id="d188f-118">Another simple CLI command for a regression problem:</span></span>

``` console
mlnet regression --dataset "cars.csv" --label-col Price
```

<span data-ttu-id="d188f-119">トレーニング データセット、テスト データセット、その他のカスタマイズの明示的な引数を使用して、分類モデルを作成し、トレーニングします。</span><span class="sxs-lookup"><span data-stu-id="d188f-119">Create and train a classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
mlnet classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-col "InsuranceRisk" --cache on --train-time 600
```

## <a name="command-options"></a><span data-ttu-id="d188f-120">コマンド オプション</span><span class="sxs-lookup"><span data-stu-id="d188f-120">Command options</span></span>

<span data-ttu-id="d188f-121">`mlnet` ML タスク コマンド (`classification`、`regression`、`recommendation`) によって、指定されたデータセットと ML.NET CLI オプションに基づいて複数のモデルがトレーニングされます。</span><span class="sxs-lookup"><span data-stu-id="d188f-121">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) train multiple models based on the provided dataset and ML.NET CLI options.</span></span> <span data-ttu-id="d188f-122">これらのコマンドから、最適なモデルの選択、シリアル化された .zip ファイルとしてのモデルの保存、スコア付けとトレーニングを行うための C# の関連コードの生成を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="d188f-122">These commands also select the best model, save the model as a serialized .zip file, and generate related C# code for scoring and training.</span></span>

### <a name="classification-options"></a><span data-ttu-id="d188f-123">分類オプション</span><span class="sxs-lookup"><span data-stu-id="d188f-123">Classification options</span></span>

<span data-ttu-id="d188f-124">`mlnet classification` を実行すると、分類モデルがトレーニングされます。</span><span class="sxs-lookup"><span data-stu-id="d188f-124">Running `mlnet classification` will train a classification model.</span></span> <span data-ttu-id="d188f-125">ML モデルでデータを 2 つ以上のクラスに分類する場合 (例: 感情分析) は、このコマンドを選択します。</span><span class="sxs-lookup"><span data-stu-id="d188f-125">Choose this command if you want an ML Model to categorize data into 2 or more classes (e.g. sentiment analysis).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="regression-options"></a><span data-ttu-id="d188f-126">回帰オプション</span><span class="sxs-lookup"><span data-stu-id="d188f-126">Regression options</span></span>

<span data-ttu-id="d188f-127">`mlnet regression` を実行すると、回帰モデルがトレーニングされます。</span><span class="sxs-lookup"><span data-stu-id="d188f-127">Running `mlnet regression` will train a regression model.</span></span> <span data-ttu-id="d188f-128">ML モデルで数値を予測する場合 (例: 価格予測) は、このコマンドを選択します。</span><span class="sxs-lookup"><span data-stu-id="d188f-128">Choose this command if you want an ML Model to predict a numeric value (e.g. price prediction).</span></span>

```console
mlnet regression

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="recommendation-options"></a><span data-ttu-id="d188f-129">推奨オプション</span><span class="sxs-lookup"><span data-stu-id="d188f-129">Recommendation options</span></span>

<span data-ttu-id="d188f-130">`mlnet recommendation` を実行すると、推奨モデルがトレーニングされます。</span><span class="sxs-lookup"><span data-stu-id="d188f-130">Running `mlnet recommendation` will train a recommendation model.</span></span>  <span data-ttu-id="d188f-131">ML モデルで評価に基づいてユーザーに項目を推奨する場合 (例: 製品推奨) は、このコマンドを選択します。</span><span class="sxs-lookup"><span data-stu-id="d188f-131">Choose this command if you want an ML Model to recommend items to users based on ratings (e.g. product recommendation).</span></span>

```console
mlnet recommendation

--dataset <path> (REQUIRED)

--item-col <col> (REQUIRED)

--rating-col <col> (REQUIRED)

--user-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

<span data-ttu-id="d188f-132">無効な入力オプションを指定すると、CLI ツールによって、有効な入力の一覧とエラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="d188f-132">Invalid input options cause the CLI tool to emit a list of valid inputs and an error message.</span></span>

## <a name="dataset"></a><span data-ttu-id="d188f-133">データセット</span><span class="sxs-lookup"><span data-stu-id="d188f-133">Dataset</span></span>

<span data-ttu-id="d188f-134">`--dataset | -d` (文字列)</span><span class="sxs-lookup"><span data-stu-id="d188f-134">`--dataset | -d` (string)</span></span>

<span data-ttu-id="d188f-135">この引数には、次のオプションのいずれかのファイルパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="d188f-135">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="d188f-136">*A:データセット ファイル全体:* このオプションを使用し、ユーザーが `--test-dataset` と `--validation-dataset` を指定していない場合は、モデルの検証にクロス検証 (k 分割など) または自動データ分割アプローチが内部的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d188f-136">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="d188f-137">その場合、ユーザーはデータセットのファイルパスを入力するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="d188f-137">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="d188f-138">*B:トレーニング データセット ファイル:* ユーザーがモデル検証用のデータセットも指定している場合 (`--test-dataset` と、必要に応じて `--validation-dataset` を使用)、`--dataset` 引数は "トレーニング データセット" のみがあることを意味します。</span><span class="sxs-lookup"><span data-stu-id="d188f-138">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="d188f-139">たとえば、80% - 20% のアプローチを使用してモデルの品質を検証し、正確度のメトリックを取得する場合、"トレーニング データセット" には 80% のデータが含まれ、"テスト データセット" には 20% のデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d188f-139">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

## <a name="test-dataset"></a><span data-ttu-id="d188f-140">テスト データセット</span><span class="sxs-lookup"><span data-stu-id="d188f-140">Test dataset</span></span>

<span data-ttu-id="d188f-141">`--test-dataset | -t` (文字列)</span><span class="sxs-lookup"><span data-stu-id="d188f-141">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="d188f-142">テスト データセット ファイルを指すファイル パス。たとえば、正確度のメトリックを取得するために定期的な検証を行うときに 80% - 20% のアプローチを使用する場合です。</span><span class="sxs-lookup"><span data-stu-id="d188f-142">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="d188f-143">`--test-dataset` を使用する場合は `--dataset` も必要です。</span><span class="sxs-lookup"><span data-stu-id="d188f-143">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="d188f-144">--validation-dataset が使用されていない限り、`--test-dataset` 引数は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="d188f-144">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="d188f-145">その場合、ユーザーは 3 つの引数を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d188f-145">In that case, the user must use the three arguments.</span></span>

## <a name="validation-dataset"></a><span data-ttu-id="d188f-146">検証データセット</span><span class="sxs-lookup"><span data-stu-id="d188f-146">Validation dataset</span></span>

<span data-ttu-id="d188f-147">`--validation-dataset | -v` (文字列)</span><span class="sxs-lookup"><span data-stu-id="d188f-147">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="d188f-148">検証データセット ファイルを指すファイル パス。</span><span class="sxs-lookup"><span data-stu-id="d188f-148">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="d188f-149">どのような場合でも、検証データセットは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="d188f-149">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="d188f-150">`validation dataset` を使用している場合、動作は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d188f-150">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="d188f-151">`test-dataset` と `--dataset` の引数も必須です。</span><span class="sxs-lookup"><span data-stu-id="d188f-151">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="d188f-152">`validation-dataset` データセットは、モデル選択の予測誤差を推定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d188f-152">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="d188f-153">`test-dataset` は、最終的に選択されたモデルの一般化誤差の評価に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d188f-153">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="d188f-154">テスト セットを "コンテナー" に保管し、データ分析の最後にのみ取り出すのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="d188f-154">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="d188f-155">基本的に、`validation dataset` と `test dataset` を使用する場合、検証フェーズは 2 つの部分に分けられます。</span><span class="sxs-lookup"><span data-stu-id="d188f-155">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="d188f-156">1 つ目の部分では、モデルを見て、検証データを使用して最適なパフォーマンスのアプローチを選択します (= 検証)。</span><span class="sxs-lookup"><span data-stu-id="d188f-156">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="d188f-157">次に、選択したアプローチの正確度を見積もります (= テスト)。</span><span class="sxs-lookup"><span data-stu-id="d188f-157">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="d188f-158">そのため、データの分離は 80/10/10 または 75/15/10 になります。</span><span class="sxs-lookup"><span data-stu-id="d188f-158">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="d188f-159">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d188f-159">For example:</span></span>

- <span data-ttu-id="d188f-160">`training-dataset` ファイルには 75% のデータがあります。</span><span class="sxs-lookup"><span data-stu-id="d188f-160">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="d188f-161">`validation-dataset` ファイルには 15% のデータがあります。</span><span class="sxs-lookup"><span data-stu-id="d188f-161">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="d188f-162">`test-dataset` ファイルには 10% のデータがあります。</span><span class="sxs-lookup"><span data-stu-id="d188f-162">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="d188f-163">いずれの場合でも、これらのパーセンテージは、既に分割されているファイルを指定する CLI の使用ユーザーが決定します。</span><span class="sxs-lookup"><span data-stu-id="d188f-163">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

## <a name="label-column"></a><span data-ttu-id="d188f-164">ラベル列</span><span class="sxs-lookup"><span data-stu-id="d188f-164">Label column</span></span>

<span data-ttu-id="d188f-165">`--label-col` (整数または文字列)</span><span class="sxs-lookup"><span data-stu-id="d188f-165">`--label-col` (int or string)</span></span>

<span data-ttu-id="d188f-166">この引数を使用すると、データセットのヘッダーに設定されている列の名前またはデータセットのファイル内の列の数値インデックスを使用して、特定の目的またはターゲット列 (予測する変数) を指定できます (列インデックス値は 0 から始まります)。</span><span class="sxs-lookup"><span data-stu-id="d188f-166">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="d188f-167">この引数は、"*分類*" および "*回帰*" の問題に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d188f-167">This argument is used for *classification* and *regression* problems.</span></span>

## <a name="item-column"></a><span data-ttu-id="d188f-168">アイテム列</span><span class="sxs-lookup"><span data-stu-id="d188f-168">Item column</span></span>

<span data-ttu-id="d188f-169">`--item-col` (整数または文字列)</span><span class="sxs-lookup"><span data-stu-id="d188f-169">`--item-col` (int or string)</span></span>

<span data-ttu-id="d188f-170">アイテム列には、ユーザーによって評価されるアイテムの一覧が含まれます (ユーザーにはアイテムをお勧めします)。</span><span class="sxs-lookup"><span data-stu-id="d188f-170">The item column has the list of items that users rate (items are recommended to users).</span></span> <span data-ttu-id="d188f-171">データセットのヘッダーに設定されている列の名前またはデータセットのファイル内の列の数値インデックスを使用して、この列を指定できます (列インデックス値は 0 から始まります)。</span><span class="sxs-lookup"><span data-stu-id="d188f-171">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="d188f-172">この引数は、"*推奨*" タスクにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="d188f-172">This argument is used only for the *recommendation* task.</span></span>

## <a name="rating-column"></a><span data-ttu-id="d188f-173">評価列</span><span class="sxs-lookup"><span data-stu-id="d188f-173">Rating column</span></span>

<span data-ttu-id="d188f-174">`--rating-col` (整数または文字列)</span><span class="sxs-lookup"><span data-stu-id="d188f-174">`--rating-col` (int or string)</span></span>

<span data-ttu-id="d188f-175">評価列には、ユーザーによってアイテムに指定された評価の一覧が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d188f-175">The rating column has the list of ratings that are given to items by users.</span></span> <span data-ttu-id="d188f-176">データセットのヘッダーに設定されている列の名前またはデータセットのファイル内の列の数値インデックスを使用して、この列を指定できます (列インデックス値は 0 から始まります)。</span><span class="sxs-lookup"><span data-stu-id="d188f-176">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="d188f-177">この引数は、"*推奨*" タスクにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="d188f-177">This argument is used only for the *recommendation* task.</span></span>

## <a name="user-column"></a><span data-ttu-id="d188f-178">ユーザー列</span><span class="sxs-lookup"><span data-stu-id="d188f-178">User column</span></span>

<span data-ttu-id="d188f-179">`--user-col` (整数または文字列)</span><span class="sxs-lookup"><span data-stu-id="d188f-179">`--user-col` (int or string)</span></span>

<span data-ttu-id="d188f-180">ユーザー列には、アイテムに評価を指定するユーザーの一覧が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d188f-180">The user column has the list of users that give ratings to items.</span></span> <span data-ttu-id="d188f-181">データセットのヘッダーに設定されている列の名前またはデータセットのファイル内の列の数値インデックスを使用して、この列を指定できます (列インデックス値は 0 から始まります)。</span><span class="sxs-lookup"><span data-stu-id="d188f-181">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="d188f-182">この引数は、"*推奨*" タスクにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="d188f-182">This argument is used only for the *recommendation* task.</span></span>

## <a name="ignore-columns"></a><span data-ttu-id="d188f-183">列を無視</span><span class="sxs-lookup"><span data-stu-id="d188f-183">Ignore columns</span></span>

<span data-ttu-id="d188f-184">`--ignore-columns` (文字列)</span><span class="sxs-lookup"><span data-stu-id="d188f-184">`--ignore-columns` (string)</span></span>

<span data-ttu-id="d188f-185">この引数を使用すると、トレーニング プロセスで読み込まれたり使用されたりしないように、データセット ファイル内の既存の列を無視することができます。</span><span class="sxs-lookup"><span data-stu-id="d188f-185">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="d188f-186">無視する列名を指定します。</span><span class="sxs-lookup"><span data-stu-id="d188f-186">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="d188f-187">複数の列名を区切るには、", " (コンマとスペース) または " " (スペース) を使用します。</span><span class="sxs-lookup"><span data-stu-id="d188f-187">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="d188f-188">空白を含む列名には引用符を使用することができます (例: "logged in")。</span><span class="sxs-lookup"><span data-stu-id="d188f-188">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="d188f-189">例:</span><span class="sxs-lookup"><span data-stu-id="d188f-189">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a><span data-ttu-id="d188f-190">ヘッダーの有無</span><span class="sxs-lookup"><span data-stu-id="d188f-190">Has header</span></span>

<span data-ttu-id="d188f-191">`--has-header` (ブール値)</span><span class="sxs-lookup"><span data-stu-id="d188f-191">`--has-header` (bool)</span></span>

<span data-ttu-id="d188f-192">データセット ファイルにヘッダー行があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d188f-192">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="d188f-193">指定できる値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d188f-193">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="d188f-194">この引数がユーザーによって指定されていない場合、ML.NET CLI ではこのプロパティの検出が試行されます。</span><span class="sxs-lookup"><span data-stu-id="d188f-194">The ML.NET CLI will try to detect this property if this argument is not specified by the user.</span></span>

## <a name="train-time"></a><span data-ttu-id="d188f-195">トレーニング時間</span><span class="sxs-lookup"><span data-stu-id="d188f-195">Train time</span></span>

<span data-ttu-id="d188f-196">`--train-time` (文字列)</span><span class="sxs-lookup"><span data-stu-id="d188f-196">`--train-time` (string)</span></span>

<span data-ttu-id="d188f-197">既定では、探索またはトレーニングの最長時間は 30 分です。</span><span class="sxs-lookup"><span data-stu-id="d188f-197">By default, the maximum exploration / train time is 30 minutes.</span></span>

<span data-ttu-id="d188f-198">この引数では、プロセスで複数のトレーナーと構成を探索できる最長時間 (秒単位) を設定します。</span><span class="sxs-lookup"><span data-stu-id="d188f-198">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="d188f-199">指定した時間が 1 回の反復処理に対して短すぎる (たとえば 2 秒) 場合、構成された時間を超えることがあります。</span><span class="sxs-lookup"><span data-stu-id="d188f-199">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="d188f-200">この場合、実際の時間は、1 回の反復処理で 1 つのモデル構成を作成するために必要な時間です。</span><span class="sxs-lookup"><span data-stu-id="d188f-200">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="d188f-201">反復処理に必要な時間は、データセットのサイズによって変わります。</span><span class="sxs-lookup"><span data-stu-id="d188f-201">The needed time for iterations can vary depending on the size of the dataset.</span></span>

## <a name="cache"></a><span data-ttu-id="d188f-202">キャッシュ</span><span class="sxs-lookup"><span data-stu-id="d188f-202">Cache</span></span>

<span data-ttu-id="d188f-203">`--cache` (文字列)</span><span class="sxs-lookup"><span data-stu-id="d188f-203">`--cache` (string)</span></span>

<span data-ttu-id="d188f-204">キャッシングを使用すると、トレーニング データセット全体がメモリ内に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="d188f-204">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="d188f-205">中小規模のデータセットでは、キャッシュを使用するとトレーニングのパフォーマンスが大幅に向上します。つまり、キャッシュを使用しない場合よりもトレーニング時間が短くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d188f-205">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="d188f-206">ただし、大規模なデータセットの場合、メモリ内のすべてのデータを読み込むと、メモリ不足になる可能性があるので、悪影響が出る可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d188f-206">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="d188f-207">大規模なデータセット ファイルを使用してトレーニングし、キャッシュを使用しない場合、ML.NET では、トレーニング中により多くのデータを読み込む必要があるときに、ドライブから大量のデータがストリーミングされます。</span><span class="sxs-lookup"><span data-stu-id="d188f-207">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="d188f-208">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d188f-208">You can specify the following values:</span></span>

<span data-ttu-id="d188f-209">`on`:トレーニング時にキャッシュを強制的に使用します。</span><span class="sxs-lookup"><span data-stu-id="d188f-209">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="d188f-210">`off`:トレーニング時にキャッシュを使用しないように強制します。</span><span class="sxs-lookup"><span data-stu-id="d188f-210">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="d188f-211">`auto`:AutoML のヒューリスティックに応じて、キャッシュを使用するかどうかが決まります。</span><span class="sxs-lookup"><span data-stu-id="d188f-211">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="d188f-212">通常、`auto` を選択した場合、中小規模のデータセットではキャッシュが使用され、大規模なデータセットではキャッシュが使用されません。</span><span class="sxs-lookup"><span data-stu-id="d188f-212">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="d188f-213">`--cache` パラメーターを指定しない場合、既定でキャッシュの `auto` 構成が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d188f-213">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

## <a name="name"></a><span data-ttu-id="d188f-214">名前</span><span class="sxs-lookup"><span data-stu-id="d188f-214">Name</span></span>

<span data-ttu-id="d188f-215">`--name` (文字列)</span><span class="sxs-lookup"><span data-stu-id="d188f-215">`--name` (string)</span></span>

<span data-ttu-id="d188f-216">作成される出力プロジェクトまたはソリューションの名前。</span><span class="sxs-lookup"><span data-stu-id="d188f-216">The name for the created output project or solution.</span></span> <span data-ttu-id="d188f-217">名前が指定されていない場合は、名前 `sample-{mltask}` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d188f-217">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="d188f-218">ML.NET モデル ファイル (.ZIP ファイル) も同じ名前になります。</span><span class="sxs-lookup"><span data-stu-id="d188f-218">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

## <a name="output-path"></a><span data-ttu-id="d188f-219">出力パス</span><span class="sxs-lookup"><span data-stu-id="d188f-219">Output path</span></span>

<span data-ttu-id="d188f-220">`--output | -o` (文字列)</span><span class="sxs-lookup"><span data-stu-id="d188f-220">`--output | -o` (string)</span></span>

<span data-ttu-id="d188f-221">生成された出力を配置するルートの場所/フォルダー。</span><span class="sxs-lookup"><span data-stu-id="d188f-221">Root location/folder to place the generated output.</span></span> <span data-ttu-id="d188f-222">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="d188f-222">The default is the current directory.</span></span>

## <a name="verbosity"></a><span data-ttu-id="d188f-223">詳細度</span><span class="sxs-lookup"><span data-stu-id="d188f-223">Verbosity</span></span>

<span data-ttu-id="d188f-224">`--verbosity | -v` (文字列)</span><span class="sxs-lookup"><span data-stu-id="d188f-224">`--verbosity | -v` (string)</span></span>

<span data-ttu-id="d188f-225">標準出力の詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="d188f-225">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="d188f-226">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d188f-226">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="d188f-227">`m[inimal]` (既定値)</span><span class="sxs-lookup"><span data-stu-id="d188f-227">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="d188f-228">`diag[nostic]` (ログ情報レベル)</span><span class="sxs-lookup"><span data-stu-id="d188f-228">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="d188f-229">既定で CLI ツールには、作業時に最小限のフィードバック (`minimal`) が表示されます。たとえば、作業中かどうか、可能であれば残り時間、または完了した時間の割合などが示されます。</span><span class="sxs-lookup"><span data-stu-id="d188f-229">By default, the CLI tool should show some minimum feedback (`minimal`) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

## <a name="help"></a><span data-ttu-id="d188f-230">ヘルプ</span><span class="sxs-lookup"><span data-stu-id="d188f-230">Help</span></span>

`-h |--help`

<span data-ttu-id="d188f-231">各コマンドのパラメーターの説明と共に、コマンドのヘルプを出力します。</span><span class="sxs-lookup"><span data-stu-id="d188f-231">Prints out help for the command with a description for each command's parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="d188f-232">関連項目</span><span class="sxs-lookup"><span data-stu-id="d188f-232">See also</span></span>

- [<span data-ttu-id="d188f-233">ML.NET CLI ツールのインストール方法</span><span class="sxs-lookup"><span data-stu-id="d188f-233">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="d188f-234">ML.NET CLI の概要</span><span class="sxs-lookup"><span data-stu-id="d188f-234">Overview of the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="d188f-235">チュートリアル: ML.NET CLI を使用してセンチメントを分析する</span><span class="sxs-lookup"><span data-stu-id="d188f-235">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="d188f-236">ML.NET CLI のテレメトリ</span><span class="sxs-lookup"><span data-stu-id="d188f-236">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
