---
ms.openlocfilehash: c0a281b05f453b68495e6fa6fca45f3f36a204a3
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804404"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>Проверка схемы XSD теперь правильно обнаруживает нарушения уникальных ограничений, если используются составные ключи и один ключ пуст

|   |   |
|---|---|
|Подробные сведения|В версиях платформы .NET Framework, предшествовавших версии 4.6, была ошибка, из-за которой проверка XSD не могла обнаруживать уникальные ограничения по составным ключам, если один из ключей был пуст. Эта проблема решена в .NET Framework 4.6. Это приведет к выполнению более правильной проверки, но также может привести к невозможности проверки некоторого XML-кода, которая осуществлялась раньше.|
|Предложение|Если требуется менее строгая проверка .NET Framework 4.0, проверяющее приложение может быть предназначено для версии 4.5 (или более ранней) платформы .NET Framework. Однако при изменении целевой платформы на .NET Framework 4.6 следует выполнить проверку кода, чтобы не проверять повторяющиеся составные ключи (как указано в описании этой проблемы).|
|Область|Пограничный случай|
|Версия|4.6|
|Тип|Изменение целевой платформы|

