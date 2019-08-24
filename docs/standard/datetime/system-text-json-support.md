---
title: Поддержка DateTime и DateTimeOffset в System. Text. JSON
description: Общие сведения о поддержке типов DateTime и DateTimeOffset в библиотеке System. Text. JSON.
ms.technology: dotnet-standard
author: layomia
ms.author: laakinri
ms.date: 07/22/2019
helpviewer_keywords:
- JSON, Serializer, Utf8
- JSON DateTime, JSON DateTimeOffset
- DateTime, DateTimeOffset
- JsonSerializer, Utf8JsonReader, Utf8JsonWriter, JsonElement, JsonDocument
- JSON Serializer, JSON Reader, JSON Writer
- Converter, JSON Converter, DateTime Converter
- ISO, ISO 8601, ISO 8601-1:2019
ms.openlocfilehash: 182694a3d2df02d5e2c709e33a02bd9fa7d20383
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69973218"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a><span data-ttu-id="cda84-103">Поддержка DateTime и DateTimeOffset в System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="cda84-103">DateTime and DateTimeOffset support in System.Text.Json</span></span>

<span data-ttu-id="cda84-104">Библиотека System. Text. JSON выполняет синтаксический анализ и <xref:System.DateTime> запись <xref:System.DateTimeOffset> и значения в соответствии с расширенным профилем ISO 8601:-2019.</span><span class="sxs-lookup"><span data-stu-id="cda84-104">The System.Text.Json library parses and writes <xref:System.DateTime> and <xref:System.DateTimeOffset> values according to the ISO 8601:-2019 extended profile.</span></span>
<span data-ttu-id="cda84-105">[Преобразователи](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0) обеспечивают пользовательскую поддержку сериализации и десериализации с <xref:System.Text.Json.JsonSerializer>помощью.</span><span class="sxs-lookup"><span data-stu-id="cda84-105">[Converters](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0) provide custom support for serializing and deserializing with <xref:System.Text.Json.JsonSerializer>.</span></span>

## <a name="support-for-the-iso-8601-12019-format"></a><span data-ttu-id="cda84-106">Поддержка формата ISO 8601-1:2019</span><span class="sxs-lookup"><span data-stu-id="cda84-106">Support for the ISO 8601-1:2019 format</span></span>

<span data-ttu-id="cda84-107"><xref:System.Text.Json.JsonSerializer>Типы, <xref:System.Text.Json.Utf8JsonReader>, и<xref:System.Text.Json.Utf8JsonWriter> могутанализировать<xref:System.DateTime> и записывать и<xref:System.DateTimeOffset> текстовые представления в соответствии с расширенным профилем формата ISO 8601-1:2019, например 2019-07-26T16 <xref:System.Text.Json.JsonElement> : 59:57-05:00.</span><span class="sxs-lookup"><span data-stu-id="cda84-107">The <xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, <xref:System.Text.Json.Utf8JsonWriter>, and <xref:System.Text.Json.JsonElement> types parse and write <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations according to the extended profile of the ISO 8601-1:2019 format; for example, 2019-07-26T16:59:57-05:00.</span></span>

<span data-ttu-id="cda84-108"><xref:System.DateTime>данные <xref:System.DateTimeOffset> и могут быть сериализованы с <xref:System.Text.Json.JsonSerializer>помощью:</span><span class="sxs-lookup"><span data-stu-id="cda84-108"><xref:System.DateTime> and <xref:System.DateTimeOffset> data can be serialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/serializing-with-jsonserializer.cs)]

<span data-ttu-id="cda84-109">Их также можно десериализовать с помощью <xref:System.Text.Json.JsonSerializer>:</span><span class="sxs-lookup"><span data-stu-id="cda84-109">They can also be deserialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-valid.cs)]

<span data-ttu-id="cda84-110">При использовании параметров по умолчанию <xref:System.DateTimeOffset> входные <xref:System.DateTime> и текстовые представления должны соответствовать расширенному профилю ISO 8601-1:2019.</span><span class="sxs-lookup"><span data-stu-id="cda84-110">With default options, input <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations must conform to the extended ISO 8601-1:2019 profile.</span></span>
<span data-ttu-id="cda84-111">Попытка десериализовать представления, которые не соответствуют профилю <xref:System.Text.Json.JsonSerializer> , приведет к <xref:System.Text.Json.JsonException>созданию исключения:</span><span class="sxs-lookup"><span data-stu-id="cda84-111">Attempting to deserialize representations that don't conform to the profile will cause <xref:System.Text.Json.JsonSerializer> to throw a <xref:System.Text.Json.JsonException>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-error.cs)]

<span data-ttu-id="cda84-112">Предоставляет структурированный доступ к содержимому полезных данных JSON, включая <xref:System.DateTime> представления и <xref:System.DateTimeOffset>. <xref:System.Text.Json.JsonDocument></span><span class="sxs-lookup"><span data-stu-id="cda84-112">The <xref:System.Text.Json.JsonDocument> provides structured access to the contents of a JSON payload, including <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span> <span data-ttu-id="cda84-113">В приведенном ниже примере показано, как при наличии коллекции температур можно вычислить среднюю температуру по понедельникам.</span><span class="sxs-lookup"><span data-stu-id="cda84-113">The example below shows how, when given a collection of temperatures, the average temperature on Mondays can be calculated:</span></span>

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-valid.cs)]

<span data-ttu-id="cda84-114">Попытка вычисления средней температуры при наличии полезных данных с несоответствующими <xref:System.DateTime> представлениями <xref:System.Text.Json.JsonDocument> вызовет исключение <xref:System.FormatException>:</span><span class="sxs-lookup"><span data-stu-id="cda84-114">Attempting to compute the average temperature given a payload with non-compliant <xref:System.DateTime> representations will cause <xref:System.Text.Json.JsonDocument> to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-error.cs)]

<span data-ttu-id="cda84-115">Записи <xref:System.Text.Json.Utf8JsonWriter> <xref:System.DateTime> и данныенижнегоуровня:<xref:System.DateTimeOffset></span><span class="sxs-lookup"><span data-stu-id="cda84-115">The lower level <xref:System.Text.Json.Utf8JsonWriter> writes <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/writing-with-utf8jsonwriter.cs)]

<span data-ttu-id="cda84-116"><xref:System.Text.Json.Utf8JsonReader>синтаксические анализы <xref:System.DateTimeOffset>иданные <xref:System.DateTime> :</span><span class="sxs-lookup"><span data-stu-id="cda84-116"><xref:System.Text.Json.Utf8JsonReader> parses <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-valid.cs)]

<span data-ttu-id="cda84-117">Попытка чтения несовместимых форматов с <xref:System.Text.Json.Utf8JsonReader> вызовет <xref:System.FormatException>исключение:</span><span class="sxs-lookup"><span data-stu-id="cda84-117">Attempting to read non-compliant formats with <xref:System.Text.Json.Utf8JsonReader> will cause it to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-error.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset-in-xrefsystemtextjsonjsonserializer"></a><span data-ttu-id="cda84-118">Пользовательская поддержка <xref:System.DateTime> для <xref:System.DateTimeOffset> и в<xref:System.Text.Json.JsonSerializer></span><span class="sxs-lookup"><span data-stu-id="cda84-118">Custom support for <xref:System.DateTime> and <xref:System.DateTimeOffset> in <xref:System.Text.Json.JsonSerializer></span></span>

<span data-ttu-id="cda84-119">Если вы хотите, чтобы сериализатор выполнял пользовательское синтаксический анализ или форматирование, можно реализовать [пользовательские преобразователи](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="cda84-119">If you want the serializer to perform custom parsing or formatting, you can implement [custom converters](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0).</span></span>
<span data-ttu-id="cda84-120">Вот несколько примеров.</span><span class="sxs-lookup"><span data-stu-id="cda84-120">Here are a few examples:</span></span>

### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a><span data-ttu-id="cda84-121">Использование `DateTime(Offset).Parse` и`DateTime(Offset).ToString`</span><span class="sxs-lookup"><span data-stu-id="cda84-121">Using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`</span></span>

<span data-ttu-id="cda84-122">Если не удается определить форматы входных <xref:System.DateTime> или <xref:System.DateTimeOffset> текстовых представлений `DateTime(Offset).Parse` , можно использовать метод в логике чтения преобразователя.</span><span class="sxs-lookup"><span data-stu-id="cda84-122">If you can't determine the formats of your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations, you can use the `DateTime(Offset).Parse` method in your converter read logic.</span></span> <span data-ttu-id="cda84-123">Это позволяет использовать. Обширная поддержка для анализа различных <xref:System.DateTime> форматов и <xref:System.DateTimeOffset> текста, в том числе строк, отличных от ISO 8601, и форматов ISO 8601, которые не соответствуют расширенному профилю ISO 8601-1:2019.</span><span class="sxs-lookup"><span data-stu-id="cda84-123">This allows you to use .NET's extensive support for parsing various <xref:System.DateTime> and <xref:System.DateTimeOffset> text formats, including non-ISO 8601 strings and ISO 8601 formats that don't conform to the extended ISO 8601-1:2019 profile.</span></span> <span data-ttu-id="cda84-124">Этот подход значительно меньше, чем использование собственной реализации сериализатора.</span><span class="sxs-lookup"><span data-stu-id="cda84-124">This approach is significantly less performant than using the serializer's native implementation.</span></span>

<span data-ttu-id="cda84-125">Для сериализации можно использовать `DateTime(Offset).ToString` метод в логике записи преобразователя.</span><span class="sxs-lookup"><span data-stu-id="cda84-125">For serializing, you can use the `DateTime(Offset).ToString` method in your converter write logic.</span></span> <span data-ttu-id="cda84-126"><xref:System.DateTime> Это позволяет писать значения <xref:System.DateTimeOffset> и использовать любые [стандартные форматы даты](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)и времени, а также [пользовательские форматы даты и времени](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).</span><span class="sxs-lookup"><span data-stu-id="cda84-126">This allows you to write <xref:System.DateTime> and <xref:System.DateTimeOffset> values using any of the [standard date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), and the [custom date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).</span></span>
<span data-ttu-id="cda84-127">Это также значительно менее производительно, чем использование собственной реализации сериализатора.</span><span class="sxs-lookup"><span data-stu-id="cda84-127">This is also significantly less performant than using the serializer's native implementation.</span></span>

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> <span data-ttu-id="cda84-128">При реализации <xref:System.Text.Json.Serialization.JsonConverter%601> `T` , `typeToConvert` и параметр всегда будет иметь`typeof(DateTime)`значение. <xref:System.DateTime></span><span class="sxs-lookup"><span data-stu-id="cda84-128">When implementing <xref:System.Text.Json.Serialization.JsonConverter%601>, and `T` is <xref:System.DateTime>, the `typeToConvert` parameter will always be `typeof(DateTime)`.</span></span>
<span data-ttu-id="cda84-129">Параметр полезен для обработки полиморфизмов и использования универсальных шаблонов для получения `typeof(T)` производительного способа.</span><span class="sxs-lookup"><span data-stu-id="cda84-129">The parameter is useful for handling polymorphic cases and when using generics to get `typeof(T)` in a performant way.</span></span>

### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a><span data-ttu-id="cda84-130">Использование <xref:System.Buffers.Text.Utf8Parser> и<xref:System.Buffers.Text.Utf8Formatter></span><span class="sxs-lookup"><span data-stu-id="cda84-130">Using <xref:System.Buffers.Text.Utf8Parser> and <xref:System.Buffers.Text.Utf8Formatter></span></span>

<span data-ttu-id="cda84-131">В логике преобразователя можно использовать быстрые методы синтаксического анализа и форматирования на основе UTF-8, если <xref:System.DateTime> входные <xref:System.DateTimeOffset> или текстовые представления совместимы с одной из строк "R", "l", "O" или "G" [стандартного формата даты и времени](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)или если вы хотите запись в соответствии с одним из этих форматов.</span><span class="sxs-lookup"><span data-stu-id="cda84-131">You can use fast UTF-8-based parsing and formatting methods in your converter logic if your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations are compliant with one of the "R", "l", "O", or "G" [standard date and time format Strings](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), or you want to write according to one of these formats.</span></span> <span data-ttu-id="cda84-132">Это гораздо быстрее, чем использование `DateTime(Offset).Parse` и `DateTime(Offset).ToString`.</span><span class="sxs-lookup"><span data-stu-id="cda84-132">This is much faster than using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`.</span></span>

<span data-ttu-id="cda84-133">В этом примере показан пользовательский преобразователь, который сериализует и десериализует <xref:System.DateTime> значения в соответствии со [стандартным форматом "R"](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):</span><span class="sxs-lookup"><span data-stu-id="cda84-133">This example shows a custom converter that serializes and deserializes <xref:System.DateTime> values according to [the "R" standard format](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):</span></span>

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> <span data-ttu-id="cda84-134">Стандартный формат "R" всегда будет иметь длину 29 символов.</span><span class="sxs-lookup"><span data-stu-id="cda84-134">The "R" standard format will always be 29 characters long.</span></span>

### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a><span data-ttu-id="cda84-135">Использование `DateTime(Offset).Parse` в качестве резервного варианта для собственного анализа сериализатора</span><span class="sxs-lookup"><span data-stu-id="cda84-135">Using `DateTime(Offset).Parse` as a fallback to the serializer's native parsing</span></span>

<span data-ttu-id="cda84-136">Если обычно вход <xref:System.DateTime> или <xref:System.DateTimeOffset> данные должны соответствовать расширенному профилю ISO 8601-1:2019, можно использовать собственную логику синтаксического анализа сериализатора.</span><span class="sxs-lookup"><span data-stu-id="cda84-136">If you generally expect your input <xref:System.DateTime> or <xref:System.DateTimeOffset> data to conform to the extended ISO 8601-1:2019 profile, you can use the serializer's native parsing logic.</span></span> <span data-ttu-id="cda84-137">Также можно реализовать резервный механизм, как и в случае.</span><span class="sxs-lookup"><span data-stu-id="cda84-137">You can also implement a fallback mechanism just in case.</span></span>
<span data-ttu-id="cda84-138">В этом примере показано, что после сбоя синтаксического анализа <xref:System.DateTime> текстового представления с <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>помощью преобразователь успешно проанализирует данные с помощью <xref:System.DateTime.Parse(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="cda84-138">This example shows that, after failing to parse a <xref:System.DateTime> text representation using <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>, the converter successfully parses the data using <xref:System.DateTime.Parse(System.String)>.</span></span>

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example3/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a><span data-ttu-id="cda84-139">Расширенный профиль ISO 8601-1:2019 в System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="cda84-139">The extended ISO 8601-1:2019 profile in System.Text.Json</span></span>

### <a name="date-and-time-components"></a><span data-ttu-id="cda84-140">Компоненты даты и времени</span><span class="sxs-lookup"><span data-stu-id="cda84-140">Date and time components</span></span>

<span data-ttu-id="cda84-141">Расширенный профиль ISO 8601-1:2019, реализованный <xref:System.Text.Json> в, определяет следующие компоненты для представлений даты и времени.</span><span class="sxs-lookup"><span data-stu-id="cda84-141">The extended ISO 8601-1:2019 profile implemented in <xref:System.Text.Json> defines the following components for date and time representations.</span></span> <span data-ttu-id="cda84-142">Эти компоненты используются для определения различных уровней детализации, поддерживаемых при анализе и форматировании <xref:System.DateTime> <xref:System.DateTimeOffset> и представлениях.</span><span class="sxs-lookup"><span data-stu-id="cda84-142">These components are used to define various levels of granularity supported when parsing and formatting <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span>

| <span data-ttu-id="cda84-143">Компонент</span><span class="sxs-lookup"><span data-stu-id="cda84-143">Component</span></span>       | <span data-ttu-id="cda84-144">Формат</span><span class="sxs-lookup"><span data-stu-id="cda84-144">Format</span></span>                      | <span data-ttu-id="cda84-145">Описание</span><span class="sxs-lookup"><span data-stu-id="cda84-145">Description</span></span>                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| <span data-ttu-id="cda84-146">Год</span><span class="sxs-lookup"><span data-stu-id="cda84-146">Year</span></span>            | <span data-ttu-id="cda84-147">"yyyy"</span><span class="sxs-lookup"><span data-stu-id="cda84-147">"yyyy"</span></span>                      | <span data-ttu-id="cda84-148">0001-9999</span><span class="sxs-lookup"><span data-stu-id="cda84-148">0001-9999</span></span>                                                                       |
| <span data-ttu-id="cda84-149">Месяц</span><span class="sxs-lookup"><span data-stu-id="cda84-149">Month</span></span>           | <span data-ttu-id="cda84-150">"MM"</span><span class="sxs-lookup"><span data-stu-id="cda84-150">"MM"</span></span>                        | <span data-ttu-id="cda84-151">01-12</span><span class="sxs-lookup"><span data-stu-id="cda84-151">01-12</span></span>                                                                           |
| <span data-ttu-id="cda84-152">День</span><span class="sxs-lookup"><span data-stu-id="cda84-152">Day</span></span>             | <span data-ttu-id="cda84-153">"dd"</span><span class="sxs-lookup"><span data-stu-id="cda84-153">"dd"</span></span>                        | <span data-ttu-id="cda84-154">01-28, 01-29, 01-30, 01-31 в зависимости от месяца/года</span><span class="sxs-lookup"><span data-stu-id="cda84-154">01-28, 01-29, 01-30, 01-31 based on month/year</span></span>                                  |
| <span data-ttu-id="cda84-155">Час</span><span class="sxs-lookup"><span data-stu-id="cda84-155">Hour</span></span>            | <span data-ttu-id="cda84-156">"HH"</span><span class="sxs-lookup"><span data-stu-id="cda84-156">"HH"</span></span>                        | <span data-ttu-id="cda84-157">00-23</span><span class="sxs-lookup"><span data-stu-id="cda84-157">00-23</span></span>                                                                           |
| <span data-ttu-id="cda84-158">Минута</span><span class="sxs-lookup"><span data-stu-id="cda84-158">Minute</span></span>          | <span data-ttu-id="cda84-159">"mm"</span><span class="sxs-lookup"><span data-stu-id="cda84-159">"mm"</span></span>                        | <span data-ttu-id="cda84-160">00-59</span><span class="sxs-lookup"><span data-stu-id="cda84-160">00-59</span></span>                                                                           |
| <span data-ttu-id="cda84-161">Вторая</span><span class="sxs-lookup"><span data-stu-id="cda84-161">Second</span></span>          | <span data-ttu-id="cda84-162">"ss"</span><span class="sxs-lookup"><span data-stu-id="cda84-162">"ss"</span></span>                        | <span data-ttu-id="cda84-163">00-59</span><span class="sxs-lookup"><span data-stu-id="cda84-163">00-59</span></span>                                                                           |
| <span data-ttu-id="cda84-164">Вторая дробь</span><span class="sxs-lookup"><span data-stu-id="cda84-164">Second fraction</span></span> | <span data-ttu-id="cda84-165">"FFFFFFF"</span><span class="sxs-lookup"><span data-stu-id="cda84-165">"FFFFFFF"</span></span>                   | <span data-ttu-id="cda84-166">Минимум одна цифра, максимум 16 цифр</span><span class="sxs-lookup"><span data-stu-id="cda84-166">Minimum of one digit, maximum of 16 digits</span></span>                                      |
| <span data-ttu-id="cda84-167">Смещение времени</span><span class="sxs-lookup"><span data-stu-id="cda84-167">Time offset</span></span>     | <span data-ttu-id="cda84-168">"K"</span><span class="sxs-lookup"><span data-stu-id="cda84-168">"K"</span></span>                         | <span data-ttu-id="cda84-169">"Z" или "(' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="cda84-169">Either "Z" or "('+'/'-')HH':'mm"</span></span>                                                |
| <span data-ttu-id="cda84-170">Частичное время</span><span class="sxs-lookup"><span data-stu-id="cda84-170">Partial time</span></span>    | <span data-ttu-id="cda84-171">"HH": "mm": "SS [FFFFFFF]"</span><span class="sxs-lookup"><span data-stu-id="cda84-171">"HH':'mm':'ss[FFFFFFF]"</span></span>     | <span data-ttu-id="cda84-172">Время без сведений о смещении UTC</span><span class="sxs-lookup"><span data-stu-id="cda84-172">Time without UTC offset information</span></span>                                             |
| <span data-ttu-id="cda84-173">Полная дата</span><span class="sxs-lookup"><span data-stu-id="cda84-173">Full date</span></span>       | <span data-ttu-id="cda84-174">"yyyy'-'MM'-'дд"</span><span class="sxs-lookup"><span data-stu-id="cda84-174">"yyyy'-'MM'-'dd"</span></span>            | <span data-ttu-id="cda84-175">Дата календаря</span><span class="sxs-lookup"><span data-stu-id="cda84-175">Calendar date</span></span>                                                                   |
| <span data-ttu-id="cda84-176">Полное время</span><span class="sxs-lookup"><span data-stu-id="cda84-176">Full time</span></span>       | <span data-ttu-id="cda84-177">"Partial Тиме'к"</span><span class="sxs-lookup"><span data-stu-id="cda84-177">"'Partial time'K"</span></span>           | <span data-ttu-id="cda84-178">Время суток в формате UTC или местного времени дня с смещением времени между местным временем и временем в формате UTC</span><span class="sxs-lookup"><span data-stu-id="cda84-178">UTC of day or Local time of day with the time offset between local time and UTC</span></span> |
| <span data-ttu-id="cda84-179">Дата и время</span><span class="sxs-lookup"><span data-stu-id="cda84-179">Date time</span></span>       | <span data-ttu-id="cda84-180">"' Полная дата ' \ ' ' полное время ' '</span><span class="sxs-lookup"><span data-stu-id="cda84-180">"'Full date''T''Full time'"</span></span> | <span data-ttu-id="cda84-181">Календарная дата и время суток, например 2019-07-26T16:59:57-05:00</span><span class="sxs-lookup"><span data-stu-id="cda84-181">Calendar date and time of day, e.g. 2019-07-26T16:59:57-05:00</span></span>                   |

### <a name="support-for-parsing"></a><span data-ttu-id="cda84-182">Поддержка синтаксического анализа</span><span class="sxs-lookup"><span data-stu-id="cda84-182">Support for parsing</span></span>

<span data-ttu-id="cda84-183">Для синтаксического анализа определены следующие уровни детализации:</span><span class="sxs-lookup"><span data-stu-id="cda84-183">The following levels of granularity are defined for parsing:</span></span>

1. <span data-ttu-id="cda84-184">"Полная дата"</span><span class="sxs-lookup"><span data-stu-id="cda84-184">'Full date'</span></span>
    1. <span data-ttu-id="cda84-185">"yyyy'-'MM'-'дд"</span><span class="sxs-lookup"><span data-stu-id="cda84-185">"yyyy'-'MM'-'dd"</span></span>

2. <span data-ttu-id="cda84-186">"' Полная дата ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '</span><span class="sxs-lookup"><span data-stu-id="cda84-186">"'Full date''T''Hour'':''Minute'"</span></span>
    1. <span data-ttu-id="cda84-187">"yyyy'-'MM'-'dd'T'HH": "mm"</span><span class="sxs-lookup"><span data-stu-id="cda84-187">"yyyy'-'MM'-'dd'T'HH':'mm"</span></span>

3. <span data-ttu-id="cda84-188">"' Полная дата ' 'T ' ' частичное время ' '</span><span class="sxs-lookup"><span data-stu-id="cda84-188">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="cda84-189">"yyyy'-'MM'-'dd'T'HH": "mm": "SS" ([Описатель сортируемого формата ("s")](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="cda84-189">"yyyy'-'MM'-'dd'T'HH':'mm':'ss" ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>
    2. <span data-ttu-id="cda84-190">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS '. ' FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="cda84-190">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

4. <span data-ttu-id="cda84-191">"' Полная дата ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '</span><span class="sxs-lookup"><span data-stu-id="cda84-191">"'Full date''T''Time hour'':''Minute''Time offset'"</span></span>
    1. <span data-ttu-id="cda84-192">"yyyy'-'MM'-'dd'T'HH": "ММЗ"</span><span class="sxs-lookup"><span data-stu-id="cda84-192">"yyyy'-'MM'-'dd'T'HH':'mmZ"</span></span>
    2. <span data-ttu-id="cda84-193">"yyyy'-'MM'-'dd'T'HH": "mm (' + '/'-') HH ': ' mm"</span><span class="sxs-lookup"><span data-stu-id="cda84-193">"yyyy'-'MM'-'dd'T'HH':'mm('+'/'-')HH':'mm"</span></span>

5. <span data-ttu-id="cda84-194">"Дата и время"</span><span class="sxs-lookup"><span data-stu-id="cda84-194">'Date time'</span></span>
    1. <span data-ttu-id="cda84-195">"yyyy'-'MM'-'dd'T'HH": "mm": "ссZ"</span><span class="sxs-lookup"><span data-stu-id="cda84-195">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>
    2. <span data-ttu-id="cda84-196">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS '. ' ФФФФФФФЗ "</span><span class="sxs-lookup"><span data-stu-id="cda84-196">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>
    3. <span data-ttu-id="cda84-197">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="cda84-197">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>
    4. <span data-ttu-id="cda84-198">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS '. ' FFFFFFF (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="cda84-198">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

<span data-ttu-id="cda84-199">Если в секундах есть десятичные дроби, должна быть хотя бы одна цифра; `2019-07-26T00:00:00.` не допускается.</span><span class="sxs-lookup"><span data-stu-id="cda84-199">If there are decimal fractions for seconds, there must be at least one digit; `2019-07-26T00:00:00.` is not allowed.</span></span>
<span data-ttu-id="cda84-200">Хотя допускается до 16 цифр дробной части, анализируются только первые семь.</span><span class="sxs-lookup"><span data-stu-id="cda84-200">While up to 16 fractional digits are allowed, only the first seven are parsed.</span></span> <span data-ttu-id="cda84-201">Все, что больше, считается нулем.</span><span class="sxs-lookup"><span data-stu-id="cda84-201">Anything beyond that is considered a zero.</span></span>
<span data-ttu-id="cda84-202">Например, будет `2019-07-26T00:00:00.1234567890` анализироваться так, как если бы он `2019-07-26T00:00:00.1234567`был.</span><span class="sxs-lookup"><span data-stu-id="cda84-202">For example, `2019-07-26T00:00:00.1234567890` will be parsed as if it is `2019-07-26T00:00:00.1234567`.</span></span>
<span data-ttu-id="cda84-203">Это позволяет обеспечить совместимость с <xref:System.DateTime> реализацией, которая ограничена этим разрешением.</span><span class="sxs-lookup"><span data-stu-id="cda84-203">This is to stay compatible with the <xref:System.DateTime> implementation, which is limited to this resolution.</span></span>

<span data-ttu-id="cda84-204">Високосные секунды не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="cda84-204">Leap seconds are not supported.</span></span>

### <a name="support-for-formatting"></a><span data-ttu-id="cda84-205">Поддержка форматирования</span><span class="sxs-lookup"><span data-stu-id="cda84-205">Support for formatting</span></span>

<span data-ttu-id="cda84-206">Для форматирования определены следующие уровни гранулярности:</span><span class="sxs-lookup"><span data-stu-id="cda84-206">The following levels of granularity are defined for formatting:</span></span>

1. <span data-ttu-id="cda84-207">"' Полная дата ' 'T ' ' частичное время ' '</span><span class="sxs-lookup"><span data-stu-id="cda84-207">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="cda84-208">"yyyy'-'MM'-'dd'T'HH": "mm": "SS" ([Описатель сортируемого формата ("s")](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="cda84-208">"yyyy'-'MM'-'dd'T'HH':'mm':'ss"  ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>

        <span data-ttu-id="cda84-209">Используется для форматирования <xref:System.DateTime> без дробной части секунд и без сведений о смещении.</span><span class="sxs-lookup"><span data-stu-id="cda84-209">Used to format a <xref:System.DateTime> without fractional seconds and without offset information.</span></span>

    2. <span data-ttu-id="cda84-210">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS '. ' FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="cda84-210">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

        <span data-ttu-id="cda84-211">Используется для форматирования <xref:System.DateTime> с долей секунды, но без сведений о смещении.</span><span class="sxs-lookup"><span data-stu-id="cda84-211">Used to format a <xref:System.DateTime> with fractional seconds but without offset information.</span></span>

2. <span data-ttu-id="cda84-212">"Дата и время"</span><span class="sxs-lookup"><span data-stu-id="cda84-212">'Date time'</span></span>
    1. <span data-ttu-id="cda84-213">"yyyy'-'MM'-'dd'T'HH": "mm": "ссZ"</span><span class="sxs-lookup"><span data-stu-id="cda84-213">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>

        <span data-ttu-id="cda84-214">Используется для форматирования <xref:System.DateTime> или <xref:System.DateTimeOffset> без доли секунды, но с смещением в формате UTC.</span><span class="sxs-lookup"><span data-stu-id="cda84-214">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a UTC offset.</span></span>

    2. <span data-ttu-id="cda84-215">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS '. ' ФФФФФФФЗ "</span><span class="sxs-lookup"><span data-stu-id="cda84-215">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>

        <span data-ttu-id="cda84-216">Используется для форматирования <xref:System.DateTime> или <xref:System.DateTimeOffset> с долей секунды и со смещением в формате UTC.</span><span class="sxs-lookup"><span data-stu-id="cda84-216">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a UTC offset.</span></span>

    3. <span data-ttu-id="cda84-217">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="cda84-217">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="cda84-218">Используется для форматирования <xref:System.DateTime> или <xref:System.DateTimeOffset> без доли секунды, но с локальным смещением.</span><span class="sxs-lookup"><span data-stu-id="cda84-218">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a local offset.</span></span>

    4. <span data-ttu-id="cda84-219">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS '. ' FFFFFFF (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="cda84-219">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="cda84-220">Используется для форматирования <xref:System.DateTime> или <xref:System.DateTimeOffset> с долей секунды и с локальным смещением.</span><span class="sxs-lookup"><span data-stu-id="cda84-220">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a local offset.</span></span>