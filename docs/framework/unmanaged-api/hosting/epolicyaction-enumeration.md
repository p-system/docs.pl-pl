---
title: EPolicyAction — Wyliczenie
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14908ae641c8539659e6014deb2c5f35a6d1cfbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433633"
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction — Wyliczenie
Opisuje akcje podejmowane zasad hosta można ustawić dla operacji opisanego przez [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) i błędów opisanego przez [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`eAbortThread`|Określa, że środowisko uruchomieniowe języka wspólnego (CLR) należy przerwać wątek bezpiecznie. Bezpieczne przerwania obejmuje próbuje uruchomić wszystkie `finally` blokuje żadnego `catch` bloki związanych z wątku przerwań i finalizatory.|  
|`eDisableRuntime`|Określa, czy CLR należy wprowadzić w stanie wyłączenia. Żadne dodatkowe zarządzanego kodu mogą być wykonywane w procesie dotyczy i wątków jest blokowane wprowadzeniu do środowiska CLR.|  
|`eExitProcess`|Określa, że środowisko CLR powinien podejmować próbę łagodne zakończenia procesu, w tym systemem finalizatory i oczyszczania i operacji rejestrowania.|  
|`eFastExitProcess`|Określa środowisko CLR powinien natychmiast zakończyć proces bez przeprowadzania finalizatory lub oczyszczania i operacji rejestrowania. Nowever, powiadomienie jest wysyłane do debugera.|  
|`eNoAction`|Określa, że wykonywane żadne działania.|  
|`eRudeAbortThread`|Określa, że środowisko CLR powinna wykonuje przerwania niegrzeczny wątku. Tylko te `catch` i `finally` oznaczonej jako bloki <xref:System.EnterpriseServices.MustRunInClientContextAttribute> są wykonywane.|  
|`eRudeExitProcess`|Określa środowisko CLR powinna zakończyć proces bez przeprowadzania finalizatory lub rejestrowania operacji.|  
|`eRudeUnloadAppDomain`|Określa, że niegrzeczny zwolnienie powinno być wykonywane przez środowisko CLR <xref:System.AppDomain>. Finalizatory tylko oznaczone <xref:System.EnterpriseServices.MustRunInClientContextAttribute> są wykonywane. Podobnie, wszystkie wątki z tym <xref:System.AppDomain> ich stosu odbierania `ThreadAbortException`, ale tylko te `catch` i `finally` oznaczonej jako bloki <xref:System.EnterpriseServices.MustRunInClientContextAttribute> są wykonywane.|  
|`eThrowException`|Określa, że jest zgłaszany wyjątek odpowiednie do warunku, takich jak braku pamięci, przepełnienie buforu i tak dalej.|  
|`eUnloadAppDomain`|Określa, że <xref:System.AppDomain> powinny zostać zwolniony. Środowisko CLR podejmie próbę uruchomienia finalizatory.|  
  
## <a name="remarks"></a>Uwagi  
 Host ustawia akcje zasady przez wywołanie metody [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interfejsu. Uzyskać informacji o niegrzeczny i bezpieczne przerwań, zobacz [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wyliczenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [EClrFailure, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [ICLRPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [IHostPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
