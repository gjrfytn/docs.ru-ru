---
title: Метод ICorRuntimeHost::CreateEvidence
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a06d57348cfbdfb8bb57580a48e54e298e27e166
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="icorruntimehostcreateevidence-method"></a>Метод ICorRuntimeHost::CreateEvidence
Получает указатель интерфейса типа <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, что позволяет узлу создавать свидетельством безопасности для передачи [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) или [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pEvidence`  
 [out] Указатель на интерфейс для <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> экземпляр, используемый для создания свидетельством безопасности. Этот указатель является типизированным `IUnknown`, поэтому обычно следует вызывать вызывающим объектам `QueryInterface` на этот интерфейс для получения указателя на <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
|HRESULT|Описание|  
|-------------|-----------------|  
|S_OK|Операция выполнена успешно.|  
|S_FALSE|Не удалось завершить операцию.|  
|E_FAIL|Неизвестный, Разрушительный сбой. Если метод вернет значение E_FAIL, общеязыковой среды выполнения (CLR) больше не может использоваться в процессе. Последующие вызовы любых размещающих интерфейсов API, возвращают значение HOST_E_CLRNOTAVAILABLE.|  
|ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE|Среда CLR не загружена в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает пустую коллекцию, которую нельзя заполнить из машинного кода. Следует использовать <xref:System.Security.Policy.Evidence> метод вместо него.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** MSCorEE.h  
  
 **Библиотека:** включена как ресурс в MSCorEE.dll  
  
 **Версия платформы .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>См. также  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [Интерфейс ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
