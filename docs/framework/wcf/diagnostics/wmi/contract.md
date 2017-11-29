---
title: Contract1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2e92c5d804fca3c04506e951a5c341c89eed1c54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="contract"></a><span data-ttu-id="10105-102">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="10105-102">Contract</span></span>
<span data-ttu-id="10105-103">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="10105-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10105-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="10105-104">Syntax</span></span>  
  
```  
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="10105-105">Metody</span><span class="sxs-lookup"><span data-stu-id="10105-105">Methods</span></span>  
 <span data-ttu-id="10105-106">Klasa kontraktu nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="10105-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="10105-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="10105-107">Properties</span></span>  
 <span data-ttu-id="10105-108">Klasa kontraktu ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="10105-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="10105-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="10105-109">AppDomainId</span></span>  
 <span data-ttu-id="10105-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="10105-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="10105-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="10105-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10105-112">Identyfikator domeny aplikacji obsługującej kontrakt.</span><span class="sxs-lookup"><span data-stu-id="10105-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="10105-113">Zachowania</span><span class="sxs-lookup"><span data-stu-id="10105-113">Behaviors</span></span>  
 <span data-ttu-id="10105-114">Typ danych: zachowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="10105-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="10105-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="10105-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10105-116">Zachowania skojarzone z tym kontraktem.</span><span class="sxs-lookup"><span data-stu-id="10105-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="10105-117">Nazwa</span><span class="sxs-lookup"><span data-stu-id="10105-117">Name</span></span>  
 <span data-ttu-id="10105-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="10105-118">Data type: string</span></span>  
  
 <span data-ttu-id="10105-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="10105-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10105-120">Nazwa kontraktu w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="10105-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="10105-121">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="10105-121">Namespace</span></span>  
 <span data-ttu-id="10105-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="10105-122">Data type: string</span></span>  
  
 <span data-ttu-id="10105-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="10105-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10105-124">Przestrzeń nazw `portType` elementu w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="10105-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="10105-125">Operacje</span><span class="sxs-lookup"><span data-stu-id="10105-125">Operations</span></span>  
 <span data-ttu-id="10105-126">Typ danych: operacja tablicy</span><span class="sxs-lookup"><span data-stu-id="10105-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="10105-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="10105-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10105-128">Operacje tego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="10105-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="10105-129">Identyfikator procesu</span><span class="sxs-lookup"><span data-stu-id="10105-129">ProcessId</span></span>  
 <span data-ttu-id="10105-130">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="10105-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="10105-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="10105-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10105-132">Identyfikator procesu obsługującego kontrakt procesu.</span><span class="sxs-lookup"><span data-stu-id="10105-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="10105-133">ref</span><span class="sxs-lookup"><span data-stu-id="10105-133">ref</span></span>  
 <span data-ttu-id="10105-134">Typ danych: kontraktu</span><span class="sxs-lookup"><span data-stu-id="10105-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="10105-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="10105-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10105-136">Typ wywołania zwrotnego w przypadku kontraktu dupleksowego.</span><span class="sxs-lookup"><span data-stu-id="10105-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="10105-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="10105-137">SessionMode</span></span>  
 <span data-ttu-id="10105-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="10105-138">Data type: string</span></span>  
  
 <span data-ttu-id="10105-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="10105-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10105-140">Wskazuje, czy kontrakt wymaga powiązanie skojarzone z tym kontraktem, aby używać sesji kanału.</span><span class="sxs-lookup"><span data-stu-id="10105-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="10105-141">Typ</span><span class="sxs-lookup"><span data-stu-id="10105-141">Type</span></span>  
 <span data-ttu-id="10105-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="10105-142">Data type: string</span></span>  
  
 <span data-ttu-id="10105-143">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="10105-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10105-144">Typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="10105-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10105-145">Wymagania</span><span class="sxs-lookup"><span data-stu-id="10105-145">Requirements</span></span>  
  
|<span data-ttu-id="10105-146">MOF</span><span class="sxs-lookup"><span data-stu-id="10105-146">MOF</span></span>|<span data-ttu-id="10105-147">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="10105-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="10105-148">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="10105-148">Namespace</span></span>|<span data-ttu-id="10105-149">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="10105-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10105-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10105-150">See Also</span></span>  
 <xref:System.ServiceModel.Description.ContractDescription>