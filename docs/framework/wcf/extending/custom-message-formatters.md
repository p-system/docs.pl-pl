---
title: Niestandardowe elementy formatujące komunikaty
ms.date: 03/30/2017
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
ms.openlocfilehash: 301c508a0c639985e226dc55f62431ad8bb9c12b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487675"
---
# <a name="custom-message-formatters"></a>Niestandardowe elementy formatujące komunikaty
Zawartość komunikatu jest często w formacie XML, która zazwyczaj nie jest wygodne format dla aplikacji. Aplikacje manipulowania obiektami, pobierania i ustawiania ich właściwości. Windows Communication Foundation (WCF) używa *kontraktu danych* przekonwertować <xref:System.ServiceModel.Channels.Message> obiektu do obiektu z łatwością obsłużyć przez aplikację. Te procesy są nazywane serializacji i deserializacji. Należy pamiętać, że tych samych warunków służą do opisywania serializacji i deserializacji wykonywane przez warstwę transportu do i z formatu przesyłania wiadomości, które jest procesem niepowiązanych.  
  
 Można użyć elementu formatującego niestandardowy komunikat, jeśli musisz wdrożyć specjalne konwersji między komunikatów i obiekty, które nie można wykonać za pomocą kontraktu danych. W tym celu modyfikowania i rozszerzania sposób wykonywania operacji określonym kontraktem na klienta lub usługi.  
  
## <a name="custom-message-formatters-on-the-client"></a>Niestandardowe elementy formatujące komunikaty na kliencie  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Interfejs definiuje metody służące do sterowania konwersji wiadomości w obiekty i do wiadomości dla aplikacji klienckich.  
  
 Musisz zaimplementować ten interfejs. Najpierw zastąpić <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> metodę deserializacji komunikatu. Ta metoda jest wywoływana po otrzymaniu komunikatu przychodzącego, ale przed jego jest wysyłane do operacji klienta.  
  
 Następnie zastąp <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> metody szeregowania obiektu. Ta metoda jest wywoływana przed wysłaniem wiadomości wychodzącej.  
  
 Aby wstawić niestandardowego elementu formatującego do aplikacji usługi, należy przypisać <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> do obiektu <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> właściwości przy użyciu zachowanie operacji. Aby uzyskać informacje dotyczące zachowania, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="custom-message-formatters-on-the-service"></a>Niestandardowe elementy formatujące komunikaty w usłudze  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Interfejs definiuje metody, które konwertują <xref:System.ServiceModel.Channels.Message> obiektu do parametrów operacji i z parametrów w <xref:System.ServiceModel.Channels.Message> obiektów w aplikacji usługi.  
  
 Musisz zaimplementować ten interfejs. Najpierw zastąpić <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> metodę deserializacji komunikatu. Ta metoda jest wywoływana po otrzymaniu komunikatu przychodzącego, ale przed jego jest wysyłane do operacji klienta.  
  
 Następnie zastąp <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> metody szeregowania obiektu. Ta metoda jest wywoływana przed wysłaniem wiadomości wychodzącej.  
  
 Aby wstawić niestandardowego elementu formatującego do aplikacji usługi, należy przypisać <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> do obiektu <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> właściwości przy użyciu zachowanie operacji. Aby uzyskać informacje dotyczące zachowania, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>  
 [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
