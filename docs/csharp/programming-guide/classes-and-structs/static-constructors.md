---
title: "Konstruktory statyczne (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ee5448095cf06c2473c94bae542c02557918271a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="bde60-102">Konstruktory statyczne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="bde60-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="bde60-103">Statyczny Konstruktor używany do inicjowania żadnego [statycznych](../../../csharp/language-reference/keywords/static.md) danych, lub wykonania określonej akcji, która musi zostać wykonana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="bde60-103">A static constructor is used to initialize any [static](../../../csharp/language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="bde60-104">Jest ona wywoływana automatycznie przed utworzeniu pierwszego wystąpienia lub odwołuje się żadnych statycznych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="bde60-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 <span data-ttu-id="bde60-105">Konstruktory statyczne mieć następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="bde60-105">Static constructors have the following properties:</span></span>  
  
-   <span data-ttu-id="bde60-106">Konstruktor statyczny zająć modyfikatory dostępu lub nie ma parametrów.</span><span class="sxs-lookup"><span data-stu-id="bde60-106">A static constructor does not take access modifiers or have parameters.</span></span>  
  
-   <span data-ttu-id="bde60-107">Konstruktor statyczny jest wywoływana automatycznie zainicjować [klasy](../../../csharp/language-reference/keywords/class.md) przed utworzeniu pierwszego wystąpienia lub odwołuje się żadnych statycznych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="bde60-107">A static constructor is called automatically to initialize the [class](../../../csharp/language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span>  
  
-   <span data-ttu-id="bde60-108">Konstruktor statyczny nie może wywołać bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="bde60-108">A static constructor cannot be called directly.</span></span>  
  
-   <span data-ttu-id="bde60-109">Użytkownik nie ma kontroli na kiedy Konstruktor statyczny jest wykonywane w programie.</span><span class="sxs-lookup"><span data-stu-id="bde60-109">The user has no control on when the static constructor is executed in the program.</span></span>  
  
-   <span data-ttu-id="bde60-110">Typowym zastosowaniem konstruktorów statycznych jest po klasie jest używany plik dziennika i Konstruktor jest używany do zapisywania wpisów do tego pliku.</span><span class="sxs-lookup"><span data-stu-id="bde60-110">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
  
-   <span data-ttu-id="bde60-111">Konstruktory statyczne są także przydatne podczas tworzenia klasy otoki dla niezarządzanego kodu, gdy można wywołać konstruktora `LoadLibrary` metody.</span><span class="sxs-lookup"><span data-stu-id="bde60-111">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  
  
-   <span data-ttu-id="bde60-112">Jeśli w konstruktorze statycznym zgłasza wyjątek, środowisko uruchomieniowe nie wywoła go po raz drugi, a typ pozostanie niezainicjowanej przez czas ich istnienia domeny aplikacji, w którym jest uruchomiony program.</span><span class="sxs-lookup"><span data-stu-id="bde60-112">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bde60-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="bde60-113">Example</span></span>  
 <span data-ttu-id="bde60-114">W tym przykładzie klasa `Bus` ma Konstruktor statyczny.</span><span class="sxs-lookup"><span data-stu-id="bde60-114">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="bde60-115">Po pierwsze wystąpienie `Bus` utworzeniu (`bus1`), Konstruktor statyczny jest wywoływane w celu zainicjowania klasy.</span><span class="sxs-lookup"><span data-stu-id="bde60-115">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="bde60-116">Przykładowe dane wyjściowe sprawdza, czy Konstruktor statyczny uruchamiane tylko jeden raz, nawet jeśli dwa wystąpienia `Bus` są tworzone i że będzie ono przeprowadzane przed uruchomieniem konstruktora wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="bde60-116">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bde60-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bde60-117">See Also</span></span>  
 [<span data-ttu-id="bde60-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bde60-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bde60-119">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="bde60-119">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="bde60-120">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="bde60-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="bde60-121">Klasy statyczne i statyczni członkowie klas</span><span class="sxs-lookup"><span data-stu-id="bde60-121">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [<span data-ttu-id="bde60-122">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="bde60-122">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)