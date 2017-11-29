---
title: Funkcja CertTimestampAuthenticodeLicense
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertTimestampAuthenticodeLicense
api_location: clr.dll
api_type: DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42ec863e9accbd2156b6eeed5857ff86075cf0a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="319ff-102">Funkcja CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="319ff-102">CertTimestampAuthenticodeLicense Function</span></span>
<span data-ttu-id="319ff-103">Sygnatury czasowe jako Authenticode XrML licencji.</span><span class="sxs-lookup"><span data-stu-id="319ff-103">Time-stamps an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="319ff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="319ff-104">Syntax</span></span>  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="319ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="319ff-105">Parameters</span></span>  
 `pSignedLicenseBlob`  
 <span data-ttu-id="319ff-106">[in] Podpisem Authenticode XrML licencji za sygnaturami czasowymi.</span><span class="sxs-lookup"><span data-stu-id="319ff-106">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="319ff-107">Zobacz [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="319ff-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pwszTimestampURI`  
 <span data-ttu-id="319ff-108">[in] Identyfikator URI serwera sygnatury czasowej.</span><span class="sxs-lookup"><span data-stu-id="319ff-108">[in] The time-stamp server's URI.</span></span>  
  
 `pTimestampSignatureBlob`  
 <span data-ttu-id="319ff-109">[out] Wskaźnik do CRYPT_DATA_BLOB do odbierania podpisu sygnatury czasowej algorytmem Base64.</span><span class="sxs-lookup"><span data-stu-id="319ff-109">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="319ff-110">Wywołującego odpowiedzialność za wolny `pTimestampSignatureBlob` -> `pbData` z `HepFree()` po użyciu.</span><span class="sxs-lookup"><span data-stu-id="319ff-110">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="319ff-111">Zobacz [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="319ff-111">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="319ff-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="319ff-112">Remarks</span></span>  
 <span data-ttu-id="319ff-113">Podpis sygnatury czasowej jest rzeczywiście komunikat PKCS #7 SignedData, którego zawartość jest Forma binarna SignatureValue z nim licencja podpisu.</span><span class="sxs-lookup"><span data-stu-id="319ff-113">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="319ff-114">Zasadniczo to dodatkowe zaradczych podpis licencji.</span><span class="sxs-lookup"><span data-stu-id="319ff-114">Basically, this acts as a counter-signature of the license.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="319ff-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="319ff-115">Return Value</span></span>  
 <span data-ttu-id="319ff-116">`S_OK`Jeśli funkcja zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="319ff-116">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="319ff-117">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="319ff-117">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="319ff-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="319ff-118">See Also</span></span>  
 [<span data-ttu-id="319ff-119">Authenticode</span><span class="sxs-lookup"><span data-stu-id="319ff-119">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)