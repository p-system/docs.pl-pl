---
title: Kolekcje schematów ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: 36d0859b897bfcea33803c219ade14722ed90421
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766650"
---
# <a name="odbc-schema-collections"></a>Kolekcje schematów ODBC
W tej sekcji omówiono obsługi kolekcji schematu dla sterowników ODBC dla programu Microsoft SQL Server, Oracle i Microsoft Jet.  
  
## <a name="microsoft-sql-server-odbc-driver"></a>Sterownik ODBC programu Microsoft SQL Server  
 Sterownik ODBC programu Microsoft SQL Server obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:  
  
-   Tabele  
  
-   Indeksy  
  
-   Kolumny  
  
-   Procedury  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Widoki  
  
### <a name="tables-and-views"></a>Tabele i widoki  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|TABLE_CAT|String|  
|TABLE_SCHEM|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|REMARKS|String|  
  
### <a name="indexes"></a>Indeksy  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|TABLE_CAT|String|  
|TABLE_SCHEM|String|  
|TABLE_NAME|String|  
|NON_UNIQUE|Int16|  
|INDEX_QUALIFIER|String|  
|INDEX_NAME|String|  
|TYP|Int16|  
|ORDINAL_POSITION|Int16|  
|COLUMN_NAME|String|  
|ASC_OR_DESC|String|  
|CARDINATLITY|Int32|  
|STRONY|Int32|  
|FILTER_CONDITION|String|  
|SS_TYPE_SCHEMA|String|  
|SS_DATA_TYPE|Byte|  
  
### <a name="columns"></a>Kolumny  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|TABLE_CAT|String|  
|TABLE_SCHEM|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|DOPUSZCZAJĄCE WARTOŚCI ZEROWE|Int16|  
|REMARKS|String|  
|COLUMN_DEF|String|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|String|  
|SS_TYPE_CATALOG|String|  
|SS_TYPE_SCHEMA|String|  
|SS_DATA_TYPE|Byte|  
  
### <a name="procedures"></a>Procedury  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|PROCEDURE_CAT|String|  
|PROCEDURE_SCHEM|String|  
|PROCEDURE_NAME|String|  
|NUM_INPUT_PARAMS|Int32|  
|NUM_OUTPUT_PARAMS|Int32|  
|NUM_RESULT_SETS|Int32|  
|REMARKS|String|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|PROCEDURE_CAT|String|  
|PROCEDURE_SCHEM|String|  
|PROCEDURE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|DOPUSZCZAJĄCE WARTOŚCI ZEROWE|Int16|  
|REMARKS|String|  
|COLUMN_DEF|String|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|String|  
|SS_TYPE_CATALOG|String|  
|SS_TYPE_SCHEMA|String|  
|SS_DATA_TYPE|Byte|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|PROCEDURE_CAT|String|  
|PROCEDURE_SCHEM|String|  
|PROCEDURE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|DOPUSZCZAJĄCE WARTOŚCI ZEROWE|Int16|  
|REMARKS|String|  
|COLUMN_DEF|String|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|String|  
|SS_TYPE_CATALOG|String|  
|SS_TYPE_SCHEMA|String|  
|SS_DATA_TYPE|Byte|  
  
## <a name="microsoft-oracle-odbc-driver"></a>Sterownik ODBC rozwiązań Microsoft Oracle  
 Sterownik ODBC programu Oracle do programu Microsoft SQL Server obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:  
  
-   Tabele  
  
-   Kolumny  
  
-   Procedury  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Widoki  
  
-   Indeksy  
  
### <a name="tables-and-views"></a>Tabele i widoki  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|TABLE_QUALIFIER|String|  
|TABLE_OWNER|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|REMARKS|String|  
  
### <a name="columns"></a>Kolumny  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|TABLE_QUALIFIER|String|  
|TABLE_OWNER|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|DOKŁADNOŚĆ|Int32|  
|DŁUGOŚĆ|Int32|  
|SKALI|Int16|  
|PODSTAWA|Int16|  
|DOPUSZCZAJĄCE WARTOŚCI ZEROWE|Int16|  
|REMARKS|String|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedures"></a>Procedury  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|String|  
|PROCEDURE_OWNER|String|  
|PROCEDURE_NAME|String|  
|NUM_INPUT_PARAMS|Int16|  
|NUM_OUTPUT_PARAMS|Int16|  
|NUM_RESULT_SETS|Int16|  
|REMARKS|String|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|String|  
|PROCEDURE_OWNER|String|  
|PROCEDURE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|DOKŁADNOŚĆ|Int32|  
|DŁUGOŚĆ|Int32|  
|SKALI|Int16|  
|PODSTAWA|Int16|  
|DOPUSZCZAJĄCE WARTOŚCI ZEROWE|Int16|  
|REMARKS|String|  
|PRZECIĄŻENIA|Int32|  
|ORDINAL_POSITION|Int32|  
  
## <a name="microsoft-jet-odbc-driver"></a>Sterownik ODBC dla programu Microsoft Jet  
 Sterownik ODBC firmy Microsoft Jet obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:  
  
-   Tabele  
  
-   Indeksy  
  
-   Kolumny  
  
-   Procedury  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Widoki  
  
### <a name="tables-and-views"></a>Tabele i widoki  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|TABLE_QUALIFIER|String|  
|TABLE_OWNER|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|REMARKS|String|  
  
### <a name="columns"></a>Kolumny  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|TABLE_QUALIFIER|String|  
|TABLE_OWNER|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|DOKŁADNOŚĆ|Int32|  
|DŁUGOŚĆ|Int32|  
|SKALI|Int16|  
|PODSTAWA|Int16|  
|DOPUSZCZAJĄCE WARTOŚCI ZEROWE|Int16|  
|REMARKS|String|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedures"></a>Procedury  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|String|  
|PROCEDURE_OWNER|String|  
|PROCEDURE_NAME|String|  
|NUM_INPUT_PARAMS|Int16|  
|NUM_OUTPUT_PARAMS|Int16|  
|NUM_RESULT_SETS|Int16|  
|REMARKS|String|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|String|  
|PROCEDURE_OWNER|String|  
|PROCEDURE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|DOKŁADNOŚĆ|Int32|  
|DŁUGOŚĆ|Int32|  
|SKALI|Int16|  
|PODSTAWA|Int16|  
|DOPUSZCZAJĄCE WARTOŚCI ZEROWE|Int16|  
|REMARKS|String|  
|PRZECIĄŻENIA|Int32|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|PROCEDURE_CAT|String|  
|PROCEDURE_SCHEM|String|  
|PROCEDURE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|DOPUSZCZAJĄCE WARTOŚCI ZEROWE|Int16|  
|REMARKS|String|  
|COLUMN_DEF|String|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|String|  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
