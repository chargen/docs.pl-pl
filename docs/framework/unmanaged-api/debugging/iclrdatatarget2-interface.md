---
title: "ICLRDataTarget2 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget2
helpviewer_keywords: ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1780df0a4659d232a27faf4fdc2f6c9b13db98a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="0c34c-102">ICLRDataTarget2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0c34c-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="0c34c-103">Podklasa [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) używany przez warstwę usługi dostępu do danych do manipulowania regiony pamięci wirtualnej w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="0c34c-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0c34c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0c34c-104">Methods</span></span>  
  
|<span data-ttu-id="0c34c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0c34c-105">Method</span></span>|<span data-ttu-id="0c34c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0c34c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0c34c-107">AllocVirtual — metoda</span><span class="sxs-lookup"><span data-stu-id="0c34c-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="0c34c-108">Przydziela pamięć w przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="0c34c-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="0c34c-109">FreeVirtual — metoda</span><span class="sxs-lookup"><span data-stu-id="0c34c-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="0c34c-110">Zwalnia pamięć, która była przydzielona wcześniej do przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="0c34c-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c34c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c34c-111">Remarks</span></span>  
 <span data-ttu-id="0c34c-112">Klient API (tzn. debuger) musi implementować ten interfejs stosownie do określonego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="0c34c-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="0c34c-113">Na przykład żywy proces miałby inną implementację od tej ze zrzutu pamięci.</span><span class="sxs-lookup"><span data-stu-id="0c34c-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="0c34c-114">Cel może nie obsługiwać modyfikacji regionów pamięci.</span><span class="sxs-lookup"><span data-stu-id="0c34c-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c34c-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c34c-115">Requirements</span></span>  
 <span data-ttu-id="0c34c-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c34c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c34c-117">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="0c34c-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0c34c-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c34c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c34c-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c34c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c34c-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c34c-120">See Also</span></span>  
 [<span data-ttu-id="0c34c-121">ICLRDataTarget — interfejs</span><span class="sxs-lookup"><span data-stu-id="0c34c-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="0c34c-122">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="0c34c-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)