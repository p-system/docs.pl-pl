---
title: 'Instrukcje: Zabezpieczanie usługi za pomocą certyfikatu X.509'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 73fd9919d1403ef592e5b81c11b6eb659baea669
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493045"
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a>Instrukcje: Zabezpieczanie usługi za pomocą certyfikatu X.509
Zabezpieczanie usługi za pomocą certyfikatu X.509 to technika podstawowe, używanego przez większość powiązania w systemie Windows Communication Foundation (WCF). W tym temacie przedstawiono kroki konfigurowania samodzielnie hostowana usługa za pomocą certyfikatu X.509.  
  
 Warunkiem wstępnym jest ważny certyfikat, który może służyć do uwierzytelniania serwera. Certyfikat musi wystawiony na serwerze przez zaufany urząd certyfikacji. Jeśli certyfikat nie jest prawidłowy, każdy klient próbuje użyć usługi nie ufa usługi, a w związku z tym połączenie nie zostanie ustanowione. Aby uzyskać więcej informacji o korzystaniu z certyfikatów, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a>Aby skonfigurować usługę przy użyciu certyfikatu przy użyciu kodu  
  
1.  Utworzyć kontrakt usługi i Usługa zaimplementowana. Aby uzyskać więcej informacji, zobacz [projektowanie i Implementowanie usług](../../../../docs/framework/wcf/designing-and-implementing-services.md).  
  
2.  Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw jego tryb zabezpieczeń <xref:System.ServiceModel.SecurityMode.Message>, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3.  Utwórz dwa <xref:System.Type> zmiennych, z których jeden typ kontraktu i zaimplementowanego kontraktu, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4.  Utwórz wystąpienie <xref:System.Uri> klasy dla podstawowego adresu usługi. Ponieważ `WSHttpBinding` używa transportu HTTP, jednolity identyfikator zasobów (URI) musi zaczynać się od tego schematu lub Windows Communication Foundation (WCF) spowoduje zgłoszenie wyjątku, gdy usługa jest otwarty.  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5.  Utwórz nowe wystąpienie klasy <xref:System.ServiceModel.ServiceHost> klasy z zaimplementowanym kontrakcie typu zmienną i identyfikator URI.  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6.  Dodaj <xref:System.ServiceModel.Description.ServiceEndpoint> do usługi przy użyciu <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody. Przekaż kontraktu, powiązania i adresu punktu końcowego dla konstruktora, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7.  Opcjonalna. Aby pobrać metadane z usługi, Utwórz nową <xref:System.ServiceModel.Description.ServiceMetadataBehavior> obiektu i ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> właściwości `true`.  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8.  Użyj <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> klasę, aby dodać prawidłowy certyfikat do usługi. Metoda może używać jednej z kilku metod można znaleźć certyfikatu. W tym przykładzie użyto <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> wyliczenia. Wyliczenie Określa, czy podana wartość jest nazwą jednostki, który certyfikat został wystawiony dla.  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. Wywołanie <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metodę, aby rozpocząć nasłuchiwania usługi. W przypadku tworzenia aplikacji konsoli, należy wywołać <xref:System.Console.ReadLine%2A> metody, aby zapewnić usługę w stanie nasłuchiwania.  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metodę, aby skonfigurować usługę za pomocą certyfikatu X.509.  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Następujących przestrzeni nazw są wymagane, aby skompilować kod:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.Web.Services.Description>  
  
-   <xref:System.Security.Cryptography.X509Certificates>  
  
-   <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
