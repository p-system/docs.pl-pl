---
title: '&lt;privacyNoticeAt&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63501539db4dc01d86eb675c28001dc960f1bf7f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltprivacynoticeatgt"></a><span data-ttu-id="97124-102">&lt;privacyNoticeAt&gt;</span><span class="sxs-lookup"><span data-stu-id="97124-102">&lt;privacyNoticeAt&gt;</span></span>
<span data-ttu-id="97124-103">Reprezentuje element konfiguracji, który określa powiadomienie o prywatności użyte w `wsFederationHttp` powiązania.</span><span class="sxs-lookup"><span data-stu-id="97124-103">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="97124-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="97124-104">\<system.serviceModel></span></span>  
<span data-ttu-id="97124-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="97124-105">\<bindings></span></span>  
<span data-ttu-id="97124-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="97124-106">\<customBinding></span></span>  
<span data-ttu-id="97124-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="97124-107">\<binding></span></span>  
<span data-ttu-id="97124-108">\<privacyNotice ></span><span class="sxs-lookup"><span data-stu-id="97124-108">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97124-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="97124-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"  
        version="Integer" />  
```  
  
## <a name="type"></a><span data-ttu-id="97124-110">Typ</span><span class="sxs-lookup"><span data-stu-id="97124-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97124-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="97124-111">Attributes and Elements</span></span>  
 <span data-ttu-id="97124-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="97124-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97124-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="97124-113">Attributes</span></span>  
  
|<span data-ttu-id="97124-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="97124-114">Attribute</span></span>|<span data-ttu-id="97124-115">Opis</span><span class="sxs-lookup"><span data-stu-id="97124-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="97124-116">Ciąg określający URI, w której znajduje się zasadach zachowania poufności informacji.</span><span class="sxs-lookup"><span data-stu-id="97124-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="97124-117">Liczba całkowita określająca wersję tego zawiadomienia o prywatności.</span><span class="sxs-lookup"><span data-stu-id="97124-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97124-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="97124-118">Child Elements</span></span>  
 <span data-ttu-id="97124-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="97124-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="97124-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="97124-120">Parent Elements</span></span>  
  
|<span data-ttu-id="97124-121">Element</span><span class="sxs-lookup"><span data-stu-id="97124-121">Element</span></span>|<span data-ttu-id="97124-122">Opis</span><span class="sxs-lookup"><span data-stu-id="97124-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97124-123">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="97124-123">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="97124-124">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="97124-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="97124-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97124-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="97124-126">Powiązania</span><span class="sxs-lookup"><span data-stu-id="97124-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="97124-127">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="97124-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="97124-128">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="97124-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="97124-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="97124-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)