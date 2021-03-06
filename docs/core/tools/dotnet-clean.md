---
title: polecenie - .NET Core interfejsu wiersza polecenia czyszczenia DotNet
description: Polecenie Wyczyść dotnet czyści bieżącego katalogu.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 9e68781fe00590f3c8d429631a3f72d525d29fa9
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697034"
---
# <a name="dotnet-clean"></a>Wyczyść DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet clean` -Czyści dane wyjściowe projektu.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a>Opis

`dotnet clean` Polecenie czyści dane wyjściowe ostatniej kompilacji. Jest zaimplementowany jako [docelowy programu MSBuild](/visualstudio/msbuild/msbuild-targets), więc projekt jest oceniane w czasie uruchomienia polecenia. Tylko dane wyjściowe tworzone podczas kompilacji zostały wyczyszczone. Zarówno pośredni (*obj*) i pliku wyjściowego (*bin*) foldery zostały wyczyszczone.

## <a name="arguments"></a>Argumenty

`PROJECT`

Aby wyczyścić projektu MSBuild. Jeśli nie określono pliku projektu, MSBuild wyszukuje bieżącego katalogu roboczego dla pliku, który ma rozszerzenie pliku, który kończy się *proj* i używa tego pliku.

## <a name="options"></a>Opcje

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`. Ta opcja jest tylko wymagane podczas oczyszczania, jeśli określono w czasie kompilacji.

`-f|--framework <FRAMEWORK>`

[Framework](../../standard/frameworks.md) , która została określona podczas kompilacji. Platformę musi być zdefiniowana w [pliku projektu](csproj.md). Jeśli określono platformę w czasie kompilacji, należy określić platformę podczas czyszczenia.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`-o|--output <OUTPUT_DIRECTORY>`

Katalog, w którym są umieszczane dane wyjściowe kompilacji. Określ `-f|--framework <FRAMEWORK>` przełącznika z przełącznikiem katalogu wyjściowego, jeśli określony platformę, gdy projekt został skompilowany.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Czyści folderze wyjściowym określonym środowiska uruchomieniowego. Ten element jest używany podczas [niezależne wdrożenia](../deploying/index.md#self-contained-deployments-scd) został utworzony.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone poziomy są q [uiet], [najmniej] m, n [ormal], d [egółowy] i diag [nostic].

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`. Ta opcja jest tylko wymagane podczas oczyszczania, jeśli określono w czasie kompilacji.

`-f|--framework <FRAMEWORK>`

[Framework](../../standard/frameworks.md) , która została określona podczas kompilacji. Platformę musi być zdefiniowana w [pliku projektu](csproj.md). Jeśli określono platformę w czasie kompilacji, należy określić platformę podczas czyszczenia.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`-o|--output <OUTPUT_DIRECTORY>`

Katalog, w którym są umieszczane dane wyjściowe kompilacji. Określ `-f|--framework <FRAMEWORK>` przełącznika z przełącznikiem katalogu wyjściowego, jeśli określony platformę, gdy projekt został skompilowany.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone poziomy są q [uiet], [najmniej] m, n [ormal], d [egółowy] i diag [nostic].

---

## <a name="examples"></a>Przykłady

Czyszczenie kompilacji domyślnego projektu:

`dotnet clean`

Wyczyść projekt utworzony przy użyciu konfiguracji wydania:

`dotnet clean --configuration Release`
