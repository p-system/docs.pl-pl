---
title: Funkcja CloneEnumWbemClassObject (niezarządzany wykaz interfejsów API)
description: Funkcja CloneEnumWbemClassObject tworzy kopię logicznej moduł wyliczający.
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71e881eca541d6a987fa7d27e1d73903f843e26a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460609"
---
# <a name="cloneenumwbemclassobject-function"></a>Funkcja CloneEnumWbemClassObject
Tworzy kopię logicznej moduł wyliczający, zachowując jego bieżącym położeniu w wyliczeniu.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum, 
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject, 
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority 
); 
```  

## <a name="parameters"></a>Parametry

`ppEnum`  
[out] Odbiera Wskaźnik do nowego [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx).

`authLevel`  
[in] Poziom autoryzacji.

`impLevel` [in] Poziom personifikacji.

`pCurrentEnumWbemClassObject`  
[out] Wskaźnik do [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) wystąpienia w klonowania.

`strUser`   
[in] Nazwa użytkownika. Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.

`strPassword`   
[in] Hasło. Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.

`strAuthority`   
[in] Nazwa domeny użytkownika. Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci ukończyć operacji. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Procedury zdalnej łącze wywołań (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IEnumWbemClassObject::Clone](https://msdn.microsoft.com/library/aa390859(v=vs.85).aspx) metody.

Ta metoda powoduje, że tylko kopii "optymalne działania". Ze względu na specyfikę dynamiczne wiele obiektów modelu wspólnych informacji jest to możliwe, że nowy moduł wyliczający nie wylicza ten sam zestaw obiektów jako modułu wyliczającego źródła.  

Jeśli wystąpi błąd wywołania funkcji, można uzyskać dodatkowe informacje o błędzie przez wywołanie metody [GetErrorInfo](geterrorinfo.md) funkcji.

## <a name="example"></a>Przykład

Na przykład zobacz [IEnumWbemClassObject::Clone](https://msdn.microsoft.com/library/aa390859(v=vs.85).aspx) metody.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
