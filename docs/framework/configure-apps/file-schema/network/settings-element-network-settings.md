---
title: '&lt;ustawienia&gt; elementu (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3f717705a6cd4cc29fe333f5012c7fec466d350b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752481"
---
# <a name="ltsettingsgt-element-network-settings"></a>&lt;ustawienia&gt; elementu (ustawienia sieciowe)
Służy do konfigurowania opcji sieci podstawowej dla <xref:System.Net?displayProperty=nameWithType> przestrzeni nazw.  
  
 \<Konfiguracja >  
\<system.net>  
\<Ustawienia >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<settings>  
  <httpListener> … </httpListener>  
  <httpWebRequest> … </httpWebRequest>  
  <ipv6> … </ipv6>  
  <performanceCounters> … </performanceCounters>  
  <servicePointManager> … </servicePointManager>  
  <socket> … </socket>  
  <webProxyScript> … </webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[HttpListener](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|Dostosowuje parametry używane przez <xref:System.Net.HttpListener> klasy.|  
|[httpWebRequest](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|Dostosowuje parametry żądania sieci Web.|  
|[Protokół IPv6](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|Włącza Internet Protocol w wersji 6 (IPv6) obsługuje.|  
|[\<performanceCounter > elementu (ustawienia sieciowe)](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|Umożliwia sieciowym liczników wydajności.|  
|[Element servicePointManager](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|Służy do konfigurowania połączeń z zasobami sieciowymi.|  
|[Gniazda](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|Określa, czy operacje gniazda używać portów.|  
|[\<webproxyscript — > elementu (ustawienia sieciowe)](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|Konfiguruje właściwości skryptu używana do wykrywania, serwer proxy sieci Web.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Zawiera ustawienia, które określają sposób programu .NET Framework łączy się z siecią.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net?displayProperty=nameWithType>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
