---
title: KnownAssemblyAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3bc7f31-95ff-46e1-8308-d206ec426f6e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5e3df3ff5a5cbccc36e712815de5e70236612e3d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="knownassemblyattribute"></a><span data-ttu-id="5329d-102">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="5329d-102">KnownAssemblyAttribute</span></span>
<span data-ttu-id="5329d-103">W tym przykładzie pokazano, jak można dostosować procesy serializacji i deserializacji za pomocą <xref:System.Runtime.Serialization.DataContractResolver> klasy.</span><span class="sxs-lookup"><span data-stu-id="5329d-103">This sample demonstrates how the serialization and deserialization processes can be customized by using the <xref:System.Runtime.Serialization.DataContractResolver> class.</span></span> <span data-ttu-id="5329d-104">W tym przykładzie przedstawiono sposób dynamicznego dodawania znane typy podczas serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="5329d-104">This sample shows how to dynamically add known types during serialization and deserialization.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="5329d-105">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="5329d-105">Sample Details</span></span>  
 <span data-ttu-id="5329d-106">W tym przykładzie składa się z czterech projektów.</span><span class="sxs-lookup"><span data-stu-id="5329d-106">This sample is composed of four projects.</span></span> <span data-ttu-id="5329d-107">Jeden z nich odnosi się do usługi ma być obsługiwana przez usługi IIS, który definiuje następujące kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="5329d-107">One of them corresponds to the service, to be hosted by IIS, which defines the following service contract.</span></span>  
  
```  
// Definition of a service contract.  
[ServiceContract(Namespace = "http://Microsoft.Samples.KAA")]  
[KnownAssembly("Types")]  
public interface IDataContractCalculator  
 {  
    [OperationContract]  
    ComplexNumber Add(ComplexNumber n1, ComplexNumber n2);  
  
    [OperationContract]  
    ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2);  
  
    [OperationContract]  
    ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2);  
  
    [OperationContract]  
    ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2);  
  
    [OperationContract]  
    List<ComplexNumber> CombineLists(List<ComplexNumber> list1, List<ComplexNumber> list2);  
}  
```  
  
 <span data-ttu-id="5329d-108">Kontrakt usługi jest zaimplementowana, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5329d-108">The service contract is implemented as shown in the following example.</span></span>  
  
```  
// Service class that implements the service contract.  
 public class DataContractCalculatorService : IDataContractCalculator  
 {  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        return new ComplexNumberWithMagnitude(n1.Real + n2.Real, n1.Imaginary + n2.Imaginary);  
    }  
  
    public ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2)  
    {  
        return new ComplexNumberWithMagnitude(n1.Real - n2.Real, n1.Imaginary - n2.Imaginary);  
    }  
  
    public ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2)  
    {  
        double real1 = n1.Real * n2.Real;  
        double imaginary1 = n1.Real * n2.Imaginary;  
        double imaginary2 = n2.Real * n1.Imaginary;  
        double real2 = n1.Imaginary * n2.Imaginary * -1;  
  
        return new ComplexNumber(real1 + real2, imaginary1 + imaginary2);  
    }  
  
    public ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2)  
    {  
        ComplexNumber conjugate = new ComplexNumber(n2.Real, -1 * n2.Imaginary);  
        ComplexNumber numerator = Multiply(n1, conjugate);  
        ComplexNumber denominator = Multiply(n2, conjugate);  
  
        return new ComplexNumber(numerator.Real / denominator.Real, numerator.Imaginary);  
    }  
  
    public List<ComplexNumber> CombineLists(List<ComplexNumber> list1, List<ComplexNumber> list2)  
    {  
        List<ComplexNumber> result  = new List<ComplexNumber>();  
        result.AddRange(list1);  
        result.AddRange(list2);  
  
        return result;  
    }  
}  
```  
  
 <span data-ttu-id="5329d-109">Inny projekt odnosi się do klienta, który komunikuje się z serwerem, a następnie wywołuje metody, które ujawnia on.</span><span class="sxs-lookup"><span data-stu-id="5329d-109">Another project corresponds to the client, which communicates with the server and invokes the methods that it exposes.</span></span> <span data-ttu-id="5329d-110">W poniższym przykładzie przedstawiono definicję klienta.</span><span class="sxs-lookup"><span data-stu-id="5329d-110">The definition of the client is shown in the following example.</span></span>  
  
```  
 // Client implementation code.  
 class Client  
 {  
    static void Main()  
    {  
        // Create a channel.  
         EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc/IDataContractCalculator");  
        BasicHttpBinding binding = new BasicHttpBinding();  
        ChannelFactory<IDataContractCalculator> factory = new ChannelFactory<IDataContractCalculator>(binding, address);  
        IDataContractCalculator channel = factory.CreateChannel();  
  
        // Call the Add service operation.  
         ComplexNumber value1 = new ComplexNumber(1, 2);  
        ComplexNumber value2 = new ComplexNumberWithMagnitude(3, 4);  
        ComplexNumber result = channel.Add(value1, value2);  
        Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
            value1.Real, value1.Imaginary, value2.Real, value2.Imaginary, result.Real, result.Imaginary);  
        if (result is ComplexNumberWithMagnitude)  
        {  
            Console.WriteLine("Magnitude: {0}", ((ComplexNumberWithMagnitude)result).Magnitude);  
        }  
        else  
         {  
            Console.WriteLine("No magnitude was sent from the service");  
        }  
        Console.WriteLine();  
  
        // Call the Subtract service operation.  
         value1 = new ComplexNumber(1, 2);  
        value2 = new ComplexNumber(3, 4);  
        result = channel.Subtract(value1, value2);  
        Console.WriteLine("Subtract({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
            value1.Real, value1.Imaginary, value2.Real, value2.Imaginary, result.Real, result.Imaginary);  
        if (result is ComplexNumberWithMagnitude)  
        {  
            Console.WriteLine("Magnitude: {0}", ((ComplexNumberWithMagnitude)result).Magnitude);  
        }  
        else  
         {  
            Console.WriteLine("No magnitude was sent from the service");  
        }  
        Console.WriteLine();  
  
        // Call the Multiply service operation.  
         value1 = new ComplexNumber(2, 3);  
        value2 = new ComplexNumber(4, 7);  
        result = channel.Multiply(value1, value2);  
        Console.WriteLine("Multiply({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
            value1.Real, value1.Imaginary, value2.Real, value2.Imaginary, result.Real, result.Imaginary);  
        if (result is ComplexNumberWithMagnitude)  
        {  
            Console.WriteLine("Magnitude: {0}", ((ComplexNumberWithMagnitude)result).Magnitude);  
        }  
        else  
         {  
            Console.WriteLine("No magnitude was sent from the service");  
        }  
        Console.WriteLine();  
  
        // Call the Divide service operation.  
         value1 = new ComplexNumber(3, 7);  
        value2 = new ComplexNumber(5, -2);  
        result = channel.Divide(value1, value2);  
        Console.WriteLine("Divide({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
            value1.Real, value1.Imaginary, value2.Real, value2.Imaginary, result.Real, result.Imaginary);  
        if (result is ComplexNumberWithMagnitude)  
        {  
            Console.WriteLine("Magnitude: {0}", ((ComplexNumberWithMagnitude)result).Magnitude);  
        }  
        else  
         {  
            Console.WriteLine("No magnitude was sent from the service");  
        }  
        Console.WriteLine();  
  
        // Call the CombineLists service operation.  
         List<ComplexNumber> list1 = new List<ComplexNumber>();  
        List<ComplexNumber> list2 = new List<ComplexNumber>();  
        list1.Add(new ComplexNumber(1, 1));  
        list1.Add(new ComplexNumber(2, 2));  
        list1.Add(new ComplexNumberWithMagnitude(3, 3));  
        list1.Add(new ComplexNumberWithMagnitude(4, 4));  
        List<ComplexNumber> listResult = channel.CombineLists(list1, list2);  
        Console.WriteLine("Lists combined:");  
        foreach (ComplexNumber n in listResult)  
        {  
            Console.WriteLine("{0} + {1}i", n.Real, n.Imaginary);  
        }  
        Console.WriteLine();  
  
        // Close the channel  
         ((IChannel)channel).Close();  
  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```  
  
 <span data-ttu-id="5329d-111">Definicja kontraktu usługi jest oznaczony atrybutem `KnownAssembly` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5329d-111">The definition of the service contract is marked with the `KnownAssembly` attribute.</span></span> <span data-ttu-id="5329d-112">Ten atrybut zawiera nazwę biblioteki typów, które stają się znane w czasie wykonywania zarówno przez usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="5329d-112">This attribute contains the name of a library of types, which all become known at runtime by both the service and the client.</span></span>  
  
 <span data-ttu-id="5329d-113">`KnownAssembly` Atrybutu implementuje `IContractBehavior` Aby zdefiniować `DataContractSerializer` z `DataContractResolver` zdefiniowane dla każdej operacji zachowania.</span><span class="sxs-lookup"><span data-stu-id="5329d-113">The `KnownAssembly` attribute implements `IContractBehavior` in order to define a `DataContractSerializer` with a `DataContractResolver` defined for each of the operation behaviors.</span></span> <span data-ttu-id="5329d-114">`DataContractResolver` Odzwierciedla za pośrednictwem zestawu po utworzeniu i tworzy słownik z mapowania między typami i nazwy, który będzie używany podczas serializacji i deserializacji różnych typów.</span><span class="sxs-lookup"><span data-stu-id="5329d-114">The `DataContractResolver` reflects over the assembly when it is created, and creates the dictionary with the mapping between types and names to be used when serializing and deserializing the different types.</span></span> <span data-ttu-id="5329d-115">W ten sposób `ResolveType` i `ResolveName` typy musisz sprawdzić danych wymaganych w słowniku.</span><span class="sxs-lookup"><span data-stu-id="5329d-115">In that way, the `ResolveType` and `ResolveName` types must look up the data required in the dictionary.</span></span>  
  
 <span data-ttu-id="5329d-116">`DataContractResolver` Zdefiniowane w tym przykładzie przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5329d-116">The `DataContractResolver` defined for this sample is shown in the following example.</span></span>  
  
```  
public class MyDataContractResolver : DataContractResolver  
    {  
       Dictionary<string, XmlDictionaryString> dictionary = new Dictionary<string, XmlDictionaryString>();  
       Assembly assembly;  
  
       public MyDataContractResolver(string assemblyName)  
       {  
           this.KnownTypes = new List<Type>();  
  
           assembly = Assembly.Load(new AssemblyName(assemblyName));  
           foreach (Type type in assembly.GetTypes())  
           {  
               bool knownTypeFound = false;  
               System.Attribute[] attrs = System.Attribute.GetCustomAttributes(type);  
               if (attrs.Length != 0)  
               {  
                   foreach (System.Attribute attr in attrs)  
                   {  
                       if (attr is KnownTypeAttribute)  
                       {  
                           Type t = ((KnownTypeAttribute)attr).Type;  
                           if (this.KnownTypes.IndexOf(t) < 0)  
                           {  
                               this.KnownTypes.Add(t);  
                           }  
                           knownTypeFound = true;  
                       }  
                   }  
               }  
               if (!knownTypeFound)  
               {  
                   string name = type.Name;  
                   string namesp = type.Namespace;  
                   if (!dictionary.ContainsKey(name))  
                   {  
                       dictionary.Add(name, new XmlDictionaryString(XmlDictionary.Empty, name, 0));  
                   }  
                   if (!dictionary.ContainsKey(namesp))  
                   {  
                       dictionary.Add(namesp, new XmlDictionaryString(XmlDictionary.Empty, namesp, 0));  
                   }  
               }  
           }  
       }  
  
       public IList<Type> KnownTypes  
       {  
           get; set;  
       }  
  
       // Used at deserialization  
        // Allows users to map xsi:type name to any Type   
        public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
       {  
           XmlDictionaryString tName;  
           XmlDictionaryString tNamespace;  
  
           if (dictionary.TryGetValue(typeName, out tName) && dictionary.TryGetValue(typeNamespace, out tNamespace))  
           {  
               return this.assembly.GetType(tNamespace.Value + "." + tName.Value);  
           }  
           else  
            {  
               return knownTypeResolver.ResolveName(typeName, typeNamespace, null);  
           }  
       }  
  
       // Used at serialization  
        // Maps any Type to a new xsi:type representation  
        public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
       {  
           knownTypeResolver.ResolveType(dataContractType, null, out typeName, out typeNamespace);  
           if (typeName == null || typeNamespace == null)  
           {  
               typeName = new XmlDictionaryString(XmlDictionary.Empty, dataContractType.Name, 0);  
               typeNamespace = new XmlDictionaryString(XmlDictionary.Empty, dataContractType.Namespace, 0);  
           }  
       }  
   }  
```  
  
 <span data-ttu-id="5329d-117">Biblioteki typów używanych w tym przykładzie przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5329d-117">The library of types used in this sample is shown in the following example.</span></span>  
  
```  
 [DataContract]  
 public class ComplexNumber  
 {  
    [DataMember]  
    private double real;  
  
    [DataMember]  
    private double imaginary;  
  
    public ComplexNumber(double r1, double i1)  
    {  
        this.Real = r1;  
        this.Imaginary = i1;  
    }  
  
    public double Real  
    {  
        get { return real; }  
        set { real = value; }  
    }  
  
    public double Imaginary  
    {  
        get { return imaginary; }  
        set { imaginary = value; }  
    }  
}  
  
[DataContract]  
public class ComplexNumberWithMagnitude : ComplexNumber  
 {  
    public ComplexNumberWithMagnitude(double real, double imaginary) : base(real, imaginary) { }  
  
    [DataMember]  
    public double Magnitude  
    {  
        get { return Math.Sqrt(Imaginary * Imaginary + Real * Real); }  
        set { }  
    }  
}  
```  
  
 <span data-ttu-id="5329d-118">Należy pamiętać, że `ComplexNumber` nie trzeba znać statycznie `ComplexNumberWithMagnitude` typu, ponieważ jego staje się znane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5329d-118">Note that `ComplexNumber` does not need to statically know the `ComplexNumberWithMagnitude` type, because it becomes known at runtime.</span></span>  
  
 <span data-ttu-id="5329d-119">Gdy próbki jest skompilowany i wykonać, jest to oczekiwane dane wyjściowe uzyskane w kliencie:</span><span class="sxs-lookup"><span data-stu-id="5329d-119">When the sample is built and executed, this is the expected output obtained in the client:</span></span>  
  
```  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Magnitude: 7.21110255092798  
  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Magnitude: 2.82842712474619  
  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
No magnitude was sent from the service  
  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 41i  
No magnitude was sent from the service  
  
Lists combined:  
1 + 1i  
2 + 2i  
3 + 3i  
4 + 4i  
```  
  
#### <a name="to-set-up-run-and-build-the-sample"></a><span data-ttu-id="5329d-120">Aby skonfigurować, uruchomić i tworzyć przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="5329d-120">To set up, run, and build the sample</span></span>  
  
1.  <span data-ttu-id="5329d-121">Kliknij prawym przyciskiem myszy rozwiązanie **KnownAssemblyAttribute** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="5329d-121">Right-click the solution **KnownAssemblyAttribute** and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="5329d-122">W **wspólne właściwości**, wybierz pozycję **projekt startowy**, a następnie kliknij przycisk **wiele projektów startowych**.</span><span class="sxs-lookup"><span data-stu-id="5329d-122">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>  
  
3.  <span data-ttu-id="5329d-123">Dodaj **Start** akcji **usługi** i **klienta** projektów.</span><span class="sxs-lookup"><span data-stu-id="5329d-123">Add the **Start** action to the **Service** and **Client** projects.</span></span>  
  
4.  <span data-ttu-id="5329d-124">Kliknij przycisk **OK**i naciśnij klawisz **F5** do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="5329d-124">Click **OK**, and press **F5** to run the sample.</span></span>  
  
5.  <span data-ttu-id="5329d-125">Jeśli aplikacja nie pracuje poprawnie, wykonaj następujące kroki, aby upewnić się, że środowiska nie został prawidłowo skonfigurowany:</span><span class="sxs-lookup"><span data-stu-id="5329d-125">If the application does not run properly, follow these steps to make sure your environment has been properly set up:</span></span>  
  
6.  <span data-ttu-id="5329d-126">Upewnij się, że wykonano procedurę [jednorazowego ustawić się procedury dla przykładów Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=150774).</span><span class="sxs-lookup"><span data-stu-id="5329d-126">Ensure that you have performed the [One-Time Set Up Procedure for the Windows Communication Foundation Samples](http://go.microsoft.com/fwlink/?LinkId=150774).</span></span>  
  
7.  <span data-ttu-id="5329d-127">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [tworzenia Windows Communication Foundation — przykład](http://go.microsoft.com/fwlink/?LinkId=150775).</span><span class="sxs-lookup"><span data-stu-id="5329d-127">To build the solution, follow the instructions in [Building the Windows Communication Foundation Sample](http://go.microsoft.com/fwlink/?LinkId=150775).</span></span>  
  
8.  <span data-ttu-id="5329d-128">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=150776).</span><span class="sxs-lookup"><span data-stu-id="5329d-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](http://go.microsoft.com/fwlink/?LinkId=150776).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5329d-129">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="5329d-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5329d-130">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="5329d-130">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5329d-131">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="5329d-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5329d-132">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5329d-132">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\KnownAssemblyAttribute`  
  
## <a name="see-also"></a><span data-ttu-id="5329d-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5329d-133">See Also</span></span>