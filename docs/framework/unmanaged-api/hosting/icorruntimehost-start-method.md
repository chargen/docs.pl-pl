---
title: "ICorRuntimeHost::Start — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.Start
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f259a28009ed12583bc8f7baa63e2ca17e4a21e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="9bca4-102">ICorRuntimeHost::Start — Metoda</span><span class="sxs-lookup"><span data-stu-id="9bca4-102">ICorRuntimeHost::Start Method</span></span>
<span data-ttu-id="9bca4-103">Uruchamia środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="9bca4-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bca4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9bca4-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9bca4-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9bca4-105">Return Value</span></span>  
  
|<span data-ttu-id="9bca4-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9bca4-106">HRESULT</span></span>|<span data-ttu-id="9bca4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9bca4-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9bca4-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9bca4-108">S_OK</span></span>|<span data-ttu-id="9bca4-109">Operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="9bca4-109">The operation was successful.</span></span>|  
|<span data-ttu-id="9bca4-110">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9bca4-110">S_FALSE</span></span>|<span data-ttu-id="9bca4-111">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="9bca4-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="9bca4-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9bca4-112">E_FAIL</span></span>|<span data-ttu-id="9bca4-113">Wystąpił nieznany, poważnej awarii.</span><span class="sxs-lookup"><span data-stu-id="9bca4-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="9bca4-114">Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="9bca4-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="9bca4-115">Kolejne wywołania żadnych hostingu interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9bca4-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9bca4-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9bca4-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9bca4-117">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="9bca4-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bca4-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9bca4-118">Remarks</span></span>  
 <span data-ttu-id="9bca4-119">Zazwyczaj nie jest konieczne do wywołania `Start` metody, ponieważ środowisko CLR jest uruchamiany automatycznie po pierwsze żądanie do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="9bca4-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bca4-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9bca4-120">Requirements</span></span>  
 <span data-ttu-id="9bca4-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bca4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bca4-122">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9bca4-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9bca4-123">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9bca4-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9bca4-124">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="9bca4-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bca4-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9bca4-125">See Also</span></span>  
 [<span data-ttu-id="9bca4-126">ICorRuntimeHost — interfejs</span><span class="sxs-lookup"><span data-stu-id="9bca4-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)