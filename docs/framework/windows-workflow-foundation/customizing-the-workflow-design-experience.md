---
title: "Dostosowywanie projektu przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 60e8d01ad32e10f06191f7e0b38dcb648780ba29
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="229ad-102">Dostosowywanie projektu przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="229ad-102">Customizing the Workflow Design Experience</span></span>
<span data-ttu-id="229ad-103">Scenariusze dotyczące projektowania niestandardowych działań i rehosting [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] znacznie zostały uproszczone w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="229ad-103">The scenarios for designing custom activities and for rehosting the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] have been greatly simplified in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span> <span data-ttu-id="229ad-104">Opracowywania i wdrażania są teraz zarówno łatwiejsze i bardziej elastyczne.</span><span class="sxs-lookup"><span data-stu-id="229ad-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="229ad-105">Zmiany infrastrukturalne klucza jest, że nowy model programowania projektanta działania jest oparty na [!INCLUDE[avalon1](../../../includes/avalon1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="229ad-105">The key infrastructural change is that the new activity designer programming model is built upon [!INCLUDE[avalon1](../../../includes/avalon1-md.md)].</span></span> <span data-ttu-id="229ad-106">Daje to możliwość deklaratywnego definiowania projektantów działań oraz rehost [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] w innych aplikacjach z porównawczych łatwe.</span><span class="sxs-lookup"><span data-stu-id="229ad-106">This gives you the ability to define activity designers declaratively and to rehost the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in other applications with comparative easy.</span></span> <span data-ttu-id="229ad-107">Gdy rehosting, Edytor wyrażenia niestandardowego mogą być opracowane obsługę funkcji IntelliSense lub domeny uproszczony wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="229ad-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="229ad-108">Integracja z [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] stał się aby usprawnić przy użyciu usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="229ad-108">The integration with [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] has become more seamless with use of workflow services.</span></span> <span data-ttu-id="229ad-109">W celu zwiększenia projektowy czasu wykonywania w projektantach rehosted przepływu pracy można projektantów działań niestandardowych i drzewa elementu modelu.</span><span class="sxs-lookup"><span data-stu-id="229ad-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="229ad-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="229ad-110">In This Section</span></span>  
 [<span data-ttu-id="229ad-111">Przy użyciu projektantów działań niestandardowych i szablonów</span><span class="sxs-lookup"><span data-stu-id="229ad-111">Using Custom Activity Designers and Templates</span></span>](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md)  
 <span data-ttu-id="229ad-112">Opisuje sposób tworzenia nowego niestandardowego działania projektantów i szablonów.</span><span class="sxs-lookup"><span data-stu-id="229ad-112">Describes how to create new custom activity designers and templates.</span></span>  
  
 [<span data-ttu-id="229ad-113">Rehosting projektanta przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="229ad-113">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 <span data-ttu-id="229ad-114">Opisuje sposób ponownego hostowania [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] poza [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] oraz jak wyświetlać błędy sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="229ad-114">Describes how to re-host the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] outside of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] and how to display validation errors.</span></span>  
  
 [<span data-ttu-id="229ad-115">Za pomocą edytora wyrażeń niestandardowych</span><span class="sxs-lookup"><span data-stu-id="229ad-115">Using a Custom Expression Editor</span></span>](../../../docs/framework/windows-workflow-foundation/using-a-custom-expression-editor.md)  
 <span data-ttu-id="229ad-116">Opisuje sposób implementacji edytorze wyrażenia niestandardowego do użycia z przepływu pracy projektantów rehosted poza [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="229ad-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="229ad-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="229ad-117">Reference</span></span>  
 <xref:System.Activities.Presentation.ActivityDesigner>  
  
## <a name="see-also"></a><span data-ttu-id="229ad-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="229ad-118">See Also</span></span>  
 [<span data-ttu-id="229ad-119">Rozszerzanie programu Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="229ad-119">Extending Windows Workflow Foundation</span></span>](../../../docs/framework/windows-workflow-foundation/extend.md)  
 [<span data-ttu-id="229ad-120">Projektant</span><span class="sxs-lookup"><span data-stu-id="229ad-120">Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/designer.md)  
 [<span data-ttu-id="229ad-121">Projektanci działań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="229ad-121">Custom Activity Designers</span></span>](../../../docs/framework/windows-workflow-foundation/samples/custom-activity-designers.md)  
 [<span data-ttu-id="229ad-122">Projektant ReHosting</span><span class="sxs-lookup"><span data-stu-id="229ad-122">Designer ReHosting</span></span>](../../../docs/framework/windows-workflow-foundation/samples/designer-rehosting.md)