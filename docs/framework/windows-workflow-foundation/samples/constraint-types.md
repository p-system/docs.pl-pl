---
title: "Ograniczenia typów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd73776aebb571fad732f554d6a96c1611506e8c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="constraint-types"></a><span data-ttu-id="0d2bc-102">Ograniczenia typów</span><span class="sxs-lookup"><span data-stu-id="0d2bc-102">Constraint Types</span></span>
<span data-ttu-id="0d2bc-103">W tym przykładzie pokazano dwa różne sposoby, aby zastosować ograniczenia do przepływu pracy, jest jednym z wewnątrz działania (Kompilacja) i jeden jest z poza (zasady).</span><span class="sxs-lookup"><span data-stu-id="0d2bc-103">This sample shows two different ways to apply constraints to a workflow, one is from inside the activity (build) and one is from outside of it (policy).</span></span> <span data-ttu-id="0d2bc-104">W tym scenariuszu działania (firmy 3rth firm) chce, aby sprawdzić poprawność relacji między dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-104">In this scenario, an activity author (from a 3rth-party software company) wants to validate the relationship between two arguments.</span></span> <span data-ttu-id="0d2bc-105">W takim przypadku koszt powinna być mniejsza niż lub równa cenie.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-105">In this case, the cost should be smaller than or equal to the price.</span></span> <span data-ttu-id="0d2bc-106">Jest to ograniczenie ogólne weryfikacji kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-106">This is a general validation build constraint.</span></span>  
  
 <span data-ttu-id="0d2bc-107">Następnie chce dodać niektóre sprawdzania poprawności tego ogólnego działania właściciela sklepu.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-107">Then a shop owner wants to add some validation to this generic activity.</span></span> <span data-ttu-id="0d2bc-108">W przypadku jego Maciej chce większość jego produktów niż 9,99 $ lub mniej.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-108">In his case, he wants the majority of its products to be $9.99 or less.</span></span> <span data-ttu-id="0d2bc-109">Tak, używa ograniczenia zasad, które jest nad `CreateProduct` działania.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-109">So, he uses a policy constraint that is on top of the `CreateProduct` activity.</span></span>  
  
 <span data-ttu-id="0d2bc-110">W przykładzie:</span><span class="sxs-lookup"><span data-stu-id="0d2bc-110">In the sample:</span></span>  
  
 <span data-ttu-id="0d2bc-111">Określony przez autora działania (Kompilacja) musi:</span><span class="sxs-lookup"><span data-stu-id="0d2bc-111">The activity author (build) must:</span></span>  
  
-   <span data-ttu-id="0d2bc-112">Tworzenie ograniczenia (`PriceGreaterThanCost`).</span><span class="sxs-lookup"><span data-stu-id="0d2bc-112">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="0d2bc-113">Jest to, gdzie znajduje się całą logikę sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-113">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="0d2bc-114">Zastąpienie `System.Activities.CodeActivity.OnGetConstraints()` i Dodaj ograniczenie (`PriceGreaterThanCost`) do ograniczenia <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-114">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="0d2bc-115">Autor przepływu pracy (zasady) musi:</span><span class="sxs-lookup"><span data-stu-id="0d2bc-115">The workflow author (policy) must:</span></span>  
  
-   <span data-ttu-id="0d2bc-116">Tworzenie przepływów pracy przy użyciu wystąpienia działania do sprawdzania poprawności (`CreateProduct`).</span><span class="sxs-lookup"><span data-stu-id="0d2bc-116">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="0d2bc-117">Tworzenie ograniczenia (`MaxPrice`).</span><span class="sxs-lookup"><span data-stu-id="0d2bc-117">Create a constraint (`MaxPrice`).</span></span>  
  
-   <span data-ttu-id="0d2bc-118">Utwórz <xref:System.Activities.Validation.ValidationSettings> wystąpienia (`validationSettings`) i Dodaj ograniczenie (`MaxPrice`) do kolekcji `AdditionalConstraints`.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-118">Create a <xref:System.Activities.Validation.ValidationSettings> instance (`validationSettings`) and add the constraint (`MaxPrice`) to the collection `AdditionalConstraints`.</span></span> <span data-ttu-id="0d2bc-119">W tym miejscu autorem przepływu pracy można dodać zasad ograniczeń do żadnego działania, takie jak sekwencji lub równolegle.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-119">Here the workflow author can add policy constraints to any activity, such as a sequence or parallel.</span></span>  
  
-   <span data-ttu-id="0d2bc-120">Wywołanie <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, która zwraca <xref:System.Activities.Validation.ValidationResults> Kolekcja <xref:System.Activities.Validation.ValidationError> obiektów.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-120">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
-   <span data-ttu-id="0d2bc-121">(Opcjonalnie) Drukuj <xref:System.Activities.Validation.ValidationError> obiektów.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-121">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0d2bc-122">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="0d2bc-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0d2bc-123">Otwórz rozwiązanie próbki ConstraintTypes.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0d2bc-123">Open the ConstraintTypes.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="0d2bc-124">Tworzenie i uruchamianie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-124">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0d2bc-125">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0d2bc-126">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="0d2bc-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0d2bc-127">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0d2bc-128">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`