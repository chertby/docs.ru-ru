---
title: Структура COR_TYPE_LAYOUT
ms.date: 03/30/2017
api_name:
- COR_TYPE_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPE_LAYOUT
helpviewer_keywords:
- COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1793547cfc0d9637352b62ff47beee41e9f5ac5c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740501"
---
# <a name="cortypelayout-structure"></a>Структура COR_TYPE_LAYOUT
Предоставляет сведения о расположении объекта в памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a>Участники  
  
|Член|Описание|  
|------------|-----------------|  
|`parentID`|Идентификатор родительского типа к этому типу. Это будет идентификатор типа NULL (токен1 = 0, токен2 = 0), если идентификатор типа соответствует <xref:System.Object?displayProperty=nameWithType>.|  
|`objectSize`|Размер базового объекта этого типа. Это общий размер для размера объектов, не являющийся переменной.|  
|`numFields`|Число полей, включенных в объекты этого типа.|  
|`boxOffset`|Если этот тип упаковывается, начало смещения полей объекта. Это поле является допустимым только для типов значений, таких как примитивы и структуры.|  
|`type`|CorElementType, к которой принадлежит этот тип.|  
  
## <a name="remarks"></a>Примечания  
 Если `numFields` больше нуля, можно вызвать [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) метод, чтобы получить сведения о полях в этом типе. Если `type` — `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, или `ELEMENT_TYPE_SZARRAY`, размер объектов этого типа является переменной, и вы можете передать [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) структуру [ICorDebugProcess5::GetArrayLayout ](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) метод.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Структуры отладки](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Отладка](../../../../docs/framework/unmanaged-api/debugging/index.md)
