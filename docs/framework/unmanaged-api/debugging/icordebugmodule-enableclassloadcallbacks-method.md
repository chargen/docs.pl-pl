---
title: "ICorDebugModule::EnableClassLoadCallbacks — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.EnableClassLoadCallbacks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9045cceda54e6fe89c8c1baa8d4b9fa63105607
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="78f2f-102">ICorDebugModule::EnableClassLoadCallbacks — Metoda</span><span class="sxs-lookup"><span data-stu-id="78f2f-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="78f2f-103">Formanty czy [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) wywołań zwrotnych są nazywane dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="78f2f-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78f2f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="78f2f-104">Syntax</span></span>  
  
```  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78f2f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78f2f-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="78f2f-106">[in] Ta wartość `true` Aby włączyć środowisko uruchomieniowe języka wspólnego (CLR), aby wywołać `ICorDebugManagedCallback::LoadClass` i `ICorDebugManagedCallback::UnloadClass` metody, gdy występują ich skojarzonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="78f2f-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="78f2f-107">Wartość domyślna to `false` dla modułów-dynamic.</span><span class="sxs-lookup"><span data-stu-id="78f2f-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="78f2f-108">Wartość jest zawsze `true` dla modułów dynamicznych i nie można zmienić.</span><span class="sxs-lookup"><span data-stu-id="78f2f-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78f2f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="78f2f-109">Remarks</span></span>  
 <span data-ttu-id="78f2f-110">`ICorDebugManagedCallback::LoadClass` i `ICorDebugManagedCallback::UnloadClass` wywołań zwrotnych dla modułów dynamicznej zawsze są włączone i nie można wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="78f2f-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78f2f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="78f2f-111">Requirements</span></span>  
 <span data-ttu-id="78f2f-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78f2f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78f2f-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78f2f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78f2f-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78f2f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78f2f-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78f2f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78f2f-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78f2f-116">See Also</span></span>  
    
 