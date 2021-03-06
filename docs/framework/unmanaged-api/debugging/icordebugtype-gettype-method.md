---
title: Метод ICorDebugType::GetType
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
ms.openlocfilehash: 25ffbf73fbefbb3c584450283c3080dfc11ee598
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791243"
---
# <a name="icordebugtypegettype-method"></a>Метод ICorDebugType::GetType
Возвращает значение Корелементтипе, которое описывает собственный тип <xref:System.Type> среды CLR, представленный этим объектом ICorDebugType.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `ty`  
 заполняет Указатель на значение перечисления `CorElementType`, указывающее <xref:System.Type> среды CLR, которую представляет этот `ICorDebugType`.  
  
## <a name="remarks"></a>Заметки  
 Если значение `ty` является ELEMENT_TYPE_CLASS или ELEMENT_TYPE_VALUETYPE, можно вызвать метод [ICorDebugType::-Class](icordebugtype-getclass-method.md) , чтобы получить неэкземплярный тип для универсального типа. в противном случае не вызывайте `ICorDebugType::GetClass`.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** см. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
