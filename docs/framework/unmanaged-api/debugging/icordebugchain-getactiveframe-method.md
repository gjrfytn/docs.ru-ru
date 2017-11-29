---
title: "Метод ICorDebugChain::GetActiveFrame"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetActiveFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b5de327c1579d05f6ae4a440fc76a3fb9ee99b13
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="fee91-102">Метод ICorDebugChain::GetActiveFrame</span><span class="sxs-lookup"><span data-stu-id="fee91-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="fee91-103">Получает активный (то есть последней) кадра в цепочке.</span><span class="sxs-lookup"><span data-stu-id="fee91-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fee91-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fee91-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fee91-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="fee91-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="fee91-106">[out] Указатель на адрес объекта ICorDebugFrame, представляющий активный (то есть самые последние) кадра в цепочке.</span><span class="sxs-lookup"><span data-stu-id="fee91-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fee91-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="fee91-107">Remarks</span></span>  
 <span data-ttu-id="fee91-108">Если не управляемый кадр стека, `ppFrame` задано значение null.</span><span class="sxs-lookup"><span data-stu-id="fee91-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="fee91-109">Если активная рамка не доступен, то вызов завершится успешно и `ppFrame` будет иметь значение null.</span><span class="sxs-lookup"><span data-stu-id="fee91-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="fee91-110">Активные кадры не будет доступен для запуска из-за CHAIN_ENTER_UNMANAGED цепочек, а также для некоторых цепей, инициированных из-за CHAIN_CLASS_INIT.</span><span class="sxs-lookup"><span data-stu-id="fee91-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="fee91-111">См. Перечисление CorDebugChainReason.</span><span class="sxs-lookup"><span data-stu-id="fee91-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fee91-112">Требования</span><span class="sxs-lookup"><span data-stu-id="fee91-112">Requirements</span></span>  
 <span data-ttu-id="fee91-113">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fee91-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fee91-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fee91-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fee91-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fee91-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fee91-116">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fee91-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>