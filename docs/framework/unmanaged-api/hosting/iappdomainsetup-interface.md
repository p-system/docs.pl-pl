---
title: "IAppDomainSetup — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAppDomainSetup
api_location: mscoree.dll
api_type: COM
f1_keywords: IAppDomainSetup
helpviewer_keywords: IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e6ed5ea00799fff70626114257efef2d06b505ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="96b96-102">IAppDomainSetup — Interfejs</span><span class="sxs-lookup"><span data-stu-id="96b96-102">IAppDomainSetup Interface</span></span>
<span data-ttu-id="96b96-103">Dostarcza właściwości, które umożliwia konfigurowanie hosta <xref:System.AppDomain?displayProperty=nameWithType> typu przed wywołaniem [ICorRuntimeHost::CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metodę, aby go utworzyć.</span><span class="sxs-lookup"><span data-stu-id="96b96-103">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="96b96-104">Właściwości</span><span class="sxs-lookup"><span data-stu-id="96b96-104">Properties</span></span>  
  
|<span data-ttu-id="96b96-105">Właściwość</span><span class="sxs-lookup"><span data-stu-id="96b96-105">Property</span></span>|<span data-ttu-id="96b96-106">Opis</span><span class="sxs-lookup"><span data-stu-id="96b96-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="96b96-107">Pobiera lub ustawia nazwę katalogu, który zawiera aplikację.</span><span class="sxs-lookup"><span data-stu-id="96b96-107">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="96b96-108">Pobiera lub ustawia nazwę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="96b96-108">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="96b96-109">Pobiera lub ustawia nazwę obszaru określonych aplikacji gdy pliki są kopiowane w tle.</span><span class="sxs-lookup"><span data-stu-id="96b96-109">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="96b96-110">Pobiera lub ustawia nazwę pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="96b96-110">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="96b96-111">Pobiera lub ustawia nazwę katalogu, w którym przechowywane dynamicznie generowanym plików i dostępne.</span><span class="sxs-lookup"><span data-stu-id="96b96-111">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="96b96-112">Pobiera lub ustawia ścieżkę do pliku licencji, który jest skojarzony z tą domeną.</span><span class="sxs-lookup"><span data-stu-id="96b96-112">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="96b96-113">Pobiera lub ustawia listę katalogów, w połączeniu z <xref:System.AppDomainSetup.ApplicationBase%2A> katalog sondować zestawy prywatne.</span><span class="sxs-lookup"><span data-stu-id="96b96-113">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="96b96-114">Pobiera lub ustawia wartość ciągu, która obejmuje lub wyklucza <xref:System.AppDomainSetup.ApplicationBase%2A> ze ścieżki wyszukiwania dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="96b96-114">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="96b96-115">Pobiera lub ustawia nazwy katalogów, które zawierają zestawy należy skopiować w tle.</span><span class="sxs-lookup"><span data-stu-id="96b96-115">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="96b96-116">Pobiera lub ustawia ciąg, który wskazuje, czy kopiowanie w tle jest włączony czy wyłączony.</span><span class="sxs-lookup"><span data-stu-id="96b96-116">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="96b96-117">Prawidłowe wartości to "true" lub "false".</span><span class="sxs-lookup"><span data-stu-id="96b96-117">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96b96-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="96b96-118">Remarks</span></span>  
 <span data-ttu-id="96b96-119">`IAppDomainSetup` Interfejsu odpowiada zarządzanej <xref:System.IAppDomainSetup> interfejsu, który <xref:System.AppDomainSetup> typ implementuje.</span><span class="sxs-lookup"><span data-stu-id="96b96-119">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="96b96-120">Zobacz <xref:System.IAppDomainSetup?displayProperty=nameWithType> szczegółowe opisy jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="96b96-120">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="96b96-121">`IAppDomainSetup`reprezentuje informacje o powiązaniu zestawu, które mogą być dodawane do <xref:System.AppDomain> wystąpienia przed jego utworzenie.</span><span class="sxs-lookup"><span data-stu-id="96b96-121">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="96b96-122">Na przykład można ustawić hosta <xref:System.AppDomainSetup.ApplicationBase%2A> właściwości ustanowienie katalogu głównego sondy środowisko uruchomieniowe języka wspólnego (CLR) do zarządzanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="96b96-122">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96b96-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="96b96-123">Requirements</span></span>  
 <span data-ttu-id="96b96-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96b96-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96b96-125">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="96b96-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="96b96-126">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="96b96-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96b96-127">**Wersje programu .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96b96-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96b96-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="96b96-128">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup>  
 [<span data-ttu-id="96b96-129">Hosting — interfejsy</span><span class="sxs-lookup"><span data-stu-id="96b96-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)