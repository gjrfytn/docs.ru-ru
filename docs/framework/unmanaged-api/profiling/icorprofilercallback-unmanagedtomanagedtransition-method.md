---
title: Метод ICorProfilerCallback::UnmanagedToManagedTransition
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.UnmanagedToManagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c6bd0c9796fa2c5d8eff8dfb9d3fa3f707ce4761
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a>Метод ICorProfilerCallback::UnmanagedToManagedTransition
Уведомляет профилировщик о переход от неуправляемого кода в управляемый код.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
#### <a name="parameters"></a>Параметры  
 `functionId`  
 [in] Идентификатор функции, которая вызывается.  
  
 `reason`  
 [in] Значение [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) перечисления, которое указывает, произошло из-за вызова управляемого кода из неуправляемого кода или из-за возврат из неуправляемой функции, вызываемой управляемыми перехода.  
  
## <a name="remarks"></a>Примечания  
 Если значение `reason` — COR_PRF_TRANSITION_RETURN и `functionId` не равно NULL, функция ID будет соответствовать неуправляемой функции и никогда не будет выполняться компиляция с помощью время JIT-компилятора. Неуправляемые функции имеют некоторые основные сведения, связанные с ними, такие как имя и некоторые метаданные.  
  
 Если значение `reason` является COR_PRF_TRANSITION_CALL, возможно, вызываемой функции (то есть, управляемую функцию) еще не JIT-компиляции.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Интерфейс ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Метод ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)  
 [Использование явного вызова Pinvoke в C++ (атрибут DllImport)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)  
 [Использование взаимодействия языка C++ (неявный PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
