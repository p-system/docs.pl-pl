---
title: IMetaDataImport::FindMember — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 79c9a54a44ae1751cb8b1b57379ccfd6485f6e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448194"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember — Metoda
Pobiera wskaźnik do MemberDef token dla pola lub metody, która jest zawarta w określonym <xref:System.Type> z określoną sygnaturą nazwy i metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `td`  
 [in] Token TypeDef dla klasy lub interfejsu, który dodaje element do wyszukania. Jeśli ta wartość jest `mdTokenNil`, wyszukiwanie jest wykonywane na potrzeby zmiennej globalnej lub globalnego funkcji.  
  
 `szName`  
 [in] Nazwa elementu członkowskiego do wyszukania.  
  
 `pvSigBlob`  
 [in] Wskaźnik do sygnatury binarne metadanych elementu członkowskiego.  
  
 `cbSigBlob`  
 [in] Wyrażony w bajtach rozmiar `pvSigBlob`.  
  
 `pmb`  
 [out] Wskaźnik do dopasowania tokenu MemberDef.  
  
## <a name="remarks"></a>Uwagi  
 Określ element członkowski za pomocą jego otaczającej klasy lub interfejsu (`td`), jego nazwa (`szName`) i opcjonalnie jego podpis (`pvSigBlob`). Może to być wielu członków o tej samej nazwie w klasie lub interfejs. W takim przypadku należy przekazać podpisu elementu członkowskiego można znaleźć unikatowego dopasowania.  
  
 Podpis przekazany do `FindMember` musi został wygenerowany w bieżącym zakresie, ponieważ podpisy są powiązane z określonego zakresu. Podpis osadzić token, który identyfikuje typ otaczający klasy lub wartości. Token jest indeks do lokalnej tabeli TypeDef. Nie można skompilować podpisu środowiska wykonawczego poza kontekstem bieżącego zakresu i używania jako danych wejściowych do danych wejściowych do tego podpisu `FindMember`.  
  
 `FindMember` Wyszukuje tylko elementy członkowskie, które zostały zdefiniowane bezpośrednio w klasy lub interfejsu; dziedziczone elementy członkowskie nie zostanie znaleziona.  
  
> [!NOTE]
>  `FindMember` jest to metoda pomocnika. Wywołuje [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); Jeśli tego wywołania nie znaleziono dopasowania, `FindMember` następnie wywołuje [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
