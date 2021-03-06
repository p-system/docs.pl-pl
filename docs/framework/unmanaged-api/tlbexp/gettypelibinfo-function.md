---
title: GetTypeLibInfo — Funkcja
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56a9b97f37240e385dbd1788bafea62578d687a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457871"
---
# <a name="gettypelibinfo-function"></a>GetTypeLibInfo — Funkcja
Zwraca informacje na temat określonej biblioteki typów, sprawdzając jego [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) struktury.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szFile`  
 [in] Nazwa pliku biblioteki typów.  
  
 `pTypeLibID`  
 [out] Identyfikator GUID biblioteki typów.  
  
 `pTypeLibLCID`  
 [out] Identyfikator lokalizacji biblioteki typów.  
  
 `pTypeLibPlatform`  
 [out] A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) flagę, która identyfikuje docelowego systemu operacyjnego dla biblioteki typów. Typowe wartości to SYS_WIN32 i SYS_WIN64.  
  
 `pTypeLibMajorVer`  
 [out] Numer wersji głównej biblioteki typów. Na przykład w przypadku wersji *x.y*, numer wersji głównej jest *x*.  
  
 `pTypeLibMinorVer`  
 [out] Podrzędny numer wersji biblioteki typów. Na przykład w przypadku wersji *x.y*, podrzędny numer wersji jest *y*.  
  
## <a name="remarks"></a>Uwagi  
 `GetTypeLibInfo` Funkcja jest wywoływana przez [Tlbexp.exe (Eksporter biblioteki typów)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md). Narzędzie to generuje biblioteki typów, który opisuje typów w zestawie wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR).  
  
 Jeśli żadnych parametrów ma wartość null, funkcja zwraca `HRESULT` z `E_POINTER`. W przeciwnym razie zwraca `S_OK`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** TlbRef.h  
  
 **Biblioteka:** TlbRef.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tlbexp, funkcje pomocy](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [Funkcja LoadTypeLibEx](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)
