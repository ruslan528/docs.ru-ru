---
title: Метод EnumImportTypes
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
ms.openlocfilehash: ca7c7570aff63aa328dddc0626648fa74397addc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448737"
---
# <a name="enumimporttypes-method"></a>Метод EnumImportTypes

Перечисляет каждый тип в каждой области.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a>Параметры

`hEnum`\
Обработчик для перечислителя.

`dwMax`\
Максимальное число извлекаемых типов.

`aTypeDefs`\
Получает токены типа, не превышающие `dwMax`.

`pdwCount`\
Получает фактическое число типов в `aTypeDefs`.

## <a name="return-value"></a>Возвращаемое значение

Возвращает S_OK, если метод завершается с ошибкой.

## <a name="requirements"></a>Требования

Требуется ALink. h

## <a name="see-also"></a>См. также

- [Интерфейс IALink](ialink-interface.md)
- [Интерфейс IALink2](ialink2-interface.md)
- [API ALink](index.md)
