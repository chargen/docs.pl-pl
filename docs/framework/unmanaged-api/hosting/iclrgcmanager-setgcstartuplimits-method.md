---
title: "ICLRGCManager::SetGCStartupLimits — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager.SetGCStartupLimits
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1fd0c31fd6f988d4ee36bfe140b95ec258d4214e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="669ad-102">ICLRGCManager::SetGCStartupLimits — Metoda</span><span class="sxs-lookup"><span data-stu-id="669ad-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="669ad-103">Ustawia rozmiar segmentu kolekcji pamięci i maksymalny rozmiar pamięci systemu kolekcji generacji 0.</span><span class="sxs-lookup"><span data-stu-id="669ad-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="669ad-104">Począwszy od [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], można ustawić rozmiar segmentu i rozmiar maksymalny generacji 0 do wartości większej niż `DWORD` za pomocą [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="669ad-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="669ad-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="669ad-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="669ad-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="669ad-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="669ad-107">[in] Określony rozmiar pamięci segment kolekcji.</span><span class="sxs-lookup"><span data-stu-id="669ad-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="669ad-108">Rozmiar segmentu minimalna wynosi 4 MB.</span><span class="sxs-lookup"><span data-stu-id="669ad-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="669ad-109">Segmenty może być większa w krokach 1 MB lub większy.</span><span class="sxs-lookup"><span data-stu-id="669ad-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="669ad-110">[in] Określony maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="669ad-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="669ad-111">Rozmiar minimalny generacji 0 to 64 KB.</span><span class="sxs-lookup"><span data-stu-id="669ad-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="669ad-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="669ad-112">Return Value</span></span>  
  
|<span data-ttu-id="669ad-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="669ad-113">HRESULT</span></span>|<span data-ttu-id="669ad-114">Opis</span><span class="sxs-lookup"><span data-stu-id="669ad-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="669ad-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="669ad-115">S_OK</span></span>|<span data-ttu-id="669ad-116">`SetGCStartupLimits`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="669ad-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="669ad-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="669ad-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="669ad-118">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="669ad-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="669ad-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="669ad-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="669ad-120">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="669ad-120">The call timed out.</span></span>|  
|<span data-ttu-id="669ad-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="669ad-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="669ad-122">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="669ad-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="669ad-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="669ad-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="669ad-124">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="669ad-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="669ad-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="669ad-125">E_FAIL</span></span>|<span data-ttu-id="669ad-126">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="669ad-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="669ad-127">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="669ad-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="669ad-128">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="669ad-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="669ad-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="669ad-129">Remarks</span></span>  
 <span data-ttu-id="669ad-130">Wartości który `SetGCStartupLimits` zestawy można określić tylko raz.</span><span class="sxs-lookup"><span data-stu-id="669ad-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="669ad-131">Później wywołań `SetGCStartupLimits` są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="669ad-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="669ad-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="669ad-132">Requirements</span></span>  
 <span data-ttu-id="669ad-133">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="669ad-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="669ad-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="669ad-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="669ad-135">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="669ad-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="669ad-136">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="669ad-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="669ad-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="669ad-137">See Also</span></span>  
 [<span data-ttu-id="669ad-138">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="669ad-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="669ad-139">Wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="669ad-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="669ad-140">ICLRControl — interfejs</span><span class="sxs-lookup"><span data-stu-id="669ad-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="669ad-141">ICLRGCManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="669ad-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)