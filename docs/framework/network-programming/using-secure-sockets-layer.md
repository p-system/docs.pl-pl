---
title: Przy użyciu bezpiecznych gniazd warstwy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Networking
- SSL
- Secure Sockets Layer
- requesting data from Internet, Secure Sockets Layer
- sending data, Secure Sockets Layer
- Network Resources
- data requests, Secure Sockets Layer
- receiving data, Secure Sockets Layer
- Internet, Secure Sockets Layer
ms.assetid: 6e4289e6-d1b7-4e82-ab0d-e83e3b6063ed
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2baedaa445f81e3e204f7414c5142232755581ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396249"
---
# <a name="using-secure-sockets-layer"></a>Przy użyciu bezpiecznych gniazd warstwy
<xref:System.Net> Klasy użyj protokół Secure Sockets Layer (SSL) do szyfrowania połączenia dla kilku protokołów sieciowych.  
  
 W przypadku połączeń http <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy używają protokołu SSL do komunikowania się z hostami sieci web, które obsługują protokół SSL. Decyzja do używania protokołu SSL jest tworzone przez <xref:System.Net.WebRequest> klasy oparte na identyfikator URI jest on podawany. Jeśli identyfikator URI, który rozpoczyna się od "https:", używany jest protokół SSL; Jeśli identyfikator URI rozpoczyna się od ciągu "http:", nieszyfrowanego połączenia jest używany.  
  
 Aby używać protokołu SSL z protokołem FTP (File Transfer), ustaw <xref:System.Net.FtpWebRequest.EnableSsl> właściwości na wartość true, przed wywołaniem <xref:System.Net.FtpWebRequest.GetResponse>. Podobnie do używania protokołu SSL z transportu protokołu SMTP (Simple Mail), należy ustawić <xref:System.Net.Mail.SmtpClient.EnableSsl> właściwości na wartość true przed wysłaniem wiadomości e-mail.  
  
 <xref:System.Net.Security.SslStream> Klasy zapewnia abstrakcji strumienia SSL i oferuje wiele sposobów konfigurowania procedury uzgadniania protokołu SSL.  
  
## <a name="example"></a>Przykład  
  
### <a name="code"></a>Kod  
  
```vb  
Dim MyURI As String = "https://www.contoso.com/"  
Dim Wreq As WebRequest = WebRequest.Create(MyURI)  
  
Dim serverUri As String = "ftp://ftp.contoso.com/file.txt"  
Dim request As FtpWebRequest = CType(WebRequest.Create(serverUri), FtpWebRequest)  
request.Method = WebRequestMethods.Ftp.DeleteFile  
request.EnableSsl = True  
Dim response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)  
```  
  
```csharp  
String MyURI = "https://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
  
String serverUri = "ftp://ftp.contoso.com/file.txt"  
FtpWebRequest request = (FtpWebRequest)WebRequest.Create(serverUri);  
request.EnableSsl = true;  
request.Method = WebRequestMethods.Ftp.DeleteFile;  
FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołuje się do **System.Net** przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia w programowaniu sieciowym](../../../docs/framework/network-programming/security-in-network-programming.md)  
 [Programowanie dla sieci w programie .NET Framework](../../../docs/framework/network-programming/index.md)  
 [Wybór i sprawdzanie poprawności certyfikatu](../../../docs/framework/network-programming/certificate-selection-and-validation.md)
