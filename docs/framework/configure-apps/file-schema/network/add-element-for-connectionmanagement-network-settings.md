---
title: '&lt;Dodaj&gt; elementu connectionmanagement — (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add
helpviewer_keywords:
- <add> element, connectionManagement
- <connectionManagement>, add element
- add element, connectionManagement
- connectionManagement, add element
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c6cfd036a98c345da23fc7b3699987c9678e149d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753745"
---
# <a name="ltaddgt-element-for-connectionmanagement-network-settings"></a>&lt;Dodaj&gt; elementu connectionmanagement — (ustawienia sieciowe)
Dodaje adres IP lub nazwa DNS do listy zarządzania połączenia.  
  
 \<Konfiguracja >  
\<system.net>  
\<connectionmanagement — >  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<add   
  address="address expression"   
  maxconnection="integer"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Atrybut**|**Opis**|  
|-------------------|---------------------|  
|`address`|Ciąg opisujący adresu IP lub nazwy DNS.|  
|`maxconnection`|Maksymalna liczba połączeń z serwerem. Jeśli nie zostaną podane, wartość domyślna to 2.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[connectionmanagement —](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|Określa maksymalną liczbę połączeń z hostem sieci.|  
  
## <a name="remarks"></a>Uwagi  
 Wartość `address` atrybut powinien być gwiazdkę, aby wskazać wszystkie połączenia lub ciąg w formie `<schema>://<idn_hostname>[:<port>]`.  
  
 Jeśli identyfikator URI przekazane do żadnych interfejsów API HTTP zawiera Unicode, nazwa zostanie przekonwertowany wewnętrznie przy użyciu <xref:System.Uri.DnsSafeHost%2A> które może zwracać ciąg punicode (zachowanie zależy od bieżącej konfiguracji IDN).  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład konfiguruje aplikację do korzystania z połączeń cztery www.contoso.com serwera i dwa połączenia do innych serwerów.  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
