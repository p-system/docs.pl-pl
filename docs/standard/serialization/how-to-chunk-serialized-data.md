---
title: "Porady: bryłkach danych serializacji."
ms.date: 03/30/2017
ms.prod: .net
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- chunking serialized data
- data chunking
- binary serialization, chunking data
- large data set chunking
- serialization, chunking data
- serialization, examples
- binary serialization, examples
ms.assetid: 22f1b818-7e0d-428a-8680-f17d6ebdd185
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 769dcbd554f8b39fbe449a8e3a6b379a7472a38f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-chunk-serialized-data"></a><span data-ttu-id="5c348-102">Porady: bryłkach danych serializacji.</span><span class="sxs-lookup"><span data-stu-id="5c348-102">How to: chunk serialized data</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="5c348-103">Są dwa problemy, które występują podczas wysyłania dużych zestawach danych w wiadomości usługi sieci Web:</span><span class="sxs-lookup"><span data-stu-id="5c348-103">Two issues that occur when sending large data sets in Web service messages are:</span></span>  
  
1.  <span data-ttu-id="5c348-104">Duży zestaw roboczy (pamięć) z powodu buforowania przez aparat serializacji.</span><span class="sxs-lookup"><span data-stu-id="5c348-104">A large working set (memory) due to buffering by the serialization engine.</span></span>  
  
2.  <span data-ttu-id="5c348-105">Długi przepustowości z powodu inflacji procent 33 po związanych z kodowaniem Base64.</span><span class="sxs-lookup"><span data-stu-id="5c348-105">Inordinate bandwidth consumption due to 33 percent inflation after Base64 encoding.</span></span>  
  
 <span data-ttu-id="5c348-106">Aby rozwiązać te problemy, zaimplementuj <xref:System.Xml.Serialization.IXmlSerializable> interfejsu do sterowania serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="5c348-106">To solve these problems, implement the <xref:System.Xml.Serialization.IXmlSerializable> interface to control the serialization and deserialization.</span></span> <span data-ttu-id="5c348-107">W szczególności zaimplementować <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> i <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metody bryłkach danych.</span><span class="sxs-lookup"><span data-stu-id="5c348-107">Specifically, implement the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> and <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> methods to chunk the data.</span></span>  
  
### <a name="to-implement-server-side-chunking"></a><span data-ttu-id="5c348-108">Aby zaimplementować podziału po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="5c348-108">To implement server-side chunking</span></span>  
  
1.  <span data-ttu-id="5c348-109">Na komputerze z serwerem, metody sieci Web należy wyłączyć buforowanie ASP.NET i zwracany typ, który implementuje <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="5c348-109">On the server machine, the Web method must turn off ASP.NET buffering and return a type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
2.  <span data-ttu-id="5c348-110">Typ, który implementuje <xref:System.Xml.Serialization.IXmlSerializable> chunks dane w <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5c348-110">The type that implements <xref:System.Xml.Serialization.IXmlSerializable> chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
### <a name="to-implement-client-side-processing"></a><span data-ttu-id="5c348-111">Aby zaimplementować przetwarzania po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="5c348-111">To implement client-side processing</span></span>  
  
1.  <span data-ttu-id="5c348-112">Metoda sieci Web na serwerze proxy klienta, aby zwracany typ, który implementuje ALTER <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="5c348-112">Alter the Web method on the client proxy to return the type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="5c348-113">Można użyć <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> aby zrobić to automatycznie, ale to nie jest widoczne w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="5c348-113">You can use a <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> to do this automatically, but this isn't shown here.</span></span>  
  
2.  <span data-ttu-id="5c348-114">Implementowanie <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metody odczytać podzielony danych strumienia i zapisać bajtów na dysku.</span><span class="sxs-lookup"><span data-stu-id="5c348-114">Implement the <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> method to read the chunked data stream and write the bytes to disk.</span></span> <span data-ttu-id="5c348-115">Ta implementacja wywołuje również zdarzenia postępu, które mogą być używane przez formant graficznych, takich jak pasek postępu.</span><span class="sxs-lookup"><span data-stu-id="5c348-115">This implementation also raises progress events that can be used by a graphic control, such as a progress bar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c348-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c348-116">Example</span></span>  
<span data-ttu-id="5c348-117">Poniższy przykład kodu pokazuje metody sieci Web na komputerze klienckim, który powoduje wyłączenie buforowania platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5c348-117">The following code example shows the Web method on the client that turns off ASP.NET buffering.</span></span> <span data-ttu-id="5c348-118">Przedstawiono również implementacja po stronie klienta <xref:System.Xml.Serialization.IXmlSerializable> interfejs, który chunks dane w <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5c348-118">It also shows the client-side implementation of the <xref:System.Xml.Serialization.IXmlSerializable> interface that chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)]
[!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)]
[!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)]
[!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5c348-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5c348-119">Compiling the code</span></span>  
  
-   <span data-ttu-id="5c348-120">W kodzie za pomocą następujących przestrzeni nazw: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, i <xref:System.Xml.Schema>.</span><span class="sxs-lookup"><span data-stu-id="5c348-120">The code uses the following namespaces: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, and <xref:System.Xml.Schema>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c348-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c348-121">See also</span></span>  
 [<span data-ttu-id="5c348-122">Niestandardowej serializacji</span><span class="sxs-lookup"><span data-stu-id="5c348-122">Custom Serialization</span></span>](custom-serialization.md)