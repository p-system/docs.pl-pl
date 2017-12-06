---
title: "Dane struktury usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a2c8ddc-4e82-4e7f-a79f-97085c469517
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a7c20da9f4eafa615ff23bad4d78e669a8417464
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="service-framework-data"></a><span data-ttu-id="ed609-102">Dane struktury usługi</span><span class="sxs-lookup"><span data-stu-id="ed609-102">Service Framework Data</span></span>
<span data-ttu-id="ed609-103">W tym temacie wymieniono wszystkie wyjątki generowane przez dane struktury usługi.</span><span class="sxs-lookup"><span data-stu-id="ed609-103">This topic lists all exceptions generated by Service Framework Data.</span></span>  
  
## <a name="exception-list"></a><span data-ttu-id="ed609-104">Listy wyjątków</span><span class="sxs-lookup"><span data-stu-id="ed609-104">Exception List</span></span>  
  
|<span data-ttu-id="ed609-105">Kod zasobu</span><span class="sxs-lookup"><span data-stu-id="ed609-105">Resource Code</span></span>|<span data-ttu-id="ed609-106">Ciąg zasobu</span><span class="sxs-lookup"><span data-stu-id="ed609-106">Resource String</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="ed609-107">AddressingExtensionInBadNS</span><span class="sxs-lookup"><span data-stu-id="ed609-107">AddressingExtensionInBadNS</span></span>|<span data-ttu-id="ed609-108">Określony element w określonej przestrzeni nazw jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="ed609-108">The specified element in the specified namespace is not valid.</span></span> <span data-ttu-id="ed609-109">Oznacza to, że określony element jest zduplikowany element lub że nie jest nielegalnym rozszerzeniem ponieważ elementów rozszerzeń nie może być w przestrzeni nazw adresowania.</span><span class="sxs-lookup"><span data-stu-id="ed609-109">This means that the specified element is a duplicate element or that it is not a legal extension because extension elements cannot be in the addressing namespace.</span></span>|  
|<span data-ttu-id="ed609-110">BinaryEncoderSessionInvalid</span><span class="sxs-lookup"><span data-stu-id="ed609-110">BinaryEncoderSessionInvalid</span></span>|<span data-ttu-id="ed609-111">Sesja kodera binarnego jest nieprawidłowa, ponieważ wystąpił błąd podczas dekodowania poprzedniego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="ed609-111">The binary encoder session is not valid because there was an error decoding a previous message.</span></span>|  
|<span data-ttu-id="ed609-112">CannotDetectAddressingVersion</span><span class="sxs-lookup"><span data-stu-id="ed609-112">CannotDetectAddressingVersion</span></span>|<span data-ttu-id="ed609-113">Nie można wykryć wersji WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="ed609-113">Cannot detect WS-Addressing version.</span></span> <span data-ttu-id="ed609-114">EndpointAddress nie rozpoczyna się od elementu.</span><span class="sxs-lookup"><span data-stu-id="ed609-114">EndpointAddress does not start with an element.</span></span>|  
|<span data-ttu-id="ed609-115">CouldNotFindNamespaceForPrefix</span><span class="sxs-lookup"><span data-stu-id="ed609-115">CouldNotFindNamespaceForPrefix</span></span>|<span data-ttu-id="ed609-116">Określony prefiks nie zawiera żadnego wiązania przestrzeni nazw w zakresie.</span><span class="sxs-lookup"><span data-stu-id="ed609-116">The specified prefix has no namespace binding in scope.</span></span>|  
|<span data-ttu-id="ed609-117">EncoderBadContentType</span><span class="sxs-lookup"><span data-stu-id="ed609-117">EncoderBadContentType</span></span>|<span data-ttu-id="ed609-118">Nie można przetworzyć do contentType.</span><span class="sxs-lookup"><span data-stu-id="ed609-118">Cannot process to contentType.</span></span>|  
|<span data-ttu-id="ed609-119">EncoderEnvelopeVersionMismatch</span><span class="sxs-lookup"><span data-stu-id="ed609-119">EncoderEnvelopeVersionMismatch</span></span>|<span data-ttu-id="ed609-120">Wersja schematu envelope określony komunikat przychodzący nie jest zgodna wskazanego kodera.</span><span class="sxs-lookup"><span data-stu-id="ed609-120">The envelope version of the specified incoming message does not match the specified encoder.</span></span> <span data-ttu-id="ed609-121">Upewnij się, że powiązanie jest skonfigurowane przy użyciu tej samej wersji, co oczekiwane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="ed609-121">Make sure the binding is configured with the same version as the expected messages.</span></span>|  
|<span data-ttu-id="ed609-122">EncoderMessageVersionMismatch</span><span class="sxs-lookup"><span data-stu-id="ed609-122">EncoderMessageVersionMismatch</span></span>|<span data-ttu-id="ed609-123">Wersja określonego komunikatu wychodzącego jest niezgodny z określonym kodera.</span><span class="sxs-lookup"><span data-stu-id="ed609-123">The message version of the specified outgoing message does not match the specified encoder.</span></span> <span data-ttu-id="ed609-124">Upewnij się, że powiązanie jest skonfigurowane z tej samej wersji, co komunikat.</span><span class="sxs-lookup"><span data-stu-id="ed609-124">Make sure the binding is configured with the same version as the message.</span></span>|  
|<span data-ttu-id="ed609-125">ExtraContentIsPresentInFaultDetail</span><span class="sxs-lookup"><span data-stu-id="ed609-125">ExtraContentIsPresentInFaultDetail</span></span>|<span data-ttu-id="ed609-126">Dodatkowa zawartość Extensible Markup Language znajduje się w błędnym elemencie szczegółowym.</span><span class="sxs-lookup"><span data-stu-id="ed609-126">Additional Extensible Markup Language content is present in the fault detail element.</span></span> <span data-ttu-id="ed609-127">Dozwolone jest tylko jeden element.</span><span class="sxs-lookup"><span data-stu-id="ed609-127">Only one element is allowed.</span></span>|  
|<span data-ttu-id="ed609-128">FilterBadTableType</span><span class="sxs-lookup"><span data-stu-id="ed609-128">FilterBadTableType</span></span>|<span data-ttu-id="ed609-129">Obiekt IMessageFilterTable utworzony dla elementu Filter nie może być obiektem lub typ pochodzący od obiektu MessageFilterTable.</span><span class="sxs-lookup"><span data-stu-id="ed609-129">The IMessageFilterTable created for a Filter cannot be a MessageFilterTable or derived from MessageFilterTable.</span></span>|  
|<span data-ttu-id="ed609-130">FilterTableInvalidForLookup</span><span class="sxs-lookup"><span data-stu-id="ed609-130">FilterTableInvalidForLookup</span></span>|<span data-ttu-id="ed609-131">Obiekt MessageFilterTable jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="ed609-131">The MessageFilterTable state is corrupt.</span></span> <span data-ttu-id="ed609-132">Nie można wykonać żądanego wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="ed609-132">The requested search cannot be performed.</span></span>|  
|<span data-ttu-id="ed609-133">MandatoryHeaderNotUnderstood</span><span class="sxs-lookup"><span data-stu-id="ed609-133">MandatoryHeaderNotUnderstood</span></span>|<span data-ttu-id="ed609-134">Co najmniej jednego wymaganego są niezrozumiałe bloków nagłówków protokołu dostępu prostego obiektu.</span><span class="sxs-lookup"><span data-stu-id="ed609-134">One or more required simple object access protocol header blocks were not understood.</span></span>|  
|<span data-ttu-id="ed609-135">MessageBodyIsStream</span><span class="sxs-lookup"><span data-stu-id="ed609-135">MessageBodyIsStream</span></span>|<span data-ttu-id="ed609-136">Treść komunikatu jest typu stream.</span><span class="sxs-lookup"><span data-stu-id="ed609-136">The message body is a stream.</span></span>|  
|<span data-ttu-id="ed609-137">MessageBodyIsUnknown</span><span class="sxs-lookup"><span data-stu-id="ed609-137">MessageBodyIsUnknown</span></span>|<span data-ttu-id="ed609-138">Format treści wiadomości jest nieznany.</span><span class="sxs-lookup"><span data-stu-id="ed609-138">The format of the message body is unknown.</span></span>|  
|<span data-ttu-id="ed609-139">MessageBodyReaderInvalidReadState</span><span class="sxs-lookup"><span data-stu-id="ed609-139">MessageBodyReaderInvalidReadState</span></span>|<span data-ttu-id="ed609-140">Określony ReadState czytnika treść wiadomości nie mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="ed609-140">The specified ReadState of the message body reader cannot be consumed.</span></span>|  
|<span data-ttu-id="ed609-141">MessageTextEncodingNotSupported</span><span class="sxs-lookup"><span data-stu-id="ed609-141">MessageTextEncodingNotSupported</span></span>|<span data-ttu-id="ed609-142">Kodowanie określony tekst, który jest używany w formacie wiadomości tekstowej nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ed609-142">The specified text encoding that is used in the text message format is not supported.</span></span>|  
|<span data-ttu-id="ed609-143">MissingMessageID</span><span class="sxs-lookup"><span data-stu-id="ed609-143">MissingMessageID</span></span>|<span data-ttu-id="ed609-144">Żądanie wiadomości Brak nagłówka MessageID.</span><span class="sxs-lookup"><span data-stu-id="ed609-144">Request Message is missing a MessageID header.</span></span> <span data-ttu-id="ed609-145">Nagłówka MessageID jest wymagany do dopasowania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="ed609-145">A MessageID header is required to correlate a reply.</span></span>|  
|<span data-ttu-id="ed609-146">MultipleMessageHeaders</span><span class="sxs-lookup"><span data-stu-id="ed609-146">MultipleMessageHeaders</span></span>|<span data-ttu-id="ed609-147">Znaleziono więcej niż jeden nagłówek o określonej nazwie i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ed609-147">More than one header with the specified name and namespace were found.</span></span>|  
|<span data-ttu-id="ed609-148">MultipleMessageHeadersWithActor</span><span class="sxs-lookup"><span data-stu-id="ed609-148">MultipleMessageHeadersWithActor</span></span>|<span data-ttu-id="ed609-149">Znaleziono więcej niż jeden nagłówek o określonej nazwie, przestrzeni nazw i roli.</span><span class="sxs-lookup"><span data-stu-id="ed609-149">More than one header with the specified name, namespace and role were found.</span></span>|  
|<span data-ttu-id="ed609-150">MultipleRelatesToHeaders</span><span class="sxs-lookup"><span data-stu-id="ed609-150">MultipleRelatesToHeaders</span></span>|<span data-ttu-id="ed609-151">Znaleziono więcej niż jeden nagłówka RelatesTo z określonej relacji.</span><span class="sxs-lookup"><span data-stu-id="ed609-151">More than one RelatesTo header with the specified relationship were found.</span></span> <span data-ttu-id="ed609-152">Dla każdej relacji jest dozwolony tylko jeden.</span><span class="sxs-lookup"><span data-stu-id="ed609-152">Only one is allowed for each relationship.</span></span>|  
|<span data-ttu-id="ed609-153">QueryFunctionTypeNotSupported</span><span class="sxs-lookup"><span data-stu-id="ed609-153">QueryFunctionTypeNotSupported</span></span>|<span data-ttu-id="ed609-154">Określony zwracany typ funkcji IXsltContextFunction nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ed609-154">The specified return type for the IXsltContextFunction is not supported.</span></span>|  
|<span data-ttu-id="ed609-155">QueryIteratorOutOfScope</span><span class="sxs-lookup"><span data-stu-id="ed609-155">QueryIteratorOutOfScope</span></span>|<span data-ttu-id="ed609-156">Element XPathNodeIterator został unieważniony.</span><span class="sxs-lookup"><span data-stu-id="ed609-156">The XPathNodeIterator has been invalidated.</span></span> <span data-ttu-id="ed609-157">Elementy XPathNodeIterators przekazywane jako argumenty do elementów IXsltContextFunctions są prawidłowe tylko w funkcji.</span><span class="sxs-lookup"><span data-stu-id="ed609-157">XPathNodeIterators that are passed as arguments to IXsltContextFunctions are only valid within the function.</span></span> <span data-ttu-id="ed609-158">Nie może być w pamięci podręcznej do późniejszego użycia ani zwracane przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="ed609-158">They cannot be cached for later use or returned by the function.</span></span>|  
|<span data-ttu-id="ed609-159">QueryVariableNull</span><span class="sxs-lookup"><span data-stu-id="ed609-159">QueryVariableNull</span></span>|<span data-ttu-id="ed609-160">Metody IXsltContextVariable nie może zwracać wartości null.</span><span class="sxs-lookup"><span data-stu-id="ed609-160">IXsltContextVariable methods cannot return null.</span></span>|  
|<span data-ttu-id="ed609-161">QueryVariableTypeNotSupported</span><span class="sxs-lookup"><span data-stu-id="ed609-161">QueryVariableTypeNotSupported</span></span>|<span data-ttu-id="ed609-162">Określony IXsltContextVariable, typu pochodnego nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="ed609-162">The specified IXsltContextVariable derived type is not supported.</span></span>|  
|<span data-ttu-id="ed609-163">ReceiveShutdownReturnedMessage</span><span class="sxs-lookup"><span data-stu-id="ed609-163">ReceiveShutdownReturnedMessage</span></span>|<span data-ttu-id="ed609-164">Kanał odebrał nieoczekiwany komunikat wejściowy o określonej akcji podczas zamykania.</span><span class="sxs-lookup"><span data-stu-id="ed609-164">The channel received an unexpected input message with the specified Action while closing.</span></span> <span data-ttu-id="ed609-165">Zamknij kanał, gdy żadne komunikaty wejściowe nie są oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="ed609-165">Close the channel when you are not expecting any more input messages.</span></span>|  
|<span data-ttu-id="ed609-166">XmlBufferInInvalidState</span><span class="sxs-lookup"><span data-stu-id="ed609-166">XmlBufferInInvalidState</span></span>|<span data-ttu-id="ed609-167">Wystąpił błąd wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="ed609-167">An internal error has occurred.</span></span> <span data-ttu-id="ed609-168">Nie można wykonać operacji z powodu stan buforu XML.</span><span class="sxs-lookup"><span data-stu-id="ed609-168">The operation cannot be performed because of the state of the XML buffer.</span></span>|  
|<span data-ttu-id="ed609-169">XmlBufferQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="ed609-169">XmlBufferQuotaExceeded</span></span>|<span data-ttu-id="ed609-170">Rozmiar wymagany do buforowania zawartości Extensible Markup Language przekracza limit przydziału buforu.</span><span class="sxs-lookup"><span data-stu-id="ed609-170">The size necessary to buffer the Extensible Markup Language content exceeded the buffer quota.</span></span>|