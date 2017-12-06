---
title: "Włączanie przepływu transakcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transactions [WCF], enabling flow
ms.assetid: a03f5041-5049-43f4-897c-e0292d4718f7
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b5d0b90ed28928e734089265cb8c58839b6d0cd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="enabling-transaction-flow"></a><span data-ttu-id="585a1-102">Włączanie przepływu transakcji</span><span class="sxs-lookup"><span data-stu-id="585a1-102">Enabling Transaction Flow</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="585a1-103">zapewnia bardzo elastyczne opcje kontroli przepływu transakcji.</span><span class="sxs-lookup"><span data-stu-id="585a1-103"> provides highly flexible options for controlling transaction flow.</span></span> <span data-ttu-id="585a1-104">Ustawienia przepływu transakcji usługi można wyrazić przy użyciu kombinacji atrybutów i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="585a1-104">A service's transaction flow settings can be expressed using a combination of attributes and configuration.</span></span>  
  
## <a name="transaction-flow-settings"></a><span data-ttu-id="585a1-105">Ustawienia przepływu transakcji</span><span class="sxs-lookup"><span data-stu-id="585a1-105">Transaction Flow Settings</span></span>  
 <span data-ttu-id="585a1-106">Ustawienia przepływu transakcji są generowane dla punktu końcowego wyniku przecięcia trzech następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="585a1-106">Transaction flow settings are generated for a service endpoint as a result of the intersection of the following three values:</span></span>  
  
-   <span data-ttu-id="585a1-107"><xref:System.ServiceModel.TransactionFlowAttribute> Atrybutu dla każdej metody w kontrakcie usługi określono.</span><span class="sxs-lookup"><span data-stu-id="585a1-107">The <xref:System.ServiceModel.TransactionFlowAttribute> attribute specified for each method in the service contract.</span></span>  
  
-   <span data-ttu-id="585a1-108">`TransactionFlow` Właściwości binding określone powiązanie.</span><span class="sxs-lookup"><span data-stu-id="585a1-108">The `TransactionFlow` binding property in the specific binding.</span></span>  
  
-   <span data-ttu-id="585a1-109">`TransactionFlowProtocol` Właściwości binding określone powiązanie.</span><span class="sxs-lookup"><span data-stu-id="585a1-109">The `TransactionFlowProtocol` binding property in the specific binding.</span></span> <span data-ttu-id="585a1-110">`TransactionFlowProtocol` Właściwości binding pozwala wybrać jeden z dwóch protokołów innej transakcji, czy służy do uruchomienia przepływu transakcji.</span><span class="sxs-lookup"><span data-stu-id="585a1-110">The `TransactionFlowProtocol` binding property enables you to choose among two different transaction protocols that you can use to flow a transaction.</span></span> <span data-ttu-id="585a1-111">W poniższych sekcjach opisano krótko każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="585a1-111">The following sections briefly describe each of them.</span></span>  
  
### <a name="ws-atomictransaction-protocol"></a><span data-ttu-id="585a1-112">Protokół WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="585a1-112">WS-AtomicTransaction Protocol</span></span>  
 <span data-ttu-id="585a1-113">Protokół WS-AtomicTransaction (WS-AT) jest przydatne w scenariuszach, gdy wymagane jest współdziałanie z stosy protokołu innych firm.</span><span class="sxs-lookup"><span data-stu-id="585a1-113">The WS-AtomicTransaction (WS-AT) protocol is useful for scenarios when interoperability with third-party protocol stacks is required.</span></span>  
  
### <a name="oletransactions-protocol"></a><span data-ttu-id="585a1-114">Protokołu OleTransactions</span><span class="sxs-lookup"><span data-stu-id="585a1-114">OleTransactions Protocol</span></span>  
 <span data-ttu-id="585a1-115">Protokołu OleTransactions jest przydatne w scenariuszach, po współdziałanie z stosy protokołu innych firm nie jest wymagane, a narzędzie wdrażania usługi z wyprzedzeniem wie, że Usługa protokołu WS-AT jest wyłączona lokalnie lub nie istniejących topologii sieci Preferuj nie użycia protokołu WS-AT.</span><span class="sxs-lookup"><span data-stu-id="585a1-115">The OleTransactions protocol is useful for scenarios when interoperability with third-party protocol stacks is not required, and the deployer of a service knows in advance that the WS-AT protocol service is disabled locally or the existing network topology does not favor the usage of WS-AT.</span></span>  
  
 <span data-ttu-id="585a1-116">W poniższej tabeli przedstawiono różne typy przepływy transakcji, które mogą być generowane przy użyciu tych różnych kombinacji.</span><span class="sxs-lookup"><span data-stu-id="585a1-116">The following table shows the different types of transaction flows that can be generated using these various combinations.</span></span>  
  
|<span data-ttu-id="585a1-117">TransactionFlow</span><span class="sxs-lookup"><span data-stu-id="585a1-117">TransactionFlow</span></span><br /><br /> <span data-ttu-id="585a1-118">powiązanie</span><span class="sxs-lookup"><span data-stu-id="585a1-118">binding</span></span>|<span data-ttu-id="585a1-119">Właściwość powiązania TransactionFlow</span><span class="sxs-lookup"><span data-stu-id="585a1-119">TransactionFlow binding property</span></span>|<span data-ttu-id="585a1-120">Protokół powiązania TransactionFlowProtocol</span><span class="sxs-lookup"><span data-stu-id="585a1-120">TransactionFlowProtocol binding protocol</span></span>|<span data-ttu-id="585a1-121">Typ przepływu transakcji</span><span class="sxs-lookup"><span data-stu-id="585a1-121">Type of transaction flow</span></span>|  
|---------------------------------|--------------------------------------|----------------------------------------------|------------------------------|  
|<span data-ttu-id="585a1-122">Obowiązkowy</span><span class="sxs-lookup"><span data-stu-id="585a1-122">Mandatory</span></span>|<span data-ttu-id="585a1-123">true</span><span class="sxs-lookup"><span data-stu-id="585a1-123">true</span></span>|<span data-ttu-id="585a1-124">WS-AT.</span><span class="sxs-lookup"><span data-stu-id="585a1-124">WS-AT</span></span>|<span data-ttu-id="585a1-125">Transakcja musi przepływ interoperacyjne format WS-AT.</span><span class="sxs-lookup"><span data-stu-id="585a1-125">Transaction must be flowed in the interoperable WS-AT format.</span></span>|  
|<span data-ttu-id="585a1-126">Obowiązkowy</span><span class="sxs-lookup"><span data-stu-id="585a1-126">Mandatory</span></span>|<span data-ttu-id="585a1-127">true</span><span class="sxs-lookup"><span data-stu-id="585a1-127">true</span></span>|<span data-ttu-id="585a1-128">OleTransactions</span><span class="sxs-lookup"><span data-stu-id="585a1-128">OleTransactions</span></span>|<span data-ttu-id="585a1-129">Transakcji musi być umieszczane w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] OleTransactions formatu.</span><span class="sxs-lookup"><span data-stu-id="585a1-129">Transaction must be flowed in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] OleTransactions format.</span></span>|  
|<span data-ttu-id="585a1-130">Obowiązkowy</span><span class="sxs-lookup"><span data-stu-id="585a1-130">Mandatory</span></span>|<span data-ttu-id="585a1-131">false</span><span class="sxs-lookup"><span data-stu-id="585a1-131">false</span></span>|<span data-ttu-id="585a1-132">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="585a1-132">Not applicable</span></span>|<span data-ttu-id="585a1-133">Nie dotyczy, ponieważ jest to nieprawidłowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="585a1-133">Not applicable because this is an invalid configuration.</span></span>|  
|<span data-ttu-id="585a1-134">Dozwolone</span><span class="sxs-lookup"><span data-stu-id="585a1-134">Allowed</span></span>|<span data-ttu-id="585a1-135">true</span><span class="sxs-lookup"><span data-stu-id="585a1-135">true</span></span>|<span data-ttu-id="585a1-136">WS-AT.</span><span class="sxs-lookup"><span data-stu-id="585a1-136">WS-AT</span></span>|<span data-ttu-id="585a1-137">Transakcja może przepływ interoperacyjne format WS-AT.</span><span class="sxs-lookup"><span data-stu-id="585a1-137">Transaction may be flowed in the interoperable WS-AT format.</span></span>|  
|<span data-ttu-id="585a1-138">Dozwolone</span><span class="sxs-lookup"><span data-stu-id="585a1-138">Allowed</span></span>|<span data-ttu-id="585a1-139">true</span><span class="sxs-lookup"><span data-stu-id="585a1-139">true</span></span>|<span data-ttu-id="585a1-140">OleTransactions</span><span class="sxs-lookup"><span data-stu-id="585a1-140">OleTransactions</span></span>|<span data-ttu-id="585a1-141">Transakcja może przepływ w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] OleTransactions formatu.</span><span class="sxs-lookup"><span data-stu-id="585a1-141">Transaction may be flowed in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] OleTransactions format.</span></span>|  
|<span data-ttu-id="585a1-142">Dozwolone</span><span class="sxs-lookup"><span data-stu-id="585a1-142">Allowed</span></span>|<span data-ttu-id="585a1-143">false</span><span class="sxs-lookup"><span data-stu-id="585a1-143">false</span></span>|<span data-ttu-id="585a1-144">Dowolna wartość</span><span class="sxs-lookup"><span data-stu-id="585a1-144">Any value</span></span>|<span data-ttu-id="585a1-145">Transakcja nie jest umieszczane.</span><span class="sxs-lookup"><span data-stu-id="585a1-145">A transaction is not flowed.</span></span>|  
|<span data-ttu-id="585a1-146">NotAllowed</span><span class="sxs-lookup"><span data-stu-id="585a1-146">NotAllowed</span></span>|<span data-ttu-id="585a1-147">Dowolna wartość</span><span class="sxs-lookup"><span data-stu-id="585a1-147">Any value</span></span>|<span data-ttu-id="585a1-148">Dowolna wartość</span><span class="sxs-lookup"><span data-stu-id="585a1-148">Any value</span></span>|<span data-ttu-id="585a1-149">Transakcja nie jest umieszczane.</span><span class="sxs-lookup"><span data-stu-id="585a1-149">A transaction is not flowed.</span></span>|  
  
 <span data-ttu-id="585a1-150">Poniższa tabela zawiera podsumowanie wyników przetwarzania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="585a1-150">The following table summarizes the message processing result.</span></span>  
  
|<span data-ttu-id="585a1-151">Komunikat przychodzący</span><span class="sxs-lookup"><span data-stu-id="585a1-151">Incoming message</span></span>|<span data-ttu-id="585a1-152">Ustawienie TransactionFlow</span><span class="sxs-lookup"><span data-stu-id="585a1-152">TransactionFlow setting</span></span>|<span data-ttu-id="585a1-153">Nagłówek transakcji</span><span class="sxs-lookup"><span data-stu-id="585a1-153">Transaction header</span></span>|<span data-ttu-id="585a1-154">Wynik przetwarzania komunikatu</span><span class="sxs-lookup"><span data-stu-id="585a1-154">Message processing result</span></span>|  
|----------------------|-----------------------------|------------------------|-------------------------------|  
|<span data-ttu-id="585a1-155">Protokół oczekiwany format jest zgodny transakcji</span><span class="sxs-lookup"><span data-stu-id="585a1-155">Transaction matches expected protocol format</span></span>|<span data-ttu-id="585a1-156">Dozwolone lub obowiązkowego</span><span class="sxs-lookup"><span data-stu-id="585a1-156">Allowed or Mandatory</span></span>|<span data-ttu-id="585a1-157">`MustUnderstand`Equals `true`.</span><span class="sxs-lookup"><span data-stu-id="585a1-157">`MustUnderstand` equals `true`.</span></span>|<span data-ttu-id="585a1-158">Proces</span><span class="sxs-lookup"><span data-stu-id="585a1-158">Process</span></span>|  
|<span data-ttu-id="585a1-159">Transakcja nie jest zgodny z formatem oczekiwanym protokołu</span><span class="sxs-lookup"><span data-stu-id="585a1-159">Transaction does not match expected protocol format</span></span>|<span data-ttu-id="585a1-160">Obowiązkowy</span><span class="sxs-lookup"><span data-stu-id="585a1-160">Mandatory</span></span>|<span data-ttu-id="585a1-161">`MustUnderstand`Equals `false`.</span><span class="sxs-lookup"><span data-stu-id="585a1-161">`MustUnderstand` equals `false`.</span></span>|<span data-ttu-id="585a1-162">Odrzucone, ponieważ wymagana jest transakcja</span><span class="sxs-lookup"><span data-stu-id="585a1-162">Rejected because a transaction is required</span></span>|  
|<span data-ttu-id="585a1-163">Transakcja nie jest zgodny z formatem oczekiwanym protokołu</span><span class="sxs-lookup"><span data-stu-id="585a1-163">Transaction does not match expected protocol format</span></span>|<span data-ttu-id="585a1-164">Dozwolone</span><span class="sxs-lookup"><span data-stu-id="585a1-164">Allowed</span></span>|<span data-ttu-id="585a1-165">`MustUnderstand`Equals `false`.</span><span class="sxs-lookup"><span data-stu-id="585a1-165">`MustUnderstand` equals `false`.</span></span>|<span data-ttu-id="585a1-166">Odrzucone, ponieważ nagłówek jest niezrozumiały.</span><span class="sxs-lookup"><span data-stu-id="585a1-166">Rejected because the header is not understood</span></span>|  
|<span data-ttu-id="585a1-167">Transakcja formacie protokołu</span><span class="sxs-lookup"><span data-stu-id="585a1-167">Transaction using any protocol format</span></span>|<span data-ttu-id="585a1-168">NotAllowed</span><span class="sxs-lookup"><span data-stu-id="585a1-168">NotAllowed</span></span>|<span data-ttu-id="585a1-169">`MustUnderstand`Equals `false`.</span><span class="sxs-lookup"><span data-stu-id="585a1-169">`MustUnderstand` equals `false`.</span></span>|<span data-ttu-id="585a1-170">Odrzucone, ponieważ nagłówek jest niezrozumiały.</span><span class="sxs-lookup"><span data-stu-id="585a1-170">Rejected because the header is not understood</span></span>|  
|<span data-ttu-id="585a1-171">Brak transakcji</span><span class="sxs-lookup"><span data-stu-id="585a1-171">No transaction</span></span>|<span data-ttu-id="585a1-172">Obowiązkowy</span><span class="sxs-lookup"><span data-stu-id="585a1-172">Mandatory</span></span>|<span data-ttu-id="585a1-173">Brak</span><span class="sxs-lookup"><span data-stu-id="585a1-173">N/A</span></span>|<span data-ttu-id="585a1-174">Odrzucone, ponieważ wymagana jest transakcja</span><span class="sxs-lookup"><span data-stu-id="585a1-174">Rejected because a transaction is required</span></span>|  
|<span data-ttu-id="585a1-175">Brak transakcji</span><span class="sxs-lookup"><span data-stu-id="585a1-175">No transaction</span></span>|<span data-ttu-id="585a1-176">Dozwolone</span><span class="sxs-lookup"><span data-stu-id="585a1-176">Allowed</span></span>|<span data-ttu-id="585a1-177">Brak</span><span class="sxs-lookup"><span data-stu-id="585a1-177">N/A</span></span>|<span data-ttu-id="585a1-178">Proces</span><span class="sxs-lookup"><span data-stu-id="585a1-178">Process</span></span>|  
|<span data-ttu-id="585a1-179">Brak transakcji</span><span class="sxs-lookup"><span data-stu-id="585a1-179">No transaction</span></span>|<span data-ttu-id="585a1-180">NotAllowed</span><span class="sxs-lookup"><span data-stu-id="585a1-180">NotAllowed</span></span>|<span data-ttu-id="585a1-181">Brak</span><span class="sxs-lookup"><span data-stu-id="585a1-181">N/A</span></span>|<span data-ttu-id="585a1-182">Proces</span><span class="sxs-lookup"><span data-stu-id="585a1-182">Process</span></span>|  
  
 <span data-ttu-id="585a1-183">Podczas każdej metody na kontrakt mogą mieć wymagania przepływu innej transakcji, obejmuje ustawienia protokołu przepływ transakcji na poziomie powiązania.</span><span class="sxs-lookup"><span data-stu-id="585a1-183">While each method on a contract can have different transaction flow requirements, the transaction flow protocol setting is scoped at the level of the binding.</span></span> <span data-ttu-id="585a1-184">Oznacza to, że wszystkie metody, które współużytkują tego samego punktu końcowego (i w związku z tym to samo powiązanie) również udostępniać te same zasady, umożliwiając lub wymagających przepływu transakcji, jak również ten sam protokół transakcji, jeśli ma to zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="585a1-184">This means that all methods that share the same endpoint (and therefore the same binding) also share the same policy allowing or requiring transaction flow, as well as the same transaction protocol if applicable.</span></span>  
  
## <a name="enabling-transaction-flow-at-the-method-level"></a><span data-ttu-id="585a1-185">Włączanie przepływu transakcji na poziomie — metoda</span><span class="sxs-lookup"><span data-stu-id="585a1-185">Enabling Transaction Flow at the Method Level</span></span>  
 <span data-ttu-id="585a1-186">Wymagania dotyczące przepływu transakcji nie zawsze są takie same dla wszystkich metod w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="585a1-186">Transaction flow requirements are not always the same for all methods in a service contract.</span></span> <span data-ttu-id="585a1-187">W związku z tym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] również zapewnia mechanizm opartych na atrybutach umożliwia wyrażane preferencji przepływu transakcji każdej metody.</span><span class="sxs-lookup"><span data-stu-id="585a1-187">Therefore, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] also provides an attribute-based mechanism to allow each method's transaction flow preferences to be expressed.</span></span> <span data-ttu-id="585a1-188">Jest to osiągane przez <xref:System.ServiceModel.TransactionFlowAttribute> , który określa poziom, w którym operacji usługi akceptuje Nagłówek transakcji.</span><span class="sxs-lookup"><span data-stu-id="585a1-188">This is achieved by the <xref:System.ServiceModel.TransactionFlowAttribute> that specifies the level in which a service operation accepts a transaction header.</span></span> <span data-ttu-id="585a1-189">Należy oznaczyć metody kontraktu usługi z tym atrybutem, jeśli chcesz włączyć przepływu transakcji.</span><span class="sxs-lookup"><span data-stu-id="585a1-189">You should mark your service contract methods with this attribute if you want to enable transaction flow.</span></span> <span data-ttu-id="585a1-190">Ten atrybut ma jedną z wartości <xref:System.ServiceModel.TransactionFlowOption> wyliczenia, w którym wartość domyślna to <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.</span><span class="sxs-lookup"><span data-stu-id="585a1-190">This attribute takes one of the values of the <xref:System.ServiceModel.TransactionFlowOption> enumeration, in which the default value is <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.</span></span> <span data-ttu-id="585a1-191">Jeśli wszystkie wartości z wyjątkiem <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> jest określona metoda jest wymagana będzie jednokierunkowe.</span><span class="sxs-lookup"><span data-stu-id="585a1-191">If any value except <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> is specified, the method is required to not be one-way.</span></span> <span data-ttu-id="585a1-192">Projektant można użyć tego atrybutu, aby określić wymagania dotyczące przepływu transakcji poziomie metody lub ograniczenia w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="585a1-192">A developer can use this attribute to specify method-level transaction flow requirements or constraints at design time.</span></span>  
  
## <a name="enabling-transaction-flow-at-the-endpoint-level"></a><span data-ttu-id="585a1-193">Włączanie przepływu transakcji na poziomie punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="585a1-193">Enabling Transaction Flow at the Endpoint Level</span></span>  
 <span data-ttu-id="585a1-194">Oprócz ustawienia przepływ transakcji na poziomie metody <xref:System.ServiceModel.TransactionFlowAttribute> zawiera atrybut, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zawiera ustawienia dla punktu końcowego dla przepływu transakcji umożliwia administratorom przepływ transakcji na wyższym poziomie.</span><span class="sxs-lookup"><span data-stu-id="585a1-194">In addition to the method-level transaction flow setting  the <xref:System.ServiceModel.TransactionFlowAttribute> attribute provides, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides an endpoint-wide setting for transaction flow to allow administrators to control transaction flow at a higher level.</span></span>  
  
 <span data-ttu-id="585a1-195">Jest to osiągane przez <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, co umożliwia włączanie lub wyłączanie przychodzący transakcji w punkcie końcowym powiązania ustawienia, a także określenie transakcji żądany format protokołu przychodzących transakcji.</span><span class="sxs-lookup"><span data-stu-id="585a1-195">This is achieved by the <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, which enables you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired transaction protocol format for incoming transactions.</span></span>  
  
 <span data-ttu-id="585a1-196">Jeśli powiązanie wyłączył przepływu transakcji, ale wymaga jednej z operacji na kontrakt usługi transakcji przychodzącej, podczas uruchamiania usługi jest zgłaszany wyjątek sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="585a1-196">If the binding has disabled transaction flow, but one of the operations on a service contract requires an incoming transaction, then a validation exception is thrown at service startup.</span></span>  
  
 <span data-ttu-id="585a1-197">Większość powiązań stałego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewnia zawierają `transactionFlow` i `transactionProtocol` atrybutów w celu włączenia, skonfigurowania określone powiązanie do akceptowania przychodzących transakcji.</span><span class="sxs-lookup"><span data-stu-id="585a1-197">Most of the standing bindings [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides contain the `transactionFlow` and `transactionProtocol` attributes to enable you to configure the specific binding to accept incoming transactions.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="585a1-198">Ustawianie elementów konfiguracji, zobacz [ \<powiązania >](../../../../docs/framework/misc/binding.md).</span><span class="sxs-lookup"><span data-stu-id="585a1-198"> setting the configuration elements, see [\<binding>](../../../../docs/framework/misc/binding.md).</span></span>  
  
 <span data-ttu-id="585a1-199">Administrator lub narzędzia wdrażania umożliwia przepływu transakcji poziomie punktu końcowego skonfigurować wymagania dotyczące przepływu transakcji lub ograniczenia w czasie wdrażania przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="585a1-199">An administrator or deployer can use endpoint-level transaction flow to configure transaction flow requirements or constraints at deployment time using the configuration file.</span></span>  
  
## <a name="security"></a><span data-ttu-id="585a1-200">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="585a1-200">Security</span></span>  
 <span data-ttu-id="585a1-201">Aby zapewnić bezpieczeństwo systemu i integralności, należy zabezpieczyć wymiany komunikatów podczas przepływu transakcji między aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="585a1-201">To ensure system security and integrity, you must secure message exchanges when flowing transactions between applications.</span></span> <span data-ttu-id="585a1-202">Nie należy przepływu ani ujawnić szczegóły transakcji do dowolnej aplikacji, która nie jest uprawniony do udziału w tej samej transakcji.</span><span class="sxs-lookup"><span data-stu-id="585a1-202">You should not flow or disclose transaction details to any application that is not entitled to participate in the same transaction.</span></span>  
  
 <span data-ttu-id="585a1-203">Podczas generowania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientom nieznaną lub niezaufaną usług sieci Web za pomocą wymiany metadanych, wywołania operacji na te usługi sieci Web ma pomijać bieżącą transakcję, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="585a1-203">When generating [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients to unknown or untrusted Web services through the use of metadata exchange, calls to operations on these Web services should suppress the current transaction if possible.</span></span> <span data-ttu-id="585a1-204">Poniższy przykład demonstruje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="585a1-204">The following example demonstrates how to do this.</span></span>  
  
```  
//client code which has an ambient transaction  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Suppress))  
{  
    // No transaction will flow to this operation  
    untrustedProxy.Operation1(...);  
    scope.Complete();  
}  
//remainder of client code  
```  
  
 <span data-ttu-id="585a1-205">Ponadto należy skonfigurować usług do akceptowania przychodzących transakcji tylko od klientów, którzy mają one uwierzytelnieniu i autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="585a1-205">In addition, services should be configured to accept incoming transactions only from clients that they have authenticated and authorized.</span></span> <span data-ttu-id="585a1-206">Przychodzące transakcje powinna być akceptowana tylko, jeśli pochodzą z wysoce zaufanych klientów.</span><span class="sxs-lookup"><span data-stu-id="585a1-206">Incoming transactions should only be accepted if they come from highly trusted clients.</span></span>  
  
## <a name="policy-assertions"></a><span data-ttu-id="585a1-207">Asercji zasad</span><span class="sxs-lookup"><span data-stu-id="585a1-207">Policy Assertions</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="585a1-208">używa potwierdzenia zasad w celu kontroli przepływu transakcji.</span><span class="sxs-lookup"><span data-stu-id="585a1-208"> uses policy assertions to control transaction flow.</span></span> <span data-ttu-id="585a1-209">Potwierdzenia zasad można znaleźć w dokumencie zasad usługi, która jest generowana przez agregację kontrakty, konfiguracji i atrybuty.</span><span class="sxs-lookup"><span data-stu-id="585a1-209">Policy assertions can be found in a service’s policy document, which is generated by aggregating contracts, configuration, and attributes.</span></span> <span data-ttu-id="585a1-210">Klient może pobrać dokument zasad usługi przy użyciu HTTP GET lub WS-MetadataExchange żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="585a1-210">The client can obtain the service’s policy document using an HTTP GET or a WS-MetadataExchange request-reply.</span></span> <span data-ttu-id="585a1-211">Klienci mogą następnie przetworzyć dokument zasad, aby ustalić, jakie operacje na kontrakt usługi może obsługuje ani nie wymaga przepływu transakcji.</span><span class="sxs-lookup"><span data-stu-id="585a1-211">Clients can then process the policy document to determine which operations on a service contract may support or require transaction flow.</span></span>  
  
 <span data-ttu-id="585a1-212">Potwierdzenia zasad przepływu transakcji wpływają na przepływu transakcji, określając nagłówki SOAP czy klienta należy wysłać do usługi do reprezentowania transakcji.</span><span class="sxs-lookup"><span data-stu-id="585a1-212">Transaction flow policy assertions affect transaction flow by specifying the SOAP headers that a client should send to a service to represent a transaction.</span></span> <span data-ttu-id="585a1-213">Wszystkie nagłówki transakcji musi być oznaczone `MustUnderstand` równa `true`.</span><span class="sxs-lookup"><span data-stu-id="585a1-213">All transaction headers must be marked with `MustUnderstand` equal to `true`.</span></span> <span data-ttu-id="585a1-214">Dowolny komunikat z nagłówkiem, w przeciwnym razie oznaczone jest odrzucane błędu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="585a1-214">Any message with a header marked otherwise is rejected with a SOAP fault.</span></span>  
  
 <span data-ttu-id="585a1-215">Tylko jeden potwierdzenia zasad dotyczących transakcji mogą być obecne w ramach jednej operacji.</span><span class="sxs-lookup"><span data-stu-id="585a1-215">Only one transaction-related policy assertion can be present on a single operation.</span></span> <span data-ttu-id="585a1-216">Dokumenty zasad z więcej niż jednego potwierdzenia transakcji w przypadku operacji są uznawane za nieprawidłowe i są odrzucane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="585a1-216">Policy documents with more than one transaction assertion on an operation are considered invalid and are rejected by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="585a1-217">Ponadto tylko jednej transakcji protokołu może znajdować się wewnątrz każdego typu portu.</span><span class="sxs-lookup"><span data-stu-id="585a1-217">In addition, only a single transaction protocol can be present inside each port type.</span></span> <span data-ttu-id="585a1-218">Zasady dokumentów za pomocą operacji odwołuje się do więcej niż jeden protokół transakcji wewnątrz typu jednego portu są uznawane za nieprawidłowe i są odrzucane przez [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="585a1-218">Policy documents with operations referencing more than one transaction protocol inside a single port type are considered invalid, and are rejected by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="585a1-219">Zasady dokumentów za pomocą transakcji potwierdzenia znajduje się on na komunikaty wyjściowe lub jednokierunkowe komunikaty wejściowe również są uznawane za nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="585a1-219">Policy documents with transaction assertions present on output messages or one-way input messages are also considered invalid.</span></span>