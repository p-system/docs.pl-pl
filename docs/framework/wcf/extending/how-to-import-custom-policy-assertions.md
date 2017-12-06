---
title: 'Instrukcje: Importowanie niestandardowych asercji zasad'
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
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3cc7eecbef66c3e4a80759912260b973d441a8a3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-import-custom-policy-assertions"></a><span data-ttu-id="aa662-102">Instrukcje: Importowanie niestandardowych asercji zasad</span><span class="sxs-lookup"><span data-stu-id="aa662-102">How to: Import Custom Policy Assertions</span></span>
<span data-ttu-id="aa662-103">Potwierdzenia zasad opisano wymagania punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="aa662-103">Policy assertions describe the capabilities and requirements of a service endpoint.</span></span>  <span data-ttu-id="aa662-104">Aplikacje klienckie można użyć potwierdzeń zasad w metadanych usługi, aby skonfigurować klienta powiązanie lub dostosować kontraktu usługi dla punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="aa662-104">Client applications can use policy assertions in service metadata to configure the client binding or to customize the service contract for a service endpoint.</span></span>  
  
 <span data-ttu-id="aa662-105">Niestandardowych asercji zasad są importowane z zastosowaniem <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interfejsu i przekazywanie obiektu metadanych systemu lub rejestrując implementacja typu w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa662-105">Custom policy assertions are imported by implementing the <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface and passing that object to the metadata system or by registering the implementation type in your application configuration file.</span></span>  <span data-ttu-id="aa662-106">Implementacje <xref:System.ServiceModel.Description.IPolicyImportExtension> interfejsu podać konstruktora domyślnego.</span><span class="sxs-lookup"><span data-stu-id="aa662-106">Implementations of the <xref:System.ServiceModel.Description.IPolicyImportExtension> interface must provide a default constructor.</span></span>  
  
### <a name="to-import-custom-policy-assertions"></a><span data-ttu-id="aa662-107">Aby importowanie niestandardowych asercji zasad</span><span class="sxs-lookup"><span data-stu-id="aa662-107">To import custom policy assertions</span></span>  
  
1.  <span data-ttu-id="aa662-108">Implementowanie <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="aa662-108">Implement the <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface on a class.</span></span> <span data-ttu-id="aa662-109">Zobacz poniższe procedury.</span><span class="sxs-lookup"><span data-stu-id="aa662-109">See the following procedures.</span></span>  
  
2.  <span data-ttu-id="aa662-110">Wstaw importera zasad niestandardowych albo przez:</span><span class="sxs-lookup"><span data-stu-id="aa662-110">Insert the custom policy importer either by:</span></span>  
  
3.  <span data-ttu-id="aa662-111">Przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="aa662-111">Using a configuration file.</span></span> <span data-ttu-id="aa662-112">Zobacz poniższe procedury.</span><span class="sxs-lookup"><span data-stu-id="aa662-112">See the following procedures.</span></span>  
  
4.  <span data-ttu-id="aa662-113">Korzystanie z pliku konfiguracji z [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="aa662-113">Using a configuration file with [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="aa662-114">Zobacz poniższe procedury.</span><span class="sxs-lookup"><span data-stu-id="aa662-114">See the following procedures.</span></span>  
  
5.  <span data-ttu-id="aa662-115">Programowane Wstawianie importera zasad.</span><span class="sxs-lookup"><span data-stu-id="aa662-115">Programmatically inserting the policy importer.</span></span> <span data-ttu-id="aa662-116">Zobacz poniższe procedury.</span><span class="sxs-lookup"><span data-stu-id="aa662-116">See the following procedures.</span></span>  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a><span data-ttu-id="aa662-117">Aby zaimplementować interfejs System.ServiceModel.Description.IPolicyImportExtension w dowolnej klasy</span><span class="sxs-lookup"><span data-stu-id="aa662-117">To implement the System.ServiceModel.Description.IPolicyImportExtension interface on any class</span></span>  
  
1.  <span data-ttu-id="aa662-118">W <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> metody, dla każdego tematu zasad, które planuje się, Znajdź potwierdzeń zasad, które chcesz zaimportować, wywołując metodę odpowiednie (w zależności od zakresu potwierdzenia, które mają) na <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> obiekt przekazywany do Metoda.</span><span class="sxs-lookup"><span data-stu-id="aa662-118">In the <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> method, for each policy subject that you are interested in, find the policy assertions that you want to import by calling the appropriate method (depending upon the scope of the assertion that you want) on the <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> object passed to the method.</span></span> <span data-ttu-id="aa662-119">Poniższy przykładowy kod przedstawia sposób użycia <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> metodę, aby zlokalizować potwierdzenia zasad niestandardowych i usunąć go z kolekcji w jednym kroku.</span><span class="sxs-lookup"><span data-stu-id="aa662-119">The following code example shows how to use the <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> method to locate the custom policy assertion and remove it from the collection in one step.</span></span> <span data-ttu-id="aa662-120">Metoda usuwania umożliwia lokalizowanie i usuwanie potwierdzenia, nie trzeba wykonać krok 4.</span><span class="sxs-lookup"><span data-stu-id="aa662-120">If you use the remove method to locate and remove the assertion, you do not have to perform step 4.</span></span>  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2.  <span data-ttu-id="aa662-121">Przetwarzają potwierdzeń zasad.</span><span class="sxs-lookup"><span data-stu-id="aa662-121">Process the policy assertions.</span></span> <span data-ttu-id="aa662-122">Należy pamiętać, że system zasad nie normalizacji zagnieżdżone zasad i `wsp:optional`.</span><span class="sxs-lookup"><span data-stu-id="aa662-122">Note that the policy system does not normalize nested policies and `wsp:optional`.</span></span> <span data-ttu-id="aa662-123">Te konstrukcje musi przetworzyć w implementacji rozszerzenia importu zasad.</span><span class="sxs-lookup"><span data-stu-id="aa662-123">You must process these constructs in your policy import extension implementation.</span></span>  
  
3.  <span data-ttu-id="aa662-124">Wykonaj dostosowanie binding lub kontraktu, który obsługuje możliwości lub wymagania określone przez potwierdzenia zasad.</span><span class="sxs-lookup"><span data-stu-id="aa662-124">Perform the customization to the binding or contract that supports the capability or requirement specified by the policy assertion.</span></span> <span data-ttu-id="aa662-125">Zwykle potwierdzenia wskazują, czy powiązanie wymaga określoną konfigurację lub element określonego powiązania.</span><span class="sxs-lookup"><span data-stu-id="aa662-125">Typically assertions indicate that a binding requires a particular configuration or a specific binding element.</span></span> <span data-ttu-id="aa662-126">Wprowadź poniższe zmiany, uzyskując dostęp do <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="aa662-126">Make these modifications by accessing the <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="aa662-127">Inne potwierdzenia wymagać modyfikacji kontraktu.</span><span class="sxs-lookup"><span data-stu-id="aa662-127">Other assertions require that you modify the contract.</span></span>  <span data-ttu-id="aa662-128">Masz dostęp i modyfikować za pomocą kontraktu <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="aa662-128">You can access and modify the contract using the <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="aa662-129">Pamiętaj, że Twoje importera zasad może pobrać wywołana wiele razy dla tego samego powiązania i kontraktu, ale różnych zasad alternatywnych alternatywne zasady importowania kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="aa662-129">Note that your policy importer may get called multiple times for the same binding and contract, but different policy alternatives if importing a policy alternative fails.</span></span> <span data-ttu-id="aa662-130">Kod powinien być odporny na takie zachowanie.</span><span class="sxs-lookup"><span data-stu-id="aa662-130">Your code should be resilient to this behavior.</span></span>  
  
4.  <span data-ttu-id="aa662-131">Usuń potwierdzenia zasad niestandardowych z kolekcji potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="aa662-131">Remove the custom policy assertion from the assertion collection.</span></span> <span data-ttu-id="aa662-132">Jeśli usuniesz to potwierdzenie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] założono, że importowanie zasad nie powiodło się i nie importuje powiązanie skojarzone.</span><span class="sxs-lookup"><span data-stu-id="aa662-132">If you do not remove the assertion [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] assumes that the policy import was unsuccessful and does not import the associated binding.</span></span> <span data-ttu-id="aa662-133">Jeśli używasz <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> metodę, aby zlokalizować potwierdzenia zasad niestandardowych i usunąć go z kolekcji w jednym kroku, nie trzeba wykonać ten krok.</span><span class="sxs-lookup"><span data-stu-id="aa662-133">If you used the <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> method to locate the custom policy assertion and remove it from the collection in one step you do not have to perform this step.</span></span>  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a><span data-ttu-id="aa662-134">Aby wstawić importera zasad niestandardowych do metadanych systemu przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="aa662-134">To insert the custom policy importer into the metadata System using a configuration file</span></span>  
  
1.  <span data-ttu-id="aa662-135">Dodaj typ importera `<extensions>` element wewnątrz [ \<policyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) w pliku konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="aa662-135">Add the importer type to the `<extensions>` element inside the [\<policyImporters>](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) element in the client configuration file.</span></span>  
  
     [!code-xml[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]   
  
2.  <span data-ttu-id="aa662-136">W aplikacji klienta za pomocą <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> do rozpoznania metadanych i importer jest wywoływana automatycznie.</span><span class="sxs-lookup"><span data-stu-id="aa662-136">In the client application, use the <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> to resolve the metadata and the importer is invoked automatically.</span></span>  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a><span data-ttu-id="aa662-137">Aby wstawić importera zasad niestandardowych systemu metadanych, za pomocą Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="aa662-137">To insert the custom policy importer into the metadata system using Svcutil.exe</span></span>  
  
1.  <span data-ttu-id="aa662-138">Dodaj typ importera `<extensions>` element wewnątrz [ \<policyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) elementu w pliku konfiguracyjnym Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="aa662-138">Add the importer type to the `<extensions>` element inside the [\<policyImporters>](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) element in the Svcutil.exe.config configuration file.</span></span> <span data-ttu-id="aa662-139">Możesz również Svcutil.exe punktu załadować zarejestrowanego w pliku konfiguracji różnych przy użyciu typów importera zasad `/svcutilConfig` opcji.</span><span class="sxs-lookup"><span data-stu-id="aa662-139">You can also point Svcutil.exe to load policy importer types registered in a different configuration file by using the `/svcutilConfig` option.</span></span>  
  
2.  <span data-ttu-id="aa662-140">Użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) Aby zaimportować metadane i importer jest wywoływana automatycznie.</span><span class="sxs-lookup"><span data-stu-id="aa662-140">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to import the metadata and the importer is invoked automatically.</span></span>  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a><span data-ttu-id="aa662-141">Aby wstawić importera zasad niestandardowych do systemu metadanych programowo</span><span class="sxs-lookup"><span data-stu-id="aa662-141">To insert the custom policy importer into the metadata system programmatically</span></span>  
  
1.  <span data-ttu-id="aa662-142">Dodaj importera <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=nameWithType> właściwości (na przykład, jeśli używasz <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>) przed Importowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="aa662-142">Add the importer to the <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=nameWithType> property (for example, if you are using the <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>) prior to importing the metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa662-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa662-143">See Also</span></span>  
 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>  
 [<span data-ttu-id="aa662-144">Rozszerzanie systemu metadanych</span><span class="sxs-lookup"><span data-stu-id="aa662-144">Extending the Metadata System</span></span>](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)