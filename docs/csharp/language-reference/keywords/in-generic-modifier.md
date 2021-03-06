---
title: Справочник по C#. Универсальный модификатор in
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 57da13f6dc6719166b9051afeb2532ba5fbeff3a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713485"
---
# <a name="in-generic-modifier-c-reference"></a>in (универсальный модификатор) (Справочник по C#)

Для параметров универсального типа ключевое слово `in` указывает, что параметр типа является контравариантным. Ключевое слово `in` может применяться в универсальных интерфейсах и делегатах.

Контравариантность позволяет использовать производные типы со степенью наследования меньше, чем у типа, заданного универсальным параметром. Благодаря этому можно осуществлять неявное преобразование классов, реализующих контравариантные интерфейсы, и неявное преобразование типов делегатов. Ковариантность и контравариантность поддерживаются для ссылочных типов, но не для типов значений.

Тип может быть объявлен контравариантным в универсальном интерфейсе или делегате, только если он определяет тип параметров метода, но не тип значения, возвращаемого методом. Параметры `In`, `ref` и `out` должны быть инвариантными, то есть не являться ковариантными или контравариантными.

Интерфейс с параметром контравариантного типа позволяет своим методам принимать аргументы производных типов, степень наследования у которых меньше, чем у параметра типа интерфейса. Например, в интерфейсе <xref:System.Collections.Generic.IComparer%601> тип T является контравариантным, поэтому можно присвоить объект типа `IComparer<Person>` объекту типа `IComparer<Employee>` без применения каких-либо специальных методов преобразования, если `Employee` наследует `Person`.

Контравариантный делегат может быть назначен другому делегату того же типа, но с производным параметром универсального типа меньшей степени.

Дополнительные сведения см. в разделе [Ковариация и контравариантность](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="contravariant-generic-interface"></a>Контравариантный универсальный интерфейс

В следующем примере показано, как объявить, расширить и реализовать контравариантный универсальный интерфейс. В нем также показано, как можно использовать неявное преобразование для классов, реализующих этот интерфейс.

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a>Контравариантный универсальный делегат

В следующем примере кода показано, как объявить контравариантный универсальный делегат. В нем также показано, как можно выполнить неявное преобразование типа делегата.

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a>Спецификация языка C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>См. также

- [out](out-generic-modifier.md)
- [Ковариация и контрвариантность](../../programming-guide/concepts/covariance-contravariance/index.md)
- [Модификаторы](index.md)
