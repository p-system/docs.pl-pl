---
title: "Typ elementu członkowskiego &#39; &lt;membername&gt;&#39; nie jest zgodne ze specyfikacją CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords: BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c09a71675275758220691ad09eeab48e53309f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="type-of-member-39ltmembernamegt39-is-not-cls-compliant"></a><span data-ttu-id="1f0bd-102">Typ elementu członkowskiego &#39; &lt;membername&gt;&#39; nie jest zgodne ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="1f0bd-102">Type of member &#39;&lt;membername&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="1f0bd-103">Typ danych określony dla tego elementu członkowskiego nie jest częścią [niezależność od języka i elementy niezależne od języka](https://msdn.microsoft.com/library/12a7a7h3) (ze specyfikacją CLS).</span><span class="sxs-lookup"><span data-stu-id="1f0bd-103">The data type specified for this member is not part of the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span></span> <span data-ttu-id="1f0bd-104">Nie jest to błąd w ramach składnika, ponieważ [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] i [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] obsługuje tego typu danych.</span><span class="sxs-lookup"><span data-stu-id="1f0bd-104">This is not an error within your component, because the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] support this data type.</span></span> <span data-ttu-id="1f0bd-105">Jednak inny składnik napisana ściśle kodu zgodne ze specyfikacją CLS nie może obsługiwać ten typ danych.</span><span class="sxs-lookup"><span data-stu-id="1f0bd-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="1f0bd-106">Takie składnika nie można pomyślnie interakcyjnie składnika.</span><span class="sxs-lookup"><span data-stu-id="1f0bd-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="1f0bd-107">Następujące [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] typy danych nie są zgodne ze specyfikacją CLS:</span><span class="sxs-lookup"><span data-stu-id="1f0bd-107">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="1f0bd-108">SByte — typ danych</span><span class="sxs-lookup"><span data-stu-id="1f0bd-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="1f0bd-109">Uinteger — typ danych</span><span class="sxs-lookup"><span data-stu-id="1f0bd-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="1f0bd-110">Ulong — typ danych</span><span class="sxs-lookup"><span data-stu-id="1f0bd-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="1f0bd-111">Ushort — typ danych</span><span class="sxs-lookup"><span data-stu-id="1f0bd-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="1f0bd-112">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="1f0bd-112">By default, this message is a warning.</span></span> <span data-ttu-id="1f0bd-113">Aby uzyskać więcej informacji na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="1f0bd-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="1f0bd-114">**Identyfikator błędu:** BC40025</span><span class="sxs-lookup"><span data-stu-id="1f0bd-114">**Error ID:** BC40025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1f0bd-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="1f0bd-115">To correct this error</span></span>  
  
-   <span data-ttu-id="1f0bd-116">Jeśli składnik interfejsy tylko z innymi [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] składniki lub nie nie interfejsu z innymi składnikami, jest konieczne wprowadzanie zmian.</span><span class="sxs-lookup"><span data-stu-id="1f0bd-116">If your component interfaces only with other [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="1f0bd-117">Jeśli są relacje ze składnikiem nie napisane dla [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], może być możliwe ustalenie, albo za pomocą odbicia lub z dokumentacji, czy ten typ danych.</span><span class="sxs-lookup"><span data-stu-id="1f0bd-117">If you are interfacing with a component not written for the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="1f0bd-118">Jeśli tak, nie jest konieczne wprowadzanie zmian.</span><span class="sxs-lookup"><span data-stu-id="1f0bd-118">If it does, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="1f0bd-119">Jeśli użytkownik są relacje ze składnikiem, który nie obsługuje tego typu danych, należy ją zastąpić najbliższego CLS typu.</span><span class="sxs-lookup"><span data-stu-id="1f0bd-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="1f0bd-120">Na przykład zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości powyżej 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="1f0bd-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="1f0bd-121">Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.</span><span class="sxs-lookup"><span data-stu-id="1f0bd-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="1f0bd-122">Jeśli użytkownik są relacje z obiektami automatyzacji lub COM, należy pamiętać, że niektóre typy szerokości danych innego niż w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1f0bd-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="1f0bd-123">Na przykład `uint` jest często 16 bitów w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="1f0bd-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="1f0bd-124">Jeśli argument 16-bitowych jest przekazywany do takich składników, Zadeklaruj ją jako `UShort` zamiast `UInteger` w sieci zarządzanej [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kodu.</span><span class="sxs-lookup"><span data-stu-id="1f0bd-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f0bd-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f0bd-125">See Also</span></span>  
 [<span data-ttu-id="1f0bd-126">Odbicie</span><span class="sxs-lookup"><span data-stu-id="1f0bd-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
 [<span data-ttu-id="1f0bd-127">\<PAVE za pośrednictwem > Pisanie kodu zgodne ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="1f0bd-127">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)