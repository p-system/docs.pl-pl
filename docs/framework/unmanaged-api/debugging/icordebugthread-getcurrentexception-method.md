---
title: "ICorDebugThread::GetCurrentException — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetCurrentException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fb48e99aa719e564bd23842efcaeda071441023b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="462b0-102">ICorDebugThread::GetCurrentException — Metoda</span><span class="sxs-lookup"><span data-stu-id="462b0-102">ICorDebugThread::GetCurrentException Method</span></span>
<span data-ttu-id="462b0-103">Pobiera wskaźnika interfejsu do obiektu ICorDebugValue, który reprezentuje wyjątek, który obecnie został zgłoszony przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="462b0-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="462b0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="462b0-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="462b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="462b0-105">Parameters</span></span>  
 `ppExceptionObject`  
 <span data-ttu-id="462b0-106">[out] Wskaźnik do adresu `ICorDebugValue` obiekt, który reprezentuje wyjątek, który obecnie został zgłoszony przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="462b0-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="462b0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="462b0-107">Remarks</span></span>  
 <span data-ttu-id="462b0-108">Obiekt wyjątku będzie istnieć od czasu wyjątku do końca `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="462b0-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="462b0-109">Obliczanie funkcji, które jest wykonywane za pomocą metod ICorDebugEval, należy usunąć obiekt wyjątku w instalacji, a następnie przywróć ją po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="462b0-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="462b0-110">Wyjątki mogą być zagnieżdżane (na przykład, jeśli w filtrze lub obliczanie funkcji jest zgłaszany wyjątek), dlatego może być wiele oczekujących wyjątków w jednym wątku.</span><span class="sxs-lookup"><span data-stu-id="462b0-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="462b0-111">`GetCurrentException`Zwraca najbardziej bieżącego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="462b0-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="462b0-112">Obiekt wyjątku i typ mogą ulec zmianie przez cały czas życia wyjątku.</span><span class="sxs-lookup"><span data-stu-id="462b0-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="462b0-113">Na przykład po wyjątek typu x, środowisko uruchomieniowe języka wspólnego (CLR) może przekroczyć dostępną ilość pamięci i Podwyższ go do wyjątku braku pamięci.</span><span class="sxs-lookup"><span data-stu-id="462b0-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="462b0-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="462b0-114">Requirements</span></span>  
 <span data-ttu-id="462b0-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="462b0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="462b0-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="462b0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="462b0-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="462b0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="462b0-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="462b0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>