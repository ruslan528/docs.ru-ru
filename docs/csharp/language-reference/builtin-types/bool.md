---
title: Тип bool. Справочник по C#
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 720ece2f7f47961e0ab6ebf03c8afeb5fa3a6271
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093270"
---
# <a name="bool-c-reference"></a>bool (справочник по C#)

Ключевое слово типа `bool` — это псевдоним для типа структуры <xref:System.Boolean?displayProperty=nameWithType> .NET, представляющий логическое значение: `true` или `false`.

Для выполнения логических операций со значениями типа `bool` используйте [логические](../operators/boolean-logical-operators.md) операторы. Тип `bool` является типом результата операторов [сравнения](../operators/comparison-operators.md) и [равенства](../operators/equality-operators.md). Выражение `bool` может быть управляющим условным выражением в операторах [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md) и [for](../keywords/for.md) и [условном операторе `?:`](../operators/conditional-operator.md).

Значение по умолчанию для типа `bool` — `false`.

## <a name="literals"></a>Литералы

Вы можете использовать литералы `true` и `false` для инициализации переменной `bool` или передачи значения `bool`:

[!code-csharp-interactive[bool literals](~/samples/csharp/language-reference/builtin-types/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a>Трехзначная булева логика

Используйте тип `bool?`, допускающий значение NULL, если нужно использовать трехзначную логику, например, при работе с базами данных, которые поддерживают трехзначный логический тип. Для операндов `bool?` предопределенные операторы `&` и `|` поддерживают троичную логику. См. подробнее о [логических операторах, поддерживающих значение NULL](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) в описании [логических операторов](../operators/boolean-logical-operators.md).

См. дополнительные сведения о [типах значений, допускающих значение NULL](nullable-value-types.md).

## <a name="conversions"></a>Преобразования

В C# доступно только два преобразования, использующих тип `bool`. Это неявное преобразование в соответствующий тип `bool?`, допускающий значение NULL, и явное преобразование из типа `bool?`. Однако .NET предоставляет дополнительные методы, позволяющие выполнять преобразование в тип `bool` или из него. Дополнительные сведения см. в разделе о [преобразовании в логические значения и из них](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) справочника по API <xref:System.Boolean?displayProperty=nameWithType>.

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в разделе [Тип bool](~/_csharplang/spec/types.md#the-bool-type)[спецификации языка C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>См. также

- [справочник по C#](../index.md)
- [Типы значений](value-types.md)
- [Операторы true и false](../operators/true-false-operators.md)
