---
title: Метод ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31766fed66368c044b188b5a58452a5e264a25cb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782201"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a>Метод ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
Задает реализуемые профилировщиком функции, вызываемого на обновленные версии «enter», «проверить» и «tailcall» обработчиков управляемых функций.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a>Параметры  
 `pFuncEnter`  
 [in] Указатель на реализацию для использования в качестве [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) обратного вызова.  
  
 `pFuncLeave`  
 [in] Указатель на реализацию для использования в качестве [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) обратного вызова.  
  
 `pFuncTailcall`  
 [in] Указатель на реализацию для использования в качестве [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) обратного вызова.  
  
## <a name="remarks"></a>Примечания  
 `SetEnterLeaveFunctionHooks2` Метод аналогичен методу [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) метод. Первый вариант используется для указания функции для использования в качестве более новых версиях enter/leave/tailcall обратные вызовы, а второй – для указания функции для использования в качестве более старых версиях enter/leave/tailcall обратных вызовов.  
  
 Одновременно может быть активным только один набор обратных вызовов. Таким образом Если профилировщик вызывает оба `ICorProfilerInfo::SetEnterLeaveFunctionHooks` и `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` используется.  
  
 `SetEnterLeaveFunctionHooks2` Метод может вызываться только из профилировщика [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) обратного вызова.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Интерфейс ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
