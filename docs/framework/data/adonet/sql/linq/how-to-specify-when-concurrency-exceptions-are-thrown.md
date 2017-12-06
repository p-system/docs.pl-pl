---
title: "Porady: Określanie, kiedy są zgłaszane wyjątki współbieżności"
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
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8af833574544410977b9f881f9b2db4e6d88aa73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a><span data-ttu-id="ae3c3-102">Porady: Określanie, kiedy są zgłaszane wyjątki współbieżności</span><span class="sxs-lookup"><span data-stu-id="ae3c3-102">How to: Specify When Concurrency Exceptions are Thrown</span></span>
<span data-ttu-id="ae3c3-103">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.ChangeConflictException> jest zgłaszany wyjątek, jeśli obiekty nie będą aktualizowane z powodu konfliktów optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="ae3c3-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when objects do not update because of optimistic concurrency conflicts.</span></span> <span data-ttu-id="ae3c3-104">Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ae3c3-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="ae3c3-105">Przed przesłaniem zmiany do bazy danych, można określić podczas wyjątków współbieżności powinien zostać zgłoszony:</span><span class="sxs-lookup"><span data-stu-id="ae3c3-105">Before you submit your changes to the database, you can specify when concurrency exceptions should be thrown:</span></span>  
  
-   <span data-ttu-id="ae3c3-106">Zgłoszenie wyjątku w pierwszym niepowodzeniu (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span><span class="sxs-lookup"><span data-stu-id="ae3c3-106">Throw the exception at the first failure (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span></span>  
  
-   <span data-ttu-id="ae3c3-107">Zakończ wszystkie próby aktualizacji, accumulate wszystkie błędy oraz tworzenie raportów narastająco błędy w wyjątek (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span><span class="sxs-lookup"><span data-stu-id="ae3c3-107">Finish all update tries, accumulate all failures, and report the accumulated failures in the exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span></span>  
  
 <span data-ttu-id="ae3c3-108">Gdy zgłoszone, <xref:System.Data.Linq.ChangeConflictException> wyjątek zapewnia dostęp do <xref:System.Data.Linq.ChangeConflictCollection> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ae3c3-108">When thrown, the <xref:System.Data.Linq.ChangeConflictException> exception provides access to a <xref:System.Data.Linq.ChangeConflictCollection> collection.</span></span> <span data-ttu-id="ae3c3-109">Ta kolekcja zawiera szczegółowe informacje dla wszystkich konfliktów (przypisane do bloku try jednej aktualizacji nie powiodło się), łącznie z dostępem do <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ae3c3-109">This collection provides details for each conflict (mapped to a single failed update try), including access to the <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> collection.</span></span> <span data-ttu-id="ae3c3-110">Każdy element członkowski konflikt mapuje do jednego elementu członkowskiego w aktualizacji nie powiodło się sprawdzanie współbieżności.</span><span class="sxs-lookup"><span data-stu-id="ae3c3-110">Each member conflict maps to a single member in the update that failed the concurrency check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae3c3-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae3c3-111">Example</span></span>  
 <span data-ttu-id="ae3c3-112">Poniższy kod przedstawia przykłady obu wartości.</span><span class="sxs-lookup"><span data-stu-id="ae3c3-112">The following code shows examples of both values.</span></span>  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ae3c3-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae3c3-113">See Also</span></span>  
 [<span data-ttu-id="ae3c3-114">Porady: Zarządzanie konfliktów zmian</span><span class="sxs-lookup"><span data-stu-id="ae3c3-114">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="ae3c3-115">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="ae3c3-115">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)