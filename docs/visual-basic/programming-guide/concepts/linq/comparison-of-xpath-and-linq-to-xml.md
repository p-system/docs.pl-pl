---
title: "Porównanie XPath i składnika LINQ to XML1"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3fd07c1-6761-4e4b-8eb1-ddd780ed8d44
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 761df14ee4bdfa9ddeb3f742134f4f47f8bb283f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="84cc8-102">Porównanie XPath i LINQ do XML</span><span class="sxs-lookup"><span data-stu-id="84cc8-102">Comparison of XPath and LINQ to XML</span></span>
<span data-ttu-id="84cc8-103">Wyrażenie XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] oferują niektórych podobnych możliwościach.</span><span class="sxs-lookup"><span data-stu-id="84cc8-103">XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] offer some similar functionality.</span></span> <span data-ttu-id="84cc8-104">Jednocześnie może służyć do badania drzewo XML zwracania wyników takich jako kolekcję elementów, Kolekcja atrybutów, kolekcja węzłów lub wartość elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="84cc8-104">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="84cc8-105">Istnieją jednak także pewne różnice.</span><span class="sxs-lookup"><span data-stu-id="84cc8-105">However, there are also some differences.</span></span>  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="84cc8-106">Różnice między XPath i LINQ do XML</span><span class="sxs-lookup"><span data-stu-id="84cc8-106">Differences Between XPath and LINQ to XML</span></span>  
 <span data-ttu-id="84cc8-107">Wyrażenie XPath nie zezwala na projekcji nowych typów.</span><span class="sxs-lookup"><span data-stu-id="84cc8-107">XPath does not allow projection of new types.</span></span> <span data-ttu-id="84cc8-108">Można tylko zwraca kolekcje węzłów w drzewie, natomiast [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] można wykonać zapytania i projektu wykres obiektu lub drzewo XML w nowy kształt.</span><span class="sxs-lookup"><span data-stu-id="84cc8-108">It can only return collections of nodes from the tree, whereas [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] can execute a query and project an object graph or an XML tree in a new shape.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="84cc8-109">zapytania obejmować większą funkcjonalność i są bardziej efektywne niż wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="84cc8-109"> queries encompass much more functionality and are much more powerful than XPath expressions.</span></span>  
  
 <span data-ttu-id="84cc8-110">Wyrażenia XPath istnieje w izolacji w ramach ciągu.</span><span class="sxs-lookup"><span data-stu-id="84cc8-110">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="84cc8-111">Kompilator Visual Basic nie może pomóc przeanalizować wyrażenia XPath w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="84cc8-111">The Visual Basic compiler cannot help parse the XPath expression at compile time.</span></span> <span data-ttu-id="84cc8-112">Z kolei [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania są przeanalizować i kompilowany przez kompilator podstawowe theVisual.</span><span class="sxs-lookup"><span data-stu-id="84cc8-112">By contrast, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries are parsed and compiled by theVisual Basic compiler.</span></span> <span data-ttu-id="84cc8-113">Kompilator jest w stanie catch wiele błędów zapytania.</span><span class="sxs-lookup"><span data-stu-id="84cc8-113">The compiler is able to catch many query errors.</span></span>  
  
 <span data-ttu-id="84cc8-114">Wyniki XPath nie są silnie typizowane.</span><span class="sxs-lookup"><span data-stu-id="84cc8-114">XPath results are not strongly typed.</span></span> <span data-ttu-id="84cc8-115">W wielu sytuacjach wynikiem obliczenia wyrażenia XPath jest obiektem, a zależy od dewelopera określenie odpowiedniego typu i Rzutuj wynik w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="84cc8-115">In a number of circumstances, the result of evaluating an XPath expression is an object, and it is up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="84cc8-116">Przez kontrast, projekcje z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania są silnie typizowane.</span><span class="sxs-lookup"><span data-stu-id="84cc8-116">By contrast, the projections from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query are strongly typed.</span></span>  
  
## <a name="result-ordering"></a><span data-ttu-id="84cc8-117">Powoduje porządkowanie</span><span class="sxs-lookup"><span data-stu-id="84cc8-117">Result Ordering</span></span>  
 <span data-ttu-id="84cc8-118">Wyrażenie XPath 1.0 zalecenie informujący nieuporządkowaną kolekcją będącą wynikiem obliczenia wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="84cc8-118">The XPath 1.0 Recommendation states that a collection that is the result of evaluating an XPath expression is unordered.</span></span>  
  
 <span data-ttu-id="84cc8-119">Jednak gdy iteracji w kolekcji zwracane przez [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] metody osi XPath, węzły w kolekcji są zwracane w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="84cc8-119">However, when iterating through a collection returned by a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="84cc8-120">Jest to możliwe nawet wtedy, gdy dostęp do osi XPath gdzie predykaty są wyrażone w kolejności odwrotnej dokumentu, takich jak `preceding` i `preceding-sibling`.</span><span class="sxs-lookup"><span data-stu-id="84cc8-120">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>  
  
 <span data-ttu-id="84cc8-121">Przez kontrast, większość [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osie zwracają kolekcje w kolejności dokumentu, ale dwa z nich, <xref:System.Xml.Linq.XNode.Ancestors%2A> i <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, zwróć kolekcji w kolejności odwrotnej dokumentu.</span><span class="sxs-lookup"><span data-stu-id="84cc8-121">By contrast, most of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes return collections in document order, but two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="84cc8-122">W poniższej tabeli wylicza osi i wskazuje kolejność kolekcji dla każdego:</span><span class="sxs-lookup"><span data-stu-id="84cc8-122">The following table enumerates the axes, and indicates collection order for each:</span></span>  
  
|<span data-ttu-id="84cc8-123">LINQ do XML osi</span><span class="sxs-lookup"><span data-stu-id="84cc8-123">LINQ to XML axis</span></span>|<span data-ttu-id="84cc8-124">Szeregowanie</span><span class="sxs-lookup"><span data-stu-id="84cc8-124">Ordering</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="84cc8-125">XContainer.DescendantNodes</span><span class="sxs-lookup"><span data-stu-id="84cc8-125">XContainer.DescendantNodes</span></span>|<span data-ttu-id="84cc8-126">Kolejności dokumentów</span><span class="sxs-lookup"><span data-stu-id="84cc8-126">Document order</span></span>|  
|<span data-ttu-id="84cc8-127">XContainer.Descendants</span><span class="sxs-lookup"><span data-stu-id="84cc8-127">XContainer.Descendants</span></span>|<span data-ttu-id="84cc8-128">Kolejności dokumentów</span><span class="sxs-lookup"><span data-stu-id="84cc8-128">Document order</span></span>|  
|<span data-ttu-id="84cc8-129">XContainer.Elements</span><span class="sxs-lookup"><span data-stu-id="84cc8-129">XContainer.Elements</span></span>|<span data-ttu-id="84cc8-130">Kolejności dokumentów</span><span class="sxs-lookup"><span data-stu-id="84cc8-130">Document order</span></span>|  
|<span data-ttu-id="84cc8-131">XContainer.Nodes</span><span class="sxs-lookup"><span data-stu-id="84cc8-131">XContainer.Nodes</span></span>|<span data-ttu-id="84cc8-132">Kolejności dokumentów</span><span class="sxs-lookup"><span data-stu-id="84cc8-132">Document order</span></span>|  
|<span data-ttu-id="84cc8-133">XContainer.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="84cc8-133">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="84cc8-134">Kolejności dokumentów</span><span class="sxs-lookup"><span data-stu-id="84cc8-134">Document order</span></span>|  
|<span data-ttu-id="84cc8-135">XContainer.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="84cc8-135">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="84cc8-136">Kolejności dokumentów</span><span class="sxs-lookup"><span data-stu-id="84cc8-136">Document order</span></span>|  
|<span data-ttu-id="84cc8-137">XElement.AncestorsAndSelf</span><span class="sxs-lookup"><span data-stu-id="84cc8-137">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="84cc8-138">Odwracanie kolejności dokumentów</span><span class="sxs-lookup"><span data-stu-id="84cc8-138">Reverse document order</span></span>|  
|<span data-ttu-id="84cc8-139">XElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="84cc8-139">XElement.Attributes</span></span>|<span data-ttu-id="84cc8-140">Kolejności dokumentów</span><span class="sxs-lookup"><span data-stu-id="84cc8-140">Document order</span></span>|  
|<span data-ttu-id="84cc8-141">XElement.DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="84cc8-141">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="84cc8-142">Kolejności dokumentów</span><span class="sxs-lookup"><span data-stu-id="84cc8-142">Document order</span></span>|  
|<span data-ttu-id="84cc8-143">XElement.DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="84cc8-143">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="84cc8-144">Kolejności dokumentów</span><span class="sxs-lookup"><span data-stu-id="84cc8-144">Document order</span></span>|  
|<span data-ttu-id="84cc8-145">XNode.Ancestors</span><span class="sxs-lookup"><span data-stu-id="84cc8-145">XNode.Ancestors</span></span>|<span data-ttu-id="84cc8-146">Odwracanie kolejności dokumentów</span><span class="sxs-lookup"><span data-stu-id="84cc8-146">Reverse document order</span></span>|  
|<span data-ttu-id="84cc8-147">XNode.ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="84cc8-147">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="84cc8-148">Kolejności dokumentów</span><span class="sxs-lookup"><span data-stu-id="84cc8-148">Document order</span></span>|  
|<span data-ttu-id="84cc8-149">XNode.ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="84cc8-149">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="84cc8-150">Kolejności dokumentów</span><span class="sxs-lookup"><span data-stu-id="84cc8-150">Document order</span></span>|  
|<span data-ttu-id="84cc8-151">XNode.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="84cc8-151">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="84cc8-152">Kolejności dokumentów</span><span class="sxs-lookup"><span data-stu-id="84cc8-152">Document order</span></span>|  
|<span data-ttu-id="84cc8-153">XNode.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="84cc8-153">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="84cc8-154">Kolejności dokumentów</span><span class="sxs-lookup"><span data-stu-id="84cc8-154">Document order</span></span>|  
  
## <a name="positional-predicates"></a><span data-ttu-id="84cc8-155">Predykaty pozycyjne</span><span class="sxs-lookup"><span data-stu-id="84cc8-155">Positional Predicates</span></span>  
 <span data-ttu-id="84cc8-156">W wyrażeniu XPath predykaty pozycyjne są wyrażone w kolejności dokumentów dla wielu osi, ale są wyrażane w kolejności odwrotnej dokumentu dla osi wstecznego, które są `preceding`, `preceding-sibling`, `ancestor`, i `ancestor-or-self`.</span><span class="sxs-lookup"><span data-stu-id="84cc8-156">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes, which are `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="84cc8-157">Na przykład, wyrażenie XPath `preceding-sibling::*[1]` zwraca natychmiast poprzedni element równorzędny.</span><span class="sxs-lookup"><span data-stu-id="84cc8-157">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="84cc8-158">Dotyczy to nawet, jeśli zestaw wyników końcowych są prezentowane w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="84cc8-158">This is the case even though the final result set is presented in document order.</span></span>  
  
 <span data-ttu-id="84cc8-159">Z kolei wszystkie predykaty pozycyjne w składniku LINQ to XML są zawsze wyrażone w porządku osi.</span><span class="sxs-lookup"><span data-stu-id="84cc8-159">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="84cc8-160">Na przykład `anElement.ElementsBeforeSelf().ToList()[0]` zwraca pierwszy element podrzędny elementu nadrzędnego elementu, którego dotyczy kwerenda nie natychmiastowego poprzedniego elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="84cc8-160">For example, `anElement.ElementsBeforeSelf().ToList()[0]` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="84cc8-161">Inny przykład: `anElement.Ancestors().ToList()[0]` zwraca element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="84cc8-161">Another example: `anElement.Ancestors().ToList()[0]` returns the parent element.</span></span>  
  
 <span data-ttu-id="84cc8-162">Należy pamiętać, że powyższe podejście zostaje całą kolekcję.</span><span class="sxs-lookup"><span data-stu-id="84cc8-162">Note that the above approach materializes the entire collection.</span></span> <span data-ttu-id="84cc8-163">Nie jest najbardziej wydajnym sposobem zapisu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="84cc8-163">This is not the most efficient way to write that query.</span></span> <span data-ttu-id="84cc8-164">Plik został zapisany w ten sposób, aby zademonstrować zachowanie pozycyjnych predykatów.</span><span class="sxs-lookup"><span data-stu-id="84cc8-164">It was written in that way to demonstrate the behavior of positional predicates.</span></span> <span data-ttu-id="84cc8-165">Sposób bardziej odpowiednie do zapisu w jednym zapytaniu jest użycie <xref:System.Linq.Enumerable.First%2A> metody, w następujący sposób: `anElement.ElementsBeforeSelf().First()`.</span><span class="sxs-lookup"><span data-stu-id="84cc8-165">A more appropriate way to write the same query is to use the <xref:System.Linq.Enumerable.First%2A> method, as follows: `anElement.ElementsBeforeSelf().First()`.</span></span>  
  
 <span data-ttu-id="84cc8-166">Jeśli chcesz znaleźć natychmiast poprzedniego elementu w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], możesz zapisać następującego wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="84cc8-166">If you wanted to find the immediately preceding element in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you would write the following expression:</span></span>  
  
 `ElementsBeforeSelf().Last()`  
  
## <a name="performance-differences"></a><span data-ttu-id="84cc8-167">Różnice dotyczące wydajności</span><span class="sxs-lookup"><span data-stu-id="84cc8-167">Performance Differences</span></span>  
 <span data-ttu-id="84cc8-168">Kwerendy XPath, korzystających z funkcji XPath w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nie będzie wykonywać oraz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="84cc8-168">XPath queries that use the XPath functionality in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="comparison-of-composition"></a><span data-ttu-id="84cc8-169">Porównanie kompozycji</span><span class="sxs-lookup"><span data-stu-id="84cc8-169">Comparison of Composition</span></span>  
 <span data-ttu-id="84cc8-170">Skład [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytanie jest nieco zbliżony do kompozycji wyrażenie XPath, mimo że jest to bardzo różnią się w składni.</span><span class="sxs-lookup"><span data-stu-id="84cc8-170">Composition of a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query is somewhat parallel to composition of an XPath expression, although very different in syntax.</span></span>  
  
 <span data-ttu-id="84cc8-171">Na przykład, jeśli element w zmiennej o nazwie `customers`, i chcesz znaleźć podwójnym elementu o nazwie `CompanyName` w obszarze wszystkich elementów podrzędnych o nazwie `Customer`, możesz zapisać wyrażenie XPath w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="84cc8-171">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write an XPath expression as follows:</span></span>  
  
```vb  
customers.XPathSelectElements("./Customer/CompanyName")  
```  
  
 <span data-ttu-id="84cc8-172">Odpowiednik [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytanie jest:</span><span class="sxs-lookup"><span data-stu-id="84cc8-172">The equivalent [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query is:</span></span>  
  
```vb  
customers.Element("Customer").Elements("CompanyName")  
```  
  
 <span data-ttu-id="84cc8-173">Istnieją podobne równoleżników dla każdego osi XPath.</span><span class="sxs-lookup"><span data-stu-id="84cc8-173">There are similar parallels for each of the XPath axes.</span></span>  
  
|<span data-ttu-id="84cc8-174">Wyrażenie XPath osi</span><span class="sxs-lookup"><span data-stu-id="84cc8-174">XPath axis</span></span>|<span data-ttu-id="84cc8-175">LINQ do XML osi</span><span class="sxs-lookup"><span data-stu-id="84cc8-175">LINQ to XML axis</span></span>|  
|----------------|----------------------|  
|<span data-ttu-id="84cc8-176">podrzędne (oś domyślne)</span><span class="sxs-lookup"><span data-stu-id="84cc8-176">child (the default axis)</span></span>|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="84cc8-177">Nadrzędny (.)</span><span class="sxs-lookup"><span data-stu-id="84cc8-177">Parent (..)</span></span>|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="84cc8-178">osi atrybutu (@)</span><span class="sxs-lookup"><span data-stu-id="84cc8-178">attribute axis (@)</span></span>|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="84cc8-179">lub</span><span class="sxs-lookup"><span data-stu-id="84cc8-179">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="84cc8-180">elementem nadrzędnym osi</span><span class="sxs-lookup"><span data-stu-id="84cc8-180">ancestor axis</span></span>|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="84cc8-181">elementem nadrzędnym or-self osi</span><span class="sxs-lookup"><span data-stu-id="84cc8-181">ancestor-or-self axis</span></span>|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="84cc8-182">osi elementu podrzędnego (/ /)</span><span class="sxs-lookup"><span data-stu-id="84cc8-182">descendant axis (//)</span></span>|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="84cc8-183">lub</span><span class="sxs-lookup"><span data-stu-id="84cc8-183">or</span></span><br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="84cc8-184">obiekt podrzędny lub własne</span><span class="sxs-lookup"><span data-stu-id="84cc8-184">descendant-or-self</span></span>|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="84cc8-185">lub</span><span class="sxs-lookup"><span data-stu-id="84cc8-185">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="84cc8-186">element równorzędny poniżej</span><span class="sxs-lookup"><span data-stu-id="84cc8-186">following-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="84cc8-187">lub</span><span class="sxs-lookup"><span data-stu-id="84cc8-187">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="84cc8-188">poprzedzający element równorzędny</span><span class="sxs-lookup"><span data-stu-id="84cc8-188">preceding-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="84cc8-189">lub</span><span class="sxs-lookup"><span data-stu-id="84cc8-189">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="84cc8-190">Po</span><span class="sxs-lookup"><span data-stu-id="84cc8-190">following</span></span>|<span data-ttu-id="84cc8-191">Bezpośredniego odpowiednika.</span><span class="sxs-lookup"><span data-stu-id="84cc8-191">No direct equivalent.</span></span>|  
|<span data-ttu-id="84cc8-192">poprzedzających</span><span class="sxs-lookup"><span data-stu-id="84cc8-192">preceding</span></span>|<span data-ttu-id="84cc8-193">Bezpośredniego odpowiednika.</span><span class="sxs-lookup"><span data-stu-id="84cc8-193">No direct equivalent.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84cc8-194">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="84cc8-194">See Also</span></span>  
 [<span data-ttu-id="84cc8-195">LINQ do XML dla wyrażenia XPath użytkowników (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84cc8-195">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)