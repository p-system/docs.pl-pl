---
title: '&lt;Routing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cbe682ef9f7bca25ab4f5089a295ada9a00a8bc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltroutinggt"></a><span data-ttu-id="b892e-102">&lt;Routing&gt;</span><span class="sxs-lookup"><span data-stu-id="b892e-102">&lt;routing&gt;</span></span>

<span data-ttu-id="b892e-103">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu tabel docelowych punktów końcowych do wysyłania komunikatów do podczas definiowania kryteria filtru.</span><span class="sxs-lookup"><span data-stu-id="b892e-103">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="b892e-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="b892e-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="b892e-105">&nbsp;&nbsp;**\<Routing >**</span><span class="sxs-lookup"><span data-stu-id="b892e-105">&nbsp;&nbsp;**\<routing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b892e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b892e-106">Syntax</span></span>

```xml
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String" 
              filterData="String" 
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath" 
              name="String" />
    </filters>
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String" 
               filterName="String" 
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
  </routing>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b892e-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b892e-107">Attributes and elements</span></span>

<span data-ttu-id="b892e-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b892e-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b892e-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b892e-109">Attributes</span></span>

<span data-ttu-id="b892e-110">Brak</span><span class="sxs-lookup"><span data-stu-id="b892e-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="b892e-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b892e-111">Child elements</span></span>

|     | <span data-ttu-id="b892e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b892e-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="b892e-113">**\<Filtry >**</span><span class="sxs-lookup"><span data-stu-id="b892e-113">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="b892e-114">Zawiera zestaw filtrów routingu, które określają typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter będą używane podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="b892e-114">Contains a set of routing filters that determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="b892e-115">**\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="b892e-115">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="b892e-116">Zawiera mapowania między filtrami i docelowymi punktami końcowymi, aby określić, który punkt końcowy do użycia podczas kryteria filtru są spełnione.</span><span class="sxs-lookup"><span data-stu-id="b892e-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="b892e-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b892e-117">Parent elements</span></span>

|     | <span data-ttu-id="b892e-118">Opis</span><span class="sxs-lookup"><span data-stu-id="b892e-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="b892e-119">**\<System. ServiceModel >**</span><span class="sxs-lookup"><span data-stu-id="b892e-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="b892e-120">Element główny wszystkich elementów konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="b892e-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="b892e-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b892e-121">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>