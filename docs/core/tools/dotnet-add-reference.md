---
title: "DotNet — Dodaj polecenie odwołanie - .NET Core interfejsu wiersza polecenia"
description: "Dotnet Dodaj odwołanie polecenie zapewnia to wygodny sposób, aby dodać odwołania projektu do projektu."
author: mairaw
ms.author: mairaw
ms.date: 09/19/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 9c6b0f434a9d6b1431e375ec6a437497aaddfc61
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="3cb96-103">DotNet — Dodaj odwołanie</span><span class="sxs-lookup"><span data-stu-id="3cb96-103">dotnet-add reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="3cb96-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3cb96-104">Name</span></span>

<span data-ttu-id="3cb96-105">`dotnet add reference`-Dodaje odwołania do projektu do projektu (P2P).</span><span class="sxs-lookup"><span data-stu-id="3cb96-105">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3cb96-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="3cb96-106">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="3cb96-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3cb96-107">Description</span></span>

<span data-ttu-id="3cb96-108">`dotnet add reference` Polecenie zapewnia to wygodny sposób, aby dodać odwołania projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="3cb96-108">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="3cb96-109">Po uruchomieniu polecenia [ `<ProjectReference>` ](/visualstudio/msbuild/common-msbuild-project-items) elementy są dodawane do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="3cb96-109">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="3cb96-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3cb96-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="3cb96-111">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="3cb96-111">Specifies the project file.</span></span> <span data-ttu-id="3cb96-112">Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.</span><span class="sxs-lookup"><span data-stu-id="3cb96-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="3cb96-113">Projekt do projektu (P2P) odwołuje się do dodania.</span><span class="sxs-lookup"><span data-stu-id="3cb96-113">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="3cb96-114">Określ co najmniej jeden projekt.</span><span class="sxs-lookup"><span data-stu-id="3cb96-114">Specify one or more projects.</span></span> <span data-ttu-id="3cb96-115">[Wzorce glob](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w systemach opartych na systemie Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="3cb96-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="3cb96-116">Opcje</span><span class="sxs-lookup"><span data-stu-id="3cb96-116">Options</span></span>

`-h|--help`

<span data-ttu-id="3cb96-117">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="3cb96-117">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="3cb96-118">Dodaje odwołania do projektu, tylko gdy jest określony [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="3cb96-118">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="3cb96-119">Przykłady</span><span class="sxs-lookup"><span data-stu-id="3cb96-119">Examples</span></span>

<span data-ttu-id="3cb96-120">Dodaj odwołanie do projektu:</span><span class="sxs-lookup"><span data-stu-id="3cb96-120">Add a project reference:</span></span>

`dotnet add app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="3cb96-121">Dodaj wiele odwołań do projektu do projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="3cb96-121">Add multiple project references to the project in the current directory:</span></span>

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="3cb96-122">Dodaj wiele odwołań do projektu przy użyciu wzorca globbing na systemie Linux/Unix:</span><span class="sxs-lookup"><span data-stu-id="3cb96-122">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

`dotnet add app/app.csproj reference **/*.csproj`