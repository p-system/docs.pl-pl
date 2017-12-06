---
title: "Łączenie statycznych funkcji globalnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 38462833e3b0ccd56265b02d9a1bc9f37ac12f5f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="fusion-global-static-functions"></a><span data-ttu-id="04cf0-102">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="04cf0-102">Fusion Global Static Functions</span></span>
<span data-ttu-id="04cf0-103">W tej sekcji opisano niezarządzane statyczne funkcje globalne, używane fusion interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="04cf0-103">This section describes the unmanaged global static functions that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="04cf0-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="04cf0-104">In This Section</span></span>  
 [<span data-ttu-id="04cf0-105">Cleardownloadcache — funkcja</span><span class="sxs-lookup"><span data-stu-id="04cf0-105">ClearDownloadCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/cleardownloadcache-function.md)  
 <span data-ttu-id="04cf0-106">Powoduje wyczyszczenie pamięci podręcznej GAC pobrany zestawów.</span><span class="sxs-lookup"><span data-stu-id="04cf0-106">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
 [<span data-ttu-id="04cf0-107">Compareassemblyidentity — funkcja</span><span class="sxs-lookup"><span data-stu-id="04cf0-107">CompareAssemblyIdentity Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 <span data-ttu-id="04cf0-108">Porównuje dwa tożsamości zestawu do ustalenia, czy są równoważne.</span><span class="sxs-lookup"><span data-stu-id="04cf0-108">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
 [<span data-ttu-id="04cf0-109">Createapplicationcontext — funkcja</span><span class="sxs-lookup"><span data-stu-id="04cf0-109">CreateApplicationContext Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createapplicationcontext-function.md)  
 <span data-ttu-id="04cf0-110">Tylko wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="04cf0-110">Internal only.</span></span> <span data-ttu-id="04cf0-111">(Ta funkcja obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie).</span><span class="sxs-lookup"><span data-stu-id="04cf0-111">(This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="04cf0-112">Createassemblycache — funkcja</span><span class="sxs-lookup"><span data-stu-id="04cf0-112">CreateAssemblyCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblycache-function.md)  
 <span data-ttu-id="04cf0-113">Pobiera wskaźnik do nowego [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) wystąpienie reprezentującego globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="04cf0-113">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
 [<span data-ttu-id="04cf0-114">CreateAssemblyEnum — funkcja</span><span class="sxs-lookup"><span data-stu-id="04cf0-114">CreateAssemblyEnum Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblyenum-function.md)  
 <span data-ttu-id="04cf0-115">Pobiera wskaźnik do [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) wystąpienia, który reprezentuje listę obiektów, które istnieją w określonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="04cf0-115">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that represents a list of objects that exist in the specified assembly.</span></span>  
  
 [<span data-ttu-id="04cf0-116">Createassemblynameobject — funkcja</span><span class="sxs-lookup"><span data-stu-id="04cf0-116">CreateAssemblyNameObject Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 <span data-ttu-id="04cf0-117">Pobiera wskaźnik do [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) wystąpienia, który reprezentuje unikatową tożsamość zestawu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="04cf0-117">Gets a pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
 [<span data-ttu-id="04cf0-118">Createhistoryreader — funkcja</span><span class="sxs-lookup"><span data-stu-id="04cf0-118">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 <span data-ttu-id="04cf0-119">Tworzy czytnik historii dla określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="04cf0-119">Creates a history reader for the specified file.</span></span>  
  
 [<span data-ttu-id="04cf0-120">Createinstallreferenceenum — funkcja</span><span class="sxs-lookup"><span data-stu-id="04cf0-120">CreateInstallReferenceEnum Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createinstallreferenceenum-function.md)  
 <span data-ttu-id="04cf0-121">Pobiera wskaźnik do [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) wystąpienia, który reprezentuje listę odwołań aplikacji do określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="04cf0-121">Gets a pointer to an [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
 [<span data-ttu-id="04cf0-122">Getappidauthority — funkcja</span><span class="sxs-lookup"><span data-stu-id="04cf0-122">GetAppIdAuthority Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getappidauthority-function.md)  
 <span data-ttu-id="04cf0-123">Pobiera wskaźnik do [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) wystąpienia zarządzanego kluczy dla tożsamości aplikacji i odwołań.</span><span class="sxs-lookup"><span data-stu-id="04cf0-123">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="04cf0-124">Getassemblyidentityfromfile — funkcja</span><span class="sxs-lookup"><span data-stu-id="04cf0-124">GetAssemblyIdentityFromFile Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getassemblyidentityfromfile-function.md)  
 <span data-ttu-id="04cf0-125">Pobiera wskaźnik do `IUnknown` obiektu z określonym `IID` w zestawie przy użyciu określonej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="04cf0-125">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
 [<span data-ttu-id="04cf0-126">Getcachepath — funkcja</span><span class="sxs-lookup"><span data-stu-id="04cf0-126">GetCachePath Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 <span data-ttu-id="04cf0-127">Pobiera ścieżkę do zestawu pamięci podręcznej, przy użyciu określonych flag.</span><span class="sxs-lookup"><span data-stu-id="04cf0-127">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
 [<span data-ttu-id="04cf0-128">Gethistoryfiledirectory — funkcja</span><span class="sxs-lookup"><span data-stu-id="04cf0-128">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 <span data-ttu-id="04cf0-129">Pobiera ścieżkę katalogu historii aplikacji.</span><span class="sxs-lookup"><span data-stu-id="04cf0-129">Retrieves the path of the application history directory.</span></span>  
  
 [<span data-ttu-id="04cf0-130">Getidentityauthority — funkcja</span><span class="sxs-lookup"><span data-stu-id="04cf0-130">GetIdentityAuthority Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getidentityauthority-function.md)  
 <span data-ttu-id="04cf0-131">Pobiera wskaźnik do [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) wystąpienia zarządzanego klucze obiekty kod.</span><span class="sxs-lookup"><span data-stu-id="04cf0-131">Gets a pointer to an [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
 [<span data-ttu-id="04cf0-132">Isframeworkassembly — funkcja</span><span class="sxs-lookup"><span data-stu-id="04cf0-132">IsFrameworkAssembly Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/isframeworkassembly-function.md)  
 <span data-ttu-id="04cf0-133">Pobiera wartość wskazującą, czy jest zarządzana w określonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="04cf0-133">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
 [<span data-ttu-id="04cf0-134">Nukedownloadedcache — funkcja</span><span class="sxs-lookup"><span data-stu-id="04cf0-134">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 <span data-ttu-id="04cf0-135">Usuwa pamięć podręczną wspólnego języka środowiska uruchomieniowego pobierania.</span><span class="sxs-lookup"><span data-stu-id="04cf0-135">Deletes the common language runtime download cache.</span></span>  
  
 [<span data-ttu-id="04cf0-136">Prebindassemblyex — funkcja</span><span class="sxs-lookup"><span data-stu-id="04cf0-136">PreBindAssemblyEx Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/prebindassemblyex-function.md)  
 <span data-ttu-id="04cf0-137">Pobiera nazwę wyświetlaną po zastosowaniu zasad dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="04cf0-137">Gets the post-policy display name for an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="04cf0-138">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="04cf0-138">Related Sections</span></span>  
 [<span data-ttu-id="04cf0-139">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="04cf0-139">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
  
 [<span data-ttu-id="04cf0-140">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="04cf0-140">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [<span data-ttu-id="04cf0-141">Łączenie — struktury</span><span class="sxs-lookup"><span data-stu-id="04cf0-141">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
  
 [<span data-ttu-id="04cf0-142">Globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="04cf0-142">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)