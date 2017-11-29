---
title: "Метод IMetaDataImport::GetPinvokeMap"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetPinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: adb6a9a5f53dcfd8ada5b3aa9d75daac18d50283
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="dcbf6-102">Метод IMetaDataImport::GetPinvokeMap</span><span class="sxs-lookup"><span data-stu-id="dcbf6-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="dcbf6-103">Возвращает токен ModuleRef, представляющий целевую сборку вызова PInvoke.</span><span class="sxs-lookup"><span data-stu-id="dcbf6-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcbf6-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dcbf6-104">Syntax</span></span>  
  
```  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dcbf6-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcbf6-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="dcbf6-106">[in] Маркер FieldDef или MethodDef, чтобы получить метаданные сопоставления PInvoke для.</span><span class="sxs-lookup"><span data-stu-id="dcbf6-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="dcbf6-107">[out] Указатель флаги, используемые для сопоставления.</span><span class="sxs-lookup"><span data-stu-id="dcbf6-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="dcbf6-108">Это значение является битовой [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) перечисления.</span><span class="sxs-lookup"><span data-stu-id="dcbf6-108">This value is a bitmask from the [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="dcbf6-109">[out] Имя целевой неуправляемые библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="dcbf6-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="dcbf6-110">[in] Размер в расширенных символах с `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="dcbf6-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="dcbf6-111">[out] Число расширенных символов, возвращаемых в `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="dcbf6-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="dcbf6-112">[out] Указатель на токен ModuleRef, представляющий неуправляемый целевой объект библиотеки.</span><span class="sxs-lookup"><span data-stu-id="dcbf6-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcbf6-113">Требования</span><span class="sxs-lookup"><span data-stu-id="dcbf6-113">Requirements</span></span>  
 <span data-ttu-id="dcbf6-114">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcbf6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcbf6-115">**Заголовок:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dcbf6-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dcbf6-116">**Библиотека:** включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dcbf6-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dcbf6-117">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcbf6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcbf6-118">См. также</span><span class="sxs-lookup"><span data-stu-id="dcbf6-118">See Also</span></span>  
 [<span data-ttu-id="dcbf6-119">IMetaDataImport-интерфейс</span><span class="sxs-lookup"><span data-stu-id="dcbf6-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="dcbf6-120">IMetaDataImport2-интерфейс</span><span class="sxs-lookup"><span data-stu-id="dcbf6-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)