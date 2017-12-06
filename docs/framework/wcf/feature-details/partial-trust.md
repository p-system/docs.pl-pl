---
title: "Zaufanie częściowe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 489b1587-9909-4d0e-8c1a-5e83c8f8292b
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 893b8bb58c9d78d6880f95f2490c55c7d9e27483
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="partial-trust"></a><span data-ttu-id="5e053-102">Zaufanie częściowe</span><span class="sxs-lookup"><span data-stu-id="5e053-102">Partial Trust</span></span>
<span data-ttu-id="5e053-103">Począwszy od [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)], częściowo zaufanych wywołań może uzyskiwać dostęp do publicznego typy i metody implementowane w <xref:System.ServiceModel>, <xref:System.Runtime.Serialization>, i <xref:System.ServiceModel.Web>.</span><span class="sxs-lookup"><span data-stu-id="5e053-103">Starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)], partially trusted callers can access public types and methods implemented in <xref:System.ServiceModel>, <xref:System.Runtime.Serialization>, and <xref:System.ServiceModel.Web>.</span></span> <span data-ttu-id="5e053-104">W tej sekcji opisano obsługiwane scenariusze korzystania z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] w częściowo zaufanych aplikacji, a także ograniczonym podzbiorem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkcje dostępne dla aplikacji z ograniczone uprawnienia (CAS) zabezpieczeń dostępu kodu.</span><span class="sxs-lookup"><span data-stu-id="5e053-104">This section describes supported scenarios for using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] within a partially trusted application as well as the limited subset of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] functionality available to applications running with reduced code access security (CAS) permissions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5e053-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="5e053-105">In This Section</span></span>  
 [<span data-ttu-id="5e053-106">Obsługiwane scenariusze wdrażania</span><span class="sxs-lookup"><span data-stu-id="5e053-106">Supported Deployment Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)  
 <span data-ttu-id="5e053-107">Opisuje scenariusze głównego częściowej relacji zaufania działa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5e053-107">Describes the main partial trust scenarios for running [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="5e053-108">Zgodność funkcji zaufania częściowego</span><span class="sxs-lookup"><span data-stu-id="5e053-108">Partial Trust Feature Compatibility</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md)  
 <span data-ttu-id="5e053-109">W tym artykule opisano [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkcje, których nie można używać z częściowa relacja zaufania.</span><span class="sxs-lookup"><span data-stu-id="5e053-109">Describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] features that cannot be used with partial trust.</span></span>  
  
 [<span data-ttu-id="5e053-110">Najlepsze rozwiązania w częściowej relacji zaufania</span><span class="sxs-lookup"><span data-stu-id="5e053-110">Partial Trust Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)  
 <span data-ttu-id="5e053-111">Zawiera najlepsze rozwiązania dotyczące używania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] w częściowo zaufane aplikacje.</span><span class="sxs-lookup"><span data-stu-id="5e053-111">Contains best practices for using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in partially trusted applications.</span></span>