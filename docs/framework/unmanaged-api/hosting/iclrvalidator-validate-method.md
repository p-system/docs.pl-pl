---
title: ICLRValidator::Validate — Metoda
ms.date: 03/30/2017
api_name:
- ICLRValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b2ad9ef473a498804e5b3ac0469b5b68697c49f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439176"
---
# <a name="iclrvalidatorvalidate-method"></a>ICLRValidator::Validate — Metoda
Weryfikuje przenośny plik wykonywalny (PE) lub język pośredni firmy Microsoft (MSIL) w określonym pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);      
```  
  
#### <a name="parameters"></a>Parametry  
 `veh`  
 [in] Wskaźnik do `IVEHandler` wystąpienie, które obsługuje błędy sprawdzania poprawności.  
  
 `ulAppDomainId`  
 [in] Identyfikator bieżącego <xref:System.AppDomain>.  
  
 `ulFlags`  
 [in] Kombinację [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) wartości i wskazujący rodzaj weryfikacji, które powinno być wykonywane.  
  
 `ulMaxError`  
 [in] Maksymalna liczba błędów umożliwia przed zakończeniem sprawdzania poprawności.  
  
 `token`  
 [in] Nieużywane.  
  
 `fileName`  
 [in] Nazwa pliku, który ma zostać zweryfikowana.  
  
 `pe`  
 [in] Wskaźnik do pliku buforu.  
  
 `ulSize`  
 [in] Rozmiar w bajtach, pliku, który ma zostać zweryfikowana.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`Validate` zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** IValidator.idl, IValidator.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRValidator, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
