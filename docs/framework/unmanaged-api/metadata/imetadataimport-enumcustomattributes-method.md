---
title: IMetaDataImport::EnumCustomAttributes — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b549c6eacad63b165d26c203817f1a2adac57bca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448641"
---
# <a name="imetadataimportenumcustomattributes-method"></a>IMetaDataImport::EnumCustomAttributes — Metoda
Wylicza tokenów niestandardowych definicja atrybutu skojarzone z określonego typu lub elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumCustomAttributes (   
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,   
   [in]  mdToken            tkType,   
   [out] mdCustomAttribute  rCustomAttributes[],   
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phEnum`  
 [w, out] Wskaźnik do zwrócony modułu wyliczającego.  
  
 `tk`  
 [in] Token do zakresu wyliczenia lub zero dla wszystkich atrybutów niestandardowych.  
  
 `tkType`  
 [in] Token dla konstruktora typu atrybutów, które mają zostać wyliczone lub `null` dla wszystkich typów.  
  
 `rCustomAttributes`  
 [out] Tablica atrybutów niestandardowych.  
  
 `cMax`  
 [in] Maksymalny rozmiar `rCustomAttributes` tablicy.  
  
 `pcCustomAttributes`  
 [out, opcjonalnie] Rzeczywista liczba tokenów wartości zwracanych w `rCustomAttributes`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumCustomAttributes` zwrócona pomyślnie.|  
|`S_FALSE`|Nie ma żadnych atrybutów niestandardowych do wyliczenia. W takim przypadku `pcCustomAttributes` wynosi zero.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
