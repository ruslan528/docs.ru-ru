---
title: Метод ICorDebugHeapSegmentEnum::Next
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
ms.openlocfilehash: 89ce4eafa46be3e9ba7cdb06884034a521e43bca
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777538"
---
# <a name="icordebugheapsegmentenumnext-method"></a>Метод ICorDebugHeapSegmentEnum::Next
Возвращает указанное число экземпляров [COR_HEAPOBJECT](cor-heapobject-structure.md) , содержащих сведения о регионах памяти управляемой кучи.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Параметры  
 celt  
 окне Число извлекаемых сегментов.  
  
 сегменты  
 заполняет Массив указателей, каждый из которых указывает на объект [COR_HEAPOBJECT](cor-heapobject-structure.md) , который предоставляет сведения о области памяти в управляемой куче.  
  
 pceltFetched  
 заполняет Указатель на число объектов [COR_HEAPOBJECT](cor-heapobject-structure.md) , фактически возвращаемых в `segments`. Это значение может быть `null`, если параметр `celt` имеет значение 1.  
  
## <a name="remarks"></a>Заметки  
  
## <a name="requirements"></a>Требования  
 **Платформы:** см. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>См. также:

- [Интерфейс ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md)
- [Интерфейсы отладки](debugging-interfaces.md)
