---
title: "Функция CreateAssemblyEnum"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: CreateAssemblyEnum
helpviewer_keywords: CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c229496a79b146b5dcac3d06fa3efd9237e39d3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="e648a-102">Функция CreateAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="e648a-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="e648a-103">Возвращает указатель на [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) экземпляр, предназначенный для перечисления объектов в сборке с указанным [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e648a-103">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e648a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e648a-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e648a-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="e648a-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="e648a-106">[out] Указатель на область памяти, содержащей запрошенный `IAssemblyEnum` указателя.</span><span class="sxs-lookup"><span data-stu-id="e648a-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="e648a-107">[in] Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="e648a-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="e648a-108">`pUnkReserved`должен быть пустой ссылкой.</span><span class="sxs-lookup"><span data-stu-id="e648a-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="e648a-109">[in] `IAssemblyName` Запрошенной сборки.</span><span class="sxs-lookup"><span data-stu-id="e648a-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="e648a-110">Это имя используется для фильтрации перечисления.</span><span class="sxs-lookup"><span data-stu-id="e648a-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="e648a-111">Он может быть null для перечисления всех сборок в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="e648a-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e648a-112">[in] Флаги для изменения поведения перечислителя.</span><span class="sxs-lookup"><span data-stu-id="e648a-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="e648a-113">Этот параметр содержит ровно один бит из [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) перечисления.</span><span class="sxs-lookup"><span data-stu-id="e648a-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="e648a-114">[in] Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="e648a-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="e648a-115">`pvReserved`должен быть пустой ссылкой.</span><span class="sxs-lookup"><span data-stu-id="e648a-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e648a-116">Примечания</span><span class="sxs-lookup"><span data-stu-id="e648a-116">Remarks</span></span>  
 <span data-ttu-id="e648a-117">`dwFlags` Параметр содержит ровно один бит из `ASM_CACHE_FLAGS` перечисления.</span><span class="sxs-lookup"><span data-stu-id="e648a-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e648a-118">Требования</span><span class="sxs-lookup"><span data-stu-id="e648a-118">Requirements</span></span>  
 <span data-ttu-id="e648a-119">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e648a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e648a-120">**Заголовок:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="e648a-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e648a-121">**Библиотека:** включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e648a-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e648a-122">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e648a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e648a-123">См. также</span><span class="sxs-lookup"><span data-stu-id="e648a-123">See Also</span></span>  
 [<span data-ttu-id="e648a-124">IAssemblyEnum-интерфейс</span><span class="sxs-lookup"><span data-stu-id="e648a-124">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 [<span data-ttu-id="e648a-125">IAssemblyName-интерфейс</span><span class="sxs-lookup"><span data-stu-id="e648a-125">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="e648a-126">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="e648a-126">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)