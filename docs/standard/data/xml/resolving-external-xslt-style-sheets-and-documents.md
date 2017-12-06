---
title: "Rozpoznawanie arkuszy stylów XSLT zewnętrznych i dokumentów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a5e84935f9fff1f993a677d408287cd775269f03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a><span data-ttu-id="3da85-102">Rozpoznawanie arkuszy stylów XSLT zewnętrznych i dokumentów</span><span class="sxs-lookup"><span data-stu-id="3da85-102">Resolving External XSLT Style Sheets and Documents</span></span>
<span data-ttu-id="3da85-103">Istnieje kilka razy podczas transformację, gdy trzeba rozwiązać zasobów zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="3da85-103">There are several times during a transformation when you may need to resolve external resources.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3da85-104"><xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3da85-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="3da85-105">Może wykonywać rozszerzalny język arkusza stylów dla transformacji przekształcenia XSLT () przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="3da85-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 <span data-ttu-id="3da85-106">Istnieje kilka razy podczas transformację, gdy trzeba rozwiązać zasobów zewnętrznych:</span><span class="sxs-lookup"><span data-stu-id="3da85-106">There are several times during a transformation when you may need to resolve external resources:</span></span>  
  
-   <span data-ttu-id="3da85-107">Podczas <xref:System.Xml.Xsl.XslTransform.Load%2A> można znaleźć zewnętrznego arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="3da85-107">During the <xref:System.Xml.Xsl.XslTransform.Load%2A> to locate an external style sheet.</span></span>  
  
-   <span data-ttu-id="3da85-108">Podczas <xref:System.Xml.Xsl.XslTransform.Load%2A> do rozwiązania `<xsl:include>` lub `<xsl:import>` elementy znalezione w arkuszu stylów.</span><span class="sxs-lookup"><span data-stu-id="3da85-108">During <xref:System.Xml.Xsl.XslTransform.Load%2A> to resolve any `<xsl:include>` or `<xsl:import>` elements found in the style sheet.</span></span>  
  
-   <span data-ttu-id="3da85-109">Podczas <xref:System.Xml.Xsl.XslTransform.Transform%2A> do rozwiązania `document()` funkcji.</span><span class="sxs-lookup"><span data-stu-id="3da85-109">During <xref:System.Xml.Xsl.XslTransform.Transform%2A> to resolve any `document()` functions.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="3da85-110">Używanie klasy element XmlResolver</span><span class="sxs-lookup"><span data-stu-id="3da85-110">Using the XmlResolver Class</span></span>  
 <span data-ttu-id="3da85-111">Jeśli wymagane jest uwierzytelnienie dostępu do zasobu sieciowego, użyj <xref:System.Xml.Xsl.XslTransform.Load%2A> metod, które mają <xref:System.Xml.XmlResolver> parametr do przekazania <xref:System.Xml.XmlResolver> obiektu, który ma wartość właściwości niezbędne poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="3da85-111">If authentication is required to access a network resource, use the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that have an <xref:System.Xml.XmlResolver> parameter to pass the <xref:System.Xml.XmlResolver> object, which has the necessary credential properties set.</span></span>  
  
 <span data-ttu-id="3da85-112">Jeśli masz niestandardowego <xref:System.Xml.XmlResolver> czy ma być używany, lub jeśli chcesz określić inne poświadczenia w poniższej tabeli przedstawiono zadania wymagane w zależności od tego, gdy zasób zewnętrzny potrzebuje rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="3da85-112">If you have a custom <xref:System.Xml.XmlResolver> that you want to use, or if you need to specify different credentials, the following table lists the task required, depending on when the external resource needs resolution.</span></span>  
  
|<span data-ttu-id="3da85-113">Jakie procesy wymaga rozpoznawania</span><span class="sxs-lookup"><span data-stu-id="3da85-113">What process requires resolution</span></span>|<span data-ttu-id="3da85-114">Wymagane zadania</span><span class="sxs-lookup"><span data-stu-id="3da85-114">Task required</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="3da85-115">Podczas <xref:System.Xml.Xsl.XslTransform.Load%2A> zlokalizować arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="3da85-115">During <xref:System.Xml.Xsl.XslTransform.Load%2A> to locate the style sheet.</span></span>|<span data-ttu-id="3da85-116">Określ przeciążone <xref:System.Xml.Xsl.XslTransform.Load%2A> metodę, która przyjmuje jako parametr, <xref:System.Xml.XmlResolver> Jeśli arkusz stylów znajduje się na zasobie, który wymaga poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="3da85-116">Specify the overloaded <xref:System.Xml.Xsl.XslTransform.Load%2A> method that takes, as a parameter, an <xref:System.Xml.XmlResolver> if the style sheet is on a resource that requires credentials.</span></span>|  
|<span data-ttu-id="3da85-117">Podczas <xref:System.Xml.Xsl.XslTransform.Load%2A> rozwiązywać `<xsl:include>` lub `<xsl:import>`.</span><span class="sxs-lookup"><span data-stu-id="3da85-117">During <xref:System.Xml.Xsl.XslTransform.Load%2A> to resolve `<xsl:include>` or `<xsl:import>`.</span></span>|<span data-ttu-id="3da85-118">Określ przeciążone <xref:System.Xml.Xsl.XslTransform.Load%2A> metodę, która przyjmuje jako parametr, <xref:System.Xml.XmlResolver>.</span><span class="sxs-lookup"><span data-stu-id="3da85-118">Specify the overloaded <xref:System.Xml.Xsl.XslTransform.Load%2A> method that takes, as a parameter, an <xref:System.Xml.XmlResolver>.</span></span> <span data-ttu-id="3da85-119"><xref:System.Xml.XmlResolver> Jest używana do załadowania arkusze stylów odwołuje się `import` lub `include` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="3da85-119">The <xref:System.Xml.XmlResolver> is used to load the style sheets referenced by the `import` or `include` statements.</span></span> <span data-ttu-id="3da85-120">W przypadku przekazania w `null`, zasobów zewnętrznych nie są rozpoznawane.</span><span class="sxs-lookup"><span data-stu-id="3da85-120">If you pass in `null`, the external resources are not resolved.</span></span>|  
|<span data-ttu-id="3da85-121">Podczas transformacji do rozwiązania `document()` funkcji.</span><span class="sxs-lookup"><span data-stu-id="3da85-121">During a transformation to resolve any `document()` functions.</span></span>|<span data-ttu-id="3da85-122">Określ <xref:System.Xml.XmlResolver> podczas transformacji przy użyciu <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody pobierającej <xref:System.Xml.XmlResolver> argumentu.</span><span class="sxs-lookup"><span data-stu-id="3da85-122">Specify the <xref:System.Xml.XmlResolver> during the transformation by using the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method that takes an <xref:System.Xml.XmlResolver> argument.</span></span>|  
  
 <span data-ttu-id="3da85-123">`document()` Funkcja pobiera inne zasoby XML z arkusza stylów, oprócz początkowej danych XML udostępniane przez strumień wejściowy.</span><span class="sxs-lookup"><span data-stu-id="3da85-123">The `document()` function retrieves other XML resources from a style sheet, in addition to the initial XML data provided by the input stream.</span></span> <span data-ttu-id="3da85-124">Ponieważ ta funkcja umożliwia dołączenie danych XML, które mogą być zlokalizowany w innym miejscu, <xref:System.Xml.XmlResolver> z `null` wartość dostarczona do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda `document()` funkcję wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3da85-124">Since this function allows the inclusion of XML data that can be located elsewhere, an <xref:System.Xml.XmlResolver> with a `null` value supplied to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method prevents the `document()` function from executing.</span></span> <span data-ttu-id="3da85-125">Jeśli chcesz użyć `document()` funkcji, należy użyć <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody pobierającej <xref:System.Xml.XmlResolver> jako parametru, oprócz odpowiednich uprawnień ustawić.</span><span class="sxs-lookup"><span data-stu-id="3da85-125">If you want to use the `document()` function, use the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method that takes an <xref:System.Xml.XmlResolver> as a parameter, in addition to having the appropriate permission set.</span></span>  
  
 <span data-ttu-id="3da85-126">Aby uzyskać więcej informacji na temat <xref:System.Xml.Xsl.XslTransform.Load%2A> — metoda i jego użycie <xref:System.Xml.XmlResolver>, zobacz <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3da85-126">For more information on the <xref:System.Xml.Xsl.XslTransform.Load%2A> method and its use of the <xref:System.Xml.XmlResolver>, see <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="3da85-127">Gdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda jest wywoływana, uprawnienia są obliczane względem dowodów w czasie ładowania i przypisane do procesu transformacji cały zestaw uprawnień.</span><span class="sxs-lookup"><span data-stu-id="3da85-127">When the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is called, permissions are calculated against the evidence provided at load time, and that permission set is assigned to the entire transformation process.</span></span> <span data-ttu-id="3da85-128">Jeśli `document()` funkcja próbuje zainicjować akcję, która wymaga uprawnienia nie można odnaleźć w zestawie, jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3da85-128">If the `document()` function attempts to initiate an action that requires permissions not found in the set, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3da85-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3da85-129">See Also</span></span>  
 [<span data-ttu-id="3da85-130">Przekształcenia XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="3da85-130">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="3da85-131">Klasa XslTransform implementuje procesorze XSLT</span><span class="sxs-lookup"><span data-stu-id="3da85-131">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [<span data-ttu-id="3da85-132">Dane wyjściowe z XslTransform</span><span class="sxs-lookup"><span data-stu-id="3da85-132">Outputs from an XslTransform</span></span>](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md)  
 [<span data-ttu-id="3da85-133">Przekształcenia XSLT w sklepach</span><span class="sxs-lookup"><span data-stu-id="3da85-133">XSLT Transformations Over Different Stores</span></span>](../../../../docs/standard/data/xml/xslt-transformations-over-different-stores.md)  
 [<span data-ttu-id="3da85-134">XsltArgumentList parametry arkusza stylów i rozszerzenia obiektów</span><span class="sxs-lookup"><span data-stu-id="3da85-134">XsltArgumentList for Style Sheet Parameters and Extension Objects</span></span>](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)  
 [<span data-ttu-id="3da85-135">XSLT skryptów przy użyciu arkusza stylów \<msxsl:script ></span><span class="sxs-lookup"><span data-stu-id="3da85-135">XSLT Stylesheet Scripting Using \<msxsl:script></span></span>](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)  
 [<span data-ttu-id="3da85-136">Obsługa msxsl:node-set() — funkcja</span><span class="sxs-lookup"><span data-stu-id="3da85-136">Support for the msxsl:node-set() Function</span></span>](../../../../docs/standard/data/xml/support-for-the-msxsl-node-set-function.md)  
 [<span data-ttu-id="3da85-137">Element XPathNavigator w przekształcenia</span><span class="sxs-lookup"><span data-stu-id="3da85-137">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [<span data-ttu-id="3da85-138">Element XPathNodeIterator w przekształcenia</span><span class="sxs-lookup"><span data-stu-id="3da85-138">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [<span data-ttu-id="3da85-139">Dane wejściowe XPathDocument XslTransform</span><span class="sxs-lookup"><span data-stu-id="3da85-139">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [<span data-ttu-id="3da85-140">Dane wejściowe dokumentu XmlDataDocument XslTransform</span><span class="sxs-lookup"><span data-stu-id="3da85-140">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [<span data-ttu-id="3da85-141">Dane wejściowe XmlDocument XslTransform</span><span class="sxs-lookup"><span data-stu-id="3da85-141">XmlDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)