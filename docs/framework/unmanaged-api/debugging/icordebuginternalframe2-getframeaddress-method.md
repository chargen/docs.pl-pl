---
title: ICorDebugInternalFrame2::GetFrameAddress — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.GetFrameAddress Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d088aaaaa80ee3513a37ea0345d720832504c005
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebuginternalframe2getframeaddress-method"></a>ICorDebugInternalFrame2::GetFrameAddress — Metoda
Zwraca adres stosu wewnętrznego ramki.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAddress`  
 [out] Wskaźnik do `CORDB_ADDRESS` wewnętrzny ramki.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Pomyślnie zwrócono adres wewnętrzny ramki.|  
|E_FAIL|Nie można zwrócić adres wewnętrzny ramki.|  
|E_INVALIDARG|`pAddress` jest `null`.|  
  
## <a name="remarks"></a>Uwagi  
 Wartość zwracana w `pAddress` może służyć do określenia lokalizacji wewnętrznych ramki względem innych ramek na stosie. Nawet w przypadku komputerów z procesorami IA-64 wewnętrzny ramki znajduje się na stosie tylko, a nie ma odpowiedniego wskaźnika do magazynu zapasowego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugInternalFrame2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
