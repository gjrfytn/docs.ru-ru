---
title: "Метод ICorProfilerInfo3::GetFunctionLeave3Info"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetFunctionLeave3Info Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetFunctionLeave3Info
helpviewer_keywords:
- GetFunctionLeave3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionLeave3Info method [.NET Framework profiling]
ms.assetid: df7083d2-fd43-44c7-9ce5-912c25cef0ff
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 04f48562e1ddc07ad1ae166ec44ac7de8afd4312
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="6d565-102">Метод ICorProfilerInfo3::GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="6d565-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>
<span data-ttu-id="6d565-103">Предоставляет кадр стека и возвращаемое значение функции, которая сообщается профилировщику [функция FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) функции.</span><span class="sxs-lookup"><span data-stu-id="6d565-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="6d565-104">Этот метод может быть вызван только во время обратного вызова `FunctionLeave3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="6d565-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d565-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6d565-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d565-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6d565-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="6d565-107">[in] `FunctionID` Функции, которая возвращает.</span><span class="sxs-lookup"><span data-stu-id="6d565-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="6d565-108">[in] Непрозрачный дескриптор, представляющий сведения об указанном кадре стека.</span><span class="sxs-lookup"><span data-stu-id="6d565-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="6d565-109">Профилировщик должен предоставлять тот же `eltInfo` , которому был назначен профилировщику [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) функции.</span><span class="sxs-lookup"><span data-stu-id="6d565-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="6d565-110">[out] Непрозрачный дескриптор, представляющий универсальные сведения об указанном кадре стека.</span><span class="sxs-lookup"><span data-stu-id="6d565-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="6d565-111">Этот дескриптор допустим только во время обратного вызова `FunctionLeave3WithInfo`, в котором профилировщик вызывал метод `GetFunctionLeave3Info`.</span><span class="sxs-lookup"><span data-stu-id="6d565-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="6d565-112">[out] Указатель на [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) структуру, содержащую значение, которое возвращается из функции.</span><span class="sxs-lookup"><span data-stu-id="6d565-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="6d565-113">Для доступа к сведениям возвращаемое значение `COR_PRF_ENABLE_FUNCTION_RETVAL` должен быть установлен флаг.</span><span class="sxs-lookup"><span data-stu-id="6d565-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="6d565-114">Можно использовать профилировщик [метод ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) установить флаги событий.</span><span class="sxs-lookup"><span data-stu-id="6d565-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d565-115">Примечания</span><span class="sxs-lookup"><span data-stu-id="6d565-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d565-116">Требования</span><span class="sxs-lookup"><span data-stu-id="6d565-116">Requirements</span></span>  
 <span data-ttu-id="6d565-117">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d565-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d565-118">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6d565-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6d565-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d565-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d565-120">**Версии платформы .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d565-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d565-121">См. также</span><span class="sxs-lookup"><span data-stu-id="6d565-121">See Also</span></span>  
 [<span data-ttu-id="6d565-122">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="6d565-122">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="6d565-123">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="6d565-123">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="6d565-124">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="6d565-124">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="6d565-125">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="6d565-125">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="6d565-126">Интерфейсы профилирования</span><span class="sxs-lookup"><span data-stu-id="6d565-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="6d565-127">Профилирование</span><span class="sxs-lookup"><span data-stu-id="6d565-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)