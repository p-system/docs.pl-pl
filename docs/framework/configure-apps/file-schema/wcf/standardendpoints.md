---
title: '&lt;standardEndpoints&gt;'
ms.date: 03/30/2017
ms.assetid: d62153d7-a6e6-462a-a784-cca61e9c2ba1
ms.openlocfilehash: 689ed041304d5ae84218dde2575d7bbd0440490d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353185"
---
# <a name="ltstandardendpointsgt"></a>&lt;standardEndpoints&gt;
Ta sekcja konfiguracji umożliwia zdefiniowanie kolekcji standardowych punktów końcowych, które są do ponownego użycia wstępnie skonfigurowanymi punktami końcowymi. Standardowy punkt końcowy będzie mieć jeden lub więcej z address, binding i atrybuty kontraktu ustawioną wartością stałą. Na przykład w punkcie końcowym odnajdywania kontrakt jest stała. Umożliwia także standardowych punktów końcowych do rozszerzenia punktu końcowego usługi z nowymi właściwościami podobne do definiowania niestandardowego powiązania.  
  
 \<system.ServiceModel>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>  
    </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|Definiuje standardowy punkt końcowy ze stałym kontraktem zawiadomieniowym. Usługi można opcjonalnie ogłaszamy jego dostępność, wysyłając wiadomość online i offline powiadomienia, gdy jest otwarty lub zamknięty odpowiednio. Usługi Windows Communication Foundation (WCF) określa punktów końcowych powiadomienia w [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element i używa AnnouncementClient przeprowadzić anonsów. Klient chcą nasłuchiwania anonsu z innej usługi rzeczywiście działa jako usługa WCF; w związku z tym należy skonfigurować punktów końcowych powiadomienia dla tego klienta w [ \<usługi >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) sekcji.|  
|[\<obiektu discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|Definiuje standardowy punkt końcowy ze stałym kontraktem odkrywania. Po dodaniu do konfiguracji usługi, określa gdzie nasłuchiwać komunikatów odnajdywania. Po dodaniu do konfiguracji klienta Określa gdzie wysyłanie zapytań odnajdywania.|  
|[\<dynamicEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/dynamicendpoint.md)|Ten element konfiguracji definiuje standardowy punkt końcowy, który zawiera informacje, aby umożliwić aplikacji funkcjonowanie jako program kliencki, który można znaleźć adres punktu końcowego dynamicznie w czasie wykonywania.|  
|[\<mexEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/mexendpoint.md)|Definiuje standardowy punkt końcowy ze stałym kontraktem IMetadataExchange. Ponieważ wszystkie punkty końcowe wymiany metadanych określić IMetadataExchange jako umowy, może użyć tego standardowego punktu, zamiast definiować jeden dla siebie.|  
|[\<udpAnnoucementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpannoucementendpoint.md)|Definiuje standardowy punkt końcowy jest używany przez usługi do wysłania komunikatów Anons powiązania protokołu UDP. Ma stały kontraktu i obsługuje dwie wersje odnajdywania. Ponadto ma stałym powiązaniem UDP oraz domyślną wartość adresu zgodnie ze specyfikacją WS-Discovery (WS-Discovery kwietnia 2005 lub WS-Discovery w wersji 1.1). Można określić adres multiemisji do użycia na potrzeby wysyłania i odbierania wiadomości powiadomienia.|  
|[\<udpDiscoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)|Definiuje standardowy punkt końcowy, który jest wstępnie konfigurowany dla operacji odnajdowania za pośrednictwem protokołu UDP powiązanie multiemisji. Ten punkt końcowy ma stały kontraktu i obsługuje dwie wersje protokołu WS-Discovery. Ponadto ma stałym powiązaniem UDP i domyślny adres zgodnie ze specyfikacją WS-Discovery (WS-Discovery kwietnia 2005 lub WS-Discovery w wersji 1.1).|  
|[\<webHttpEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpendpoint.md)|Definiuje standardowy punkt końcowy ze stałym [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) powiązania, które automatycznie dodaje [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) zachowanie. Podczas zapisywania usługi REST, należy używać tego punktu końcowego.|  
|[\<webScriptEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/webscriptendpoint.md)|Definiuje standardowy punkt końcowy ze stałym [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) powiązania, które automatycznie dodaje [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) zachowanie. Podczas pisania to usługa, która jest wywoływana z aplikacji ASP.NET AJAX, należy używać tego punktu końcowego.|  
|[\<obiektu workflowControlEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowcontrolendpoint.md)|Definiuje standardowy punkt końcowy do kontroli wykonania wystąpień przepływu pracy (Tworzenie, uruchom, zawieszenie, przerwanie, itp).|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|\<system.ServiceModel>|Element główny wszystkich elementów konfiguracji usługi WCF.|  
  
## <a name="see-also"></a>Zobacz też  
 [Standardowe punkty końcowe](../../../../../docs/framework/wcf/feature-details/standard-endpoints.md)
