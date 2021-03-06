---
title: Функция StrongNameSignatureVerificationFromImage
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 919c746b738246d76e90730c42882bfdd3ac6edc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="strongnamesignatureverificationfromimage-function"></a>Функция StrongNameSignatureVerificationFromImage
Проверяет допустимость сборки, который уже сопоставлен в памяти для связанного открытого ключа.  
  
 Эта функция устарела. Используйте [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) метод вместо него.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbBase`  
 [in] Относительный виртуальный адрес сопоставленных манифест.  
  
 `dwLength`  
 [in] Размер в байтах, сопоставленные изображения.  
  
 `dwInFlags`  
 [in] Флаги, которые влияют на поведение проверки. Поддерживаются следующие значения:  
  
-   `SN_INFLAG_FORCE_VER` (0x00000001) — принудительная проверка, даже если это необходимо переопределить параметры реестра.  
  
-   `SN_INFLAG_INSTALL` (0x00000002) — указывает, что это первая проверка, выполняемая для данного образа.  
  
-   `SN_INFLAG_ADMIN_ACCESS` (0x00000004) — указывает, что кэш будет предоставлять доступ только пользователям с правами администратора.  
  
-   `SN_INFLAG_USER_ACCESS` (0x00000008) — указывает, что сборка будет доступен только для текущего пользователя.  
  
-   `SN_INFLAG_ALL_ACCESS` (0x00000010) — указывает, что кэш будет предоставляют никаких гарантий ограничения доступа.  
  
-   `SN_INFLAG_RUNTIME` (0x80000000) — зарезервировано для внутренней отладки.  
  
 `pdwOutFlags`  
 [out] Флаг для дополнительных выходных данных. Поддерживается следующее значение:  
  
-   `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) — это значение равно `false` для указания, что проверка прошла успешно из-за параметров реестра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 `true` При успешном завершении; в противном случае `false`.  
  
## <a name="remarks"></a>Примечания  
 Если `StrongNameSignatureVerificationFromImage` функция не завершена, вызовите [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) функции для получения последнего формируемой ошибки.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** StrongName.h  
  
 **Библиотека:** включена как ресурс в mscoree.dll  
  
 **Версии платформы .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод StrongNameSignatureVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)  
 [Интерфейс ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
