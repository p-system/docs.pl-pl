---
title: CorDebugMappingResult — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugMappingResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMappingResult
helpviewer_keywords:
- CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ca3f5a6af6ea19ec81af3f6ac0a028440f80d56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407962"
---
# <a name="cordebugmappingresult-enumeration"></a>CorDebugMappingResult — Wyliczenie
Zawiera szczegółowe informacje o sposobie uzyskano wartość wskaźnika instrukcji (IP).  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`MAPPING_PROLOG`|Kod natywny znajduje się w prologu, więc wartość adresu IP wynosi 0.|  
|`MAPPING_EPILOG`|Kod natywny jest w epilogu, dlatego wartość adres IP jest adresem ostatniej instrukcji metody.|  
|`MAPPING_NO_INFO`|Informacje mapowania są niedostępne w przypadku metody, więc wartość adresu IP wynosi 0.|  
|`MAPPING_UNMAPPED_ADDRESS`|Ma informacji o mapowaniu dla metody, ale bieżący adres nie można mapować do kodu języka pośredniego (MSIL) firmy Microsoft. Wartość adresu IP to 0.|  
|`MAPPING_EXACT`|Metoda mapuje się dokładnie do kodu MSIL albo został zinterpretowany ramki, dlatego wartość adres IP jest dokładne.|  
|`MAPPING_APPROXIMATE`|Metoda został pomyślnie zamapowany, ale wartość adresu IP może być przybliżonej.|  
  
## <a name="remarks"></a>Uwagi  
 Można użyć [ICorDebugILFrame::GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) metodę, aby uzyskać wartość wskaźnika instrukcji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
