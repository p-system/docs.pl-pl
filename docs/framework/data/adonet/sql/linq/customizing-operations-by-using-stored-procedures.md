---
title: "Dostosowywanie operacje przy użyciu procedur składowanych"
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
ms.assetid: aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9110cec32075c85807d3ef1550ae1a9e63b4239f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="customizing-operations-by-using-stored-procedures"></a><span data-ttu-id="ed0a4-102">Dostosowywanie operacje przy użyciu procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="ed0a4-102">Customizing Operations By Using Stored Procedures</span></span>
<span data-ttu-id="ed0a4-103">Procedury składowane reprezentują wspólnego podejścia do Zastępowanie domyślnego zachowania.</span><span class="sxs-lookup"><span data-stu-id="ed0a4-103">Stored procedures represent a common approach to overriding default behavior.</span></span> <span data-ttu-id="ed0a4-104">Przykłady w tym temacie przedstawiono sposób korzystania wygenerować otoki metody dla procedury składowane i jak można wywoływać procedur składowanych bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="ed0a4-104">The examples in this topic show how you can use generated method wrappers for stored procedures, and how you can call stored procedures directly.</span></span>  
  
 <span data-ttu-id="ed0a4-105">Jeśli używasz [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], można użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] można przypisać procedur składowanych do wykonywania operacji wstawiania, aktualizacji i usunięć.</span><span class="sxs-lookup"><span data-stu-id="ed0a4-105">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to assign stored procedures to perform inserts, updates, and deletes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed0a4-106">Można odczytać wartości powrotem generowanych przez bazę danych, należy użyć parametrów wyjściowych w Twojej procedur składowanych.</span><span class="sxs-lookup"><span data-stu-id="ed0a4-106">To read back database-generated values, use output parameters in your stored procedures.</span></span> <span data-ttu-id="ed0a4-107">Jeśli nie możesz użyć parametrów wyjściowych, zapisać implementacji metody częściowej zamiast polegania na zastąpienia generowane przez [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ed0a4-107">If you cannot use output parameters, write a partial method implementation instead of relying on overrides generated by the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="ed0a4-108">Elementy członkowskie mapowane na wartości generowanych przez bazy danych musi być ustawiona na odpowiednie wartości po `INSERT` lub `UPDATE` operacje zostały pomyślnie ukończone.</span><span class="sxs-lookup"><span data-stu-id="ed0a4-108">Members mapped to database-generated values must be set to appropriate values after `INSERT` or `UPDATE` operations have successfully completed.</span></span> <span data-ttu-id="ed0a4-109">Aby uzyskać więcej informacji, zobacz [obowiązki deweloperów w zastępowanie domyślne zachowanie](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="ed0a4-109">For more information, see [Responsibilities of the Developer In Overriding Default Behavior](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed0a4-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="ed0a4-110">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ed0a4-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ed0a4-111">Description</span></span>  
 <span data-ttu-id="ed0a4-112">W poniższym przykładzie przyjęto założenie, że `Northwind` klasa zawiera dwie metody do wywołania procedur składowanych, które są używane dla zastąpienia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="ed0a4-112">In the following example, assume that the `Northwind` class contains two methods to call stored procedures that are being used for overrides in a derived class.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ed0a4-113">Kod</span><span class="sxs-lookup"><span data-stu-id="ed0a4-113">Code</span></span>  
 [!code-csharp[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="ed0a4-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="ed0a4-114">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ed0a4-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ed0a4-115">Description</span></span>  
 <span data-ttu-id="ed0a4-116">Następujące klasy są używane do zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="ed0a4-116">The following class uses these methods for the override.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ed0a4-117">Kod</span><span class="sxs-lookup"><span data-stu-id="ed0a4-117">Code</span></span>  
 [!code-csharp[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="ed0a4-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="ed0a4-118">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ed0a4-119">Opis</span><span class="sxs-lookup"><span data-stu-id="ed0a4-119">Description</span></span>  
 <span data-ttu-id="ed0a4-120">Można użyć `NorthwindThroughSprocs` dokładnie tak jak w przypadku `Northwnd`.</span><span class="sxs-lookup"><span data-stu-id="ed0a4-120">You can use `NorthwindThroughSprocs` exactly as you would use `Northwnd`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ed0a4-121">Kod</span><span class="sxs-lookup"><span data-stu-id="ed0a4-121">Code</span></span>  
 [!code-csharp[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ed0a4-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed0a4-122">See Also</span></span>  
 [<span data-ttu-id="ed0a4-123">Obowiązki dewelopera w Zastępowanie domyślnego zachowania</span><span class="sxs-lookup"><span data-stu-id="ed0a4-123">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)