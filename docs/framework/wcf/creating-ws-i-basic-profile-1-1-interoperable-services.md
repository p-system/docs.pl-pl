---
title: Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: aa76a6633ef86a908e00bb9dcb1b16eefe35c12d
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804953"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I
Aby skonfigurować punkt końcowy usługi WCF do współdziałać z [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] obsługi klientów w sieci Web:  
  
-   Użyj <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> typu powiązanie dla punktu końcowego usługi.  
  
-   Nie używaj wywołania zwrotnego i funkcje kontraktu sesji lub transakcji zachowania punktu końcowego usługi  
  
 Opcjonalnie można włączyć obsługę uwierzytelniania klienta na poziomie transportu dla powiązania i HTTPS.  
  
 Poniższe funkcje <xref:System.ServiceModel.BasicHttpBinding> klasy wymagają funkcji poza WS-I Basic Profile 1.1:  
  
-   Kodowanie komunikatu mechanizmu optymalizacji transmisji (MTOM) komunikatu kontrolowane przez <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> właściwości. Pozostaw tę właściwość na wartość domyślną, która jest <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> aby nie używać mechanizmu MTOM.  
  
-   Kontrolowane przez zabezpieczenia wiadomości <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> wartość zapewnia obsługę WS-Security zgodne z WS-I Basic 1.0 profil zabezpieczeń. Pozostaw tę właściwość na wartość domyślną, która jest <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> nieużywanie WS-Security.  
  
 Aby udostępnić metadanych dla usługi WCF [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], użyj narzędzia generowania klienta usługi sieci Web: [narzędzia języka opisu usługi sieci Web (Wsdl.exe)](http://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88), [narzędzia odnajdywania usług sieci Web (Disco.exe)](http://msdn.microsoft.com/library/acd88078-c581-42bc-94ca-6633e2851979)i `Add Web Reference` funkcji w programie Visual Studio; należy włączyć publikowanie metadanych. Aby uzyskać więcej informacji, zobacz [publikowanie punktów końcowych metadanych](../../../docs/framework/wcf/publishing-metadata-endpoints.md).  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykładowy kod przedstawia sposób dodawania punktu końcowego WCF, która jest zgodna z [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sieci Web obsługi klientów w kodzie i alternatywnie w pliku konfiguracji.  
  
### <a name="code"></a>Kod  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie z usługami ASP.NET w sieci Web](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
