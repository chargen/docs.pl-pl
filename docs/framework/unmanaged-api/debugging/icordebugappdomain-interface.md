---
title: ICorDebugAppDomain Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84a11b6264ac0e241c1975eea5626edbdddce206
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomain-interface1"></a>ICorDebugAppDomain Interface1
Dostarcza metody do debugowania domen aplikacji. Ten interfejs jest podklasą klasy ICorDebugController.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Attach, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|Dołącza debuger do domeny aplikacji.|  
|[EnumerateAssemblies, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Pobiera moduł wyliczający dla zestawów w domenie aplikacji.|  
|[EnumerateBreakpoints, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|Pobiera moduł wyliczający dla wszystkich aktywnych punktów przerwania w domenie aplikacji.|  
|[EnumerateSteppers, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|Pobiera moduł wyliczający dla wszystkich aktywnych steppery w domenie aplikacji.|  
|[GetID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|Pobiera unikatowy identyfikator domeny aplikacji.|  
|[GetModuleFromMetaDataInterface, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|Pobiera obiekt ICorDebugModule z interfejsem określonych metadanych.|  
|[GetName, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|Pobiera nazwę domeny aplikacji.|  
|[GetObject, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|Pobiera wskaźnika interfejsu do typowych domeny aplikacji języka wspólnego (CLR).|  
|[GetProcess, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|Pobiera proces zawierający domeny aplikacji.|  
|[IsAttached, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|Określa, czy debuger jest dołączony do domeny aplikacji.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
