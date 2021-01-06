---
title: ML.NET の概要とそのしくみ
description: ML.NET を使用すると、オンラインまたはオフラインのどちらのシナリオでも、.NET アプリケーションに機械学習を追加できます。 この機能により、データを使った自動予測をアプリケーションで利用できるようになります。ML.NET を使うためにネットワークに接続する必要はありません。 この記事では、ML.NET の機械学習の基本について説明します。
ms.date: 11/5/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: 2c44a83b4d45c95cbe45f125523207811f6368c2
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97634067"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a><span data-ttu-id="af480-105">ML.NET の概要とそのしくみ</span><span class="sxs-lookup"><span data-stu-id="af480-105">What is ML.NET and how does it work?</span></span>

<span data-ttu-id="af480-106">ML.NET を使用すると、オンラインまたはオフラインのどちらのシナリオでも、.NET アプリケーションに機械学習を追加できます。</span><span class="sxs-lookup"><span data-stu-id="af480-106">ML.NET gives you the ability to add machine learning to .NET applications, in either online or offline scenarios.</span></span> <span data-ttu-id="af480-107">この機能により、データを使う自動予測をアプリケーションに利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="af480-107">With this capability, you can make automatic predictions using the data available to your application.</span></span> <span data-ttu-id="af480-108">機械学習アプリケーションでは、明示的なプログラミングを必要とする代わりに、データ内のパターンを利用して予測を行います。</span><span class="sxs-lookup"><span data-stu-id="af480-108">Machine learning applications make use of patterns in the data to make predictions rather than needing to be explicitly programmed.</span></span>

<span data-ttu-id="af480-109">ML.NET の中心となるのは、機械学習 **モデル** です。</span><span class="sxs-lookup"><span data-stu-id="af480-109">Central to ML.NET is a machine learning **model**.</span></span> <span data-ttu-id="af480-110">このモデルでは、入力データを予測に変換するために必要な手順が指定されます。</span><span class="sxs-lookup"><span data-stu-id="af480-110">The model specifies the steps needed to transform your input data into a prediction.</span></span> <span data-ttu-id="af480-111">.ML.NET を使用すると、アルゴリズムを指定してカスタム モデルをトレーニングすることができます。または、事前トレーニング済みの TensorFlow および ONNX モデルをインポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="af480-111">With ML.NET, you can train a custom model by specifying an algorithm, or you can import pre-trained TensorFlow and ONNX models.</span></span>

<span data-ttu-id="af480-112">モデルを用意したら、それをアプリケーションに追加して予測を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="af480-112">Once you have a model, you can add it to your application to make the predictions.</span></span>

<span data-ttu-id="af480-113">ML.NET は、.NET Core を使用して Windows、Linux、macOS 上で動作します。また、.NET Framework を使用して Windows 上で動作します。</span><span class="sxs-lookup"><span data-stu-id="af480-113">ML.NET runs on Windows, Linux, and macOS using .NET Core, or Windows using .NET Framework.</span></span> <span data-ttu-id="af480-114">64 ビットはすべてのプラットフォームでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="af480-114">64 bit is supported on all platforms.</span></span> <span data-ttu-id="af480-115">TensorFlow、LightGBM、および ONNX 関連の機能を除き、32 ビットは Windows 上でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="af480-115">32 bit is supported on Windows, except for TensorFlow, LightGBM, and ONNX-related functionality.</span></span>

<span data-ttu-id="af480-116">ML.NET で行うことができる予測の種類の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="af480-116">Examples of the type of predictions that you can make with ML.NET:</span></span>

|||
|-|-|
|<span data-ttu-id="af480-117">分類/カテゴリ化</span><span class="sxs-lookup"><span data-stu-id="af480-117">Classification/Categorization</span></span>|<span data-ttu-id="af480-118">カスタマー フィードバックを自動的に肯定的なカテゴリと否定的なカテゴリに分類する</span><span class="sxs-lookup"><span data-stu-id="af480-118">Automatically divide customer feedback into positive and negative categories</span></span>|
|<span data-ttu-id="af480-119">回帰/連続値の予測</span><span class="sxs-lookup"><span data-stu-id="af480-119">Regression/Predict continuous values</span></span>|<span data-ttu-id="af480-120">サイズと場所に基づいて住宅の価格を予測する</span><span class="sxs-lookup"><span data-stu-id="af480-120">Predict the price of houses based on size and location</span></span>|
|<span data-ttu-id="af480-121">異常検出</span><span class="sxs-lookup"><span data-stu-id="af480-121">Anomaly Detection</span></span>|<span data-ttu-id="af480-122">不正な銀行取引を検出する</span><span class="sxs-lookup"><span data-stu-id="af480-122">Detect fraudulent banking transactions</span></span> |
|<span data-ttu-id="af480-123">推奨事項</span><span class="sxs-lookup"><span data-stu-id="af480-123">Recommendations</span></span>|<span data-ttu-id="af480-124">以前の購入に基づいてオンラインの買い物客が購入する可能性がある商品を提案する</span><span class="sxs-lookup"><span data-stu-id="af480-124">Suggest products that online shoppers may want to buy, based on their previous purchases</span></span>|
|<span data-ttu-id="af480-125">時系列/シーケンシャル データ</span><span class="sxs-lookup"><span data-stu-id="af480-125">Time series/sequential data</span></span>|<span data-ttu-id="af480-126">天気/製品売上を予測する</span><span class="sxs-lookup"><span data-stu-id="af480-126">Forecast the weather/product sales</span></span>|
|<span data-ttu-id="af480-127">イメージ分類</span><span class="sxs-lookup"><span data-stu-id="af480-127">Image classification</span></span>|<span data-ttu-id="af480-128">病状を医療画像で分類する</span><span class="sxs-lookup"><span data-stu-id="af480-128">Categorize pathologies in medical images</span></span>|

## <a name="hello-mlnet-world"></a><span data-ttu-id="af480-129">ML.NET の基本</span><span class="sxs-lookup"><span data-stu-id="af480-129">Hello ML.NET World</span></span>

<span data-ttu-id="af480-130">次のスニペットのコードは、最も簡単な ML.NET アプリケーションの例です。</span><span class="sxs-lookup"><span data-stu-id="af480-130">The code in the following snippet demonstrates the simplest ML.NET application.</span></span> <span data-ttu-id="af480-131">この例では、住宅のサイズと価格のデータを使用して住宅価格を予測する線形回帰モデルを構築します。</span><span class="sxs-lookup"><span data-stu-id="af480-131">This example constructs a linear regression model to predict house prices using house size and price data.</span></span>

 ```csharp
    using System;
    using Microsoft.ML;
    using Microsoft.ML.Data;

    class Program
    {
        public class HouseData
        {
            public float Size { get; set; }
            public float Price { get; set; }
        }

        public class Prediction
        {
            [ColumnName("Score")]
            public float Price { get; set; }
        }

        static void Main(string[] args)
        {
            MLContext mlContext = new MLContext();

            // 1. Import or create training data
            HouseData[] houseData = {
                new HouseData() { Size = 1.1F, Price = 1.2F },
                new HouseData() { Size = 1.9F, Price = 2.3F },
                new HouseData() { Size = 2.8F, Price = 3.0F },
                new HouseData() { Size = 3.4F, Price = 3.7F } };
            IDataView trainingData = mlContext.Data.LoadFromEnumerable(houseData);

            // 2. Specify data preparation and model training pipeline
            var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
                .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));

            // 3. Train model
            var model = pipeline.Fit(trainingData);

            // 4. Make a prediction
            var size = new HouseData() { Size = 2.5F };
            var price = mlContext.Model.CreatePredictionEngine<HouseData, Prediction>(model).Predict(size);

            Console.WriteLine($"Predicted price for size: {size.Size*1000} sq ft= {price.Price*100:C}k");

            // Predicted price for size: 2500 sq ft= $261.98k
        }
    }
```

## <a name="code-workflow"></a><span data-ttu-id="af480-132">コードのワークフロー</span><span class="sxs-lookup"><span data-stu-id="af480-132">Code workflow</span></span>

<span data-ttu-id="af480-133">次の図は、アプリケーション コードの構造とモデル開発の反復処理を表しています。</span><span class="sxs-lookup"><span data-stu-id="af480-133">The following diagram represents the application code structure, as well as the iterative process of model development:</span></span>

- <span data-ttu-id="af480-134">トレーニング データを収集して **IDataView** オブジェクトに読み込む</span><span class="sxs-lookup"><span data-stu-id="af480-134">Collect and load training data into an **IDataView** object</span></span>
- <span data-ttu-id="af480-135">特徴を抽出し、機械学習アルゴリズムを適用するように操作のパイプラインを指定する</span><span class="sxs-lookup"><span data-stu-id="af480-135">Specify a pipeline of operations to extract features and apply a machine learning algorithm</span></span>
- <span data-ttu-id="af480-136">パイプラインに対して **Fit()** を呼び出してモデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="af480-136">Train a model by calling **Fit()** on the pipeline</span></span>
- <span data-ttu-id="af480-137">モデルを評価し、反復処理で改善する</span><span class="sxs-lookup"><span data-stu-id="af480-137">Evaluate the model and iterate to improve</span></span>
- <span data-ttu-id="af480-138">アプリケーションで使用できるようにモデルをバイナリ形式で保存する</span><span class="sxs-lookup"><span data-stu-id="af480-138">Save the model into binary format, for use in an application</span></span>
- <span data-ttu-id="af480-139">モデルを **ITransformer** オブジェクトに読み込む</span><span class="sxs-lookup"><span data-stu-id="af480-139">Load the model back into an **ITransformer** object</span></span>
- <span data-ttu-id="af480-140">**CreatePredictionEngine.Predict()** を呼び出して予測を行う</span><span class="sxs-lookup"><span data-stu-id="af480-140">Make predictions by calling **CreatePredictionEngine.Predict()**</span></span>

![データ生成、パイプライン開発、モデル トレーニング、モデル評価、およびモデル使用のためのコンポーネントを含む ML.NET アプリケーション開発フロー](./media/mldotnet-annotated-workflow.png)

<span data-ttu-id="af480-142">これらの概念についてもう少し詳しく掘り下げてみましょう。</span><span class="sxs-lookup"><span data-stu-id="af480-142">Let's dig a little deeper into those concepts.</span></span>

## <a name="machine-learning-model"></a><span data-ttu-id="af480-143">機械学習モデル</span><span class="sxs-lookup"><span data-stu-id="af480-143">Machine learning model</span></span>

<span data-ttu-id="af480-144">ML.NET モデルは、予測される出力に到達するために入力データに対して実行される変換を含むオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="af480-144">An ML.NET model is an object that contains transformations to perform on your input data to arrive at the predicted output.</span></span>

### <a name="basic"></a><span data-ttu-id="af480-145">Basic</span><span class="sxs-lookup"><span data-stu-id="af480-145">Basic</span></span>

<span data-ttu-id="af480-146">最も基本的なモデルは、前述の住宅価格の例のように、ある連続的な数量が別の連続的な数量と比例する 2 次元の線形回帰です。</span><span class="sxs-lookup"><span data-stu-id="af480-146">The most basic model is two-dimensional linear regression, where one continuous quantity is proportional to another, as in the house price example above.</span></span>

![バイアスと重みのパラメーターがある線形回帰モデル](./media/linear-regression-model.svg)

<span data-ttu-id="af480-148">このモデルは $Price = b + Size \* w$ のようにシンプルです。</span><span class="sxs-lookup"><span data-stu-id="af480-148">The model is simply: $Price = b + Size \* w$.</span></span> <span data-ttu-id="af480-149">パラメーター $b$ と $w$ は、(サイズ、価格) ペアのセットに直線を合わせることで推定されます。</span><span class="sxs-lookup"><span data-stu-id="af480-149">The parameters $b$ and $w$ are estimated by fitting a line on a set of (size, price) pairs.</span></span> <span data-ttu-id="af480-150">モデルのパラメーターを見つけるために使用されるデータは、**トレーニング データ** と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="af480-150">The data used to find the parameters of the model is called **training data**.</span></span> <span data-ttu-id="af480-151">機械学習モデルの入力は **特徴** と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="af480-151">The inputs of a machine learning model are called **features**.</span></span> <span data-ttu-id="af480-152">この例では、$Size$ が唯一の特徴です。</span><span class="sxs-lookup"><span data-stu-id="af480-152">In this example, $Size$ is the only feature.</span></span> <span data-ttu-id="af480-153">機械学習モデルのトレーニングに使用される真値は、**ラベル** と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="af480-153">The ground-truth values used to train a machine learning model are called **labels**.</span></span> <span data-ttu-id="af480-154">ここでは、トレーニング データ セットの $Price$ 値がラベルです。</span><span class="sxs-lookup"><span data-stu-id="af480-154">Here, the $Price$ values in the training data set are the labels.</span></span>

### <a name="more-complex"></a><span data-ttu-id="af480-155">より複雑</span><span class="sxs-lookup"><span data-stu-id="af480-155">More complex</span></span>

<span data-ttu-id="af480-156">より複雑なモデルでは、取引の説明文を使用して金融取引をカテゴリに分類します。</span><span class="sxs-lookup"><span data-stu-id="af480-156">A more complex model classifies financial transactions into categories using the transaction text description.</span></span>

<span data-ttu-id="af480-157">各取引の説明を特徴セットに分類するには、冗長な単語と文字を削除し、単語と文字の組み合わせを数えます。</span><span class="sxs-lookup"><span data-stu-id="af480-157">Each transaction description is broken down into a set of features by removing redundant words and characters, and counting word and character combinations.</span></span> <span data-ttu-id="af480-158">特徴セットは、トレーニング データ内の一連のカテゴリに基づいて線形モデルをトレーニングするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="af480-158">The feature set is used to train a linear model based on the set of categories in the training data.</span></span> <span data-ttu-id="af480-159">新しい説明がトレーニング セット内の説明に似ているほど、同じカテゴリに割り当てられる可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="af480-159">The more similar a new description is to the ones in the training set, the more likely it will be assigned to the same category.</span></span>

![テキスト分類モデル](./media/text-classification-model.svg)

<span data-ttu-id="af480-161">住宅価格モデルとテキスト分類モデルはどちらも **線形** モデルです。</span><span class="sxs-lookup"><span data-stu-id="af480-161">Both the house price model and the text classification model are **linear** models.</span></span> <span data-ttu-id="af480-162">データの性質や解決対象の問題に応じて、**デシジョン ツリー** モデル、**一般化加法** モデルなどを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="af480-162">Depending on the nature of your data and the problem you are solving, you can also use **decision tree** models, **generalized additive** models, and others.</span></span> <span data-ttu-id="af480-163">モデルの詳細については、[タスク](./resources/tasks.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af480-163">You can find out more about the models in [Tasks](./resources/tasks.md).</span></span>

## <a name="data-preparation"></a><span data-ttu-id="af480-164">データ準備</span><span class="sxs-lookup"><span data-stu-id="af480-164">Data preparation</span></span>

<span data-ttu-id="af480-165">ほとんどの場合、利用できるデータは、機械学習モデルのトレーニングにそのまま使用するために適していません。</span><span class="sxs-lookup"><span data-stu-id="af480-165">In most cases, the data that you have available isn't suitable to be used directly to train a machine learning model.</span></span> <span data-ttu-id="af480-166">生データは使用前に準備するか前処理して、モデルのパラメーターを見つける必要があります。</span><span class="sxs-lookup"><span data-stu-id="af480-166">The raw data needs to be prepared, or pre-processed, before it can be used to find the parameters of your model.</span></span> <span data-ttu-id="af480-167">文字列値から数値表現へのデータの変換が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="af480-167">Your data may need to be converted from string values to a numerical representation.</span></span> <span data-ttu-id="af480-168">入力データには冗長な情報が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="af480-168">You might have redundant information in your input data.</span></span> <span data-ttu-id="af480-169">入力データの次元の縮小または拡大が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="af480-169">You may need to reduce or expand the dimensions of your input data.</span></span> <span data-ttu-id="af480-170">データの正規化またはスケールが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="af480-170">Your data might need to be normalized or scaled.</span></span>

<span data-ttu-id="af480-171">「[ML.NET のチュートリアル](./tutorials/index.md)」では、特定の機械学習タスクに使用されるテキスト、画像、数値、および時系列データ用のさまざまなデータ処理パイプラインが説明されています。</span><span class="sxs-lookup"><span data-stu-id="af480-171">The [ML.NET tutorials](./tutorials/index.md) teach you about different data processing pipelines for text, image, numerical, and time-series data used for specific machine learning tasks.</span></span>

<span data-ttu-id="af480-172">[データの準備方法](./how-to-guides/prepare-data-ml-net.md)に関する記事では、データ準備を適用する方法が全般的に説明されています。</span><span class="sxs-lookup"><span data-stu-id="af480-172">[How to prepare your data](./how-to-guides/prepare-data-ml-net.md) shows you how to apply data preparation more generally.</span></span>

<span data-ttu-id="af480-173">すべての[使用できる変換](./resources/transforms.md)の付録については、リソース セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="af480-173">You can find an appendix of all of the [available transformations](./resources/transforms.md) in the resources section.</span></span>

## <a name="model-evaluation"></a><span data-ttu-id="af480-174">モデル評価</span><span class="sxs-lookup"><span data-stu-id="af480-174">Model evaluation</span></span>

<span data-ttu-id="af480-175">トレーニングを完了したモデルが今後の予測にどのくらい役立つかは、どうすればわかるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="af480-175">Once you have trained your model, how do you know how well it will make future predictions?</span></span> <span data-ttu-id="af480-176">ML.NET を使用すると、いくつかの新しいテスト データに対してモデルを評価できます。</span><span class="sxs-lookup"><span data-stu-id="af480-176">With ML.NET, you can evaluate your model against some new test data.</span></span>

<span data-ttu-id="af480-177">機械学習タスクの種類ごとに、テスト データ セットに対するモデルの正確度と精度の評価に使用されるメトリックがあります。</span><span class="sxs-lookup"><span data-stu-id="af480-177">Each type of machine learning task has metrics used to evaluate the accuracy and precision of the model against the test data set.</span></span>

<span data-ttu-id="af480-178">住宅価格の例では、**回帰** タスクを使用しました。</span><span class="sxs-lookup"><span data-stu-id="af480-178">For our house price example, we used the **Regression** task.</span></span> <span data-ttu-id="af480-179">このモデルを評価するには、元のサンプルに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="af480-179">To evaluate the model, add the following code to the original sample.</span></span>

```csharp
        HouseData[] testHouseData =
        {
            new HouseData() { Size = 1.1F, Price = 0.98F },
            new HouseData() { Size = 1.9F, Price = 2.1F },
            new HouseData() { Size = 2.8F, Price = 2.9F },
            new HouseData() { Size = 3.4F, Price = 3.6F }
        };

        var testHouseDataView = mlContext.Data.LoadFromEnumerable(testHouseData);
        var testPriceDataView = model.Transform(testHouseDataView);

        var metrics = mlContext.Regression.Evaluate(testPriceDataView, labelColumnName: "Price");

        Console.WriteLine($"R^2: {metrics.RSquared:0.##}");
        Console.WriteLine($"RMS error: {metrics.RootMeanSquaredError:0.##}");

        // R^2: 0.96
        // RMS error: 0.19
```

<span data-ttu-id="af480-180">評価メトリックから、誤差が少ないことと、予測される出力とテスト出力の間の相関度が高いことがわかります。</span><span class="sxs-lookup"><span data-stu-id="af480-180">The evaluation metrics tell you that the error is low-ish, and that correlation between the predicted output and the test output is high.</span></span> <span data-ttu-id="af480-181">簡単でしたね。</span><span class="sxs-lookup"><span data-stu-id="af480-181">That was easy!</span></span> <span data-ttu-id="af480-182">実際の例で優れたモデル メトリックを実現するには、さらに調整が必要です。</span><span class="sxs-lookup"><span data-stu-id="af480-182">In real examples, it takes more tuning to achieve good model metrics.</span></span>

## <a name="mlnet-architecture"></a><span data-ttu-id="af480-183">ML.NET のアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="af480-183">ML.NET architecture</span></span>

<span data-ttu-id="af480-184">このセクションでは、ML.NET のアーキテクチャ パターンについて説明します。</span><span class="sxs-lookup"><span data-stu-id="af480-184">In this section, we go through the architectural patterns of ML.NET.</span></span> <span data-ttu-id="af480-185">経験豊富な .NET 開発者であれば、なじみのあるパターンと、あまりなじみのないパターンがあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="af480-185">If you are an experienced .NET developer, some of these patterns will be familiar to you, and some will be less familiar.</span></span> <span data-ttu-id="af480-186">詳しく説明しますので、ついてきてください。</span><span class="sxs-lookup"><span data-stu-id="af480-186">Hold tight, while we dive in!</span></span>

<span data-ttu-id="af480-187">ML.NET アプリケーションは <xref:Microsoft.ML.MLContext> オブジェクトから始まります。</span><span class="sxs-lookup"><span data-stu-id="af480-187">An ML.NET application starts with an <xref:Microsoft.ML.MLContext> object.</span></span> <span data-ttu-id="af480-188">このシングルトン オブジェクトには **カタログ** が含まれます。</span><span class="sxs-lookup"><span data-stu-id="af480-188">This singleton object contains **catalogs**.</span></span> <span data-ttu-id="af480-189">カタログは、データの読み込みと保存、変換、トレーナー、およびモデル運用コンポーネントのためのファクトリです。</span><span class="sxs-lookup"><span data-stu-id="af480-189">A catalog is a factory for data loading and saving, transforms, trainers, and model operation components.</span></span> <span data-ttu-id="af480-190">各カタログ オブジェクトには、さまざまな種類のコンポーネントを作成するメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="af480-190">Each catalog object has methods to create the different types of components:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="af480-191">データの読み込みと保存</span><span class="sxs-lookup"><span data-stu-id="af480-191">Data loading and saving</span></span>||<xref:Microsoft.ML.DataOperationsCatalog>||
|<span data-ttu-id="af480-192">データ準備</span><span class="sxs-lookup"><span data-stu-id="af480-192">Data preparation</span></span>||<xref:Microsoft.ML.TransformsCatalog>||
|<span data-ttu-id="af480-193">トレーニングのアルゴリズム</span><span class="sxs-lookup"><span data-stu-id="af480-193">Training algorithms</span></span>|<span data-ttu-id="af480-194">二項分類</span><span class="sxs-lookup"><span data-stu-id="af480-194">Binary classification</span></span>|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||<span data-ttu-id="af480-195">多クラス分類</span><span class="sxs-lookup"><span data-stu-id="af480-195">Multiclass classification</span></span>|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||<span data-ttu-id="af480-196">異常検出</span><span class="sxs-lookup"><span data-stu-id="af480-196">Anomaly detection</span></span>|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||<span data-ttu-id="af480-197">クラスタリング</span><span class="sxs-lookup"><span data-stu-id="af480-197">Clustering</span></span>|<xref:Microsoft.ML.ClusteringCatalog>||
||<span data-ttu-id="af480-198">予測</span><span class="sxs-lookup"><span data-stu-id="af480-198">Forecasting</span></span>|<xref:Microsoft.ML.ForecastingCatalog>||
||<span data-ttu-id="af480-199">ランキング</span><span class="sxs-lookup"><span data-stu-id="af480-199">Ranking</span></span>|<xref:Microsoft.ML.RankingCatalog>||
||<span data-ttu-id="af480-200">回帰</span><span class="sxs-lookup"><span data-stu-id="af480-200">Regression</span></span>|<xref:Microsoft.ML.RegressionCatalog>||
||<span data-ttu-id="af480-201">推奨事項</span><span class="sxs-lookup"><span data-stu-id="af480-201">Recommendation</span></span>|<xref:Microsoft.ML.RecommendationCatalog>|<span data-ttu-id="af480-202">`Microsoft.ML.Recommender` NuGet パッケージを取得する</span><span class="sxs-lookup"><span data-stu-id="af480-202">add the `Microsoft.ML.Recommender` NuGet package</span></span>|
||<span data-ttu-id="af480-203">TimeSeries</span><span class="sxs-lookup"><span data-stu-id="af480-203">TimeSeries</span></span>|<xref:Microsoft.ML.TimeSeriesCatalog>|<span data-ttu-id="af480-204">`Microsoft.ML.TimeSeries` NuGet パッケージを取得する</span><span class="sxs-lookup"><span data-stu-id="af480-204">add the `Microsoft.ML.TimeSeries` NuGet package</span></span>|
|<span data-ttu-id="af480-205">モデルの使用法</span><span class="sxs-lookup"><span data-stu-id="af480-205">Model usage</span></span> ||<xref:Microsoft.ML.ModelOperationsCatalog>||

<span data-ttu-id="af480-206">上記の各カテゴリの作成方法に移動できます。</span><span class="sxs-lookup"><span data-stu-id="af480-206">You can navigate to the creation methods in each of the above categories.</span></span> <span data-ttu-id="af480-207">Visual Studio を使用すると、IntelliSense を介してカタログが表示されます。</span><span class="sxs-lookup"><span data-stu-id="af480-207">Using Visual Studio, the catalogs show up via IntelliSense.</span></span>

   ![回帰トレーナー用の IntelliSense](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a><span data-ttu-id="af480-209">パイプラインを構築する</span><span class="sxs-lookup"><span data-stu-id="af480-209">Build the pipeline</span></span>

<span data-ttu-id="af480-210">各カタログ内には、一連の拡張メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="af480-210">Inside each catalog is a set of extension methods.</span></span> <span data-ttu-id="af480-211">トレーニング パイプラインを作成するために拡張メソッドがどのように使用されるかを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="af480-211">Let's look at how extension methods are used to create a training pipeline.</span></span>

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

<span data-ttu-id="af480-212">このスニペットで、`Concatenate` と `Sdca` はどちらもカタログ内のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="af480-212">In the snippet, `Concatenate` and `Sdca` are both methods in the catalog.</span></span> <span data-ttu-id="af480-213">それぞれ、パイプラインに追加される [IEstimator](xref:Microsoft.ML.IEstimator%601) オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="af480-213">They each create an [IEstimator](xref:Microsoft.ML.IEstimator%601) object that is appended to the pipeline.</span></span>

<span data-ttu-id="af480-214">この時点では、オブジェクトが作成されるだけです。</span><span class="sxs-lookup"><span data-stu-id="af480-214">At this point, the objects are created only.</span></span> <span data-ttu-id="af480-215">実行は行われません。</span><span class="sxs-lookup"><span data-stu-id="af480-215">No execution has happened.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="af480-216">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="af480-216">Train the model</span></span>

<span data-ttu-id="af480-217">パイプライン内にオブジェクトが作成されたら、データを使用してモデルをトレーニングできます。</span><span class="sxs-lookup"><span data-stu-id="af480-217">Once the objects in the pipeline have been created, data can be used to train the model.</span></span>

```csharp
    var model = pipeline.Fit(trainingData);
```

<span data-ttu-id="af480-218">`Fit()` を呼び出すと、入力トレーニング データを使用してモデルのパラメーターが推定されます。</span><span class="sxs-lookup"><span data-stu-id="af480-218">Calling `Fit()` uses the input training data to estimate the parameters of the model.</span></span> <span data-ttu-id="af480-219">これはモデルのトレーニングと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="af480-219">This is known as training the model.</span></span> <span data-ttu-id="af480-220">前述の線形回帰モデルには、**バイアス** と **重み** という 2 つのモデル パラメーターがあったことを思い出してください。</span><span class="sxs-lookup"><span data-stu-id="af480-220">Remember, the linear regression model above had two model parameters: **bias** and **weight**.</span></span> <span data-ttu-id="af480-221">`Fit()` の呼び出しの後は、パラメーターの値がわかっています。</span><span class="sxs-lookup"><span data-stu-id="af480-221">After the `Fit()` call, the values of the parameters are known.</span></span> <span data-ttu-id="af480-222">ほとんどのモデルには、これよりもさらに多くのパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="af480-222">Most models will have many more parameters than this.</span></span>

<span data-ttu-id="af480-223">モデルのトレーニングの詳細については、[モデルのトレーニング方法](./how-to-guides/train-machine-learning-model-ml-net.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="af480-223">You can learn more about model training in [How to train your model](./how-to-guides/train-machine-learning-model-ml-net.md).</span></span>

<span data-ttu-id="af480-224">結果のモデル オブジェクトには <xref:Microsoft.ML.ITransformer> インターフェイスが実装されます。</span><span class="sxs-lookup"><span data-stu-id="af480-224">The resulting model object implements the <xref:Microsoft.ML.ITransformer> interface.</span></span> <span data-ttu-id="af480-225">つまり、このモデルによって入力データは予測に変換されます。</span><span class="sxs-lookup"><span data-stu-id="af480-225">That is, the model transforms input data into predictions.</span></span>

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a><span data-ttu-id="af480-226">モデルを使用する</span><span class="sxs-lookup"><span data-stu-id="af480-226">Use the model</span></span>

<span data-ttu-id="af480-227">入力データを一括して予測に変換するか、入力を 1 つずつ変換することができます。</span><span class="sxs-lookup"><span data-stu-id="af480-227">You can transform input data into predictions in bulk, or one input at a time.</span></span> <span data-ttu-id="af480-228">住宅価格の例では、その両方を行いました。つまり、モデルの評価を目的とした一括処理と、新しい予測を行うための個別処理です。</span><span class="sxs-lookup"><span data-stu-id="af480-228">In the house price example, we did both: in bulk for the purpose of evaluating the model, and one at a time to make a new prediction.</span></span> <span data-ttu-id="af480-229">1 つの予測を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="af480-229">Let's look at making single predictions.</span></span>

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```

<span data-ttu-id="af480-230">`CreatePredictionEngine()` メソッドは、入力クラスと出力クラスを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="af480-230">The `CreatePredictionEngine()` method takes an input class and an output class.</span></span> <span data-ttu-id="af480-231">このフィールドの名前やコード属性によって、モデルのトレーニングと予測中に使用されるデータ列の名前が決まります。</span><span class="sxs-lookup"><span data-stu-id="af480-231">The field names and/or code attributes determine the names of the data columns used during model training and prediction.</span></span> <span data-ttu-id="af480-232">詳細については、「[トレーニング済みモデルを使用して予測する](how-to-guides/machine-learning-model-predictions-ml-net.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af480-232">For more information, see [Make predictions with a trained model](how-to-guides/machine-learning-model-predictions-ml-net.md).</span></span>

### <a name="data-models-and-schema"></a><span data-ttu-id="af480-233">データ モデルとスキーマ</span><span class="sxs-lookup"><span data-stu-id="af480-233">Data models and schema</span></span>

<span data-ttu-id="af480-234">ML.NET 機械学習パイプラインの中心には [DataView](xref:Microsoft.ML.IDataView) オブジェクトがあります。</span><span class="sxs-lookup"><span data-stu-id="af480-234">At the core of an ML.NET machine learning pipeline are [DataView](xref:Microsoft.ML.IDataView) objects.</span></span>

<span data-ttu-id="af480-235">パイプライン内の各変換には、入力スキーマ (変換で入力にあると想定されているデータの名前、型、およびサイズ) と、出力スキーマ (変換によって変換後に生成されるデータの名前、型、およびサイズ) があります。</span><span class="sxs-lookup"><span data-stu-id="af480-235">Each transformation in the pipeline has an input schema (data names, types, and sizes that the transform expects to see on its input); and an output schema (data names, types, and sizes that the transform produces after the transformation).</span></span>

<span data-ttu-id="af480-236">パイプライン内の 1 つの変換からの出力スキーマが次の変換の入力スキーマと一致しない場合、ML.NET から例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="af480-236">If the output schema from one transform in the pipeline doesn't match the input schema of the next transform, ML.NET will throw an exception.</span></span>

<span data-ttu-id="af480-237">データ ビュー オブジェクトには列と行があります。</span><span class="sxs-lookup"><span data-stu-id="af480-237">A data view object has columns and rows.</span></span> <span data-ttu-id="af480-238">各列には、名前、型、および長さがあります。</span><span class="sxs-lookup"><span data-stu-id="af480-238">Each column has a name and a type and a length.</span></span> <span data-ttu-id="af480-239">たとえば、住宅価格例の入力列は **Size** と **Price** です。</span><span class="sxs-lookup"><span data-stu-id="af480-239">For example, the input columns in the house price example are **Size** and **Price**.</span></span> <span data-ttu-id="af480-240">これらはどちらも型であり、ベクターではなくスカラーの数量です。</span><span class="sxs-lookup"><span data-stu-id="af480-240">They are both type and they are scalar quantities rather than vector ones.</span></span>

   ![住宅価格の予測データを含む ML.NET データ ビューの例](./media/ml-net-dataview.png)

<span data-ttu-id="af480-242">すべての ML.NET アルゴリズムは、ベクターである入力列を探します。</span><span class="sxs-lookup"><span data-stu-id="af480-242">All ML.NET algorithms look for an input column that is a vector.</span></span> <span data-ttu-id="af480-243">既定では、このベクター列は **Features** という名前です。</span><span class="sxs-lookup"><span data-stu-id="af480-243">By default this vector column is called **Features**.</span></span> <span data-ttu-id="af480-244">住宅価格の例で、**Size** 列を **Features** という新しい列に連結したのはこのためです。</span><span class="sxs-lookup"><span data-stu-id="af480-244">This is why we concatenated the **Size** column into a new column called **Features** in our house price example.</span></span>

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

<span data-ttu-id="af480-245">予測を実行した後は、いずれのアルゴリズムでも新しい列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="af480-245">All algorithms also create new columns after they have performed a prediction.</span></span> <span data-ttu-id="af480-246">このような新しい列の固定名は、機械学習アルゴリズムの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="af480-246">The fixed names of these new columns depend on the type of machine learning algorithm.</span></span> <span data-ttu-id="af480-247">回帰タスクでは、新しい列の 1 つは **Score** という名前です。</span><span class="sxs-lookup"><span data-stu-id="af480-247">For the regression task, one of the new columns is called **Score**.</span></span> <span data-ttu-id="af480-248">価格データにこの名前を付けたのはこのためです。</span><span class="sxs-lookup"><span data-stu-id="af480-248">This is why we attributed our price data with this name.</span></span>

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```

<span data-ttu-id="af480-249">さまざまな機械学習タスクの出力列の詳細については、[機械学習のタスク](resources/tasks.md)に関するガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="af480-249">You can find out more about output columns of different machine learning tasks in the [Machine Learning Tasks](resources/tasks.md) guide.</span></span>

<span data-ttu-id="af480-250">DataView オブジェクトの重要なプロパティは、**遅延** 評価されることです。</span><span class="sxs-lookup"><span data-stu-id="af480-250">An important property of DataView objects is that they are evaluated **lazily**.</span></span> <span data-ttu-id="af480-251">データ ビューは、モデルのトレーニングと評価、およびデータの予測中にのみ読み込まれ、操作されます。</span><span class="sxs-lookup"><span data-stu-id="af480-251">Data views are only loaded and operated on during model training and evaluation, and data prediction.</span></span> <span data-ttu-id="af480-252">ML.NET アプリケーションの作成とテストを行っている間は、[Preview](xref:Microsoft.ML.DebuggerExtensions.Preview%2A) メソッドを呼び出すことで、Visual Studio デバッガーを使用して任意のデータ ビュー オブジェクトを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="af480-252">While you are writing and testing your ML.NET application, you can use the Visual Studio debugger to take a peek at any data view object by calling the [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview%2A) method.</span></span>

```csharp
    var debug = testPriceDataView.Preview();
```

<span data-ttu-id="af480-253">`debug` 変数はデバッガーで監視し、その内容を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="af480-253">You can watch the `debug` variable in the debugger and examine its contents.</span></span> <span data-ttu-id="af480-254">運用環境のコードでは、パフォーマンスが大幅に低下するので Preview メソッドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="af480-254">Do not use the Preview method in production code, as it significantly degrades performance.</span></span>

### <a name="model-deployment"></a><span data-ttu-id="af480-255">モデル デプロイ</span><span class="sxs-lookup"><span data-stu-id="af480-255">Model Deployment</span></span>

<span data-ttu-id="af480-256">実際のアプリケーションでは、モデル トレーニングと評価のコードは予測とは別になります。</span><span class="sxs-lookup"><span data-stu-id="af480-256">In real-life applications, your model training and evaluation code will be separate from your prediction.</span></span> <span data-ttu-id="af480-257">実際、これら 2 つの活動は、別のチームによって行われることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="af480-257">In fact, these two activities are often performed by separate teams.</span></span> <span data-ttu-id="af480-258">モデル開発チームは、予測アプリケーションで使用するためにモデルを保存することができます。</span><span class="sxs-lookup"><span data-stu-id="af480-258">Your model development team can save the model for use in the prediction application.</span></span>

```csharp
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="next-steps"></a><span data-ttu-id="af480-259">次の手順</span><span class="sxs-lookup"><span data-stu-id="af480-259">Next steps</span></span>

* <span data-ttu-id="af480-260">[チュートリアル](./tutorials/index.md)で、より現実的なデータ セットと共にさまざまな機械学習タスクを使用してアプリケーションを構築する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="af480-260">Learn how to build applications using different machine learning tasks with more realistic data sets in the [tutorials](./tutorials/index.md).</span></span>

* <span data-ttu-id="af480-261">[ハウツー ガイド](./how-to-guides/index.md)で、特定のトピックについてさらに詳しく学習します。</span><span class="sxs-lookup"><span data-stu-id="af480-261">Learn about specific topics in more depth in the [How To Guides](./how-to-guides/index.md).</span></span>

* <span data-ttu-id="af480-262">さらに詳しく学習するには、[API リファレンスのドキュメント](../../api/index.md?view=ml-dotnet)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af480-262">If you're super keen, you can dive straight into the [API Reference documentation](../../api/index.md?view=ml-dotnet).</span></span>
