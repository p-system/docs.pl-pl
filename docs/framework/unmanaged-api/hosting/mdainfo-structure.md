---
title: MDAInfo — Struktura
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5164e85ecc97de99dcc493c2ba5efa8fc3468471
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443183"
---
# <a name="mdainfo-structure"></a>MDAInfo — Struktura
Zawiera szczegółowe informacje na temat `Event_MDAFired` zdarzenie, które wyzwala tworzenie zarządzany Asystent debugowania (MDA).  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`lpMDACaption`|Tytuł bieżącego MDA. Tytuł opisuje rodzaj awarii, która wyzwoliła `Event_MDAFired` zdarzeń.|  
|`lpMDAMessage`|Dostarczone przez bieżący MDA komunikatu wyjściowego.|  
  
## <a name="remarks"></a>Uwagi  
 Asystenci zarządzanego debugowania (mda) są debugowania pomocy, które działają w połączeniu z środowisko uruchomieniowe języka wspólnego (CLR) do wykonywania zadań, takich jak identyfikujący nieprawidłowe warunki w aparacie wykonawczym środowiska uruchomieniowego lub zrzucanie dodatkowe informacje o stanie aparat. Mda generowania komunikatów XML o zdarzeniach, które w przeciwnym razie są trudne do pułapki. Są one szczególnie przydatne w przypadku przejścia między zarządzanymi i niezarządzanymi kodu do debugowania.  
  
 Środowisko uruchomieniowe wykonuje następujące czynności w przypadku jest generowane zdarzenie, które wyzwala tworzenie MDA:  
  
-   Jeśli host nie został zarejestrowany [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) wystąpienia przez wywołanie metody [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) ma być powiadamiany o `Event_MDAFired` zdarzenia środowiska uruchomieniowego kontynuuje jego Domyślnie zachowanie nie jest obsługiwane.  
  
-   Jeśli host został zarejestrowany obsługi dla tego zdarzenia, środowisko uruchomieniowe sprawdza, czy debuger jest dołączony do procesu. Jeśli tak jest, środowisko uruchomieniowe przechodzi do debugera. Debuger będzie nadal występował, wywołuje do hosta. Jeśli żaden debuger jest dołączony, środowisko urchomieniowe wywołuje `IActionOnCLREvent::OnEvent` i przekazuje wskaźnik do `MDAInfo` jako `data` parametru.  
  
 Aby aktywować mda i zgłaszane po aktywowaniu MDA, można wybrać hosta. Host daje możliwość zastąpienie zachowania domyślnego i abort zarządzanego wątku, który wywołał zdarzenie, aby uniknąć uszkodzenia stan procesu. Aby uzyskać więcej informacji na temat używania mda, zobacz [diagnozowanie problemów z Asystenci zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.idl  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting, struktury](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
