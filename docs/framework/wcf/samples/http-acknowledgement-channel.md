---
title: Kanał potwierdzania HTTP
ms.date: 03/30/2017
ms.assetid: 469f3056-5ef2-4753-8acf-b574d23d83cf
ms.openlocfilehash: c56b2fbe9d0bac3143ee7d234fd36a75f7b8071c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502835"
---
# <a name="http-acknowledgement-channel"></a>Kanał potwierdzania HTTP
Kanał potwierdzania HTTP jest przykładem warstwowego kanału, który zmienia jednokierunkowe wzorzec przesyłania komunikatów, co umożliwia usłudze potwierdzić lub odmówić wiadomości przychodzących, a nie automatycznie wysyła po otrzymaniu potwierdzenia. Kanał potwierdzania HTTP umożliwia również usługą Opóźnienie potwierdzenia do momentu go gwarancji biznesowej, otrzymasz wiadomość.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.ServiceModel.Channels.ReceiveContext>, Warstwowego kanału przykład (kanał potwierdzania HTTP).  
  
## <a name="discussion"></a>Omówienie  
 Kanał potwierdzania HTTP implementuje <xref:System.ServiceModel.Channels.ReceiveContext> Aby przekształcić wzorzec komunikatów żądanie odpowiedź HTTP do wzorca jednokierunkowe opóźnione potwierdzenia. Za pomocą tego nowego wzorca, usługi zapewnia przetwarzania komunikatów przez wysłanie potwierdzenia w postaci kodu stanu HTTP OK 200 bez blokowania klienta, aż do ukończenia przetwarzania komunikatu, lub wysłać komunikat o błędzie do klienta w postaci HTTP Wewnętrzny serwer kod stanu błędu 500. Na przykład usługi można wysłać potwierdzenie po zapisaniu wiadomości do kolejki, a następnie kontynuuj, przetwarzanie wiadomości asynchronicznie. W tym scenariuszu klient może mieć pewność, że jego wiadomości przetworzono co najmniej raz przez usługę, jeśli ponownie program wysyłane wiadomości do momentu otrzymania potwierdzenia z usługi. Należy zauważyć, że jeśli usługa wymaga przetwarzania za pośrednictwem protokołu HTTP bez żadnych gwarancji, przetwarzania komunikatów o fast asynchroniczne, a następnie <xref:System.ServiceModel.Channels.OneWayBindingElement> jest to odpowiednie rozwiązanie.  
  
 <xref:System.ServiceModel.Channels.ReceiveContext> Służy do przechowywania wiadomości w miejsce, gdy okaże się, czy wiadomości mogą być przetwarzane w usłudze. Możliwość pomyślnie przetworzyć komunikatu usługi jest określane przez wywoływanie Complete <xref:System.ServiceModel.Channels.ReceiveContext> obiekt, który wysyła kod stanu HTTP OK i czy usługa może przetworzyć komunikatu jest wskazane przez wywołanie metody <xref:System.ServiceModel.Channels.ReceiveContext>w `Abandon` Metoda <xref:System.ServiceModel.Channels.ReceiveContext> obiektu, który wysyła kod stanu błędu wewnętrznego serwera HTTP.  
  
 W tym przykładzie klient żąda informacji przetwarzania przez wysyłanie identyfikatora pracownika. Na stronie usługi, jeśli identyfikator Odebrano jest większa niż 50, usługa wysyła kod stanu HTTP 500 (wewnętrzny błąd serwera) z powrotem do klienta, w przeciwnym razie zakłada się, że przetwarzanie może być wykonane pomyślnie i wysyła kod stanu HTTP 200 ( Pomyślne) do klienta.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Otwórz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] z uprawnieniami administratora.  
  
2.  Otwórz **HttpAckChannel** rozwiązania.  
  
3.  Uruchom nowe wystąpienie klasy **usługi** projektu, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**i wybierając **debugowania**, **Start nowe wystąpienie** z menu kontekstowego.  
  
4.  Uruchom nowe wystąpienie klasy **klienta** projektu, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**i wybierając **debugowania**, i **Start nowe wystąpienie** z menu kontekstowego.  
  
5.  Po uruchomieniu usługi, naciśnij klawisz ENTER w oknie klienta, aby umożliwić klientowi wysłać komunikatu do usługi.  
  
6.  Pierwszy komunikat jest przetwarzany w usłudze, a kod stanu HTTP OK wysyła do klienta.  
  
7.  Drugi komunikat zakończy się niepowodzeniem, a kod stanu błędu wewnętrznego serwera HTTP wysyłane z powrotem do klienta, który wywołuje <xref:System.ServiceModel.CommunicationException> na kliencie.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpAckChannel`
