---
title: 'Метод ICorDebugVariableHome:: с кодом'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetCode
helpviewer_keywords:
- ICorDebugVariableHome::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: ef002890-4a7b-4a5d-abbf-16c60083f794
topic_type:
- apiref
ms.openlocfilehash: fdfa38a4cdbbaad2fc2c987a10a122af4a1fc9a9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791040"
---
# <a name="icordebugvariablehomegetcode-method"></a>Метод ICorDebugVariableHome:: с кодом
Возвращает экземпляр "ICorDebugCode", который содержит этот объект [ICorDebugVariableHome](icordebugvariablehome-interface.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `ppCode`  
 заполняет Указатель на адрес экземпляра ICorDebugCode, который содержит этот объект [ICorDebugVariableHome](icordebugvariablehome-interface.md) .  
  
## <a name="requirements"></a>Требования  
 **Платформы:** см. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>См. также:

- [Интерфейс ICorDebugVariableHome](icordebugvariablehome-interface.md)
