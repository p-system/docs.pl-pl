---
title: 'Porady: wykonywanie podstawowych działań na ciągach w programie .NET Framework'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e8c6c3f9b7ec418fdbf6365a3e7d90fe65e9caa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567188"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>Porady: wykonywanie podstawowych działań na ciągach w .NET
W poniższym przykładzie użyto niektóre metody omówione w [podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md) tematy, aby utworzyć klasę, która wykonuje na ciągach w sposób, który może zostać znaleziony w rzeczywistych aplikacjach. `MailToData` Klasy przechowuje nazwę i adres osoby w oddzielnych właściwości i umożliwia łączenie `City`, `State`, i `Zip` pól w jednym ciągu do wyświetlenia dla użytkownika. Ponadto klasa umożliwia użytkownikowi Wprowadź miejscowość, stan i kod POCZTOWY jako pojedynczy ciąg; Aplikacja automatycznie analizuje jeden ciąg i wprowadza odpowiednie informacje do odpowiadających im właściwości.  
  
 Dla uproszczenia w tym przykładzie użyto aplikacji konsoli przy użyciu interfejsu wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 Jeśli poprzedni kod jest wykonywane, użytkownik jest proszony o wprowadzenie jego nazwę lub adres. Aplikacja umieszcza informacje w odpowiednich właściwości i wyświetla informacje do użytkownika, tworzenie jeden ciąg, który wyświetla miejscowość, stan i kod POCZTOWY.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
