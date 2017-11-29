---
title: "ICeeGen::TruncateSection — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.TruncateSection
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::TruncateSection
helpviewer_keywords:
- TruncateSection method [.NET Framework metadata]
- ICeeGen::TruncateSection method [.NET Framework metadata]
ms.assetid: 0451d752-1e5c-4c9a-8bad-6cd35b7ba3df
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 204c71b55c4ba2ec1e3b137137d8f08845b12e49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="76e84-102">ICeeGen::TruncateSection — Metoda</span><span class="sxs-lookup"><span data-stu-id="76e84-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="76e84-103">Obcina sekcji określonego kodu przez określony czas.</span><span class="sxs-lookup"><span data-stu-id="76e84-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="76e84-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="76e84-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76e84-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="76e84-105">Syntax</span></span>  
  
```  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76e84-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="76e84-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="76e84-107">[in] Sekcja do obcięcia.</span><span class="sxs-lookup"><span data-stu-id="76e84-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="76e84-108">[in] Długość w bajtach, według którego ma zostać obcięta sekcji.</span><span class="sxs-lookup"><span data-stu-id="76e84-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76e84-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76e84-109">Remarks</span></span>  
 <span data-ttu-id="76e84-110">Wywołanie `TruncateSection` tylko wtedy, gdy sekcja specjalne wymagania, które nie są obsługiwane za pomocą innych metod.</span><span class="sxs-lookup"><span data-stu-id="76e84-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76e84-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="76e84-111">Requirements</span></span>  
 <span data-ttu-id="76e84-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76e84-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76e84-113">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="76e84-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="76e84-114">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="76e84-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="76e84-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76e84-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76e84-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76e84-116">See Also</span></span>  
 [<span data-ttu-id="76e84-117">ICeeGen — interfejs</span><span class="sxs-lookup"><span data-stu-id="76e84-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)