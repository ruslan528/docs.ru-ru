---
title: Типы данных
ms.date: 12/13/2019
description: Описание поддерживаемых типов данных и некоторых ограничений, связанных с ними.
ms.openlocfilehash: ae70cb91a5a6d9cfed45a5a47dda25a70362871e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/25/2019
ms.locfileid: "75450420"
---
# <a name="data-types"></a>Типы данных

SQLite имеет только четыре примитивных типа данных: целые, реальные, текстовые и BLOB. API-интерфейсы, возвращающие значения базы данных в виде `object`, возвращают только один из этих четырех типов. В Microsoft. Data. SQLite поддерживаются дополнительные типы .NET, но значения в конечном итоге приведены между этими типами и одним из четырех типов-примитивов.

| .NET           | SQLite  | Заметки                                                       |
| -------------- | ------- | ------------------------------------------------------------- |
| Логическое значение .        | INTEGER | `0` или `1`                                                    |
| Байт           | INTEGER |                                                               |
| Byte[]         | BLOB    |                                                               |
| Char           | TEXT    | UTF-8                                                         |
| DateTime       | TEXT    | гггг-мм-дд чч: мм: СС. FFFFFFF                                   |
| DateTimeOffset | TEXT    | гггг-мм-дд чч: мм: СС. FFFFFFFzzz                                |
| Десятичное число        | TEXT    | формат `0.0###########################`. Реальная сумма будет утеряна. |
| С двойной точностью         | ВЕЩЕСТВЕННОЕ ЧИСЛО    |                                                               |
| Идентификатор GUID           | TEXT    | 00000000-0000-0000-0000-000000000000                          |
| Int16          | INTEGER |                                                               |
| Int32          | INTEGER |                                                               |
| Int64          | INTEGER |                                                               |
| SByte          | INTEGER |                                                               |
| Single         | ВЕЩЕСТВЕННОЕ ЧИСЛО    |                                                               |
| Строка         | TEXT    | UTF-8                                                         |
| TimeSpan       | TEXT    | d. чч: мм: СС. fffffff                                            |
| UInt16         | INTEGER |                                                               |
| UInt64         | INTEGER | Переполнение больших значений                                         |

## <a name="alternative-types"></a>Альтернативные типы

Некоторые типы .NET можно считывать из альтернативных типов SQLite. Параметры также можно настроить для использования этих альтернативных типов. Дополнительные сведения см. в разделе [Параметры](parameters.md#alternative-types).

| .NET           | SQLite  | Заметки          |
| -------------- | ------- | ---------------- |
| Char           | INTEGER | UTF-16           |
| DateTime       | ВЕЩЕСТВЕННОЕ ЧИСЛО    | Значение юлианского дня |
| DateTimeOffset | ВЕЩЕСТВЕННОЕ ЧИСЛО    | Значение юлианского дня |
| Идентификатор GUID           | BLOB    |                  |
| TimeSpan       | ВЕЩЕСТВЕННОЕ ЧИСЛО    | В днях          |

Например, следующий запрос считывает значение TimeSpan из ДЕЙСТВИТЕЛЬНОго столбца в результирующем наборе.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_AlternativeType)]

## <a name="column-types"></a>Типы столбцов

SQLite использует систему динамического типа, где тип значения связан с самим значением, а не со столбцом, где он хранится. Вы можете использовать любое имя нужного типа столбца. Microsoft. Data. SQLite не применяет дополнительную семантику к этим именам.

Имя типа столбца влияет на [сходство типов](https://www.sqlite.org/datatype3.html#type_affinity). Одна из распространенных проблем заключается в том, что использование типа столбца STRING попытается преобразовать значения в INTEGER или REAL, что может привести к непредвиденным результатам. Рекомендуется использовать только четыре простых имени типа SQLite: INTEGER, REAL, TEXT и BLOB.

SQLite позволяет задавать аспекты типа, такие как длина, точность и масштаб, но они не применяются ядром СУБД. Приложение несет ответственность за их применение.

## <a name="see-also"></a>См. также:

- [Типы в SQLite](https://www.sqlite.org/datatype3.html)