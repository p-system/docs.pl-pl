---
title: Mapowanie typu danych ODBC
ms.date: 03/30/2017
ms.assetid: 43c35d32-831d-480f-a150-78f7e869d17f
ms.openlocfilehash: bfabdb73b9435a98b4d0d625a8392723bdcdbc37
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765428"
---
# <a name="odbc-data-type-mappings"></a>Mapowanie typu danych ODBC
W poniższej tabeli przedstawiono wnioskowany [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu dla typów danych z dostawcy danych programu .NET Framework dla ODBC (<xref:System.Data.Odbc>). Metody dostępu typu dla <xref:System.Data.Odbc.OdbcDataReader> są także wyświetlone.  
  
|Typ ODBC|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Typ|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typizowane metody dostępu|  
|---------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|SQL_BIGINT|Int64|GetInt64()|  
|SQL_BINARY|Byte[]|GetBytes()|  
|SQL_BIT|Boolean|GetBoolean()|  
|SQL_CHAR|String<br /><br /> CHAR]|GetString()<br /><br /> GetChars()|  
|SQL_DECIMAL|Wartość dziesiętna|GetDecimal()|  
|SQL_DOUBLE|Double|GetDouble()|  
|SQL_GUID|Identyfikator GUID|GetGuid()|  
|SQL_INTEGER|Int32|GetInt32()|  
|SQL_LONG_VARCHAR|String<br /><br /> CHAR]|GetString()<br /><br /> GetChars()|  
|SQL_LONGVARBINARY|Byte[]|GetBytes()|  
|SQL_NUMERIC|Wartość dziesiętna|GetDecimal()|  
|SQL_REAL|Single|GetFloat()|  
|SQL_SMALLINT|Int16|GetInt16()|  
|SQL_TINYINT|Byte|GetByte()|  
|SQL_TYPE_TIMES|DataGodzina|GetDateTime()|  
|SQL_TYPE_TIMESTAMP|DataGodzina|GetDateTime()|  
|SQL_VARBINARY|Byte[]|GetBytes()|  
|SQL_WCHAR|String<br /><br /> CHAR]|GetString()<br /><br /> GetChars()|  
|SQL_WLONGVARCHAR|String<br /><br /> CHAR]|GetString()<br /><br /> GetChars()|  
|SQL_WVARCHAR|String<br /><br /> CHAR]|GetString()<br /><br /> GetChars()|  
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
