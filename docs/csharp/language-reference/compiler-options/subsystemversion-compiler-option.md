---
title: -subsystemversion (opcje kompilatora C#)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: 25391dd504fb8a2b9458fd9495477258fc23d81a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215517"
---
# <a name="-subsystemversion-c-compiler-options"></a>-subsystemversion (opcje kompilatora C#)
Określa minimalną wersję podsystemu, na którym można uruchomić wygenerowanego pliku wykonywalnego, określając wersje systemu Windows, na którym można uruchomić pliku wykonywalnego. Najczęściej ta opcja zapewnia, że plik wykonywalny mogą korzystać z funkcji zabezpieczeń, które nie są dostępne w starszych wersjach systemu Windows.  
  
> [!NOTE]
>  Aby określić podsystem, użyj [-docelowy](../../../csharp/language-reference/compiler-options/target-compiler-option.md) — opcja kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a>Parametry  
 `major.minor`  
 Minimalna wymagana wersja podsystemu, wyrażone w kropkowego dla wersji głównej i pomocniczej. Na przykład można określić, że aplikacja nie można uruchomić w systemie operacyjnym, który jest starsze niż Windows 7 można ustawić wartości tej opcji 6.01, zgodnie z opisem w tabeli w dalszej części tego tematu. Należy określić wartości `major` i `minor` liczbami całkowitymi.  
  
 Wiodące wyzerowania `minor` wersji nie zmieniają wersji, ale czy końcowe zera. Na przykład 6.1 i 6.01 odwołują się do tej samej wersji, ale 6.10 odwołuje się do innej wersji. Firma Microsoft zaleca, przedstawiając wersja pomocnicza jako dwie cyfry, aby uniknąć pomyłek.  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli wymieniono typowe podsystemu wersjach systemu Windows.  
  
|Wersja systemu Windows|Wersję podsystemu|  
|---------------------|-----------------------|  
|Windows 2000|5.00|  
|Windows XP|5.01|  
|Windows Server 2003|5.02|  
|Windows Vista|6.00|  
|Windows 7|6.01|  
|Windows Server 2008|6.01|  
|[!INCLUDE[win8](~/includes/win8-md.md)]|6.02|  
  
## <a name="default-values"></a>Wartości domyślne  
 Wartość domyślna **- subsystemversion** — opcja kompilatora zależy od warunków na poniższej liście:  
  
-   Wartość domyślna to 6.02, jeśli ustawiono żadnych — opcja kompilatora na poniższej liście:  
  
    -   [-target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
  
    -   [-target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
  
    -   [-platform: arm](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)  
  
-   Wartość domyślna to 6,00, jeśli używasz programu MSBuild, docelowych [!INCLUDE[net_v45](~/includes/net-v45-md.md)], i nie zostały jeszcze skonfigurowane opcje kompilatora, które zostały określone we wcześniejszej części tej listy.  
  
-   Wartość domyślna to 4.00, jeśli żaden z powyższych warunków nie jest spełniony.  
  
## <a name="setting-this-option"></a>Ustawienie tej opcji  
 Aby ustawić **- subsystemversion** — opcja kompilatora w programie Visual Studio, należy otworzyć pliku .csproj i określić wartość dla `SubsystemVersion` właściwości w kodzie XML programu MSBuild. Nie można ustawić tej opcji w programie Visual Studio IDE. Aby uzyskać więcej informacji, zobacz "Wartości domyślnej" we wcześniejszej części tego tematu lub [wspólne właściwości projektów MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
