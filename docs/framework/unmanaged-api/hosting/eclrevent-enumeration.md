---
title: "Перечисление EClrEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrEvent
helpviewer_keywords: EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0585cea00865f4798c57ef5276076c2b0a5ff284
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="505d6-102">Перечисление EClrEvent</span><span class="sxs-lookup"><span data-stu-id="505d6-102">EClrEvent Enumeration</span></span>
<span data-ttu-id="505d6-103">Описывает распространенные события языка среды CLR, для которых узел может регистрировать обратные вызовы.</span><span class="sxs-lookup"><span data-stu-id="505d6-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="505d6-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="505d6-104">Syntax</span></span>  
  
```  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="505d6-105">Члены</span><span class="sxs-lookup"><span data-stu-id="505d6-105">Members</span></span>  
  
|<span data-ttu-id="505d6-106">Член</span><span class="sxs-lookup"><span data-stu-id="505d6-106">Member</span></span>|<span data-ttu-id="505d6-107">Описание</span><span class="sxs-lookup"><span data-stu-id="505d6-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="505d6-108">Задает неустранимую ошибку среды CLR.</span><span class="sxs-lookup"><span data-stu-id="505d6-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="505d6-109">Задает, выгрузкой конкретной <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="505d6-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="505d6-110">Указывает, что сообщение управляемого помощника по отладке (MDA) был создан.</span><span class="sxs-lookup"><span data-stu-id="505d6-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="505d6-111">Указывает, что произошла ошибка переполнения стека.</span><span class="sxs-lookup"><span data-stu-id="505d6-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="505d6-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="505d6-112">Remarks</span></span>  
 <span data-ttu-id="505d6-113">Узел может регистрировать обратные вызовы для любых типов событий, описываемого `EClrEvent` путем вызова методов [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) интерфейса.</span><span class="sxs-lookup"><span data-stu-id="505d6-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="505d6-114">Узел получает указатель на этот интерфейс путем вызова [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="505d6-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="505d6-115">`Event_CLRDisabled` И `Event_DomainUnload` события может вызываться несколько раз и из разных потоков, чтобы сообщить о выгрузке или отключении среды CLR.</span><span class="sxs-lookup"><span data-stu-id="505d6-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="505d6-116">`Event_MDAFired` Событие вызывает создание [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) экземпляр, содержащий сведения о сообщении MDA.</span><span class="sxs-lookup"><span data-stu-id="505d6-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="505d6-117">Дополнительные сведения о помощниках MDA см. в разделе [Диагностика ошибок посредством управляемых помощников по отладке](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="505d6-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="505d6-118">Требования</span><span class="sxs-lookup"><span data-stu-id="505d6-118">Requirements</span></span>  
 <span data-ttu-id="505d6-119">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="505d6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="505d6-120">**Заголовок:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="505d6-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="505d6-121">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="505d6-121">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="505d6-122">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="505d6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="505d6-123">См. также</span><span class="sxs-lookup"><span data-stu-id="505d6-123">See Also</span></span>  
 [<span data-ttu-id="505d6-124">IActionOnCLREvent-интерфейс</span><span class="sxs-lookup"><span data-stu-id="505d6-124">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="505d6-125">ICLRControl-интерфейс</span><span class="sxs-lookup"><span data-stu-id="505d6-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="505d6-126">Перечисления размещения</span><span class="sxs-lookup"><span data-stu-id="505d6-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)