---
title: Сопоставления типов данных OLE DB
ms.date: 03/30/2017
ms.assetid: 04bcb259-59d3-4fd7-894d-4f0dd0c68069
ms.openlocfilehash: 4287b125b26bc0c7233f59322c84e2ac27c0c594
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="ole-db-data-type-mappings"></a>Сопоставления типов данных OLE DB
В приведенной ниже таблице показаны выводимые типы [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] для типов данных поставщика данных .NET Framework для ADO и OLE DB (<xref:System.Data.OleDb>). Приведены также типизированные методы доступа для <xref:System.Data.OleDb.OleDbDataReader>.  
  
|Тип ADO|Тип OLE DB|Тип [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]|Типизированный метод доступа [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]|  
|--------------|-----------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|adBigInt|DBTYPE_I8|Int64|GetInt64()|  
|adBinary|DBTYPE_BYTES|Byte[]|GetBytes()|  
|adBoolean|DBTYPE_BOOL|Boolean|GetBoolean()|  
|adBSTR|DBTYPE_BSTR|Строковое|GetString()|  
|adChapter|DBTYPE_HCHAPTER|Поддерживается с помощью `DataReader`. В разделе [получение данных с помощью объекта DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).|GetValue()|  
|adChar|DBTYPE_STR|Строковое|GetString()|  
|adCurrency|DBTYPE_CY|Десятичное число|GetDecimal()|  
|adDate|DBTYPE_DATE|DateTime|GetDateTime()|  
|adDBDate|DBTYPE_DBDATE|DateTime|GetDateTime()|  
|adDBTime|DBTYPE_DBTIME|DateTime|GetDateTime()|  
|adDBTimeStamp|DBTYPE_DBTIMESTAMP|DateTime|GetDateTime()|  
|adDecimal|DBTYPE_DECIMAL|Десятичное число|GetDecimal()|  
|adDouble|DBTYPE_R8|Double|GetDouble()|  
|adError|DBTYPE_ERROR|ExternalException|GetValue()|  
|adFileTime|DBTYPE_FILETIME|DateTime|GetDateTime()|  
|adGUID|DBTYPE_GUID|Guid|GetGuid()|  
|adIDispatch|DBTYPE_IDISPATCH *|Объект|GetValue()|  
|adInteger|DBTYPE_I4|Int32|GetInt32()|  
|adIUnknown|DBTYPE_IUNKNOWN *|Объект|GetValue()|  
|adNumeric|DBTYPE_NUMERIC|Десятичное число|GetDecimal()|  
|adPropVariant|DBTYPE_PROPVARIANT|Объект|GetValue()|  
|adSingle|DBTYPE_R4|Single|GetFloat()|  
|adSmallInt|DBTYPE_I2|Int16|GetInt16()|  
|adTinyInt|DBTYPE_I1|Byte|GetByte()|  
|adUnsignedBigInt|DBTYPE_UI8|UInt64|GetValue()|  
|adUnsignedInt|DBTYPE_UI4|UInt32|GetValue()|  
|adUnsignedSmallInt|DBTYPE_UI2|UInt16|GetValue()|  
|adUnsignedTinyInt|DBTYPE_UI1|Byte|GetByte()|  
|adVariant|DBTYPE_VARIANT|Объект|GetValue()|  
|adWChar|DBTYPE_WSTR|Строковое|GetString()|  
|adUserDefined|DBTYPE_UDT|не поддерживается||  
|adVarNumeric|DBTYPE_VARNUMERIC|не поддерживается||  
  
 \* Для таких типов OLE DB `DBTYPE_IUNKNOWN` и `DBTYPE_IDISPATCH`, ссылка на объект служит представлением указателя в упакованном виде.  
  
## <a name="see-also"></a>См. также  
 [Извлечение и изменение данных в ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Центр разработчиков наборов данных и управляемых поставщиков ADO.NET](http://go.microsoft.com/fwlink/?LinkId=217917)
