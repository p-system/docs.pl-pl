---
title: "Wywołania metody lokalnego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 32d4726924140029ebe94676f23ba5c495891e8a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="local-method-calls"></a><span data-ttu-id="e899f-102">Wywołania metody lokalnego</span><span class="sxs-lookup"><span data-stu-id="e899f-102">Local Method Calls</span></span>
<span data-ttu-id="e899f-103">Wywołanie metody lokalnych to taki, który jest wykonywana w ramach modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="e899f-103">A local method call is one that is executed within the object model.</span></span> <span data-ttu-id="e899f-104">Wywołanie metody zdalnej jest jednym który [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy do bazy danych SQL i przesyła do aparatu bazy danych w celu wykonania.</span><span class="sxs-lookup"><span data-stu-id="e899f-104">A remote method call is one that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates to SQL and transmits to the database engine for execution.</span></span> <span data-ttu-id="e899f-105">Wywołania metody lokalnym są wymagane podczas [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie może dokonywać translacji wywołania SQL.</span><span class="sxs-lookup"><span data-stu-id="e899f-105">Local method calls are needed when [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot translate the call into SQL.</span></span> <span data-ttu-id="e899f-106">W przeciwnym razie <xref:System.InvalidOperationException> jest generowany.</span><span class="sxs-lookup"><span data-stu-id="e899f-106">Otherwise, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="e899f-107">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="e899f-107">Example 1</span></span>  
 <span data-ttu-id="e899f-108">W poniższym przykładzie `Order` klasy jest mapowany do tabeli zamówienia w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="e899f-108">In the following example, an `Order` class is mapped to the Orders table in the Northwind sample database.</span></span> <span data-ttu-id="e899f-109">Metoda lokalne wystąpienie dodano do klasy.</span><span class="sxs-lookup"><span data-stu-id="e899f-109">A local instance method has been added to the class.</span></span>  
  
 <span data-ttu-id="e899f-110">W 1 kwerendy. Konstruktor `Order` klasy jest wykonywane lokalnie.</span><span class="sxs-lookup"><span data-stu-id="e899f-110">In Query 1, the constructor for the `Order` class is executed locally.</span></span> <span data-ttu-id="e899f-111">W kwerendzie 2, jeśli [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] próbował tłumaczenie `LocalInstanceMethod()`SQL, próba nie powiedzie się i <xref:System.InvalidOperationException> może zostać zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e899f-111">In Query 2, if [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tried to translate `LocalInstanceMethod()`into SQL, the attempt would fail and an <xref:System.InvalidOperationException> exception would be thrown.</span></span> <span data-ttu-id="e899f-112">Jednak ponieważ [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia obsługę dla wywołań metod lokalnego kwerenda2 nie spowoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="e899f-112">But because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides support for local method calls, Query2 will not throw an exception.</span></span>  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e899f-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e899f-113">See Also</span></span>  
 [<span data-ttu-id="e899f-114">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="e899f-114">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)