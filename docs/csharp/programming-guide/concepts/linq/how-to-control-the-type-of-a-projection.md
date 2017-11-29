---
title: 'Porady: kontrolowanie typu projekcji (C#)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9b7b5b39ca308449b09023bc21446859a728e738
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-the-type-of-a-projection-c"></a><span data-ttu-id="af8f9-102">Porady: kontrolowanie typu projekcji (C#)</span><span class="sxs-lookup"><span data-stu-id="af8f9-102">How to: Control the Type of a Projection (C#)</span></span>
<span data-ttu-id="af8f9-103">Projekcja to proces biorąc jeden zestaw danych, filtrowania jej zmiana jego kształtu i nawet zmianę jej typu.</span><span class="sxs-lookup"><span data-stu-id="af8f9-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="af8f9-104">Wyrażenia zapytań większości wykonać projekcje.</span><span class="sxs-lookup"><span data-stu-id="af8f9-104">Most query expressions perform projections.</span></span> <span data-ttu-id="af8f9-105">Wynikiem obliczania większość wyrażenia zapytań w tej sekcji <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, można jednak sterować typ projekcji, aby utworzyć kolekcje innych typów.</span><span class="sxs-lookup"><span data-stu-id="af8f9-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="af8f9-106">W tym temacie pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="af8f9-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af8f9-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="af8f9-107">Example</span></span>  
 <span data-ttu-id="af8f9-108">W poniższym przykładzie zdefiniowano nowy typ `Customer`.</span><span class="sxs-lookup"><span data-stu-id="af8f9-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="af8f9-109">Wyrażenia zapytania następnie tworzy nowy `Customer` obiekty w `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="af8f9-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="af8f9-110">Powoduje to, że typ tego wyrażenia zapytania <xref:System.Collections.Generic.IEnumerable%601> z `Customer`.</span><span class="sxs-lookup"><span data-stu-id="af8f9-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="af8f9-111">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="af8f9-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
public class Customer  
{  
    private string customerID;  
    public string CustomerID{ get{return customerID;} set{customerID = value;}}  
  
    private string companyName;  
    public string CompanyName{ get{return companyName;} set{companyName = value;}}  
  
    private string contactName;  
    public string ContactName { get{return contactName;} set{contactName = value;}}  
  
    public Customer(string customerID, string companyName, string contactName)  
    {  
        CustomerID = customerID;  
        CompanyName = companyName;  
        ContactName = contactName;  
    }  
  
    public override string ToString()  
    {  
        return String.Format("{0}:{1}:{2}", this.customerID, this.companyName, this.contactName);  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement custOrd = XElement.Load("CustomersOrders.xml");  
        IEnumerable<Customer> custList =  
            from el in custOrd.Element("Customers").Elements("Customer")  
            select new Customer(  
                (string)el.Attribute("CustomerID"),  
                (string)el.Element("CompanyName"),  
                (string)el.Element("ContactName")  
            );  
        foreach (Customer cust in custList)  
            Console.WriteLine(cust);  
    }  
}  
```  
  
 <span data-ttu-id="af8f9-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="af8f9-112">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="af8f9-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af8f9-113">See Also</span></span>  
 <xref:System.Linq.Enumerable.Select%2A>  
 [<span data-ttu-id="af8f9-114">Projekcje i przekształcenia (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="af8f9-114">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)