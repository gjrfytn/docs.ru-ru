---
title: Размещение сборок
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6a10a896494304b9c3c17bc320464a8273e430d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="assembly-placement"></a>Размещение сборок
Для большинства приложений .NET Framework сборки, составляющие приложение, располагаются в папке приложения, во вложенной папке этой папки или в глобальном кэше сборок (если сборка является совместно используемой). С помощью [элемента \<codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) в файле конфигурации можно изменить место, где среда CLR будет искать сборки. Если у сборки нет строгого имени, то расположение, которое указывается с помощью [элемента \<codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md), ограничивается папкой приложения или вложенной папкой этой папки. Если у сборки есть строгое имя, то [элемент \<codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) может указывать любое расположение на компьютере или в сети.  
  
 Аналогичные правила применяются к расположению сборок при работе с неуправляемым кодом или с приложениями, реализующими COM-взаимодействие: если сборка совместно используется несколькими приложениями, то она должна устанавливаться в глобальный кэш сборок. При использовании сборок с неуправляемым кодом их необходимо экспортировать в виде библиотеки типов и зарегистрировать. Сборки, использующиеся для обеспечения COM-взаимодействия, должны регистрироваться в каталоге, хотя в некоторых случаях такая регистрация производится автоматически.  
  
## <a name="see-also"></a>См. также  
 [Обнаружение сборок в среде выполнения](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Настройка приложений](../../../docs/framework/configure-apps/index.md)  
 [Расширенное COM-взаимодействие](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [Сборки в среде CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
