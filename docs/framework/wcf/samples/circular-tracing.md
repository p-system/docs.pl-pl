---
title: Śledzenie cykliczne
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: ce39a5d1b65bad78ff67154a7d8b62c2f19b1fa9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33503314"
---
# <a name="circular-tracing"></a>Śledzenie cykliczne
W tym przykładzie przedstawiono implementacji obiektu nasłuchującego śledzenia cyklicznego buforu. Typowy scenariusz dla usług produkcji jest usług, które są dostępne przez dłuższy czas i ma włączonego na niskim poziomie rejestrowania śledzenia. Te usługi używać dużej ilości miejsca na dysku. Podczas rozwiązywania problemów z usługą, najnowszych danych w dzienniku śledzenia ma zastosowanie w rozwiązaniu problemu. Ten przykład przedstawia implementację odbiornika śledzenia cyklicznego buforu, w którym tylko najnowsze dane śledzenia są przechowywane na dysku do skonfigurowanej ilości danych. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i zawiera odbiornik śledzenia niestandardowych.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie przyjęto założenie, że czytelnik zna [śledzenie i rejestrowanie komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) przykładowe i przeczytanie w dokumentacji dostarczonej [śledzenie i rejestrowanie komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) próbki.  
  
## <a name="circular-buffer-trace-listener"></a>Odbiornik śledzenia bufora cykliczne  
 Pojęcie za implementacji obiektu nasłuchującego śledzenia cyklicznego buforu jest dwóch plików, które każdego przechowywać do połowy danych dziennika całkowita żądanego śledzenia. Odbiornik tworzą jeden plik i zapisuje do tego pliku, dopóki nie osiągnie limitu połowy rozmiaru danych, po czym przełącza do pliku. Gdy odbiornika osiągnie limit dla drugiego pliku - zastępuje pierwszy plik z nowe śledzenie.  
  
 Tym odbiorniku pochodną `XmlWriteTraceListener` i umożliwia dzienniki, aby je przeglądać za pomocą [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Podczas próby wyświetlić dzienniki, dwa pliki dziennika można łatwo odtwarzane otwierając oba pliki dziennika w tym samym czasie w narzędziu Podgląd śledzenia usługi. Narzędzia podglądu śledzenia usługi automatycznie odpowiada on za sortowanie dane śledzenia, aby były wyświetlane w odpowiedniej kolejności.  
  
## <a name="configuration"></a>Konfiguracja  
 Usługę można skonfigurować do używania cykliczne nasłuchującego śledzenia buforu, dodając następujący kod dla elementów źródła i odbiornika. Maksymalny rozmiar jest określany przez ustawienie `maxFileSizeKB` atrybut w konfiguracji odbiornika śledzenia cykliczne. Zostało to przedstawione w poniższym kodzie.  
  
```xml  
<system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">  
      <listeners>  
        <add name="CircularTraceListener" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"   
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Pamiętaj, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
