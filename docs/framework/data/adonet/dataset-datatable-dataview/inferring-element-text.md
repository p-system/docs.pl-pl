---
title: Wnioskowanie tekstu elementu
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: b32d8f3f89a16166ffc0e903ef1f63c3b97a249c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762718"
---
# <a name="inferring-element-text"></a>Wnioskowanie tekstu elementu
Jeśli element zawiera tekst i nie ma żadnych elementów podrzędnych, można go wywnioskować, ponieważ tabele takie jak (elementy z atrybutami) lub powtarzane elementy nową kolumnę o nazwie **TableName_Text** zostaną dodane do tabeli, która jest wywnioskowany dla elementu. Tekst zawarte w elemencie zostanie dodany do wiersza w tabeli i przechowywane w nowej kolumnie. **ColumnMapping** właściwości nowej kolumny, która zostanie ustawiona do **MappingType.SimpleContent**.  
  
 Rozważmy na przykład następujący kod XML.  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 Proces wnioskowania spowoduje utworzenie tabeli o nazwie **Element1** z dwiema kolumnami: **attr1** i **Element1_Text**. **ColumnMapping** właściwość **attr1** kolumny zostanie ustawiona do **MappingType.Attribute**. **ColumnMapping** właściwość **Element1_Text** kolumny zostanie ustawiona do **MappingType.SimpleContent**.  
  
 **Zestaw danych:** DocumentElement  
  
 **Tabela:** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|Wartość1|Tekst1|  
  
 Jeśli element zawiera tekst, ale ma także elementy podrzędne, które zawierają tekst, nie można dodać kolumny do tabeli do przechowywania tekstu zawarte w elemencie. Tekst zawarte w elemencie zostanie zignorowany, gdy tekst w elementach podrzędnych jest uwzględniany w wiersza w tabeli. Rozważmy na przykład następujący kod XML.  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 Proces wnioskowania spowoduje utworzenie tabeli o nazwie **Element1** z jedną kolumną o nazwie **ChildElement1**. Tekst dla **ChildElement1** element mają być uwzględnieni w wiersza w tabeli. Inny tekst zostanie zignorowany. **ColumnMapping** właściwość **ChildElement1** kolumny zostanie ustawiona do **MappingType.Element**.  
  
 **Zestaw danych:** DocumentElement  
  
 **Tabela:** Element1  
  
|ChildElement1|  
|-------------------|  
|Tekst2|  
  
## <a name="see-also"></a>Zobacz też  
 [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Ładowanie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Ładowanie informacji o schemacie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
