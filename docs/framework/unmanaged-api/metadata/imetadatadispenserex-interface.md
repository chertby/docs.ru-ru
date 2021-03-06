---
title: Интерфейс IMetaDataDispenserEx
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96475086b1244ae75ed692dd10cb693af0be9af7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992606"
---
# <a name="imetadatadispenserex-interface"></a>Интерфейс IMetaDataDispenserEx
Расширяет [интерфейс IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) интерфейс, чтобы предоставить возможность контролировать работу API метаданных в текущей области метаданных.  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод FindAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|Этот метод не реализован. При вызове, он возвращает E_NOTIMPL.|  
|[Метод FindAssemblyModule](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|Этот метод не реализован. При вызове, он возвращает E_NOTIMPL.|  
|[Метод GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|Получает каталог, содержащий текущий среда CLR (CLR). Этот метод поддерживается только для использования вне процесса отладки. Если вызывается из другого компонента, он возвращает E_NOTIMPL.|  
|[Метод GetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|Получает значение указанного параметра в текущей области метаданных. Параметр определяет, как обрабатываются вызовы к текущей области метаданных.|  
|[Метод OpenScopeOnITypeInfo](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|Этот метод не реализован. При вызове, он возвращает E_NOTIMPL.|  
|[Метод SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|Задает указанному параметру заданное значение для текущей области метаданных. Параметр определяет, как обрабатываются вызовы к текущей области метаданных.|  
  
## <a name="requirements"></a>Требования  
 **Платформа:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** Cor.h  
  
 **Библиотека:** Используется как ресурс в MsCorEE.dll  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейсы метаданных](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [Интерфейс IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [Интерфейс IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Интерфейс IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
