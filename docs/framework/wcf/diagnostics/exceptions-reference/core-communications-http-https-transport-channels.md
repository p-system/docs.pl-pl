---
title: 'Podstawowe wiadomości: Kanały transportu HTTP i HTTPS'
ms.date: 03/30/2017
ms.assetid: 6c0a23c9-a663-461c-bdab-58b4d3e23642
ms.openlocfilehash: fbdb5b350425aad7108402dec939f036e971d053
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473330"
---
# <a name="core-communications-httphttps-transport-channels"></a>Podstawowe wiadomości: Kanały transportu HTTP/HTTPS
W tym temacie wymieniono wszystkie wyjątki generowane przez kanały programu Windows Communication Foundation (WCF) transportu HTTP/HTTPS.  
  
## <a name="exception-list"></a>Listy wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|DigestExplicitCredsImpersonationLevel|Określono poziom personifikacji określony. Uwierzytelniania Digest protokołu HTTP obsługuje tylko poziom "Personifikacji", gdy jest używany z jawnym poświadczeniem.|  
|FramingContentTypeMismatch|Określony typ zawartości nie jest obsługiwana przez określoną usługę. Powiązania klienta i usługi mogą być niezgodne.|  
|Hosting_SslSettingsMisconfigured|Ustawienia protokołu Secure Sockets Layer dla określonej usługi nie są zgodne z tych funkcji w usługach Internet Information Services.|  
|HttpAuthSchemeAndClientCert|Fabryka odbiornika protokołu HTTPS została skonfigurowana do wymagają certyfikatu klienta i określony schemat uwierzytelniania. Jednak tylko jedna forma uwierzytelniania klienta może być wymagana jednocześnie.|  
|HttpReceiveFailure|Wystąpił błąd podczas odbierania odpowiedzi HTTP do określonego. Powiązanie punktu końcowego usługi nie może używać protokołu HTTP. Inną możliwością jest, że kontekst żądania HTTP został przerwany przez serwer z powodu zamykania usługi. Zobacz dzienniki serwera, aby uzyskać więcej informacji.|  
|HttpRegistrationAccessDenied|Protokół HTTP nie można zarejestrować określonego adresu URL. Proces nie ma praw dostępu do tej przestrzeni nazw (zobacz http://msdn.microsoft.com/library/default.asp?url=/library/http/http/namespace_reservations_registrations_and_routing.asp szczegółowe informacje).|  
|HttpRegistrationAlreadyExists|Protokół HTTP nie można zarejestrować określonego adresu URL. Inna aplikacja już zarejestrowany ten adres URL protokołu HTTP. SYS.|  
|HttpRegistrationPortInUse|Protokół HTTP nie można zarejestrować określonego adresu URL, ponieważ określony port TCP jest używany przez inną aplikację.|  
|HttpSendFailure|Wystąpił błąd podczas tworzenia żądania HTTP do określonego. Upewnij się, że przyczyną nie jest niezgodność powiązania zabezpieczeń. Upewnij się również, że usługa nie jest skonfigurowany dla protokołu Secure Sockets Layer.|  
|MessageXmlProtocolError|Wystąpił problem z plikiem XML odebranym z sieci. Zobacz wyjątek wewnętrzny, aby uzyskać więcej informacji.|  
|MissingContentType|Odbiorca zwrócił błąd wskazujący, że brak typu zawartości na żądanie do określonego. Zobacz wyjątek wewnętrzny, aby uzyskać więcej informacji.|  
|ProxyAuthenticationLevelMismatch|Poświadczenie uwierzytelnienia serwera proxy HTTP określić wymaganie wzajemnego uwierzytelniania, które jest bardziej restrykcyjne od wymagania dotyczącego uwierzytelnienia serwera docelowego.|  
|ProxyImpersonationLevelMismatch|Poświadczenie uwierzytelnienia serwera proxy HTTP określiło ograniczenie poziomu personifikacji, który jest bardziej restrykcyjne od ograniczenia dotyczącego uwierzytelnienia serwera docelowego.|  
|SecureChannelFailure|Bezpieczny kanał nie można ustanowić dla Secure Socket Layer/Transport Layer Security z urzędem określony.|  
|TrustFailure|Nie można ustanowić relacji zaufania dla Secure Sockets Layer / Transport Layer Security bezpieczny kanał z urzędem określony.|  
|UseDefaultWebProxyCantBeUsedWithExplicitProxyAddress|Nie można określić adres serwera proxy jawne, a także UseDefaultWebProxy = true w elemencie Twojej HttpTransportBinding.|
