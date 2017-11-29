---
title: "ICLRGCManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager
helpviewer_keywords: ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7215ce1423e8541b23daae7b9e051ade6e25f1b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="1519f-102">ICLRGCManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1519f-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="1519f-103">Udostępnia metody umożliwiające hosta do interakcji z systemem zbierania odzyskiwanie środowisko uruchomieniowe języka wspólnego firmy.</span><span class="sxs-lookup"><span data-stu-id="1519f-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1519f-104">Począwszy od [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], można użyć [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metodę, aby wartość rozmiaru segmentu kolekcji pamięci i maksymalny rozmiar pamięci systemu kolekcji generacji 0 wartości większą niż `DWORD` limit, który jest narzucone przez [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="1519f-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1519f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1519f-105">Methods</span></span>  
  
|<span data-ttu-id="1519f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="1519f-106">Method</span></span>|<span data-ttu-id="1519f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1519f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1519f-108">Collect — metoda</span><span class="sxs-lookup"><span data-stu-id="1519f-108">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|<span data-ttu-id="1519f-109">Wymusza wyrzucania elementów bezużytecznych dla określonej generacji.</span><span class="sxs-lookup"><span data-stu-id="1519f-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="1519f-110">GetStats — metoda</span><span class="sxs-lookup"><span data-stu-id="1519f-110">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|<span data-ttu-id="1519f-111">Pobiera zestaw bieżącego Statystyka systemu czyszczenia pamięci.</span><span class="sxs-lookup"><span data-stu-id="1519f-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="1519f-112">SetGCStartupLimits — metoda</span><span class="sxs-lookup"><span data-stu-id="1519f-112">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="1519f-113">Ustawia rozmiar segmentu kolekcji pamięci i maksymalny rozmiar pamięci systemu kolekcji generacji 0.</span><span class="sxs-lookup"><span data-stu-id="1519f-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1519f-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1519f-114">Remarks</span></span>  
 <span data-ttu-id="1519f-115">Środowisko uruchomieniowe języka wspólnego (CLR) implementuje mechanizm kolekcji jego odzyskiwanie z zarządzanego <xref:System.GC> typu.</span><span class="sxs-lookup"><span data-stu-id="1519f-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="1519f-116">Aby uzyskać więcej informacji o systemie kolekcji pamięci, zobacz [wyrzucanie elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="1519f-116">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1519f-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1519f-117">Requirements</span></span>  
 <span data-ttu-id="1519f-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1519f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1519f-119">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1519f-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1519f-120">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1519f-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1519f-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1519f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1519f-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1519f-122">See Also</span></span>  
 [<span data-ttu-id="1519f-123">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="1519f-123">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="1519f-124">Cor_gc_stats — struktura</span><span class="sxs-lookup"><span data-stu-id="1519f-124">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="1519f-125">ICLRControl — interfejs</span><span class="sxs-lookup"><span data-stu-id="1519f-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="1519f-126">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="1519f-126">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="1519f-127">Hosting — interfejsy</span><span class="sxs-lookup"><span data-stu-id="1519f-127">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="1519f-128">Hosting</span><span class="sxs-lookup"><span data-stu-id="1519f-128">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)