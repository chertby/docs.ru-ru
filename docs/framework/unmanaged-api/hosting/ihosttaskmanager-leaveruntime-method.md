---
title: Метод IHostTaskManager::LeaveRuntime
ms.date: 03/30/2017
api_name:
- IHostTaskManager.LeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 959cb541013ca0a26557e849874dbb329489d855
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749533"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a>Метод IHostTaskManager::LeaveRuntime
Уведомляет основное приложение, что текущая выполняющаяся задача сейчас оставьте общеязыковой среды выполнения (CLR) и введите неуправляемого кода.  
  
> [!IMPORTANT]
>  Соответствующего вызова [IHostTaskManager::EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) Уведомляет основное приложение, что текущая выполняющаяся задача является повторное введение управляемого кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `target`  
 [in] Адрес в сопоставленной переносимый исполняемый файл для вызова неуправляемой функции.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
|HRESULT|Описание|  
|-------------|-----------------|  
|S_OK|`LeaveRuntime` успешно возвращен.|  
|ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE|Среда CLR не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.|  
|HOST_E_TIMEOUT|Истекло время ожидания вызова.|  
|HOST_E_NOT_OWNER|Вызывающий объект не является владельцем блокировки.|  
|HOST_E_ABANDONED|Событие было отменено с сохранением заблокированный поток или ожидал волокон.|  
|E_FAIL|Неизвестный Разрушительный сбой. Когда метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе. Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Недостаточно памяти для завершения запрошенного выделения.|  
  
## <a name="remarks"></a>Примечания  
 Последовательность вызовов к и из неуправляемого кода могут быть вложенными. Например, следующий список содержит гипотетическую ситуацию, в котором последовательность вызовов к `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), и `IHostTaskManager::EnterRuntime` позволяет основному приложению определить вложенные слои.  
  
|Действие|Вызов соответствующего метода|  
|------------|-------------------------------|  
|Управляемый исполняемый файл вызывает Visual Basic вызова неуправляемой функции, написанные на языке C с помощью платформы.|`IHostTaskManager::LeaveRuntime`|  
|Неуправляемая функция C вызывает метод в управляемую библиотеку DLL, написанные на C#.|`IHostTaskManager::ReverseEnterRuntime`|  
|Управляемый C# функция вызывает другую неуправляемую функцию, написанную на языке C, также использование вызов платформ.|`IHostTaskManager::LeaveRuntime`|  
|Второй неуправляемая функция возвращает результат выполнения для C# функции.|`IHostTaskManager::EnterRuntime`|  
|C# Функции возвращает результат выполнения первой неуправляемой функции.|`IHostTaskManager::ReverseLeaveRuntime`|  
|Первая неуправляемая функция возвращает выполнение программы на Visual Basic.|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** MSCorEE.h  
  
 **Библиотека:** Включена как ресурс в MSCorEE.dll  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [Интерфейс ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [Интерфейс IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [Интерфейс IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
