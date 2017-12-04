---
title: "Метод ICorDebugProcess5::EnumerateHeapRegions"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateHeapRegions
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1365ed5fd8cf308716b16d78e79a26584bd966c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="e6969-102">Метод ICorDebugProcess5::EnumerateHeapRegions</span><span class="sxs-lookup"><span data-stu-id="e6969-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="e6969-103">Возвращает перечислитель для диапазона памяти управляемой кучи.</span><span class="sxs-lookup"><span data-stu-id="e6969-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6969-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e6969-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6969-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="e6969-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="e6969-106">[out] Указатель на адрес [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) интерфейс объект, который является перечислителем для диапазонов, в которой находятся объекты в управляемой куче памяти.</span><span class="sxs-lookup"><span data-stu-id="e6969-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6969-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="e6969-107">Remarks</span></span>  
 <span data-ttu-id="e6969-108">Перед вызовом метода `ICorDebugProcess5::EnumerateHeapRegions` метод, необходимо вызвать [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) метод и проверьте значение `areGCStructuresValid` поле возвращенного [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Убедитесь, что куче сборщика мусора в ее текущем состоянии перечислимый объект.</span><span class="sxs-lookup"><span data-stu-id="e6969-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="e6969-109">Кроме того `ICorDebugProcess5::EnumerateHeapRegions` возвращает метод `E_FAIL` при присоединении слишком раннем этапе процесса, прежде чем памяти создаются областей.</span><span class="sxs-lookup"><span data-stu-id="e6969-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="e6969-110">Этот метод гарантируется для перечисления всех областей памяти, которые могут содержать управляемые объекты, но не гарантирует фактически управляемые объекты находятся в этих областях.</span><span class="sxs-lookup"><span data-stu-id="e6969-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="e6969-111">[ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) объект коллекции может включать областей памяти пустой или зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="e6969-111">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="e6969-112">[ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) объект интерфейса является стандартным перечислителем производными ICorDebugEnum-интерфейс, позволяющий перечислить [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) объектов.</span><span class="sxs-lookup"><span data-stu-id="e6969-112">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objects.</span></span> <span data-ttu-id="e6969-113">Каждый [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) предоставляет сведения о диапазоне памяти конкретного сегмента, а также создания объектов в этом сегменте.</span><span class="sxs-lookup"><span data-stu-id="e6969-113">Each [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6969-114">Требования</span><span class="sxs-lookup"><span data-stu-id="e6969-114">Requirements</span></span>  
 <span data-ttu-id="e6969-115">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6969-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6969-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6969-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6969-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6969-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6969-118">**Версии платформы .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6969-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6969-119">См. также</span><span class="sxs-lookup"><span data-stu-id="e6969-119">See Also</span></span>  
 [<span data-ttu-id="e6969-120">Интерфейс ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="e6969-120">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="e6969-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="e6969-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)