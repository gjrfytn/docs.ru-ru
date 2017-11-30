---
title: "Перечисление CorCallingConvention"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorCallingConvention
api_location: mscoree.dll
api_type: COM
f1_keywords: CorCallingConvention
helpviewer_keywords: CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8c0fbbb5f2c8f73cb6c76137263fa457840cdddc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="01c89-102">Перечисление CorCallingConvention</span><span class="sxs-lookup"><span data-stu-id="01c89-102">CorCallingConvention Enumeration</span></span>
<span data-ttu-id="01c89-103">Содержит значения, описывающие типы соглашений о вызовах, выполняемых в управляемом коде.</span><span class="sxs-lookup"><span data-stu-id="01c89-103">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01c89-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="01c89-104">Syntax</span></span>  
  
```  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="01c89-105">Члены</span><span class="sxs-lookup"><span data-stu-id="01c89-105">Members</span></span>  
  
|<span data-ttu-id="01c89-106">Член</span><span class="sxs-lookup"><span data-stu-id="01c89-106">Member</span></span>|<span data-ttu-id="01c89-107">Описание</span><span class="sxs-lookup"><span data-stu-id="01c89-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="01c89-108">Указывает значение по умолчанию, соглашение о вызовах.</span><span class="sxs-lookup"><span data-stu-id="01c89-108">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="01c89-109">Указывает, что метод принимает переменное число параметров.</span><span class="sxs-lookup"><span data-stu-id="01c89-109">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="01c89-110">Указывает, что вызов к полю.</span><span class="sxs-lookup"><span data-stu-id="01c89-110">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="01c89-111">Указывает, что вызов локального метода.</span><span class="sxs-lookup"><span data-stu-id="01c89-111">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="01c89-112">Указывает, что вызов к свойству.</span><span class="sxs-lookup"><span data-stu-id="01c89-112">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="01c89-113">Указывает, что вызов является неуправляемым.</span><span class="sxs-lookup"><span data-stu-id="01c89-113">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="01c89-114">Указывает на создание экземпляров универсального метода.</span><span class="sxs-lookup"><span data-stu-id="01c89-114">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="01c89-115">Указывает метод, который принимает переменное число параметров вызова PInvoke 64-разрядной.</span><span class="sxs-lookup"><span data-stu-id="01c89-115">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="01c89-116">Описывает недопустимое 4-разрядное значение.</span><span class="sxs-lookup"><span data-stu-id="01c89-116">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="01c89-117">Указывает, что соглашение о вызове описывается четырьмя младшими битами.</span><span class="sxs-lookup"><span data-stu-id="01c89-117">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="01c89-118">Указывает, что старшие биты описывают `this` параметра.</span><span class="sxs-lookup"><span data-stu-id="01c89-118">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="01c89-119">Указывает, что `this` параметр четко описаны в сигнатуре.</span><span class="sxs-lookup"><span data-stu-id="01c89-119">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="01c89-120">Указывает сигнатуру универсального метода с явной количество аргументов типа.</span><span class="sxs-lookup"><span data-stu-id="01c89-120">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="01c89-121">Это предшествует обычное число параметров.</span><span class="sxs-lookup"><span data-stu-id="01c89-121">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="01c89-122">Требования</span><span class="sxs-lookup"><span data-stu-id="01c89-122">Requirements</span></span>  
 <span data-ttu-id="01c89-123">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01c89-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01c89-124">**Заголовок:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="01c89-124">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="01c89-125">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01c89-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01c89-126">См. также</span><span class="sxs-lookup"><span data-stu-id="01c89-126">See Also</span></span>  
 [<span data-ttu-id="01c89-127">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="01c89-127">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)