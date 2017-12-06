---
title: "Niestandardowych dostawców usług danych (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9a242f6f62435440660c81d6b9838250f3d253c0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="custom-data-service-providers-wcf-data-services"></a><span data-ttu-id="603f9-102">Niestandardowych dostawców usług danych (usługi danych WCF)</span><span class="sxs-lookup"><span data-stu-id="603f9-102">Custom Data Service Providers (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="603f9-103">obejmuje zestaw dostawców, który umożliwia zdefiniowanie na podstawie typów danych z późnym wiązaniem modelu danych.</span><span class="sxs-lookup"><span data-stu-id="603f9-103"> includes a set of providers that enables you to define a data model based on late-bound data types.</span></span>  
  
|<span data-ttu-id="603f9-104">Dostawcy</span><span class="sxs-lookup"><span data-stu-id="603f9-104">Provider</span></span>|<span data-ttu-id="603f9-105">Opis</span><span class="sxs-lookup"><span data-stu-id="603f9-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="603f9-106">Dostawca metadanych</span><span class="sxs-lookup"><span data-stu-id="603f9-106">Metadata provider</span></span>|<span data-ttu-id="603f9-107">Jest to dostawca usług danych niestandardowych core umożliwia zdefiniowanie modelu danych niestandardowych w czasie wykonywania, implementując <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="603f9-107">This is the core custom data service provider that enables you to define a custom data model at runtime by implementing the <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interface.</span></span>|  
|<span data-ttu-id="603f9-108">Wyślij zapytanie do dostawcy</span><span class="sxs-lookup"><span data-stu-id="603f9-108">Query provider</span></span>|<span data-ttu-id="603f9-109">Ten dostawca umożliwia wykonywanie zapytań względem modelu danych niestandardowych, które zdefiniowano przy użyciu <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="603f9-109">This provider enables you to execute queries against a custom data model that is defined by using the <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interface.</span></span> <span data-ttu-id="603f9-110">Wyślij zapytanie do dostawcy jest tworzony przez wdrożenie <xref:System.Data.Services.Providers.IDataServiceQueryProvider> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="603f9-110">The query provider is created by implementing the <xref:System.Data.Services.Providers.IDataServiceQueryProvider> interface.</span></span>|  
|<span data-ttu-id="603f9-111">Aktualizowanie dostawcy</span><span class="sxs-lookup"><span data-stu-id="603f9-111">Update provider</span></span>|<span data-ttu-id="603f9-112">Ten dostawca pozwala na aktualizowanie typów, które są dostępne w dostawcy usług dane niestandardowe i zarządzać współbieżności.</span><span class="sxs-lookup"><span data-stu-id="603f9-112">This provider enables you to make updates to types that are exposed in a custom data service provider and to manage concurrency.</span></span> <span data-ttu-id="603f9-113">Zaimplementowanie tworzony jest dostawca aktualizacji <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> — interfejs</span><span class="sxs-lookup"><span data-stu-id="603f9-113">An update provider is created by implementing the <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> interface</span></span>|  
|<span data-ttu-id="603f9-114">Dostawca stronicowania</span><span class="sxs-lookup"><span data-stu-id="603f9-114">Paging provider</span></span>|<span data-ttu-id="603f9-115">Ten dostawca jest używany z dostawcą usług danych niestandardowych można włączyć obsługę stronicowania obsługiwanego przez serwer.</span><span class="sxs-lookup"><span data-stu-id="603f9-115">This provider is used with the custom data service provider to enable server-driven paging support.</span></span> <span data-ttu-id="603f9-116">Zaimplementowanie tworzony jest dostawca stronicowania dla usługi danych niestandardowych <xref:System.Data.Services.Providers.IDataServicePagingProvider> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="603f9-116">A paging provider for a custom data service is created by implementing the <xref:System.Data.Services.Providers.IDataServicePagingProvider> interface.</span></span>|  
|<span data-ttu-id="603f9-117">Dostawca przesyłania strumieniowego</span><span class="sxs-lookup"><span data-stu-id="603f9-117">Streaming provider</span></span>|<span data-ttu-id="603f9-118">Ten dostawca umożliwia ujawnia typy danych dużego obiektu binarnego jako strumień.</span><span class="sxs-lookup"><span data-stu-id="603f9-118">This provider enables you to expose binary large object data types as a stream.</span></span> <span data-ttu-id="603f9-119">Zaimplementowanie tworzony jest dostawca przesyłania strumieniowego <xref:System.Data.Services.Providers.IDataServiceStreamProvider> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="603f9-119">A streaming provider is created by implementing the <xref:System.Data.Services.Providers.IDataServiceStreamProvider> interface.</span></span> <span data-ttu-id="603f9-120">Dostawca przesyłania strumieniowego można również z programu Entity Framework i odbicie dostawcy źródła danych.</span><span class="sxs-lookup"><span data-stu-id="603f9-120">The streaming provider can also be used with Entity Framework and reflection data source providers.</span></span> <span data-ttu-id="603f9-121">Aby uzyskać więcej informacji, zobacz [przesyłania strumieniowego dostawcy](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="603f9-121">For more information, see [Streaming Provider](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).</span></span>|  
  
 <span data-ttu-id="603f9-122">Aby uzyskać więcej informacji, zobacz artykuł [dostawców usług danych niestandardowych](http://go.microsoft.com/fwlink/?LinkID=186850) i [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Toolkit dostawcy w [OData SDK](http://go.microsoft.com/fwlink/?LinkId=186069).</span><span class="sxs-lookup"><span data-stu-id="603f9-122">For more information, see the article [Custom Data Service Providers](http://go.microsoft.com/fwlink/?LinkID=186850) and the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Provider Toolkit in the [OData SDK](http://go.microsoft.com/fwlink/?LinkId=186069).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="603f9-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="603f9-123">See Also</span></span>  
 [<span data-ttu-id="603f9-124">Dostawców usług danych</span><span class="sxs-lookup"><span data-stu-id="603f9-124">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [<span data-ttu-id="603f9-125">Dostawcy programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="603f9-125">Entity Framework Provider</span></span>](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
 [<span data-ttu-id="603f9-126">Dostawca odbicia</span><span class="sxs-lookup"><span data-stu-id="603f9-126">Reflection Provider</span></span>](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)