---
title: Właściwości programu vs. Argumenty
ms.date: 03/30/2017
ms.assetid: 14651389-4a49-4cbb-9ddf-c83fdc155df1
ms.openlocfilehash: a6ea4755599f18e8bbaa8187941623578d2168ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514771"
---
# <a name="properties-vs-arguments"></a>Właściwości programu vs. Argumenty
Brak dostępnych kilka opcji przekazywania danych do działania. Oprócz używania <xref:System.Activities.InArgument>, działania mogą również być opracowane odbierające dane przy użyciu standardowych CLR właściwości lub publicznego <xref:System.Activities.ActivityAction> właściwości. W tym temacie omówiono sposób wybierania typu odpowiedniej metody.  
  
## <a name="using-clr-properties"></a>Przy użyciu właściwości CLR  
 Podczas przekazywania danych do działania, CLR właściwości (oznacza to, że metody publiczne czy Użyj Get i Set procedury do udostępniania danych) są opcji, która ma najwięcej ograniczeń. Wartość parametru przekazanego do właściwość CLR musi być znane, gdy rozwiązanie jest kompilowany; Ta wartość będzie taka sama dla każdego wystąpienia przepływu pracy. W ten sposób wartość przekazany właściwość CLR jest podobny do stałej zdefiniowane w kodzie; Ta wartość nie może zmienić okres aktywności i nie można zmienić w różnych wystąpieniach działania. <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A> Przykładem CLR właściwości udostępnianych przez działanie; nazwę metody, która wywołuje działania nie można zmienić na podstawie warunków środowiska uruchomieniowego i będzie taka sama dla każdego wystąpienia działania.  
  
## <a name="using-arguments"></a>Przy użyciu argumentów  
 Argumenty mają być używane w podczas szacowania tylko raz w ciągu okresu istnienia działania; danych oznacza to, że jego wartość nie zmieni się przez cały okres istnienia działania, ale wartość mogą być różne w różnych wystąpieniach działania. <xref:System.Activities.Statements.If.Condition%2A> Przykładem wartość, która pobiera obliczone raz; w związku z tym jest on zdefiniowany jako argument. <xref:System.Activities.Statements.WriteLine.Text%2A> inny przykład metodę, która powinna być zdefiniowana jako argumentu, ponieważ jest szacowana tylko raz podczas wykonywania działania, ale mogą być różne dla różnych wystąpień działania.  
  
## <a name="using-activityaction"></a>Przy użyciu ActivityAction  
 Gdy danych powinna być oceniana wiele razy w czasie trwania wykonywania działania <xref:System.Activities.ActivityAction> powinien być używany. Na przykład <xref:System.Activities.Statements.While.Condition%2A> właściwości jest sprawdzany pod kątem każdej iteracji <xref:System.Activities.Statements.While> pętli. Jeśli <xref:System.Activities.InArgument> były używane w tym celu pętli nigdy nie zakończenia, ponieważ argument może nie być ponownie oceniane pod kątem każdej iteracji i będzie zawsze zwróci takiego samego wyniku.
