---
title: "ISymUnmanagedMethod::GetScopeFromOffset — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetScopeFromOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b863031cae487a2c081f23aeada1971893aa339f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="beb32-102">ISymUnmanagedMethod::GetScopeFromOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="beb32-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="beb32-103">Pobiera najbardziej otaczającym zakresie leksykalne w ramach tej metody, które umieszcza danego przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="beb32-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="beb32-104">Może być używany w celu rozpoczęcia wyszukiwania zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="beb32-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beb32-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="beb32-105">Syntax</span></span>  
  
```  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="beb32-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="beb32-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="beb32-107">[in] A `ULONG` zawiera przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="beb32-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="beb32-108">[out] Wskaźnik, który jest ustawiony na zwróconego [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="beb32-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="beb32-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="beb32-109">Return Value</span></span>  
 <span data-ttu-id="beb32-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="beb32-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="beb32-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="beb32-111">Requirements</span></span>  
 <span data-ttu-id="beb32-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="beb32-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beb32-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="beb32-113">See Also</span></span>  
 [<span data-ttu-id="beb32-114">ISymUnmanagedMethod — interfejs</span><span class="sxs-lookup"><span data-stu-id="beb32-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)