---
title: Typowe scenariusze zabezpieczeń
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0fb51ea0624c4fa686e4e99ffb9c30decedfea10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490906"
---
# <a name="common-security-scenarios"></a>Typowe scenariusze zabezpieczeń
Tematy w tej części wykazu liczba możliwych klienta i konfiguracje zabezpieczeń usługi. Konfiguracje różny w zależności od szeregu czynników. Na przykład czy usługi lub klienta znajduje się w intranecie lub czy zabezpieczeń są dostarczane przez Windows lub transportu (na przykład HTTPS).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Niezabezpieczony klient internetowy i usługa](../../../../docs/framework/wcf/feature-details/internet-unsecured-client-and-service.md)  
 Przykład publiczny, niezabezpieczony klient i usługa.  
  
 [Niezabezpieczony klient i usługa w intranecie](../../../../docs/framework/wcf/feature-details/intranet-unsecured-client-and-service.md)  
 Podstawowe usługi Windows Communication Foundation (WCF) opracowany, aby podać informacje w sieci prywatnej bezpieczny do aplikacji usługi WCF.  
  
 [Zabezpieczenia transportu z uwierzytelnianiem podstawowym](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 Aplikacja umożliwia klientom zalogować się przy użyciu uwierzytelniania niestandardowego.  
  
 [Zabezpieczenia transportu z uwierzytelnianiem systemu Windows](../../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)  
 Przedstawia klientów i usług zabezpieczonych przez zabezpieczenia systemu Windows.  
  
 [Zabezpieczanie transportu za pomocą anonimowego klienta](../../../../docs/framework/wcf/feature-details/transport-security-with-an-anonymous-client.md)  
 Zabezpieczenia transportu (na przykład HTTPS) w tym scenariuszu są używane do zapewnienia poufności i integralności.  
  
 [Zabezpieczanie transportu przy użyciu uwierzytelniania certyfikatów](../../../../docs/framework/wcf/feature-details/transport-security-with-certificate-authentication.md)  
 Pokazuje klienta i usługi zabezpieczone za pomocą certyfikatu.  
  
 [Zabezpieczenia komunikatów z anonimowym klientem](../../../../docs/framework/wcf/feature-details/message-security-with-an-anonymous-client.md)  
 Przedstawia klientów i usług zabezpieczonych przez zabezpieczenia wiadomości WCF.  
  
 [Zabezpieczenia na poziomie komunikatu z użyciem klienta nazwy użytkownika](../../../../docs/framework/wcf/feature-details/message-security-with-a-user-name-client.md)  
 Klient jest aplikacji formularzy systemu Windows, która umożliwia klientom zalogować się przy użyciu nazwy użytkownika domeny i hasła.  
  
 [Zabezpieczenia komunikatów z klientem dysponującym certyfikatem](../../../../docs/framework/wcf/feature-details/message-security-with-a-certificate-client.md)  
 Serwery mają certyfikaty, a każdy klient ma certyfikat. Kontekst zabezpieczeń jest nawiązywane za pośrednictwem negocjacji zabezpieczeń TLS (Transport Layer).  
  
 [Zabezpieczanie komunikatów za pomocą klienta systemu Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md)  
 Zmiana certyfikatu klienta. Serwery mają certyfikaty, a każdy klient ma certyfikat. Kontekst zabezpieczeń jest określana za pomocą negocjowania protokołu TLS.  
  
 [Zabezpieczanie komunikatów za pomocą klienta systemu Windows bez negocjowania poświadczeń](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client-without-credential-negotiation.md)  
 Pokazuje klienta i usługi zabezpieczonej przez protokół Kerberos domeny.  
  
 [Zabezpieczenia komunikatów ze wzajemnymi certyfikatami](../../../../docs/framework/wcf/feature-details/message-security-with-mutual-certificates.md)  
 Serwery mają certyfikaty, a każdy klient ma certyfikat. Certyfikat serwera jest dystrybuowane w aplikacji i jest dostępny poza pasmem.  
  
 [Zabezpieczenia komunikatów z wystawionymi tokenami](../../../../docs/framework/wcf/feature-details/message-security-with-issued-tokens.md)  
 Federacyjnego zabezpieczenia umożliwia ustanowienie zaufania między domenami niezależne.  
  
 [Zaufany podsystem](../../../../docs/framework/wcf/feature-details/trusted-subsystem.md)  
 Klient uzyskuje dostęp do usług sieci Web, które są rozproszone w sieci. Usługi sieci Web dostęp do dodatkowych zasobów (np. baz danych lub innych usług sieci Web), które muszą być zabezpieczone.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Autoryzacja](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
 [Zabezpieczenia](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [Powiązania i zabezpieczenia](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
 [Uwierzytelnianie](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [Autoryzacja](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące zabezpieczeń i najlepsze rozwiązania](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 [Model zabezpieczeń systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
