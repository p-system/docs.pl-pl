---
title: 'Jak: utworzyć dostawcę tokenu zabezpieczającego niestandardowych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], providing credentials
ms.assetid: db8cb478-aa43-478b-bf97-c6489ad7c7fd
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 16bdbf3aa2403a3af603b24df90391d36660dbd4
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808965"
---
# <a name="how-to-create-a-custom-security-token-provider"></a>Jak: utworzyć dostawcę tokenu zabezpieczającego niestandardowych
W tym temacie przedstawiono sposób tworzenia nowych typów tokenu z dostawcę tokenu zabezpieczającego niestandardowych i sposobu integracji dostawcy z Menedżer tokenów zabezpieczających niestandardowych.  
  
> [!NOTE]
>  Utworzyć niestandardowego dostawcę tokenów, jeśli dostarczane przez system tokenów w <xref:System.IdentityModel.Tokens> przestrzeni nazw nie są zgodne z wymaganiami.  
  
 Dostawcy tokenów zabezpieczających tworzy reprezentację tokenu zabezpieczeń na podstawie informacji w poświadczeniach klienta lub usługi. Aby użyć dostawcy tokenów zabezpieczających niestandardowych w zabezpieczeń systemu Windows Communication Foundation (WCF), należy utworzyć niestandardowe poświadczenia i implementacje Menedżer tokenów zabezpieczeń.  
  
 Aby uzyskać więcej informacji o niestandardowych poświadczeń i Menedżer tokenów zabezpieczających zobacz [wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Aby uzyskać więcej informacji o poświadczeniach zabezpieczeń tokenu Menedżera dostawcy klas i uwierzytelniania, zobacz [Architektura zabezpieczeń](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f).  
  
### <a name="to-create-a-custom-security-token-provider"></a>Aby utworzyć dostawcę tokenu zabezpieczającego niestandardowych  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy.  
  
2.  Implementowanie <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> metody. Metoda jest odpowiedzialna za tworzenie i zwracanie wystąpienie tokenu zabezpieczającego. Poniższy przykład tworzy klasę o nazwie `MySecurityTokenProvider`i zastępuje <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> sposób zwrócenia wystąpienia klasy <xref:System.IdentityModel.Tokens.X509SecurityToken> klasy. Konstruktor klasy wymaga wystąpienia <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> klasy.  
  
     [!code-csharp[c_CustomTokenProvider#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#1)]
     [!code-vb[c_CustomTokenProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#1)]  
  
### <a name="to-integrate-a-custom-security-token-provider-with-a-custom-security-token-manager"></a>Aby zintegrować dostawcę tokenu zabezpieczającego niestandardowych z Menedżer tokenów zabezpieczających niestandardowych  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.IdentityModel.Selectors.SecurityTokenManager> klasy. (Poniższy przykład pochodzi z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy, która jest pochodną <xref:System.IdentityModel.Selectors.SecurityTokenManager> klasy.)  
  
2.  Zastąpienie <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> metodę, jeśli jeszcze nie jest przeciążona.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> Metoda jest odpowiedzialna za zwracanie wystąpienia <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy należy <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametr przekazywany do metody przez strukturę zabezpieczeń WCF. Zmodyfikuj metodę, aby zwrócić implementacji dostawcy tokenów zabezpieczeń niestandardowe (utworzonego w poprzedniej procedurze) gdy metoda jest wywoływana z parametrem tokenu odpowiednich ustawień zabezpieczeń. Aby uzyskać więcej informacji na temat Menedżer tokenów zabezpieczających, zobacz [wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
3.  Dodanie logiki niestandardowej metody do zwrócić dostawcy tokenu zabezpieczeń niestandardowe na podstawie <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametru. Poniższy przykład zwraca dostawcę tokenów zabezpieczających niestandardowych, jeśli spełnione są wymagania tokenu. Wymagania obejmują tokenu zabezpieczającego X.509 i kierunek wiadomości (czy jest używany dla danych wyjściowych komunikat). We wszystkich innych przypadkach kod wywołuje klasa podstawowa do obsługi innych wymagań dotyczących zabezpieczeń tokenu zachowanie dostarczane przez system.  
  
 [!code-csharp[c_CustomTokenProvider#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#2)]
 [!code-vb[c_CustomTokenProvider#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#2)]  
  
## <a name="example"></a>Przykład  
 Poniżej pokazano pełnego <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementacji wraz z odpowiednią <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementacji.  
  
 [!code-csharp[c_CustomTokenProvider#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#0)]
 [!code-vb[c_CustomTokenProvider#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#0)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Selectors.SecurityTokenProvider>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.IdentityModel.Tokens.X509SecurityToken>  
 [Przewodnik: tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Instrukcje: tworzenie niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Architektura zabezpieczeń](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
