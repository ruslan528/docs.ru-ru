---
title: Обучение модели машинного обучения, данные для которой находятся не в текстовом файле — ML.NET
description: Сведения об использовании ML.NET для загрузки обучающих данных, находящихся не в файле, для обучения модели машинного обучения в рамках конвейера прогнозирования.
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 971c5c62acc9dd7bf29aa11ce898c2b76822c3d7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2018
ms.locfileid: "53125406"
---
# <a name="train-a-machine-learning-model-with-data-thats-not-in-a-text-file---mlnet"></a><span data-ttu-id="77f4a-103">Обучение модели машинного обучения, данные для которой находятся не в текстовом файле — ML.NET</span><span class="sxs-lookup"><span data-stu-id="77f4a-103">Train a machine learning model with data that's not in a text file - ML.NET</span></span>

<span data-ttu-id="77f4a-104">Как правило, при работе с ML.NET используется вариант с чтением данных для обучения из файла с помощью `TextLoader`.</span><span class="sxs-lookup"><span data-stu-id="77f4a-104">The commonly demonstrated use case for ML.NET is use the `TextLoader` to read the training data from a file.</span></span>
<span data-ttu-id="77f4a-105">Тем не менее, в сценариях обучения в реальном времени возможны и другие варианты размещения данных. Данные могут:</span><span class="sxs-lookup"><span data-stu-id="77f4a-105">However, in real-time training scenarios the data can be elsewhere, such as:</span></span>

* <span data-ttu-id="77f4a-106">располагаться в таблицах SQL;</span><span class="sxs-lookup"><span data-stu-id="77f4a-106">in SQL tables</span></span>
* <span data-ttu-id="77f4a-107">извлекаться из файлов журналов;</span><span class="sxs-lookup"><span data-stu-id="77f4a-107">extracted from log files</span></span>
* <span data-ttu-id="77f4a-108">генерироваться "на лету".</span><span class="sxs-lookup"><span data-stu-id="77f4a-108">generated on the fly</span></span>

<span data-ttu-id="77f4a-109">Используйте [понимание схемы](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md), чтобы перенести существующий интерфейс `IEnumerable` C# в ML.NET как `DataView`.</span><span class="sxs-lookup"><span data-stu-id="77f4a-109">Use [schema comprehension](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) to bring an existing C# `IEnumerable` into ML.NET as a `DataView`.</span></span>

<span data-ttu-id="77f4a-110">В этом примере вам предстоит создать модель прогнозирования оттока клиентов, а также извлечь следующие функции из производственной системы:</span><span class="sxs-lookup"><span data-stu-id="77f4a-110">For this example, you'll build the customer churn prediction model, and extract the following features from your production system:</span></span>

* <span data-ttu-id="77f4a-111">идентификатор клиента (игнорируется моделью);</span><span class="sxs-lookup"><span data-stu-id="77f4a-111">Customer ID (ignored by the model)</span></span>
* <span data-ttu-id="77f4a-112">прекратил ли клиент сотрудничество (целевая "метка");</span><span class="sxs-lookup"><span data-stu-id="77f4a-112">Whether the customer has churned (the target 'label')</span></span>
* <span data-ttu-id="77f4a-113">"демографическая категория" (одна строка, например "молодой взрослый" и т. д.);</span><span class="sxs-lookup"><span data-stu-id="77f4a-113">The 'demographic category' (one string, like 'young adult' etc.)</span></span>
* <span data-ttu-id="77f4a-114">число посещений за последние 5 дней.</span><span class="sxs-lookup"><span data-stu-id="77f4a-114">The number of visits from the last 5 days.</span></span>

```csharp
private class CustomerChurnInfo
{
    public string CustomerID { get; set; }
    public bool HasChurned { get; set; }
    public string DemographicCategory { get; set; }
    // Visits during last 5 days, latest to newest.
    [VectorType(5)]
    public float[] LastVisits { get; set; }
}
```

<span data-ttu-id="77f4a-115">Загрузите эти данные в `DataView` и обучите модель, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="77f4a-115">Load this data into the `DataView` and train the model, using the following code:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging,
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// Let's assume that 'GetChurnData()' fetches and returns the training data from somewhere.
IEnumerable<CustomerChurnInfo> churnData = GetChurnInfo();

// Turn the data into the ML.NET data view.
// We can use CreateDataView or CreateStreamingDataView, depending on whether 'churnData' is an IList,
// or merely an IEnumerable.
var trainData = mlContext.CreateStreamingDataView(churnData);

// Build the learning pipeline.
// In our case, we will one-hot encode the demographic category, and concatenate that with the number of visits.
// We apply our FastTree binary classifier to predict the 'HasChurned' label.

var pipeline = mlContext.Transforms.Categorical.OneHotEncoding("DemographicCategory")
    .Append(mlContext.Transforms.Concatenate("Features", "DemographicCategory", "LastVisits"))
    .Append(mlContext.BinaryClassification.Trainers.FastTree("HasChurned", "Features", numTrees: 20));

var model = pipeline.Fit(trainData);
```