---
title: "&lt;secureConversationBootstrap&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 66b46f95-fa2d-4b5b-b6ce-0572ab0cdd50
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 13
---
# &lt;secureConversationBootstrap&gt;
Задает значения по умолчанию, используемые для инициализации службы безопасного обмена данными.  
  
## Синтаксис  
  
```  
  
<secureConversationBootstrap  
   allowSerializedSigningTokenOnReply="Boolean"  
   authenticationMode="AuthenticationMode"  
   defaultAlgorithmSuite="SecurityAlgorithmSuite"  
   includeTimestamp="Boolean"  
   requireDerivedKeys="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"  
   messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"  
   requireDerivedKeys="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   requireSignatureConfirmation="Boolean" >  
   securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"  
   includeTimestamp="Boolean" />  
```  
  
## Тип  
 `Type`  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`allowSerializedSigningTokenOnReply`|Необязательно.  Логическое значение, определяющее, может ли в ответе использоваться сериализованный маркер.  Значение по умолчанию — `false`.  При использовании двойной привязки для всех параметров, имеющих значение по умолчанию `true`, пропускаются любые установки.|  
|`authenticationMode`|Указывает режим проверки подлинности протокола SOAP, используемый между инициатором и респондентом.<br /><br /> Значение по умолчанию \- sspiNegotiated.<br /><br /> Это атрибут типа <xref:System.ServiceModel.Configuration.AuthenticationMode>.|  
|`defaultAlgorithmSuite`|Набор алгоритмов безопасности содержит различные алгоритмы, такие как Canonicalization, Digest, KeyWrap, Signature, Encryption и KeyDerivation.  Каждый из наборов алгоритмов безопасности определяет значения для этих различных параметров.  Данные алгоритмы обеспечивают безопасность на уровне сообщений.<br /><br /> Этот атрибут используется при работе с другой платформой, которая использует набор алгоритмов, отличный от набора по умолчанию.  При внесении изменений в параметры настройки необходимо знать о сильных и слабых сторонах соответствующих алгоритмов.  Это атрибут типа <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.  Значение по умолчанию — `Basic256`.|  
|`includeTimestamp`|Логическое значение, определяющее, включается ли в каждое сообщение отметка времени.  Значение по умолчанию — `true`.|  
|`keyEntropyMode`|Указывает способ вычисления ключей для защиты сообщений.  Ключи могут быть основаны только на данных ключа клиента, только на данных ключа службы или на сочетании обоих типов данных.  Допустимые значения:<br /><br /> -   ClientEntropy: сеансовый ключ основывается на данных ключа, которые предоставляются клиентом.<br />-   ServerEntropy: сеансовый ключ основывается на данных ключа, которые предоставляются службой.<br />-   CombinedEntropy: сеансовый ключ основывается на данных ключа, которые предоставляются клиентом и службой.<br /><br /> Значение по умолчанию \- CombinedEntropy.<br /><br /> Это атрибут типа <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`messageProtectionOrder`|Определяет порядок, в котором к сообщению применяются алгоритмы безопасности уровня сообщения.  Допустимы следующие значения:<br /><br /> -   SignBeforeEncrypt: сначала подпись, затем шифрование.<br />-   SignBeforeEncryptAndEncryptSignature: подпись, шифрование и затем шифрование сигнатуры.<br />-   EncryptBeforeSign: сначала шифрование, затем подпись.<br /><br /> SignBeforeEncryptAndEncryptSignature \- значение по умолчанию, если используются взаимные сертификаты и WS\-Security 1.1.  SignBeforeEncrypt \- значение по умолчанию, если используется WS\-Security 1.0.<br /><br /> Это атрибут типа <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|`messageSecurityVersion`|Задает используемую версию WS\-Security.  Допустимы следующие значения:<br /><br /> -   WSSecurityJan2004<br />-   WSSecurityXXX2005<br /><br /> Значение по умолчанию \- WSSecurityXXX2005.  Это атрибут типа <xref:System.ServiceModel.MessageSecurityVersion>.|  
|`requireDerivedKeys`|Логическое значение, которое указывает, могут ли ключи быть производными от исходных ключей проверки.  Значение по умолчанию — `true`.|  
|`requireSecurityContextCancellation`|Логическое значение, определяющее, следует ли закрывать и завершать контекст безопасности, когда он больше не нужен.  Значение по умолчанию — `true`.|  
|`requireSignatureConfirmation`|Логическое значение, определяющее, включено ли подтверждение сигнатуры WS\-Security.  Если установлено значение `true`, то сигнатуры сообщений подтверждаются респондентом.  Значение по умолчанию — `false`.<br /><br /> Подтверждение сигнатуры используется для подтверждения того, что служба отвечает, получив запрос полностью.|  
|`securityHeaderLayout`|Определяет порядок расположения элементов в заголовке безопасности.  Допустимые значения:<br /><br /> -   Strict.  Элементы добавляются в заголовок безопасности в соответствии с общим принципом «объявление перед использованием».<br />-   Lax.  Элементы добавляются в заголовок безопасности в любом порядке, отвечающем требованиям безопасности сообщений WSS: SOAP.<br />-   LaxWithTimestampFirst.  Элементы добавляются в заголовок безопасности в любом порядке, который соответствует требованиям безопасности сообщений WSS: SOAP, за исключением того, что первым элементом в заголовке безопасности должен быть wsse:Timestamp.<br />-   LaxWithTimestampLast.  Элементы добавляются в заголовок безопасности в любом порядке, который соответствует требованиям безопасности сообщений WSS: SOAP, за исключением того, что последним элементом в заголовке безопасности должен быть wsse:Timestamp.<br /><br /> Значение по умолчанию \- Strict.<br /><br /> Это элемент типа <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[\<issuedTokenParameters\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Определяет текущий выданный маркер.  Это элемент типа <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings\>](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|Задает параметры безопасности локального клиента для этой привязки.  Это элемент типа <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings\>](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|Задает параметры безопасности локальной службы для этой привязки.  Это элемент типа <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[\<безопасность\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Задает параметры безопасности для пользовательской привязки.|  
  
## См. также  
 <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>   
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>   
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [Привязки](../../../../../docs/framework/wcf/bindings.md)   
 [Расширение привязок](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [Пользовательские привязки](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)   
 [Как создавать пользовательскую привязку с использованием элемента SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)   
 [Безопасность пользовательской привязки](../../../../../docs/framework/wcf/samples/custom-binding-security.md)