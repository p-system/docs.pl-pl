---
title: Uruchom .NET Framework 1.1 aplikacji w systemie Windows 8, Windows 8.1 lub Windows 10
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8b234d4e2fe7d5efe0a6c33f61b9ba422b55803d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386460"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Uruchom .NET Framework 1.1 aplikacji w systemie Windows 8, Windows 8.1 lub Windows 10

.NET Framework 1.1 nie jest obsługiwana w [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], lub w systemach operacyjnych Windows 10. W niektórych przypadkach, .NET Framework 1.1 zostanie dokładnie zidentyfikowana jako wymagane do uruchamiania aplikacji. W takich przypadkach należy skontaktować się z niezależnego dostawcy oprogramowania (ISV) aplikacjami uaktualniony do uruchamiania na [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] lub nowszej wersji. Aby uzyskać dodatkowe informacje, zobacz [Migrowanie z programu .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a>Zainstaluj program .NET Framework 1.1 z dysku CD lub Centrum pobierania

Nie można ręcznie zainstalować program .NET Framework 1.1 na [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], lub Windows 10. Nie jest już obsługiwany. Jeśli spróbujesz zainstalować pakiet, zostanie wyświetlony następujący komunikat o błędzie: "Instalator nie może kontynuować, ponieważ ta wersja programu .NET Framework jest niezgodna z zainstalowaną wcześniej." Aby rozwiązać ten problem, zainstaluj [.NET Framework 3.5 SP1](http://www.microsoft.com/download/details.aspx?id=22). Ta wersja zawiera programu .NET Framework 2.0 (wersję, która wykonuje programu .NET Framework 1.1), który jest obsługiwany w [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)]i Windows 10. Zawsze należy dążyć do zainstalowania aplikacji, aby ustalić, czy jego zostaną automatycznie zaktualizowane do nowszej wersji programu .NET Framework. Jeśli nie, skontaktuj się z Twojej niezależnego dostawcy oprogramowania w celu aktualizacji aplikacji.

## <a name="see-also"></a>Zobacz także

[Migrowanie z programu .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)
[Zainstaluj program .NET Framework 3.5 w systemie Windows 10, Windows 8.1 i Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md)
