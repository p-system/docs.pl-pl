---
title: Konfigurowanie serializacji w usłudze przepływu pracy
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 74d9a812b9e0cd51a401fa3526c947d52413807a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488875"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Konfigurowanie serializacji w usłudze przepływu pracy
Usługi przepływu pracy są usług Windows Communication Foundation (WCF), więc za pomocą opcji <xref:System.Runtime.Serialization.DataContractSerializer> (ustawienie domyślne) lub <xref:System.Xml.Serialization.XmlSerializer>. Podczas zapisywania bez przepływu pracy typu serializatora do użycia usług został określony w kontrakcie usługi lub operacji. Podczas tworzenia usługi przepływu pracy WCF w kodzie braku określenia tych umów, ale raczej są one generowane w czasie wykonywania przez wnioskowania kontraktu. Aby uzyskać więcej informacji na temat wnioskowania kontraktu, zobacz [za pomocą kontraktów w przepływie pracy](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  Serializator jest określona za pomocą <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> właściwości. To może można ustawić w projektancie, jak pokazano na poniższej ilustracji.  
  
 ![Ustawienia serializatora](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")  
  
 Serializator również można ustawić w kodzie, jak pokazano w poniższym przykładzie  
  
```  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
 Znane typy można określać również usług przepływu pracy. Aby uzyskać więcej informacji na temat znanych typów zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Znane typy można określić w Projektancie lub w kodzie. Aby określić znanych typów w projektancie, kliknij przycisk wielokropka obok właściwości element KnownTypes w oknie dialogowym właściwości <xref:System.ServiceModel.Activities.Receive> działania, jak pokazano na poniższej ilustracji.  
  
 ![Element KnownTypes właściwości](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "element KnownTypes")  
  
 Spowoduje to wyświetlenie Edytor kolekcji typów, który umożliwia wyszukiwanie i określ znanych typów.  
  
 ![Dodawanie ze znanych typów](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")  
  
 Kliknij przycisk **dodać nowy typ** link i użyć listy do wybierania lub wyszukiwania typu można dodać do kolekcji znanych typów. Aby określić znane typy używany kod <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> właściwości, jak pokazano w poniższym przykładzie.  
  
```  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
            approveExpense.KnownTypes.Add(typeof(Travel));  
            approveExpense.KnownTypes.Add(typeof(Meal));  
```  
  
 Aby wyświetlić pełny przykład kodu przedstawiający Konfigurowanie serializacji dla usługi przepływów pracy zobacz [formatowania wiadomości w przepływie pracy usług](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).
