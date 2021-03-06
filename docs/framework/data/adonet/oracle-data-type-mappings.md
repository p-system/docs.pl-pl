---
title: Mappings1 typ danych Oracle
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: 2b5a3a90c704dd6edf32e6fb77b551e6fc0f78ec
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759624"
---
# <a name="oracle-data-type-mappings"></a>Mapowanie typu danych Oracle
W poniższej tabeli przedstawiono typy danych Oracle i ich mapowania <xref:System.Data.OracleClient.OracleDataReader>.  
  
|Typ danych Oracle|Typ danych .NET framework zwracanych przez OracleDataReader.GetValue|OracleClient typ danych zwracanych przez OracleDataReader.GetOracleValue|Uwagi|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BPLIK**|**Byte[]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte[]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**Ciąg**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**Ciąg**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATA**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**FLOAT**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Ten typ danych jest aliasem **numer** typu danych i został zaprojektowany, aby <xref:System.Data.OracleClient.OracleDataReader> zwraca **System.Decimal** lub <xref:System.Data.OracleClient.OracleNumber> zamiast wartości zmiennoprzecinkowych. Przy użyciu typu danych .NET Framework może spowodować przepełnienie.|  
|**LICZBA CAŁKOWITA**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Ten typ danych jest aliasem **NUMBER(38)** typu danych i został zaprojektowany, aby <xref:System.Data.OracleClient.OracleDataReader> zwraca **System.Decimal** lub <xref:System.Data.OracleClient.OracleNumber> zamiast wartość całkowitą. Przy użyciu typu danych .NET Framework może spowodować przepełnienie.|  
|**INTERWAŁ ROK, MIESIĄC**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**INTERWAŁ DZIEŃ NA SEKUNDĘ**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**DŁUGA**|**Ciąg**|<xref:System.Data.OracleClient.OracleString>||  
|**LONG RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**Ciąg**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**Ciąg**|<xref:System.Data.OracleClient.OracleLob>||  
|**NUMER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Przy użyciu typu danych .NET Framework może spowodować przepełnienie.|  
|**NVARCHAR2**|**Ciąg**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||Oracle **REF CURSOR** typ danych nie jest obsługiwany przez <xref:System.Data.OracleClient.OracleDataReader> obiektu.|  
|**ROWID**|**Ciąg**|<xref:System.Data.OracleClient.OracleString>||  
|**ZNACZNIK CZASU**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**SYGNATURA CZASOWA Z LOKALNEJ STREFIE CZASOWEJ**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**SYGNATURA CZASOWA ZE STREFĄ CZASOWĄ**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**LICZBA CAŁKOWITA BEZ ZNAKU**|**Numer**|<xref:System.Data.OracleClient.OracleNumber>|Ten typ danych jest aliasem **NUMBER(38)** typu danych i został zaprojektowany, aby <xref:System.Data.OracleClient.OracleDataReader> zwraca **System.Decimal** lub <xref:System.Data.OracleClient.OracleNumber> zamiast całkowitą bez znaku. Przy użyciu typu danych .NET Framework może spowodować przepełnienie.|  
|**VARCHAR2**|**Ciąg**|<xref:System.Data.OracleClient.OracleString>||  
  
 W poniższej tabeli przedstawiono typy danych Oracle i typy danych .NET Framework (**System.Data.DbType** i <xref:System.Data.OracleClient.OracleType>) do użycia podczas wiązania je jako parametry.  
  
|Typ danych Oracle|Wyliczenie DbType powiązać jako parametr|Wyliczenie typu OracleType powiązać jako parametr|Uwagi|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BPLIK**||**BFile**|Oracle tylko umożliwia powiązanie **BPLIK** jako **BPLIK** parametru. Dostawcy danych programu .NET dla Oracle nie automatycznie utworzyć ją, jeśli próba powiązania niż**BPLIK** wartości, takich jak **byte []** lub <xref:System.Data.OracleClient.OracleBinary>.|  
|**BLOB**||**Blob**|Oracle tylko umożliwia powiązanie **obiektu BLOB** jako **obiektu BLOB** parametru. Dostawcy danych programu .NET dla Oracle nie automatycznie utworzyć ją, jeśli próba powiązania niż**obiektu BLOB** wartości, takich jak **byte []** lub <xref:System.Data.OracleClient.OracleBinary>.|  
|**CHAR**|**AnsiStringFixedLength**|**char**||  
|**CLOB**||**Clob**|Oracle tylko umożliwia powiązanie **CLOB** jako **CLOB** parametru. Dostawcy danych programu .NET dla Oracle nie automatycznie utworzyć ją, jeśli próba powiązania niż**CLOB** wartości, takich jak **System.String** lub <xref:System.Data.OracleClient.OracleString>.|  
|**DATA**|**DateTime**|**DateTime**||  
|**FLOAT**|**Single, Double, Decimal**|**Float, kliknij dwukrotnie, liczba**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Określa **System.Data.DBType** i <xref:System.Data.OracleClient.OracleType>.|  
|**LICZBA CAŁKOWITA**|**SByte, Int16, Int32, Int64, Decimal**|**SByte, Int16, Int32, liczba**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Określa **System.Data.DBType** i <xref:System.Data.OracleClient.OracleType>.|  
|**INTERWAŁ ROK, MIESIĄC**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> jest dostępna tylko wtedy, gdy oprogramowanie zarówno Oracle 9i klienta i serwera.|  
|**INTERWAŁ DZIEŃ NA SEKUNDĘ**|**Obiekt**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> jest dostępna tylko wtedy, gdy oprogramowanie zarówno Oracle 9i klienta i serwera.|  
|**DŁUGA**|**AnsiString**|**LongVarChar**||  
|**LONG RAW**|**Binary**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle tylko umożliwia powiązanie **NCLOB** jako **NCLOB** parametru. Dostawcy danych programu .NET dla Oracle nie automatycznie utworzyć ją, jeśli próba powiązania niż**NCLOB** wartości, takich jak **System.String** lub <xref:System.Data.OracleClient.OracleString>.|  
|**NUMER**|**VarNumeric**|**Numer**||  
|**NVARCHAR2**|**Ciąg**|**NVarChar**||  
|**RAW**|**Binary**|**nieprzetworzone**||  
|**REF CURSOR**||**Kursor**|Aby uzyskać więcej informacji, zobacz [kursory REF Oracle](../../../../docs/framework/data/adonet/oracle-ref-cursors.md).|  
|**ROWID**|**AnsiString**|**RowId**||  
|**ZNACZNIK CZASU**|**DateTime**|**Znacznik czasu**|<xref:System.Data.OracleClient.OracleType> jest dostępna tylko wtedy, gdy oprogramowanie zarówno Oracle 9i klienta i serwera.|  
|**SYGNATURA CZASOWA Z LOKALNEJ STREFIE CZASOWEJ**|**DateTime**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> jest dostępna tylko wtedy, gdy oprogramowanie zarówno Oracle 9i klienta i serwera.|  
|**SYGNATURA CZASOWA ZE STREFĄ CZASOWĄ**|**DateTime**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> jest dostępna tylko wtedy, gdy oprogramowanie zarówno Oracle 9i klienta i serwera.|  
|**LICZBA CAŁKOWITA BEZ ZNAKU**|**Byte, UInt16, UInt32, UInt64, Decimal**|**Byte, UInt16, Uint32, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Określa **System.Data.DBType** i <xref:System.Data.OracleClient.OracleType>.|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 **Wejścia/wyjścia**, **dane wyjściowe**, i **ReturnValue** **właściwość ParameterDirection** wartości używane przez <xref:System.Data.OracleClient.OracleParameter.Value%2A> właściwości <xref:System.Data.OracleClient.OracleParameter> obiektu są typy danych .NET Framework, chyba że wartość wejściowa jest typ danych Oracle (na przykład <xref:System.Data.OracleClient.OracleNumber> lub <xref:System.Data.OracleClient.OracleString>). To nie ma zastosowania do **REF CURSOR**, **BPLIK**, lub **LOB** typów danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Oracle i ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
