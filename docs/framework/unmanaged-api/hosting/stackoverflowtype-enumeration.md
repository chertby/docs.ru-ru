---
title: Перечисление StackOverflowType
ms.date: 03/30/2017
api_name:
- StackOverflowType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowType
helpviewer_keywords:
- StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44d5b7fdb2908678671505649bb906c0c5f740e3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751128"
---
# <a name="stackoverflowtype-enumeration"></a>Перечисление StackOverflowType
Содержит значения, указывающие на основную причину события переполнения стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a>Участники  
  
|Член|Описание|  
|------------|-----------------|  
|`SO_ClrEngine`|Переполнение стека было вызвано подсистему выполнения.|  
|`SO_Managed`|Переполнение стека было вызвано управляемого кода.|  
|`SO_Other`|Переполнение стека было вызвано неуправляемого кода.|  
  
## <a name="remarks"></a>Примечания  
 Эти сведения передаются на узел посредством вызова [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) метод.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** MSCorEE.h  
  
 **Библиотека:** MSCorEE.dll  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Размещение перечислений](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
