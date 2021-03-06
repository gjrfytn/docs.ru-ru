---
title: Пользовательский элемент NameValueSectionHandler и DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 3a16952c5cd3759873faeb0fce45b8aa5170b083
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>Пользовательский элемент NameValueSectionHandler и DictionarySectionHandler

Определяет параметры для пользовательских разделов конфигурации, использующие <xref:System.Configuration.NameValueSectionHandler> и <xref:System.Configuration.DictionarySectionHandler> классы.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<sectionName >**

## <a name="attributes"></a>Атрибуты

Нет

## <a name="parent-element"></a>Родительский элемент

|     | Описание |
| --- | ----------- |
| [**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework. |

## <a name="child-elements"></a>Дочерние элементы

|     | Описание |
| --- | ----------- |
| [**\<Добавить >** ](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md) для <xref:System.Configuration.NameValueSectionHandler> и <xref:System.Configuration.DictionarySectionHandler>  | Добавляет пользовательские параметры приложения. |
| [**\<Удалите >** ](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md) для <xref:System.Configuration.NameValueSectionHandler> и <xref:System.Configuration.DictionarySectionHandler> |    Удаляет ранее определенный параметр. |
| [**\<Очистить >** ](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md) для <xref:System.Configuration.NameValueSectionHandler> и <xref:System.Configuration.DictionarySectionHandler> | Удаляет все ранее определенные параметры в разделе. |

## <a name="remarks"></a>Примечания

**\<SectionName >** элемент является пользовательским элементом определяется  **\<раздел >** тегом  **\<configSections >** элемент.

В следующей таблице показаны возвращает тип объекта, метод ConfigurationSettings.GetConfig для каждого обработчика раздела конфигурации:

| Обработчик раздела конфигурации                        | Тип возвращаемого значения                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a>Пример

В следующем примере показан способ объявления разделах, использующих <xref:System.Configuration.DictionarySectionHandler> и <xref:System.Configuration.NameValueSectionHandler> классы. 

Первый элемент пользовательского  **\<dictionarySample >**, который содержит параметры, считываемых <xref:System.Configuration.DictionarySectionHandler> в класс `System.dll` сборки. Второй пользовательский элемент —  **\<mySection >**, который содержит параметры, считываемых <xref:System.Configuration.NameValueSectionHandler> в класс `System.dll` сборки.

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
    <sectionGroup name="mySectionGroup">
      <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a>файл конфигурации

Этот элемент может использоваться в файле конфигурации приложения, файле конфигурации компьютера (*Machine.config*), и *Web.config* файлы, которые находятся не на уровне папки приложения.

## <a name="see-also"></a>См. также

[Схема файла конфигурации для платформы .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
