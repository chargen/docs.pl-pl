---
title: StackOverflowType — Wyliczenie
ms.date: 03/30/2017
api_name:
- StackOverflowType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowType
helpviewer_keywords:
- StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e888b2359336c68ea6fdf52f798145fda12002e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="stackoverflowtype-enumeration"></a>StackOverflowType — Wyliczenie
Zawiera wartości, które wskazują podstawową przyczyną wydarzenia przepełnienie stosu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`SO_ClrEngine`|Przepełnienie stosu spowodowane przez aparat wykonywania.|  
|`SO_Managed`|Przepełnienie stosu spowodowane przez kod zarządzany.|  
|`SO_Other`|Przepełnienie stosu spowodowane przez kod niezarządzany.|  
  
## <a name="remarks"></a>Uwagi  
 Te informacje są przesyłane do hosta przez wywołanie [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
