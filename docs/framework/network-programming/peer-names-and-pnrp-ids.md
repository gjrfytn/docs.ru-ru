---
title: Одноранговые имена и идентификаторы PNRP
ms.date: 03/30/2017
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 02e6d65baac0a0eab9bfde545a117d3636239c17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="peer-names-and-pnrp-ids"></a>Одноранговые имена и идентификаторы PNRP
Имя однорангового узла представляет конечную точку для взаимодействия, в качестве которой может выступать компьютер, пользователь, группа, служба или любой другой объект, связанный с одноранговым узлом, которую можно разрешить в IPv6-адрес. Протокол PNRP принимает статистически уникальное имя однорангового узла для создания идентификатора PNRP, который используется для идентификации членов облака.  
  
## <a name="peer-names"></a>Имена одноранговых узлов  
 Имена одноранговых узлов можно зарегистрировать как незащищенные или защищенные. Незащищенные имена представляют собой обычные текстовые строки, которые подвержены спуфингу, так как зарегистрировать повторяющееся имя может любой пользователь. Такие имена лучше всего использовать в частных или защищенных иным образом сетях. Безопасность защищенных имен обеспечивается благодаря применению сертификата и цифровой подписи. Подтвердить право владения защищенным именем может только его первоначальный издатель.  
  
 Достаточный уровень безопасности среды для одноранговых узлов, взаимодействующих по протоколу PNRP, обеспечивается за счет сочетания облака и области действия. Тем не менее применение защищенного имени однорангового узла не гарантирует общую безопасность сетевого приложения. Безопасность приложения зависит от его реализации.  
  
 Защищенные имена одноранговых узлов регистрируются только их владельцем и защищаются посредством шифрования с открытым ключом. Защищенное имя однорангового узла считается принадлежащим сущности однорангового узла, которой принадлежит соответствующий закрытый ключ. Право владения может быть подтверждено сертифицированным адресом однорангового узла (CPA), который подписывается закрытым ключом. Не имея соответствующего закрытого ключа, злоумышленники не могут подделать право владения именем однорангового узла.  
  
## <a name="pnrp-ids"></a>Идентификаторы PNRP  
 ![Идентификатор PNRP](../../../docs/framework/network-programming/media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")  
  
 Идентификаторы PNRP состоят из следующих компонентов:  
  
-   Старшие 128 бит (идентификатор одноранговой сети) содержат хэш имени однорангового узла, назначенного конечной точке. Имя однорангового узла имеет следующий формат: *Authority.Classifier*. Для защищенных имен в качестве атрибута *Authority* используется хэш алгоритма SHA1 для открытого ключа имени однорангового узла в шестнадцатеричном формате. Для незащищенных имен атрибут *Authority* содержит единственный символ: "0". Атрибут *Classifier* содержит строку, которая определяет приложение. Длина классификатора имени однорангового узла не может превышать 149 символов, включая конечный символ `null`.  
  
-   Младшие 128 бит используются для расположения службы и содержат число, которое идентифицирует другие экземпляры этого идентификатора одноранговой сети в том же облаке.  
  
 Такое сочетание идентификатора одноранговой сети и расположения службы позволяет регистрировать несколько идентификаторов PNRP с одного компьютера.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Net.PeerToPeer.PeerName>  
 <xref:System.Net.PeerToPeer>
