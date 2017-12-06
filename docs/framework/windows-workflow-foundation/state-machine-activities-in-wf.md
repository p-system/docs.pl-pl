---
title: "Działania automatu stanów w WF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ed2b5ace499af3c050529e9f0f2cdd3634c247fd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="state-machine-activities-in-wf"></a><span data-ttu-id="fd98e-102">Działania automatu stanów w WF</span><span class="sxs-lookup"><span data-stu-id="fd98e-102">State Machine Activities in WF</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<span data-ttu-id="fd98e-103">zawiera kilka działań dostarczane przez system i projektantów działań do tworzenia przepływów pracy komputera stanu.</span><span class="sxs-lookup"><span data-stu-id="fd98e-103"> provides several system-provided activities and activity designers for creating state machine workflows.</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|<span data-ttu-id="fd98e-104">Wykonuje zawarte działania przy użyciu modelu maszyny znanego stanu.</span><span class="sxs-lookup"><span data-stu-id="fd98e-104">Executes contained activities using the familiar state machine paradigm.</span></span>|  
|<xref:System.Activities.Statements.State>|<span data-ttu-id="fd98e-105">Reprezentuje stan komputera stanu.</span><span class="sxs-lookup"><span data-stu-id="fd98e-105">Represents a state in a state machine.</span></span>|  
|<xref:System.Activities.Core.Presentation.FinalState>|<span data-ttu-id="fd98e-106">Reprezentuje zakończenia stan komputera stanu.</span><span class="sxs-lookup"><span data-stu-id="fd98e-106">Represents a terminating state in a state machine.</span></span> <span data-ttu-id="fd98e-107"><xref:System.Activities.Core.Presentation.FinalState>Projektant działań jest że w przypadku używane tworzy <xref:System.Activities.Statements.State> wstępnie skonfigurowane jako stan zakończenia.</span><span class="sxs-lookup"><span data-stu-id="fd98e-107"><xref:System.Activities.Core.Presentation.FinalState> is an activity designer that when used creates a <xref:System.Activities.Statements.State> preconfigured as a terminating state.</span></span> <span data-ttu-id="fd98e-108">Aby uzyskać więcej informacji, zobacz [Projektant działań stan końcowy](/visualstudio/workflow-designer/finalstate-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="fd98e-108">For more information, see [FinalState Activity Designer](/visualstudio/workflow-designer/finalstate-activity-designer).</span></span>|  
|<xref:System.Activities.Statements.Transition>|<span data-ttu-id="fd98e-109">Reprezentuje przejście między dwoma stanami.</span><span class="sxs-lookup"><span data-stu-id="fd98e-109">Represents the transition between two states.</span></span> <span data-ttu-id="fd98e-110">Brak nie **przybornika** element do <xref:System.Activities.Statements.Transition>; przejścia na projektanta przepływów pracy są tworzone przez przeciąganie i upuszczanie linii między dwoma stanami lub poprzez upuszczenie stanu na trójkąty widocznych jednego stanu jest aktywowany przez inny .</span><span class="sxs-lookup"><span data-stu-id="fd98e-110">There is no **Toolbox** item for <xref:System.Activities.Statements.Transition>; transitions are created on the workflow designer by dragging and dropping a line between two states, or by dropping a state on the triangles that appear when one state is hovered over another.</span></span> <span data-ttu-id="fd98e-111">Aby uzyskać więcej informacji, zobacz [Projektant działań przejścia](/visualstudio/workflow-designer/transition-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="fd98e-111">For more information, see [Transition Activity Designer](/visualstudio/workflow-designer/transition-activity-designer).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd98e-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd98e-112">See Also</span></span>  
 [<span data-ttu-id="fd98e-113">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="fd98e-113">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)