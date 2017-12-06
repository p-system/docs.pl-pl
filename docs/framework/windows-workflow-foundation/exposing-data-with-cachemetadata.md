---
title: "Udostępnianie danych z CacheMetadata"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34832f23-e93b-40e6-a80b-606a855a00d9
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 26c68c24ad525d077d26f0b7bd917a936372e0a5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="exposing-data-with-cachemetadata"></a><span data-ttu-id="84935-102">Udostępnianie danych z CacheMetadata</span><span class="sxs-lookup"><span data-stu-id="84935-102">Exposing data with CacheMetadata</span></span>
<span data-ttu-id="84935-103">Przed wykonaniem działania, czas wykonywania przepływu pracy uzyskuje wszystkie informacje o działaniach wymaganych w celu zachowania jego wykonywania.</span><span class="sxs-lookup"><span data-stu-id="84935-103">Before executing an activity, the workflow runtime obtains all of the information about the activity that it needs in order to maintain its execution.</span></span> <span data-ttu-id="84935-104">Te informacje podczas wykonywania pobiera środowiska uruchomieniowego przepływu pracy <xref:System.Activities.Activity.CacheMetadata%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="84935-104">The workflow runtime gets this information during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="84935-105">Domyślna implementacja tej metody zawiera środowiska wykonawczego o wszystkich publicznych argumenty, zmienne i działań podrzędnych udostępnianych przez działania w czasie wykonania; Jeśli działanie wymaga więcej informacji do środowiska wykonawczego równą (na przykład prywatne elementy Członkowskie lub działań do zaplanowania przez działanie), ta metoda może zostać zastąpiona do tego celu.</span><span class="sxs-lookup"><span data-stu-id="84935-105">The default implementation of this method provides the runtime with all of the public arguments, variables, and child activities exposed by the activity at the time it is executed; if the activity needs to give more information to the runtime than this (such as private members, or activities to be scheduled by the activity), this method can be overridden to provide it.</span></span>  
  
## <a name="default-cachemetadata-behavior"></a><span data-ttu-id="84935-106">Domyślne zachowanie CacheMetadata</span><span class="sxs-lookup"><span data-stu-id="84935-106">Default CacheMetadata behavior</span></span>  
 <span data-ttu-id="84935-107">Domyślna implementacja <xref:System.Activities.NativeActivity.CacheMetadata%2A> działań, które pochodzą z <xref:System.Activities.NativeActivity> przetwarza następujących typów — metoda w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="84935-107">The default implementation of <xref:System.Activities.NativeActivity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.NativeActivity> processes the following method types in the following ways:</span></span>  
  
-   <span data-ttu-id="84935-108"><xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, lub <xref:System.Activities.InOutArgument%601> (argumentów ogólnych): argumenty są widoczne do środowiska wykonawczego jako argumenty z nazwą i wpisz nazwę ujawnionych właściwości i typ, odpowiedni kierunek i niektórych danych sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="84935-108"><xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, or <xref:System.Activities.InOutArgument%601> (generic arguments): These arguments are exposed to the runtime as arguments with a name and type equal to the exposed property name and type, the appropriate argument direction, and some validation data.</span></span>  
  
-   <span data-ttu-id="84935-109"><xref:System.Activities.Variable>lub jego żadnych podklasa klasy: elementy te są widoczne dla środowiska uruchomieniowego jako zmiennych publicznych.</span><span class="sxs-lookup"><span data-stu-id="84935-109"><xref:System.Activities.Variable> or any subclass thereof: These members are exposed to the runtime as public variables.</span></span>  
  
-   <span data-ttu-id="84935-110"><xref:System.Activities.Activity>lub jego żadnych podklasa klasy: elementy te są widoczne dla środowiska uruchomieniowego jako działania podrzędnego publicznego.</span><span class="sxs-lookup"><span data-stu-id="84935-110"><xref:System.Activities.Activity> or any subclass thereof: These members are exposed to the runtime as public child activities.</span></span> <span data-ttu-id="84935-111">Domyślne zachowanie może być jawnie implementowane przez wywołanie metody <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, przekazując działania podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="84935-111">The default behavior can be implemented explicity by calling <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, passing in the child activity.</span></span>  
  
-   <span data-ttu-id="84935-112"><xref:System.Activities.ActivityDelegate>lub jego żadnych podklasa klasy: elementy te są widoczne dla środowiska uruchomieniowego pełnomocnikiem publicznego.</span><span class="sxs-lookup"><span data-stu-id="84935-112"><xref:System.Activities.ActivityDelegate> or any subclass thereof: These members are exposed to the runtime as public delegates.</span></span>  
  
-   <span data-ttu-id="84935-113"><xref:System.Collections.ICollection>typu <xref:System.Activities.Variable>: wszystkie elementy w kolekcji są widoczne dla środowiska uruchomieniowego jako zmiennych publicznych.</span><span class="sxs-lookup"><span data-stu-id="84935-113"><xref:System.Collections.ICollection> of type <xref:System.Activities.Variable>: All elements in the collection are exposed to the runtime as public variables.</span></span>  
  
-   <span data-ttu-id="84935-114"><xref:System.Collections.ICollection>typu <xref:System.Activities.Activity>: wszystkie elementy w kolekcji są widoczne dla środowiska uruchomieniowego jako publiczne elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="84935-114"><xref:System.Collections.ICollection> of type <xref:System.Activities.Activity>: All elements in the collection are exposed to the runtime as public children.</span></span>  
  
-   <span data-ttu-id="84935-115"><xref:System.Collections.ICollection>typu <xref:System.Activities.ActivityDelegate>: wszystkie elementy w kolekcji są widoczne dla środowiska uruchomieniowego pełnomocnikiem publicznego.</span><span class="sxs-lookup"><span data-stu-id="84935-115"><xref:System.Collections.ICollection> of type <xref:System.Activities.ActivityDelegate>: All elements in the collection are exposed to the runtime as public delegates.</span></span>  
  
 <span data-ttu-id="84935-116"><xref:System.Activities.Activity.CacheMetadata%2A> Działań, które pochodzą z <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, i <xref:System.Activities.AsyncCodeActivity> również działać zgodnie z powyższym, z wyjątkiem następujących różnic:</span><span class="sxs-lookup"><span data-stu-id="84935-116">The <xref:System.Activities.Activity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, and <xref:System.Activities.AsyncCodeActivity> also function as above, except for the following differences:</span></span>  
  
-   <span data-ttu-id="84935-117">Klasy, które pochodzą z <xref:System.Activities.Activity> nie można zaplanować działania podrzędne lub delegatów, więc takich elementów są widoczne jako importowanych elementów podrzędnych i obiektów delegowanych;</span><span class="sxs-lookup"><span data-stu-id="84935-117">Classes that derive from <xref:System.Activities.Activity> cannot schedule child activities or delegates, so such members are exposed as imported children and delegates; the</span></span>  
  
-   <span data-ttu-id="84935-118">Klasy, które pochodzą z <xref:System.Activities.CodeActivity> i <xref:System.Activities.AsyncCodeActivity> nie obsługują zmiennych, elementów podrzędnych lub delegatów, więc tylko argumenty, które mają być widoczne.</span><span class="sxs-lookup"><span data-stu-id="84935-118">Classes that derive from <xref:System.Activities.CodeActivity> and <xref:System.Activities.AsyncCodeActivity> do not support variables, children, or delegates, so only arguments will be exposed.</span></span>  
  
## <a name="overriding-cachemetadata-to-provide-information-to-the-runtime"></a><span data-ttu-id="84935-119">Zastępowanie CacheMetadata, aby podać informacje do środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="84935-119">Overriding CacheMetadata to provide information to the runtime</span></span>  
 <span data-ttu-id="84935-120">Poniższy fragment kodu przedstawia sposób dodawania informacji o elementach członkowskich metadanych działania podczas wykonywania <xref:System.Activities.Activity.CacheMetadata%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="84935-120">The following code snippet demonstrates how to add information about members to an activity’s metadata during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="84935-121">Należy pamiętać, że podstawowej metody jest wywoływana w pamięci podręcznej wszystkie publiczne dane dotyczące działania.</span><span class="sxs-lookup"><span data-stu-id="84935-121">Note that the base of the method is called to cache all public data about the activity.</span></span>  
  
```  
protected override void CacheMetadata(NativeActivityMetadata metadata)  
{      
    base.CacheMetadata(metadata);  
    metadata.AddImplementationChild(this._writeLine);  
    metadata.AddVariable(this._myVariable);  
    metadata.AddImplementationVariable(this._myImplementationVariable);  
  
    RuntimeArgument argument = new RuntimeArgument("MyArgument", ArgumentDirection.In, typeof(SomeType));  
    metadata.Bind(argument, this.SomeName);  
    metadata.AddArgument(argument);  
}  
```  
  
## <a name="using-cachemetadata-to-expose-implementation-children"></a><span data-ttu-id="84935-122">Przy użyciu CacheMetadata do udostępnienia implementacji elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="84935-122">Using CacheMetadata to expose implementation children</span></span>  
 <span data-ttu-id="84935-123">Aby przekazać dane do działania podrzędne, które mają być zaplanowane przez działanie za pomocą zmiennych, należy dodać zmienne jako zmienne implementacji; zmienne publiczne nie może mieć wartości skonfigurowane w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="84935-123">In order to pass data to child activities that are to be scheduled by an activity using variables, it is necessary to add the variables as implementation variables; public variables cannot have their values set this way.</span></span> <span data-ttu-id="84935-124">Przyczyną tego jest działania mają więcej wykonywanej jako implementacji funkcji (które mają parametry), a nie klasy hermetyzowany, (które mają właściwości).</span><span class="sxs-lookup"><span data-stu-id="84935-124">The reason for this is that activities are intended to be executed more as implementations of functions (which have parameters), rather than encapsulated classes (which have properties).</span></span> <span data-ttu-id="84935-125">Jednak istnieją sytuacje, w których argumentów musi być jawnie ustawiona, takich jak podczas obliczania przy użyciu <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, ponieważ zaplanowanego działania nie ma dostępu do argumentów działania nadrzędnego w taki sposób, czy działania podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="84935-125">However, there are situations in which the arguments must be explicitly set, such as when using <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, since the scheduled activity doesn't have access to the parent activity's arguments in the way a child activity would.</span></span>  
  
 <span data-ttu-id="84935-126">Poniższy fragment kodu przedstawia sposób przekazania formularza argumentu działania natywnego do zaplanowanego działania przy użyciu <xref:System.Activities.Activity.CacheMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="84935-126">The following code snippet demonstrates how to pass an argument form a native activity into a scheduled activity using <xref:System.Activities.Activity.CacheMetadata%2A>.</span></span>  
  
```  
public sealed class ChildActivity : NativeActivity  
{  
    public WriteLine _writeLine;  
    public InArgument<string> Message { get; set; }  
    private Variable<string> MessageVariable { get; set; }  
    public ChildActivity()  
    {  
        MessageVariable = new Variable<string>();  
        _writeLine = new WriteLine  
        {  
            Text = new InArgument<string>(MessageVariable),  
        };  
    }  
    protected override void CacheMetadata(NativeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        metadata.AddImplementationVariable(this.MessageVariable);  
        metadata.AddImplementationChild(this._writeLine);  
    }  
    protected override void Execute(NativeActivityContext context)  
    {  
        string configuredMessage = context.GetValue(Message);  
        context.SetValue(MessageVariable, configuredMessage);  
        context.ScheduleActivity(this._writeLine);  
    }  
}  
```