---
title: Obsługą elementu ReceiveContext kanały programu WCF
ms.date: 03/30/2017
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
ms.openlocfilehash: 3e5ac914ae4d0c97ed617ea4a8d5a893ec740179
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502937"
---
# <a name="receivecontext-enabled-wcf-channels"></a>Obsługą elementu ReceiveContext kanały programu WCF
W tym przykładzie pokazano przydatność <xref:System.ServiceModel.Channels.ReceiveContext>— włączone kanały programu WCF. Przykład implementuje usługi można znaleźć iloczyn dwóch liczb za pomocą kanału NetMSMQ.  
  
 <xref:System.ServiceModel.Channels.ReceiveContext> Klasa umożliwia aplikacji zdecyduj, czy dostęp do wiadomości lub pozostaw w kolejce dla dalszego przetwarzania, nawet po sprawdzeniu treści wiadomości. W tym przykładzie klient wysyła losowych liczb całkowitych do kolejką transakcyjną. `ProductCalculator` Usługa odbiera komunikaty i sprawdza treść wiadomości, które są liczbami całkowitymi, aby określić, czy można obliczyć produktu. Jeśli operacja usługi nie zawiera produktu, wiadomość jest przywracane do kolejki i mogą być ponownie odbierane przez usługę nasłuchiwania w kolejce.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Upewnij się, że zainstalowano usługi kolejkowania wiadomości firmy Microsoft (MSMQ).  
  
    1.  Aby zainstalować usługi MSMQ na [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:  
  
        1.  W **Menedżera serwera**, kliknij przycisk **funkcji**.  
  
        2.  W prawym okienku w obszarze **Podsumowanie funkcji**, kliknij przycisk **Dodaj funkcje**.  
  
        3.  W oknie wynikowy rozwiń **usługi kolejkowania komunikatów**.  
  
        4.  Rozwiń węzeł **komunikatów usługi kolejkowania wiadomości**.  
  
        5.  Kliknij przycisk **integracji z usługami katalogu** (na komputerach przyłączonych do domeny), a następnie kliknij przycisk **obsługi protokołu HTTP**.  
  
        6.  Kliknij przycisk **dalej**, a następnie kliknij przycisk **zainstalować**.  
  
    2.  Aby zainstalować usługi MSMQ na [!INCLUDE[wv](../../../../includes/wv-md.md)]:  
  
        1.  Otwórz **Panel sterowania**.  
  
        2.  Kliknij przycisk **programy** , a następnie w obszarze **programy i funkcje**, kliknij przycisk **włączyć lub wyłączyć funkcje systemu Windows**.  
  
        3.  Rozwiń węzeł **serwera Microsoft kolejki komunikatów (MSMQ)**, rozwiń węzeł **Microsoft kolejki komunikatów (MSMQ) Server Core**, a następnie zaznacz pola wyboru dla następujące funkcje usługi kolejkowania komunikatów do zainstalowania:  
  
            -   Serwer usługi kolejkowania komunikatów  
  
            -   Usługa MSMQ domeny integracji usług Active Directory (na komputerach przyłączonych do domeny)  
  
            -   Obsługa protokołu HTTP w usłudze MSMQ  
  
        4.  Kliknij przycisk **OK**.  
  
        5.  Jeśli zostanie wyświetlony monit o ponowne uruchomienie komputera, kliknij przycisk **OK** do ukończenia instalacji.  
  
2.  Upewnij się, że [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] jest zainstalowany na komputerze.  
  
3.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania ReceiveContextProductGenerator.sln.  
  
4.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
5.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.
