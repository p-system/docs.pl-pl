---
title: Atrybuty, które kontrolują serializacji XML
ms.date: 03/30/2017
helpviewer_keywords:
- classes, serializing
- XmlSerializer class, serializing
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
- XML Schema, serializing
ms.assetid: 414b820f-a696-4206-b576-2711d85490c7
ms.openlocfilehash: 3c6e46c97a943f1c77ffd12dd2b3bc85a64b3c11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585042"
---
# <a name="attributes-that-control-xml-serialization"></a>Atrybuty, które kontrolują serializacji XML
Możesz stosowanie atrybutów w poniższej tabeli do klas i klasy elementów członkowskich do kontrolowania sposobu, w jaki <xref:System.Xml.Serialization.XmlSerializer> serializuje i deserializuje wystąpienia klasy. Aby zrozumieć, jak te atrybuty sterowania serializacją XML, zobacz [kontrolowanie atrybutów za pomocą serializacji XML](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md).  
  
 Te atrybuty mogą również kontrolować wiadomości protokołu SOAP literału stylu generowanych przez usługi sieci Web XML. Aby uzyskać więcej informacji dotyczących stosowania tych atrybutów do metody usług XML sieci Web, zobacz [szeregowanie XML z usług XML sieci Web](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md).  
  
 Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybutów](../../../docs/standard/attributes/index.md).  
  
|Atrybut|Informacje zawarte w tym artykule dotyczą|Określa|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.XmlAnyAttributeAttribute>|Pole publiczne, właściwość, parametru lub zwracanej wartości, która zwraca tablicę <xref:System.Xml.XmlAttribute> obiektów.|Podczas deserializacji, tablica będzie wypełniona <xref:System.Xml.XmlAttribute> obiektów, które reprezentują wszystkie atrybuty XML nieznany schematu.|  
|<xref:System.Xml.Serialization.XmlAnyElementAttribute>|Pole publiczne, właściwość, parametru lub zwracanej wartości, która zwraca tablicę <xref:System.Xml.XmlElement> obiektów.|Podczas deserializacji, tablica jest wypełniany <xref:System.Xml.XmlElement> obiekty reprezentujące wszystkie elementy XML nieznany schematu.|  
|<xref:System.Xml.Serialization.XmlArrayAttribute>|Pole publiczne, właściwości, parametr lub wartości zwracanej, która zwraca tablicę obiektów złożonych.|Zostanie wygenerowany tablicy elementów członkowskich jako elementy członkowskie tablicy XML.|  
|<xref:System.Xml.Serialization.XmlArrayItemAttribute>|Pole publiczne, właściwości, parametr lub wartości zwracanej, która zwraca tablicę obiektów złożonych.|Typy pochodne, które mogą być wstawiane do tablicy. Zazwyczaj stosowane w połączeniu z <xref:System.Xml.Serialization.XmlArrayAttribute>.|  
|<xref:System.Xml.Serialization.XmlAttributeAttribute>|Pole publiczne, właściwość, parametru lub wartości zwracanej.|Element członkowski będzie serializowana jako atrybut XML.|  
|<xref:System.Xml.Serialization.XmlChoiceIdentifierAttribute>|Pole publiczne, właściwość, parametru lub wartości zwracanej.|Element członkowski może dodatkowo rozróżniane przy użyciu wyliczenia.|  
|<xref:System.Xml.Serialization.XmlElementAttribute>|Pole publiczne, właściwość, parametru lub wartości zwracanej.|Pole lub właściwość będzie serializowana jako XML element.|  
|<xref:System.Xml.Serialization.XmlEnumAttribute>|Pole publicznej jest identyfikatorem wyliczenia.|Nazwa elementu element członkowski wyliczenia.|  
|<xref:System.Xml.Serialization.XmlIgnoreAttribute>|Właściwości publiczne i pola.|Właściwości lub pól mają być ignorowane, gdy klasa zawierająca jest serializowana.|  
|<xref:System.Xml.Serialization.XmlIncludeAttribute>|Publiczna uzyskiwany deklaracje klas i zwracanymi wartościami metod publicznych w dokumentach sieci Web Services Description Language (WSDL).|Klasa mają zostać uwzględnione podczas generowania schematów (do rozpoznany po serializacji).|  
|<xref:System.Xml.Serialization.XmlRootAttribute>|Klasa publiczna deklaracji.|Formanty XML serializacji w celu atrybutu jako element główny XML. Użyj atrybutu do dalszego określenia nazwy obszaru nazw i elementu.|  
|<xref:System.Xml.Serialization.XmlTextAttribute>|Właściwości publiczne i pola.|Właściwości lub pól powinien zostać Zserializowany jako tekst XML.|  
|<xref:System.Xml.Serialization.XmlTypeAttribute>|Klasa publiczna deklaracji.|Nazwa i nazw typu XML.|  
  
 Oprócz tych atrybutów, które są wszystkie znalezione w <xref:System.Xml.Serialization> przestrzeni nazw, można także zastosować <xref:System.ComponentModel.DefaultValueAttribute> atrybutu do pola. **DefaultValueAttribute** ustawia wartość, która zostanie automatycznie przypisany do elementu członkowskiego, jeśli nie określono wartości.  
  
 Aby kontrolować zakodowanego serializacji XML protokołu SOAP, zobacz [atrybuty że formant zakodowane SOAP serializacji](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja XML i SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Kontrolowanie serializacji XML przy użyciu atrybutów](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 [Instrukcje: Określanie alternatywnej nazwy elementu dla strumienia XML](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 [Instrukcje: Serializacja obiektu](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Instrukcje: Deserializacja obiektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
