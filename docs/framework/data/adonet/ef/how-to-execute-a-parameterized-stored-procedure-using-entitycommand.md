---
title: Практическое руководство. Выполнение параметризованной хранимой процедуры с использованием EntityCommand
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: 68589cf8906e35313e261e373cf87017ffe6f8f9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a>Практическое руководство. Выполнение параметризованной хранимой процедуры с использованием EntityCommand
В данном разделе приведен пример выполнения параметризированной хранимой процедуры при помощи команды <xref:System.Data.EntityClient.EntityCommand>.  
  
### <a name="to-run-the-code-in-this-example"></a>Выполнение кода в этом примере  
  
1.  Добавить [модели School](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) в проект и настроить проект для использования [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Дополнительные сведения см. в разделе [как: использовать мастер моделей EDM](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  На странице кода приложения добавьте следующие инструкции `using` (`Imports` в Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  Импортируйте хранимую процедуру `GetStudentGrades` и укажите сущности `CourseGrade` в качестве возвращаемого типа. Сведения о том, как импортировать хранимую процедуру в разделе [как: Импорт хранимой процедуры](http://msdn.microsoft.com/library/24e68bf4-bd6d-428d-bc35-92d7b8e3736d).  
  
## <a name="example"></a>Пример  
 Следующий код выполняет хранимую процедуру `GetStudentGrades`, где параметр `StudentId` является обязательным. Затем результаты считываются объектом <xref:System.Data.EntityClient.EntityDataReader>.  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a>См. также  
 [Поставщик EntityClient для Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
