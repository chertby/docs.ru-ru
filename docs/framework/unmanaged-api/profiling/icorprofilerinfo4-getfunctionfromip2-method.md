---
title: Метод ICorProfilerInfo4::GetFunctionFromIP2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7281f1aa0da417eba618b748ac68ba1fefb4907d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780857"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a>Метод ICorProfilerInfo4::GetFunctionFromIP2
Сопоставляет указатель инструкции управляемого кода для перекомпиляции JIT версию функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a>Параметры  
 `ip`  
 [in] Указатель инструкций в управляемом коде.  
  
 `pFunctionId`  
 [out] Идентификатор функции.  
  
 `pReJitId`  
 [out] Идентификация версию функции перекомпиляции JIT.  
  
## <a name="remarks"></a>Примечания  
 `GetFunctionFromIP2` аналогичен `GetFunctionFromIP`, за исключением того, что он получает идентификатор перекомпиляции JIT, а не идентификатор функции, функции, которая содержит указанный IP-адрес.  
  
> [!NOTE]
>  `GetFunctionFromIP2` можно запустить сбор мусора, тогда как `GetFunctionFromIP` не будет.  Дополнительные сведения см. в разделе [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
