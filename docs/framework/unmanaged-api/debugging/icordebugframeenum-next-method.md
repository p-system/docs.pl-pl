---
title: ICorDebugFrameEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum::Next
helpviewer_keywords:
- ICorDebugFrameEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: 0bc96acb-6179-4328-a447-cda562ce9e98
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f049a7cadf1857495e49b9bdc2fecd1b49103af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415486"
---
# <a name="icordebugframeenumnext-method"></a>ICorDebugFrameEnum::Next — Metoda
Pobiera określoną liczbę wystąpień ICorDebugFrame, zaczynając od bieżącego położenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba `ICorDebugFrame` wystąpienia mają zostać pobrane.  
  
 `frames`  
 [out] Tablicy wskaźników, z których każdy wskazuje `ICorDebugFrame` obiektu.  
  
 `pceltFetched`  
 [out] Wskaźnik do liczby `ICorDebugFrame` wystąpienia faktycznie zwracane. Ta wartość może mieć wartości zerowej Jeśli `celt` jeden.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
