---
title: "Метод IHostThreadPoolManager::SetMinThreads"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.SetMinThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ab0b107c050b1c4b686f761ede75ea2349825270
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="480c6-102">Метод IHostThreadPoolManager::SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="480c6-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="480c6-103">Задает минимальное количество свободных потоков, которые должен поддерживать узла обработки запросов.</span><span class="sxs-lookup"><span data-stu-id="480c6-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="480c6-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="480c6-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="480c6-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="480c6-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="480c6-106">[in] Новый минимальное количество потоков, которые необходимо обслуживать основное приложение.</span><span class="sxs-lookup"><span data-stu-id="480c6-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="480c6-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="480c6-107">Return Value</span></span>  
  
|<span data-ttu-id="480c6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="480c6-108">HRESULT</span></span>|<span data-ttu-id="480c6-109">Описание</span><span class="sxs-lookup"><span data-stu-id="480c6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="480c6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="480c6-110">S_OK</span></span>|<span data-ttu-id="480c6-111">`SetMinThreads`успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="480c6-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="480c6-112">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="480c6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="480c6-113">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="480c6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="480c6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="480c6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="480c6-115">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="480c6-115">The call timed out.</span></span>|  
|<span data-ttu-id="480c6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="480c6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="480c6-117">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="480c6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="480c6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="480c6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="480c6-119">Событие было отменено заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="480c6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="480c6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="480c6-120">E_FAIL</span></span>|<span data-ttu-id="480c6-121">Неизвестная Неустранимая ошибка.</span><span class="sxs-lookup"><span data-stu-id="480c6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="480c6-122">Если метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="480c6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="480c6-123">Последующие вызовы размещение методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="480c6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="480c6-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="480c6-124">E_NOTIMPL</span></span>|<span data-ttu-id="480c6-125">Узел не предоставляет реализацию `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="480c6-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="480c6-126">Примечания</span><span class="sxs-lookup"><span data-stu-id="480c6-126">Remarks</span></span>  
 <span data-ttu-id="480c6-127">Узел не требуется предоставлять реализацию `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="480c6-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="480c6-128">В этом случае он должен возвращать значение HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="480c6-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="480c6-129">Требования</span><span class="sxs-lookup"><span data-stu-id="480c6-129">Requirements</span></span>  
 <span data-ttu-id="480c6-130">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="480c6-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="480c6-131">**Заголовок:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="480c6-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="480c6-132">**Библиотека:** включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="480c6-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="480c6-133">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="480c6-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="480c6-134">См. также</span><span class="sxs-lookup"><span data-stu-id="480c6-134">See Also</span></span>  
 <xref:System.Threading.ThreadPool.SetMinThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="480c6-135">Метод GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="480c6-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)  
 [<span data-ttu-id="480c6-136">Метод SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="480c6-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="480c6-137">IHostThreadPoolManager-интерфейс</span><span class="sxs-lookup"><span data-stu-id="480c6-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)