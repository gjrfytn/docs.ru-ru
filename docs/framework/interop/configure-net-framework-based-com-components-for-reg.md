---
title: Практическое руководство. Настройка COM-компонентов на основе платформы .NET Framework для активации без регистрации
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 744ce1f2810eee025f071cafaa71e473b6ed4c50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a>Практическое руководство. Настройка COM-компонентов на основе платформы .NET Framework для активации без регистрации
Активация компонентов на основе платформы .NET Framework без регистрации осуществляется лишь немного сложнее, чем для COM-компонентов. При установке требуются два манифеста:  
  
-   Для определения управляемого компонента в COM-приложениях используется манифест приложения в стиле Win32.  
  
-   Компоненты на основе платформы .NET Framework используют манифест компонента для получения необходимых для активации сведений во время выполнения.  
  
 В этом разделе описывается, как связать манифест приложения с приложением, манифест компонента с компонентом и внедрить манифест компонента в сборку.  
  
### <a name="to-create-an-application-manifest"></a>Создание манифеста приложения  
  
1.  С помощью редактора XML создайте (или измените) манифест приложения, принадлежащий COM-приложению, которое взаимодействует с одним или несколькими управляемыми компонентами.  
  
2.  Вставьте следующий стандартный заголовок в начало файла:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     Сведения об элементах манифеста и их атрибутов см. в разделе [манифесты приложения](https://msdn.microsoft.com/library/windows/desktop/aa374191.aspx).  
  
3.  Определите владельца манифеста. В следующем примере владельцем файла манифеста является `myComApp` версии 1.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4.  Определите зависимые сборки. В следующем примере `myComApp` зависит от `myManagedComp`.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="x86"   
                        publicKeyToken="8275b28176rcbbef"  
      />  
      <dependency>  
        <dependentAssembly>  
          <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myManagedComp"   
                        version="6.0.0.0"   
                        processorArchitecture="X86"   
                        publicKeyToken="8275b28176rcbbef"  
          />  
        </dependentAssembly>  
      </dependency>  
    </assembly>  
    ```  
  
5.  Сохраните файл манифеста под соответствующим именем. Имя манифеста приложения состоит из имени исполняемого файла сборки и расширения manifest. Например, для приложения myComApp.exe файл манифеста будет носить имя myComApp.exe.manifest.  
  
 Манифест приложения можно установить в тот же каталог, что и COM-приложение. Также его можно добавить в качестве ресурса в EXE-файл приложения. За дополнительной информацией, Дополнительные сведения см. в разделе [о сборках Side-by-Side](https://msdn.microsoft.com/library/windows/desktop/ff951640.aspx).  
  
#### <a name="to-create-a-component-manifest"></a>Создание манифеста компонента  
  
1.  С помощью редактора XML создайте манифест компонента, описывающий управляемую сборку.  
  
2.  Вставьте следующий стандартный заголовок в начало файла:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3.  Определите владельца файла. Элемент `<assemblyIdentity>` элемента `<dependentAssembly>` в файле манифеста приложения должен соответствовать аналогичному элементу в манифесте компонента. В следующем примере владельцем файла манифеста является `myManagedComp` версии 1.2.3.4.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />  
    ```  
  
4.  Определите каждый класс в сборке. Используйте `<clrClass>` элемент для уникальной идентификации каждого класса в управляемой сборке. Атрибуты элемента, вложенного в `<assembly>`, определены в следующей таблице.  
  
    |Атрибут|Описание|Обязательно|  
    |---------------|-----------------|--------------|  
    |`clsid`|Идентификатор, который задает активируемый класс.|Да|  
    |`description`|Строка, которая сообщает пользователю о компоненте. По умолчанию используется пустая строка.|Нет|  
    |`name`|Строка, представляющая управляемый класс.|Да|  
    |`progid`|Идентификатор, который используется для отложенной активации.|Нет|  
    |`threadingModel`|Потоковая модель COM. По умолчанию используется значение "Both" (Оба).|Нет|  
    |`runtimeVersion`|Используемая версия среды CLR. Если этот атрибут не задан, а среда CLR еще не загружена, компонент загружает последнюю установленную версию среды CLR, предшествующую версии 4. Если указать v1.0.3705, v1.1.4322 или v2.0.50727, автоматически выполняется накат версии до последней установленной версии среды CLR, предшествующей версии 4 (как правило, v2.0.50727). Если уже загружена другая версия среды CLR и не удается загрузить указанную версию в рамках параллельного процесса, загружается указанная версия. В противном случае используется загруженная версия CLR. Это может привести к сбою загрузки.|Нет|  
    |`tlbid`|Идентификатор библиотеки типов, содержащей сведения о типе класса.|Нет|  
  
     Во всех тегах атрибутов учитывается регистр символов. Просматривая библиотеку типов, экспортированную для сборки с помощью средства ObjectViewer OLE/COM (Oleview.exe), можно получить идентификаторы классов (CLSID), программ (ProgID), потоковые модели и версию среды выполнения.  
  
     В следующем манифесте компонента определяются два класса: `testClass1` и `testClass2`.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"   
                        publicKeyToken="8275b28176rcbbef"  
           />  
           <clrClass  
                        clsid="{65722BE6-3449-4628-ABD3-74B6864F9739}"  
                        progid="myManagedComp.testClass1"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass1"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <clrClass  
                        clsid="{367221D6-3559-3328-ABD3-45B6825F9732}"  
                        progid="myManagedComp.testClass2"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass2"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <file name="MyManagedComp.dll">  
           </file>  
    </assembly>  
    ```  
  
5.  Сохраните файл манифеста под соответствующим именем. Имя манифеста компонента состоит из имени библиотеки сборки и расширения manifest. Например, манифест для myManagedComp.dll будет носить имя myManagedComp.manifest.  
  
 Манифест компонента необходимо внедрить в сборку в качестве ресурса.  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a>Внедрение манифеста компонента в управляемую сборку  
  
1.  Создайте скрипт ресурсов, содержащий следующую инструкцию:  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     В этой инструкции `myManagedComp.manifest` определяет имя внедряемого манифеста компонента. В этом примере файл скрипта будет носить имя `myresource.rc`.  
  
2.  Скомпилируйте скрипт с помощью средства компиляции ресурсов Microsoft Windows (Rc.exe). В командной строке введите следующую команду:  
  
     `rc myresource.rc`  
  
     Программа Rc.exe создает файл ресурсов `myresource.res`.  
  
3.  Снова скомпилируйте исходный файл сборки и укажите файл ресурсов с помощью параметра **/win32res**:  
  
    ```  
    /win32res:myresource.res  
    ```  
  
     Файл, содержащий внедренный ресурс, также будет носить имя `myresource.res`.  
  
## <a name="see-also"></a>См. также  
 [COM-взаимодействие без регистрации](registration-free-com-interop.md)  
 [Требования для регистрации COM-взаимодействия без](https://msdn.microsoft.com/library/0c43bc57-eecf-4e6c-8114-490141cce4da(v=vs.100)))  
 [Настройка COM-компонентов для активации без регистрации](https://msdn.microsoft.com/library/bfe9b02f-d964-4784-960e-a1f94692fbfe(v=vs.100)))  
 [Пошаговое руководство. Активация компонентов на основе платформы .NET без регистрации](https://msdn.microsoft.com/library/ms973915.aspx)
