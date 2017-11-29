---
title: 'Instrukcje: Eksportowanie niestandardowych asercji zasad'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 466aecb5102332d3e246fd340e43b482d2c17a4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-export-custom-policy-assertions"></a><span data-ttu-id="d9fb8-102">Instrukcje: Eksportowanie niestandardowych asercji zasad</span><span class="sxs-lookup"><span data-stu-id="d9fb8-102">How to: Export Custom Policy Assertions</span></span>
<span data-ttu-id="d9fb8-103">Potwierdzenia zasad opisano wymagania punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="d9fb8-103">Policy assertions describe the capabilities and requirements of a service endpoint.</span></span> <span data-ttu-id="d9fb8-104">Aplikacje usługi mogą używać niestandardowych asercji zasad w metadanych usługi do komunikowania się punkt końcowy, powiązanie lub kontrakt informacje o dostosowaniu do aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="d9fb8-104">Service applications can use custom policy assertions in service metadata to communicate endpoint, binding or contract customization information to the client application.</span></span> <span data-ttu-id="d9fb8-105">Można użyć [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] można wyeksportować potwierdzenia w wyrażeniach zasad dołączona w powiązania WSDL na punkt końcowy, operacji lub komunikat tematów, w zależności od możliwości lub wymagania komunikują się.</span><span class="sxs-lookup"><span data-stu-id="d9fb8-105">You can use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to export assertions in policy expressions attached in WSDL bindings at the endpoint, operation, or message subjects, depending upon the capabilities or requirements you are communicating.</span></span>  
  
 <span data-ttu-id="d9fb8-106">Niestandardowych asercji zasad są eksportowane z zastosowaniem <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interfejs w <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> i wstawianie element powiązania bezpośrednio do powiązania punktu końcowego usługi lub poprzez zarejestrowanie element powiązania w aplikacji plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d9fb8-106">Custom policy assertions are exported by implementing the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface on a <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> and either inserting the binding element directly into the binding of the service endpoint or by registering the binding element in your application configuration file.</span></span> <span data-ttu-id="d9fb8-107">Implementacji eksportu zasad należy dodać potwierdzenia Twojej zasad niestandardowych jako <xref:System.Xml.XmlElement?displayProperty=nameWithType> wystąpienie do odpowiedniego <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> na <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> przekazany <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d9fb8-107">Your policy export implementation should add your custom policy assertion as a <xref:System.Xml.XmlElement?displayProperty=nameWithType> instance to the appropriate <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> on the <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> passed into the <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> method.</span></span>  
  
 <span data-ttu-id="d9fb8-108">Ponadto należy sprawdzić <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> właściwość <xref:System.ServiceModel.Description.WsdlExporter> klasy i eksportowanie zasad zagnieżdżonych wyrażeń atrybutów framework zasad w poprawną przestrzeń nazw na podstawie określonej wersji zasad.</span><span class="sxs-lookup"><span data-stu-id="d9fb8-108">In addition you must check the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property of the <xref:System.ServiceModel.Description.WsdlExporter> class and export nested policy expressions and policy framework attributes in the correct namespace based on the policy version specified.</span></span>  
  
 <span data-ttu-id="d9fb8-109">Aby zaimportować niestandardowych asercji zasad, zobacz <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> i [porady: importowanie niestandardowych asercji zasad](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md).</span><span class="sxs-lookup"><span data-stu-id="d9fb8-109">To import custom policy assertions, see <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> and [How to: Import Custom Policy Assertions](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md).</span></span>  
  
### <a name="to-export-custom-policy-assertions"></a><span data-ttu-id="d9fb8-110">Aby wyeksportować niestandardowych asercji zasad</span><span class="sxs-lookup"><span data-stu-id="d9fb8-110">To export custom policy assertions</span></span>  
  
1.  <span data-ttu-id="d9fb8-111">Implementowanie <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interfejs w <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d9fb8-111">Implement the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface on a <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d9fb8-112">Poniższy przykładowy kod przedstawia implementację potwierdzenia zasad niestandardowych, na poziomie powiązania.</span><span class="sxs-lookup"><span data-stu-id="d9fb8-112">The following code example shows the implementation of a custom policy assertion at the binding level.</span></span>  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2.  <span data-ttu-id="d9fb8-113">Wstaw element powiązania do punktu końcowego powiązanie albo programowo lub przy użyciu pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d9fb8-113">Insert the binding element into the endpoint binding either programmatically or using an application configuration file.</span></span> <span data-ttu-id="d9fb8-114">Zobacz poniższe procedury.</span><span class="sxs-lookup"><span data-stu-id="d9fb8-114">See the following procedures.</span></span>  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a><span data-ttu-id="d9fb8-115">Aby wstawić element powiązania przy użyciu pliku konfiguracji aplikacji</span><span class="sxs-lookup"><span data-stu-id="d9fb8-115">To insert a binding element using an application configuration file</span></span>  
  
1.  <span data-ttu-id="d9fb8-116">Implementowanie <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> Twojego elementu powiązania potwierdzenia zasad niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d9fb8-116">Implement <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> for your custom policy assertion binding element.</span></span>  
  
2.  <span data-ttu-id="d9fb8-117">Dodaj element rozszerzenia powiązania do pliku konfiguracji przy użyciu [ \<bindingElementExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="d9fb8-117">Add the binding element extension to the configuration file using the [\<bindingElementExtensions>](../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md) element.</span></span>  
  
3.  <span data-ttu-id="d9fb8-118">Tworzenie niestandardowego powiązania za pomocą <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d9fb8-118">Build a custom binding using the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-insert-a-binding-element-programmatically"></a><span data-ttu-id="d9fb8-119">Aby wstawić element powiązania programowo</span><span class="sxs-lookup"><span data-stu-id="d9fb8-119">To insert a binding element programmatically</span></span>  
  
1.  <span data-ttu-id="d9fb8-120">Utwórz nową <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> i dodaj go do <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d9fb8-120">Create a new <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> and add it to a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span></span>  
  
2.  <span data-ttu-id="d9fb8-121">Dodawanie niestandardowego powiązania z kroku 1.</span><span class="sxs-lookup"><span data-stu-id="d9fb8-121">Add the custom binding from step 1.</span></span> <span data-ttu-id="d9fb8-122">do nowego punktu końcowego i Dodaj ten nowy punkt końcowy usługi do <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> przez wywołanie metody <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d9fb8-122">to a new endpoint and add that new service endpoint to the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> by calling the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
3.  <span data-ttu-id="d9fb8-123">Otwórz <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="d9fb8-123">Open the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="d9fb8-124">Poniższy przykładowy kod przedstawia tworzenie niestandardowego powiązania i programowe wstawiania elementów wiązania.</span><span class="sxs-lookup"><span data-stu-id="d9fb8-124">The following code example shows the creation of a custom binding and the programmatic insertion of binding elements.</span></span>  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d9fb8-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9fb8-125">See Also</span></span>  
 <xref:System.ServiceModel.Description.IPolicyImportExtension>  
 <xref:System.ServiceModel.Description.IPolicyExportExtension>  
 [<span data-ttu-id="d9fb8-126">Porady: importowanie niestandardowych asercji zasad</span><span class="sxs-lookup"><span data-stu-id="d9fb8-126">How to: Import Custom Policy Assertions</span></span>](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)